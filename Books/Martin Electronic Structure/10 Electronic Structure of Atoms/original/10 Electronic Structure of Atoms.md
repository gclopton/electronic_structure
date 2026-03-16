## PART III

## IMPORTANT PRELIMINARIES ON ATOMS

## 10

## Electronic Structure of Atoms

## Summary

This chapter is concerned with the issues of solving the self-consistent Kohn-Sham and Hartree-Fock equations in the simplest geometry. We will not be concerned with the intricate details of the states of many-electron atoms but only those aspects relevant to our primary goal, the electronic structure of condensed matter and molecules. Studies of the atom illustrate the concepts and are directly relevant for the following sections since they are the basis for construction of $a b$ initio pseudopotentials (Chapter 11) and the augmentation functions (Chapter 16) that are at the heart of the augmented plane wave (APW), the linear combination of muffin-tin orbitals (LMTO), and KKR methods. Furthermore, we shall see that calculations on atoms and atomiclike radial problems are extremely useful in qualitative understanding of many aspects of condensed matter, including band widths, equilibrium volume, and bulk modulus, as discussed in Section 10.7.

### 10.1 One-Electron Radial Schrödinger Equation

We start with the case of the hydrogenic one-electron atom. Although this is treated in many texts, it is useful to establish notation that will be used in many chapters. If there is no spin-orbit coupling, the wavefunction can be decoupled into a product of space and spin. (The relativistic Dirac equations and spin-orbit interaction are treated in Section 10.3 and Appendix O .) Since the potential acting on the electron is spherically symmetric $V_{\text {ext }}(\mathbf{r})= V_{\text {ext }}(r)=-Z / r$, the spatial part of the orbital can be classified by angular momentum $\left(L=\left\{l, m_{l}\right\}\right)$

$$
\psi_{l m}(\mathbf{r})=\psi_{l}(r) Y_{l m}(\theta, \phi)=r^{-1} \phi_{l}(r) Y_{l m}(\theta, \phi),
$$

where the normalized spherical harmonics are given by

$$
Y_{l m}(\theta, \phi)=\sqrt{\frac{2 l+1}{4 \pi} \frac{(l-m)!}{(l+m)!}} P_{l}^{m}[\cos (\theta)] \mathrm{e}^{\mathrm{i} m \phi}
$$

with $P_{l}^{m}(x)$ denoting the associated Legendre polynomials defined in Section K.2. The traditional labels for angular momenta are $\mathrm{s}, \mathrm{p}, \mathrm{d}, \mathrm{f}, \mathrm{g}, \ldots$, for $l=0,1,2,3, \ldots$, and explicit formulas for the first few functions are given in Eq. (K.10).

Using the form of the Laplacian in spherical coordinates,

$$
\nabla^{2}=\frac{1}{r^{2}} \frac{\partial}{\partial r}\left(r^{2} \frac{\partial}{\partial r}\right)+\frac{1}{r^{2} \sin (\theta)} \frac{\partial}{\partial \theta}\left[\sin (\theta) \frac{\partial}{\partial \theta}\right]+\frac{1}{r^{2} \sin ^{2}(\theta)}\left(\frac{\partial^{2}}{\partial \phi^{2}}\right)
$$

the wave equation can be reduced to the radial equation (Exercise 10.1) for principal quantum number $n$

$$
-\frac{1}{2 r^{2}} \frac{\mathrm{~d}}{\mathrm{~d} r}\left[r^{2} \frac{\mathrm{~d}}{\mathrm{~d} r} \psi_{n, l}(r)\right]+\left[\frac{l(l+1)}{2 r^{2}}+V_{\mathrm{ext}}(r)-\varepsilon_{n, l}\right] \psi_{n, l}(r)=0
$$

or

$$
-\frac{1}{2} \frac{\mathrm{~d}^{2}}{\mathrm{~d} r^{2}} \phi_{n, l}(r)+\left[\frac{l(l+1)}{2 r^{2}}+V_{\mathrm{ext}}(r)-\varepsilon_{n, l}\right] \phi_{n, l}(r)=0
$$

The equations can be solved for bound states with the boundary conditions $\phi_{n, l}(r)$, $\psi_{n, l}(r) \rightarrow 0$ for $r \rightarrow \infty$, and $\phi_{n, l}(r) \propto r^{l+1}$ and $\psi_{n, l}(r) \propto r^{l}$ for $r \rightarrow 0$, and subject to the normalization condition

$$
\int_{0}^{\infty} \mathrm{d} r \phi_{n, l}(r)^{2}=1
$$

For a one-electron atom, the well-known analytic solutions have eigenvalues independent of $l$ given by

$$
\varepsilon_{n, l}=-\frac{1}{2} \frac{Z^{2}}{n^{2}}
$$

in Hartree atomic units.

## Logarithmic Grid

It is convenient to have regular grids in numerical algorithms; however, for atoms a higher density of radial points is needed near the origin and only a low density in the outer region. In the program of Herman and Skillman [481] this is accomplished by doubling the grid density several times as one proceeds toward the nucleus. This is simple in concept but leads to a complicated algorithm. Another choice is to use a logarithmic grid with $\rho \equiv \ln (r)$, which is suggested by the hydrogenic orbital, which has amplitude $\propto \exp (-Z r)$, where
$Z$ is the atomic number. If we define $\tilde{\phi}_{l}(\rho)=r^{1 / 2} \psi(r)$, then the radial equation (10.5) becomes (see Fischer [482] and Exercise 10.2)

