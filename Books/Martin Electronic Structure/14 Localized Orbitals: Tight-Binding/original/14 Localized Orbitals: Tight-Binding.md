## 14

## Localized Orbitals: Tight-Binding

## Summary

Localized functions afford a satisfying description of electronic structure and bonding in an intuitive localized picture. They are widely used in chemistry and have been revived in recent years in physics for efficiency in large simulations, especially "order- $N$ " methods (Chapter 18). The tight-binding method is particularly simple and instructive since the basis is not explicitly specified and one needs only the matrix elements of the overlap and the hamiltonian. This chapter starts with a definition of the problem of electronic structure in terms of localized orbitals and considers various illustrative examples in the tight-binding approach. Two-band models are illustrated for graphene and are the basis for much of the analysis of Shockley surface states, topological insulators, and other phenomena in Chapters 22-28. Many of the concepts and forms carry over to full calculations with localized functions that are the subject of the following chapter, Chapter 15.

The hallmark of the approaches considered in this chapter and the next is that the wavefunction is expanded in a linear combination of fixed, energy-independent orbitals, each associated with a specific atom in the molecule or crystal. For example, the linear combination of atomic orbitals (LCAO) formulation denotes a basis of atomic or modified atomic-like functions. Such a basis provides a natural, physically motivated description of electronic states in materials; in fact, possibly the first theory of electrons in a crystal was the tight-binding ${ }^{1}$ method developed by Bloch [35] in 1928. The history of this approach is summarized nicely by Slater and Koster [613], who point out that the seminal work of Bloch considered only the simplest s-symmetry function and the first to consider a basis of different atomic orbitals were Jones, Mott, and Skinner [614] in 1934.

[^0]We will highlight three ways in which the local orbital, or tight-binding, formulation plays an important role in electronic structure:

- Of all the methods, perhaps tight-binding provides the simplest understanding of the fundamental features of electronic bands. In particular, this provided the original derivation of the Bloch theorem [35], which will also suffice for us to derive the theorem yet again in Section 14.1.
- Viewed as simply models for electrons on a lattice expressed in terms of a localized basis, this is the formulation of many of the most used models in physics, such as the Hubbard model for interacting electron problems (not explored here but studied in detail in the companion book [1]) and the two-band models that are the basis for understanding topological insulators in Chapters 25-28.
- Viewed as useful models to describe electronic bands and total energies, empirical tight-binding methods can provide both accurate results and valuable insights for real materials. In this approach, one assumes a form for the hamiltonian and overlap matrix elements without actually specifying anything about the orbitals except their symmetry. The values of the matrix elements may be derived approximately or may be fitted to experiment or other theory. This is generically called "tight-binding" and is widely used as a fitting procedure or as a quick (and sometimes dirty) electronic structure method. As such it is the method of choice for development of many ideas and new methods, e.g., "order- $N$ " techniques in Chapter 18. This is the subject of later sections in this chapter.
- Finally, local orbital methods are not restricted to such simplifications. They can be used as a basis to carry out a full self-consistent solution of independent-particle equations. Analytic forms, especially gaussians, are extensively used in chemistry, where standard basis sets have been developed. Alternatively, one can use atomic-like orbitals with all integrals calculated numerically. Localized orbital methods are powerful, general tools and are the subject of Chapter 15.


### 14.1 Localized Atom-Centered Orbitals

A local orbital basis is a set of orbitals $\chi_{\alpha}\left(\mathbf{r}-\mathbf{R}_{I}\right)$, each associated with an atom at position $\mathbf{R}_{I}$. In order to simplify notation, we will let $m$ denote both $\alpha$ and site $I$, so that $m=1, \ldots, N_{\text {basis }}$ labels all the states in the basis, which can also be written $\chi_{m}\left(\mathbf{r}-\mathbf{R}_{m}\right) .{ }^{2}$ In a crystal, the atoms in a unit cell are at positions $\tau_{\kappa, j}$, where $\tau_{\kappa, j}$ is the position of $j=1, \ldots, n^{\kappa}$ atoms of type $\kappa$. The composite index $\{\kappa, j, \alpha\} \rightarrow m$ allows the entire basis to be specified by $\chi_{m}\left(\mathbf{r}-\left(\tau_{m}+\mathbf{T}\right)\right)$, where $\mathbf{T}$ is a translation vector. The matrix elements of the hamiltonian of a state $m$ in the cell at the origin and state $m^{\prime}$ in the cell labeled by translation vector $\mathbf{T}$ is

$$
H_{m, m^{\prime}}(\mathbf{T})=\int \mathrm{d} \mathbf{r} \chi_{m}^{*}\left(\mathbf{r}-\tau_{m}\right) \hat{H} \chi_{m^{\prime}}\left[\mathbf{r}-\left(\tau_{m^{\prime}}+\mathbf{T}\right)\right]
$$

[^1]which applies to any orbitals $m$ and $m^{\prime}$ in cells separated by the translation $\mathbf{T}$, since the crystal is translationally invariant. Similarly, the overlap matrix is given by
$$
S_{m, m^{\prime}}(\mathbf{T})=\int \mathrm{d} \mathbf{r} \chi_{m}^{*}\left(\mathbf{r}-\tau_{m}\right) \chi_{m^{\prime}}\left[\mathbf{r}-\left(\tau_{m^{\prime}}+\mathbf{T}\right)\right]
$$

The Bloch theorem for the eigenstates can be derived by defining a basis state with wavevector $\mathbf{k}$,

$$
\chi_{m \mathbf{k}}(\mathbf{r})=A_{m \mathbf{k}} \sum_{\mathbf{T}} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}} \chi_{m}\left[\mathbf{r}-\left(\tau_{m}+\mathbf{T}\right)\right]
$$

where $\mathrm{A}_{m \mathbf{k}}$ is a normalization factor (Exercise 14.4). The analysis proceeds much like the derivation of the Bloch theorem in a plane wave basis in Sections 12.1 and 12.2, except that here the wavevector $\mathbf{k}$ is restricted to the Brillouin zone. This is sufficient since the phase factor $\mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}}$ in Eq. (14.3) is unchanged if a reciprocal lattice vector is added. Using the translation invariance of the hamiltonian, it is straightforward (Exercise 14.3) to show that matrix elements of the hamiltonian with basis functions $\chi_{m \mathbf{k}}$ and $\chi_{m^{\prime} \mathbf{k}^{\prime}}$ are nonzero only for $\mathbf{k}=\mathbf{k}^{\prime}$, with

$$
H_{m, m^{\prime}}(\mathbf{k})=\int \mathrm{d} \mathbf{r} \chi_{m \mathbf{k}}^{*}(\mathbf{r}) \hat{H} \chi_{m^{\prime} \mathbf{k}}(\mathbf{r})=\sum_{\mathbf{T}} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}} H_{m, m^{\prime}}(\mathbf{T})
$$

and

$$
S_{m, m^{\prime}}(\mathbf{k})=\int \mathrm{d} \mathbf{r} \chi_{m \mathbf{k}}^{*}(\mathbf{r}) \chi_{m^{\prime} \mathbf{k}}(\mathbf{r})=\sum_{\mathbf{T}} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}} S_{m, m^{\prime}}(\mathbf{T})
$$

Since the hamiltonian conserves $\mathbf{k}$, an eigenfunction of the Schrödinger equation in a basis always can be written in the form

$$
\psi_{i \mathbf{k}}(\mathbf{r})=\sum_{m} c_{m}(\mathbf{k}) \chi_{m \mathbf{k}}(\mathbf{r})
$$

and the secular equation for wavevector $\mathbf{k}$ is

$$
\sum_{m^{\prime}}\left[H_{m, m^{\prime}}(\mathbf{k})-\varepsilon_{i}(\mathbf{k}) S_{m, m^{\prime}}(\mathbf{k})\right] c_{i, m^{\prime}}(\mathbf{k})=0
$$

This has the same form as Eq. (12.9) except that in Eq. (14.7) the orbitals are not assumed to be orthonormal. The only fundamental sense in which local orbitals are different from any other basis is that the locality of $\chi_{m}\left(\mathbf{r}-\left(\tau_{m}+\mathbf{T}\right)\right)$ is expected to cause $H_{m, m^{\prime}}(\mathbf{T})$ and $S_{m, m^{\prime}}(\mathbf{T})$ to decrease and become negligible for large distances $\left|\tau_{m}-\left(\tau_{m^{\prime}}+\mathbf{T}\right)\right|$.

### 14.2 Matrix Elements with Atomic-Like Orbitals

Much can be gained from consideration of the symmetries of the basis orbitals and the crystal or molecule. This is the basis for tight-binding approaches and continues to be essential in full calculations (Chapter 15). An appropriate choice for basis functions is a set of atomic-like functions centered on the atom sites, i.e., functions with the same symmetry

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-04_588_752_255_459.jpg)
Figure 14.1. Schematic figures of local orbitals indicating all possible overlap and two-center hamiltonian matrix elements for $\mathrm{s}, \mathrm{p}$, and d orbitals, which are classified by the angular momentum about the axis with the notation $\sigma(m=0), \pi(m=1)$, and $\delta(m=2)$. The orbitals shown are the real combinations of the angular momentum eigenstates. Positive and negative lobes are denoted by solid and dashed lines, respectively. Note that the sign of the p orbitals must be fixed by convention; here and in Table 14.1 the positive $\mathrm{p}_{x}$ lobe is along the positive $x$-axis, etc.

