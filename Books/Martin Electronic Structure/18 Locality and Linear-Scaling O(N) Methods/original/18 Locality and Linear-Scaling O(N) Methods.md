## 18

# Locality and Linear-Scaling $\mathrm{O}(N)$ Methods 

Nearsightedness<br>W. Kohn<br>Throwing out $k$-space<br>V. Heine

## Summary

The concept of localization can be imbedded directly into the methods of electronic structure to create new algorithms that take advantage of locality or "nearsightedness" as coined by W. Kohn. As opposed to the textbook starting point for describing crystals in terms of extended Bloch eigenstates, many physical properties can be calculated from the density matrix $\rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$, which is exponentially localized in an insulator or a metal at finite $T$. For large systems, this fact can be used to make "order- $N$ " or $\mathrm{O}(N)$ methods where the computational time scales linearly in the size of the system. There are two aspects of the problem: building the hamiltonian and solving the equations. Solving the problem presents more fundamental issues, but constructing the hamiltonian is essential for useful methods. In this chapter are representative $\mathrm{O}(N)$ approaches that either treat $\rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ directly or work in terms of Wannier-like localized orbitals.

### 18.1 What Is the Problem?

Every textbook on solid state physics begins with the symmetry of crystals. The entire subject of electronic structure is cast in the framework of the eigenstates of the hamiltonian classified in $k$ space by the Bloch theorem. So far this volume is no exception. However, the real goal is to understand the properties of materials from the fundamental theory of the electrons and this is not always the best approach, neither for understanding nor for calculations.

What does one do when there is no periodicity, e.g., an amorphous solid or a liquid or a large molecule? One approach is to use periodic boundary conditions on artificial "supercells" chosen to be large enough that the effects of the boundary conditions are small or can be removed from the calculation by an analytic extrapolation procedure. This
approach can be very effective and is widely used, especially with efficient plane wave methods (Chapter 13) and molecular dynamics simulations (Chapter 19).

The subject of this chapter is an alternative approach built upon the general principle of locality, i.e., that properties at one point can be considered independent of what happens at distant points. If the theory is cast in a way that takes advantage of the locality, this can lead to algorithms that are "linear scaling" ("order- $N$ " or $\mathrm{O}(N)$ ), i.e., the computational time and computer memory needed is proportional to $N$ as the number of particles $N$ is increased to a large number. $\mathrm{O}(N)$ methods emerge naturally in classical mechanics. If there are only short-range interactions, the forces on each particle depend on only a small number of neighboring particles. One step in a molecular dynamics calculation can be done updating the position of each particle in time $\propto N .^{1}$ The same conclusion holds even if there are long-range Coulomb forces, since there are various methods to sum the long-range forces in time $\propto N$ [737].

The problem is that quantum mechanics is inherently not local: eigenstates in extended systems, in general, are extended and the solutions of the wave equation depend on boundary conditions. Indistinguishability of identical particles requires that the wavefunctions obey the symmetry or antisymmetry conditions among all particles, whether they are nearby or far away. Quantum entanglement of pairs or groups of particles can occur at a large distance. ${ }^{2}$ In practical applications with independent-particle methods, the ground state of $N$ electrons is an antisymmetric combination of $N$ eigenstates, each of which is, in general, extended through a volume also proportional to $N$. Working in terms of the independentparticle eigenstates leads to scaling at least $\propto N^{2}$, and specific methods are often worse. Full matrix diagonalization scales as $N_{\text {basis }}^{3}$, where the number of basis functions $N_{\text {basis }} \propto N$. The widely used Car-Parrinello-type algorithms in a plane wave basis scales as $N^{2} N_{\text {basis }}$, which is much better since $N \ll N_{\text {basis }}$. Solutions of correlated many-body problems, in general, scale much worse, growing exponentially in $N$ for exact solutions and as high powers for practical configuration interaction calculations [738].

Despite the inherent nonlocality in quantum mechanics, many important properties can be found without calculating the eigenstates, using information that is only "local" (as defined in the following section). For example, the density and total energy are integrated quantities that are invariant to unitary transformations of the states, and these quantities are sufficient to determine the stable ground state and the force on every nucleus. In this chapter we discuss algorithms for calculation of such quantities with computational time $\propto N$. It is not possible to cover all methods; here we discuss selected examples that illustrate the developments and several of the available codes are listed in Appendix R. More extensive

[^0]exposition of linear-scaling methods and codes can be found in the review by Bowler and Miyazaki [739] and developments related to chemistry and biology are the topics of [740] and [741].

### 18.2 Locality in Many-Body Quantum Systems

The term "nearsightedness" has been coined by Walter Kohn [742] for such integrated quantities that can be calculated at one point $\mathbf{r}$ in terms only of information at points $\mathbf{r}^{\prime}$ in a neighborhood of $\mathbf{r}$. This embodies the ideas developed by Friedel [733] and Heine and coworkers [499] on locality and other work such as the 1964 paper by Kohn, "The nature of the insulating state," in which the key idea is the localization of electronic states in insulators. Nearsightedness is a property of a many-body system of particles: the density of an individual eigenstate at any point is dependent on the boundary conditions and the potential at all other points; however, for systems of many particles, the net effect is reduced due to interference between the different independent-particle eigenstates (i.e., in the sum in Eqs. (18.1) and (18.2) below). In insulators and metals at nonzero temperature, the oneelectron density matrix decays exponentially, and in metals at $T=0$ as a power law $\left(1 / R^{3}\right.$ in three dimensions), with Gibbs oscillations due to the sharp cutoff at the Fermi surface. Interactions introduce correlations with the longest range being van de Waals type that decay as $1 / R^{6}$ in the energy and $1 / R^{3}$ in the wavefunction [738]. We will use the term "local" in this sense to mean "dependent on only distant regions to an extent which decays rapidly": exponential decay is sufficient to ensure convergent algorithms; the power law decay in metals at $T=0$ is problematic [743] but a possible approach is to use the fact that the states near the Fermi energy vary smoothly with energy [744].

All the linear-scaling $\mathrm{O}(N)$ methods discussed here take advantage of the decay of the density matrix with distance, which is zero or can be truncated at some point, as depicted in Fig. 18.1. One of the great advantages of the density matrix formalism is that it is a general approach applicable at finite temperature, where all correlations become shorter range. Therefore, in general, the range of the density matrix is decreased and $\mathrm{O}(N)$ algorithms should become more feasible and efficient. In addition, the possibility of continuous variation of fractional occupation of states is of great advantage in problematic cases where occupation must be fractional by symmetry or jumps discontinuously at $T=0$. This problem is well known in standard electronic structure algorithms and is discussed in Chapter 7, where a fictitious temperature is often added to improve calculations by smoothing details of the state distribution.

For noninteracting particles, the density matrix can be written (see Section 3.6) as

$$
\hat{\rho}=\sum_{i=1}^{M}\left|\psi_{i}\right\rangle f_{i}\left\langle\psi_{i}\right| \text { or } \rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\sum_{i=1}^{M} \psi_{i}^{*}(\mathbf{r}) f_{i} \psi_{i}\left(\mathbf{r}^{\prime}\right),
$$

where $f_{i}=1 /\left(1+\exp \left(\beta\left(\epsilon_{i}-\mu\right)\right)\right.$ is the Fermi function and $\beta=1 / k_{B} T$. For $T \neq 0$, the number of states $M$ must be greater than the number of electrons $N$, which is related to the Fermi energy $\mu$ by $N=\sum_{i=1}^{M} f_{i}$. At $T=0$ this becomes

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-04_489_1153_240_262.jpg)
Figure 18.1. Schematic diagram of treating a quantum system in terms of overlapping regions, often in terms of functions centered on atoms (left) or with strictly nonoverlapping regions as shown at the right for an irregular disordered system. A typical region at the center interacts only with neighboring regions (dark lines), which generates a sparse hamiltonian. Different methods use such divisions to create linear-scaling $\mathrm{O}(N)$ methods.

