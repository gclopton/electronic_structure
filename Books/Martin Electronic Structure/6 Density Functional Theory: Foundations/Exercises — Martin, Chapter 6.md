# Exercises — Martin, Chapter 6: Density Functional Theory: Foundations

Electronic Structure Vault

---

# Exercise 6.2 — The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization

> [!exercise] The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization
> The earliest density functional theory was proposed by Thomas (1927) and Fermi (1927), later extended by Dirac (1930). Rather than solving the many-body Schrödinger equation in $3N$-dimensional configuration space, the Thomas-Fermi-Dirac approach writes the total energy as an explicit functional of the electron density $n(\mathbf{r})$ — a single function of three variables. Consider a system of $N$ electrons in an external potential $V_{\text{ext}}(\mathbf{r})$.
>
> (a) Write the Thomas-Fermi-Dirac energy functional $E_{\text{TF}}[n]$ (Eq. 6.1). It contains four terms. Identify each by name, explain what physical contribution to the total energy it represents, and describe what approximation is being made in each.
>
> (b) The ground-state density is found by minimizing $E_{\text{TF}}[n]$ subject to the particle number constraint $\int n(\mathbf{r})\,d^3r = N$ (Eq. 6.2). Using the method of Lagrange multipliers, construct an unconstrained functional and show that the stationarity condition yields the Thomas-Fermi equation (Eq. 6.5). What is the physical meaning of the Lagrange multiplier that enforces the constraint? How does it relate to a quantity you already know from statistical mechanics at zero temperature?
>
> (c) The Hartree energy $E_{\text{Hartree}} = \frac{1}{2}\int d^3r\,d^3r'\,n(\mathbf{r})n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$ contains a factor of $\frac{1}{2}$ and a product $n(\mathbf{r})n(\mathbf{r}')$. Explain the physical reason for the $\frac{1}{2}$ prefactor. Why does the product of densities at two different points represent a mean-field, classical approximation to the true electron-electron repulsion? Identify what physical effects are missing from this classical treatment and explain why each is absent.
>
> (d) The Weizsäcker correction $T_W[n] = \frac{1}{4}\int d^3r\,|\nabla n(\mathbf{r})|^2/n(\mathbf{r})$ was proposed to improve the kinetic energy beyond the local Thomas-Fermi approximation. Explain why this is called a gradient correction — what does $|\nabla n|/n$ measure physically about the density at a given point? In what regions of an atom (near the nucleus, in the valence, far from the atom) is this correction largest, and why?
>
> (e) Despite its conceptual elegance, the Thomas-Fermi-Dirac approximation fails to predict atomic shell structure and molecular binding. Given that the kinetic energy is approximated as a local functional of the density, explain why this approximation cannot distinguish between two systems that have the same local density but different numbers of occupied quantum states. What does this failure motivate about the approach taken by Kohn and Sham in Chapter 7?

##### Part (a) — The Four Terms of the Thomas-Fermi-Dirac Energy Functional

The Thomas-Fermi-Dirac energy functional is

$$
E_{\text{TF}}[n] = C_1 \int d^3r\, n(\mathbf{r})^{5/3} + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + C_2 \int d^3r\, n(\mathbf{r})^{4/3} + \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\, n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}
$$

where $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$ and $C_2 = -\frac{3}{4}\left(\frac{3}{\pi}\right)^{1/3}$.

**Term 1: Local kinetic energy** — $T_{\text{TF}}[n] = C_1 \int d^3r\, n(\mathbf{r})^{5/3}$

This term approximates the total quantum-mechanical kinetic energy of the electrons. The approximation is the *local density approximation for the kinetic energy*: at each point $\mathbf{r}$, the kinetic energy density is taken to be that of a *uniform, noninteracting electron gas* whose density equals the local density $n(\mathbf{r})$.

The $n^{5/3}$ scaling comes from the free electron gas at zero temperature, where the Fermi wavevector is $k_F = (3\pi^2 n)^{1/3}$ and the kinetic energy per unit volume is

$$
\begin{aligned}
\frac{T}{V} &= \frac{3}{5} n \cdot \frac{\hbar^2 k_F^2}{2m_e} \\
&= \frac{3}{5} n \cdot \frac{\hbar^2}{2m_e}(3\pi^2 n)^{2/3} \\
&= \frac{3}{10}\frac{\hbar^2}{m_e}(3\pi^2)^{2/3}\, n^{5/3}
\end{aligned}
$$