as for an atom in free space but may have radial dependence modified from the atom. On each site $\kappa, j$ the basis functions can be written as radial functions multiplied by spherical harmonics,

$$
\chi_{\alpha}(\mathbf{r}) \rightarrow \chi_{n l m}(\mathbf{r})=\chi_{n l}(r) Y_{l m}(\hat{\mathbf{r}}),
$$

where $n$ indicates different functions with the same angular momentum. Real basis functions can also be defined using the real angular functions $S_{l m}^{+}=\frac{1}{\sqrt{2}}\left(Y_{l m}+Y_{l m}^{*}\right)$ and $S_{l m}^{-}=\frac{1}{\sqrt{2} i}\left(Y_{l m}-Y_{l m}^{*}\right)$ defined in Eq. (K.11). These are useful for visualization and in actual calculations, but the $Y_{l m}$ are most convenient for symmetry analysis. Examples of real s, p, and d orbitals are given in Fig. 14.1.

The matrix elements, Eqs. (14.1) and (14.2), can be divided into one-, two-, and threecenter terms. The simplest is the overlap matrix $S$ in Eq. (14.2), which involves only one center if the two orbitals are on the same site ( $\mathbf{T}=0$ and $\tau_{m}=\tau_{m^{\prime}}$ ) and two centers otherwise. The hamiltonian matrix elements in Eq. (14.1) consist of kinetic and potential terms with

$$
\hat{H}=-\frac{1}{2} \nabla^{2}+\sum_{\mathbf{T} \kappa j} V^{\kappa}\left[\left|\mathbf{r}-\left(\tau_{\kappa j}+\mathbf{T}\right)\right|\right],
$$

where the first term is the usual kinetic energy and the second is the potential decomposed into a sum of spherical terms centered on each site $\kappa, j$ in the unit cell. ${ }^{3}$ The kinetic

[^2]part of the hamiltonian matrix element always involves one or two centers. However, the potential terms may depend on the positions of other atoms; they can be divided into the following:

- One center, where both orbitals and the potential are centered on the same site. These terms have the same symmetry as an atom in free space. Spin-orbit interaction is a onecenter term that is considered in Section 14.3.
- Two center, where the orbitals are centered on different sites and the potential is on one of the two. These terms have the same symmetry as other two-center terms.
- Three center, where the orbitals and the potential are all centered on different sites. These terms can also be classified into various symmetries based on the fact that three sites define a triangle.
- A special class of two-center terms with both orbitals on the same site and the potential centered on a different site. These terms add to the one-center terms above but depend on the crystal symmetry.


## Two-Center Matrix Elements

Two-center matrix elements play a special role in calculations with local orbitals and are considered in more detail here. The analysis applies to all overlap terms and to any hamiltonian matrix elements that involve only orbitals and potentials on two sites. For these integrals the problem is the same as for a diatomic molecule in free space with cylindrical symmetry. The orbitals can be classified in terms of the azimuthal angular momentum about the line between the centers, i.e., the value of $m$ with the axis chosen along the line, and the only nonzero matrix elements are between orbitals with the same $m=m^{\prime}$. If $K_{l m, l^{\prime} m^{\prime}}$ denotes an overlap or two-center hamiltonian matrix element for states $l m$ and $l^{\prime} m^{\prime}$, then in the standard form with orbitals quantized about the axis between the pair of atoms, the matrix elements are diagonal in $m m^{\prime}$ and can be written $K_{l m, l^{\prime} m^{\prime}}=K_{l l^{\prime} m} \delta_{m, m^{\prime}}$. The quantities $K_{l l^{\prime} m}$ are independent matrix elements that are irreducible, i.e., they cannot be further reduced by symmetry. By convention the states are labeled with $l$ or $l^{\prime}$ denoted by $\mathrm{s}, \mathrm{p}, \mathrm{d}, \ldots$, and $m=0, \pm 1, \pm 2, \ldots$, denoted by $\sigma, \pi, \delta, \ldots$, leading to the notation $K_{\mathrm{ss} \sigma}, K_{\mathrm{sp} \sigma}, K_{\mathrm{pp} \pi}, \ldots$.

Figure 14.1 illustrates the orbitals for the nonzero $\sigma, \pi$, and $\delta$ matrix elements for s, p, and d orbitals. The orbitals shown are the real basis functions $S_{l m}^{ \pm}$defined in Eq. (K.11) as combinations of the $\pm m$ angular momentum eigenstates. These are oriented along the axes defined by the line between the neighbors and two perpendicular axes. All states except the s state have positive and negative lobes, denoted by solid and dashed lines, respectively. States with odd $l$ are odd under inversion, and their sign must be fixed by convention. Typically one chooses the positive lobe along the positive axis of the displacement vector from the site denoted by the first index to the site denoted by the second index. For example, in Fig. 14.1, the $K_{\mathrm{sp} \sigma}$ matrix element in the top center has the negative lobe of the p function oriented toward the s function. Interchange of the indices leads to $K_{\mathrm{ps} \sigma}=-K_{\mathrm{sp} \sigma}$ and, more generally, to $K_{l l^{\prime} m}=(-1)^{l+l^{\prime}} K_{l^{\prime} l m}$ (Exercise 14.5).

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-06_622_820_247_425.jpg)
Figure 14.2. Schematic figures for two-center matrix elements of s and $\mathrm{p}_{i}=\left\{\mathrm{p}_{x}, \mathrm{p}_{y}, \mathrm{p}_{z}\right\}$ orbitals for atoms separated by displacement vector $\mathbf{R}$. Matrix elements are related to $\sigma$ and $\pi$ integrals by the transformation to a combination of orbitals that are aligned along $\mathbf{R}$ and perpendicular to $\mathbf{R}$. The top figure illustrates the transformation to write a real matrix element $K_{\mathrm{s}, \mathrm{p}_{x}}$ in terms of $K_{\mathrm{sp} \sigma}$ : the s orbital is unchanged and the $\mathrm{p}_{x}$ orbital is written as a sum of the $\sigma$ orbital, which is shown, and the $\pi$ orbitals, which are not shown because there is no sp $\pi$ matrix element. The lower figure illustrates the transformation needed to write $K_{\mathrm{p}_{x}, \mathrm{p}_{z}}$ in terms of $K_{\mathrm{pp} \sigma}$ and $K_{\mathrm{pp} \pi}$. The coefficients of the transformation for all s and p matrix elements are given in Table 14.1. Matrix elements for arbitrary angular momenta can be found using the rotation matrix method described in Appendix N.

In general the displacement vector $\mathbf{R}$ is not oriented along the cartesian axes and the functions must be transformed to utilize the standard irreducible form of the matrix elements. Examples of two-center matrix elements of s and $\mathrm{p}_{i}=\left\{\mathrm{p}_{x}, \mathrm{p}_{y}, \mathrm{p}_{z}\right\}$ orbitals are shown in Fig. 14.2. Each of the orbitals on the left-hand side can be expressed as a linear combination of orbitals that have the standard form oriented along the rotated axes, as shown on the right. An s orbital is invariant and a p orbital is transformed to a linear combination of $p$ orbitals. The only nonzero matrix elements are the $\sigma$ and $\pi$ matrix elements, as shown. The top row of the figure illustrates the transformation of the $\mathrm{p}_{x}$ orbital needed to write the matrix element $K_{\mathrm{s}, \mathrm{p}_{x}}$ in terms of $K_{\mathrm{sp} \sigma}$ and the bottom row illustrates the relation of $K_{\mathrm{p}_{x}, \mathrm{p}_{z}}$ to $K_{\mathrm{pp} \sigma}$ and $K_{\mathrm{pp} \pi}$. The relations for s and p matrix elements are given in Table 14.1, and all other s and p matrix elements are related by symmetry. Expressions for d orbitals are given in many places including [354, 613], and [615]; arbitrary angular momenta can be treated using the procedures in Appendix N.

## Three-Center Matrix Elements

The hamiltonian matrix elements, in general, depend on the presence of other atoms, resulting in three-center or multicenter matrix elements. Such terms are discussed in Chapter 15 since they arise naturally in the integrals required in a local orbital basis. In this

Table 14.1. Two-center matrix elements for real orbitals s and $\mathrm{p}_{x}, \mathrm{p}_{y}, \mathrm{p}_{z}$, where the vector between sites is $\hat{\mathbf{R}} \equiv\{x, y, z\}$ (see Fig. 14.2)
| Element | Expression |
| :--- | :---: |
| $K_{\mathrm{s}, \mathrm{s}}$ | $K_{\mathrm{ss} \sigma}$ |
| $K_{\mathrm{s}, \mathrm{p}_{x}}$ | $x^{2} K_{\mathrm{sp} \sigma}$ |
| $K_{\mathrm{p}_{x}}, \mathrm{p}_{x}$ | $x^{2} K_{\mathrm{pp} \sigma}+\left(1-x^{2}\right) K_{\mathrm{pp} \pi}$ |
| $K_{\mathrm{p}_{x}, \mathrm{p}_{z}}$ | $x z\left(K_{\mathrm{pp} \sigma}-K_{\mathrm{pp} \pi}\right)$ |


