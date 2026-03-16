## 20

## Response Functions: Phonons and Magnons


#### Abstract

Summary Many properties of materials - mechanical, electrostatic, magnetic, thermal, etc. - are determined by the variations of the total energy around the equilibrium configuration, defined by formulas such as Eqs. (2.1)-(2.6). Experimentally, vast amounts of information about materials are garnered from studies of vibration spectra, magnetic excitations, and other responses to experimental probes. This chapter is devoted to the role of electronic structure in providing $a b$ initio predictions and understanding of such properties, through the total energy and force methods described in previous chapters, as well as advances in efficient methods that are now widely used for calculation of response functions. Through these developments, calculation of full phonon dispersion curves, dielectric functions, infrared activity, Raman scattering intensities, magnons, anharmonic energies to all orders, phase transitions, and many other properties have been brought into the fold of practical electronic structure theory.


### 20.1 Lattice Dynamics from Electronic Structure Theory

Total energy and forces are sufficient to treat a vast array of problems including stability of structures, phase transitions, surfaces and interfaces, spin polarization, elastic constants, ab initio molecular dynamics, etc. One can also use such direct methods to calculate all the derivatives of the energy with respect to perturbations, by carrying out full self-consistent calculations for various values of the perturbation, and extracting derivatives from finite difference formulas. For problems like structural phase transitions, the methods are very useful and successful as illustrated for the ferroelectric $\mathrm{BaTi}_{2} \mathrm{O}_{3}$ and the instability in Nb shown in Fig. 2.10.

The first part of this chapter is devoted to ways to use such direct calculations to determine other properties. The approach is often termed the "frozen phonon" method since all calculations are done for static structures. A great advantage of this approach is that it requires only the calculation of energy and forces available in essentially any density
functional calculation. The disadvantage is that it often requires calculations on supercells, which are more computation intensive. ${ }^{1}$

Is it possible to calculate the derivatives directly instead of extracting derivatives from energy differences and forces? The answer is, of course, yes, since it is just a matter of well-known perturbation theory and response functions, for which the general theory is summarized in Appendix D. The subject of the rest of the chapter is developments that allow the perturbation expressions to be rewritten in ways that are much more efficient for actual calculations. In contrast to the frozen phonon methods, the perturbation theory approach makes it possible to calculate phonon frequencies at any $\mathbf{k}$ from a much smaller calculation based on one unit cell.

The starting point is the same in the previous chapter. If the nuclei are treated classically, their dynamics is determined by Newton's equation

$$
M_{I} \frac{\partial^{2} \mathbf{R}_{I}}{\partial t^{2}}=\mathbf{F}_{I}(\mathbf{R})=-\frac{\partial}{\partial \mathbf{R}_{I}} E(\mathbf{R}),
$$

where $\mathbf{R}_{I}$ and $M_{I}$ are the coordinate and mass of nucleus $I$, and $\mathbf{R} \equiv\left\{\mathbf{R}_{I}\right\}$ indicates the set of all the nuclear coordinates. Since nuclear motion is slow compared to typical electron frequencies, it is usually an excellent approximation to neglect any dependence of electronic energies on the velocities of nuclei, i.e., the adiabatic or Born and Oppenheimer (BO) approximation [90] (see Appendix C). All effects of the electrons on the dynamics of the nuclei are completely determined by the forces $\mathbf{F}_{I}(\mathbf{R})$, which are the sum of Coulomb forces between the nuclei and the forces due to the electrons that are determined by the electronic structure.

In the previous chapter the dynamics was determined by molecular dynamics. However, for stable solids at moderate temperature, it is much more useful and informative to cast the expressions in terms of an expansion of the energy $E(\mathbf{R})$ in powers of displacements and external perturbations, as in Eqs. (2.1)-(2.6). Equilibrium positions $\left\{\mathbf{R}_{I}^{0}\right\}=\mathbf{R}^{0}$ are determined by the zero-force condition on each nucleus,

$$
\mathbf{F}_{I}\left(\mathbf{R}^{0}\right)=0 .
$$

Quantum zero-point motion, thermal vibrations, and response to perturbations are described by higher powers of displacements,

$$
C_{I, \alpha ; J, \beta}=\frac{\partial^{2} E(\mathbf{R})}{\partial \mathbf{R}_{I, \alpha} \partial \mathbf{R}_{J, \beta}}, \quad C_{I, \alpha ; J, \beta ; K, \gamma}=\frac{\partial^{3} E(\mathbf{R})}{\partial \mathbf{R}_{I, \alpha} \partial \mathbf{R}_{J, \beta} \partial \mathbf{R}_{K, \gamma}}, \ldots,
$$

where Greek subscripts $\alpha, \beta, \ldots$, indicate cartesian components.
Within the harmonic approximation [91], the vibrational modes at frequency $\omega$ are described by displacements

$$
\mathbf{u}_{I}(t)=\mathbf{R}_{I}(t)-\mathbf{R}_{I}^{0} \equiv \mathbf{u}_{I} \mathrm{e}^{\mathrm{i} \omega t}
$$

[^0]so that Eq. (20.1) becomes for each $I$
$$
-\omega^{2} M_{I} u_{I \alpha}=-\sum_{J \beta} C_{I, \alpha ; J, \beta} u_{J \beta} .
$$

The full solution for all vibrational states is the set of independent oscillators, each with vibrational frequency $\omega$, determined by the classical equation

$$
\operatorname{det}\left|\frac{1}{\sqrt{M_{I} M_{J}}} C_{I, \alpha ; J, \beta}-\omega^{2}\right|=0,
$$

where the dependence on the masses $M_{I}, M_{J}$ has been cast in a symmetric form.
For a crystal, the atomic displacement eigenvectors obey the Bloch theorem, Eqs. (4.32) and (4.33), i.e., the vibrations are classified by $\mathbf{k}$ with the displacements $\mathbf{u}_{s}\left(\mathbf{T}_{\mathbf{n}}\right) \equiv \mathbf{R}_{s}\left(\mathbf{T}_{\mathbf{n}}\right)-\mathbf{R}_{s}^{0}\left(\mathbf{T}_{\mathbf{n}}\right)$ of atom $s=1, S$ in cell $\mathbf{T}_{\mathbf{n}}$ given by

$$
\mathbf{u}_{s, \mathbf{T}_{\mathbf{n}}}=\mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}_{\mathbf{n}}} \mathbf{u}_{s}(\mathbf{k})
$$

Inserting this into Eq. (20.6) leads to decoupling of the equations at different $\mathbf{k}$ (just as for electrons - Exercise 20.2), with frequencies $\omega_{i \mathbf{k}}, i=1,3 S$ called dispersion curves that are solutions of the $3 S \times 3 S$ determinant equation

$$
\operatorname{det}\left|\frac{1}{\sqrt{M_{s} M_{s^{\prime}}}} C_{s, \alpha ; s^{\prime}, \alpha^{\prime}}(\mathbf{k})-\omega_{i \mathbf{k}}^{2}\right|=0,
$$

where the reduced force constant matrix for wavevector $\mathbf{k}$ is given by

