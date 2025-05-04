---
title: toroidal
nav: false
---

# Toroidal Propeller Geometry Generator

This repository contains MATLAB scripts designed to generate 3D surface geometry of toroidal propellers.

## Methodology

The generation process is based on parameterizing the propeller geometry along its **axial span (l/L)**, rather than purely radially. This approach is essential for accurately capturing the complex, continuous shape of the toroidal blades.

Key geometric parameters are defined as distributions along this axial span in an offset table. These include:

*   Standard propeller parameters: local radius (`r_l/R`), chord (`b/D`), pitch (`P/D`), thickness-to-chord ratio (`t/b`), camber-to-chord ratio (`f/b`), skew (`θs`), and rake (`x_l/D`).
*   Toroidal-specific parameters necessary to define the blade's 3D path and orientation: **lateral angle (`φ`)**, **roll angle (`ψ`)**, and **vertical angle (`α`)**.

The mathematical formulation used to transform these distributed parameters into 3D Cartesian coordinates (`x`, `y`, `z`) for points on the blade surface is derived from the method presented by Ye, Wang, and Son (2024). The coordinate system that defines the blade geometry can be expressed as:

$$
\begin{aligned}
x &= (R + r \cos \theta) \cos \phi \\
y &= (R + r \cos \theta) \sin \phi \\
z &= r \sin \theta
\end{aligned}
$$

Ref: Ye L Y, Wang C, Sun C, et al. “Mathematical expression method for geometric shape of toroidal propeller”. *Chinese Journal of Ship Research*, 2024.

## Key Features

*   **Base Geometry + Scaling:** The code utilizes a base offset table (`getBaseOffsets`) representing a reference toroidal propeller design. Users can modify this base design by applying scaling factors to the distributions of pitch, chord, thickness, camber, skew, and rake via the main `Params` struct in `generateToroidalProp.m`. The hub radius (`hubRadius`) can also be parametrically adjusted.
*   **Blade Section Definition:** A dedicated `BladeSection.m` class handles the generation of the 2D airfoil profiles at each axial station.
    *   It currently implements the **NACA 66 (DTRC Modified)** thickness distribution and **NACA a=0.8** meanline profile using robust `pchip` interpolation on tabulated data.
    *   The class structure separates meanline and thickness definitions, allowing for easier extension to other airfoil families in the future.
*   **Cosine Spacing:** For improved geometric fidelity, especially near edges and roots, the discretization along both the axial span (`nSpan`) and the chordwise direction (`nChord`) utilizes **cosine spacing** (`getCosineSpacing`).

## Integration

This codebase is being developed as a modular tool. It is intended to complement and potentially integrate with established open-source propeller design frameworks like **OpenProp**, providing specific capabilities for generating toroidal geometries that can then be used within broader design and analysis workflows.

## Usage and Output

1.  Configure the desired propeller parameters within the `Params` structure in the main script `generateToroidalProp.m`.
2.  Run the `generateToroidalProp.m` script.
3.  The script outputs arrays (`xCoords`, `yCoords`, `zCoords`) containing the coordinates of points defining the surfaces of a single blade, which are then rotated to generate all blades (`allBlades` struct). This point cloud data can be used for meshing, visualization, or further analysis. Optional plotting and export functions are included or planned.

## Repository

The complete MATLAB source code is available on GitHub.
