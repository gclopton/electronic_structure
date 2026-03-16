## 16

# Augmented Functions: APW, KKR, MTO 


#### Abstract

Summary Augmentation provides a method of constructing a basis that is in some ways the "best of both worlds": the smoothly varying parts of the wavefunctions between the atoms represented by plane waves or other smoothly varying functions and the rapidly varying parts near the nuclei represented as radial functions times spherical harmonics inside a sphere around each nucleus. The solution of the equations becomes a problem of matching the functions at the sphere boundary. The original approach is the augmented plane wave (APW) method of Slater, which leads to equations similar to the pseudopotential and OPW equations but with matrix elements of a more complicated, energy-dependent potential operator. The disadvantage of augmentation is that the matching conditions lead to nonlinear equations, which has led to the now widely used linearized methods described in Chapter 17. The KKR method is a multiple-scattering Green's function approach that yields directly local quantities. The muffin-tin orbital (MTO) approach reformulates the KKR method, leading to physically meaningful descriptions of the electronic bands in terms of a small basis of localized, augmented functions.


### 16.1 Augmented Plane Waves (APWs) and "Muffin Tins"

The augmented plane wave (APW) method, introduced by Slater [61] in 1937, expands the eigenstates of an independent-particle Schrödinger equation in terms of basis functions, each of which is represented differently in the two characteristic regions illustrated in Fig. 16.1. In the region around each atom the potential is similar to the potential of the atom and the solution for the wavefunction is represented in a form appropriate to the central region of an atom. In the interstitial region between atoms the potential is smooth and the wavefunction is represented in a form appropriate to smooth variations coupling the atomic-like regions.

If the total effective potential is approximated as spherically symmetric $V_{\text {eff }}(\mathbf{r}) \rightarrow V_{\text {eff }}(r)$ within each sphere, and constant $V_{\text {eff }}(\mathbf{r}) \rightarrow V_{0}$ in the interstitial region, it is termed a "muffin-tin potential." This approximation is very appropriate for many problems and

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-02_540_1020_247_324.jpg)
Figure 16.1. The "muffin-tin" division of space into intra-atomic spheres of radius $S$, and interstitial regions. This is the basis for representing wavefunctions differently in the different regions used in all augmented formulations. The muffin-tin potential approximates the potential in the two regions, but the division into spheres and interstitial regions is more general and can be applied to any potential. (The picturesque name derives from the fact that the figure looks like a pan for cooking muffins.)

allows for dramatic simplifications, since the wavefunctions can be represented in terms of the eigenstates in each region, i.e., spherical harmonics around each atom and plane waves in between. The entire problem is recast into a matching or boundary condition problem. It is most instructive to first discuss the APW approach for such idealized muffin-tin potentials; however, we emphasize that the Schrödinger equation with a general potential (and the full Poisson equation) can be solved using the APW basis. Generalization of the equations to "full-potential" problems is discussed in Chapter 17 after linearization is introduced.

In many ways, the APW approach brings together the "best of both worlds" with the ability to treat highly localized atomic-like states (e.g., core states) using atomiclike spherical functions and delocalized states using delocalized plane waves - the Bloch wavefunctions for the crystal illustrated in Fig. 4.11 are solved separately in the two regions in terms of the APW basis functions (defined in Eq. (16.2) and illustrated in Fig. 16.2). The disadvantage is the difficulty of matching the functions and solving the resulting nonlinear equations in this basis. We will first describe the original nonlinear methods, which illustrate many of the main ideas and the relations to other methods, OPW, pseudopotential, and KKR, etc., through their common features of describing the valence states in terms of the scattering properties of the atoms, which in turn are determined by the phase shifts. A separate chapter (Chapter 17) is devoted to linearized methods because of their conceptual and practical importance in transforming the augmented methods into more useful forms.

Just as in the plane wave (see Eq. (12.11)) or OPW (see Eq. (11.1)) method, each Bloch function $\psi_{i, \mathbf{k}}(\mathbf{r})$ is expanded in a set of basis functions labeled by the reciprocal lattice vectors $\mathbf{G}_{m}, m=1,2, \ldots$,

$$
\psi_{i, \mathbf{k}}(\mathbf{r})=\sum_{m} c_{i, m}(\mathbf{k}) \chi_{\mathbf{k}+\mathbf{G}_{m}}^{\mathrm{APW}}(\mathbf{r}) .
$$

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-03_741_1130_247_272.jpg)
Figure 16.2. Schematic representation of the APW basis functions for $\mathbf{k}=0$ (top) and the zone boundary (real part shown in bottom panel). The sphere boundaries are represented by the vertical dashed lines. In the interstitial region, each APW is a single plane wave. Inside each sphere the APW is a solution of the radial equation, with the boundary condition that it match the plane wave in value. A single APW has a discontinuous derivative at the boundaries. The solution for the eigenstate minimizes the final discontinuity in the derivative, leading to Bloch states like those illustrated in Fig. 4.11.

However, in the APW method each basis function $\chi_{\mathbf{k}+\mathbf{G}}(\mathbf{r})$ is represented as a single plane wave only in the interstitial region between atoms, and within a sphere of radius S around each atom the function is represented in spherical harmonics:

$$
\chi_{\mathbf{k}+\mathbf{G}_{m}}^{\mathrm{APW}}(\mathbf{r})= \begin{cases}\exp \left(\mathrm{i}\left(\mathbf{k}+\mathbf{G}_{m}\right) \cdot \mathbf{r}\right), & r>S, \\ \sum_{L S} C_{L S}\left(\mathbf{k}+\mathbf{G}_{m}\right) \psi_{L S}(\varepsilon, \mathbf{r}), & r<S,\end{cases}
$$

where the compact notation for the wavefunction, ${ }^{1}$

$$
\psi_{L s}(\varepsilon, \mathbf{r})=i^{l} Y_{L}(\hat{r}) \psi_{l s}(\varepsilon, r),
$$

is introduced to simplify the notation. The angular momentum is indicated by upper case $L \equiv l, m_{l}$, and $Y_{L}(\hat{r}) \equiv Y_{l, m_{l}}(\theta, \phi)$ are spherical harmonics, with $r$ and $\hat{r}$ referred to an origin $\tau_{s}$ for each atom $s$ in the unit cell. The function $\psi_{l s}(\varepsilon, r)$ is a solution of the radial

[^0]Schrödinger equation regular at the origin at energy $\varepsilon$, i.e., it satisfies Eq. (10.12), written here keeping factors of $\hbar$ and $m_{e}{ }^{2}$

$$
\left[\frac{\hbar^{2}}{2 m_{e}}\left(-\frac{\mathrm{d}^{2}}{\mathrm{~d} r^{2}}+\frac{l(l+1)}{r^{2}}\right)+V_{s}(r)-\varepsilon\right] r \psi_{l s}(r)=0
$$

It is important here that $\varepsilon$ is a variable and need not be an eigenvalue. Schematic forms of two $\chi_{\mathbf{k}+\mathbf{G}_{m}}^{\mathrm{APW}}(\mathbf{r})$ are shown along a line through the atoms in Fig. 16.2.

The coefficients $C_{L s}\left(\mathbf{k}+\mathbf{G}_{m}\right)$ are obtained by requiring the waves to match at the surface of the muffin-tin spheres, i.e., that the phase shifts match as described in scattering theory, Section J.1. Using the expansion given in Eq. (J.1),

$$
\mathrm{e}^{\mathrm{i} \mathbf{q} \cdot \mathbf{r}}=4 \pi \sum_{L} i^{l} j_{l}(q r) Y_{L}^{*}(\hat{\mathbf{q}}) Y_{L}(\hat{\mathbf{r}})
$$

where $j_{l}(q r)$ are spherical Bessel functions, it follows that $\chi^{\mathrm{APW}}$ is continuous at the sphere boundary if

$$
C_{L s}\left(\mathbf{K}_{m}\right)=4 \pi \mathrm{e}^{\mathrm{i} \mathbf{K}_{m} \cdot \tau_{s}} j_{l}\left(\left|\mathbf{K}_{m}\right| S_{s}\right) \frac{Y_{L}^{*}\left(\hat{\mathbf{K}}_{m}\right)}{\psi_{l s}\left(\varepsilon, S_{s}\right)},
$$

where $\mathbf{K}_{m}=\mathbf{k}+\mathbf{G}_{m}$. An APW is, by construction, discontinuous in slope on the muffintin boundary (see Fig. 16.2), a fact that must be taken into account when applying the kinetic energy operator.

Within the APW basis, the secular equation can be written

$$
\sum_{m}\left\{\left\langle m^{\prime}\right| H-\varepsilon_{i, \mathbf{k}}|m\rangle+\left\langle m^{\prime}\right| H^{S}|m\rangle\right\} c_{i, m}(\mathbf{k})=0
$$

where

$$
\left\langle m^{\prime}\right| H-\varepsilon_{n}(\mathbf{k})|m\rangle=\int_{\text {cell }} \mathrm{d}^{3} r \chi_{\mathbf{k}+\mathbf{G}_{m^{\prime}}}^{*}(\mathbf{r})\left[H-\varepsilon_{n}(\mathbf{k})\right] \chi_{\mathbf{k}+\mathbf{G}_{m}}(\mathbf{r}),
$$

and the discontinuity is incorporated into the integral over the sphere surface(s) using Green's identity (Exercise 16.2)

$$
\begin{aligned}
\left\langle m^{\prime}\right| H^{S}|m\rangle & =\int_{S} \mathrm{~d} S \chi_{\mathbf{k}+\mathbf{G}_{m^{\prime}}}^{*}(\mathbf{r})\left[\frac{\partial}{\partial r} \chi_{\mathbf{k}+\mathbf{G}_{m}}\left(\mathbf{r}^{-}\right)-\frac{\partial}{\partial r} \chi_{\mathbf{k}+\mathbf{G}_{m}}\left(\mathbf{r}^{+}\right)\right] \\
& =\int_{S} \mathrm{~d} S \chi_{\mathbf{k}+\mathbf{G}_{m^{\prime}}}^{*}(\mathbf{r})\left[\frac{\partial}{\partial r} \ln \chi_{\mathbf{k}+\mathbf{G}_{m}}\left(\mathbf{r}^{-}\right)-\frac{\partial}{\partial r} \ln \chi_{\mathbf{k}+\mathbf{G}_{m}}\left(\mathbf{r}^{+}\right)\right] \chi_{\mathbf{k}+\mathbf{G}_{m}}\left(\mathbf{r}^{-}\right)
\end{aligned}
$$

where $+(-)$ indicates just outside (inside) the sphere.
${ }^{2}$ The factor $\hbar^{2} / 2 m_{e}=\frac{1}{2}$ in Hartree atomic units, where $\hbar=m_{e}=e=1$ is used in this text. In the present chapter and the next, $\hbar$ and $m_{e}$ are explicitly indicated where needed to avoid confusion with expressions in the literature, since many authors use "Rydberg atomic units," where $\hbar=2 m_{e}=e^{2} / 2=1$.

One way to proceed is to solve the secular equation (16.7) in terms of matrix elements of the hamiltonian and the overlap matrix, just as for any nonorthogonal orbital. However, one can take advantage of the fact that the basis functions are not fixed but instead are chosen to satisfy the Schrödinger equation inside each muffin-tin sphere at energy $\varepsilon$. Thus the integral Eq. (16.7) is zero inside each sphere and needs to be evaluated only in the interstitial region where the hamiltonian is just the kinetic energy operator and $\chi$ is a plane wave. All the information about the way each atom affects the bands is incorporated into the boundary terms, i.e., boundary conditions on the plane waves. This is, of course, not surprising since the wavefunction both inside and outside the spheres must each obey the Schrödinger equation in their respective regions subject to the boundary conditions. ${ }^{3}$