$$
C_{s, \alpha ; s^{\prime}, \alpha^{\prime}}(\mathbf{k})=\sum_{\mathbf{T}_{\mathbf{n}}} \mathrm{e}^{\mathrm{i} \mathbf{k} \cdot \mathbf{T}_{\mathbf{n}}} \frac{\partial^{2} E(\mathbf{R})}{\partial \mathbf{R}_{s, \alpha}(0) \partial \mathbf{R}_{s^{\prime}, \alpha^{\prime}}\left(\mathbf{T}_{\mathbf{n}}\right)}=\frac{\partial^{2} E(\mathbf{R})}{\partial \mathbf{u}_{s, \alpha}(\mathbf{k}) \partial \mathbf{u}_{s^{\prime}, \alpha^{\prime}}(\mathbf{k})}
$$

Since the vibrations are independent, quantization is easily included as usual for harmonic oscillators: phonons are the quantized states of each oscillator with energy $\hbar \omega_{i \mathbf{k}}$.

A useful analogy can be made between phonons and electrons described in a tightbinding model. Since the nuclei have three spatial degrees of freedom, the equation of motion, Eq. (20.8), has exactly the same form as Eq. (14.7) for the case with only three states of p symmetry for the electrons. The set of exercises comprising Exercises 20.120.7 is designed to show the relationships, derive phonon dispersion curves in simple cases, and explicitly transform a computational code for the tight-binding algorithm into a code for phonon frequencies with force constants described by models analogous to the parameterized models used in tight-binding methods.

Examples of dispersion curves are given in Figs. 2.11, 20.1, and 20.3. There are three acoustic modes with $\omega \rightarrow 0$ for $\mathbf{k} \rightarrow 0$ and the other $3 S-3$ modes are classified as optic. In insulators, there may be nonanalytic behavior with different limits for longitudinal and transverse modes, illustrated in Figs. 20.1 and 2.11.

The framework is set for derivation of the lattice dynamical properties from electronic structure so long as attention is paid to certain features:

- Careful treatment of the long-range effects due to macroscopic electric fields in insulators
- Formulation of the theory of elasticity in ways that facilitate calculations.

The key aspects of dealing with macroscopic electric fields are treated in Section E.6. In particular, "Born effective charges" $Z_{I, \alpha \beta}^{*}$ are defined in Eq. (E.20) in terms of the polarization per unit displacement in the absence of a macroscopic electric field. Similarly, proper piezoelectric constants $e_{\alpha, \beta \gamma}$ are defined in terms of polarization per unit strain in the absence of a macroscopic electric field. Fortunately, the theory and practical expressions for polarization are well established due to the advances described in Chapter 24. The result is that $C_{s, \alpha ; s^{\prime}, \alpha^{\prime}}(\mathbf{k})$ can be divided into terms that are analytic, as in the small $\mathbf{k}$ limit, plus nonanalytic contributions that can be treated exactly in terms of $Z_{I, \alpha \beta}^{*}$ and $e_{\alpha, \beta \gamma}$. These considerations are required in any approach that aspires to be a fundamental theory of lattice properties.

The basic definition of stress is given in Eq. (G.4) and the elastic constants, defined in Eq. (G.5), are the subject of many volumes [285, 300, 806, 807]. The important point to emphasize here is that both the electrons and the nuclei contribute directly to the stress, for which there are rigorous formulations (Appendix G). The expressions use the (generalized) force theorem, which depends on the requirement that all internal degrees of freedom be at their minimum energy values. This includes the electron wavefunctions and the nuclear positions, which are described by "internal strains" that are determined by the zero-force condition, Eq. (G.13). In many simple cases, e.g., in Bravais lattices, the force is zero by symmetry for zero internal strain; however, in general, the positions of the nuclei in a strained crystal are not fixed by symmetry, and any fundamental calculations of elastic properties must find the internal strains from the theory.

### 20.2 The Direct Approach: "Frozen Phonons," Magnons

The most direct approach is simply to calculate the total energy and/or forces and stresses as a function of the position of the nuclei, i.e., "frozen phonons," using any of the expressions valid for the electronic structure. Then the relevant quantities are defined by numerical derivatives for the force $\mathbf{F}$ and polarization $\mathbf{P}$ as a function of displacement $\mathbf{R}$

$$
C_{I, \alpha ; J, \beta} \approx-\frac{\Delta \mathbf{F}_{I, \alpha}}{\Delta \mathbf{R}_{J, \beta}},\left.\quad Z_{I, \alpha \beta}^{*}|e| \approx \frac{\Delta \mathbf{P}_{\alpha}}{\Delta \mathbf{R}_{I, \beta}}\right|_{\mathbf{E}_{\mathrm{mac}}},
$$

and for stress $\sigma$ and polarization $\mathbf{P}$ as a function of strain $\epsilon$,

$$
C_{\alpha \beta ; \gamma \delta} \approx-\frac{\Delta \sigma_{\alpha \beta}}{\Delta u_{\alpha \beta}},\left.\quad e_{\alpha \beta \gamma} \approx \frac{\Delta \mathbf{P}_{\alpha}}{\Delta \epsilon_{\alpha \beta}}\right|_{\mathbf{E}_{\mathrm{mac}}} .
$$

Such calculations are widely used since they require no additional computational algorithms; furthermore, this is the method of choice in cases where there are large displacements since the energy is automatically found to all orders. The direct approach played a critical role in early work, for example [171] and [808], where it was shown that phonons in materials (other than the sp-bonded metals) could be derived from the electronic structure.

An example of the energy versus displacements of atoms is shown in the left side of Fig. 2.10 for displacement of Ti atoms in $\mathrm{BaTiO}_{3}$. The origin corresponds to atoms
in centrosymmetric positions in perovskite structure shown in Fig. 4.8. If the energy had increased with displacement the structure would be stable and the curvature would determine the frequency of an optic mode. In this case there is an instability and at the lowest-energy state it has a finite displacement. One could describe this in terms of perturbation theory with fourth (and higher)-order anharmonic terms; however, it is convenient to calculate the energy directly for finite displacement. Then it is just an example of relaxation to the find the stable structure, a feature in all present-day codes. As pointed out in Section 2.9 the polarization can be calculated using Berry phases (Chapter 24), which is explicitly constructed as a method to calculate polarization directly to all orders.

## Supercells: Phonons and Instabilities

One can also treat displacements that increase the size of the cell, i.e., supercells illustrated in Fig. 13.1. Transition metals are an excellent example where electronic structure calculations of "frozen phonon" energies can provide much information on the total bonding and the states near the Fermi energy that couple strongly to the phonons. The phonon energies for many transition metals have been shown to be well described, e.g., in [809] and [170], by calculations at wavevectors $\mathbf{k}$ along high-symmetry directions. For example, there is an interesting anomaly in the longitudinal frequency for $\mathbf{k}=\left(\frac{2}{3}, \frac{2}{3}, \frac{2}{3}\right)$ in the bcc structure crystals Mo and Nb . This is a precursor to the phase transition that actually occurs in Zr , which has bcc structure only above $1,100 \mathrm{~K}$ [157, 170]. The left side of Fig. 2.10 shows the calculated energy versus displacement for this phonon for $\mathrm{Mo}, \mathrm{Nb}$, and Zr . The inset shows the displacements that correspond to the " $\omega$ phase" with each third plane undisplaced, and the other two planes displaced to form a more dense bilayer. The LDA calculations agree well with the phonon frequencies in Mo and Nb and with the observed low-temperature structure of all three elements. The transition to bcc at high temperature is believed to be an effect of entropy, since it is well known that many metals have bcc structure at high temperature. A simple explanation is provided by the general arguments of Heine and Samson [810] that such a superlattice can occur for a $1 / 3$ filled d band, which is the case for Zr. The electronic structure calculations provide a more complete picture, showing that this is not a delicate Fermi surface effect but is a combination of effects of $\mathrm{s}-\mathrm{p}$ states and directional (covalent) d bonding involving states in a range around the Fermi energy [170].

