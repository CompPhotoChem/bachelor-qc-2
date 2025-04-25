# Excited-State Simulations of Azobenzene-type Photoswitches
## Introduction

**Photoswitches** are molecules that can reversibly change their structure upon exposure to light. 
These changes in geometry often lead to shifts in physical or chemical properties, making photoswitches valuable in fields ranging from molecular machines and smart materials to drug delivery and optoelectronics.

A classic example of a molecular photoswitch is **azobenzene**, which can undergo reversible *E*-to–*Z* isomerization upon photoexcitation. 
The absorption characteristics of azobenzene — and how they are altered by protonation or substitution — make it an ideal system for studying **structure–property relationships** in excited-state chemistry.

In this practical course, we will use **excited state simulations** to explore how these factors influence the absorption behavior of azobenzene and its derivatives. 
The calculations will primarily rely on **Time-Dependent Density Functional Theory (TD-DFT)**, with an optional comparison to wavefunction-based methods for more accurate results.

## Goals

- Learn how to perform TDDFT simulations in [ORCA](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html)
- Calculate excited states in solution (implicit solvation)
- Visualize Charge Density Differences (CDDs)
- Explore how the electronic absorption properties depend on
    - the spatial configuration (*E/Z*-isomers), and
    - electronic effects (induced by protonation and introduction of substituents)

## Calculations — Part I

In the first part, we will focus on the *E/Z*-isomers of azobenzene (*E/Z*-AB) and their mono-protonated forms (*E/Z*-ABH+), as visualized below:

<img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/img/AB_ABH%2B_black.png" width="400px" />

### I.a) Absorption Properties of *E*-/*Z*-AB and *E*-/*Z*-ABH+ (gas)