$$
\left\{\frac{-\hbar^{2}}{2 m_{e}} \frac{\mathrm{~d}^{2}}{\mathrm{~d} \rho^{2}}+\frac{l}{2}\left(l+\frac{1}{2}\right)^{2}+r^{2}\left[V_{\mathrm{ext}}(r)-\varepsilon_{n, l}\right]\right\} \tilde{\phi}_{l}(\rho)=0
$$

This has the disadvantage of transforming the interval $0 \leq r \leq \infty$ to $-\infty \leq \rho \leq \infty$. In practice, one can treat an inner region $0 \leq r \leq r_{1}$ with a series expansion [482]

$$
\phi_{l}(r) \propto r^{l+1}\left[1-\frac{Z r}{l+1}+\alpha r^{2}+O\left(r^{3}\right)\right],
$$

where $\alpha$ is given in Section 6.2 of [482]. The boundary $r_{1}$ is chosen so that $\rho_{1}=\ln (Z r)$ is constant for all atoms. Then the outer region $\rho_{1} \leq \rho \leq \infty$ can be treated on a regular grid in the variable $\rho$.

The atomic equations can be solved on a regular grid in $r$ or $\rho$ following the flow chart for a Kohn-Sham calculation given in Fig. 7.2. The radial equations can be solved using the Numerov method described in Appendix L, Section L.1. Excellent atomic programs exist, often built upon the one written originally by Herman and Skillman [481]. The ideas are described in great detail by Slater [483, 484] and by Fischer [482] in the Hartree-Fock approximation, and a simplified description is given by Koonin and Meredith [485]. Some of the codes for atomic calculations are listed in Appendix R.

### 10.2 Independent-Particle Equations: Spherical Potentials

The Kohn-Sham equations for a general problem have been given in Eqs. (7.11)-(7.13), which are independent-particle equations with a potential that must be determined selfconsistently. The same form applies to the Hartree-Fock equations (3.45) or (3.46), except that the exchange potential Eq. (3.48) is state dependent. In each case, the solution requires solving independent-particle equations having the same form as the one-electron equation (10.4) or (10.5), except that $V_{\text {ext }}$ is replaced by some effective potential $V_{\text {eff }}$ that must be determined self-consistently.

For closed-shell systems, such as rare-gas atoms, all the filled states are spin paired and the charge density $n(r)$,

$$
n(r)=\sum_{n, l}^{\text {occupied }}(2 l+1)\left|\psi_{n, l}(r)\right|^{2}=\sum_{n, l}^{\text {occupied }}(2 l+1)\left|\phi_{n, l}(r)\right|^{2} / r^{2}
$$

has spherical symmetry. The potential

$$
V_{\text {eff }}(r)=V_{\text {ext }}(r)+V_{\text {Hartree }}(r)+V_{\mathrm{xc}}(r)
$$

is obviously spherically symmetric in the Kohn-Sham approach. In the Hartree-Fock case, the last term is the orbital-dependent exchange $\hat{V}_{x}^{n, l}(\mathbf{r})$, but it is not difficult to show (Exercise 10.5) that matrix elements of $\hat{V}_{x}$ are independent of $m$ and $\sigma$ and lead to an effective radial potential for each $n, l$.

Thus the independent-particle states can be rigorously classified by the angular momentum quantum numbers $L=\left\{l, m_{l}\right\}$ and there is no net spin. This leads to the simplest-case radial equations with eigenvectors $\phi_{l, m_{l}}$ independent of spin and eigenvalues independent of $m_{l}$. The resulting radial equation for $\phi_{n, l}(r)$, analogous to Eq. (10.5), is

$$
-\frac{1}{2} \frac{\mathrm{~d}^{2}}{\mathrm{~d} r^{2}} \phi_{n, l}(r)+\left[\frac{l(l+1)}{2 r^{2}}+V_{\mathrm{eff}}(r)-\varepsilon_{n, l}\right] \phi_{n, l}(r)=0
$$

which can be solved for bound states with the same boundary conditions and normalization as for the one-electron atom.

## Achieving Self-Consistency

The general form for solution of self-consistent equations has been given in Section 7.4. In a closed-shell case the effective potential is spherically symmetric (Exercise 10.5). In most cases, strongly bound states pose no great problems and the linear-mixing algorithm, Eq. (7.33), is usually sufficient. (A value of $\alpha<0.3$ will converge for most cases but may have to be reduced for heavy atoms.) However, weakly bound "floppy" states may need the more sophisticated methods described in Section 7.4. and systems with near degeneracies (e.g., energies of 3d and 4s states in transition metal atoms) may present special problems, since the order of states may change during the iterations, so that filling the states according to the minimum energy principle leads to abrupt changes in the potential. Since this principle really applies only at the minimum, often there is a simple solution; however, in some cases, there is no stable solution.

An essential part of the problem is the calculation of the Hartree or Coulomb potential. There are two approaches: solution of the Poisson equation [485] or analytic formulas that can be written down for the special case of wavefunctions that are radial functions times spherical harmonics [484]. The former approach has the advantage that the Poisson equation,

$$
\frac{\mathrm{d}^{2}}{\mathrm{~d} r^{2}} V_{\mathrm{Hart}}(r)=-4 \pi n(r)
$$

has the form of the second-order equation (L.1) and can be solved by numerical methods similar to those used for the Schrödinger equation [485]. The latter approach involves expressions that are applicable to open-shell atoms (Section 10.4) and special cases of the Fock integrals needed in for Hartree-Fock calculations [484].

