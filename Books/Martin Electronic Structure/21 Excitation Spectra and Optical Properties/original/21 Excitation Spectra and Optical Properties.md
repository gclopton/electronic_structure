## 21

## Excitation Spectra and Optical Properties

> Look, Simba, everything the light touches is our kingdom.

King Mufasa in The Lion King


#### Abstract

\section*{Summary}

Excitation spectra reveal the properties of matter in terms of the response to time- or frequency-dependent perturbations. Particularly important examples are the dielectric function $\epsilon(\omega)$ and the inverse function $\epsilon^{-1}(\omega)$ in solids and the polarizability $\alpha(\omega)$ in molecules. The basic formulas relating the response to the electronic structure are rooted in perturbation theory and response functions in Appendixes D and E. This chapter is devoted to time-dependent density functional theory (TDDFT), which provides an exact framework in principle. In practice, approximate forms are very successful and TDDFT is now a tool used expansively for molecules and nanosize clusters. There are special issues in solids that provide insights into the effects of interactions.


### 21.1 Overview

As emphasized in Sections 2.14 and 2.15, two types of excitations are of primary importance for electronic structure: those in which an electron is added or removed from the system, and those in which the number of electrons remains fixed. In independent-particle theories, such as the Hartree-Fock or Kohn-Sham approaches, the addition and removal energies are the eigenstates of the independent-particle hamiltonian, which form bands $\varepsilon_{i \mathbf{k}}$ in a crystal. As discussed in Section 7.7, the Kohn-Sham equations are meant to determine the total energy and it is a misuse of the original Kohn-Sham approach to identify the eigenvalues with true electron removal or addition energies. Even if the theory is on a more firm basis in the generalized Kohn-Sham picture (Section 9.2), the eigenvalues are still just a band structure that cannot describe the broadening of the spectra and satellites that occur in real systems due to interactions, as illustrated in Fig. 2.22. Many examples of bands are given in other chapters and will not be covered further here.

A new set of concepts emerges for excitations in which the number of electrons does not change. An example is optical spectra, which are among the most important properties
of materials and one of the most important experimental tools for studying the electronic structure of materials. There are also other techniques such as inelastic scattering of charged particles and X-rays [834]. In the independent-particle approximation the spectrum is only a convolution of one-particle processes in which an electron is removed from an occupied state (creating a hole) and added to an empty state with no interactions. However, in the real world, the added electron interacts with the hole, and the interaction is screening by the other electrons. Since the Kohn-Sham method cannot describe aspects of the one-particle spectra for the electron and hole individually, it may seem surprising that there could be ways to use the Kohn-Sham approach that are better for problems in which both are present and there are even more effects of interaction.

The topic of this chapter is time-dependent density functional theory (TDFT), the extension of the Kohn-Sham theory that provides a way to calculate spectra, in principle exactly. The ideas are similar to the time-dependent Hartree-Fock approximation, which has a long history [329, 835], and were perhaps first used by Ando et al. [836] for model problems in semiconductors and by Zangwill and Soven [245] for atoms. It is only since the 1980s with the work of Runge and Gross [246] that it has been put on a firm footing analogous to the Kohn-Sham formulation for the ground state. TDDFT has been extremely successful and is the method of choice for many problems, especially in the chemistry community. It is widely applied to clusters and nanosystems (Section 21.7) and there are more recent developments that make it more practical for solids (Section 21.8). At the end of this chapter are listed a few of the many books and reviews that provide penetrating analyses and practical information.

### 21.2 Time-Dependent Density Functional Theory (TDDFT)

The derivation of timedependent density functional theory (TDDFT) is fundamentally different from that for DFT, yet there is much in common. Like the static version, the equations are remarkably simple; the difficult issues of treating exchange and correlation are buried in a functional that is unknown, but feasible approximations turn out to be very successful. For a time-dependent problem, the equations are not derived by minimizing an energy, like the original static Kohn-Sham theory; instead, the time-dependent Kohn-Sham equations can be derived from the stationarity principle for the action $A$ [246],

$$
\frac{\delta A}{\delta n(\mathbf{r}, t)}=0
$$

where

$$
A=\int_{t_{0}}^{t_{1}} \mathrm{~d} t\langle\Psi(t)|\left[i \frac{\mathrm{~d}}{\mathrm{~d} t}-\hat{H}(t)\right]|\Psi(t)\rangle
$$

If one adds the Kohn-Sham idea of replacing the density with the density of independent particles, this leads to time-dependent Kohn-Sham density functional theory (TDDFT), in which there is a time-dependent Schrödinger-like equation

$$
i \hbar \frac{\mathrm{~d} \psi_{i}(t)}{\mathrm{d} t}=\hat{H}_{\mathrm{eff}}(t) \psi_{i}(t)
$$

with an effective hamiltonian that depends on time $t$