In atomic units ($\hbar = m_e = e = 1$), the prefactor is $C_1 = \frac{3}{10}(3\pi^2)^{2/3} \approx 2.871$. The approximation replaces the true kinetic energy — which depends on the full set of single-particle wavefunctions — with a local functional of the density alone, discarding all orbital structure.

**Term 2: External potential energy** — $E_{\text{ext}}[n] = \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r})$

This is the energy of interaction between the electrons and the external potential (typically the nuclear Coulomb potential). No approximation is made — this term is exact. The energy of a charge distribution $n(\mathbf{r})$ in an external potential $V_{\text{ext}}(\mathbf{r})$ is simply the integral of the potential weighted by the density. This exactness follows from $\hat{V}_{\text{ext}}$ being a one-body operator:

$$
\begin{aligned}
\langle \Psi | \hat{V}_{\text{ext}} | \Psi \rangle &= \left\langle \Psi \left| \sum_{i=1}^{N} V_{\text{ext}}(\mathbf{r}_i) \right| \Psi \right\rangle \\
&= \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r})
\end{aligned}
$$

where the last step uses the definition $n(\mathbf{r}) = N \int d^3r_2 \cdots d^3r_N\, |\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2$.

**Term 3: Local exchange energy (Dirac exchange)** — $E_x[n] = C_2 \int d^3r\, n(\mathbf{r})^{4/3}$

This approximates the exchange energy from the antisymmetry (Pauli exclusion) of the wavefunction, again using a local density approximation: at each point, the exchange energy density is that of a uniform electron gas with density $n(\mathbf{r})$.

The $n^{4/3}$ scaling follows from dimensional analysis. Exchange is a Coulomb effect (energy $\sim e^2/r$) involving electrons separated by a characteristic distance set by the mean interelectron spacing $r_s \sim n^{-1/3}$:

$$
\begin{aligned}
\text{exchange energy per electron} &\sim \frac{e^2}{r_s} \sim n^{1/3} \\
\text{exchange energy per unit volume} &\sim n \cdot n^{1/3} = n^{4/3}
\end{aligned}
$$

The constant $C_2 = -\frac{3}{4}\left(\frac{3}{\pi}\right)^{1/3}$ is negative because exchange *lowers* the energy: antisymmetry keeps same-spin electrons apart, reducing their Coulomb repulsion. The approximation neglects the fact that in an inhomogeneous system, the exchange hole shape depends on the local electronic structure, not just on the local density value.

**Term 4: Hartree energy** — $E_{\text{Hartree}}[n] = \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\, n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}$