chapter we consider only the "empirical tight-binding" or "semiempirical tight-binding" approaches that involve only the matrix elements $H_{m, m^{\prime}}(\mathbf{T})$ and $S_{m, m^{\prime}}(\mathbf{T})$ expressed in a parameterized form, without an explicit representation for the basis orbitals.

The only rigorous result that one can apply immediately to the nature of matrix elements Eqs. (14.1) and (14.2) is that they must obey crystal symmetry. This is often very helpful in reducing the number of parameters to a small number for a high-symmetry crystal as is done in the tables of Papaconstantopoulos [616] for many crystalline metals. In this form, the tight-binding method is very useful for interpolation of results of more expensive methods [616].

### 14.3 Spin-Orbit Interaction

The spin-orbit interaction is a relativistic effect derived in Appendix O, where it is shown that the effects can be described using the nonrelativistic Schrödinger equation with an added term

$$
\hat{H}_{\mathrm{SO}}=\frac{\hbar^{2}}{4 M^{2} c^{2}} \frac{1}{r} \frac{\mathrm{~d} V}{\mathrm{~d} r} \mathbf{L} \cdot \sigma .
$$

Because $\hat{H}_{\text {SO }}$ is a velocity-dependent operator, it has effects that cannot be reproduced by any potential. Since the effect is largest near the nucleus where the potential is spherically symmetric, it can be take into account by a term in the hamiltonian centered on each atom, which can be written as a matrix in the basis of ↑ and ↓ spin states,

$$
H_{S O}=\left[\begin{array}{lll}
H_{S O}(\uparrow, & \uparrow) & H_{S O}(\uparrow, \downarrow) \\
H_{S O}(\downarrow, \uparrow) & H_{S O}(\downarrow, \downarrow)
\end{array}\right],
$$

with $H_{S O}(\downarrow \downarrow)=-H_{S O}(\uparrow \uparrow)$ and $H_{S O}(\uparrow \downarrow)=H_{S O}^{\dagger}(\downarrow \uparrow)$. Thus the size of the hamiltonian is doubled, and in general the eigenstates are linear combinations of the ↑ and ↓ spin states.

In electronic structure methods that deal with wavefunctions in the continuum, such as plane waves and local orbitals, the problem is defined by taking matrix elements of Eq. (14.10). In methods with a basis of orbitals with definite angular momentum $L$ centered on the atoms, the spin-orbit interaction can be included as an on-site term for each atom that is determined by one parameter for each $L>0$. (Strictly, this is an approximation and there are other terms if the orbitals on an atom overlap the nuclei on neighboring atoms.)

This has the same symmetry as in an atom, i.e., each state with angular momentum L is split into states with $\mathrm{J}=\mathrm{L} \pm 1 / 2$, but the quantitative values may be different since the wavefunctions in the solid are not the same as in the atom. In calculations for a crystal it is often more convenient to work with a basis specified in cartesian coordinates, for example, $p$ states $p_{x}, p_{y}$ and $p_{z}$. In this basis the hamiltonian in Eq. (14.11) has the form

$$
H_{S O}(\uparrow \uparrow)=\left[\begin{array}{ccc}
0 & -i \zeta & 0 \\
i \zeta & 0 & 0 \\
0 & 0 & 0
\end{array}\right], \quad \text { and } \quad H_{S O}(\downarrow \uparrow)=\left[\begin{array}{ccc}
0 & 0 & \zeta \\
0 & 0 & -i \zeta \\
-\zeta & i \zeta & 0
\end{array}\right] \text {, }
$$

where $\zeta=\frac{\hbar e}{4 m^{2} c^{2}}\left\langle p_{x}\right|\left(V^{\prime}(r) / r\right)(i \mathbf{p} \times \mathbf{r})_{z}\left|p_{y}\right\rangle$, which is a real number. It is especially simple to include in an sp tight-binding model where $\zeta$ is a parameter fit to experiment or to a calculation for the solid. The only thing one needs to do is to double the matrix size, compared to a case without spin-orbit interaction, and add $H_{S O}$ in the p components of the hamiltonian at each site.

### 14.4 Slater-Koster Two-Center Approximation

Slater and Koster (SK) [613] developed the widely used [354, 615] approach that bears their name. They proposed that the hamiltonian matrix elements be approximated with the two-center form and fitted to theoretical calculations (or empirical data) as a simplified way of describing and extending calculations of electronic bands. Within this approach, all matrix elements have the same symmetry as for two atoms in free space given in Fig. 14.2 and Table 14.1. This is a great simplification that leads to an extremely useful approach to understanding electrons in materials. Of all the methods for treating electrons, the SK approach provides the simplest, most illuminating picture of electronic states. In addition, more accurate treatments involving localized orbitals (Chapter 15) are often best understood in terms of matrix elements having SK form plus additional terms that modify the conclusions in quantitative ways.

Slater and Koster gave extensive tables for matrix elements with the symmetry of atomcentered s, p, and d states, and analytic formulas for bands in several crystal structures. Explicit expressions for the s and p matrix elements are given in Table 14.1 and illustrated in Fig. 14.2. The power of using such models to capture qualitative effects such as topology of band structures are illustrated in Chapters 25-28. Examples of quantitative descriptions for band structures in Section 14.10 illustrate useful information that can be derived simple, pedagogical models that also can be used to description of large complicated systems, including the bands, total energies, and forces for relaxation of structures and molecular dynamics. These different applications have very different requirements that often lead to different choices of SK parameters.

For quantitative description of bands, the parameters are usually designed to fit selected eigenvalues for a particular crystal structure and lattice constant. For example, the extensive tables derived by Papaconstantopoulos [616] are very useful for interpolation of results of more expensive methods. It has been pointed out by Stiles [617] that for a fixed ionic
configuration, effects of multicenter integrals can be included in two-center terms that can be generated by an automatic procedure. This makes it possible to describe any band structure accurately with a sufficient number of matrix elements in SK form. However, the two-center matrix elements are not transferable to different structures.

On the other hand, any calculation of total energies, forces, etc. requires that the parameters be known as a function of the positions of the atoms. Thus the choices are usually compromises that attempt to fit a large range of data. Such models are fit to structural data and, in general, are only qualitatively correct for the bands. Since the total energy depends only on the occupied states, the conduction bands may be poorly described in these models. Of particular note, Harrison [354, 615] has introduced a table that provides parameters for any element or compound. The forms are chosen for simplicity, generality, and ability to describe many properties in a way that is instructive and useful, albeit approximate. The basis is assumed to be orthonormal, i.e., $S_{m m^{\prime}}=\delta_{m m^{\prime}}$. The diagonal hamiltonian matrix elements are given in a table for each atom. Any hamiltonian matrix element for orbitals on neighboring atoms separated by a distance $R$ is given by a factor times $1 / R^{2}$ for s and p orbitals and $1 / R^{l+l^{\prime}}$ for $l>1$. The form for s and p orbitals comes from scaling arguments on the homogeneous gas [615] and the form for higher angular momenta is taken from muffin-tin orbital theory (Section 16.7).

Many other SK parameterizations have been proposed, each tailored to particular elements and compounds. Examples are given in Sections 14.5-14.11, chosen to illustrate various aspects of electronic structure calculations in the present and other chapters. Care must be used in applying the different parameterizations to the appropriate problems.

### 14.5 Tight-Binding Bands: Example of a Single s Band

This section and following ones are concerned with electronic bands calculated using tightbinding with the SK two-center form for the hamiltonian that can be worked out analytically, with further examples in exercises. The later sections of this chapter give examples of applications to bands in materials and more complex problems, such as the electronic structure of nanotubes.

## s-Bands in Line, Square, and Cubic Bravais Lattices

The simplest possible example of bands is for s-symmetry states on each site $I$ in a Bravais lattice so that there is only one band. As a further simplification, we consider the case of orthogonal basis states and nonzero hamiltonian matrix elements $\langle I| \hat{H}\left|I^{\prime}\right\rangle \equiv t$ only if $I$ and $I^{\prime}$ are nearest neighbors. The on-site term can be chosen to be zero, $\langle 0| \hat{H}|0\rangle=0$. There are three cases (line, square, and cubic lattices) that can be treated together. For the cubic lattice with spacing $a$ the general expressions (14.4) and (14.7) reduce to

$$
\varepsilon(\mathbf{k})=H(\mathbf{k})=2 t\left[\cos \left(k_{x} a\right)+\cos \left(k_{y} a\right)+\cos \left(k_{z} a\right)\right] .
$$

The bands for the square lattice in the $x, y$-plane are given by this expression, omitting the $k_{z}$ term; for a line in the $x$-direction, only the $k_{x}$ term applies.

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-10_534_1218_245_227.jpg)
Figure 14.3. Tight-binding bands in the square lattice with only an s state on each site and nearest neighbor interactions. The left figure shows the BZ and the dashed line shows the Fermi surface in the case of a half-filled band. The right figure shows the bands with $\mathbf{k}$ along the lines between the high-symmetry points.

