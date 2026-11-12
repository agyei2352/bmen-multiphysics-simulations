# Cardiovascular Hemodynamics & Multiphysics Simulation Suite

> [!NOTE]
> ### Engineering Portfolio & Technical Archive Notice
> **Development Context:** This project suite was engineered, modeled, and solved as part of advanced biomechanics and bioelectricity laboratory research in Biomedical Engineering (BMEN 3310) at the University of North Texas.  
> **Toolchain:** Simulations, finite element meshing, and non-Newtonian CFD were executed in **SOLIDWORKS Flow Simulation** and **COMSOL Multiphysics**, with mathematical verification in **MATLAB**. VS Code is utilized for documentation, parametric data synthesis, and technical portfolio presentation.  
> **Repository Purpose:** This repository serves as an **external public portfolio and verification archive** for engineering recruiters, hiring managers, and interviewers to inspect the simulation setups, governing equations, mesh convergence, and technical findings.

---

## Executive Overview

Biomedical devices operating within the human body interact with complex multiphysics environments: pulsatile blood flow generates non-linear shear forces against arterial walls, while implantable bioelectronics conduct electrical currents through anisotropic living myocardium.

This repository consolidates two major advanced computational engineering investigations:
1. **Cardiovascular Hemodynamics (CFD):** 3D non-Newtonian laminar blood flow through a bifurcated arterial vessel using **SOLIDWORKS Flow Simulation**.
2. **Cardiac Electrophysiology (FEM):** 3D stationary finite element analysis of a bipolar pacemaker lead in conductive myocardium using **COMSOL Multiphysics**.

```
+-------------------------------------------------------------------------------------------------+
|                        MULTIPHYSICS SIMULATION SUITE ARCHITECTURE                               |
+-------------------------------------------------------------------------------------------------+
|                                                                                                 |
|   +---------------------------------------+       +-----------------------------------------+   |
|   |  MODULE 1: ARTERIAL HEMODYNAMICS     |       |  MODULE 2: CARDIAC ELECTROPHYSIOLOGY    |   |
|   |  (SOLIDWORKS Flow Simulation CFD)     |       |  (COMSOL Multiphysics 3D FEA)           |   |
|   +---------------------------------------+       +-----------------------------------------+   |
|                       |                                                       |                 |
|       +---------------+---------------+                       +---------------+---------------+ |
|       v                               v                       v                               v |
|   +-----------------------+   +-------------------+       +-----------------------+   +-------+ |
|   | 100-Pipe Trajectories |   | 80-Particle Study |       | Potential Field (1-0V)|   | Stream| |
|   | Peak WSS: 59.55 Pa    |   | 100.96-101.59 kPa |       | Myocardium σ = 0.4 S/m|   | lines | |
|   +-----------------------+   +-------------------+       +-----------------------+   +-------+ |
|                       |                                                       |                 |
|                       +-----------------------+-------------------------------+                 |
|                                               |                                                 |
|                                               v                                                 |
|                       +-----------------------------------------------+                         |
|                       | Consolidated Technical Reports & Verification |                         |
|                       +-----------------------------------------------+                         |
+-------------------------------------------------------------------------------------------------+
```

---

## Key Quantitative Simulation Results

| Investigation | Tool | Key Parameter | Value | Engineering Significance |
| :--- | :--- | :--- | :--- | :--- |
| **Arterial Hemodynamics** | SOLIDWORKS Flow | **Peak Wall Shear Stress** | **$59.55\text{ Pa}$** | Localized at bifurcation carina; evaluates endothelial tear/atherosclerosis risk |
| **Arterial Hemodynamics** | SOLIDWORKS Flow | **Peak Flow Velocity** | **$0.828\text{ m/s}$** | Flow constriction entering branch daughter vessels |
| **Particle Transport** | SOLIDWORKS Flow | **Particle Tracking** | **80 Particles** | Solid erythrocyte analogs with reflection boundary conditions |
| **Pressure Gradient** | SOLIDWORKS Flow | **Static Pressure Drop** | **$100.96\text{ to }101.59\text{ kPa}$** | Total driving $\Delta P = 0.63\text{ kPa}$ ($4.73\text{ mmHg}$) |
| **Pacemaker Pacing** | COMSOL FEM | **Myocardial Conductivity** | **$\sigma = 0.4\text{ S/m}$** | Measured human ventricular conductivity constant |
| **Pacemaker Pacing** | COMSOL FEM | **Cathode Contact Density**| **$>127.3\text{ A/m}^2$** | Exceeds cardiac membrane excitation threshold ($r = 1\text{ mm}$) |
| **Pacemaker Pacing** | COMSOL FEM | **Potential Range** | **$1.0\text{ V to } 0.0\text{ V}$** | Bipolar tip-to-ring field confinement over $10\text{ mm}$ spacing |

