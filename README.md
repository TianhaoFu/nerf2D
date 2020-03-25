## nerf2D 

nerf2D is a 2D toy illustration of the [Neural Radiance Fields](http://www.matthewtancik.com/nerf). The code shows how adding the gamma encoding (also referred to as positional encoding) (Eq. 4) in the paper improves results significantly. 

The task is to reconstruct an image from its 2D coordinates. The dataset consists of tuples ((x, y), (r, g, b)) where the input is (x, y) and output is (r, g, b). We train a 2 layer MLP with relu activations to map (x, y) to (r, g, b). The input is normalised (as also mentioned in the paper) to range [-1, 1] and we also output in range [-1, 1]. However, simply training with with raw (x, y) results in blurry reconstructions while adding gamma encoding shows dramatic improvements in the results. The gamma encoding is able to preserve the sharp edges in the image.

![equation](https://latex.codecogs.com/gif.latex?\dpi{200}&space;\large&space;\gamma(p)&space;=&space;[\sin(\pi&space;x),&space;\cos(\pi&space;x),&space;\sin(\pi&space;y),&space;\cos(\pi&space;y),&space;\sin(2\pi&space;x),&space;\cos(2\pi&space;x),\sin(2\pi&space;y),&space;\cos(2\pi&space;y),.....,&space;\sin(2^{L-1}\pi&space;x),&space;\cos(2^{L-1}\pi&space;x),&space;\sin(2^{L-1}\pi&space;y),&space;\cos(2^{L-1}\pi&space;y)&space;])

The sin plots for various values of L look like the following 

![Sin-Plots](sin.png)

The corresponding cos plots are

![Cos-Plots](cos.png)