This simple example leads to useful insights. In particular, the bands are symmetric about $\varepsilon(\mathbf{k})=0$ in the sense that every state at $+\varepsilon$ has a corresponding state at $-\varepsilon$. This can be seen by plotting the bands in two ways: first in the usual Brillouin zone centered on $\mathbf{k}=0$, and second in a cell of the reciprocal lattice centered on $\mathbf{k}=(\pi / a, \pi / a, \pi / a)$. Since $\cos \left(k_{x} a-\pi\right)=-\cos \left(k_{x} a\right)$, etc., it follows that the bands have exactly the same shape except that the sign of the energy is changed,

$$
\varepsilon(\mathbf{k})=-\varepsilon(\mathbf{k}-(\pi / a, \pi / a, \pi / a)) .
$$

The same arguments apply to the line and square: the line has a simple cosine band and the bands for a square lattice are illustrated in Fig. 14.3. The densities of states (DOS) for one, two, and three dimensions are shown in Fig. 14.4. The shapes can be found analytically in this case, which is the subject of Exercise 14.6.

There are several remarkable consequences in the case of the square. The energy $\varepsilon(\mathbf{k})=0$ at a zone face $\mathbf{k}=(\pi / a, 0)$, which is easily verified using Eq. (14.13) and omitting the $k_{z}$ term. This is a saddle point since the slope vanishes and the bands curve upward and downward in different directions as shown in Fig. 14.3. This leads to a density of states with a logarithmic divergence at $\varepsilon=0$ (Exercise 14.7). Furthermore, for a half-filled band (one electron per cell), the Fermi surface is at energy $\varepsilon(\mathbf{k})=0$. This leads to the result shown in Fig. 14.4 that the Fermi surface is a square (Exercise 14.7) rotated by $\pi / 4$ with half the volume of the Brillouin zone, and the density of states diverges at $\varepsilon=E_{F}$ as shown in Fig. 14.3. If there are second-neighbor interactions, the symmetry of the bands in $\pm \varepsilon$ is broken and the Fermi surface is no longer square.

## Nonorthogonal Orbitals

The solution of the tight-binding equations in terms of non-orthogonal orbitals can be found simply in terms of the overlap matrix $S$ using Eq. (14.7). The matrix elements of $S$ can be

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-11_349_1188_243_242.jpg)
Figure 14.4. Schematic densities of states (DOS) for an s band in a one-dimensional (1D) line, a two-dimensional (2D) square, and a three-dimensional (3-D) simple cubic lattice with nearest neighbor interactions $t$. The bands are symmetric about the center and the width of each segment is $4 t$, i.e., the width of the 1-D DOS is $4 t$, that of the 2-D DOS is $8 t$ divided into two parts, and the 3D band has width $12 t$ divided into three parts of equal width. The special property of the square lattice in this leads to a logarithmic singularity at the band center. See also Exercise 14.6 for further information.

parameterized in the same way as the hamiltonian, with the added benefit that the twocenter form is rigorous and each orbital is normalized so that $S_{m m}=1$. The effect can be illustrated by line, square, or simple cubic lattices, with nearest neighbor overlap defined to be $s$. Then the solution for the bands, Eq. (14.13), is generalized to

$$
\varepsilon(\mathbf{k})=\frac{H(\mathbf{k})}{S(\mathbf{k})}=\frac{2 t\left[\cos \left(k_{x}\right)+\cos \left(k_{y} a\right)+\cos \left(k_{z} a\right)\right]}{1+2 s\left[\cos \left(k_{x} a\right)+\cos \left(k_{y} a\right)+\cos \left(k_{z} a\right)\right]} .
$$

The effect of nonzero $s$ is discussed in Exercises 14.16 and 14.17. In this case, the symmetry about $\varepsilon=0$ is broken, so that the conclusions on bands and the Fermi surface no longer apply. In fact $s$ has an effect like longer-range hamiltonian matrix elements, indeed showing strictly infinite range but rapid exponential decay.

Nonorthogonal orbitals play an essential role in realistic tight-binding models. As discussed more completely in Section 14.12, it is never rigourously consistent to cut off the hamiltonian matrix elements while assuming orthogonal orbitals. This is a manifestation of the well-known properties of Wannier functions (Chapter 23) and the fact that Wannier functions are very environment dependent. On the other hand, nonorthogonal functions can be much more useful because they are more transferable between different environments. This is illustrated by examples in Sections 14.12 and 23.4.

### 14.6 Two-Band Models

Two-band models play a special role in electronic structure of crystals. The hamiltonian can be expressed in the form

$$
H(k)=\left[\begin{array}{cc}
E_{1}(\mathbf{k}) & t(\mathbf{k}) \\
t^{*}(\mathbf{k}) & E_{2}(\mathbf{k})
\end{array}\right],
$$

where the diagonal and off-diagonal terms have different interpretation in different models. In one dimension the lowest two bands can always be represented by Bloch states that are
linear combinations of an even and an odd state per cell. This was used by by Shockley to draw very general conclusions about the bands including a transition in the bulk band structure and emergence of a surface state. This is described in Chapter 22, where it is the origin of a class of surface states often observed on metals, and in Chapter 26, where it is a forerunner of topological insulators.

Because the models are so useful in the chapters on topology, description of the models is deferred to Chapter 26. However, it is appropriate to emphasize here that the models are not only for surfaces and topological insulators! They are instructive models for physical problems. Two characteristic models are shown in Figs. 26.2 and Fig. 26.3. The first case has two sites, each with one state, which can represent an ionic crystal with different energies on the two sites, or a molecular crystal with strong and weak hopping. The second has one site with even and odd states, which is the natural model to describe covalent bonding. See Exercise 26.2 for examples. These and other models all share the same mathematical structure and can be mapped into one another as brought out in Chapter 26. In this chapter, the two-band model is illustrated by graphene in two dimensions.

### 14.7 Graphene

Graphene is one the most fascinating materials in nature and in theoretical models. It can be made easily by the "Scotch tape method" to peel off one layer from graphite; it is the thinnest stable material known (one atomic layer) and the strongest material known (in the twodimensional layer); it has exceptionally large thermal conductivity and ballistic electron transport; and it is the basis for a plethora of structures like nanotubes and ribbons with a fabulous array of properties. It is also one of the best examples where a very simple model provides quantitative results, as well as qualitative new effects including nontrivial topology!

Graphene has the planar honeycomb structure shown in Fig. 4.5. The Brillouin zone is a hexagon that is the same as for the three-dimensional hexagonal zone in Fig. 4.10 with $k_{z}=0$; it is also shown in Fig. 27.12, where the corners of the zone are labeled $K$ and $K^{\prime}$, which are related by inversion. For a single, flat graphene sheet, the $\pi$ states are odd in reflection in the plane and symmetry forbids coupling to the $\sigma$ bands that are well below and well above the Fermi energy (in the absence of spin-orbit interaction). Since graphene has two atoms per cell, the $\pi$ states are an example of the two-site model with the same energy of each site that can be set to zero for convenience, and hopping matrix element $t_{p p \pi} \equiv t$ between nearest neighbors. The bands $\varepsilon(\mathbf{k})$ are given by the determinant equation (see Exercise 14.20 and [233])

$$
|\hat{H}(\mathbf{k})-\varepsilon(\mathbf{k})|=\left|\begin{array}{cc}
-\varepsilon(\mathbf{k}) & t(\mathbf{k}) \\
t^{*}(\mathbf{k}) & -\varepsilon(\mathbf{k})
\end{array}\right|=0 \text {, }
$$

with

$$
t(\mathbf{k})=t\left[\mathrm{e}^{\mathrm{i} k_{y} a / \sqrt{3}}+2 \mathrm{e}^{-\mathrm{i} k_{y} a / 2 \sqrt{3}} \cos \left(k_{x} \frac{a}{2}\right)\right]
$$

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-13_459_1266_243_202.jpg)
Figure 14.5. The $\pi$ bands for graphene without and with spin-orbit interaction. At the left is shown only the $\pi$ bands without spin-orbit interaction showing the Dirac linear dispersion with no gap at the K points. At the right is shown the bands that are modified by adding the s and other p states with spin-orbit interaction, which shifts the bands and opens the gap. (The magnitude of the spin-orbit interaction is chosen to be much larger than the actual value for graphene in order to make the effect visible.)

where $a$ is the lattice constant, $t$ is the nearest neighbor hopping matrix element, and $x$ and $y$ are the horizontal and vertical directions in Fig. 4.5. This is readily solved to yield the band energies

$$
\varepsilon(\mathbf{k})= \pm|t(\mathbf{k})|= \pm t\left[1+4 \cos \left(k_{y} \frac{\sqrt{3} a}{2}\right) \cos \left(k_{x} \frac{a}{2}\right)+4 \cos ^{2}\left(k_{x} \frac{a}{2}\right)\right]^{1 / 2} .
$$

