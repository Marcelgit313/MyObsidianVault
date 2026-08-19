
---
## Pathtracing
![[Pasted image 20260819144118.png]]

**Path Types**
L = light source
D = difussion
S = specular reflection/refraction
E = eye/camera
$*$ = caustic

![[Pasted image 20260819144210.png]]

---
**Classical Ray Tracing**
- Sharp mirror like reflections
- perfect transparency
- sharp shadows
*NOT:*
- soft/natural shadows
- indirect lightning/global illumination color bleeding
- caustics focused light pattern through glass/water
- more photorealistic but noisy with not enough samples


![[Pasted image 20260818161040.png]]

Answer: No.

  Rationale: The image shows soft global-illumination effects such as color bleeding, diffuse interreflection, and very soft shadows. Classical ray
  tracing mainly handles direct visibility, mirror reflection, and refraction, and typically produces sharper shadows unless extended with
  distributed/path-tracing techniques.

---
![[Pasted image 20260818161115.png]]

Completed equation:

  $$
  L(x,\omega_r)=L_e(x,\omega_r)+\int_{\Omega} f_r(x,\omega_i,\omega_r),L_i(x,\omega_i),(\omega_i\cdot n),d\omega_i
  $$
L:Radiance, the amount of light traveling from point $(x)$ in direction $(\omega)$.
  
f:BRDF, bidirectional reflectance distribution function; it describes how incoming light from $(\omega_i)$ is reflected toward outgoing$/view$direction $(\omega_r)$.

---
![[Pasted image 20260819123358.png]]

 Using column vectors and right-to-left composition, with T(x) translating along the local x-axis:
  $$M_L = R(\alpha),T(d_L)$$
  
  $$M_A = R(\alpha+\beta),T(d_A)$$

  Here, $M_L$ maps coordinates from the local coordinate system of Luminance into Radiance coordinates, and $M_A$ maps coordinates from the local coordinate system of Atlantis into Radiance coordinates.

  To express Atlantis in the coordinate system of Luminance, the captain inverts the Luminance transform:
  $$\boxed{M_L^{-1}} ; *$$
  

  and applies it after mapping Atlantis into Radiance coordinates:

  $$p_L = M_L^{-1} M_A p_A$$
---
![[Pasted image 20260819124556.png]]

You need two different ways to map the black shape to the red shape.

From the grid:

- black bottom-left point is at ((0,0))
- black bottom-right point is at ((4,0))
- red bottom-left point is at ((5,0))
- red bottom-right point is at ((7,0))

So the red shape is half as wide and half as tall:
$$S\left(\frac12\right)$$
and shifted right by (5):

$T(5)$


One valid transform is:

$$\boxed{M_1 = T(5)S\left(\frac12\right)}$$

Applied right to left: first scale the black shape by ($\frac12$), then translate it right by (5).

The matrix is:

$$M_1 =
\begin{pmatrix}
  \frac12 & 0 & 5\\
   0 & \frac12 & 0\\
   0 & 0 & 1
\end{pmatrix}$$


A second valid transform can scale around the red left point instead of the origin. For example:

$$\boxed{M_2 = T(10)S\left(\frac12\right)}$$

---
![[Pasted image 20260819132605.png]]

The three terms of the Blinn-Phong local lighting model are:

$$\text{ambient}:\quad I_a = k_a L_a$$

$$\text{diffuse}:\quad I_d = k_d L_d \max(0, n \cdot l)$$
  
$$\text{specular}:\quad I_s = k_s L_s \max(0, n \cdot h)^s$$

where$$h = \frac{l+v}{|l+v|}$$
Vectors to annotate in the sketch:

- (n): surface normal, perpendicular to the surface
- (l): direction from the surface point to the light source
- (v): direction from the surface point to the viewer/camera
- (h): half-vector between (l) and (v)

![[Pasted image 20260819143222.png]]

The three terms of the Phong local lighting model are:
  $$\text{ambient}:\quad I_a = k_a I_L$$
  $$\text{diffus}:\quad I_d = k_d I_L \max(0, N \cdot L)$$
  $$\text{spekular}:\quad I_s = k_s I_L \max(0, R \cdot V)^n$$

Die Vektoren in der Skizze:

  - (N): Normale, bereits eingezeichnet nach oben
  - (L): Richtung vom Oberflächenpunkt zur Lichtquelle (linker Pfeil)
  - (V): Richtung vom Oberflächenpunkt zur Kamera / zum Betrachter (rechter Pfeil)
  - (R): perfekt reflektierte Lichtrichtung (neben N rechts)

---
![[Pasted image 20260819134131.png]]

For c, diffuse reflection is maximal where
$$n \cdot l$$

is maximal.

The cube has center ((0,0,0)) and side length (2), so in the sketch it spans

$$x \in [-1,1], \qquad y \in [-1,1].$$

The light is at ((-4,2,0)), so it shines most directly onto the upper-left corner of the cube.
$$\boxed{(x_D,y_D)=(-1,1)}$$

because there the surface normal points most toward the light direction, so $(n \cdot l)$ is largest.

For d, specular reflection is maximal where the light direction reflects toward the camera.

Light:
$$L=(-4,2)$$

Camera:
$$C=(-4,-2)$$

The symmetric point between them on the left face of the cube is halfway in (y):
$$y_S = 0$$

and the left face has
$$x_S=-1$$

So:
$$\boxed{(x_S,y_S)=(-1,0)}$$

because at the middle of the left face, the incoming light ray from above reflects downward toward the camera.

---
![[Pasted image 20260819142733.png]]

a)
$$RGB(x)=\beta_1RGB(p_1)+\beta_2RGB(p_2)+\beta_3RGB(p_3)$$ where:
$$\beta_{i}=\frac{A_i}{A_1+A_2+A_3}$$
b)



---
## Color Spaces

- CMY: Cyan/Magenta/Yellow => Printing
- CMYK: Cyan/Magenta/Yellow/Key => Printing
- RGB: Red/Green/Blue => Displays
- HSV: Hue/Value/Saturation => UIs
- YUV: Luminance/Chromas => image compression application

YUV $\to$ HSV: H/S = egal wenn U=V; V = Y
CMY $\to$ RGB: R = $1-C$; G = $1-M$; B = $1-Y$
RGB $\to$ HSV: H = Das zwischendrin (kuerzester Weg); S = $\max - \min / \max$; V = $\max$

---
## Graphics Pipeline

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

---
## Modeling

- meshes
- parametric surfaces
- implicit surfaces