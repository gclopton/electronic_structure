## Notation

## Abbreviations

| BZ | first Brillouin zone |
| :--- | :--- |
| wrt | with respect to |
| + c.c. | denotes adding the complex conjugate of the |
|  | preceding quantity |

## General Physical Quantities

| $E$ | energy |
| :--- | :--- |
| $\Omega$ | volume (to avoid confusion with $V$ used for potential) |
| $P=-(\mathrm{d} E / \mathrm{d} \Omega)$ | pressure |
| $B=\Omega\left(\mathrm{d}^{2} E / \mathrm{d} \Omega^{2}\right)$ | bulk modulus (inverse of compressibility) |
| $H=E+P \Omega$ | enthalpy |
| $u_{\alpha \beta}$ | strain tensor (symmetrized form of $\epsilon_{\alpha \beta}$ ) |
| $\sigma_{\alpha \beta}=-(1 / \Omega)\left(\partial E / \partial u_{\alpha \beta}\right)$ | stress tensor (note the sign convention) |
| $\mathbf{F}_{I}=-\left(\mathrm{d} E / \mathrm{d} \mathbf{R}_{I}\right)$ | force on nucleus I |
| $C_{I J}=\mathrm{d}^{2} E / \mathrm{d} \mathbf{R}_{I} \mathrm{~d} \mathbf{R}_{J}$ | force constant matrix |
| $n(\mathbf{r})$ | density of electrons |
| $t(\mathbf{r})$ | kinetic energy density $t(\mathbf{r})=n(\mathbf{r}) \tau(\mathbf{r})$ |

## Notation for Crystals

| $\Omega_{\text {cell }}$ | volume of primitive cell |
| :--- | :--- |
| $\mathbf{a}_{i}$ | primitive translation vectors |
| $\mathbf{T}$ or $\mathbf{T}(\mathbf{n})$ | lattice translations |
|  | $\mathbf{T}(\mathbf{n}) \equiv \mathbf{T}\left(n_{1}, n_{2}, n_{3}\right)=n_{1} \mathbf{a}_{1}+n_{2} \mathbf{a}_{2}+n_{3} \mathbf{a}_{3}$ |
| $\tau_{s}, s=1, \ldots, S$ | positions of atoms in the basis |
| $\mathbf{b}_{i}$ | primitive vectors of reciprocal lattice |
| $\mathbf{G}$ or $\mathbf{G}(\mathbf{m})$ | reciprocal lattice vectors |
| k | $\mathbf{G}(\mathbf{m}) \equiv \mathbf{G}\left(m_{1}, m_{2}, m_{3}\right)=m_{1} \mathbf{b}_{1}+m_{2} \mathbf{b}_{2}+m_{3} \mathbf{b}_{3}$ |
|  | wavevector in first Brillouin zone (BZ) |
| q | general wavevector ( $\mathbf{q}=\mathbf{k}+\mathbf{G}$ ) |