The resulting bands are shown in the left side of Fig. 14.5 in units where the hopping matrix element is set to $t=1$. This shows the remarkable feature that the bands touch with zero gap at the $K$ and $K^{\prime}$ points. These are called Dirac points, since the dispersion is linear like a relativistic particle with no mass. But it should be kept in mind that this is only a useful analogy: it is not a relativistic effect, the velocities are much less than the speed of light and the dispersion is not strictly linear for momenta a finite distance from the $K$ and $K^{\prime}$ points.

## Spin-Orbit Interactions

It might seem surprising that there is an effect of spin-orbit interaction on the $\pi$ bands. If there were only a single $\pi$ state on each atom, like in the model described by Eq. (14.19), there would be no angular momentum and no effect. However, in actual graphene the other p states are present and are part of the bonding and antibonding states that are well below and above the $\pi$ bands, outside the energy range shown in the figure. There is an effect because the spin-orbit interaction mixes the three p states, but it is extremely small for two reasons: carbon is a light atom with small spin-orbit interaction and it is a second-order effect due to mixing with the other p states. The right side of Fig. 14.5 shows the bands including a spin-orbit interaction that is chosen to be much larger than the actual value to make the effect more visible. Note that a point $K^{\prime}$ is related to $K$ by time-reversal symmetry
such that it has opposite momentum and opposite spin state. The eigenvalues are the same as at $K$ but since the spins are opposite this is referred to as a negative gap in the sense that at $K$ the valence band is for one spin (say $\uparrow$ ) and the bottom of the conduction band is ↓ , whereas at $K^{\prime}$ the spins are reversed. This is an essential aspect of graphene as a topological insulator in Section 27.8.

### 14.8 Nanotubes

Nanotubes are ideal for illustrating the use of tight-binding to reveal the most vital information about the electronic structure in a simple, illuminating way. Carbon nanotubes were discovered in 1991 by Iijima [228] and recognized to be nanoscale versions of "microtubes," long tubular graphitic structures that had been grown using iron particles for catalysis [234]. In a perfect single-wall tube, each carbon atom is equivalent and is at a junction of three hexagons. The various ways a sheet of graphene (i.e., a single honeycomb-structure plane of carbon) can be rolled into a tube leads to an enormous variety of semiconductors and metals [232-234] that originate in the way the Dirac points in graphene are modified by the structure of the nanotube.

The structures of nanotubes are defined in terms of a graphene layer as shown in Fig. 14.6. The vector indicated connects atoms in the layer that are equivalent in the tube, i.e., the tube is defined by rolling the plane of graphene to bring those points together. The tube axis is perpendicular to the vector. The convention is to label the vector with multiples of graphene translation vectors, $\mathbf{a}_{1}$ and $\mathbf{a}_{2}$, defined as in Fig. 4.5. The example shown is for a (6,1) tube, which denotes ( $6 \times \mathbf{a}_{1}, 1 \times \mathbf{a}_{2}$ ) and which defines the chiral tube shown on the right. Special examples of "zigzag" ( $n, 0$ ) and "armchair" ( $n, n$ ) tubes are shown in Fig. 14.7. These are not chiral but have very different properties due to the underlying atomic structure. See Exercise 14.21.

The first approximation is to assume that the bands are unchanged from graphene and the only effect is that certain states are allowed by the boundary condition. The condition

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-14_403_1174_1568_247.jpg)
Figure 14.6. Rolling of a graphene sheet to form a nanotube. On the left is shown a tube with circumference indicated by the circle $\mathbf{c}$. The middle and right figures show a graphene translation vector $\mathbf{c}=n \mathbf{a}_{1}+m \mathbf{a}_{2}$ with $n=6$ and $m=1$ and the chiral $(6,1)$ tube formed by rolling to join the site related by $\mathbf{c}$. The basis vectors $\mathbf{a}_{1}$ and $\mathbf{a}_{2}$ shown are the same as in Fig. 4.5 and in [233,618]; in this notation the example shown is a $(6,1)$ nanotube. Provided by J. Kim

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-15_511_1266_239_203.jpg)
Figure 14.7. Structures, Brillouin zones, and bands of the "zigzag" ( $a$ ) and "armchair" ( $b$ ) nanotubes. The bands are calculated using the orthogonal tight-binding model of Xu et al. [619]. The zigzag tubes shown are denoted $(13,0)$ and $(12,0)$; the latter is insulating and the former has a small gap that is due to curvature. However, for smaller tubes, the curvature can induce large effects, including band overlap leading to metallic tubes as shown in Fig. 22.9 and discussed in the text. The armchair $(n, n)$ tubes are always metallic since the lines of allowed states with $k$ along the tube always include $\Gamma$ and one of the K points. (b) illustrates the bands for a $(3,3)$ tube. In each case the bands of the tube are plotted in the one-dimensional BZ denoted $\Gamma \rightarrow$ X. Provided by J. Kim

on allowed functions is that they must be single valued in the circumferential direction but have Bloch boundary conditions along the tube axis. This leads to allowed $\mathbf{k}$ vectors, which are shown as lines in Fig. 14.7. The resulting bands have been analyzed in general [232234] with the simple conclusion that there is a gap between filled and empty states unless the allowed $k$ lines pass through the point K . If they do include K , e.g., the armchair tube, then the interesting situation of one-dimensional metallic bands arises.

The next approximation is to include expected effects due to curvature [232,233]. The simplest depends only on symmetry: curvature makes bonds along the axis inequivalent to those at an angle to the axis. Therefore, the $k$ point where the bands touch moves away from the point K opening a small gap, as shown in Fig. 14.7 for the $(13,0)$ zigzag tube. The gap is expected to increase for small tubes with larger curvature. On the other hand, there is no effect upon the band crossing at point K , which is along the tube axis for the armchair tube, so that it remains metallic in all cases.

However, small changes from graphene are not the whole story. As shown in Fig. 22.9, calculations [620] on small tubes have shown that the bands can be qualitatively changed from the graphene-like states considered thus far. The reason is that in small tubes there is large mixing of $\pi$ states with a $\sigma$ antibonding state that pushes a band below the Fermi level. This leads to the prediction [620] that small-diameter nanotubes can be metallic due to band overlap, even in cases where analogy to graphene would expect an insulator. This effect is also found in local orbital calculations [621] and in the improved tight-binding model of [622], which has been fitted to LDA calculations of many properties (eigenvalues, total energies, phonons, etc.) of carbon in various coordinations and geometries. This is an
example of a tight-binding method that allows fast calculations that span the range from small to large tubes, as well as other carbon structures.

There is an interesting relation to graphene topological insulators. As the circumference of a tube is increased to be much larger than the length it becomes a ribbon: the zigzag and armchair tubes map directly onto the zigzag and armchair ribbons in Section 27.8. For example, the zero-gap tubes in Fig. 14.7 are the equivalent of the points where the bulk spectrum has zero gaps in Fig. 27.14, and as the tube circumference increases the other low-energy states in Fig. 14.7 approach zero and become the edge state in Fig. 27.14. The spin-orbit interaction would lead to a gap and circulating end states!

## Boron Nitride Nanotubes

Nanotubes of boron nitride have been proposed theoretically [623] and later made experimentally [624]. Structures for the tubes are allowed if they maintain the B-N equal stoichiometry, and the tubes always have a large gap due to the difference between the B and N atoms. Thus the electronic properties are very different from carbon nanotubes and BN tubes hold the potential to act like one-dimensional semiconductors in the III-V family. Like other III-V materials they exhibit piezoelectric and pyroelectric effects, but in this case the one dimensionality leads to extreme anisotropy and novel electric polarization and piezoelectric effects [612, 625].

### 14.9 Square Lattice and $\mathbf{C u O}_{\mathbf{2}}$ Planes

The problem of an s band in a square lattice has a particularly noteworthy application in the case of the cuprate high-temperature superconductors. ${ }^{4}$ Figure 4.5 shows the square lattice structure of $\mathrm{CuO}_{2}$ planes that is the common feature of these materials, e.g., each of the planes in the bilayer in $\mathrm{YBa}_{2} \mathrm{Cu}_{3} \mathrm{O}_{7}$ shown in Fig. 17.3. Extensive calculations, exemplified by the bands presented in Fig. 17.4, have shown that the primary electronic states at the Fermi energy are a single band formed from Cu d and O p states. The band has the same symmetry as $\mathrm{d}_{x^{2}-y^{2}}$ states centered on each Cu (where $x$ and $y$ are in directions toward the neighboring Cu atoms). This can be understood in terms of the Cu and O states shown in Fig. 14.8. The three states per cell form a bonding, a nonbonding, and an antibonding combination, with the antibonding band crossing the Fermi level. In fact, the single antibonding band has the same symmetry as a $\mathrm{Cu} \mathrm{d}_{x^{2}-y^{2}}$ band with an effective hamiltonian matrix element (Exercise 14.15) so that the problem is equivalent to a model with one $\mathrm{d}_{x^{2}-y^{2}}$ state per Cu , as shown on the right-hand side of Fig. 14.8. This highly schematic figure is supported by detailed calculations of the oneband orbital shown in Fig. 17.8. The orbital has $\mathrm{d}_{x^{2}-y^{2}}$ symmetry about the Cu site and it