$$
\hat{H}_{\mathrm{eff}}(t)=-\frac{1}{2} \nabla^{2}+V_{\mathrm{ext}}(\mathbf{r}, t)+\int \frac{n\left(\mathbf{r}^{\prime}, t\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \mathrm{d} \mathbf{r}^{\prime}+V_{\mathrm{xc}}[n](\mathbf{r}, t)
$$

where $V_{\mathrm{xc}}[n](\mathbf{r}, t)$ is a function of $\mathbf{r}$ and $t$ and a functional of density $n\left(\mathbf{r}^{\prime}, t^{\prime}\right)$.
The original derivation [246] was in terms of the current density $\mathbf{j}(\mathbf{r}, t)$; however, in a finite system it can be transformed to a theory strictly in terms of the density using the continuity equation $\nabla \cdot \mathbf{j}(\mathbf{r}, t)=-n(\mathbf{r}, t)$. In the applications later in this chapter, we will first consider (Section 21.7) finite systems such as molecules and nanoscale clusters using Eqs. (21.3) and (21.4) as they are written. Afterward we consider (Section 21.8) electromagnetic waves in crystals where it is advantageous to use the formulation in terms of the current and the vector potential $\mathbf{A}(\mathbf{r}, t)$, but the approach will still be called TDDFT, which is traditional in the literature.

The seemingly simple equations of TDDFT conceal subtleties that we will not deal with, but which should be pointed out; the issues are discussed in reviews such as [395, 427, 837, 838], which give references to the literature. In the formally exact theory, $V_{\mathrm{xc}}[n](\mathbf{r}, t)$ is a functional of $n\left(\mathbf{r}^{\prime}, t^{\prime}\right)$ for all earlier times $t^{\prime} \leq t$. This leads to issues related to causality that have been controversial but been resolved [839]. Most applications get around the difficulties by making the adiabatic approximation in which $V_{\mathrm{xc}}[n(t)](\mathbf{r})$ depends only on the density at the same time, e.g., in the adiabatic LDA (ALDA), it is simply $V_{\mathrm{xc}}(\mathbf{r}, t)=V_{\mathrm{xc}}(n(\mathbf{r}, t))$. However, it is clear that the adiabatic approximation is not always sufficient. For example, in a system driven near a resonance, the functional should take into account the particular states involved in the transition. The effects are not easily captured in terms of the density alone; however, orbital-dependent functionals naturally incorporate at least some aspects of spatial and dynamical effects and they play an essential role in the theory and applications.

One of the main applications of TDDFT is to calculate optical spectra, which is emphasized in the rest of this chapter. But it should be kept in mind that TDDFT is a very general theory that applies for various perturbations. Inelastic scattering of charged particles is described in terms of the inverse dielectric function $\epsilon^{-1}\left(\mathbf{q}, \mathbf{q}^{\prime}, \omega\right)$ defined in Section E.4. This is discussed more fully in [1], Section 14.3. It is the inverse function that is most convenient to derive the expression for the macroscopic dielectric constant including the microscopic internal fields as expressed in Eq. (E.17). This is also the response function needed to describe energy loss for high-energy charged particles and stopping power of energetic ions (see, e.g., [840]). Inelastic X-ray scattering is another active area of experiments that can be addressed by TDDFT (see, e.g., the review [834]).

### 21.3 Dielectric Response for Noninteracting Particles

Before proceeding, it is useful to first define the dielectric function and give the expressions in the independent-particle approximation. The forms are illuminating and examples of the independent-particle spectra are shown later for comparison with the TDDFT spectra. For
a finite system, such as a cluster, with size much less than the wavelength of light, the expressions in terms of a scalar potential and the position vectors $\mathbf{r}$ is a convenient approach. The external perturbation ${ }^{1}$ can be written in terms of the applied electric field $\mathbf{E}_{\text {ext }}(t)$ acting upon an electron at point $\mathbf{r}$,

$$
\Delta \hat{H}(t)=\Delta V_{\mathrm{ext}}(\mathbf{r}, t)=-e \mathbf{E}_{\mathrm{ext}}(t) \cdot \mathbf{r}
$$

instead of Eq. (21.8), and the response is the induced dipole moment per unit volume given by

$$
\Delta \mathbf{d}(t)=\frac{-e}{\Omega} \int_{\text {all space }} \mathrm{d} \mathbf{r} \Delta n(\mathbf{r}, t) \mathbf{r} .
$$

This is the approach used directly in the real-time method. In the frequency domain the expression for linear response is the polarizability $\alpha(\omega)=d(\omega) / E(\omega)$ (omitting vector indices for simplicity), which involves matrix elements of the position operator $\mathbf{r}$,

$$
\alpha(\omega)=e^{2} \sum_{i j}\left(f_{i}-f_{j}\right) \frac{\left\langle\psi_{i}\right| \mathbf{r}\left|\psi_{j}\right\rangle\left\langle\psi_{j}\right| \mathbf{r}\left|\psi_{i}\right\rangle}{\varepsilon_{i}-\varepsilon_{j}+\omega+i \eta}
$$

It is not apparent but Exercise 9.8 is to show that $\alpha$ has units of volume. In TDDFT these expressions are modified due to the induced variation of the Kohn-Sham potential. The general form of the expressions is discussed below with references to papers where detailed expressions can be found.

In a crystal the formulation in terms of electric fields, dipoles, and matrix elements of the position $\mathbf{r}$ are ill-defined and they have led to enormous confusion over years. ${ }^{2}$ Those problems are avoided if the macroscopic field is treated in terms of the vector potential $\mathbf{A}(t)$ instead of the scalar potential $V$. Then the perturbation can be included in the hamiltonian as given in Eq. (E.19),

$$
\Delta \hat{H}(t)=\frac{1}{2 m_{e}} \sum_{i}\left\{\left[\hat{\mathbf{p}}_{i}-\frac{e}{c} \mathbf{A}(t)\right]^{2}-\hat{\mathbf{p}}_{i}^{2}\right\},
$$

where $\mathbf{E}(t)=-\frac{1}{c} \frac{\mathrm{~d} \mathbf{A}}{\mathrm{~d} t}$ and $\mathbf{E}(\omega)=-\frac{i \omega}{c} \mathbf{A}(\omega)$. The desired response is the macroscopic average current density $\mathbf{j}=-e\langle\mathbf{v}\rangle$, and since $\mathbf{p}=m \mathbf{v}-\frac{e}{c} \mathbf{A}$, it follows that $\mathbf{j}=\frac{-e}{m}\langle\mathbf{p}+ \left.\frac{e}{c} \mathbf{A}\right\rangle$, and the relation of $\mathbf{j}(\omega)$ to $\mathbf{E}(\omega)$ determines the conductivity $\sigma(\omega)$ and $\epsilon(\omega)$ (see Section E.2). Using the general form of a response function Eq. (D.19) one finds the expression

$$
\epsilon_{\alpha \beta}(\omega)=\delta_{\alpha \beta}-\frac{e^{2}}{m_{e} \Omega} \frac{1}{\omega^{2}} \sum_{i}\left[f_{i} \delta_{\alpha \beta}+\sum_{j} \frac{f_{i}-f_{j}}{\hbar m_{e}} \frac{\left\langle\psi_{i}\right| p_{\alpha}\left|\psi_{j}\right\rangle\left\langle\psi_{j}\right| p_{\beta}\left|\psi_{i}\right\rangle}{\varepsilon_{i}-\varepsilon_{j}+\omega+i \eta}\right],
$$

[^0]where the $f_{i}$ are occupation numbers and $\eta>0$ is a small damping factor. (The first term in the square brackets comes from the contribution of $\mathbf{A}$ to the current operator (Exercise 21.1) and the second is the response function $\chi^{0}$ for noninteracting particles.)

This expression shows the basic reason that measurements of optical spectra are such powerful tools for studies of electronic properties of crystals. If the $\mathbf{p}$ matrix elements do not vary rapidly as a function of energy for transitions between each pair of bands of electronic states, the imaginary part of $\epsilon(\omega)$ (or the real part of $\sigma(\omega)$ ) directly reveals singularities in the density of states for optical transitions. In the noninteracting approximation, this is a joint density of states for transitions between pairs of filled and empty bands weighted by the matrix elements. Examples of $\epsilon(\omega)$ calculated in the independent-particle approximation are given in Figs. 2.25 and 21.5; see [561] and [565] for many other examples.

### 21.4 Time-Dependent DFT and Linear Response

In this chapter are three methods for calculations using time-dependent DFT. The first is based on well-established perturbation theory and response functions. It has a great advantage that it is close in spirit to many-body perturbation theory (MBPT), in particular the Bethe-Salpeter equation (BSE) and implementations that are described in [1]. The relation of TDDFT and MBPT is the topic of the review by Onida et al. [841]. One of the fortunate consequences is that codes developed for calculation of spectra using the BSE can be readily adapted to TDDFT, including hybrid functionals that involve the nonlocal Hartree-Fock exchange. A disadvantage of this approach is that it is formulated in terms of transitions to empty states, i.e., all combinations of pairs of occupied and empty states (notice the number of indices on the kernel $K_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}}$ and the expression for each term in Eq. (21.14), which leads to large matrices especially for cases where there is a large basis such as plane waves or grids.

The general form of response functions in self-consistent field theories is given in Appendix D in terms of the noninteracting response functions $\chi^{0}$ and the interaction kernel $K$. The dynamical density response function is given by Eq. (D.23), which can also be written

$$
\chi(\omega)=\chi^{0}(\omega)\left[1-\chi^{0}(\omega) K(\omega)\right]^{-1} \quad \text { or } \quad \chi(\omega)=\chi^{0}(\omega)[1+\chi(\omega) K(\omega)]
$$

where $K$ is the Fourier transform of the space- and frequency-dependent kernel given in Eq. (D.22). To put flesh on these bare bones, we can give useful explicit expressions following [447]. Expanding the expressions in terms of the time-independent KohnSham orbitals, ${ }^{3}$ the matrix elements of the effective potential are given by $\delta\left[V_{\text {eff }}\right]_{i j}^{\sigma} \equiv \left\langle\psi_{i}^{\sigma}\right| \delta V_{\text {eff }}(\mathbf{r}, \omega)\left|\psi_{j}^{\sigma}\right\rangle$, and the density can be written in terms of the density matrix $\rho_{i j}^{\sigma}$ using

$$
\delta n^{\sigma}(\mathbf{r}, \omega)=\sum_{i j} \psi_{i}^{\sigma}(\mathbf{r}) \rho_{i j}^{\sigma} \psi_{j}^{\sigma}(\mathbf{r})
$$

[^1]The response of the system can be expressed in terms of the density matrix and one can define a noninteracting $\chi^{0}$ given by [447]

$$
\chi_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}}^{0}=\frac{\delta \rho_{i j}^{\sigma}}{\delta\left[V_{\mathrm{eff}}\right]_{i^{\prime} j^{\prime}}^{\sigma^{\prime}}}=\delta_{i i^{\prime}} \delta_{j j^{\prime}} \delta_{\sigma \sigma^{\prime}} \frac{f_{i}^{\sigma}-f_{j}^{\sigma}}{\omega-\left(\varepsilon_{i}^{\sigma}-\varepsilon_{j}^{\sigma}\right)}
$$

