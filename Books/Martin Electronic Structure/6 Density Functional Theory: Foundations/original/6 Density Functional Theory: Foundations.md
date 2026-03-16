# PART II <br> DENSITY FUNCTIONAL THEORY <br> 6 <br> Density Functional Theory: Foundations 

E pluribus unum.

## Summary

The fundamental tenet of density functional theory (DFT) is that any property of a system of many interacting particles can be viewed as a functional of the ground state density $n_{0}(\mathbf{r})$; that is, one scalar function of position $n_{0}(\mathbf{r})$, in principle, determines all the information in the many-body wavefunctions for the ground state and all excited states. The existence proofs for such functionals, given in the original works of Hohenberg and Kohn and of Mermin, are disarmingly simple. However, they provide no guidance whatsoever for constructing the functionals, and no exact functionals are known for any system of more than one electron. Density functional theory would remain a minor curiosity today if it were not for the construction of an auxiliary system by Kohn and Sham, which has provided a way to make useful, approximate functionals for real systems of many electrons. The subject of this chapter is density functional theory as a methodology for many-body systems; Chapter 7 describes the Kohn-Sham auxiliary independent-particle system and the formulation of the self-consistent Kohn-Sham equations; and Chapters 8 and 9 deal with widely used approximations for the exchange-correlation functional. Following chapters in this volume are devoted to algorithms for actual calculations, and applications to problems in atomic, molecular, and condensed matter physics.

### 6.1 Overview

The modern formulation of density functional theory originated in a famous paper by Hohenberg and Kohn in 1964 [83]. These authors showed that a special role can be assigned to the density of particles in the ground state of a quantum many-body system: the density can be considered to be a "basic variable" - i.e., that all properties of the system can be considered to be unique functionals of the ground-state density. Shortly thereafter in 1965,

Mermin [326] extended the Hohenberg-Kohn arguments to finite temperature canonical and grand canonical ensembles. Although the finite temperature extension has not been widely used, it illuminates both the generality of density functional theory and the difficulty of realizing the promise of exact density functional theory. Also in 1965 appeared the other classic work by Kohn and Sham [84], whose formulation of density functional theory has become the basis of much of present-day methods for treating electrons in atoms, molecules, and condensed matter.

In present-day literature, "density functional theory" and "DFT" usually mean the Kohn-Sham formulation, often blurring the distinction between Hohenberg-Kohn and Kohn-Sham. Here they are divided into different chapters to clearly distinguish between them. The goals of the chapters on density functional theory are to elucidate the fundamental ideas and current practices, to give the reader sufficient background to use density functional theory intelligently for real problems, and to expose potential pitfalls and possible avenues for future developments. The present chapter is concerned with the reformulation of the theory in interacting electrons in terms of functionals of the density. Sections 6.2 and 6.3 are devoted to background and the famous existence proofs by Hohenberg and Kohn; however, the less famous derivation by Levy and Lieb in Section 6.4 provides greater insight into the meaning of the functionals. Section 6.5 describes some of the extensions including the Mermin functional at nonzero temperature, current functionals, and issues related to electric polarization. Finally, some of the many intricacies and difficulties associated with density functional theory, as formulated by Hohenberg and Kohn, are the topics of Sections 6.6 and 6.7.

### 6.2 Thomas-Fermi-Dirac Approximation

The original density functional theory of quantum systems is the Thomas-Fermi method proposed in 1927 in separate papers by Thomas [327] and Fermi [328]. Although their approximation is not accurate enough for present-day electronic structure calculations, the approach illustrates the way density functional theory works. The approximation was to treat the kinetic energy of the system of electrons as an explicit functional of the density, idealized as noninteracting electrons in a homogeneous gas with density equal to the local density at any given point. Both Thomas and Fermi neglected exchange and correlation among the electrons; however, this was extended by Dirac [329] in 1930, who formulated the local approximation for exchange (see Sections 5.2 and 8.3) still in use today. This leads to the energy functional for electrons in an external potential $V_{\text {ext }}(\mathbf{r})$ :

$$
\begin{aligned}
E_{\mathrm{TF}}[n]= & C_{1} \int \mathrm{~d}^{3} r n(\mathbf{r})^{(5 / 3)}+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r}) \\
& +C_{2} \int \mathrm{~d}^{3} r n(\mathbf{r})^{4 / 3}+\frac{1}{2} \int \mathrm{~d}^{3} r \mathrm{~d}^{3} r^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
\end{aligned}
$$

where the first term is the local approximation to the kinetic energy with $C_{1}= \frac{3}{10}\left(3 \pi^{2}\right)^{(2 / 3)}=2.871$ in atomic units (see Section 5.2), the third term is the local exchange with $C_{2}=-\frac{3}{4}\left(\frac{3}{\pi}\right)^{1 / 3}$ (Eq. (5.15) for the case of equal up and down spins) and the last term
is the classical electrostatic Hartree energy. (In Appendix H, improved approximations for inhomogeneous systems including gradients are given.)

The ground state density and energy can be found by minimizing the functional $E[n]$ in Eq. (6.1) for all possible $n(\mathbf{r})$ subject to the constraint on the total number of electrons

$$
\int \mathrm{d}^{3} r n(\mathbf{r})=N
$$

Using the method of Lagrange multipliers (Exercise 6.1), the solution can be found by an unconstrained minimization of the functional

$$
\Omega_{\mathrm{TF}}[n]=E_{\mathrm{TF}}[n]-\mu\left\{\int \mathrm{d}^{3} r n(\mathbf{r})-N\right\},
$$

where the Lagrange multiplier $\mu$ is the Fermi energy. For small variations of the density $\delta n(\mathbf{r})$, the condition for a stationary point is ${ }^{1}$