## Supercells and Dispersion Curves

It is also possible [608-610] to derive full-dispersion curves from the direct force calculations using supercells as illustrated in Fig. 13.1 for a zinc blende crystal. Any given phonon corresponds to a displacement of planes of atoms perpendicular to the wavevector $\mathbf{k}$, as shown on the left-hand side of the figure. All the information needed in Eq. (20.10) for all phonons with a given direction $\hat{\mathbf{k}}$ can be derived by displacing each inequivalent plane of atoms and calculating the force of all the atoms [608]. One must do a separate calculation for each inequivalent plane and each inequivalent displacement (four in the case shown in Fig. 13.1, for longitudinal and transverse displacement of Ga and As ). If the size of

![](./images/ff0e914c-2d9f-4ed2-948b-28a636134739-06_767_794_245_439.jpg)
Figure 20.1. Dispersion curves for phonons in GaAs in the [100] direction calculated using the frozen phonon method. The supercell used for the calculation is a longer version of the cell shown in Fig. 13.1 with displacements as indicated that are either transverse or longitudinal. The same methods are used for interfaces, sublattices, and surfaces treated by making periodic cells, which illustrates the versatility of supercells for many problems. From [608].

the supercell exceeds twice the range of the forces, then all terms can be identified with no ambiguities. The results [608] for GaAs are shown in Fig. 20.1, compared with experiment. These are early calculations that used a semiempirical local pseudopotential. It is satisfying that better agreement with experiment has been found in more recent calculations [181, 811] shown in Fig. 2.11, which use $a b$ initio norm-conserving potentials and the response function method (Section 20.3). The inverse dielectric constant $\epsilon^{-1}$ and the effective charges $Z_{I}^{*}$ can also be calculated from the change in the potentials due to an induced dipole layer [608].

The practical advantage of this approach is immediately apparent from the fact that exactly the same methods can be used to calculate the properties of superlattices and interfaces. As shown in the middle figure of Fig. 13.1, a superlattice can be created by the theoretical alchemy of replacing Ga with Al in part of the supercell. Furthermore, the same methods apply directly to surfaces where part of the supercell is vacuum. This is illustrated on the right-hand side figure of Fig. 13.1, where the surface may undergo massive reconstruction beyond any perturbation expansion.

Another instructive example of the use of supercells is the calculation [611] of the inverse dielectric constant $\epsilon^{-1}(\mathbf{k})$ by imposing a periodic electrostatic potential of wavevector $\mathbf{k}$, i.e., a "frozen field." If the atoms are held fixed, the resulting potential leads to the static electronic inverse dielectric constant $\epsilon_{0}^{-1}(\mathbf{k})$; if the atoms are allowed to displace so that

![](./images/ff0e914c-2d9f-4ed2-948b-28a636134739-07_544_560_247_557.jpg)
Figure 20.2. Dispersion curves for magnons in Fe: open circles are experimental points, compared to the dark circles that are theoretical results [161] calculated using the Berry phase approach [160]. Triangles show magnon energies for an alloy with $12 \% \mathrm{Si}$. From [161].

the forces are zero, one finds the result including the lattice contribution $\epsilon_{\infty}^{-1}(\mathbf{k})$. In each case, the $\mathbf{k} \rightarrow 0$ limit can be found by extrapolation from a few values of $\mathbf{k}$ and using the fact that $\epsilon_{\infty}^{-1}(\mathbf{k}) \propto k^{2}$ at small $\mathbf{k}$.

Spin excitations, or magnons, can be treated in the same way by calculating the energy of "frozen magnons." But how does one freeze the magnetization? Unlike phonons, magnetization is a continuous function of position that must be calculated. An elegant way of doing this is to generalize the Berry phase idea, Section 24.3, for electric polarization to the magnetic case of Niu and Kleinman [160]. An example of results [161] from this method for Fe , calculated using plane waves with a pseudopotential, are shown in Fig. 20.2: this shows excellent agreement with experiment. In this case, a supercell is not needed: because the magnon is a spiral excitation, the excitation obeys a generalized Bloch theorem [159] in which each cell is rotated equally with respect to its neighbors. See also Fig. 20.4.

### 20.3 Phonons and Density Response Functions

Historically, ${ }^{2}$ the first approach for calculation of phonons was based on response functions: since all harmonic force constants, elastic constants, etc. involve only second derivatives of the energy, they can be derived using second-order perturbation theory. Furthermore, this builds on the fact that in many cases one can calculate small changes more accurately than the total energy itself. This section is devoted to the formulation, which is directly useful for simple cases and leads up to the efficient methods of Section 20.4.

The general expressions for the response to an external perturbation $V_{\text {ext }}(\mathbf{r})$ that varies with parameters $\lambda_{i}$ (where $\lambda$ denotes the position of an atom, the strain, etc.) are

[^1]$$
\begin{aligned}
\frac{\partial E}{\partial \lambda_{i}} & =\frac{\partial E_{I I}}{\partial \lambda_{i}}+\int \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \lambda_{i}} n(\mathbf{r}) \mathrm{d} \mathbf{r} \\
\frac{\partial^{2} E}{\partial \lambda_{i} \partial \lambda_{j}} & =\frac{\partial^{2} E_{I I}}{\partial \lambda_{i} \partial \lambda_{j}}+\int \frac{\partial^{2} V_{\mathrm{ext}}(\mathbf{r})}{\partial \lambda_{i} \partial \lambda_{j}} n(\mathbf{r}) \mathrm{d} \mathbf{r}+\int \frac{\partial n(\mathbf{r})}{\partial \lambda_{i}} \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \lambda_{j}} \mathrm{~d} \mathbf{r}
\end{aligned}
$$
plus higher-order terms. The first equation is just the force (Hellmann-Feynman) theorem, which involves only the external potential and the unperturbed density. The first two terms in the second equation involve only the unperturbed density; however, the last term requires knowledge of $\partial n(\mathbf{r}) / \partial \lambda_{i}$. Using the chain rule, the last term can be written in symmetric form [180]
$$
\int \frac{\partial V_{\mathrm{ext}}\left(\mathbf{r}^{\prime}\right)}{\partial \lambda_{i}} \frac{\partial n(\mathbf{r})}{\partial V_{\mathrm{ext}}\left(\mathbf{r}^{\prime}\right)} \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \lambda_{j}} \mathrm{~d} \mathbf{r} \mathrm{~d} \mathbf{r}^{\prime}=\int \frac{\partial V_{\mathrm{ext}}\left(\mathbf{r}^{\prime}\right)}{\partial \lambda_{i}} \chi\left(\mathbf{r}, \mathbf{r}^{\prime}\right) \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \lambda_{j}} \mathrm{~d} \mathbf{r} \mathrm{~d} \mathbf{r}^{\prime},
$$
where $\chi$ is the density response function, Eq. (D.9). The expressions may be written in either $\mathbf{r}$ or $\mathbf{q}$ space as in Eq. (D.10), and may be expressed in terms of inverse dielectric function using the relation $\epsilon^{-1}=1+V_{C} \chi$, given explicitly in Eq. (E.15).

Following this approach, expressions for any second derivative of the energy can be found in two steps: using a relation like Eq. (D.14),

