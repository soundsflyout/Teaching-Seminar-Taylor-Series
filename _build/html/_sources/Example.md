# Examples of Taylor Approximations

```{code-cell} ipython3
:tags: [remove-input]

import numpy as np
import math 
from bokeh.layouts import column, row, layout
from bokeh.models import ColumnDataSource, CustomJS, Slider
from bokeh.plotting import figure
from bokeh.io import push_notebook, show, output_notebook
output_notebook()
```

## Taylor Approximations of cos(x)

Below is a graph of $\cos(x)$ compared to its Taylor approximations. The formula for the approximations are 
```{math}
    p_{2n}(x) := \sum_{k=0}^n \frac{(-1)^k}{(2k)!}x^{2k} \;.
```
Here we only care about the even degrees since $\cos^{(n)}(0) = 0$ when $n$ is an odd number. In blue is the graph of $\cos(x)$ and in red is the graph of $p_n(x)$. Change the degree to see what happens! 

```{code-cell} ipython3
:tags: [remove-input]
taylor_approximate_cos = lambda degree, x: sum([((-1)**(k//2))*x**k/math.factorial(k) for k in range(0,degree+1,2)])


x =np.linspace(-200,200,10000)
cosine =np.cos(x)
y = taylor_approximate_cos(4,x)

source = ColumnDataSource(data=dict(x=x, y =y))
cos_graph = ColumnDataSource(data=dict(x=x, y=cosine))

plot = figure(title="Taylor Approximation of cos(x)", 
              tools="crosshair,pan,reset,save",
              x_range=[-6,6], y_range=[-5,5])

plot.line('x', 'y', source=source, line_width=3, line_alpha=0.8, color = "red")
plot.line('x','y', source=cos_graph, line_width=3, line_alpha=0.8, color ="blue")

degree = Slider(title="degree", value=4, start=0, end=20, step=2)

callback = CustomJS(args=dict(source=source), code=""" 
    const d = cb_obj.value
    const x = source.data.x

    function test(d,x) {
        let soln = 0;
        let factorial = 1;
        for (let i=0; i <=d; i++) {
            if (i != 0) {
                factorial = factorial*i;
            }
            if (i % 2 == 0) { 
                soln += Math.pow(-1,i / 2)*Math.pow(x, i)/factorial ;
                }
            }
        return soln;
    }

    const y = Array.from(x, (x) => test(d,x))
    source.data = { x, y}
""")

degree.js_on_change("value", callback)
show(column(degree, plot))
```