$$
\begin{aligned}
& \int \mathrm{d}^{3} r\left\{\Omega_{\mathrm{TF}}[n(\mathbf{r})+\delta n(\mathbf{r})]-\Omega_{\mathrm{TF}}[n(\mathbf{r})]\right\} \rightarrow \\
& \int \mathrm{d}^{3} r\left\{\frac{5}{3} C_{1} n(\mathbf{r})^{2 / 3}+V(\mathbf{r})-\mu\right\} \delta n(\mathbf{r})=0
\end{aligned}
$$

where $V(\mathbf{r})=V_{\text {ext }}(\mathbf{r})+V_{\text {Hartree }}(\mathbf{r})+V_{x}(\mathbf{r})$ is the total potential. Since Eq. (6.4) must be satisfied for any function $\delta n(\mathbf{r})$, it follows that the functional is stationary if and only if the density and potential satisfy the relation

$$
\frac{1}{2}\left(3 \pi^{2}\right)^{(2 / 3)} n(\mathbf{r})^{2 / 3}+V(\mathbf{r})-\mu=0
$$

Extensions to treat inhomogeneous systems more accurately require going beyond the local density approximation for the kinetic energy density. For example, the Weizsacker [330] correction, $\frac{1}{4}(\nabla n(\mathbf{r}))^{2} / n(\mathbf{r})$, which is in essence a gradient correction in the same spirit as the gradient corrections in more modern density functionals in Section 8.5. In Section H. 1 it is shown that this can be viewed as the kinetic energy density of a system of bosons with density $n(\mathbf{r})$, and a more accurate expression for fermions always increases the kinetic energy at each point $\mathbf{r}$.

The attraction of density functional theory is evident by the fact that one equation for the density is remarkably simpler than the full many-body Schrödinger equation that involves $3 N$ degrees of freedom for $N$ electrons. However, the Thomas-Fermi-type approach starts with approximations that are too crude, missing essential physics and chemistry, such as shell structures of atoms and binding of molecules [331]. Thus it falls short of the goal of a useful description of electrons in matter.

### 6.3 The Hohenberg-Kohn Theorems

The approach of Hohenberg and Kohn is to formulate density functional theory as an exact theory of many-body systems. The formulation applies to any system of interacting particles

[^0]![](./images/1c0364fd-5946-44bc-86c9-16d5c52eedb4-04_247_488_247_592.jpg)
Figure 6.1. Schematic representation of Hohenberg-Kohn theorem. The smaller arrows denote the usual solution of the Schrödinger equation where the potential $V_{\text {ext }}(\mathbf{r})$ determines all states of the system $\Psi_{i}(\{\mathbf{r}\})$, including the ground state $\Psi_{0}(\{\mathbf{r}\})$ and ground-state density $n_{0}(\mathbf{r})$. The long arrow labeled "HK" denotes the Hohenberg-Kohn theorem, which completes the circle.

in an external potential $V_{\text {ext }}(\mathbf{r})$, including any problem of electrons and fixed nuclei, where the hamiltonian can be written ${ }^{2}$

$$
\hat{H}=-\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2}+\sum_{i} V_{\mathrm{ext}}\left(\mathbf{r}_{i}\right)+\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|} .
$$

Density functional theory is based on two theorems first proved by Hohenberg and Kohn [83]. Here we first present the theorems and the proofs along with discussion of the consequences; Section 6.4 contains the alternative formulation of Levy and Lieb, which is more general and gives a more intuitive definition of the functional. The relations established by Hohenberg and Kohn are illustrated in Fig. 6.1 and can be started as follows:

- Theorem I. For any system of interacting particles in an external potential $V_{\text {ext }}(\mathbf{r})$, the potential $V_{\text {ext }}(\mathbf{r})$ is determined uniquely, except for a constant, by the ground-state particle density $n_{0}(\mathbf{r})$.
Corollary I. Since the hamiltonian is thus fully determined, except for a constant shift of the energy, it follows that the many-body wavefunctions for all states (ground and excited) are determined. Therefore all properties of the system are completely determined given only the ground-state density $n_{0}(\mathbf{r})$.
- Theorem II. A universal functional for the energy $E[n]$ in terms of the density $n(\mathbf{r})$ can be defined, valid for any external potential $V_{\text {ext }}(\mathbf{r})$. For any particular $V_{\text {ext }}(\mathbf{r})$, the exact ground-state energy of the system is the global minimum value of this functional, and the density $n(\mathbf{r})$ that minimizes the functional is the exact ground-state density $n_{0}(\mathbf{r})$.
Corollary II. The functional $E[n]$ alone is sufficient to determine the exact ground-state energy and density. In general, excited states of the electrons must be determined by other means. Nevertheless, the work of Mermin (Section 6.5) shows that thermal equilibrium properties such as specific heat are determined directly by the free-energy functional of the density.

[^1]These assertions are so encompassing and the proofs are so simple that it is crucial for any practitioner in the field to understand the basis of the theorems and the limits of the logical consequences.

## Proof of Theorem I: Density As a Basic Variable

The proofs of the Hohenberg-Kohn theorems are disarmingly simple. Consider first Theorem I, using the general expressions given in Eqs. (3.8) and (3.9) for density and energy in terms of the many-body wavefunction. Suppose that there were two different external potentials $V_{\text {ext }}^{(1)}(\mathbf{r})$ and $V_{\text {ext }}^{(2)}(\mathbf{r})$ that differ by more than a constant and that lead to the same ground-state density $n(\mathbf{r})$. The two external potentials lead to two different hamiltonians, $\hat{H}^{(1)}$ and $\hat{H}^{(2)}$, which have different ground-state wavefunctions, $\Psi^{(1)}$ and $\Psi^{(2)}$, that are hypothesized to have the same ground-state density $n_{0}(\mathbf{r})$. (It is straightforward to find different $\Psi_{\text {S }}$ with the same density, as discussed below.) Since $\Psi^{(2)}$ is not the ground state of $\hat{H}^{(1)}$, it follows that

