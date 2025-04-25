# Excited-State Simulations of Molecular Photoswitches
## Introduction

**Photoswitches** are molecules that can reversibly change their structure upon exposure to light. 
These changes in geometry often lead to shifts in physical or chemical properties, making photoswitches valuable in fields ranging from molecular machines and smart materials to drug delivery and optoelectronics.

A classic example of a molecular photoswitch is **azobenzene**, which can undergo reversible *E*-to–*Z* isomerization upon photoexcitation. 
The absorption characteristics of azobenzene — and how they are altered by protonation or substitution — make it an ideal system for studying **structure–property relationships** in excited-state chemistry.

In this practical course, we will use **excited state simulations** to explore how these factors influence the absorption behavior of azobenzene and its derivatives. 
The calculations will primarily rely on Time-Dependent Density Functional Theory (TD-DFT), with an optional comparison to wavefunction-based methods for more accurate results.

## Goals

- Learn how to perform (static) excited state simulations in ORCA
- Calculate excited states in solution
- Compare DFT and wave function based methods

## Calculations
### Part I: Absorption Properties of Azobenzene and its Protonated Forms

|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 1,2   | Structure optimization <br> $S_0^{min}$ of *E*- & *Z*-AB  | -              | B3LYP/def2-TZVP |  Ground-state equilibrium geometries |
| 3,4   | Excited State Calculations | -  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-AB |
| 5,6   | Excited State Calculation | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-AB |
| 7,8     | Structure optimization  <br> $S_0^{min}$ of *E*- & *Z*-ABH+  | -              | B3LYP/def2-TZVP | Ground-state equilibrium geometry,<br> use minimum geometry of unprotonated isomers as starting point |
| 9,10  | Excited State Calculations | -  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-ABH$^+$ |
| 11,12 | Excited State Calculation | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-ABH$^+$ |



In this section, we focus on the E and Z isomers of azobenzene, examining how their absorption spectra change with protonation. We will:

- Optimize the ground-state geometries of each isomer.
- Compute vertical excitation energies and oscillator strengths at the TD-DFT level.

    Analyze how protonation influences the nature and intensity of the lowest-energy transitions.