Following this approach, it is straightforward to cast the APW equation (16.6) in a form identical to that in plane wave Fourier methods,

$$
\sum_{\mathbf{G}}\left\{\left[\frac{\hbar^{2}}{2 m_{e}}(\mathbf{k}+\mathbf{G})^{2}-\varepsilon_{i, \mathbf{k}}\right] \delta_{\mathbf{G}^{\prime} \mathbf{G}}+V_{\mathbf{G}^{\prime}, \mathbf{G}}^{\mathrm{APW}}\left(\varepsilon_{k}, \mathbf{k}\right)\right\} c_{i, \mathbf{G}}(\mathbf{k})=0,
$$

where the first term is the usual kinetic energy for a plane wave extended throughout the cell including the sphere, the energy is relative to the constant in the muffin-tin potential, and all effects due to the potential in the sphere are collected into an APW "potential" $\hat{V}^{\mathrm{APW}}$, which is an operator that is both nonlocal and energy dependent. The matrix elements of $\hat{V}^{\mathrm{APW}}$ for a sphere at $\tau=0$ in the unit cell are [157, 666]

$$
\begin{aligned}
V_{\mathbf{G}^{\prime}, \mathbf{G}}^{\mathrm{APW}}\left(\varepsilon_{k}, \mathbf{k}\right)= & -\frac{4 \pi S^{2}}{\Omega_{\mathrm{cell}}}\left(\frac{\hbar^{2}}{2 m_{e}}|\mathbf{k}+\mathbf{G}|^{2}-\varepsilon_{k}\right) \frac{j_{1}\left(\left|\mathbf{G}-\mathbf{G}^{\prime}\right| S\right)}{\left|\mathbf{G}-\mathbf{G}^{\prime}\right|} \\
& +\frac{\hbar^{2}}{2 m_{e}} \frac{4 \pi S}{\Omega_{\mathrm{cell}}} \sum_{l}\left\{(2 l+1) P_{l}\left(\cos \left(\theta_{\mathbf{G G}^{\prime}}\right) j_{l}\left(\left|\mathbf{k}+\mathbf{G}^{\prime}\right| S\right) j_{l}(|\mathbf{k}+\mathbf{G}| S)\right\}\right. \\
& \times \Delta D_{l, \mathbf{G}}\left(\varepsilon_{k}\right)
\end{aligned}
$$

with $\theta_{\mathbf{G G}^{\prime}}$ the angle between vectors $\mathbf{k}+\mathbf{G}$ and $\mathbf{k}+\mathbf{G}^{\prime}$, and $S$ the sphere radius. For a crystal with more than one sphere centered at positions $\tau_{s}$, it is simple to show that the potential is a sum of terms with phase factors $\exp \left(\mathrm{i}\left(\mathbf{G}-\mathbf{G}^{\prime}\right) \cdot \tau_{s}\right)$ just as in the plane wave method (Eq. (12.16) and Exercise 12.2). The first term in the APW potential operator Eq. (16.10) subtracts the kinetic energy for that part of the plane wave inside the spheres (see Loucks [666], p. 32-33), and the last term ${ }^{4}$ includes all the effects of the atoms in

[^1]terms of the difference of the dimensionless logarithmic derivative $\Delta D_{l, \mathbf{G}}(\varepsilon)$ from that of an empty sphere
$$
\Delta D_{l, \mathbf{G}}(\varepsilon)=\left[r \frac{\mathrm{~d}}{\mathrm{~d} r} \ln \psi_{l}(\varepsilon, r)-r \frac{\mathrm{~d}}{\mathrm{~d} r} \ln j_{l}(|\mathbf{k}+\mathbf{G}| r)\right]_{r=S},
$$
which follows from Eq. (16.8) for the boundary "kink" term, with the function just inside the sphere given by $\psi_{l}(\varepsilon, r)$ and the function just outside by the partial wave component of the unscattered plane wave $j_{l}$. (The normalization is not needed for the logarithmic derivative.) It is interesting that the "potential" operator involves $\frac{\hbar^{2}}{2 m_{e}}$; this is because it really is a "matching operator."

### 16.2 Solving APW Equations: Examples

The APW equations are more difficult than the usual independent-particle equations that are linear in energy $\varepsilon$, such as Eq. (12.9) for plane waves or Eq. (14.7) for localized orbitals, where all the eigenvalues and eigenvectors can be determined at once from a single diagonalization. Instead, the APW equations must be solved separately for each eigenstate as follows:

- Solution of the matrix equation (16.9) has exactly the same form as the usual linear equations, except that the potential operator depends on the logarithmic derivatives in Eq. (16.11) that are functions of the energy $\varepsilon=\varepsilon_{i, k}$, which are not known in advance and are different for each band.
- In order to find the logarithmic derivatives, the radial equations (16.3) for $r \psi_{l}(\varepsilon, r) \equiv \phi_{l}(\varepsilon, r)$ must be solved for each band energy $\varepsilon_{i, k}$, individually. However, $\varepsilon_{i, k}$ are established only in conjunction with solution of the plane wave equations (16.9). In general, this requires "root tracing," i.e., searching for the zeros of the determinant on the APW matrix given in Eq. (16.9). This may be done by fixing $\varepsilon$ and varying $k$ or vice versa.
- There can be simplification in some cases, e.g., highly localized states, such as core states that are completely contained in the sphere, are fully specified by $\psi_{l}(\varepsilon, r)$ and there is no $\mathbf{k}$ dependence and it can often be considered to be the same as in an atom. This is termed the "frozen-core approximation."


## Illustrative Examples

Two limiting cases illustrate the power and generality of the APW method: the nearly-free-electron case and the opposite limit in which the spherical potential has a strong resonance. It is important that, despite the artificial division of space, the free-electron case is solved trivially. If the potential inside the muffin-tin sphere is set to be the same constant value as in the interstitial, exact solutions inside the spheres are spherical Bessel functions $j_{l}$, in which case the difference in logarithmic derivatives vanishes $\Delta D_{l}\left(\varepsilon_{k}\right)=0$.

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-07_549_798_249_439.jpg)
Figure 16.3. Logarithmic derivatives of the radial wavefunctions in Cu , defined in Eq. (16.11) as a function of energy in Hartrees for different angular momenta $l$, evaluated at a sphere radius $S=2.415 a_{0}$ appropriate for metallic Cu . For comparison are shown the free-electron curves (Exercise 16.5). The $l=2 \mathrm{~d}$ channels show strong resonance, leading to narrow bands, whereas the $l=0,1,3$ channels reveal the nearly-free-electron behavior. These are essentially the same as for the Chodorow potential [668] used in the pioneering work of Burdick [669]. From Kubler and Eyert [157], who attribute the figure to Slater and Mattheiss

It follows immediately that the eigenvalues of Eq. (16.9) are just those for free electrons $\varepsilon_{k}=\frac{1}{2}|\mathbf{k}+\mathbf{G}|^{2}$. If the phase shift $\Delta D_{l}\left(\varepsilon_{k}\right) \neq 0$ but is small, then the dispersion $\varepsilon_{k}$ will be only slightly modified. This is the "nearly-free-electron case" and the APW method clarifies an important point: this does not necessarily mean the potential is small or that the wavefunctions are close to a single plane wave. The difference in phase shift can be small even for strong potentials. Explicit cases, where actual phase shifts are close to free-electron values, are for Na ([484], p. 242) and many examples in [667]. Logarithmic derivatives for Cu are presented in Fig. 16.3, which shows that the phase shifts for $l=0,1,3$ are very close to the free-electron values (see Exercise 16.5). Thus the APW approach explains the nearly-free-electron character of bands in many materials that are weak scatterers just as well as the OPW or pseudopotential methods.

The opposite limit is a resonance at energy $\varepsilon_{0}$ where the phase shift becomes large. In an isolated atom, the logarithmic derivative $D(\varepsilon)$ evaluated at large radius diverges at $\varepsilon=\varepsilon_{0}$, signifying a bound state at that energy. (This is one of the standard methods to find bound states in actual atomic programs.) In a crystal, the fact that the phase shift at radius $S$ changes rapidly with energy means that the Bloch boundary conditions for different $\mathbf{k}$ can be satisfied with only small changes in energy, i.e., a band $\varepsilon(\mathbf{k})$ with only a small dispersion. In the case of Cu , the $l=2$ logarithmic derivative disperses rapidly corresponding to the d bands in Cu , which are much narrower than the $\mathrm{s}-\mathrm{p}$ bands. In general, the bands start as parabolic and each resonance introduces a new band, which has the physical interpretation of each atomic state broadening into a band in the crystal.

## Calculations of Bands Using the APW Method

The power of the APW approach was first fully realized after the advent of electronic computers, in particular, for the first accurate calculations of bands of transition and rare earth metals. A well-known early example is the band structure of Cu calculated by Burdick [669] in 1963, which are in very good agreement with measurements from angle-resolved photoemission experiments by Thiry et al. [670] in 1979. The logarithmic derivatives in the APW equations were calculated using the Chodorow potential [668], derived in 1939 for the Cu atom, and are essentially the same as shown in Fig. 16.3. The impressive agreement between measured and calculated energies is due to two factors: (1) the potential was modeled as a sum of atomic potentials fitted to the atom and (2) Cu has a filled (closed-shell) d band and a wide $\mathrm{s}-\mathrm{p}$ band, a case in which independent-particle methods are expected to work well. ${ }^{5}$ In general, one should exercise caution in identifying Kohn-Sham eigenvalues as excitation energies and one should not expect such agreement.

Bands for the entire series of 3d transition metals are presented in Fig. 16.4, which shows narrow d bands crossing the wider s-p bands. The 3d bands are much broader than the 4f bands of the lanthanides but narrow enough to indicate that many atomic-like properties carry over to the solid. At the time this work was done in 1964, a central issue was the choice of the potential. Mattheiss used overlapping atomic potentials derived from HartreeFock density and Slater's local approximation for exchange [672]. This is very similar to a Kohn-Sham calculation but the exchange differs from the LDA by a factor of $4 / 3$, and correlation is not included. In hindsight, this choice has been found to have some justification (see Fig. 8.6).

The transition metals have partially occupied d bands. This leads to their magnetic behavior and correlations among the d electrons. Nevertheless, independent-particle methods are in many ways adequate to describe the basic properties of these metals [673], e.g., the prediction of magnetism from the Stoner criterion, as illustrated in Fig. 2.8 [104, 157, 673]. At the end of the series is the noble metal Cu in which the d bands are filled but only slightly below the Fermi energy, which leads to its closed-shell, nonmagnetic behavior and its yellow color. The total energies for the series are remarkably well described by the local density approximation, as illustrated in Fig. 2.2.

Looking at the bands in more detail, we see that in all cases the lowest band is minimum at the $\Gamma$ point $(\mathbf{k}=0)$ in the BZ, with energy defined to be $\varepsilon=0$; the label $\Gamma_{1}$ designates the same symmetry as an s wave function $(l=0)$. The nearly parabolic $\varepsilon_{k}$ curve is modified because it mixes with narrower bands (examples of a resonance) that start at $\Gamma$ with labels $\Gamma_{25^{\prime}}$ and $\Gamma_{12}$, which are labels for $\mathrm{d}(1=2)$ states in cubic symmetry: $\Gamma_{25^{\prime}}$ is threefold degenerate and transforms under rotations like $x y, y z$, and $z x$, whereas $\Gamma_{12}$ is twofold degenerate and transforms like $x^{2}-y^{2}$ and $2 z^{2}-x^{2}-y^{2}$. The bands labeled $\Delta_{5}$ and $\Lambda_{3}$ are twofold degenerate d states along the lines shown. At higher energy around the Fermi level, the bands are also approximately parabolic; this is the feature that explains why Cu

