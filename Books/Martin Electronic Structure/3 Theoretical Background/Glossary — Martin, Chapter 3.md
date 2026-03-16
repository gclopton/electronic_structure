# Glossary — Martin, Chapter 3: Theoretical Background

Electronic Structure Vault

---

**Adiabatic approximation**. See *Born-Oppenheimer approximation*. The term "adiabatic" in this context means the electrons remain in their instantaneous ground state as the nuclei move — there are no electronic transitions. Not to be confused with "adiabatic connection," which is a different use of the same word.

**Adiabatic connection**. A continuous variation of a parameter $\lambda$ in the Hamiltonian that connects two states of the system — typically the noninteracting ($\lambda = 0$) and fully interacting ($\lambda = 1$) ground states. The system is assumed to remain in its ground state at each value of $\lambda$. The energy difference between the two endpoints can be computed as an integral $\Delta E = \int_0^1 d\lambda\,\langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$, which requires the wavefunction at intermediate (unphysical) coupling strengths.

**Antisymmetric wavefunction**. A many-body wavefunction $\Psi(\mathbf{r}_1, \mathbf{r}_2, \ldots, \mathbf{r}_N)$ that changes sign when any two electron coordinates are exchanged: $\Psi(\ldots, \mathbf{r}_i, \ldots, \mathbf{r}_j, \ldots) = -\Psi(\ldots, \mathbf{r}_j, \ldots, \mathbf{r}_i, \ldots)$. This is the requirement of Fermi-Dirac statistics for electrons and is the mathematical expression of the Pauli exclusion principle. The simplest antisymmetric wavefunction is a Slater determinant.

**Born-Oppenheimer approximation**. The approximation that the nuclear kinetic energy can be neglected, so that nuclear positions $\{\mathbf{R}_I\}$ enter the electronic Hamiltonian as fixed parameters rather than dynamical variables. Justified by the small electron-to-nuclear mass ratio $m_e/M_I \ll 1$: electrons adjust instantaneously to nuclear motion. The electronic energy $E(\{\mathbf{R}_I\})$ then defines a potential energy surface on which the nuclei move. Excellent for structural properties, lattice dynamics, and most ground-state calculations. Breaks down when electron-phonon coupling is strong (metals near phase transitions, polarons, superconductivity) or when electronic states become degenerate (conical intersections).

**Chemical potential** ($\mu$). The energy cost of adding one more electron to the system. At zero temperature it equals the Fermi energy — the energy of the highest occupied single-particle state. At finite temperature it is defined implicitly by the requirement $\sum_{i,\sigma} f_i^\sigma = N$, where $f_i^\sigma$ is the Fermi-Dirac occupation. In VASP, $\mu$ appears as `E-fermi` in the OUTCAR file.

**Classical Coulomb energy** ($E^{\text{CC}}$). The neutral grouping of all classical electrostatic terms: $E^{\text{CC}} = E_{\text{Hartree}} + \int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r + E_{II}$. Each individual term diverges in an extended system, but their sum — the electrostatic energy of a neutral charge distribution — is finite and well-defined. Evaluated by Ewald summation in periodic calculations.

**Correlation energy** ($E_c$). The lowering of the total energy due to electron-electron correlations beyond exchange. Defined as $E_c = E_{\text{exact}} - E_{\text{HF}}$ in the Hartree-Fock context, or as the difference from the Kohn-Sham single-determinant energy constrained to give the exact density in the DFT context. Always negative for the ground state. Correlation affects both kinetic and potential energies and is more complicated to compute than exchange.

**Correlation hole** ($n_c$). The part of the exchange-correlation hole beyond the exchange contribution: $n_{\text{xc}} = n_x + n_c$. Unlike the exchange hole, the correlation hole can be positive or negative at different points. It integrates to zero — it redistributes the hole density without changing the total weight. Correlation is most important for opposite-spin electrons, since same-spin electrons are already kept apart by exchange.

**Coupling constant integration**. The technique of computing energy differences by integrating the generalized force theorem $\partial E/\partial\lambda = \langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$ over a continuous parameter $\lambda$. When $\lambda$ scales the electron-electron interaction from 0 to 1, this provides the adiabatic connection formula for the exchange-correlation energy.

