# PWV-Arterial-Stiffness-Detection

**Computational Hemodynamic Modeling of Pulse Wave Velocity for Arterial Stiffness Detection and Cardiovascular Risk Assessment**

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![NumPy](https://img.shields.io/badge/NumPy-1.21%2B-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4%2B-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## 📖 Introduction

Arterial stiffness is an independent predictor of cardiovascular events, including hypertension, atherosclerosis, and myocardial infarction. **Pulse Wave Velocity (PWV)** — the speed at which the pressure pulse travels along the arterial wall — is the gold-standard non-invasive measure of arterial stiffness. Higher PWV indicates stiffer arteries and elevated cardiovascular risk.

This project builds a simplified computational model of a pulsatile pressure wave traveling through a 0.5 m artery segment, using the **Moens–Korteweg equation** to compute PWV from arterial wall properties. It simulates the mechanical and hemodynamic response of normal and stiff arteries under physiological pulsatile loading, and applies a clinical threshold to classify each artery as **Normal** or **High Risk**. The goal is to evaluate how arterial wall stiffening alters pressure wave propagation and to provide an interpretable framework for cardiovascular risk detection.

---

## 📊 Results

### 1. Computed Pulse Wave Velocities

| Artery Type | Elastic Modulus (Pa) | PWV (m/s) | Detection Result |
|-------------|----------------------|-----------|------------------|
| Normal | 5 × 10⁵ | **3.07** | Normal |
| Stiff | 2 × 10⁶ | **6.14** | High Risk |

Peak PWV in the stiff artery is approximately **2× higher** than the normal artery, crossing the clinical risk threshold of 6.0 m/s. This reflects the reduced compliance of the arterial wall, which causes the pressure pulse to travel faster — a hallmark of vascular aging and cardiovascular disease.

### 2. 3D Spatiotemporal Pressure Distribution

<img width="1070" height="493" alt="image" src="https://github.com/user-attachments/assets/cc4e8180-86b2-4a48-8a2b-d86449df209f" />


*Figure 1: 3D spatiotemporal pressure distribution along the artery for normal (left) and stiff (right) cases.*

### 3. Mid-Artery Pressure Waveform

<img width="726" height="469" alt="image" src="https://github.com/user-attachments/assets/1d13d5e3-34f7-45fb-a743-fe5adea8f573" />


*Figure 2: Mid-artery pressure waveform comparison showing phase shift between normal and stiff arteries.*

### 4. Console Output

<img width="450" height="128" alt="image" src="https://github.com/user-attachments/assets/586e2311-4c6e-468b-b16d-1acda6cac11c" />


*Figure 3: Console output showing computed PWV values and risk classifications.*

### 5. Simulation Summary

| Quantity | Value | Unit |
|----------|-------|------|
| Blood density (ρ) | 1060 | kg/m³ |
| Artery radius (R) | 0.004 | m |
| Wall thickness (h) | 0.0008 | m |
| Heart rate (f) | 1.25 | Hz |
| Pressure amplitude (P₀) | 10,000 | Pa |
| Artery length | 0.5 | m |
| PWV risk threshold | 6.0 | m/s |
| Normal PWV | 3.07 | m/s |
| Stiff PWV | 6.14 | m/s |
| Normal risk classification | Normal | — |
| Stiff risk classification | High Risk | — |

---

## 📋 Key Results Summary

| Quantity | Value | Unit |
|----------|-------|------|
| Normal artery PWV | 3.07 | m/s |
| Stiff artery PWV | 6.14 | m/s |
| PWV ratio (stiff/normal) | ~2.0 | — |
| Pressure amplitude | 10,000 | Pa |
| Heart rate | 1.25 | Hz |
| Artery length | 0.5 | m |
| Risk threshold | 6.0 | m/s |
| Normal detection | Normal | — |
| Stiff detection | High Risk | — |

---

## 🔧 Methods Overview

### Geometry

| Component | Count | Dimensions |
|-----------|-------|------------|
| Artery segment | 1 | 0.5 m length |
| Artery radius | — | 4 mm |
| Wall thickness | — | 0.8 mm |
| Spatial resolution | 200 | points |
| Temporal resolution | 500 | points per cycle |

### Material Properties

| Property | Value | Justification |
|----------|-------|---------------|
| Blood density (ρ) | 1060 kg/m³ | Standard physiological value |
| Normal elastic modulus (E) | 5 × 10⁵ Pa | Healthy arterial wall |
| Stiff elastic modulus (E) | 2 × 10⁶ Pa | Remodeled/stiff arterial wall |
| Wall thickness (h) | 0.0008 m | Typical large artery |
| Artery radius (R) | 0.004 m | Typical large artery |

### Future Work
This project provides a foundation for more advanced hemodynamic and cardiovascular risk modeling. The following extensions are planned:

Nonlinear arterial wall models — Replace linear elasticity with hyperelastic constitutive laws (e.g., Holzapfel–Gasser–Ogden) to capture the realistic strain-stiffening behavior of arterial tissue under physiological loads.

Wave reflection analysis — Incorporate arterial bifurcations and peripheral resistance to model pressure wave reflections, which are clinically significant for understanding augmented pressure and cardiac afterload.

Patient-specific geometry — Import arterial geometry from ultrasound or MRI scans to build subject-specific models for individualized PWV estimation and risk stratification.

Fluid–structure interaction (FSI) — Couple blood flow (fluid domain) with arterial wall deformation (solid domain) to capture the full biomechanical response, including wall shear stress and compliance.

Machine learning integration — Train classifiers (e.g., Random Forest, SVM, or deep learning) on PWV and waveform features for automated cardiovascular risk prediction using large clinical datasets.