$$
\chi=\chi^{0}\left[1-\chi^{0} K\right]^{-1}, \quad \text { or } \quad \chi^{-1}=\left[\chi^{0}\right]^{-1}-\mathrm{K},
$$

that expresses $\chi$ in terms of the kernel $K$ in Eq. (D.13) and the noninteracting response function $\chi^{0}$. In turn, $\chi^{0}$ is given by Eqs. (D.6)-(D.8), which are derived from standard expressions of perturbation theory in terms of sums over the entire spectrum of eigenstates. The form that is most useful for comparison with Green's function methods is Eq. (D.5), repeated here,

$$
\Delta n(\mathbf{r})=2 \sum_{i=1}^{N} \sum_{j=N+1}^{\infty} \psi_{i}^{*}(\mathbf{r}) \psi_{j}(\mathbf{r}) \frac{\left\langle\psi_{j}\right| \Delta V_{\mathrm{KS}}\left|\psi_{i}\right\rangle}{\varepsilon_{i}-\varepsilon_{j}} .
$$

The formulation of response functions in Eqs. (20.14) and (20.15) is extremely fruitful in cases where the response function can be approximated by a simple form. For example, calculations of phonon dispersion curves in sp-bonded metals are well described by $\chi$ from the homogeneous electron gas, i.e., the static Lindhard dielectric function $\epsilon^{-1}(|\mathbf{q}|)$, Eq. (5.38), which is an analytic, scalar function of the one-dimensional magnitude $|\mathbf{q}|$. The foundation for the theory is the nearly-free-electron approximation with the ions represented by weak pseudopotentials [506,508]. ${ }^{3}$

However, the approach is very difficult for accurate calculations on general materials. There are two primary problems: The quantities involved are six-dimensional functions $\epsilon^{-1}\left(\mathbf{q}, \mathbf{q}^{\prime}\right)$, which become large matrices $\epsilon_{\mathbf{G G}^{\prime}}^{-1}(\mathbf{k})$ in crystals. Furthermore, calculation of each of the entries in the matrix involves a sum over the BZ of the filled and empty bands

[^2](as in Eqs. (D.6)-(D.8)) up to some energy sufficient for convergence. This is a very difficult task that we will not belabor; the next section describes a much more efficient approach.

### 20.4 Green's Function Formulation

An alternative, much more effective, approach is "density-functional perturbation theory" (DFPT) [181, 811, 813, 814], which builds upon earlier classic works [52, 815]. Instead of calculation of the inverse dielectric function $\epsilon_{\mathbf{G G}^{\prime}}^{-1}(\mathbf{k})$, which gives the response to all possible perturbations, DFPT is designed to calculate the needed response to a particular perturbation. Instead of the standard perturbation theory sums over empty states, the expressions are transformed into forms that involve only the occupied states, which can be calculated using efficient electronic structure methods. This leads to two related types of expressions: (1) self-consistent equations for the response function in terms of the change in the wavefunctions to a given order, or (2) variational expressions in which the calculation of a response at any given order of perturbation is cast as a problem of minimizing a functional defined at that order. The theory can be applied to any order (Sections D. 1 and D.6) but the main ideas can be seen in the lowest-order linear response.

The formulation can be understood by first returning to the fundamentals of perturbation theory. In terms of the wavefunctions, the first-order change in density is

$$
\Delta n(\mathbf{r})=2 \operatorname{Re} \sum_{i=1}^{N} \psi_{i}^{*}(\mathbf{r}) \Delta \psi_{i}(\mathbf{r})
$$

where $\Delta \psi_{i}(\mathbf{r})$ is given by first-order perturbation theory as

$$
\left(H_{\mathrm{KS}}-\varepsilon_{i}\right)\left|\Delta \psi_{i}\right\rangle=-\left(\Delta V_{\mathrm{KS}}-\Delta \varepsilon_{i}\right)\left|\psi_{i}\right\rangle
$$

Here $H_{\mathrm{KS}}$ is the unperturbed Kohn-Sham hamiltonian, $\Delta \varepsilon_{i}=\left\langle\psi_{i}\right| \Delta V_{\mathrm{KS}}\left|\psi_{i}\right\rangle$ is the firstorder variation of the KS eigenvalue, $\varepsilon_{i}$, and the change in the effective potential is given by

$$
\begin{aligned}
\Delta V_{\mathrm{KS}}(\mathbf{r}) & =\Delta V_{\mathrm{ext}}(\mathbf{r})+e^{2} \int \mathrm{~d} \mathbf{r}^{\prime} \frac{\Delta n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}+\int \mathrm{d} \mathbf{r}^{\prime} \frac{\mathrm{d} V_{\mathrm{xc}}(\mathbf{r})}{\mathrm{d} n\left(\mathbf{r}^{\prime}\right)} \Delta n\left(\mathbf{r}^{\prime}\right) \\
& \equiv \Delta V_{\mathrm{ext}}(\mathbf{r})+\int \mathrm{d} \mathbf{r}^{\prime} K\left(\mathbf{r}, \mathbf{r}^{\prime}\right) \Delta n\left(\mathbf{r}^{\prime}\right)
\end{aligned}
$$

The kernel $K\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ is pervasive in the response function formalism and is discussed further in Chapter 9 and Appendix D (where $K$ is given in $\mathbf{k}$ space in Eq. (D.13)). It incorporates the effects of Coulomb interaction and exchange and correlation to linear order through $f_{\mathrm{XC}}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\mathrm{d} V_{\mathrm{Xc}}(\mathbf{r}) / \mathrm{d} n\left(\mathbf{r}^{\prime}\right)$.

The standard perturbation theory approach is to expand Eq. (20.17) in eigenfunctions of the zero-order Schrödinger equation, which leads to Expression (20.15). Although this approach is not efficient because it requires knowledge of the full spectrum of the zeroorder hamiltonian and sums over many unoccupied states, nevertheless, the expressions are useful for demonstration of important properties. In particular, Eq. (20.15) shows that
$\Delta n(\mathbf{r})$ involves only mixing of the unoccupied ( $j>N$ ) space into the space of the occupied $(i \leq N)$ states because contributions from the occupied states cancel in pairs in the sum.

It is much more effective for actual calculations to view the set of equations, Eqs. (20.16)(20.18), as a self-consistent set of equations for $\Delta n$ and $\Delta V_{\mathrm{KS}}$ to linear order in $\Delta V_{\text {ext }}$. It might appear that there is a problem since the left-hand side of Eq. (20.17) is singular because the operator has a zero eigenvalue, for which the eigenvector is $\psi_{i}$. However, as shown in Eq. (20.15), the response of the system to an external perturbation only depends on the component of the perturbation that couples the manifold occupied states with the empty states. The desired correction to the occupied orbitals can be obtained from Eq. (20.17) by projecting the right-hand side onto the empty-state manifold,

$$
\left(H_{\mathrm{KS}}-\varepsilon_{i}\right)\left|\Delta \psi_{i}\right\rangle=-\hat{P}_{\mathrm{empty}} \Delta V_{\mathrm{KS}}\left|\psi_{i}\right\rangle
$$

where the projection operator is given by (see also Eq. (23.18))

$$
\hat{P}_{\mathrm{occ}}=\sum_{i=1}^{N}\left|\psi_{i}\right\rangle\left\langle\psi_{i}\right| ; \quad \hat{P}_{\mathrm{empty}}=1-\hat{P}_{\mathrm{occ}}
$$