$$
\hat{\rho}=\sum_{i=1}^{N}\left|\psi_{i}\right\rangle\left\langle\psi_{i}\right| \text { or } \rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\sum_{i=1}^{N} \psi_{i}^{*}(\mathbf{r}) \psi_{i}\left(\mathbf{r}^{\prime}\right) .
$$

Even if the independent-particle eigenfunctions are extended, the density matrix is exponentially localized and vanishes at large relative separation $\left|\mathbf{r}-\mathbf{r}^{\prime}\right|$ in all cases for $T \neq 0$ (see discussion following Eq. (5.10)) and at $T=0$ in an insulator.

The sum of independent-particle energies $E_{S}$, written in terms of eigenstates, is given by

$$
E_{s}=\sum_{i=1}^{M} \frac{1}{1+\exp \left(\beta\left(\epsilon_{i}-\mu\right)\right)} \epsilon_{i},
$$

where the sum is over all eigenvalues. (This is also sufficient for Kohn-Sham theory (Section 7.3) where the total energy can always be found from $E_{s}$ plus terms that involve only the density $n(\mathbf{r})=\rho(\mathbf{r}, \mathbf{r})$.) In general, one can rewrite the sum over all eigenvectors as a trace, so that energy can be written

$$
E_{s}=\operatorname{Tr}\left\{\frac{1}{1+\exp (\beta(\hat{H}-\mu))} \hat{H}\right\}=\operatorname{Tr}\{\hat{\rho} \hat{H}\} .
$$

Similarly, the grand potential that describes the energy for different numbers of particles is given by

$$
\Omega_{s}=\operatorname{Tr}\left\{\frac{1}{1+\exp (\beta(\hat{H}-\mu))}(\hat{H}-\mu)\right\}=\operatorname{Tr}\{\hat{\rho}(\hat{H}-\mu)\} .
$$

The difficulty in using the Fermi function is the exponentiation of the operators that are nondiagonal, if one wishes to avoid diagonalization, e.g., in an $\mathrm{O}(N)$ scheme.

At $T=0$ in an insulator, the expressions are closely related to the construction of Wannier functions. The $N$ eigenstates can be transformed to $N$ localized orthogonal Wannier-like functions $w_{i}$ (Chapter 23)

$$
\hat{\rho}=\sum_{i=1}^{N}\left|w_{i}\right\rangle\left\langle w_{i}\right|, \quad T=0
$$

It may also be advantageous $[745,746]$ to work in terms of nonorthogonal functions $\hat{w}_{i}$ which are more localized, so that

$$
\hat{\rho}=\sum_{i=1, j}^{N}\left|\hat{w}_{i}\right\rangle S_{i j}^{-}\left\langle\hat{w}_{j}\right|, \quad T=0,
$$

where $S^{-}$is the inverse of the overlap matrix. ${ }^{3}$ For $T \neq 0$ the form of the decay can be derived for model problems, such as the free-electron gas discussed in Section 5.2.

For all cases, the challenge is to determine efficient, robust ways to find the density matrix $\hat{\rho}$ or the generalized Wannier functions $w_{i}$ or $\tilde{w}_{i}$. In the latter case, the functions are not unique, which leads to possible advantages that can accrue by using particular choices and possible problems due to approximations that violate the invariance of the functionals.

There are two aspects to the creation of linear-scaling methods, both relying upon sparsity of the hamiltonian and overlap matrices, assumed to have nonzero elements only for a finite range as shown schematically in Fig. 18.1:

- Building the hamiltonian, i.e., generating the nonzero matrix elements in a sparse form that is linear in the size of the system. For many approaches, this is the rate-limiting step for sizes up to hundreds of atoms, and therefore it is relevant even if the solution is done with traditional $O\left(N^{2}\right)$ or $O\left(N^{3}\right)$ methods.
- Solving the equations. This is the more fundamental aspect that is necessary for $\mathrm{O}(N)$ scaling in the large $N$ limit. We will consider approaches that treat $\rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ (or a Green's function) or work in terms of Wannier-like localized orbitals. The key division is between "nonvariational methods," which truncate well-known expansions, and "variational methods," which work with variational functionals.


### 18.3 Building the Hamiltonian

The hamiltonian can be constructed in a sparse form in real space in any case in which the basis functions are localized to regions much smaller than the system size. The most obvious basis for such an approach are local atomic-like orbitals, as in Chapter 14, which are illustrated at the left in Fig. 18.1. The tight-binding model approach is ideal for this purpose since the matrix elements of $\hat{H}$ and the overlap matrix $\hat{S}$ are defined to be short range. In the full local orbital method, matrix elements of the hamiltonian vanish beyond some distance

[^1]only if the orbitals are strictly localized. This can be accomplished in a basis of numerical orbitals purposefully chosen to be strictly localized as described in Section 15.4. This is the approach in the SIESTA code used for the calculation shown in Fig. 18.8 and in the FHIaims all-electron code. In general, analytic bases such as gaussians decay exponentially but never vanish entirely, so they must be used with care.

The real space methods in Sections 12.8 and 12.9 naturally suggest ways to use localized functions. The CONQUEST and ONETEP codes use grids with representations in localized regions done respectively with Blip (b-splies) and with FFT restricted to a box. The construction of discontinuous functions illustrated in Fig. 12.6 generates nonoverlapping basis function like those indicated at the right in Fig. 18.1. Finite elements and multiresolution methods involve functions that are overlapping but are strictly localized as described in Section 12.8. For example, the BigDFT code is based on Daubechies wavelets, which have been used for calculations on large systems [588].

The augmented approaches can also be cast in localized forms. LMTOs can be transformed to an orthogonal tight-binding form, in which the hamiltonian has a power law decay (Section 17.6) that is much shorter range than in the original method. In Green's function methods, such as KKR, $G$ is generated in terms of $G_{0}$, which is very long range for positive energies, but decays exponentially for negative energies. This has been used to construct an $\mathrm{O}(N)$ KKR method [704] in which $G_{0}$ is the numerically calculated Green's function for an electron in an array of repulsive centers, as described in Section 16.7. In these methods one must invert a matrix labeled by the orbital quantum numbers at the atomic sites, and linear scaling is accomplished in constructing the hamiltonian or Green's function matrix including only neighbors in a "local interaction zone." The approach, termed "locally selfconsistent multiple scattering" (LSMS), involves a calculation on a finite cell around each site; an alternative approach is to use Lanczos or recursion methods to solve the multiple scattering problem around each site [747].

It is, however, not essential that the basis be localized. One of the original ideas is due to Galli and Parrinello [748], who combined the plane wave Car-Parrinello algorithm (Chapter 19) with transformations of the wavefunctions to a localized form as in Eq. (18.5). Physical properties are unchanged due to the invariance of the trace. By constraining orbitals to be localized to regions, they showed that one can construct an algorithm that automatically generates localized functions and a sparse hamiltonian, even though the plane wave basis is not localized.

### 18.4 Solution of Equations: Nonvariational Methods

## Green's Functions, Recursion, and Moments

The original ideas for electronic structure methods that take advantage of the locality grew out of Green's function approaches, using the facts that the density matrix and the sum of eigenvalues are directly expressible in terms of integrals over the Green's function. The basic relations are given in Section D. 5 and in Eqs. (16.33)-(16.35), which we rewrite
here in slightly different notation. If the basis states are denoted $\chi_{m}$ (here assumed to be orthonormal for simplicity), the local density of states projected on state $m$ is given by

$$
n_{m}(\varepsilon, \mathbf{R})=-\frac{1}{\pi} \operatorname{Im} G_{m, m}(\varepsilon+i \delta)
$$

For example, $m$ might denote a site and basis orbital on that site. The sum of eigenvalues of occupied states projected on state $m$ can be found from the relation

$$
\sum_{i} \varepsilon_{i}\left|\left\langle i \mid \chi_{m}\right\rangle\right|^{2}=-\frac{1}{\pi} \int_{-\infty}^{E_{F}} \mathrm{~d} \varepsilon \varepsilon \operatorname{Im} G_{m, m}(\varepsilon+i \delta, 0)
$$

and the total sum of eigenvalues is given by

$$
\sum_{i} \varepsilon_{i}=-\frac{1}{\pi} \sum_{m} \int_{-\infty}^{E_{F}} \mathrm{~d} \varepsilon \varepsilon \operatorname{Im} G_{m, m}(\varepsilon+i \delta, 0)
$$

The left-hand sides of Eqs. (18.9)-(18.10) are in the standard eigenstate form, whereas the right-hand sides are in the form of Green's functions that can be evaluated locally. This provides all the information needed to determine the total energy and related quantities from integrals over the Green's functions.

Elegant methods have been devised to calculate the Green's functions as local quantities. The basic idea can be illustrated by Fig. 18.1 in which we desire to determine the Green's function $G_{0,0}(\varepsilon+i \delta)$ for the orbital 0 shown as dark gray. This can be accomplished by repeated applications of the hamiltonian, called recursion [732], which has close relations to the Lanczos algorithm (Section M.5). The ideas are used in tight-binding approaches (summarized, e.g., in [749]), KKR Green's function methods (see Section 16.3 for the basic ideas and references such as [704] and [747] for $\mathrm{O}(N)$ algorithm developments), and LMTO Green's function methods that use recursion (see, e.g., [725]). The diagonal elements of the Green's function can be used to find the charge density and the sum of single-particle energies; however, there are difficulties in finding the off-diagonal elements of the Green's function needed for forces. This problem is addressed by "bond-order" potential methods [750-752].

The basic idea of the recursion method [732, 753] is to use the Lanczos algorithm (Section M.5) as a method to construct a Green's function, using the properties of a tridiagonal matrix. The Lanczos recursion relation, Eq. (M.9), for the hamiltonian applied to a sequence of vectors,

$$
\psi_{n+1}=C_{n+1}\left[\hat{H} \psi_{n}-H_{n n} \psi_{n}-H_{n n-1} \psi_{n-1}\right]
$$

generates the set of vectors $\psi_{n}$ and the coefficients in the tridiagonal matrix Eq. (M.10), $\alpha_{n}=H_{n n}$ and $\beta_{n}=H_{n-1 n}$. The normalization constant is readily shown (Exercise 18.1) to be $C_{n+1}=1 / \beta_{n}, n \geq 1$. If the starting vector $\psi_{0}$ is a basis state localized at a site, ${ }^{4}$ and the hamiltonian is short range, then the algorithm generates a sequence of states in "shells"

[^2]around the central site. The diagonal part of the Green's function for state 0 is given by the continued fraction [732, 749, 753]
$$
G_{0,0}(z)=\frac{1}{z-\alpha_{0}-\frac{\beta_{1}^{2}}{z-\alpha_{1}-\frac{\beta_{2}^{2}}{z-\alpha_{2}-\frac{\beta_{3}^{2}}{\ddots}}}}
$$
where $z$ is the complex energy.
The properties of the continued fraction and a proper termination are the key features of the recursion method, and an introductory discussion can be found in [754]. If the fraction is terminated at level $N$, then the density of states consists of $N$ delta functions that is useful only for integrations over $G(z)$. If a constant imaginary energy $\delta$ is used as a terminator, this is equivalent to a lorentzian broadening of each delta function. However, there are other approaches that are just as simple but much more elegant and physical. One follows from the observation [754] that the coefficients $\alpha_{n}$ and $\beta_{n}$ tend to converge quickly to asymptotic values that can be denoted $\alpha_{\infty}$ and $\beta_{\infty}$. If one sets the coefficients $\alpha_{n}=\alpha_{\infty}$ and $\beta_{n}=\beta_{\infty}$ for all $n>N$, then one can evaluate the remainder of the fraction analytically. This leads to replacement of the $\beta_{N+1}^{2}$ coefficient by $t(z)$ given by
$$
t(z)=\frac{1}{z-\alpha_{N+1}-\frac{\beta_{N+2}^{2}}{z-\alpha_{N+2}-\frac{\beta_{N+3}^{2}}{z-\ldots}}}=\frac{1}{z-\alpha_{\infty}-\beta_{\infty}^{2} t(z)},
$$
which has the solution [754] (Exercise 18.3)

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-08_395_791_1520_439.jpg)
Figure 18.2. Density of states (DOS) for an s band in a simple cubic lattice with nearest-neighbor interactions. The recursion is up to $N=20$ levels on cells of size $(21)^{3}$ with open boundary conditions (left) and periodic boundary conditions (right). Compared to the schematic DOS in Fig. 14.4 recursion yields correct features, although there are oscillations. The similarity of the two results demonstrates the insensitivity of local properties to the boundary conditions. (The small asymmetry results from odd-length paths to its image in an adjacent cell.) From [754].

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-09_574_1277_243_198.jpg)
Figure 18.3. Electronic density of states (DOS) for liquid $\mathrm{Fe}(\mathrm{a})$ and $\mathrm{Co}(\mathrm{b})$ calculated with the tight-binding LMTO method (Section 17.6) and recursion [726]. The liquid was simulated by 600 atom cells generated by classical Monte Carlo and empirical interatomic potentials. The density is similar to the crystal (see, for example, the canonical DOS in Fig. 16.12) broadened by the disorder. From [726].

$$
t(z)=\frac{1}{2 \beta_{\infty}^{2}}\left\{\left(z-\alpha_{\infty}\right)-\left[\left(z-\alpha_{\infty}\right)^{2}-4 \beta_{\infty}^{2}\right]^{1 / 2}\right\}
$$

This has the appealing form of a terminator that is an analytic square root function, which is real outside the range $\alpha_{\infty} \pm 2\left|\beta_{\infty}\right|$ and has a branch cut corresponding to a band width $4\left|\beta_{\infty}\right|$. The ideal choice is that which yields the correct band width. In actual practice it is important not to choose $\left|\beta_{\infty}\right|$ too small in which case there are spurious delta functions in the range between the real band width and the approximate interval $\alpha_{\infty} \pm 2\left|\beta_{\infty}\right|$. If the range is overestimated, there is broadening but no serious problems.

An example of the use of the recursion method is shown in Fig. 18.2 for the density of states (DOS) for an s band in a simple cubic lattice with nearest-neighbor interactions. The bands are given analytically in Section 14.5 and the DOS is shown schematically in Fig. 14.4. In comparison, the DOS calculated with the recursion method up to $N=20$ levels shows correct features, but with added oscillations. Other types of terminators can improve the convergence to the exact result [732]. The two results shown in Fig. 18.2 are for open and periodic boundary conditions, showing the basic point of the insensitivity of local properties to the boundary conditions.

The recursion method is very powerful and general. It is not limited to tight-binding and it can be applied to any hermitian operator to generate a continued fraction form for the Green's function. This is a stable method to generate the density of states so long as care is taken in constructing a proper terminator for the continued fraction [732, 749, 753]. An example is shown in Fig. 18.3, which shows the electronic density of states of liquid Fe and Co determined using the tight-binding LMTO method (Section 17.6) and recursion [726]. The actual calculations were done on 600 atom cells with atomic positions generated by classical Monte Carlo methods with empirical interatomic potentials. This illustrates a
powerful combination of the recursion approach with a basic electronic structure method that is now widely used for many problems in complicated structures and disordered systems.

Determination of the moments of the density of states is also a powerful tool to extract information in an $\mathrm{O}(N)$ fashion. Moments of the local DOS for basis function $m$,

$$
\mu_{m}^{(n)} \equiv\langle m|[\hat{H}]^{n}|m\rangle,
$$

in principle contain all the information about the local DOS, and thus about all local properties. The basic ideas are described in Section L.7, where the two issues, generating the moments efficiently and inverting the moment information to reconstruct the DOS are emphasized.

There are a number of ways to generate the moments; one approach, which is very stable, is to construct the moments in terms of the tridiagonal matrix elements generated by the Lanczos algorithm. For the state labeled 0 , the moments can be written [749]