[^2]![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-09_1490_1038_243_317.jpg)
Figure 16.4. Bands of 3d metals calculated by Mattheiss [671] in 1964 using the APW method. The figures show the narrow d bands crossing the wide s band and the progression of band filling across transition series. At the top are elements with body centered cubic (bcc) and at the bottom face centered cubic (fcc) structures. The bands are shown along the lines labeled $\Delta$ from $\Gamma-\mathrm{H}$ and $\Gamma-\mathrm{X}$ respectively, in the Brillouin zones shown in Fig. 4.10. The potential was derived in a clever way that preceded DFT as described in the text.

is a good electrical conductor. The states $\mathrm{X}_{4^{\prime}}$ at $\varepsilon \approx 0.80 \mathrm{Ry}$ and $\Lambda_{2^{\prime}}$ at $\varepsilon \approx 0.61 \mathrm{Ry}$ have labels that designate p symmetries ( $l=1$ ), which is expected for a free-electron band, and the eigenvalues are quite close to free-electron energies at the density of one electron per Cu atom as discussed in Exercise 16.5.

The bands $\varepsilon_{k}$ for the non- d states are close to free-electron bands; however, the wavefunctions are far from single plane waves. Although they are close to a single plane wave between the atomic spheres, inside each sphere the wavefunctions have all the oscillations characteristic of atomic 4 s and 4 p wave functions. The point is that a single plane wave joins smoothly onto the solution of the Schrödinger equation inside the sphere, illustrated in Fig. 4.11, so that the energy is essentially the same as that of the plane wave. In addition, the $\mathrm{s}-\mathrm{p}$ states hybridize with the d states, which act like a resonance in the scattering of the s electrons from the atoms. This is the basis of the "s-d model" [674], which describes the $s-p$ bands near the energies of the $d$ states and the resulting dispersion in the narrow $d$ bands (Exercise 16.6).

As an example of spin-dependent bands in a ferromagnet, Fig. 16.5 shows the bands for Ni in the fcc structure calculated by Connolly [675]. The solid lines show the majorityspin and the dashed lines the minority-spin bands calculated with the local spin-density formalism of Kohn and Sham. Connolly also found the bands using the Slater local exchange and concluded that it gives much poorer agreement with experiment. The larger exchange causes significant changes in the bands, particularly around the L point.

It should be emphasized, however, that density functional theory approximations often lead to wrong predictions, especially for more strongly correlated electron systems such

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-10_643_876_1315_399.jpg)
Figure 16.5. Spin-polarized bands of ferromagnetic Ni in the fcc structure [675]. Solid lines indicate the majority-spin and dashed lines the minority-spin bands. The numbers indicate symmetry labels at high-symmetry points. This figure represents the results using the Kohn-Sham local spin density approximation. (The Slater local exchange gives poorer agreement with experiment, especially around the L point, as shown in [675].)

as the rare earths and the transition metal oxides [240]. In a nutshell, methods that start from the homogeneous gas (LDAs and GGAs) tend to predict solutions that are too much like the gas - nonmagnetic and metallic - whereas methods that involve Hartree-Fockexchange (Hartree-Fock itself and exact exchange tend to predict solutions that are too much like Hartree-Fock - too magnetic and insulating. Methods such as self-interaction correction (SIC) and "DFT+U" can apparently describe aspects of strongly correlated electron systems, but at the cost that the functionals are not universal. Hybrid functionals (Chapter 9) that combine density functionals with a fraction of Hartree-Fock-like exchange have proven to be successful in many cases. The issues related to correlation in 3d and 4f materials is a major topic of [1].

## Practical Aspects

How large is the secular equation? The number of plane waves is determined by the fact that they must accurately represent the variations in the wavefunctions in the interstitial region. These are determined by the fact that they must match the solutions inside the spheres, which is incorporated into the logarithmic derivatives in Eq. (16.9). Thus, in general, we expect the number of plane waves (i.e., the number of APWs) to be comparable to the number of plane waves needed in a norm-conserving pseudopotential calculation, so long as the atoms have relatively smooth orbitals and large interstitial regions (like Si ). However, unlike norm-conserving pseudopotentials, the number of basis functions does not increase as the states become more localized around the atoms (e.g., 3d states in transition metals or 4f in rare earths) since the augmentation takes care of the regions around the atoms. Indeed, roughly 40 APW basis functions are needed for each atom in the unit cell for transition metals [157]. In this respect, APW methods are more closely related to "ultrasoft pseudopotential" and PAW methods (Chapter 11), which can also describe localized states, since they add localized functions and use plane waves only for the smooth part. In addition, spherical harmonics with high angular momenta are required for accurate description of the bands (see also Section 17.4).

The APW method is not restricted to muffin-tin potentials and it can be extended to general potentials [107]. The APW basis can be defined as before (using an effective muffin-tin potential determined by averaging the full potential) but now one must calculate matrix elements of the full potential. The solution has the same general form as Eqs. (16.9) and (16.10), but it becomes more complicated because the matrix elements are no longer diagonal in angular momentum in the sphere nor in momentum in the interstitial region. The extension becomes much more feasible using linearized methods and further discussion is given in Section 17.10.

### 16.3 The KKR or Multiple-Scattering Theory (MST) Method

In the words of J. Ziman [676]:
From mathematical point of view, the most refined method of calculating energy band structures is the subtle procedure invented independently by Korringa [677] and Kohn and

Rostoker [678]. This method is indeed so fundamental that it is to be found in all its essentials in a study by Rayleigh [679] [in 1892] of the propagation of sound waves through an assembly of spheres.

The KKR method, also called "multiple-scattering theory" (MST) or Green's function method, finds the stationary values of the inverse transition matrix $T$ rather than the hamiltonian. This is the method used in the pioneering work of Moruzzi and coworkers [103, 104], highlighted in Section 2.3, that first established the efficacy of density functional theory for calculation of properties of close-packed metals. In addition, KKR is the method of choice for most calculations on liquids, disordered systems, and impurities in various metallic and nonmetallic hosts. Probably the most important features of the KKR or Green's function formulation are (1) it separates the two aspects of the problem, the structure (positions of the atoms) from the scattering (chemical identity of the atoms) and (2) Green's functions provide a natural approach to a localized description of electronic properties that can be adapted to alloys and other disordered systems.

Here we consider only muffin-tin potentials, where each site can be viewed as a spherical scatterer; and electrons propagate between sites with the free propagator or Green's function. This greatly simplifies the equations and was the basis of all KKR calculations until the development of full potential methods [680, 681]. The problem of overlapping potentials is subtle and the reader is referred to papers in the collection in [682] and references given there.

A Green's function $G$ describes propagation of a system from one event to another [683], e.g., $G\left(\varepsilon, \mathbf{r}, \mathbf{r}^{\prime}\right)$ describes the system with a particle added at point $\mathbf{r}$ and removed at $\mathbf{r}^{\prime}$ with energy $\varepsilon$. In terms of a reference Green's function $G_{0}$ (for example, the free-particle propagator given in Eq. (16.18) below) and scattering matrix elements $t$, representing single scattering events from any of the atoms in the system, the full Green's function can be written in schematic form as

$$
\begin{aligned}
G & =G_{0}+G_{0} t G_{0}+G_{0} t G_{0} t G_{0}+\cdots \\
& =G_{0}+G_{0} t G \Rightarrow \\
G & =\left(G_{0}^{-1}-t\right)^{-1}
\end{aligned}
$$

Similarly, one can sum the series to write $G$ as

$$
G=G_{0}+G_{0} T G_{0}
$$

where $T$ is the full multiple-scattering matrix for the entire system

$$
\begin{aligned}
T & =t+t G_{0} t+t G_{0} t G_{0} t+\cdots \\
& =t+t G_{0}\left(t+t G_{0} t+\cdots\right) \\
& =t+t G_{0} T \Rightarrow \\
T & =\left(t^{-1}-G_{0}\right)^{-1}
\end{aligned}
$$

The stationary states of the system are given by the poles of $G$ or $T$ as functions of $\varepsilon$ and hence are obtained from the zeros of the determinant ${ }^{6}$

$$
\operatorname{det}\left(t^{-1}-G_{0}\right)=0
$$

For independent-particle electronic structure problems with hamiltonian $\hat{H}=-\left(h^{2} /\right. \left.2 m_{e}\right) \nabla^{2}+V_{\text {eff }}(\mathbf{r}),{ }^{7}$ a convenient starting point is to take $G_{0}$ to be the free Green's function. It is useful to first give the well-known solution for the Helmholtz equation $\left(\nabla^{2}+\kappa^{2}\right) g \left(\mathbf{r}-\mathbf{r}^{\prime}\right)=\delta\left(\mathbf{r}-\mathbf{r}^{\prime}\right)$, for which the real solution is

$$
g(x)=-\frac{1}{4 \pi} \frac{\cos (\kappa x)}{x},
$$

where $x=\left|\mathbf{r}-\mathbf{r}^{\prime}\right|$. Thus the Green's function for the Schrödinger equation with $V=0$ satisfies

$$
\left[-\frac{\hbar^{2}}{2 m_{e}} \nabla_{r}^{2}-\left(\varepsilon-V_{0}\right)\right] G_{0}\left(\varepsilon, \mathbf{r}-\mathbf{r}^{\prime}\right)=\delta\left(\mathbf{r}-\mathbf{r}^{\prime}\right),
$$

which has the solution

$$
G_{0}(\varepsilon, x)=\frac{2 m_{e}}{\hbar^{2}} \frac{1}{4 \pi} \frac{\cos (\kappa x)}{x}
$$

where $\left(h^{2} / 2 m_{e}\right) \kappa^{2}=\varepsilon-V_{0}$ and $V_{0}$ is the "muffin-tin zero" reference energy. For positive energies $\varepsilon, G_{0}(\varepsilon, x)$ is a slowly decaying oscillatory function; for negative $\varepsilon$, it decays exponentially.

Within the muffin-tin spherical approximation, the scattering amplitude $t(\varepsilon)$ of an electron from each sphere conserves angular momentum $L \equiv\{l, m\}$ referred to the center of that sphere. Because the scattering is unitary and independent of $m$ [684, 685], $t_{l}(\varepsilon)$ and can be written in terms of the phase shift $\eta_{l}(\varepsilon)$ (see Section J.8)

$$
t_{l}(\varepsilon)=\frac{i}{2 \kappa}\left(\mathrm{e}^{i 2 \eta_{l}(\varepsilon)}-1\right)=-\frac{1}{\kappa} \mathrm{e}^{\mathrm{i} \eta_{l}(\varepsilon)} \sin \left(\eta_{l}(\varepsilon)\right)
$$

The scattering amplitude plays a key role in many phenomena in physics, such as Friedel oscillations around an impurity, resistivity due to impurities, etc. (see Section J.1). The scattering is represented pictorially in Fig. J.1. In the present case, the great advantage is that the electronic bands and Green's functions can be described by a few phase shifts $\eta_{l}(\varepsilon)$, typically $l \leq 3$.

The full solution for the multiple-scattering problem for the muffin-tin potential is given by Eq. (16.15), where $G_{0}$ depends only on the structure and the energy $\varepsilon$, and $t$ incorporates all the effects of the potential inside each sphere. The expressions needed are for the Green's function $G_{0}\left(\varepsilon,\left|\mathbf{r}-\mathbf{r}^{\prime}\right|\right)$ when $\mathbf{r}$ and $\mathbf{r}^{\prime}$ are in the same and different spheres. For different spheres, this requires that a spherical wave of angular momenta $L$ about one sphere be

[^3]expressed in terms of waves centered at another site, which involves a sum over $L^{\prime}$ at that sphere. The needed formulas are given in [10, 157, 684], which can be understood using the addition formula for plane waves
$$
\mathrm{e}^{\mathrm{i} \mathbf{k} \cdot\left(\mathbf{r}-\mathbf{R}_{1}\right)}=\mathrm{e}^{\mathrm{i} \mathbf{k} \cdot\left(\mathbf{r}-\mathbf{R}_{2}\right)} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot\left(\mathbf{R}_{2}-\mathbf{R}_{1}\right)}
$$
together with the identity Eq. (16.4). The result for sites $\mathbf{R} \neq \mathbf{R}^{\prime}$ is given by (see Exercise 16.3)
$$
G_{0}\left(\varepsilon,\left|\mathbf{r}-\mathbf{r}^{\prime}\right|\right)=\sum_{L, L^{\prime}} i^{l} j_{l}(\kappa r) Y_{L}(\hat{\mathbf{r}}) B_{L L^{\prime}}(-i)^{l^{\prime}} j_{l^{\prime}}\left(\kappa r^{\prime}\right) Y_{L^{\prime}}^{*}\left(\hat{\mathbf{r}^{\prime}}\right)
$$
where $\mathbf{r}$ and $\mathbf{r}^{\prime}$ are referred to the centers of their respective spheres, and $B_{L L^{\prime}}$ denotes the "KKR structure constants"
$$
B_{L L^{\prime}}\left(\varepsilon, \mathbf{R}-\mathbf{R}^{\prime}\right)=-4 \pi \kappa \sum_{L^{\prime \prime}} i^{l^{\prime \prime}} C_{L^{\prime} L^{\prime \prime}}^{L} n_{l^{\prime \prime}}\left(\kappa\left|\mathbf{R}-\mathbf{R}^{\prime}\right|\right) Y_{L^{\prime \prime}}\left(\widetilde{\mathbf{R}-\mathbf{R}^{\prime}}\right)
$$
where the $C$ s are directly related to the Gaunt coefficients $c^{l^{\prime \prime}}\left(l m, l^{\prime} m^{\prime}\right)$ defined in Eq. (K.14),
$$
C_{L^{\prime} L^{\prime \prime}}^{L} \equiv \int \mathrm{~d} \Omega Y_{L}^{*}(\Omega) Y_{L^{\prime}}(\Omega) Y_{L^{\prime \prime}}(\Omega)=\sqrt{\frac{2 l^{\prime \prime}+1}{4 \pi}} c^{l^{\prime \prime}}\left(l m, l^{\prime} m^{\prime}\right)
$$