In practice, if the linear system is solved by the conjugate-gradient or any other iterative method in which orthogonality to the occupied-state manifold is enforced during iteration, there is no problem with the zero eigenvalue.

The basic algorithm for DFPT consists of solving the set of linear equation (20.19) for $\Delta \psi_{i}$ given the definition in Eq. (20.20) and expression (20.18) for $\Delta V_{\mathrm{KS}}$ in terms of $\Delta n$, which is given by Eq. (20.16). Since $\Delta n$ is a function of the set of occupied $\Delta \psi_{i}$, this forms a self-consistent set of equations. Any of the efficient iterative methods (Appendix M) developed for electronic structure problems can be applied to reach the solution by iteration. This is a more efficient approach than the standard "textbook" approach outlined following Eq. (20.13): the equivalent of the matrix inverse in Eq. (19.14) is accomplished by the selfconsistent solution for $\Delta \psi_{i}$ and $\Delta V_{\mathrm{KS}}$, and the sum over excited states is accomplished by mixing of the unoccupied space into the occupied space using Eq. (20.19).

### 20.5 Variational Expressions

Variational expressions in perturbation theory have a long history, for example the ingenious use of the variational principle for accurate solution of the two-electron problem by Hylleraas [52] in the 1930s. The ideas have been brought to the fore by Gonze [816, 817] (see also [181]), who has derived expressions equivalent to the Green's function formulas of Sections 20.4 and 20.6. The variational perspective provides an alternative approach for solution of electronic structure problems and is one that involves minimization rather than solution of linear equations.

The basic idea of variational expressions in perturbation theory is very simple. If a system has internal degrees of freedom, which are free to adjust (within any constraints that they must obey), then the static response to an external perturbation requires that all internal degrees of freedom adjust to minimize the energy. Exercise 20.5 gives a simple example of
a system made up of two harmonic springs with an internal degree of freedom. In electronic structure the perturbation is a change in the external potential $\Delta V_{\text {ext }}$, and the internal degrees of freedom are the density $n(\mathbf{r})$ or the wavefunctions $\psi_{i}$. These can be viewed as independent variables, i.e., one can define a functional $E^{(m)}[n]$ or $E^{(m)}\left[\psi_{i}\right]$ valid at a chosen order $m$ of perturbation theory, and the correct solution is found by minimizing the functional. Just as for the variational principle that leads to the Schrödinger or Kohn-Sham equations, the energy, $\psi_{i}$ and $n(\mathbf{r})$ are determined by minimizing the energy.

The variational principle in perturbation theory can be derived directly from the same variational principle that leads to the Schrödinger or Kohn-Sham equations, but the new point is that it is applied only to a given order. For example, to second order in the changes $\Delta V_{\text {ext }}=V_{\text {ext }}-V_{\text {ext }}^{0}$ and $\Delta n=n-n^{0}$, the Kohn-Sham energy functional, Eqs. (7.5) or (7.20), can be written in a form similar to Eq. (7.21) with the addition of terms involving $\Delta V_{\text {ext }},{ }^{4}$

$$
\begin{aligned}
E^{(2)}\left[V_{\mathrm{ext}}, n\right]= & E\left[V_{\mathrm{ext}}^{0}, n^{0}\right]+\int \mathrm{d} \mathbf{r} n^{0}(\mathrm{~d} \mathbf{r}) \Delta V_{\mathrm{ext}}(\mathbf{r}) \\
& +\frac{1}{2} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime}\left[\frac{\delta^{2} E}{\delta V_{\mathrm{ext}}(\mathbf{r}) \Delta n\left(\mathbf{r}^{\prime}\right)}\right] \Delta V_{\mathrm{ext}}(\mathbf{r}) \Delta n\left(\mathbf{r}^{\prime}\right) \\
& +\frac{1}{2} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime}\left[\frac{\delta^{2} E}{\delta n(\mathbf{r}) \delta n\left(\mathbf{r}^{\prime}\right)}\right] \Delta n(\mathbf{r}) \Delta n\left(\mathbf{r}^{\prime}\right)
\end{aligned}
$$

where derivatives are evaluated at the minimum energy solution with $V_{\text {ext }}^{0}$ and $n^{0}$. There is no term involving $\Delta V_{\text {ext }}^{2}$ since the functional is linear in $V_{\text {ext }}$. The first intergral in Eq. (20.21) is the force theorem. The middle line is linear in $\Delta n$. The last line is quadratic in $\Delta n$ and is always positive since the functional is minimum at $V_{\text {ext }}^{0}$ and $n^{0}$. Minimization of the functional is, in principle, merely a matter of minimizing a quadratic form, no harder than the harmonic springs in Exercise 20.5. However, practical solutions must be done in terms of the wavefunctions $\psi_{i}$ since the functionals of density are unknown.

In terms of the orbitals, Expression (20.21) becomes [181] (omitting terms that are zero for $\Delta V_{\text {ext }}=0$ )

$$
\begin{aligned}
E^{(2)}\left[V_{\mathrm{ext}}, \psi_{i}\right]= & E\left[V_{\mathrm{ext}}^{0}, \psi_{i}^{0}\right] \\
& +\frac{1}{2} \sum_{i} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime}\left[\frac{\delta^{2} E}{\delta V_{\mathrm{ext}}(\mathbf{r}) \delta \psi_{i}\left(\mathbf{r}^{\prime}\right)}\right] \Delta V_{\mathrm{ext}}(\mathbf{r}) \Delta \psi_{i}\left(\mathbf{r}^{\prime}\right) \\
& +\frac{1}{2} \sum_{i j} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime}\left[\frac{\delta^{2} E}{\delta \psi_{i}(\mathbf{r}) \delta \psi_{j}\left(\mathbf{r}^{\prime}\right)}\right] \Delta \psi_{i}(\mathbf{r}) \Delta \psi_{j}\left(\mathbf{r}^{\prime}\right)
\end{aligned}
$$

[^3]where
$$
\begin{aligned}
{\left[\frac{\delta^{2} E}{\delta V_{\mathrm{ext}}(\mathbf{r}) \delta \psi_{i}\left(\mathbf{r}^{\prime}\right)}\right] } & =\psi_{i}^{0}(\mathbf{r}) \delta\left(\mathbf{r}-\mathbf{r}^{\prime}\right) \\
{\left[\frac{\delta^{2} E}{\delta \psi_{i}(\mathbf{r}) \delta \psi_{j}\left(\mathbf{r}^{\prime}\right)}\right] } & =H_{\mathrm{KS}}^{0}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)+K\left(\mathbf{r}, \mathbf{r}^{\prime}\right) \Delta \psi_{i}(\mathbf{r}) \Delta \psi_{j}\left(\mathbf{r}^{\prime}\right) \Delta \psi_{i}(\mathbf{r}) \Delta \psi_{j}\left(\mathbf{r}^{\prime}\right)
\end{aligned}
$$
with $K$ defined in Eq. (20.18); see also Eq. (D.13).
The solution can be found directly by minimizing Eq. (20.22) with respect to $\Delta \psi_{i}$ subject to the orthonormality constraint
$$
\left\langle\psi_{i}^{0}+\Delta \psi_{i} \mid \psi_{j}^{0}+\Delta \psi_{j}\right\rangle=\delta_{i j}
$$