This is the classical electrostatic self-energy of the charge distribution $n(\mathbf{r})$. It approximates the electron-electron Coulomb repulsion by treating the electrons as a continuous classical charge cloud — each element $n(\mathbf{r})\,d^3r$ interacts with every other element $n(\mathbf{r}')\,d^3r'$ via the Coulomb potential. The approximation is the *mean-field approximation*: the quantum-mechanical pair correlation between electrons is ignored, replacing the true pair density with the uncorrelated product $n(\mathbf{r})n(\mathbf{r}')$.

##### Part (b) — Constrained Minimization and the Thomas-Fermi Equation

We seek the density $n(\mathbf{r})$ that minimizes $E_{\text{TF}}[n]$ subject to the particle number constraint $\int d^3r\, n(\mathbf{r}) = N$.

**Constructing the unconstrained functional.** Introduce a Lagrange multiplier $\mu$ and define

$$
\Omega_{\text{TF}}[n] = E_{\text{TF}}[n] - \mu \left( \int d^3r\, n(\mathbf{r}) - N \right)
$$

Expanding explicitly:

$$
\Omega_{\text{TF}}[n] = C_1 \int d^3r\, n^{5/3} + \int d^3r\, V_{\text{ext}}\, n + C_2 \int d^3r\, n^{4/3} + \frac{1}{2}\int d^3r\, d^3r'\, \frac{n\, n'}{|\mathbf{r} - \mathbf{r}'|} - \mu \int d^3r\, n + \mu N
$$

**Computing the first variation.** Consider a small variation $n(\mathbf{r}) \to n(\mathbf{r}) + \delta n(\mathbf{r})$. We need $\Omega_{\text{TF}}[n + \delta n] - \Omega_{\text{TF}}[n] = 0$ to first order in $\delta n$ for all admissible variations.

*Variation of the kinetic term.* Factor out $n^{5/3}$ and use the binomial expansion $(1+x)^\alpha \approx 1 + \alpha x$ for small $x = \delta n / n$:

$$
\begin{aligned}
(n+\delta n)^{5/3}
&= n^{5/3}\left(\frac{n+\delta n}{n}\right)^{5/3} \\
&= n^{5/3}\left(1+\frac{\delta n}{n}\right)^{5/3} \\
&\approx n^{5/3}\left(1+\frac{5}{3}\frac{\delta n}{n}\right) \\
&= n^{5/3} + \frac{5}{3}\,n^{2/3}\,\delta n
\end{aligned}
$$

Therefore

$$
\begin{aligned}
\delta T_{\text{TF}}
&= C_1 \int d^3r\,\left[\left(n^{5/3} + \frac{5}{3}\,n^{2/3}\,\delta n\right) - n^{5/3}\right] \\
&= C_1 \int d^3r\, \frac{5}{3}\, n(\mathbf{r})^{2/3}\, \delta n(\mathbf{r})
\end{aligned}
$$

*Variation of the external potential term.* This term is already linear in $n$, so:

$$
\delta E_{\text{ext}} = \int d^3r\, V_{\text{ext}}(\mathbf{r})\, \delta n(\mathbf{r})
$$

*Variation of the exchange term.* The same binomial expansion with exponent $4/3$:

$$
\begin{aligned}
(n+\delta n)^{4/3}
&= n^{4/3}\left(1+\frac{\delta n}{n}\right)^{4/3} \\
&\approx n^{4/3}\left(1+\frac{4}{3}\frac{\delta n}{n}\right) \\
&= n^{4/3} + \frac{4}{3}\,n^{1/3}\,\delta n
\end{aligned}
$$

Hence

$$
\begin{aligned}
\delta E_x
&= C_2 \int d^3r\,\left[\left(n^{4/3} + \frac{4}{3}\,n^{1/3}\,\delta n\right) - n^{4/3}\right] \\
&= C_2 \int d^3r\, \frac{4}{3}\, n(\mathbf{r})^{1/3}\, \delta n(\mathbf{r})
\end{aligned}
$$

*Variation of the Hartree term.* Expand the product in the numerator:

$$
\begin{aligned}
(n+\delta n)(n'+\delta n') &= n\,n' + n\,\delta n' + n'\,\delta n + \delta n\,\delta n'
\end{aligned}
$$

Substituting and dropping the second-order term $\delta n\,\delta n'$:

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n\,\delta n' + n'\,\delta n}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

Separate the two integrals:

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\,\delta n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}
\;+\; \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

In the first integral, interchange the dummy variables $\mathbf{r} \leftrightarrow \mathbf{r}'$. Because $d^3r\,d^3r'$ is symmetric and $|\mathbf{r}-\mathbf{r}'| = |\mathbf{r}'-\mathbf{r}|$:

$$
\begin{aligned}
\frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\,\delta n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}
&= \frac{1}{2}\int d^3r'\, d^3r\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}'-\mathbf{r}|} \\
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