$$
E^{(1)}=\left\langle\Psi^{(1)}\right| \hat{H}^{(1)}\left|\Psi^{(1)}\right\rangle<\left\langle\Psi^{(2)}\right| \hat{H}^{(1)}\left|\Psi^{(2)}\right\rangle .
$$

The strict inequality follows if the ground state is nondegenerate, which we will assume here following the arguments of Hohenberg and Kohn. ${ }^{3}$ The last term in Eq. (6.7) can be written

$$
\begin{aligned}
\left\langle\Psi^{(2)}\right| \hat{H}^{(1)}\left|\Psi^{(2)}\right\rangle & =\left\langle\Psi^{(2)}\right| \hat{H}^{(2)}\left|\Psi^{(2)}\right\rangle+\left\langle\Psi^{(2)}\right| \hat{H}^{(1)}-\hat{H}^{(2)}\left|\Psi^{(2)}\right\rangle \\
& =E^{(2)}+\int \mathrm{d}^{3} r\left[V_{\mathrm{ext}}^{(1)}(\mathbf{r})-V_{\mathrm{ext}}^{(2)}(\mathbf{r})\right] n_{0}(\mathbf{r})
\end{aligned}
$$

so that

$$
E^{(1)}<E^{(2)}+\int \mathrm{d}^{3} r\left[V_{\mathrm{ext}}^{(1)}(\mathbf{r})-V_{\mathrm{ext}}^{(2)}(\mathbf{r})\right] n_{0}(\mathbf{r})
$$

On the other hand if we consider $E^{(2)}$ in exactly the same way, we find the same equation with superscripts (1) and (2) interchanged,

$$
E^{(2)}<E^{(1)}+\int \mathrm{d}^{3} r\left[V_{\mathrm{ext}}^{(2)}(\mathbf{r})-V_{\mathrm{ext}}^{(1)}(\mathbf{r})\right] n_{0}(\mathbf{r})
$$

Now if we add together Eqs. (6.10) and (6.11), we arrive at the contradictory inequality $E^{(1)}+E^{(2)}<E^{(1)}+E^{(2)}$. This establishes the desired result: there cannot be two different external potentials differing by more than a constant that give rise to the same nondegenerate ground-state charge density. The density uniquely determines the external potential to within a constant.
${ }^{3}$ This is not a necessary restriction. The proof can readily be extended to degenerate cases [332], which are also included in the alternative formulation by Levy [333-335] discussed in Section 6.4. Except in special cases the density of any one of the degenerate ground states uniquely determines the external potential. In the exercises is an example where two degenerate states have exactly the same density so that the expectation values of general operators cannot be unique functionals of the density. Even then, the expectation value of the energy is the same for all linear combinations of the degenerate states so that the Hohenberg-Kohn theorem is recovered.

The corollary follows since the hamiltonian is uniquely determined (except for a constant) by the ground-state density. Then, in principle, the wavefunction of any state is determined by solving the Schrödinger equation with this hamiltonian. Among all the solutions that are consistent with the given density, the unique ground-state wavefunction is the one that has the lowest energy.

Despite the appeal of this result, it is clear from the reasoning that no prescription has been given to solve the problem. Since all that was proved is that $n_{0}(\mathbf{r})$ uniquely determines $V_{\text {ext }}(\mathbf{r})$, we are still left with the problem of solving the many-body problem in the presence of $V_{\text {ext }}(\mathbf{r})$. For example, for electrons in materials, the external potential is the Coulomb potential due to the nuclei. The theorem only requires that the electron density uniquely determines the positions and types of nuclei, which can easily be proven from elementary quantum mechanics (see Exercise 6.6). At this level we have gained nothing: we are still faced with the original problem of many interacting electrons moving in the potential due to the nuclei.

## Proof of Theorem II

The second theorem is just as easily proven once one has carefully defined the meaning of a functional of the density and restricted the space of densities. The original proof of Hohenberg-Kohn is restricted to densities $n(\mathbf{r})$ that are ground-state densities of the electron hamiltonian with some external potential $V_{\text {ext }}$. Such densities are called " $V$ representable." This defines a space of possible densities within which we can construct functionals of the density. (As discussed below in Section 6.4 it is possible to extend the range of validity of the functional.) Since all properties such as the kinetic energy, etc. are uniquely determined if $n(\mathbf{r})$ is specified, then each such property can be viewed as a functional of $n(\mathbf{r})$, including the total energy functional

$$
\begin{aligned}
E_{\mathrm{HK}}[n] & =T[n]+E_{\mathrm{int}}[n]+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I} \\
& \equiv F_{\mathrm{HK}}[n]+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I},
\end{aligned}
$$

where $E_{I I}$ is the interaction energy of the nuclei (see Eq. (3.2) and related discussion). The functional $F_{\mathrm{HK}}[n]$ defined in Eq. (6.12) includes all internal energies, kinetic and potential, of the interacting electron system,

$$
F_{\mathrm{HK}}[n]=T[n]+E_{\mathrm{int}}[n],
$$

which must be universal by construction because the kinetic energy and interaction energy of the particles are functionals only of the density. ${ }^{4}$

[^2]Now consider a system with the ground state density $n^{(1)}(\mathbf{r})$ corresponding to external potential $V_{\text {ext }}^{(1)}(\mathbf{r})$. Following the discussion above, the Hohenberg-Kohn functional is equal to the expectation value of the hamiltonian in the unique ground state, which has wavefunction $\Psi^{(1)}$

$$
E^{(1)}=E_{\mathrm{HK}}\left[n^{(1)}\right]=\left\langle\Psi^{(1)}\right| \hat{H}^{(1)}\left|\Psi^{(1)}\right\rangle .
$$