The steepest descent directions for $\Delta \psi_{i}$ are found by writing out the equations, which also show equivalence to the Green's function method [181]. Minimizing $E^{(2)}\left[V_{\text {ext }}, \psi_{i}\right]$ in Eq. (20.22) with condition Eq. (20.25) leads to

$$
H_{\mathrm{KS}}^{0} \Delta \psi_{i}-\sum_{j} \Lambda_{i j} \Delta \psi_{j}=-\left(\Delta V_{\mathrm{eff}}-\varepsilon_{i}\right) \psi_{i}+\sum_{j} \Lambda_{i j} \Delta \psi_{j},
$$

where $\Delta V_{\text {eff }}$ is the change in total effective potential given to the second order by Eq. (20.18). Taking matrix elements with respect to the orbitals, one recovers (Exercise 20.10) the form given in Eq. (20.19).

### 20.6 Periodic Perturbations and Phonon Dispersion Curves

The DFPT equations have a marvelous simplification for the case of a crystal with a perturbation at a given wavevector, e.g., a phonon of wavevector $\mathbf{k}_{p}$, with displacements given by Eq. (20.7). To linear order, the change in density, external potential, and KohnSham potential all have Fourier components only for wavevectors $\mathbf{k}_{p}+\mathbf{G}$, where $\mathbf{G}$ is any reciprocal lattice vector. The expressions can be written

$$
\begin{aligned}
\Delta V_{\mathrm{ext}}(\mathbf{r}) & =\Delta v_{\mathrm{ext}}^{\mathbf{k}_{p}}(\mathbf{r}) \mathrm{e}^{\mathrm{i} \mathbf{k}_{p} \cdot \mathbf{r}}=\sum_{\mathbf{T}} \frac{V_{s}\left[\mathbf{r}-\mathbf{R}_{s}(\mathbf{T})\right]}{\partial \mathbf{R}_{s}(\mathbf{T})} \mathrm{e}^{-\mathrm{i} \mathbf{k}_{p} \cdot\left(\mathbf{r}-\mathbf{R}_{s}(\mathbf{T})\right)} \mathbf{u}_{s}\left(\mathbf{k}_{p}\right) \mathrm{e}^{\mathrm{i} \mathbf{k}_{p} \cdot \mathbf{r}}, \\
\Delta V_{\mathrm{KS}}(\mathbf{r}) & =\Delta v_{\mathrm{KS}}^{\mathbf{k}_{p}}(\mathbf{r}) \mathrm{e}^{\mathrm{i} \mathbf{k}_{p} \cdot \mathbf{r}}, \\
\Delta n(\mathbf{r}) & =\Delta n^{\mathbf{k}_{p}}(\mathbf{r}) e^{\mathrm{i} \mathbf{k}_{p} \cdot \mathbf{r}} .
\end{aligned}
$$

The wavefunction for an electron at wavevector $\mathbf{k}_{e}$ is modified to linear order only by mixing of states with wavevector $\mathbf{k}_{e}+\mathbf{k}_{p}$, so that Eq. (20.19) becomes

$$
\left(H_{\mathrm{KS}}^{\mathbf{k}_{e}}-\varepsilon_{i}^{\mathbf{k}_{e}}\right)\left|\Delta \psi_{i}^{\mathbf{k}_{e}+\mathbf{k}_{p}}\right\rangle=-\left[1-\hat{P}_{\mathrm{Occ}}^{\mathbf{k}_{e}+\mathbf{k}_{p}}\right] \Delta V_{\mathrm{KS}}^{\mathbf{k}_{p}}\left|\psi_{i}^{\mathbf{k}_{e}}\right\rangle .
$$

To linear order the density is given by

$$
\Delta n^{\mathbf{k}_{p}}(\mathbf{r})=2 \sum_{\mathbf{k}_{e}, i} u_{\mathbf{k}_{e}, i}^{*}(\mathbf{r}) \Delta u_{\mathbf{k}_{e}+\mathbf{k}_{p}, i}(\mathbf{r})
$$

where $u$ denotes the periodic part of the Bloch function, and the Kohn-Sham potential is

$$
\Delta v_{\mathrm{KS}}^{\mathbf{k}_{p}}(\mathbf{r})=\Delta v_{\mathrm{ext}}^{\mathbf{k}_{p}}(\mathbf{r})+\int \mathrm{d} \mathbf{r}^{\prime}\left[\frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}+f_{\mathrm{xc}}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)\right] \Delta n^{\mathbf{k}_{p}}(\mathbf{r}) .
$$

The DFPT algorithm for the calculation of the response to any periodic external perturbation $\Delta v_{\text {ext }}^{\mathbf{k}_{p}}(\mathbf{r})$ is the solution of the set of equations Eqs. (20.29)-(20.31). Note that the calculation involves only pairs of wavevectors, $\mathbf{k}_{e}$ and $\mathbf{k}_{e}+\mathbf{k}_{p}$ for the electrons, in the linear equation (20.29), and a sum over all $\mathbf{k}_{e}$ and filled states $i$ for the self-consistency. The calculations can be done using the same fast Fourier transform (FFT) techniques that are standard in efficient plane wave methods (Chapter 13 and Appendix M): Eqs. (20.29) and (20.31) can be solved partly in $\mathbf{r}$ space and partly in $\mathbf{k}$ space, and Eq. (20.30) is most efficiently done in $\mathbf{r}$ space, with transformations done by FFTs.

Figure 2.11 shows the results of DFPT calculations for the phonon dispersion curves of GaAs [182], done using the local approximation (LDA). Similar results are found for other semiconductors and it is clear that agreement with experiment is nearly perfect. Calculations have been done for many other materials, and an example is the set of results presented in Fig. 20.3 for the phonon dispersion curves of a set of metals. From top to bottom, these represent increasing electron-phonon interactions and increasing complexity of the Fermi surface. The LDA is essentially perfect for Al (as expected!), but the GGA provides a significant improvement in Nb where there is a soft phonon (see discussion in Section 20.2 and calculation for Nb in Fig. 2.10). Similar results are found for many materials using many methods, finding agreement with experimental frequencies within $\approx 5 \%$ is typical.

### 20.7 Dielectric Response Functions, Effective Charges

Electric fields present a special problem due to long-range Coulomb interaction. This arises in any property in which electric fields are intrinsically involved, e.g., dielectric functions, effective charges, and piezoelectric constants. One approach is to formulate the theory of response functions at finite wavelengths and take limits analytically [180, 819]. Is it possible to generate an efficient Green's function approach that involves only the infinite wavelength $\mathbf{q}=0$ limit? The answer is yes, but only with careful analysis. The problem is that the limit corresponds to a homogeneous electric field with potential $V_{\text {ext }}(\mathbf{r})=\mathbf{E} \cdot \mathbf{r}$, which leads to an ill-defined hamiltonian in an extended system; see Chapter 24. The saving grace is that perturbation theory in the electric field involves matrix elements of the form of Eq. (20.15) or Eq. (20.19), i.e., only off-diagonal matrix elements of the perturbing potential between eigenfunctions of the unperturbed hamiltonian. These matrix elements are well defined even for a macroscopic electric field, which can be seen by rewriting them in terms of the commutator between $\mathbf{r}$ and the unperturbed hamiltonian,

$$
\left\langle\psi_{i}\right| \mathbf{r}\left|\psi_{j}\right\rangle=\frac{\left\langle\psi_{i}\right|[H, \mathbf{r}]\left|\psi_{j}\right\rangle}{\epsilon_{i}-\epsilon_{j}}, \quad i \neq j
$$

