# Equation Index — Martin, Chapter 6: Density Functional Theory: Foundations

Electronic Structure Vault

---

## Master Reference

### Definitions & Building Blocks (1–7)

| # | Name | Section |
|---|---|---|
| 1 | Electron density $n(\mathbf{r})$ | §6.2 |
| 2 | External potential $V_{\text{ext}}(\mathbf{r})$ | §6.2 |
| 3 | Hartree energy | §6.2 |
| 4 | Particle number constraint | §6.2 |
| 5 | Many-body Hamiltonian for electrons | §6.3 |
| 6 | Spin density | §6.5 |
| 7 | $V$-representability vs. $N$-representability | §6.6 |

### Theoretical Foundations (8–15)

| # | Name | Section |
|---|---|---|
| 8 | Hohenberg-Kohn Theorem I — density determines potential | §6.3.1 |
| 9 | Hohenberg-Kohn Theorem II — variational principle | §6.3.2 |
| 10 | Hohenberg-Kohn energy functional $E_{\text{HK}}[n]$ | §6.3.2 |
| 11 | Universal functional $F_{\text{HK}}[n]$ | §6.3.2 |
| 12 | Levy-Lieb constrained search functional $F_{\text{LL}}[n]$ | §6.4 |
| 13 | Mermin finite-temperature grand potential functional | §6.5.1 |
| 14 | Spin density functional theory | §6.5 |
| 15 | Nonanalyticity of the exact functional | §6.7 |

### Approximations & Their Failures (16–17)

| # | Name | Section |
|---|---|---|
| 16 | Thomas-Fermi-Dirac energy functional | §6.2 |
| 17 | Weizsäcker gradient correction | §6.2 |

---

# Definitions & Building Blocks

## 1. Electron density $n(\mathbf{r})$

> [!question]
>
> (a) Write the definition of the electron density in terms of the many-body wavefunction.
> (b) What is the physical meaning of $n(\mathbf{r})\,d^3r$?
> (c) Why is the density — a single scalar function of three variables — so much simpler than the many-body wavefunction?

> [!definition] Electron density
>
> $$ n(\mathbf{r}) = N \int d^3r_2 \cdots d^3r_N \,|\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2 $$

Read this equation right to left: start with $|\Psi|^2$, the joint probability density for finding all $N$ electrons at specific positions $(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)$. The integration $\int d^3r_2 \cdots d^3r_N$ then says "I don't care where the other $N-1$ electrons are — average over all their possible positions." What remains is the probability of finding one particular electron at $\mathbf{r}$. The prefactor $N$ accounts for the fact that electrons are indistinguishable: since any of the $N$ electrons could be the one sitting at $\mathbf{r}$, you multiply by $N$ to get the total density of electrons at that point.

The result is an extraordinary compression of information. The many-body wavefunction $\Psi$ lives in $3N$-dimensional configuration space — for a unit cell of CeO₂ with hundreds of electrons, that is a function of hundreds of variables. The density $n(\mathbf{r})$ lives in ordinary three-dimensional space regardless of how many electrons the system contains. The entire power of DFT rests on the Hohenberg-Kohn proof that this single scalar field encodes, in principle, all ground-state information that was in the full wavefunction. The density is directly measurable by X-ray and electron scattering experiments, making it a physically observable quantity rather than a mathematical abstraction.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\|\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)\|^2$ | Probability density in $3N$-space | Å$^{-3N}$ | **Joint probability density** | The probability per unit $3N$-dimensional volume of finding the electrons at positions $(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)$. |
| $\int d^3r_2 \cdots d^3r_N$ | Integration over $(N-1)$ positions | Å$^{3(N-1)}$ | **Marginal integration** | Traces out all electron coordinates except the one at $\mathbf{r}$; reduces the $3N$-dimensional object to a 3-dimensional one. |
| $N$ | Integer | — | **Electron number prefactor** | Accounts for indistinguishability: any of the $N$ electrons could be the one at $\mathbf{r}$. |
| $n(\mathbf{r})$ | Scalar field: $\mathbb{R}^3 \to \mathbb{R}^+$ | Å⁻³ (or Bohr⁻³) | **Electron density** | The total density of electrons at point $\mathbf{r}$; integrates to $N$. The VASP output `CHGCAR` file is this quantity on a real-space grid. |

> **Connections Forward:** The density is the variable in every functional in this chapter and in Chapters 7–9. Your VASP output `CHGCAR` file *is* this quantity on a real-space grid.

## 2. External potential $V_{\text{ext}}(\mathbf{r})$

> [!question]
>
> (a) For electrons in a solid, what is the physical origin of $V_{\text{ext}}(\mathbf{r})$?
> (b) Why does $V_{\text{ext}}$ play a special role in the Hohenberg-Kohn theorems — what is it about the form of the Hamiltonian that singles it out?
> (c) Is the electron-electron interaction part of $V_{\text{ext}}$?

> [!definition] External potential
>
> The potential acting on the electrons from sources external to the electron system — typically the Coulomb potential of the nuclei:
> $$ V_{\text{ext}}(\mathbf{r}) = -\sum_I \frac{Z_I e^2}{|\mathbf{r} - \mathbf{R}_I|} $$

Read this expression as a sum of Coulomb wells, one per nucleus. Each term $-Z_I e^2 / |\mathbf{r} - \mathbf{R}_I|$ says: "nucleus $I$, sitting at position $\mathbf{R}_I$ with charge $Z_I$, pulls on an electron at $\mathbf{r}$ with the classical Coulomb attraction." The negative sign reflects the attractive nature of the interaction — electrons are drawn toward nuclei. The denominator $|\mathbf{r} - \mathbf{R}_I|$ is just the distance between the electron and nucleus $I$: the closer the electron, the stronger the pull. The sum $\sum_I$ adds up the pulls from all nuclei in the system — in a CeO₂ unit cell, this sums over the Ce and O nuclei.

The external potential is the "input" to the electronic structure problem: given the nuclear positions $\{\mathbf{R}_I\}$ and charges $\{Z_I\}$, $V_{\text{ext}}$ is completely specified. It plays a distinguished role in the Hohenberg-Kohn theorems because it enters the total energy through the bilinear coupling $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$ — external potential times density — and it is this simple multiplicative structure that allows the density to serve as the basic variable. The electron-electron interaction is *not* part of $V_{\text{ext}}$; it is an internal energy that belongs to the universal functional $F_{\text{HK}}[n]$ and has the same form regardless of which material you study.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $-Z_I e^2 / \|\mathbf{r} - \mathbf{R}_I\|$ | Scalar field per nucleus | Hartree (or eV) | **Single-nucleus Coulomb well** | The attractive potential felt by an electron at $\mathbf{r}$ due to nucleus $I$. Diverges as $\mathbf{r} \to \mathbf{R}_I$. |
| $\sum_I$ | Sum over all nuclei | — | **Nuclear summation** | Adds up the Coulomb pulls from every nucleus in the system. |
| $V_{\text{ext}}(\mathbf{r})$ | Scalar field: $\mathbb{R}^3 \to \mathbb{R}$ | Hartree (or eV) | **External potential** | The total potential landscape that electrons move through. System-specific — it is the only part of the Hamiltonian that distinguishes one material from another. |
| $Z_I$ | Integer | — | **Nuclear charge** | Atomic number of nucleus $I$; 58 for Ce, 8 for O. |
| $\mathbf{R}_I$ | Position vector | Å (or Bohr) | **Nuclear position** | Location of nucleus $I$. In VASP, these come from the POSCAR file. |

