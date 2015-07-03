[[1](http://scicomp.stackexchange.com/questions/20073/)] I tried using Python's matplotlib on the logarithm and here is what I got, a kind of starburst pattern.  Since the angle jumps between $\theta = 0$ and $\theta = 2\pi$, contour assumes there is a contour line between those those two points.  Here in in fact $\bbox[#EEEDAA,1pt]{0=2\pi}$  

Perhaps instead of `matplotlib.pyplot.contour` the contour lines can be connected with `meshgrid` and `numpy.where` statements.

## Contour Plot of $\log z$ on $z \in [-1,1] + i[-1,1]$

    import numpy as np
    import matplotlib.pyplot as plt
    %matplotlib inline
    plt.rcParams['figure.figsize']=4,4

    plt.contour(
        np.arange(-1,1,0.01),
        np.arange(-1,1,0.01), 
        np.angle(t[...,None] + 1j*t[None,...]) , 
        levels = 2*np.pi*np.arange(-1,1,0.025)
    )

![enter image description here][1]

  [1]: http://i.stack.imgur.com/f4rGn.png