![](./images/ff0e914c-2d9f-4ed2-948b-28a636134739-14_1213_924_247_377.jpg)
Figure 20.3. Phonon dispersion curves calculated for the metals $\mathrm{Al}, \mathrm{Pb}$, and Nb compared with experiment [818]. The agreement using the LDA is excellent for Al and progressively worse for the other metals, which are further from the homogeneous gas, where GGA functionals improve the agreement. The dips in the phonon dispersion curves for Pb and Nb indicate strong electron-phonon interactions and sensitivity to Fermi surface features that are important for superconductivity in these elements.

If the total potential acting on the electrons is local, the commutator is simply proportional to the momentum operator,

$$
[H, \mathbf{r}]=-\frac{\hbar^{2}}{m_{e}} \frac{\partial}{\partial \mathbf{r}}=i \frac{\hbar}{m_{e}} \mathbf{p} .
$$

For nonlocal potentials, the commutator involves an explicit contribution from the potential [547, 548] as defined in Eq. (11.72). Littlewood [820] has used the momentum form for the matrix elements to derive expressions for the dielectric functions of crystals in
terms of the periodic Bloch functions, and the explicit iterative Green's function algorithm corresponding to Eqs. (20.16)-(20.20) is given in [181].

An example of the application of the ideas is the calculation of effective charges $Z^{*}$ in ionic insulators. Linear response calculations have been done for many materials, e.g., the ferroelectric perovskite materials with formula unit $\mathrm{ABO}_{3}$. Anomalously large effective charges of the B atoms and the O atoms moving along the line joining them have been found and interpreted as resulting from covalency [821, 822]. Results are essentially the same as those given in table 24.1 from [823] using the Berry phase method.

### 20.8 Electron-Phonon Interactions and Superconductivity

Electron-phonon coupling plays a crucial role in the theory of transport and superconductivity in solids, and there are excellent sources showing the relation of the microscopic interactions to the phenomena [824-826]. In particular, the basic quantity in the Eliashberg [827] equations for phonon-mediated superconductivity is $\alpha^{2} F(\omega)$, where $F(\omega)$ is a phonon density of states and $\alpha$ denotes an average over all phonons of energy $\omega$.

The quantities that can be derived from the underlying electronic structure are the electron bands and density of states, the phonon dispersion curves and density of states, and electron-phonon coupling (Appendix C). The matrix element for scattering an electron from state $i \mathbf{k}$ to $j \mathbf{k}+\mathbf{q}$ while emitting or absorbing a phonon $v \mathbf{q}$ with frequency $\omega$ is given by [825]

$$
g_{i \mathbf{k} ; j \mathbf{k}+\mathbf{q}}(v)=\frac{1}{\sqrt{2 M \omega_{\nu \mathbf{q}}}}\langle i \mathbf{k}| \Delta V_{\nu \mathbf{q}}|j \mathbf{k}+\mathbf{q}\rangle,
$$

where $M$ is the (mode-dependent) reduced mass and $1 / \sqrt{\left(2 M \omega_{\nu \mathbf{q}}\right)}$ is the zero-point phonon amplitude.

For scattering at the Fermi surface, one can define the dimensionless coupling to the phonon branch $v$, where $v=1, \ldots, 3 S$, with $S$ the number of atoms per cell, by [825]

$$
\lambda_{\nu}=\frac{2}{N(0)} \sum_{\mathbf{q}} \frac{1}{\omega_{\nu \mathbf{q}}} \sum_{i j \mathbf{k}}\left|g_{i \mathbf{k} ; j \mathbf{k}+\mathbf{q}}(\nu)\right|^{2} \delta\left(\varepsilon_{i \mathbf{k}}\right) \delta\left(\varepsilon_{j \mathbf{k}+\mathbf{q}}-\varepsilon_{i \mathbf{k}}-\omega_{\nu \mathbf{q}}\right),
$$

where $N(0)$ is the electronic density of states per spin at the Fermi energy and $\omega_{\nu \mathbf{q}}$ is the energy of phonon $v$ with the wavevector $\mathbf{q}$. The energy of electron band $i$ with the wavevector $\mathbf{k}$ is $\varepsilon_{i \mathbf{k}}$ and $g_{i \mathbf{k} ; j \mathbf{k}+\mathbf{q}}(\nu)$ is the matrix element between the states $i \mathbf{k}$ and $j \mathbf{k}+\mathbf{q}$ due to the induced potential when phonon $\nu \mathbf{q}$ is excited. The delta functions restrict the electron scattering to the Fermi surface.

A key quantity in the theory is the induced potential $\Delta V$ per unit displacement needed in the matrix element Eq. (20.34). To linear order it is given by

$$
\Delta V_{\nu \mathbf{q}}=\frac{\partial V}{\partial u_{\nu \mathbf{q}}}=\sum_{I \alpha} X_{\nu \mathbf{q}}(I \alpha) \frac{\partial V}{\partial u_{I \alpha}}
$$

where $u_{\nu \mathbf{q}}$ is the phonon normal coordinate and $X_{\nu \mathbf{q}}(I \alpha)$ is the eigenvector of the dynamical matrix, Eq. (20.8), expressed in terms of displacements $u_{I \alpha}$ of the nucleus $I$ in the $\alpha$ direction. Since the phonon is low frequency, the potential $\Delta V_{\nu \mathbf{q}}$ is a "screened potential," i.e., the electrons react to contribute to the effective potential.

There are four general methods for calculation of the matrix elements with the properly screened $\Delta V_{\nu \mathbf{q}}$ :

- Displacement of rigid atomic-like potentials, e.g., muffin-tin potentials [828]. The justification is that the coupling is primarily local [829] and the potential is very much like a sum of atomic potentials, which has been shown to be appropriate for transition metals, even with displaced atoms. The same ideas apply for displacement of any effective total potential, such as empirical pseudopotentials.
- Calculations using a general expression for the screening, which can be conveniently expressed in Fourier space as

$$
\frac{\partial V(\mathbf{q}+\mathbf{G})}{\partial u_{\nu \mathbf{q}}}=\sum_{\mathbf{G}^{\prime}} \epsilon^{-1}\left(\mathbf{q}+\mathbf{G}, \mathbf{q}+\mathbf{G}^{\prime}\right) \frac{\partial V_{\mathrm{ion}}\left(\mathbf{q}+\mathbf{G}^{\prime}\right)}{\partial u_{\nu \mathbf{q}}}
$$

following the definition of $\epsilon^{-1}$, given, e.g., above Eq. (20.14). This is particularly convenient when one can use a simple model for $\epsilon^{-1}$, e.g., the Lindhard function, Eq. (5.38), which is appropriate for simple metals. In general, however, it is more efficient to use the Green's function approach.

- Methods using direct calculation of the linear order screened potential [181, 830]. This can be done conveniently using the Green's function technique described in Sections 20.4 and 20.6. As is clear from Eq. (20.37), one of the by-products of the calculation of phonons is the screened $\Delta V_{\nu \mathbf{q}}$ itself. This needs to be done for all relevant phonons needed for the integral over the Fermi surface.
- Self-consistent "frozen phonon" calculations [718, 831]. As described in Section 20.2, the calculations involve $V$ directly to all orders in the displacement. The linear change in potential can be extracted as the linear fit to calculations with finite displacements of the atoms. Alternatively, one can find the mixing of wavefunctions from which the matrix elements can be found. The "frozen phonons" can be determined on a grid of $\mathbf{k}$ points and interpolated to points on the Fermi surface.

