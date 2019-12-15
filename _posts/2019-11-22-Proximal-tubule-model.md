---
layout:     post
title:      Proximal Tubule Dynamic Model
subtitle:   Oscillations on Parameters
date:       2019-12-15
updated:    2019-12-15
author:     Jing Yang
stickie:    false
header-img: img/scene8.jpg
catalog: true
tags:
    - My articles
    - Academic
---
# Proximal Tubule Dynamic Model

-----

## Abstract

We developed a dynamic model of a male rat proximal tubule in order to investigate results brought by changes on different lumen boundary conditions. We examined how long it will take to reach a steady state again from a sudden change. We also investigated whether oscillation on a single parameter will result in similar oscillations on other parameters. We determined that these oscillations will not have a significant passive effect on proximal tubule's re-absorption. We also noticed several irregular phenomenon such as phase difference and amplitude difference on the oscillation pattern of concentrations in different part along the tubule. And we tried to explain these response by using physiological knowledge.

**keyword** : Proximal tubule $\cdot$ Oscillations $\cdot$ Concentrations $\cdot$ Dynamic model

-----
## Model Formulation

In proximal tubule, cells and tight junctions between cells form a single-layer cell wall between lumen and bath. We build our model based on the steady state model that Anita Layton published. The model consider fifteen kinds of solutes, including $\rm {Na}^{+}$,$\rm {K}^{+}$,$\rm {Cl}^{-}$,$\rm {HCO}_{3}^{-}$,$\rm H_{2}CO_{3}$,$\rm CO_{2}$,$\rm HPO_{4}^{2-}$,$\rm H_{2}PO_{4}^{-}$,urea,$\rm NH_{3}$,$\rm NH_{4}^{+}$,$\rm H^{+}$,\\$\rm HCO_{2}^{-}$,$\rm H_{2}CO_2$ and glucose. Model contains four compartments (Lumen, cell, lateral space, bath).Solutes are exchanged between different compartments through diffusion, transporters and coupled transporters. System equations are based on mass conservation and electronic neutrality. 

### Water Conservation

Water conservation in cell and lateral space (denoted by subscripts "C" and "P'' respectively) is given by :

$\frac{\mathrm{d} V_{\mathrm{C}}}{\mathrm{d} t}=J_{v, \mathrm{LC}}+J_{v, \mathrm{BC}}+J_{v, \mathrm{PC}}$

$\frac{\mathrm{d} V_{\mathrm{p}}}{\mathrm{d} t}=J_{v, \mathrm{LP}}+J_{v, \mathrm{BP}}+J_{v, \mathrm{CP}}$

where the subscripts "L"and "B" denote lumen and bath respectively, and "v" denotes volume of water. Water conservation in lumen is given by:

$0=-\frac{\partial \mathrm{F}_{v}}{\partial x}+2 \pi r (J_{v,\mathrm{CL}}+J_{v,\mathrm{PL}})$

where $\mathrm{F}_{v}$ means water flow in lumen, $r$ means radius of lumen and partial derivative means along the lumen.

### Solute Conservation

For non-reacting solute $k$, conservation equations are given by:
$\frac{\mathrm{d} V_{\mathrm{C}} C_{k, \mathrm{C}}}{\mathrm{d} t}=J_{k, \mathrm{LC}}+J_{k, \mathrm{BC}}+J_{k, \mathrm{PC}}$
$\frac{\mathrm{d} V_{\mathrm{P}} C_{k, \mathrm{P}}}{\mathrm{d} t}=J_{k, \mathrm{LP}}+J_{k, \mathrm{BP}}+J_{k, \mathrm{CP}}$
$0=-\frac{\partial\left(\mathrm{F}_{v} C_{k,\mathrm{L}}\right)}{\partial x}+2 \pi r (J_{k,\mathrm{CL}}+J_{k,\mathrm{PL}})$

where $C_{k,i}$ denotes the concentration of solute $k$ in compartment $i$ and $J_{k,ij}$ denotes flux of solute $k$ from compartment $i$ to $j$.

Reference

* [Katifori E, Szöllősi G J, Magnasco M O. Damage and fluctuations induce loops in optimal transport networks[J]. Physical Review Letters, 2010, 104(4): 048704.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.104.048704)