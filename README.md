# Water-Propelled Aircraft Flight Simulation
### Airbus Sloshing Rocket Workshop (ASRW) 2023 | Team AirSloths

**MATLAB · Simulink · Digital DATCOM · Flight Dynamics · Aerospace Design**

> **1st place — Airbus Sloshing Rocket Workshop 2023, Belgrade**  
> Developed by **Vincenzo Junior Di Rosa** and **Piercarlo Mirto** as part of Team AirSloths, University of Naples Federico II.

![Water-propelled aircraft flight simulation](https://blogs.mathworks.com/student-lounge/files/2025/01/25jan7_6.gif)

## Project Overview

This project models the flight dynamics of a **water-propelled rocket–glider** developed for the 2023 Airbus Sloshing Rocket Workshop. The objective was to assess how aircraft geometry and a **deployable V-tail** affect flight stability, trajectory, and range.

A MATLAB/Simulink simulation framework was developed to compare two flight configurations:

- **Gliding mode:** the V-tail deploys to generate aerodynamic forces and pitching moments that support the descent and pull-up maneuver.
- **Non-gliding mode:** the same basic model is evaluated without the tail's aerodynamic contribution.

The simulation supported iterative design decisions for the team's competition aircraft.

## Engineering Approach

The model integrates several disciplines:

| Area | Implementation |
| --- | --- |
| Aircraft geometry | Component-based geometric and material definitions |
| Mass properties | Center of gravity and inertia calculations |
| Aerodynamics | Digital DATCOM coefficients imported into MATLAB and represented using Simulink lookup tables |
| Propulsion | Water-rocket thrust profile, including thrust eccentricity and its pitching moment |
| Flight dynamics | Variable-mass, 3-DOF equations of motion in Simulink |
| Configuration analysis | Eight V-tail folding configurations between 0° (closed) and 75° (fully deployed) |
| Visualization | Trajectory comparison and 3-DOF flight animation |

### Vehicle Concept

The aircraft uses a **foldable V-tail** to transition from a rocket-like ascent configuration to a gliding descent configuration. Its tail opening angle is associated with the vehicle's elevation angle to influence pitching behavior throughout the flight.

The team's physical vehicle used a **2 L PET propulsion bottle**, **0.7 L of water**, and a **10 bar initial pressure**. The design also incorporated a separate tank intended to introduce water sloshing during the competition.

![Aircraft CAD model](Simulating-Water-Propelled-Aircraft-for-ASRW/Images/glider%20parts.jpeg)

## Simulation Results

In the reported simulation scenario:

- **+6.545 m flight-range advantage** for the gliding configuration relative to the non-gliding configuration.
- **8.4987 m maximum altitude** for both simulated configurations.
- The deployable tail enabled a post-apogee pitch-down and subsequent pull-up maneuver, improving the modeled descent trajectory.

The numerical results were approximate and were used to inform the design alongside physical flight testing.

## Assumptions and Scope

The reported flight model adopts four simplifying assumptions:

1. The aircraft is treated as a **rigid body**.
2. **Water sloshing is neglected** in the simulation.
3. **Avionics latency is neglected**.
4. The aircraft is assumed to have **longitudinal symmetry**.

**Important:** Although water sloshing was a central requirement of the *competition*, the published simulation **does not directly model sloshing dynamics**. The results therefore describe the simplified flight-dynamics model, not a validated sloshing-response simulation.

## Code and Resources

The original MATLAB/Simulink implementation is available in the co-authored project repository:

**[View the original source code on GitHub](https://github.com/VincenzoPiercarlo/Simulating-Water-Propelled-Aircraft-for-ASRW)**

Key files include:

| File | Purpose |
| --- | --- |
| `main.mlx` | Main MATLAB Live Script |
| `defineAircraftComponents.mlx` | Geometric definition of aircraft components |
| `defineMaterialDensities.mlx` | Material-property inputs |
| `buildAircraft.mlx` | Aircraft configuration assembly |
| `setupInertia.mlx` | Mass and inertia properties |
| `setupAerodynamics.mlx` | Aerodynamic data preparation |
| `setupPropulsion.mlx` | Propulsion data preparation |
| `massflowRate.mlx` | Mass-flow modeling |
| `simulateFlight.slx` | Simulink flight-dynamics model |

For setup, code requirements, and execution details, consult the **original repository**. The project uses MATLAB and Simulink, including functionality from Aerospace Toolbox and Aerospace Blockset.

## Publications and Demonstration

- **MathWorks Student Lounge:** [Simulating Water-Propelled Aircraft for Airbus Sloshing Rocket Workshop](https://blogs.mathworks.com/student-lounge/2025/01/07/simulating-water-propelled-aircraft-for-airbus-sloshing-rocket-workshop/) (January 2025).
- **Flight-test video:** [AirSloths Flight Tests](https://www.youtube.com/watch?v=y8TNEQP7Qss).
- **Original source repository:** [VincenzoPiercarlo / Simulating-Water-Propelled-Aircraft-for-ASRW](https://github.com/VincenzoPiercarlo/Simulating-Water-Propelled-Aircraft-for-ASRW).

## Contributors and Attribution

**Simulation development:** Vincenzo Junior Di Rosa and Piercarlo Mirto.  
**Competition project:** Team AirSloths, University of Naples Federico II.

This README is a portfolio overview of the co-authored work. The original repository contains the implementation and its license; consult it before reusing or redistributing the code.

