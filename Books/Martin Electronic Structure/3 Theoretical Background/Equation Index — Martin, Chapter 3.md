# Equation Index — Martin, Chapter 3: Theoretical Background

Electronic Structure Vault


## Master Reference

### Definitions & Building Blocks (1–9)

| # | Name | Section |
|---|---|---|
| 1 | Electronic Hamiltonian (compact form) | §3.1 |
| 2 | Electron density $n(\mathbf{r})$ | §3.1.1 |
| 3 | Hartree energy $E_{\text{Hartree}}$ | §3.2 |
| 4 | Slater determinant | §3.6.2 |
| 5 | Single-body density matrix | §3.6.1 |
| 6 | Fermi-Dirac distribution | §3.6.1 |
| 7 | Joint pair probability $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | §3.7 |
| 8 | Pair distribution function $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | §3.7 |
| 9 | Exchange-correlation hole $n_{\text{xc}}$ | §3.7.2 |

### Theoretical Foundations (10–17)

| # | Name | Section |
|---|---|---|
| 10 | Total energy as expectation value | §3.1.1 |
| 11 | Rayleigh-Ritz variational principle | §3.1.1 |
| 12 | Time-independent Schrödinger equation | §3.1.1 |
| 13 | Force (Hellmann-Feynman) theorem | §3.3.1 |
| 14 | Stress (generalized virial) theorem | §3.3.2 |
| 15 | Virial theorem for pressure | §3.3.2 |
| 16 | Generalized force theorem and coupling constant integration | §3.4 |
| 17 | Koopmans' theorem | §3.6.3 |

### Energy Expressions & Functionals (18–22)

| # | Name | Section |
|---|---|---|
| 18 | Classical Coulomb energy grouping $E^{\text{CC}}$ | §3.2 |
| 19 | Total energy decomposition with exchange-correlation | §3.2 |
| 20 | Hartree-Fock total energy | §3.6.2 |
| 21 | Exchange energy from the exchange hole | §3.7.1 |
| 22 | Independent-particle energy at finite temperature | §3.6.1 |

### Approximations & Their Failures (23–26)

| # | Name | Section |
|---|---|---|
| 23 | Born-Oppenheimer (adiabatic) approximation | §3.1 |
| 24 | Noninteracting (Hartree-like) electron approximation | §3.6.1 |
| 25 | Hartree-Fock approximation | §3.6.2 |
| 26 | $\Delta$SCF method | §3.6.4 |

### Supplementary Entries (S1–S3)

| # | Name | Section |
|---|---|---|
| S1 | Free energy and the density matrix | §3.5 |
| S2 | Full Hamiltonian for electrons and nuclei | §3.1 |
| S3 | Exchange hole for noninteracting fermions | §3.7.1 |



# Definitions & Building Blocks

## 1. Electronic Hamiltonian (compact form)



> [!question]
>
> (a) Write the electronic Hamiltonian in compact notation, identifying each of the four terms.
> (b) What physical approximation has already been made in going from the full Hamiltonian Eq. (3.1) to the electronic Hamiltonian Eq. (3.2)?
> (c) Which terms are "universal" (the same for all electron systems) and which are system-specific?



> [!definition] Electronic Hamiltonian (Eq. 3.2)
>
> $$ \hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II} $$
>
> with, in Hartree atomic units ($\hbar = m_e = e = 4\pi/\epsilon_0 = 1$):
>
> $$ \hat{T} = \sum_i -\frac{1}{2}\nabla_i^2 \qquad \hat{V}_{\text{ext}} = \sum_{i,I} V_I(|\mathbf{r}_i - \mathbf{R}_I|) \qquad \hat{V}_{\text{int}} = \frac{1}{2}\sum_{i \neq j} \frac{1}{|\mathbf{r}_i - \mathbf{r}_j|} $$


The electronic hamiltonian is a decomposition of the total electronic energy into four physically distinct contributions. The first term $\hat{T}$ is the kinetic energy of all electrons: the Laplacian $\nabla_i^2$ measures how sharply the wavefunction curves around electron $i$, and the prefactor $-\frac{1}{2}$ (in Hartree units) sets the quantum-mechanical kinetic energy scale. The second term $\hat{V}_{\text{ext}}$ is the "external" potential — the attraction between electrons and nuclei. It is the only system-specific part of the Hamiltonian: it is what makes CeO$_2$ different from Si or H$_2$. The third term $\hat{V}_{\text{int}}$ is the electron-electron Coulomb repulsion, summed over all distinct pairs. The $\frac{1}{2}$ corrects for double-counting since the sum over $i \neq j$ counts each pair $(i,j)$ and $(j,i)$ separately. The fourth term $E_{II}$ is the classical ion-ion interaction — a number, not an operator — which is essential for total energies but plays no role in determining the electronic wavefunction.

The Born-Oppenheimer approximation has already been invoked to reach this form: the nuclear kinetic energy term $-\sum_I \hbar^2/(2M_I) \nabla_I^2$ from the full Hamiltonian Eq. (3.1) has been dropped, and the nuclear positions $\{\mathbf{R}_I\}$ enter only as fixed parameters. This is justified because $m_e/M_I \ll 1$ — the nuclei are thousands of times heavier than the electrons and move on a much slower timescale.


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



## 2. Electron density $n(\mathbf{r})$

> [!question]
>
> (a) Write the definition of the electron density in terms of the many-body wavefunction.
> (b) Why does the prefactor $N$ appear?
> (c) Write the density for independent particles in terms of single-particle orbitals.

> [!definition] Electron density (Eq. 3.8)
>
> $$ n(\mathbf{r}) = N \frac{\int d^3r_2 \cdots d^3r_N \sum_{\sigma_1} |\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2}{\int d^3r_1 \, d^3r_2 \cdots d^3r_N \, |\Psi(\mathbf{r}_1, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2} $$
>
> For independent particles with occupation numbers $f_i^\sigma$:
>
> $$ n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2 $$

Read the many-body definition from the inside out. Start with $|\Psi|^2$, the joint probability density for finding all $N$ electrons at positions $(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)$. The integration $\int d^3r_2 \cdots d^3r_N$ then traces out all coordinates except the one at $\mathbf{r}$ — it says "I don't care where the other $N-1$ electrons are." The prefactor $N$ accounts for indistinguishability: since any of the $N$ electrons could be the one at $\mathbf{r}$, and the wavefunction is antisymmetric, each electron contributes equally, so you multiply by $N$. The denominator normalizes.

The independent-particle expression $n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2$ is far simpler: you add up the probability densities of each occupied orbital, weighted by the occupation number $f_i^\sigma$ (which is 0 or 1 at zero temperature, and given by the Fermi-Dirac distribution at finite temperature). This is the expression used in all Kohn-Sham calculations.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r})$ | Scalar field: $\mathbb{R}^3 \to \mathbb{R}^+$ | Å⁻³ (or Bohr⁻³) | **Electron density** | Total density of electrons at point $\mathbf{r}$; integrates to $N$. |
| $\|\Psi\|^2$ | Probability density in $3N$-space | Bohr⁻$^{3N}$ | **Many-body probability density** | Joint probability per unit volume of finding all electrons at their respective positions. |
| $\int d^3r_2 \cdots d^3r_N$ | Integration over $(N-1)$ positions | Bohr$^{3(N-1)}$ | **Marginal integration** | Traces out all electron coordinates except the one at $\mathbf{r}$. |
| $\psi_i^\sigma(\mathbf{r})$ | Single-particle orbital | Bohr⁻$^{3/2}$ | **Kohn-Sham / Hartree orbital** | Eigenstate of the effective single-particle Hamiltonian for spin $\sigma$. |
| $f_i^\sigma$ | Scalar, $0 \leq f_i^\sigma \leq 1$ | — | **Occupation number** | Probability of state $(i,\sigma)$ being occupied; equals 0 or 1 at $T=0$. |

> **Connections Forward:** The density is the central variable of DFT (Ch 6–9). The Hohenberg-Kohn theorem proves it determines all ground-state properties. In VASP, the CHGCAR file contains $n(\mathbf{r})$ on a real-space grid.

## 3. Hartree energy $E_{\text{Hartree}}$