The two terms are identical, so they combine:

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \left(\frac{1}{2}+\frac{1}{2}\right) \int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|} \\
&= \int d^3r\, \delta n(\mathbf{r}) \left[\int d^3r'\,\frac{n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}\right]
\end{aligned}
$$

Defining the Hartree potential $V_{\text{Hartree}}(\mathbf{r}) \equiv \int d^3r'\, \frac{n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}$:

$$
\delta E_{\text{Hartree}} = \int d^3r\, V_{\text{Hartree}}(\mathbf{r})\, \delta n(\mathbf{r})
$$

*Variation of the constraint term:*

$$
\delta(-\mu \int d^3r\, n) = -\mu \int d^3r\, \delta n(\mathbf{r})
$$

**Assembling the total variation.** Combining all terms:

$$
\delta \Omega_{\text{TF}} = \int d^3r\, \left[\frac{5}{3} C_1\, n(\mathbf{r})^{2/3} + V_{\text{ext}}(\mathbf{r}) + \frac{4}{3} C_2\, n(\mathbf{r})^{1/3} + V_{\text{Hartree}}(\mathbf{r}) - \mu \right] \delta n(\mathbf{r})
$$

By the fundamental lemma of the calculus of variations, $\delta \Omega_{\text{TF}} = 0$ for all $\delta n(\mathbf{r})$ requires the bracketed expression to vanish identically:

$$
\frac{5}{3} C_1\, n(\mathbf{r})^{2/3} + V_{\text{ext}}(\mathbf{r}) + \frac{4}{3} C_2\, n(\mathbf{r})^{1/3} + V_{\text{Hartree}}(\mathbf{r}) = \mu
$$

**Simplifying the kinetic prefactor.** Substituting $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$:

$$
\begin{aligned}
\frac{5}{3} \cdot \frac{3}{10}(3\pi^2)^{2/3}\, n^{2/3}
&= \frac{5}{10}(3\pi^2)^{2/3}\, n^{2/3} \\
&= \frac{1}{2}(3\pi^2)^{2/3}\, n^{2/3} \\
&= \frac{1}{2}k_F^2 \\
&= \varepsilon_F
\end{aligned}
$$

where we used $k_F = (3\pi^2 n)^{1/3}$ and the last line holds in atomic units ($\hbar^2/2m_e = 1/2$).

**The Thomas-Fermi equation.** Defining $V_x(\mathbf{r}) = \frac{4}{3}C_2\, n(\mathbf{r})^{1/3}$ and the total effective potential $V(\mathbf{r}) = V_{\text{ext}}(\mathbf{r}) + V_{\text{Hartree}}(\mathbf{r}) + V_x(\mathbf{r})$, the stationarity condition becomes

$$
\boxed{\frac{1}{2}(3\pi^2)^{2/3}\, n(\mathbf{r})^{2/3} + V(\mathbf{r}) = \mu}
$$

This is the Thomas-Fermi equation (Eq. 6.5). It is self-consistent: the density $n(\mathbf{r})$ determines $V_{\text{Hartree}}$ and $V_x$, which determine $V(\mathbf{r})$, which in turn determines $n(\mathbf{r})$.

**Physical meaning of $\mu$.** The Lagrange multiplier $\mu$ is the **chemical potential** of the electron system — the energy cost of adding one more electron while keeping the external potential fixed:

$$
\mu = \left(\frac{\partial E}{\partial N}\right)_{V_{\text{ext}}}
$$

At zero temperature, the chemical potential of a system of noninteracting fermions equals the **Fermi energy** $\varepsilon_F$. This can be seen directly from the Thomas-Fermi equation: rearranging gives $\frac{1}{2}(3\pi^2 n)^{2/3} = \mu - V(\mathbf{r})$, which says that the local kinetic energy of the fastest electron at position $\mathbf{r}$ plus the local potential $V(\mathbf{r})$ equals the constant $\mu$ everywhere. This is exactly the statement that $\mu$ is the total energy of an electron at the Fermi level. In regions where $V(\mathbf{r}) > \mu$, the density vanishes (classically forbidden), since the kinetic energy cannot be negative.

##### Part (c) — The Hartree Energy: The $\frac{1}{2}$ Prefactor and Missing Physics

**The $\frac{1}{2}$ prefactor.** The Hartree double integral $\int d^3r\, d^3r'$ runs over all pairs $(\mathbf{r}, \mathbf{r}')$, counting every pair twice: once as $(\mathbf{r}, \mathbf{r}')$ and once as $(\mathbf{r}', \mathbf{r})$. The factor of $\frac{1}{2}$ corrects for this double counting. The true pairwise interaction energy sums over each pair once:

$$
E_{\text{pair}} = \sum_{i < j} \frac{e^2}{|\mathbf{r}_i - \mathbf{r}_j|}
$$

In the continuum limit, the ordered sum $\sum_{i<j}$ becomes $\frac{1}{2}\sum_{i \neq j}$, which gives the $\frac{1}{2}$ in front of the double integral.

**Why $n(\mathbf{r})n(\mathbf{r}')$ is a mean-field approximation.** The true quantum-mechanical interaction energy involves the **pair density** $n_2(\mathbf{r}, \mathbf{r}')$ — the probability of finding one electron at $\mathbf{r}$ and another simultaneously at $\mathbf{r}'$:

$$
E_{\text{int}} = \frac{1}{2} \int d^3r\, d^3r'\, \frac{n_2(\mathbf{r}, \mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}
$$