[^3]![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-17_495_978_243_347.jpg)
Figure 14.8. Tight-binding models representing electronic states in the square lattice structure of a CuO plane. On the left is shown the three-band model representing one $\mathrm{Cud}_{x^{2}-y^{2}}$ and two Op states per cell. As discussed in the text, the most relevant states are the antibonding combination of Cu and O states that are equivalent to the model shown on the right with modified orbitals that have $\mathrm{d}_{x^{2}-y^{2}}$ symmetry around each Cu site. The effective orbitals are more extended, as shown on the right; actual calculated orbitals shown in Fig. 17.8 are more realistic and show extended shape with $\mathrm{d}_{x^{2}-y^{2}}$ symmetry. Finally, the band is isomorphic to a single s band because, by symmetry, all hamiltonian matrix elements have the same symmetry; e.g., the nearest neighbor elements all have the same sign, as is evident from the right-hand figure.

is extended in the directions along the $\mathrm{Cu}-\mathrm{O}$ bonds, with large amplitude on the O sites. If the orbitals are required to be orthonormal, like Wannier functions, then each orbital must also extend to the neighboring Cu sites.

Finally, the problem is isomorphic to a single s band; this occurs because nearest neighbor $\mathrm{d}_{x^{2}-y^{2}}$ states always have lobes of the same sign ( ++ or -- ) so that the matrix elements are equal for all four neighbors, exactly as for s symmetry states. Thus the simplest model for the bands is a single s band, with dispersion shown in Fig. 14.4, and a square Fermi surface at half-filling. In fact, there are second-neighbor interactions that modify the bands and the calculated Fermi surface [490, 626]. The single band resulting from the orbital in Fig. 17.8 is shown in Fig. 17.9. It accurately describes the actual band, and its dispersion is significantly different from the nearest neighbor model due to longer-range matrix elements in a realistic model.

### 14.10 Semiconductors and Transition Metals

In this section two examples illustrate different applications of the tight-binding approach. The left side of Fig. 14.9 shows the bands of GaAs calculated using nanoHUB (nanohub.org), which provides databases and codes that can be run online to simulate the electronic structure of semiconductor nanostructure devices. This example is for bulk GaAs using a large $\mathrm{s}, \mathrm{p}, \mathrm{d}, \mathrm{s} *$ basis with parameters carefully fit to experiment. The calculations show the direct gap at $\Gamma$ and the effect of spin-orbit interaction that splits the valence band at $\Gamma$ into $\Gamma_{7}$ and $\Gamma_{8}$ components, the same as for CdTe and HgTe in Chapter 27 on topological insulators.

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-18_517_1080_242_296.jpg)
Figure 14.9. Left: band structure of GaAs calculated using the online tools at nanoHUB (nanohub.org) and a s, p, d, s* basis with parameters fit to experiment and results good enough for device simulations. Compare with the LDA bands in Fig. 17.7, where the gap is too small. Right: bands for the transition metal Ni calculated with Harrison's universal parameters [354, 615]. This is an example of tight-binding used to find approximate results that reveal characteristic features of the narrow d bands and wide s bands, as shown by comparing with LDA calculations in Figs. 16.4 and 16.5.

Simpler models with minimal $\mathrm{s}, \mathrm{p}$ basis are not nearly so accurate. For example, calculations using the parameters in Harrison's "universal" table [354, 615] yield valence bands in reasonable agreement with experiment but the conduction bands may be qualitatively incorrect. The conduction bands can be greatly improved, e.g., for Si the correct indirect gap can be fit by including a second s symmetry state (called s*) at high energy [627]. This is a way to mimic the effect found in full calculations that it is the admixture of Si 3d states that affects the shape of the conduction bands. The detailed fitting illustrated for GaAs in Fig. 14.9 uses both d and s* states. Description of bands using extended tight-binding models for many elements is given in the book [628].

The bands of transition metals have features that are dominated by localized d states. Tight-binding is a very natural approach for these states, as is also emphasized in the tightbinding LMTO method (Sections 16.7 and 17.6). The right side of Fig. 14.9 shows the bands of Ni calculated using Harrison's parameters [354, 615]. The bands have the right features, compared to full calculations (see Figs. 16.4 and 16.5) with narrow d bands and a wide s band, but the bands are somewhat too narrow and the model is inadequate to describe the other bands at higher energy. Nevertheless, such an approach is very valuable because it can describe the main features of entire classes on materials. Improved tightbinding descriptions of transition metal systems can be found in [629] and in the extensive handbook of band structures [628].

### 14.11 Total Energy, Force, and Stress in Tight-Binding

The total energy in any self-consistent method, such as the Kohn-Sham approach, can be written as in Eqs. (7.20) and (7.22) expressed as a sum of eigenvalues (Eq. (7.19))
plus the interaction of the nuclei and a correction needed to avoid double counting the interactions

$$
E_{\text {total }}=\sum_{i} \varepsilon_{i} f\left(\varepsilon_{i}\right)+F[n]
$$

Here $f\left(\varepsilon_{i}\right)$ is the Fermi function and $i$ labels eigenstates including the spin index; in a crystal, the sum is over all bands and $\mathbf{k}$ in the BZ. In terms of $E_{\text {pot }}$ in Eq. (7.16), $F[n]$ is given by

$$
\begin{aligned}
F[n] & \equiv E_{\mathrm{pot}}[n]-\int \mathrm{d} \mathbf{r} V_{\mathrm{KS}}(\mathbf{r}) n(\mathbf{r}) \\
& =E_{I I}-E_{\mathrm{Hartree}}[n]+\int \mathrm{d} \mathbf{r}\left[\epsilon_{\mathrm{xc}}(\mathbf{r})-V_{\mathrm{xc}}(\mathbf{r})\right] n(\mathbf{r})
\end{aligned}
$$

where $V_{\mathrm{KS}}$ is the Kohn-Sham potential taken to be spin independent for simplicity.
In the tight-binding method, the parameterized hamiltonian matrix elements lead to the eigenvalues $\varepsilon_{i}$. How can the second term be included in such an approach? How can it be approximated as a function of the positions of the nuclei, even though the full theory defines $F[n]$ as a complicated functional of the density? An elegant analysis of the problem has been given by Foulkes and Haydock [361] based on the expression for the energy, Eq. (7.22). They used the variational properties of that functional and the choice of the density as a sum of neutral spherical atom densities, which is a good approximation [359, 360, 630]. It immediately follows that the difference of the Hartree and ion-ion terms in Eq. (14.21) is a sum of short-range, pair-wise interactions between atoms. The exchange-correlation term in Eq. (14.21) is also short range and it can be approximated as a pair potential. Thus we are led to the approximation that $F$ can be expressed as a sum of terms $f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)$ that depend only on distances to near neighbors, so that the total energy in the tight-binding approach can be expressed as

$$
E_{\mathrm{total}}=\sum_{i=1}^{N} \sum_{m, m^{\prime}} c_{i, m}^{*} H_{m, m^{\prime}} c_{i, m^{\prime}}+\sum_{I<J} f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)
$$

where the eigenvectors are given by

$$
\psi_{i}=\sum_{m} c_{i, m} \chi_{m}
$$

Finally, defining the density matrix,

$$
\rho_{m, m^{\prime}}=\sum_{i=1}^{N} c_{i, m}^{*} c_{i, m^{\prime}}
$$

the energy can be written

$$
E_{\text {total }}=\sum_{m, m^{\prime}} \rho_{m, m^{\prime}} H_{m, m^{\prime}}+\sum_{I<J} f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)=\operatorname{Tr}\{\hat{\rho} \hat{H}\}+\sum_{I<J} f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right) .
$$

The added functions $F$ or $f$ can be found by fitting to additional information related to the total energy, e.g., the elastic constants or phonon frequencies. There can be no unique
form of $F$, however, because of the fundamental ambiguity in separating the two terms in Eq. (14.20). An arbitrary function of the nuclear positions can be added to the hamiltonian matrix elements, shifting all eigenvalues rigidly with no change in the physics. The function $F$ must be chosen consistent with the choice in the matrix elements. One choice of $F$ is a sum of pair potentials, as is done in many models such as that of Harrison [354, 615] and models mentioned below. A different approach to is define eigenvalues that include a shift due to repulsive affects [631],

$$
\varepsilon_{i}^{\prime} \equiv \varepsilon_{i}+F / N_{e}
$$

Then the total energy is simply

$$
E_{\text {total }}=\sum_{i=1}^{N} \varepsilon_{i}^{\prime}=\operatorname{Tr}\left\{\hat{\rho} \hat{H}^{\prime}\right\}
$$

and the challenge is to parameterize the tight-binding matrix elements to describe both the eigenvalues and the total energy. Considerable success has been demonstrated with this form (see Section 14.12). In any case, the results depend on the availability of calculated and/or experimental energies and the adequacy of the forms chosen to represent different structures.

Forces can be found by taking derivatives of the energy using the force theorem just as in other methods. In tight-binding, the matrix elements are considered as functions of the positions of the nuclei and the expression follows from the condition that the energy is variational w.r.t. the density matrix $\hat{\rho}$ (Exercise 14.22). Taking the derivative of Eq. (14.25) with respect to the position of atom $I$ leads to