For the general case where the scattering amplitude $t_{l}(\varepsilon, \mathbf{R})$ is site dependent, the resulting equation for the Green's function Eq. (16.12) is

$$
\left[G_{L L^{\prime}}\left(\varepsilon, \mathbf{R}, \mathbf{R}^{\prime}\right)\right]^{-1}=\left[\left[B_{L, L^{\prime}}\left(\varepsilon, \mathbf{R}-\mathbf{R}^{\prime}\right)\right]^{-1}-t_{l}(\varepsilon, \mathbf{R}) \delta_{\mathbf{R}, \mathbf{R}^{\prime}} \delta_{L, L^{\prime}}\right]
$$

and condition Eq. (16.15) for stationary states becomes

$$
\operatorname{det}\left[t_{l}^{-1}(\varepsilon, \mathbf{R}) \delta_{\mathbf{R R}^{\prime}} \delta_{L L^{\prime}}-B_{L L^{\prime}}\left(\varepsilon, \mathbf{R}-\mathbf{R}^{\prime}\right)\right]=0
$$

where $\mathbf{R}, \mathbf{R}^{\prime}$ denote centers of the spheres, and $B_{L L^{\prime}}(\varepsilon, 0) \equiv 0$ for the same site. As it stands, this is a matrix equation in all the sites and angular momenta - a formal expression valid for crystals, molecules, and disordered solids.

## KKR Band Structure Equations

The original equation of Koringa [677] results if we consider a crystal where the scattering is the same at every site, centered on the translations vectors $\mathbf{T}$. Then the determinant equation can be solved separately for each wavevector $\mathbf{k}$. The structure constants can be defined as

$$
B_{L L^{\prime}}(\varepsilon, \mathbf{k})=\sum_{\mathbf{T} \neq 0} B_{L L^{\prime}}(\varepsilon, \mathbf{T}) \mathrm{e}^{-\mathrm{i} \mathbf{k} \cdot \mathbf{T}}
$$

and the bands $\varepsilon=\varepsilon_{\mathbf{k}}$ are the solution of

$$
\operatorname{det}\left[t_{l}^{-1}(\varepsilon) \delta_{L L^{\prime}}-B_{L L^{\prime}}(\varepsilon, \mathbf{k})\right]=0
$$

The well-known form for the KKR equations is found by using expression (16.19) for $t$ (only the real part is needed) in terms of the phase shifts,

$$
\sum_{L^{\prime}}\left[B_{L L^{\prime}}\left(\varepsilon_{\mathbf{k}}, \mathbf{k}\right)+\kappa \cot \left(\eta_{l}\left(\varepsilon_{\mathbf{k}}\right)\right) \delta_{L L^{\prime}}\right] a_{L^{\prime}}(\mathbf{k})=0
$$

This can be generalized straightforwardly to more than one atom per cell, $\alpha=1, \ldots, N$, leading to one band per atom and angular momentum

$$
\sum_{L^{\prime}} \sum_{\beta=1}^{N}\left[B_{L L^{\prime}}\left(\tau_{\alpha}-\tau_{\beta}, \varepsilon_{\mathbf{k}}, \mathbf{k}\right)+\kappa \cot \eta_{l \beta}\left(\varepsilon_{\mathbf{k}}\right) \delta_{L L^{\prime}} \delta_{\alpha \beta}\right] a_{L^{\prime} \beta}(\mathbf{k})=0
$$

The dispersion relation $\varepsilon_{\mathbf{k}}$ can be found from the roots of the determinant of the matrix in square brackets. Often it is most effective to fix the energy and scan the wavevector $\mathbf{k}$ to find the roots, since the phase shifts depend only on energy and the structure constants depend only on $\mathbf{k}$ at a given energy. For example, the Fermi surface can be mapped out conveniently in this way.

The eigenvectors of Eqs. (16.28) or (16.29) determine the wavefunction, since the eigenvectors of the Green's function are the same as those of the hamiltonian. Inside each sphere, the solution is simply a linear combination of the augmentation functions (apart from a normalization factor)

$$
\psi_{\mathbf{k}}(\mathbf{r})=\sum_{L^{\prime}} \sum_{\beta=1}^{N} a_{L^{\prime} \beta}(\mathbf{k}) \psi_{L^{\prime} \beta}(\mathbf{r})
$$

where $\psi_{L^{\prime} \beta}$ are known since they were used to find the phase shifts and $t$ matrix. Outside the spheres the wavefunction can be found from the Green's function equation (see Exercise 16.8)

$$
\psi_{\mathbf{k}}(\mathbf{r})=-\int \mathrm{d} \mathbf{r}^{\prime} G_{0}\left(\varepsilon_{\mathbf{k}}^{n},\left|\mathbf{r}-\mathbf{r}^{\prime}\right|\right) V\left(\mathbf{r}^{\prime}\right) \psi_{\mathbf{k}}\left(\mathbf{r}^{\prime}\right)
$$

which can be evaluated with $\mathbf{r}^{\prime}$ restricted to the interstitial region with boundary conditions on each sphere or with an integral over all space. The integral can be done in different ways, since the free Green's function $G_{0}$ given in Eq. (16.18) is long ranged for energy in the continuum but is exponential for energies below the continuum (see also Section 16.7).

The size of the secular equation depends on the maximum angular momentum needed. In the case of Cu and the elementary transition metals it is sufficient to take $l_{\text {max }}=3$ and therefore the rank of the secular equation is 16 . Note that the basis is much smaller than in the APW (or plane wave) method; the number of functions is determined by the principle angular momenta of the atomic states needed and not by an accuracy criterion for representation of the wavefunctions.

The KKR method has provided some of the most influential and insightful examples of electronic structure calculations. For example, Fig. 16.6 shows the bands of Al [558]. This is an ideal case for the muffin-tin approximation and illustrates the simple physics that emerges from the KKR approach. The results are similar to previous OPW [559] and pseudopotential calculations [504], all showing the free-electron character of the valence

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-16_746_1249_242_213.jpg)
Figure 16.6. Band structure of Al (solid line) calculated by the KKR method [558] compared to free-electron bands (dashed lines). The results can also be easily understood in terms of a weak effective scattering in the plane wave method and the nearly-free-electron approximation, Chapter 12. From [558].

bands. The KKR method conveniently integrates over all plane waves in the analytic Green's function, whereas the plane wave methods make use of the fact that for weak effective scattering only a few plane waves are needed.

KKR is the method used for the first quantitative calculations of the total energy, equilibrium lattice constants, and bulk moduli given in Fig. 2.2; the density of states and Stoner interaction that led to Fig. 2.8; and hosts of other properties, as documented in [104, 673, 682] and many other sources. As a band method, however, it suffers from the same nonlinearity difficulties as the APW method and it is very difficult to extend to a full potential [681]. Therefore, we focus on Green's function approaches where KKR shines.

## KKR Green's Function Equations

The power of the KKR approach is most apparent in its formulation as a Green's function method that determines electronic properties directly from $G_{L L^{\prime}}(\varepsilon)$ in Eq. (16.12). The explicit form in real space for the muffin-tin potential is given by $G_{L L^{\prime}}\left(\varepsilon, \mathbf{R}, \mathbf{R}^{\prime}\right)$ in Eq. (16.24). In a crystal with one atom per cell (the expressions are easily generalized to many atoms per cell) the Green's function is a function only of the relative separation $G_{L L^{\prime}}\left(\varepsilon, \mathbf{R}-\mathbf{R}^{\prime}\right)$. It is most convenient to work with the Fourier transform $G_{L L^{\prime}}(\varepsilon, \mathbf{k})$, which can be evaluated at each $\mathbf{k}$ separately, as follows from the Bloch theorem. Furthermore, in a crystal, the fact that $G_{L L^{\prime}}(\varepsilon, \mathbf{k})$ is only a small matrix, of dimension determined
by $l_{\text {max }}$, is a great advantage: the inversion of such small matrices is of negligible computational cost and the method can be very efficient depending on the effort required to set up the matrices.

The Green's function provides a spectral representation and many physical properties can be calculated as integrals over energy. The basic relations given in Section D. 5 apply to any representation of a Green's function. In particular, the imaginary part of $G(\varepsilon, \mathbf{R})$ provides a local density of states, whereas $G(\varepsilon, \mathbf{k})$ provides a "Bloch spectral representation" i.e., energy- and wavevector-resolved spectra. For example, the density of states per unit energy $\varepsilon$ in the $L$ channel is given by the diagonal part of $G$ with $L=L^{\prime}$,

$$
n_{L}(\varepsilon, \mathbf{k})=-\frac{1}{\pi} \operatorname{Im} G_{L L}(\varepsilon+\mathrm{i} \delta, \mathbf{k})
$$

where $\delta$ is a positive infinitesimal. The total density of states at wavevector $\mathbf{k}$ is given by $n(\varepsilon, \mathbf{k})=\sum_{L} n_{L}(\varepsilon, \mathbf{k})$, which is a sum of delta functions of unity weight at the band energies $\varepsilon=\varepsilon_{i}(\mathbf{k})$.