> **Connections Forward:** $V_{\text{ext}}$ is the system-specific input to every DFT calculation. In VASP, the nuclear positions (POSCAR) and pseudopotentials (POTCAR) together define $V_{\text{ext}}$. Pseudopotentials (Ch 11) replace the divergent all-electron $V_{\text{ext}}$ near the nucleus with a smooth effective potential.

## 3. Hartree energy

> [!question]
>
> (a) Write the Hartree energy in terms of the electron density.
> (b) What physics does the Hartree energy capture, and what does it miss?
> (c) Why does it include a spurious self-interaction?

> [!definition] Hartree energy
>
> $$ E_{\text{Hartree}}[n] = \frac{1}{2} \int d^3r \, d^3r' \, \frac{n(\mathbf{r})\,n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} $$

Read this double integral from the inside out. The product $n(\mathbf{r})\,n(\mathbf{r}')$ asks: "how much charge is at point $\mathbf{r}$, and independently, how much charge is at point $\mathbf{r}'$?" — it treats the two chunks of charge as if they were independent, uncorrelated classical charge distributions. The Coulomb kernel $1/|\mathbf{r} - \mathbf{r}'|$ weights each pair by the inverse of their separation: nearby charge pairs contribute large repulsion, distant pairs contribute little. The double integration $\int d^3r\,d^3r'$ sums over all pairs of points in space — every bit of charge repels every other bit. The prefactor $\frac{1}{2}$ corrects for double-counting: the integral counts the pair $(\mathbf{r}, \mathbf{r}')$ and the pair $(\mathbf{r}', \mathbf{r})$ separately, but they represent the same physical interaction.

The Hartree energy captures the dominant, long-range, mean-field part of the electron-electron repulsion — the energy you would get if you smeared the electrons into a continuous, classical charge cloud. What it misses is everything quantum mechanical about the electron-electron interaction. It misses *exchange*: the tendency of same-spin electrons to avoid each other due to the Pauli principle, which lowers the repulsion energy. It misses *correlation*: the additional avoidance due to Coulomb repulsion beyond the mean-field level. And it includes a physically spurious *self-interaction*: since the integral does not exclude the case $\mathbf{r} = \mathbf{r}'$ from the same electron, each electron repels itself through the mean field. Correcting for all three of these errors — exchange, correlation, and self-interaction — is the central challenge of constructing the exchange-correlation functional.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r})\,n(\mathbf{r}')$ | Scalar function of two positions | Å⁻⁶ | **Uncorrelated pair density** | Treats charge at $\mathbf{r}$ and $\mathbf{r}'$ as independent — the classical, mean-field approximation to the true pair density. |
| $1/\|\mathbf{r} - \mathbf{r}'\|$ | Coulomb kernel | Å⁻¹ (or Bohr⁻¹) | **Pair Coulomb repulsion** | Weights each pair of charges by the inverse of their separation; nearby pairs contribute more. |
| $\frac{1}{2}\int d^3r\,d^3r'$ | Double spatial integration | — | **Pair summation with double-counting correction** | Sums the Coulomb repulsion over all pairs of points; the $\frac{1}{2}$ prevents counting each pair twice. |
| $E_{\text{Hartree}}[n]$ | Functional: $n(\mathbf{r}) \mapsto \mathbb{R}$ | Hartree | **Hartree energy** | The classical electrostatic self-energy of the electron charge distribution. Includes spurious self-interaction. |

> **Connections Forward:** The Hartree energy appears in the Kohn-Sham total energy (Ch 7) and understanding its self-interaction error is key to understanding why DFT+U is needed for Ce 4f electrons.

## 4. Particle number constraint (Eq. 6.2)

> [!question]
>
> (a) Write the constraint that the density must satisfy.
> (b) How is this constraint enforced in the variational minimization?
> (c) What is the physical meaning of the Lagrange multiplier $\mu$?

> [!equation] Particle number constraint (Eq. 6.2)
>
> $$ \int d^3r \, n(\mathbf{r}) = N $$

This is the normalization condition for the density, analogous to $\int |\psi|^2 d^3r = 1$ for a single-particle wavefunction. Read it as: "if you add up all the electron density throughout all of space, you must get exactly $N$ electrons." It ensures that the density is a legitimate density — that no electrons have been created or destroyed in the process of minimizing the energy functional.

When minimizing $E[n]$ subject to this constraint, one introduces a Lagrange multiplier $\mu$ by constructing the unconstrained functional $\Omega[n] = E[n] - \mu\left(\int n(\mathbf{r})\,d^3r - N\right)$. The stationarity condition $\delta\Omega/\delta n(\mathbf{r}) = 0$ then gives $\delta E/\delta n(\mathbf{r}) = \mu$ — the functional derivative of the energy with respect to density equals $\mu$ everywhere in space. The multiplier $\mu$ is the *chemical potential*: it is the energy cost of adding one more electron to the system. At zero temperature, it equals the Fermi energy — the energy of the highest occupied state. Its value adjusts itself self-consistently so that the minimizing density integrates to exactly $N$.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\int d^3r\,n(\mathbf{r})$ | Integral over all space | — | **Total electron count** | The sum of all electron density; must equal the integer $N$. |
| $N$ | Integer | — | **Electron number** | Total number of electrons in the system. |
| $\mu$ | Scalar | Hartree (or eV) | **Chemical potential** | Lagrange multiplier enforcing particle number; $\mu = \delta E/\delta n$. Equals the Fermi energy at $T = 0$. |
| $\Omega[n] = E[n] - \mu(\int n\,d^3r - N)$ | Functional | Hartree | **Grand potential functional** | The unconstrained functional whose stationarity simultaneously satisfies the energy minimization and the particle number constraint. |

> **Connections Forward:** The chemical potential $\mu$ becomes the Fermi energy in the Kohn-Sham equations (Ch 7). In VASP, $\mu$ is the `E-fermi` printed in the OUTCAR. Its discontinuity at integer electron number is related to the band gap (Entry 15).

## 5. Many-body Hamiltonian for electrons (Eq. 6.6)

> [!question]
>
> (a) Write the many-body Hamiltonian for electrons in an external potential.
> (b) Identify the three terms and state what physics each represents.
> (c) Which term is universal (the same for all electron systems), and which is system-specific?

> [!equation] Many-body Hamiltonian (Eq. 6.6)
>
> $$ \hat{H} = -\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2 + \sum_i V_{\text{ext}}(\mathbf{r}_i) + \frac{1}{2}\sum_{i \neq j} \frac{e^2}{|\mathbf{r}_i - \mathbf{r}_j|} $$

This is the full quantum mechanical problem that DFT replaces with a density functional. Read the three terms as three contributions to the total energy, each representing a distinct physical mechanism.

The first term, $-\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2$, is the kinetic energy of all $N$ electrons. The Laplacian $\nabla_i^2$ measures how sharply the wavefunction curves around electron $i$ — the more it curves (the more tightly confined the electron), the higher the kinetic energy. The prefactor $\hbar^2/(2m_e)$ sets the energy scale for quantum confinement. The sum $\sum_i$ runs over every electron.

The second term, $\sum_i V_{\text{ext}}(\mathbf{r}_i)$, is the interaction of each electron with the nuclei. This is the *only* system-specific part of the Hamiltonian — it is the term that distinguishes CeO₂ from silicon from hydrogen. All the information about what material you are studying — the positions and charges of the nuclei — enters exclusively through this term.