The interacting response function can be derived from the relation $\delta V_{\text {eff }}=\delta V_{\text {ext }}+\delta V_{H}+ \delta V_{\mathrm{xc}} \equiv \delta V_{\mathrm{ext}}+\delta V_{H \mathrm{xc}}$, which to linear order is given by $\delta V_{\mathrm{eff}}=\delta V_{\mathrm{ext}}+K \delta n$. The full expression can be written in the form of Eq. (21.10),

$$
\chi_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}}=\frac{\delta \rho_{i j}^{\sigma}}{\delta\left[V_{\mathrm{ext}}\right]_{i^{\prime} j^{\prime}}^{\sigma^{\prime}}}=\chi_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}}^{0}\left[\delta_{i i^{\prime}} \delta_{j j^{\prime}} \delta_{\sigma \sigma^{\prime}}+\sum_{i^{\prime \prime} j^{\prime \prime} \sigma^{\prime \prime}} \chi_{i^{\prime \prime} j^{\prime \prime} \sigma^{\prime \prime}, i^{\prime} j^{\prime} \sigma^{\prime}} K_{i j \sigma, i^{\prime \prime} j^{\prime \prime} \sigma^{\prime \prime}}\right]
$$

where $K$ is the array of matrix elements of the interaction terms

$$
\begin{aligned}
K_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}} & =\frac{\delta\left[V_{H \mathrm{xc}}\right]_{i j}^{\sigma}}{\delta \rho_{i^{\prime} j^{\prime}}^{\sigma^{\prime}}} \\
& =\int \mathrm{d} \mathbf{r} \int \mathrm{~d} \mathbf{r}^{\prime} \psi_{i}^{\sigma *}(\mathbf{r}) \psi_{j}^{\sigma}(\mathbf{r})\left[\frac{\delta_{\sigma \sigma^{\prime}}}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}+f_{\mathrm{xc}}^{\sigma \sigma^{\prime}}\left(\mathbf{r}, \mathbf{r}^{\prime}, \omega\right)\right] \psi_{i^{\prime}}^{\sigma^{\prime}} *\left(\mathbf{r}^{\prime}\right) \psi_{j^{\prime}}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)
\end{aligned}
$$

where $f_{\mathrm{xc}}$ is the second derivative of $E_{\mathrm{xc}}[n]$ given explicitly in Eqs. (D.21) and (D.22). The frequency dependence of $f_{\mathrm{xc}}$ presents difficult issues and essentially all work to date uses the adiabatic approximation where $E_{\mathrm{xc}}[n]$ and $f_{\mathrm{xc}}$ are the same as in the static KohnSham method.

With some algebra (Exercise 21.2), the solution of the equation can be cast in the form of an eigenvalue equation often called the Casida equation [447]

$$
\left[\omega_{i j \sigma}^{2} \delta_{i i^{\prime}} \delta_{j j^{\prime}} \delta_{\sigma \sigma^{\prime}}+2 \sqrt{f_{i j \sigma} \omega_{i j \sigma}} K_{i j \sigma, i^{\prime} j^{\prime} \sigma^{\prime}} \sqrt{f_{i^{\prime} j^{\prime} \sigma^{\prime}} \omega_{i^{\prime} j^{\prime} \sigma^{\prime}}}\right] F_{n}=\Omega_{n}^{2} F_{n}
$$

where $f_{i j \sigma}=f_{i}^{\sigma}-f_{j}^{\sigma}$ and $\omega_{i j \sigma}=\varepsilon_{i}^{\sigma}-\varepsilon_{j}^{\sigma}$. The TDDFT problem thus becomes a matrix problem with the basis of pairs of Kohn-Sham states $i j \sigma$. If there are $N_{\mathrm{occ}}$ filled orbitals and one includes $N_{\text {empty }}$ empty orbitals of each spin, then the size of the matrices is $N_{\text {pair }} \times N_{\text {pair }}$, where $N_{\text {pair }}=2 N_{\text {occ }} \times N_{\text {empty }}$. These are very general equations for the density matrix, which can be utilized in the problem of polarizability of a molecule or cluster in terms of matrix elements of the position vector $\left\langle\psi_{i}\right| \mathbf{r}\left|\psi_{j}\right\rangle$ and the density matrix. An efficient approach is to use the eigenvectors $F_{n}$ of the Casida equation (21.15), which is explained in detail in references such as [575].

