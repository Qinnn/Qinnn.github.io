---
layout: post
title: "Notes on COMSOL ( II ) -- SBC and PML"
categories:
- Research
tags:
- COMSOL

---

When solving wave electromagnetics problems, it is likely that you will want to model a domain with open boundaries — that is, a boundary of the computational domain through which an electromagnetic wave will pass without any reflection. COMSOL Multiphysics offers several solutions for this. Today, we will look at using scattering boundary conditions and perfectly matched layers for truncating domains and discuss their relative merits.

For 2D fields, Sommerfeld radiation condition, can be written as:

$$
\huge
\lim_{r\rightarrow\infty}\sqrt{r}\left(\frac{\partial E_z}{\partial r}+ik_0E_z\right)=0
$$

First-order scattering boundary condition (SBC):

$$
\huge
\mathbf{n}\cdot(\nabla E_z)+ik_0E_z=0
$$

Second-order SBC

$$
\huge
\mathbf{n}\cdot(\nabla E_z)+ik_0E_z-\frac{i}{2k_0}\nabla_t^2E_z=0
$$

Mathematically speaking, the PML is simply a domain that has an anisotropic and complex-valued permittivity and permeability. Although PMLs are theoretically non-reflecting, they do exhibit some reflection due to the numerical discretization: the mesh. To minimize this reflection, we want to use a mesh in the PML that aligns with the anisotropy in the material properties. 

The reflection from a PML with respect to incident angle as compared to the SBCs is shown in the following figure:

<iframe src="https://onedrive.live.com/embed?cid=0769DCB84E94551A&resid=769DCB84E94551A%2165932&authkey=ADUHleFwoEOq1b0" width="320" height="245" frameborder="0" scrolling="no"></iframe>

Clearly, the PML is the best of the approaches described here. However, the PML does use more memory as compared to the SBC.