This Green's function approach provides a convenient of way of calculating the band structure. For example, the Fermi surface can be calculated directly as the locus of states with $\varepsilon_{F}=\varepsilon_{i}(\mathbf{k})$ by calculating only the Green's function at $\varepsilon_{F}$, without calculating the entire band structure. But how does one know $\varepsilon_{F}$ and the potential $V_{\text {eff }}$ from which the phase shifts are derived? The Fermi energy can be fixed by a fast procedure for counting the total number of states up to a given energy, which is given by a formula due to Lloyd [686] that effectively evaluates the integral in Eq. (D.30). The potential is fixed by the density, which is considered next.

The density in real space $n(\mathbf{r})$ can be calculated from the projected density at each site $\mathbf{R}$ due to angular momentum component $L$. The local density of states is

$$
n_{L}(\varepsilon, \mathbf{R})=-\frac{1}{\pi} \operatorname{Im} G_{L L}(\varepsilon+\mathrm{i} \delta, \mathbf{R})
$$

and the total density in the sphere at site $\mathbf{R}$ is

$$
n_{L, \mathbf{R}}=-\frac{1}{\pi} \int_{\infty}^{E_{F}} \mathrm{~d} \varepsilon \operatorname{Im} G_{L L}(\varepsilon+\mathrm{i} \delta, 0)
$$

Another quantity that is easily derived is the sum of eigenvalues of occupied states, which is given by

$$
\sum_{i} \varepsilon_{i}=-\frac{1}{\pi} \sum_{L} \int_{\infty}^{E_{F}} \mathrm{~d} \varepsilon \varepsilon \operatorname{Im} G_{L L}(\varepsilon+\mathrm{i} \delta, 0)
$$

The last equation represents a way of summing the eigenvalues: each eigenvalue leads to a pole in $G(\varepsilon)$, which gives a contribution of $\varepsilon$ to the integral in Eq. (16.35). This provides all the information needed to determine the total energy.

The integrals for total quantities can also be evaluated as contour integrals as shown in Fig. D. 1 and given in Eqs. (D.30)-(D.31), which can be evaluated by a discrete sum over points on the contour in the complex plane. Thus one evaluates the Green's function for chosen complex energies $z$, so that there is no disadvantage due to the nonlinear nature of
the secular equations. Furthermore, wherever the contour is far from any pole, the Green's function $G_{L L}(z, \mathbf{R})$ decays exponentially as a function of distance $|\mathbf{R}|$, so that it can be evaluated using only a cluster of atoms. However, in a metal, the contour necessarily approaches the poles at the Fermi energy, and $G(z, \mathbf{R})$ must exhibit long-range oscillatory behavior in real space (Friedel or Ruderman-Kittel oscillations) due to the sharp cutoff in Fourier space at the Fermi surface.

### 16.4 Alloys and the Coherent Potential Approximation (CPA)

Alloys represent important classes of materials ranging from metallic alloys, where mechanical and magnetic properties can be controlled, to semiconductors where delicate electronic properties are tuned by composition. There are two general types of theoretical approaches: direct calculations on selected supercells and methods that average over disorder. The former approach allows direct studies of effects of short-range order and can be very powerful using clusters and supercell methods (see, e.g., [687] and refences given there). We will concentrate on the coherent potential approximation (CPA), which provides an intuitive, yet accurate, approach when combined with Green's function methods. Such methods are widely applied in crystalline metallic alloys. The formulation that underlies present-day work is due to Soven [688] and Velicky et al. [689], and the earlier work of Lax [690] and Beeby [691].

The general idea of the CPA approach is to formulate an effective (or coherent) potential that, when placed on every site of the alloy lattice, will mimic the electronic properties of the actual alloy. As distinguished from a "virtual crystal approximation" in which the alloy is replaced by an average crystal potential, the coherent potential is derived from averaging the scattering properties of the different atoms embedded in an effective potential as illustrated in Fig. 16.7. Requiring the weighted site average to be the same as the effective potential results in a complex, energy-dependent CPA potential. This is readily treated in terms of Green's functions, in which a complex energy is naturally introduced. An early formulation of the KKR-CPA method, with application to $\mathrm{Cu}-\mathrm{Ni}$ alloys, is that of Stocks, Temmerman, and Gyorffy [692].

As an example of the "band structure" of alloys calculated in the CPA approximation, Fig. 16.8 shows the Bloch spectral function at five $\mathbf{k}$ points along the $\Delta$ direction in a $\mathrm{Cu}_{0.77} \mathrm{Ni}_{0.23}$ alloy [693]. The peaks (which would be delta functions in a perfect crystal) indicate effective bands that are broadened by scattering due to disorder. The energy- and $\mathbf{k}$-dependent broadening is directly related to scattering rates and lengths, and therefore to transport properties such as resistivity [694].

The KKR-CPA equations can also yield total quantities such as energy, pressure, and magnetization in random substitutional alloys [695]. As an example, a calculation of the total energy and magnetic moments in disordered $\mathrm{Fe}_{x} \mathrm{Cu}_{1-x}$ alloys [696] finds an abrupt first-order transition from a nonmagnetic Cu-like phase to a magnetic phase with a change in volume. Alloys can also be treated in a response function approach in which the differences are treated in perturbation theory (see, e.g., [697]).

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-19_292_976_243_347.jpg)
Figure 16.7. Schematic illustration of the averaging over sites in the CPA. The shaded spheres represent an effective average environment and the equation indicates that the average is required to equal the weighted average over sites $A$ and $B$ with concentrations $C_{A}$ and $C_{B}$, each in the same average environment. This leads to the complex CPA potential most readily represented by a Green's function.

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-19_885_1250_829_210.jpg)
Figure 16.8. Bloch spectral function for a $\mathrm{Cu}_{0.77} \mathrm{Ni}_{0.23}$ alloy calculated using the KKR-CPA muffin-tin approximation for potential. The figure shows peaks that disperse, revealing the underlying crystal-like bands and broadening that is due to the disorder treated in the coherent potential approximation (CPA). From [693].

### 16.5 Muffin-Tin Orbitals (MTOs)

Muffin-tin orbitals form a basis of localized augmented orbitals introduced by Andersen [698] in 1971 and subsequently extended into an entire methodology. The goal of the MTO approach is not merely to devise another band structure method but to provide a
satisfying interpretation of the electronic structure of materials in terms of a minimal basis of orbitals. Like local orbital methods, the electronic states are described in a small number of meaningful orbitals; however, unlike those approaches the minimal basis can be accurate because the MTOs are generated from the Kohn-Sham hamiltonian itself.

This section is devoted to the MTO approach, which sets the stage for the linearized LMTO extension [699, 700] (Chapter 17) that exhibits the real power of the approach. The (L)MTO approach has led to many new concepts and methods, for example, "canonical bands" [699, 700], a new approach to the first-principles tight-binding method [701], and many other features. The (L)MTO methodology has been developed in a way most appropriate for close-packed solids, and the descriptions in the literature are often difficult to penetrate because the basic theory is interwoven with approximations and motivational aspects. The goal of the presentation here and in Section 17.6 is to bring out the simplicity of the (L)MTO approach, the ways in which the concepts enhance our understanding, difficulties in its use in structures that are open or have low symmetry, and the power of the method in actual calculations when used appropriately.

An MTO can be understood in terms of a single atomic sphere with a flat potential in all space outside the sphere, which is the subject of Section J. 1 and is closely related to the KKR method. The MTO is defined to be a localized basis function continuous in value and derivative at the sphere boundary. Direct application of the KKR formalism would be to construct an orbital as the energy dependent $\psi_{l}(\varepsilon, r)$ inside the sphere as in Eq. (J.3), and matching the wavefunction outside the sphere, leading to the form $\propto j_{l}(\kappa r)-\tan \left(\eta_{l}(\varepsilon)\right) n_{l}(\kappa r)$ outside the sphere, where $j_{l}$ and $\eta_{l}$ are spherical Bessel and Neumann functions. For negative energies, the Neumann functions are replaced by Hankel functions $h_{l}^{(1)}=j_{l}+i \eta_{l}$, which have the asymptotic form $i^{-l} \mathrm{e}^{-|\kappa| r} /|\kappa| r$, and the Bessel functions are unbounded. Such orbitals are not suitable as basis functions since, at negative energies, they are normalizable only at $\varepsilon$ corresponding to eigenvalues where the coefficient of the Bessel function vanishes.

The insight of Andersen [698] was to reformulate the problem defining a new set of functions that depend separately on $\kappa$ and $\varepsilon$,

$$
\operatorname{MTO}_{L}(\varepsilon, \kappa, \mathbf{r})=i^{l} Y_{L}(\hat{r}) \begin{cases}\psi_{l}(\varepsilon, r)+\kappa \cot \left(\eta_{l}(\varepsilon)\right) j_{l}(\kappa r), & r<S, \\ \kappa n_{l}(\kappa r), & r>S,\end{cases}
$$

where $Y_{L}(\hat{r}) \equiv Y_{l}^{m}(\hat{r})$ and the factor $i^{l}$ is a convenient definition. (This is the same as adopted in [157, 673, 699] and it leads to bound-state functions that are real, as shown in Section J.1). The definition in Eq. (16.36) leads to a very simple envelope function outside the sphere with the property that each MTO basis function is well defined, both inside the sphere (since $j_{l}(\kappa r)$ is regular at the origin) and outside the sphere (since $n_{l}(\kappa r)$ is regular at $\infty$ ). Furthermore, the states are normalizable for all negative energies for any $\kappa$. Of course, the $\chi^{\text {MTO }}$ cannot be eigenstates of a single-muffin-tin potential, but they are basis functions with desirable features for the many-site problem.

The form of Eq. (16.36) contains the seed of an idea that flows through the development of the MTO and LMTO methods: the wavefunction inside the sphere has been modified in a
way that takes into account the presence of neighboring atoms to some approximation. The Bessel function $j_{l}(\kappa r)$ added for $r<S$ is a step toward incorporating into the wavefunction effects due to the neighbors so that a minimal basis of MTO functions $\chi^{\text {MTO }}$ can accurately describe the system.

The equations for many atoms can be derived using an expansion theorem of the form of Eq. (15.1), which expresses the tail of an MTO extending into another sphere in terms of functions centered on that sphere. Fortunately, there is a well-known expansion analogous to Eq. (16.21),

$$
n_{L}(\kappa, \mathbf{r}-\mathbf{R})=4 \pi \sum_{L^{\prime} L^{\prime \prime}} C_{L^{\prime} L^{\prime \prime}}^{L} n_{L^{\prime \prime}}^{*}\left(\kappa, \mathbf{R}-\mathbf{R}^{\prime}\right) j_{L^{\prime}}\left(\kappa, \mathbf{r}-\mathbf{R}^{\prime}\right),
$$

where the $C_{L^{\prime} L^{\prime \prime}}^{L}$ are defined by Eq. (16.23). At this point, the MTO basis can be used for calculation of bands by requiring that the total wave function be a solution both inside and outside the spheres, i.e., that the energy and $\kappa$ be related by $\left(\hbar^{2} / 2 m_{e}\right) \kappa^{2}=\varepsilon-V_{0}$. This amounts to a transformation of the KKR method and would lead to nonlinear equations equivalent to Eqs. (16.27) or (16.28).

