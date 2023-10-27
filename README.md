# Differential Gaussian Rasterization

**What's new** : Except for the RGB image, we also support render depth map and alpha map (both forward and backward process) compared with the [original repository](https://github.com/graphdeco-inria/diff-gaussian-rasterization).

We modify the dependency name as **diff_gauss** to avoid dependecy conflict with the original version. You can install our repo by executing the following command lines
```shell
git clone --recurse-submodules https://github.com/slothfulxtx/diff-gaussian-rasterization.git 
cd diff-gaussian-rasterization
python setup.py install
```

Here's an example of our modified differential gaussian rasterization repo
```python
from diff_gauss import GaussianRasterizationSettings, GaussianRasterizer

rendered_image, rendered_depth, rendered_alpha, radii = rasterizer(
    means3D = means3D,
    means2D = means2D,
    shs = shs,
    colors_precomp = colors_precomp,
    opacities = opacity,
    scales = scales,
    rotations = rotations,
    cov3D_precomp = cov3D_precomp
)
```

Details: By default, the depth is calculated as 'median depth', where the depth values of each pixels covered by 3D Gaussian Splatting are set to be the depth of the 3D Gaussian center. Thus, there exist numerical errors when the scales of 3D Gaussian are large. However, thanks to the densificaiton scheme, most 3D Gaussians are small. Currently, we ignore the numerical error of depth maps. 

Used as the rasterization engine for the paper "3D Gaussian Splatting for Real-Time Rendering of Radiance Fields". If you can make use of it in your own research, please be so kind to cite us.

<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@Article{kerbl3Dgaussians,
      author       = {Kerbl, Bernhard and Kopanas, Georgios and Leimk{\"u}hler, Thomas and Drettakis, George},
      title        = {3D Gaussian Splatting for Real-Time Radiance Field Rendering},
      journal      = {ACM Transactions on Graphics},
      number       = {4},
      volume       = {42},
      month        = {July},
      year         = {2023},
      url          = {https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/}
}</code></pre>
  </div>
</section>