|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 1,2  | Structure optimization <br> $S_0^{min}$ of *E*- & *Z*-AB     | -  | B3LYP/def2-TZVP |  Ground-state equilibrium geometries |
| 3,4  | Structure optimization  <br> $S_0^{min}$ of *E*- & *Z*-ABH+  | -  | B3LYP/def2-TZVP | Ground-state equilibrium geometry,<br> use minimum geometry of the <br> unprotonated isomers as starting point |
| 5,6  | Excited State Calculations | -  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*-/*Z*-AB |
| 7,8  | Excited State Calculations | -  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*-/*Z*-ABH+ |

<br>

> [!IMPORTANT]  
> ## Charge Density Differences (CDDs)
>
> A charge density difference (also called electron density difference) is a visualization that shows how the electron density changes when a molecule transitions between two states — here between the ground state and an excited state.
> In simple terms, it tells you where electrons are coming from and going to during a photoexcitation.
> 
> <details>
> <summary><strong>Step 1: Generating cube files with Multiwfn </strong></summary>
> <br>
> We will generation the charge density differences from the TD-DFT outputs using [Multiwfn](http://sobereva.com/multiwfn/).
> To this end, you firstly need to convert the orbital files `*.gbw` to `*.molden` files using the ```orca6_2mkl``` function, *e.g.*, 
> ```bash
> orca_2mkl td_ss_E-AB_gas -molden 
> ```
> Next, start Multiwfn and load the `*.molden` file, e.g., run the following in a terminal:
> 
> ```
> multiwfn td_ss_E-AB_gas.molden
> ```
>
> This will open a menu, where you navigate by typing numbers or strings into the terminal.
> To generate a charge density difference cube file, the subsequent choices are listed below:
> 
> ```
> 18        #Electron excitation analysis
> 1         #Analyze and visualize hole-electron distribution, transition dipole moment and transition density
> 'outfile' #Input the path of the ORCA output file
> 'state'   #There are N transitions, analyze which one?  e.g. 1 (for S1)
> 1         #Visualize and analyze hole, electron and transition density and so on
> 2         #High quality grid  , covering whole system, about vieeeeele points in total
> 15        #Output cube file of charge density difference to current folder
> 0         #Return
> 0         #Return
> 0         #Return
> # repeat for all states of interest
> (-10      #Exit)
> ```
> </details>
> 
> <details>
> <summary><strong>Step 2: Visualizing CDDs from cube files with VMD </strong></summary>
> <br>
> To visualize the `*.cub` files, you can use VMD.
> You can open VMD form ther terminal, by simply typing `vmd`.
> 
> To display the charge density differences, you need to display the surface of the elctron hole and electron excess of a transition.
> To this end, go to `Graphics > Representation`. This will open a menu.
> Click the button `Create Rep`, select as the Drawing Method from the Dropdown Menu `Isosurface` and adapt the Isovalue, e.g. use 0.001.
> Change the color of the surface by Choosing in the Coloring Method dropdown menu `Color ID` and choose an ID in the newly appearing dropdown menu, *e.g.* `32` for yellow.
> Repeat these steps, and use the isovalue from before but as negative number, *e.g.*, -0.001 and select a different color, e.g. `23` for blue.
> 
> This shows you your molecule with the two electron densities, whereas in the respective selected transition electron density is shifted (in this example) from blue to yellow.
> This visualization will help you to assess the nature of the electronic transition.
> Below you find a GIF illustrating these steps at the example of the $S_1$ and $S_2$ state of *E*-AB (in vacuum).
>
> <details>
> <summary><strong>🎥 Visualizing a CDD from a cube file with VMD</strong></summary>
> <img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/img/vmd_cdds.gif" width="1000px" />
> </details>
> </details>
>

### I.b) Absorption Properties of *E*-/*Z*-AB and *E*-/*Z*-ABH+ (acetonitrile)

As seen above the main, low-energy absorption bands of the investigated azobenzene dyes are of nπ* and ππ* character.
Naturally, these transitions are characterized by different transition dipoles, in other words, the nπ* transition is more localized than the ππ* transition as apparent from the CDDs.
Thus, the energetic position of the excited state is assumed to strongly depend on the solvent polarity.
To investigate such a solvatochromism, we will calculate in this part of the excercise the absorption properties of the fours species in a solvent environment as modelled by an implicit solvent model.


|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 9,10  | Excited State Calculation* | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-AB |
| 11,12 | Excited State Calculation* | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-ABH+ |

*Use the vacuum geometries without further re-optimization.

<br>

## Results and Discussion — Part I

> [!IMPORTANT]
> Compile for the two lowest optical excitations, i.e., S<sub>0</sub>→S<sub>1</sub> and S<sub>0</sub>→S<sub>2</sub> for the four studied species in gas and acetonitrile the following properties:
> 
>  - vertical excitation energies,
>  - oscillator strengths,
>  - dipole moments
>  - nature of the transition (image of the respective CDD)
>  

Discuss the following points:

### Part I.a Gas-phase

<details>
<summary><strong>What is the impact of isomerization?</strong></summary>
<br>
Compare the vertical excitation energies and oscillator strengths between the <i>E</i>/<i>Z</i>-isomers (gas): Which isomer absorbs stronger at lower energies (higher wavelengths), why?
<br><br>
One of the isomers has a much brighter (higher osc. strength) nπ* transition than the other, how to rationalize this? (Tip: Compare the dipole momements of the ground and excited states)
</details>

<details>
<summary><strong>What is the impact of protonation?</strong></summary>
<br>
Compare the absorption properties of <i>E</i>-AB and <i>E</i>-ABH+ as well as <i>Z</i>-AB and <i>Z</i>-ABH+. Discuss how protonation influences the absorption behavior of each isomer.
<br>
<br>
As illustrated in Figure 1, experimental data show that protonation causes a shift in the excitation wavelength required for photoisomerization: the <i>E</i>→<i>Z</i> transition 
moves from the UV to the visible region, while the <i>Z</i>→<i>E</i> transition shifts from the visible back to the UV. Does your computational data reproduce this trend at the current level of theory?
</details>

### Part I.b Solvent

<details>
<summary><strong>What is the impact of solvent? </strong></summary>
<br>
Compare the energies of the excited states when calculated with and without solvent methods (Are states red- or blue-shifted, i.e., stabilized or destabilized by solvent?)
<br>
<br>
Compare the nature of the transitions associated with S<sub>1</sub> and S<sub>2</sub> (Does the solvent affect the state ordering?)
</details>

## Calculations — Part II

In this part, we will study the pH-dependent absorption properties of **Methyl Yellow (MY)**, a derivative of AB in which one of the benzene rings is para-substituted with a dimethylamino group.
This electron-donating substituent significantly alters the molecule’s electronic structure and absorption behavior, especially under varying pH conditions.
We will examine how such substitution affects the absorption spectrum, using the same calculation strategy as in the previous section and performing the TDDFT simulations listed below.

Under **acidic conditions**, MY can undergo protonation at two distinct sites:

- At the dimethylamino group, forming an **ammonium** tautomer, and
- At the azo nitrogen, forming an **azonium**-type ion.

These two protonated forms are tautomers with distinct electronic structures and absorption features. 

<img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/img/MY_MYH%2B.png" width="400px" />

Your task is to simulate and compare the absorption spectra of both isomers to determine which species is primarily responsible for visible-light absorption at low pH, to gain 
insight into how protonation site and electronic substitution modulate excited-state properties in AB-type dyes.

|       | Task                                      | Solvent        | Method         | Notes                                 |
|-------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 13,14 | Excited State Calculation* | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-MY |
| 15,16 | Excited State Calculation* | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-MYH+ (azonium) |
| 17,18 | Excited State Calculation* | Acetonitrile (CPCM)  | TD-B3LYP/def2-TZVP | Absorption spectra of *E*- and *Z*-MYH+ (ammonium) |

*The equilibrium geometries of all isomers and tautomers are provided [here]().

## Results — Part II

Compile for the six calculated absorption spectra the same properties as for the first part. Decide which electronic states are relevant based on their oscillator strength.

Discuss the following points:

- What is the effect of the auxochrom (Dimethyl-amino group) on the absorption properties of the neutral and charged isomers?
- Which tautomer, azonium or ammonium, absorbs at lower energy? How to rationalize this?

**Summary**: Create a schematic similar to Figure 1 (used for azobenzene) that illustrates which wavelengths can induce the *E*→*Z* and *Z*→*E* isomerization in MY and its protonated forms MYH⁺. 
Include both protonated tautomers — the **ammonium** ion and the **azonium** ion — in your comparison. 
Indicate the type of light (predicted absorption wavelength) required for each transition, and clearly differentiate between the isomerization pathways for each species.

## Extra* / Ideas for Last Day Projects
(* not mandatory)

### Calculate pKa values

Compute the **pKa** values of *E*- and *Z*-AB as well as *E*- and *Z*-MY. The **experimental pKa of MY** was determined to be **3.3**.
Can theory reprocude this value? Which isomer is associated with that value: *E*, *Z* or a mixture?

- [This tutorial might provide useful information](https://pogorelov.scs.illinois.edu/wp-content/uploads/2019/09/pKa_Estimations_Tutorial_web.pdf)
- [This article might help you](https://chemistry-europe.onlinelibrary.wiley.com/doi/full/10.1002/chem.202303167)

### Compare DFT and wavefuntion methods

While TD-DFT is often successful in predicting excited-state properties, its accuracy depends heavily on the choice of functional. 
Unfortunately, there is no universal way to determine in advance which functional will perform best for a given system — different functionals can yield significantly different results.

To avoid this kind of trial-and-error, it is sometimes preferable to use ab initio, unparameterized wavefunction-based methods. 
ORCA provides access to several such approaches, including EOM-CCSD, CISD, and CASSCF.

In this part of the exercise, simulate the absorption properties of the *E* and *Z*-isomers of Methyl Yellow (MY), as well as their protonated forms — *E/Z*-MYH⁺ (azonium) and *E/Z*-MYH⁺ (ammonium) — using a wavefunction-based method of your choice. 
Compare the computed absorption features (such as vertical excitation energies, relative oscillator strengths, and state ordering) to the results obtained from TD-DFT earlier in the exercise.

