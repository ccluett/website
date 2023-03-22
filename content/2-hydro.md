---
title: hydro
nav: false
---

Reynolds Averaged Navier Stokes (RANS) CFD is a time averaged approch to simulate a flow field. I use Ansys Fluent to solve applied hydrodynamics problems using RANS CFD, such as performance and powering prediction of UUVs and surface vessels, control surface modeling, and interaction of components in a flow field.

------

## DARPA SUBOFF

The DARPA SUBOFF model and Carderock Tow Tank data are available in the public domain and serve as a valdiation data set for CFD. Using 3D RANS CFD, good correlation is able to be demonstrated between tow tank and CFD.

{% include figure.html img="picture2.png" width="100%" %}

{% include figure.html img="suboff-results.png" width="100%" %}

------

## Solcum Glider Flight Performance

CFD aided in identifying and quantifying poor flight performance of a Solcum Glider, and helped develop solutions for integrating scientific sensors while maintaining flight performance. 

{% include figure.html img="slocum-glider.JPG" width="100%" %}

------

## Propeller Performance Simulation

Propeller performance can be modeled using either steady and unsteady RANS. For highest fidelity simulations, overset or adaptive grids are used with a transient approach. Rotating frames of reference can be used for a steady state simulation, which greatly reduces computational resources required. The Potsdam Propeller is a validation data set available in the public domain. I conducted this simulation using a relatively small grid at a fixed RPM across a range of advance velocities to develop the open water propeller curves to compare to tank tested results. Overall, it demonstrates the ability to get reasonable results using a computationally efficient rotating frame of reference approach.

{% include figure.html img="potsdam.png" width="100%" %}

{% include figure.html img="potsdam-curves.png" width="100%" %}

------

## Physics of a Turning Maneuver for UUVs

I built a 6-degree of freedom model of a UUV, using CFD and emprical methods to develop a set of hydrodynamic coefficients of the vehicle for both forward and reverse. The model combines rigid body dynamics with hydrodynamic forces and moments to develop the equations of motion for a UUV in all 6-degrees. The model uses Feldman's Revised Standard Equations of Motions for a Submarine. I put the below graphic together to better help illustrate the physics of a turning maneuver. Principles of Naval Architecture Vol III is used as reference.

{% include figure.html img="turning.JPG" width="200%" %}