However, the MTO approach can also be used in a different way. By treating the $\chi_{L}^{\text {MTO }}(\varepsilon, \kappa, \mathbf{r})$ defined in Eq. (16.36) as functions of $\varepsilon$ and $\kappa$ separately, a judicious fixed choice of $\kappa$ can be used to define a basis that greatly simplifies the problem and yet is accurate for many problems. This has the advantage that one can define structure constants $S_{L^{\prime} L}(\mathbf{R})$ or $S_{L^{\prime} L}(\mathbf{k})$ that depend only on the structure (and the fixed value of $\kappa$ ); in contrast, the KKR "structure constants" are not really constant but are functions of energy $\varepsilon$. This leads to a second hallmark of the (L)MTO approach: developing the method in such a way to take advantage of the fact that an error in the wavefunction leads to higher-order errors in the energy and certain other properties, so that a minimal basis and energy-independent structure constants suffice for accurate calculations.

### 16.6 Canonical Bands

The simplest version of the MTO equations results if the constant $\kappa$ is chosen to be $\kappa=0$, which has been shown to be remarkably accurate for many problems, especially closepacked crystals. The rationale for the freedom to choose $\kappa$ is that it is finally needed only to represent the variation in the wavefunction in the interstitial between the spheres; if there is only a short distance between the spheres (as in a close-packed solid), the wavefunction will be nearly correct because it has the correct value and slope at the sphere boundary. Many of the applications and much of the motivation for the method [699, 700] is associated with the atomic sphere approximation (ASA) in which the Wigner-Seitz sphere around each atom is replaced by a sphere as shown schematically in Fig. 16.9. It is evident that for closepacked cases the distances between spheres are indeed short; since the spheres overlap, the extrapolation to connect the spheres can be either forward or backward.

For $\kappa=0$, the wavefunction satisfies the Laplace equation in the interstitial region, i.e., it is equivalent to the electrostatic potential due to a multipole moment. The form

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-22_555_1020_243_324.jpg)
Figure 16.9. Atomic sphere approximation (ASA) in which the muffin-tin spheres are chosen to have the same volume as the Wigner-Seitz cell, which leads to overlapping spheres. The ASA is often a very good approximation for a close-packed solid. Even some open structures (like diamond) can be formed from close-packed spheres (Exercise 16.11) by including "empty spheres" not centered on atoms [702, 703].

can be derived from the previous equations with the $\kappa \rightarrow 0$ limit of the Bessel and Neumann functions: inside the sphere $j_{l} \rightarrow(r / S)^{l}$ with logarithmic derivative $D=l$ and outside, $n_{l} \rightarrow(r / S)^{-l-1}$ with $D=-l-1$. The MTO in Eq. (16.36) can be written ([157], eq. (1-221); see also [699], eq. (2.2))

$$
\chi_{L}^{\mathrm{MTO}}(\varepsilon, 0, \mathbf{r})=i^{l} Y_{L}(\hat{r}) \psi_{l}(\varepsilon, S) \begin{cases}\frac{\psi_{l}(\varepsilon, r)}{\psi_{l}(\varepsilon, S)}-\frac{D_{l}(\varepsilon)+l+1}{2 l+1}\left(\frac{r}{S}\right)^{l}, & r<S, \\ +\frac{l-D_{l}(\varepsilon)}{2 l+1}\left(\frac{S}{r}\right)^{l+1}, & r>S,\end{cases}
$$

where $D_{l}(\varepsilon)$ the dimensionless logarithmic derivative of $\psi_{l}(\varepsilon, r)$ evaluated at the boundary $r=S$. This function is continuous and differentiable everywhere (Exercise 16.12). The expansion theorem can be found as the $\kappa \rightarrow 0$ limit of Eq. (16.36), which is a well-known multipole expansion,

$$
\begin{aligned}
& {\left[\frac{S}{|\mathbf{r}-\mathbf{R}|}\right]^{l+1} i^{l} Y_{L}(\widehat{\mathbf{r}-\mathbf{R}})} \\
& \quad=4 \pi \sum_{L^{\prime}}\left[\frac{r}{S}\right]^{l^{\prime}} i^{l^{\prime}} Y_{L^{\prime}}(\hat{\mathbf{r}})\left\{\frac{\left(2 l^{\prime \prime}-1\right)!!}{(2 l-1)!!\left(2 l^{\prime}+1\right)!!} C_{L^{\prime} L^{\prime \prime}}^{L}\left[\frac{S}{|\mathbf{R}|}\right]^{l^{\prime \prime}+1} i^{-l^{\prime \prime}} Y_{L^{\prime \prime}}^{*}(\hat{\mathbf{R}})\right\},
\end{aligned}
$$

where $l^{\prime \prime}=l^{\prime}+l$ and $m^{\prime \prime}=m^{\prime}-m$ and the notation (...)!! denotes $1 \times 3 \times 5 \ldots$.
The essential features of the method are illustrated by a crystal with one atom per cell (extension to more atoms per cell is straightforward). Details of the calculation of the structure constants can be found in [699]; we give only limited results to emphasize that
they can be cast in closed form using well-known formulas. The structure factor in $\mathbf{k}$ space is found from the Fourier transform of Eq. (16.37),

$$
\sum_{\mathbf{T} \neq 0} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}}\left[\frac{S}{|\mathbf{r}-\mathbf{T}|}\right]^{l+1} i^{l} Y_{L}(\widehat{\mathbf{r}-\mathbf{T}}) \equiv \sum_{L^{\prime}} \frac{-1}{2\left(2 l^{\prime}+1\right)}\left[\frac{r}{S}\right]^{l^{\prime}} i^{l^{\prime}} Y_{L^{\prime}}(\hat{\mathbf{r}}) S_{L^{\prime} L}(\mathbf{k})
$$

where the factors have been chosen to make $S_{L^{\prime} L}(\mathbf{k})$ hermitian [699]. The result is

$$
S_{L^{\prime} L}(\mathbf{k})=g_{l^{\prime} m^{\prime}, l m} \sum_{\mathbf{T} \neq 0} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}}\left[\frac{S}{|\mathbf{T}|}\right]^{l^{\prime \prime}+1}\left[\sqrt{4 \pi} i^{\prime \prime} Y_{L^{\prime \prime}}(\hat{\mathbf{T}})\right]^{*}
$$

where $g_{l^{\prime} m^{\prime}, l m}$ can be expressed in terms of Gaunt coefficients [699].
An MTO basis function with wavevector $\mathbf{k}$ is constructed by placing a localized MTO on each lattice site with the Bloch phase factor, e.g., for $\kappa=0$,

$$
\chi_{L, \mathbf{k}}^{\mathrm{MTO}}(\varepsilon, 0, \mathbf{r})=\sum_{\mathbf{T}} \mathrm{e}^{\mathrm{ik} \cdot \mathbf{T}} \chi_{L}^{\mathrm{MTO}}(\varepsilon, 0, \mathbf{r}-\mathbf{T})
$$

The wavefunction in the sphere at the origin is the sum of the "head function" (Eq. (16.37) for $r<S$ ) in that sphere plus the tails (Eq. (16.37) for $r>S$ ) from neighboring spheres, and can be written using Eq. (16.38) as

$$
\begin{aligned}
\chi_{L, \mathbf{k}}^{\mathrm{MTO}}(\varepsilon, 0, \mathbf{r})= & \psi_{l}(\varepsilon, r) i^{l} Y_{L}(\hat{r})-\frac{D_{l}(\varepsilon)+l+1}{2 l+1} \psi_{l}(\varepsilon, S)\left(\frac{r}{S}\right)^{l} i^{l} Y_{L}(\hat{r}) \\
& +\frac{l-D_{l}(\varepsilon)}{2 l+1} \psi_{l}(\varepsilon, S) \sum_{L^{\prime}}\left(\frac{r}{S}\right)^{l^{\prime}} \frac{1}{2\left(2 l^{\prime}+1\right)} i^{l^{\prime}} Y_{L^{\prime}}(\hat{r}) S_{L L^{\prime}}(\mathbf{k})
\end{aligned}
$$

The solution can now be found for an eigenstate as a linear combination of the Bloch MTOs Eq. (16.41),

$$
\psi_{\mathbf{k}}(\varepsilon, \mathbf{r})=\sum_{L} a_{L}(\mathbf{k}) \chi_{L, \mathbf{k}}^{\mathrm{MTO}}(\varepsilon, 0, \mathbf{r})
$$

Since the first term on the right-hand side of Eq. (16.41) is already a solution inside the atomic sphere, $\psi_{\mathbf{k}}(\varepsilon, \mathbf{r})$ can be an eigenfunction only if the linear combination of the last two terms on the right-hand side of Eq. (16.41) vanishes - called "tail cancellation" for obvious reasons. This condition can be expressed as

$$
\sum_{L}\left\{S_{L L^{\prime}}(\mathbf{k})-P_{l}(\varepsilon) \delta_{L L^{\prime}}\right\} a_{L}(\mathbf{k})=0
$$

where $P_{l}(\varepsilon)$ is the "potential function" ${ }^{8}$

$$
P_{l}(\varepsilon)=2(2 l+1) \frac{D_{l}(\varepsilon)+l+1}{D_{l}(\varepsilon)-l}
$$

[^4]![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-24_709_704_247_486.jpg)
Figure 16.10. Potential function $P_{l}(\varepsilon)$ (bottom) compared to logarithmic derivative $D_{l}(\varepsilon)$ (top) versus energy. The functions are related by Eq. (16.44) and the energies $\{A, C, B\}$ denote, respectively, the top, center, and bottom of the $n$th band formed from states of angular momentum $l$. The energy $V$ denotes the singularities in $P_{l}(\varepsilon)$ that separate bands. The key point is that $P_{l}(\varepsilon)$ is a smooth function for all energies in the band so that it can be parameterized as discussed in the text. (Taken from a similar figure in [699], ch. 2.)

Equation (16.43) is a set of linear, homogeneous equations for the eigenvectors $a_{L}(\mathbf{k})$ at energies $\varepsilon=\varepsilon_{k}$ for which the determinant of the coefficient matrix vanishes:

$$
\operatorname{det}\left[S_{L L^{\prime}}(\mathbf{k})-P_{l}(\varepsilon) \delta_{L L^{\prime}}\right]=0 .
$$

This is a KKR-type equation, but here $S_{L L^{\prime}}(\mathbf{k})$ does not depend on the energy.
The potential function $P_{l}(\varepsilon)$ contains the same information as the phase shift or the logarithmic derivative $D_{l}(\varepsilon)$, and the relation between them is illustrated in Fig. 16.10. $P_{l}(\varepsilon)$ provides a convenient description of the effective potential in Eq. (16.45) because it varies smoothly as a function of energy in the region of the eigenvalues, as opposed to the logarithmic derivative $D_{l}(\varepsilon)$, which varies strongly and is very nonlinear in the desired energy range. This leads to the simple, but very useful, approximations discussed next.

One of the powerful concepts that arises from Eqs. (16.43) or (16.45) is "canonical bands," which allow one to obtain more insight into the band-structure problem. In essence it is the solution of the problem of states in an atomic sphere (as considered in Section 10.7 but here with nonspherical boundary conditions imposed by the lattice through the structure constants, $S_{L L^{\prime}}(\mathbf{k})$; see also further discussion in Section 17.2). Since the potential function, $P_{l}(\varepsilon)$, does not depend on the magnetic quantum number, $m$, the structure matrix

$$
S_{L L^{\prime}}(\mathbf{k}) \equiv S_{l m, l^{\prime} m^{\prime}}(\mathbf{k})
$$

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-25_718_763_249_457.jpg)
Figure 16.11. Canonical unhybridized bands for an fcc lattice. Comparison with 16.4 , and 16.5 shows that this "canonical band" structure has remarkable similarity to the full calculated bands in an elemental fcc crystal. The canonical bands have only one material-dependent factor that scales the overall band width, and even that parameter can be found from simple atomic calculations as discussed in Sections 10.7 and 17.6. Further improvement can be included through information about the potential function as described in the text. Provided by O. K. Andersen; similar to those in [495, 498, 700] and [699]