$$
\begin{aligned}
& \mu_{0}^{(0)}=1 \\
& \mu_{0}^{(1)}=\alpha_{0} \\
& \mu_{0}^{(2)}=\alpha_{0}^{2}+\beta_{1}^{2} \\
& \mu_{0}^{(3)}=\alpha_{0}^{3}+2 \alpha_{0} \beta_{1}^{2}+\alpha_{1} \beta_{1}^{2} \\
& \mu_{0}^{(4)}=\alpha_{0}^{4}+3 \alpha_{0}^{2} \beta_{1}^{2}+2 \alpha_{0} \alpha_{1} \beta_{1}^{2}+\alpha_{1}^{2} \beta_{1}^{2}+\beta_{1}^{2} \beta_{2}^{2}+\beta_{1}^{4}
\end{aligned}
$$

and so forth.
Inversion of the moments to find the DOS is the well-known, difficult, "classical moment problem" [822] discussed in Section L.7. As an example of the construction of the density of states using moments for an actual problem done in $\mathrm{O}(N)$ fashion, Fig. 18.4 shows the calculated [755] density of states (DOS) of the series of fullerenes (carbon clusters with flat graphene-like facets and 12 pentagons at the vertices, calculated by an $\mathrm{O}(N)$ method [756] as described in Section 18.5) showing the progression from discrete spectra small molecules to the continuous spectrum of graphene with critical points of a two-dimensional crystal. The results for the large fullerenes up to $\mathrm{C}_{3840}$ demonstrate the exquisite details that can be resolved with $\approx 150$ moments using the maximum entropy method [757] discussed in Section L.7. Similarly, the phonon spectrum can be calculated in an $\mathrm{O}(N)$ manner [758].

## Bond Order and Forces in Recursion

A key problem with the recursion method is the difficulty in computing off-diagonal matrix elements of $G$ that are essential for forces. The expression in terms of the density matrix is given in Eq. (14.28); omitting the simple two-body term, the contribution from the sum of eigenvalues is given by

$$
\mathbf{F}_{I}=-\operatorname{Tr}\left\{\hat{\rho} \frac{\partial \hat{H}}{\partial \mathbf{R}_{I}}\right\}=-\sum_{m, m^{\prime}} \rho_{m, m^{\prime}} \frac{\partial H_{m, m^{\prime}}}{\partial \mathbf{R}_{I}}
$$

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-11_936_701_247_484.jpg)
Figure 18.4. Density of states (DOS) for electrons in the fullerenes with size from $\mathrm{C}_{60}$ to $\mathrm{C}_{3840}$ [755] calculated using tight-binding model of [619]. The structures were also calculated by an $\mathrm{O}(N)$ method [756] as described in Section 18.5. The smaller molecules and graphene were computed using diagonalization methods and the DOS for the larger fullerenes was calculated by the method of moments as implemented in [757] (see Section L.7). The figure illustrates the evolution of the DOS from delta functions of the $\mathrm{C}_{60}$ molecule to the spectrum of graphene shown in the bottom panel, which has the critical point features of a two-dimensional DOS, as shown in Fig. 14.4. From [755].

General expressions in terms of Green's functions with localized bases are given by Feibelman [663]. The generic problem is the calculation of 'bond order," which is the offdiagonal components of the density matrix $\rho_{m, m^{\prime}}$ that correspond to bonding and are given by integrals over $G_{m, m^{\prime}}(z)$ analogous to Eqs. (18.8)-(18.10). There has been considerable work to derive efficient recursion-type expressions for the bond order [750-752]. The basic idea is that off-diagonal terms $G_{m, m^{\prime}}(z)$ can be calculated using recursion with a starting vector

$$
\psi_{0}=\frac{1}{\sqrt{2}}\left[\chi_{m}+\mathrm{e}^{\mathrm{i} \theta} \chi_{m^{\prime}}\right],
$$

and computing $G_{m, m^{\prime}}(z)$ from

$$
G_{m, m^{\prime}}(z)=\frac{\partial G_{0,0}^{\lambda}(z)}{\partial \lambda},
$$

with $\lambda=\cos (\theta)$. Further generalizations of this idea have been derived as described in [752] with a summary in [749].

## "Divide and Conquer" or "Fragment" Method

One of the first $\mathrm{O}(N)$ methods is based directly on the argument that the interior of a large region depends only weakly on the boundary conditions. The procedure termed "divide and conquer" [759] or a fragmentation method (see [740] for a review) is to divide a large system into small subsystems each of size $N_{\text {small }}$, for example the central orbital (gray) plus the set of orbitals shown as heavy circles in the left side of Fig. 18.1. For each of these systems one can solve for the electronic eigenstates using ordinary $N^{3}$ methods. For each small system one must add buffer regions of size $N_{\text {buffer }}$ (the outer orbitals in Fig. 18.1) large enough so that the density and energy in the original small subsystem converges and is independent of the buffer termination. The solution for the density and other properties is then kept only for the interior of each small region. The division of the system into nonoverlapping regions shown in the right side of Fig. 18.1 also involves using a buffer to calculate the functions in a region, as explained in Fig. 12.6. Using traditional methods, the cost is of order $\left(N_{\text {small }}+N_{\text {buffer }}\right)^{3}$ for each subsystem, which may be prohibitive, especially for three-dimensional systems where $N_{\text {buffer }}$ may need to be very large. However, the calculations for each subsystem can be done in parallel and the overall method is $\mathrm{O}(N)$ for large enough systems. This approach is particularly applicable for long linear molecules with large energy gaps (i.e., small localization lengths (see Chapter 24)) that are important in biochemistry (see, e.g., [741] which makes case for large-scale DFT calculations).

## Polynomial Expansion of the Density Matrix

One class of methods uses the form in Eq. (18.4) directly and expands the Fermi function in Eq. (18.4) in powers of the hamiltonian. This is the approach used, e.g., in [760] and [761]. The basic requirement is for the expansion to have the same properties as the Fermi function, i.e., that all states with eigenvalues far above the Fermi energy $\mu$ have vanishing weight, all those well below $\mu$ have unity weight, and the variation near $\mu$ is reproduced accurately. This is difficult to accomplish in an expansion; however, if the eigenvalues are limited to the range [ $E_{\text {min }}, E_{\text {max }}$ ], then the expansion can be done efficiently using Chebyshev polynomials $T_{n}$ defined in Section K.5. The advantage of the Chebyshev polynomials is that they are orthogonal and fit the function over the entire range $[-1,+1]$ (see Section K.5) and they can be generated recursively using the relation (K.19). Let us define $\Delta E=E_{\text {max }}-E_{\text {min }}$, the scaled hamiltonian operator $\tilde{H}=(\hat{H}-\mu \hat{I}) / \Delta E$, and the scaled temperature $\tilde{\beta}=\beta \Delta E$. Then we can express the expansion of the Fermi operator as

$$
\hat{F}[\hat{H}]=\frac{1}{1+\mathrm{e}^{\beta(\hat{H}-\mu)}} \rightarrow \frac{c_{0}}{2} \hat{I}+\sum_{j=1}^{M_{p}} c_{j} T_{j}(\tilde{H}) .
$$

The highest power needed in the expansion depends on the ratio of the largest energy in the spectrum to the smallest energy resolution required. The higher the temperature the lower
the power needed, since the Fermi function is smoother. For a metal, $T$ must be of the order of the actual temperature (or at least smaller than the energy scale on any variations in the states near $\mu$ ). For insulators, a larger effective $T$ can often be chosen so long as states below (above) the gap are essentially filled (empty). For hamiltonians that are bounded (such as in tight-binding), the ratio $E_{\max } / T$ can be estimated and powers $\approx 10$ to 100 are needed for realistic cases.