### 21.5 Time-Dependent Density-Functional Perturbation Theory

Dynamical response functions can also be formulated in ways closely related to the iterative or variational Green's function methods of Section 20.4 called density functional perturbation theory (DFPT). The general idea is that the response functions developed in the previous section can describe the response to all possible perturbations. However, what
we need in any particular case is the response to the particular perturbation. In the static case, DFPT was developed as a framework in which the desired result to a given order in perturbation theory can be found by iterative solution of a self-consistent set of equations involving only the occupied subspace.

The corresponding formulation has been developed for dynamic perturbations in two papers by Walker et al. [842] and Rocca et al. [843], and there is an overview in a paper [844] that describes the resulting computer code turboTDDFT that is publicly available. In static DFPT, the basic algorithm is iteratively solving the set of equations (20.19) for the change in the occupied set of wavefunctions projected onto the empty space, i.e., orthogonal to the occupied space. The corresponding problem in the time-dependent case is cast in terms of a Liouvillian superoperator that acts on pairs of functions. Like the static form, it is transformed into a set of equations that do not require calculation of the empty states. The calculation can be much more efficient than the standard perturbation theory, especially for large systems or large basis sets, such as plane waves or real-space grids. With efficient adaptations of the Lanczos method, the entire spectrum of a molecule or extended system can be computed with computational effort comparable to that required for a ground-state calculation.

### 21.6 Explicit Real-Time Calculations

An alternative approach is to propagate the system in time. The evolution of each oneparticle state $\psi_{i}(t)$ is given by a Schrödinger-like equation (21.3) with an effective hamiltonian that depends on time. If we adopt the adiabatic approximation, as is done in the other methods, then $V_{\mathrm{xc}}(\mathbf{r}, t)$ depends on only the density at the same time for each step. Many of the basic ideas originated in nuclear physics [845] and an excellent exposition can be found in the text by Koonin and Meredith [485].

The main difference from the other approaches in that the evolution is not limited to linear response (or nonlinear response, which is more and more difficult for higher orders). Instead it treats the effect nonperturbatively and can be for nonlinear effects, including extreme conditions created by laser pulses. (See, e.g., [395] and references therein.) A great advantage is that, like the time-dependent DFPT methods, there is no need to explicitly calculate excited states. One needs only to propagate $N$ wavefunctions for $N$ particles. A convenient choice is for the initial wavefunctions $\psi_{i}(t=0)$ to be the filled ground-state functions before the perturbation is turned on. When the external field is turned on, this is not the ground state; the wavefunctions are not eigenstates and they evolve in time mixing in components of the states that were empty of the initial system. The algorithm for realtime calculations is very straightforward and it automatically includes the effects of $f_{\mathrm{xc}}$ as the hamiltonian is updated.

The fact that the one does not have to know $f_{\mathrm{xc}}$ is also a disadvantage; because the effects are hidden, it is more difficult to understand the physics and one has lost the connection to the many-body pertubation theory. Another drawback is the fact that the time step has to be very small in order to capture the details of the response of the electrons.

The key requirement for the iterations in time is that the propagation is unitary, which is essential for particle number conservation. If the functions $\psi_{i}(t)$ are expanded in a fixed time-independent basis

$$
\psi_{i}(t)=\sum_{\alpha} c_{i, \alpha}(t) \chi_{\alpha}
$$

then the iteration from $c_{i, \alpha}^{n}$ at time $t^{n}$ to $c_{i, \alpha^{\prime}}^{n+1}$ at time $t^{n+1}=t^{n}+\delta t$ is given by

$$
c_{i, \alpha}^{n+1}=\sum_{\alpha^{\prime}}\left[\mathrm{e}^{-\mathrm{i} \hat{H} \delta t}\right]_{\alpha, \alpha^{\prime}} c_{i, \alpha^{\prime}}^{n}
$$

where $\hat{H}$ is a matrix in the basis $\alpha, \alpha^{\prime}$. The hamiltonian $\hat{H}$ depends on the density $n(\mathbf{r}, t)$, but this is not written explicitly to keep the notation simple. Because the complex exponential operator has unity modulus, Eq. (21.17) is a unitary transformation. The size of the time step $\delta t$ is limited by condition that $\hat{H}(t)$ can be considered constant over the interval $\delta t$; nevertheless, one can still choose the time at which $\hat{H}(t)$ is evaluated. Since $\hat{H}$ must be updated as a function of the time-dependent density, this can have important consequences for efficiency. Two examples are the predictor-corrector method [846] and the "railway curve interpolation" [847].

Here we describe four types of approaches used in actual calculations:

- Explicit operations with the exponential. In general it is not possible to perform the exponentiation of an operator exactly, and one must bring the operators to diagonal form. In that case, $\exp (A)=\sum_{i}\left|\zeta_{i}\right\rangle \exp \left(A_{i i}\right)\left\langle\zeta_{i}\right|, A_{i i}=\left\langle\zeta_{i}\right| A\left|\zeta_{i}\right\rangle$, with $\zeta_{i}$ an eigenvector of $A, A_{i i}=\left\langle\zeta_{i}\right| A\left|\zeta_{i}\right\rangle$, and $\exp \left(A_{i i}\right)$ the ordinary exponential of a scalar (Exercise 21.3). This can be done separately for the potential ( $V$ ) and kinetic ( $T$ ) operators, which are diagonal, respectively, in real and reciprocal space. However, the hamiltonian involves both operators, which cannot in general be separated since they do not commute. Nevertheless, one can use a Suzuki-Trotter expansion, of which a simple example is

$$
\exp [-\mathrm{i}(T+V) \delta t] \simeq \exp \left(-\mathrm{i} \frac{1}{2} V \Delta t\right) \exp (-\mathrm{i} T \Delta t) \exp \left(-\mathrm{i} \frac{1}{2} V \Delta t\right)
$$

plus corrections $\propto \delta t^{2}$ (Exercise 21.4). This approach is well suited for plane wave or real-space methods, where efficient fast Fourier transform algorithms provide an exact transformation between finite plane wave expansions and real-space grids. The transformations are exactly the same as used in ground-state plane codes and described in Section M.11, especially Fig. M.2.

- Expansion of the exponential. The simplest approach is to expand the exponential in Eq. (21.17) in powers of the hamiltonian, which leads to

$$
c^{n+1}=\left[1-i \hat{H} \delta t-\frac{1}{2} \hat{H}^{2} \delta t^{2}+\cdots\right] c^{n}
$$

