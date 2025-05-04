---
title: toroidal
nav: false
---

# Advanced Toroidal Propeller Geometry Generation

## The Promise of Toroidal Propellers

Toroidal propellers represent a significant potential leap in marine and aerial propulsion. Their unique, closed-loop blade structure offers compelling advantages over traditional designs:

*   **Reduced Noise:** By eliminating blade tips, the formation of strong tip vortices – a major source of noise – is significantly minimized.
*   **Enhanced Efficiency:** The continuous blade surface and altered vortex dynamics can lead to improved hydrodynamic/aerodynamic performance.
*   **Improved Structural Integrity:** The closed structure inherently offers greater stiffness and strength compared to cantilevered blades.

However, the very geometric complexity that provides these benefits also makes toroidal propellers challenging to design and model using conventional methods.

## My Solution: A Parametric Toroidal Propeller Generator

To address this challenge, I developed a sophisticated MATLAB-based toolset for generating precise 3D geometric models of toroidal propellers. This tool allows for rapid design exploration and provides a solid foundation for detailed performance analysis (CFD, FEA).

*(Placeholder: Image of a generated toroidal propeller model)*

### Key Features & Approach:

1.  **Advanced Mathematical Formulation:**
    *   The geometry is defined using a robust mathematical parameterization based on the work by Ye et al. (Chinese Journal of Ship Research, 2024).
    *   This method uses key parameters distributed along the **axial span (l/L)** rather than just the radius, which is crucial for capturing the toroidal shape.
    *   Parameters include local radius (`r_l/R`), chord (`b/D`), pitch (`P/D`), thickness (`t/b`), camber (`f/b`), skew (`θs`), rake (`x_l/D`), and the critical toroidal parameters: **lateral angle (`φ`)**, **roll angle (`ψ`)**, and **vertical angle (`α`)**.

2.  **Parametric Control & Scaling:**
    *   The core `generateToroidalProp.m` script allows users to define high-level parameters (`Params` struct): Diameter (`D`), Axial Span (`L`), Number of Blades (`Z`).
    *   It starts from a **base offset table** (derived from established designs like the one in Ye et al.) representing a reference toroidal propeller.
    *   Crucially, users can apply **scaling factors** to modify pitch, chord, thickness, camber, skew, and rake distributions, allowing significant design variations from the base geometry. Hub radius (`hubRadius`) can also be parametrically adjusted.

3.  **Sophisticated Blade Section Generation:**
    *   A dedicated `BladeSection.m` class handles the creation of 2D airfoil sections at each axial location.
    *   Currently implements the **NACA 66 (DTRC Modified)** thickness distribution and **NACA a=0.8** meanline, commonly used in marine applications.
    *   The framework separates **meanline** and **thickness** definitions, allowing for future expansion to other profile types (e.g., NACA 4-digit, NACA 16).
    *   Uses robust `pchip` interpolation for smooth profile generation from tabulated data.

4.  **Accurate 3D Point Calculation:**
    *   The `calculatePoint` function implements the core coordinate transformation from the Ye et al. formulation (Equations 16/18 in their paper, adapted in the code).
    *   It precisely maps the 2D section coordinates (`sRatio`, `y_b`, `y_f`) and the interpolated 3D parameters (`params` at a given `lRatio`) onto the toroidal surface in Cartesian coordinates (`x`, `y`, `z`).
    *   Includes calculations for total rake (`x_T`), incorporating both direct rake (`x_l`) and skew-induced rake.

5.  **Optimized Discretization:**
    *   Employs **cosine spacing** (`getCosineSpacing`) along both the axial span (`nSpan`) and chordwise direction (`nChord`). This provides higher point density near the leading/trailing edges and the front/rear root connections, critical areas for accurate flow simulation.

6.  **Modular & Extensible Code:**
    *   The code is structured logically with a main generation script and a separate class for blade sections, making it maintainable and extensible.
    *   Default parameters are handled gracefully (`setDefaultParams`).

*(Placeholder: Image illustrating the key parameters like roll angle, lateral angle on a blade section)*

### Foundation for High-Fidelity Analysis:

While the provided scripts focus on geometry *generation*, the output is a point cloud defining the blade surfaces. This data is directly usable as input for:

*   **Meshing software** for Computational Fluid Dynamics (CFD) analysis (e.g., OpenFOAM, STAR-CCM+).
*   **Finite Element Analysis (FEA)** for structural assessment.
*   **Advanced visualization** and prototyping.

The framework includes flags (`Params.export`, `Params.exportRhino`, etc.) indicating the *intent* to integrate direct export capabilities, further streamlining the design-to-analysis workflow.

*(Placeholder: Image showing CFD mesh generated from the points, or CFD results like pressure contours)*

## Future Directions

This geometry generation capability serves as the cornerstone for a complete toroidal propeller design and analysis system. As outlined in the associated technical proposal, future work leveraging this foundation includes:

*   Integrating with **lifting-line theory** for rapid aerodynamic/hydrodynamic optimization.
*   Developing automated workflows for **high-fidelity CFD** (e.g., RANS with cavitation models) and **acoustic analysis** (e.g., Ffowcs Williams-Hawkings).
*   Extending the framework to handle **counter-rotating** toroidal propeller systems.
*   Exploring **manufacturing constraints** and optimization.

## Conclusion

This work demonstrates a robust and flexible methodology for generating complex toroidal propeller geometries. By combining a rigorous mathematical foundation with parametric control and modular code design, this toolset empowers efficient design exploration and provides the necessary geometric inputs for advanced performance simulations, paving the way for the practical realization of next-generation toroidal propulsion systems.
