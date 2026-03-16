# Adiabatic approximation

**Adiabatic approximation**. See *Born-Oppenheimer approximation*. The term "adiabatic" in this context means that as the nuclei move, the electrons always occupy the ground state corresponding to the current nuclear positions — they readjust instantly to each new configuration without ever being excited to higher states. The ground state itself changes continuously as the nuclei drift, but the electrons follow it perfectly with no lag and no transitions. Not to be confused with "adiabatic connection," which is a different use of the same word.

# Adiabatic connection

**Adiabatic connection**. A thought experiment in which you imagine a dial $\lambda$ that controls the strength of the electron-electron repulsion: at $\lambda = 0$ the electrons don't interact at all (the Kohn-Sham system, which you can solve exactly), and at $\lambda = 1$ they repel each other with full Coulomb strength (the real physical system). As you slowly turn the dial from 0 to 1, the system is assumed to stay in its ground state at every setting — "adiabatic" in the same sense as the Born-Oppenheimer approximation (no transitions). The total energy change accumulated along the way is given by the integral $\Delta E = \int_0^1 d\lambda\,\langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$, which is the coupling-constant integration idea from Equation Index Entry 23 applied specifically to the interaction strength. This is how the ==exchange-correlation energy== is formally defined in DFT: it is the integral over $\lambda$ of the exchange-correlation hole's contribution at each coupling strength. The intermediate values of $\lambda$ (between 0 and 1) don't correspond to any real physical system, but they provide the mathematical bridge between the solvable non-interacting problem and the real interacting one.

# Antisymmetric wavefunction

**Antisymmetric wavefunction**. A many-body wavefunction $\Psi(\mathbf{r}_1, \mathbf{r}_2, \ldots, \mathbf{r}_N)$ that changes sign when any two electron coordinates are exchanged: $\Psi(\ldots, \mathbf{r}_i, \ldots, \mathbf{r}_j, \ldots) = -\Psi(\ldots, \mathbf{r}_j, \ldots, \mathbf{r}_i, \ldots)$. This is the requirement of Fermi-Dirac statistics for electrons and is the mathematical expression of the Pauli exclusion principle. The simplest antisymmetric wavefunction is a Slater determinant.

# Born-Oppenheimer approximation

**Born-Oppenheimer approximation**. The approximation that the nuclear kinetic energy can be neglected, so that nuclear positions $\{\mathbf{R}_I\}$ enter the electronic Hamiltonian as fixed parameters rather than dynamical variables. Justified by the small electron-to-nuclear mass ratio $m_e/M_I \ll 1$: electrons adjust instantaneously to nuclear motion. The electronic energy $E(\{\mathbf{R}_I\})$ then defines a potential energy surface on which the nuclei move. Excellent for structural properties, lattice dynamics, and most ground-state calculations. Breaks down when electron-phonon coupling is strong (metals near phase transitions, polarons, superconductivity) or when electronic states become degenerate (conical intersections).

# Chemical potential

**Chemical potential** ($\mu$). The energy cost of adding one more electron to the system. At zero temperature it equals the ==Fermi energy==: imagine filling energy levels from the bottom up, dropping electrons into the lowest available state one at a time (two per level, one per spin). The Fermi energy is the energy of the last electron that fit — the waterline of the electron sea. Everything below is occupied, everything above is empty, and $\mu$ sits right at that boundary. At finite temperature, the sharp waterline smears out over a range $\sim k_BT$: states just below $\mu$ become partially empty and states just above become partially filled, with the occupations given by the Fermi-Dirac distribution $f_i^\sigma$. The chemical potential is then defined implicitly by the requirement that the total number of electrons is conserved, $\sum_{i,\sigma} f_i^\sigma = N$, which may shift $\mu$ slightly from its $T = 0$ value. In VASP, $\mu$ appears as `E-fermi` in the OUTCAR file.

# Classical Coulomb energy

**Classical Coulomb energy** ($E^{\text{CC}}$). The combination of all three classical electrostatic terms — electron-electron repulsion ($E_{\text{Hartree}}$), electron-nuclear attraction ($\int V_{\text{ext}}\,n\,d^3r$), and nuclear-nuclear repulsion ($E_{II}$) — grouped together because the group is electrically neutral: $E^{\text{CC}} = E_{\text{Hartree}} + \int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r + E_{II}$. The grouping matters because in a periodic crystal each individual term is a Coulomb sum over infinitely many charges, and the Coulomb interaction falls off so slowly ($1/r$) that these sums diverge to $\pm\infty$ individually — the electron-electron and nuclear-nuclear terms are each positive infinity, the electron-nuclear term is negative infinity. But because the total charge is zero (electrons + nuclei = neutral), the infinities cancel exactly when the three terms are summed, leaving a finite, well-defined energy. ==Ewald summation== is the mathematical technique that carries out this cancellation efficiently in practice, splitting the sum into a short-range part in real space and a long-range part in reciprocal space (Equation Index Entry 26).

# Correlation energy