The key idea is that all operations can be done by repeated applications of $\hat{H}$ to a basis function, which amounts to repeated multiplication of a matrix times a vector. Each of the basis functions shown in Fig. 18.1 is treated one at a time. ${ }^{5}$ In the general case, this procedure scales as $N_{\text {basis }}^{2}$, since it involves multiplication of a vector by the matrix. However, if $\hat{H}$ is sparse, only a few matrix elements are nonzero (e.g., the nonzero elements in a tight-binding hamiltonian that involve only a few neighbors) and the multiplication, times one localized basis function, is independent of the size of the system. Furthermore, if we invoke the localization property of the density matrix, all matrix operations can be made sparse, so that the calculation scales as order $N_{\text {basis }} \propto N$. This method has two great advantages: (1) the computation scales linearly with the number of other basis functions included in the maximum range, compared to cubic scaling in the "divide and conquer" and the variational function methods and (2) the algorithm is perfectly parallel. Major disadvantages are (1) that the results of the expansion are not variational since the truncation errors can be of either sign and (2) the fact that an independent calculation must be done for each orbital means that information is discarded, in comparison to the variational methods that exchange information between the subparts of the system.

The Chebyshev expansion method can be a very efficient procedure if the basis set is small, e.g., in tight-binding models, where $M$ is only a factor of order 2 larger than $N$. However, it fails for unbounded spectra, because the polynomial expansion must be taken to higher and higher orders as the range of the spectrum is increased. For a typical plane wave calculation, high powers would be required since the energy range is large and $N_{\text {basis }} \gg N$.

## Inverse Power Expansion of the Density Matrix

There are several approaches that work with an unbounded spectrum employing operators that properly converge at high energies. One is the inverse power method, which is in essence a Green's function approach, Section D.5, and is closely related to the recursion method, Section M.5. In this approach, one expands the Fermi function as follows:

$$
\hat{F}[\hat{H}]=\frac{1}{1+\exp [\beta(\hat{H}-\mu)]} \rightarrow \sum_{i=1}^{M_{\text {pole }}} \frac{w_{i}}{\hat{H}-z_{i}}
$$

Using the well-known relations for contour integration, the sum over poles on the real axis can be converted into an integral in the complex plane enclosing the poles [306, 704, 763]

[^3]![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-14_501_1174_243_247.jpg)
Figure 18.5. Total energy of Cu and Mo calculated using multiple-scattering theory with localized regions, plotted as a function of the radius of the localization region [704]. These are, in fact, hard cases, since the density matrix is most delocalized in perfect crystals, leading to the sharp variations shown. Provided by Y. Wang; similar to [704]

as discussed in Section D. 5 and shown schematically in Fig. D.1. For each of the terms with $z_{i}$ in the complex plane, the inverse operator $\hat{G}_{i}\left(z_{i}\right)$ can be found in a basis by solving linear equations $\left(\hat{H}-z_{i}\right) \hat{G}_{i}\left(z_{i}\right)=I$. In terms of basis functions in real space, the operators $\hat{G}_{i}\left(z_{i}\right)$ are more localized for large complex $z_{i}$, which is advantageous for calculations (Exercise 18.5). Their maximum range is where the contour crosses the real axis. In order to describe the contour integral accurately in an insulator one needs the number of poles $M_{\text {pole }} \propto\left(\mu-E_{\text {min }}\right) / E_{\text {gap }}$; in a metal there is no gap and an accurate evaluation of the integral near the axis requires poles with a more dense spacing $\propto T$. An advantage of this approach is that, unlike the power expansion, it always converges independent of the high-energy spectrum. Furthermore, it corresponds to the physical picture that highenergy processes are more localized, and low-energy ones more delocalized. An example of multiple-scattering Green's function calculations [704] is shown in Fig. 18.5.

## Exponential Operators

Perhaps the most fundamental approach of all is to work directly with the time-dependent Schrödinger equation. The density matrix for quantum statistics is $\exp (-\beta \hat{H})$, which is equivalent to the imaginary time propagator. Thus essentially the same techniques can be used as in the real-time methods of Section 21.6. As $\beta \rightarrow \infty$, the operation of $\exp (-\beta \hat{H})$ on any wavefunction $\Psi$ projects out of the ground state provided it is not orthogonal to $\Psi$. The expressions can be evaluated using the fact that $\exp (-\beta \hat{H})=(\exp (-\delta \tau \hat{H}))^{n}$, where $\delta \tau=\beta / n$ represents a temperature that is higher by a factor $n$. In the high-temperature, short-time regime, the operations can be simplified using the Suzuki-Trotter decomposition, as in Eq. (21.18) rewritten here,

$$
\exp [-\delta \tau(T+V)] \simeq \exp \left(-\frac{1}{2} \delta \tau V\right) \exp (-\delta \tau T) \exp \left(-\frac{1}{2} \delta \tau V\right),
$$

which is factored into exponentials of kinetic and potential terms. One approach for the kinetic term is to use an implicit method that solves linear equations (see Section M. 10 and [764]). One can also use FFTs to transform from real space (where $V$ is diagonal) to reciprocal space (where $T$ is diagonal) as in Section M.11. The former is widely used for quantum dots [764] and the latter has been used in simulations, e.g., of hydrogen fluid at high temperature and pressure [765].

### 18.5 Variational Density Matrix Methods

Two properties must be satisfied ${ }^{6}$ by the density matrix $\hat{\rho}$ at $T=0$ :

- "Idempotency," which literally means $\hat{\rho}^{2}=\hat{\rho}$, which is equivalent to requiring all eigenvalues of $\hat{\rho}$ to be 1 or 0 .
- The eigenvectors of the density matrix with eigenvalue 1 are the occupied eigenvectors of the hamiltonian.

Li et al. [767] showed how to use a minimization method to drive the density matrix to its proper $T=0$ form. See also Exercise 18.7 for further details. The starting point is the "McWeeny purification [275]" idea: if $\tilde{\rho}_{i j}$ is an approximate trial density matrix with eigenvalues between 0 and 1 , then the matrix $3 \tilde{\rho}_{i j}^{2}-2 \tilde{\rho}_{i j}^{3}$ is always an improved approximation to the density matrix with eigenvalues closer to 0 or 1 . This is illustrated in Fig. 18.6 (left panel), which shows the function $y=3 x^{2}-2 x^{3}$. It is easy to see that for $x<1 / 2, y<x$, i.e., the occupation is closer to zero, whereas for $x>1 / 2, y>x$, i.e., the occupation is closer to one. However, if one iterates the matrix using the purification equation alone, there is no reason for the eigenvectors to satisfy the second requirement, i.e., to correspond to the lowest-energy states. In order to make a functional that when minimized yields the proper idempotent density matrix that also minimizes the total energy, one can modify the usual expression, (18.5), for the grand potential at $T=0$ to use the "purified" form,

$$
\Omega_{s}=\operatorname{Tr} \hat{\rho}(\hat{H}-\mu) \rightarrow \operatorname{Tr}\left(3 \hat{\rho}^{2}-2 \hat{\rho}^{3}\right)(\hat{H}-\mu)
$$

Since the functional is minimum for the true density matrix, the energy given by Eq. (18.23) is variational.

The functional can be minimized by iteration using the gradients

$$
\frac{\partial \Omega_{s}}{\partial \hat{\rho}}=3[\hat{\rho}(\hat{H}-\mu)+(\hat{H}-\mu) \hat{\rho}]-2\left[\hat{\rho}^{2}(\hat{H}-\mu)+\hat{\rho}(\hat{H}-\mu) \hat{\rho}+(\hat{H}-\mu) \hat{\rho}^{2}\right]
$$

which denotes the matrix expression for the derivative with respect to each of the elements of the density matrix $\hat{\rho}$. So long as the density matrixis never allowed to go into the

[^4]![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-16_549_1266_245_202.jpg)
Figure 18.6. Functional forms for the cubic "McWeeny" purification algorithm [767] for the density matrix (left) and the quadratic Mauri-Ordejon-Kim functional [768-770] for the wavefunctions (right). "Purification" of the density matrix results because the function $3 x^{2}-2 x^{3}$ is always closer to 0 or 1 than the input value $x$, as shown by the dashed line $(=x)$. The form $2 x^{2}-x^{4}$ applied to the localized wavefunctions is minimized for occupied functions normalized to 1 , empty functions to 0 .