The third term, $\frac{1}{2}\sum_{i \neq j} e^2/|\mathbf{r}_i - \mathbf{r}_j|$, is the electron-electron Coulomb repulsion. It sums the repulsive interaction over all pairs of electrons; the $\frac{1}{2}$ corrects for double-counting, and the $i \neq j$ restriction prevents an electron from repelling itself. This term is what makes the many-body problem hard: every electron interacts with every other electron, coupling all $N$ degrees of freedom together. This term is universal — it has the same form in every electron system.

The first and third terms together form the universal functional $F_{\text{HK}}[n] = T[n] + E_{\text{int}}[n]$: they encode the kinetic and interaction energies that depend on the density alone, independent of which material you are studying.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $-\frac{\hbar^2}{2m_e}\nabla_i^2$ | Single-electron operator | Hartree | **Kinetic energy of electron $i$** | Measures the quantum kinetic energy from wavefunction curvature. Higher curvature (tighter confinement) means more kinetic energy. |
| $\sum_i$ (on kinetic term) | Sum over $N$ electrons | — | **Kinetic sum** | Totals the kinetic energy over all electrons. Universal — same form in every system. |
| $V_{\text{ext}}(\mathbf{r}_i)$ | Single-electron potential | Hartree | **Electron-nuclear interaction for electron $i$** | The Coulomb attraction of electron $i$ to all nuclei. System-specific — this is what makes Ce different from Si. |
| $e^2/\|\mathbf{r}_i - \mathbf{r}_j\|$ | Pairwise operator | Hartree | **Coulomb repulsion between electrons $i$ and $j$** | The electrostatic repulsion between one pair of electrons. Grows without bound as the electrons approach each other. |
| $\frac{1}{2}\sum_{i \neq j}$ | Pair summation | — | **Pair sum with double-counting correction** | Sums over all distinct electron pairs. The $\frac{1}{2}$ corrects for counting each pair $(i,j)$ and $(j,i)$. Universal. |

> **Connections Forward:** The Kohn-Sham construction (Ch 7) replaces this intractable many-body Hamiltonian with an auxiliary system of non-interacting electrons moving in an effective potential. The electron-electron interaction is folded into the exchange-correlation functional $E_{\text{xc}}[n]$.

## 6. Spin density

> [!question]
>
> (a) Write the total density and spin density in terms of spin-resolved densities.
> (b) In the absence of an external magnetic field, does the Hohenberg-Kohn theorem still hold for a spin-polarized system?
> (c) Why is spin density functional theory essential for your ceria calculations?

> [!definition] Spin density
>
> $$ n(\mathbf{r}) = n(\mathbf{r}, \uparrow) + n(\mathbf{r}, \downarrow) \qquad s(\mathbf{r}) = n(\mathbf{r}, \uparrow) - n(\mathbf{r}, \downarrow) $$

These two equations decompose the electron population at each point in space into a charge channel and a magnetic channel. The first equation, $n(\mathbf{r}) = n(\mathbf{r},\uparrow) + n(\mathbf{r},\downarrow)$, is the total charge density: "how many electrons are here, regardless of spin?" It sums up-spin and down-spin contributions and is the quantity that determines electrostatic interactions and bonding. The second equation, $s(\mathbf{r}) = n(\mathbf{r},\uparrow) - n(\mathbf{r},\downarrow)$, is the magnetization density: "is there an imbalance between up-spin and down-spin electrons here?" Where $s(\mathbf{r}) > 0$, there are more up-spin electrons; where $s(\mathbf{r}) = 0$, the spin populations are balanced. Together, $n$ and $s$ carry the same information as the two spin-resolved densities $n(\mathbf{r},\uparrow)$ and $n(\mathbf{r},\downarrow)$, just rotated into sum-and-difference form.

In the absence of an external magnetic field, the original Hohenberg-Kohn theorem guarantees that the total density $n(\mathbf{r})$ alone is sufficient in principle. However, approximate functionals that depend on both $n$ and $s$ separately are far more accurate for spin-polarized systems because they can capture the *exchange splitting* between spin channels — the energy difference arising from the Pauli exclusion principle acting differently on majority and minority spins.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n(\mathbf{r}, \uparrow)$ | Scalar field | Å⁻³ | **Majority-spin density** | Density of electrons with spin up at $\mathbf{r}$. In VASP, extracted from spin-decomposed `CHGCAR`. |
| $n(\mathbf{r}, \downarrow)$ | Scalar field | Å⁻³ | **Minority-spin density** | Density of electrons with spin down at $\mathbf{r}$. |
| $n(\mathbf{r},\uparrow) + n(\mathbf{r},\downarrow)$ | Sum | Å⁻³ | **Total charge density (charge channel)** | Counts all electrons at $\mathbf{r}$ regardless of spin. Governs electrostatics and bonding. |
| $n(\mathbf{r},\uparrow) - n(\mathbf{r},\downarrow)$ | Difference | Å⁻³ | **Spin (magnetization) density (magnetic channel)** | Measures the local spin imbalance. Nonzero in magnetically ordered systems and for odd-electron systems. |

> **Connections Forward:** Every DFT+U calculation on ceria uses spin density functional theory. The AFM ordering you seed in Ce₇O₁₂ sets the initial $n(\mathbf{r},\uparrow)$ and $n(\mathbf{r},\downarrow)$ separately. The `ISPIN=2` tag in VASP activates this.

## 7. $V$-representability vs. $N$-representability

> [!question]
>
> (a) Define $V$-representable and $N$-representable densities.
> (b) Which is the more restrictive condition, and why does this matter for defining energy functionals?
> (c) How does the Levy-Lieb formulation resolve the $V$-representability problem?

> [!definition] $V$-representability and $N$-representability
>
> A density is **$V$-representable** if it is the ground-state density of some external potential $V_{\text{ext}}(\mathbf{r})$. A density is **$N$-representable** if it can be obtained from some antisymmetric $N$-electron wavefunction.

Think of the set of all "reasonable-looking" densities — non-negative functions that integrate to $N$ and have well-behaved gradients. $N$-representability asks: "can I find *any* antisymmetric wavefunction that produces this density?" The answer is almost always yes — the conditions are mild ($n(\mathbf{r}) \geq 0$ and $\int |\nabla n^{1/2}|^2 < \infty$), so the set of $N$-representable densities is large and permissive. $V$-representability asks a much harder question: "is this density the *ground state* of some local potential?" This is a far more restrictive condition — you are not just asking whether the density is physically realizable, but whether Nature could produce it as an equilibrium. There exist densities that look perfectly reasonable but are *not* the ground state of any local potential (for example, the spherically averaged density of an open-shell atom, or any excited-state density).