**Correlation energy** ($E_c$). The ==Pauli exclusion principle== requires that same-spin electrons have zero probability of occupying the same point in space — this is the exchange effect (glossary: *Exchange energy*), and Hartree-Fock captures it exactly. But the Pauli principle says nothing about opposite-spin pairs: in a Hartree-Fock calculation, an up-spin and a down-spin electron still have a nonzero probability of being found at the same point. Correlation energy is the additional energy lowering gained when the wavefunction adjusts to reduce the probability of *any* two electrons — regardless of spin — being close together. Correlation is the reduction in electron-electron repulsion gained when the wavefunction adjusts to keep *all* electron pairs — regardless of spin — farther apart than the single-determinant (Hartree-Fock) wavefunction predicts. Formally, $E_c = E_{\text{exact}} - E_{\text{HF}}$: it is everything the best single Slater determinant misses, and it is always negative because the true ground state is always lower in energy than the HF approximation. Unlike exchange, which is purely a potential-energy effect (reduced Coulomb repulsion from the exchange hole), correlation has both a potential-energy piece (further reduction in repulsion from the ==correlation hole==) and a kinetic-energy piece (the correlated wavefunction has different curvature than the HF wavefunction, changing the kinetic energy). This dual nature makes $E_c$ much harder to compute or approximate than exchange — it is the central challenge of electronic structure theory and the reason DFT exchange-correlation functionals exist.

# Correlation hole

**Correlation hole** ($n_c$). The further rearrangement of electron density around an electron due to Coulomb repulsion, on top of the depletion already caused by the ==exchange hole== (which handles same-spin avoidance from the Pauli principle). The correlation hole primarily affects opposite-spin pairs, since same-spin electrons are already kept apart by exchange. Close to the reference electron, the correlation hole is negative — meaning the true electron density is even lower there than the exchange hole alone would predict, because Coulomb repulsion pushes opposite-spin electrons away. At larger distances, the correlation hole is positive — the density displaced from nearby has to go somewhere, so it accumulates farther out. These positive and negative regions cancel exactly: the correlation hole integrates to zero, because it is not removing any total charge (the exchange hole already accounts for exactly one missing electron), only redistributing where the remaining density sits. Formally it is defined as the difference $n_c = n_{\text{xc}} - n_x$ between the full exchange-correlation hole and the exchange-only hole.

# Coupling constant integration

**Coupling constant integration**. The technique of computing energy differences by integrating the generalized force theorem $\partial E/\partial\lambda = \langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$ over a continuous parameter $\lambda$. When $\lambda$ scales the electron-electron interaction from 0 to 1, this provides the adiabatic connection formula for the exchange-correlation energy.

# Density matrix

**Density matrix** ($\hat{\rho}$). A wavefunction describes a system in a single, definite quantum state. But at finite temperature, the system is not in any one state — it occupies many different states, each with a probability that depends on the temperature. The density matrix is the generalization of the wavefunction that handles this situation: it carries the full set of probabilistic weights (which states the system might be in, and with what likelihood), so that ==expectation values== can still be computed as $\langle\hat{O}\rangle = \text{Tr}(\hat{\rho}\hat{O})$ without having to specify a single wavefunction. At thermal equilibrium, the many-body density matrix takes the Boltzmann form $\hat{\rho} = \frac{1}{Z}e^{-\beta\hat{H}}$, which assigns each energy eigenstate a weight proportional to $e^{-\beta E}$ — low-energy states are more probable, and temperature controls how steeply the weights fall off (Equation Index Entry 24). There is also a single-body density matrix $\hat{\rho} = \sum_i |\psi_i^\sigma\rangle f_i^\sigma \langle\psi_i^\sigma|$, which contains more information than the electron density alone: its diagonal elements ($\mathbf{r} = \mathbf{r}'$) give the density $n(\mathbf{r})$, but its off-diagonal elements ($\mathbf{r} \neq \mathbf{r}'$) describe how the quantum state at one point in space is connected to the state at another point — this off-diagonal information is what determines the kinetic energy (which involves derivatives, requiring knowledge of how the wavefunction varies between nearby points) and the exchange energy (which involves orbital overlap between two different points).