---

## Governing Multiphysics Equations

### 1. Incompressible Non-Newtonian Navier-Stokes (Hemodynamics)
Blood flow is solved under laminar internal conditions using the non-Newtonian **Carreau-Yasuda** rheology model:

$$\rho (\mathbf{u} \cdot \nabla) \mathbf{u} = -\nabla p + \nabla \cdot \left[ \mu(\dot{\gamma}) (\nabla \mathbf{u} + (\nabla \mathbf{u})^T) \right]$$

$$\mu(\dot{\gamma}) = \mu_\infty + (\mu_0 - \mu_\infty)\left[1 + (\lambda \dot{\gamma})^a\right]^{(n-1)/a}$$

Where:
- $\mu_0 = 0.056\text{ Pa}\cdot\text{s}$ (Zero-shear viscosity)
- $\mu_\infty = 0.00345\text{ Pa}\cdot\text{s}$ (Infinite-shear viscosity)
- $\lambda = 3.313\text{ s}$ (Relaxation time constant)
- $n = 0.3568$ (Power-law shear-thinning exponent)
- $\rho = 1060\text{ kg/m}^3$ (Blood mass density)

### 2. Electroquasistatic Volume Conduction (Cardiac Pacemaker)
In low-frequency electrical stimulation of conductive biological tissue, displacement currents are negligible. The potential distribution $V$ satisfies the conductive Laplace equation:

$$\nabla \cdot \mathbf{J} = 0 \quad \implies \quad \nabla \cdot (\sigma \nabla V) = 0$$

Where current density $\mathbf{J}$ is given by Ohm's law:

$$\mathbf{J} = -\sigma \nabla V = \sigma \mathbf{E}$$

---

## Repository Directory Structure

```text
bmen-multiphysics-simulations/
├── .gitignore                     # Ignores large transient CFD/FEM mesh cache files
├── README.md                      # Master multiphysics documentation & verification report
├── 01_hemodynamics_solidworks_cfd/
│   ├── CAD_Models/                # 3D bifurcated arterial vessel geometries
│   ├── Simulation_Config/         # Boundary conditions & Carreau-Yasuda blood rheology
│   │   ├── blood_rheology_carreau_yasuda.json
│   │   └── mesh_boundary_conditions.json
│   ├── Results_and_Plots/         # Quantitative pressure & shear stress data
│   │   └── pressure_gradient_analysis.csv
│   └── Lab_Report_Summaries/      # Technical lab report writeup (BMEN 3310 Labs 8 & 9)
│       └── BMEN3310_Lab8_9_Hemodynamics_Summary.md
└── 02_pacemaker_comsol_fem/
    ├── Model_Parameters/          # Myocardium conductivity & electrode geometries
    │   └── myocardium_electrophysiology_constants.json
    ├── Results_and_Plots/         # Radial current drop & potential gradient data
    │   └── radial_current_drop_data.csv
    └── Lab_Report_Summaries/      # Technical lab report writeup (BMEN 3310 Lab 7)
        └── BMEN3310_Lab7_Pacemaker_FEM_Summary.md
```

---

## How to Review & Inspect Files

- **Inspect CFD Boundary Conditions & Rheology:** Open [`01_hemodynamics_solidworks_cfd/Simulation_Config/blood_rheology_carreau_yasuda.json`](01_hemodynamics_solidworks_cfd/Simulation_Config/blood_rheology_carreau_yasuda.json) to view the non-Newtonian blood viscosity constants.
- **Review Hemodynamic Pressure Data:** Inspect [`01_hemodynamics_solidworks_cfd/Results_and_Plots/pressure_gradient_analysis.csv`](01_hemodynamics_solidworks_cfd/Results_and_Plots/pressure_gradient_analysis.csv) for pressure loss and wall shear stresses along the normalized vessel length.
- **Inspect Pacemaker FEA Setup:** Open [`02_pacemaker_comsol_fem/Model_Parameters/myocardium_electrophysiology_constants.json`](02_pacemaker_comsol_fem/Model_Parameters/myocardium_electrophysiology_constants.json) to view tissue conductivity ($\sigma = 0.4\text{ S/m}$) and electrode boundary specs.
- **Review Technical Lab Summaries:** Read [`01_hemodynamics_solidworks_cfd/Lab_Report_Summaries/BMEN3310_Lab8_9_Hemodynamics_Summary.md`](01_hemodynamics_solidworks_cfd/Lab_Report_Summaries/BMEN3310_Lab8_9_Hemodynamics_Summary.md) and [`02_pacemaker_comsol_fem/Lab_Report_Summaries/BMEN3310_Lab7_Pacemaker_FEM_Summary.md`](02_pacemaker_comsol_fem/Lab_Report_Summaries/BMEN3310_Lab7_Pacemaker_FEM_Summary.md).