The expansion can easily be carried to high orders and the calculation done by iterative applications of $\hat{H}$. Just as for other iterative methods (Appendix M), the operations can be done efficiently so long as the hamiltonian is sparse, e.g., with localized states, or using transformations such the FFT to make all operations sparse (Section M.11, especially Fig. M.2). Although the operations are not manifestly unitary, they can be used for practical calculations [846] with small $\delta t$.

- Unitary expansion of the exponential. The expansion of the exponential can be done in an alternative form using the Crank-Nicholson operator [485],

$$
c^{n+1}=\frac{1-i \hat{H} \frac{\delta t}{2}+\cdots}{1+i \hat{H} \frac{\delta t}{2}+\cdots} c^{n}
$$

This method is unitary, strictly preserving the orthonormality of the states for an arbitrary $\delta t$. For time-independent hamiltonians, it is also explicitly time-reversal invariant, and exactly conserves energy. In practice, with a suitable choice of $\delta t$, energy is satisfactorily conserved even when the hamiltonian changes with time. The disadvantage is that it involves an inverse operator, which requires a matrix inversion or solution of linear equations [485].

- Expansion in Chebyshev polynomials. An alternative to iterative approaches is to expand in Chebyshev orthogonal polynomials [848] that provide a global fit to the propagation over the entire time range,

$$
\mathrm{e}^{-\mathrm{i} H t} \simeq \mathrm{e}^{-\mathrm{i} E_{\mathrm{av}} t} \sum_{n=0}^{N} a_{n}\left(\frac{\Delta E t}{2}\right) T_{n}\left(H_{\mathrm{norm}}\right),
$$

where $T_{n}$ are the Chebyshev polynomials (Section K.5) and the expansion coefficients $a_{n}(x)$ can be shown to be analogous to Bessel functions of the first kind of order $n$. Here $H_{\text {norm }} \equiv\left(2 H-E_{\text {av }}\right) / \Delta E$ is a normalized hamiltonian, where $E_{\text {av }}=\left(E_{\text {max }}+E_{\text {min }}\right) / 2$ and $\Delta E=E_{\max }-E_{\min }$, with $E_{\max }$ and $E_{\min }$ the maximum and minimum eigenvalues of $H$. The Chebyshev polynomials are chosen because their error decreases exponentially when $N$ is large enough, due to the uniform character of the Chebyshev expansion [848].

### 21.7 Optical Properties of Molecules and Clusters

TDDFT has become a standard tool in chemistry to characterize spectra of molecules. There are vast numbers of calculations described in references such as [447, 838, 849], and comparisons of functionals, for example in [850]. Here we focus on methods and applications on clusters and large molecules (exemplified by $\mathrm{C}_{60}$ ) that are close to work in condensed matter. Many calculations have been done using the adiabatic LDA and GGA, which improve agreement with experiment significantly compared to the noninteracting approximation.

For a finite system with size much less than the wavelength of light, such as molecules and clusters, the relevant response function is the polarizability $\alpha(\omega)=d(\omega) / E(\omega)$ where $d$ is the induced dipole defined as a function of time in Eq. (21.6) or the Fourier transform
to frequency after Eq. (21.6). The spectra are often presented as the imaginary part of the polarizability $\alpha(\omega)$ or as the dipole strength function ${ }^{4}$

$$
S(\omega)=\frac{2 m}{\pi e^{2} \hbar} \omega \operatorname{Im} \alpha(\omega)
$$

The strength function is proportional to the experimentally measured photoabsorption cross-section, and it satisfies the $f$ sum rule,

$$
\hbar \int_{0}^{\infty} d \omega S(\omega)=\sum_{i} f_{i}=N_{e}
$$

where $f_{i}$ are the oscillator strengths (see Exercise 21.5).
Metal clusters are an interesting class of systems that can be varied from atomic to macroscopic size [222]. The simplest approximation is spherical jellium ignoring the atomic structure, which leads to the correct general features of the optical spectra dominated by a plasmon-like peak. ${ }^{5}$ The question for quantitative calculations is the extent to which the real atomic structure matters. An example of one of the first quantitative calculations on metal clusters is shown in Fig. 21.1. The structure was determined by a ground-state LDA calculation and the spectrum by time-dependent DFT using the LDA (TDLDA) and a plane wave basis. There is a two-peak structure very different from the jellium model, with the main peak shifted and in better agreement with experiment. The shift in the main peak from the noninteracting particle response, Eq. (21.9), shows the effects of the Coulomb interaction in this confined geometry. Many calculations for metallic clusters have been reported (e.g., [851]), including quantum molecular dynamics (QMD) simulations [852] that account for thermal broadening due to dynamical motion of the nuclei.

Semiconductor clusters, or "quantum dots," terminated by H or other elements, are of great interest because of their enhanced optical properties (see, e.g., [854]). Figure 21.2 shows TDLDA spectra for selected structures compared to independent-particle spectra calculated using a real-space finite difference method as described in Section 12.8 [575]. For the smallest system (the $\mathrm{SiH}_{4}$ molecule), TDLDA results in a small shift to lower energy due to the fact that the electron and hole are confined to a small volume reducing the energy due to Coulomb attraction. For large clusters, still much smaller than the wavelength of light, the spectra shift to higher energy and have a plasma-like resonance that couples to light because of finite size effects.

The lowest-energy excitations and an effective gap corresponding to the onset of strong absorption are shown in Fig. 21.3 for H-terminated Si clusters as a function of diameter. Experimental results are shown for molecules and for large clusters. The gap increases with decreasing cluster size due to quantum confinement effects, and it is evident that the theory explains the trends in general agreement with experiment. For example, the gap of

[^2]![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-11_703_708_247_482.jpg)
Figure 21.1. Example of optical spectrum of a metal cluster ( $\mathrm{Li}_{8}$ ) calculated [853] using TDDFT with the adiabatic local density approximation (TDLDA). The inset shows the structure of the cluster determined by the usual ground-state density functional theory. The resulting spectrum is significantly changed from the spherical jellium model, in better agreement with experiment (arrow), and from the noninteracting approximation (dotted line labeled $\sigma_{0}$ ). From [853].

![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-11_606_604_1232_532.jpg)
Figure 21.2. Optical spectra of selected hydrogen-terminated Si systems, from the molecule $\mathrm{SiH}_{4}$ to the $\mathrm{Si}_{147} \mathrm{H}_{100}$ cluster. The solid lines are spectra from TDLDA calculations, which are compared to uncorrected independent-particle spectra (dotted lines) that follows from Eq. (21.9) applied to a finite system. For $\mathrm{SiH}_{4}$, TDLDA results in a small shift to lower energy; whereas for the larger clusters, the intensity of the optical absorption shifts to higher energy due to Coulomb interactions and finite size effects (see text). Provided by I. Vasiliev