| **Symbol** | **Name** | **Description** |
|---|---|---|
| $\hat{\rho}$ | **Density matrix** | The operator encoding the statistical state of the system. Replaces the wavefunction when the system is in a mixture of states rather than a single definite state. |
| $Z$ | **Partition function** | The normalization constant $Z = \text{Tr}(e^{-\beta\hat{H}})$ that ensures probabilities sum to 1. |
| $\beta$ | **Inverse temperature** | $\beta = 1/k_BT$. Large $\beta$ (low temperature) concentrates weight on the lowest-energy states; small $\beta$ (high temperature) spreads weight more evenly. |
| $e^{-\beta\hat{H}}$ | **Boltzmann operator** | Assigns each energy eigenstate $|n\rangle$ a weight $e^{-\beta E_n}$. This is the quantum generalization of the classical Boltzmann factor. |
| $\langle\hat{O}\rangle = \text{Tr}(\hat{\rho}\hat{O})$ | **Expectation value rule** | The generalization of the bra-operator-ket sandwich $\langle\Psi\lvert\hat{O}\rvert\Psi\rangle$ to the case where the system is in a statistical mixture of states rather than a single wavefunction. Multiply the density matrix by the operator and sum the diagonal elements — this automatically averages over all the states in the mixture, weighted by their probabilities. |
| $\text{Tr}$ | **Trace** | Sum over all diagonal matrix elements — the quantum analog of summing over all microstates. |
| $f_i^\sigma$ | **Fermi-Dirac occupation** | The probability that single-particle state $(i,\sigma)$ is occupied at temperature $T$. Ranges from 0 to 1. |
| $\lvert\psi_i^\sigma\rangle$ | **Single-particle orbital** | An eigenstate of the effective single-particle Hamiltonian. The bra-ket $\lvert\psi_i^\sigma\rangle\langle\psi_i^\sigma\rvert$ is a projection operator onto that state. |
| Diagonal: $\mathbf{r} = \mathbf{r}'$ | **Electron density** | The diagonal part of the single-body density matrix gives $n(\mathbf{r})$ — where electrons are. |
| Off-diagonal: $\mathbf{r} \neq \mathbf{r}'$ | **Quantum coherence** | Describes how the quantum state at $\mathbf{r}$ is connected to the state at $\mathbf{r}'$. Required for computing kinetic energy (nearby-point connections) and exchange energy (two-point orbital overlap). |

# Density operator

