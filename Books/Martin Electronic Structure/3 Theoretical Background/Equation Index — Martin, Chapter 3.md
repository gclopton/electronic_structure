# Equation Index — Martin, Chapter 3: Theoretical Background

Electronic Structure Vault


## Master Reference

### Definitions & Building Blocks (1–16)

| # | Name | Section |
|---|---|---|
| 1 | Electron kinetic energy $\hat{T}$ | §3.1 |
| 2 | External potential $\hat{V}_{\text{ext}}$ | §3.1 |
| 3 | Electron-electron interaction $\hat{V}_{\text{int}}$ | §3.1 |
| 4 | Nuclear kinetic energy $\hat{T}_{\text{nuclei}}$ | §3.1 |
| 5 | Ion-ion interaction energy $E_{II}$ | §3.1 |
| 6 | Full Hamiltonian for electrons and nuclei | §3.1 |
| 7 | Electronic Hamiltonian (compact form) | §3.1 |
| 8 | Electron density $n(\mathbf{r})$ | §3.1.1 |
| 9 | Hartree energy $E_{\text{Hartree}}$ | §3.2 |
| 10 | Slater determinant | §3.6.2 |
| 11 | Single-body density matrix | §3.6.1 |
| 12 | Fermi-Dirac distribution | §3.6.1 |
| 13 | Joint pair probability $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | §3.7 |
| 14 | Pair distribution function $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | §3.7 |
| 15 | Exchange hole for noninteracting fermions | §3.7.1 |
| 16 | Exchange-correlation hole $n_{\text{xc}}$ | §3.7.2 |

### Theoretical Foundations (17–25)

| # | Name | Section |
|---|---|---|
| 17 | Total energy as expectation value | §3.1.1 |
| 18 | Rayleigh-Ritz variational principle | §3.1.1 |
| 19 | Time-independent Schrödinger equation | §3.1.1 |
| 20 | Force (Hellmann-Feynman) theorem | §3.3.1 |
| 21 | Stress (generalized virial) theorem | §3.3.2 |
| 22 | Virial theorem for pressure | §3.3.2 |
| 23 | Generalized force theorem and coupling constant integration | §3.4 |
| 24 | Free energy and the density matrix | §3.5 |
| 25 | Koopmans' theorem | §3.6.3 |

### Energy Expressions & Functionals (26–30)

| # | Name | Section |
|---|---|---|
| 26 | Classical Coulomb energy grouping $E^{\text{CC}}$ | §3.2 |
| 27 | Total energy decomposition with exchange-correlation | §3.2 |
| 28 | Hartree-Fock total energy | §3.6.2 |
| 29 | Exchange energy from the exchange hole | §3.7.1 |
| 30 | Independent-particle energy at finite temperature | §3.6.1 |

### Approximations & Their Failures (31–34)

| # | Name | Section |
|---|---|---|
| 31 | Born-Oppenheimer (adiabatic) approximation | §3.1 |
| 32 | Noninteracting (Hartree-like) electron approximation | §3.6.1 |
| 33 | Hartree-Fock approximation | §3.6.2 |
| 34 | $\Delta$SCF method | §3.6.4 |


# Definitions & Building Blocks


## 1. Electron kinetic energy $\hat{T}$


> [!question]
>
> (a) Write the electron kinetic energy operator. For a free particle with wavefunction $e^{ikx}$, show that the Laplacian returns $k^2$ and explain what this means: why does a rapidly oscillating wavefunction correspond to high kinetic energy?
> (b) Using the uncertainty principle, explain why confining an electron to a small region forces it to have high kinetic energy. How does this explain why atoms have a finite size rather than collapsing to a point?
> (c) The density tells you *where* electrons are. Why is that not enough to determine the kinetic energy — what additional information do you need?
> (d) What is the Thomas-Fermi approximation for the kinetic energy, and why does it fail qualitatively for atoms? How does the Kohn-Sham construction solve this problem?

> [!definition] Electron kinetic energy (from Eq. 3.1)
>
> $$ \hat{T} = -\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2 = \sum_i -\frac{1}{2}\nabla_i^2 \quad \text{(Hartree units)} $$


Electron kinetic energy, $\hat{T}$ — The operator representing the total kinetic energy of all electrons in the system. The sum runs over every electron $i$, with each term containing the Laplacian $\nabla_i^2$ acting on that electron's spatial coordinates. In SI-like form the prefactor $\hbar^2 / 2m_e$ sets the energy scale using the electron mass $m_e$; in Hartree atomic units (where $\hbar = m_e = 1$) this simplifies to a prefactor of $\frac{1}{2}$. The negative sign arises because the Laplacian of a localized wavefunction is negative in regions of high curvature, so that more spatially confined electrons — those with more rapidly varying wavefunctions — carry greater kinetic energy. This operator is one of the few terms in the electronic Hamiltonian that acts on each electron independently, making it straightforward to evaluate for any single-particle basis set. In density functional theory, the exact many-body kinetic energy is not directly accessible as a functional of the density alone; the Kohn-Sham scheme addresses this by computing the kinetic energy of a fictitious non-interacting reference system and absorbing the remainder into the exchange-correlation functional.



| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{T}$ | Sum of single-electron operators | Hartree | **Electron kinetic energy** | Measures total kinetic energy from wavefunction curvature. Universal — same form in every electron system. |
| $-\frac{1}{2}\nabla_i^2$ | Single-electron operator | Hartree | **Kinetic energy of electron $i$** | The Laplacian measures the second spatial derivative; the prefactor $-1/2$ (in Hartree units) sets the energy scale. |
| $T_{\text{TF}}[n]$ | Density functional | Hartree | **Thomas-Fermi kinetic energy** | Local density approximation to $\langle\hat{T}\rangle$. Exact for the uniform gas; fails for inhomogeneous systems. |

> **Connections Forward:** The inability to write $T[n]$ exactly motivates the Kohn-Sham construction (Ch 7): use auxiliary orbitals to compute the noninteracting kinetic energy $T_s$ exactly, and absorb the remainder $T - T_s$ (kinetic correlation energy) into $E_{\text{xc}}$. The kinetic energy also appears in the stress tensor (Entry 21) and the virial theorem (Entry 22).




## 2. External potential $\hat{V}_{\text{ext}}$


> [!question]
>
> (a) Write the external potential operator and explain why it is the only system-specific term in the Hamiltonian.
> (b) Why does its expectation value reduce to a simple integral over the electron density?
> (c) What is the significance of $\hat{V}_{\text{ext}}$ for the Hohenberg-Kohn theorem?

> [!definition] External potential (from Eqs. 3.1–3.2)
>
> $$ \hat{V}_{\text{ext}} = \sum_{i,I} V_I(|\mathbf{r}_i - \mathbf{R}_I|) = -\sum_{i,I}\frac{Z_I}{|\mathbf{r}_i - \mathbf{R}_I|} \quad \text{(Hartree units, bare Coulomb)} $$



External potential, $\hat{V}_{\text{ext}}$ — The operator representing the total potential energy experienced by the electrons due to all sources external to the electron system itself — most commonly the nuclei. For each electron $i$ and nucleus $I$ of charge $Z_I$ located at $\mathbf{R}_I$, it contributes an attractive Coulomb interaction inversely proportional to their separation $|\mathbf{r}_i - \mathbf{R}_I|$, with the negative sign reflecting the attraction between the negatively charged electron and the positively charged nucleus. The double sum runs over all electrons and all nuclei. Although written here for the specific case of bare (unscreened) Coulomb interactions in Hartree atomic units, the more general form $V_I(|\mathbf{r}_i - \mathbf{R}_I|)$ allows for the substitution of pseudopotentials or other effective ion-electron potentials that replace the singular nuclear Coulomb potential with a smoother function, particularly in solid-state calculations where core electrons are treated implicitly. In density functional theory, the external potential plays a foundational role: the Hohenberg-Kohn theorem establishes that the ground-state electron density uniquely determines $\hat{V}_{\text{ext}}$ (up to a constant), making it the bridge between the nuclear configuration and all electronic properties of the system.


| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{V}_{\text{ext}}$ | Sum of single-electron operators | Hartree | **External potential** | The electron-nuclear attraction. System-specific — encodes what material you are studying. |
| $V_I(\|\mathbf{r} - \mathbf{R}_I\|)$ | Scalar function of position | Hartree | **Nuclear potential from nucleus $I$** | Bare Coulomb: $-Z_I/\|\mathbf{r} - \mathbf{R}_I\|$. Replaced by a pseudopotential in plane-wave calculations. |
| $\int V_{\text{ext}} \, n \, d^3r$ | Scalar | Hartree | **Electron-nuclear energy** | The only term in the total energy that is an explicit, exact functional of the density alone. |

> **Connections Forward:** The Hohenberg-Kohn theorem (Ch 6) proves $n(\mathbf{r}) \to V_{\text{ext}}(\mathbf{r})$ is unique. Pseudopotentials (Ch 11) replace the bare nuclear potential with a smoother effective potential. In VASP, $V_{\text{ext}}$ comes from the POTCAR file (PAW potentials) and the nuclear positions from POSCAR.

## 3. Electron-electron interaction $\hat{V}_{\text{int}}$


> [!question]
>
> (a) Write the electron-electron interaction operator and explain the double-counting correction.
> (b) Why does this term make the many-body problem fundamentally hard?
> (c) How is $\langle\hat{V}_{\text{int}}\rangle$ decomposed into Hartree and exchange-correlation contributions?

> [!definition] Electron-electron interaction (from Eqs. 3.1–3.2)
>
> $$ \hat{V}_{\text{int}} = \frac{1}{2}\sum_{i \neq j} \frac{1}{|\mathbf{r}_i - \mathbf{r}_j|} \quad \text{(Hartree units)} $$


Electron-electron interaction, $\hat{V}_{int}$ - The operator representing the total Coulomb repulsion between all pairs of electrons in the system, expressed here in Hartree atomic units. For each distinct pair of electrons $i$ and $j$, it contributes an energy inversely proportional to their separation $\left|\mathbf{r}_i-\mathbf{r}_j\right|$, reflecting the fact that like charges repel more strongly at shorter distances. The factor of $\frac{1}{2}$ corrects for double-counting, since the unrestricted sum over $i \neq j$ counts each pair twice. This term is the source of the many-body problem in electronic structure theory: because every electron interacts with every other electron simultaneously, the full wavefunction cannot be written as a simple product of oneelectron states. Approximations to this term - such as the mean-field treatment in Hartree and Hartree-Fock theory, or the exchange-correlation functional in density functional theory - form the central distinction between different electronic structure methods.



| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{V}_{\text{int}}$ | Two-electron operator | Hartree | **Electron-electron interaction** | Coulomb repulsion between all electron pairs. Universal. This is the term that makes the problem hard. |
| $\frac{1}{2}\sum_{i \neq j}$ | Sum with double-counting correction | — | **Pair sum** | Counts each pair once: the factor $\frac{1}{2}$ corrects the double-counting in the sum over all ordered pairs. |
| $1/\|\mathbf{r}_i - \mathbf{r}_j\|$ | Coulomb kernel | Hartree/Bohr | **Pair Coulomb repulsion** | Long-ranged: decays as $1/r$ at large separation. Couples electron $i$ to electron $j$. |

> **Connections Forward:** Decomposition into Hartree + xc is the basis of DFT (Ch 7). The coupling constant integration (Entry 23) connects noninteracting and interacting systems by scaling $\hat{V}_{\text{int}}$. The exchange-correlation hole (Entry 16) provides a real-space picture of how $\hat{V}_{\text{int}}$ is modified by quantum effects.

## 4. Nuclear kinetic energy $\hat{T}_{\text{nuclei}}$


> [!question]
>
> (a) Write the nuclear kinetic energy operator.
> (b) Why is $m_e/M_I \ll 1$ the key small parameter, and what approximation does dropping this term correspond to?
> (c) What physical phenomena require keeping this term (or treating it perturbatively)?

> [!definition] Nuclear kinetic energy (from Eq. 3.1)
>
> $$ \hat{T}_{\text{nuclei}} = -\sum_I \frac{\hbar^2}{2M_I}\nabla_I^2 $$