The exchange-correlation potential $V_{\text {eff }}(r)$ depends on the type of independent-particle approximation. An explicit expressions for the state-dependent exchange potential $V_{x}^{n, l}(r)$ in the Hartree-Fock approximation is given in the following section. (The exchange potential is purely radial for a closed-shell atom and is shown in Exercise 10.5.) The OEP formulation of the energy is exactly the same as for Hartree-Fock but the potential is required to be $V_{x}(r)$ independent of the state. In approximations such as the LDA and GGAs, explicit expressions are given in Appendix B. Examples of results for selected
spherically symmetric atoms with various functionals are given in Table 9.1 and are discussed further in Section 10.5.

### 10.3 Spin-Orbit Interaction

Relativistic effects are essential for heavy atoms. Fortunately, they originate deep inside the core, and they act on each electron independently, so that it is sufficient to solve the relativistic equations in a spherical atomic geometry. The results carry over to molecules and solids essentially unchanged. Appendix O is devoted to the Dirac equation and the conclusion that, for cases where the effects are not too large, they can be included in the ordinary nonrelativistic Schrödinger equation by adding a spin-orbit interaction term in the hamiltonian (see Eq. (O.8))

$$
H_{S O}=\frac{e \hbar}{4 m^{2} c^{2}}(\mathbf{p} \times \nabla V) \cdot \boldsymbol{\sigma}
$$

and other scalar relativistic terms that shift the energies of the states. This may appear to be an innocuous addition to the hamiltonian and it is typically much smaller than other terms; however, it has major qualitative consequences that are different from anything that can be produced by a potential. The spin-orbit interaction opens gaps that cannot occur otherwise, and it leads to such fascinating phenomena as topological insulators in Chapters 25-28.

In an actual calculation on solids or molecules, relativistic effects can be included directly within the augmentation methods (Chapter 16), where the calculation in the spherical regions is analogous to that for an atom or in local orbitals centered on the nuclei (Chapters 14 and 15). Relativistic effects can be built into pseudopotentials as described in Section 11.5 by generating them using relativistic atomic calculations; the pseudopotentials can then be used in a nonrelativistic Schrödinger equation to determine the valence states including relativistic effects [486, 487].

### 10.4 Open-Shell Atoms: Nonspherical Potentials

The term "open shell" denotes cases where the spins are not paired and/or the angular momentum states $m=-l, \ldots, l$, are not completely filled for a given $l$. Then the proper classification is in terms of "multiplets," with given total angular momentum $J=\left\{j, m_{j}\right\}$ that are linear combinations of the space ( $L=\left\{l, m_{l}\right\}$ ) and spin ( $S=\left\{s, m_{s}\right\}$ ) variables. In general, one must deal with multiple-determinant wavefunctions. Even though the external potential (the nuclear potential for an atom) has spherical symmetry, the effective independent-particle potential $V_{\text {eff }}(\mathbf{r})$ does not, since it depends on the occupations of the orbitals. The only simplification is that one can choose the axes of quantization so that $V_{\text {eff }}(\mathbf{r})=V_{\text {eff }}(r, \theta)$ has cylindrical symmetry. Fortunately, a method due to Slater [453] shows how to reduce all the needed calculations to purely radial calculations, by using symmetry to choose appropriate multiplets. There are no general rules, but an extensive
compilation of cases is given in appendix 21 of [484]. ${ }^{1}$ In the atom one needs to consider only the cases where $V_{\text {eff }}$ is purely radial $V_{\text {eff }}(r)$ or cylindrical $V_{\text {eff }}(r, \theta)$.

For open-shell problems there are a set of approximations with various degrees of accuracy:

- Restricted: Treat the problem as spherical (derive $V_{\text {eff }}(r)$ by a spherical average over any nonspherical terms) and independent of spin (average over spin states so that orbitals are the same for each spin state). This is the correct form for closed-shell, spin $=0$ systems and, with care, can be viewed as an approximation for open shells.
- Spin unrestricted: Treat as spherical but allow the potential and the orbitals to depend on the spin. This is the correct form for half-filled shells with maximum spin so that they are closed shell for each spin separately. This case has been treated in the section on closed shells.
- Unrestricted: Treat the full problem in which only the total $m_{l}$ and $m_{s}$ are good quantum numbers. In this case, Slater's method [484] can be used to simplify the problem.


## Equations for Open-Shell Cases

For the fully unrestricted case, additional complications arise from the electron-electron interaction terms. If we chose an axis then the density $n(r, \theta)$ and the potential $V_{\mathrm{xc}}(r, \theta)$ have cylindrical symmetry. In the Kohn-Sham approach, the wavefunctions are expanded in spherical harmonics and angular integrals with $V_{\mathrm{xc}}(r, \theta)$ must be done numerically because the nonlinear relation of $V_{\mathrm{xc}}(\mathbf{r})$ to $n(\mathbf{r})$ means that an expansion of $V_{\mathrm{xc}}(r, \theta)$ in spherical harmonics has no maximum cutoff in $L$. Also the Coulomb potential has multi-pole moments and the solution of the Poisson equation is not as simple as in the spherical case.

For the open-shell case, the Hartree-Fock equations are actually simpler because the exchange term can be expanded in a finite sum of spherical harmonics. In order to calculate the matrix elements of the electron-electron interaction, one can use the well-known expansion [480] in terms of the spherical harmonics (Appendix K), which allows the factorization into terms involving $\mathbf{r}_{1}$ and $\mathbf{r}_{2}$