**Density operator** ($\hat{n}(\mathbf{r})$). The quantum mechanical operator that counts how many electrons are at position $\mathbf{r}$: each $\delta(\mathbf{r} - \mathbf{r}_i)$ asks "is electron $i$ here?" (zero everywhere except at the electron's position), and the sum $\hat{n}(\mathbf{r}) = \sum_{i=1}^N \delta(\mathbf{r} - \mathbf{r}_i)$ tallies contributions from all $N$ electrons. Taking the ==expectation value== (averaging over all possible electron configurations weighted by probability) gives the electron density $n(\mathbf{r})$ — the average number of electrons per unit volume at that point in space.


# ΔSCF method

**$\Delta$SCF (Self-Consistent Field) method**. A method for computing electron addition and removal energies as explicit total energy differences — $E(N-1) - E(N)$ for ionization, $E(N) - E(N+1)$ for electron affinity — where each total energy is obtained from a separate self-consistent calculation with all orbitals allowed to relax. The "$\Delta$" refers to taking a difference between two SCF calculations, and "self-consistent field" means the orbitals and the effective potential are solved together iteratively until they are mutually consistent (Equation Index Entry 34). This improves upon ==Koopmans' theorem== (which freezes all orbitals) by capturing orbital relaxation — the rearrangement of all remaining electrons in response to the added or removed electron — and, within DFT, whatever correlation the chosen functional provides. The method works well for finite systems (atoms, molecules) where removing or adding one electron produces a measurable energy change, but becomes less useful for bulk solids: one electron added to an infinite crystal is an infinitesimal perturbation, and the energy difference per electron vanishes.



# Effective potential

**Effective potential** ($V_{\text{eff}}^\sigma(\mathbf{r})$). In the real many-body problem, each electron interacts with every other electron simultaneously — a problem that cannot be solved directly for more than a few particles. The effective potential is the replacement that makes the problem tractable: instead of seeing all the other electrons individually, each electron moves in a single potential $V_{\text{eff}}^\sigma(\mathbf{r})$ that approximates the combined effect of the nuclei and all other electrons. This converts the many-body problem into $N$ independent single-particle Schrödinger equations, each of the form $[-\frac{\hbar^2}{2m_e}\nabla^2 + V_{\text{eff}}^\sigma(\mathbf{r})]\psi_i^\sigma = \varepsilon_i^\sigma\psi_i^\sigma$ (Equation Index Entry 32). What goes into $V_{\text{eff}}$ determines the quality of the approximation: in the original Hartree approach, $V_{\text{eff}} = V_{\text{ext}} + V_{\text{Hartree}}$ includes only the nuclear attraction and the classical electrostatic repulsion from the average electron density, ignoring exchange and correlation entirely. In ==Kohn-Sham DFT==, $V_{\text{eff}}^\sigma = V_{\text{ext}} + V_{\text{Hartree}} + V_{\text{xc}}^\sigma$ adds the ==exchange-correlation potential==, which folds in exchange, correlation, and the self-interaction correction. The spin label $\sigma$ appears because $V_{\text{xc}}^\sigma$ can differ between spin-up and spin-down electrons (important for magnetic systems). The effective potential depends on the density, which depends on the orbitals, which depend on $V_{\text{eff}}$ — this circular dependence is resolved by the ==self-consistent field== (SCF) procedure: guess $V_{\text{eff}}$, solve for orbitals, compute the new density, update $V_{\text{eff}}$, and repeat until the input and output agree.

# Electron density

**Electron density** ($n(\mathbf{r})$). The average number of electrons per unit volume at position $\mathbf{r}$. If you could freeze the system and count how many electrons are in a tiny box of volume $d^3r$ centered at $\mathbf{r}$, then repeat for every possible configuration of the electrons and average the result, you would get $n(\mathbf{r})\,d^3r$. The full many-body wavefunction $\Psi(\mathbf{r}_1,\mathbf{r}_2,\ldots,\mathbf{r}_N)$ lives in $3N$-dimensional space (three coordinates per electron), but the density collapses all of that information into a function of just three spatial coordinates by integrating out the positions of all electrons except one: $n(\mathbf{r}) = N\int d^3r_2\cdots d^3r_N\,|\Psi(\mathbf{r},\mathbf{r}_2,\ldots,\mathbf{r}_N)|^2$. The factor of $N$ appears because each of the $N$ electrons contributes equally (they are indistinguishable), so integrating out $N-1$ of them and multiplying by $N$ counts all contributions (Equation Index Entry 8). The density integrates to the total number of electrons: $\int n(\mathbf{r})\,d^3r = N$. For independent particles, the density simplifies to $n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2$ — each orbital contributes its own probability density $|\psi_i^\sigma|^2$, weighted by its occupation $f_i^\sigma$. The electron density is the central variable of ==density functional theory==: the Hohenberg-Kohn theorems (Equation Index Entry 17) prove that the ground-state density uniquely determines all ground-state properties, making the $3N$-dimensional wavefunction unnecessary in principle.

# Electron correlation

**Electron correlation**. The dependence of one electron's position on where other electrons are — if knowing where one electron is changes the probability of finding another at a given location, the two are correlated. There are two physically distinct sources. *Exchange correlation* arises from the Pauli exclusion principle: the antisymmetry of the wavefunction forces same-spin electrons apart, regardless of the Coulomb interaction. This is captured exactly by a single Slater determinant and is responsible for the exchange hole and exchange energy. *Coulomb correlation* is the additional avoidance (or, for opposite-spin pairs, occasional clustering) caused by the electrostatic repulsion between electrons, beyond what exchange already accounts for. When the term "correlation" is used without a qualifier in the Hartree-Fock or DFT context, it almost always refers to the Coulomb part — the piece missing from a single-determinant description. The pair correlation $\Delta n$ (see *joint pair probability*) and the pair distribution function $g$ both measure the total correlation, including exchange and Coulomb contributions together.

# Exchange charge density

**Exchange charge density**. The quantity $\sum_j \psi_j^{\sigma*}(\mathbf{r}')\psi_i^\sigma(\mathbf{r}')$ appearing in the Hartree-Fock exchange operator. It represents the overlap between orbital $i$ and all other same-spin orbitals $j$ at point $\mathbf{r}'$, and determines the nonlocal exchange potential acting on orbital $i$.

# Exchange energy

**Exchange energy** ($E_x$) — The lowering of the total energy that occurs because same-spin electrons are forced to avoid each other by the Pauli exclusion principle. Because the wavefunction must be antisymmetric, same-spin electrons cannot occupy the same point in space, which creates an exchange hole — a depletion of same-spin density around each electron (see *exchange hole*). This keeps same-spin electrons farther apart on average than the classical mean-field (Hartree) picture predicts, reducing their Coulomb repulsion below the Hartree estimate. The exchange energy is this reduction: the difference between the true electron-electron repulsion (computed with the antisymmetric wavefunction) and the Hartree energy (computed from the smooth average density). Equivalently, it can be written as the Coulomb interaction of each electron with its exchange hole, $E_x = \frac{1}{2}\int d^3r\,d^3r'\,\Delta n_x(\mathbf{r};\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$, which makes the physics vivid: each electron sits inside a region of depleted same-spin density, and the attraction between the electron and this "missing charge" lowers the energy. Exchange energy is always negative (the avoidance always reduces repulsion), involves only same-spin electron pairs, and is computable exactly from the occupied orbitals. It is distinct from the exchange-correlation energy $E_{\text{xc}}$, which additionally includes correlation effects (see *exchange-correlation energy*).

# Exchange-correlation energy

**Exchange-correlation energy** ($E_{\text{xc}}$) — Everything the Hartree energy gets wrong about electron-electron interactions, bundled into a single term. The Hartree energy treats electrons as a smooth, classical charge cloud that interacts with itself through the average density — it ignores the fact that electrons are quantum-mechanical fermions that actively avoid each other. The exchange-correlation energy is the correction: $E_{\text{xc}} = \langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}} + (T - T_s)$, where the first part is the difference between the true quantum electron-electron repulsion and the classical mean-field estimate (the potential part), and the second part $(T - T_s)$ is the difference between the true interacting kinetic energy and the non-interacting Kohn-Sham kinetic energy (the kinetic part — yes, correlation affects even the kinetic energy). It decomposes into exchange and correlation: $E_{\text{xc}} = E_x + E_c$. Exchange (see *exchange energy*) is the part from Pauli exclusion alone — same-spin avoidance — and can be computed exactly from the orbitals. Correlation (see *correlation energy*) is everything beyond that — the additional avoidance from Coulomb repulsion that a single Slater determinant cannot capture. The exchange-correlation energy is the central quantity that DFT must approximate, and the entire zoo of density functionals (LDA, GGA, meta-GGA, hybrids) are different strategies for estimating it. It is short-ranged because the long-range $1/r$ tails cancel between $\langle\hat{V}_{\text{int}}\rangle$ and $E_{\text{Hartree}}$, which is the physical reason local and semi-local approximations work as well as they do.