This distinction matters because the Hohenberg-Kohn functional $F_{\text{HK}}[n]$ is defined only for $V$-representable densities — if you feed it a non-$V$-representable density, the functional is undefined, which is a formal weakness. The Levy-Lieb constrained search formulation resolves this by defining $F_{\text{LL}}[n]$ for the larger set of $N$-representable densities. At the energy minimum — where the density *is* $V$-representable — the two functionals agree, so you get the same physics. But away from the minimum, during the variational search, $F_{\text{LL}}$ is better behaved because it is defined for a wider class of trial densities.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $V$-representable | Property of a density | — | **$V$-representable** | Density is the ground state of some $V_{\text{ext}}(\mathbf{r})$. More restrictive — many reasonable densities fail this test. |
| $N$-representable | Property of a density | — | **$N$-representable** | Density comes from some antisymmetric $N$-electron wavefunction. Less restrictive — requires only $n \geq 0$ and $\int \|\nabla n^{1/2}\|^2 < \infty$. |
| $\int \|\nabla n^{1/2}\|^2$ | Integral | Å⁻¹ | **Gradient-square integrability condition** | A regularity condition ensuring the density doesn't have pathological cusps or jumps. The von Weizsäcker kinetic energy $T_W[n]$ is proportional to this. |

> **Connections Forward:** The $V$-representability issue is sidestepped in practice by the Kohn-Sham construction (Ch 7), which generates densities from single-particle orbitals — these are automatically $V$-representable for the non-interacting system.

---

# Theoretical Foundations

## 8. Hohenberg-Kohn Theorem I — density determines potential (§6.3.1)

> [!question]
>
> (a) State Hohenberg-Kohn Theorem I precisely.
> (b) Sketch the proof by contradiction — what quantity leads to the contradictory inequality?
> (c) What assumption on the ground state is needed for the original proof, and how is this relaxed in the Levy-Lieb formulation?
> (d) The theorem says the density determines the potential. Why does this *not* immediately solve the electronic structure problem?

> [!theorem] Hohenberg-Kohn Theorem I (§6.3)
>
> For any system of interacting particles in an external potential $V_{\text{ext}}(\mathbf{r})$, the potential $V_{\text{ext}}(\mathbf{r})$ is determined uniquely, except for a constant, by the ground-state particle density $n_0(\mathbf{r})$.
>
> **Corollary:** Since the Hamiltonian is fully determined (up to a constant) by $n_0(\mathbf{r})$, all properties of the system — ground and excited states — are completely determined by the ground-state density alone.

The theorem establishes a one-to-one correspondence: $n_0(\mathbf{r}) \leftrightarrow V_{\text{ext}}(\mathbf{r})$. Read this as a logical chain: the density uniquely determines the external potential, which uniquely determines the Hamiltonian, which uniquely determines all wavefunctions (ground and excited), which determines every observable. That is, a single scalar function of three variables — the ground-state density — encodes everything about the quantum many-body system.

The proof is by contradiction and is built on the variational principle. Assume two different potentials $V_{\text{ext}}^{(1)}$ and $V_{\text{ext}}^{(2)}$ (differing by more than a constant) give the same ground-state density $n_0(\mathbf{r})$. They produce two different Hamiltonians with two different ground-state wavefunctions $\Psi^{(1)}$ and $\Psi^{(2)}$. Using $\Psi^{(2)}$ as a trial wavefunction for $\hat{H}^{(1)}$ gives $E^{(1)} < E^{(2)} + \int [V_{\text{ext}}^{(1)} - V_{\text{ext}}^{(2)}]\,n_0\,d^3r$. Repeating with indices swapped and adding the two inequalities gives the contradiction $E^{(1)} + E^{(2)} < E^{(1)} + E^{(2)}$. The key step is that the difference between the two Hamiltonians involves only $\int \Delta V_{\text{ext}} \cdot n_0\,d^3r$ — the bilinear coupling between potential and density — which is the structural reason the density has its privileged role.

Despite its power, the theorem provides no practical recipe. It says the density determines the potential — but given a density, you still have to solve the full many-body Schrödinger equation to find any property. The theorem is an existence proof, not a construction. The practical route comes from the Kohn-Sham construction in Chapter 7.

### Conditions

- Requires a nondegenerate ground state in the original proof (relaxed by Levy-Lieb).
- Assumes the external potentials differ by more than a constant.
- Valid for any interacting particle system, not just electrons.

### Practical Consequences

The theorem justifies the entire DFT enterprise: you are allowed to write every ground-state property as a functional of $n(\mathbf{r})$ alone. When you run a VASP calculation, the self-consistent density it converges to is, in principle, sufficient to determine everything about the electronic ground state.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $n_0(\mathbf{r})$ | Scalar field | Å⁻³ | **Ground-state density** | The density that uniquely determines $V_{\text{ext}}$ and hence all properties. The "basic variable" of DFT. |
| $V_{\text{ext}}(\mathbf{r})$ | Scalar field | Hartree | **External potential** | Determined (up to a constant) by $n_0$. Once known, the full Hamiltonian is fixed. |
| $n_0 \leftrightarrow V_{\text{ext}}$ | One-to-one mapping | — | **HK correspondence** | The central result: the density-potential map is invertible (up to a constant). |
| $E^{(1)} + E^{(2)} < E^{(1)} + E^{(2)}$ | Contradiction | — | **Proof by contradiction** | The absurd inequality obtained by assuming two different potentials give the same density. |

> **Connections Forward:** Foundation of all DFT. The practical realization is the Kohn-Sham construction (Ch 7). The theorem does NOT guarantee that approximate functionals will work — that is a separate question addressed in Chs 8–9.

## 9. Hohenberg-Kohn Theorem II — variational principle (§6.3.2)

> [!question]
>
> (a) State Hohenberg-Kohn Theorem II precisely.
> (b) What does this theorem tell you about trial densities that are not the ground-state density?
> (c) Why is this theorem essential for making DFT practical?

> [!theorem] Hohenberg-Kohn Theorem II (§6.3)
>
> A universal functional for the energy $E[n]$ can be defined, valid for any external potential $V_{\text{ext}}(\mathbf{r})$. For any particular $V_{\text{ext}}(\mathbf{r})$, the exact ground-state energy is the global minimum of this functional, and the density that minimizes the functional is the exact ground-state density $n_0(\mathbf{r})$.

Where Theorem I says "the density contains the information," Theorem II says "you can *find* the density by minimization." It provides the variational principle that makes DFT a usable theory: the ground-state density and energy are obtained by minimizing an energy functional over trial densities, just as in standard quantum mechanics you minimize $\langle \Psi | \hat{H} | \Psi \rangle$ over trial wavefunctions. Any trial density $\tilde{n}(\mathbf{r})$ gives an energy $E[\tilde{n}]$ that is an upper bound to the true ground-state energy — you can search for the minimum with confidence that you are approaching the answer from above.

The practical consequence is immediate: if you have a good approximate functional and a good way to minimize it, you can find the ground-state energy and density without ever confronting the $3N$-dimensional Schrödinger equation. This is what the Kohn-Sham self-consistency cycle does — it iteratively adjusts the density, re-evaluates the energy functional, and converges to the minimum.

### Conditions

- The minimization is restricted to allowed densities (in the HK formulation, $V$-representable; in the LL formulation, $N$-representable).
- The variational bound $E[\tilde{n}] \geq E_0$ is exact only if $E[n]$ is evaluated exactly. Approximate functionals do not, in general, provide rigorous upper bounds — they can overshoot or undershoot the true energy.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E[n]$ | Functional: $n \mapsto \mathbb{R}$ | Hartree | **Universal energy functional** | The total energy as a functional of density. Valid for any $V_{\text{ext}}$. |
| $\tilde{n}(\mathbf{r})$ | Trial density | Å⁻³ | **Trial density** | Any allowed density used in the variational search. Gives an upper bound: $E[\tilde{n}] \geq E_0$. |
| $n_0(\mathbf{r})$ | Ground-state density | Å⁻³ | **Minimizing density** | The unique density that achieves the global minimum of $E[n]$ for a given $V_{\text{ext}}$. |
| $E_0 = E[n_0]$ | Scalar | Hartree | **Exact ground-state energy** | The global minimum of the energy functional. |