Now consider a different density, say $n^{(2)}(\mathbf{r})$, which necessarily corresponds to a different wavefunction $\Psi^{(2)}$. It follows immediately that the energy $E^{(2)}$ of this state is greater than $E^{(1)}$, since

$$
E^{(1)}=\left\langle\Psi^{(1)}\right| \hat{H}^{(1)}\left|\Psi^{(1)}\right\rangle<\left\langle\Psi^{(2)}\right| \hat{H}^{(1)}\left|\Psi^{(2)}\right\rangle=E^{(2)} .
$$

Thus the energy given by Eq. (6.12) in terms of the Hohenberg-Kohn functional evaluated for the correct ground-state density $n_{0}(\mathbf{r})$ is indeed lower than the value of this expression for any other density $n(\mathbf{r})$.

It follows that if the functional $F_{\mathrm{HK}}[n]$ was known, then by minimizing the total energy of the system, Eq. (6.12), with respect to variations in the density function $n(\mathbf{r})$, one would find the exact ground-state density and energy. This establishes Corollary II. Note that the functional only determines the ground-state properties; it does not provide any guidance concerning excited states.

### 6.4 Constrained Search Formulation of DFT

An alternative definition of a functional due to Levy [333-335] and Lieb [336-338] is very instructive because it

- extends the range of definition of the functional in a way that is formally more tractable and clarifies its physical meaning;
- provides an in-principle way to determine the exact functional; and
- leads to the same ground-state density and energy at the minimum as in the HohenbergKohn analysis, and also applies for degenerate ground states.

The idea of Levy and Lieb (LL) is to define a two-step minimization procedure beginning with the usual general expression for the energy in terms of the many-body wavefunction $\Psi$ given by Eq. (3.9). The ground state can be found, in principle, by minimizing the energy with respect to all the variables in $\Psi$. However, suppose one first considers the energy only for the class of many-body wavefunctions $\Psi$ that have the same density $n(\mathbf{r})$. For any wavefunction, the total energy can be written
structure: the case of "noninteracting electrons" - i.e., fermions with the electron mass but with no interactions among themselves, which are the particles that explicitly enter the Kohn-Sham equations. It is advantageous to use the general ideas of density functionals in that case as well, and we will carefully indicate the distinction between the different use of the functionals for the Kohn-Sham equations.

$$
E=\langle\Psi| \hat{T}|\Psi\rangle+\langle\Psi| \hat{V}_{\mathrm{int}}|\Psi\rangle+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})
$$

Now if one minimizes the energy Eq. (6.16) over the class of wavefunctions with the same density $n(\mathbf{r})$, then one can define a unique lowest energy for that density

$$
\begin{aligned}
E_{\mathrm{LL}}[n] & =\min _{\Psi \rightarrow n(\mathbf{r})}\left[\langle\Psi| \hat{T}|\Psi\rangle+\langle\Psi| \hat{V}_{\mathrm{int}}|\Psi\rangle\right]+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I} \\
& \equiv F_{\mathrm{LL}}[n]+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}
\end{aligned}
$$

where the Levy-Lieb functional of the density is defined by

$$
F_{\mathrm{LL}}[n]=\min _{\Psi \rightarrow n(\mathbf{r})}\langle\Psi| \hat{T}+\hat{V}_{\mathrm{int}}|\Psi\rangle
$$

In this form, $E_{\mathrm{LL}}[n]$ is manifestly a functional of the density and the ground state is found by minimizing $E_{\mathrm{LL}}[n]$.

The Levy-Lieb formulation is much more than just a restatement of the HohenbergKohn functional, Eq. (6.12). First, Eq. (6.18) clarifies the meaning of the functional and provides a way to make an operational definition: the minimum of the sum of kinetic plus interaction energies for all possible wavefunctions having the given density $n(\mathbf{r})$. The LL functional also has important formal differences from the Hohenberg-Kohn functional; in particular, the LL functional in Eq. (6.18) is defined for any density $n(\mathbf{r})$ derivable from a wavefunction $\Psi_{N}$ for $N$ electrons. This is termed " $N$-representability" and the existence of such a wavefunction $\Psi_{N}$ for any density satisfying simple conditions is known [339], as discussed in Section 6.6. In contrast, the Hohenberg-Kohn functional is defined only for densities that can be generated by some external potential; this is called " $V$-representability" and the conditions for such densities are not known in general. At the minimum of the total energy of the system in a given external potential, the Levy-Leib functional $F_{\mathrm{LL}}[n]$ must equal the Hohenberg-Kohn functional defined in Eq. (6.13), since the minimum is a density that can be generated by an external potential. In addition, the LL form eliminates the restriction in the original proof of Hohenberg-Kohn to nondegenerate ground states; now one can do the search in the space of any one of a set of degenerate states.

Thus it has been established that a functional can be defined for any density (subject to certain conditions given below) and that by minimizing this functional one would find the exact density and energy of the true interacting many-body system. Just as for the original Hohenberg-Kohn proofs, however, we are faced with the cold fact that no method has been given to find the functional other than the original definition in terms of manybody wavefunctions. Nevertheless, as we shall see in the following chapter, the dependence of the functional on the kinetic and potential energies of the full, correlated many-body wavefunction points the way toward constructing approximate functionals that are of great utility in practical calculations and in understanding the effects of exchange and correlation among the electrons.

### 6.5 Extensions of Hohenberg-Kohn Theorems

Spin Density Functional Theory

The above analysis also shows how the Hohenberg-Kohn theorems can be generalized to several types of particles. The reason for the special role of the density and the external potential in the Hohenberg-Kohn theorems, rather than some other properties of the particles, is simply that these quantities enter the total energy Eq. (3.9) explicitly only through the simple bilinear integral term $\int \mathrm{d}^{3} r V_{\text {ext }}(\mathbf{r}) n(\mathbf{r})$. If there are other terms in the hamiltonian having this form, then each such pair of external potential and particle density will obey a Hohenberg-Kohn theorem.

