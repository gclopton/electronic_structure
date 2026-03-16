# Glossary — Martin, Chapter 6: Density Functional Theory: Foundations

Electronic Structure Vault

---

**Chemical potential** ($\mu$). The Lagrange multiplier enforcing the particle number constraint $\int n(\mathbf{r})\,d^3r = N$ during energy minimization. At zero temperature it equals the Fermi energy. In the Mermin finite-temperature formulation it controls the average electron number in the grand canonical ensemble.

**Constrained search**. The minimization procedure introduced by Levy and Lieb in which one searches over all antisymmetric $N$-electron wavefunctions $\Psi$ that yield a given density $n(\mathbf{r})$ and selects the one that minimizes $\langle \Psi | \hat{T} + \hat{V}_{\text{int}} | \Psi \rangle$. This defines the Levy-Lieb functional $F_{\text{LL}}[n]$ and extends the Hohenberg-Kohn framework to all $N$-representable densities.

**Current density functional theory**. Extension of DFT required when time-reversal symmetry is broken, as in the presence of a magnetic field coupling to orbital motion. The properties of the system then depend on both the particle density $n(\mathbf{r})$ and the current density $\mathbf{j}(\mathbf{r})$, since the Hamiltonian contains terms of the form $\mathbf{p} \cdot \mathbf{A}_{\text{ext}}$ in addition to $V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})$.

**Derivative discontinuity**. The property that the exact kinetic energy functional $T[n]$ — and by the virial theorem, all parts of the exact energy functional — must have derivatives that are discontinuous at integer electron occupation numbers. This discontinuity distinguishes metals from insulators and cannot be captured by any smooth, explicit functional of the density. It is the fundamental reason approximate LDA and GGA functionals underestimate band gaps.

**Dirac exchange**. The local approximation to the exchange energy, $C_2 \int n(\mathbf{r})^{4/3}\,d^3r$ with $C_2 = -\frac{3}{4}(3/\pi)^{1/3}$, derived by Dirac (1930) for a homogeneous electron gas. It appears as the third term in the Thomas-Fermi-Dirac functional and is the ancestor of the exchange component in modern LDA.

**Electron density** ($n(\mathbf{r})$). The probability density for finding any one of the $N$ electrons at position $\mathbf{r}$, defined as $n(\mathbf{r}) = N \int d^3r_2 \cdots d^3r_N\,|\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2$. It integrates to $N$, lives in three-dimensional space regardless of the number of electrons, and is directly measurable by X-ray and electron scattering. The Hohenberg-Kohn theorems establish it as the "basic variable" of DFT.

**External potential** ($V_{\text{ext}}(\mathbf{r})$). The potential acting on the electrons from sources external to the electron system. For electrons in a solid it is the Coulomb potential of the nuclei, $V_{\text{ext}}(\mathbf{r}) = -\sum_I Z_I e^2 / |\mathbf{r} - \mathbf{R}_I|$. It is the only part of the Hamiltonian that distinguishes one material from another; the kinetic and electron-electron interaction operators are universal.

**Fermi energy**. At zero temperature, the chemical potential of the electron system — the energy of the highest occupied single-particle state. It appears as the Lagrange multiplier $\mu$ in the Thomas-Fermi variational equation and, more generally, in the Kohn-Sham equations.

**Grand potential** ($\Omega$). The thermodynamic potential minimized at thermal equilibrium in the grand canonical ensemble: $\Omega = -\frac{1}{\beta}\ln \text{Tr}\,e^{-\beta(\hat{H}-\mu\hat{N})}$. In the Mermin formulation of finite-temperature DFT, the grand potential is expressed as a functional of the density matrix and its minimum defines the equilibrium state.

**Hartree energy** ($E_{\text{Hartree}}[n]$). The classical electrostatic self-energy of the electron charge distribution: $E_{\text{Hartree}} = \frac{1}{2}\int d^3r\,d^3r'\,n(\mathbf{r})\,n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$. It captures the dominant, long-range, mean-field part of the electron-electron Coulomb repulsion but includes a spurious self-interaction (each electron repels itself) and misses exchange and correlation effects.

**Hohenberg-Kohn energy functional** ($E_{\text{HK}}[n]$). The total energy expressed as a functional of the density: $E_{\text{HK}}[n] = F_{\text{HK}}[n] + \int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r + E_{II}$. The first term is the universal functional (internal energies), the second is the electron-nuclear coupling, and the third is the ion-ion repulsion. Its global minimum over allowed densities gives the exact ground-state energy and density.

**Hohenberg-Kohn Theorem I**. For any system of interacting particles in an external potential $V_{\text{ext}}(\mathbf{r})$, the ground-state density $n_0(\mathbf{r})$ uniquely determines $V_{\text{ext}}(\mathbf{r})$ up to a constant. Corollary: since the Hamiltonian is thereby fully determined, all properties of the system — ground and excited states — are in principle determined by $n_0(\mathbf{r})$ alone. The original proof assumes a nondegenerate ground state; this restriction is removed by the Levy-Lieb formulation.

**Hohenberg-Kohn Theorem II**. A universal energy functional $E[n]$ can be defined for any external potential $V_{\text{ext}}(\mathbf{r})$. The exact ground-state energy is the global minimum of this functional, and the density that achieves the minimum is the exact ground-state density. This provides the variational principle that makes DFT practical.

