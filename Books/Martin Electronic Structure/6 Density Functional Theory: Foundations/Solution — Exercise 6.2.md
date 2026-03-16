# Solution — Exercise 6.2: The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization

Electronic Structure Vault

---

## (a) The Four Terms of the Thomas-Fermi-Dirac Energy Functional

The Thomas-Fermi-Dirac energy functional is

$$
E_{\text{TF}}[n] = C_1 \int d^3r\, n(\mathbf{r})^{5/3} + \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + C_2 \int d^3r\, n(\mathbf{r})^{4/3} + \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\, n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}
$$

where $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$ and $C_2 = -\frac{3}{4}\left(\frac{3}{\pi}\right)^{1/3}$.

We now identify each term.

---

**Term 1: Local kinetic energy** — $T_{\text{TF}}[n] = C_1 \int d^3r\, n(\mathbf{r})^{5/3}$

This term approximates the total quantum-mechanical kinetic energy of the electrons. The approximation being made is the *local density approximation for the kinetic energy*: at each point $\mathbf{r}$, the kinetic energy density is taken to be that of a *uniform, noninteracting electron gas* whose density equals the local density $n(\mathbf{r})$ at that point.

To see where the $n^{5/3}$ scaling comes from, recall that for a free electron gas at zero temperature, the Fermi wavevector is

$$
k_F = (3\pi^2 n)^{1/3}
$$

and the kinetic energy per unit volume is

$$
\frac{T}{V} = \frac{3}{5} n \cdot \frac{\hbar^2 k_F^2}{2m_e} = \frac{3}{5} n \cdot \frac{\hbar^2}{2m_e}(3\pi^2 n)^{2/3} = \frac{3}{10}\frac{\hbar^2}{m_e}(3\pi^2)^{2/3}\, n^{5/3}
$$

In atomic units ($\hbar = m_e = e = 1$), this gives $C_1 = \frac{3}{10}(3\pi^2)^{2/3} \approx 2.871$.

The approximation *replaces the true quantum-mechanical kinetic energy* — which depends on the full set of single-particle wavefunctions — *with a local functional of the density alone*. This throws away all information about the orbital structure of the system.

---

**Term 2: External potential energy** — $E_{\text{ext}}[n] = \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r})$

This term gives the energy of interaction between the electrons and the external potential (typically the Coulomb potential of the nuclei). No approximation is made here — this is exact. The energy of a charge distribution $n(\mathbf{r})$ in an external potential $V_{\text{ext}}(\mathbf{r})$ is simply the integral of the potential weighted by the density. This bilinear coupling between $V_{\text{ext}}$ and $n$ is exact because $V_{\text{ext}}$ is a one-body operator:

$$
\langle \Psi | \hat{V}_{\text{ext}} | \Psi \rangle = \left\langle \Psi \left| \sum_{i=1}^{N} V_{\text{ext}}(\mathbf{r}_i) \right| \Psi \right\rangle = \int d^3r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r})
$$

where the last step follows directly from the definition of the electron density $n(\mathbf{r}) = N \int d^3r_2 \cdots d^3r_N\, |\Psi(\mathbf{r}, \mathbf{r}_2, \ldots, \mathbf{r}_N)|^2$.

---

**Term 3: Local exchange energy (Dirac exchange)** — $E_x[n] = C_2 \int d^3r\, n(\mathbf{r})^{4/3}$

This term approximates the exchange energy arising from the antisymmetry (Pauli exclusion) of the electronic wavefunction. The approximation is again a local density approximation: at each point $\mathbf{r}$, the exchange energy density is taken to be that of a *uniform electron gas* with density $n(\mathbf{r})$.

The $n^{4/3}$ scaling can be understood dimensionally. Exchange is a Coulomb effect (energy $\sim e^2/r$) involving electrons separated by a characteristic distance set by the mean interelectron spacing $r_s \sim n^{-1/3}$. Therefore the exchange energy per electron scales as $e^2/r_s \sim n^{1/3}$, and the exchange energy *per unit volume* scales as $n \cdot n^{1/3} = n^{4/3}$.