The Hartree approximation replaces $n_2(\mathbf{r}, \mathbf{r}') \approx n(\mathbf{r})\, n(\mathbf{r}')$, assuming the probability of finding an electron at $\mathbf{r}'$ is independent of whether there is already one at $\mathbf{r}$. This is the mean-field assumption: each electron moves in the average field of all the others, with no awareness of any particular electron's position.

**Missing physical effects.** Writing $n_2(\mathbf{r}, \mathbf{r}') = n(\mathbf{r})\, n(\mathbf{r}') + \Delta n_2(\mathbf{r}, \mathbf{r}')$, the Hartree energy misses the entire $\Delta n_2$ contribution, which contains three effects:

*Exchange.* The Pauli exclusion principle requires antisymmetry of the wavefunction, forcing it to vanish when two same-spin electrons coincide. This creates the exchange hole — a depletion of same-spin density around each electron — lowering the Coulomb repulsion. The product $n(\mathbf{r})n(\mathbf{r}')$ ignores the antisymmetry constraint entirely.

*Correlation.* Beyond exchange, electrons dynamically avoid each other due to Coulomb repulsion. The probability of finding two electrons close together is reduced even for opposite-spin pairs. The uncorrelated product contains no information about this dynamical avoidance.

*Self-interaction.* The double integral includes contributions where the same electron appears at both $\mathbf{r}$ and $\mathbf{r}'$ — each electron spuriously interacts with itself. For $N = 1$, the Hartree energy is nonzero even though there is no other electron. In the exact theory, exchange cancels the self-interaction for each orbital, but in the Hartree approximation this cancellation is absent.

##### Part (d) — The Weizsäcker Correction

The Weizsäcker correction is

$$
T_W[n] = \frac{1}{4}\int d^3r\, \frac{|\nabla n(\mathbf{r})|^2}{n(\mathbf{r})}
$$

**Why it is a gradient correction.** The Thomas-Fermi kinetic energy $T_{\text{TF}} = C_1 \int d^3r\, n^{5/3}$ depends only on the local value of the density at each point, assuming the density is locally uniform. The Weizsäcker correction depends on $\nabla n$, the spatial gradient of the density, and therefore goes beyond the local approximation by incorporating information about how rapidly the density varies from point to point.

**Physical meaning of $|\nabla n|/n$.** The ratio $|\nabla n(\mathbf{r})|/n(\mathbf{r})$ is the fractional rate of change of the density — equivalently, $|\nabla \ln n|$. It has dimensions of inverse length. If the density varies on a characteristic length scale $\ell$, then $|\nabla n|/n \sim 1/\ell$, and the correction is large when the density varies rapidly (small $\ell$).

The Weizsäcker integrand can be rewritten by substituting $\phi = n^{1/2}$:

$$
\begin{aligned}
\frac{|\nabla n|^2}{4n}
&= \frac{|2\phi\,\nabla\phi|^2}{4\phi^2} \\
&= |\nabla \phi|^2
\end{aligned}
$$

so $T_W = \int d^3r\, |\nabla n^{1/2}|^2$. This is the exact kinetic energy of a single-particle wavefunction $\phi(\mathbf{r}) = n^{1/2}(\mathbf{r})$ in atomic units — the exact kinetic energy for a single fermion, or equivalently for noninteracting bosons all in the same orbital.

**Where the correction is largest.** Consider a hydrogen-like atom with nuclear charge $Z$.

*Near the nucleus:* The density falls off as $n(r) \sim e^{-2Zr}$, giving $|\nabla n|/n = 2Z$, which is large (especially for heavy atoms). The density has a cusp at the nucleus, and the assumption of local uniformity fails most dramatically here. The correction is largest in this region.

*In the valence region:* The density varies on the scale of bond lengths or the atomic radius, so $|\nabla n|/n$ is moderate.

*Far from the atom:* The density decays as $n(r) \sim e^{-2\kappa r}$ where $\kappa = \sqrt{2|\varepsilon|}$ and $\varepsilon$ is the outermost binding energy. Then $|\nabla n|/n = 2\kappa$ is constant, but the integrand $|\nabla n|^2/n = 4\kappa^2 n \to 0$ exponentially because $n$ itself vanishes. The relative inhomogeneity is finite, but the absolute contribution to the integral is negligible.

##### Part (e) — Failure of the TFD Approximation and Motivation for Kohn-Sham

The Thomas-Fermi kinetic energy $T_{\text{TF}} = C_1 \int d^3r\, n^{5/3}$ depends on the density at each point independently — the kinetic energy density at $\mathbf{r}$ is determined entirely by $n(\mathbf{r})$, with no reference to the quantum state of the system.

But the true kinetic energy is

$$
T = -\frac{1}{2}\sum_{i=1}^{N} \int d^3r\, \psi_i^*(\mathbf{r})\, \nabla^2 \psi_i(\mathbf{r})
$$

which depends on the individual orbitals $\psi_i$ — specifically, on their curvature $\nabla^2 \psi_i$. Two systems can have the same density $n(\mathbf{r}) = \sum_i |\psi_i(\mathbf{r})|^2$ at every point while having completely different sets of occupied orbitals, and therefore completely different kinetic energies. The local approximation $n^{5/3}$ cannot distinguish between these situations because it has discarded all orbital information.

Atomic shell structure is a direct consequence of orbital structure. The $1s$, $2s$, $2p$, $3s$, ... orbitals have different numbers of radial nodes, angular momenta, and spatial extents. The shell structure visible in the radial density $4\pi r^2 n(r)$ arises from the interference between different orbital contributions. A functional that knows only $n(\mathbf{r})$ pointwise cannot reconstruct this structure.

Molecular binding fails for a related reason. Bond formation involves the rearrangement of orbitals into bonding and antibonding combinations, lowering the kinetic energy through delocalization. The Thomas-Fermi functional, which evaluates kinetic energy pointwise from the density, cannot detect whether the electrons at a given point are localized on one atom or delocalized across a bond. Teller's no-binding theorem (1962) makes this precise: within the Thomas-Fermi approximation, the total energy of any collection of atoms is minimized at infinite separation. No molecule or solid is bound.

This failure demonstrates that any practical density functional theory must reintroduce orbital information. This is precisely what Kohn and Sham accomplished (Chapter 7): they introduced an auxiliary system of noninteracting electrons that reproduces the true ground-state density, computing the kinetic energy of this system exactly using its orbitals. The remaining corrections (exchange and correlation) are small enough to be modeled as approximate functionals of the density. This sidesteps the central failing of Thomas-Fermi while preserving the simplicity of working with the density for the interaction terms.

---

# Exercise 6.3 — The Hohenberg-Kohn Theorems and the Energy Functional

> [!exercise] The Hohenberg-Kohn Theorems and the Energy Functional
> The Hohenberg-Kohn theorems (1964) elevated density functional theory from an approximation to an exact reformulation of the many-body problem. The starting point is the many-body Hamiltonian $\hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}}$ (Eq. 6.6), where $\hat{T} = -\frac{\hbar^2}{2m_e}\sum_i \nabla_i^2$ is the kinetic energy, $\hat{V}_{\text{ext}} = \sum_i V_{\text{ext}}(\mathbf{r}_i)$ is the external potential, and $\hat{V}_{\text{int}} = \frac{1}{2}\sum_{i \neq j} e^2/|\mathbf{r}_i - \mathbf{r}_j|$ is the electron-electron Coulomb repulsion.
>
> (a) Classify each of the three terms in the Hamiltonian as universal (the same for all electron systems) or system-specific (changes from one material to another). Which term distinguishes CeO₂ from silicon from hydrogen? Write the expectation value of $\hat{V}_{\text{ext}}$ in terms of the density. What is special about the mathematical structure of this coupling that gives the density its privileged role in the Hohenberg-Kohn theorems?
>
> (b) State Hohenberg-Kohn Theorem I precisely. Now prove it by contradiction: suppose two external potentials $V_{\text{ext}}^{(1)}$ and $V_{\text{ext}}^{(2)}$ (differing by more than a constant) give rise to the same ground-state density $n_0$. Using the variational principle, derive an inequality relating $E^{(1)}$ and $E^{(2)}$, then exploit the symmetry of the argument to reach a contradiction. What assumption about the ground state is needed for the strict inequality?
>
> (c) State Hohenberg-Kohn Theorem II. Construct the Hohenberg-Kohn energy functional $E_{\text{HK}}[n]$ (Eq. 6.12) by separating it into a part that depends on the external potential and a part that does not. Define the universal functional $F_{\text{HK}}[n]$ (Eq. 6.13) and explain what makes it "universal." Show that $E_{\text{HK}}$ obeys a variational inequality for any trial density. What does this provide that Theorem I alone does not?
>
> (d) Despite their power, the Hohenberg-Kohn theorems provide no practical recipe for solving the electronic structure problem. Explain why these theorems, as they stand, are existence proofs rather than computational methods. What is still missing that prevents you from using them to calculate the energy of a real material?