> **Connections Forward:** This variational principle is what the Kohn-Sham self-consistency cycle (Ch 7) implements in practice — iteratively adjusting the density toward the minimum of the (approximate) energy functional.

## 10. Hohenberg-Kohn energy functional $E_{\text{HK}}[n]$ (Eq. 6.12)

> [!question]
>
> (a) Write the Hohenberg-Kohn total energy functional.
> (b) Which part of the functional is universal, and which part is system-specific?
> (c) Why is the nucleus-nucleus repulsion $E_{II}$ included even though it doesn't depend on the electron density?

> [!functional] Hohenberg-Kohn energy functional (Eq. 6.12)
>
> $$ E_{\text{HK}}[n] = F_{\text{HK}}[n] + \int d^3r \, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} $$

Read this as a three-part energy accounting for the total energy of the material.

The first term, $F_{\text{HK}}[n]$, is the *universal functional* — it contains all the internal energies of the electron system: the kinetic energy of all the electrons (how fast they are moving) and their mutual Coulomb repulsion (how much they push each other apart). It is "universal" because neither quantum kinetic energy nor Coulomb repulsion knows or cares what material you are studying — these operators are the same for hydrogen and for uranium. This is the unknown, difficult part — the "Holy Grail" of DFT.

The second term, $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$, is the *electron-nuclear interaction energy*. Read this integral as: "at every point in space, multiply the potential energy of an electron at that point ($V_{\text{ext}}$) by the number of electrons at that point ($n$), and sum over all space." This bilinear, multiplicative coupling — potential times density — is why the density has its special role: it is the simplest possible coupling between the system-specific part (the potential) and the electron distribution. This is the only system-specific piece of the energy.

The third term, $E_{II}$, is the classical Coulomb repulsion between the nuclei. It is a constant for fixed nuclear positions — it does not depend on the electron density at all and does not affect the electronic minimization. It is included for completeness so that $E_{\text{HK}}$ gives the total energy of the material, not just the electronic energy. In VASP, this is the `TEWEN` or ion-ion energy contribution.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $F_{\text{HK}}[n]$ | Functional: $n \mapsto \mathbb{R}$ | Hartree | **Universal functional** | All internal electron energies: kinetic + electron-electron interaction. Same for every material. Unknown exactly. |
| $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$ | Scalar | Hartree | **Electron-nuclear coupling energy** | The electrostatic attraction between electrons and nuclei. Bilinear in potential and density — this simple structure is why $n(\mathbf{r})$ is the "basic variable." System-specific. |
| $E_{II}$ | Constant | Hartree | **Ion-ion energy** | Classical Coulomb repulsion between nuclei. Independent of $n$ — a constant shift. In VASP, computed via Ewald summation. |
| $E_{\text{HK}}[n]$ | Functional: $n \mapsto \mathbb{R}$ | Hartree | **HK total energy functional** | The complete energy of the material: electrons, nuclei, and their interactions. Its minimum over allowed densities gives the exact ground-state energy. |

> **Connections Forward:** In the Kohn-Sham construction (Ch 7), $F_{\text{HK}}[n]$ is decomposed as $T_s[n] + E_{\text{Hartree}}[n] + E_{\text{xc}}[n]$, which makes $E_{\text{HK}}$ computable. The VASP total energy in OSZICAR is this functional evaluated at the converged density.

## 11. Universal functional $F_{\text{HK}}[n]$ (Eq. 6.13)

> [!question]
>
> (a) Write $F_{\text{HK}}[n]$ in terms of kinetic and interaction energies.
> (b) Why is this functional called "universal"?
> (c) If you could evaluate $F_{\text{HK}}[n]$ exactly, would you need to know anything about which material you are studying?

> [!functional] Universal Hohenberg-Kohn functional (Eq. 6.13)
>
> $$ F_{\text{HK}}[n] = T[n] + E_{\text{int}}[n] $$

This equation says: "the internal energy of the electron system is the sum of their kinetic energy and their mutual repulsion, and both can be written as functionals of the density alone." Read the two pieces:

$T[n]$ is the exact kinetic energy of the interacting $N$-electron system, expressed as a functional of the density. This is *not* simply $\sum_i p_i^2/(2m)$ evaluated using the density — that would require knowledge of the individual electron momenta. Rather, $T[n]$ is defined implicitly through the Hohenberg-Kohn theorem: given $n$, the potential is determined, the Hamiltonian is determined, the ground-state wavefunction is determined, and the kinetic energy expectation value $\langle \Psi | \hat{T} | \Psi \rangle$ is determined. No one knows how to write $T[n]$ as an explicit formula of $n(\mathbf{r})$ for more than one electron.

$E_{\text{int}}[n]$ is the exact electron-electron Coulomb interaction energy. Like $T[n]$, it is defined implicitly through the density → potential → wavefunction → expectation value chain. It includes the Hartree energy (classical mean-field repulsion) plus all quantum corrections: exchange (Pauli avoidance), correlation (Coulomb avoidance beyond mean field), and the self-interaction correction.

The functional is "universal" because neither the kinetic energy operator $\hat{T}$ nor the Coulomb interaction $\hat{V}_{\text{int}}$ depends on which material you are studying — these operators have the same form for every electron system. The external potential $V_{\text{ext}}$, which is the only system-specific piece, has been separated out into the second term of $E_{\text{HK}}$. If you could evaluate $F_{\text{HK}}[n]$ exactly, you would have a single formula that solves *every* electronic structure problem — you would only need to specify the external potential and minimize.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $T[n]$ | Functional | Hartree | **Interacting kinetic energy functional** | The exact kinetic energy of the correlated $N$-electron system, as an implicit functional of $n$. Not computable without solving the many-body problem. |
| $E_{\text{int}}[n]$ | Functional | Hartree | **Electron-electron interaction functional** | The exact Coulomb repulsion energy, including Hartree, exchange, correlation, and self-interaction correction. Also implicit. |
| $F_{\text{HK}}[n] = T[n] + E_{\text{int}}[n]$ | Functional | Hartree | **Universal functional** | The total internal energy of the electron system. "Universal" because it is independent of which material you study. |

> **Connections Forward:** In the Kohn-Sham construction (Ch 7), $F_{\text{HK}}[n]$ is decomposed into $T_s[n]$ (non-interacting kinetic energy, computed from orbitals) + $E_{\text{Hartree}}[n]$ + $E_{\text{xc}}[n]$. This decomposition is the key insight that makes DFT practical — it isolates the unknown part into $E_{\text{xc}}$, which is a small fraction of the total energy.

## 12. Levy-Lieb constrained search functional $F_{\text{LL}}[n]$ (Eq. 6.18)

> [!question]
>
> (a) Write the Levy-Lieb functional and explain the constrained minimization.
> (b) What does "$\min_{\Psi \to n(\mathbf{r})}$" mean physically?
> (c) How does $F_{\text{LL}}$ differ from $F_{\text{HK}}$ in terms of the domain of allowed densities?
> (d) At the ground-state density, how do $F_{\text{LL}}$ and $F_{\text{HK}}$ compare?