**Density matrix** ($\hat{\rho}$). In statistical mechanics, the operator $\hat{\rho} = \frac{1}{Z}e^{-\beta\hat{H}}$ that encodes the thermal equilibrium state of a quantum system. In the single-body context, $\hat{\rho} = \sum_i |\psi_i^\sigma\rangle f_i^\sigma \langle\psi_i^\sigma|$ is the operator whose diagonal part gives the density and whose off-diagonal part encodes quantum coherence. The density matrix determines the kinetic energy and the exchange energy — quantities the density alone cannot give.

**Density operator** ($\hat{n}(\mathbf{r})$). The quantum mechanical operator $\hat{n}(\mathbf{r}) = \sum_{i=1}^N \delta(\mathbf{r} - \mathbf{r}_i)$ whose expectation value gives the electron density $n(\mathbf{r})$.

**$\Delta$SCF method**. A method for computing addition and removal energies as explicit total energy differences $E(N-1) - E(N)$ or $E(N) - E(N+1)$, with self-consistent relaxation of all orbitals in each calculation. Improves upon Koopmans' theorem by including orbital relaxation and (in DFT) correlation effects. Works well for finite systems; less useful for bulk solids where the perturbation of one electron is infinitesimal.

**Effective potential** ($V_{\text{eff}}^\sigma(\mathbf{r})$). The local, multiplicative potential in the single-particle Schrödinger equation that incorporates all many-body effects approximately. In the Hartree approach, $V_{\text{eff}} = V_{\text{ext}} + V_{\text{Hartree}}$; in Kohn-Sham DFT, $V_{\text{eff}} = V_{\text{ext}} + V_{\text{Hartree}} + V_{\text{xc}}$.

**Electron density** ($n(\mathbf{r})$). The probability density for finding any one of the $N$ electrons at position $\mathbf{r}$, defined as $n(\mathbf{r}) = N\int d^3r_2\cdots d^3r_N\,|\Psi(\mathbf{r},\mathbf{r}_2,\ldots,\mathbf{r}_N)|^2$ for the many-body wavefunction, or $n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2$ for independent particles. Integrates to $N$. Lives in three-dimensional space regardless of the number of electrons. The central variable of DFT.

**Exchange charge density**. The quantity $\sum_j \psi_j^{\sigma*}(\mathbf{r}')\psi_i^\sigma(\mathbf{r}')$ appearing in the Hartree-Fock exchange operator. It represents the overlap between orbital $i$ and all other same-spin orbitals $j$ at point $\mathbf{r}'$, and determines the nonlocal exchange potential acting on orbital $i$.

**Exchange energy** ($E_x$). The lowering of the total energy due to the Pauli exclusion principle. It equals $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$ in the Hartree-Fock approximation and can be written as the Coulomb interaction of each electron with its exchange hole: $E_x = \frac{1}{2}\int d^3r\,d^3r'\,\Delta n_x(\mathbf{r};\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$. Always negative.

