# Absorption spectra of azobenzene 


While TD-DFT is often successful in predicting excited-state properties, its accuracy depends heavily on the choice of functional. 
Unfortunately, there is no universal way to determine in advance which functional will perform best for a given system — different functionals can yield significantly different results.

To avoid this kind of trial-and-error, it is sometimes preferable to use ab initio, unparameterized wavefunction-based methods. 
ORCA provides access to several such approaches, including [EOM-CCSD](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html), [CISD](https://www.faccts.de/docs/orca/6.0/manual/contents/typical/excitedstates.html), and [CASSCF](https://www.faccts.de/docs/orca/6.0/manual/contents/detailed/casscf.html).

In this part of the exercise, simulate the absorption properties of the *E* and *Z*-isomers of Methyl Yellow (MY), as well as their protonated forms — *E/Z*-MYH⁺ (azonium) and *E/Z*-MYH⁺ (ammonium) — using a wavefunction-based method of your choice. 
Compare the computed absorption features (such as vertical excitation energies, relative oscillator strengths, and state ordering) to the results obtained from TD-DFT earlier in the exercise.

## Goals

- compute electronic absorption spectra of E/Z-azobenzene at wavefunction level of theory
- compare results from TDDFT and wavefunction methods

<img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/projects/absorption_methods/project_AB_abs.png" width="300px" />

## Calculations

You can work with the optimized structures from the [previous TD-DFT exercise](https://github.com/CompPhotoChem/bachelor-qc-2/tree/main/azobenzene).

|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| n.a. | Structure optimization <br> $S_0^{min}$ of *E*- & *Z*-MY      | Acetonitrile  | B3LYP/def2-TZVP, D3 |  Ground-state equilibrium geometries |
| n.a.  | Structure optimization  <br> $S_0^{min}$ of *E*- & *Z*-MYH+  | Acetonitrile  | B3LYP/def2-TZVP, D3 | Ground-state equilibrium geometries |
| 1,2  | Excited State Calculations | Acetonitrile  | *e.g.* [STEOM-CCSD/def2TZVP](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html) | Absorption spectra of *E*-/*Z*-MY |
| 3,4  | Excited State Calculations | Acetonitrile  | *e.g.* [STEOM-CCSD/def2TZVP](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html) | Absorption spectra of *E*-/*Z*-MYH+ |


The experimental absorption spectrum of E-MY can be found [here](https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/abs_AB_MY_benzene.dat).
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