# Exchange hole

**Exchange hole** ($\Delta n_x$ or $n_x$). The depletion of same-spin electron density around each electron due to the Pauli exclusion principle. In the Hartree-Fock approximation, $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -\delta_{\sigma\sigma'}|\rho_\sigma(\mathbf{r},\mathbf{r}')|^2$, where $\rho_\sigma$ is the single-body density matrix. The exchange hole is always non-positive ($\leq 0$), involves only same-spin electrons, and integrates to exactly $-1$ electron — one electron's worth of charge is excluded from the neighborhood of each electron.

# Exchange-correlation hole

**Exchange-correlation hole** ($n_{\text{xc}}$). The total change in electron density around a reference electron, relative to what you would expect if electrons were distributed uniformly. It captures both effects that keep electrons apart: the ==exchange hole== (same-spin avoidance from the Pauli principle) and the ==correlation hole== (further avoidance of all pairs from Coulomb repulsion). The combined hole is always centered on the reference electron, and it integrates to exactly $-1$ — meaning that exactly one electron's worth of charge is missing from the neighborhood of every electron. This integration rule holds because the exchange hole already removes $-1$ and the correlation hole integrates to zero (it redistributes density without changing the total). The physical payoff of defining the xc hole is that the ==exchange-correlation energy== can be written as the Coulomb interaction of each electron with its own xc hole: $E_{\text{xc}} = \frac{1}{2}\int d^3r\,n(\mathbf{r})\int d^3r'\,\frac{n_{\text{xc}}(\mathbf{r},\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}$. This expression is exact, and it is the physical picture behind all approximate xc functionals — if you can approximate the shape of the hole accurately, you get a good functional (Equation Index Entry 16).

# Exclusion principle

**Exclusion principle**. See *Pauli exclusion principle*.

# Expectation value

**Expectation value** — The probability-weighted average of all possible outcomes of measuring an observable $\hat{O}$ in a quantum state $|\Psi\rangle$, written $\langle\hat{O}\rangle = \langle\Psi|\hat{O}|\Psi\rangle$ for a normalized state. The operator $\hat{O}$ encodes both the possible measurement outcomes (its eigenvalues) and the rule for extracting them from the wavefunction; the bra $\langle\Psi|$ and ket $|\Psi\rangle$ on either side project onto the system's actual state, so the result adds up each eigenvalue weighted by the probability of measuring it — if energy eigenstates are $|\phi_n\rangle$ with energies $E_n$, then $\langle\hat{H}\rangle = \sum_n |c_n|^2 E_n$ where $|c_n|^2$ is the probability of finding energy $E_n$. This is not the value any single measurement returns, but the average you would converge to over many measurements on identically prepared systems. At finite temperature, the expectation value generalizes to $\langle\hat{O}\rangle = \text{Tr}\,\hat{\rho}\hat{O}$, where $\hat{\rho}$ is the density matrix encoding the thermal occupation of states.

# External potential

**External potential** ($V_{\text{ext}}(\mathbf{r})$). The potential acting on the electrons from sources external to the electron system — typically the Coulomb attraction of the nuclei: $V_{\text{ext}}(\mathbf{r}) = \sum_I V_I(|\mathbf{r} - \mathbf{R}_I|)$. It is the only system-specific part of the Hamiltonian, distinguishing one material from another. Can also include electric fields and Zeeman terms.

# Fermi-Dirac distribution

**Fermi-Dirac distribution**. The probability that a quantum state with energy $\varepsilon_i^\sigma$ is occupied by an electron at thermal equilibrium: $f_i^\sigma = [e^{(\varepsilon_i^\sigma - \mu)/k_BT} + 1]^{-1}$, where $\mu$ is the chemical potential and $k_BT$ — the Boltzmann constant times the absolute temperature — is roughly how much energy the thermal environment has available to kick an electron from one state to another. The exponent $(\varepsilon - \mu)/k_BT$ compares the energy gap between a state and the chemical potential to this thermal energy: if the gap is much larger than $k_BT$, thermal agitation cannot reach the state and its occupation is locked at 0 or 1; if the gap is comparable to $k_BT$, the thermal energy is enough to shuffle electrons in and out, giving fractional occupation. At $T = 0$ the distribution collapses to a step function — every state below $\mu$ is filled and every state above is empty. The formula is exact for non-interacting fermions; in Kohn-Sham DFT it is applied to the fictitious non-interacting system as an approximation.

# Fermi energy

**Fermi energy**. At zero temperature, the chemical potential of the electron system — the energy of the highest occupied single-particle state. It separates filled from empty states and determines many electronic properties including whether a material is a metal (states at $E_F$) or an insulator (gap at $E_F$).

# Force theorem

**Force theorem**. The result that the force on a nucleus $I$ is $\mathbf{F}_I = -\int d^3r\,n(\mathbf{r})\,\partial V_{\text{ext}}/\partial\mathbf{R}_I - \partial E_{II}/\partial\mathbf{R}_I$ — the nuclear charge times the total electric field at the nucleus, computed from the electron density and other nuclei. The kinetic and exchange-correlation energies do not appear explicitly. Valid when the electronic state is at the variational minimum; requires Pulay corrections if the basis is incomplete and position-dependent.

# Helmholtz free energy

**Helmholtz free energy** ($F$) — The thermodynamic potential that governs equilibrium at fixed temperature, volume, and particle number, defined as $F = U - TS$ where $U$ is the internal energy and $S$ is the entropy. It encodes a competition: the internal energy $U$ favors states with low energy, while the entropy term $-TS$ favors states that spread probability over as many quantum states as possible. At low temperature the energy term dominates and the system collapses to its ground state; at high temperature the entropy term dominates and all states become equally populated. The equilibrium state is the one that minimizes $F$ — the best compromise between low energy and high entropy at the given temperature. In quantum statistical mechanics, $F$ can be expressed as a functional of the many-body density matrix: $F = \text{Tr}\,\hat{\rho}(\hat{H} + \frac{1}{\beta}\ln\hat{\rho})$, and minimizing over $\hat{\rho}$ yields the Boltzmann distribution $\hat{\rho} = e^{-\beta\hat{H}}/Z$. In VASP, Fermi-Dirac smearing introduces a finite electronic temperature, and the free energy $F$ (labeled `TOTEN` or `free energy TOTEN` in OUTCAR) should be used rather than the total energy $E$ for metallic systems.

# Grand canonical ensemble

**Grand canonical ensemble**. The statistical mechanical framework in which the number of particles fluctuates and is controlled by the chemical potential $\mu$. The grand partition function is $Z = \text{Tr}\,e^{-\beta(\hat{H}-\mu\hat{N})}$, where the trace is over all states with any particle number.

# Grand potential

**Grand potential** ($\Omega$). The thermodynamic potential for the grand canonical ensemble: $\Omega = -\frac{1}{\beta}\ln Z$, where $Z$ is the grand partition function. Related to the Helmholtz free energy by $\Omega = F - \mu N$.

# Ground state

**Ground state**. The state with the lowest energy, determined by minimizing the total energy over all properly antisymmetric trial wavefunctions subject to conservation laws. The ground state must be found by nonperturbative methods because different energy terms are large and nearly cancel.

# Hamiltonian

**Hamiltonian** ($\hat{H}$). The total energy operator for the electronic system: $\hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II}$. In Hartree atomic units: $\hat{T} = \sum_i -\frac{1}{2}\nabla_i^2$, $\hat{V}_{\text{ext}} = \sum_{i,I} V_I(|\mathbf{r}_i - \mathbf{R}_I|)$, $\hat{V}_{\text{int}} = \frac{1}{2}\sum_{i\neq j} 1/|\mathbf{r}_i - \mathbf{r}_j|$.