Nuclear kinetic energy, $\hat{T}_{\text{nuclei}}$ — The quantum mechanical kinetic energy operator for the nuclei, representing the energy associated with the translational motion of all nuclei in the system. The sum runs over all nuclei $I$, each with mass $M_I$. The Laplacian $\nabla_I^2$ acts on the coordinates $\mathbf{R}_I$ of nucleus $I$, and the prefactor $\hbar^2 / 2M_I$ sets the energy scale for each nucleus's motion. Because nuclear masses are several orders of magnitude larger than the electron mass, this term is far smaller than its electronic counterpart, which forms the physical basis for the Born-Oppenheimer approximation: the nuclear kinetic energy is separated from the electronic problem, and the nuclei are treated as classical or semiclassical particles moving on a potential energy surface determined by the electronic ground-state energy. This term becomes important again when one explicitly treats nuclear dynamics, as in phonon calculations, molecular dynamics beyond Born-Oppenheimer, or problems involving light nuclei (e.g., hydrogen) where quantum nuclear effects are non-negligible.



| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{T}_{\text{nuclei}}$ | Sum of single-nucleus operators | Hartree | **Nuclear kinetic energy** | Kinetic energy of all nuclei. Small by the factor $m_e/M_I$ relative to electronic energies. |
| $M_I$ | Scalar constant | kg (or atomic mass units) | **Nuclear mass** | Mass of nucleus $I$. $M_I/m_e \gg 1$ is the basis for the Born-Oppenheimer approximation. |
| $\nabla_I^2$ | Differential operator | Bohr⁻² | **Nuclear Laplacian** | Second derivative with respect to nuclear position $\mathbf{R}_I$. Measures the curvature of the nuclear wavefunction. |

> **Connections Forward:** Dropping this term gives the Born-Oppenheimer approximation (Entry 31). Treating it perturbatively gives electron-phonon coupling (Ch 19). Ab initio molecular dynamics (Ch 18) restores nuclear motion classically on the BO energy surface. Nuclear quantum effects (zero-point energy, tunneling) require path-integral methods or explicit nuclear wavefunction calculations.

## 5. Ion-ion interaction energy $E_{II}$


> [!question]
>
> (a) Write the ion-ion interaction energy.
> (b) Why is this a scalar (number) rather than an operator?
> (c) Why does it diverge in an extended system, and how is this handled in practice?

> [!definition] Ion-ion interaction energy (from Eq. 3.1)
>
> $$ E_{II} = \frac{1}{2}\sum_{I \neq J} \frac{Z_I Z_J}{|\mathbf{R}_I - \mathbf{R}_J|} \quad \text{(Hartree units)} $$


Ion-ion interaction energy, $E_{II}$ — The classical Coulomb repulsion energy between all pairs of nuclei (ions) in the system, expressed here in Hartree atomic units (where $e^2 = 1$ and energies are measured in Hartrees). Each pair of nuclei $I$ and $J$, carrying charges $Z_I$ and $Z_J$ and separated by a distance $|\mathbf{R}_I - \mathbf{R}_J|$, contributes a repulsive energy proportional to the product of their charges divided by their separation. The factor of $\frac{1}{2}$ corrects for the double-counting that arises from summing over all ordered pairs. Within the Born-Oppenheimer approximation, the nuclear positions are treated as fixed parameters, making $E_{II}$ a constant for any given nuclear configuration. It therefore does not influence the electronic eigenvalue problem but must be added back to the total energy when comparing energies across different geometries, as in structure optimization or molecular dynamics.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E_{II}$ | Scalar (classical) | Hartree | **Ion-ion interaction energy** | Classical electrostatic repulsion among nuclei. Essential for total energy, irrelevant for electronic structure. |
| $Z_I Z_J / \|\mathbf{R}_I - \mathbf{R}_J\|$ | Scalar | Hartree | **Pair Coulomb repulsion** | Repulsive energy between nuclei $I$ and $J$. Long-ranged. |
| $\frac{1}{2}\sum_{I \neq J}$ | Sum with double-counting correction | — | **Nuclear pair sum** | Counts each nuclear pair once. Same structure as the electron-electron pair sum. |

> **Connections Forward:** Appears in the classical Coulomb grouping (Entry 26) where it combines with $E_{\text{Hartree}}$ and $\int V_{\text{ext}}\,n\,d^3r$ to form the finite $E^{\text{CC}}$. In VASP, the Ewald energy in OUTCAR is $E_{II}$ computed via Ewald summation. The Madelung constant (Appendix F) characterizes $E_{II}$ for specific crystal structures.


## 6. Full Hamiltonian for electrons and nuclei (§3.1)

> [!question]
>
> (a) Write the full Hamiltonian for a system of interacting electrons and nuclei.
> (b) Identify each of the five terms and explain what physics it encodes.
> (c) Which term is the only one that can be treated as a small parameter for a perturbation expansion, and why?

> [!definition] Full Hamiltonian (Eq. 3.1)
>
> $$
> \hat{H} = -\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2 - \sum_{i,I}\frac{Z_I e^2}{|\mathbf{r}_i - \mathbf{R}_I|} + \frac{1}{2}\sum_{i \neq j}\frac{e^2}{|\mathbf{r}_i - \mathbf{r}_j|} - \sum_I \frac{\hbar^2}{2M_I}\nabla_I^2 + \frac{1}{2}\sum_{I \neq J}\frac{Z_I Z_J e^2}{|\mathbf{R}_I - \mathbf{R}_J|}
> $$


Full Hamiltonian, $\hat{H}$ — The total energy operator for a system of interacting electrons and nuclei. It consists of five terms, each representing a distinct physical contribution: (1) the kinetic energy of the electrons, where the Laplacian $\nabla_i^2$ acts on each electron coordinate and $m_e$ is the electron mass; (2) the Coulomb attraction between each electron at $\mathbf{r}_i$ and each nucleus of charge $Z_I$ at $\mathbf{R}_I$; (3) the electron-electron Coulomb repulsion between all distinct pairs of electrons, with the factor of $\frac{1}{2}$ correcting for double-counting; (4) the kinetic energy of the nuclei, with $M_I$ the mass of nucleus $I$; and (5) the nucleus-nucleus Coulomb repulsion between all distinct pairs of nuclei. Under the Born-Oppenheimer approximation, the nuclear kinetic energy (term 4) is separated out and the nuclear positions are treated as fixed parameters, reducing the problem to solving for the electronic degrees of freedom in a static external potential created by the nuclei. The nucleus-nucleus repulsion (term 5) then enters only as a constant energy offset for a given nuclear configuration. The remaining three purely electronic terms define the electronic Hamiltonian proper, whose eigenvalue problem is the central task of electronic structure theory.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $m_e$ | Scalar constant | kg | **Electron mass** | Sets the scale of electron kinetic energy. |
| $M_I$ | Scalar constant | kg | **Nuclear mass** | Mass of nucleus $I$. $M_I/m_e \gg 1$ is the basis for the Born-Oppenheimer approximation. |
| $Z_I$ | Integer | — | **Nuclear charge** | Atomic number of nucleus $I$. |
| $e^2$ | Scalar constant | Hartree·Bohr | **Coulomb coupling** | Strength of the electromagnetic interaction ($e^2 = q_e^2 / 4\pi\epsilon_0$ in SI). |

> **Connections Forward:** Dropping the nuclear kinetic energy gives the electronic Hamiltonian (Entry 7). The nuclear kinetic energy, treated perturbatively, gives electron-phonon coupling (Ch 19) — essential for superconductivity, polaron formation, and electrical transport.



## 7. Electronic Hamiltonian (compact form)



> [!question]
>
> (a) Write the electronic Hamiltonian in compact notation, identifying each of the four terms.
> (b) What physical approximation has already been made in going from the full Hamiltonian Eq. (3.1) to the electronic Hamiltonian Eq. (3.2)?
> (c) Which terms are "universal" (the same for all electron systems) and which are system-specific?



> [!definition] Electronic Hamiltonian (Eq. 3.2)
>
> $$ \hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II} $$


Electronic Hamiltonian (compact form), $\hat{H}$ — The total energy operator for $N$ electrons in a fixed nuclear potential, obtained from the full Hamiltonian by invoking the Born-Oppenheimer approximation (dropping the nuclear kinetic energy term, justified by $m_e/M_I \ll 1$) so that the nuclear positions $\{\mathbf{R}_I\}$ enter only as fixed parameters. It decomposes into four physically distinct contributions: the electron kinetic energy $\hat{T}$, which is universal (identical for every electron system); the external potential $\hat{V}_{\text{ext}}$, the electron-nuclear attraction that is the only system-specific part of the Hamiltonian — what makes CeO$_2$ different from Si or H$_2$; the electron-electron Coulomb repulsion $\hat{V}_{\text{int}}$, summed over all distinct pairs with a factor of $\frac{1}{2}$ to correct for double-counting; and the ion-ion interaction $E_{II}$, a classical scalar (not an operator) that is essential for total energies but plays no role in determining the electronic wavefunction.

### Simplifications

Setting $\hbar = m_e = e = 4\pi/\epsilon_0 = 1$ (Hartree atomic units) eliminates all fundamental constants from the equations, reducing notational clutter. The physics is unchanged. Energies are in Hartrees and lengths in Bohr radii, and the individual terms become:

$$ \hat{T} = \sum_i -\frac{1}{2}\nabla_i^2 \qquad \hat{V}_{\text{ext}} = \sum_{i,I} V_I(|\mathbf{r}_i - \mathbf{R}_I|) \qquad \hat{V}_{\text{int}} = \frac{1}{2}\sum_{i \neq j} \frac{1}{|\mathbf{r}_i - \mathbf{r}_j|} $$


| **Symbol**                                                                            | **Type**                               | **Units**   | **Name**                          | **Description**                                                                                                             |
| ------------------------------------------------------------------------------------- | -------------------------------------- | ----------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| $\hat{H}$                                                                             | Operator on $N$-electron Hilbert space | Hartree     | **Electronic Hamiltonian**        | The total energy operator for $N$ electrons in a fixed nuclear potential. Its eigenvalues are the electronic energy levels. |
| $\hat{T} = \sum_i -\frac{1}{2}\nabla_i^2$                                             | Sum of single-electron operators       | Hartree     | **Electron kinetic energy**       | Measures total kinetic energy from wavefunction curvature. Universal — same form in every electron system.                  |
| $\hat{V}_{\text{ext}} = \sum_{i,I} V_I(\|\mathbf{r}_i - \mathbf{R}_I\|)$              | Sum of single-electron operators       | Hartree     | **External potential**            | The electron-nuclear attraction. System-specific — encodes what material you are studying.                                  |
| $\hat{V}_{\text{int}} = \frac{1}{2}\sum_{i \neq j} 1/\|\mathbf{r}_i - \mathbf{r}_j\|$ | Two-electron operator                  | Hartree     | **Electron-electron interaction** | Coulomb repulsion between all electron pairs. Universal. This is the term that makes the problem hard.                      |
| $E_{II}$                                                                              | Scalar (classical)                     | Hartree     | **Ion-ion interaction energy**    | Classical electrostatic repulsion among nuclei. Essential for total energy, irrelevant for electronic structure.            |
| $\mathbf{r}_i$                                                                        | Position vector                        | Bohr (or Å) | **Electron position**             | Coordinate of electron $i$. Lowercase subscripts denote electrons.                                                          |
| $\mathbf{R}_I$                                                                        | Position vector (parameter)            | Bohr (or Å) | **Nuclear position**              | Coordinate of nucleus $I$. Uppercase subscripts denote nuclei. Fixed parameters under Born-Oppenheimer.                     |

> **Connections Forward:** This Hamiltonian is the starting point for everything in the book. The Hohenberg-Kohn theorems (Ch 6) prove that the ground-state density determines all properties of this Hamiltonian. The Kohn-Sham construction (Ch 7) replaces this intractable many-body operator with an auxiliary single-particle system. In VASP, the nuclear positions come from POSCAR and the external potential from POTCAR.




## 8. Electron density $n(\mathbf{r})$

> [!question]
>
> (a) What physical question does $n(\mathbf{r})$ answer? What are its units, and what does it integrate to over all space?
> (b) The many-body wavefunction $\Psi$ is a function of $3N$ variables. The density is a function of 3. Explain, step by step, how the integration in the definition collapses $3N$ dimensions down to 3, and why the factor of $N$ must appear.
> (c) Why is this compression of information — from $3N$ variables to 3 — so important? What does the Hohenberg-Kohn theorem say about whether any information is lost?
> (d) Write the density for independent particles in terms of single-particle orbitals. Why is this expression so much simpler than the many-body definition?