---

# Exercise 6.4 — The Levy-Lieb Constrained Search and the Domain of the Functional

> [!exercise] The Levy-Lieb Constrained Search and the Domain of the Functional
> The Levy-Lieb constrained search (Levy 1979, Lieb 1983) provides an alternative definition of the universal energy functional that is both more intuitive and more general than the original Hohenberg-Kohn formulation. The central idea is a two-step minimization: first minimize the kinetic-plus-interaction energy over all wavefunctions that produce a given density, then minimize the resulting functional over all densities.
>
> (a) Write the Levy-Lieb functional $F_{\text{LL}}[n]$ (Eq. 6.18). Explain in words what the constrained minimization means — what set of objects are you searching over, what quantity are you minimizing, and what constraint must each candidate satisfy? Why does this construction define a functional of the density?
>
> (b) The Hohenberg-Kohn functional $F_{\text{HK}}[n]$ and the Levy-Lieb functional $F_{\text{LL}}[n]$ are defined on different domains. Define $V$-representability and $N$-representability, explain which is more restrictive, and give a physical argument for why. Why does the choice of domain matter when performing a variational minimization over densities?
>
> (c) At the energy minimum — where the density is the ground-state density $n_0(\mathbf{r})$ — the Levy-Lieb functional equals the Hohenberg-Kohn functional: $F_{\text{LL}}[n_0] = F_{\text{HK}}[n_0]$. Explain why this must be the case. What property of $n_0$ guarantees that both functionals are defined and agree at the minimum?
>
> (d) Give an example of a density that is $N$-representable but not $V$-representable. (Hint: consider the spherically averaged density of an open-shell atom, or the density of an excited state of a particle in a box.) Why can such densities be produced by a wavefunction but not as the ground state of any local potential?