**Exchange hole** ($\Delta n_x$ or $n_x$). The depletion of same-spin electron density around each electron due to the Pauli exclusion principle. In the Hartree-Fock approximation, $\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma') = -\delta_{\sigma\sigma'}|\rho_\sigma(\mathbf{r},\mathbf{r}')|^2$, where $\rho_\sigma$ is the single-body density matrix. The exchange hole is always non-positive ($\leq 0$), involves only same-spin electrons, and integrates to exactly $-1$ electron — one electron's worth of charge is excluded from the neighborhood of each electron.

**Exchange-correlation hole** ($n_{\text{xc}}$). The total depletion of electron density around each electron due to both exchange and correlation: $n_{\text{xc}} = n_x + n_c$. It integrates to exactly $-1$ (the exchange hole contributes $-1$, the correlation hole contributes $0$). The xc energy is the Coulomb interaction of each electron with its xc hole — this is the physical picture underlying the construction of approximate xc functionals.

**Exclusion principle**. See *Pauli exclusion principle*.

**Expectation value**. For an eigenstate $|\Psi\rangle$, the expectation value of an operator $\hat{O}$ is $\langle\hat{O}\rangle = \langle\Psi|\hat{O}|\Psi\rangle / \langle\Psi|\Psi\rangle$. At finite temperature, $\langle\hat{O}\rangle = \text{Tr}\,\hat{\rho}\hat{O}$.

**External potential** ($V_{\text{ext}}(\mathbf{r})$). The potential acting on the electrons from sources external to the electron system — typically the Coulomb attraction of the nuclei: $V_{\text{ext}}(\mathbf{r}) = \sum_I V_I(|\mathbf{r} - \mathbf{R}_I|)$. It is the only system-specific part of the Hamiltonian, distinguishing one material from another. Can also include electric fields and Zeeman terms.

**Fermi-Dirac distribution**. The equilibrium occupation probability for non-interacting fermions: $f_i^\sigma = [e^{\beta(\varepsilon_i^\sigma - \mu)} + 1]^{-1}$. At $T = 0$ it is a step function; at finite $T$ it smooths over a window of $\sim k_BT$ around the chemical potential $\mu$.

**Fermi energy**. At zero temperature, the chemical potential of the electron system — the energy of the highest occupied single-particle state. It separates filled from empty states and determines many electronic properties including whether a material is a metal (states at $E_F$) or an insulator (gap at $E_F$).

**Force theorem**. The result that the force on a nucleus $I$ is $\mathbf{F}_I = -\int d^3r\,n(\mathbf{r})\,\partial V_{\text{ext}}/\partial\mathbf{R}_I - \partial E_{II}/\partial\mathbf{R}_I$ — the nuclear charge times the total electric field at the nucleus, computed from the electron density and other nuclei. The kinetic and exchange-correlation energies do not appear explicitly. Valid when the electronic state is at the variational minimum; requires Pulay corrections if the basis is incomplete and position-dependent.

**Free energy** ($F$). The Helmholtz free energy $F = U - TS$, where $U$ is the internal energy and $S$ is the entropy. Expressed in terms of the density matrix as $F = \text{Tr}\,\hat{\rho}(\hat{H} + \frac{1}{\beta}\ln\hat{\rho})$. Minimized at thermal equilibrium for fixed $T$, $V$, $N$.

**Grand canonical ensemble**. The statistical mechanical framework in which the number of particles fluctuates and is controlled by the chemical potential $\mu$. The grand partition function is $Z = \text{Tr}\,e^{-\beta(\hat{H}-\mu\hat{N})}$, where the trace is over all states with any particle number.

**Grand potential** ($\Omega$). The thermodynamic potential for the grand canonical ensemble: $\Omega = -\frac{1}{\beta}\ln Z$, where $Z$ is the grand partition function. Related to the Helmholtz free energy by $\Omega = F - \mu N$.

**Ground state**. The state with the lowest energy, determined by minimizing the total energy over all properly antisymmetric trial wavefunctions subject to conservation laws. The ground state must be found by nonperturbative methods because different energy terms are large and nearly cancel.

**Hamiltonian** ($\hat{H}$). The total energy operator for the electronic system: $\hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II}$. In Hartree atomic units: $\hat{T} = \sum_i -\frac{1}{2}\nabla_i^2$, $\hat{V}_{\text{ext}} = \sum_{i,I} V_I(|\mathbf{r}_i - \mathbf{R}_I|)$, $\hat{V}_{\text{int}} = \frac{1}{2}\sum_{i\neq j} 1/|\mathbf{r}_i - \mathbf{r}_j|$.

**Hartree atomic units**. The system of units in which $\hbar = m_e = e = 4\pi/\epsilon_0 = 1$. The unit of energy is the Hartree (27.211 eV), the unit of length is the Bohr radius $a_0$ (0.529 Å). Used throughout Martin's text and in most theoretical derivations.

**Hartree energy** ($E_{\text{Hartree}}$). The classical electrostatic self-energy of the electron charge distribution: $E_{\text{Hartree}} = \frac{1}{2}\int d^3r\,d^3r'\,n(\mathbf{r})n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$. It captures the dominant mean-field part of the electron-electron Coulomb repulsion but includes a spurious self-interaction because it does not distinguish electrons from one another.

**Hartree-Fock approximation**. The variational method that finds the single Slater determinant minimizing the total energy of the interacting Hamiltonian. The resulting Hartree-Fock equations include a nonlocal, state-dependent exchange operator that captures the Pauli exclusion principle exactly but neglects all correlation. Band gaps are overestimated because of missing correlation and orbital relaxation.

**Hellmann-Feynman theorem**. See *Force theorem*.

**Ion-ion interaction** ($E_{II}$). The classical Coulomb repulsion among the nuclei: $E_{II} = \frac{1}{2}\sum_{I \neq J} Z_I Z_J e^2/|\mathbf{R}_I - \mathbf{R}_J|$. A constant for fixed nuclear positions. Essential for total energies and forces, but does not affect the electronic wavefunction.