![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-12_645_692_247_491.jpg)
Figure 21.3. Optical properties of Si nanoclusters predicted using TDLDA compared to experiment. The graph shows results for the lowest gap and for a higher energy, designating a threshold in the optical strength that corresponds to experimental assignments of an effective gap [575]. Provided by I. Vasiliev

Si nanoclusters is increased above the bulk gap, and it has been found that Si clusters can become efficient emitters of blue light [855].

## Real-Time Calculations for Molecules and Clusters

In the real time approach for a small system, the dipole moment $\mathbf{d}(t)$ is calculated as the response to an applied field, and the polarizability $\alpha(\omega)=d(\omega) / E(\omega)$ is found by a Fourier transform. A convenient procedure is to start with the equilibrium ground-state wavefunctions $\psi_{i}^{\bar{E}}$ of the system in a constant applied electric field $\bar{E}$, i.e., with an added potential $\Delta V(\mathbf{r})=-e \bar{E} x$. At time $t=0$, the field $\bar{E}$ is suddenly removed and for $t>0$ the system evolves as given by the time-dependent Schrödinger equation (21.3) with initial independent-particle states $\psi_{i}^{\bar{E}}$ at $t=0$ and the usual Kohn-Sham hamiltonian, which is a function of time for $t>0$ since the density $n(\mathbf{r}, t)$ is a function of time, even though there is no applied field. The electric field $E(\omega)$ is the Fourier transform of a step function $E(t)=\bar{E} \Theta(-t)$, so that $E(\omega)=\bar{E} /(i \omega)$ and $\operatorname{Im} \alpha(\omega)=\omega \operatorname{Re} d(\omega) / \bar{E}$. Finally, $d(\omega)$ can be calculated from $d(t)=e \int d \mathbf{r} n(\mathbf{r}, t) x=e \sum_{i}\left\langle\psi_{i}(t)\right| x\left|\psi_{i}(t)\right\rangle$ and Fourier transforming to give

$$
d(\omega)=\int_{0}^{\infty} d t \mathrm{e}^{\mathrm{i} \omega t-\delta t} d(t)
$$

where the factor $\mathrm{e}^{-\delta t}$ is a damping factor introduced for convergence at large times.
There are various methods for real time calculations. One of the first is that of Yabana and Bertsch [846], who used a real-space grid and a hamiltonian with a finite difference

![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-13_668_1264_243_202.jpg)
Figure 21.4. Spectrum of the dipole strength function $S(\omega)$ for $\mathrm{C}_{60}$ calculated by two different methods. The solid lines were calculated using a real-time method and local orbitals [856], and the dashed lines with the dynamic density functional perturbation theory method (DFPT) and a plane wave basis [843]. At the right are the spectra for a large energy range; the agreement is good, given that the local orbital basis is limited and not expected to accurately represent high energy states, and plane waves are affected by the size of the simulation box. At the left is the comparison with experiment in the low-energy range. The calculations agree well as expected in the low-energy range. However, the energies of the transitions are somewhat too low, and the strengths of the first two peaks are much too low, compared to experiment [857]. The spectra at the left are normalized to have the same integrated weight in the low-energy range for comparison with the experiment. Provided by D. Rocca and A. Tsolakidis

expression for the kinetic energy. The real-time method can also be implemented [856] for localized bases where it is difficult to exponentiate the hamiltonian operator directly. Instead, it is convenient to use the Crank-Nicholson form in Eq. (21.20). This is explicitly unitary and inversion of the matrix $1+i \hat{H} \frac{\delta t}{2}+\cdots$ can be done since a local orbital basis can be very small and since there can be efficient inversion methods for matrices close to the unit matrix.

Figure 21.4 shows the spectra for a $\mathrm{C}_{60}$ molecule calculated by the real-time local orbital method [856] and the dynamic density functional perturbation theory (DFPT) method described in Section 21.5 [843] with a very large basis of plane waves. The real-time simulation was done with time step of $2.128 \times 10^{-17} \mathrm{~s}$ and the total time of 130 fs , and both methods are expected to be accurate in the low-energy range. As shown at the left in Fig. 21.4, the two methods agree well and agree with experiment except for the peak at $\approx 5 \mathrm{eV}$. The two calculations used LDA and PBE functionals respectively, but they should be comparable since the spectra of the two functionals are comparable.

The lowest-energy excitations in the calculated spectra are too low and are too weak compared to the experiment. A discrepancy in the energies $\approx 0.4 \mathrm{eV}$ is also found in a large survey of other systems [857, 858]. Presumably the difference from experiment is
due to the approximations for the functional - the local or semilocal form and the adiabatic approximation. Possibly this is related to the failures of such functionals for excitons in solids, as described in the following section; in any case, it shows that care must be taken in the interpretation of the calculations.

### 21.8 Optical Properties of Crystals

Crystals and other macroscopic systems with size much greater than the wavelength of light are in the opposite regime from clusters. The optical properties are governed by the dielectric function $\epsilon(\omega)$ instead of polarizability $\alpha(\omega)$, and similarly for nonlinear response functions. In that case the appropriate formulation is in terms of the macroscopic currents $\mathbf{j}$ and the vector potential $\mathbf{A}$ instead of charge $n$ and the scalar potential $V$. This is what is done in the response function for independent particles in Eq. (21.9) and the goal is to take into account effects of exchange and correlation using TDDFT. ${ }^{6}$

Even though there is a vast amount of work on molecules and clusters, TDDFT has been used much less to calculate optical properties of crystals. There are difficulties in solids that can be understood on physical grounds. One of the great problems with LDA and GGA functionals is the large error in the bandgap. One might hope that TDDFT would be a way to alleviate this problem, but, in fact, the gap in TDDFT is the same as the difference in Kohn-Sham eigenvalues. This can be seen immediately from the form of the response functions, e.g., in the left side of Eq. (21.10). In a crystal there is a continuum of excitations and the absorption is the imaginary part of a response function. Since the independentparticle response function $\chi^{0}(\omega)$ has an imaginary part across the entire band, it follows that the full function $\chi(\omega)$ also has an imaginary part fo the same range. Thus even though the shape of the spectrum may change, the band edges do not.

