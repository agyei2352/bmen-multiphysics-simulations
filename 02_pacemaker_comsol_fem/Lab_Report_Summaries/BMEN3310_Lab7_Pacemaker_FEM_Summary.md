# BMEN 3310 Lab 7: Bipolar Cardiac Pacemaker Electrode in Conductive Myocardium

**Course:** BMEN 3310 - Biomedical Engineering Laboratory (Bioelectricity & Multiphysics)  
**Author:** Prince Agyei (agyei2352@icloud.com)  
**Software:** COMSOL Multiphysics (Electric Currents Interface)  

---

## 1. Executive Summary & Clinical Engineering Context

Cardiac pacemakers deliver localized electrical impulses to depolarize excitable myocardial tissue and re-establish physiologic ventricular contraction rhythms. In bipolar endocardial lead configurations, pacing stimulus energy is focused between a distal cathode tip and a proximal ring anode.

In this finite element investigation:
1. A **3D stationary electrophysiology model** of a bipolar pacing lead embedded in a representative block of cardiac myocardium was developed in **COMSOL Multiphysics**.
2. Biological tissue properties were parameterized using an isotropic electrical conductivity of **$\sigma = 0.4\text{ S/m}$**.
3. Electric potential gradients ($1\text{ V to } 0\text{ V}$) and volumetric current-density streamlines ($\mathbf{J} = -\sigma \nabla V$) were computed to characterize current spread, capture thresholds, and energy loss into surrounding ventricular muscle.

---

## 2. Key Quantitative Findings

- **Active Pacing Volume:** The peak current density magnitude exceeded **$127.3\text{ A/m}^2$** at the direct hemispherical contact boundary ($r = 1\text{ mm}$), ensuring local transmembrane potential thresholds required for cardiac action potential propagation are reached.
- **Radial Field Attenuation:** Pacing current density dropped precipitously according to inverse-square dispersion ($1/r^2$), decaying to **$<5.1\text{ A/m}^2$** at $5\text{ mm}$ from the cathode.
- **Electrode Shunting Evaluation:** The $10\text{ mm}$ inter-electrode spacing provided strong directional field confinement between tip and ring, minimizing far-field skeletal muscle stimulation and phrenic nerve cross-talk.
- **Governing Equation & Mesh Convergence:** Solved the electroquasistatic Laplace equation $\nabla \cdot (\sigma \nabla V) = 0$ across a fine tetrahedral mesh with boundary layer refinement, demonstrating $<0.2\%$ potential divergence under adaptive h-refinement.