# Hartree atomic units

**Hartree atomic units**. The system of units in which $\hbar = m_e = e = 4\pi/\epsilon_0 = 1$. The unit of energy is the Hartree (27.211 eV), the unit of length is the Bohr radius $a_0$ (0.529 Å). Used throughout Martin's text and in most theoretical derivations.

# Hartree energy

**Hartree energy** ($E_{\text{Hartree}}$). The classical electrostatic self-energy of the electron charge distribution: $E_{\text{Hartree}} = \frac{1}{2}\int d^3r\,d^3r'\,n(\mathbf{r})n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$. It captures the dominant mean-field part of the electron-electron Coulomb repulsion but includes a spurious self-interaction because it does not distinguish electrons from one another.

# Hartree-Fock approximation

**Hartree-Fock approximation**. The variational method that finds the single Slater determinant minimizing the total energy of the interacting Hamiltonian. The resulting Hartree-Fock equations include a nonlocal, state-dependent exchange operator that captures the Pauli exclusion principle exactly but neglects all correlation. Band gaps are overestimated because of missing correlation and orbital relaxation.

# Hellmann-Feynman theorem

**Hellmann-Feynman theorem**. See *Force theorem*.

# Ion-ion interaction

**Ion-ion interaction** ($E_{II}$). The classical Coulomb repulsion among the nuclei: $E_{II} = \frac{1}{2}\sum_{I \neq J} Z_I Z_J e^2/|\mathbf{R}_I - \mathbf{R}_J|$. A constant for fixed nuclear positions. Essential for total energies and forces, but does not affect the electronic wavefunction.

# Joint pair probability

**Joint pair probability** ($n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$). The probability density for simultaneously finding an electron of spin $\sigma$ at $\mathbf{r}$ and an electron of spin $\sigma'$ at $\mathbf{r}'$. Obtained from the many-body wavefunction by integrating out all electron coordinates except two. Decomposes into an uncorrelated product $n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')$ plus a correlation correction $\Delta n$.

