
## Extra* / Ideas for Last Day Projects
(* not mandatory)

### a) Calculate pKa values

Compute the **pKa** values of *E*- and *Z*-AB as well as *E*- and *Z*-MY. The **experimental pKa of MY** was determined to be **3.3**.
Can theory reprocude this value? Which isomer is associated with that value: *E*, *Z* or a mixture?

- [This tutorial might provide useful information](https://pogorelov.scs.illinois.edu/wp-content/uploads/2019/09/pKa_Estimations_Tutorial_web.pdf)
- [This article might help you](https://chemistry-europe.onlinelibrary.wiley.com/doi/full/10.1002/chem.202303167)

### b) Compare DFT and wavefuntion methods

While TD-DFT is often successful in predicting excited-state properties, its accuracy depends heavily on the choice of functional. 
Unfortunately, there is no universal way to determine in advance which functional will perform best for a given system — different functionals can yield significantly different results.

To avoid this kind of trial-and-error, it is sometimes preferable to use ab initio, unparameterized wavefunction-based methods. 
ORCA provides access to several such approaches, including [EOM-CCSD](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html), [CISD](https://www.faccts.de/docs/orca/6.0/manual/contents/typical/excitedstates.html), and [CASSCF](https://www.faccts.de/docs/orca/6.0/manual/contents/detailed/casscf.html).

In this part of the exercise, simulate the absorption properties of the *E* and *Z*-isomers of Methyl Yellow (MY), as well as their protonated forms — *E/Z*-MYH⁺ (azonium) and *E/Z*-MYH⁺ (ammonium) — using a wavefunction-based method of your choice. 
Compare the computed absorption features (such as vertical excitation energies, relative oscillator strengths, and state ordering) to the results obtained from TD-DFT earlier in the exercise.