> [!functional] Levy-Lieb constrained search functional (Eq. 6.18)
>
> $$ F_{\text{LL}}[n] = \min_{\Psi \to n(\mathbf{r})} \langle \Psi | \hat{T} + \hat{V}_{\text{int}} | \Psi \rangle $$

Read this equation as a two-step procedure. The notation $\min_{\Psi \to n(\mathbf{r})}$ means: "consider *all* antisymmetric $N$-electron wavefunctions $\Psi$ that produce the density $n(\mathbf{r})$" — this is the constraint, and there are infinitely many such wavefunctions for any given density. Among all of these, pick the one that minimizes $\langle \Psi | \hat{T} + \hat{V}_{\text{int}} | \Psi \rangle$ — the sum of kinetic and interaction energies. That minimum value *is* $F_{\text{LL}}[n]$.

This definition is more intuitive and more powerful than $F_{\text{HK}}[n]$ in three ways. First, it gives an *operational* definition: in principle, you could compute $F_{\text{LL}}[n]$ by searching over wavefunctions, even if you cannot do so in practice. Second, it is defined for any $N$-representable density (a much larger class than $V$-representable densities), so the variational search over trial densities has a bigger, better-behaved domain. Third, it naturally handles degenerate ground states — you simply search over all wavefunctions, including the degenerate ones, and take the minimum.

At the actual ground-state density $n_0(\mathbf{r})$, the constrained search automatically selects the true ground-state wavefunction $\Psi_0$, and $F_{\text{LL}}[n_0] = F_{\text{HK}}[n_0]$. The two functionals agree at the minimum — they lead to the same physics — but $F_{\text{LL}}$ is the better-defined object away from the minimum.

The constrained search also provides the deepest insight into what approximate functionals are doing: they are trying to approximate the result of this minimization over wavefunctions without actually performing it.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\min_{\Psi \to n}$ | Constrained minimization | — | **Constrained search** | Search over all antisymmetric $\Psi$ with density $n(\mathbf{r})$ and select the one with the lowest internal energy. |
| $\langle \Psi \| \hat{T} \| \Psi \rangle$ | Expectation value | Hartree | **Kinetic energy of trial $\Psi$** | The kinetic energy of whichever wavefunction is being tested in the search. |
| $\langle \Psi \| \hat{V}_{\text{int}} \| \Psi \rangle$ | Expectation value | Hartree | **Interaction energy of trial $\Psi$** | The electron-electron repulsion energy of whichever wavefunction is being tested. |
| $\langle \Psi \| \hat{T} + \hat{V}_{\text{int}} \| \Psi \rangle$ | Expectation value | Hartree | **Total internal energy of trial $\Psi$** | The objective function of the constrained search: kinetic + interaction, to be minimized. |
| $F_{\text{LL}}[n]$ | Functional: $n \mapsto \mathbb{R}$ | Hartree | **Levy-Lieb functional** | The minimum internal energy achievable by any wavefunction that yields density $n$. Defined for all $N$-representable densities. |

> **Connections Forward:** The constrained search viewpoint extends to the Kohn-Sham system (Ch 7), where one searches over Slater determinants rather than arbitrary wavefunctions. This defines the non-interacting kinetic energy $T_s[n]$ and isolates the exchange-correlation energy.

## 13. Mermin finite-temperature grand potential functional (§6.5.1, Eqs. 6.20–6.22)

> [!question]
>
> (a) Write the Mermin grand potential functional.
> (b) What additional properties beyond ground-state energy does the Mermin theorem guarantee are functionals of the equilibrium density?
> (c) Why is the Mermin functional much harder to approximate in practice than the Hohenberg-Kohn functional?

> [!functional] Mermin grand potential functional (Eq. 6.20)
>
> $$ \Omega[\hat{\rho}] = \text{Tr}\, \hat{\rho}\left[(\hat{H} - \mu\hat{N}) + \frac{1}{\beta}\ln\hat{\rho}\right] $$

Read this functional as three competing contributions to the grand potential of a thermal ensemble. The trace $\text{Tr}$ means "sum over all quantum states" — this is a statistical average, not a single-state expectation value.

Inside the brackets, $\hat{H} - \mu\hat{N}$ is the *grand canonical energy*: the Hamiltonian minus the chemical potential times the number operator. The $\hat{H}$ term wants to minimize the energy (favoring low-energy states), while $-\mu\hat{N}$ penalizes deviations from the target average particle number. The ratio $\hat{H} - \mu\hat{N}$ determines which states are thermodynamically favorable.

The term $\frac{1}{\beta}\ln\hat{\rho}$ is the *entropy contribution* (since $S = -k_B \text{Tr}\,\hat{\rho}\ln\hat{\rho}$, this term equals $-TS/k_B T = -TS \cdot \beta$, i.e., the entropic free energy). It favors disorder — at higher temperature ($\beta$ small), the entropy term dominates and many states become populated. At low temperature ($\beta$ large), the entropy term becomes negligible and the functional reduces to the ground-state energy.

The Mermin theorem says that the equilibrium density at temperature $T$ uniquely determines all thermal equilibrium properties — including entropy and specific heat — just as the Hohenberg-Kohn theorem says the ground-state density determines all ground-state properties. This is a stronger statement: thermodynamic properties involving excited states (like specific heat) are determined by the equilibrium density.

In practice, the Mermin functional has not been widely used because constructing approximate functionals for the entropy is far harder than for the ground-state energy. The entropy involves weighted sums over excited states, which requires knowledge of the excitation spectrum — precisely the information that ground-state DFT sidesteps.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\hat{\rho}$ | Density matrix (operator) | — | **Trial density matrix** | A statistical ensemble state. The variational search minimizes $\Omega$ over all valid $\hat{\rho}$. |
| $\text{Tr}\,\hat{\rho}\,\hat{H}$ | Scalar | Hartree | **Average energy** | The thermal average of the total energy over the ensemble. Favors populating low-energy states. |
| $-\mu\,\text{Tr}\,\hat{\rho}\,\hat{N}$ | Scalar | Hartree | **Chemical potential term** | Penalizes deviation from the target average electron number. Controls how many electrons the system has on average. |
| $\frac{1}{\beta}\text{Tr}\,\hat{\rho}\ln\hat{\rho}$ | Scalar | Hartree | **Entropic free energy (= $-TS$)** | Favors disorder; dominant at high temperature. This is what makes the Mermin functional so much harder to approximate than the ground-state HK functional. |
| $\beta = 1/(k_BT)$ | Scalar | Hartree⁻¹ | **Inverse temperature** | Controls the balance between energy and entropy. $\beta \to \infty$ recovers the ground state. |
| $\mu$ | Scalar | Hartree | **Chemical potential** | Controls the average electron number in the grand canonical ensemble. |
| $\hat{\rho}_0$ | Density matrix | — | **Equilibrium density matrix** | The grand canonical state $\hat{\rho}_0 = e^{-\beta(\hat{H}-\mu\hat{N})}/\text{Tr}\,e^{-\beta(\hat{H}-\mu\hat{N})}$ that minimizes $\Omega$. |

> **Connections Forward:** Your TTM-MD simulations involve extremely high electronic temperatures during the thermal spike. The Mermin functional is the formal justification for finite-temperature DFT (Fermi-Dirac smearing of Kohn-Sham occupations in VASP, `ISMEAR=-1`).

## 14. Spin density functional theory (§6.5, Eq. 6.19)