> [!question]
>
> (a) Write the Hartree energy in terms of the electron density.
> (b) What physics does it capture, and what does it miss?
> (c) Why does it include a spurious self-interaction, and how is this corrected in Hartree-Fock?


> [!definition] Hartree energy (Eq. 3.15)
>
> $$ E_{\text{Hartree}} = \frac{1}{2} \int d^3r \, d^3r' \, \frac{n(\mathbf{r})\,n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} $$

Read this double integral from the inside out. The product $n(\mathbf{r})\,n(\mathbf{r}')$ is the uncorrelated pair density: it treats the charge at $\mathbf{r}$ and $\mathbf{r}'$ as independent, classical charge distributions. The Coulomb kernel $1/|\mathbf{r} - \mathbf{r}'|$ weights each pair by the inverse of their separation — nearby charge pairs contribute large repulsion, distant pairs contribute little. The double integration sums over all pairs of points, and the prefactor $\frac{1}{2}$ corrects for double-counting.

The Hartree energy captures the dominant, long-range, mean-field part of the electron-electron repulsion. It misses exchange (same-spin avoidance from the Pauli principle), correlation (additional avoidance from Coulomb repulsion), and includes a spurious self-interaction — each electron repels itself through the mean field because the integral does not exclude the case where $\mathbf{r}$ and $\mathbf{r}'$ belong to the same electron. In the Hartree-Fock approximation, the exchange term exactly cancels this self-interaction for each orbital.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r})\,n(\mathbf{r}')$ | Scalar function of two positions | Bohr⁻⁶ | **Uncorrelated pair density** | Treats charge at two points as independent — the classical, mean-field approximation to the true pair density. |
| $1/\|\mathbf{r} - \mathbf{r}'\|$ | Coulomb kernel | Bohr⁻¹ | **Pair Coulomb weight** | Weights each pair of charges by the inverse of their separation. |
| $\frac{1}{2}\int d^3r\,d^3r'$ | Double spatial integration | — | **Pair summation with double-counting correction** | Sums the Coulomb repulsion over all pairs; $\frac{1}{2}$ prevents counting each pair twice. |
| $E_{\text{Hartree}}$ | Functional: $n(\mathbf{r}) \mapsto \mathbb{R}$ | Hartree | **Hartree energy** | Classical electrostatic self-energy of the electron charge distribution. Includes spurious self-interaction. |

> **Connections Forward:** The Hartree energy appears in the Kohn-Sham total energy (Ch 7) and in the classical Coulomb grouping (Entry 18). Understanding self-interaction error is essential for understanding why DFT+U is needed for Ce 4f electrons.



## 4. Slater determinant


> [!question]
>
> (a) Write the Slater determinant for $N$ electrons.
> (b) Why does the determinant form automatically enforce antisymmetry?
> (c) What is the relationship between the Slater determinant and the exclusion principle?


> [!definition] Slater determinant (Eq. 3.43)
>
> $$ \Phi = \frac{1}{(N!)^{1/2}} \begin{vmatrix} \phi_1(\mathbf{r}_1,\sigma_1) & \phi_1(\mathbf{r}_2,\sigma_2) & \cdots \\ \phi_2(\mathbf{r}_1,\sigma_1) & \phi_2(\mathbf{r}_2,\sigma_2) & \cdots \\ \vdots & \vdots & \ddots \end{vmatrix} $$


Read this as: "construct the many-body wavefunction by arranging $N$ spin-orbitals $\phi_i$ into a determinant, one orbital per row, one electron coordinate per column." The determinant automatically enforces antisymmetry because swapping two columns (exchanging two electrons) flips the sign. If two rows are identical (two electrons in the same spin-orbital), the determinant vanishes — this is the Pauli exclusion principle expressed algebraically. The prefactor $1/\sqrt{N!}$ normalizes the wavefunction when the single-particle orbitals are orthonormal.

The Slater determinant is the simplest possible antisymmetric wavefunction and the starting point for both the Hartree-Fock approximation (which minimizes the energy over all single determinants) and the Kohn-Sham construction (which uses a determinant of auxiliary orbitals to build the density). All correlation beyond exchange is, by definition, what a single determinant cannot capture.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\Phi$ | $N$-electron wavefunction | Bohr⁻$^{3N/2}$ | **Slater determinant** | The simplest antisymmetric many-body wavefunction built from $N$ single-particle orbitals. |
| $\phi_i(\mathbf{r}_j, \sigma_j)$ | Single-particle spin-orbital | Bohr⁻$^{3/2}$ | **Spin-orbital** | Product of a spatial orbital $\psi_i^\sigma(\mathbf{r}_j)$ and a spin function $\alpha_i(\sigma_j)$. Rows of the determinant. |
| $1/\sqrt{N!}$ | Normalization constant | — | **Normalization prefactor** | Ensures $\langle\Phi|\Phi\rangle = 1$ when spin-orbitals are orthonormal. $N!$ is the number of permutations of $N$ electrons. |

> **Connections Forward:** Hartree-Fock (Entry 25) minimizes the energy over single determinants. The Kohn-Sham construction (Ch 7) uses a Slater determinant of auxiliary orbitals to produce the exact density. Correlation (Entry 9) is everything a single determinant misses.



## 5. Single-body density matrix

> [!question]
>
> (a) Write the single-body density matrix operator and its position-spin representation.
> (b) How is the electron density obtained from the density matrix?
> (c) What additional information does the off-diagonal part $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ carry beyond the density?

> [!definition] Single-body density matrix (Eqs. 3.40–3.42)
>
> $$ \hat{\rho} = \sum_i |\psi_i^\sigma\rangle\, f_i^\sigma \,\langle\psi_i^\sigma| $$
>
> In position-spin representation:
>
> $$ \rho(\mathbf{r},\sigma;\mathbf{r}',\sigma') = \delta_{\sigma,\sigma'} \sum_i \psi_i^{\sigma*}(\mathbf{r})\, f_i^\sigma \,\psi_i^\sigma(\mathbf{r}') $$
>
> The density is the diagonal part:
>
> $$ n^\sigma(\mathbf{r}) = \rho(\mathbf{r},\sigma;\mathbf{r},\sigma) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2 $$

Read the operator form as a weighted sum of projection operators: each term $|\psi_i^\sigma\rangle f_i^\sigma \langle\psi_i^\sigma|$ says "orbital $i$ with spin $\sigma$ is occupied with probability $f_i^\sigma$." The density matrix packages all the single-particle occupation information into one object. Its diagonal part in position space gives the density $n^\sigma(\mathbf{r})$ — "how many electrons of spin $\sigma$ are at point $\mathbf{r}$." Its off-diagonal part $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma)$ with $\mathbf{r} \neq \mathbf{r}'$ encodes quantum coherence: the amplitude for finding an electron at $\mathbf{r}$ that was at $\mathbf{r}'$. This off-diagonal part determines the kinetic energy and the exchange energy — quantities the density alone cannot give.

