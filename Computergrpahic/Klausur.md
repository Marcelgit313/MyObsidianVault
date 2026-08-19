
## Pathtracing

**Path Types**
L = light source
D = difussion
S = specular reflection/refraction
E = eye/camera
$*$ = caustic

**Classical Ray Tracing**
- Sharp mirror like reflections
- perfect transparency
- sharp shadows
*NOT:*
- soft/natural shadows
- indirect lightning/global illumination color bleeding
- caustics focused light pattern through glass/water
- more photorealistic but noisy with not enough samples

**Rendering Equation**

![[Pasted image 20250828150252.png]]

**BRDF:** Bidirectional Reflectance Distribution Function

## Color Spaces

- CMY: Cyan/Magenta/Yellow
- CMYK: Cyan/Magenta/Yellow/Key
- RGB: Red/Green/Blue
- HSV: Hue/Value/Saturation
- YUV: Luminance/Chromas

YUV $\to$ HSV: H/S = egal wenn U=V; V = Y
CMY $\to$ RGB: R = $1-C$; G = $1-M$; B = $1-Y$
RGB $\to$ HSV: H = Das zwischendrin (kuerzester Weg); S = $\max - \min / \max$; V = $\max$

## Modeling

- meshes
- parametric surfaces
- implicit surfaces

**Detailed surface appearance**
- color/texture mapping
- bump/normal mapping
- displacement mapping

## Lighting Models and BRDFs

![[Pasted image 20250828170039.png]]

- diffuse: $k_d<N,L>$
- specular: $k_s<N,H>^n$
- ambient: $k_a$

## Graphics Pipelines

![[Pasted image 20250828171637.png]]

**Output:**
- depth test
- blending
- stencil test
**Fragment Stage*:**
- bump mapping
- lighting model
- shadow mapping
**Primitive Assembly/Scan converison:**
- primitive assembly
- scan conversion (rasterization)
- clipping/cutting
**Vertex Stage*:**
- geometric transformation
- attribute transformation
- model views