> [!question]
>
> (a) Write the spin density functional energy.
> (b) In what sense is spin DFT more general than the original HK theorems?
> (c) When is spin DFT *necessary* versus merely convenient?

> [!theorem] Spin density functional theory (Eq. 6.19)
>
> $$ E = E_{\text{HK}}[n, s] \equiv E'_{\text{HK}}[n(\mathbf{r},\sigma)] $$
> where the functional depends on both the total density $n(\mathbf{r})$ and the spin density $s(\mathbf{r})$, or equivalently on the spin-resolved densities $n(\mathbf{r},\uparrow)$ and $n(\mathbf{r},\downarrow)$.

The two equivalent notations express the same idea in different coordinates. In the $[n, s]$ form, the energy depends on the total charge density (how many electrons are here?) and the spin density (is there a net spin?). In the $[n(\mathbf{r},\sigma)]$ form, the energy depends on the up-spin and down-spin densities separately. These are related by $n = n_\uparrow + n_\downarrow$ and $s = n_\uparrow - n_\downarrow$, so the two forms carry identical information.

The generalization follows the same logic as the original Hohenberg-Kohn theorems, but now the bilinear coupling includes a spin-dependent Zeeman term in addition to $\int V_{\text{ext}}\,n\,d^3r$. Each spin-dependent external field couples to its corresponding density, so both $n$ and $s$ become "basic variables."

Even without an external magnetic field, the lowest-energy solution may be spin-polarized — $n(\mathbf{r},\uparrow) \neq n(\mathbf{r},\downarrow)$ — which is the DFT analog of the broken-symmetry solution in unrestricted Hartree-Fock. In such cases, the original HK theorem technically still guarantees that $n(\mathbf{r})$ alone is sufficient, but in practice approximate spin-dependent functionals are far more accurate because they can describe the *exchange splitting*: the energy difference between majority and minority spin channels that arises from the Pauli exclusion principle acting differently in each channel.

### Practical Consequences

Spin DFT is not optional for your research. Every DFT+U calculation on ceria phases with Ce³⁺ (which carries a 4f¹ magnetic moment) requires `ISPIN=2`. The choice of magnetic ordering (FM, AFM, or nonmagnetic) determines the initial spin densities and can lead to different SCF solutions — the multiple minima you encounter in Ce₇O₁₂ are a direct consequence of the spin degree of freedom.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E_{\text{HK}}[n, s]$ | Functional of two fields | Hartree | **Spin-dependent HK functional** | Total energy depending on both charge and spin channels. Needed when spin polarization matters. |
| $E'_{\text{HK}}[n(\mathbf{r},\sigma)]$ | Functional of spin-resolved densities | Hartree | **Equivalent spin-resolved form** | Same physics, different parametrization: uses $n_\uparrow$ and $n_\downarrow$ directly instead of $n$ and $s$. |

> **Connections Forward:** Spin-dependent exchange-correlation functionals (LSDA, spin-polarized GGA) are developed in Chs 8–9. The spin-dependent Kohn-Sham equations (Ch 7) have separate effective potentials for each spin channel.

## 15. Nonanalyticity of the exact functional (§6.7)

> [!question]
>
> (a) Why must the exact kinetic energy functional have discontinuous derivatives at integer electron numbers?
> (b) What does this imply about the difficulty of constructing approximate functionals for insulators?
> (c) How is the kinetic energy actually evaluated in the Kohn-Sham approach, and why does this help?

> [!theorem] Nonanalyticity of the exact functional (§6.7)
>
> The exact kinetic energy functional $T[n]$ — and by the virial theorem, all parts of the exact functional — must have derivatives that are discontinuous at integer occupation numbers.

This result reveals a deep structural property of the exact functional and explains why orbital-free DFT fails fundamentally while the Kohn-Sham construction succeeds.

Consider what happens when you add electrons one at a time to a finite system. Each new electron fills the next available state, which generally has a different energy from the previous one. At each integer electron number $N$, the cost of adding the next electron — the functional derivative $\delta E/\delta n$ — jumps discontinuously. This jump is called the *derivative discontinuity*. It is not a small correction: for insulators, the size of the jump is related to the band gap. The derivative discontinuity is what separates metals (no gap, continuous derivative) from insulators (gap, discontinuous derivative).

Now, if you try to write $T[n]$ as an explicit, smooth, analytic functional of the density — any combination of $n$, $\nabla n$, $\nabla^2 n$, etc. — the result will be a smooth function that cannot produce discontinuous derivatives. Such a functional will systematically miss the derivative discontinuity and therefore underestimate band gaps. This is exactly what happens with Thomas-Fermi and its gradient corrections: smooth functionals of the density cannot describe the metal-insulator distinction.

The Kohn-Sham approach sidesteps this by evaluating the dominant part of the kinetic energy from *orbitals* rather than directly from the density. The orbitals have discrete occupation numbers (0 or 1 at zero temperature), and the kinetic energy $T_s = \sum_i f_i \langle \phi_i | -\frac{\hbar^2}{2m}\nabla^2 | \phi_i \rangle$ naturally produces the discontinuity when an orbital crosses the Fermi level. This is the fundamental reason why Kohn-Sham DFT works and orbital-free DFT does not.

### Practical Consequences

This nonanalyticity is the root cause of the band-gap problem in DFT: standard LDA and GGA functionals are smooth functions of the density and cannot reproduce the derivative discontinuity. The systematic underestimation of the CeO₂ band gap (and the tendency to predict metallic behavior in reduced ceria) traces back to this limitation. Hybrid functionals and DFT+U partially restore the derivative discontinuity by adding orbital-dependent terms.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\delta E / \delta n$ | Functional derivative | Hartree | **Energy response to density change** | How much the energy changes per unit change in density. Must be discontinuous at integer $N$ for the exact functional. |
| $\Delta_{\text{xc}}$ | Scalar | Hartree (or eV) | **Derivative discontinuity** | The jump in $\delta E/\delta n$ at integer electron number. Related to the band gap; absent in LDA and GGA. |

> **Connections Forward:** The band-gap problem is addressed by hybrid functionals and DFT+U (Ch 9), both of which add orbital-dependent terms that partially restore the derivative discontinuity.

---

# Approximations & Their Failures

## 16. Thomas-Fermi-Dirac energy functional (§6.2, Eq. 6.1)

> [!question]
>
> (a) Write the Thomas-Fermi-Dirac energy functional and identify each term.
> (b) What physical approximation is made for the kinetic energy?
> (c) Name two essential features of electronic structure that TF-Dirac gets completely wrong.
> (d) Despite its failures, why is the TF model important historically and conceptually?

> [!approximation] Thomas-Fermi-Dirac energy functional (Eq. 6.1)
>
> $$ E_{\text{TF}}[n] = C_1 \int d^3r \, n(\mathbf{r})^{5/3} + \int d^3r \, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + C_2 \int d^3r \, n(\mathbf{r})^{4/3} + \frac{1}{2}\int d^3r\,d^3r' \frac{n(\mathbf{r})\,n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} $$
>
> with $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$ and $C_2 = -\frac{3}{4}(3/\pi)^{1/3}$.

Read this as a four-term energy budget where each term represents a distinct physical contribution, all expressed as explicit functionals of the density.

