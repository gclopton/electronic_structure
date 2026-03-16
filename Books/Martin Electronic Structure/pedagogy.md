# Martin — Electronic Structure: Reading Guide

A prioritized reading plan tailored to DFT+U calibration on ceria, MLIP training, and TTM-MD track simulations.

---

## Critical Path (Read Carefully, In Order)

### Ch 6 → Ch 7: DFT Foundations & Kohn-Sham Auxiliary System
The theoretical core of everything you do in VASP. You need to understand what the Kohn-Sham equations are actually solving, what the auxiliary system means, and what the self-consistency cycle is doing when it converges (or doesn't). Every time your SCF fails on Ce₇O₁₂, the problem lives in the physics of these two chapters.

### Ch 8 → Ch 9: Functionals for Exchange and Correlation I & II
Where you build real understanding of LDA vs GGA, what each approximation throws away, and the theoretical context for DFT+U. Martin doesn't cover Hubbard corrections in depth (that's more Cococcioni & de Gironcoli territory), but you can't understand *why* you need +U until you understand what LDA/GGA gets wrong for strongly correlated systems. Ch 9 in particular likely covers hybrid functionals and corrections beyond standard GGA.

### Ch 11: Pseudopotentials
You use PAW in VASP, and PAW is a bridge between pseudopotentials and all-electron methods. This chapter gives you the physics of what your PAW potentials are doing — frozen core approximation, transferability, the Ce PAW with f-electrons in the valence. When you're choosing between different Ce PAW potentials (Ce, Ce_3, etc.), this is the chapter that tells you what's actually different.

### Ch 13: Plane Waves, Full Calculations
This is how VASP works. Plane-wave basis, energy cutoffs, k-point sampling, Pulay stress, convergence with respect to basis size. Practical and conceptual.

### Ch 10: Electronic Structure of Atoms
Important for understanding the atomic physics of Ce — the 4f shell, why f-electrons are so localized, the competition between 4f and 5d occupancy. This grounds your intuition for why Ce is hard.

### Ch 19: Quantum Molecular Dynamics
Directly relevant. Car-Parrinello vs Born-Oppenheimer MD, how forces are computed from the electronic structure, the adiabatic approximation and when it breaks. This connects the DFT world to the MD world.

---

## Read Selectively (Skim Narrative, Study Specific Sections)

### Ch 2: Overview
Rich conceptual orientation. Worth a full read early on as a map of the field, but conceptual rather than technical.

### Ch 3 & Ch 4: Theoretical Background & Periodic Solids / Bands
Skim unless you hit a gap. If you already know Bloch's theorem, reciprocal space, and band structure basics, these are review. Ch 4 is worth revisiting when interpreting band structures and DOS plots from CeO₂ calculations.

### Ch 12: Plane Waves, Basics
Foundation for Ch 13. If Ch 13 feels hard, come back here. Otherwise skim.

### Ch 17: Augmented Functions, Linear Methods
PAW's intellectual ancestry lives here (LAPW → PAW). Read the sections on PAW specifically — it deepens your understanding of what VASP is doing beyond the pseudopotential picture.

### Ch 20: Response Functions, Phonons and Magnons
Not urgent, but when you eventually need phonon dispersions or want to understand the lattice dynamics side of TTM parameters, this is where to go.

---

## Skip For Now

- **Ch 1** (Introduction) — brief, low density
- **Ch 5** (Uniform Electron Gas) — background for LDA, but Chs 6–8 cover what you need
- **Ch 14** (Tight-Binding) — not your method
- **Ch 15** (Localized Orbitals, Full Calculations) — Gaussian-basis code territory, not VASP
- **Ch 16** (APW, KKR, MTO) — historical methods you don't use
- **Ch 18** (O(N) Methods) — scaling methods for huge systems, not relevant yet
- **Ch 21** (Excitation Spectra) — optical properties, not your focus
- **Ch 22** (Surfaces and Interfaces) — not your current problem
- **Ch 23** (Wannier Functions) — beautiful physics but not urgent for track simulations

---

## Summary

**Read:** 6 → 7 → 8 → 9 → 11 → 13 → 10 → 19 (8 chapters out of 23)

**Skim as needed:** 2, 3, 4, 12, 17, 20

**Skip:** 1, 5, 14, 15, 16, 18, 21, 22, 23