> [!definition] Electron density (Eq. 3.8)
>
> $$ n(\mathbf{r}) = N \frac{\int d^3r_2 \cdots d^3r_N \sum_{\sigma_1} |\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2}{\int d^3r_1 \, d^3r_2 \cdots d^3r_N \, |\Psi(\mathbf{r}_1, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2} $$


Electron density, $n(\mathbf{r})$ — The probability per unit volume of finding any one of the $N$ electrons at position $\mathbf{r}$, regardless of the positions of all other electrons and regardless of spin. It is obtained by fixing one electron's coordinate at $\mathbf{r}$, summing over its spin, integrating the squared modulus of the full $N$-electron wavefunction over the coordinates of the remaining $N-1$ electrons, and multiplying by $N$ to account for the indistinguishability of electrons. The denominator ensures that the density is properly normalized, meaning $n(\mathbf{r})$ integrates over all space to give exactly $N$, the total number of electrons in the system. The total density $n(\mathbf{r}) = n^\uparrow(\mathbf{r}) + n^\downarrow(\mathbf{r})$ serves as the central variable in density functional theory (DFT), where, by the Hohenberg-Kohn theorems, it uniquely determines (up to a constant) the external potential and hence all ground-state properties of the system.

### Simplifications

For a system of independent particles described by single-particle orbitals $\psi_i^\sigma$ with occupation numbers $f_i^\sigma$, the spin-resolved density reduces to a weighted sum of orbital densities:

$$ n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2 $$

This is far simpler than the full many-body definition because there is no $3N$-dimensional integral to evaluate — each orbital contributes independently.


| **Symbol**                                             | **Name**                         | **Type**                                      | **Units**       | **Description**                                                                                                                                                                    |
| ------------------------------------------------------ | -------------------------------- | --------------------------------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $n(\mathbf{r})$                                        | **Electron density**             | Scalar field: $\mathbb{R}^3 \to \mathbb{R}^+$ | Å⁻³ (or Bohr⁻³) | Expected number of electrons per unit volume at point $\mathbf{r}$. Integrates to $N$. Measurable by X-ray diffraction.                                                            |
| $n^\uparrow(\mathbf{r})$                               | **Spin-up density**              | Scalar field                                  | Å⁻³ (or Bohr⁻³) | Density of spin-up electrons at point $\mathbf{r}$. Obtained by setting $\sigma = \uparrow$ in the spin-resolved density $n^\sigma(\mathbf{r})$.                                   |
| $n^\downarrow(\mathbf{r})$                             | **Spin-down density**            | Scalar field                                  | Å⁻³ (or Bohr⁻³) | Density of spin-down electrons at point $\mathbf{r}$. The total density is $n(\mathbf{r}) = n^\uparrow(\mathbf{r}) + n^\downarrow(\mathbf{r})$.                                    |
| $n^\sigma(\mathbf{r})$                                 | **Spin-resolved density**        | Scalar field                                  | Å⁻³ (or Bohr⁻³) | Density of electrons with spin $\sigma$ at point $\mathbf{r}$, where $\sigma \in \{\uparrow, \downarrow\}$.                                                                        |
| $N$                                                    | **Total number of electrons**    | Integer                                       | —               | The number of electrons in the system. Converts the single-electron marginal probability into a count of all electrons.                                                            |
| $\|\Psi(\mathbf{r}, \mathbf{r}_2, \ldots)\|^2$         | **Joint probability density**    | Function of $3N$ coordinates                  | Bohr⁻$^{3N}$    | Probability per unit ($3N$-dimensional) volume that electron 1 is at $\mathbf{r}$, electron 2 is at $\mathbf{r}_2$, etc. A single point in configuration space.                    |
| $\int d^3r_2 \cdots d^3r_N \sum_{\sigma_1} \|\Psi\|^2$ | **Marginal probability density** | Function of 3 coordinates                     | Bohr⁻³          | Probability density that electron 1 is at $\mathbf{r}$, regardless of its spin and regardless of where all other electrons are. Obtained by integrating out all other coordinates. |
| $\int d^3r_1 \cdots d^3r_N \|\Psi\|^2$                 | **Normalization**                | Scalar                                        | —               | Total probability. Equals 1 for a normalized wavefunction. Included so the definition works for unnormalized $\Psi$.                                                               |
| $\sum_{\sigma_1}$                                      | **Spin trace**                   | Summation over spin                           | —               | Sums over spin-up and spin-down for the electron at $\mathbf{r}$. The density is a spatial quantity — it does not distinguish spin.                                                |
| $\psi_i^\sigma(\mathbf{r})$                            | **Kohn-Sham / Hartree orbital**  | Single-particle orbital                       | Bohr⁻$^{3/2}$   | Eigenstate of the effective single-particle Hamiltonian for spin $\sigma$.                                                                                                         |
| $f_i^\sigma$                                           | **Occupation number**            | Scalar, $0 \leq f_i^\sigma \leq 1$            | —               | Probability of state $(i,\sigma)$ being occupied. Equals 0 or 1 at $T=0$; given by Fermi-Dirac at finite $T$.                                                                      |

> **Connections Forward:** The density is the central variable of DFT (Ch 6–9). The Hohenberg-Kohn theorem proves it determines all ground-state properties. In VASP, the CHGCAR file contains $n(\mathbf{r})$ on a real-space grid.

## 9. Hartree energy $E_{\text{Hartree}}$

> [!question]
>
> (a) Write the Hartree energy in terms of the electron density.
> (b) What physics does it capture, and what does it miss?
> (c) Why does it include a spurious self-interaction, and how is this corrected in Hartree-Fock?


> [!definition] Hartree energy (Eq. 3.15)
>
> $$ E_{\text{Hartree}} = \frac{1}{2} \int d^3r \, d^3r' \, \frac{n(\mathbf{r})\,n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} $$


Hartree energy, $E_{\text{Hartree}}$ — The classical electrostatic self-interaction energy of the electron density with itself. It is computed by treating the electron density $n(\mathbf{r})$ as a continuous charge distribution and calculating the Coulomb repulsion between every pair of infinitesimal charge elements $n(\mathbf{r})\,d^3r$ and $n(\mathbf{r}')\,d^3r'$ separated by a distance $|\mathbf{r} - \mathbf{r}'|$. The factor of $\frac{1}{2}$ prevents double-counting, since each pair of points is integrated over twice. While the Hartree energy captures the dominant portion of the electron-electron repulsion, it is an approximation: it neglects both exchange effects (arising from the antisymmetry of the wavefunction) and correlation effects (arising from the instantaneous avoidance of electrons beyond what mean-field theory describes). These missing contributions are accounted for separately by the exchange and exchange-correlation energy terms, respectively, in Hartree-Fock theory and density functional theory.



| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r})\,n(\mathbf{r}')$ | Scalar function of two positions | Bohr⁻⁶ | **Uncorrelated pair density** | Treats charge at two points as independent — the classical, mean-field approximation to the true pair density. |
| $1/\|\mathbf{r} - \mathbf{r}'\|$ | Coulomb kernel | Bohr⁻¹ | **Pair Coulomb weight** | Weights each pair of charges by the inverse of their separation. |
| $\frac{1}{2}\int d^3r\,d^3r'$ | Double spatial integration | — | **Pair summation with double-counting correction** | Sums the Coulomb repulsion over all pairs; $\frac{1}{2}$ prevents counting each pair twice. |
| $E_{\text{Hartree}}$ | Functional: $n(\mathbf{r}) \mapsto \mathbb{R}$ | Hartree | **Hartree energy** | Classical electrostatic self-energy of the electron charge distribution. Includes spurious self-interaction. |

> **Connections Forward:** The Hartree energy appears in the Kohn-Sham total energy (Ch 7) and in the classical Coulomb grouping (Entry 26). Understanding self-interaction error is essential for understanding why DFT+U is needed for Ce 4f electrons.



## 10. Slater determinant


> [!question]
>
> (a) Write the Slater determinant for $N$ electrons.
> (b) Why does the determinant form automatically enforce antisymmetry?
> (c) What is the relationship between the Slater determinant and the exclusion principle?


> [!definition] Slater determinant (Eq. 3.43)
>
> $$ \Phi = \frac{1}{(N!)^{1/2}} \begin{vmatrix} \phi_1(\mathbf{r}_1,\sigma_1) & \phi_1(\mathbf{r}_2,\sigma_2) & \cdots \\ \phi_2(\mathbf{r}_1,\sigma_1) & \phi_2(\mathbf{r}_2,\sigma_2) & \cdots \\ \vdots & \vdots & \ddots \end{vmatrix} $$


Slater determinant, $\Phi$ — An antisymmetrized, multielectron wavefunction constructed as the determinant of a matrix whose elements are one-electron spin-orbitals $\phi_i(\mathbf{r}_j, \sigma_j)$, written compactly as $\Phi(1, 2, \ldots, N) = (1/\sqrt{N!})\det[\phi_i(\mathbf{r}_j, \sigma_j)]$, where the rows label orbitals and the columns label electrons (or vice versa). It is the simplest wavefunction that satisfies the Pauli exclusion principle: swapping any two columns (exchanging two electrons) flips the sign of the determinant, enforcing antisymmetry. The prefactor $1/\sqrt{N!}$ normalizes the wavefunction when the spin-orbitals are orthonormal. Slater determinants serve as the fundamental building blocks of Hartree-Fock theory and configuration interaction methods, and all correlation beyond exchange is, by definition, what a single determinant cannot capture.

### Simplifications

If any two rows are identical — meaning two electrons occupy the same spin-orbital — the determinant vanishes ($\Phi = 0$). This is the Pauli exclusion principle expressed algebraically: no two electrons can share the same quantum state.

| **Symbol**                       | **Type**                     | **Units**      | **Name**                    | **Description**                                                                                                               |     |
| -------------------------------- | ---------------------------- | -------------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --- |
| $\Phi$                           | $N$-electron wavefunction    | Bohr⁻$^{3N/2}$ | **Slater determinant**      | The simplest antisymmetric many-body wavefunction built from $N$ single-particle orbitals.                                    |     |
| $\phi_i(\mathbf{r}_j, \sigma_j)$ | Single-particle spin-orbital | Bohr⁻$^{3/2}$  | **Spin-orbital**            | Product of a spatial orbital $\psi_i^\sigma(\mathbf{r}_j)$ and a spin function $\alpha_i(\sigma_j)$. Rows of the determinant. |     |
| $1/\sqrt{N!}$                    | Normalization constant       | —              | **Normalization prefactor** | Ensures $\langle\Phi\Phi\rangle = 1$ when spin-orbitals are orthonormal. $N!$ is the number of permutations of $N$ electrons. |     |

> **Connections Forward:** Hartree-Fock (Entry 33) minimizes the energy over single determinants. The Kohn-Sham construction (Ch 7) uses a Slater determinant of auxiliary orbitals to produce the exact density. Correlation (Entry 16) is everything a single determinant misses.

## 11. Single-body density matrix

> [!question]
>
> (a) Write the single-body density matrix operator and its position-spin representation.
> (b) How is the electron density obtained from the density matrix?
> (c) What additional information does the off-diagonal part $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ carry beyond the density?

> [!definition] Single-body density matrix (Eqs. 3.40–3.42)
>
> $$ \hat{\rho} = \sum_i |\psi_i^\sigma\rangle\, f_i^\sigma \,\langle\psi_i^\sigma| $$

Single-body density matrix, $\hat{\rho}$ — An operator that encodes the complete single-particle occupation information for a system of independent or effectively independent electrons, constructed as a weighted sum of projection operators $|\psi_i^\sigma\rangle f_i^\sigma \langle\psi_i^\sigma|$ over all orbitals, where $f_i^\sigma$ is the occupation probability of orbital $i$ with spin $\sigma$. Its diagonal part in the position-spin representation yields the electron density, $n^\sigma(\mathbf{r}) = \rho(\mathbf{r},\sigma;\mathbf{r},\sigma)$, while its off-diagonal part $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma)$ with $\mathbf{r} \neq \mathbf{r}'$ encodes quantum coherence between spatial points and determines quantities the density alone cannot provide, including the kinetic energy and the exchange energy. Any expectation value of a single-body operator reduces to $\langle\hat{O}\rangle = \text{Tr}\,\hat{\rho}\hat{O} = \sum_{i,\sigma} f_i^\sigma \langle\psi_i^\sigma|\hat{O}|\psi_i^\sigma\rangle$, collapsing the many-body trace to a weighted sum over single-particle matrix elements.

### Simplifications

In the position-spin representation, the density matrix becomes:

