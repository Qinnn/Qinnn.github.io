---
layout: post
title: "Notes on COMSOL ( I ) -- lumped port boundary conditions"
categories:
- Research
tags:
- COMSOL

---

[COMSOL Multiphysics](http://cn.comsol.com/) is a general-purpose software platform, based on advanced numerical methods, for modeling and simulating physics-based problems. With COMSOL Multiphysics, you will be able to account for coupled or multiphysics phenomena. With more than 30 add-on products to choose from, you can further expand the simulation platform with dedicated physics interfaces and tools for electrical, mechanical, fluid flow, and chemical applications. Additional interfacing products connect your COMSOL Multiphysics simulations with technical computing, CAD, and ECAD software.

We mainly use RF module and wave optics module to simulate the coupling between tapered fiber and microcavities and field distribution inside the cavities. 

---
This first note mainly deal with lumped port boundary conditions.

Rectangular, Coaxial, and Circular Ports are predefined as shown in the following figure.

<iframe src="https://onedrive.live.com/embed?cid=0769DCB84E94551A&resid=769DCB84E94551A%2165931&authkey=AA9nDbJj8wEi750" width="320" height="94" frameborder="0" scrolling="no"></iframe>

Using these lumped port boundary conditions properly can significantly reduce compute cost.

Besides these, numeric port boundary condition must be used. This condition can be applied to an arbitrary waveguide cross section. When solving a model with a Numeric Port, it is also necessary to first solve for the fields at the boundary.