Any expectation value of a single-body operator is $\langle\hat{O}\rangle = \text{Tr}\,\hat{\rho}\hat{O} = \sum_{i,\sigma} f_i^\sigma \langle\psi_i^\sigma|\hat{O}|\psi_i^\sigma\rangle$, which reduces the many-body trace to a weighted sum over single-particle matrix elements.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{\rho}$ | Operator on single-particle Hilbert space | — | **Single-body density matrix operator** | Encodes all occupation information for independent particles. Positive semi-definite, trace equals $N$. |
| $\rho(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Density matrix in position-spin basis** | Diagonal in spin for non-spin-orbit systems. Diagonal part ($\mathbf{r}=\mathbf{r}'$) is the density; off-diagonal part encodes coherence. |
| $f_i^\sigma$ | Scalar, $0 \leq f_i^\sigma \leq 1$ | — | **Occupation number** | Weight for orbital $i$ with spin $\sigma$. Given by the Fermi-Dirac distribution at finite temperature. |

> **Connections Forward:** The density matrix appears in the exchange hole (Entry 21), in the force theorem applied to nonlocal potentials (Ch 13), and in the formulation of the Kohn-Sham equations (Ch 7). In VASP, the density matrix for correlated orbitals is the object that the DFT+U correction acts on.

## 6. Fermi-Dirac distribution

> [!question]
>
> (a) Write the Fermi-Dirac distribution.
> (b) What is the physical meaning of the chemical potential $\mu$?
> (c) What does the distribution reduce to at $T = 0$?

> [!definition] Fermi-Dirac distribution (Eq. 3.38)
>
> $$ f_i^\sigma = \frac{1}{e^{\beta(\varepsilon_i^\sigma - \mu)} + 1} $$

Read this as the probability of finding an electron in single-particle state $(i,\sigma)$ at thermal equilibrium. The exponent $\beta(\varepsilon_i^\sigma - \mu)$ compares the state's energy $\varepsilon_i^\sigma$ to the chemical potential $\mu$, measured in units of thermal energy $k_BT = 1/\beta$. For states well below $\mu$ the exponent is large and negative, so $f \approx 1$ — the state is fully occupied. For states well above $\mu$ the exponent is large and positive, so $f \approx 0$ — the state is empty. The transition from occupied to empty occurs over an energy window of order $k_BT$ around $\mu$. At $T = 0$ the distribution becomes a step function: $f = 1$ for $\varepsilon < \mu$ and $f = 0$ for $\varepsilon > \mu$.

The chemical potential $\mu$ adjusts itself so that the total occupation $\sum_{i,\sigma} f_i^\sigma = N$. At zero temperature it equals the Fermi energy — the energy of the highest occupied state.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $f_i^\sigma$ | Scalar, $[0,1]$ | — | **Fermi-Dirac occupation** | Probability of state $(i,\sigma)$ being occupied at thermal equilibrium. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalue** | Energy of orbital $i$ with spin $\sigma$ from the effective Schrödinger equation. |
| $\mu$ | Scalar | Hartree (or eV) | **Chemical potential** | Energy at which occupation is $\frac{1}{2}$. Equals the Fermi energy at $T=0$. Self-consistently determined by $\sum f_i^\sigma = N$. |
| $\beta = 1/(k_BT)$ | Scalar | Hartree⁻¹ | **Inverse temperature** | Sets the energy scale of thermal smearing. $\beta \to \infty$ at $T=0$. |

> **Connections Forward:** The Fermi-Dirac distribution is used in all finite-temperature DFT calculations. In VASP, `ISMEAR` and `SIGMA` control the smearing scheme — Fermi-Dirac smearing (`ISMEAR = -1`) directly implements this distribution. The E-fermi in OUTCAR is $\mu$.

## 7. Joint pair probability $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$

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

Read the first expression as: "integrate out all electron coordinates except two, and count the probability of simultaneously finding an electron of spin $\sigma$ at $\mathbf{r}$ and an electron of spin $\sigma'$ at $\mathbf{r}'$." The prefactor $N(N-1)$ accounts for the $N$ choices for the first electron and $N-1$ for the second (distinct electrons only).

The decomposition in the second equation separates the pair probability into an uncorrelated product $n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')$ — what you would get if electrons were distributed independently — plus a correction $\Delta n$ that measures all correlations. For uncorrelated particles $\Delta n = 0$. The uncorrelated product already captures all long-range structure (since the density itself has long-range order in a crystal), so $\Delta n$ is short-ranged — it decays to zero at large $|\mathbf{r} - \mathbf{r}'|$. This short-range character of correlation is the physical reason that local and semi-local approximations (LDA, GGA) work as well as they do.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻⁶ | **Joint pair probability** | Probability density for simultaneously finding electrons of spins $\sigma$ and $\sigma'$ at positions $\mathbf{r}$ and $\mathbf{r}'$. |
| $n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')$ | Product of densities | Bohr⁻⁶ | **Uncorrelated pair density** | What the joint probability would be if electrons were distributed independently. |
| $\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻⁶ | **Pair correlation function** | Measures all deviations from independent-particle behavior. Short-ranged. Negative for fermions (exchange) at short range. |

> **Connections Forward:** The pair correlation function determines the exchange-correlation energy (Entry 21) and its decomposition into exchange and correlation holes (Entry 9). The coupling constant integration (Entry 16) provides a route to the xc energy through the pair distribution.

## 8. Pair distribution function $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$

> [!question]
>
> (a) Write the normalized pair distribution function.
> (b) What value does $g$ take for uncorrelated particles?
> (c) What are the constraints on $g$ coming from the exchange hole?

> [!definition] Pair distribution function (Eq. 3.52)
>
> $$ g(\mathbf{r},\sigma;\mathbf{r}',\sigma') = \frac{n(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')} = 1 + \frac{\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')} $$

Read this as the ratio of the actual pair probability to the uncorrelated pair probability. If $g = 1$, the electrons are uncorrelated at that pair of points. If $g < 1$, the electrons avoid each other more than independent particles would — there is a "hole" in the pair distribution. If $g > 1$, the electrons cluster more than expected. For fermions, the Pauli principle forces $g(\mathbf{r},\sigma;\mathbf{r},\sigma) = 0$ for same-spin electrons — two electrons of the same spin can never occupy the same point.

At large separations $|\mathbf{r} - \mathbf{r}'| \to \infty$, $g \to 1$ because the correlation $\Delta n$ is short-ranged. The deviation $g - 1$ is thus a dimensionless measure of correlation that is nonzero only at short range. For independent fermions (the Hartree-Fock approximation), $g - 1$ is entirely due to exchange and can be expressed in terms of the density matrix (Eq. 3.56).

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Dimensionless two-point function | — | **Pair distribution function** | Ratio of actual to uncorrelated pair probability. Unity for independent particles; less than 1 where electrons avoid each other. |
| $g - 1$ | Dimensionless | — | **Correlation measure** | The deviation from uncorrelated behavior. Short-ranged. Vanishes at $\|\mathbf{r}-\mathbf{r}'\| \to \infty$. |

> **Connections Forward:** The pair distribution function is the central object for understanding exchange and correlation energies. It connects directly to the xc hole (Entry 9) and the coupling constant integration formula for $E_{\text{xc}}$ in DFT (Ch 8, §8.2).

## 9. Exchange-correlation hole $n_{\text{xc}}$

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

Read the first equation as: "the total pair correlation splits into an exchange part $n_x$ (from the Pauli principle) and a correlation part $n_c$ (from the remaining many-body effects)." The exchange hole, given in the second equation, involves only same-spin electrons (the $\delta_{\sigma\sigma'}$) and is always negative — it represents the depletion of electron density around each electron due to the exclusion principle. It equals minus the square of the single-body density matrix, which means it can be computed exactly from the occupied orbitals.

The sum rules are physically transparent: the exchange hole integrates to exactly $-1$ electron (because if one electron is at $\mathbf{r}$, that same electron is missing from everywhere else). The correlation hole integrates to zero (it merely redistributes the hole density without changing its total weight). Together, the xc hole integrates to $-1$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n_{\text{xc}}$ | Two-point function | Bohr⁻³ | **Exchange-correlation hole** | Total depletion of electron density around each electron. Integrates to $-1$. |
| $n_x$ | Two-point function | Bohr⁻³ | **Exchange hole** | Depletion from the Pauli principle alone. Always $\leq 0$. Involves same-spin electrons only. Integrates to $-1$. |
| $n_c$ | Two-point function | Bohr⁻³ | **Correlation hole** | Additional depletion (or redistribution) beyond exchange. Integrates to zero — it rearranges but does not add charge to the hole. |
| $\rho_\sigma(\mathbf{r},\mathbf{r}')$ | Off-diagonal density matrix | Bohr⁻³ | **Single-body density matrix** | The off-diagonal part encodes quantum coherence and determines the exchange hole via $n_x = -\|\rho_\sigma\|^2$. |

> **Connections Forward:** The xc hole is the physical object that determines $E_{\text{xc}}$ (Ch 8, §8.2). The coupling constant averaged xc hole $\bar{n}_{\text{xc}}$ is the key quantity in the adiabatic connection formula. Understanding the xc hole gives physical intuition for why LDA works (it satisfies the sum rules) and when it fails.

---

# Theoretical Foundations

## 10. Total energy as expectation value


> [!question]
>
> (a) Write the total energy as an expectation value of the Hamiltonian.
> (b) Identify each of the four terms and explain how the external potential term simplifies to an integral over the density.
> (c) Why is $E_{II}$ just an additive constant for the electronic problem?


> [!theorem] Total energy (Eq. 3.9)
>
> $$ E = \langle\hat{H}\rangle = \langle\hat{T}\rangle + \langle\hat{V}_{\text{int}}\rangle + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} $$


Read the four terms left to right. The first, $\langle\hat{T}\rangle$, is the total kinetic energy of all electrons — it requires the full many-body wavefunction and cannot be expressed as a simple functional of the density. The second, $\langle\hat{V}_{\text{int}}\rangle$, is the expectation value of the electron-electron Coulomb repulsion — again requiring the pair distribution function, not just the density. The third term is a dramatic simplification: because $\hat{V}_{\text{ext}}$ is a single-body operator (it acts on one electron at a time), its expectation value reduces to a simple integral of $V_{\text{ext}}$ weighted by the density. This is the term that couples the electrons to the nuclei — it is just the classical electrostatic energy of the electron charge cloud in the nuclear potential. The fourth term $E_{II}$ is a constant for fixed nuclear positions.

The key structural insight is that the only term computable from the density alone is the electron-nuclear interaction. The kinetic and electron-electron terms require more information (the wavefunction or the pair distribution function). This is why DFT needs the Kohn-Sham construction: it provides an indirect route to the kinetic energy through auxiliary orbitals.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\langle\hat{T}\rangle$ | Scalar | Hartree | **Kinetic energy** | Requires the full wavefunction. Cannot be written as an explicit, known functional of the density alone. |
| $\langle\hat{V}_{\text{int}}\rangle$ | Scalar | Hartree | **Electron-electron interaction energy** | Requires the pair distribution function. Decomposed into Hartree + xc contributions. |
| $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$ | Scalar | Hartree | **Electron-nuclear energy** | The only term that is an explicit, exact functional of the density. Simple classical coupling. |
| $E_{II}$ | Scalar (constant) | Hartree | **Ion-ion energy** | Classical Coulomb repulsion among nuclei. Fixed for given nuclear positions. |

> **Connections Forward:** This energy expression is reorganized in Entry 18 (classical Coulomb grouping) and Entry 19 (xc decomposition) for practical use. The Kohn-Sham total energy (Ch 7) is a rearrangement of these same four contributions.

## 11. Rayleigh-Ritz variational principle

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

Read this as: "the energy is extremal — not just at a minimum, but at any eigenstate." The ground state is the global minimum of the energy functional over all properly antisymmetric, normalized trial wavefunctions. Excited states are saddle points — minima in some directions in the space of wavefunctions, maxima in others. The Lagrange multiplier $E$ enforcing normalization turns out to be the energy eigenvalue itself.

The power of the variational principle is that it converts a differential equation (the Schrödinger equation) into an optimization problem. Any approximate wavefunction gives an energy that is an upper bound to the true ground-state energy — this is the basis for all variational methods (Hartree-Fock, CI, VMC) and underlies the Hohenberg-Kohn variational principle for the density in DFT.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\Omega_{\text{RR}}$ | Functional of $\Psi$ | Hartree | **Rayleigh-Ritz functional** | Stationary at every eigenstate of $\hat{H}$. |
| $E$ | Lagrange multiplier → eigenvalue | Hartree | **Energy eigenvalue** | Enforces normalization; equals the energy of the stationary state. |
| $\|\Psi\rangle$ | Trial wavefunction | — | **Variational wavefunction** | Any normalized, antisymmetric $N$-electron wavefunction. The one that minimizes $\langle\hat{H}\rangle$ is the ground state. |

> **Connections Forward:** The variational principle is the logical backbone of the force theorem (Entry 13), the Hohenberg-Kohn theorems (Ch 6), and the Kohn-Sham construction (Ch 7). The Hartree-Fock equations (Entry 25) arise from restricting the variational search to single determinants.

## 12. Time-independent Schrödinger equation

> [!question]
>
> (a) Write the time-independent many-body Schrödinger equation.
> (b) How is it derived from the variational principle?
> (c) Why is direct solution infeasible for many-electron systems?

> [!theorem] Time-independent Schrödinger equation (Eq. 3.13)
>
> $$ \hat{H}|\Psi\rangle = E|\Psi\rangle $$

Read this as: "the Hamiltonian acting on an eigenstate reproduces the same state scaled by the energy." This is the central equation of quantum mechanics. It follows from the variational principle (Entry 11) by requiring that $\langle\delta\Psi|\hat{H} - E|\Psi\rangle = 0$ for all possible variations $\langle\delta\Psi|$.

Direct solution is infeasible because $|\Psi\rangle$ lives in $3N$-dimensional configuration space. For a CeO$_2$ unit cell with $\sim$200 electrons, you would need to represent a function of $\sim$600 variables. If you used just 10 grid points per dimension, the wavefunction would require $10^{600}$ numbers — far beyond any conceivable computer. This exponential wall is the fundamental reason we need DFT, Hartree-Fock, and other approximate methods rather than solving the Schrödinger equation directly.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{H}$ | Operator on $N$-electron Hilbert space | Hartree | **Many-body Hamiltonian** | The full electronic Hamiltonian (Entry 1). |
| $\|\Psi\rangle$ | Eigenstate in $N$-electron Hilbert space | Bohr⁻$^{3N/2}$ | **Many-body eigenstate** | Antisymmetric wavefunction solving the eigenvalue equation. The ground state has the lowest $E$. |
| $E$ | Scalar | Hartree | **Energy eigenvalue** | The total electronic energy of the eigenstate. |

> **Connections Forward:** All of electronic structure theory is an attempt to solve this equation approximately. DFT (Ch 6–9) replaces it with single-particle equations. Hartree-Fock (Entry 25) restricts the solution space to single determinants. Quantum Monte Carlo samples the wavefunction stochastically.

## 13. Force (Hellmann-Feynman) theorem

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

Read the force expression as: "the force on nucleus $I$ is the nuclear charge times the total electric field at the nucleus, computed from the electron density and the other nuclei." The first term is the force from the electron cloud — the integral of the density weighted by the gradient of the nuclear potential. The second term is the force from the other nuclei. Remarkably, the kinetic energy, exchange, and correlation do not appear explicitly — they affect the density $n(\mathbf{r})$, and through it the force, but they do not appear as separate terms.

The theorem relies on the variational principle: at the exact ground state (or any eigenstate), the energy is extremal with respect to variations of $\Psi$, so the terms $\langle\partial\Psi/\partial\mathbf{R}_I|\hat{H}|\Psi\rangle$ and $\langle\Psi|\hat{H}|\partial\Psi/\partial\mathbf{R}_I\rangle$ vanish. If the wavefunction is not an exact eigenstate — for instance, if the basis set is incomplete — these terms do not vanish and Pulay corrections must be added.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\mathbf{F}_I$ | Vector | Hartree/Bohr (or eV/Å) | **Force on nucleus $I$** | The negative gradient of the total energy with respect to nuclear position. Drives structural relaxation. |
| $-\int n(\mathbf{r})\,\partial V_{\text{ext}}/\partial\mathbf{R}_I\,d^3r$ | Vector | Hartree/Bohr | **Electron-nuclear force** | Force exerted by the electron cloud on nucleus $I$. Purely electrostatic. |
| $-\partial E_{II}/\partial\mathbf{R}_I$ | Vector | Hartree/Bohr | **Ion-ion force** | Coulomb repulsion from other nuclei. Classical. |

### Conditions

The theorem is exact when $|\Psi\rangle$ is an exact eigenstate (or, more generally, when the energy is stationary with respect to all variational parameters). When the basis is incomplete and depends on nuclear positions, Pulay corrections must be added. For nonlocal potentials (pseudopotentials), the force cannot be expressed solely in terms of the density but retains the form $-\langle\Psi|\partial\hat{H}/\partial\mathbf{R}_I|\Psi\rangle$.

> **Connections Forward:** Forces are computed in every structural relaxation. In VASP with a plane-wave basis, the basis is independent of nuclear positions so there are no Pulay corrections for internal coordinates — but Pulay *stress* corrections are needed (Ch 13). The force theorem also underlies the coupling constant integration (Entry 16).

## 14. Stress (generalized virial) theorem


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


Read the first equation as: "the stress tensor component $\sigma_{\alpha\beta}$ is minus the energy change per unit volume when the system is deformed by an infinitesimal strain $\epsilon_{\alpha\beta}$." The strain scales every vector in the system — electron positions, nuclear positions, and cell vectors — uniformly. The wavefunction transforms by inverse-scaling all coordinates, with a prefactor to maintain normalization.

As with the force theorem, the key is that the energy is variational: the wavefunction and nuclear positions are at their equilibrium values, so the only contribution to the energy derivative comes from the explicit strain dependence of the Hamiltonian. The explicit expression involves a kinetic energy tensor $\nabla_{k\alpha}\nabla_{k\beta}$ and an interaction tensor built from the pair distances.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\sigma_{\alpha\beta}$ | Rank-2 tensor | Hartree/Bohr³ (or GPa) | **Stress tensor** | Force per unit area in direction $\alpha$ on a surface with normal $\beta$. Drives cell relaxation. |
| $\epsilon_{\alpha\beta}$ | Rank-2 tensor (symmetric) | — | **Strain tensor** | Dimensionless measure of deformation. Defined by the scaling $\mathbf{r}_\alpha \to (\delta_{\alpha\beta} + \epsilon_{\alpha\beta})\mathbf{r}_\beta$. |
| $\Omega$ | Scalar | Bohr³ (or ų) | **System volume** | Volume of the simulation cell. |

> **Connections Forward:** The stress tensor is needed for cell optimization in VASP (ISIF ≥ 3). Pulay stress — the spurious stress from an incomplete plane-wave basis — is a major practical concern (Ch 13). Setting ENCUT sufficiently high or using the correction from Appendix G is essential.

## 15. Virial theorem for pressure

> [!question]
>
> (a) Write the virial theorem relating pressure, kinetic energy, and potential energy.
> (b) Under what conditions is this theorem exact?
> (c) How does the factor of 3 arise?

> [!theorem] Virial theorem (Eq. 3.24)
>
> $$ 3P\Omega = 2E_{\text{kinetic}} + E_{\text{potential}} $$

Read this as a constraint on the partition of energy between kinetic and potential parts at equilibrium. For a system with only Coulomb interactions (where $V \propto 1/r$), the virial theorem takes this particularly simple form. The pressure $P = -\frac{1}{3}\text{Tr}\,\sigma_{\alpha\beta}$ is the isotropic part of the stress tensor — the trace of Eq. (3.23) with isotropic scaling $\epsilon_{\alpha\beta} = \epsilon\,\delta_{\alpha\beta}$. The factor of 3 comes from the three spatial dimensions (the trace of $\delta_{\alpha\beta}$).

For a system in equilibrium at zero pressure ($P = 0$), the theorem gives $E_{\text{potential}} = -2E_{\text{kinetic}}$ and $E_{\text{total}} = -E_{\text{kinetic}}$. This means the total energy of a bound Coulomb system at equilibrium is always negative and equals minus the kinetic energy — a powerful consistency check. The theorem is exact and general: it holds for any system in equilibrium, classical or quantum, at any temperature, so long as all interactions are Coulombic.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $P$ | Scalar | Hartree/Bohr³ (or GPa) | **Pressure** | Isotropic part of the stress tensor: $P = -\frac{1}{3}\text{Tr}\,\sigma_{\alpha\beta}$. |
| $E_{\text{kinetic}}$ | Scalar | Hartree | **Total kinetic energy** | Kinetic energy of all particles (electrons and nuclei). |
| $E_{\text{potential}}$ | Scalar | Hartree | **Total potential energy** | All Coulomb interactions: electron-electron, electron-nuclear, and nuclear-nuclear. |

> **Connections Forward:** The virial theorem constrains DFT functionals — exact functionals must satisfy it. It provides a consistency check for calculations and is used in the derivation of the exact conditions on the xc functional (Ch 8).

## 16. Generalized force theorem and coupling constant integration

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

Read the first equation as a generalization of the Hellmann-Feynman theorem: the derivative of the energy with respect to *any* parameter $\lambda$ equals the expectation value of the derivative of the Hamiltonian, evaluated with the eigenstate at that parameter value $\Psi_\lambda$. The second equation integrates this derivative to get a finite energy difference — an "adiabatic connection" between two states of the system.

The most important application is the third equation, which connects the non-interacting system ($\lambda = 0$) to the fully interacting system ($\lambda = 1$) by continuously turning on the electron-electron interaction. Since $\hat{H}$ is linear in $e^2$ (through $\hat{V}_{\text{int}}$), the derivative $\partial\hat{H}/\partial\lambda = \hat{V}_{\text{int}}$. The disadvantage is that you need the wavefunction $\Psi_\lambda$ at every intermediate coupling strength — these are unphysical states that don't correspond to any real system. Nevertheless, this formula is the foundation of the adiabatic connection formula for the exchange-correlation energy in DFT.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\lambda$ | Scalar parameter | — | **Coupling constant** | Scales the electron-electron interaction from 0 (noninteracting) to 1 (fully interacting). |
| $\Psi_\lambda$ | $N$-electron eigenstate | — | **Adiabatically connected wavefunction** | The ground-state wavefunction at intermediate coupling strength $\lambda$. Unphysical for $0 < \lambda < 1$. |
| $\partial\hat{H}/\partial\lambda$ | Operator | Hartree | **Hamiltonian derivative** | For coupling constant integration with $e^2\lambda$, this is $\hat{V}_{\text{int}}$. |
| $\Delta E$ | Scalar | Hartree | **Energy difference from integration** | The total energy change in going from coupling $\lambda_1$ to $\lambda_2$. |

> **Connections Forward:** The coupling constant integration is a key ingredient in the construction of the adiabatic connection formula for $E_{\text{xc}}$ (Ch 8, §8.2; Ch 9, §9.7). It provides the conceptual foundation for hybrid functionals, which mix exact exchange ($\lambda = 0$) with DFT correlation ($\lambda = 1$).

## 17. Koopmans' theorem

> [!question]
>
> (a) State Koopmans' theorem precisely.
> (b) What two effects does the theorem neglect that cause Hartree-Fock eigenvalues to be inaccurate for excitation energies?
> (c) Why do Hartree-Fock band gaps greatly overestimate experimental values?

> [!theorem] Koopmans' theorem (§3.6.3)
>
> The eigenvalue $\varepsilon_i^\sigma$ of a filled (empty) orbital in the Hartree-Fock equation is equal to the change in total energy when an electron is removed from (added to) that orbital, keeping all other orbitals unchanged.

Read this as: "in Hartree-Fock, eigenvalues are frozen-orbital ionization energies and electron affinities." For occupied states, the eigenvalue is lowered by the exchange term, which cancels the spurious self-interaction in the Hartree potential. For empty states, there is no self-interaction since both direct and exchange terms involve only occupied states. The theorem is exact within the frozen-orbital approximation — the error comes from what it neglects.

Two effects are missing: (1) *orbital relaxation* — when an electron is removed, the remaining orbitals readjust, lowering the energy of the ion relative to the Koopmans estimate; and (2) *correlation* — the change in correlation energy upon ionization. These two effects partially cancel, but the net result is that Hartree-Fock band gaps (the difference between the lowest empty and highest filled eigenvalues) greatly overestimate experimental values — often by a factor of 2 or more for semiconductors.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Semiconductors and insulators | Band gaps overestimated by factor of ~2 | Missing orbital relaxation and correlation |
| Metals | Qualitatively wrong bandwidth, density of states | Exchange is long-ranged and state-dependent |
| Strongly correlated systems (e.g., CeO₂) | Fails to capture Mott physics | Missing correlation is the dominant energy scale |

> **Connections Forward:** Koopmans' theorem motivates the $\Delta$SCF method (Entry 26). In DFT, the Kohn-Sham eigenvalues do not obey Koopmans' theorem, but Janak's theorem (Ch 7) provides an analog. The discrepancy between HF and DFT gaps is central to understanding the band gap problem.

---

# Energy Expressions & Functionals

## 18. Classical Coulomb energy grouping $E^{\text{CC}}$

> [!question]
>
> (a) Write the classical Coulomb energy in terms of the Hartree energy, electron-nuclear, and ion-ion terms.
> (b) Why must the terms be grouped as a neutral combination?
> (c) How does this grouping ensure that all individual contributions are finite in an extended system?

> [!equation] Classical Coulomb energy grouping (Eq. 3.14)
>
> $$ E^{\text{CC}} = E_{\text{Hartree}} + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} $$

Read the three terms as: (1) the self-repulsion of the electron cloud ($E_{\text{Hartree}}$), (2) the attraction between the electron cloud and the nuclei ($\int V_{\text{ext}}\,n\,d^3r$), and (3) the repulsion among the nuclei ($E_{II}$). Each individual term diverges in an extended system — the Hartree energy of an infinite charged system is infinite, as is the electron-nuclear attraction. But their sum is the electrostatic energy of a *neutral* system (positive nuclei plus negative electrons), which is finite and well-defined.

This neutral grouping is essential for practical computation. In a periodic crystal, the three terms are evaluated together using Ewald summation (Appendix F), which cancels the divergences analytically and produces a convergent sum. Never try to compute the Hartree, electron-nuclear, and ion-ion energies separately and add them — the individual terms are meaningless in an infinite system.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E^{\text{CC}}$ | Scalar | Hartree | **Classical Coulomb energy** | The total electrostatic energy of a neutral system: electron-electron + electron-nuclear + nuclear-nuclear. Finite for neutral systems. |
| $E_{\text{Hartree}}$ | Functional of $n$ | Hartree | **Hartree energy** | Classical electron self-repulsion (Entry 3). Diverges alone in extended systems. |
| $\int V_{\text{ext}}\,n\,d^3r$ | Functional of $n$ | Hartree | **Electron-nuclear attraction** | The coupling between the electron cloud and the nuclear potential. Diverges alone. |
| $E_{II}$ | Scalar | Hartree | **Ion-ion repulsion** | Classical nuclear-nuclear Coulomb energy. Diverges alone. |

> **Connections Forward:** This grouping appears in VASP output as the sum of Hartree, electron-nuclear, and Ewald energies. In the Kohn-Sham total energy (Ch 7), $E^{\text{CC}}$ is one of the well-defined energy blocks. Ewald summation (Appendix F) evaluates it in reciprocal space.

## 19. Total energy decomposition with exchange-correlation

> [!question]
>
> (a) Write the total energy decomposed into kinetic, exchange-correlation, and classical Coulomb contributions.
> (b) What is the physical interpretation of the middle term $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$?
> (c) Why is this difference short-ranged?

> [!equation] Total energy decomposition (Eq. 3.16)
>
> $$ E = \langle\hat{T}\rangle + \left(\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}\right) + E^{\text{CC}} $$

Read the three terms as: (1) kinetic energy of the interacting electrons, (2) the potential part of exchange-correlation energy, and (3) the classical Coulomb energy of the neutral system. Each of the three terms is individually well-defined and finite.

The middle term in parentheses — $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ — is the difference between the true quantum-mechanical electron-electron interaction energy and the classical mean-field approximation to it. This difference is exactly the potential part of $E_{\text{xc}}$ as defined in DFT. Physically, it represents the energy lowering from exchange (Pauli avoidance) and correlation (Coulomb avoidance beyond mean field). Crucially, this difference is *short-ranged*: the long-range Coulomb interactions cancel between $\langle\hat{V}_{\text{int}}\rangle$ and $E_{\text{Hartree}}$ because both have the same long-range $1/r$ tail from the average density. Only the short-range corrections from exchange and correlation survive. This is why local and semi-local density functionals (LDA, GGA) can approximate $E_{\text{xc}}$ — the object they need to approximate is fundamentally local.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ | Scalar | Hartree | **Potential part of $E_{\text{xc}}$** | Difference between quantum and classical electron-electron energy. Short-ranged. Always negative (exchange lowers the energy). |
| $E^{\text{CC}}$ | Scalar | Hartree | **Classical Coulomb energy** | Neutral grouping from Entry 18. Well-defined and long-ranged. |

> **Connections Forward:** This decomposition is the prototype for the Kohn-Sham energy expression (Ch 7). The insight that xc is short-ranged is the physical justification for LDA (Ch 8) and GGA. It also explains why the xc hole picture (Entry 9) works — the relevant physics is local.

## 20. Hartree-Fock total energy

> [!question]
>
> (a) Write the Hartree-Fock total energy in terms of orbital integrals.
> (b) Identify the direct (Hartree) and exchange contributions.
> (c) Why is the self-interaction included in the direct term and then canceled by exchange?

> [!equation] Hartree-Fock total energy (Eq. 3.44)
>
> $$\begin{aligned} \langle\Phi|\hat{H}|\Phi\rangle = &\sum_{i,\sigma} \int d\mathbf{r}\, \psi_i^{\sigma*}(\mathbf{r})\left[-\frac{1}{2}\nabla^2 + V_{\text{ext}}(\mathbf{r})\right]\psi_i^\sigma(\mathbf{r}) + E_{II} \\ &+ \frac{1}{2}\sum_{i,j,\sigma_i,\sigma_j} \int d\mathbf{r}\,d\mathbf{r}'\, \frac{|\psi_i^{\sigma_i}(\mathbf{r})|^2 |\psi_j^{\sigma_j}(\mathbf{r}')|^2}{|\mathbf{r}-\mathbf{r}'|} \\ &- \frac{1}{2}\sum_{i,j,\sigma} \int d\mathbf{r}\,d\mathbf{r}'\, \frac{\psi_i^{\sigma*}(\mathbf{r})\psi_j^{\sigma*}(\mathbf{r}')\psi_j^\sigma(\mathbf{r})\psi_i^\sigma(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|} \end{aligned}$$

Read this as four contributions. The first line is the sum of single-particle energies: kinetic energy plus external potential for each occupied orbital, plus the ion-ion energy. The second line is the *direct* (Hartree) interaction — the Coulomb repulsion between the charge densities $|\psi_i|^2$ and $|\psi_j|^2$ of all pairs of orbitals, including the self-term $i = j$. Including the self-term lets you write $\sum_{i,j} |\psi_i|^2 |\psi_j|^2 = n(\mathbf{r})\,n(\mathbf{r}')$, which is the Hartree energy of the total density. The third line is the *exchange* interaction, summed over same-spin pairs only (opposite-spin exchange vanishes due to spin orthogonality). It involves the exchange of coordinates: orbital $i$ at $\mathbf{r}$ and orbital $j$ at $\mathbf{r}'$ swap positions. Crucially, the $i = j$ self-term in the exchange exactly cancels the spurious $i = j$ self-term in the direct sum — this is the self-interaction cancellation.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| First line (single-body terms) | Sum over orbitals | Hartree | **Kinetic + external + $E_{II}$** | Orbital kinetic energies and electron-nuclear attraction. Same as in an independent-particle calculation. |
| Second line (direct term) | Double sum over orbitals | Hartree | **Direct (Hartree) energy** | Classical Coulomb repulsion between orbital charge densities. Includes spurious self-interaction. |
| Third line (exchange term) | Double sum over same-spin orbitals | Hartree | **Exchange energy** | Energy lowering from Pauli exclusion. Same-spin only. Cancels self-interaction. Always negative. |

> **Connections Forward:** The Hartree-Fock energy is the reference for defining the correlation energy ($E_c = E_{\text{exact}} - E_{\text{HF}}$). The DFT definition of $E_c$ differs slightly — orbitals are constrained to give the exact density rather than minimize $E_{\text{HF}}$ (see Ch 7). The exchange term here becomes the "exact exchange" mixed into hybrid functionals (PBE0, HSE).

## 21. Exchange energy from the exchange hole

> [!question]
>
> (a) Write the exchange energy in terms of the exchange hole.
> (b) Why can the exchange energy be interpreted as the interaction of each electron with a positive hole?
> (c) For a one-electron system, show that the exchange energy exactly cancels the Hartree energy.

> [!equation] Exchange energy (Eq. 3.57)
>
> $$ E_x = \left[\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}(n)\right]_{\text{HFA}} = \frac{1}{2}\sum_{\sigma\sigma'}\int d^3r \int d^3r'\, \frac{\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{|\mathbf{r}-\mathbf{r}'|} $$

Read this as: "the exchange energy is the Coulomb interaction between each electron and its exchange hole." The exchange hole $\Delta n_x$ (Entry 9) is always negative — it represents a depletion of one electron's worth of charge around each electron. Since the hole is negative and the Coulomb kernel $1/|\mathbf{r} - \mathbf{r}'|$ is positive, the exchange energy is always negative — it lowers the total energy. Physically, the exchange hole keeps same-spin electrons apart, reducing their Coulomb repulsion below the mean-field (Hartree) value.

For a one-electron system (e.g., hydrogen), the exchange hole is exactly the electron density: $\Delta n_x(\mathbf{r};\mathbf{r}') = -|\psi(\mathbf{r})|^2\delta_{\sigma\sigma'}$, and the exchange energy exactly cancels the Hartree energy. There is no real "exchange" for one electron — the exchange term is just removing the self-interaction that the Hartree term incorrectly included. This cancellation is exact in Hartree-Fock but is only approximate in DFT with approximate functionals — the resulting self-interaction error is a major source of error for localized states.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E_x$ | Scalar | Hartree | **Exchange energy** | Energy lowering from Pauli exclusion. Always negative. Equals $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ in the Hartree-Fock approximation. |
| $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Exchange hole** | Depletion of same-spin electron density around each electron. Always $\leq 0$. Integrates to $-1$. |
| $1/\|\mathbf{r}-\mathbf{r}'\|$ | Coulomb kernel | Bohr⁻¹ | **Pair Coulomb weight** | Weights the exchange hole by inverse separation; determines the energy contribution of the hole. |

> **Connections Forward:** The exchange energy is the starting point for understanding $E_{\text{xc}}$ in DFT. The LDA exchange (Dirac, Ch 5) approximates it locally. The exact exchange is the $\lambda = 0$ limit in the adiabatic connection (Ch 9, §9.7) and appears explicitly in hybrid functionals (PBE0: 25% exact exchange; HSE: screened exact exchange).

## 22. Independent-particle energy at finite temperature

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

Read the first equation as: "the expectation value of any single-body operator for non-interacting particles is just the weighted sum of the operator's expectation value in each orbital, weighted by the occupation probability $f_i^\sigma$." This is a dramatic simplification: instead of tracing over all many-body states, you sum over single-particle states with Fermi-Dirac weights. The second equation specializes this to the Hamiltonian, giving the total energy as the occupation-weighted sum of eigenvalues.

The Fermi-Dirac weights $f_i^\sigma$ (Entry 6) encode the thermal equilibrium occupation: at $T = 0$ they are step functions (all states below $\mu$ occupied, all above empty); at finite $T$ the step softens over a range $\sim k_BT$. This smearing allows fractional occupation of states near $\mu$, which is computationally useful for metallic systems where a sharp step function would cause convergence problems in the self-consistency cycle.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\sum_{i,\sigma} f_i^\sigma \varepsilon_i^\sigma$ | Weighted sum | Hartree | **Band energy** | Sum of eigenvalues weighted by occupation. Equals the total energy only for noninteracting particles — in DFT it is the band energy, not the total energy. |
| $f_i^\sigma$ | Occupation weight | — | **Fermi-Dirac weight** | Thermal occupation probability for state $(i,\sigma)$. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalue** | Energy of orbital $i$ with spin $\sigma$. |

> **Connections Forward:** In Kohn-Sham DFT (Ch 7), the band energy $\sum f_i \varepsilon_i$ is *not* the total energy — it double-counts the Hartree energy and includes the xc potential contribution. The total energy must be corrected (see the Kohn-Sham energy expression). In VASP, the smearing scheme is set by `ISMEAR` and `SIGMA`.

---

# Approximations & Their Failures

## 23. Born-Oppenheimer (adiabatic) approximation

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

Read this as: "electrons are so much lighter than nuclei that they adjust instantaneously to any nuclear motion." The electronic problem is solved for fixed nuclear positions, giving an energy surface $E(\{\mathbf{R}_I\})$ on which the nuclei then move classically (or quantum-mechanically, in a second step). The nuclear positions enter the electronic Hamiltonian as parameters, not as quantum-mechanical degrees of freedom.

The approximation is excellent for most ground-state properties: crystal structures, elastic constants, phonon frequencies (via the energy surface). It begins to fail when electronic states come close in energy and nuclear motion can cause transitions between them — this is electron-phonon coupling, which is the basis for electrical resistance in metals, polaron formation, superconductivity (BCS theory), and certain metal-insulator transitions.

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

## 24. Noninteracting (Hartree-like) electron approximation

> [!question]
>
> (a) Write the effective single-particle Schrödinger equation.
> (b) How is the ground state constructed from the single-particle solutions?
> (c) What is the relationship between this approximation and the Kohn-Sham equations?

> [!approximation] Noninteracting electron approximation (Eq. 3.36)
>
> $$ \hat{H}_{\text{eff}}\psi_i^\sigma(\mathbf{r}) = \left[-\frac{\hbar^2}{2m_e}\nabla^2 + V_{\text{eff}}^\sigma(\mathbf{r})\right]\psi_i^\sigma(\mathbf{r}) = \varepsilon_i^\sigma \psi_i^\sigma(\mathbf{r}) $$

Read this as: "replace the intractable many-body problem with $N$ independent single-particle problems, each electron moving in an effective potential $V_{\text{eff}}^\sigma(\mathbf{r})$ that incorporates the average effect of all other electrons." The ground state is built by filling the lowest $N$ eigenstates according to the Pauli principle. There is no need to construct an explicit antisymmetric wavefunction — the single-particle eigenvalues and orbitals give all the information needed.

The key question is: what goes into $V_{\text{eff}}^\sigma$? In the original Hartree approach, it was the nuclear potential plus an average Coulomb potential from the other electrons (with a self-correction). In the Kohn-Sham approach, $V_{\text{eff}}^\sigma$ is chosen so that the resulting density exactly matches the true interacting density — this requires including exchange and correlation effects in the potential. The Kohn-Sham equations have exactly this form, with $V_{\text{eff}}^\sigma = V_{\text{ext}} + V_{\text{Hartree}} + V_{\text{xc}}^\sigma$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{H}_{\text{eff}}$ | Single-particle operator | Hartree | **Effective Hamiltonian** | Single-electron Hamiltonian with all many-body effects folded into $V_{\text{eff}}$. |
| $V_{\text{eff}}^\sigma(\mathbf{r})$ | Scalar field (spin-dependent) | Hartree | **Effective potential** | The local, multiplicative potential acting on each electron. Includes nuclear attraction plus an approximation to electron-electron effects. |
| $\psi_i^\sigma(\mathbf{r})$ | Single-particle orbital | Bohr⁻$^{3/2}$ | **Eigenstates** | Solutions of the effective Schrödinger equation. Orthogonal by construction. |
| $\varepsilon_i^\sigma$ | Scalar | Hartree (or eV) | **Single-particle eigenvalues** | Energies of the orbitals. Their physical meaning depends on what $V_{\text{eff}}$ represents. |

### Practical Consequences

This is the equation solved in every Kohn-Sham DFT calculation. The entire machinery of electronic structure — plane-wave basis sets (Ch 12–13), pseudopotentials (Ch 11), k-point sampling — is devoted to solving this equation efficiently and accurately.

> **Connections Forward:** The Kohn-Sham equations (Ch 7) are exactly this equation with a specific choice of $V_{\text{eff}}$. All the computational methods in Chapters 11–17 are methods for solving it. In VASP, the SCF cycle iteratively updates $V_{\text{eff}}$ until self-consistency.

## 25. Hartree-Fock approximation

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

Read the first three terms (in square brackets) as the same effective single-particle equation as Entry 24, with the external potential and the Hartree potential. The fourth term — the exchange operator — is fundamentally different from a local potential: it acts on $\psi_i^\sigma(\mathbf{r})$ through an *integral* involving all the other occupied same-spin orbitals $\psi_j^\sigma$. The integrand $\psi_j^{\sigma*}(\mathbf{r}')\psi_i^\sigma(\mathbf{r}')$ is the "exchange charge density" for the pair $(i,j)$ — it measures the overlap of orbitals $i$ and $j$ at the point $\mathbf{r}'$. The integral of this charge density times the Coulomb kernel gives a potential at $\mathbf{r}$ that multiplies $\psi_j^\sigma(\mathbf{r})$, not $\psi_i^\sigma(\mathbf{r})$ — this is what makes the operator nonlocal and state-dependent.

The nonlocality and state-dependence mean that Hartree-Fock is computationally much more expensive than a local-potential calculation: the exchange integrals involve four orbital indices and scale as $N_{\text{basis}}^4$ in general. For localized basis functions, the scaling can be reduced because the exchange charge density decays rapidly with the distance between orbitals.

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

## 26. $\Delta$SCF method

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

Read this as: "instead of using eigenvalues as approximate excitation energies (Koopmans' theorem), compute the actual energy difference between the $N$-electron and $(N \pm 1)$-electron systems, allowing all orbitals to relax in each calculation." This captures orbital relaxation (the rearrangement of all other electrons in response to adding or removing one) and, within DFT, also includes whatever correlation the functional captures.

The method works well for finite systems (atoms, molecules) because the added or removed electron changes the system's properties locally and the energy difference is well-defined. For extended systems (bulk solids), adding one electron to an infinite system is an infinitesimal perturbation — the energy change per electron goes to zero, and the method becomes equivalent to computing the Fermi level. In practice, $\Delta$SCF for solids requires supercell calculations with careful finite-size corrections.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Extended solids (bulk) | Energy difference goes to zero as $1/N_{\text{atoms}}$ | One electron in an infinite system is an infinitesimal perturbation |
| Systems with strong charge transfer | Requires multiple SCF solutions | May converge to wrong state if initial guess is poor |

> **Connections Forward:** The $\Delta$SCF approach is used in DFT for computing ionization energies and electron affinities of molecules (Ch 10, §10.6). For solids, constrained DFT or the quasiparticle approach (GW) is more appropriate. Your CeO₂ calculations use total energy differences between oxidation states, which is conceptually related.

---

# Statistical Mechanics (Supplementary Entries)

The following entries cover the statistical mechanics framework from §3.5, which provides the finite-temperature foundation used in all practical calculations.

## S1. Free energy and the density matrix (§3.5)

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

Read the free energy expression as two competing terms. The first, $\text{Tr}\,\hat{\rho}\hat{H}$, is the internal energy $U = \langle\hat{H}\rangle$ — it favors low-energy states. The second, $\frac{1}{\beta}\text{Tr}\,\hat{\rho}\ln\hat{\rho}$, is minus the temperature times the entropy ($-TS$) — it favors spreading probability over many states. At low temperature ($\beta \to \infty$), the energy term dominates and the system collapses to the ground state. At high temperature, the entropy term dominates and all states become equally likely.

The equilibrium density matrix $\hat{\rho} = e^{-\beta\hat{H}}/Z$ is the Boltzmann distribution: it assigns probability $\propto e^{-\beta E_i}$ to each eigenstate $i$. This reduces to $|\Psi_0\rangle\langle\Psi_0|$ at $T = 0$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $F$ | Scalar | Hartree | **Helmholtz free energy** | $F = U - TS$. The thermodynamic potential minimized at fixed $T$, $V$, and $N$. |
| $\hat{\rho}$ | Operator | — | **Density matrix** | Encodes the statistical mixture of quantum states. Positive definite; $\text{Tr}\,\hat{\rho} = 1$. |
| $Z$ | Scalar | — | **Partition function** | Normalization constant. $Z = e^{-\beta F}$ connects statistical mechanics to thermodynamics. |
| $\beta = 1/(k_BT)$ | Scalar | Hartree⁻¹ | **Inverse temperature** | Controls the competition between energy and entropy. |

> **Connections Forward:** The Mermin functional (Ch 6, §6.5.1) extends DFT to finite temperature using the density matrix. In VASP, Fermi-Dirac smearing effectively works at finite electronic temperature; the free energy $F$ (rather than $E$) should be used for metallic systems.



## S2. Full Hamiltonian for electrons and nuclei (§3.1)

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

This is the most general starting point for all of electronic structure theory — before any approximations. The five terms are, in order: electron kinetic energy, electron-nuclear attraction, electron-electron repulsion, nuclear kinetic energy, and nuclear-nuclear repulsion. The first three involve electrons (lowercase subscripts); the last two involve nuclei (uppercase subscripts, with charge $Z_I$ and mass $M_I$).

The only small parameter is $1/M_I$ — the inverse nuclear mass. Since $M_I \gg m_e$ (even the lightest nucleus, hydrogen, is ~1836 times heavier than an electron), the nuclear kinetic energy is small compared to all other terms. This is what justifies the Born-Oppenheimer approximation (Entry 23): set $M_I \to \infty$, drop the nuclear kinetic energy, and treat $\{\mathbf{R}_I\}$ as fixed parameters. Everything else — including the electron-electron interaction, which makes the problem hard — is not small and must be treated nonperturbatively.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $m_e$ | Scalar constant | kg | **Electron mass** | Sets the scale of electron kinetic energy. |
| $M_I$ | Scalar constant | kg | **Nuclear mass** | Mass of nucleus $I$. $M_I/m_e \gg 1$ is the basis for the Born-Oppenheimer approximation. |
| $Z_I$ | Integer | — | **Nuclear charge** | Atomic number of nucleus $I$. |
| $e^2$ | Scalar constant | Hartree·Bohr | **Coulomb coupling** | Strength of the electromagnetic interaction ($e^2 = q_e^2 / 4\pi\epsilon_0$ in SI). |

> **Connections Forward:** Dropping the nuclear kinetic energy gives the electronic Hamiltonian (Entry 1). The nuclear kinetic energy, treated perturbatively, gives electron-phonon coupling (Ch 19) — essential for superconductivity, polaron formation, and electrical transport.



## S3. Exchange hole for noninteracting fermions (§3.7.1)

> [!question]
>
> (a) Write the explicit expression for the exchange hole in the Hartree-Fock approximation.
> (b) What three properties must any exchange hole satisfy, and can you prove each from the formula?
> (c) Why does the exchange hole involve only same-spin electrons?

> [!definition] Exchange hole (Eq. 3.54)
>
> $$ \Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -\delta_{\sigma\sigma'}\left|\sum_i \psi_i^{\sigma*}(\mathbf{r})\,\psi_i^\sigma(\mathbf{r}')\right|^2 $$

Read this as: the exchange hole at $\mathbf{r}'$ around an electron of spin $\sigma$ at $\mathbf{r}$ is the negative of the squared modulus of the density matrix $\rho_\sigma(\mathbf{r},\mathbf{r}')$. The Kronecker delta $\delta_{\sigma\sigma'}$ means exchange acts only between same-spin electrons — opposite-spin electrons are unaffected because the spin parts of their orbitals are orthogonal.

Three constraints govern any exchange hole: (1) it is always non-positive, $\Delta n_x \leq 0$, since it is minus a squared quantity; (2) the probability of finding two same-spin electrons at the same point vanishes ($\Delta n_x(\mathbf{r},\sigma;\mathbf{r},\sigma) = -n(\mathbf{r},\sigma)$, which cancels the density); and (3) it integrates to exactly one missing electron, $\int d^3r'\,\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -1$, because the exchange hole accounts for the fact that the electron at $\mathbf{r}$ cannot simultaneously be at $\mathbf{r}'$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ | Two-point function | Bohr⁻³ | **Exchange hole** | Charge depletion around an electron due to Pauli exclusion. Always $\leq 0$; integrates to $-1$. |
| $\delta_{\sigma\sigma'}$ | Kronecker delta | — | **Spin selector** | Restricts exchange to same-spin electron pairs. |
| $\sum_i \psi_i^{\sigma*}(\mathbf{r})\psi_i^\sigma(\mathbf{r}')$ | Scalar | Bohr⁻³ | **Off-diagonal density matrix** | $\rho_\sigma(\mathbf{r},\mathbf{r}')$; the exchange hole is $-|\rho_\sigma|^2$. |

> **Connections Forward:** The exchange energy (Entry 21) is the Coulomb interaction of each electron with its exchange hole. The exchange hole is the starting point for understanding the exchange-correlation hole (Entry 9) and for constructing approximate density functionals (Ch 8–9). Self-interaction cancellation in Hartree-Fock is a direct consequence of the exchange hole integrating to exactly one electron.