The full calculation requires a double sum over the Brillouin zone and determination of the matrix elements $g$ at each pair of points and for each phonon $v$.

### 20.9 Magnons and Spin Response Functions

Response functions for spin excitations are the fundamental quantities measured in spindependent neutron scattering from solids just as lattice dynamical response functions are the fundamental quantities measured in lattice dynamics experiments. Since spin dynamics is strongly affected by magnetic order and excitations tend to be damped by coupling to

![](./images/ff0e914c-2d9f-4ed2-948b-28a636134739-17_688_761_247_454.jpg)
Figure 20.4. Spin response spectral functions $\operatorname{Im} \chi(\mathbf{q}, \omega)$ for Fe . The line shows the dispersion corresponding to the maximum in $\operatorname{Im} \chi$ compared with experimental values (points). Compare also with Fig. 20.2. Note that the excitations broaden at higher frequency and momentum. From [833].

the electron degrees of freedom, the form of the spectral function $\operatorname{Im} \chi(\mathbf{q}, \omega)$ is often of importance. For many years the basic formalism has been known and calculations have been done with standard Green's function techniques and realistic band structures of metals, e.g., in the work of Cooke [832] and many more recent calculations. The method is based on a simple extension of the random-phase approximation of the relevant Green's function equation and an interpolation formalism for treating wavefunctions and matrix elements.

There is a Green's function method that generalizes the approach used for phonons to treat spin response functions [833]. The formulas are closely related and involve spin density instead of number density. An example of results for Fe using the LMTO approach is shown in Fig. 20.4. Comparison with Fig. 20.2 shows good agreement with calculations done using the Berry phase method and the plane wave pseudopotential method. In addition, however, the results in Fig. 20.4 show the full spectral function, with its broadening increasing rapidly for wavevectors near the zone boundary, in qualitative agreement with experiment. Such work has been extended to alloys using the KKR-CPA method and for the treatment of disorder within linear response theory [697].

## SELECT FURTHER READING

Classic text for lattice vibrations.
Born, M. and Huang, K., Dynamical Theory of Crystal Lattices (Oxford University Press, Oxford, 1954).

Theory of phonons in terms of the electronic resonse functions.
Pick, R., Cohen, M. H., and Martin, R. M., "Microscopic theory of force constants in the adiabatic approximation," Phys. Rev. B 1:910-920, 1970.

Review of density-functional perturbation theory and Green's Function methods.
Baroni, S., de Gironcoli, S., Dal Corso, A., and Giannozzi, P., "Phonons and related crystal properties from density-functional perturbation theory," Rev. Mod. Phys. 73:515-562, 2000.

## Exercises

20.1 See many excellent problems (and solutions) on phonons in the book by Mihaly and Martin [598].
20.2 Show that the Bloch theorem for phonons follows from exactly the same logic as for electrons treated in the local orbital representation (Exercise 14.3).
20.3 By comparing Expressions (14.7) and (20.8), show that the equations for phonons are exactly the same as a tight-binding formulation in which there are three states of p symmetry for each atom, corresponding to the three degrees of freedom for the atomic displacements. Show explicitly the correspondence of the terms of the two problems, especially the fact that the eigenvalue in the electron problem corresponds to the square of the frequency in the phonon problem.
20.4 This exercise is to explain a salient difference in the tight-binding electron and the phonon problems. The force constant has the property of translational invariance; show that the fact that the total energy does not change if all the atoms are displaced uniformly leads to the relation $\sum_{J} C_{I, \alpha ; J, \beta}=0$. This condition can be used to fix the self-term $C_{I, \alpha ; I, \beta}$ so that, unlike the electron tight-binding problem, the on-site term is not an independent variable. In addition, show that this means that there are three zero frequency phonon modes at $\mathbf{k}=0$.
20.5 The simplest model for phonons is the central force model in which the energy is a function only of the distance between the nearest neighbors. Find expressions for a force constant $C_{I, \alpha ; J, \beta}$ using the definition as a second derivative of the energy expressed as a sum of pair terms $E=\sum_{I<J} E_{I J}\left(\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|\right)$. Show that the resulting expressions are equivalent to a tight-binding problem of electron p states, Exercise 14.11, with the $t_{p p \pi}$ matrix elements equal to zero.
20.6 Find expressions for phonon dispersion curves respectively in elemental simple cubic and fcc crystals using the simplest model for phonons, a nearest-neighbor central potential model with energy given by $E=\frac{1}{2} \sum_{I<J} K\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|^{2}$, where $J$ is restricted to nearest neighbor. Show the relation to tight-binding equations for $p$ bands in Exercise 14.11 as explicit examples of the relationship given in Exercises 20.3-20.5.
(a) Show that there are two dispersion curves that have zero frequency for all $k$ in simple cubic but not in fcc crystals. Explain why this instability occurs in a simple cubic crystal in a central potential model.
(b) There is a corresponding result in the tight-binding model for p bands in a simple cubic crystal if the only nonzero matrix element is $t_{p p \sigma}$ between nearest neighbors. Show that in this case there are two bands with no dispersion.
20.7 Computational exercise: using the properties established in Exercises 20.3-20.5, construct a computer program (or use a tight-binding code that is available) to evaluate phonon frequencies in a model analogous to a tight-binding model for electrons.
20.8 Why is there no term involving $\partial^{2} n /\left(\partial \lambda_{i} \partial \lambda_{j}\right)$ in the expression for $\partial^{2} E /\left(\partial \lambda_{i} \partial \lambda_{j}\right)$ in Eq. (20.12)?
20.9 Derive Eq. (20.15), which is the same as from the basic perturbation expressions (D.4) and (20.16). In particular, show that all contributions involving $i$ and $j$, both occupied, vanish in the expression for the change in the density.
20.10 Show that Eq. (20.19) follows from Eq. (20.26) by taking matrix elements of the equation.
20.11 This is an example of the variational principle in perturbation theory. Consider a system composed of three points $x_{0}, x_{1}, x_{2}$ in a line connected by two springs. The energy is $E=\frac{1}{2} k_{1}\left(x_{1}-x_{0}\right)^{2}+\frac{1}{2} k_{2}\left(x_{2}-x_{1}\right)^{2}$. Suppose forces $f=f_{0}=-f_{2}$ are applied to the two ends.
(a) Identify the functional $F\left[f, x_{1}\right]$ valid for all $f$ and $x_{1}$.
(b) If the middle position $x_{1}$ is free to move, calculate the change in position $x_{1}-x_{0}$ and total length $x_{2}-x_{0}$ as a function of $f$.
(c) See Exercise D. 7 for extension to nonlinear springs.


[^0]:    ${ }^{1}$ In fact, the $a b$ initio molecular dynamics method called "Born-Oppenheimer" in the previous chapter use this approach; at each step the forces are calculated with the electrons in their ground state for the positions of the nuclei at that step.

[^1]:    ${ }^{2}$ See references 2-13 in [180].

[^2]:    ${ }^{3}$ The formulas in terms of density response functions do not apply directly to nonlocal pseudopotentials, but appropriate modifications can be made [812].

[^3]:    ${ }^{4}$ Spin indices are omitted for simplicity and the subscript "KS" is omitted because the expressions apply more generally.