$$
\frac{1}{\left|\mathbf{r}_{1}-\mathbf{r}_{2}\right|}=4 \pi \sum_{l=0}^{\infty} \sum_{m=-l}^{l} \frac{1}{2 l+1} \frac{r_{<}^{l}}{r_{>}^{l+1}} Y_{-l m}^{*}\left(\theta_{2}, \phi_{2}\right) Y_{-l m}\left(\theta_{1}, \phi_{1}\right),
$$

where $r_{<}$and $r_{>}$are the lesser and the greater of $r_{1}$ and $r_{2}$. Using this expression, matrix elements involving the orbitals $i, j, r, t$ can be written

$$
\begin{aligned}
\langle i j| \frac{1}{r_{12}}|r t\rangle= & \delta\left(\sigma_{i}, \sigma_{r}\right) \delta\left(\sigma_{j}, \sigma_{t}\right) \delta\left(m_{i}+m_{j}, m_{r}+m_{t}\right) \\
& \times \sum_{k=0}^{k_{\max }} c^{k}\left(l_{i}, m_{i} ; l_{r}, m_{r}\right) c^{k}\left(l_{t}, m_{t} ; l_{j}, m_{j}\right) R^{k}(i, j ; r, t),
\end{aligned}
$$

[^0]where
$$
R^{k}(i, j ; r, t)=\int_{0}^{\infty} \int_{0}^{\infty} \phi_{n_{i}, l_{i}}^{\dagger}\left(r_{1}\right) \phi_{n_{j}, l_{j}}^{\dagger}\left(r_{2}\right) \frac{r_{<}^{k}}{r_{>}^{k+1}} \phi_{n_{r}, l_{r}}\left(r_{1}\right) \phi_{n_{t}, l_{t}}\left(r_{2}\right) \mathrm{d} r_{1} \mathrm{~d} r_{2}
$$

The $\delta$ functions in Eq. (10.16) reflect the fact that the interaction is spin independent and conserves the $z$ component of the angular momentum. The angular integrals can be done analytically resulting in the Gaunt coefficients $c^{k}\left(l, m ; l^{\prime}, m^{\prime}\right)$, which are given explicitly in [484] and Appendix K. Fortunately, the values of $R^{k}$ are only needed for a few values of $k$; the maximum value is set by the vector-addition limits $\left|l-l^{\prime}\right| \leq k_{\max } \leq\left|l+l^{\prime}\right|$, and, furthermore, $c^{k}=0$ except for $k+l+l^{\prime}=$ even.

The radial Hartree-Fock equations are derived by functional derivatives of the energy with respect to the radial functions $\psi_{n, l, m, \sigma}(r)$. If we define a function ${ }^{2}$

$$
Y^{k}\left(n_{i}, l_{i} ; n_{j}, l_{j} ; r\right)=\frac{1}{r^{k}} \int_{0}^{r} \mathrm{~d} r^{\prime} \phi_{n_{i}, l_{i}}^{\dagger}\left(r^{\prime}\right) \phi_{n_{j}, l_{j}}\left(r^{\prime}\right) r^{\prime k}+r^{k+1} \int_{r}^{\infty} \mathrm{d} r^{\prime} \phi_{n_{i}, l_{i}}^{\dagger}\left(r^{\prime}\right) \phi_{n_{j}, l_{j}}\left(r^{\prime}\right) \frac{1}{r^{\prime k+1}}
$$

and use the relation between the Gaunt and Clebsch-Gordan coefficients Eq. (K.17), then the Hartree potential is given by

$$
\begin{aligned}
V_{\text {Hartree }}(r)= & \sum_{\sigma=\uparrow, \downarrow} \sum_{j=1, N_{\sigma}} \sum_{k=0}^{\min \left(2 l_{i}, 2 l_{j}\right)}(-1)^{m_{i}+m_{j}} \frac{\left(2 l_{i}+1\right)\left(2 l_{j}+1\right)}{(2 k+1)^{2}} \frac{Y^{k}\left(n_{j}, l_{j} ; n_{j}, l_{j} ; r\right)}{r} \\
& \times C_{l_{i} 0, l_{i} 0}^{k 0} C_{l_{j} 0, l_{j} 0}^{k 0} C_{l_{i} m_{i}, l_{i}-m_{i}}^{k 0} C_{l_{j} m_{j}, l_{j}-m_{j}}^{k 0}
\end{aligned}
$$

and the exchange potential acting on state $n_{i}, l_{i}, \sigma_{i}$ can be written

$$
\begin{aligned}
V_{x}(r)= & -\sum_{\sigma=\uparrow, \downarrow} \delta\left(\sigma, \sigma_{i}\right) \sum_{j=1, N_{\sigma}} \sum_{k=\left|l_{i}-l_{j}\right|}^{l_{i}+l_{j}} \frac{\left(2 l_{i}+1\right)\left(2 l_{j}+1\right)}{(2 k+1)^{2}} \\
& \times\left[C_{l_{i} 0, l_{j} 0}^{k 0} C_{l_{i} m_{i}, l_{j}-m_{j}}^{k m_{i}-m_{j}}\right]^{2} \frac{Y^{k}\left(n_{j}, l_{j} ; n_{j}, l_{j} ; r\right)}{r} \frac{\phi_{n_{j}, l_{j}}(r)}{\phi_{n_{i}, l_{i}}(r)},
\end{aligned}
$$

where $C_{j_{1} m_{1}, j_{2} m_{2}}^{j_{3} m_{3}}$ are the Clebsch-Gordan coefficients defined in Appendix K.