$$ \rho(\mathbf{r},\sigma;\mathbf{r}',\sigma') = \delta_{\sigma,\sigma'} \sum_i \psi_i^{\sigma*}(\mathbf{r})\, f_i^\sigma \,\psi_i^\sigma(\mathbf{r}') $$

Setting $\mathbf{r}' = \mathbf{r}$ (the diagonal part) recovers the spin-resolved electron density:

$$ n^\sigma(\mathbf{r}) = \rho(\mathbf{r},\sigma;\mathbf{r},\sigma) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2 $$

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{\rho}$ | Operator on single-particle Hilbert space | — | **Single-body density matrix operator** | Encodes all occupation information for independent particles. Positive semi-definite, trace equals $N$. |
| $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Density matrix in position-spin basis** | Diagonal in spin for non-spin-orbit systems. Diagonal part ($\mathbf{r}=\mathbf{r}'$) is the density; off-diagonal part encodes coherence. |
| $\lvert\psi_i^\sigma\rangle\langle\psi_i^\sigma\rvert$ | Operator | — | **Projection operator** | Isolates the contribution of a single quantum state $\lvert\psi_i^\sigma\rangle$ from the full Hilbert space, keeping only the component along that state and discarding everything orthogonal to it. This is what makes it possible to ask "how much of orbital $i$ is present?" in a system that may be a superposition of many states. Weighted by $f_i^\sigma$, it assigns an occupation probability to that orbital in the density matrix. |
| $\psi_i^\sigma(\mathbf{r})$ | Single-particle orbital | Bohr⁻$^{3/2}$ | **Kohn-Sham / Hartree orbital** | Eigenstate of the effective single-particle Hamiltonian for spin $\sigma$. The density matrix is built from these orbitals. |
| $f_i^\sigma$ | Scalar, $0 \leq f_i^\sigma \leq 1$ | — | **Occupation number** | Weight for orbital $i$ with spin $\sigma$. Given by the Fermi-Dirac distribution at finite temperature. |
| $\delta_{\sigma,\sigma'}$ | Kronecker delta | — | **Spin selector** | Equals 1 if $\sigma = \sigma'$, 0 otherwise. The density matrix is diagonal in spin in the absence of spin-orbit coupling. |
| $n^\sigma(\mathbf{r})$ | Scalar field | Å⁻³ (or Bohr⁻³) | **Spin-resolved density** | Diagonal part of the density matrix: $n^\sigma(\mathbf{r}) = \rho(\mathbf{r},\sigma;\mathbf{r},\sigma)$. |

> **Connections Forward:** The density matrix appears in the exchange hole (Entry 29), in the force theorem applied to nonlocal potentials (Ch 13), and in the formulation of the Kohn-Sham equations (Ch 7). In VASP, the density matrix for correlated orbitals is the object that the DFT+U correction acts on.

## 12. Fermi-Dirac distribution

> [!question]
>
> (a) Write the Fermi-Dirac distribution.
> (b) What is the physical meaning of the chemical potential $\mu$?
> (c) What does the distribution reduce to at $T = 0$?

> [!definition] Fermi-Dirac distribution (Eq. 3.38)
>
> $$ f_i^\sigma = \frac{1}{e^{\beta(\varepsilon_i^\sigma - \mu)} + 1} $$

Fermi-Dirac distribution, $f_i^\sigma$ — The equilibrium occupation probability for a single-particle quantum state $(i,\sigma)$ at temperature $T$, giving the probability that the state is occupied by an electron. The exponent $\beta(\varepsilon_i^\sigma - \mu)$ compares the state's energy to the chemical potential $\mu$ in units of the thermal energy $k_BT = 1/\beta$: states well below $\mu$ are fully occupied ($f \approx 1$), states well above $\mu$ are empty ($f \approx 0$), and the transition from occupied to empty is smoothed over an energy window of order $k_BT$ around $\mu$. At zero temperature the distribution becomes a sharp step function, $f = 1$ for $\varepsilon < \mu$ and $f = 0$ for $\varepsilon > \mu$. The chemical potential is determined self-consistently by the constraint that the total occupation $\sum_{i,\sigma} f_i^\sigma = N$ equals the number of electrons; at $T = 0$ it equals the Fermi energy.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $f_i^\sigma$ | Scalar, $[0,1]$ | — | **Fermi-Dirac occupation** | Probability of state $(i,\sigma)$ being occupied at thermal equilibrium. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalue** | Energy of orbital $i$ with spin $\sigma$ from the effective Schrödinger equation. |
| $\mu$ | Scalar | Hartree (or eV) | **Chemical potential** | Energy at which occupation is $\frac{1}{2}$. Equals the Fermi energy at $T=0$. Self-consistently determined by $\sum f_i^\sigma = N$. |
| $\beta = 1/(k_BT)$ | Scalar | Hartree⁻¹ | **Inverse temperature** | Sets the energy scale of thermal smearing. $\beta \to \infty$ at $T=0$. |

> **Connections Forward:** The Fermi-Dirac distribution is used in all finite-temperature DFT calculations. In VASP, `ISMEAR` and `SIGMA` control the smearing scheme — Fermi-Dirac smearing (`ISMEAR = -1`) directly implements this distribution. The E-fermi in OUTCAR is $\mu$.

## 13. Joint pair probability $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$

> [!question]
>
> (a) Write the definition of the joint pair probability.
> (b) How does it decompose into an uncorrelated part and a correlation correction?
> (c) Why is the measure of correlation short-ranged?

> [!definition] Joint pair probability (Eqs. 3.50–3.51)
>
> $$ n(\mathbf{r},\sigma;\mathbf{r}',\sigma') = N(N-1) \sum_{\sigma_3,\ldots} \int d\mathbf{r}_3 \cdots d\mathbf{r}_N \, |\Psi(\mathbf{r},\sigma;\mathbf{r}',\sigma';\ldots)|^2 $$
>
> Decomposition:
>
> $$ n(\mathbf{r},\sigma;\mathbf{r}',\sigma') = n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma') + \Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma') $$

Joint pair probability, $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ — The probability density for simultaneously finding one electron of spin $\sigma$ at position $\mathbf{r}$ and a different electron of spin $\sigma'$ at position $\mathbf{r}'$, obtained by integrating the squared modulus of the many-body wavefunction over all electron coordinates except two and multiplying by $N(N-1)$ to account for the number of distinct pairs. It decomposes into an uncorrelated product of densities $n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')$ — the result if electrons were distributed independently — plus a correction $\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ that measures all deviations from independent-particle behavior. Because the uncorrelated product already captures the long-range density structure, the correction $\Delta n$ is short-ranged, decaying to zero at large $|\mathbf{r} - \mathbf{r}'|$. This short-range character of electronic correlation is the physical reason that local and semi-local density functional approximations (LDA, GGA) work as well as they do.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻⁶ | **Joint pair probability** | Probability density for simultaneously finding electrons of spins $\sigma$ and $\sigma'$ at positions $\mathbf{r}$ and $\mathbf{r}'$. |
| $n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')$ | Product of densities | Bohr⁻⁶ | **Uncorrelated pair density** | What the joint probability would be if electrons were distributed independently. |
| $\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻⁶ | **Pair correlation function** | Measures all deviations from independent-particle behavior. Short-ranged. Negative for fermions (exchange) at short range. |

> **Connections Forward:** The pair correlation function determines the exchange-correlation energy (Entry 29) and its decomposition into exchange and correlation holes (Entry 16). The coupling constant integration (Entry 23) provides a route to the xc energy through the pair distribution.

## 14. Pair distribution function $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$

> [!question]
>
> (a) Write the normalized pair distribution function.
> (b) What value does $g$ take for uncorrelated particles?
> (c) What are the constraints on $g$ coming from the exchange hole?

> [!definition] Pair distribution function (Eq. 3.52)
>
> $$ g(\mathbf{r},\sigma;\mathbf{r}',\sigma') = \frac{n(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')} = 1 + \frac{\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')} $$

Pair distribution function, $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ — A dimensionless function measuring the ratio of the actual joint pair probability to the uncorrelated product of densities, so that $g = 1$ indicates uncorrelated behavior, $g < 1$ indicates that electrons avoid each other more than independent particles would (a "hole" in the pair distribution), and $g > 1$ indicates clustering. For same-spin fermions the Pauli principle enforces $g(\mathbf{r},\sigma;\mathbf{r},\sigma) = 0$ — two electrons of the same spin can never be found at the same point. At large separations $g \to 1$, since the correlation correction $\Delta n$ is short-ranged, making the deviation $g - 1$ a dimensionless, short-ranged measure of electronic correlation. In the Hartree-Fock approximation, $g - 1$ arises entirely from exchange and can be expressed directly in terms of the single-body density matrix.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Dimensionless two-point function | — | **Pair distribution function** | Ratio of actual to uncorrelated pair probability. Unity for independent particles; less than 1 where electrons avoid each other. |
| $g - 1$ | Dimensionless | — | **Correlation measure** | The deviation from uncorrelated behavior. Short-ranged. Vanishes at $\|\mathbf{r}-\mathbf{r}'\| \to \infty$. |

> **Connections Forward:** The pair distribution function is the central object for understanding exchange and correlation energies. It connects directly to the xc hole (Entry 16) and the coupling constant integration formula for $E_{\text{xc}}$ in DFT (Ch 8, §8.2).

## 15. Exchange hole for noninteracting fermions (§3.7.1)

> [!question]
>
> (a) Write the explicit expression for the exchange hole in the Hartree-Fock approximation.
> (b) What three properties must any exchange hole satisfy, and can you prove each from the formula?
> (c) Why does the exchange hole involve only same-spin electrons?

> [!definition] Exchange hole (Eq. 3.54)
>
> $$ \Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -\delta_{\sigma\sigma'}\left|\sum_i \psi_i^{\sigma*}(\mathbf{r})\,\psi_i^\sigma(\mathbf{r}')\right|^2 $$

Exchange hole, $\Delta n_x$ — The reduction in same-spin electron density at position $\mathbf{r}'$ in the vicinity of an electron of spin $\sigma$ at position $\mathbf{r}$, arising purely from the antisymmetry (Pauli exclusion) of the wavefunction. It equals minus the squared modulus of the off-diagonal density matrix, $-|\rho_\sigma(\mathbf{r},\mathbf{r}')|^2$, and the Kronecker delta $\delta_{\sigma\sigma'}$ restricts it to same-spin pairs only — opposite-spin electrons are unaffected because their spin functions are orthogonal. Three exact constraints govern the exchange hole: it is always non-positive ($\Delta n_x \leq 0$); at coincidence it exactly cancels the spin density ($\Delta n_x(\mathbf{r},\sigma;\mathbf{r},\sigma) = -n(\mathbf{r},\sigma)$, enforcing the Pauli exclusion principle); and it integrates over $\mathbf{r}'$ to exactly $-1$, accounting for the fact that the electron at $\mathbf{r}$ is missing from everywhere else.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Exchange hole** | Charge depletion around an electron due to Pauli exclusion. Always $\leq 0$; integrates to $-1$. |
| $\delta_{\sigma\sigma'}$ | Kronecker delta | — | **Spin selector** | Restricts exchange to same-spin electron pairs. |
| $\sum_i \psi_i^{\sigma*}(\mathbf{r})\psi_i^\sigma(\mathbf{r}')$ | Scalar | Bohr⁻³ | **Off-diagonal density matrix** | $\rho_\sigma(\mathbf{r},\mathbf{r}')$; the exchange hole is $-|\rho_\sigma|^2$. |

> **Connections Forward:** The exchange energy (Entry 29) is the Coulomb interaction of each electron with its exchange hole. The exchange hole is the starting point for understanding the exchange-correlation hole (Entry 16) and for constructing approximate density functionals (Ch 8–9). Self-interaction cancellation in Hartree-Fock is a direct consequence of the exchange hole integrating to exactly one electron.

## 16. Exchange-correlation hole $n_{\text{xc}}$

> [!question]
>
> (a) Write the decomposition of the pair correlation into exchange and correlation contributions.
> (b) What sum rules do the exchange hole and correlation hole individually satisfy?
> (c) Why is the exchange hole always negative, and what does this mean physically?

> [!definition] Exchange-correlation hole (Eq. 3.58)
>
> $$ \Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma') \equiv n_{\text{xc}}(\mathbf{r},\sigma;\mathbf{r}',\sigma') = n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') + n_c(\mathbf{r},\sigma;\mathbf{r}',\sigma') $$
>
> The exchange hole in the Hartree-Fock approximation:
>
> $$ \Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -\delta_{\sigma\sigma'} \left|\sum_i \psi_i^{\sigma*}(\mathbf{r})\,\psi_i^\sigma(\mathbf{r}')\right|^2 = -\delta_{\sigma\sigma'} |\rho_\sigma(\mathbf{r},\mathbf{r}')|^2 $$

Exchange-correlation hole, $n_{\text{xc}}$ — The total depletion of electron density around each electron due to both the Pauli exclusion principle and Coulomb correlation, defined as the full pair correlation $\Delta n$ decomposed into an exchange part $n_x$ and a correlation part $n_c$. The exchange hole, which involves only same-spin electrons and equals minus the squared modulus of the single-body density matrix, is always non-positive and can be computed exactly from the occupied orbitals. The correlation hole captures all remaining many-body effects beyond exchange. The two components satisfy distinct sum rules: the exchange hole integrates to exactly $-1$ (one electron is at $\mathbf{r}$ and therefore missing from everywhere else), the correlation hole integrates to zero (it merely redistributes the hole without changing its total weight), and together the full xc hole integrates to $-1$. These sum rules are satisfied exactly by the LDA, which is one reason it performs as well as it does.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n_{\text{xc}}$ | Two-point function | Bohr⁻³ | **Exchange-correlation hole** | Total depletion of electron density around each electron. Integrates to $-1$. |
| $n_x$ | Two-point function | Bohr⁻³ | **Exchange hole** | Depletion from the Pauli principle alone. Always $\leq 0$. Involves same-spin electrons only. Integrates to $-1$. |
| $n_c$ | Two-point function | Bohr⁻³ | **Correlation hole** | Additional depletion (or redistribution) beyond exchange. Integrates to zero — it rearranges but does not add charge to the hole. |
| $\rho_\sigma(\mathbf{r},\mathbf{r}')$ | Off-diagonal density matrix | Bohr⁻³ | **Single-body density matrix** | The off-diagonal part encodes quantum coherence and determines the exchange hole via $n_x = -\|\rho_\sigma\|^2$. |

> **Connections Forward:** The xc hole is the physical object that determines $E_{\text{xc}}$ (Ch 8, §8.2). The coupling constant averaged xc hole $\bar{n}_{\text{xc}}$ is the key quantity in the adiabatic connection formula. Understanding the xc hole gives physical intuition for why LDA works (it satisfies the sum rules) and when it fails.

---

# Theoretical Foundations

## 17. Total energy as expectation value


> [!question]
>
> (a) Write the total energy as an expectation value of the Hamiltonian.
> (b) Identify each of the four terms and explain how the external potential term simplifies to an integral over the density.
> (c) Why is $E_{II}$ just an additive constant for the electronic problem?


> [!theorem] Total energy (Eq. 3.9)
>
> $$ E = \langle\hat{H}\rangle = \langle\hat{T}\rangle + \langle\hat{V}_{\text{int}}\rangle + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} $$


Total energy as expectation value — The ground-state total energy expressed as the expectation value of the electronic Hamiltonian, decomposed into four physically distinct contributions: the electron kinetic energy $\langle\hat{T}\rangle$, the electron-electron interaction energy $\langle\hat{V}_{\text{int}}\rangle$, the electron-nuclear attraction $\int V_{\text{ext}}\,n\,d^3r$, and the ion-ion repulsion $E_{II}$. Of these, only the electron-nuclear term is an explicit, exact functional of the density alone — because $\hat{V}_{\text{ext}}$ is a single-body operator, its expectation value reduces to a simple integral of the external potential weighted by the density. The kinetic and electron-electron terms require the full many-body wavefunction or the pair distribution function, respectively, and cannot be written as known functionals of $n(\mathbf{r})$. This structural fact is the fundamental reason DFT requires the Kohn-Sham construction: auxiliary orbitals provide an indirect route to the kinetic energy that the density alone cannot supply.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\langle\hat{T}\rangle$ | Scalar | Hartree | **Kinetic energy** | Requires the full wavefunction. Cannot be written as an explicit, known functional of the density alone. |
| $\langle\hat{V}_{\text{int}}\rangle$ | Scalar | Hartree | **Electron-electron interaction energy** | Requires the pair distribution function. Decomposed into Hartree + xc contributions. |
| $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$ | Scalar | Hartree | **Electron-nuclear energy** | The only term that is an explicit, exact functional of the density. Simple classical coupling. |
| $E_{II}$ | Scalar (constant) | Hartree | **Ion-ion energy** | Classical Coulomb repulsion among nuclei. Fixed for given nuclear positions. |

> **Connections Forward:** This energy expression is reorganized in Entry 26 (classical Coulomb grouping) and Entry 27 (xc decomposition) for practical use. The Kohn-Sham total energy (Ch 7) is a rearrangement of these same four contributions.

## 18. Rayleigh-Ritz variational principle

> [!question]
>
> (a) Write the Rayleigh-Ritz functional and explain what "stationary" means.
> (b) How does the variational principle connect the minimum of the energy to the ground-state wavefunction?
> (c) How are excited states related to the variational principle?

> [!theorem] Rayleigh-Ritz variational principle (Eqs. 3.10–3.11)
>
> The energy functional
>
> $$ \Omega_{\text{RR}} = \langle\Psi|\,\hat{H} - E\,|\Psi\rangle $$
>
> is stationary ($\delta\Omega_{\text{RR}} = 0$) at every eigensolution $|\Psi_m\rangle$. Equivalently, minimizing the energy ratio $\langle\Psi|\hat{H}|\Psi\rangle / \langle\Psi|\Psi\rangle$ subject to the constraint $\langle\Psi|\Psi\rangle = 1$ via Lagrange multipliers:
>
> $$ \delta\left[\langle\Psi|\hat{H}|\Psi\rangle - E(\langle\Psi|\Psi\rangle - 1)\right] = 0 $$
>
> yields the time-independent Schrödinger equation $\hat{H}|\Psi\rangle = E|\Psi\rangle$.

Rayleigh-Ritz variational principle — The statement that the energy functional $\langle\Psi|\hat{H}|\Psi\rangle / \langle\Psi|\Psi\rangle$ is stationary (its first variation vanishes) at every eigenstate of $\hat{H}$, and that the ground state is the global minimum over all properly antisymmetric, normalized trial wavefunctions. Requiring stationarity subject to the normalization constraint $\langle\Psi|\Psi\rangle = 1$, enforced by the Lagrange multiplier $E$, yields the time-independent Schrödinger equation $\hat{H}|\Psi\rangle = E|\Psi\rangle$ as the Euler-Lagrange condition. The principle converts a differential equation into an optimization problem and guarantees that any approximate wavefunction yields an energy that is an upper bound to the true ground-state energy — a property that underlies all variational methods (Hartree-Fock, configuration interaction, variational Monte Carlo) and the Hohenberg-Kohn variational principle for the density in DFT.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\Omega_{\text{RR}}$ | Functional of $\Psi$ | Hartree | **Rayleigh-Ritz functional** | Stationary at every eigenstate of $\hat{H}$. |
| $E$ | Lagrange multiplier → eigenvalue | Hartree | **Energy eigenvalue** | Enforces normalization; equals the energy of the stationary state. |
| $\|\Psi\rangle$ | Trial wavefunction | — | **Variational wavefunction** | Any normalized, antisymmetric $N$-electron wavefunction. The one that minimizes $\langle\hat{H}\rangle$ is the ground state. |

> **Connections Forward:** The variational principle is the logical backbone of the force theorem (Entry 20), the Hohenberg-Kohn theorems (Ch 6), and the Kohn-Sham construction (Ch 7). The Hartree-Fock equations (Entry 33) arise from restricting the variational search to single determinants.

## 19. Time-independent Schrödinger equation

> [!question]
>
> (a) Write the time-independent many-body Schrödinger equation.
> (b) How is it derived from the variational principle?
> (c) Why is direct solution infeasible for many-electron systems?

> [!theorem] Time-independent Schrödinger equation (Eq. 3.13)
>
> $$ \hat{H}|\Psi\rangle = E|\Psi\rangle $$

Time-independent Schrödinger equation — The eigenvalue equation $\hat{H}|\Psi\rangle = E|\Psi\rangle$ stating that the Hamiltonian acting on an eigenstate reproduces the same state scaled by its energy eigenvalue $E$, derivable as the Euler-Lagrange condition of the Rayleigh-Ritz variational principle. It is the central equation of non-relativistic quantum mechanics. Direct solution is infeasible for many-electron systems because the wavefunction $|\Psi\rangle$ lives in $3N$-dimensional configuration space: even a modest system of $\sim$200 electrons would require representing a function of $\sim$600 variables, an exponentially large problem far beyond any conceivable computer. This exponential wall is the fundamental reason approximate methods — DFT, Hartree-Fock, quantum Monte Carlo — are necessary rather than direct solution.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{H}$ | Operator on $N$-electron Hilbert space | Hartree | **Many-body Hamiltonian** | The full electronic Hamiltonian (Entry 7). |
| $\|\Psi\rangle$ | Eigenstate in $N$-electron Hilbert space | Bohr⁻$^{3N/2}$ | **Many-body eigenstate** | Antisymmetric wavefunction solving the eigenvalue equation. The ground state has the lowest $E$. |
| $E$ | Scalar | Hartree | **Energy eigenvalue** | The total electronic energy of the eigenstate. |

> **Connections Forward:** All of electronic structure theory is an attempt to solve this equation approximately. DFT (Ch 6–9) replaces it with single-particle equations. Hartree-Fock (Entry 33) restricts the solution space to single determinants. Quantum Monte Carlo samples the wavefunction stochastically.

## 20. Force (Hellmann-Feynman) theorem

> [!question]
>
> (a) State the force theorem: what is the force on nucleus $I$ in terms of the density?
> (b) Why do the middle two terms in the derivative of the energy (involving $\partial\Psi/\partial\mathbf{R}_I$) vanish?
> (c) Under what conditions does the theorem fail, and what corrections are needed?
> (d) Why is the force a purely electrostatic result — why doesn't the kinetic or exchange-correlation energy appear?

> [!theorem] Force (Hellmann-Feynman) theorem (Eqs. 3.17–3.19)
>
> $$ \mathbf{F}_I = -\frac{\partial E}{\partial \mathbf{R}_I} = -\int d^3r\, n(\mathbf{r})\, \frac{\partial V_{\text{ext}}(\mathbf{r})}{\partial \mathbf{R}_I} - \frac{\partial E_{II}}{\partial \mathbf{R}_I} $$
>
> More generally, for any parameter $\lambda$ in the Hamiltonian:
>
> $$ -\frac{\partial E}{\partial \lambda} = -\langle\Psi|\frac{\partial \hat{H}}{\partial \lambda}|\Psi\rangle $$

Force (Hellmann-Feynman) theorem — The statement that the force on nucleus $I$ is given entirely by classical electrostatics: the integral of the electron density weighted by the gradient of the nuclear potential, plus the Coulomb force from all other nuclei. The kinetic energy, exchange, and correlation do not appear as separate terms — they influence the density $n(\mathbf{r})$, and through it the force, but contribute no explicit additional terms. More generally, the derivative of the energy with respect to any parameter $\lambda$ in the Hamiltonian equals the expectation value $\langle\Psi|\partial\hat{H}/\partial\lambda|\Psi\rangle$. The theorem relies on the variational principle: at an eigenstate the energy is stationary with respect to variations of $\Psi$, so the terms involving $\partial\Psi/\partial\mathbf{R}_I$ vanish. If the wavefunction is not fully variational — for instance, with an incomplete, position-dependent basis set — these terms do not vanish and Pulay corrections must be added.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\mathbf{F}_I$ | Vector | Hartree/Bohr (or eV/Å) | **Force on nucleus $I$** | The negative gradient of the total energy with respect to nuclear position. Drives structural relaxation. |
| $-\int n(\mathbf{r})\,\partial V_{\text{ext}}/\partial\mathbf{R}_I\,d^3r$ | Vector | Hartree/Bohr | **Electron-nuclear force** | Force exerted by the electron cloud on nucleus $I$. Purely electrostatic. |
| $-\partial E_{II}/\partial\mathbf{R}_I$ | Vector | Hartree/Bohr | **Ion-ion force** | Coulomb repulsion from other nuclei. Classical. |

### Conditions

The theorem is exact when $|\Psi\rangle$ is an exact eigenstate (or, more generally, when the energy is stationary with respect to all variational parameters). When the basis is incomplete and depends on nuclear positions, Pulay corrections must be added. For nonlocal potentials (pseudopotentials), the force cannot be expressed solely in terms of the density but retains the form $-\langle\Psi|\partial\hat{H}/\partial\mathbf{R}_I|\Psi\rangle$.

> **Connections Forward:** Forces are computed in every structural relaxation. In VASP with a plane-wave basis, the basis is independent of nuclear positions so there are no Pulay corrections for internal coordinates — but Pulay *stress* corrections are needed (Ch 13). The force theorem also underlies the coupling constant integration (Entry 23).

## 21. Stress (generalized virial) theorem


> [!question]
>
> (a) Write the stress tensor as a derivative of the energy with respect to strain.
> (b) What is the physical meaning of a scaling of space — what happens to the wavefunction and nuclear positions?
> (c) Why do the wavefunction relaxation terms vanish, as in the force theorem?


> [!theorem] Stress theorem (Eqs. 3.21, 3.23)
>
> $$ \sigma_{\alpha\beta} = -\frac{1}{\Omega}\frac{\partial E}{\partial \epsilon_{\alpha\beta}} $$
>
> where strain is a scaling of space: $\mathbf{r}_\alpha \to (\delta_{\alpha\beta} + \epsilon_{\alpha\beta})\mathbf{r}_\beta$. The explicit expression is:
>
> $$ \sigma_{\alpha\beta} = -\langle\Psi|\sum_k \frac{\hbar^2}{2m_k}\nabla_{k\alpha}\nabla_{k\beta} - \frac{1}{2}\sum_{k \neq k'}\frac{(\mathbf{x}_{kk'})_\alpha (\mathbf{x}_{kk'})_\beta}{x_{kk'}}\left(\frac{d}{dx_{kk'}}\hat{V}\right)|\Psi\rangle $$


Stress (generalized virial) theorem — The statement that the stress tensor component $\sigma_{\alpha\beta}$ equals minus the derivative of the total energy with respect to strain $\epsilon_{\alpha\beta}$, divided by the system volume $\Omega$, where strain is defined as a uniform scaling of all coordinates (electron positions, nuclear positions, and cell vectors) via $\mathbf{r}_\alpha \to (\delta_{\alpha\beta} + \epsilon_{\alpha\beta})\mathbf{r}_\beta$. As with the force theorem, the energy is variational at equilibrium, so the only contribution to the energy derivative comes from the explicit strain dependence of the Hamiltonian — wavefunction relaxation terms vanish. The explicit expression involves a kinetic energy tensor $\nabla_{k\alpha}\nabla_{k\beta}$ and an interaction tensor built from pair separations, and is the generalization of the force theorem from point displacements to continuous deformations of space.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\sigma_{\alpha\beta}$ | Rank-2 tensor | Hartree/Bohr³ (or GPa) | **Stress tensor** | Force per unit area in direction $\alpha$ on a surface with normal $\beta$. Drives cell relaxation. |
| $\epsilon_{\alpha\beta}$ | Rank-2 tensor (symmetric) | — | **Strain tensor** | Dimensionless measure of deformation. Defined by the scaling $\mathbf{r}_\alpha \to (\delta_{\alpha\beta} + \epsilon_{\alpha\beta})\mathbf{r}_\beta$. |
| $\Omega$ | Scalar | Bohr³ (or ų) | **System volume** | Volume of the simulation cell. |

> **Connections Forward:** The stress tensor is needed for cell optimization in VASP (ISIF ≥ 3). Pulay stress — the spurious stress from an incomplete plane-wave basis — is a major practical concern (Ch 13). Setting ENCUT sufficiently high or using the correction from Appendix G is essential.

## 22. Virial theorem for pressure

> [!question]
>
> (a) Write the virial theorem relating pressure, kinetic energy, and potential energy.
> (b) Under what conditions is this theorem exact?
> (c) How does the factor of 3 arise?

> [!theorem] Virial theorem (Eq. 3.24)
>
> $$ 3P\Omega = 2E_{\text{kinetic}} + E_{\text{potential}} $$

Virial theorem for pressure — An exact constraint relating the pressure, total kinetic energy, and total potential energy of a system with Coulomb interactions at equilibrium: $3P\Omega = 2E_{\text{kinetic}} + E_{\text{potential}}$. It follows from the stress theorem by taking the isotropic trace ($P = -\frac{1}{3}\text{Tr}\,\sigma_{\alpha\beta}$), with the factor of 3 arising from the three spatial dimensions. At zero pressure the theorem yields $E_{\text{potential}} = -2E_{\text{kinetic}}$ and $E_{\text{total}} = -E_{\text{kinetic}}$, meaning the total energy of a bound Coulomb system at equilibrium is always negative and equals minus the kinetic energy. The theorem is exact and general, holding for any system in equilibrium — classical or quantum, at any temperature — provided all interactions are Coulombic, and serves as a powerful consistency check on calculations.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $P$ | Scalar | Hartree/Bohr³ (or GPa) | **Pressure** | Isotropic part of the stress tensor: $P = -\frac{1}{3}\text{Tr}\,\sigma_{\alpha\beta}$. |
| $E_{\text{kinetic}}$ | Scalar | Hartree | **Total kinetic energy** | Kinetic energy of all particles (electrons and nuclei). |
| $E_{\text{potential}}$ | Scalar | Hartree | **Total potential energy** | All Coulomb interactions: electron-electron, electron-nuclear, and nuclear-nuclear. |

> **Connections Forward:** The virial theorem constrains DFT functionals — exact functionals must satisfy it. It provides a consistency check for calculations and is used in the derivation of the exact conditions on the xc functional (Ch 8).

## 23. Generalized force theorem and coupling constant integration

> [!question]
>
> (a) Write the generalized force theorem for an arbitrary parameter $\lambda$ in the Hamiltonian.
> (b) Write the coupling constant integration formula for the energy difference.
> (c) When the coupling constant $\lambda$ scales the electron-electron interaction from 0 to 1, what are the initial and final states?
> (d) Why is the coupling constant integration useful for constructing density functionals even though it requires the wavefunction at unphysical intermediate coupling strengths?

> [!theorem] Coupling constant integration (Eqs. 3.25–3.27)
>
> $$ \frac{\partial E}{\partial \lambda} = \langle\Psi_\lambda|\frac{\partial \hat{H}}{\partial \lambda}|\Psi_\lambda\rangle $$
>
> $$ \Delta E = \int_{\lambda_1}^{\lambda_2} d\lambda\, \langle\Psi_\lambda|\frac{\partial \hat{H}}{\partial \lambda}|\Psi_\lambda\rangle $$
>
> For scaling the interaction $e^2 \to e^2\lambda$:
>
> $$ \Delta E = \int_0^1 d\lambda\, \langle\Psi_\lambda|\hat{V}_{\text{int}}|\Psi_\lambda\rangle $$

Generalized force theorem and coupling constant integration — A generalization of the Hellmann-Feynman theorem stating that the derivative of the energy with respect to any parameter $\lambda$ in the Hamiltonian equals the expectation value $\langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$, evaluated with the eigenstate at that parameter value. Integrating this derivative over $\lambda$ yields a finite energy difference — an "adiabatic connection" — between two states of the system. The most important application scales the electron-electron interaction from zero ($\lambda = 0$, a non-interacting system) to full strength ($\lambda = 1$, the physical system), giving $\Delta E = \int_0^1 d\lambda\,\langle\Psi_\lambda|\hat{V}_{\text{int}}|\Psi_\lambda\rangle$. This requires the wavefunction $\Psi_\lambda$ at every intermediate, unphysical coupling strength, but the formula nevertheless provides the conceptual foundation for the adiabatic connection formula for the exchange-correlation energy in DFT and for the construction of hybrid functionals, which mix exact exchange ($\lambda = 0$) with DFT correlation ($\lambda = 1$).

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\lambda$ | Scalar parameter | — | **Coupling constant** | Scales the electron-electron interaction from 0 (noninteracting) to 1 (fully interacting). |
| $\Psi_\lambda$ | $N$-electron eigenstate | — | **Adiabatically connected wavefunction** | The ground-state wavefunction at intermediate coupling strength $\lambda$. Unphysical for $0 < \lambda < 1$. |
| $\partial\hat{H}/\partial\lambda$ | Operator | Hartree | **Hamiltonian derivative** | For coupling constant integration with $e^2\lambda$, this is $\hat{V}_{\text{int}}$. |
| $\Delta E$ | Scalar | Hartree | **Energy difference from integration** | The total energy change in going from coupling $\lambda_1$ to $\lambda_2$. |

> **Connections Forward:** The coupling constant integration is a key ingredient in the construction of the adiabatic connection formula for $E_{\text{xc}}$ (Ch 8, §8.2; Ch 9, §9.7). It provides the conceptual foundation for hybrid functionals, which mix exact exchange ($\lambda = 0$) with DFT correlation ($\lambda = 1$).

## 24. Free energy and the density matrix (§3.5)

> [!question]
>
> (a) Write the free energy in terms of the density matrix.
> (b) What is the equilibrium density matrix that minimizes the free energy?
> (c) What does the entropy term $\frac{1}{\beta}\text{Tr}\,\hat{\rho}\ln\hat{\rho}$ represent physically?

> [!equation] Free energy (Eq. 3.28)
>
> $$ F = \text{Tr}\,\hat{\rho}\left(\hat{H} + \frac{1}{\beta}\ln\hat{\rho}\right) $$
>
> Minimized by:
>
> $$ \hat{\rho} = \frac{1}{Z}e^{-\beta\hat{H}}, \qquad Z = \text{Tr}\,e^{-\beta\hat{H}} = e^{-\beta F} $$

Free energy and the density matrix — The Helmholtz free energy $F = U - TS$ expressed as a functional of the many-body density matrix $\hat{\rho}$, consisting of two competing contributions: the internal energy $\text{Tr}\,\hat{\rho}\hat{H}$, which favors low-energy states, and minus the temperature times the entropy $\frac{1}{\beta}\text{Tr}\,\hat{\rho}\ln\hat{\rho}$, which favors spreading occupation probability over many states. At low temperature the energy term dominates and the system collapses to the ground state; at high temperature the entropy term dominates and all states become equally populated. Minimizing $F$ with respect to $\hat{\rho}$ yields the equilibrium Boltzmann density matrix $\hat{\rho} = e^{-\beta\hat{H}}/Z$, which assigns occupation probability proportional to $e^{-\beta E_i}$ to each eigenstate and reduces to the ground-state projector $|\Psi_0\rangle\langle\Psi_0|$ at $T = 0$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $F$ | Scalar | Hartree | **Helmholtz free energy** | $F = U - TS$. The thermodynamic potential minimized at fixed $T$, $V$, and $N$. |
| $\hat{\rho}$ | Operator | — | **Density matrix** | Encodes the statistical mixture of quantum states. Positive definite; $\text{Tr}\,\hat{\rho} = 1$. |
| $Z$ | Scalar | — | **Partition function** | Normalization constant. $Z = e^{-\beta F}$ connects statistical mechanics to thermodynamics. |
| $\beta = 1/(k_BT)$ | Scalar | Hartree⁻¹ | **Inverse temperature** | Controls the competition between energy and entropy. |

> **Connections Forward:** The Mermin functional (Ch 6, §6.5.1) extends DFT to finite temperature using the density matrix. In VASP, Fermi-Dirac smearing effectively works at finite electronic temperature; the free energy $F$ (rather than $E$) should be used for metallic systems.

## 25. Koopmans' theorem

> [!question]
>
> (a) State Koopmans' theorem precisely.
> (b) What two effects does the theorem neglect that cause Hartree-Fock eigenvalues to be inaccurate for excitation energies?
> (c) Why do Hartree-Fock band gaps greatly overestimate experimental values?

> [!theorem] Koopmans' theorem (§3.6.3)
>
> The eigenvalue $\varepsilon_i^\sigma$ of a filled (empty) orbital in the Hartree-Fock equation is equal to the change in total energy when an electron is removed from (added to) that orbital, keeping all other orbitals unchanged.

Koopmans' theorem — The statement that, within the Hartree-Fock approximation, the eigenvalue $\varepsilon_i^\sigma$ of an occupied (unoccupied) orbital equals the energy required to remove (add) an electron from (to) that orbital, provided all other orbitals are held fixed. It is exact within this frozen-orbital approximation and reflects the fact that the exchange term cancels the spurious self-interaction in the Hartree potential for occupied states. Two effects are neglected: orbital relaxation (the rearrangement of all remaining orbitals upon ionization, which lowers the ion energy) and changes in correlation energy. These partially cancel, but the net result is that Hartree-Fock eigenvalue differences — in particular band gaps — systematically overestimate experimental values, often by a factor of two or more for semiconductors.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Semiconductors and insulators | Band gaps overestimated by factor of ~2 | Missing orbital relaxation and correlation |
| Metals | Qualitatively wrong bandwidth, density of states | Exchange is long-ranged and state-dependent |
| Strongly correlated systems (e.g., CeO₂) | Fails to capture Mott physics | Missing correlation is the dominant energy scale |

> **Connections Forward:** Koopmans' theorem motivates the $\Delta$SCF method (Entry 34). In DFT, the Kohn-Sham eigenvalues do not obey Koopmans' theorem, but Janak's theorem (Ch 7) provides an analog. The discrepancy between HF and DFT gaps is central to understanding the band gap problem.

---

# Energy Expressions & Functionals

## 26. Classical Coulomb energy grouping $E^{\text{CC}}$

> [!question]
>
> (a) Write the classical Coulomb energy in terms of the Hartree energy, electron-nuclear, and ion-ion terms.
> (b) Why must the terms be grouped as a neutral combination?
> (c) How does this grouping ensure that all individual contributions are finite in an extended system?

> [!equation] Classical Coulomb energy grouping (Eq. 3.14)
>
> $$ E^{\text{CC}} = E_{\text{Hartree}} + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} $$

Classical Coulomb energy grouping, $E^{\text{CC}}$ — The total classical electrostatic energy of the combined electron-plus-nuclear charge distribution, formed by grouping three terms: the Hartree self-repulsion of the electron cloud, the electron-nuclear attraction $\int V_{\text{ext}}\,n\,d^3r$, and the ion-ion repulsion $E_{II}$. Each term individually diverges in an extended (periodic) system — the Hartree energy of an infinite charged system is infinite, as is the electron-nuclear attraction — but their sum is the electrostatic energy of a neutral system (positive nuclei plus negative electrons), which is finite and well-defined. This neutral grouping is essential for practical computation: in a periodic crystal, the three terms are evaluated together via Ewald summation, which cancels the divergences analytically and produces a convergent result. The individual terms are meaningless in an infinite system and must never be computed separately.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E^{\text{CC}}$ | Scalar | Hartree | **Classical Coulomb energy** | The total electrostatic energy of a neutral system: electron-electron + electron-nuclear + nuclear-nuclear. Finite for neutral systems. |
| $E_{\text{Hartree}}$ | Functional of $n$ | Hartree | **Hartree energy** | Classical electron self-repulsion (Entry 9). Diverges alone in extended systems. |
| $\int V_{\text{ext}}\,n\,d^3r$ | Functional of $n$ | Hartree | **Electron-nuclear attraction** | The coupling between the electron cloud and the nuclear potential. Diverges alone. |
| $E_{II}$ | Scalar | Hartree | **Ion-ion repulsion** | Classical nuclear-nuclear Coulomb energy. Diverges alone. |

> **Connections Forward:** This grouping appears in VASP output as the sum of Hartree, electron-nuclear, and Ewald energies. In the Kohn-Sham total energy (Ch 7), $E^{\text{CC}}$ is one of the well-defined energy blocks. Ewald summation (Appendix F) evaluates it in reciprocal space.

## 27. Total energy decomposition with exchange-correlation

> [!question]
>
> (a) Write the total energy decomposed into kinetic, exchange-correlation, and classical Coulomb contributions.
> (b) What is the physical interpretation of the middle term $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$?
> (c) Why is this difference short-ranged?

> [!equation] Total energy decomposition (Eq. 3.16)
>
> $$ E = \langle\hat{T}\rangle + \left(\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}\right) + E^{\text{CC}} $$

Total energy decomposition with exchange-correlation — A rearrangement of the total energy into three individually well-defined, finite contributions: the interacting kinetic energy $\langle\hat{T}\rangle$, the potential part of the exchange-correlation energy $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$, and the classical Coulomb energy $E^{\text{CC}}$ of the neutral system. The middle term is the difference between the true quantum-mechanical electron-electron repulsion and the classical mean-field (Hartree) approximation to it, representing the energy lowering from exchange (Pauli avoidance) and correlation (Coulomb avoidance beyond mean field). This difference is short-ranged: the long-range $1/r$ tails cancel between $\langle\hat{V}_{\text{int}}\rangle$ and $E_{\text{Hartree}}$ because both share the same average density at large separations, leaving only short-range exchange and correlation corrections. This short-range character is the fundamental physical reason that local and semi-local density functionals (LDA, GGA) can approximate $E_{\text{xc}}$ successfully.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ | Scalar | Hartree | **Potential part of $E_{\text{xc}}$** | Difference between quantum and classical electron-electron energy. Short-ranged. Always negative (exchange lowers the energy). |
| $E^{\text{CC}}$ | Scalar | Hartree | **Classical Coulomb energy** | Neutral grouping from Entry 26. Well-defined and long-ranged. |

> **Connections Forward:** This decomposition is the prototype for the Kohn-Sham energy expression (Ch 7). The insight that xc is short-ranged is the physical justification for LDA (Ch 8) and GGA. It also explains why the xc hole picture (Entry 16) works — the relevant physics is local.

## 28. Hartree-Fock total energy

> [!question]
>
> (a) Write the Hartree-Fock total energy in terms of orbital integrals.
> (b) Identify the direct (Hartree) and exchange contributions.
> (c) Why is the self-interaction included in the direct term and then canceled by exchange?

> [!equation] Hartree-Fock total energy (Eq. 3.44)
>
> $$\begin{aligned} \langle\Phi|\hat{H}|\Phi\rangle = &\sum_{i,\sigma} \int d\mathbf{r}\, \psi_i^{\sigma*}(\mathbf{r})\left[-\frac{1}{2}\nabla^2 + V_{\text{ext}}(\mathbf{r})\right]\psi_i^\sigma(\mathbf{r}) + E_{II} \\ &+ \frac{1}{2}\sum_{i,j,\sigma_i,\sigma_j} \int d\mathbf{r}\,d\mathbf{r}'\, \frac{|\psi_i^{\sigma_i}(\mathbf{r})|^2 |\psi_j^{\sigma_j}(\mathbf{r}')|^2}{|\mathbf{r}-\mathbf{r}'|} \\ &- \frac{1}{2}\sum_{i,j,\sigma} \int d\mathbf{r}\,d\mathbf{r}'\, \frac{\psi_i^{\sigma*}(\mathbf{r})\psi_j^{\sigma*}(\mathbf{r}')\psi_j^\sigma(\mathbf{r})\psi_i^\sigma(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|} \end{aligned}$$

Hartree-Fock total energy — The total energy of a system described by a single Slater determinant, expressed as a sum of four contributions: single-particle terms (kinetic energy plus external potential for each occupied orbital), the ion-ion repulsion $E_{II}$, the direct (Hartree) Coulomb repulsion between all pairs of orbital charge densities $|\psi_i|^2$ and $|\psi_j|^2$ including the self-term $i = j$, and the exchange interaction summed over same-spin orbital pairs only (opposite-spin exchange vanishes by spin orthogonality). The exchange term involves swapping the coordinates of orbitals $i$ and $j$ in the Coulomb integral. Including the self-term $i = j$ in the direct sum allows it to be written compactly as the Hartree energy of the total density $n(\mathbf{r})$; the corresponding $i = j$ self-term in the exchange then exactly cancels this spurious self-interaction, ensuring that each electron does not repel itself. This exact self-interaction cancellation is a defining feature of Hartree-Fock theory and is only approximately achieved by standard density functional approximations.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| First line (single-body terms) | Sum over orbitals | Hartree | **Kinetic + external + $E_{II}$** | Orbital kinetic energies and electron-nuclear attraction. Same as in an independent-particle calculation. |
| Second line (direct term) | Double sum over orbitals | Hartree | **Direct (Hartree) energy** | Classical Coulomb repulsion between orbital charge densities. Includes spurious self-interaction. |
| Third line (exchange term) | Double sum over same-spin orbitals | Hartree | **Exchange energy** | Energy lowering from Pauli exclusion. Same-spin only. Cancels self-interaction. Always negative. |

> **Connections Forward:** The Hartree-Fock energy is the reference for defining the correlation energy ($E_c = E_{\text{exact}} - E_{\text{HF}}$). The DFT definition of $E_c$ differs slightly — orbitals are constrained to give the exact density rather than minimize $E_{\text{HF}}$ (see Ch 7). The exchange term here becomes the "exact exchange" mixed into hybrid functionals (PBE0, HSE).

## 29. Exchange energy from the exchange hole

> [!question]
>
> (a) Write the exchange energy in terms of the exchange hole.
> (b) Why can the exchange energy be interpreted as the interaction of each electron with a positive hole?
> (c) For a one-electron system, show that the exchange energy exactly cancels the Hartree energy.

> [!equation] Exchange energy (Eq. 3.57)
>
> $$ E_x = \left[\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}(n)\right]_{\text{HFA}} = \frac{1}{2}\sum_{\sigma\sigma'}\int d^3r \int d^3r'\, \frac{\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{|\mathbf{r}-\mathbf{r}'|} $$

Exchange energy from the exchange hole, $E_x$ — The energy lowering due to the Pauli exclusion principle, equal to the Coulomb interaction between each electron and its exchange hole, and equivalent to the difference $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ evaluated in the Hartree-Fock approximation. Because the exchange hole $\Delta n_x$ is always non-positive (a depletion of same-spin electron density), and the Coulomb kernel $1/|\mathbf{r} - \mathbf{r}'|$ is positive, the exchange energy is always negative — it reduces the electron-electron repulsion below the mean-field Hartree value. For a one-electron system the exchange hole equals minus the electron density itself, and the exchange energy exactly cancels the Hartree energy, removing the spurious self-interaction. This cancellation is exact in Hartree-Fock but only approximate in DFT with standard functionals, making self-interaction error a major source of error for localized states such as $d$ and $f$ electrons.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E_x$ | Scalar | Hartree | **Exchange energy** | Energy lowering from Pauli exclusion. Always negative. Equals $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ in the Hartree-Fock approximation. |
| $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Exchange hole** | Depletion of same-spin electron density around each electron. Always $\leq 0$. Integrates to $-1$. |
| $1/\|\mathbf{r}-\mathbf{r}'\|$ | Coulomb kernel | Bohr⁻¹ | **Pair Coulomb weight** | Weights the exchange hole by inverse separation; determines the energy contribution of the hole. |

> **Connections Forward:** The exchange energy is the starting point for understanding $E_{\text{xc}}$ in DFT. The LDA exchange (Dirac, Ch 5) approximates it locally. The exact exchange is the $\lambda = 0$ limit in the adiabatic connection (Ch 9, §9.7) and appears explicitly in hybrid functionals (PBE0: 25% exact exchange; HSE: screened exact exchange).

## 30. Independent-particle energy at finite temperature

> [!question]
>
> (a) Write the total energy for non-interacting particles at finite temperature.
> (b) How does the expectation value of any single-body operator simplify for independent particles?
> (c) What is the physical meaning of the Fermi-Dirac weights?

> [!equation] Independent-particle energy and expectation values (Eqs. 3.37, 3.39)
>
> $$ \langle\hat{O}\rangle = \sum_{i,\sigma} f_i^\sigma \langle\psi_i^\sigma|\hat{O}|\psi_i^\sigma\rangle $$
>
> $$ E(T) = \sum_{i,\sigma} f_i^\sigma \varepsilon_i^\sigma $$

Independent-particle energy at finite temperature — The expectation value of any single-body operator for a system of non-interacting particles, reduced from a many-body trace to a simple weighted sum over single-particle orbitals: $\langle\hat{O}\rangle = \sum_{i,\sigma} f_i^\sigma \langle\psi_i^\sigma|\hat{O}|\psi_i^\sigma\rangle$, where the Fermi-Dirac occupation numbers $f_i^\sigma$ give the probability that each state is occupied at thermal equilibrium. Specializing to the Hamiltonian gives the total energy as the occupation-weighted sum of eigenvalues, $E(T) = \sum_{i,\sigma} f_i^\sigma \varepsilon_i^\sigma$. At $T = 0$ the occupations are step functions (all states below the chemical potential $\mu$ filled, all above empty); at finite $T$ the step softens over a range $\sim k_BT$, allowing fractional occupation of states near $\mu$. In Kohn-Sham DFT, this occupation-weighted eigenvalue sum is the band energy, not the total energy — it double-counts the Hartree energy and includes the exchange-correlation potential contribution, requiring correction terms.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\sum_{i,\sigma} f_i^\sigma \varepsilon_i^\sigma$ | Weighted sum | Hartree | **Band energy** | Sum of eigenvalues weighted by occupation. Equals the total energy only for noninteracting particles — in DFT it is the band energy, not the total energy. |
| $f_i^\sigma$ | Occupation weight | — | **Fermi-Dirac weight** | Thermal occupation probability for state $(i,\sigma)$. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalue** | Energy of orbital $i$ with spin $\sigma$. |

> **Connections Forward:** In Kohn-Sham DFT (Ch 7), the band energy $\sum f_i \varepsilon_i$ is *not* the total energy — it double-counts the Hartree energy and includes the xc potential contribution. The total energy must be corrected (see the Kohn-Sham energy expression). In VASP, the smearing scheme is set by `ISMEAR` and `SIGMA`.

---

# Approximations & Their Failures

## 31. Born-Oppenheimer (adiabatic) approximation

> [!question]
>
> (a) State the Born-Oppenheimer approximation and the physical argument for its validity.
> (b) In what sense are the nuclear positions "parameters" rather than dynamical variables?
> (c) Name two physical phenomena where the Born-Oppenheimer approximation breaks down.

> [!approximation] Born-Oppenheimer approximation (§3.1)
>
> The nuclear kinetic energy is neglected, and nuclear positions $\{\mathbf{R}_I\}$ enter the electronic Hamiltonian as fixed parameters:
>
> $$ \hat{H}_{\text{full}} = \hat{H}_{\text{elec}}(\{\mathbf{R}_I\}) + \hat{T}_{\text{nuclei}} \quad \xrightarrow{\text{BO}} \quad \hat{H} = \hat{H}_{\text{elec}}(\{\mathbf{R}_I\}) $$
>
> Justified by $m_e / M_I \ll 1$ (the electron-to-nuclear mass ratio).

Born-Oppenheimer (adiabatic) approximation — The approximation that the nuclear kinetic energy can be neglected in the electronic problem, so that nuclear positions $\{\mathbf{R}_I\}$ enter the electronic Hamiltonian as fixed parameters rather than quantum-mechanical degrees of freedom, justified by the small electron-to-nuclear mass ratio $m_e/M_I \ll 1$. The electronic Schrödinger equation is solved for each fixed nuclear configuration, producing an energy surface $E(\{\mathbf{R}_I\})$ on which the nuclei subsequently move classically or semiclassically. The approximation is excellent for most ground-state properties — crystal structures, elastic constants, phonon frequencies — and begins to fail when electronic states come close in energy and nuclear motion can induce transitions between them, as in electron-phonon coupling (electrical resistance, polaron formation, superconductivity) and at conical intersections in molecules.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Metals near phase transitions | Wrong transport properties | Strong electron-phonon coupling mixes electronic states |
| Polarons in oxides | Wrong charge carrier mass | Lattice distortion strongly coupled to electronic state |
| Superconductors | Cannot predict $T_c$ from BO surface alone | Cooper pairing requires explicit electron-phonon interaction |
| Conical intersections (molecules) | Breakdown of adiabatic energy surface | Degenerate electronic states at nuclear configuration |

### Practical Consequences

For your CeO₂ calculations, the Born-Oppenheimer approximation is excellent — you compute the electronic ground state for each set of nuclear positions during structural relaxation, and generate Born-Oppenheimer molecular dynamics (BOMD) trajectories for MLIP training data. Phonons can be computed from the curvature of the energy surface via finite differences or DFPT.

> **Connections Forward:** Every DFT calculation assumes Born-Oppenheimer. Ab initio molecular dynamics (AIMD) in VASP computes forces from the BO energy surface at each time step. Electron-phonon coupling (perturbation theory on top of BO) is needed for transport properties and superconductivity.

## 32. Noninteracting (Hartree-like) electron approximation

> [!question]
>
> (a) Write the effective single-particle Schrödinger equation.
> (b) How is the ground state constructed from the single-particle solutions?
> (c) What is the relationship between this approximation and the Kohn-Sham equations?

> [!approximation] Noninteracting electron approximation (Eq. 3.36)
>
> $$ \hat{H}_{\text{eff}}\psi_i^\sigma(\mathbf{r}) = \left[-\frac{\hbar^2}{2m_e}\nabla^2 + V_{\text{eff}}^\sigma(\mathbf{r})\right]\psi_i^\sigma(\mathbf{r}) = \varepsilon_i^\sigma \psi_i^\sigma(\mathbf{r}) $$

Noninteracting (Hartree-like) electron approximation — The replacement of the intractable many-body problem with $N$ independent single-particle Schrödinger equations, each electron moving in a local effective potential $V_{\text{eff}}^\sigma(\mathbf{r})$ that incorporates the average effect of all other electrons. The ground state is constructed by filling the lowest $N$ eigenstates according to the Pauli principle, with no need to build an explicit antisymmetric many-body wavefunction. The content of the approximation depends entirely on what is included in $V_{\text{eff}}^\sigma$: in the original Hartree approach it was the nuclear potential plus an average Coulomb repulsion from the other electrons; in the Kohn-Sham formulation of DFT, $V_{\text{eff}}^\sigma = V_{\text{ext}} + V_{\text{Hartree}} + V_{\text{xc}}^\sigma$ is chosen so that the resulting single-particle density exactly reproduces the true interacting ground-state density, folding all exchange and correlation effects into the potential. This is the equation solved in every Kohn-Sham DFT calculation.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{H}_{\text{eff}}$ | Single-particle operator | Hartree | **Effective Hamiltonian** | Single-electron Hamiltonian with all many-body effects folded into $V_{\text{eff}}$. |
| $V_{\text{eff}}^\sigma(\mathbf{r})$ | Scalar field (spin-dependent) | Hartree | **Effective potential** | The local, multiplicative potential acting on each electron. Includes nuclear attraction plus an approximation to electron-electron effects. |
| $\psi_i^\sigma(\mathbf{r})$ | Single-particle orbital | Bohr⁻$^{3/2}$ | **Eigenstates** | Solutions of the effective Schrödinger equation. Orthogonal by construction. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalues** | Energies of the orbitals. Their physical meaning depends on what $V_{\text{eff}}$ represents. |

### Practical Consequences

This is the equation solved in every Kohn-Sham DFT calculation. The entire machinery of electronic structure — plane-wave basis sets (Ch 12–13), pseudopotentials (Ch 11), k-point sampling — is devoted to solving this equation efficiently and accurately.

> **Connections Forward:** The Kohn-Sham equations (Ch 7) are exactly this equation with a specific choice of $V_{\text{eff}}$. All the computational methods in Chapters 11–17 are methods for solving it. In VASP, the SCF cycle iteratively updates $V_{\text{eff}}$ until self-consistency.

## 33. Hartree-Fock approximation

> [!question]
>
> (a) Write the Hartree-Fock equations including the nonlocal exchange term.
> (b) Why is the exchange operator nonlocal — what does that mean for the equation?
> (c) Why does the Hartree-Fock effective Hamiltonian depend on the state $i$?
> (d) For which system classes does Hartree-Fock perform well, and where does it fail badly?

> [!approximation] Hartree-Fock approximation (Eqs. 3.45–3.48)
>
> $$\begin{aligned} &\left[-\frac{1}{2}\nabla^2 + V_{\text{ext}}(\mathbf{r}) + V_{\text{Hartree}}(\mathbf{r})\right]\psi_i^\sigma(\mathbf{r}) \\ &\quad - \sum_j \int d\mathbf{r}'\, \psi_j^{\sigma*}(\mathbf{r}')\psi_i^\sigma(\mathbf{r}')\frac{1}{|\mathbf{r}-\mathbf{r}'|}\psi_j^\sigma(\mathbf{r}) = \varepsilon_i^\sigma \psi_i^\sigma(\mathbf{r}) \end{aligned}$$
>
> Equivalently: $\hat{H}_{\text{eff}}^{i}\psi_i^\sigma = \varepsilon_i^\sigma\psi_i^\sigma$ with $\hat{V}_{\text{eff}}^{i,\sigma} = V_{\text{ext}} + V_{\text{Hartree}} + \hat{V}_x^{i,\sigma}$

Hartree-Fock approximation — The variational approximation in which the many-body wavefunction is restricted to a single Slater determinant, leading to a set of self-consistent single-particle equations that include the external potential, the Hartree potential, and a nonlocal, state-dependent exchange operator. The exchange operator acts on orbital $\psi_i^\sigma(\mathbf{r})$ through an integral over all occupied same-spin orbitals $\psi_j^\sigma$, involving the "exchange charge density" $\psi_j^{\sigma*}(\mathbf{r}')\psi_i^\sigma(\mathbf{r}')$ weighted by the Coulomb kernel — this nonlocality and orbital dependence distinguish it fundamentally from a local potential and make Hartree-Fock computationally more expensive, scaling as $N_{\text{basis}}^4$ in general. Hartree-Fock captures exchange exactly and cancels the self-interaction error present in the Hartree term, but neglects all correlation effects by construction, leading to systematic overestimation of band gaps, failure for metals (where the long-ranged exchange produces an unphysical zero in the density of states at $E_F$), and qualitative failure for strongly correlated systems.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Metals | No metallic screening; unphysical density of states at $E_F$ | Exchange is long-ranged in HF; the logarithmic divergence in $dE/dk$ at $k_F$ gives zero DOS at the Fermi level |
| Semiconductors/insulators | Band gaps overestimated by ~2× | Neglect of correlation and orbital relaxation (Koopmans' theorem limitations) |
| Strongly correlated oxides | Cannot describe Mott insulating state | Missing correlation is the dominant energy scale for localized electrons |
| Van der Waals systems | No binding | Dispersion is a pure correlation effect, absent in HF |

### Practical Consequences

Hartree-Fock is rarely used as a standalone method for solids. Its main roles in modern electronic structure are: (1) defining the correlation energy as $E_c = E_{\text{exact}} - E_{\text{HF}}$, (2) providing the exact exchange used in hybrid functionals (PBE0, HSE), and (3) serving as the starting point for post-HF methods in quantum chemistry (MP2, CCSD(T)).

> **Connections Forward:** The exchange term here is the "exact exchange" ($E_{\text{xx}}$) mixed into hybrid functionals (Ch 9). HSE screens the long-range part to cure the metallic-DOS problem. The Hartree-Fock exchange operator reappears in the generalized Kohn-Sham scheme.

## 34. $\Delta$SCF method

> [!question]
>
> (a) What is the $\Delta$SCF method and how does it improve upon Koopmans' theorem?
> (b) Why does it work better for finite systems than for extended systems?
> (c) What is the relationship to total energy differences in DFT?

> [!approximation] $\Delta$SCF method (§3.6.4)
>
> Compute addition and removal energies as explicit total energy differences:
>
> $$ E_{\text{removal}} = E(N-1) - E(N), \qquad E_{\text{addition}} = E(N) - E(N+1) $$
>
> where each total energy is computed self-consistently with relaxed orbitals.

$\Delta$SCF method — The approach of computing electron addition and removal energies as explicit total energy differences between self-consistent calculations with $N$ and $N \pm 1$ electrons, rather than approximating them by single-particle eigenvalues as in Koopmans' theorem. By allowing all orbitals to relax in each separate calculation, the method captures orbital relaxation (the rearrangement of remaining electrons in response to adding or removing one) and, within DFT, whatever correlation the chosen functional provides. The method works well for finite systems (atoms, molecules) where the added or removed electron produces a localized, well-defined energy change, but becomes problematic for extended systems: adding one electron to an infinite solid is an infinitesimal perturbation, so the energy difference per electron vanishes and the method reduces to computing the Fermi level. Practical application to solids requires supercell calculations with careful finite-size corrections.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Extended solids (bulk) | Energy difference goes to zero as $1/N_{\text{atoms}}$ | One electron in an infinite system is an infinitesimal perturbation |
| Systems with strong charge transfer | Requires multiple SCF solutions | May converge to wrong state if initial guess is poor |

> **Connections Forward:** The $\Delta$SCF approach is used in DFT for computing ionization energies and electron affinities of molecules (Ch 10, §10.6). For solids, constrained DFT or the quasiparticle approach (GW) is more appropriate. Your CeO₂ calculations use total energy differences between oxidation states, which is conceptually related.

---