# Koopmans' theorem

**Koopmans' theorem**. In the Hartree-Fock approximation, the eigenvalue of a filled (empty) orbital equals the removal (addition) energy, assuming all other orbitals remain frozen. The theorem neglects orbital relaxation and correlation, causing Hartree-Fock eigenvalues to overestimate gaps.

# Local / Semi-local / Nonlocal approximation

**Local / Semi-local / Nonlocal approximation**. These terms classify density functional approximations by how much spatial information they use when computing the exchange-correlation energy at each point. A *local* approximation (LDA) depends only on the value of the density at exactly the point $\mathbf{r}$ — it treats each point as if it were part of a uniform electron gas with that density. A *semi-local* approximation (GGA) also uses the gradient $\nabla n(\mathbf{r})$, which tells it how the density is changing at that point, but still only evaluates quantities at $\mathbf{r}$ itself. A *nonlocal* approximation depends on the density at pairs of points $(\mathbf{r}, \mathbf{r}')$ separated by finite distances — the exact exchange energy is nonlocal in this sense because it involves the off-diagonal density matrix $\rho(\mathbf{r},\mathbf{r}')$. Local and semi-local approximations work well because electronic correlation is short-ranged (see *electron correlation*, *joint pair probability*): since electrons only significantly affect each other when they are close together, a functional that only looks at the density in the immediate vicinity of each point can still capture most of the correlation physics.

# Lagrange multiplier

**Lagrange multiplier**. A mathematical device for enforcing constraints during variational minimization. In the Rayleigh-Ritz principle, the multiplier enforcing wavefunction normalization becomes the energy eigenvalue. In DFT, the multiplier enforcing $\int n\,d^3r = N$ becomes the chemical potential $\mu$.

# Many-body wavefunction

**Many-body wavefunction** ($\Psi(\mathbf{r}_1,\mathbf{r}_2,\ldots,\mathbf{r}_N)$). The quantum mechanical state of $N$ electrons, living in $3N$-dimensional configuration space. Must be antisymmetric under exchange of any two electron coordinates. Contains all information about the electronic system but is intractable to compute or store for more than a few tens of electrons.

# Non-relativistic quantum mechanics

**Non-relativistic quantum mechanics** — The formulation of quantum mechanics in which electrons are treated as slow compared to the speed of light, so that relativistic effects — mass increase at high velocity, spin-orbit coupling, and the existence of positrons — are neglected. The governing equation is the Schrödinger equation $\hat{H}|\Psi\rangle = E|\Psi\rangle$, where the kinetic energy operator $\hat{T} = -\frac{1}{2}\nabla^2$ comes from the classical $p^2/2m$ rather than from the relativistic energy-momentum relation. This is an excellent approximation for light elements (up to roughly the 3d transition metals), where electron velocities are a small fraction of $c$. For heavy elements — lanthanides, actinides, and late transition metals like Au and Pt — electrons near the nucleus move fast enough that relativistic corrections become significant: core orbitals contract, valence $s$ and $p$ orbitals are pulled inward, and $d$ and $f$ orbitals expand. These effects are typically incorporated through relativistic pseudopotentials or the scalar-relativistic approximation rather than by solving the full Dirac equation.

# Pair correlation

**Pair correlation** ($\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$). The difference between the actual joint pair probability and the product of individual densities: $\Delta n \equiv n(\mathbf{r},\sigma;\mathbf{r}',\sigma') - n(\mathbf{r},\sigma)\,n(\mathbf{r}',\sigma')$. It measures exactly how much the presence of one electron at $\mathbf{r}$ changes the probability of finding another at $\mathbf{r}'$, compared to if they were completely independent. Negative $\Delta n$ means electrons avoid that pair of positions more than independent particles would; positive means they are found together more often. The pair correlation includes both exchange and Coulomb contributions (see *electron correlation*) and is short-ranged — it decays to zero at large $|\mathbf{r} - \mathbf{r}'|$ because distant electrons barely influence each other. It is the quantity that determines the exchange-correlation energy, making it central to DFT.

# Pair distribution function

**Pair distribution function** ($g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$). The normalized ratio $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')/[n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')]$, measuring the probability of finding an electron pair relative to the uncorrelated probability. Unity for independent particles. The deviation $g-1$ is a dimensionless, short-ranged measure of correlation.

# Partition function

**Partition function** ($Z$). The normalization constant for the Boltzmann distribution: $Z = \text{Tr}\,e^{-\beta\hat{H}}$. Related to the free energy by $Z = e^{-\beta F}$.

# Pauli exclusion principle

**Pauli exclusion principle**. The requirement that no two fermions can occupy the same quantum state. Expressed mathematically by the antisymmetry of the wavefunction. In a Slater determinant, two identical rows make the determinant vanish. The exclusion principle is responsible for the exchange hole and the exchange energy.

# Pressure (quantum-mechanical)