### 10.5 Example of Atomic States: Transition Elements

Examples for selected spherically symmetric atoms are given in Table 9.1 using various functionals for exchange and correlation, respectively. Three atoms shown there ( $\mathrm{He}, \mathrm{Be}$, and Ne ) are closed shell and the other two ( H and N ) are half-filled shells in which the spatial wavefunction is spherically symmetric. The latter are called "spin unrestricted" and require spin functionals with separate potentials for $V_{\text {eff }}^{\sigma}(r)$ for spin up and down. The results show that the local approximation works remarkably well, considering that it is derived

[^1]from the homogeneous gas, and that GGAs in general improve the overall agreement with experiment.

Hydrogen is the special case where the one-electron solution for the ground-state energy is exact. This is satisfied in any theory that has no self-interactions, including HartreeFock and exact exchange (EXX). The results in the tables indicate the error in the other functionals in this limit. The accuracy is quite remarkable, especially for functionals derived from the homogeneous gas, which supports the use of the functionals for the entire range from homogeneous solids to isolated atoms. Nevertheless, there are important errors. In particular, there are large effects on the eigenvalues due to the long-range asymptotic form of the potential. The form is correct in Hartree-Fock and EXX calculations that take into account the nonlocal exchange but is incorrect in local and GGA approximations. The effects are large in one- and two-electron cases, shown explicitly in Section 9.10, but are smaller in heavier atoms with many electrons.