contains $(2 l+1) \times(2 l+1)$ blocks. If one neglects hybridization, i.e., if one sets the elements of $S_{L L^{\prime}}(\mathbf{k})$ with $l \neq l^{\prime}$ equal to zero, the unhybridized bands $\left[\varepsilon_{l i}(\mathbf{k})\right]$ are simply found as the $i$ th solution of the equation

$$
\left|P_{l}(\varepsilon)-S_{l m, l m^{\prime}}(\mathbf{k})\right|=0 .
$$

This motivates the idea of "canonical bands," which are defined to be the $2 l+1$ eigenvalues $S_{l, i}(\mathbf{k})$ of the block of the structure constant matrix, $S_{l m, l m^{\prime}}(\mathbf{k})$, for angular momentum $l$. Since each $S_{l, i}(\mathbf{k})$ depends only on the structure, canonical bands can be defined once and for all for any crystal structure. An example of canonical bands is given in Fig. 16.11 for unhybridized s, p, and d canonical bands for an fcc crystal plotted along symmetry lines in the Brillouin zone [495, 498, 699, 700]. Similar bands for bcc and hcp can be found in [493,498,699] and the canonical bands for hcp along $\Gamma-K$ are shown in the left panel of Fig. 17.6. The canonical d densities of states for fcc, bcc, and hcp crystals are given in Fig. 16.12. All the information about the actual material-dependent properties is included in the potential function $P(\varepsilon)$.

The potential function $P(\varepsilon)$ captures information about the bands in a material in terms of a few parameters, all of which can be calculated approximately (often accurately) from

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-26_951_734_245_471.jpg)
Figure 16.12. Canonical densities of states for unhybridized d bands in the fcc, bcc, and hcp structures. The d states dominate the densities of states for transition metals; the DOS s and p bands are not shown. From [498]. (See also [495, 700], and [699].)

very simple models. A simple three-parameter form that contains the features shown in Fig. 16.10 is

$$
P_{l}(\varepsilon)=\frac{1}{\gamma} \frac{\varepsilon-C_{l}}{\varepsilon-V_{l}},
$$

which can be inverted to yield ${ }^{9}$

$$
\varepsilon\left(P_{l}\right)=C_{l}+\gamma\left(C_{l}-V_{l}\right) \frac{P_{l}}{1-\gamma P_{l}} \equiv C_{l}+\frac{\hbar^{2}}{2 \mu S^{2}} \frac{P_{l}}{1-\gamma_{l} P_{l}},
$$

where $\hbar^{2} / 2 \mu S^{2} \equiv \gamma\left(C_{l}-V_{l}\right)$. This expression has an important physical interpretation with $\mu$ an effective mass that sets the scale for the band width. The formulation takes added significance from the fact that $\mu$ can be calculated from the wavefunction in the sphere. It is a matter of algebra (Exercise 16.10) to relate $\mu$ to the linear energy variation of the

[^5]logarithmic derivative $D_{l}(\varepsilon)$ at the band center ( $\varepsilon=C_{l}$, where $D_{l}(\varepsilon)=-l-1$ ), which is then simply related to the value of the wavefunction at the sphere boundary, as given explicitly in Eq. (17.10). This expresses the simple physical fact that the band width is due to coupling between sites, which scales with the value of the wavefunction at the atomic sphere boundary as discussed in Section 10.7. Expressions can also be derived for $\gamma$ [699].

Combining Eqs. (16.49) with (16.47) leads to the unhybridized band structure

$$
\varepsilon_{l i}(\mathbf{k})=C_{l}+\frac{\hbar^{2}}{2 \mu S^{2}} \frac{S_{l, i}(\mathbf{k})}{1-\gamma_{l} S_{l, i}(\mathbf{k})} .
$$

This formulation provides a simple intuitive formulation of the energy bands in terms of the "canonical bands" $S_{l, i}(\mathbf{k})$, with center fixed by $C_{l}$, the width scaled by an effective mass $\mu$, and a distortion parameter $\gamma$ that is very similar to the effect of a nonorthogonal basis. If $\gamma$ is small, the canonical bands illustrated in Fig. 16.11 and the DOS in Fig. 16.12 are a scaled version of the actual bands and DOS of a crystal, thus providing a good starting point for understanding the bands. This can be seen from the remarkable similarity to the calculated bands in Figs. 16.4, and 16.5, and to the tight-binding bands in Fig. 14.9. (Indeed, the real-space interpretation of canonical bands leads to a new formulation of tight-binding described in Section 16.7.) Of course, it is necessary to take into account hybridization to describe the bands fully. This is a notable achievement: essential features of all five d bands are captured by one parameter, the mass in Eq. (16.50). Furthermore, as we shall see in Section 17.6, the mass can be determined simply from an atomic calculation. In addition, the bands can be improved by including the parameter $\gamma$, which distorts the canonical bands as in Eq. (16.50) and which can also be calculated from atomic information. Canonical bands can be used to predict tight-binding parameters, which follows from the structure factors in real space and is discussed in the next section. Finally, many important results for real materials can be found simply using the notions of canonical bands; however, the examples are best deferred to Section 17.8 to include features of the linear LMTO method.

### 16.7 Localized "Tight-Binding," MTO, and KKR Formulations

The subject of this section is transformations to express the MTO and KKR methods in localized form, with the goal of making possible "first-principles" tight-binding (Chapter 14), localized interpretations, linear scaling methods (Chapter 18), and other developments in electronic structure. The original formulations of the KKR method involve structure constants $B_{L L^{\prime}}$ in Eq. (16.22) that oscillate and decay slowly as a function of distance $\left|\mathbf{R}-\mathbf{R}^{\prime}\right|$. For positive energies ${ }^{10}$ the range is so long that it is not possible to make any simple short-range pictures analogous to the local orbital or tight-binding pictures.

The MTO formalism partly remedies this situation to provide a more localized picture. The distance dependence in Eq. (16.37) illustrates the important features that emerge from

[^6]the MTO approach: since $\kappa=0$ has been shown to be a good approximation in many cases and since all the information about interactions between sites is contained in the structure constants, this identity shows the characteristic feature that interactions between orbitals of angular momenta $L=l, m$ and $L^{\prime}=l^{\prime}, m^{\prime}$ decrease as a structure factor
$$
S_{L L^{\prime}}(|\mathbf{R}|) \propto\left[\frac{S}{|\mathbf{R}|}\right]^{l+l^{\prime}+1}
$$

For high angular momenta, the sums converge rapidly, which provides a new formulation of tight-binding [615] in which the matrix elements decay as $(1 / r)^{l+l^{\prime}+1}$ and are derived from the original independent-particle Schrödinger equation.

For $l=0$ and $l=1$, however, this does not lead to a simple picture because the sums do not converge rapidly - in fact there are singularities in the longest-range terms just as for the Coulomb problem. This is not a pleasant prospect for providing a simple physical picture of electronic states! How can the properties of the MTO basis be interpreted to provide a more satisfying picture? The answer lies in the fact that the long-range terms are Coulomb multipole in nature; the distance dependence has inverse power because it is equivalent to the long-range behavior of electrostatic multipole fields. By a unitary transformation that is equivalent to "screening of the multipoles" one can transform to a fully localized tightbinding form for all angular momenta [701]. There are many ways of screening multipoles, all having the effect shown in Fig. 16.13 that contributions from neighboring sites are added with opposite sign to give net exponential decay of the basis function. An example of a transformation choice is given in [701]. The reason that one can transform to a set of exponentially decaying orbitals is not accidental; this properly can be understood using the same ideas as for the construction of Wannier functions. Since the space spanned by the minimal-basis MTO hamiltonian is a finite set of bands, bounded both above and below in energy, the transformations given in Chapter 23 can be used to construct localized functions that span this finite-basis subspace.

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-28_262_1252_1583_210.jpg)
Figure 16.13. Schematic illustration of MTO orbital centered on the site indicated by the dark sphere. Left: a standard MTO. Outside its sphere it decays as a power law with a smooth tail that extends through other spheres. Right: the "screened MTO" that results from linear transformation of the MTOs set of. The essence of the transformation is to add neighboring MTOs with opposite signs as shown; since the tails of the original MTO functions have excatly the same form as the fields due to electronstatic multipoles, the long-range behavior can be "screened" by a linear combination that cancels each multipole field. The transformation to localized functions can also be understood in terms of the construction of Wannier functions; see text.

![](./images/44df8361-7bb5-4476-a31d-0ea57f06b9e2-29_448_910_245_380.jpg)
Figure 16.14. Schematic illustration for creation of localized Green's functions $G_{0}$ in the KKR method. Because of strong repulsive potentials at every site, $G_{0}$ decays exponentially at all energies in the range of the energy bands.

A localized form of KKR also can be generated very straightforwardly, even though the ideas may at first seem counterintuitive. The idea is simply to choose a different reference $G_{0}$ instead of the free propagator equation, (16.18), that satisfies Eq. (16.17). If $G_{0}$ is chosen to be the solution of the Schrödinger equation for a particle in a set of strongly repulsive potentials, as illustrated in Fig. 16.14, then $G_{0}(\mathbf{r})$ is localized for all energies of interest [680]. Simply inserting this into the Dyson equation, (16.12), leads to a localized form for any of the KKR expressions in Section 16.3. The greatest advantage is realized in the Green's function formulation, in which the nonlinearity is not a problem and the equations can be made fully localized. "Order- $N$ " methods have been developed using this approach (see, e.g., [704] and Chapter 18).

There are important advantages of using augmented localized orbitals over the standard tight-binding-like local orbital approach. A basis of fixed local orbitals has the inherent difficulty that the tails of orbitals extending into the neighboring atoms are far from the correct solution - e.g., they do not obey the correct cusp conditions at the nucleus - and a sufficient number of orbitals (beyond a minimal basis) must be used to achieve the "tail cancellation" that is built into the KKR and MTO methods. In general, local orbitals are nonorthogonal, whereas the transformed MTO basis can be made nearly orthogonal [701, 705].

On the other hand there are disadvantages in the use of KKR and MTO methods. The KKR formalism is more difficult to apply to general low-symmetry problems where the potential is not of muffin-tin form. The localized MTO form has been developed for closepacked systems and application to open structures requires care and often introduction of empty spheres (see also Section 17.6). Thus these methods have been applied primarily to close-packed metals and high-symmetry ionic crystals but have not been widely applied to molecules, surfaces, and related systems.

### 16.8 Total Energy, Force, and Pressure in Augmented Methods

Total energies and related quantities are more difficult to calculate than in the pseudopotential method because of the large energies and strong potentials involved. It is especially
important to use appropriate functions for the total energy, such as Eq. (7.22), which was derived by Weinert and coworkers [360] explicitly for APW-type methods. Augmented methods have played a key role in total energy calculations since the 1960s when selfconsistent calculations became feasible, e.g., for KCl [107], alkali metals [108, 109], and Cu [110]. One of the most complete studies was done by Janak, Moruzzi, and Williams [103, 111], who were pioneers in making Kohn-Sham density functional theory a practical approach to computation of the properties of solids. Their results, shown in Fig. 2.2, were calculated using the KKR method. Many other examples of LAPW calculations are given in Chapters 2 and 17.