$$
\mathbf{F}_{I}=-\operatorname{Tr}\left\{\hat{\rho} \frac{\partial \hat{H}}{\partial \mathbf{R}_{I}}\right\}-\sum_{J \neq I} \frac{\partial f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)}{\partial \mathbf{R}_{I}}
$$

where the last term is absent if equation (14.27) is used. Pressure and stress are also straightforward since the stress tensor, Eq. (G.4), can be written as the sum of terms with the form

$$
\sigma_{\alpha \beta}=-\frac{1}{\Omega} \frac{\partial E_{\text {total }}}{\partial u_{\alpha \beta}}=-\operatorname{Tr}\left\{\hat{\rho} \frac{\partial \hat{H}}{u_{\alpha \beta}}\right\}-\sum_{J \neq I} \frac{\partial f\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)}{\partial u_{\alpha \beta}} .
$$

The first term involves the derivative of the matrix elements with distance, and the final term is a sum of two-body contributions, as treated in Section G.2.

## Examples of Tight-Binding Models for Total Energies

Perhaps the most useful and widely used tight-binding formulations are for carbon and silicon, for which there are several very successful parameterizations. For carbon, these are extremely useful for the amazing variety of structures found, including graphite, diamond, buckyballs, nanotubes, and amorphous and liquid carbon. For example, the form of Xu et al. [619] was constructed to fit the total energies of C in low-coordination structures, the chain,
graphitic, and diamond. The potential has been used for many simulations and agrees well with other calculations, e.g., the bands of nanotubes shown in Fig. 14.7 and simulations of liquid carbon [619]. Other potentials are also successful and widely used, such as [632] and forms given in Section 14.12.

A number of parameterizations, e.g., those in [633-636], have been developed for Si and applied to problems involving defects, diffusion, and many other interesting properties. For example, Fig. 18.7 shows the results of an $\mathrm{O}(N)$ molecular dynamics calculation [637, 638] of the structure of complex $\{311\}$ defects done using the model of Kwon et al. [634], with checks on smaller cells with plane wave density functional theory calculations.

### 14.12 Transferability: Nonorthogonality and Environment Dependence

There is a basic difficulty in generating tight-binding models that can describe very different structures, in particular, those with different numbers of near neighbors such as open- and close-packed structures [615]. In models that have only two-center matrix elements, the values of the matrix elements must take into account effects of three-center terms. These effects change drastically between structures such as diamond (4 nearest neighbors that lead to $4 \times 3=12$ three-center terms) and a close-packed structure ( 12 nearest-neighbors that lead to $12 \times 11=132$ three-center terms). There are two primary approaches toward making tight-binding models that are transferable between such different structures. One is to define environment-dependent tight-binding matrix elements, the values of which depend on the presence of other neighbors. The other approach involves nonorthogonal tight-binding, which is more transferable than orthogonal forms. The reasons are brought out in Section 23.4, where it is clear that a small basis of orthogonal functions must extend to long range and be environment dependent in order to be accurate; on the other hand, nonorthogonal functions can accurately describe bands even if they are short-range atomiclike functions that are almost environment independent. Indeed, such functions are also the bread and butter of the local orbital methods of Chapter 15.

The different models can be exemplified by the extensive body of work of Cohen, Mehl, and Papaconstantopoulos [631], developed in many subsequent papers, which utilizes nonorthogonal tight-binding with environment-dependent matrix elements. This approach employs shifted eigenvalues $\varepsilon_{i}^{\prime}$, defined in Eq. (14.26), with the diagonal on-site matrix elements dependent on a sum of densities representing the neighboring atoms. The explicit form suggested [631] for the state at atom $I$ with angular momentum $l$ and $\operatorname{spin} \sigma$ is

$$
H_{I l \sigma}=\sum_{n=0}^{3} b_{I l \sigma}^{(n)} \rho_{I \sigma}^{2 n / 3},
$$

where the $b_{I l \sigma}^{(n)}$ are parameters and $\rho_{I \sigma}$ depends on the surrounding atoms

$$
\rho_{I \sigma}=\sum_{J \neq I} \exp \left(-\lambda_{I J \sigma}^{2} R_{I J}\right) f\left(\frac{R_{I J}-R_{0}}{R_{c}}\right) .
$$

![](./images/2b1b0404-43ef-4abd-b9b0-d1fe2640a89c-22_437_1202_247_234.jpg)
Figure 14.10. Left: density of states of ferromagnetic Fe in the bcc structure with $a=5.40 a_{0}$, comparing LAPW (solid) and fitted tight-binding (dashed curves). Right: total energy versus volume for Fe in various structures, comparing points from LAPW calculations (+, ferromagnetic bcc; square, ferromagnetic fcc; $\times$, paramagnetic bcc) and lines from the tight-binding calculations. The left figure and most of the total energies illustrate the quality of the fit. The total energy of the ferromagnetic fcc state was not fitted and the results are a test of transferability. For example, the tight-binding calculations reproduce the delicate collapse of the moment at $\approx 70 a_{0}^{3}$ where the paramagnetic and ferromagnetic energies cross. From [640].

Here the exponential factor represents a density assigned to a neighboring atom, with the scales set by the parameters $\lambda_{I J \sigma}$, and $f$ is a cutoff factor taken to be the Fermi function. The spin dependence is needed for magnetic systems. The intersite matrix elements of the hamiltonian and overlap are each parameterized and have the same functional form that can be written

$$
K_{\gamma}(R)=\left(\sum_{n=0}^{3} c_{\gamma}^{(n)} R^{n}\right) \exp \left(-g_{\gamma}^{2} R\right) f\left(\frac{R-R_{0}}{R_{c}}\right),
$$

where $K_{\gamma}(R)$ denotes either hamiltonian and overlap matrix elements, and the subscript $\gamma$ denotes $\mathrm{ss} \sigma, \mathrm{sp} \sigma, \mathrm{sp} \pi$, etc.

This form has been applied to a large number of systems, including carbon [622], silicon [622, 639], and many transition metals. As an example, Fig. 14.10 shows the results for the density of states of ferromagnetic Fe in the bcc structure and the total energies in fcc and bcc structures, both paramagnetic and ferromagnetic. The tight-binding parameters are the same for all structures and are fitted with a total of 106 parameters ${ }^{5}$ to the LAPW results at several volumes for paramagnetic and ferromagnetic bcc and paramagnetic fcc Fe. The total energies and moments for ferromagnetic fcc Fe were not fitted but reproduce correctly the energies, including collapse of the moment to form a paramagnetic state at $\approx 70 a_{0}^{3}$. It is evident that the fits are extremely good and useful for analysis, given that the tight-binding calculations are orders of magnitude faster than the LAPW ones.

[^4]
## SELECT FURTHER READING

Classic paper and books with emphasis on tight-binding theory and methods:
Harrison, W. A., Electronic Structure and the Properties of Solids (Dover, New York, 1989).
Harrison, W. A., Elementary Electronic Structure (World Publishing, Singapore, 1999).
Slater, J. C. and Koster, G. F., "Simplified LCAO method for the periodic potential problem," Phys. Rev. 94:1498-1524, 1954.

Turchi, P. E. A., Gonis, A., and Columbo, L., eds., Tight-Binding Approach to Computational Materials Science (Materials Research Society, Warrendale, PA, 1998).
Papaconstantopoulos, D. A., Handbook of the Band Structure of Elemental Solids: From $Z=1$ to $Z=112$, 2nd ed. (Springer, New York, 2015).

Online resources:
Extensive tutorials, databases, and simnulation tools can be found at nanohub.org, and other sources are listed in Appendix R.

## Exercises