| $\hat{H}$ | hamiltonian for either many particles or a single particle |
| :--- | :--- |
| $\Psi\left(\left\{\mathbf{r}_{i}\right\}\right)$ | many-body wavefunction of a set of particle positions |
|  | $\mathbf{r}_{i}, i=1, N_{\text {particle }}$; spin is assumed to be included in the argument $\mathbf{r}_{i}$ unless otherwise specified |
| $E_{i}$ | energy of many-body state |
| $\Phi\left(\left\{\mathbf{r}_{i}\right\}\right)$ | single determinant uncorrelated wavefunction |
| $H_{m, m^{\prime}}$ | matrix element of independent-particle hamiltonian |
| $S_{m, m^{\prime}}$ | overlap matrix elements of states $m$ and $m^{\prime}$ |
| $\varepsilon_{i}$ <br> $f_{i}=f\left(\varepsilon_{i}\right)$ <br> $\psi_{i}^{\sigma}(\mathbf{r}), \varepsilon_{i}^{\sigma}$ <br> $\psi_{l}(r)$ | independent-particle wavefunction or "orbital," |
|  | independent-particle eigenvalue, $i=1, \ldots, N_{\text {states }}$ |
|  | occupation of state $i$ where $f$ is the Fermi function |
|  | used when spin is explicitly indicated |
|  | single-body radial wavefunction |
|  | $\left(\psi_{l, m}(\mathbf{r})=\psi_{l}(r) Y_{l m}(\theta, \phi)\right)$ |
| $\phi_{l}(r)$ | single-body radial wavefunction $\phi_{l}(r)=r \psi_{l}(r)$ |
| $\eta_{l}(\varepsilon)$ | phase shift |
| $\psi_{i, \mathbf{k}}(\mathbf{r})=\mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{r}} u_{i, \mathbf{k}}(\mathbf{r})$ | Bloch function in crystal, with $u_{i, \mathbf{k}}(\mathbf{r})$ periodic |
| $\varepsilon_{i, \mathbf{k}}$ | eigenvalues that define bands as a function of $\mathbf{k}$ |
| $\hat{H}(\mathbf{k})$ | "gauge-transformed" hamiltonian given by Eq. (4.37) with eigenvectors $u_{i, \mathbf{k}}(\mathbf{r})$ |
| $w_{i \mathbf{n}}(\mathbf{r})$ | Wannier function for band $i$ and cell $\mathbf{n}$ |
| $w_{i n, \mathbf{k}_{\perp}}(\mathbf{r})$ | hybrid Wannier function for band $i$ and cell $n$ in one direction and momentum $\mathbf{k}_{\perp}$ in the other directions |
| $\tilde{w}_{i \mathbf{n}}(\mathbf{r})$ | nonorthogonal transformation of Wannier functions |
| $\chi_{\alpha}(\mathbf{r})$ | single-body basis function, $\alpha=1, \ldots, N_{\text {basis }}$. |
|  | $\psi_{i}(\mathbf{r})=\sum_{\alpha} c_{i \alpha} \chi_{\alpha}(\mathbf{r})$ |
| $\chi_{\alpha}(\mathbf{r}-(\tau+\mathbf{T}))$ | ocalized orbital basis function on atom at position $\tau$ in cell labeled by translation vector $\mathbf{T}$ |
| $\chi^{\mathrm{OPW}}(\mathbf{r}), \chi^{\mathrm{APW}}(\mathbf{r})$, $\chi^{\text {LMTO }}(\mathbf{r})$ | basis function for orthogonalized, augmented, or muffin-tin orbital basis functions |

## Spin and Spin-Orbit Interaction

$\sigma_{i}$ or $\tau_{i}$
Pauli matrices
$H_{\text {SO }}$
hamiltonian for spin-orbit interaction (Appendix O)
$\zeta$

Density Functional Theory
| $F[f]$ | general notational for $F$ a functional of the function $f$ |
| :--- | :--- |
| $E_{\mathrm{xc}}[n]$ | exchange-correlation energy in Kohn-Sham theory |
| $\epsilon_{\mathrm{xc}}(\mathbf{r})$ | exchange-correlation energy per electron |
| $V_{\mathrm{xc}}(\mathbf{r})$ | exchange-correlation potential in Kohn-Sham theory |
| $V_{\mathrm{xc}}^{\sigma}(\mathbf{r})$ | exchange-correlation potential for spin $\sigma$ |
| $f_{\mathrm{XC}}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ | response $\delta^{2} E_{\mathrm{xc}} / \delta n(\mathbf{r}) \delta n\left(\mathbf{r}^{\prime}\right)$ |


Response Functions and Correlation Functions
| $\chi(\omega)$ | general response function |
| :--- | :--- |
| $\chi_{0}(\omega)$ | general response function for independent particles |
| $K(\omega)$ | kernel in self-consistent response function $\chi^{-1}=$ $\left[\chi_{0}\right]^{-1}-K$ |
| $\epsilon(\omega)$ | frequency-dependent dielectric function |
| $n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ | pair distribution |
| $g\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ | normalized pair distribution (often omitting the spin indices) |
| $G\left(z, \mathbf{r}, \mathbf{r}^{\prime}\right)$ or $G_{m, m^{\prime}}(z) \rho\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ | Green's function of complex frequency $z$ density matrix |
| $\rho_{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ | density matrix diagonal in spin for independent particles |


Berry Phases and Topological Insulators
| $\phi$ | Berry phase |
| :--- | :--- |
| $\mathcal{A}_{\alpha}(\boldsymbol{\lambda})$ | Berry connection as function of a parameter $\lambda$ |
| $\Omega_{\alpha \beta}(\lambda)$ | Berry curvature |
| $\Omega=\Omega_{x y}=-\Omega_{y x}$ | Berry curvature in two dimensions |
| $\Phi$ | Berry flux |
| C | Chern number for closed surface |
| Z | set of integers, topology class of quantum Hall systems |
| $Z_{2}$ | set of integers modulo 2 , equivalent to even and odd, topology class of topological insulators with time-reversal symmetry |