The constant $C_2 = -\frac{3}{4}\left(\frac{3}{\pi}\right)^{1/3}$ is negative, reflecting the fact that exchange *lowers* the energy: antisymmetry keeps same-spin electrons apart, reducing their Coulomb repulsion.

This approximation neglects the fact that in a real, inhomogeneous system the exchange hole (the depletion of same-spin electron density around each electron) has a shape that depends on the local electronic structure, not just on the local value of the density.

---

**Term 4: Hartree energy (classical electrostatic energy)** — $E_{\text{Hartree}}[n] = \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\, n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}$

This term is the classical electrostatic self-energy of the charge distribution $n(\mathbf{r})$. It approximates the full quantum-mechanical electron-electron Coulomb repulsion by treating the electrons as a continuous, classical charge cloud — each infinitesimal element of charge $n(\mathbf{r})\,d^3r$ interacts with every other element $n(\mathbf{r}')\,d^3r'$ via the Coulomb potential $1/|\mathbf{r} - \mathbf{r}'|$.

The approximation being made is the *mean-field approximation*: the quantum-mechanical pair correlation between electrons is ignored. In the true system, the probability of finding an electron at $\mathbf{r}'$ given one at $\mathbf{r}$ is *not* simply $n(\mathbf{r}')$; it is modified by exchange (antisymmetry) and correlation (dynamical avoidance). The Hartree energy replaces the true pair density with the uncorrelated product $n(\mathbf{r})n(\mathbf{r}')$.

---

## (b) Constrained Minimization and the Thomas-Fermi Equation

We seek the density $n(\mathbf{r})$ that minimizes $E_{\text{TF}}[n]$ subject to the constraint that the total number of particles is fixed:

$$
\int d^3r\, n(\mathbf{r}) = N
$$

**Step 1. Construct the unconstrained functional using a Lagrange multiplier.**

Introduce a Lagrange multiplier $\mu$ and define the unconstrained functional

$$
\Omega_{\text{TF}}[n] = E_{\text{TF}}[n] - \mu \left( \int d^3r\, n(\mathbf{r}) - N \right)
$$

Expanding $E_{\text{TF}}[n]$ explicitly:

$$
\Omega_{\text{TF}}[n] = C_1 \int d^3r\, n^{5/3} + \int d^3r\, V_{\text{ext}}\, n + C_2 \int d^3r\, n^{4/3} + \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}) n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|} - \mu \int d^3r\, n + \mu N
$$

**Step 2. Consider a small variation $n(\mathbf{r}) \to n(\mathbf{r}) + \delta n(\mathbf{r})$.**

The stationarity condition requires $\Omega_{\text{TF}}[n + \delta n] - \Omega_{\text{TF}}[n] = 0$ to first order in $\delta n$ for *all* variations $\delta n(\mathbf{r})$.

We compute the first-order change in each term separately.

---

**Variation of Term 1:** $\delta T_{\text{TF}} = C_1 \int d^3r\, \left[(n + \delta n)^{5/3} - n^{5/3}\right]$

Expand explicitly to first order. Factor out $n^{5/3}$ and use $(1+x)^\alpha \approx 1 + \alpha x$ for small $x = \delta n/n$:

$$
\begin{aligned}
(n+\delta n)^{5/3}
&= n^{5/3}\left(\frac{n+\delta n}{n}\right)^{5/3} \\
&= n^{5/3}\left(1+\frac{\delta n}{n}\right)^{5/3} \\
&\approx n^{5/3}\left(1+\frac{5}{3}\frac{\delta n}{n}\right) \\
&= n^{5/3} + \frac{5}{3}n^{5/3}\frac{\delta n}{n} \\
&= n^{5/3} + \frac{5}{3}\,n^{2/3}\,\delta n
\end{aligned}
$$