Another problem has been the subject of much work for years: the difficulty is describing excitons, which are bound states below the continuum. Excitons are very important in the spectra of many solids, as illusioned by the spectrum for LiF in Figs. 2.26 and 21.5. Since the band edges do not change in TDDFT, the only way a bound state can emerge from the theory is for there to be a pole in the response function. From the expression in the left part of Eq. (21.10), this can happen if the denominator in the response function $\chi$ goes to zero, which means that the Kernel $K$ has to be sufficiently large and attractive. However, we can see from Eq. (21.14) that this can happen only if the term $f_{\mathrm{xc}}$ is sufficiently large that it overcomes the $1 /\left|\mathbf{r}-\mathbf{r}^{\prime}\right|$ Coulomb term. It is a stringent requirement for a functional of only the density to capture this behavior and, in general, it means that $f_{\mathrm{xc}}^{\sigma \sigma^{\prime}}\left(\mathbf{r}, \mathbf{r}^{\prime}, \omega\right)$ must be a very nonlocal function. Local and semilocal functionals are not enough; they simply fail to capture the physics. There have been various suggestions to create functionals $f_{\mathrm{xc}}$ that

[^3]![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-15_633_1272_242_202.jpg)
Figure 21.5. Optical spectra of LiF calculated in the independent-particle approximation and using time-dependent DFT (TDDFT) for two functionals and time-dependent Hartree-Fock. The left panel illustrates the fact that a short range functional (in this case HSE) does not produce bound states below the band gap in either the IPA or TDDFT. The right figure illustrates the fact that the gap in Hartree-Fock is much too large (off the scale and not shown) and time-dependent Hartree-Fock (TDHF) leads to bound excitons that are at energy too high and have oscillator strength too large. In the middle is the results for a range-separated hybrid functional with a long-range part (screened Hartree-Fock), which has an exciton series below the gap. The middle and right panels are calculated using real-time methods; the spectrum of the hybrid functional is the Fourier transforms of the data shown in the lower part of Fig. 21.6. Provided by C. D. Pemmaraju with the curves for HSE provided by J. Paier

have the requisite properties. The history and the physics issues are discussed, for example, in the reviews by Onida et al. [841] and Maitra [395].

Both problems are addressed by hybrid functionals. There is considerable improvement in the bandgaps for many materials, as shown in Fig. 2.24. Regarding the ability to describe excitons, there is a qualitative effect. If the exchange has a long-range form such as the Coulomb interaction in Hartree-Fock, it leads to an attractive term that can lead to a pole in the response function, i.e., an exciton that is a bound state in the gap. A range-separated hybrid functional like HSE that has only short-range exchange may improve bandgaps but only functionals with long-range Hartree-Fock-like exchange can describe excitons.

It is ironic that for more than 80 years (at least since the work of Bardeen in 1936 [254]) condensed matter theory has striven to avoid the Hartree-Fock singularity at the Fermi surface of metals discussed in Chapter 5. A great accomplishment of the RPA invented by Pines and others in the 1950s was to show that summation of selected diagrams leads to short-range exchange and correlation. (See the list of classic books at the end of this chapter and extensive discussion in [1].) Now we find that long-range Hartree-Fock-like effects must be included to solve another problem in condensed matter. A working strategy is to create functionals that have long-range exchange scaled by $1 / \epsilon$ so that it vanishes in a metal.

This can be justified in the approach of range-separated functions: just as keeping only a short range was justified in part by arguments based on RPA, so also can keeping some amount of the long-range exchange be justified in insulators. Such functions are described in Section 9.3 and two examples are the "tuned" [859] and DDH functionals [244], each supported by arguments to make functionals with no parameters.

## Optical Spectrum of LiF

The spectrum of LiF is a quintessential example of an exciton. As shown in Fig. 2.26, the spectrum is completely dominated by the exciton feature at $\approx 12.6 \mathrm{eV}$ that looks nothing like an independent-particle spectrum. Since the gap is known experimentally to be around 14.2 eV , the peak is well below the continuum with a binding energy more than 1 eV , which indicates strongly bound localized state referred to as a Frenkel exciton.

Here we illustrate the spectra calculated in two ways. The spectrum shown in Fig. 2.26 was calculated using the response function method based on the Casida equations in Section 21.4 [253]. The functional used in the calculation is one called "optimally tuned" with screened exchange [859], a range-separated hybrid functional in which the range is proposed to be an appropriate variable that determines the character of the nonlocal exchange with the added feature of the fraction of long-range exchange scaled by $1 / \epsilon$. In a finite system like a molecule, the range is determined by a condition on the asymptotic form of the wavefunctions [440]. However, this does not work in a solid and the range was adjusted to give the correct experimental gap. With that adjustment, the spectrum including the exciton feature is in excellent agreement with experiment. Any similar functional would give such exciton features, but the gap and the exciton energy might be further from the experimental values.

The results of a real-time calculation for the same problem are shown in the middle panel of Fig. 21.5. The functional was chosen to be very close to the one used in Fig. 2.26 so they could be compared, and the calculations were done using numerical local orbitals as defined in SIESTA (see Section 15.4). The spectra calculated by the two methods are very close except for two peaks above the main exciton, which are more clearly resolved in Fig. 21.5. The independent-particle approximation is also shown, which makes it clear that the sharp peaks are bound states below the continuum. The other panels of Fig. 21.5 are chosen to illustrate the limits of no long-range to full long-range exchange. At the left is the spectrum calculated with the short-range HSE06 functional from [252] that totally misses the exciton peaks. At the right is the Hartree-Fock spectrum, where the gap is so large that the continuum is off the scale, and there are exciton peaks with oscillator strength and binding energy that are much too large. The middle panel shows that TDDFT with this hybrid functional captures features of short-range exchange and correlation that go beyond Hartree-Fock, and also features that are like a screened version of Hartree-Fock.

## Real-Time Calculations for Macroscopic Systems

The real-time calculations for clusters in Section 21.7 were in terms of the dipole moment induced by an electric field. Yabana and Bertsch [860] proposed an analogous real-time

![](./images/fbc163f0-ec06-4711-8c4a-be599cfcee15-17_801_1120_245_275.jpg)
Figure 21.6. Real-time current $j(t)$ that is the response to a delta function electric field (a step in the vector potential $\mathbf{A}(t)$ at time $t=0$ ). At the top is $j(t)$ that decays quickly as a function of time, which leads to a smooth spectrum like that for the short-range functional shown at the left in Fig. 21.5. At the bottom is $j(t)$ that leads to a spectrum shown in the middle of Fig. 21.5, where the sharp peaks result from oscillations in the current that last for a long time with little decay. Figure provided by C. D. Pemmaraju

