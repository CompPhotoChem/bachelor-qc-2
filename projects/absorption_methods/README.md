# Absorption spectra of azo dyes

**supervisor:** Prof. Carolin Müller

-----

While TD-DFT is often successful in predicting excited-state properties, its accuracy depends heavily on the choice of functional. 
Unfortunately, there is no universal way to determine in advance which functional will perform best for a given system — different functionals can yield significantly different results.

To avoid this kind of trial-and-error, it is sometimes preferable to use ab initio, unparameterized wavefunction-based methods. 
ORCA provides access to several such approaches, including [EOM-CCSD](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html), [CISD](https://www.faccts.de/docs/orca/6.0/manual/contents/typical/excitedstates.html), and [CASSCF](https://www.faccts.de/docs/orca/6.0/manual/contents/detailed/casscf.html).

In this part of the exercise, simulate the absorption properties of the *E* and *Z*-isomers of an azo-dye of your choice — using a wavefunction-based method of your choice. 
Compare the computed absorption features (such as vertical excitation energies, relative oscillator strengths, and state ordering) to the results obtained from TD-DFT simulations.

## Goals

- compute electronic absorption spectra of the E/Z-isomers an azo dye at TDDFT and wavenfunction level of theory
- compare results from TDDFT and wavefunction methods

<img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/projects/absorption_methods/project_AB_abs.png" width="300px" />

## Calculations

Choose an azo dye of your interest from [PhotoChemCAD](https://www.photochemcad.com/databases/common-compounds/azo-dyes) or work with AB/MY from the [previous excercise](https://github.com/CompPhotoChem/bachelor-qc-2/tree/main/azobenzene).

|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 1 | Structure optimization <br> $S_0^{min}$ of *E*-isomer   | Benzene  | B3LYP/def2-TZVP, D3 |  Ground-state equilibrium geometries |
| 2 | Structure optimization  <br> $S_0^{min}$ of *Z*-isomer  | Benzene  | B3LYP/def2-TZVP, D3 | Ground-state equilibrium geometries |
| 1,2 | TDDFT Excited State Calculations | Benzene  | TD-B3LYP/def2-TZVP, D3 | Absorption spectra of *E*-/*Z*-isomers of azo dye |
| 3,4 | Wavefunction-method Excited State Calculations | Benzene  | wavefunction method | Absorption spectra of *E*-/*Z*-isomers of azo-dye |

The experimental absorption spectra of AB other azo-dyes listed in PhotoChemCAD can be downloaded from [PhotoChemCAD](https://www.photochemcad.com/databases/common-compounds/azo-dyes).
The experimental absorption spectrum of methyl yellow can be found [here](https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/abs_AB_MY_benzene.dat).
You can plot the spectrum alongside your results e.g. with python (see below), Scidavis, etc.

<details>
<summary><strong>Plot spectra with Python </strong></summary>
<br>
Example for plotting the experimental absorption spectra of azobenzene (AB) and methyl yellow (MY) from the provided file.
  
```python

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the data
df = pd.read_csv("abs_AB_MY_benzene.dat", sep='\t')

# Set a clean style
sns.set(style="whitegrid")

# Plot each spectrum
sns.lineplot(x=df['nm'], y=df['AB'], label='E-AB')
sns.lineplot(x=df['nm'], y=df['MY'], label='E-MY')

# Label the plot
plt.xlabel("wavelength in nm")
plt.ylabel("normalized absorbance")
plt.legend()
plt.tight_layout()
plt.show()
```
</details>

## Report

> [!IMPORTANT]
> a) Compile for the bright optical transitions (oscillator strengths > 0.1) in a spectral window between 250 and 600 nm the following properties:
> 
>  - vertical excitation energies,
>  - oscillator strengths,
>  - nature of the transition (image of the respective CDD)
>
> b) Plot the simulated absorption spectra (TDDFT and wavefunction level of theory) and assign the absorption bands (e.g. ππ* band).
> 

Compare the respective electronic absorption properties and spectra of the *E*- and *Z*-isomer of your azo dye as obtained at TDDFT and wavefunction level of theory.
Discuss the differences and make a suggestion of a suitable method for describing the absorption properties of your azo dye.

<details>
<summary><strong>Tips</strong></summary>
<br>
What are the excitation energies and oscillator strengths for similarly categorized transitions at both levels of theory?
<br><br>
Which isomer absorbs stronger at lower energies (higher wavelengths), why? Is this consistently described at both levels of theory?
</details>