14.1 See Appendix R for examples of codes that are available (or can be run online) for tightbinding calculations that are both pedagogical and able to treat problems such as semiconductor devices.
14.2 See many excellent problems (and solutions) on tight-binding bands, densities of states, and the meaning of the bands in the book by Mihaly and Martin [598].
14.3 Using translation invariance of the matrix elements, show that matrix elements of the hamiltonian with basis functions $\chi_{m \mathbf{k}}$ and $\chi_{m^{\prime} \mathbf{k}^{\prime}}$ are nonzero only for $\mathbf{k}=\mathbf{k}^{\prime}$, i.e., the Bloch theorem, and derive the form given in Eq. (14.4).
14.4 Derive the factor $A_{m \mathbf{k}}$ in Eq. (14.3) required for the Bloch basis states $\chi_{m \mathbf{k}}(\mathbf{r})$ to be normalized. Show that $A_{m \mathbf{k}}=1$ if the functions $\chi_{m}\left(\mathbf{r}-\left(\tau_{m}+\mathbf{T}\right)\right)$ are orthonormal and that in general $A_{m \mathbf{k}}=\left(S_{m, m}(\mathbf{k}=0)\right)^{-\frac{1}{2}}$, where $S(\mathbf{k})$ is defined in Eq. (14.5). This relation is used in Exercise 23.2 in examples of Wannier functions.
14.5 Show that, in general, one has the relation $K_{l l^{\prime} m}=(-1)^{l+l^{\prime}} K_{l^{\prime} l m}$ under interchange on the indices of the $K$ matrix. This follows from a consistent definition of the orbitals.
14.6 Show that for an s band in a line, square lattice, and simple cubic lattice with only nearest neighbor hamiltonian matrix elements, the respective densities of states (DOS) have the forms shown schematically in Fig. 14.4. First determine the form for the DOS for the one-dimensional line analytically. Then use this result along with the fact that the bands, Eq. (14.13), are simply a sum of cosines for orthogonal directions to derive the form of the DOS for the square and simple cubic lattice. Show that the bands are divided into segments of width $4 t$ as stated, and show that in three dimensions the DOS is exactly symmetric and flat in the central range.
14.7 Consider an s band in a square lattice with nearest neighbor matrix element $t$ and one electron per cell. Show that the Fermi surface is a square as shown in Fig. 14.3 and there is a divergence in the density of states at the Fermi energy as shown in Fig. 14.4.
14.8 Derive the expression for the tight-binding s band $\varepsilon(\mathbf{k})$ in a simple cubic crystal. Assume the states are orthonormal and have hamiltonian matrix elements $t_{1}, t_{2}$, and $t_{3}$ for the first three neighbors. The bands for $t_{2}=t_{3}=0$ are an approximation for the s-like conduction bands in CsCl , which has simple cubic structure. Compare with a calculated band structure in the literature.
14.9 Derive the expression for an s band $\varepsilon(\mathbf{k})$ in an fcc crystal with nearest neighbor hamiltonian matrix element $t$ assuming the states are orthonormal. This should be a qualitative approximation for the lowest-conduction band in an fcc metal like Al or an ionic insulator like NaCl , which has the fcc structure. Compare with the nearly-free-electron bands in Fig. 12.1, Fig. 16.6, or calculated band structures in the literature. (Note that there is a relation to the expressions derived in Exercise 14.8 for second neighbors in a simple cubic lattice. Explain the relation in detail.)
14.10 Derive the expression for an s band in an hcp crystal with nearest neighbor hamiltonian matrix element $t$ assuming the states are orthonormal. Assume the $c / a$ ratio is the ideal value. Explicitly evaluate the bands in the direction along the $c$ axis perpendicular to the hexagonal planes. Show that the lower and upper bands touch at the zone boundary, i.e., there is no gap at the zone boundary. Explain why this happens even though there are two atoms per primitive cell.
14.11 Derive expressions for p bands respectively in simple cubic and fcc crystals with nearest neighbor hamiltonian matrix element $t_{p p \sigma}$ and $t_{p p \pi}$. Compare with calculated bands in the literature for the Cl p state in CsCl and NaCl , respectively, to find reasonable values of $t_{p p \pi}$ and $t_{p p \sigma}$.
14.12 There is a close relation of p bands to the equations for phonons as expressed in Exercises 20.3-20.5. As an example, derive the explicit relation of tight-binding equations for p bands in Exercise 14.11 and the phonon dispersion curves in Exercise 20.6 for a nearest neighbor central potential model.
14.13 See Exercise 26.2 for bands in the two-site model in Fig. 26.2.
14.14 Consider a model like that in Exercise 26.2 except that the state on the B atom has p symmetry. For on-site energies $\varepsilon_{A}>\varepsilon_{B}$, this is a one-dimensional model for an ionic crystal like NaCl . From the symmetry of the crystal, show that two bands are formed from the s and $\mathrm{p}_{x}$ states decoupled from bands formed by the orthogonal $\mathrm{p}_{y}$ and $\mathrm{p}_{z}$ states. Assume the states are orthonormal and there are only nearest neighbor hamiltonian matrix elements of magnitude $t$. In terms of $\Delta=\varepsilon_{A}-\varepsilon_{B}$ and $t$, give analytic expressions for $\mathrm{s}-\mathrm{p}_{x}$ bands $\varepsilon_{i}(k)$. Describe any simplifications in the expressions at $k=0$ and the BZ boundary. Plot the bands in the Brillouin zone for the case $\Delta=4 t$ and show there is qualitative agreement with published bands of NaCl in the (100) direction. What values of $\Delta$ and $t$ provide a reasonable description of NaCl bands? Suggest changes that would better describe the bands.
14.15 Show that the model of Cu and O states shown on the left-hand side of Fig. 14.8 leads to effective model nearest neighbor interactions between Cu states as shown on the right-hand side of the figure. Hint: construct a $3 \times 3$ matrix and diagonalize to find the highest band that corresponds to the band that crosses the Fermi energy in Fig. 17.8.
14.16 Show that the expression for bands with nonorthogonal basis orbitals, Eq. (14.15), is correct. The bands are no longer symmetric about $\varepsilon=0$. Why is this? What is the physical interpretation? See the following problem for more general properties.
14.17 This problem is to analyze the general consequences of the overlap term in a nonorthogonal basis. Show that the effect of the overlap can be transformed to an orthogonal form, with the result that the hamiltonian matrix elements have infinite range, decaying exponentially. This is the correct result as shown by the decay of orthonormal Wannier functions in Chapter 23. Thus show that rigorously it can never be fully consistent to assume that the hamiltonian matrix elements are finite range and yet the orbitals are orthogonal. The same conclusion is found in Exercise 23.2.
14.18 Give a simple argument why "cosine" appeared many times in this chapter, whereas "sine" did not appear at all.
14.19 This problem relates to the structure and bands of a plane of graphene. Show that the Brillouin zone has the shape and orientation shown in the two cases in Fig. 14.7; also show that one of the K points is given by $k_{x}=4 \pi / 3 a, k_{y}=0$ and find the coordinates of all six K points. Show that the bands indeed touch at all six K points.
14.20 Derive Eq. (14.17) for the bands in graphene.
14.21 Show that rolling of a graphene sheet to form $(n, 0)$ and $(n, n)$ tubes leads, respectively, to the structures and Brillouin zones for the "zigzag" and "armchair" tubes that are shown in Fig. 14.7. For the armchair tubes show that the allowed states always include the states at the K point in graphene, so that simple mapping of graphene bands always leads to the prediction of metallic bands. For the zigzag tubes, give the conditions for which the allowed states include the graphene K point.
14.22 Show that the expressions for the force and stress theorems in tight-binding form, Eqs. (14.28) and (14.29), follow immediately from the condition that energy is minimum w.r.t. the coefficients in the wavefunctions.
14.23 Consider a heteropolar diatomic molecule with a total of two electrons. The hamiltonian is approximated by a orthogonal tight-binding model with one state per atom and hamiltonian matrix elements $H_{11}=E_{1}, H_{22}=E_{2}$, and $H_{12}=H_{21}=t(x)$, where $x$ is the distance between atoms. Find the analytic expression for the ground-state energy $E$.
(a) Calculate the force on atoms 1 and 2 directly from the derivative of the analytic expression for the energy and also from the force theorem.
(b) Do the same for a generalized force $\mathrm{d} E / \mathrm{d} \Delta$, where $\Delta=E_{1}-E_{2}$.
14.24 Find expressions for the valence and conduction band eigenvalues in a diamond-structure crystal at $\mathbf{k}=0$ in terms of the matrix elements of the hamiltonian, the on-site energies $E_{\mathrm{S}}$ and $E_{\mathrm{p}}$, and the matrix elements $H_{\mathrm{SS} \sigma}, H_{\mathrm{sp} \sigma}, H_{\mathrm{pp} \sigma}$, and $H_{\mathrm{pp} \pi}$. Do this in two steps. First, show that the eigenstates at $\mathbf{k}=0$ are pure s or pure p. Next, use this fact to find expressions for the four eigenvalues for bonding and antibonding s and p states. Assuming four electrons per atom, identify the valence and conduction states and the gap between filled and empty states at $\mathbf{k}=0$. Find numerical values for Si using Harrison's "universal" table [354, 615] and compare with bands that can be found in many references. The valence bands should be similar but the conduction bands are quite different.


[^0]:    ${ }^{1}$ Here "tight-binding" means "highly localized atomic states," whereas it has taken different meaning as a semiempirical method with two-center matrix elements following the Slater-Koster approach (Section 14.4) in more recent years.

[^1]:    ${ }^{2}$ Here the subscript $m$ is a generic label for a basis function as in other chapters; when used in combination with $l, m$ denotes the azimuthal quantum number, e.g., in Section 14.2.

[^2]:    ${ }^{3}$ This decomposition can always be done formally. Often $V^{\kappa}(|\mathbf{r}|)$ can be approximated as spherical atomic-like potentials associated with atom of type $\kappa$.

[^3]:    ${ }^{4}$ This is a well-known case [240] where the simple LDA and GGA functionals predict a metal at half-filling, whereas the real solution is an antiferromagnetic insulator. Nevertheless, the metallic state created by doping appears to be formed from the band as described here.

[^4]:    ${ }^{5}$ There are 40 parameters each for intersite hamiltonian and overlaps, and 13 on-site terms ( $\mathrm{s}, \mathrm{p}, \mathrm{d}_{e_{g}}, \mathrm{~d}_{t_{2 g}}$ ).