approach for the dielectric function in solids in terms of the vector potential and currents that avoids the fundamental difficulties of attempting to define dipoles in macroscopic systems. ${ }^{7}$ In practice the calculations involve a procedure analogous to the calculations for a cluster. The system is perturbed by a step in the vector potential $\mathbf{A}(t)$ at time $t_{0}$ (a delta function in the macroscopic electric field at time $t_{0}$ since $\left.\mathbf{E}(t)=d \mathbf{A}(t) / d t\right)$, and the calculation of the resulting macroscopic average of the current $\mathbf{j}\left(t-t_{0}\right)$ as a function of time. Since the effect of vector potential in the hamiltonian, $\mathbf{p} \rightarrow \mathbf{p}-(e / c) \mathbf{A}$, a step in $\mathbf{A}$ is equivalent to a shift of the momenta. In the calculation this amounts to modifying the ground-state wavefunction by replacing each Bloch function $u_{\mathbf{k}}$ by the function $u_{\mathbf{k}+\delta \mathbf{k}}$, which creates a state that is not an eigenstate. The system is propagated forward in time with the periodic potential $V(\mathbf{G})$ updated as the density $n(\mathbf{G})$ changes, and the current is calculated as a function of time. The spectrum as a function of frequency is calculated using a Fourier transform, the same as for the time-dependent moment in finite systems.

[^4]Two examples are shown in Fig. 21.6. The bottom curve is the real-time data that leads to the TDDFT spectra in the middle panel Fig. 21.5. Sharp peaks in the spectrum are due to the oscillations in the current that last for a long time as shown in the figure. The top curve is for a case where the current decays rapidly as a function of time, which leads to a smooth spectrum with few sharp features like that shown at the left in Fig. 21.5.

### 21.9 Beyond the Adiabatic Approximation

A fully satisfactory time-dependent theory must go beyond the adiabatic approximation [862]. In the time-dependent Kohn-Sham approach with a functional of the density, it must be nonlocal in time, i.e., a function of time differences, in order to take into account the way that the transitions to excited states affect the functional. The conceptual issues are discussed in references such as the reviews by Maitra [395] and Burke [247] and other sources listed at the end of the end of this chapter. There is, however, an alternative approach along the lines of the generalized Kohn-Sham (GKS) theory in Section 9.2. A functional in terms of the wavefunctions automatically creates a dependence on the excitations. The importance of long-range exchange that can be included in functionals of the wavefunctions was stressed in Section 21.8, where it makes possible the description of excitons. This corresponds to a pole in the response function, which is an extreme frequency dependence. Methods like "exact exchange" (EXX) [863] and hybrid functionals that include exchange to varying extents are known to improve many aspects of description of spectra. There are connections to other problems such as current functionals [342, 343], and this is an area that deserves attention in the future.

## SELECT FURTHER READING

The basic theory of dielectric functions and optical properties is in the texts listed at the end of Chapter 2.

Original paper:
Runge, E. and Gross, E. K. U., "Density-functional theory for time-dependent systems," Phys. Rev. Lett. 52:997-1000, 1984.

Reviews:
Maitra, N. T., "Perspective: Fundamental aspects of time-dependent density functional theory," J. Chem. Phys. 144:220901, 2016. Provides insights into many aspects of TDDFT along with many references.
Onida, G. Reining, L., and Rubio, A., "Electronic excitations: Density-functional versus many-body Green's-function approaches," Rev. Mod. Phys. 74:601, 2002. Describes relation of TDDFT and Green's function methods. See also the companion book [1].

Books that provide in-depth exposition of theory and applications:
Ferre, N., Filatov, M. and Huix-Rotllant, M., editors, Density-Functional Methods for Excited States (Springer International, Switzerland, 2016).
Marques, M. A. L., et al., editors, Fundamentals of Time-Dependent Density Functional Theory, Lecture Notes in Physics 837 (Springer, Berlin, 2012).

Marques, M. A. L., et al., editors, Time-Dependent Density Functional Theory, Lecture Notes in Physics 706 (Spinger, Berlin, 2016). See also earlier volumes in the series.
Ullrich, C., Time-Dependent Density-Functional Theory: Concepts and Applications (Oxford University Press, Oxford, 2012).

## Exercises

21.1 Derive expression (21.9) for the dielectric function for noninteracting particles. Show that the first term in brackets comes from the $A^{2}$ term as stated following Eq. (21.9).
21.2 Derive the matrix equation (21.15) for the eigenvalues $\Omega_{n}$ of the density response from the preceding equations. Although there are many indices, this is a straightforward problem of matrix manipulation.
21.3 The general approach for exponentials of operators is described in the text preceding Eq. (21.18); it is also used in the rotation operators in Appendix N . Show that for any operator $A$, $\exp (A)=\sum_{i}\left|\zeta_{i}\right\rangle \exp \left(A_{i}\right)\left\langle\zeta_{i}\right|$, where $A_{i}$ and $\zeta_{i}$ are eigenvalues and eigenvectors of $A$. Hint: use the power series expansion of the exponential and show the equivalence of the two sides of the equation at every order.
21.4 Show that Eq. (21.18) has error of order $\propto \delta t^{2}$. Would the error be of the same order if the potential part were not symmetric?
21.5 Derive the $f$ sum rule for the strength function $S(\omega)$ in Eq. (21.23). The proof is analogous to Exercise E.2.
21.6 Describe qualitatively how the top and bottom parts of Fig. 21.6 lead to broad and sharp spectra, respectively.


[^0]:    ${ }^{1}$ Here the electron charge $-e$ is explicitly included to avoid confusion, since the standard definition of $\mathbf{E}$ is the field acting on a positive charge.
    ${ }^{2}$ The issues are recounted in Chapter 24 and the resolution is part of the saga leading to Berry phases and topology. However, those developments are not needed here.

[^1]:    ${ }^{3}$ The expressions in terms of the wavefunctions or density matrix are general and apply with nonlocal potential operators, such the exchange term, in Hartree-Fock and hybrid functionals.

[^2]:    ${ }^{4}$ Here $m, e$, and $\hbar$ are written out explicitly to enable the conversion to usual units.
    ${ }^{5}$ In a bulk solid, the plasma peak [280] is due to a longitudinal density response dominated by a peak in the inverse function $\operatorname{Im} \epsilon^{-1}(\omega)$ for $\omega \approx \omega_{p}$; however, in a small confined system, the distinction between longitudinal and transverse is lost and there is a peak in the absorption of light at $\omega \approx \omega_{p}$.

[^3]:    ${ }^{6}$ The method is still called TDDFT even through it involves the macroscopic $\mathbf{A}$ and $\mathbf{j}$. There are changes in the periodic charge density in each cell induced by the macroscopic fields, and it is more useful to treat them in terms of potentials and densities. The induced fields are called local field corrections. They can be dealt with as described in Section E. 4 and they are included in the TDDFT response function.

[^4]:    ${ }^{7}$ Of course, the general ideas have been known for a long time in many contexts. A closely related method was proposed by Krieger and Iafrate [861], who considered the time evolution of electrons in a homogeneous electric field and a fixed crystal potential. The new feature in TDDFT is that the effective hamiltonian varies during the evolution.

