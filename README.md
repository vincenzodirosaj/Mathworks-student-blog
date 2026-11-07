# Water-Propelled Aircraft | MATLAB & Simulink Flight Simulation

### Airbus Sloshing Rocket Workshop 2023 · Team AirSloths

**MATLAB · Simulink · Aerospace Blockset · Digital DATCOM · Flight Dynamics**

> **1st Place — Airbus Sloshing Rocket Workshop 2023, Belgrade**  
> A flight-dynamics and simulation study developed by **Vincenzo Junior Di Rosa** and **Piercarlo Mirto**, University of Naples Federico II.

**[Read our article on the official MathWorks Student Lounge](https://blogs.mathworks.com/student-lounge/2025/01/07/simulating-water-propelled-aircraft-for-airbus-sloshing-rocket-workshop/)** · **[Explore the complete Airbus workshop project](https://github.com/vincenzodirosaj/Airbus-Sloshing-Rocket-Workshop)** · **[View the original MATLAB/Simulink code](https://github.com/VincenzoPiercarlo/Simulating-Water-Propelled-Aircraft-for-ASRW)**

## Overview

This repository focuses on the **mathematical modeling and MATLAB/Simulink flight simulation** of the water-propelled rocket–glider designed by Team AirSloths for the 2023 Airbus Sloshing Rocket Workshop.

While the [main Airbus Sloshing Rocket Workshop repository](https://github.com/vincenzodirosaj/Airbus-Sloshing-Rocket-Workshop) presents the broader aircraft development and competition project, **this repository documents its simulation-focused contribution**: evaluating the effect of a deployable V-tail on aircraft attitude, trajectory, and flight range.

The model compares a **gliding configuration**, in which the V-tail contributes aerodynamic forces and pitching moments, against a **non-gliding reference configuration** without that tail contribution.


### Aircraft Concept

<p align="center">
  <img src="https://blogs.mathworks.com/student-lounge/files/2025/01/25jan7_2.png" alt="AirSloths water-propelled aircraft CAD model with deployable V-tail" width="420" />
</p>
<p align="center"><em>AirSloths rocket–glider CAD model. The deployable V-tail supports the transition from powered ascent to gliding descent.</em></p>

### Flight Simulation — Animated Results

<p align="center">
  <img src="https://blogs.mathworks.com/student-lounge/files/2025/01/25jan7_6.gif" alt="MATLAB and Simulink flight simulation animation showing the aircraft trajectories" width="620" />
</p>
<p align="center"><em>Embedded animated GIF of the simulated trajectories, originally published in our MathWorks Student Lounge article.</em></p>


## Simulink Flight Dynamics Model

The flight simulation was implemented in `simulateFlight.slx`, coupling MATLAB-derived aircraft properties, aerodynamic data and propulsion inputs with a **longitudinal, variable-mass 3-DOF model**.

### Simulation architecture

<p align="center">
  <img src="https://blogs.mathworks.com/student-lounge/files/2025/01/25jan7_4.png" alt="Simulink top-level model showing gliding and non-gliding configurations, stop conditions and 3-DOF animation" width="760" />
</p>
<p align="center"><em>Figure 1 — Simulink model architecture: parallel gliding and non-gliding flight simulations, stop conditions and trajectory visualization.</em></p>

The two configurations are evaluated under the same initial conditions to isolate the contribution of the deployable V-tail to the resulting flight trajectory.

### Forces, moments and equations of motion

<p align="center">
  <img src="https://blogs.mathworks.com/student-lounge/files/2025/01/25jan7_5.png" alt="Simulink aircraft dynamics subsystem with aerodynamic and propulsion forces, variable inertia and 3-DOF equations of motion" width="760" />
</p>
<p align="center"><em>Figure 2 — Aircraft dynamics subsystem: propulsion and aerodynamic loads feed the 3-DOF equations of motion, with time-varying mass and inertia properties.</em></p>

The model combines aerodynamic forces and pitching moments, water-rocket propulsion and time-dependent inertial properties. A launch-phase pitching-moment filter represents the initial constraint imposed by the launch tube.

| Model component | Implementation |
| --- | --- |
| **Aircraft mass properties** | Component-based geometry, center of gravity, and inertia calculations in MATLAB |
| **Aerodynamics** | Digital DATCOM coefficients imported into MATLAB and supplied to Simulink through lookup tables |
| **Propulsion** | Water-rocket thrust and mass-flow evolution, including the pitching moment due to thrust eccentricity |
| **Equations of motion** | Variable-mass and variable-inertia 3-DOF dynamics using an Aerospace Blockset block |
| **V-tail deployment** | Aerodynamic configurations spanning 0° (folded) to 75° (deployed), linked to the vehicle's elevation angle |
| **Flight evaluation** | Parallel gliding/non-gliding simulation, ground-contact stop conditions, trajectory comparison, and 3-DOF visualization |

The purpose was to study the transition from a streamlined, rocket-like ascent to a lift-producing gliding descent, including the post-apogee pitch-down and subsequent pull-up maneuver.

For the detailed model architecture, equations, and illustrations, see the **[MathWorks technical article](https://blogs.mathworks.com/student-lounge/2025/01/07/simulating-water-propelled-aircraft-for-airbus-sloshing-rocket-workshop/)**.

## Simulation Results

In the published simulation scenario:

- **+6.545 m** modeled range improvement with the deployed-tail gliding configuration compared with the non-gliding configuration.
- **8.4987 m** maximum simulated altitude for both configurations.
- The deployed V-tail supported a **post-apogee pull-up maneuver**, changing the descent trajectory and improving the modeled range.

These values refer to the specific simulated conditions, rather than a generally validated performance gain.

### Model scope

The model assumes a **rigid aircraft**, **no liquid sloshing**, **no avionics latency**, and **longitudinal symmetry**. Although sloshing was central to the overall competition, this particular simulation focuses on flight dynamics and tail-deployment effects; it does **not** directly resolve sloshing dynamics.

## MathWorks Mentorship & Publication

During the project, we benefited from **technical mentoring and guidance from MathWorks**, including support from **[Khushin Lakhara](https://www.linkedin.com/in/khushin/)**, Aerospace Engineer at MathWorks, in developing our MATLAB/Simulink simulation approach.

Our work was subsequently featured on the **official MathWorks Student Lounge** in the article *[Simulating Water-Propelled Aircraft for Airbus Sloshing Rocket Workshop](https://blogs.mathworks.com/student-lounge/2025/01/07/simulating-water-propelled-aircraft-for-airbus-sloshing-rocket-workshop/)* (7 January 2025).

## Project Links & Credits

- **[Complete aircraft and competition project](https://github.com/vincenzodirosaj/Airbus-Sloshing-Rocket-Workshop)** — broader design and development context.
- **[Original co-authored simulation source](https://github.com/VincenzoPiercarlo/Simulating-Water-Propelled-Aircraft-for-ASRW)** — MATLAB Live Scripts and Simulink model.
- **[Official MathWorks article](https://blogs.mathworks.com/student-lounge/2025/01/07/simulating-water-propelled-aircraft-for-airbus-sloshing-rocket-workshop/)** — technical walkthrough and simulation results.

**Simulation development:** Vincenzo Junior Di Rosa and Piercarlo Mirto.  
**Competition team:** AirSloths — University of Naples Federico II.  
**MathWorks mentor:** [Khushin Lakhara](https://www.linkedin.com/in/khushin/).

> This repository presents the simulation work as part of a broader team project. The original co-authored repository remains the reference for the implementation and applicable license.
