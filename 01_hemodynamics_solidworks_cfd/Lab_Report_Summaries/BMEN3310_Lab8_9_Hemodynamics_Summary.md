# BMEN 3310 Lab 8 & 9: Arterial Hemodynamics & Non-Newtonian CFD

**Course:** BMEN 3310 - Biomedical Engineering Laboratory (Biomechanics & Multiphysics)  
**Author:** Prince Agyei (agyei2352@icloud.com)  
**Software:** SOLIDWORKS Flow Simulation & SOLIDWORKS 3D CAD  

---

## 1. Executive Summary & Clinical Engineering Context

Atherosclerotic plaques predominantly initiate and develop at geometric discontinuities in arterial vessels, particularly at bifurcations and curves where blood flow departs from undisturbed unidirectional laminar flow. 

In this laboratory research investigation:
1. A **3D bifurcated branching arterial vessel** (representing a carotid or coronary bifurcation) was modeled in SOLIDWORKS CAD.
2. An internal **Computational Fluid Dynamics (CFD)** numerical study was conducted using **SOLIDWORKS Flow Simulation** with a non-Newtonian blood rheology model (Carreau-Yasuda model).
3. The flow field was evaluated utilizing a **100-pipe streamline trajectory visualization** and an **80-particle reflection transport study**.

---

## 2. Key Quantitative Findings

- **Peak Flow Velocity:** Maximum velocity reached **$0.828\text{ m/s}$** entering the daughter branches due to flow constriction.
- **Peak Wall Shear Stress (WSS):** Reached a localized maximum of **$59.55\text{ Pa}$** at the bifurcation apex (carina), where the fluid momentum impacts the branching divider.
- **Recirculation & Stagnation:** Low WSS ($< 1.0\text{ Pa}$) and localized secondary vortex recirculation were observed along the outer non-divider walls of daughter branches, correlating clinically with high-risk sites for endothelial dysfunction and low-density lipoprotein (LDL) accumulation.
- **Pressure Loss Gradient:** Modeled inlet to outlet static pressure gradient ranged from **$100.96\text{ to }101.59\text{ kPa}$** ($\Delta P = 0.63\text{ kPa}$ or $\approx 4.73\text{ mmHg}$).
- **Particle Reflection Study:** 80 discrete erythrocyte particles demonstrated zero permanent stagnation, confirming that under physiologic pressure gradients, cellular reflection and transit through both daughter vessels remain patent.

---

## 3. Governing Navier-Stokes Equations

For incompressible, non-Newtonian laminar fluid flow:

$$\nabla \cdot \mathbf{u} = 0 \quad \text{(Conservation of Mass)}$$

$$\rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} \right) = -\nabla p + \nabla \cdot \boldsymbol{\tau} \quad \text{(Conservation of Momentum)}$$

Where the viscous stress tensor $\boldsymbol{\tau}$ incorporates the shear-rate-dependent viscosity:

$$\boldsymbol{\tau} = \mu(\dot{\gamma}) \left( \nabla \mathbf{u} + (\nabla \mathbf{u})^T \right)$$

$$\mu(\dot{\gamma}) = \mu_\infty + (\mu_0 - \mu_\infty)\left[1 + (\lambda \dot{\gamma})^a\right]^{(n-1)/a}$$

