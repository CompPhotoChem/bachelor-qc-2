# Abschlussprojekt 2
## Substituent Effects on the Low-Energy Absorption Features of Benzene

**supervisor:** Prof. Carolin Müller

----

## Introduction and Goal

Dyes that efficiently absorb visible light are essential in areas ranging from photovoltaics and photocatalysis to sensing and imaging.
Traditionally, strong and red-shifted absorption has been achieved using large, highly conjugated π-systems.
While effective, this strategy often relies on structurally complex molecules that require demanding syntheses and substantial material resources.

Single-benzene chromophores challenge this conventional design principle.
Remarkably, even a single aromatic ring can exhibit strongly shifted absorption when appropriately functionalized with different substituents.
In this project, you will computationally investigate a series of such functionalized single-benzene chromophores.
The goal is to understand how specific substitution patterns alter the low-energy absorption features of benzene to derive strategies for shifting the low-energy absorption towards the visible region of the solar spectrum.

To this end, you will compute and compare the absorption spectra of benzene and selected mono- and disubstituted benzene derivatives. 
Firstly, choose either one substituent or a pair of two different substituents from the provided list and construct four substituted variants.

| Electron-donating | Intermediate | Electron-withdrawing |
|---|---|---|
| -N(CH<sub>3</sub>)<sub>2</sub> (dimethylamino) | -Br (bromo) | -CHO (aldehyde) |
| -NH<sub>2</sub> (amino) | -Cl (chloro) | -COOH (acid) |
| -OH (hydroxy) | -CH<sub>3</sub> (methyl) | -NO<sub>2</sub> (nitro) |
| -OCH<sub>3</sub> (methoxy) | -CF<sub>3</sub> (trifluormethyl) | -CN (cyano) |

For example, choosing chlorine could lead to the following set:

- chlorobenzene
- 1,2-dichlorobenzene
- 1,3-dichlorobenzene
- 1,4-dichlorobenzene

Choosing a chloro and nitro substituent could instead lead to:

- nitrobenzene
- chlorobenzene
- 1-chloro-2-nitrobenzene
- 1-chloro-4-nitrobenzene

## Task

Compute the electronic absorption properties, i.e. vertical excitation energies and oscillator strengths for your set of substituted benzenes and the unsubstituted benzene at the same level of theory (e.g. at TDDFT level or EOM-CCSD level of theory, see [Orca's documentation on 'UVVis spectroscopy'](https://www.faccts.de/docs/orca/6.0/tutorials/spec/UVVis.html)).

|      | Task                                      | Solvent        | Method         | Notes                                 |
|------|-------------------------------------------|----------------|----------------|---------------------------------------|
| 1 | Structure optimization <br> $S_0^{min}$ of Benzene | Benzene | B3LYP/def2-TZVP, D3 | Ground-state equilibrium geometries |
| 2,3,4,5 | Structure optimization <br> $S_0^{min}$ of 4 substituted benzenes | Benzene | B3LYP/def2-TZVP, D3 | Ground-state equilibrium geometries |
| 6,7,8,9,10 | TDDFT Calculations for the minimum geometries of benzene and it's substited variants | Benzene  | TD-B3LYP/def2-TZVP, D3 | Absorption spectra |

## Report

Identify the relevant low-energy absorption features (e.g. ππ* or charge transfer features), and discuss how the type, number and (relative) position of the substituents influence the absorption properties compared to benzene.

> [!IMPORTANT]
> a) Compile for the bright optical transitions (oscillator strengths > 0.1) in the visible spectral window between 350 and 800 nm the following properties:
> 
>  - vertical excitation energies,
>  - oscillator strengths,
>  - nature of the transition (image of the respective CDD)
>
> b) Plot the simulated absorption spectra of all 5 compounds in a single plot or grouped in multiple plots and assign the absorption bands (e.g. ππ* band).
> 

Compare the respective electronic absorption properties and spectra the different substituted variants with respect to the unsubstituted benzene and to  each other.
Discuss the differences: How do the vertical excitation energies shift by substitution. Is the low energy band a comparable ππ* band to benzene or does the nature of the transition change?
Make a suggestion how to achieve di-substituted benzene with most red-absorbing substitution from the above list?

<details>
<summary><strong>Tips</strong></summary>
<br>
What are the excitation energies and oscillator strengths for similarly categorized transitions for the 5 compounds?
<br><br>
Which structure absorbs stronger at lower energies (higher wavelengths), why?
</details>