**Levy-Lieb functional** ($F_{\text{LL}}[n]$). The universal functional defined by the constrained search: $F_{\text{LL}}[n] = \min_{\Psi \to n(\mathbf{r})} \langle \Psi | \hat{T} + \hat{V}_{\text{int}} | \Psi \rangle$. It is defined for all $N$-representable densities (a larger domain than the $V$-representable densities of the Hohenberg-Kohn functional), works for degenerate ground states, and agrees with $F_{\text{HK}}[n]$ at the energy minimum.

**Many-body Hamiltonian** ($\hat{H}$). The full quantum mechanical operator for the electronic system: $\hat{H} = -\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2 + \sum_i V_{\text{ext}}(\mathbf{r}_i) + \frac{1}{2}\sum_{i \neq j} e^2/|\mathbf{r}_i - \mathbf{r}_j|$. The three terms are the kinetic energy (universal), external potential energy (system-specific), and electron-electron Coulomb repulsion (universal).

**Mermin functional** ($\Omega[\hat{\rho}]$). The grand potential functional $\Omega[\hat{\rho}] = \text{Tr}\,\hat{\rho}[(\hat{H}-\mu\hat{N}) + \frac{1}{\beta}\ln\hat{\rho}]$ that extends the Hohenberg-Kohn theorems to finite temperature. Its minimum over trial density matrices gives the equilibrium grand potential and density. It guarantees that thermodynamic properties (entropy, specific heat) are functionals of the equilibrium density, but constructing approximate functionals for the entropy is far more difficult than for the ground-state energy.

**$N$-representability**. The property that a density $n(\mathbf{r})$ can be obtained from some antisymmetric $N$-electron wavefunction. Any non-negative density whose gradient is square-integrable ($\int |\nabla n^{1/2}|^2 < \infty$) is $N$-representable. This is a weaker condition than $V$-representability and defines the domain of the Levy-Lieb functional.

**Particle number constraint**. The normalization condition $\int n(\mathbf{r})\,d^3r = N$ requiring the electron density to integrate to the total number of electrons. It is enforced during energy minimization through the Lagrange multiplier $\mu$ (the chemical potential).

**Self-interaction error**. The spurious repulsion of each electron with itself that is present in the Hartree energy because the mean-field Coulomb integral does not exclude the $i = j$ term. Correcting this error is one of the central challenges in constructing exchange-correlation functionals, and its persistence in approximate functionals is a major source of error for localized states such as Ce 4f electrons.

**Spin density** ($s(\mathbf{r})$). The magnetization density defined as $s(\mathbf{r}) = n(\mathbf{r},\uparrow) - n(\mathbf{r},\downarrow)$, where $n(\mathbf{r},\sigma)$ is the spin-resolved density. It is nonzero in systems with magnetic order or an odd number of electrons. In spin density functional theory the energy functional depends on both $n(\mathbf{r})$ and $s(\mathbf{r})$.

**Spin density functional theory**. The generalization of the Hohenberg-Kohn framework in which the energy functional depends on the spin-resolved densities $n(\mathbf{r},\uparrow)$ and $n(\mathbf{r},\downarrow)$ rather than the total density alone. It is required in the presence of spin-dependent external potentials (Zeeman fields) and is essential in practice for systems with magnetic order, even when no external magnetic field is present, because spin-dependent approximate functionals are far more accurate for such systems.

**Thomas-Fermi-Dirac approximation**. The original density functional, in which the kinetic energy is approximated by the local result for a uniform electron gas ($C_1 \int n^{5/3}\,d^3r$), exchange is treated in the Dirac local approximation ($C_2 \int n^{4/3}\,d^3r$), the electron-electron interaction is the Hartree energy, and correlation is neglected. It introduces the density as the central variable and the local-density idea, but fails to describe atomic shell structure or chemical bonding.

**Universal functional** ($F_{\text{HK}}[n]$). The functional $F_{\text{HK}}[n] = T[n] + E_{\text{int}}[n]$ containing the kinetic energy and electron-electron interaction energy of the interacting system. It is "universal" because neither the kinetic energy operator nor the Coulomb interaction depends on which material is being studied — only the external potential, which has been separated out, is system-specific. No exact form is known for any system with more than one electron.

**$V$-representability**. The property that a density $n(\mathbf{r})$ is the ground-state density of some external potential $V_{\text{ext}}(\mathbf{r})$. This is a more restrictive condition than $N$-representability: there exist physically reasonable densities that are not the ground state of any local potential. The Hohenberg-Kohn functional is defined only for $V$-representable densities; the Levy-Lieb formulation extends the domain to all $N$-representable densities.

**Weizsäcker correction** ($T_W[n]$). The gradient correction to the Thomas-Fermi kinetic energy: $T_W[n] = \frac{1}{4}\int d^3r\,|\nabla n(\mathbf{r})|^2/n(\mathbf{r})$. It captures the increase in kinetic energy where the density varies rapidly (near nuclei, at atomic edges) and equals the exact kinetic energy for a single electron or a system of bosons. It is the conceptual ancestor of gradient corrections in modern GGA functionals.