The most relevant example for our purposes is a Zeeman term that is different for up and down spin fermions (i.e., a magnetic field that acts only on the spins, not on the orbital motion). This is in fact one of the important effects of an external magnetic field, so that this can be considered as a physically realistic approximation. Within this model, one can rigorously generalize all the above arguments to include two types of densities, the particle density $n(\mathbf{r})=n(\mathbf{r}, \sigma=\uparrow)+n(\mathbf{r}, \sigma=\downarrow)$ and the spin density $s(\mathbf{r})=n(\mathbf{r}, \sigma=\uparrow) n(\mathbf{r}, \sigma=\downarrow)$. This leads to an energy functional

$$
E=E_{\mathrm{HK}}[n, s] \equiv E_{\mathrm{HK}}^{\prime}[n]
$$

where in the last form it is assumed that $[n]$ denotes a functional of the density that depends on both position in space $\mathbf{r}$ and spin $\sigma$. "Spin density functional theory" is essential in the theory of atoms and molecules with net spins, as well as solids with magnetic order [305, 340, 341]. (Note that this does not include effects of a magnetic field on the orbital motion, which requires an extension to current functional theory [342-345].)

In the absence of external Zeeman fields, the lowest-energy solution may be spin polarized, i.e., $n(\mathbf{r}, \uparrow) \neq n(\mathbf{r}, \downarrow)$, which is analogous to the broken symmetry solution of unrestricted Hartree-Fock theory. (This must happen in a finite system with an odd number of electrons and also occurs in some atoms polarized to Hund's rules and in magnetic solids.) The spin functional is useful in these cases as well; however, the original Hohenberg-Kohn theorem remains valid and the ground state, in principle, is determined by the total ground-state density $n(\mathbf{r})=n(\mathbf{r}, \uparrow)+n(\mathbf{r}, \downarrow)$ for any system where there is no spin-dependent external potential (see Exercise 6.8). The only modification of the statements of the theorems is to take into account the fact that the broken symmetry solution is necessarily degenerate.

## Mermin Finite Temperature and Ensemble Density Functional Theory

The theorems of Hohenberg and Kohn for the ground state carry over to the equilibrium thermal distribution by constructing the density corresponding to the thermal ensemble. For each of the conclusions of Hohenberg and Kohn for the ground state, there exists a corresponding argument for a system in thermal equilibrium, as demonstrated by Mermin [326] shortly after the Hohenberg-Kohn paper. To show this, Mermin constructed a grand potential functional of the trial density matrices $\hat{\rho}$,

$$
\Omega[\hat{\rho}]=\operatorname{Tr} \hat{\rho}\left[(\hat{H}-\mu \hat{N})+\frac{1}{\beta} \ln \hat{\rho}\right],
$$

whose minimum is the equilibrium grand potential

$$
\Omega=\Omega\left[\hat{\rho}_{0}\right]=-\frac{1}{\beta} \ln \operatorname{Tr} \mathrm{e}^{-\beta(\hat{H}-\mu \hat{N})}
$$

where $\hat{\rho}_{0}$ is the grand canonical density matrix

$$
\hat{\rho}_{0}=\frac{\mathrm{e}^{-\beta(\hat{H}-\mu \hat{N})}}{\operatorname{Tr} \mathrm{e}^{-\beta(\hat{H}-\mu \hat{N})}}
$$

The proof is completely analogous to the Hohenberg-Kohn proofs and uses only the minimum property of $\Omega[\hat{\rho}]$ and the fact that the energy depends on the external potential only through the term $\int V_{\text {ext }}(\mathbf{r}) n(\mathbf{r})$. (The independent-particle version of the Mermin functional is given in Section 7.3.)

The Mermin theorem leads to even more powerful conclusions than the HohenbergKohn theorems, namely that not only the energy but also the entropy, specific heat, etc. are functionals of the equilibrium density. However, the Mermin functional has not been widely applied. The simple fact is that it is much more difficult to construct useful, approximate functionals for the entropy (which involves sums over excited states) than for the groundstate energy. For example, in the Fermi liquid description of a metal the specific heat coefficient at low temperature is directly related to the effective mass at the Fermi surface. Thus the Mermin functional for the free energy must correctly describe the effective mass (with all its many-body renormalization) as well as the ground-state energy, whereas only the latter is required in the Hohenberg-Kohn functional.

The Hohenberg-Kohn theorems can also be generalized to other ensembles that are useful for aspects such as defining a functional of electron number as a continuous variable [346], whereas the original Hohenberg-Kohn theorems are formulated only for a ground state with a fixed integer number of electrons. The equilibrium thermal ensemble of Mermin at fixed chemical potential is an example where the number of electrons fluctuates around the average number given by the expectation value of the number operator $\hat{N}$. From ensemble theory, it also follows that there must be discontinuities in the derivative of the energy with respect to number at integer occupations or, in the case of solids, for filled bands. These are difficult properties to build into the functional and are absent in presentday approximate density functionals.

## Current Density and Time-Dependent Density Functional Theory

The Hohenberg-Kohn theorems apply only to systems that are time-reversal invariant. If there is a magnetic field or time-dependent electric field, the hamiltonian involves terms of the form $V_{\text {ext }}(\mathbf{r}) n(\mathbf{r})$ and $\mathbf{p} \cdot \mathbf{A}_{\text {ext }}$. Thus by exactly the same logic as the original HohenbergKohn arguments, the properties must depend on both the density $n$ and the current density $\mathbf{j}=-\frac{e}{m} \mathbf{p}$ [342, 343, 345]. However, the structure of the theory must be fundamentally
different because there is no analogue of the variational principle for the ground-state energy or equilibrium-free energy.

The generalization of the Hohenberg-Kohn approach to time-dependent problems has been provided by Runge and Gross [246]. For a localized systems with simply connected geometry, the theory can be cast in terms of the time-dependent density since the current is determined by $\nabla \mathbf{j}=-d n / d t$. The result is that given the initial wavefunction at one time $t^{\prime}$, the state at later times $t$ is a functional of the time-dependent density $n\left(\mathbf{r}, t^{\prime \prime}\right)$ for all $t^{\prime} \leq t^{\prime \prime} \leq t$. This may be viewed as the formal construction of a density functional theory for excitations. Although the time-dependent functional must be quite intricate, there has been considerable progress within the Kohn-Sham approach, as described in Chapter 21.

In general, however, the theory must involve the current density. In particular, in a system with no boundaries, or is not simply connected, the evolution is not a functional only of the density. For example, in a uniform ring of charge, the density is unchanged if there is a net current, and the state is determined only if the current is specified [347]. Thus there is an essential link with current functionals and to properties such as the static electric polarization.

## Electric Fields and Polarization

The issue of electric fields and polarization comes into play in extended systems. In infinite space, the potential due to an electric field $V(x)=E x$ is unbounded; there is no lower bound to the energy and therefore there is no ground state. This is a famous problem [348, 349] in the theory of the dielectric properties of materials. However, if the ground state does not exist, the Hohenberg-Kohn theorems on the ground state do not apply [350].

Is there any way to include an electric field in density functional theory? This is a very subtle problem, and the answer is that in the presence of an electric field, one must apply some constraint, within which there is a stable ground state. In the case of molecules, this is routinely done by simply constraining the electrons to remain near the molecule. In a solid, however, the constraint is not so obvious. To the knowledge of the author, all proposals involve constraining the electrons to be in localized Wannier functions (Chapter 23) or equivalent conditions on Bloch functions. Since the energy contains a term $\mathbf{E} \cdot \mathbf{P}$, where $\mathbf{P}$ is the macroscopic polarization, the theory must become a "density polarization theory" (see [351, 352] and references cited there). An interesting point is that in a system with a net polarization at zero field $\mathbf{E}=0$ (e.g., a ferroelectric) the polarization is determined by the density alone [351], i.e., the original Hohenberg-Kohn theorem applies. (But see Chapters 7 and 24 for the opposite conclusion in the Kohn-Sham approach.)

### 6.6 Intricacies of Exact Density Functional Theory

The challenge posed by the Hohenberg-Kohn theorems is how to make use of the reformulation of many-body theory in terms of functionals of the density. The theorems are in terms of unknown functionals of the density, and it is easy to show that these must be nonlocal functionals, depending simultaneously on $n(\mathbf{r})$ at different positions $\mathbf{r}$, which are difficult to cast in any simple form.

## Allowed Densities for Electrons

There are a number of general questions related to the nature of the possible densities that are allowed for fermions, given only that they must integrate to the correct number of particles:

- Can one readily construct different wavefunctions $\Psi$ that have the same density $n(\mathbf{r})$ ? Yes. An illuminating example is the homogeneous electron gas. All plane waves have the same uniform density, but only the choice of the lowest kinetic energy states gives the lowest-energy ground state for the noninteracting case. Interacting electrons also have the same uniform density even though the wavefunctions are correlated and thus quite different from a single determinant. The same logic can be applied to inhomogeneous cases, such as those discussed in Exercise 6.5.
- Is it possible to construct an antisymmetric wavefunction for fermions that can describe any possible density (" $N$-representability")?
Yes, given a few restrictions on the density. As shown by Gilbert [339], it is possible to construct any density integrating to $N$ total electrons of a given spin from a single Slater determinant of $N$ one-electron orbitals, subject only to the condition that $n(\mathbf{r}) \geq 0$, and $\int\left|\nabla n(\mathbf{r})^{1 / 2}\right|^{2}$ is finite. In certain cases, explicit techniques exist for constructing such wavefunctions [273, 353], as described in Exercise 6.6.
- Is it possible to generate any such density as the ground state of some local external potential (" $V$-representability")?
No. A number of "reasonable"-looking densities have been shown not to be the ground state for any potential $V$ [334, 336]. Such densities are termed "non- $V$-representable." This applies to any linear combination of densities of a set of degenerate states; although the densities look "reasonable" they are not the ground state for the given number of electrons and any potential. An example is the spherically averaged density of an openshell atom. If one weakens the question to ask if there are densities that cannot be generated by any smooth potential (one without delta functions) then one can find many counterexamples, e.g., any excited state density for single particles in finite systems. (The density of one electron in a 2s state in H is discussed in Exercise 6.7.)


## Properties Obeyed by the Exact Density Functional Theory

The Hohenberg-Kohn arguments are very general for properties of interacting particle systems, yet special emphasis is on the ground state. Thus questions arise as to what properties of a material should be given correctly by the minimization of the HohenbergKohn functional, if it were known exactly. These examples make it clear how difficult it is to fulfill all the properties guaranteed by the Hohenberg-Kohn and Mermin theorems!

Here we exclude magnetic fields and magnetic susceptibilities that require extension of density functional theory to include currents.

- Are excitation energies given correctly by the exact density functional theory? Yes. In principle, all properties are determined since the entire hamiltonian is determined.
- Are excitation energies given correctly by minimization of the exact Hohenberg-Kohn or Levy-Lieb functionals?
No. The functional evaluated near the minimum provides no information about excitations. Some other method is needed to determine excitation energies.
- Is the exact specific heat versus temperature given correctly by the exact finite temperature Mermin functional?
Yes. Even though the specific heat involves excitations from the ground state, nevertheless the thermal averages over these excitations must be a unique functional of the density and the temperature.
- Are static susceptibilities given correctly by the ground-state functional?

Yes. Since the functional is universal, it is still valid in a perturbed system. All static susceptibilities are second derivatives of ground-state energies with respect to external fields. Thus they must be given correctly by the variation of the ground-state HohenbergKohn functional as functions of external fields. ${ }^{5}$

- Is the exact Fermi surface of a metal given by the exact ground-state density functional theory?
Yes. This is not a trivial question for two reasons. First, for the question to be meaningful, the many-body metal must have a well-defined Fermi surface; for the present purposes we assume this. Second, it is not a priori obvious that the Fermi surface is a ground-state property. One way to see that the Fermi surface is determined by ground-state properties is to consider susceptibilities to static perturbations. The exact density functional theory must lead to the correct Kohn anomalies and Friedel oscillations of the density far from an impurity, which depend in detail on the shape of the Fermi surface of the unperturbed metal.
- Must a Mott insulator (an insulator due to correlations among the electrons) be predicted correctly by the exact density functional theory?
Yes. This follows from the above arguments on a metal in the special case where the Fermi surface vanishes.


### 6.7 Difficulties in Proceeding from the Density

The purpose of this section is to emphasize that density functional theory does not provide a way to understand the properties of a material merely by looking at the form of the density. Although the density is in principle sufficient, the relation is very subtle and no one has found a way to extract directly from the density any general set of properties, e.g., whether the material is a metal or an insulator. The key point is that the density is an allowed density of a quantum mechanical system; it is this fact that builds in the quantum effects.

[^3]The difficulty can be illustrated by considering a case where the exact solution can be found $-N$ noninteracting electrons in an external potential. This is the central problem in the Kohn-Sham approach to density functional theory, which is discussed in Chapter 7. In that case the exact Hohenberg-Kohn functional given by Eq. (6.12) is nothing other than the kinetic energy. In order to evaluate the kinetic energy exactly, the only way known is to revert to the usual expression in terms of a set of $N$ wavefunctions. There is no known way to go directly from the density to the kinetic energy. The kinetic energy expressed in terms of wavefunctions has derivatives as a function of the number of electrons that are discontinuous at integer occupation numbers (see Exercise 6.11). From the virial theorem that relates kinetic and potential energies, it follows immediately that all parts of the exact functional (kinetic and potential) will vary in a nonanalytic manner as a function of the number of electrons. This is a property of a global integral of the density and is not simply determined from any aspect of the density only in some local region.

In the case of solids, the density is remarkably similar to sums of overlapping atom densities. For example, Fig. 2.1 shows the difference in density of electrons in silicon from superposed atoms, which is much smaller than the total density. In fact, the covalent bond is hard to distinguish in the total density. An ionic crystal is often considered as a sum of ions, but it is also well represented as the sum of neutral atoms [354]. This is possible because the negative anion is so large that its density extends around the positive cation, making the density similar to that of neutral atoms. Thus, even for well-known ionic crystals, it is not obvious how to extract pertinent information from the electron density. It is yet more difficult to distinguish metals from insulators (see Exercise 12.11 for an example).

This leads us to the Kohn-Sham approach, the success of which is based on the fact that it includes the kinetic energy of noninteracting electrons in terms of independentparticle wavefunctions, in addition to interaction terms explicitly modeled as functionals of the density. Because the kinetic energy is treated in terms of orbitals - not as an explicit functional of the density - it builds in the quantum properties that have no simple relation to the density. In the example of an ionic crystal, the key point is that the density is made up of fermions that obey the exclusion principle. It is this fact that leads to filling of four bands per cell and an insulating gap, which is the essence of this ionic crystal. So long as the true many-body solution is sufficiently close to the independent-particle formulation - e.g., the states must have the same symmetry - then the Kohn-Sham approach provides insightful guidance and powerful methods for electronic structure theory.

## SELECT FURTHER READING

Original papers:
Hohenberg, P. and Kohn, W., "Inhomogeneous electron gas," Phys. Rev. 136:B864-871, 1964.
Kohn, W. and Sham, L. J., "Self-consistent equations including exchange and correlation effects," Phys. Rev. 140:A1133-1138, 1965.
Mermin, N. D., "Thermal properties of the inhomogeneous electron gas," Phys. Rev. 137:A14411443, 1965.

Reviews with historical perspective and Nobel prize lecture of Kohn:
Becke, A. D., "Perspective: Fifty years of density-functional theory in chemical physics," J. Chem. Phys. 140:301, 2014.
Burke, K., "Perspective on density functional theory," J. Chem. Phys. 136:150901 (2012).
Jones, R. O. and Gunnarsson, O., "The density functional formalism, its applications and prospect," Rev. Mod. Phys. 61:689-746, 1989.
Jones, R. O., "Density functional theory: Its origins, rise to prominence, and future," Rev. Mod. Phys. 87:897-923, 2015.
Kohn, W., "Nobel lecture: Electronic structure of matter wave functions and density functionals," Rev. Mod. Phys. 71:1253, 1999.

Book with extensive exposition:
Dreizler, R. M. and Gross, E. K. U., Density Functional Theory: An Approach to the Quantum ManyBody Problem (Springer, Berlin, 1990).
Engel, E. and Dreizler, R. M., Density Functional Theory: An Advanced Course (Theoretical and Mathematical Physics (Springer, New York, 2011).
Parr, R. G. and Yang, W., Density-Functional Theory of Atoms and Molecules (Oxford University Press, New York, 1989).
Sholl, D. and Stecklel, J. A., Density Functional Theory: A Practical Introduction (WileyInterscience, Hoboken, NJ, 2009).

Edited collections (see also many other volumes in the series):
Density Functional Methods in Physics, edited by R. M. Dreizler and J. da Providencia (Plenum, New York, 1985).
Density Functional Theory, edited by E. K. U. Gross and R. M. Dreizler (Plenum, New York, 1995).
A Primer in Density Functional Theory, edited by C. Fiolhais, F. Nogueira and M. Marques (Springer, New York, 2003).

More general books that discuss density functional theory:
Cohen, M. L. and Louie, S. G. Fundamentals of Condensed Matter Physics (Cambridge University Press, Cambridge, 2016).
Kaxiras, E., Atomic and Electronic Structure of Solids (Cambridge University Press, Cambridge, 2003).

Kaxiras, E. and Joannopoulos, J. D. Quantum Theory of Materials, 2nd rev. ed. (Cambridge University Press, Cambridge, 2019).
Kohanoff, J., Electronic Calculations for Solids and Molecules: Theory and Computational Methods (Cambridge University Press, Cambridge, 2003).

## Exercises

6.1 Derive the Thomas-Fermi equation, (6.5), from the variational of the functional. Use the method of Lagrange multipliers as given in Eqs. (3.10) and used in (6.3).
6.2 See Exercise 5.14 for a problem involving the Thomas-Fermi (TF) approximation.
6.3 The simplest example of the Mermin theorem is the homogeneous gas. For a gas held at fixed volume, as the temperature is varied the density does not change. Describe the meaning of the Mermin functional in this case.
6.4 Theorem I of Hohenberg-Kohn shows that $n_{0}(\mathbf{r})$, in principle, uniquely determines all properties of the many-body system of electrons, including ground and excited states. We have argued that, for example, the electron density uniquely determines the positions and types of nuclei, which then defines the complete hamiltonian and therefore, in principle, determines all properties. Show explicitly that only the density and its derivatives near the nuclei are sufficient to establish the proof in this case.
6.5 In one dimension it is possible to construct orthonormal independent-particle orbitals that describe any density that satisfies simple positivity and continuity conditions. See Exercise 7.9.
6.6 Following the approach of Section 6.6, show that it is not possible to construct the density of the 2s state of hydrogen (one electron in the potential of a proton) as the ground-state density of any smooth potential, i.e., one without delta functions.
6.7 Consider the lowest-energy state of Li with three electrons, which may be $1 \mathrm{~s}^{2} 2 \mathrm{~s}$ or one of the degenerate states $(1 \mathrm{~s})^{2} 2 \mathrm{p}^{0}, 1 \mathrm{~s}^{2} 2 \mathrm{p}^{-}$, or $1 \mathrm{~s}^{2} 2 \mathrm{p}^{+}$. The densities of the last two states are identical, so that the density does not determine the state. Show that, nevertheless, the energy is the same for any combination of these states so that the energy is still a functional of the density as needed for the Hohenberg-Kohn functional.
6.8 In this problem you are asked to show that in the absence of an external magnetic field, the total density is, in principle, enough to determine all the properties of the system even if it is spin polarized. To do this, consider the system in a Zeeman field $\mathbf{h} \cdot \sigma$ that distinguishes between $\sigma$ parallel and antiparallel to $\mathbf{h}$. Show that if $\mathbf{h}$ is reversed, the new solution will have exactly the same density but with $\sigma$ reversed. Using this fact show that you can reach the desired conclusion.
6.9 Suppose particles can be divided into two types (e.g., spins) of density $n_{1}$ and $n_{2}$ with internal energy $E_{\text {int }}\left[n_{1}, n_{2}\right]$. If the external potential acts on $n_{1}$ and $n_{2}$ equally, the total energy can be written $E_{\text {total }}=E\left[n_{1}, n_{2}\right]+\int V_{\text {ext }} n$, where $n=n_{1}+n_{2}$. Show that $E_{\text {total }}$ is a functional only of $n$. Do this in three ways: (a) using arguments similar to the original arguments of Hohenberg and Kohn; (b) the Levy-Lieb constrained search method; and (c) formal solution by variational equations in terms of $n$ and $\sigma=n_{1}-n_{2}$.
6.10 Consider a many-body hamiltonian $\hat{H}=\hat{H}_{\text {int }}+V_{\text {ext }}$, where $\hat{H}_{\text {int }}$ denotes all intrinsic internal kinetic and interaction terms and $V_{\text {ext }}$ is the external potential. Show that the external potential $V_{\text {ext }}(\mathbf{r})$ is determined to within a constant, given $\hat{H}_{\text {int }}$ and any eigenfunction $\Psi_{i}$. Hint: solve for $V_{\text {ext }}(\mathbf{r})$ using the Schrödinger equation. (Note a specific example of a determinant wavefunction is considered as an exercise in Chapter 7.)
6.11 Show that in a finite system the kinetic energy must be a nonanalytic function of the density $n$ with derivatives that are discontinuous at integer occupations. Hint: it is sufficient to show the result in an independent-particle example (see Exercise 7.5) with an argument that the result must also apply to many-body cases. Generalize this argument to all properties of the system and to solids with an insulating gap.


[^0]:    ${ }^{1}$ This is an example of functional equations described in Appendix A; see specifically Eq. (A.5).

[^1]:    ${ }^{2}$ The nuclei-nuclei interaction is added later; at this point it is not needed, except that care is needed to treat Coulomb interactions in extended systems (Section 3.2). Special considerations are required to include magnetic fields and there are subtle issues for electric fields in extended systems, see Section 6.5.

[^2]:    ${ }^{4}$ Note that here "universal" means the same for all electron systems, independent of the external potential $V_{\text {ext }}(\mathbf{r})$. The Hohenberg-Kohn approach leads to different functionals for different particles depending on their masses and interactions. In this book the functionals described are for electrons, unless explicitly indicated otherwise. In fact there is another important application of the ideas of density functional theory in the theory of electronic

[^3]:    ${ }^{5}$ The dielectric susceptibility of an infinite system is a special case because the ground state is not strictly defined in the presence of a finite electric field. Nevertheless, susceptibilities can be calculated. Similarly a finite polarization is problematic. As discussed in Chapter 24, it is not given directly by the density; it is determined by expressions in terms of phases of the wavefunctions, which require some other method beyond the ground-state functional.