As an example of a many-electron atom, the wavefunctions for spin-polarized Mn are shown in Fig. 10.1, calculated without relativistic corrections and spin-orbit coupling. The states of this transition metal element illustrate the difference between the loosely bound outer 4 s states and the more localized 3 d states. The atom is in the $3 \mathrm{~d}^{5 \uparrow} 4 \mathrm{~s}^{2}$ state and the right-hand side of the figure shows the up and down wavefunctions for the outer states. Since the d shell is filled for one spin (Hund's first rule for maximum spin), the atom is in a spherically symmetric spatial state. Note that the 3d states are actually in the same spatial region as the strongly bound "semicore" 3s and 3p states.

![](./images/d943c1b0-9a00-4c9f-b99b-e35c3d73a115-08_659_944_1257_364.jpg)
Figure 10.1. Radial wavefunction $\phi_{l}(r)=r \psi_{l}(r)$ for Mn in the $3 \mathrm{~d}^{5 \uparrow} 4 \mathrm{~s}^{2}$ state showing all the orbitals. Note that the 4 s states are much more delocalized than the 3d states even though they have similar energies. In contrast, the maximum in the 3 d is close to that of the 3 s and 3 p , even though these are much lower in energy and are called "semicore" states. Since the atom is spin polarized, the orbital shapes depend on the spin. There is a clear effect on the 3d and 4s, which is not shown for simplicity.

![](./images/d943c1b0-9a00-4c9f-b99b-e35c3d73a115-09_806_742_255_465.jpg)
Figure 10.2. Promotion energies for $\mathrm{d} \rightarrow \mathrm{s}$ electrons in the 3d transition metal series. Shown are the energies $\Delta_{\mathrm{sd}} \equiv E_{\text {total }}\left[3 \mathrm{~d}^{n-1} 4 \mathrm{~s}^{1}\right]-E_{\text {total }}\left[3 \mathrm{~d}^{n-2} 4 \mathrm{~s}^{2}\right]$ from experiment (solid line) and from calculated total energy differences with different functionals. This shows that LSDA (open circles), typically tends to underestimate the promotion energy, i.e., the d states are underbound, whereas full nonlocal exchange (solid circles) tends to have the opposite effect. Including correction for self-interaction (open squares) and screening, the exchange (solid squares) improves the results considerably. Such effects carry over to solids as well. From [488].

Atomic calculations can be used to gain insight into practical aspects of density functional theory and how it can be expected to work in solids. Transition metals provide an excellent example because the d states retain much of their atomic character in the solid. For example, the relative energies of the 3 d and 4 s states can be expected to carry over to the solid. Figure 10.2 shows the promotion energies for transferring a d electron to an s state. The energies plotted are the experimental promotion energies and the calculated values with different functionals. The calculated energies are total energy differences $\Delta_{\text {sd }} \equiv E_{\text {total }}\left[3 \mathrm{~d}^{n-1} 4 \mathrm{~s}^{1}\right]-E_{\text {total }}\left[3 \mathrm{~d}^{n-2} 4 \mathrm{~s}^{2}\right]$, not differences of eigenvalues, since $\Delta_{\text {sd }}$ is a better measure of the true energy for promotion than the eigenvalue difference. The primary point to notice is that there are opposite tendencies for the local approximation (LSDA) and for exact nonlocal exchange (EXX), which is very close to Hartree-Fock. The former leads to underbinding of the d relative to the s state, whereas the latter leads to overbinding. The example of screened exchange is one version of hybrid functionals (Section 9.3) that tend to give results intermediate between Hartree-Fock and LDA.

Three conclusions can be drawn from the atomic calculations that are very important for applications in molecules and solids:

- Typical density functional theory calculations using LDA or GGA functionals can be expected to give errors in the relative positions of bands, especially bands of different character, such as localized 3d versus delocalized 4s states. The errors can be of the order of electron volts.
- Hybrid functionals (Section 9.3) improve the accuracy of many results, such as bandgaps as shown in Fig. 2.24. They are widely applied in chemistry where implementation is straightforward as a mixture of Hartree-Fock and density functional calculations. In a solid Hartree-Fock is more difficult, but methods have been developed explicitly for the purpose of using hybrid functionals.
- The results for transition metals illustrate the large difference between valence orbitals that are delocalized ( s and p ) and the d states that are much more localized. The effects of exchange and correlation are much more important in highly localized orbitals, leading to effects of strong correlation in transition metal systems. The essence of the selfinteraction correction (SIC) and the "DFT+U" approach (Section 9.6) is to include orbital-dependent interactions that describe this large difference. In atoms the states of each symmetry are well defined; however, in a solid there are choices in how to define localized orbitals. Nevertheless, these approaches can provide significantly improved descriptions of strongly correlated systems like transition metal oxides [459].


### 10.6 Delta-SCF: Electron Addition, Removal, and Interaction Energies

In localized systems, electron excitation, addition, and removal energies can all be calculated as energy differences $\Delta E_{12}=E_{2}-E_{1}$ for a transition between states 1 and 2 , instead of eigenvalues calculated for state 1 or 2 . This is known as " $\triangle \mathrm{SCF}$ " and in self-consistent field methods, it produces more accurate results since the energy difference includes effects of relaxation of all the orbitals. Following the Slater transition state argument ([489], p. 51), the energy difference can be approximated by the eigenvalue calculated at the occupation halfway between the two states. For example, an electron removal energy is the eigenvalue when $1 / 2$ an electron is missing in the given state; a transition energy is the eigenvalue difference calculated when $1 / 2$ an electron is transferred between the two states,

$$
\Delta E(N \rightarrow N-1)=E(N-1)-E(N) \approx \epsilon_{i}\left(N-\frac{1}{2}\right),
$$

where $i$ denotes a particular state and $N-\frac{1}{2}$ means the density is $n(\mathbf{r})-\frac{1}{2}\left|\psi_{i}(\mathbf{r})\right|^{2}$. See Exercise 10.8 for a statement of the ideas involved in the arguments and their proof. A schematic figure for the variation of the energy with occupation $N$ is shown in the right side of Fig. 9.2.

The $\triangle \mathrm{SCF}$ or transition state methods can be used in atomic calculations and compared with experiment. For example, in [490] it was shown that results from both $\triangle \mathrm{SCF}$ and transition state calculations using LDA are in good agreement with experiment for the first and second ionization energies of 3d electrons in Cu. In addition, it is straightforward to calculate interaction energies as energy differences. An effective interaction energy that
includes relaxation of the orbitals is given by the difference of first and second ionization energies, which in terms of the transition state rule can be written

$$
U \equiv[E(N-1)-E(N)]-[E(N-2)-E(N-1)] \approx \epsilon_{i}\left(N-\frac{1}{2}\right)-\epsilon_{i}\left(N-\frac{3}{2}\right)
$$

The LDA calculation [490] for the 3d states of a Cu atom in free space yields $U_{a v}=E\left(d^{10}, s^{1}\right)+E\left(d^{8}, s^{1}\right)-2 E\left(d^{9}, s^{1}\right)=15.88 \mathrm{eV}$ compared to the experimental value 16.13 eV for the average of the multiplet energies for the three occupations. See Exercise 10.11 for discussion of the interpretation and suggested exercises.

In Section 9.6 the same approach is applied to a localized state in a molecule or solid, but in such cases it is not obvious how to identify the localized orbital whose occupation can be varied, and one must take into account the screening by the rest of the system. Here it is useful to point out the way that an atomic calculation can be used to estimate the screened $U$ in a solid. The addition of a charge in a d or f state in a solid is screened by the other electrons; within a short distance the charge is reduced to $\approx \pm 1 / \epsilon$ where the dielectric constant $\epsilon \gg 1$. This can be mimicked in an atom if the charge in the d or f state is compensated by an electron in an s state [491]. For example, in a Cu atom the energy differences $E\left(d^{10}, s^{0}\right)+E\left(d^{8}, s^{2}\right)-2 E\left(d^{9}, s^{1}\right)$ can be interpreted as a screened interaction, with the values 3.96 eV found in an LDA calculation [490] compared to 4.23 eV in experiment. Similar values are found for all 3d transition metals. For the lanthanides the result is $\approx 6-7 \mathrm{eV}$ [491, 492]. These are remarkably close to the values for screened effective interactions found in calculations for 3d and 4f states in solids, as discussed in Section 9.6 and in greater detail in [1].

### 10.7 Atomic Sphere Approximation in Solids

In a solid the wavefunctions tend to be atomic-like near each atom. This results from the full calculations are described in Part IV, but it is instructive to see that qualitative (sometimes quantitative) information about electronic bands, pressure, and energy of simple solids can be derived from calculations with spherical symmetry, analogous to the usual atomic calculations with only one difference: a change of boundary conditions to mimic the extreme limits of each band in a solid. Such calculations are also instructive because they are very closely related to the radial atomic-like calculations used in augmented plane wave (APW), linear combination of muffin-tin orbitals (LMTO), and KKR methods of Chapters 16 and 17.

The basic ideas are in the original work of Wigner and Seitz [54], extended by Andersen [495] to describe the width of bands formed by states with a given angular momentum. The environment of an atom in a close-packed solid is mimicked by boundary conditions on an atomic sphere, i.e., approximating the Wigner-Seitz cell as a sphere. As indicated in Fig. 10.3, for each angular momentum $l$ the free-atom boundary conditions are replaced by the condition that the wavefunction be zero at the boundary (the highest-energy

![](./images/d943c1b0-9a00-4c9f-b99b-e35c3d73a115-12_591_1069_245_300.jpg)
Figure 10.3. Left: Schematic figure of the radial wavefunction in the atomic sphere approximation (ASA) to a solid, where $r_{0}$ is the Wigner-Seitz radius, roughly $1 / 2$ the distance to a neighboring atom. The lines denote the different boundary conditions that correspond to the "bottom" lowest-energy bonding-type state, the "top" highest-energy antibonding-type state, and the usual free-atom state. The difference in energy from bottom to top is an estimate of the band width in a solid. Right: estimates of the d-band width for the 3d transition metals from Eq. (10.25) (called "ASM") compared to full calculations using the LMTO method (Chapter 17) by Andersen and Jepsen [493]. From Straub and Harrison [494].

antibonding-type state that corresponds to the top of the band) or have zero derivative at the boundary (the lowest-energy bonding-type state that corresponds to the bottom of the band). The difference is the band width $W_{l}$ for angular momentum $l$.

This simple picture contains the important ingredients for understanding and semiquantitative prediction of band widths in condensed matter. The width is directly related to the magnitude, the wavefunction, and its slope at the boundary. Thus the width varies from narrow-band atomic-like to wide-band delocalized states exactly as indicated in the first figure of this book, Fig. 1.1, as there is increased overlap of the atomic states. Furthermore, it is reasonably accurate as illustrated on the right-hand side of Fig. 10.3 from the work of Straub and Harrison [455] using Eq. (10.25). It gives an estimate that is particularly good in close-packed systems but also is a good starting point for liquids and even dense plasmas [496-499] One can also calculate properties like the pressure, as discussed in Section I.3. Thus a single standard atomic calculation and Eq. (10.25) provide a great start to understanding electronic structure of condensed matter!

Explicit expressions for the band widths can be derived from the radial equation, (10.4), for the wavefunction $\psi_{n, l}(r)$. The band formed for each state $n, l$ is considered separately, and we can drop the subscripts to simplify the equations. Consider any two solutions $\psi^{1}(r)$ and $\psi^{2}(r)$ with eigenvalues $\varepsilon^{1}$ and $\varepsilon^{2}$ obtained with two different specific boundary conditions. Let the equation for $\psi^{1}(r)$ be multiplied by $r^{2} \psi^{2}(r)$ and integrated from $r=0$ to the boundary $r=r_{0}$, and similarly for the equation for $\psi^{2}(r)$. Integrating by parts and subtracting the equations leads to [494] (Exercise 10.12),

$$
-\frac{1}{2} r_{0}^{2}\left(\psi^{2} \frac{\mathrm{~d} \psi^{1}}{\mathrm{~d} r}-\psi^{1} \frac{\mathrm{~d} \psi^{2}}{\mathrm{~d} r}\right)_{r-r_{0}}=\left(\varepsilon^{1}-\varepsilon^{2}\right) \int_{0}^{r_{0}} \mathrm{~d} r r^{2} \psi^{1} \psi^{2}
$$

If we let $\psi^{2}(r)$ be the solution for the top of the band $\left(\psi^{2}\left(r_{0}\right)=0\right)$ and $\psi^{1}(r)$ for the bottom ( $\mathrm{d} \psi^{1}(r) / \mathrm{d} r=0$ at $r=r_{0}$ ), then this equation can be written

$$
W \equiv \varepsilon^{2}-\varepsilon^{1}=-\frac{1}{2} \frac{r_{0}^{2}\left(\psi^{1} \frac{\mathrm{~d} \psi^{2}}{\mathrm{~d} r}\right)_{r=r_{0}}}{\int_{0}^{r_{0}} \mathrm{~d} r r^{2} \psi^{1} \psi^{2}}
$$

This gives the width $W$ for each $n, l$ in terms of the two solutions with the boundary conditions described above.

Finally, a simple, insightful expression for the band width as a function of the WignerSeitz radius $r_{0}$ can be derived [494] from a single atomic calculation with the usual boundary conditions. As suggested by the interpretation of the bottom and top of the band as bonding and antibonding, as illustrated in Fig. 10.3, the value of the bonding function at $r_{0}$ is approximately twice the value of the atomic function $\psi^{a}$, and similarly for the slope. Further approximating the product to be $\psi^{1} \psi^{2} \approx\left[\psi^{a}\right]^{2}$ leads to the very simple expression (see Exercise 10.12)

$$
W \approx-2 \frac{r_{0}^{2}\left(\psi^{a} \frac{\mathrm{~d} \psi^{a}}{\mathrm{~d} r}\right)_{r=r_{0}}}{\int_{0}^{r_{0}} \mathrm{~d} r r^{2}\left(\psi^{a}\right)^{2}}
$$

The right-hand side of Fig. 10.3 shows the band widths for d-bands in transition metals calculated from this simple formula compared to full calculations using the LMTO method (Chapter 17).

## SELECT FURTHER READING

Theory and calculations for atoms:
Fischer, C. F., The Hartree-Fock Method for Atoms: A Numerical Approach (John Wiley \& Sons, New York, 1977).
Slater, J. C., Quantum Theory of Atomic Structure, vols. 1-2 (McGraw-Hill, New York, 1960).
Tinkham, M., Group Theory and Quantum Mechanics (McGraw-Hill, New York, 1964).
Early numerical work:
Herman, F. and Skillman, S., Atomic Structure Calculations (Prentice-Hall, Engelwood Cliffs, NJ, 1963).

Relativistic theory:
Koelling, D. D. and Harmon, B. N., "A technique for relativistic spin-polarized calculations," J. Phys. C 10:3107-3114, 1977.
Kübler, J., Theory of Itinerant Electron Magnetism (Oxford University Press, Oxford, 2001).
Kübler, J. and Eyert, V., "Electronic structure calculations," in Electronic and Magnetic Properties of Metals and Ceramics, edited by K. H. J. Buschow (VCH-Verlag, Weinheim, Germany, 1992), p. 1.

MacDonald, A. H., Pickett, W. E., and Koelling, D., "A linearised relativistic augmented-plane-wave method utilising approximate pure spin basis functions," J. Phys. C: Solid State Phys. 13:26752683, 1980.

Instructive methods for calculations:
Koonin, S. E. and Meredith, D. C., Computational Physics (Addison Wesley, Menlo Park, CA, 1990).

## Exercises

10.1 Show explicitly that the wave equation can indeed be written in the form of Eq. (10.4).
10.2 Derive the form of the radial equation, (10.8) in terms of the transformed variable $\rho \equiv \ln (r)$. Give two reasons why a uniform grid in the variable $\rho$ is an advantageous choice for an atom.
10.3 Show that the Hartree-Fock equations are exact for the states of H . Show that the change in energy computed by energy differences gives exact excitations but that the eigenvalues do not.
10.4 Show that the OEP equations are exact for the states of H, just like Hartree-Fock. But unlike Hartree-Fock the eigenvalues give exact excitation energies.
10.5 Show that the general Hartree-Fock equations simplify in the closed-shell case so that the exchange potential is spherically symmetric.
10.6 Show that for the ground state of He the general Hartree-Fock equations simplify to the very simple problem of one electron moving in the average potential of the other, with both electrons required to be in the same spatial orbital.
10.7 There are results that emerge in relativistic quantum mechanics that may be surprising. For example, show that there is a $2 p$ state that has nonzero expectation value at the origin, whereas it is zero in the nonrelativistic theory.
10.8 The Slater transition state argument ([489], p. 51) is based on two facts. First, an eigenvalue is the derivative of the energy with respect to the occupation of the given state (the "Janak theorem"), and, second, that the eigenvalue varies with occupation and can be represented in a power series.
(a) Using these facts derive the "halfway" rule.
(b) Argue that one can derive the "halfway" rule based purely on the fact that one wants a result that is symmetric between the two states.
(c) Derive the explicit expression (10.21) for electron removal.
10.9 Solve the Schrödinger equation in Section 10.1 for a particle in a spherical box of radius $R$. If the boundary conditions are that $\psi=0$ at $r=R$, show that the solutions are $\psi(r)=\sin k r / r$ and derive the eigenvalues and normalization factors for the states with the three lowest energies. Show that all energies scale as $\alpha 1 / R^{2}$.
10.10 Derive the pressure $-\mathrm{d} E / \mathrm{d} \Omega$ from the expression for the energy in the problem above. Show that this is equivalent to the expression for the pressure in a spherical geometry given in Eq. (I.8).
10.11 The expression (10.22) provides a way to calculate interactions.
(a) Show that these are "effective" in the sense that orbital relations are included and are exact if the energies $E(N), E(N-1)$, and $E(N-2)$ are exact.
(b) Derive Expression (10.22) using the same arguments as in Exercise 10.8.
(c) Use an atomic code to calculate the first and second ionization energies of 3d electrons in Cu . The difference is the effective $\mathrm{d}-\mathrm{d}$ interaction. A better measure of the net effect in a solid is to calculate the difference $E\left(3 \mathrm{~d}^{9}\right)-E\left(3 \mathrm{~d}^{84} \mathrm{~s}^{1}\right)$. Compare your results with those of [490]. In this case, the effective d-d interaction is decreased because the added s electron "screens" the change in charge of the d state. As argued in [492] this is close to the screening that occurs in a solid; hence, the screened interaction is the appropriate effective interaction in the solid.
10.12 Following the arguments given in conjunction with Eqs. (10.23)-(10.25), derive the approximate expressions (10.24) and (10.25) for the band width. The full argument requires justifying the argument that this corresponds to the maximum band width in a solid and deriving the explicit expression using the linearized formulas for energy as a function of boundary condition.
10.13 The wavefunction for atomic hydrogen can be used to estimate hydrogen band widths at various states, using the approximate form of Eq. (10.25). Apply this approach to the $\mathrm{H}_{2}$ molecule to calculate bonding/antibonding splitting and compare these with the results shown in Fig. 8.2. Use this expression to derive a general argument for the functional form of the splitting as a function of proton separation $R$ at large $R$. Evaluate explicitly at the equilibrium $R$ and compare with Fig. 8.2. Calculate the band width expected for hydrogen at high density $\left(r_{s}=1.0\right)$ where it is expected to be stable as a close-packed crystal with 12 neighbors. (The result can be compared with the calculations in Exercises 12.13 and 13.4.)
10.14 Use an atomic code (possibly modified to have different boundary conditions) to calculate the band widths for elemental solids using the approach described in Section 10.7. As an example consider 3d and 4s bands in fcc Cu. Compare these with the bands shown in Fig. 16.4.


[^0]:    ${ }^{1}$ In general one needs nondiagonal Lagrange multipliers $\varepsilon_{n, l ; n^{\prime}, l^{\prime}}$ [484], but these terms appear to be small [484].

[^1]:    ${ }^{2}$ This follows the definition of Slater [483], p. 180.