---

# Exercise 6.5 — Extensions: Spin Density, Finite Temperature, and the Derivative Discontinuity

> [!exercise] Extensions: Spin Density, Finite Temperature, and the Derivative Discontinuity
> The Hohenberg-Kohn framework can be extended beyond the original ground-state, spin-unpolarized, time-reversal-invariant setting. These extensions are essential for practical calculations on magnetic materials, finite-temperature systems, and systems in external magnetic fields.
>
> (a) Consider a system with an external Zeeman field that couples differently to up-spin and down-spin electrons. The Hamiltonian now includes terms of the form $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$ and $\int h(\mathbf{r})\,s(\mathbf{r})\,d^3r$, where $s(\mathbf{r}) = n(\mathbf{r},\uparrow) - n(\mathbf{r},\downarrow)$ is the spin density. By the same logic as the original Hohenberg-Kohn argument, explain why the energy functional must now depend on both $n(\mathbf{r})$ and $s(\mathbf{r})$: $E = E_{\text{HK}}[n, s]$ (Eq. 6.19). In the absence of an external Zeeman field, does the original Hohenberg-Kohn theorem (energy as a functional of total $n$ alone) still hold for a spin-polarized ground state? If so, why is spin density functional theory still preferred in practice for magnetic systems like ceria?
>
> (b) Mermin (1965) extended the Hohenberg-Kohn theorems to finite temperature. Write the Mermin grand potential functional $\Omega[\hat{\rho}]$ (Eq. 6.20) and define all symbols. The functional splits naturally into two pieces — identify what each piece represents physically. What additional thermodynamic properties — beyond the ground-state energy — does the Mermin theorem guarantee are functionals of the equilibrium density?
>
> (c) When time-reversal symmetry is broken by a magnetic field coupling to orbital motion, the Hamiltonian includes a term $\mathbf{p} \cdot \mathbf{A}_{\text{ext}}$. Explain why the original Hohenberg-Kohn theorems — which establish $n(\mathbf{r})$ as the sole basic variable — are insufficient in this case. What additional quantity must the functional depend on, and why does the standard variational principle (for the ground-state energy) not carry over directly to this time-dependent or current-carrying setting?
>
> (d) From ensemble theory, the energy of the exact density functional must have discontinuities in its derivative with respect to electron number at integer occupations — the derivative discontinuity. Explain in physical terms what this means: why should the energy cost of adding the $(N+1)$-th electron differ from the energy gained by removing the $N$-th? Why is this property absent in present-day approximate functionals like LDA and GGA, and what observable consequence does this absence have for calculated band gaps?

