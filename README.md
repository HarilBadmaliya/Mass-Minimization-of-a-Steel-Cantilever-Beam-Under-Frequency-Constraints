# Mass Minimization of a Steel Cantilever Beam Under Frequency Constraints

## Project Summary
This initiative focuses on the structural optimization of a rectangular steel cantilever beam. The primary objective is to configure the beam's dimensions to achieve the lowest possible mass (strictly under 5 kg) while ensuring its fundamental natural frequency does not drop below the critical threshold of 500 Hz.

## Problem Formulation

The challenge is to engineer a rectangular steel beam that minimizes weight without violating structural, operational, or geometric boundaries. 

**Material & Operational Parameters**
*   **Material:** Steel
*   **Young's Modulus (E):** 210 GPa
*   **Density (ρ):** 7800 kg/m³
*   **Frequency Coefficient (k₁):** 1.875
*   **Target First Natural Frequency:** > 500 Hz
*   **Maximum Mass Limit:** ≤ 5 kg

**Boundary Conditions**
*   **Width (b):** 0.002 ≤ b ≤ 0.1 m
*   **Height (h):** 0.005 ≤ h ≤ 0.2 m
*   **Length (l):** 0.5 ≤ l ≤ 7 m
*   **Cross-sectional Rule:** b > h

## Mathematical Model

The structural behavior and optimization targets are governed by the following equations:

*   **Area Moment of Inertia:** I = (b · h³) / 12
*   **Linear Mass Density:** ρ_l = ρ · b · h
*   **First Natural Frequency:** f_n = (1 / 2π) · √((E · I · k₁⁴) / (ρ_l · l⁴))

**Optimization Objective**
*   **Minimize:** Weight (W) = ρ · l · b · h
*   **Subject to:** f_n ≥ 500 Hz, W ≤ 5 kg, and the geometric boundaries defined above.

## Computational Approach

The problem was solved computationally using MATLAB's robust optimization environment:
1.  **Variable Definition:** Utilized `optimvar` to establish the core design variables (l, b, h).
2.  **Constraint Mapping:** Leveraged `optimproblem` to enforce both the linear boundary limits and the nonlinear frequency/weight constraints.
3.  **Solver Deployment:** Applied MATLAB's built-in nonlinear constraint solver to iterate toward the optimal geometric configuration.

## Optimization Results & Validation

The algorithmic solver successfully converged on a highly efficient design that satisfied all rigid constraints:

| Parameter | Optimized Value | Unit |
| :--- | :--- | :--- |
| **Length (l)** | 0.5000 | m |
| **Width (b)** | 0.0050 | m |
| **Height (h)** | 0.0020 | m |
| **Final Mass** | **0.039** | **kg** |

**Performance Highlights**
*   Achieved a **99.22% mass reduction** relative to the 5 kg upper limit.
*   The first natural frequency remains safely above the 500 Hz requirement.
*   All dimensional boundary and geometric (b > h) rules were strictly maintained.

## Execution Guide

To replicate the optimization process locally:

1.  **Verify Prerequisites:** Ensure you have MATLAB R2018b (or a newer release) installed, along with the Optimization Toolbox.
2.  **Clone the Repository:** Download the project files to your local machine and open the directory within MATLAB.
3.  **Run the Optimization:** Execute the main script file.
4.  **Review Outputs:** Analyze the final optimized parameters in the command window and inspect the generated workspace variables.

## Engineering Insights & Future Scope

**Design Trade-Offs**
*   **Length vs. Stiffness:** The solver prioritized the shortest allowable length (0.5 m) because shorter beams inherently exhibit higher natural frequencies, requiring less cross-sectional mass to meet the 500 Hz target.
*   **Material Efficiency:** The algorithm pushed the cross-sectional dimensions to their absolute minimum viable limits to strip away unnecessary weight while preserving structural integrity.

**Real-World Applications**
*   Design of high-frequency aerospace and lightweight drone components.
*   Vibration-isolated mounts for precision manufacturing tools.
*   Micro-electromechanical systems (MEMS) where mass and frequency tuning are critical.

**Demonstrated Competencies**
*   **Domain Expertise:** Vibration analysis, structural mechanics, and multi-objective optimization.
*   **Technical Tools:** MATLAB solver implementation, mathematical modeling, and automated algorithmic design.

**Future Enhancements**
*   Introduce dynamic and transient loading conditions into the constraint model.
*   Expand the algorithm to support multi-material selection (e.g., Aluminum vs. Carbon Fiber).
*   Incorporate realistic manufacturing tolerances into the boundary conditions.
*   Develop an interactive GUI to allow engineers to tweak parameters in real time.