where terms of order $(\delta n)^2$ and higher have been dropped. Therefore,

$$
\begin{aligned}
\delta T_{\text{TF}}
&= C_1 \int d^3r\,\left[\left(n^{5/3} + \frac{5}{3}\,n^{2/3}\,\delta n\right) - n^{5/3}\right] \\
&= C_1 \int d^3r\, \frac{5}{3}\, n(\mathbf{r})^{2/3}\, \delta n(\mathbf{r})
\end{aligned}
$$

---

**Variation of Term 2:** $\delta E_{\text{ext}} = \int d^3r\, V_{\text{ext}}(\mathbf{r})\, \delta n(\mathbf{r})$

This is already linear in $n$, so the variation is immediate.

---

**Variation of Term 3:** $\delta E_x = C_2 \int d^3r\, \left[(n + \delta n)^{4/3} - n^{4/3}\right]$

Again expand explicitly to first order:

$$
\begin{aligned}
(n+\delta n)^{4/3}
&= n^{4/3}\left(\frac{n+\delta n}{n}\right)^{4/3} \\
&= n^{4/3}\left(1+\frac{\delta n}{n}\right)^{4/3} \\
&\approx n^{4/3}\left(1+\frac{4}{3}\frac{\delta n}{n}\right) \\
&= n^{4/3} + \frac{4}{3}n^{4/3}\frac{\delta n}{n} \\
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

---

**Variation of Term 4:** $\delta E_{\text{Hartree}} = \frac{1}{2}\int d^3r\, d^3r'\, \frac{(n + \delta n)(n' + \delta n') - n\, n'}{|\mathbf{r} - \mathbf{r}'|}$

Now expand the numerator in full:

$$
\begin{aligned}
(n+\delta n)(n'+\delta n') &= n\,n' + n\,\delta n' + n'\,\delta n + \delta n\,\delta n'
\end{aligned}
$$

Substituting this into the variation gives

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n\,n' + n\,\delta n' + n'\,\delta n + \delta n\,\delta n' - n\,n'}{|\mathbf{r}-\mathbf{r}'|} \\
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n\,\delta n' + n'\,\delta n + \delta n\,\delta n'}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

Now drop the second-order term $\delta n\,\delta n'$, since only first-order terms are kept in the first variation:

$$
\delta E_{\text{Hartree}} = \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\,\delta n(\mathbf{r}') + n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
$$

Separate the two integrals:

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\,\delta n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}
\;+\; \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

In the first integral, interchange the dummy variables $\mathbf{r} \leftrightarrow \mathbf{r}'$. Because $d^3r\,d^3r'$ is unchanged and $|\mathbf{r}-\mathbf{r}'| = |\mathbf{r}'-\mathbf{r}|$, one gets

$$
\begin{aligned}
\frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r})\,\delta n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}
&= \frac{1}{2}\int d^3r'\, d^3r\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}'-\mathbf{r}|} \\
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