unphysical region where the eigenvalues are $<0$ or $>1$, then the algorithm is stable and the gradients always point toward a lower energy and an improved density matrix. Any matrix satisfying the physical conditions can be used as a starting point. A possible choice is $\rho_{i j}=\delta_{i j}\left(N_{\text {elec }} / N_{\text {basis }}\right)$, and more optimal choices can be found for any particular problem. The method can be extended to nonorthogonal bases [771]. A principle difficulty with this method is that it requires explicit operations of multiplying matrices that are of the size of the basis $N_{\text {basis }}$. Thus it is appropriate for small bases such as in tight-binding, but not for large bases, such as plane waves where $N_{\text {basis }} \gg N_{\text {elec }}$ (but see Section 18.8 for alternative methods).

An example of the density matrix purification algorithm of [767] is the study of selected large icosahedral fullerenes (up to $\mathrm{C}_{8640}$ ) for which the structures were optimized [756] using the tight-binding potential of Xu et al. [619]. The calculations indicate a progression from near-spherical shape for smaller fullerenes to a faceted (polyhedral) geometrical shape made up of graphite-like faces, sharply curved edges, and 12 pentagons at the vertices. The same conclusions were reached independently [772] using the linear-scaling Wannier function approach (Section 18.6). These structures up to $\mathrm{C}_{3840}$ were used in the calculation of the DOS in Fig. 18.4.

The density matrix methods [767] can also be employed for MD calculations using the force theorem for the forces in terms of the density matrix and the derivative of the hamiltonian, as given in Section 14.11. The same tight-binding potential [619] as employed for the giant fullerenes has been used in simulations of liquid and amorphous carbon. The calculated radial density distribution $g(r)$ of liquid carbon at ordinary pressure agrees well with plane wave Car-Parrinello calculations and have been done with both usual matrix diagonalization [619] and linear-scaling density matrix methods [773]. In addition, the
results are essentially the same as found in [760], which used the Fermi projection operator approach of Section 18.4. The combination of tight-binding and linear-scaling methods has allowed calculations on larger sizes and longer times than is feasible using other methods.

### 18.6 Variational (Generalized) Wannier Function Methods

A different approach is to work with the localized wavefunctions in Eq. (18.2) rather than with the density matrix itself. However, in searching for the Wannier-like functions it is not convenient to require the constraint of orthonormality implicit in Eq. (18.2). One possibility is to work with nonorthogonal functions and use the correct general expression

$$
E_{\text {total }}=\operatorname{Tr} \hat{\rho} \hat{H}=\sum_{i, j=1}^{N} S_{i j}^{-1} H_{j i}
$$

where $S$ is the overlap matrix. Here matrices are defined by $H_{j i}=\left\langle\tilde{w}_{j}\right| \hat{H}\left|\tilde{w}_{i}\right\rangle$ (or with $\tilde{w} \rightarrow w$ for orthogonal functions), etc. However, the entire problem can be rewritten in a more advantageous form through the invention of a new class of functionals [768, 769], the simplest of which is

$$
\tilde{E}_{\text {total }}=\sum_{i=1}^{N} H_{i i}-\sum_{i, j=1}^{N}\left(S_{i j}-\delta_{i j}\right) H_{j i}=\sum_{i, j=1}^{N}\left(2 \delta_{i j}-S_{i j}\right) H_{j i}
$$

where the terms $S_{i j}-\delta_{i j}$ are like Lagrange multipliers that replace the constraint of orthonormality. The special property of $\tilde{E}$ is that $\tilde{E}_{\text {total }} \geq E_{\text {total }}$ for all wavefunctions whether or not they are normalized or orthogonal. Since $\tilde{E}_{\text {total }}=E_{\text {total }}$ for the orthonormal functions, it follows that one can minimize $\tilde{E}_{\text {total }}$ with respect to the wavefunctions with no constraints, leading to orthonormal functions at the minimum.

The behavior of $\tilde{E}_{\text {total }}$ considered as a functional of the wavefunctions can be seen by expressing Eq. (18.26) in terms of the eigenvectors. (Added discussion can be found in Exercise 18.8.) If the coefficient of the $j$ th eigenvector is $c_{j}$, then the contribution to $\tilde{E}$ is $\epsilon_{j}\left(2 c_{j}^{2}-c_{j}^{4}\right)$. Figure 18.6 (right panel) plots the function $y=2 x^{2}-x^{4}$, which shows the consequences graphically. For eigenvalues that are negative there is an absolute minimum at $\left|c_{j}\right|=1$, i.e., a properly normalized function. The same holds for the general case where we have many states, and minimization leads to an orthonormal set of functions that spans the space. For positive eigenvalues there is a local minimum at $c_{j}=0$, but also a runaway solution in the unphysical $\left|c_{j}\right|>1$ that must be avoided.

The functional has been extended by Kim et al. [770] to include more states than electrons and to minimize the grand potential $\Omega_{s}=\operatorname{Tr}\{\hat{\rho}(\hat{H}-\mu)\}$, which can be written in matrix form analogous to Eq. (18.26) (Exercise 18.9)

$$
\tilde{E}_{s}^{\prime}=\operatorname{Tr}\{(2-S)(H-\mu I)\},
$$

where $S$ and $H$ denote matrices $S_{i j}$ and $H_{i j}$ and $I$ is the unit matrix. From the above reasoning it follows that Eq. (23.27) is minimized by filling all states below the Fermi

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-18_318_886_251_392.jpg)
Figure 18.7. Projection on the $\{0 \overline{1} 1\}$ plane of a rodlike $\{311\}$ defect in silicon containing four interstitial chains $I$. The structure of $\{311\}$ defects commonly observed in ion-implanted silicon is characterized by random combinations of $/ I I /$ and $/ I O /$ units indicated by the boxes. The calculations showed that the extended defects are much lower in energy than isolated interstitial. Figure provided by J. Kim

energy, and leaving empty all those above. (It is not difficult to restrict the variations to avoid the runaway solution.) One can work with a limited number of states (somewhat larger than the number of electrons) and all operations scale as the number of these states. Thus this functional achieves the additional desired feature that the incorporation of extra states makes it easier to reach the minimum, and one can avoid being trapped in the wrong states at level crossings, etc.

An example of calculations using the Kim et al. functional is calculation to determine the structure of extended defects commonly observed in ion-implanted silicon [637, 638]. The structure shown in Fig. 18.7 was determined using by $\mathrm{O}(N)$ molecular dynamics tightbinding calculations, which allowed simulations to be run long enough for the atoms to form rodlike structures. After determination of the extended structure, DFT calculations were used to establish that the extended defects are significantly lower in energy ( $\approx 2 \mathrm{eV}$ per interstitial) than for isolated interstitials in the bulk.

## Nonorthogonal Orbitals

Generalizing the functional to non-orthogonal localized orbitals $\tilde{w}_{i}$, as in Eq. (18.7), has the advantage that the $\tilde{w}_{i}$ can be shorter range and more transferable than orthogonal Wannier functions. The latter property is illustrated in Section 23.4; it means that good guesses can be made for the orbitals initially and as the atoms move in a simulation. The difficulty is twofold: finding an efficient way to construct the inverse and dealing with the singular $S$ matrix that results if one allows extra orbitals that have zero norm as in the Kim functional, Eq. (18.27). In the latter case, the size of $S$ is the number of orbitals, but the rank (see below) is the number of electrons, i.e., $N=\operatorname{rank}\{S\}$.

An elegant formulation has been given in [746] and [774], building upon earlier work [745, 775], and using the same ideas as for generating nonorthogonal functions in Section 23.4. The first step is to define the inverse $S^{-}$of a singular matrix $S$ by the relation [746]

$$
S S^{-} S=S,
$$