Straightforward application of the "force (Hellmann-Feynman) theorem" is fraught with difficulty in any all-electron method. The wavefunctions must be described extremely accurately very near the nucleus in order for the derivative to be accurate, and the wavefunctions must be extremely well converged since the force is not a variational quantity. The problem is in the core electrons. In the atom because of spherical symmetry the force on the nucleus must vanish, which is easy to accomplish since the core states are symmetric. If the nucleus is at a site of low symmetry in a molecule or solid, however, the electric field $\mathbf{E}$ at the nucleus and the net force is nonzero. Even though the core electrons are nearly inert, in fact they polarize slightly and transmit forces to the nucleus. It is only by proper inclusion of the polarized core that one arrives at the correct conclusion that the force due to an electric field on an ion (nucleus plus core) is the "screened" force $\mathbf{F}=Z_{\text {ion }} \mathbf{E}$ instead of the "bare" force $\mathbf{F}=Z_{\text {nucleus }} \mathbf{E}$.

Difficult problems associated with calculation of the force on a nucleus can be avoided by the use of force expression that are alternative to the usual force theorem. As emphasized in Appendix I, difficult core-nucleus terms can be explicitly avoided by displacing rigidly the core around each nucleus long with the nucleus. The resulting expressions then involve additional terms due to displacement of the core. Although they lack the elegant simplicity of the original force theorem, they can be much more intuitive and appropriate for actual calculations. A method for calculation of forces and stresses in APW (and LAPW) approaches has been developed by Soler and Williams [706] and by Yu, Singh, and Krakauer [707]. The general ideas, given in Section I.5, involve finding the force on a sphere in terms of the boundary conditions that transmit forces from the plane waves plus Coulomb forces on the charge in the sphere due to charges outside. The expressions can be found by directly differentiating the explicit APW expressions for the energy.

Within the atomic sphere approximation the pressure can be calculated using the remarkably simple expressions given in Section I.3. Only the wavefunctions at the boundary of the sphere are needed. This can be applied in any of the augmented methods, and examples are given using the LMTO approach in Section 17.8.

## SELECT FURTHER READING

Books including augmented methods:
Kübler, J., Theory of Itinerant Electron Magnetism (Oxford University Press, Oxford, 2001).
Singh, D. J., Planewaves, Pseudopotentials, and the APW Method (Kluwer Academic Publishers, Boston, 1994), and references therein.

Multiple scattering and KKR:
Butler, W. H., Dederichs, P. H., Gonis, A., and Weaver, R. L., Applications of Multiple Scattering Theory to Material Science (Materials Reserach Society, Pittsburgh, PA, 1992).

Linear methods and LMTO:
Andersen, O. K., "Linear methods in band theory," Phys. Rev. B 12:3060-3083, 1975.
Andersen, O. K. and Jepsen, O., "Explicit, first-principles tight-binding theory," Physica 91B:317, 1977.

Skriver, H., The LMTO Method (Springer, New York, 1984).

## Exercises

16.1 The basic ideas of the APW method can be illustrated by a one-dimensional Schrödinger equation for which the solution is given in Exercise 4.22. In addition, close relations to pseudopotentials, plane wave, KKR, and MTO methods are brought out by comparison with Exercises 11.14, 12.6, 16.7, and 16.13. Consider an array of potentials $V(x)$ spaced by lattice constant $a ; V(x)$ is arbitrary except that it is assumed to be like a muffin tin composed of nonoverlapping potentials with $V(x)=0$ in the interstitial regions. For actual calculations it is useful to treat the case where $V(x)$ is a periodic array of square wells.
(a) Consider the deep well defined in Exercise 11.14 with width $s=2 a_{0}$ and depth $-V_{0}=-12 H a$. Solve for the two lowest states (analogous to "core" states) using the approximation that they are bound states of an infinite well.
(b) Construct APW functions that are $\mathrm{e}^{\mathrm{i} k x}$ outside the well; inside, the APW is a sum of solutions at energy $\varepsilon$ (as yet unknown) that matches $\mathrm{e}^{\mathrm{i} k x}$ at the boundary. Show that the expansion inside the cell analogous to Eq. (16.2), and the plane wave expansion, analogous to Eq. (16.4), are sums only over two terms, sine and cosine, and give the explicit form for the APW.
(c) Derive the explicit APW hamiltonian for this case. Include the terms from the discontinuity of the derivative. Show that the equation has the simple interpretation of plane waves in the interstitial with boundary conditions due to the well.
(d) Construct a computer code to solve for the eigenvalues and compare to the results of the general method described in Exercise 4.22.
(e) Use the computer code also to treat the shallow square well defined in Exercise 12.6 and compare with the results found there using the plane wave method.
(f) Compare and contrast the APW, plane wave, and the general approach in Exercise 4.22.
16.2 Derive the form for the contribution to the hamiltonian matrix elements from the kink in the wavefunctions given in Eq. (16.8) using Green's identity to transform to a surface integral.
16.3 Derive the identity given in Eqs. (16.21)-(16.23) for the expansion of a spherical wave defined about one center in terms of spherical waves about another center. One procedure is through the use of Eq. (J.1), which is also given in Eq. (16.4).
16.4 Evaluate values for the logarithmic derivatives of the radial wavefunctions for free electrons and compare with the curves shown in Fig. 16.3 for Cu . The expressions follow from Eq. (16.4) (also given in Eq. (J.1)) for zero potential and the functions should be evaluated at the radius $S=2.415 a_{0}$ appropriate for metallic Cu .
16.5 Show that the nearly parabolic $s$ band for Cu in Fig. 16.4 are well approximated by freeelectron values given that Cu has fcc crystal structure with cube edge $a=6.831 a_{0}$. Show also that the states at the zone boundary labeled would be expected to act like p states ( $\mathrm{l}=1$, odd) about each atom. (Quantitative comparisons are given in [157], p. 25).
16.6 As the simplest example of the " $\mathrm{s}-\mathrm{d}$ " hybridization model, derive the bands for a $2 \times 2$ hamiltonian for flat bands crossing a wide band in one dimension: $H_{11}(k)=E_{1}+W \cos (2 \pi k / a)$, $H_{22}(k)=E_{2}$, and $H_{12}(k)=H_{21}(k)=\Delta$. Find the minimum gap, and the minimum direct gap in the bands. Show that the bands have a form resembling the bands in a transition metal.
16.7 The KKR method can be illustrated by a one-dimensional Schrödinger equation, for which the solution is given in Exercise 4.22. See [694] for an extended analysis. Close relations to pseudopotentials, plane wave, APW, and MTO methods are brought out by comparison with Exercises 11.6, 12.6, 16.1, and 16.13. As in Exercise 16.1, the KKR approach can be applied to any periodic potential $V(x)$. The KKR solution is then given by Eq. (16.28) with the structure constants defined in Eq. (16.26). (Here we assume $V(x)$ is symmetric in each cell for simplicity. If it is not symmetric there are also cross terms $\eta^{+-}$.)
(a) The phase shifts are found from the potential in a single cell. In Exercise 11.6 it is shown that the scattering is described by two phase shifts $\eta^{+}$and $\eta^{-}$.
(b) In one dimension the structure constants define a $2 \times 2$ matrix $B_{L, L^{\prime}}(\varepsilon, \mathbf{k})$, with $L=+$, and $L^{\prime}=+,-$. Each term is a sum of exponentials that oscillates and does not converge at large distance. Find physically meaning expressions for $B_{L, L^{\prime}}(\varepsilon, \mathbf{k})$ by adding a damped exponential convergence factor.
(c) Using the relations from Exercise 11.6, show that the KKR equations lead to the same results as the general solution, Eq. (4.49), with $\delta=\eta^{+}+\eta^{-}$and $|t|=\cos \left(\eta^{+}-\eta^{-}\right)$.
16.8 This exercise is to show the relation of the Green's function expression, (16.31), and the Schrödinger equation. This can be done in four steps that reveal subtle features.
(a) Show that application of the free-electron hamiltonian $\hat{H}_{0}$ to both sides of the equation leads to a Schrödinger-like equation but without the eigenvalue. Hint: use the fact that $\hat{H}_{0} G_{0}=\delta\left(\left|\mathbf{r}-\mathbf{r}^{\prime}\right|\right)$.
(b) Show that this is consistent with the Schrödinger equation using the fact that a constant shift in $V$ has no effect on the wavefunction.
(c) Give an auxiliary equation that allows one to find the eigenvalue.
(d) Finally, give the expression for the full Green's function $G$ analogous to Eq. (16.12) from which one can derive the full spectrum of eigenvalues.
16.9 Show that $\chi_{L}^{\text {MTO }}(\varepsilon, 0, \mathbf{r})$, defined in Eq. (16.37), is continuous and has continuous derivative (i.e., $D$ is the same inside and outside) at the boundary $r=S$.
16.10 Find the relation of the mass parameter $\mu$ to the energy derivative $d D(E) / d E$ evaluated at the band center, assuming $P_{l}$ has the simple form given in Eq. (16.48).
16.11 The diamond structure can be viewed as a dense-packed structure of touching spheres with some spheres not filled with atoms. Show this explicitly, starting with the crystal structure shown in Fig. 4.7, and insert empty spheres in the holes in the structure.
16.12 Show that Eq. (16.37) indeed leads to a function that is continuous and has a continuous derivative at its boundary.
16.13 The MTO method can be illustrated by a one-dimensional Schrödinger equation. The purpose of this exercise is to show that the solution in Exercises 4.22 and 16.7 can be viewed as "tail cancellation." (An extended analysis can be found in [708].) This reinterpretation of the equations can be cast in terms of the solutions of the single-cell problem given in Exercise 4.22, $\psi_{l}$ and $\psi_{r}$, which correspond to waves incident from the left and from the right; only the part outside the cell is needed. Consider the superposition of waves inside a central cell at $T=0$ formed by the sum of waves $\psi_{l}(x)$ and $\psi_{r}(x)$ from all other cells at positions $T \neq 0$ with a phase factor $\mathrm{e}^{\mathrm{i} k T}$. Show that the requirement that the sum of waves from all other cells vanishes at any point $x$ in the central cell (i.e., tail cancellation) and leads to the same equations as in Exercises 4.22 and 16.7.


[^0]:    ${ }^{1}$ The factor of $i^{l}$ is introduced to simplify the coefficients that result when matching plane waves that have the factor $i^{l}$; see expansion Eq. (16.4).

[^1]:    ${ }^{3}$ This is exactly the same condition as used in Chapter 11 where the pseudowavefunctions were shown to equal the true wavefunctions in the outer part of the atom, so long as the eigenvalue was the same and the wavefunction satisfied the boundary conditions at the sphere boundary. Furthermore, the specification of the boundary condition in terms of the logarithmic derivative in Eq. (16.11) is the same as in Eqs. (11.20) or (J.5); here the evaluation is done at the muffin-tin boundary and with the assumption that the total potential has the spherical muffin-tin form.
    ${ }^{4}$ Another form slightly different and more convenient for computation is given by Loucks [666], p. 37).

[^2]:    5 The bands are also expected to be predicted qualitatively by density functional theory in LDA or GGA approximations, except that the energies of the filled d states will be too shallow and the $\mathrm{s}-\mathrm{p}$ bands too broad in accordance with experience on many systems.

[^3]:    ${ }^{6}$ As indicated by the form of Eq. (16.13), one must take care to avoid spurious poles appearing in the final solution at the positions of the poles of $G_{0}$.
    ${ }^{7}$ Here $\hbar^{2} / 2 m_{e}$ is explicitly indicated to avoid confusion with references that assume $m_{e}=1 / 2$.

[^4]:    ${ }^{8}$ We use the symbol $P_{l}$ since it is the standard term. It should not be confused with a Legendre polynomial.

[^5]:    ${ }^{9}$ Here we keep the explicit factors of $\hbar$ and $m_{e}$ to indicate energy units clearly and to avoid confusion with notation in the literature.

[^6]:    ${ }^{10}$ If the problem is transformed to complex energies, e.g., in Green's function method, the range can be short. See Section D.5.