Therefore the two terms are equal, so

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\;+\; \frac{1}{2}\int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|} \\
&= \left(\frac{1}{2}+\frac{1}{2}\right) \int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|} \\
&= \int d^3r\, d^3r'\, \frac{n(\mathbf{r}')\,\delta n(\mathbf{r})}{|\mathbf{r}-\mathbf{r}'|}
\end{aligned}
$$

Now pull $\delta n(\mathbf{r})$ outside the $\mathbf{r}'$-integral:

$$
\begin{aligned}
\delta E_{\text{Hartree}}
&= \int d^3r\, \delta n(\mathbf{r}) \left[\int d^3r'\,\frac{n(\mathbf{r}')}{|\mathbf{r}-\mathbf{r}'|}\right]
\end{aligned}
$$

Define the Hartree potential by

$$
V_{\text{Hartree}}(\mathbf{r}) \equiv \int d^3r'\, \frac{n(\mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}
$$

So:

$$
\delta E_{\text{Hartree}} = \int d^3r\, V_{\text{Hartree}}(\mathbf{r})\, \delta n(\mathbf{r})
$$

---

**Variation of the constraint term:** $\delta(-\mu \int d^3r\, n) = -\mu \int d^3r\, \delta n(\mathbf{r})$

---

**Step 3. Assemble the total first-order variation.**

Combining all terms:

$$
\delta \Omega_{\text{TF}} = \int d^3r\, \left[\frac{5}{3} C_1\, n(\mathbf{r})^{2/3} + V_{\text{ext}}(\mathbf{r}) + \frac{4}{3} C_2\, n(\mathbf{r})^{1/3} + V_{\text{Hartree}}(\mathbf{r}) - \mu \right] \delta n(\mathbf{r})
$$

**Step 4. Apply the fundamental lemma of the calculus of variations.**

The stationarity condition $\delta \Omega_{\text{TF}} = 0$ must hold for *all* variations $\delta n(\mathbf{r})$. By the fundamental lemma of the calculus of variations, this is possible if and only if the integrand in brackets vanishes identically:

$$
\frac{5}{3} C_1\, n(\mathbf{r})^{2/3} + V_{\text{ext}}(\mathbf{r}) + \frac{4}{3} C_2\, n(\mathbf{r})^{1/3} + V_{\text{Hartree}}(\mathbf{r}) = \mu
$$

**Step 5. Simplify the kinetic term.**

Substituting $C_1 = \frac{3}{10}(3\pi^2)^{2/3}$:

$$
\frac{5}{3} \cdot \frac{3}{10}(3\pi^2)^{2/3}\, n^{2/3} = \frac{5}{10}(3\pi^2)^{2/3}\, n^{2/3} = \frac{1}{2}(3\pi^2)^{2/3}\, n^{2/3}
$$

Recognizing that $(3\pi^2)^{2/3}\, n^{2/3} = [(3\pi^2)^{1/3}\, n^{1/3}]^2 = k_F^2$, this is simply $\frac{1}{2}k_F^2 = \varepsilon_F$, the Fermi energy of a uniform gas with density $n$ (in atomic units where $\hbar^2/2m_e = 1/2$).

**Step 6. Define the total effective potential.**

Let $V_x(\mathbf{r}) = \frac{4}{3}C_2\, n(\mathbf{r})^{1/3}$ be the local exchange potential. Then define the total potential:

$$
V(\mathbf{r}) = V_{\text{ext}}(\mathbf{r}) + V_{\text{Hartree}}(\mathbf{r}) + V_x(\mathbf{r})
$$

**Step 7. Write the Thomas-Fermi equation (Eq. 6.5).**

The stationarity condition becomes:

$$
\boxed{\frac{1}{2}(3\pi^2)^{2/3}\, n(\mathbf{r})^{2/3} + V(\mathbf{r}) = \mu}
$$

This is the Thomas-Fermi equation. It is a self-consistent equation: the density $n(\mathbf{r})$ determines $V_{\text{Hartree}}$ and $V_x$, which in turn determine $V(\mathbf{r})$, which determines $n(\mathbf{r})$ through the equation above.

---

**Physical meaning of $\mu$.**

The Lagrange multiplier $\mu$ is the **chemical potential** of the electron system. To see this, note that $\mu$ enters as the quantity conjugate to the particle number constraint. From thermodynamics, the chemical potential is defined as

$$
\mu = \left(\frac{\partial E}{\partial N}\right)_{V_{\text{ext}}}
$$

which is precisely the role played by the Lagrange multiplier: $\mu$ is the energy cost of adding one more electron to the system while keeping the external potential fixed.

At zero temperature, the chemical potential of a system of noninteracting fermions equals the **Fermi energy** $\varepsilon_F$ — the energy of the highest occupied single-particle state. This can be seen directly from the Thomas-Fermi equation: rearranging gives $\frac{1}{2}(3\pi^2 n)^{2/3} = \mu - V(\mathbf{r})$, which says that the local kinetic energy of the fastest electron at position $\mathbf{r}$ plus the local potential energy $V(\mathbf{r})$ equals the constant $\mu$ everywhere. This is exactly the statement that $\mu$ is the total energy of an electron at the Fermi level. In regions where $V(\mathbf{r}) > \mu$, the density vanishes (classically forbidden region), since the kinetic energy cannot be negative.

---

## (c) The Hartree Energy: The $\frac{1}{2}$ Prefactor and Missing Physics

**The $\frac{1}{2}$ prefactor.**

The Hartree energy counts the Coulomb interaction between every pair of infinitesimal charge elements $n(\mathbf{r})\,d^3r$ and $n(\mathbf{r}')\,d^3r'$. The double integral $\int d^3r\, d^3r'$ runs over *all* pairs $(\mathbf{r}, \mathbf{r}')$, which means it counts every pair *twice*: once as $(\mathbf{r}, \mathbf{r}')$ and once as $(\mathbf{r}', \mathbf{r})$. The factor of $\frac{1}{2}$ corrects for this double counting.

More explicitly, the true pairwise interaction energy is

$$
E_{\text{pair}} = \sum_{i < j} \frac{e^2}{|\mathbf{r}_i - \mathbf{r}_j|}
$$

where the sum runs over each pair once. In the continuum limit, the ordered sum $\sum_{i<j}$ becomes $\frac{1}{2}\sum_{i \neq j}$, and replacing the discrete sum with the density gives the factor of $\frac{1}{2}$ in front of the double integral.

---

**Why $n(\mathbf{r})n(\mathbf{r}')$ is a mean-field, classical approximation.**

The true quantum-mechanical electron-electron interaction energy is

$$
E_{\text{int}} = \frac{1}{2} \int d^3r\, d^3r'\, \frac{n_2(\mathbf{r}, \mathbf{r}')}{|\mathbf{r} - \mathbf{r}'|}
$$

where $n_2(\mathbf{r}, \mathbf{r}')$ is the **pair density** — the probability of finding *simultaneously* one electron at $\mathbf{r}$ and another at $\mathbf{r}'$. In a fully correlated quantum system, $n_2(\mathbf{r}, \mathbf{r}')$ is *not* equal to $n(\mathbf{r})n(\mathbf{r}')$. The Hartree approximation replaces

$$
n_2(\mathbf{r}, \mathbf{r}') \approx n(\mathbf{r})\, n(\mathbf{r}')
$$

This is the assumption that the probability of finding an electron at $\mathbf{r}'$ is *independent* of whether there is already an electron at $\mathbf{r}$. This is exactly the *mean-field* or *classical* approximation: each electron moves in the average field created by all the others, with no awareness of any particular electron's location.

---

**What physical effects are missing.**

We can write the exact pair density as

$$
n_2(\mathbf{r}, \mathbf{r}') = n(\mathbf{r})\, n(\mathbf{r}') + \Delta n_2(\mathbf{r}, \mathbf{r}')
$$

where $\Delta n_2$ contains all the corrections to the uncorrelated product. The Hartree energy misses the entire contribution from $\Delta n_2$, which contains three distinct physical effects:

1. **Exchange.** The Pauli exclusion principle requires that the many-body wavefunction be antisymmetric under the interchange of any two electrons. For same-spin electrons, this forces the wavefunction to vanish when two electrons coincide ($\mathbf{r} = \mathbf{r}'$), creating the *exchange hole* — a region of depleted density of same-spin electrons around each electron. This lowers the Coulomb repulsion energy relative to the Hartree value. The Hartree approximation misses exchange because it treats the pair density as a simple product, ignoring the antisymmetry constraint on the wavefunction.

2. **Correlation.** Even beyond exchange, electrons avoid each other due to their mutual Coulomb repulsion — they are dynamically correlated. The probability of finding two electrons close together is reduced relative to the mean-field prediction, even for opposite-spin electrons (which are not constrained by the Pauli principle). This is *Coulomb correlation*, and it further lowers the energy. The Hartree approximation misses it because the product $n(\mathbf{r})n(\mathbf{r}')$ contains no information about the dynamical avoidance of electron pairs.

3. **Self-interaction.** The Hartree double integral includes the interaction of the density at $\mathbf{r}$ with the density at $\mathbf{r}'$ for *all* $\mathbf{r}'$ — including contributions where the same electron contributes to both $n(\mathbf{r})$ and $n(\mathbf{r}')$. In other words, each electron spuriously interacts with itself. For a single electron ($N = 1$), the Hartree energy is nonzero even though there is no other electron to interact with. In the exact theory, exchange exactly cancels the self-interaction for each orbital. But in the Hartree approximation, this cancellation is absent, leaving a spurious positive energy contribution.

---

## (d) The Weizsäcker Correction

The Weizsäcker correction is

$$
T_W[n] = \frac{1}{4}\int d^3r\, \frac{|\nabla n(\mathbf{r})|^2}{n(\mathbf{r})}
$$

**Why it is called a gradient correction.**

The Thomas-Fermi kinetic energy $T_{\text{TF}}[n] = C_1 \int d^3r\, n^{5/3}$ depends only on the *local value* of the density at each point. It assumes the density is locally uniform — that is, it uses the result for a homogeneous electron gas applied pointwise. The Weizsäcker correction depends on $\nabla n$, the *spatial gradient* of the density, and is therefore a *gradient correction*: it goes beyond the local approximation by incorporating information about how rapidly the density varies from point to point.

**What $|\nabla n|/n$ measures.**

The ratio $|\nabla n(\mathbf{r})|/n(\mathbf{r})$ is the *fractional rate of change* of the density at position $\mathbf{r}$. It has dimensions of inverse length and measures the spatial inhomogeneity of the density on a scale set by the density itself. Equivalently, we can write

$$
\frac{|\nabla n|}{n} = \left|\nabla \ln n \right|
$$

so it is the magnitude of the gradient of the logarithm of the density. If the density varies on a characteristic length scale $\ell$ — meaning $n$ changes by an amount of order $n$ over a distance $\ell$ — then $|\nabla n|/n \sim 1/\ell$. The correction is large when $\ell$ is small, i.e., when the density varies rapidly.

The Weizsäcker integrand can also be rewritten by substituting $n = |\phi|^2$ (where $\phi = n^{1/2}$):

$$
\frac{|\nabla n|^2}{4n} = \frac{|2\phi\,\nabla\phi|^2}{4\phi^2} = |\nabla \phi|^2
$$

so $T_W = \int d^3r\, |\nabla n^{1/2}|^2$. This is precisely the kinetic energy of a single-particle wavefunction $\phi(\mathbf{r}) = n(\mathbf{r})^{1/2}$ (in atomic units). In fact, $T_W$ is the exact kinetic energy for a system of noninteracting bosons all occupying the same orbital $\phi$, or equivalently, the exact kinetic energy for a single fermion.

**Where the correction is largest in an atom.**

Consider a hydrogen-like atom with nuclear charge $Z$. The electron density near the nucleus falls off roughly as $n(r) \sim e^{-2Zr}$ (for the 1s state). Then:

$$
\frac{|\nabla n|}{n} = \frac{|dn/dr|}{n} = 2Z
$$

which is large (especially for heavy atoms with large $Z$). Near the nucleus, the density changes extremely rapidly — it has a cusp — so the gradient correction is large.

In the valence region, the density varies more slowly (on the scale of the bond length or the atomic radius), so $|\nabla n|/n$ is moderate.

Far from the atom, the density decays exponentially as $n(r) \sim e^{-2\kappa r}$ where $\kappa = \sqrt{2|\varepsilon|}$ and $\varepsilon$ is the binding energy of the outermost electron. Then:

$$
\frac{|\nabla n|}{n} = 2\kappa
$$

which is a constant. However, the *integrand* of the Weizsäcker correction is $|\nabla n|^2/n$. In the tail region:

$$
\frac{|\nabla n|^2}{n} = \frac{(2\kappa)^2 n^2}{n} = 4\kappa^2 n
$$

This goes to zero because $n \to 0$ exponentially. So while the *relative* inhomogeneity $|\nabla n|/n$ is finite in the tail, the *absolute contribution* to the kinetic energy integral is small because the density itself is vanishingly small.

The correction is largest **near the nucleus**, where both the density and its gradient are large, and the assumption of local uniformity breaks down most dramatically — the density has a cusp that no locally-uniform model can capture.

---

## (e) Failure of the Thomas-Fermi-Dirac Approximation

**Why the local approximation fails for shell structure and binding.**

The Thomas-Fermi kinetic energy functional $T_{\text{TF}}[n] = C_1 \int d^3r\, n^{5/3}$ depends on the density at each point *independently* — the kinetic energy density at $\mathbf{r}$ is determined entirely by $n(\mathbf{r})$ at that point, with no reference to the quantum state of the system.

But the quantum-mechanical kinetic energy is

$$
T = -\frac{1}{2}\sum_{i=1}^{N} \int d^3r\, \psi_i^*(\mathbf{r})\, \nabla^2 \psi_i(\mathbf{r})
$$

which depends on the individual orbital wavefunctions $\psi_i$ — specifically, on their *curvature* $\nabla^2 \psi_i$. Two systems can have the same density $n(\mathbf{r}) = \sum_i |\psi_i(\mathbf{r})|^2$ at a given point while having completely different sets of occupied orbitals $\{\psi_i\}$, and therefore completely different kinetic energies. The local approximation $n^{5/3}$ cannot distinguish between these two situations because it has thrown away the orbital information.

Atomic shell structure is a direct consequence of the orbital structure of the atom. The $1s$, $2s$, $2p$, $3s$, ... orbitals have different numbers of radial nodes, different angular momenta, and different spatial extents. The shell structure visible in the radial density $4\pi r^2 n(r)$ — the peaks and valleys corresponding to the $K$, $L$, $M$, ... shells — arises from the *interference* between the contributions of different occupied orbitals to the total density. A functional that knows only $n(\mathbf{r})$ at each point, with no memory of which orbitals produced that density, cannot reconstruct this shell structure.

Molecular binding fails for a related reason. The formation of a chemical bond involves the rearrangement of orbital structure — bonding and antibonding combinations of atomic orbitals — that lowers the kinetic energy (through delocalization) while rearranging the potential energy. The energy differences involved are small fractions of the total energy, and getting them right requires accurately capturing the change in kinetic energy when orbitals delocalize from one atom to two. The Thomas-Fermi functional, which evaluates kinetic energy pointwise from the density, cannot detect whether the electrons at a given point are localized on one atom or delocalized across a bond.

Teller's no-binding theorem (1962) makes this precise: within the Thomas-Fermi approximation (even without the Dirac exchange term), the total energy of any collection of atoms is minimized when the atoms are infinitely separated. No molecule or solid is bound. The approximation is simply too coarse to capture the energy lowering that comes from orbital delocalization.

**What this motivates.**

The failure of the Thomas-Fermi approach demonstrates that any practical density functional theory must find a way to reintroduce orbital information — specifically, the kinetic energy must be treated through single-particle wavefunctions rather than as an explicit functional of the density. This is precisely what Kohn and Sham accomplished in 1965 (Chapter 7): they introduced an auxiliary system of noninteracting electrons that reproduces the true ground-state density, and computed the kinetic energy of this auxiliary system exactly using its orbitals. The remaining corrections (exchange and correlation) are then small enough to be modeled as approximate functionals of the density. This strategy sidesteps the central failing of the Thomas-Fermi approach while preserving the simplicity of working with the density for the interaction terms.