The first term, $C_1 \int n^{5/3}\,d^3r$, is the *local kinetic energy*. It approximates the kinetic energy at each point in space by pretending that the electrons near $\mathbf{r}$ behave like a uniform electron gas with the local density $n(\mathbf{r})$. The $5/3$ power law comes from the Fermi gas formula: in a uniform gas, the kinetic energy per unit volume scales as $n^{5/3}$ because the Fermi momentum goes as $n^{1/3}$ and the kinetic energy per electron goes as $p_F^2 \propto n^{2/3}$, so the kinetic energy density is $n \cdot n^{2/3} = n^{5/3}$. This approximation is the ancestor of the "local density" idea in modern LDA — but applied to the kinetic energy, where it fails badly.

The second term, $\int V_{\text{ext}}\,n\,d^3r$, is the *electron-nuclear interaction energy* — the same bilinear coupling that appears in the exact HK functional. This term is treated exactly.

The third term, $C_2 \int n^{4/3}\,d^3r$, is the *Dirac local exchange energy*. It approximates the exchange energy using the same local-density philosophy: at each point, exchange is computed as if the electrons formed a uniform gas of density $n(\mathbf{r})$. The $4/3$ power law comes from the exchange energy of a uniform gas, where the exchange hole has a size proportional to $n^{-1/3}$ and the exchange energy per electron goes as $n^{1/3}$. The negative coefficient $C_2$ reflects that exchange always *lowers* the energy — same-spin electrons avoid each other, reducing the Coulomb repulsion.

The fourth term, $\frac{1}{2}\int n(\mathbf{r})\,n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|\,d^3r\,d^3r'$, is the *Hartree energy* — the classical electrostatic self-energy of the charge cloud (Entry 3). This is also treated exactly.

Correlation is neglected entirely.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $C_1 \int n^{5/3}\,d^3r$ | Functional | Hartree | **Local kinetic energy** | Kinetic energy approximated by the uniform-gas result at the local density. The $n^{5/3}$ power law comes from the Fermi gas kinetic energy density. Fails wherever the density varies rapidly. |
| $\int V_{\text{ext}}\,n\,d^3r$ | Functional | Hartree | **Electron-nuclear energy** | Exact bilinear coupling. The only system-specific term. |
| $C_2 \int n^{4/3}\,d^3r$ | Functional | Hartree | **Dirac local exchange energy** | Exchange approximated by the uniform-gas result. The $n^{4/3}$ power law reflects the exchange-hole size in a uniform gas. Always negative (exchange lowers energy). |
| $\frac{1}{2}\int n\,n'/\|\mathbf{r}-\mathbf{r}'\|\,d^3r\,d^3r'$ | Functional | Hartree | **Hartree energy** | Classical mean-field Coulomb repulsion. Exact but includes self-interaction. |
| $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$ | Constant | Hartree·Bohr² | **Thomas-Fermi kinetic prefactor** | Sets the energy scale for the local kinetic energy approximation. |
| $C_2 = -\frac{3}{4}(3/\pi)^{1/3}$ | Constant | Hartree·Bohr | **Dirac exchange prefactor** | Sets the energy scale for local exchange. Negative because exchange lowers the energy. |

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Atoms | No shell structure | Local kinetic energy approximation treats electrons as a smooth gas — cannot capture the quantum interference (orbital nodes) responsible for shell structure. |
| Molecules | No binding — molecules do not form | Chemical bonding requires nonlocal quantum effects (interference between orbitals on different atoms) absent in the local kinetic energy approximation. |
| All systems | Poor total energies | Correlation neglected entirely; kinetic energy too crude; exchange only approximate. |

### Practical Consequences

You will never use Thomas-Fermi in production calculations. Its importance is conceptual: it introduces the density as the central variable and the local-density idea, both of which survive in modern DFT through the Kohn-Sham construction and LDA. The Kohn-Sham approach rescues DFT from the Thomas-Fermi disaster by computing the kinetic energy from orbitals and applying the local-density approximation only to exchange and correlation, where it works much better.

> **Connections Forward:** The $n^{5/3}$ kinetic energy term reappears as part of the LDA exchange-correlation functional (Ch 8, §8.3). The Dirac exchange formula $C_2 \int n^{4/3}\,d^3r$ is the starting point for the local spin density approximation (LSDA).

## 17. Weizsäcker gradient correction (§6.2)

> [!question]
>
> (a) Write the Weizsäcker correction to the Thomas-Fermi kinetic energy.
> (b) What physical effect does the gradient term capture that the local approximation misses?
> (c) How does this relate to the gradient corrections in modern GGA functionals?

> [!approximation] Weizsäcker gradient correction (§6.2)
>
> $$ T_W[n] = \frac{1}{4}\int d^3r \, \frac{|\nabla n(\mathbf{r})|^2}{n(\mathbf{r})} $$

Read this integrand as a ratio that measures how rapidly the density varies *relative to* its local value. The numerator $|\nabla n|^2$ is the squared gradient of the density — it is large wherever the density is changing rapidly (near nuclei, at the edges of atoms, at surfaces). The denominator $n(\mathbf{r})$ normalizes by the local density, so the ratio $|\nabla n|^2/n$ is a dimensionless-like measure of the *relative* rate of change. In regions where the density is nearly uniform (bulk of a nearly-free-electron metal), $|\nabla n|$ is small and the Weizsäcker correction is negligible — the Thomas-Fermi local approximation is adequate. Near nuclei and at atomic surfaces, where the density varies over a few Bohr radii, the gradient is large and the correction is essential.

The prefactor $\frac{1}{4}$ makes this term equal to the exact kinetic energy of a system of bosons with density $n(\mathbf{r})$ (or equivalently, of a single electron). For fermions, the true kinetic energy is always higher — the Pauli exclusion principle forces electrons into higher-momentum states, increasing the kinetic energy beyond the Weizsäcker value. This means $T_W$ is a lower bound on the true kinetic energy for any fermionic system.

The conceptual importance of the Weizsäcker term extends far beyond the Thomas-Fermi model. It demonstrates that information about the *spatial variation* of the density (not just its local value) improves the energy estimate. This is exactly the idea behind the generalized gradient approximation (GGA) in modern DFT: LDA uses only $n(\mathbf{r})$, while GGA adds dependence on $|\nabla n(\mathbf{r})|$ to improve the exchange-correlation functional. The Weizsäcker term is the conceptual ancestor of the GGA enhancement factor $F_{\text{xc}}(n, |\nabla n|)$ in Chapter 8.

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $\|\nabla n(\mathbf{r})\|^2$ | Scalar field | Bohr⁻⁸ (in 3D, density in Bohr⁻³) | **Squared density gradient** | Measures how rapidly the density is changing at each point. Large near nuclei and at atomic surfaces. |
| $n(\mathbf{r})$ (in denominator) | Scalar field | Bohr⁻³ | **Local density (normalizer)** | Divides out the absolute density so that the ratio measures the *relative* rate of change. |
| $\|\nabla n\|^2 / n$ | Scalar field | Bohr⁻⁵ | **Reduced density gradient (squared, unnormalized)** | A measure of density inhomogeneity. Where this is large, the local (Thomas-Fermi) approximation fails and gradient corrections matter. |
| $T_W[n]$ | Functional | Hartree | **Weizsäcker kinetic energy** | Gradient correction to the local kinetic energy. Exact for one electron or bosons. A lower bound for fermions. Ancestor of all GGA corrections. |

> **Connections Forward:** The idea of improving a local approximation with gradient information is the conceptual basis for GGA functionals (Ch 8, §8.5), which add gradient corrections to the *exchange-correlation* energy rather than the kinetic energy.