---

# Exercise 6.6 — Allowed Densities and Properties of the Exact Functional

> [!exercise] Allowed Densities and Properties of the Exact Functional
> The formal power of the Hohenberg-Kohn theorems guarantees that the exact energy functional, if known, would give all ground-state properties correctly. But what does "all properties" actually encompass, and what subtleties arise when one asks precisely which properties are determined by the density?
>
> (a) Consider the homogeneous electron gas. All plane-wave Slater determinants produce the same uniform density, yet only the set of lowest-energy plane waves gives the ground state. More generally, many different wavefunctions can produce the same density $n(\mathbf{r})$. Explain why this multiplicity does not undermine the Hohenberg-Kohn theorems. What is it about the *ground-state* density that makes the density-to-potential map unique, even though arbitrary densities admit many wavefunctions?
>
> (b) Gilbert showed that any density satisfying $n(\mathbf{r}) \geq 0$ and $\int |\nabla n^{1/2}|^2 < \infty$ is $N$-representable — it can be obtained from an antisymmetric wavefunction. These conditions are mild. In contrast, $V$-representable densities form a smaller, less well-characterized set. Give a physical example of a density that is $N$-representable but not $V$-representable. (Hint: consider the density of the 2s excited state of hydrogen, or the spherically averaged density of an open-shell atom.)
>
> (c) Are excitation energies given correctly by the exact ground-state density functional theory? There are two reasonable answers to this question, and they appear to contradict each other. Give both, explain the sense in which each is correct, and resolve the apparent contradiction. Why does the formal content of Theorem I not translate into a practical method for computing excitation spectra?
>
> (d) Is the exact Fermi surface of a metal determined by the exact ground-state density functional? At first glance this seems unlikely, since the Fermi surface involves the topology of occupied states in momentum space — seemingly a property of wavefunctions, not densities. Construct an argument that the answer is in fact yes. (Hint: think about what physical observables depend on the Fermi surface geometry, and whether the exact functional must reproduce them.)

---

# Exercise 6.7 — Nonanalyticity of the Exact Functional and the Limits of Explicit Density Functionals

> [!exercise] Nonanalyticity of the Exact Functional and the Limits of Explicit Density Functionals
> Although the Hohenberg-Kohn theorems guarantee that the exact energy can be written as a functional of the density, they provide no guidance on the form of this functional. This exercise explores why constructing explicit density functionals is fundamentally difficult, and why the Kohn-Sham strategy of working through orbitals is not merely convenient but essential.
>
> (a) Consider the simplest possible case: $N$ noninteracting electrons in an external potential, so that the exact universal functional reduces to the kinetic energy alone. Can this kinetic energy $T_s[n]$ be evaluated as an explicit functional of the density, or does the evaluation require additional information beyond $n(\mathbf{r})$? Explain your reasoning. What does the answer imply about any practical computational scheme for density functional theory?
>
> (b) The kinetic energy of noninteracting electrons has derivatives that are discontinuous at integer occupation numbers. From the virial theorem (which relates kinetic and potential energies), show conceptually why all parts of the exact functional — kinetic and potential — must vary nonanalytically as a function of electron number. Why is this nonanalyticity a property of a global integral of the density rather than something that can be determined by examining the density at any single point?
>
> (c) In solids, the electron density is remarkably similar to sums of overlapping atomic densities. Even for well-known ionic crystals, the total density does not obviously distinguish the crystal from a collection of neutral atoms. Given this, explain why it is so difficult to determine from the density alone whether a material is a metal or an insulator. What key physical property distinguishes metals from insulators, and where does that property originate — from a local feature of the density, or from something else entirely?
>
> (d) The Kohn-Sham approach treats the kinetic energy through single-particle orbitals rather than as an explicit functional of the density. Explain how this strategy captures quantum properties (shell structure, band gaps, bonding) that have no simple relation to the density. What is the trade-off: what additional computational machinery does the Kohn-Sham approach introduce that a pure Thomas-Fermi-type density functional does not require?
