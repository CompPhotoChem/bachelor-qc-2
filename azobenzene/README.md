# Excited-State Simulations of Molecular Photoswitches
## Introduction

**Photoswitches** are molecules that can reversibly change their structure upon exposure to light. 
These changes in geometry often lead to shifts in physical or chemical properties, making photoswitches valuable in fields ranging from molecular machines and smart materials to drug delivery and optoelectronics.

A classic example of a molecular photoswitch is **azobenzene**, which can undergo reversible *E*-to–*Z* isomerization upon photoexcitation. 
The absorption characteristics of azobenzene — and how they are altered by protonation or substitution — make it an ideal system for studying **structure–property relationships** in excited-state chemistry.

In this practical course, we will use **excited state simulations** to explore how these factors influence the absorption behavior of azobenzene and its derivatives. 
The calculations will primarily rely on Time-Dependent Density Functional Theory (TD-DFT), with an optional comparison to wavefunction-based methods for more accurate results.

<img src="https://github.com/CompPhotoChem/bachelor-qc-2/blob/main/azobenzene/img/AB_ABH%2B_black.png" width="400px" />

## Goals

- Learn how to perform (static) excited state simulations in [ORCA](https://www.faccts.de/docs/orca/5.0/tutorials/spec/UVVis.html)
- Calculate excited states in solution (implicit solvation)
- Compare DFT and wave function based methods

## Calculations

### Part I: Absorption Properties of *E*-/*Z*-AB and *E*-/*Z*-ABH+ (gas)

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

### Part II: Absorption Properties of *E*-/*Z*-AB and *E*-/*Z*-ABH+ (acetonitrile)

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

## Results

Compile for the two lowest optical excitations, i.e., S<sub>0</sub>→S<sub>1</sub> and S<sub>0</sub>→S<sub>2</sub> for the four studied species in gas and acetonitrile the followign properties:

- vertical excitation energies,
- oscillator strengths,
- dipole moments
- nature of the transition (image of the respective CDD) 


Discuss the following points:

- What is the impact of isomerization?
    - Compare the vertical excitation energies and oscillator strengths between the *E*/*Z*-isomers: Which isomer absorbs stronger at lower energies (higher wavelengths)?
    - One of the isomers has a much brighter (higher osc. strength) nπ* transition than the other, how to rationalize this? (Tip: Compare the dipole momements of the ground and excited states)

- What is the impact of solvent?
    - Compare the energies of the excited states when calculated with and without solvent methods (Are states red- or blue-shifted, i.e., stabilized or destabilized by solvent?)
    - Compare the nature of the transitions associated with S<sub>1</sub> and S<sub>2</sub> (Does the solvent affect the state ordering?)