so that $S^{-}=S^{-1}$ if $S$ is nonsingular. Next, a functional can be defined that accomplishes the inverse in a way similar to the "Hotelling" method [776]

$$
\operatorname{Tr}\left\{B S^{-}\right\}=\min \operatorname{Tr}\{B(2 X-X S X)\}
$$

where $B$ is any negative definite matrix and the minimization is for all possible hermitian matrices $X$ (Exercise 18.6). Putting this together with the generalization of expression (18.25) for the energy

$$
E_{\text {total }}=\operatorname{Tr} \hat{\rho} \hat{H}=\sum_{i, j=1}^{N} S_{i j}^{-} H_{j i}
$$

leads to the functional

$$
\tilde{E}_{\text {total }}^{\prime}(N) \rightarrow \operatorname{Tr}[2 X-X S X][H-\eta S]+\eta N
$$

where the constant $\eta$ is added to shift the eigenvalues to negative energies. Finally, even the constraint on the rank of $S$ can be removed by defining the functional in terms of the Fermi energy $\mu$ as

$$
\tilde{E}_{\text {total }}^{\prime}(N) \rightarrow \operatorname{Tr}[2 X-X S X][H-\eta S]+(\eta-\mu) \operatorname{rank}(S)+\mu N,
$$

where the same trick can be used for $\operatorname{rank}(S)$

$$
\operatorname{rank}(S)=\operatorname{Tr}\left[S S^{-}\right]=-\min \{\operatorname{Tr}[(-S)(2 X-X S X)]\}
$$

The energy $\tilde{E}_{\text {total }}^{\prime}(N)$ is the minimum for all nonorthogonal wavefunctions $\tilde{w}_{i}$ that define the $S$ and $H$ matrices and all hermitian matrices $X$.

If the orbitals are confined, then the minimum of functionals Eq. (18.31) or (18.32) is for nonorthogonal orbitals, since they are more compact than orthogonal ones. Furthermore, one can constrain the orbitals further to require maximal localization, in which case the functionals still give the same energy, and the orbitals are more physical and intuitive, as discussed in Section 23.4.

## Combining Minimization and Projection

There are advantages to both the projection methods and the variational methods. An example of a calculation that combines these methods is the calculation of Wannier functions in disordered systems [777-779]. The variational approaches using Wannier functions suffer from the problem that they scale as $M^{3}$, where $M$ is the size of the localization region. Furthermore, it has been found in practice [769] that convergence is slow due to the fact that the energy function is only weakly dependent on the tails of the function. On the other hand, the projection method scales as $M$ and can be used to improve the functions in the tails. Stephan and coworkers [777, 778] combined the methods to (1) project Wannier-like functions in a large region; (2) find the largest coefficients, which leads to the best "self-adaptive" functions instead of imposing an arbitrary cutoff; and (3) use minimization method functions to improve the final functions. An example of the density of
a bonding-type Wannier function calculated for a model of amorphous Si containing 4,096 atoms. The result is plotted on a logarithmic scale extending over 20 orders of magnitude in shown a beautiful color figure in [779].

### 18.7 Linear-Scaling Self-Consistent Density Functional Calculations

Full self-consistent density functional theory calculations can be cast in an $\mathrm{O}(N)$ linearscaling form, since the charge density can be computed in $\mathrm{O}(N)$ fashion and thus one can build the hamiltonian (Section 18.3) with effort that scales as $\mathrm{O}(N)$. The difference from the tight-binding calculation is that one must explicitly represent the orbitals and one must deal with self-consistency. Because of the difficulties in carrying out such full calculations on very large systems, much less work has been done than with the simpler tight-binding methods. One such approach is illustrated in Fig. 18.5 using the KKR multiple-scattering approach [704]. Methods using wavelets have been used on many systems, such as MD simulations on clusters of water molecules, large molecules, etc. [588, 592].

Here we give results only for one of the earliest calculations that shows the possibilities, a calculation [780] for a complete turn of a selected DNA molecule is shown in Fig. 18.8.

![](./images/68d5ca19-a6bf-4c4e-b913-3e8dacbabca3-20_823_1262_1062_206.jpg)
Figure 18.8. Electron density of selected eigenstates in a DNA molecule calculated one complete turn using the self-consistent local orbital SIESTA code and a GGA functional. The density contour shown is $5 \times 10^{-4} a_{0}^{-3}$. The lighter shaded region is the sum of densities of the 11 highest occupied (HOMO) states, and the darker region represents the 11 lowest unoccupied (LUMO) states. Calculations of comparable complexity have been done using gaussian bases and linear-scaling density matrix methods, e.g., for a fragment of an RNA molecule with 1,026 atoms [652]. Figure provided by E. Artacho; similar to results in [780]

The density, potential, and thermal simulations of the atoms were calculated using $\mathrm{O}(N)$ procedures in the SIESTA code [646]. For a given structure, the resulting potential was then used in an ordinary $N^{3}$ diagonalization (One could also use a more efficient inverse iteration procedure such as the RMM-DIIS method; see Section 18.9 and Appendix M.) to find selected eigenstates, in particular the fundamental gap between the lowest unoccupied (LUMO) and highest occupied (HOMO) orbitals, which are shown in Fig. 18.8. Further information is given in [780], which investigated the effects of disorder (a mutation) upon localization of the states and electrical conductivity. Calculations on similar size systems, including a fragment of an RNA molecules with 1,026 atoms, have been done using linearscaling gaussian density matrix methods [652]. See, for example, [739-741] for reviews of DFT and quantum chemistry wavefunction methods and applications.

### 18.8 Factorized Density Matrix for Large Basis Sets

Large basis sets such as plane waves and grids are desirable in order to have robust methods that always converge to the correct answer. For such approaches, however, straightforward application of linear-scaling approaches may not be feasible. In particular, the density matrix formalism leads to unwieldy expressions since it requires matrices of size $N_{\text {basis }} \times N_{\text {basis }}$. Even if the matrix is sparse, it still becomes very large in the limit of finely spaced grids. How can it be feasible to use density matrix methods with such bases? The answer is remarkably simple: only a limited number of orbitals are needed, but each orbital needs to have many degrees of freedom. This is the basis for replacing Eq. (18.23) with a factorized form [781]

$$
\rho\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\sum_{i j} \Phi_{i}^{*}(\mathbf{r}) K_{i j} \Phi_{j}\left(\mathbf{r}^{\prime}\right),
$$

where $\Phi_{j}(\mathbf{r})=\sum_{\nu} c_{j}^{\nu} \phi_{\nu}(\mathbf{r})$ denotes an orbital expanded in a (large) basis set $\phi_{\nu}(\mathbf{r})$ and $K_{i j}$ is a matrix of a size comparable to that needed in a tight-binding calculation. Thus the "purified" density matrix in the reduced space of the orbitals can be written

$$
K=3 L O L-2 L O L O L,
$$

where $L$ is a trial density matrix and $O$ is the overlap matrix of the orbitals. In this form, one minimizes the functional with respect to $L_{i j}$ and the coefficients $c_{j}^{\nu}$. Different choices lead to different trade-offs between the number of orbitals involved in the matrix operations in Eq. (18.35) and the number of basis functions needed for each orbital in Eq. (18.34). Clearly, the general nonorthogonal formulation in Eqs. (18.31) or (18.32) can be even more advantageous as a general approach to making the orbitals as confined as possible, and therefore as optimal as possible for representation in a large basis.

The same idea can, of course, be applied to the Wannier-function-type methods. In fact, the local orbital approach is already in this form, since a limited number of localized Wannier functions are each expanded in a basis of atomic-like orbitals. One can also expand each localized function in a representation on a grid, as is done, e.g., in [782], where
nonorthogonal functions are used in a method similar to that proposed by Stechel and coworkers [745, 775]. An expansion in overlapping spherical waves has been proposed by Haynes and Payne [783].

### 18.9 Combining the Methods