**Joint pair probability** ($n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$). The probability density for simultaneously finding an electron of spin $\sigma$ at $\mathbf{r}$ and an electron of spin $\sigma'$ at $\mathbf{r}'$. Obtained from the many-body wavefunction by integrating out all electron coordinates except two. Decomposes into an uncorrelated product $n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')$ plus a correlation correction $\Delta n$.

**Koopmans' theorem**. In the Hartree-Fock approximation, the eigenvalue of a filled (empty) orbital equals the removal (addition) energy, assuming all other orbitals remain frozen. The theorem neglects orbital relaxation and correlation, causing Hartree-Fock eigenvalues to overestimate gaps.

**Lagrange multiplier**. A mathematical device for enforcing constraints during variational minimization. In the Rayleigh-Ritz principle, the multiplier enforcing wavefunction normalization becomes the energy eigenvalue. In DFT, the multiplier enforcing $\int n\,d^3r = N$ becomes the chemical potential $\mu$.

**Many-body wavefunction** ($\Psi(\mathbf{r}_1,\mathbf{r}_2,\ldots,\mathbf{r}_N)$). The quantum mechanical state of $N$ electrons, living in $3N$-dimensional configuration space. Must be antisymmetric under exchange of any two electron coordinates. Contains all information about the electronic system but is intractable to compute or store for more than a few tens of electrons.

**Pair distribution function** ($g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$). The normalized ratio $n(\mathbf{r},\sigma;\mathbf{r}',\sigma')/[n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')]$, measuring the probability of finding an electron pair relative to the uncorrelated probability. Unity for independent particles. The deviation $g-1$ is a dimensionless, short-ranged measure of correlation.

**Partition function** ($Z$). The normalization constant for the Boltzmann distribution: $Z = \text{Tr}\,e^{-\beta\hat{H}}$. Related to the free energy by $Z = e^{-\beta F}$.

**Pauli exclusion principle**. The requirement that no two fermions can occupy the same quantum state. Expressed mathematically by the antisymmetry of the wavefunction. In a Slater determinant, two identical rows make the determinant vanish. The exclusion principle is responsible for the exchange hole and the exchange energy.

**Pulay corrections**. Additional terms in the force expression that arise when the basis set is incomplete and depends on nuclear positions. Named after Peter Pulay, who identified them. In a complete basis, these terms vanish. Plane-wave bases are independent of nuclear positions (no Pulay force corrections), but Pulay stress corrections are needed because changing the cell volume changes the basis.

**Rayleigh-Ritz variational principle**. The principle that the energy functional $\langle\Psi|\hat{H}|\Psi\rangle/\langle\Psi|\Psi\rangle$ is stationary at every eigenstate of $\hat{H}$ and minimized at the ground state. Converts the Schrödinger equation into an optimization problem. The foundation of all variational methods.

**Self-interaction**. The spurious Coulomb repulsion of an electron with itself that is present in the Hartree energy because the mean-field integral does not distinguish individual electrons. Exactly canceled by the exchange term in Hartree-Fock theory. Only approximately canceled in DFT with approximate xc functionals — the residual self-interaction error is a major source of error for localized states such as Ce 4f electrons.

**Slater determinant**. An antisymmetric $N$-electron wavefunction constructed as a determinant of single-particle spin-orbitals: $\Phi = (N!)^{-1/2}\det[\phi_i(\mathbf{r}_j,\sigma_j)]$. Automatically enforces the Pauli exclusion principle. The Hartree-Fock wavefunction is the single determinant that minimizes the total energy.

**Spin-orbital** ($\phi_i(\mathbf{r},\sigma)$). A single-particle state that is a product of a spatial orbital $\psi_i^\sigma(\mathbf{r})$ and a spin function $\alpha_i(\sigma)$. The rows of the Slater determinant.

**Stress tensor** ($\sigma_{\alpha\beta}$). The generalized force conjugate to strain: $\sigma_{\alpha\beta} = -(1/\Omega)\partial E/\partial\epsilon_{\alpha\beta}$. A rank-2 tensor whose diagonal elements give the pressure and whose off-diagonal elements give shear stresses. Derived from a scaling of all coordinates in the system. Used for cell optimization in VASP (`ISIF` ≥ 3).

**Virial theorem**. For a system in equilibrium with purely Coulomb interactions: $3P\Omega = 2E_{\text{kinetic}} + E_{\text{potential}}$. At zero pressure, this gives $E_{\text{total}} = -E_{\text{kinetic}} = \frac{1}{2}E_{\text{potential}}$. A general result valid for any system at any temperature, classical or quantum.