**Pressure** ($P$) — In electronic structure theory, pressure is defined microscopically from the stress tensor as $P = -\frac{1}{3}\text{Tr}\,\sigma_{\alpha\beta}$ — the average of the three diagonal stress components, which measure the system's internal tendency to expand or contract. It is computed directly from the quantum-mechanical expectation value of the kinetic and interaction stress operators (Entry 21), with no reference to container walls, temperature, or a gas law. Positive $P$ means the system pushes outward (wants to expand); negative means it pulls inward (wants to contract); zero means equilibrium. This definition is more fundamental than the thermodynamic pressure from PChem ($PV = nRT$, force per unit area on a boundary): it applies to a single molecule in vacuum, a crystal unit cell at zero temperature, or any situation where there is no "gas" and no "walls." In the macroscopic thermodynamic limit the two definitions agree, but the stress-tensor definition works at any scale. In VASP, the external pressure is set with `PSTRESS` and the computed pressure appears in the OUTCAR stress tensor output.

# Pulay corrections

**Pulay corrections**. Additional terms in the force expression that arise when the basis set is incomplete and depends on nuclear positions. Named after Peter Pulay, who identified them. In a complete basis, these terms vanish. Plane-wave bases are independent of nuclear positions (no Pulay force corrections), but Pulay stress corrections are needed because changing the cell volume changes the basis.

# Rayleigh-Ritz variational principle

**Rayleigh-Ritz variational principle**. The principle that the energy functional $\langle\Psi|\hat{H}|\Psi\rangle/\langle\Psi|\Psi\rangle$ is stationary at every eigenstate of $\hat{H}$ and minimized at the ground state. Converts the Schrödinger equation into an optimization problem. The foundation of all variational methods.

# Self-interaction

**Self-interaction**. The spurious Coulomb repulsion of an electron with itself that is present in the Hartree energy because the mean-field integral does not distinguish individual electrons. Exactly canceled by the exchange term in Hartree-Fock theory. Only approximately canceled in DFT with approximate xc functionals — the residual self-interaction error is a major source of error for localized states such as Ce 4f electrons.

# Slater determinant

**Slater determinant**. An antisymmetric $N$-electron wavefunction constructed as a determinant of single-particle spin-orbitals: $\Phi = (N!)^{-1/2}\det[\phi_i(\mathbf{r}_j,\sigma_j)]$. Automatically enforces the Pauli exclusion principle. The Hartree-Fock wavefunction is the single determinant that minimizes the total energy.

# Spin-orbital

**Spin-orbital** ($\phi_i(\mathbf{r},\sigma)$). A single-particle state that is a product of a spatial orbital $\psi_i^\sigma(\mathbf{r})$ and a spin function $\alpha_i(\sigma)$. The rows of the Slater determinant.

# Stationary point

**Stationary point** — A point where the first variation (the functional analog of a derivative) of a functional vanishes: $\delta\Omega = 0$. At a stationary point, all infinitesimal changes to the input leave the functional's value unchanged to first order — it is a flat spot on the energy landscape. A stationary point can be a minimum, a maximum, or a saddle point; the variational principle guarantees that every eigenstate of the Hamiltonian is a stationary point of the Rayleigh-Ritz functional $\Omega_{\text{RR}}$, with the ground state being the global minimum and excited states being saddle points (lower than some trial wavefunctions, higher than others).

# Stress tensor

**Stress tensor** ($\sigma_{\alpha\beta}$). The generalized force conjugate to strain: $\sigma_{\alpha\beta} = -(1/\Omega)\partial E/\partial\epsilon_{\alpha\beta}$. A rank-2 tensor whose diagonal elements give the pressure and whose off-diagonal elements give shear stresses. Derived from a scaling of all coordinates in the system. Used for cell optimization in VASP (`ISIF` ≥ 3).

# Variational principle

**Variational principle** — The statement that the true ground-state energy $E_0$ is the lowest possible expectation value of the Hamiltonian over all valid trial wavefunctions: $\langle\Psi_{\text{trial}}|\hat{H}|\Psi_{\text{trial}}\rangle \geq E_0$ for any normalized, antisymmetric $|\Psi_{\text{trial}}\rangle$, with equality only when the trial wavefunction is the exact ground state. This means any approximate wavefunction gives an energy that is an upper bound to the truth — you can never accidentally undershoot — and minimizing the energy over a parameterized family of trial wavefunctions is guaranteed to approach the ground state from above. The formal statement is the Rayleigh-Ritz principle (Eq. 3.10), and nearly every electronic structure method is built on restricting the variational search to a tractable subset of wavefunctions: Hartree-Fock searches over single Slater determinants, configuration interaction over linear combinations of determinants, and the Hohenberg-Kohn theorem extends the idea to functionals of the density. The variational principle is also why the Hellmann-Feynman theorem works: at a stationary point of the energy, the implicit dependence on the wavefunction drops out of energy derivatives.

# Virial theorem

**Virial theorem**. For a system in equilibrium with purely Coulomb interactions: $3P\Omega = 2E_{\text{kinetic}} + E_{\text{potential}}$. At zero pressure, this gives $E_{\text{total}} = -E_{\text{kinetic}} = \frac{1}{2}E_{\text{potential}}$. A general result valid for any system at any temperature, classical or quantum.