Most of the $\mathrm{O}(N)$ methods described in this chapter are based on the localization of the density matrix in space: they capture the physics and perform well for wide-bandgap insulators, highly disordered materials, and metals at (very) high temperature. But they fail on all counts whenever the localization length is large, e.g., in a good metal at ordinary temperatures. Such states can be isolated by methods that separate the physics by localization in energy, i.e., spectral methods (Appendix M), rather than by localization in space. How can one combine the methods to take advantage of the properties of each? There can be many approaches, but all have the general feature that $\mathrm{O}(N)$ methods can be used for solution at one level, e.g., a metallic system at very high temperature $T$, and the spectral method for the difference between the high- and low- $T$ solutions that depends only on states near the Fermi energy.

Spectral methods described in Appendix M are designed to find selected states efficiently. If the hamiltonian operator can be cast in sparse form (i.e., the hamiltonian is localized in real space or one can use transforms as in Section M.11) each state can be found with effort $\propto N_{\text {basis }}$ or $\propto N_{\text {basis }} \ln N_{\text {basis }}$. Of course, the usual approach in which all states are desired requires effort that scales as $\propto N \times N_{\text {basis }} \propto N^{2}$ or $\propto N^{2} \ln N_{\text {basis }}$. The effort needed to treat only the states near the Fermi energy is $\alpha N^{2} \times \mathrm{k}_{\mathrm{B}} \mathrm{T} / \mu$, where $T$ is the needed smearing for an efficient $\mathrm{O}(N)$ scheme and the Fermi energy $\mu$ represents the characteristic total energy range of the electronic states. Although the effort scales as $\propto N^{2}$, there is an approach [744] that takes advantage of the fact that states vary smoothly near the Fermi energy and create a linear-scaling spectral resolution approach that is applicable to metals.

## SELECT FURTHER READING

Reviews:
Bowler, D. R. and Miyazaki, T., "O( $N$ ) methods in electronic structure calculations," Rep. Prog. Phys., 75:036503, 2012. A review with extensive description of methods references to available codes.

Cole, D. J. and Hine, N. M. H., "Applications of large-scale density functional theory in biology" J. Phys. Condens. Matter 28:393001, 2016. Makes case for large-scale DFT and refers to various $\mathrm{O}(N)$ methods.
Gordon, M. S., Fedorov, D. G., Pruitt, S. G., and Slipchenko, L. V., "Fragmentation methods: A route to accurate calculations on large systems," Chem. Rev. 112:632, 2012. A review of methods used in chemistry.
Goedecker, S., "Linear scaling electronic structure methods," Rev. Mod. Phys. 71:1085-1123, 1999. Compares many methods.
Arias, T. A., "Multiresolution analysis of electronic structure: Semicardinal and wavelet bases," Rev. Mod. Phys. 71:267-311, 1999. Provides a more mathematical exposition of the analysis.

Method using Daubechies wavelets:
Mohr, S., Ratcliff, L. E., Boulanger, P., Genovese, L., Caliste, D., Deutsch, T., and Goedecker, S., "Daubechies wavelets for linear scaling density functional theory," J. Chem. Phys. 140:204110, 2014.

The recursion method:
Haydock, R., in Recursion Method and Its Applications, edited by D. G. Pettifor and D. L. Weaire (Springer-Verlag, Berlin, 1985).

Discussion of locality:
Fulde, P., Electron Correlation in Molecules and Solids, 2nd ed. (Springer-Verlag, Berlin, 1993).
Discusses localization in a many-body context.

## Exercises

18.1 Derive the result stated in the text that the normalization constant in Eq. (18.11) is given by $C_{n+1}=1 / \beta_{n}, n \geq 1$. Show this by directly calculating the normalization of $\psi_{n+1}$ assuming $\psi_{n}$ is normalized.
18.2 Derive the continued fraction representation of Eq. (18.12) using the Lanczos algorithm for the coefficients. It follows that the spectrum of eigenvalues is given by the poles of the continued fraction (i.e., the zeros of the denominator) in Eq. (18.12). (Thus the spectrum of eigenvalues is given either by the continued fraction form or by the zeros of the polynomial of the previous problem.)
18.3 Derive the form of the terminator given in Eqs. (18.13) and (18.14). Show that imaginary part is nonzero in the band range indicated, so that no poles and only continuous DOS can result in this range. In fact, there is another solution with a plus sign in the square root in Eq. (18.14); show that this is not allowed since $t(z)$ must vanish for $|z| \rightarrow \infty$.
18.4 Show that the square root form for terminator Eq. (18.14) satisfies Kramers-Kronig relations, Eq. (D.18), as it must if $G(z)$ is a physically meaningful Green's function.
18.5 Show that the Green's function $G(z)=1 /(\hat{H}-z)$ becomes more localized for large $z$ for the case where $\hat{H}$ is a short-range operator in real space. This is the essence of localization in both the recursion and Fermi function expansion methods. Hint: first consider the $z \rightarrow \infty$ limit and then terms in powers of $\hat{H} / z$.
18.6 Derive Eq. (18.29) by showing that the variation around $X=S^{-}$is quadratic and always positive for matrices $B$ that are negative definite.
18.7 This exercise is to derive the form of the "purification" functional, Eq. (18.24), that leads to idempotency of the density matrix.
(a) The first step is to demonstrate that the function $y=3 x^{2}-2 x^{3}$ has the form shown in the left panel of Fig. 18.6 and that the result $y$ is always closer to 0 or 1 than the input $x$.
(b) Next, generalize this to a matrix equation for any symmetric matrix leading to eigenvalues closer to 0 or 1 .
(c) Finally, show that the functional Eq. (23.23) minimized using the gradients Eq. (23.24) leads to the desired result.
18.8 This exercise is designed to provide simple examples of the properties of the unconstrained functional, Eq. (18.26).
(a) Consider a diagonal $2 \times 2$ hamiltonian with $H_{11}=\epsilon_{1}<0, H_{22}=\epsilon_{2}>0$, and $H_{12}= H_{21}=0$ in an orthonormal basis, $\psi_{1}$ and $\psi_{2}$. Show that minimization of the functional leads to the ground state $\psi_{1}$ properly normalized.
(b) Now consider the same basis as in part (a) but with a hamiltonian that is not diagonal: $H_{11}=H_{22}=0$ and $H_{12}=H_{21}=t$. Show that in this case the functional also leads to the properly normalized ground state $\psi=\frac{1}{\sqrt{2}}\left(\psi_{1}+\psi_{2}\right)$.
18.9 Show that the functional, Eq. (18.27), has the property that it leads to orthonormal eigenvectors for states below the Fermi energy $\mu$ and projects to zero the amplitude of any states with eigenvalue above the Fermi energy.


[^0]:    ${ }^{1}$ It is a more difficult question if all desired properties can be found in time proportional to the total size of the system; for example, there could be slow relaxation modes that become increasingly difficult to determine as the system size increases. We will not deal with such issues here.
    ${ }^{2}$ Topological insulators have introduced a new aspect of the problem: entanglement of the electron wavefunctions over macroscopic distances. One manifestation is surface states that can exist only because of properties of the bulk. This is not a short-range effect and it is closely related to the conclusion that it is not possible to construct localized Wannier functions in a system with nontrivial topology of the electronic structure (see Section 25.8). These are properties that can be considered separately from the issues considered in this chapter.

[^1]:    ${ }^{3}$ Here we use the notation of [746], which generalizes the definition of $S^{-1}$ as shown later in Eq. (18.28).

[^2]:    ${ }^{4}$ Here 0 denotes the starting state, which can be any state in the basis, e.g., any of the localized atomic-like states on site $i$.

[^3]:    ${ }^{5}$ The Chebyshev polynomial expansion can also be used with random vectors to generate a statistical estimate of extensive quantities, such as the total energy [757, 762], "maximum entropy," or related methods. This is useful for extremely large matrices where it is not feasible to take the trace.

[^4]:    ${ }^{6}$ The density matrix minimization approach can also be extended to finite temperature. Corkill and Ho [766] have used the Mermin functional to allow a continuous variation of the occupation instead of the strict idempotency requirements of the original method.

