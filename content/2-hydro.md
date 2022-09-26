---
title: hydro
nav: true
---

Reynolds Averaged Navier Stokes (RANS) CFD is a time averaged approch to simulate a flow field. I use Ansys Fluent to solve applied hydrodynamics problems using RANS CFD, such as performance and powering prediction of UUVs and surface vessels, control surface modeling, and interaction of components in a flow field.

------

## DARPA SUBOFF

The DARPA SUBOFF model and Carderock Tow Tank data are available in the public domain and serve as a valdiation data set for CFD. Using 3D RANS CFD, good correlation is able to be demonstrated between tow tank and CFD.

{% include figure.html img="picture2.png" width="100%" %}

{% include figure.html img="suboff-results.png" width="100%" %}

------

## Solcum Glider Flight Performance

CFD aided in identifying and quantifying poor flight performance of a Solcum Glider, and helped develop solutions for integration of scientific sensors. 

{% include figure.html img="slocum-glider.JPG" width="100%" %}

------

## Propeller Performance Simulation

Propeller performance can be modeled using either steady and unsteady RANS. For highest fielding overset grids are simulated in a transient approach. Rotating frames of reference can be used for a steady state approximation, which allow for a computationally efficient simulation. The Potsdam Propeller is a validation data set available in the public domain. I conducted this simulation using a relatively small grid at a fixed RPM across a range of advance velocities to develop the open water propeller curves to compare to tank tested results. Overall, it demonstrates the ability to get reasonable results using a computationally efficient approach.

{% include figure.html img="potsdam.png" width="100%" %}

{% include figure.html img="potsdam-curves.png" width="100%" %}