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