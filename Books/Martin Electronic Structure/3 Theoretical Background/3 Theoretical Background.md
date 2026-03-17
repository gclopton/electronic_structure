
Our understanding of the electronic structure of matter is based on quantum mechanics and statistical mechanics. This chapter reviews fundamental definitions and expressions valid for many-body systems of interacting electrons and useful, simplified formulas that apply for noninteracting particles. This material is the foundation for subsequent chapters, which deal with the theory and practical methods for electronic structure.

# 3.1 Basic Equations for Interacting Electrons and Nuclei

The subject of this book is the ongoing progress toward describing properties of matter from theoretical methods firmly rooted in the fundamental equations. Thus our starting point is the hamiltonian for the system of electrons and nuclei, ${ }^{1}$

> [!definition] Full Hamiltonian for electrons and nuclei (Eq. 3.1)
>
> $$
> \begin{aligned}
> \hat{H}= & -\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2}-\sum_{i, I} \frac{Z_{I} e^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}+\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|} \\
> & -\sum_{I} \frac{\hbar^{2}}{2 M_{I}} \nabla_{I}^{2}+\frac{1}{2} \sum_{I \neq J} \frac{Z_{I} Z_{J} e^{2}}{\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|}
> \end{aligned}
> $$



where electrons are denoted by lowercase subscripts and nuclei - with charge $Z_{I}$ and mass $M_{I}$ - are denoted by uppercase subscripts. The challenge in the theory of electronic

[^0]structure is to develop methods that can treat the effects of the electron-electron interactions with sufficient accuracy that one can predict the diverse array of phenomena exhibited by matter starting from Eq. (3.1). It is most informative and productive to start with the fundamental many-body theory. Many expressions, such as the force theorem, are more easily derived in the full theory with no approximations. It is then straightforward to specialize to independent-particle approaches and the actual formulas needed for most of the following chapters.

There is only one term in Eq. (3.1) that can be regarded as small, the inverse mass of the nuclei $1 / M_{I}$. A perturbation series can be defined in terms of this parameter, which is expected to have general validity for the full interacting system of electrons and nuclei. If we first set the mass of the nuclei to infinity, then the kinetic energy of the nuclei can be ignored. This is the Born-Oppenheimer or adiabatic approximation [90] defined in Appendix C, which is an excellent approximation for many purposes, e.g., the calculation of nuclear vibration modes in most solids [91, 180]. In other cases, it forms the starting point for perturbation theory in electron-phonon interactions, which is the basis for understanding electrical transport in metals, polaron formation in insulators, certain metalinsulator transitions, and the BCS theory of superconductivity. Thus we shall focus on the hamiltonian for the electrons, in which the positions of the nuclei are parameters.


> [!derivation] Derivation 1: Born-Oppenheimer reduction of the full Hamiltonian
> Write the total energy as an expectation value of the Born–Oppenheimer electronic Hamiltonian. To compute the energy contribution from the electron-nuclear interaction, do you need to know the full $N$-electron wavefunction? Show why or why not.

Starting from Eq. (3.1), separate the terms into electronic kinetic energy, electron-nucleus attraction, electron-electron interaction, nuclear kinetic energy, and nucleus-nucleus interaction:

$$
\begin{aligned}
\hat{H}
&= \left(-\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2}\right)
 + \left(-\sum_{i, I} \frac{Z_{I} e^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}\right)
 + \left(\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}\right) \\
&\quad + \left(-\sum_{I} \frac{\hbar^{2}}{2 M_{I}} \nabla_{I}^{2}\right)
 + \left(\frac{1}{2} \sum_{I \neq J} \frac{Z_{I} Z_{J} e^{2}}{\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|}\right).
\end{aligned}
$$

Group the first three terms into an electronic operator at fixed nuclear positions:

$$
\hat{H}
= \hat{H}_{e}(\{\mathbf{R}_{I}\})
-\sum_{I} \frac{\hbar^{2}}{2 M_{I}} \nabla_{I}^{2}
+\frac{1}{2} \sum_{I \neq J} \frac{Z_{I} Z_{J} e^{2}}{\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|},
$$

with

$$
\hat{H}_{e}(\{\mathbf{R}_{I}\})
= -\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2}
-\sum_{i, I} \frac{Z_{I} e^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}
+\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}.
$$

In the Born-Oppenheimer approximation, the nuclei are taken to be infinitely heavy to leading order, so

$$
\frac{1}{M_{I}} \to 0
\qquad \Longrightarrow \qquad
-\sum_{I} \frac{\hbar^{2}}{2 M_{I}} \nabla_{I}^{2} \to 0.
$$

Therefore

$$
\hat{H}
\approx \hat{H}_{e}(\{\mathbf{R}_{I}\})
+\frac{1}{2} \sum_{I \neq J} \frac{Z_{I} Z_{J} e^{2}}{\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|}.
$$

Identifying

$$
\hat{T}=-\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2},
\qquad
\hat{V}_{\mathrm{ext}}=-\sum_{i, I} \frac{Z_{I} e^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|},
\qquad
\hat{V}_{\mathrm{int}}=\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|},
$$

and

$$
E_{I I}=\frac{1}{2} \sum_{I \neq J} \frac{Z_{I} Z_{J} e^{2}}{\left|\mathbf{R}_{I}-\mathbf{R}_{J}\right|},
$$

one obtains Eq. (3.2),

$$
\hat{H}=\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}}+E_{I I}.
$$

The small parameter is the inverse nuclear mass, equivalently the electron-to-nuclear mass ratio $m_{e}/M_{I}$ (or, in vibrational estimates, $\sqrt{m_{e}/M_{I}}$). It is physically reasonable because nuclei are much heavier than electrons, so their motion is much slower and the electrons can usually adjust adiabatically to a nearly fixed nuclear configuration.

The approximation breaks down when nonadiabatic coupling between electronic and nuclear motion is not small, for example near degeneracies or avoided crossings of electronic surfaces, in light-atom systems, or when proton/nuclear quantum effects are important. In such cases one loses access to effects that require explicit coupled electron-nuclear dynamics, such as vibronic mixing, phonon-assisted transitions beyond adiabatic perturbation theory, nonradiative transitions at conical intersections, and other electron-phonon nonadiabatic phenomena.

> [!lesson] Separation of scales and the Born-Oppenheimer approximation
>
> - **When two sets of degrees of freedom have very different masses (or energy scales), the heavy/slow ones can be treated as fixed parameters.** The small parameter is the mass ratio $m_e/M_I$. This strategy — freezing slow degrees of freedom and solving for fast ones — is the prototype for adiabatic approximations throughout physics.
> - **Always identify the small parameter.** The validity of any perturbative or adiabatic approximation depends on having a well-defined expansion parameter. Here it is $m_e/M_I$ (or $\sqrt{m_e/M_I}$ for vibrational estimates).
> - **Know when the approximation fails.** The Born-Oppenheimer approximation breaks down near electronic degeneracies, avoided crossings, and conical intersections — anywhere the electronic state changes rapidly with nuclear position so that the adiabatic assumption is violated.

Ignoring the nuclear kinetic energy, the fundamental hamiltonian for the theory of electronic structure can be written as

> [!definition] Electronic Hamiltonian (Eq. 3.2)
>
> $$
> \hat{H}=\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}}+E_{I I}
> $$

If we adopt Hartree atomic units $\hbar=m_{e}=e=4 \pi / \epsilon_{0}=1$, then the terms may be written in the simplest form. The kinetic energy operator for the electrons $\hat{T}$ is

$$
\hat{T}=\sum_{i}-\frac{1}{2} \nabla_{i}^{2}
$$

since

$$
\hat{T}
=-\frac{\hbar^{2}}{2 m_{e}} \sum_{i} \nabla_{i}^{2}
=-\frac{1^{2}}{2 \cdot 1} \sum_{i} \nabla_{i}^{2}
=-\frac{1}{2} \sum_{i} \nabla_{i}^{2}.
$$

$\hat{V}_{\text {ext }}$ is the potential acting on the electrons due to the nuclei,

$$
\hat{V}_{\mathrm{ext}}=\sum_{i, I} V_{I}\left(\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|\right) ;
$$

for the bare Coulomb form,

$$
\hat{V}_{\mathrm{ext}}
=-\sum_{i, I} \frac{Z_{I} e^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}
=-\sum_{i, I} \frac{Z_{I} \cdot 1^{2}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}
=-\sum_{i, I} \frac{Z_{I}}{\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|}.
$$

$\hat{V}_{\text {int }}$ is the electron-electron interaction,

$$
\hat{V}_{\mathrm{int}}=\frac{1}{2} \sum_{i \neq j} \frac{1}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}
$$

since

$$
\hat{V}_{\mathrm{int}}
=\frac{1}{2} \sum_{i \neq j} \frac{e^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}
=\frac{1}{2} \sum_{i \neq j} \frac{1^{2}}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}
=\frac{1}{2} \sum_{i \neq j} \frac{1}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}.
$$

and the final term $E_{I I}$ is the classical interaction of nuclei with one another and any other terms that contribute to the total energy of the system but are not germane to the problem of describing the electrons. Here the effect of the nuclei upon the electrons is included in a fixed potential "external" to the electrons. This general form is still valid if the bare nuclear Coulomb interaction is replaced by a pseudopotential that takes into account effects of core electrons (except that the potentials are "nonlocal"; see Chapter 11). Also, other "external potentials," such as electric fields and Zeeman terms, can readily be included. Thus, for electrons, the hamiltonian, Eq. (3.2), is central to the theory of electronic structure.

## 3.1.1 Schrödinger Equation for the Many-Body Electron System

The fundamental equation governing a nonrelativistic quantum system is the timedependent Schrödinger equation,

$$
i \hbar \frac{\mathrm{~d} \Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)}{\mathrm{d} t}=\hat{H} \Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)
$$

where the many-body wavefunction for the electrons is $\Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right) \equiv \Psi\left(\mathbf{r}_{1}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N} ; t\right)$, the spin is assumed to be included in the coordinate $\mathbf{r}_{i}$. Concretely, this means each $\mathbf{r}_i$ stands for the pair $(\mathbf{r}_i, \sigma_i)$ of spatial position and spin index, and every "integration over $\mathbf{r}_i$" is shorthand for $\sum_{\sigma_i} \int d^3 r_i$. In what follows, spin sums will sometimes be written explicitly — especially when a spatial coordinate is singled out and its integral is evaluated, leaving the spin sum with nowhere to hide. The wavefunction must be antisymmetric in the coordinates of the electrons $\mathbf{r}_{1}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N}$. The eigenstates of Eq. (3.6) can be written as $\Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)=\Psi\left(\left\{\mathbf{r}_{i}\right\}\right) \mathrm{e}^{-\mathrm{i}(E / \hbar) t}$. Even though it is not feasible to actually solve the equations for many interacting electrons, it is very useful and instructive to define properties such as the energy, density, forces, and excitations in the full many-body framework before making approximations.

For an eigenstate, the time-independent expression for any observable is an expectation value of an operator $\hat{O}$, which involves an integral over all coordinates,


> [!definition] Expectation Value of a Local Operator
> 
> $$
> \langle\hat{O}\rangle=\frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
> $$
> 



> [!exercise] Expectation Value of a Local Operator
> Let $x_i \equiv\left(\mathbf{r}_i, \sigma_i\right)$ and $\Psi\left(x_1, \ldots, x_N\right)$. 
> 1.) Write the expectation value of a local operator $\hat{O}=O\left(x_1, \ldots, x_N\right)= \frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$ for an $N$-particle wavefunction in the complete position-spin basis.
> 2.) Write the expression in the case where the many-body coordinate is written compactly as $X=\left(x_1, \ldots, x_N\right)$.
> 3.) Write the expression for the case where $\Psi$ is normalized.


##### Part A

$$\langle\hat{O}\rangle=\frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N \Psi^*\left(x_1, \ldots, x_N\right) O\left(x_1, \ldots, x_N\right) \Psi\left(x_1, \ldots, x_N\right)}{\sum \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$


##### Part B

$$\langle\hat{O}\rangle=\frac{\sum_{\left\{\sigma_i\right\}} \int d R \Psi^*(X) O(X) \Psi(X)}{\sum_{\left\{\sigma_i\right\}} \int d R|\Psi(X)|^2}, \quad d R \equiv d^3 r_1 \cdots d^3 r_N$$




##### Part C


$$\langle\hat{O}\rangle=\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N \Psi^*\left(x_1, \ldots, x_N\right) O\left(x_1, \ldots, x_N\right) \Psi\left(x_1, \ldots, x_N\right)$$





The density of particles $n(\mathbf{r})$, which plays a central role in electronic structure theory, is given by the expectation value of the density operator $\hat{n}(\mathbf{r})=\sum_{i=1, N} \delta\left(\mathbf{r}-\mathbf{r}_{i}\right)$,



> [!definition] State-Dependent Electron Density of the Many-Electron Wavefunction (Eq. 3.8)
>
> $$
> n(\mathbf{r})=\frac{\langle\Psi| \hat{n}(\mathbf{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
> $$



> [!exercise] State-Dependent Electron Density of the Many-Electron Wavefunction
> Let $x_i \equiv\left(\mathbf{r}_i, \sigma_i\right)$ and $\Psi\left(x_1, \ldots, x_N\right)$. 
> 1.) Write the expression for the state-dependent electron density $n(\mathbf{r})$ of the $N$-electron wavefunction in the complete position-spin basis.
> 2.) Write the expression for the case where $\Psi$ is normalized.
> 3.) Write the expression for the case in which the electron wavefunction is antisymmetric.





$$n(\mathbf{r})=\frac{\langle\Psi| \hat{n}(\mathbf{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$$
$$=\frac{\langle\Psi| \sum_{i=1}^N \delta\left(\mathbf{r}-\hat{\mathbf{r}}_i\right)|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}$$

$$=\frac{\sum_{\sigma_1 \cdots \sigma_N} \int d \mathbf{r}_1 \cdots d \mathbf{r}_N \Psi^*\left(x_1, \ldots, x_N\right)\left(\sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)\right) \Psi\left(x_1, \ldots, x_N\right)}{\sum_{\sigma_1 \cdots \sigma_N} \int d \mathbf{r}_1 \cdots d \mathbf{r}_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$

$$=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$




### Case 1: $\Psi$ is normalized

$$n(\mathbf{r})=\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)$$



### Case 2: $\Psi$ is antisymmetric 


For an antisymmetric electron wavefunction, all particles are equivalent, so this is often written as

$$
n(\mathbf{r})=N \sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_2 \cdots d^3 r_N\left|\Psi\left(\mathbf{r} \sigma_1, x_2, \ldots, x_N\right)\right|^2,
$$

where the sum over $\sigma_1$ is included as part of the full spin sum.








---



The total energy is the expectation value of the hamiltonian. Using $\hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II}$, the linearity of the expectation value gives

$$
E=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
=\langle\hat{T}\rangle + \langle\hat{V}_{\text{ext}}\rangle + \langle\hat{V}_{\text{int}}\rangle + E_{II},
$$

The external potential is a one-body operator, $\hat{V}_{\text{ext}} = \sum_{i} V_{\text{ext}}(\mathbf{r}_{i})$. Its expectation value therefore reduces by the same logic used for the density operator (Derivation 2): each term in the sum over $i$ gives the same integral after exploiting the exchange symmetry of $|\Psi|^{2}$. Writing the intermediate steps explicitly,


---


> [!Derivation] Electron-density form of the one-body external potential operator
> Let 
> 
> $$n(\mathrm{r})=\frac{\langle\Psi| \hat{n}(\mathrm{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle} =\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2}$$
> 
> Show that the expectation value for the external-potential energy $\hat{V}_{\text {ext }}$ for the wavefunction $\Psi\left(x_1, \ldots, x_N\right)$ that depends on $3 N$ spatial coordinates plus spin variables, can be reduced to a form that depends only on the electron density $n(\mathbf{r})$ which depends only on the three coordinates of a single point in space.


For an $N$-electron system in an external scalar potential $v_{\text {ext }}(\mathbf{r})$, the external-potential operator is

$$
\hat{V}_{\mathrm{ext}}=\sum_{i=1}^N v_{\mathrm{ext}}\left(\mathbf{r}_i\right) .
$$


The claim is that its expectation value in the many-body state $\Psi\left(x_1, \ldots, x_N\right)$, where $x_i=\left(\mathbf{r}_i, \sigma_i\right)$, can be written entirely in terms of the one-body density $n(\mathbf{r})$.

Start from the normalized expectation value:

$$
\left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\frac{\langle\Psi| \hat{V}_{\mathrm{ext}}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
$$


Using the coordinate representation,

$$
\left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N v_{\mathrm{ext}}\left(\mathbf{r}_i\right)}{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2} .
$$


Now insert the identity

$$
v_{\mathrm{ext}}\left(\mathbf{r}_i\right)=\int d^3 r v_{\mathrm{ext}}(\mathbf{r}) \delta\left(\mathbf{r}-\mathbf{r}_i\right)
$$


Then

$$
\sum_{i=1}^N v_{\text {ext }}\left(\mathbf{r}_i\right)=\sum_{i=1}^N \int d^3 r v_{\text {ext }}(\mathbf{r}) \delta\left(\mathbf{r}-\mathbf{r}_i\right)=\int d^3 r v_{\text {ext }}(\mathbf{r}) \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right) .
$$


Substituting this into the expectation value gives

$$
\left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N|\Psi|^2 \int d^3 r v_{\mathrm{ext}}(\mathbf{r}) \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\langle\Psi \mid \Psi\rangle}
$$


Interchange the order of integration:

$$
\left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\int d^3 r v_{\mathrm{ext}}(\mathbf{r}) \frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\langle\Psi \mid \Psi\rangle}
$$


But the quantity in brackets is exactly the density $n(\mathbf{r})$ from your definition:

$$
n(\mathbf{r})=\frac{\sum_{\sigma_1, \ldots, \sigma_N} \int d^3 r_1 \cdots d^3 r_N\left|\Psi\left(x_1, \ldots, x_N\right)\right|^2 \sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right)}{\langle\Psi \mid \Psi\rangle} .
$$


Therefore,

$$
\left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\int d^3 r n(\mathbf{r}) v_{\mathrm{ext}}(\mathbf{r})
$$


This is the desired reduction. Although the wavefunction $\Psi\left(x_1, \ldots, x_N\right)$ depends on all $3 N$ spatial coordinates and all spin variables, the external-potential energy depends only on the one-particle density $n(\mathbf{r})$, which is a function of just the three coordinates $\mathbf{r}$.



> [!NOTE]
> If you want the operator form stated compactly, one often writes
> 
> $$
> \hat{n}(\mathbf{r})=\sum_{i=1}^N \delta\left(\mathbf{r}-\mathbf{r}_i\right), \quad \hat{V}_{\mathrm{ext}}=\int d^3 r v_{\mathrm{ext}}(\mathbf{r}) \hat{n}(\mathbf{r})
> $$
> 
> so that immediately
> 
> $$
> \left\langle\hat{V}_{\mathrm{ext}}\right\rangle=\int d^3 r v_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})
> $$
> 
> 
> That is the key DFT result: the external part of the energy is a functional of the density alone.
> 


> [!lesson] One-body operators reduce to density integrals
>
> - **The expectation value of any one-body multiplicative operator can be written as an integral over the electron density $n(\mathbf{r})$.** This is because the operator acts on one coordinate at a time, and the remaining $N-1$ integrations produce the density. This reduction is the reason the density plays such a central role in electronic structure.
> - **The exchange symmetry of $|\Psi|^2$ produces a factor of $N$.** Since $|\Psi|^2$ is symmetric under particle exchange (even though $\Psi$ itself is antisymmetric), every electron contributes identically, giving $N$ identical terms.
> - **Two-body operators and derivative operators do not reduce to density integrals.** The kinetic energy involves $\nabla^2$ (not multiplication), and $\hat{V}_{\text{int}}$ couples pairs of coordinates. This is why the full many-body problem cannot be solved in terms of $n(\mathbf{r})$ alone without additional constructions (e.g., the exchange-correlation functional).

Thus the total energy takes the form

> [!theorem] Total energy as expectation value (Eq. 3.9)
>
> $$
> E=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle} \equiv\langle\hat{H}\rangle=\langle\hat{T}\rangle+\left\langle\hat{V}_{\mathrm{int}}\right\rangle+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}
> $$

where the expectation value of the external potential has been explicitly written as a simple integral over the density function. The final term $E_{I I}$ is the electrostatic nucleus-nucleus (or ion-ion) interaction, which is essential in the total energy calculation but is only a classical additive term in the theory of electronic structure.


---

> [!derivation] Derivation
> Starting from the Rayleigh quotient
> 
> $$
> E[\Psi]=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle},
> $$
> 
> show that if the energy functional is stationary under arbitrary variations of the wavefunction, then the eigenstates of $\hat{H}$ are precisely the stationary points of the energy expectation-value functional. In particular, show that:
> a. The Rayleigh-Ritz variational principle leads to the time-independent Schrödinger equation.
> b. The same equation follows from a constrained variational principle with a Lagrange multiplier enforcing normalization.
> c. We have shown that the Rayleigh-quotient variation and the Lagrange-multiplier constrained variation are mathematically equivalent. Which formulation is more convenient for a given derivation or approximation?


##### Part A: Stationarity of the Rayleigh quotient

Let

$$
E[\Psi]=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}, \quad N[\Psi]=\langle\Psi| \hat{H}|\Psi\rangle, \quad D[\Psi]=\langle\Psi \mid \Psi\rangle
$$


Assume $\hat{H}$ is Hermitian. We vary $|\Psi\rangle$ and its complex conjugate independently, as is standard in variational calculus for complex wavefunctions.


Start from

$$
E[\Psi]=\frac{N}{D}
$$


Its first variation is

$$
\delta E=\delta\left(\frac{N}{D}\right)=\frac{\delta N D-N \delta D}{D^2}=\frac{1}{D}(\delta N-E \delta D) .
$$


Now compute $\delta N$ and $\delta D$ :

$$
\begin{gathered}
\delta N=\delta\langle\Psi| \hat{H}|\Psi\rangle=\langle\delta \Psi| \hat{H}|\Psi\rangle+\langle\Psi| \hat{H}|\delta \Psi\rangle \\
\delta D=\delta\langle\Psi \mid \Psi\rangle=\langle\delta \Psi \mid \Psi\rangle+\langle\Psi \mid \delta \Psi\rangle
\end{gathered}
$$


Substitute these into $\delta E$ :

$$
\delta E=\frac{1}{\langle\Psi \mid \Psi\rangle}[\langle\delta \Psi| \hat{H}|\Psi\rangle+\langle\Psi| \hat{H}|\delta \Psi\rangle-E\langle\delta \Psi \mid \Psi\rangle-E\langle\Psi \mid \delta \Psi\rangle]
$$


Group terms:

$$
\delta E=\frac{1}{\langle\Psi \mid \Psi\rangle}[\langle\delta \Psi|(\hat{H}-E)|\Psi\rangle+\langle\Psi|(\hat{H}-E)|\delta \Psi\rangle]
$$



Because $\hat{H}$ is Hermitian,

$$
\langle\Psi|(\hat{H}-E)|\delta \Psi\rangle=(\langle\delta \Psi|(\hat{H}-E)|\Psi\rangle)^*,
$$

so

$$
\delta E=\frac{2 \operatorname{Re}\langle\delta \Psi|(\hat{H}-E)|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
$$


If the functional is stationary under arbitrary variations, then $\delta E=0$ for every $\delta \Psi$. Since $\delta \Psi$ is arbitrary, this is possible only if

$$
(\hat{H}-E)|\Psi\rangle=0
$$

that is,

$$
\hat{H}|\Psi\rangle=E|\Psi\rangle .
$$


This is exactly the time-independent Schrödinger equation.
In coordinate representation, this becomes

$$
\hat{H} \Psi(\mathbf{r})=E \Psi(\mathbf{r})
$$


So the Rayleigh-Ritz stationarity condition implies the TISE.
Now for the converse: if $|\Psi\rangle$ is an eigenstate,

$$
\hat{H}|\Psi\rangle=E|\Psi\rangle
$$

then substituting into the variation formula gives

$$
\delta E=\frac{1}{\langle\Psi \mid \Psi\rangle}[\langle\delta \Psi|(\hat{H}-E)|\Psi\rangle+\langle\Psi|(\hat{H}-E)|\delta \Psi\rangle]=0 .
$$


So every eigenstate is a stationary point of the energy functional.
Hence the stationary points of the Rayleigh quotient are precisely the eigenstates of $\hat{H}$ (more precisely: the normalized vectors in eigenspaces of $\hat{H}$; in a degenerate eigenspace, any normalized linear combination is also stationary).

A compact way to see the "precisely" statement is to expand in the eigenbasis $\{|n\rangle\}$ of $\hat{H}$ :

$$
|\Psi\rangle=\sum_n c_n|n\rangle, \quad \hat{H}|n\rangle=E_n|n\rangle
$$


Then

$$
E[\Psi]=\frac{\sum_n\left|c_n\right|^2 E_n}{\sum_n\left|c_n\right|^2}
$$


Varying with respect to $c_n^*$ gives

$$
0=\frac{\partial E}{\partial c_n^*}=\frac{c_n\left(E_n-E\right)}{\sum_m\left|c_m\right|^2}
$$


Therefore,

$$
c_n\left(E_n-E\right)=0 \quad \text { for all } n
$$


So any coefficient $c_n \neq 0$ must satisfy $E_n=E$. Thus $|\Psi\rangle$ can only have support inside a single eigenspace. That is exactly an eigenstate (or, in the degenerate case, any vector in that degenerate eigenspace).


##### Part B: Constrained Variational Principle with Normalization



Now impose normalization explicitly by introducing a Lagrange multiplier $\lambda$. Define

$$
\mathcal{F}\left[\Psi, \Psi^*, \lambda\right]=\langle\Psi| \hat{H}|\Psi\rangle-\lambda(\langle\Psi \mid \Psi\rangle-1)
$$


Take the variation:

$$
\delta \mathcal{F}=\delta\langle\Psi| \hat{H}|\Psi\rangle-\lambda \delta\langle\Psi \mid \Psi\rangle-(\langle\Psi \mid \Psi\rangle-1) \delta \lambda .
$$


Expanding the first two terms,

$$
\delta \mathcal{F}=\langle\delta \Psi| \hat{H}|\Psi\rangle+\langle\Psi| \hat{H}|\delta \Psi\rangle-\lambda\langle\delta \Psi \mid \Psi\rangle-\lambda\langle\Psi \mid \delta \Psi\rangle-(\langle\Psi \mid \Psi\rangle-1) \delta \lambda .
$$


Group terms:

$$
\delta \mathcal{F}=\langle\delta \Psi|(\hat{H}-\lambda)|\Psi\rangle+\langle\Psi|(\hat{H}-\lambda)|\delta \Psi\rangle-(\langle\Psi \mid \Psi\rangle-1) \delta \lambda .
$$


Because $\delta \Psi, \delta \Psi^*$, and $\delta \lambda$ are arbitrary, stationarity requires

$$
\begin{gathered}
(\hat{H}-\lambda)|\Psi\rangle=0, \\
\langle\Psi|(\hat{H}-\lambda)=0, \\
\langle\Psi \mid \Psi\rangle=1 .
\end{gathered}
$$


Thus

$$
\hat{H}|\Psi\rangle=\lambda|\Psi\rangle .
$$


So the constrained variational principle also gives the time-independent Schrödinger equation, with $\lambda$ playing the role of the eigenvalue.

To identify $\lambda$, left-multiply by $\langle\Psi|$ :

$$
\langle\Psi| \hat{H}|\Psi\rangle=\lambda\langle\Psi \mid \Psi\rangle .
$$


Using normalization $\langle\Psi \mid \Psi\rangle=1$,

$$
\lambda=\langle\Psi| \hat{H}|\Psi\rangle=E .
$$


Therefore,

$$
\hat{H}|\Psi\rangle=E|\Psi\rangle .
$$



##### Part C


In practice, the Lagrange-multiplier form is often easier when normalization is an explicit constraint you want to enforce during the calculation, especially when you may also have other constraints. It turns the problem into stationarity of

$$
\langle\Psi| \hat{H}|\Psi\rangle-\lambda(\langle\Psi \mid \Psi\rangle-1),
$$

which is usually algebraically cleaner than differentiating a quotient. It is also the natural form when you have multiple orthogonality constraints, such as when deriving equations for excited states or Hartree-Fock-type orbitals.

The Rayleigh quotient form,

$$
E[\Psi]=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle},
$$

is often nicer when you want the normalization-independence built in from the start. It makes the scale invariance obvious: multiplying $\Psi$ by any nonzero constant does not change $E[\Psi]$. It is also conceptually useful when emphasizing that the energy is defined on rays in Hilbert space rather than on normalized representatives only.


> [!NOTE] When to use the Lagrange-multiplier form vs when to use the Rayleigh quotient form
> A good rule of thumb is this. If you are doing a formal derivation of the Schrödinger equation, or handling explicit constraints, use the Lagrange-multiplier form. If you want to emphasize the variational meaning of the energy or the upper-bound property in approximation theory, the Rayleigh quotient is often the more natural language.
> 
> **Note:** Explicit constraints include things like:
> 1.) Requiring normalization
> 2.) Fixing particle number
> 3.) Enforcing orthogonality among orbitals
> 4.) Imposing symmetry restrictions that are not already built into the trial form
> 5.) imposing more than one constraint like normalization and orthogonality to the ground state


> [!lesson] The variational principle as a computational strategy
>
> - **Eigenstates are stationary points of the energy functional.** The Schrödinger equation is not an independent postulate — it is the stationarity condition of the Rayleigh-Ritz variational principle. Any method that finds an energy minimum automatically finds an eigenstate (within the space searched).
> - **Constrained minimization with Lagrange multipliers is equivalent to direct variation of the Rayleigh quotient.** Both routes give the same eigenvalue equation. Choose whichever is more convenient for the problem at hand.
> - **Restricting the trial wavefunction to a tractable class and minimizing within that class is the foundation of all practical electronic structure methods.** Hartree-Fock restricts to single determinants; DFT works with the density; quantum Monte Carlo uses stochastic sampling of trial states. The variational principle guarantees that the resulting energy is an upper bound to the true ground-state energy.

---

The ground-state wavefunction $\Psi_{0}$ is the state with the lowest energy, which can be determined, in principle, by minimizing the total energy with respect to all the parameters in $\Psi\left(\left\{\mathbf{r}_{i}\right\}\right)$, with the constraint that $\Psi$ must obey the particle symmetry and any conservation laws. Excited states are saddle points of the energy with respect to variations in $\Psi$.

## 3.1.2 Ground and Excited Electronic States

> [!question]
>
> (a) Why must the ground state of an interacting electron system be treated by nonperturbative methods, whereas excitations can often be treated perturbatively?
> (b) Name two theoretical approaches that are primarily ground-state methods and explain why this is significant.
> (c) What ground-state properties can reveal whether a material is a metal or an insulator, even though this might seem like an excited-state property?

The distinction between ground and excited states pointed out in Chapter 2 is equally obvious when approached from the point of view of solving the many-body equations for the electrons. Except in special cases, the ground state must be treated by nonperturbative methods because the different terms in the energy equation are large and tend to cancel. The properties of the ground state include the total energy, electron density, and correlation functions. From the correlation functions one can derive properties that at first sight would not be considered to be ground-state properties, such as whether the material is a metal or an insulator. In any case, one needs to establish which state is the ground state, often comparing states that are very different in character but similar in energy.

On the other hand, excitations in condensed matter are usually small perturbations on the entire system. These perturbations can be classified into variations of the ground electronic state (e.g., small displacements of the ions in phonon modes) or true electronic excitations (e.g., optical electronic excitations). In both cases, perturbation theory is the appropriate tool. Using perturbation techniques, one can calculate excitation spectra and the real and imaginary parts of response functions. Nevertheless, even in this case one needs to know the ground state, since the excitations are perturbations on the ground state.

These approaches apply both in independent-particle and in many-body problems. The ground state is special in both cases and it is interesting that both density functional theory

[^1]and quantum Monte Carlo are primarily ground-state methods. The role of perturbation theory is rather different in independent-particle and many-body problems - in the latter, it plays a key role in the basic formulation of the problem in diagrammatic perturbation series and in suggesting the key ideas for summation of appropriate diagrams.

# 3.2 Coulomb Interaction in Condensed Matter

It is helpful to clarify briefly several points that are essential to a proper definition of energies in extended systems with long-range Coulomb interaction. For a more complete analysis see Appendix F. The key points are as follows:

- Any extended system must be neutral if the energy is to be finite.
- Terms in the energy must be organized in neutral groups for actual evaluation.



> [!derivation] Derivation
> Let $E^{CC}$ represent the classical coulomb energies and $E_{Hartree}$ represent the self-interaction energy of the density $n(\mathbf{r})$ treated as a classical charge density.
> **Part I:** For an extended neutral Coulomb system
> 
> a.) show that the combination $E_H+\int d^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}$ s the classical electrostatic energy of the total charge distribution, while the three terms are not, in general, separately well-defined absolute energies. 
> b.) show that the exact total energy can be rewritten as $E=\langle\hat{T}\rangle+\left(\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_H\right)+E^{\mathrm{CC}}$ so that the energy is decomposed into kinetic, classical Coulomb, and nonclassical exchange-correlation contributions.
> c.) show that correlation effects are short ranged.
> 
>  **Part II:** Why is charge neutrality a prerequisite for finite energies in periodic systems?





> [!equation] Classical Coulomb energy grouping (Eq. 3.14)
>
> $$
> E^{\mathrm{CC}}=E_{\mathrm{Hartree}}+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I},
> $$


> [!definition] Hartree energy (Eq. 3.15)
>
> $$
> E_{\text {Hartree }}=\frac{1}{2} \int \mathrm{~d}^{3} r \mathrm{~d}^{3} r^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} .
> $$



> [!equation] Total energy decomposition with exchange-correlation (Eq. 3.16)
>
> $$
> E=\langle\hat{T}\rangle+\left(\left\langle\hat{V}_{\text {int }}\right\rangle-E_{\text {Hartree }}\right)+E^{\mathrm{CC}},
> $$



Using atomic units, let

$$
\rho_I(\mathbf{r})=\sum_I Z_I \delta\left(\mathbf{r}-\mathbf{R}_I\right), \quad \rho_{\mathrm{tot}}(\mathbf{r})=\rho_I(\mathbf{r})-n(\mathbf{r}),
$$

so that neutrality of the extended system means

$$
\int d^3 r \rho_{\mathrm{tot}}(\mathbf{r})=0
$$


Also define

$$
\begin{gathered}
E_H=\frac{1}{2} \iint d^3 r d^3 r^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \\
V_{\mathrm{ext}}(\mathbf{r})=-\sum_I \frac{Z_I}{\left|\mathbf{r}-\mathbf{R}_I\right|}=-\int d^3 r^{\prime} \frac{\rho_I\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
\end{gathered}
$$

and

$$
E_{I I}=\frac{1}{2} \sum_{I \neq J} \frac{Z_I Z_J}{\left|\mathbf{R}_I-\mathbf{R}_J\right|}
$$



##### Part 1A


The classical Coulomb energy of the total charge distribution is

$$
E^{C C}=\frac{1}{2} \iint d^3 r d^3 r^{\prime} \frac{\rho_{\mathrm{tot}}(\mathbf{r}) \rho_{\mathrm{tot}}\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
$$

with the nuclear self-energies excluded, so that the ionic part reduces to $E_{I I}$ rather than including the infinite $I=J$ self-terms.

Now expand $\rho_{\text {tot }}=\rho_I-n$ :

$$
E^{C C}=\frac{1}{2} \iint \frac{\left[\rho_I(\mathbf{r})-n(\mathbf{r})\right]\left[\rho_I\left(\mathbf{r}^{\prime}\right)-n\left(\mathbf{r}^{\prime}\right)\right]}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} d^3 r d^3 r^{\prime}
$$


Expanding term by term gives

$$
E^{C C}=\frac{1}{2} \iint \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} d^3 r d^3 r^{\prime}-\iint \frac{\rho_I(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} d^3 r d^3 r^{\prime}+\frac{1}{2} \iint \frac{\rho_I(\mathbf{r}) \rho_I\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} d^3 r d^3 r^{\prime}
$$


The first term is exactly $E_H$. The middle term is

$$
-\iint \frac{\rho_I(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} d^3 r d^3 r^{\prime}=\int d^3 r^{\prime} V_{\mathrm{ext}}\left(\mathbf{r}^{\prime}\right) n\left(\mathbf{r}^{\prime}\right)
$$

because $V_{\text {ext }}$ is the potential generated by the ionic charge density. The last term, with the point-charge self-terms removed, is $E_{I I}$. Therefore

$$
E^{C C}=E_H+\int d^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}
$$


So the combination

$$
E_H+\int d^3 r V_{\text {ext }}(\mathbf{r}) n(\mathbf{r})+E_{I I}
$$

is precisely the classical electrostatic energy of the total neutral charge distribution.


In an extended neutral Coulomb system, the electron-electron, electron-ion, and ion-ion terms each involve long-range $1 / r$ interactions between subsystems with individually infinite total charge. Because of that, each term separately is generally divergent, or at best only conditionally convergent and dependent on summation convention or boundary prescription. Only after the three pieces are combined into the neutral total-charge expression do the long-range divergences cancel. That is why $E^{C C}$ is well-defined, while the three pieces are not, in general, separately meaningful absolute energies.


##### Part 1B


The exact Born-Oppenheimer total energy is

$$
E=\langle\hat{T}\rangle+\left\langle\hat{V}_{\mathrm{int}}\right\rangle+\int d^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}
$$


Add and subtract $E_H$ :

$$
E=\langle\hat{T}\rangle+\left(\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_H\right)+\left(E_H+\int d^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}\right)
$$


Using part (a),

$$
E_H+\int d^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}=E^{C C}
$$

so

> [!NOTE] Total energy decomposition with exchange-correlation (Eq. 3.16)
> $$
> E=\langle\hat{T}\rangle+\left(\left\langle\hat{V}_{\text {int }}\right\rangle-E_H\right)+E^{C C}
> $$


That is the desired decomposition. The interpretation is the following. The term $E^{C C}$ contains all of the purely classical Coulomb electrostatics of the total charge distribution. The term

$$
\left\langle\hat{V}_{\text {int }}\right\rangle-E_H
$$

is the nonclassical correction: it measures the difference between the true electron-electron interaction energy and the Hartree energy obtained by treating $n(\mathbf{r})$ as a continuous classical charge cloud. This difference contains exchange and Coulomb-correlation effects, including removal of the unphysical Hartree self-interaction.


A useful way to make that explicit is through the pair density

$$
n^{(2)}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\left\langle\sum_{i \neq j} \delta\left(\mathbf{r}-\mathbf{r}_i\right) \delta\left(\mathbf{r}^{\prime}-\mathbf{r}_j\right)\right\rangle,
$$

for which

$$
\left\langle\hat{V}_{\mathrm{int}}\right\rangle=\frac{1}{2} \iint d^3 r d^3 r^{\prime} \frac{n^{(2)}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
$$


Writing

$$
n^{(2)}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right) g\left(\mathbf{r}, \mathbf{r}^{\prime}\right)
$$

with $g$ the pair-correlation function, gives

$$
\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_H=\frac{1}{2} \iint d^3 r d^3 r^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)\left[g\left(\mathbf{r}, \mathbf{r}^{\prime}\right)-1\right]}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
$$


So this term vanishes only if the electrons really behaved like an uncorrelated classical charge cloud with $g=1$, which they do not.

A small precision point: in Kohn-Sham DFT, the full $E_{x c}$ also contains the kinetic correction $T-T_s$. Here, since you have kept the exact interacting kinetic energy $\langle\hat{T}\rangle$ intact, the term $\left\langle\hat{V}_{\text {int }}\right\rangle-E_H$ is the nonclassical part of the interaction energy.


##### Part 1C

To show why correlation effects are short-ranged, introduce the exchange-correlation hole. Define the conditional density around an electron fixed at $\mathbf{r}$ by

$$
n_{\text {cond }}\left(\mathbf{r}^{\prime} \mid \mathbf{r}\right)=\frac{n^{(2)}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)}{n(\mathbf{r})},
$$

and then define

$$
n_{x c}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=n_{\text {cond }}\left(\mathbf{r}^{\prime} \mid \mathbf{r}\right)-n\left(\mathbf{r}^{\prime}\right) .
$$


Equivalently,

$$
n_{x c}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=n\left(\mathbf{r}^{\prime}\right)\left[g\left(\mathbf{r}, \mathbf{r}^{\prime}\right)-1\right] .
$$


Then

$$
\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_H=\frac{1}{2} \int d^3 r n(\mathbf{r}) \int d^3 r^{\prime} \frac{n_{x c}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} .
$$


The exact exchange-correlation hole satisfies the sum rule

$$
\int d^3 r^{\prime} n_{x c}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=-1
$$


That means one electron's worth of charge is missing around a reference electron. Now split

$$
n_{x c}=n_x+n_c,
$$

into exchange and correlation pieces. The exchange hole already satisfies

$$
\int d^3 r^{\prime} n_x\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=-1,
$$


so the correlation hole must satisfy

$$
\int d^3 r^{\prime} n_c\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=0
$$


That last equation is the key fact. The correlation hole carries zero net charge. Therefore it produces no long-range monopole Coulomb field. In a multipole expansion, a neutral charge distribution has no $1 / r$ tail from net charge; its far-field potential decays faster than $1 / r$. Thus correlation cannot contribute to the long-range classical electrostatics. It only rearranges charge locally around the electron.

This is the precise sense in which correlation effects are short-ranged: once the classical Coulomb term has been extracted into $E^{C C}$, the remaining correlation contribution comes from a neutral local rearrangement of charge around each electron, not from unscreened long-range electrostatics.

Equivalently, if one writes

$$
E_c^{\mathrm{int}}=\frac{1}{2} \int d^3 r n(\mathbf{r}) \int d^3 u \frac{n_c(\mathbf{r}, \mathbf{r}+\mathbf{u})}{|\mathbf{u}|}
$$

then because

$$
\int d^3 u n_c(\mathbf{r}, \mathbf{r}+\mathbf{u})=0
$$

the large- $|\mathbf{u}|$ contributions cancel rather than accumulating as a long-range Coulomb term. The dominant contribution comes from the neighborhood of the reference electron, which is exactly what "short-ranged" means here.


So the conceptual conclusion of the whole exercise is:

$$
E=\underbrace{\langle\hat{T}\rangle}_{\text {kinetic }}+\underbrace{E^{C C}}_{\text {classical Coulomb }}+\underbrace{\left(\left\langle\hat{V}_{\text {int }}\right\rangle-E_H\right)}_{\text {nonclassical exchange/correlation part of interaction }},
$$

and the reason this decomposition is useful is that all long-range Coulomb physics sits in $E^{C C}$, while the nonclassical correction is a local, short-ranged effect associated with the exchange-correlation hole.



##### Part II


Charge neutrality is required because the Coulomb interaction is long-ranged, and in a periodic system you are effectively summing that long-range interaction over infinitely many repeated copies of the cell. If the unit cell carries a nonzero net charge, then each copy also carries that same nonzero charge, so the crystal is an infinite array of uncompensated charge. The Coulomb potential of such a distribution does not decay fast enough for the electrostatic energy per cell to remain finite.

The cleanest way to see this is from the classical Coulomb energy of the total charge density $\rho(\mathbf{r})$,

$$
E^{C C}=\frac{1}{2} \iint d^3 r d^3 r^{\prime} \frac{\rho(\mathbf{r}) \rho\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
$$


In a periodic solid, $\rho(\mathbf{r})$ is periodic, so it is natural to write it in reciprocal space:

$$
\rho(\mathbf{r})=\sum_{\mathbf{G}} \rho_{\mathbf{G}} e^{i \mathbf{G} \cdot \mathbf{r}} .
$$


Then the Coulomb energy per cell takes the schematic form

$$
E^{C C} \sim \frac{1}{2 \Omega} \sum_{\mathbf{G} \neq 0} \frac{4 \pi}{G^2}\left|\rho_{\mathbf{G}}\right|^2
$$

provided the $\mathbf{G}=0$ term is absent. But

$$
\rho_{\mathbf{G}=0}=\frac{1}{\Omega} \int_{\Omega} \rho(\mathbf{r}) d^3 r
$$

is just the average charge density in the unit cell, i.e. the net cell charge divided by the cell volume. If the unit cell is neutral, then

$$
\int_{\Omega} \rho(\mathbf{r}) d^3 r=0
$$

so $\rho_{\mathbf{G}=0}=0$, and the dangerous $1 / G^2$ singularity at $G=0$ is removed. If the cell is not neutral, then the $G=0$ contribution is nonzero, and the Coulomb kernel

$$
\frac{4 \pi}{G^2}
$$

blows up as $G \rightarrow 0$. That is the reciprocal-space signature of the divergence.
The same point can be understood in real space. If one cell has net charge $Q \neq 0$, then at large distances it looks like a point charge $Q$, so the interaction between distant cells scales like

$$
\frac{Q^2}{R} .
$$


Now sum this over all cells in the infinite lattice. Because the number of cells at radius $R$ grows like $R^2$, the shell contribution behaves like

$$
R^2 \cdot \frac{1}{R} \sim R,
$$

and the integral over $R$ diverges. So the electrostatic energy per cell is not finite. Neutrality is what cancels that monopole term. Once the net charge vanishes, the far field is much weaker, and the long-range divergence is removed.



This is why, in periodic electronic-structure calculations, a non-neutral cell is fundamentally problematic. A charged supercell does not represent a well-defined infinite Coulomb system unless one adds some compensating background or other regularization. In practice, codes often introduce a uniform neutralizing background for charged cells, but then the absolute electrostatic energy is no longer the physical energy of an isolated charged periodic crystal; it is the energy of the charged cell plus that artificial compensating background, and finite-size corrections are usually needed.

So the essential lesson is this: in a periodic Coulomb system, neutrality is what removes the $G=0$ singularity, eliminates the long-range monopole field, and makes the electrostatic energy per cell finite. Without neutrality, the repeated lattice carries infinite self-repulsion, and the energy is not well-defined.






> [!lesson] Coulomb energy grouping and the short-range nature of exchange-correlation
>
> - **In extended systems, individual energy terms diverge; only neutral groupings are finite.** The Hartree, external-potential, and ion-ion terms are each divergent on their own, but their sum $E^{\text{CC}}$ — the classical Coulomb energy of the total charge distribution — is finite provided the system is charge-neutral.
> - **Exchange and correlation effects are short-ranged.** Subtracting the classical Coulomb energy from the full interaction energy leaves only the non-classical piece $\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}$, which measures the local depletion of charge around each electron. This is why local and semi-local approximations to exchange-correlation (LDA, GGA) work as well as they do.
> - **Charge neutrality is a prerequisite for finite energies in periodic systems.** This condition must be enforced in any practical calculation on extended matter.

[^2]
# 3.3 Force and Stress Theorems

## 3.3.1 Force (Hellmann-Feynman) Theorem

One of the beautiful theorems of physics is the "force theorem" for the force conjugate to any parameter in the hamiltonian. This is a very general idea perhaps formulated first in 1927 by Ehrenfest [263], who recognized that it is crucial for the correspondence principle of quantum and classical mechanics. He established the relevant relation by showing that the expression for force given below equals the expectation value of the operator corresponding to acceleration $\left\langle\mathrm{d}^{2} \hat{x} / \mathrm{d} t^{2}\right\rangle$. The ideas are implicit in the 1928 work of Born and Fock [264], and the explicit formulas used today were given by Güttiger [265] in 1932. The formulas were included in the treatises of Pauli [266] and Hellmann [267], the latter reformulating them as a variational principle in a form convenient for application to molecules. In 1939, when he was an undergraduate, Feynman [268] derived the force theorem and explicitly pointed out that the force on a nucleus is given strictly in terms of the charge density, independent of the electron kinetic energy, exchange, and correlation. Thus as an "electrostatic theorem," it should apparently be attributed to Feynman. The nomenclature "Hellmann-Feynman theorem" has been widely used, apparently originating with Slater [48]; however, we will use the term "force theorem."

> [!derivation] Derivation 6: Force (Hellmann-Feynman) theorem
> Derive the expression Eq. (3.19) for the force on a nucleus. The result is remarkable: despite the electrons having kinetic energy and mutual interactions that both change as nuclei move, the force depends only on the electron density. What principle causes all other contributions to vanish, and under what circumstances can this cancellation fail?


Let $\mathbf{R}_I$ represent the position of the nucleus, $n(\mathbf{r})$ represent the unperturbed density, $\langle\Psi \mid \Psi\rangle=1$ (for convenience) and

$$E=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle} \equiv\langle\hat{H}\rangle=\langle\hat{T}\rangle+\left\langle\hat{V}_{\text {int }}\right\rangle+\int \mathrm{d}^3 r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}$$



a.) For a local potential, show that the force $\mathbf{F}_I$ depends only on the density $n$ of the electrons and the other nuclei.
b.) For a local potential, show that the force theorem applied to a nucleus leads to the force being exactly the electric field at the given nucleus due to the charge density of the rest of the system (electrons and other nuclei) times the charge of the given nucleus.
c.) When does this simplification fail? Show why.

The force conjugate to any parameter describing a system, such as the position of a nucleus $\mathbf{R}_{I}$, can always be written

$$
\mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}
$$

Starting from Eq. (3.9) and assuming $\langle\Psi \mid \Psi\rangle=1$ for convenience,

$$
E=\langle\Psi|(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})|\Psi\rangle+E_{II}.
$$

Differentiating with respect to $\mathbf{R}_{I}$ gives

$$
\begin{aligned}
\frac{\partial E}{\partial \mathbf{R}_{I}}
&=
\left\langle\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\middle|(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})\middle|\Psi\right\rangle
+\left\langle\Psi\middle|\frac{\partial \hat{V}_{\mathrm{ext}}}{\partial \mathbf{R}_{I}}\middle|\Psi\right\rangle \\
&\quad
+\left\langle\Psi\middle|(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})\middle|\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\right\rangle
+\frac{\partial E_{II}}{\partial \mathbf{R}_{I}},
\end{aligned}
$$

because $\hat{T}$ and $\hat{V}_{\mathrm{int}}$ have no explicit dependence on nuclear positions. For an exact stationary state,

$$
(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})|\Psi\rangle=E_{\mathrm{el}}|\Psi\rangle,
$$

so the first and third terms become

$$
\begin{aligned}
\left\langle\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\middle|(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})\middle|\Psi\right\rangle
+\left\langle\Psi\middle|(\hat{T}+\hat{V}_{\mathrm{ext}}+\hat{V}_{\mathrm{int}})\middle|\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\right\rangle
&=
E_{\mathrm{el}}
\left(
\left\langle\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\middle|\Psi\right\rangle
+\left\langle\Psi\middle|\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\right\rangle
\right) \\
&=
E_{\mathrm{el}} \frac{\partial}{\partial \mathbf{R}_{I}}\langle\Psi \mid \Psi\rangle \\
&= 0.
\end{aligned}
$$

Thus

$$
-\frac{\partial E}{\partial \mathbf{R}_{I}}
=-\left\langle\Psi\middle|\frac{\partial \hat{V}_{\mathrm{ext}}}{\partial \mathbf{R}_{I}}\middle|\Psi\right\rangle
-\frac{\partial E_{II}}{\partial \mathbf{R}_{I}}.
$$

Now $\partial \hat{V}_{\mathrm{ext}}/\partial \mathbf{R}_{I}$ is still a one-body operator. Since

$$
\hat{V}_{\mathrm{ext}}=\sum_{j} V_{\mathrm{ext}}(\mathbf{r}_{j}),
$$

it follows that

$$
\frac{\partial \hat{V}_{\mathrm{ext}}}{\partial \mathbf{R}_{I}}
=\sum_{j}\frac{\partial V_{\mathrm{ext}}(\mathbf{r}_{j})}{\partial \mathbf{R}_{I}}.
$$

Therefore, by the same reduction used in Derivations 2 and 3,

$$
\left\langle\Psi\middle|\frac{\partial \hat{V}_{\mathrm{ext}}}{\partial \mathbf{R}_{I}}\middle|\Psi\right\rangle
=\int \mathrm{d}^{3}r\,n(\mathbf{r})\frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \mathbf{R}_{I}}.
$$

Hence the force depends only on the density $n$ of the electrons and the other nuclei,

> [!theorem] Force (Hellmann-Feynman) theorem (Eq. 3.19)
>
> $$
> \mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}=-\int \mathrm{d}^{3} r n(\mathbf{r}) \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \mathbf{R}_{I}}-\frac{\partial E_{I I}}{\partial \mathbf{R}_{I}} .
> $$

Here $n(\mathbf{r})$ is the unperturbed density and the other nuclei are held fixed, as shown schematically in the left-hand side of Fig. I.1. Since each nucleus interacts with the electrons and other nuclei via Coulomb interactions, the right-hand side of Eq. (3.19) can be shown (Exercise 3.3) to equal the nuclear charge times the total electric field, which is the electrostatic theorem of Feynman. The cancellation of the kinetic-energy and electron-electron terms occurs because the exact electronic state is stationary with respect to variations of the wavefunction at fixed nuclear positions. This cancellation can fail if the electronic state is not exact or not fully variational with respect to the chosen representation, for example in an incomplete basis (Pulay terms), or if the ionic potential is nonlocal, in which case the force cannot be written solely in terms of the density.

> [!lesson] The force theorem and variational stationarity
>
> - **At a variational extremum, the wavefunction-derivative terms vanish.** When differentiating $E = \langle\Psi|\hat{H}|\Psi\rangle$ with respect to any parameter $\lambda$, the terms involving $\partial\Psi/\partial\lambda$ vanish if $\Psi$ is an exact eigenstate, because $\hat{H}|\Psi\rangle = E|\Psi\rangle$ and $\partial\langle\Psi|\Psi\rangle/\partial\lambda = 0$. Only the explicit $\lambda$-dependence of $\hat{H}$ survives. This is the single most important simplification in the theory of forces, stresses, and generalized response.
> - **For local potentials, the force on a nucleus depends only on the electron density.** Despite the electrons having kinetic energy and mutual interactions, all those contributions cancel by stationarity. The force is purely electrostatic — nuclear charge times the total electric field.
> - **This simplification fails when the wavefunction is not fully variational** — e.g., with an incomplete basis set (requiring Pulay corrections) or with nonlocal pseudopotentials (where the force cannot be written solely in terms of the density).

---

In the case of nonlocal potentials (such as pseudopotentials), the force cannot be expressed solely in terms of the electron density. However, the original expression is still valid and useful expressions can be directly derived from

$$
-\frac{\partial E}{\partial \mathbf{R}_{I}}=-\langle\Psi| \frac{\partial \hat{H}}{\partial \mathbf{R}_{I}}|\Psi\rangle-\frac{\partial E_{I I}}{\partial \mathbf{R}_{I}}
$$

Because the force theorem depends on the requirement that the electronic states are at their variational minimum, it follows that there must be a continuum of "force theorems" that corresponds to the addition of any linear variation in $\Psi$ or $n$ to the above expression. Although such terms vanish in principle, they can have an enormous impact upon the accuracy and physical interpretation of resulting formulas. The most relevant example in electronic structure is the case of core electrons: It is more physical and more accurate computationally to move the electron density in the core region along with the nucleus rather than holding the density strictly fixed. The reason is that core electrons are tightly bound to the nucleus and move rigidly with it to an excellent approximation; the "frozen density" assumed in the bare force theorem is therefore a poor zeroth-order description of what actually happens when a nucleus is displaced, and including the core density motion absorbs a large part of the higher-order corrections into the leading term. Methods to accomplish this are described in Appendix I and illustrated in Figure I.1.

> [!question]
>
> (a) Under what conditions does the Hellmann-Feynman force theorem fail to give the correct force as the simple derivative of the total energy?
> (b) What are Pulay corrections, and when must they be included in a practical calculation?
> (c) Why is it more physical and computationally accurate to move the core electron density along with the nucleus rather than holding the density strictly fixed?

Finally, there are drawbacks to the fact that expressions for the force theorem depend on the electronic wavefunction being an exact eigenstate. If the basis is not complete, or the state is approximated, then there may be additional terms. For example, if the basis is not complete and it changes as the positions of the nuclei move, then Pulay corrections [269] must be explicitly included so that the expression for the force given by the force theorem is identical to the explicit derivative of the energy (Exercise 3.4). Explicit expressions are given for use in independent-particle Kohn-Sham calculations in Section 7.5.

## 3.3.2 Stress (Generalized Virial) Theorem

A physically different type of variation is a scaling of space, which leads to the "stress theorem" [162, 163] for total stress. This is a generalization of the well-known virial theorem for pressure $P$, which was derived in the early days of quantum mechanics (see references in Appendix G). An elegant derivation was given by Fock [270] in terms of "Streckung des Grundgebietes" ("stretching of the ground state").

> [!derivation] Derivation 7: Stress (generalized virial) theorem from scaling of space
> The force theorem treats displacement of a nucleus. What happens if you instead scale all of space uniformly? Derive the stress tensor Eq. (3.23) by considering the energy response to a strain deformation, and show that its trace gives the virial theorem Eq. (3.24). Why does the same variational argument that simplified the force theorem also work here? (Exercise 3.5.)

The stress is a generalized force for which the ideas of the force theorem can be applied. The key point is that for a system in equilibrium, the stress tensor $\sigma_{\alpha \beta}$ is minus the derivative of the energy with respect to strain $\epsilon_{\alpha \beta}$ per unit volume (see also Eq. (2.4))

$$
\sigma_{\alpha \beta}=-\frac{1}{\Omega} \frac{\partial E}{\partial \epsilon_{\alpha \beta}}
$$

where $\alpha$ and $\beta$ are the cartesian indices, and where strain is defined to be a scaling of space, $\mathbf{r}_{\alpha} \rightarrow\left(\delta_{\alpha \beta}+\epsilon_{\alpha \beta}\right) \mathbf{r}_{\beta}$, where $\mathbf{r}$ is any vector in space including particle positions and translation vectors. The effect is to transform the wavefunction by scaling every particle coordinate [162],

$$
\Psi_{\epsilon}\left(\left\{\mathbf{r}_{i}\right\}\right)=\operatorname{det}\left(\delta_{\alpha \beta}+\epsilon_{\alpha \beta}\right)^{-1 / 2} \Psi\left(\left\{\left(\delta_{\alpha \beta}+\epsilon_{\alpha \beta}\right)^{-1} \mathbf{r}_{i \beta}\right\}\right),
$$

where the prefactor preserves the normalization. Writing

$$
S_{\alpha\beta}=\delta_{\alpha\beta}+\epsilon_{\alpha\beta},
\qquad
\mathbf{r}'=S\mathbf{r},
$$

one has

$$
\mathrm{d}^{3}r'=\det(S)\,\mathrm{d}^{3}r,
$$

so for $N$ particles

$$
\int \mathrm{d}^{3}r_{1}'\cdots \mathrm{d}^{3}r_{N}'\,|\Psi_{\epsilon}|^{2}
=
\det(S)^{-N}\det(S)^{N}
\int \mathrm{d}^{3}r_{1}\cdots \mathrm{d}^{3}r_{N}\,|\Psi|^{2}
=
\int \mathrm{d}^{3}r_{1}\cdots \mathrm{d}^{3}r_{N}\,|\Psi|^{2}.
$$

Since the wavefunction also depends on the nuclear positions (either explicitly, treating the nuclei as quantum particles, or implicitly, as parameters in the Born-Oppenheimer approximation discussed after Eq. (3.1)), so also must the nuclear positions be scaled. Of course, the wavefunction and the nuclear positions actually change in other ways if the system is compressed or expanded; however, this has no effect on the energy to first order because the wavefunction and the nuclear positions are at variational minima. This is the same variational simplification as in the force theorem: at first order, only the explicit dependence of the hamiltonian on the strain need be kept.

After changing variables back to the unstrained coordinates, the strained energy can be written as

$$
E(\epsilon)=\langle\Psi|\hat{H}_{\epsilon}|\Psi\rangle,
$$

where the explicit strain dependence has been transferred to the operators. For the kinetic part,

$$
\nabla'_{k\gamma}=(S^{-1})_{\alpha\gamma}\nabla_{k\alpha},
$$

so

$$
\hat{T}_{\epsilon}
=-\sum_{k}\frac{\hbar^{2}}{2m_{k}}(S^{-1})_{\alpha\gamma}(S^{-1})_{\beta\gamma}\nabla_{k\alpha}\nabla_{k\beta}.
$$

To first order in the strain,

$$
S^{-1}=\delta-\epsilon+O(\epsilon^{2}),
\qquad
(S^{-1})_{\alpha\gamma}(S^{-1})_{\beta\gamma}
=\delta_{\alpha\beta}-\epsilon_{\alpha\beta}-\epsilon_{\beta\alpha}+O(\epsilon^{2}),
$$

so for symmetric strain $\epsilon_{\alpha\beta}=\epsilon_{\beta\alpha}$ one obtains directly

$$
\left.\frac{\partial \hat{T}_{\epsilon}}{\partial \epsilon_{\alpha\beta}}\right|_{\epsilon=0}
=\sum_{k}\frac{\hbar^{2}}{2m_{k}}\nabla_{k\alpha}\nabla_{k\beta},
$$

which is the kinetic contribution appearing in Eq. (3.23).

For any pair interaction depending only on the separation $x_{kk'}=|\mathbf{x}_{kk'}|$,

$$
\hat{V}_{\epsilon}
=\frac{1}{2}\sum_{k\neq k'} \hat{V}\!\left(|S\mathbf{x}_{kk'}|\right).
$$

Now

$$
|S\mathbf{x}|^{2}
=x_{\gamma}(\delta_{\gamma\alpha}+\epsilon_{\gamma\alpha})(\delta_{\alpha\delta}+\epsilon_{\alpha\delta})x_{\delta}
=x^{2}+2\epsilon_{\alpha\beta}x_{\alpha}x_{\beta}+O(\epsilon^{2}),
$$

so

$$
|S\mathbf{x}|
=x+\epsilon_{\alpha\beta}\frac{x_{\alpha}x_{\beta}}{x}+O(\epsilon^{2}),
$$

and therefore

$$
\hat{V}_{\epsilon}
=\hat{V}
+\frac{1}{2}\epsilon_{\alpha\beta}\sum_{k\neq k'}
\frac{(\mathbf{x}_{kk'})_{\alpha}(\mathbf{x}_{kk'})_{\beta}}{x_{kk'}}
\left(\frac{\mathrm{d}}{\mathrm{d}x_{kk'}}\hat{V}\right)
+O(\epsilon^{2}).
$$

Thus

$$
\frac{\partial E}{\partial \epsilon_{\alpha\beta}}
=
\left\langle\Psi\middle|
\sum_{k}\frac{\hbar^{2}}{2m_{k}}\nabla_{k\alpha}\nabla_{k\beta}
-\frac{1}{2}\sum_{k\neq k'}
\frac{(\mathbf{x}_{kk'})_{\alpha}(\mathbf{x}_{kk'})_{\beta}}{x_{kk'}}
\left(\frac{\mathrm{d}}{\mathrm{d}x_{kk'}}\hat{V}\right)
\middle|\Psi\right\rangle,
$$

and using Eq. (3.21) leads to the expression [162]

> [!theorem] Stress tensor (Eq. 3.23)
>
> $$
> \sigma_{\alpha \beta}=-\langle\Psi| \sum_{k} \frac{\hbar^{2}}{2 m_{k}} \nabla_{k \alpha} \nabla_{k \beta}-\frac{1}{2} \sum_{k \neq k^{\prime}} \frac{\left(\mathbf{x}_{k k^{\prime}}\right)_{\alpha}\left(\mathbf{x}_{k k^{\prime}}\right)_{\beta}}{x_{k k^{\prime}}}\left(\frac{\mathrm{d}}{\mathrm{~d} x_{k k^{\prime}}} \hat{V}\right)|\Psi\rangle,
> $$

where the sum over $k$ and $k^{\prime}$ denotes a double sum over all particles, nuclei, and electrons, where the interaction is a function of the distance $x_{k k^{\prime}}=\left|\mathbf{x}_{k k^{\prime}}\right|$. The virial theorem for pressure $P=-\sum_{\alpha} \sigma_{\alpha \alpha}$ is the trace of Eq. (3.23), which follows from isotropic scaling of space, $\epsilon_{\alpha \beta}=\epsilon \delta_{\alpha \beta}$. If all interactions are Coulombic and the potential energy includes all terms due to nuclei and electrons, the virial theorem leads to

For isotropic strain,

$$
\epsilon_{\alpha\beta}=\epsilon\,\delta_{\alpha\beta},
\qquad
\frac{\delta\Omega}{\Omega}=3\epsilon,
$$

so the scalar pressure relation follows from the trace of the stress tensor. Taking the trace of Eq. (3.23) gives

$$
\sum_{\alpha}\sigma_{\alpha\alpha}
=-\left\langle\Psi\middle|
\sum_{k}\frac{\hbar^{2}}{2m_{k}}\nabla_{k}^{2}
-\frac{1}{2}\sum_{k\neq k'}x_{kk'}\left(\frac{\mathrm{d}}{\mathrm{d}x_{kk'}}\hat{V}\right)
\middle|\Psi\right\rangle.
$$

Since

$$
E_{\mathrm{kinetic}}
=\left\langle\Psi\middle|-\sum_{k}\frac{\hbar^{2}}{2m_{k}}\nabla_{k}^{2}\middle|\Psi\right\rangle,
$$

the kinetic part contributes $2E_{\mathrm{kinetic}}$ after the isotropic scaling derivative is converted to a pressure derivative. For Coulomb interactions, $\hat{V}(x)\propto 1/x$, so

$$
x\frac{\mathrm{d}\hat{V}}{\mathrm{d}x}=-\hat{V},
$$

and therefore the potential contribution becomes the total potential energy. Hence

$$
3P\Omega=2E_{\mathrm{kinetic}}+E_{\mathrm{potential}},
$$

which is Eq. (3.24).

> [!theorem] Virial theorem for pressure (Eq. 3.24)
>
> $$
> 3 P \Omega=2 E_{\text {kinetic }}+E_{\text {potential }},
> $$

where $\Omega$ is the volume of the system. The expression (3.24) is a general result valid in any system in equilibrium, classical or quantum, at any temperature, so long as all particles interact with Coulomb forces. Explicit expressions [102, 163] used in practical calculations in Fourier space are discussed in Appendix G.

---

# 3.4 Generalized Force Theorem and Coupling Constant Integration

> [!derivation] Derivation 8: Coupling constant integration (adiabatic connection)
> The force theorem applies to any parameter in the Hamiltonian, not just nuclear positions. Use this idea to express the energy difference between a noninteracting and a fully interacting system as an integral over a coupling constant that scales the electron-electron interaction. What physical system does each intermediate value of the coupling constant describe, and why is this construction useful for density functional theory even though the intermediate wavefunctions are unphysical?

In the previous section, the force on a nucleus $I$ was shown to be given by the matrix element of the derivative of the hamiltonian with respect to position $\mathbf{R}_{I}$ because $\mathbf{R}_{I}$ can be considered to be a parameter. The same argument applies to any parameter, which we can denote by $\lambda$. Furthermore, finite energy differences between two states with values $\lambda_{1}$ and $\lambda_{2}$ can be calculated as an integral over a continuous variation of the hamiltonian from $\lambda_{1}$ to $\lambda_{2}$. This is also called an "adiabatic connection" following Harris [271] since it is a variation of the hamiltonian connecting the states of the system that is assumed to be in the ground state for each value of $\lambda$, i.e., it is an adiabatic variation. ${ }^{5}$ The general expressions can be written

If the hamiltonian depends smoothly on $\lambda$ and $\Psi_{\lambda}$ is the corresponding normalized stationary state, then

$$
E(\lambda)=\langle \Psi_{\lambda}|\hat{H}(\lambda)|\Psi_{\lambda}\rangle.
$$

Differentiating gives

$$
\begin{aligned}
\frac{\partial E}{\partial \lambda}
&=
\left\langle\frac{\partial \Psi_{\lambda}}{\partial \lambda}\middle|\hat{H}(\lambda)\middle|\Psi_{\lambda}\right\rangle
+\left\langle\Psi_{\lambda}\middle|\frac{\partial \hat{H}}{\partial \lambda}\middle|\Psi_{\lambda}\right\rangle
+\left\langle\Psi_{\lambda}\middle|\hat{H}(\lambda)\middle|\frac{\partial \Psi_{\lambda}}{\partial \lambda}\right\rangle.
\end{aligned}
$$

Using $\hat{H}(\lambda)|\Psi_{\lambda}\rangle=E(\lambda)|\Psi_{\lambda}\rangle$, the first and third terms become

$$
\begin{aligned}
\left\langle\frac{\partial \Psi_{\lambda}}{\partial \lambda}\middle|\hat{H}(\lambda)\middle|\Psi_{\lambda}\right\rangle
+\left\langle\Psi_{\lambda}\middle|\hat{H}(\lambda)\middle|\frac{\partial \Psi_{\lambda}}{\partial \lambda}\right\rangle
&=
E(\lambda)\left(
\left\langle\frac{\partial \Psi_{\lambda}}{\partial \lambda}\middle|\Psi_{\lambda}\right\rangle
+\left\langle\Psi_{\lambda}\middle|\frac{\partial \Psi_{\lambda}}{\partial \lambda}\right\rangle
\right) \\
&=
E(\lambda)\frac{\partial}{\partial \lambda}\langle\Psi_{\lambda}\mid\Psi_{\lambda}\rangle \\
&= 0,
\end{aligned}
$$

so only the explicit $\lambda$-dependence of the hamiltonian survives.

> [!theorem] Generalized force theorem (Eq. 3.25)
>
> $$
> \frac{\partial E}{\partial \lambda}=\left\langle\Psi_{\lambda}\right| \frac{\partial \hat{H}}{\partial \lambda}\left|\Psi_{\lambda}\right\rangle
> $$

[^3]and
$$
\Delta E=\int_{\lambda_{1}}^{\lambda_{2}} \mathrm{~d} \lambda \frac{\partial E}{\partial \lambda}=\int_{\lambda_{1}}^{\lambda_{2}} \mathrm{~d} \lambda\left\langle\Psi_{\lambda}\right| \frac{\partial \hat{H}}{\partial \lambda}\left|\Psi_{\lambda}\right\rangle
$$

For example, let the electron-electron interaction be scaled by a coupling constant,

$$
\hat{H}_{\lambda}=\hat{T}+\lambda \hat{V}_{\mathrm{int}}+\hat{V}_{\mathrm{ext}},
\qquad 0\le \lambda \le 1.
$$

Then

$$
\frac{\partial \hat{H}_{\lambda}}{\partial \lambda}=\hat{V}_{\mathrm{int}},
$$

so the generalized force theorem gives

$$
\frac{\partial E_{\lambda}}{\partial \lambda}
=\left\langle\Psi_{\lambda}\right| \hat{V}_{\mathrm{int}}\left|\Psi_{\lambda}\right\rangle.
$$

Integrating from $\lambda=0$ to $\lambda=1$ yields

$$
\begin{aligned}
E_{\lambda=1}-E_{\lambda=0}
&=\int_{0}^{1}\mathrm{d}\lambda\,\frac{\partial E_{\lambda}}{\partial \lambda} \\
&=\int_{0}^{1}\mathrm{d}\lambda\,\left\langle\Psi_{\lambda}\right| \hat{V}_{\mathrm{int}}\left|\Psi_{\lambda}\right\rangle.
\end{aligned}
$$

That is, $\lambda$ can be varied from 0 to 1 to connect the noninteracting limit to the fully interacting problem. Since the hamiltonian involves the charge only in the interaction term, and Eq. (3.5) is linear in $e^{2}$ (the nuclear term is treated separately as the "external potential"), it follows that the change in energy can be written

> [!theorem] Coupling constant integration (Eq. 3.27)
>
> $$
> \Delta E=\int_{0}^{1} \mathrm{~d} \lambda\left\langle\Psi_{\lambda}\right| V_{\mathrm{int}}\left|\Psi_{\lambda}\right\rangle
> $$

where $V_{\text {int }}$ is the full interaction term Eq. (3.5) and $\Psi_{\lambda}$ is the wavefunction for intermediate values of the interaction ${ }^{6}$ given by $e^{2} \rightarrow e^{2} \lambda$. For fixed external potential, each intermediate $\lambda$ describes a system in which the electrons interact with a fraction $\lambda$ of the full Coulomb repulsion: $\lambda=0$ is noninteracting and $\lambda=1$ is the physical system.

In density functional theory one usually refines this construction by allowing the external potential itself to depend on $\lambda$, chosen so that the ground-state density remains equal to the physical density for all $\lambda$. The resulting intermediate systems are then auxiliary rather than directly physical, because their electron-electron interaction strength is artificial. Nevertheless, the construction is useful because it converts the exchange-correlation energy into an integral over the interaction strength, making clear how exchange and correlation accumulate as the interaction is turned on.

> [!lesson] The generalized force theorem and adiabatic connection
>
> - **The force theorem applies to any parameter in the Hamiltonian, not just nuclear positions.** For any parameter $\lambda$ on which $\hat{H}$ depends smoothly, $\partial E/\partial \lambda = \langle\Psi_\lambda|\partial\hat{H}/\partial\lambda|\Psi_\lambda\rangle$, provided $\Psi_\lambda$ is an exact stationary state. This is the same variational stationarity that simplifies the force theorem.
> - **Finite energy differences can be computed by integrating the generalized force over a continuous path.** This turns a single difficult calculation (the energy of an interacting system) into an integral over a family of simpler calculations.
> - **Adiabatic connection: turning on the electron-electron interaction from $\lambda=0$ to $\lambda=1$ connects noninteracting and interacting systems.** This construction is the conceptual foundation of the exchange-correlation energy in density functional theory and explains why local and semi-local density functionals can capture non-trivial interaction effects.

---

# 3.5 Statistical Mechanics and the Density Matrix

From quantum statistical mechanics one can derive expressions for the energy $U$, entropy $S$, and free energy $F=U-T S$ at a temperature $T$. The general expression for $F$ is

> [!equation] Free energy (Eq. 3.28)
>
> $$
> F=\operatorname{Tr} \hat{\rho}\left(\hat{H}+\frac{1}{\beta} \ln \hat{\rho}\right)
> $$

where $\hat{\rho}$ is the density matrix and $\beta=1 / k_{B} T$. Here Tr means trace over all the states of the system which have a fixed number of particles $N$. The final term is the entropy term, which is the log of the number of possible states of the system.

> [!derivation] Derivation 9: Equilibrium density matrix from free energy minimization
> The free energy Eq. (3.28) is a functional of the density matrix $\hat{\rho}$. Find the $\hat{\rho}$ that minimizes it, subject to the physical constraints on a density matrix. Why does minimizing free energy — rather than energy alone — give the correct thermal equilibrium? What role does the entropy term play?

A general property of the density matrix is that it is positive definite, since its diagonal terms are the density. The correct equilibrium density matrix is the positive-definite matrix that minimizes the free energy,

$$
F[\hat{\rho}]=\operatorname{Tr}\hat{\rho}\left(\hat{H}+\frac{1}{\beta}\ln\hat{\rho}\right),
$$

subject to the physical constraints

$$
\hat{\rho}^{\dagger}=\hat{\rho},
\qquad
\hat{\rho}\ge 0,
\qquad
\operatorname{Tr}\hat{\rho}=1.
$$

Impose the trace constraint with a Lagrange multiplier $\lambda$:

$$
\Phi[\hat{\rho}]
=\operatorname{Tr}\hat{\rho}\left(\hat{H}+\frac{1}{\beta}\ln\hat{\rho}\right)
-\lambda(\operatorname{Tr}\hat{\rho}-1).
$$

Varying gives

$$
\delta \Phi
=\operatorname{Tr}\left[\delta\hat{\rho}\left(\hat{H}+\frac{1}{\beta}(\ln\hat{\rho}+1)-\lambda\right)\right].
$$

Since $\delta\hat{\rho}$ is arbitrary within the allowed Hermitian variations, stationarity requires

$$
\hat{H}+\frac{1}{\beta}(\ln\hat{\rho}+1)-\lambda=0,
$$

so

$$
\ln\hat{\rho}=\beta(\lambda-1)-\beta\hat{H}.
$$

Exponentiating,

$$
\hat{\rho}=\mathrm{e}^{\beta(\lambda-1)}\mathrm{e}^{-\beta\hat{H}}.
$$

The constant is fixed by normalization:

$$
\operatorname{Tr}\hat{\rho}
=\mathrm{e}^{\beta(\lambda-1)}\operatorname{Tr}\mathrm{e}^{-\beta\hat{H}}
=1.
$$

Therefore, defining

$$
Z=\operatorname{Tr}\mathrm{e}^{-\beta\hat{H}},
$$

one obtains

$$
\hat{\rho}=\frac{1}{Z} \mathrm{e}^{-\beta \hat{H}}
$$

with the partition function given by

$$
Z=\mathrm{Tre}^{-\beta \hat{H}}=\mathrm{e}^{-\beta F}
$$

Because $\hat{\rho}$ is a function of $\hat{H}$, it commutes with $\hat{H}$ and is diagonal in any eigenbasis of $\hat{H}$. In a basis of eigenstates $\Psi_{i}$ of $\hat{H}, \hat{\rho}$ has only diagonal matrix elements,

$$
\rho_{i i} \equiv\left\langle\Psi_{i}\right| \hat{\rho}\left|\Psi_{i}\right\rangle=\frac{1}{Z} \mathrm{e}^{-\beta E_{i}} ; Z=\sum_{j} \mathrm{e}^{-\beta E_{j}}
$$

[^4]where $\rho_{i i}$ is the probability of state $i$. Minimizing free energy rather than energy alone is essential at finite temperature because equilibrium must balance low energy against the multiplicity of accessible states. The entropy term $(1/\beta)\operatorname{Tr}(\hat{\rho}\ln\hat{\rho})=-TS$ favors spreading probability over many states, whereas the energy term $\operatorname{Tr}(\hat{\rho}\hat{H})$ favors occupation of low-energy states. Their competition produces the Gibbs distribution.

Since the $\Psi_{i}$ form a complete set, the operator $\hat{\rho}$ in Eq. (3.29) can be written
$$
\hat{\rho}=\sum_{i}\left|\Psi_{i}\right\rangle \rho_{i i}\left\langle\Psi_{i}\right|
$$
in Dirac bra and ket notation.
In the grand canonical ensemble, in which the number of particles is allowed to vary, the expressions are modified to include the chemical potential $\mu$ and the number operator $\hat{N}$. The grand potential $\Omega$ and the grand partition function $Z$ are given by
$$
Z=\mathrm{e}^{-\beta \Omega}=\operatorname{Tre}^{-\beta(\hat{H}-\mu \hat{N})}
$$
where now the trace is over all states with any particle number, and the grand density matrix operator is the generalization of Eq. (3.29),
$$
\hat{\rho}=\frac{1}{Z} \mathrm{e}^{-\beta(\hat{H}-\mu \hat{N})} .
$$

All the equilibrium properties of the system are determined by the density matrix, just as they are determined by the ground-state wavefunction at $T=0$. In particular, any expectation value is given by

$$
\langle\hat{O}\rangle=\operatorname{Tr} \hat{\rho} \hat{O},
$$

which reduces to a ground-state expectation value of the form of Eq. (3.7) at $T=0$. For the case of noninteracting particles, the general formulas reduce to the well-known expressions for fermions and bosons given in the next section.

> [!lesson] Free energy minimization and the Gibbs distribution
>
> - **At finite temperature, the correct equilibrium is found by minimizing the free energy $F = U - TS$, not the energy alone.** The energy term favors occupation of low-energy states; the entropy term favors spreading probability over many states. Their competition produces the Gibbs (Boltzmann) distribution $\hat{\rho} = Z^{-1} e^{-\beta\hat{H}}$.
> - **The density matrix $\hat{\rho}$ plays the same role at finite temperature that the wavefunction plays at $T=0$.** All equilibrium expectation values are given by $\langle\hat{O}\rangle = \text{Tr}\,\hat{\rho}\hat{O}$, which reduces to $\langle\Psi_0|\hat{O}|\Psi_0\rangle$ in the zero-temperature limit.

# 3.6 Independent-Electron Approximations

> [!question]
>
> (a) What is the key distinction between "noninteracting" (Hartree-like) and Hartree-Fock independent-particle approaches, given that both assume electrons are uncorrelated except for the exclusion principle?
> (b) In what sense does a Kohn-Sham calculation use a noninteracting Hamiltonian, yet still account for exchange and correlation effects?

There are two basic independent-particle approaches that may be classified as "noninteracting" and "Hartree-Fock." They are similar in that each assumes the electrons are uncorrelated except that they must obey the exclusion principle. However, they are different in that Hartree-Fock includes the electron-electron Coulomb interaction in the energy while neglecting the correlation that is introduced in the true wavefunction due to those interactions. In general, "noninteracting" theories have some effective potential that incorporates some effect of the real interaction, but there is no interaction term explicitly included in the effective hamiltonian. This approach is often referred to as "Hartree" or "Hartree-like," after D. R. Hartree [50], who included an average Coulomb interaction in a rather heuristic way. ${ }^{7}$ More to the point of modern calculations, all calculations

[^5]following the Kohn-Sham method (see Chapters 7-9) involve an auxiliary system with a noninteracting hamiltonian and an effective potential chosen to incorporate exchange and correlation effects approximately.

## 3.6.1 Noninteracting (Hartree-Like) Electron Approximation

With our broad definition, all noninteracting electron calculations involve the solution of a Schrödinger-like equation like Eqs. (1.1) and (1.2)

> [!approximation] Noninteracting (Hartree-like) electron equation (Eq. 3.36)
>
> $$
> \hat{H}_{\mathrm{eff}} \psi_{i}^{\sigma}(\mathbf{r})=\left[-\frac{\hbar^{2}}{2 m_{e}} \nabla^{2}+V_{\mathrm{eff}}^{\sigma}(\mathbf{r})\right] \psi_{i}^{\sigma}(\mathbf{r})=\varepsilon_{i}^{\sigma} \psi_{i}^{\sigma}(\mathbf{r}),
> $$

where $V_{\text {eff }}^{\sigma}(\mathbf{r})$ is an effective potential that acts on each electron of $\operatorname{spin} \sigma$ at point $\mathbf{r} .^{8}$ The ground state for many noninteracting electrons is found by occupying the lowest eigenstates of Eq. (3.36) obeying the exclusion principle. If the hamiltonian is not spin dependent, then up and down spin states are degenerate and one can simply consider spin as a factor of two in the counting. Excited states involve the occupation of higher-energy eigenstates. There is no need to construct an antisymmetric wavefunction explicitly. Since the eigenstates of the independent-particle Schrödinger equation are automatically orthogonal, an antisymmetric wavefunction like Eq. (3.43) can be formed from a determinant of these eigenstates. It is then straightforward to show that if the particles are noninteracting, the relations reduce to the expressions given below for the energy, density, etc.(Exercise 3.6).

The solution of equations having the form of Eq. (3.36) is at the heart of the methods described in this volume. The basic justification of the use of such independent-particle equations for electrons in materials is density functional theory, which is the subject of Chapters 6-9. Most of the rest of the book is devoted to methods for solving the equations and applications to the properties of matter, such as predictions of structures, phase transitions, magnetism, elastic constants, phonons, piezoelectric and ferroelectric moments, topology of the band structure, and many other quantities.

> [!derivation] Derivation 10: Fermi-Dirac distribution from the grand canonical ensemble
> For noninteracting fermions, derive the occupation function Eq. (3.38) from the general statistical mechanics of §3.5. What constraint on the single-particle occupation numbers is imposed by the Pauli principle, and how does it determine the functional form? Show that the general many-body expectation value Eq. (3.35) collapses to the single-particle weighted sum Eq. (3.37). (Exercises 3.7, 3.8.)

At finite temperature it is straightforward to apply the general formulas of statistical mechanics given in the previous section to show that the equilibrium distribution of electrons is given by the Fermi-Dirac (or Bose-Einstein) expression (1.3) for occupation numbers of states as a function of energy (Exercise 3.7). The expectation value Eq. (3.35) is a sum over many-body states $\Psi_{j}$, each of which is specified by the set of occupation numbers $\left\{n_{i}^{\sigma}\right\}$ for each of the independent-particle states with energy $\varepsilon_{i}^{\sigma}$. Given that each $n_{i}^{\sigma}$ can be either 0 or 1 , with $\sum_{i} n_{i}^{\sigma}=N^{\sigma}$, it is straightforward (see Exercise 3.8) to show that Eq. (3.35) simplifies to

For noninteracting particles, the many-body hamiltonian and number operator are

$$
\hat{H}=\sum_{i,\sigma}\varepsilon_{i}^{\sigma}\hat{n}_{i}^{\sigma},
\qquad
\hat{N}=\sum_{i,\sigma}\hat{n}_{i}^{\sigma},
$$

so a many-body occupation-number state $\left|\{n_{i}^{\sigma}\}\right\rangle$ has

$$
E_{\{n\}}=\sum_{i,\sigma} n_{i}^{\sigma}\varepsilon_{i}^{\sigma},
\qquad
N_{\{n\}}=\sum_{i,\sigma} n_{i}^{\sigma}.
$$

The Pauli principle for fermions requires

$$
n_{i}^{\sigma}=0 \text{ or } 1,
$$

so each single-particle state is either empty or singly occupied. In the grand canonical ensemble, the probability of a many-body configuration is

$$
P(\{n_{i}^{\sigma}\})
=\frac{1}{Z}\exp\left[-\beta\sum_{i,\sigma}n_{i}^{\sigma}(\varepsilon_{i}^{\sigma}-\mu)\right].
$$

Because the exponent is a sum over independent single-particle states, the grand partition function factorizes:

$$
\begin{aligned}
Z
&=\sum_{\{n_{i}^{\sigma}\}} \exp\left[-\beta\sum_{i,\sigma}n_{i}^{\sigma}(\varepsilon_{i}^{\sigma}-\mu)\right] \\
&=\prod_{i,\sigma}\sum_{n_{i}^{\sigma}=0}^{1}\exp\left[-\beta n_{i}^{\sigma}(\varepsilon_{i}^{\sigma}-\mu)\right] \\
&=\prod_{i,\sigma}\left(1+e^{-\beta(\varepsilon_{i}^{\sigma}-\mu)}\right).
\end{aligned}
$$

The average occupation of one state is therefore

$$
\begin{aligned}
f_{i}^{\sigma}
&=\langle n_{i}^{\sigma}\rangle \\
&=\frac{\sum_{n_{i}^{\sigma}=0}^{1} n_{i}^{\sigma} e^{-\beta n_{i}^{\sigma}(\varepsilon_{i}^{\sigma}-\mu)}}{\sum_{n_{i}^{\sigma}=0}^{1} e^{-\beta n_{i}^{\sigma}(\varepsilon_{i}^{\sigma}-\mu)}} \\
&=\frac{0\cdot e^{0}+1\cdot e^{-\beta(\varepsilon_{i}^{\sigma}-\mu)}}{e^{0}+e^{-\beta(\varepsilon_{i}^{\sigma}-\mu)}} \\
&=\frac{e^{-\beta(\varepsilon_{i}^{\sigma}-\mu)}}{1+e^{-\beta(\varepsilon_{i}^{\sigma}-\mu)}} \\
&=\frac{1}{e^{\beta(\varepsilon_{i}^{\sigma}-\mu)}+1},
\end{aligned}
$$

which is the Fermi-Dirac form. The `+1` in the denominator is a direct consequence of the Pauli restriction $n_{i}^{\sigma}=0,1$; for bosons the allowed occupations are $0,1,2,\ldots$, and the geometric sum instead gives the Bose-Einstein denominator with `-1`.

For any one-body operator

$$
\hat{O}=\sum_{i,\sigma} \hat{n}_{i}^{\sigma} O_{i}^{\sigma},
\qquad
O_{i}^{\sigma}=\left\langle\psi_{i}^{\sigma}\right|\hat{O}\left|\psi_{i}^{\sigma}\right\rangle,
$$

the general many-body expectation value becomes

$$
\begin{aligned}
\langle\hat{O}\rangle
&=\sum_{\{n_{i}^{\sigma}\}} P(\{n_{i}^{\sigma}\}) \sum_{i,\sigma} n_{i}^{\sigma} O_{i}^{\sigma} \\
&=\sum_{i,\sigma} O_{i}^{\sigma} \sum_{\{n_{i}^{\sigma}\}} P(\{n_{i}^{\sigma}\}) n_{i}^{\sigma} \\
&=\sum_{i,\sigma} O_{i}^{\sigma} \langle n_{i}^{\sigma}\rangle \\
&=\sum_{i,\sigma} f_{i}^{\sigma}\left\langle\psi_{i}^{\sigma}\right| \hat{O}\left|\psi_{i}^{\sigma}\right\rangle,
\end{aligned}
$$

which is Eq. (3.37).

> [!equation] Independent-particle expectation value (Eq. 3.37)
>
> $$
> \langle\hat{O}\rangle=\sum_{i, \sigma} f_{i}^{\sigma}\left\langle\psi_{i}^{\sigma}\right| \hat{O}\left|\psi_{i}^{\sigma}\right\rangle,
> $$

[^6]where $\left\langle\psi_{i}^{\sigma}\right| \hat{O}\left|\psi_{i}^{\sigma}\right\rangle$ is the expectation value of the operator $\hat{O}$ for the one-particle state $\psi_{i}^{\sigma}$, and $f_{i}^{\sigma}$ is the probability of finding an electron in state $i, \sigma$ given in general by Eq. (1.3). The relevant case is the Fermi-Dirac distribution
> [!definition] Fermi-Dirac distribution (Eq. 3.38)
>
> $$
> f_{i}^{\sigma}=\frac{1}{e^{\beta\left(\varepsilon_{i}^{\sigma}-\mu\right)}+1},
> $$
where $\mu$ is the Fermi energy (or chemical potential) of the electrons. For example, the energy is the weighted sum of noninteracting particle energies $\varepsilon_{i}^{\sigma}$


>[!equation] Independent-particle energy at finite temperature (Eq. 3.39)
>
> $$
> E(T)=\langle\hat{H}\rangle=\sum_{i}^{\sigma} f_{i}^{\sigma} \varepsilon_{i}^{\sigma} .
> $$

Just as in the general many-body case, one can define a single-body density matrix operator

> [!definition] Single-body density matrix (Eq. 3.40)
>
> $$
> \hat{\rho}=\sum_{i}\left|\psi_{i}^{\sigma}\right\rangle f_{i}^{\sigma}\left\langle\psi_{i}^{\sigma}\right|,
> $$

in terms of which an expectation value Eq. (3.37) is $\langle\hat{O}\rangle=\operatorname{Tr} \hat{\rho} \hat{O}$ in analogy to Eq. (3.35). For example, in an explicit spin and position representation, $\hat{\rho}$ is given by

$$
\rho\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=\delta_{\sigma, \sigma^{\prime}} \sum_{i} \psi_{i}^{\sigma *}(\mathbf{r}) f_{i} \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right),
$$

where the density is the diagonal part

$$
n^{\sigma}(\mathbf{r})=\rho(\mathbf{r}, \sigma ; \mathbf{r}, \sigma)=\sum_{i} f_{i}^{\sigma}\left|\psi_{i}^{\sigma}(\mathbf{r})\right|^{2} .
$$

> [!lesson] Fermi-Dirac statistics and the independent-particle simplification
>
> - **The Pauli exclusion principle ($n_i^\sigma = 0$ or $1$) uniquely determines the Fermi-Dirac functional form.** The "+1" in the denominator is a direct consequence of the occupation restriction. For bosons, unrestricted occupation gives the Bose-Einstein form with "−1" instead.
> - **For noninteracting particles, many-body expectation values collapse to occupation-weighted single-particle sums:** $\langle\hat{O}\rangle = \sum_{i,\sigma} f_i^\sigma \langle\psi_i^\sigma|\hat{O}|\psi_i^\sigma\rangle$. This enormous simplification — from an $N$-body trace to a sum over single-particle states — is what makes independent-particle theories computationally tractable.
> - **The density is the diagonal part of the single-body density matrix:** $n^\sigma(\mathbf{r}) = \sum_i f_i^\sigma |\psi_i^\sigma(\mathbf{r})|^2$. This formula is the practical starting point for computing densities in Kohn-Sham DFT and Hartree-Fock calculations.

## 3.6.2 Hartree-Fock Approximation

A standard method of many-particle theory is the Hartree-Fock method, which was first applied to atoms in 1930 by Fock [53]. In this approach one writes a properly antisymmetrized determinant wavefunction for a fixed number $N$ of electrons and finds the single determinant that minimizes the total energy for the full interacting hamiltonian Eq. (3.2). If there is no spin-orbit interaction, the determinant wavefunction $\Phi$ can be written as a Slater determinant ${ }^{9}$

> [!definition] Slater determinant (Eq. 3.43)
>
> $$
> \Phi=\frac{1}{(N!)^{1 / 2}}\left|\begin{array}{cccc}
> \phi_{1}\left(\mathbf{r}_{1}, \sigma_{1}\right) & \phi_{1}\left(\mathbf{r}_{2}, \sigma_{2}\right) & \phi_{1}\left(\mathbf{r}_{3}, \sigma_{3}\right) & \ldots \\
> \phi_{2}\left(\mathbf{r}_{1}, \sigma_{1}\right) & \phi_{2}\left(\mathbf{r}_{2}, \sigma_{2}\right) & \phi_{2}\left(\mathbf{r}_{3}, \sigma_{3}\right) & \ldots \\
> \phi_{3}\left(\mathbf{r}_{1}, \sigma_{1}\right) & \phi_{3}\left(\mathbf{r}_{2}, \sigma_{2}\right) & \phi_{3}\left(\mathbf{r}_{3}, \sigma_{3}\right) & \ldots \\
> . & . & . & \ldots \\
> . & . & . & \ldots
> \end{array}\right|,
> $$

> [!derivation] Derivation 11: Hartree-Fock energy from the Slater determinant
> Evaluate $\langle\Phi|\hat{H}|\Phi\rangle$ for the Slater determinant Eq. (3.43) to obtain the Hartree-Fock energy expression Eq. (3.44). Why does an antisymmetrized wavefunction produce two distinct two-body terms (direct and exchange) rather than just one? What happens to the unphysical self-interaction, and why is this significant for one-electron systems like hydrogen? (Exercise 3.11.)

[^7]where the $\phi_{i}\left(\mathbf{r}_{j}, \sigma_{j}\right)$ are single-particle "spin-orbitals." If there is no spin-orbit interaction $\phi_{i}\left(\mathbf{r}_{j}, \sigma_{j}\right)$ can be written as a product of a function of the position $\psi_{i}^{\sigma}\left(\mathbf{r}_{j}\right)$ and a function of the spin variable $\alpha_{i}\left(\sigma_{j}\right)$. (Note that $\psi_{i}^{\sigma}\left(\mathbf{r}_{j}\right)$ is independent of spin $\sigma$ in closed-shell cases. In open-shell systems, this assumption corresponds to the "spin-restricted Hartree-Fock approximation.") The spin-orbitals must be linearly independent and if in addition they are orthonormal the equations simplify greatly; it is straightforward to show (Exercise 3.10) that $\Phi$ is normalized to 1 . Furthermore, if the hamiltonian is independent of spin or is diagonal in the basis $\sigma=|\uparrow\rangle$; $|\downarrow\rangle$, the expectation value of the hamiltonian Eq. (3.2), using Hartree atomic units, with the wavefunction Eq. (3.43) is given by (Exercise 3.11)

Write the electronic Hamiltonian as a sum of one-body and two-body operators,

$$
\hat{H}=\sum_{k}\hat{h}(k)+\frac{1}{2}\sum_{k\neq l}\hat{v}(k,l)+E_{II},
$$

with

$$
\hat{h}(k)=-\frac{1}{2}\nabla_{k}^{2}+V_{\mathrm{ext}}(\mathbf{r}_{k}),
\qquad
\hat{v}(k,l)=\frac{1}{|\mathbf{r}_{k}-\mathbf{r}_{l}|}.
$$

For orthonormal spin-orbitals, the one-body part is

$$
\begin{aligned}
\langle\Phi|\sum_{k}\hat{h}(k)|\Phi\rangle
&=\sum_{i}\langle\phi_{i}|\hat{h}|\phi_{i}\rangle \\
&=\sum_{i,\sigma}\int \mathrm{d}\mathbf{r}\,
\psi_{i}^{\sigma *}(\mathbf{r})
\left[-\frac{1}{2}\nabla^{2}+V_{\mathrm{ext}}(\mathbf{r})\right]
\psi_{i}^{\sigma}(\mathbf{r}),
\end{aligned}
$$

because all cross terms vanish by orthonormality of the occupied spin-orbitals.

For the two-body part, antisymmetry of the determinant implies that the two-particle matrix element contains both the identity permutation and the exchanged permutation:

$$
\langle\Phi|\frac{1}{2}\sum_{k\neq l}\hat{v}(k,l)|\Phi\rangle
=\frac{1}{2}\sum_{i,j}
\left[
\langle\phi_{i}\phi_{j}|\hat{v}|\phi_{i}\phi_{j}\rangle
-\langle\phi_{i}\phi_{j}|\hat{v}|\phi_{j}\phi_{i}\rangle
\right].
$$

The first term is the direct Coulomb term,

$$
\begin{aligned}
\langle\phi_{i}\phi_{j}|\hat{v}|\phi_{i}\phi_{j}\rangle
&=
\sum_{\sigma_{i},\sigma_{j}}
\int \mathrm{d}\mathbf{r}\,\mathrm{d}\mathbf{r}'
\psi_{i}^{\sigma_{i}*}(\mathbf{r})
\psi_{j}^{\sigma_{j}*}(\mathbf{r}')
\frac{1}{|\mathbf{r}-\mathbf{r}'|}
\psi_{i}^{\sigma_{i}}(\mathbf{r})
\psi_{j}^{\sigma_{j}}(\mathbf{r}'),
\end{aligned}
$$

and the second is the exchange term,

$$
\begin{aligned}
\langle\phi_{i}\phi_{j}|\hat{v}|\phi_{j}\phi_{i}\rangle
&=
\sum_{\sigma_{i},\sigma_{j}}
\int \mathrm{d}\mathbf{r}\,\mathrm{d}\mathbf{r}'
\psi_{i}^{\sigma_{i}*}(\mathbf{r})
\psi_{j}^{\sigma_{j}*}(\mathbf{r}')
\frac{1}{|\mathbf{r}-\mathbf{r}'|}
\psi_{j}^{\sigma_{j}}(\mathbf{r})
\psi_{i}^{\sigma_{i}}(\mathbf{r}').
\end{aligned}
$$

Because the spin functions are orthonormal, the exchange term vanishes unless $\sigma_{i}=\sigma_{j}$, which is why exchange acts only between same-spin electrons. Collecting the one-body, two-body, and $E_{II}$ pieces gives Eq. (3.44).

The direct and exchange terms both arise because the Slater determinant is antisymmetrized: one contribution comes from pairing bra and ket orbitals without exchange, and the other comes from pairing them after exchanging two particles. If the wavefunction were not antisymmetric, only the direct Coulomb term would remain.

The $i=j$ part of the direct term is an unphysical self-interaction, but for same spin the corresponding $i=j$ exchange term is equal in magnitude and opposite in sign, so the self-interaction cancels exactly. This is especially important for one-electron systems such as hydrogen: with only one occupied orbital, the direct and exchange contributions cancel completely, leaving only the one-electron kinetic energy plus external potential, as they must.
> [!equation] Hartree-Fock total energy (Eq. 3.44)
>
> $$
> \begin{aligned}
> \langle\Phi| \hat{H}|\Phi\rangle= & \sum_{i, \sigma} \int \mathrm{~d} \mathbf{r} \psi_{i}^{\sigma *}(\mathbf{r})\left[-\frac{1}{2} \nabla^{2}+V_{\mathrm{ext}}(\mathbf{r})\right] \psi_{i}^{\sigma}(\mathbf{r})+E_{I I} \\
> & +\frac{1}{2} \sum_{i, j, \sigma_{i}, \sigma_{j}} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime} \psi_{i}^{\sigma_{i} *}(\mathbf{r}) \psi_{j}^{\sigma_{j} *}\left(\mathbf{r}^{\prime}\right) \frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \psi_{i}^{\sigma_{i}}(\mathbf{r}) \psi_{j}^{\sigma_{j}}\left(\mathbf{r}^{\prime}\right) \\
> & -\frac{1}{2} \sum_{i, j, \sigma} \int \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime} \psi_{i}^{\sigma *}(\mathbf{r}) \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right) \frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \psi_{j}^{\sigma}(\mathbf{r}) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right)
> \end{aligned}
> $$

The first term groups together the single-body expectation values that involve a sum over orbitals, whereas the third and fourth terms are the direct and exchange interactions among electrons, which are double sums. We have followed the usual practice of including the $i=j$ "self-interaction," which is spurious but which cancels in the sum of direct and exchange terms. When this term is included, the sum over all orbitals gives the density and the direct term is simply the Hartree energy defined in Eq. (3.15). The "exchange" term, which acts only between same-spin electrons since the spin parts of the orbitals are orthogonal for opposite spins, is discussed below in Section 3.7 and in the chapters on density functional theory.

> [!lesson] Antisymmetry, exchange, and self-interaction cancellation
>
> - **Antisymmetry of the wavefunction produces two distinct two-body terms: direct (Coulomb) and exchange.** The direct term comes from pairing bra and ket orbitals without exchange; the exchange term comes from swapping two particles. Without antisymmetry, only the direct Coulomb term would exist.
> - **Exchange acts only between same-spin electrons.** The orthogonality of spin functions causes the exchange integral to vanish when the two orbitals have different spins.
> - **Self-interaction cancels exactly between the direct and exchange terms.** For the $i=j$ contribution, the direct and exchange integrals are equal in magnitude and opposite in sign. This is why Hartree-Fock correctly reduces to the ordinary Schrödinger equation for one-electron systems like hydrogen — a critical consistency check for any electronic structure method.

> [!derivation] Derivation 12: Hartree-Fock equations from constrained variational minimization
> Derive the Hartree-Fock eigenvalue equations Eq. (3.45) by minimizing the energy Eq. (3.44) with respect to the orbitals. In what sense are these equations "self-consistent"? Why is the resulting effective Hamiltonian different for each orbital — what physical effect makes it state-dependent — and why does this make the equations fundamentally harder to solve than ordinary eigenvalue problems?

The Hartree-Fock approach is to minimize the total energy with respect to all degrees of freedom in the wavefunction with the restriction that it has the form Eq. (3.43). Since orthonormality was used to simplify the equations, it must be maintained in the minimization, which can be done by Lagrange multipliers as in Eqs. (3.10) to (3.13). If the spin functions are quantized along an axis, variation of $\psi_{i}^{\sigma *}(\mathbf{r})$ for each spin $\sigma$ leads to the Hartree-Fock equations

> [!approximation] Hartree-Fock equations (Eq. 3.45)
>
> $$
> \begin{aligned}
> & {\left[-\frac{1}{2} \nabla^{2}+V_{\mathrm{ext}}(\mathbf{r})+\sum_{j, \sigma_{j}} \int \mathrm{~d} \mathbf{r}^{\prime} \psi_{j}^{\sigma_{j} *}\left(\mathbf{r}^{\prime}\right) \psi_{j}^{\sigma_{j}}\left(\mathbf{r}^{\prime}\right) \frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}\right] \psi_{i}^{\sigma}(\mathbf{r})} \\
> & \quad-\sum_{j} \int \mathrm{~d} \mathbf{r}^{\prime} \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right) \frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \psi_{j}^{\sigma}(\mathbf{r})=\varepsilon_{i}^{\sigma} \psi_{i}^{\sigma}(\mathbf{r})
> \end{aligned}
> $$

where the exchange term is summed over all orbitals of the same spin including the self-term $i=j$, which cancels the unphysical self-term included in the direct term. If the exchange term is modified by multiplying and dividing by $\psi_{i}^{\sigma}(\mathbf{r})$, Eq. (3.45) can be written in a form
analogous to Eq. (3.36) except that the effective hamiltonian is an operator that depends on the state

$$
\hat{H}_{\mathrm{eff}}^{i} \psi_{i}^{\sigma}(\mathbf{r})=\left[-\frac{\hbar^{2}}{2 m_{e}} \nabla^{2}+\hat{V}_{\mathrm{eff}}^{i, \sigma}(\mathbf{r})\right] \psi_{i}^{\sigma}(\mathbf{r})=\varepsilon_{i}^{\sigma} \psi_{i}^{\sigma}(\mathbf{r})
$$

with

$$
\hat{V}_{\mathrm{eff}}^{i, \sigma}(\mathbf{r})=V_{\mathrm{ext}}(\mathbf{r})+V_{\text {Hartree }}(\mathbf{r})+\hat{V}_{x}^{i, \sigma}(\mathbf{r}),
$$

and the exchange term operator $\hat{V}_{x}$ is given by a sum over orbitals of the same spin $\sigma$

$$
\hat{V}_{x}^{i, \sigma}(\mathbf{r})=-\sum_{j} \int \mathrm{~d} \mathbf{r}^{\prime} \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right) \frac{1}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \frac{\psi_{j}^{\sigma}(\mathbf{r})}{\psi_{i}^{\sigma}(\mathbf{r})} .
$$

Note that this is a differential-integral equation for each orbital $\psi_{i}^{\sigma}$ in terms of the exchange operator $\hat{V}_{x}^{i, \sigma}(\mathbf{r})$ that is an integral involving $\psi_{i}^{\sigma}$ and all the other $\psi_{j}^{\sigma}$ with the same spin. The term in square brackets is the Coulomb potential due to the "exchange charge density" $\sum_{j} \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right)$ for the state $i, \sigma$. Furthermore, $\hat{V}_{x}^{i, \sigma}(\mathbf{r})$ diverges at points where $\psi_{i}^{\sigma}(\mathbf{r})=0$; this requires care in solving the equations but is not a fundamental problem since the product $\hat{V}_{x}^{i, \sigma}(\mathbf{r}) \psi_{i}^{\sigma}(\mathbf{r})$ has no singularity.

We will not discuss the solution of the Hartree-Fock equations in any detail since this is given in many texts [274, 275]. The only aspect that we consider here is the nature of the exchange term and issues for calculations. Unlike the case of independent Hartree-like equations, the Hartree-Fock equations can be solved directly only in special cases such as spherically symmetric atoms and the homogeneous electron gas. In general, one must introduce a basis, in which case the energy (3.44) can be written in terms of the expansion coefficients of the orbitals and the integrals involving the basis functions. Variation then leads to the Roothan and Pople-Nesbet equations widely used in quantum chemistry [274, 275]. In general, these are much more difficult to solve than the independent Hartree-like equations and the difficulty grows with size and accuracy since one must calculate $N_{\text {basis }}^{4}$ integrals.

However, there are ways to reduce the amount of computation. The nonlocal exchange potential $\hat{V}_{x}^{i, \sigma}(\mathbf{r})$ acting on state $i, \sigma$ involves the exchange charge density $\sum_{j} \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right)$ involving the other orbitals $j, \sigma$. For localized basis functions, it is nonzero only where states $i$ and $j$ overlap, which decreases rapidly in general. For gaussians, the Coulomb integrals are analytic, and for numerical basis functions fast multiple methods [276] can be used. For large systems the calculation scales linearly with size, but there may be a large prefactor. For plane waves special considerations are needed as described in Section 13.4.

## 3.6.3 Koopmans' Theorem

> [!derivation] Derivation 13: Koopmans' theorem — eigenvalues as addition/removal energies
> What is the physical meaning of the Hartree-Fock eigenvalues $\varepsilon_i^\sigma$? Prove Koopmans' theorem by relating them to total energy differences, and identify the key assumption that makes the theorem exact within Hartree-Fock. Why do the resulting band gaps systematically overestimate experiment, and what does this tell you about what Hartree-Fock neglects? (Exercise 3.18.)

What is the meaning of the eigenvalues of the Hartree-Fock equation (3.45)? Of course, Hartree-Fock is only an approximation to the energies for addition and removal of electrons, since all effects of correlation are omitted. Nevertheless, it is very valuable to have a rigorous understanding of the eigenvalues, which is provided by Koopmans' theorem ${ }^{10}$ [277]:

> [!theorem] Koopmans' theorem (§3.6.3)
>
> The eigenvalue of a filled (empty) orbital is equal to the change in the total energy Eq. (3.44) if an electron is subtracted from (added to) the system, i.e., decreasing (increasing) the size of the determinant by omitting (adding) a row and column involving a particular orbital $\phi_{j}\left(\mathbf{r}_{i}, \sigma_{i}\right)$, keeping all the other orbitals the same.

For an occupied orbital $i,\sigma$, take the matrix element of Eq. (3.45) with the normalized orbital $\psi_{i}^{\sigma *}(\mathbf{r})$. One obtains

$$
\varepsilon_{i}^{\sigma}
=h_{ii}^{\sigma}
+\sum_{j,\sigma_{j}} J_{ij}^{\sigma\sigma_{j}}
-\sum_{j} K_{ij}^{\sigma},
$$

where

$$
h_{ii}^{\sigma}
=\int \mathrm{d}\mathbf{r}\,\psi_{i}^{\sigma *}(\mathbf{r})
\left[-\frac{1}{2}\nabla^{2}+V_{\mathrm{ext}}(\mathbf{r})\right]
\psi_{i}^{\sigma}(\mathbf{r}),
$$

$$
J_{ij}^{\sigma\sigma_{j}}
=\int \mathrm{d}\mathbf{r}\,\mathrm{d}\mathbf{r}'
\psi_{i}^{\sigma *}(\mathbf{r})\psi_{j}^{\sigma_{j} *}(\mathbf{r}')
\frac{1}{|\mathbf{r}-\mathbf{r}'|}
\psi_{i}^{\sigma}(\mathbf{r})\psi_{j}^{\sigma_{j}}(\mathbf{r}'),
$$

and

$$
K_{ij}^{\sigma}
=\int \mathrm{d}\mathbf{r}\,\mathrm{d}\mathbf{r}'
\psi_{i}^{\sigma *}(\mathbf{r})\psi_{j}^{\sigma *}(\mathbf{r}')
\frac{1}{|\mathbf{r}-\mathbf{r}'|}
\psi_{j}^{\sigma}(\mathbf{r})\psi_{i}^{\sigma}(\mathbf{r}').
$$

Now write the Hartree-Fock total energy Eq. (3.44) in the compact form

$$
E_{N}
=\sum_{k,\sigma} h_{kk}^{\sigma}
+\frac{1}{2}\sum_{k,l,\sigma_{k},\sigma_{l}} J_{kl}^{\sigma_{k}\sigma_{l}}
-\frac{1}{2}\sum_{k,l,\sigma} K_{kl}^{\sigma}
+E_{II}.
$$

If one removes the occupied orbital $i,\sigma$ and keeps all other orbitals fixed, the frozen-orbital $(N-1)$-electron energy is

$$
\begin{aligned}
E_{N-1}^{(i)}
&=
E_{N}
-h_{ii}^{\sigma}
-\sum_{j,\sigma_{j}} J_{ij}^{\sigma\sigma_{j}}
+\sum_{j} K_{ij}^{\sigma},
\end{aligned}
$$

because the removed orbital contributes once to the one-body sum and twice to the symmetrized two-body sums, cancelling the factor of $1/2$. Therefore

$$
\begin{aligned}
E_{N}-E_{N-1}^{(i)}
&=
h_{ii}^{\sigma}
+\sum_{j,\sigma_{j}} J_{ij}^{\sigma\sigma_{j}}
-\sum_{j} K_{ij}^{\sigma} \\
&=\varepsilon_{i}^{\sigma}.
\end{aligned}
$$

Thus the occupied Hartree-Fock eigenvalue equals the frozen-orbital removal energy. Equivalently, if one defines the ionization energy as $I_{i}=E_{N-1}^{(i)}-E_{N}$, then $I_{i}=-\varepsilon_{i}^{\sigma}$.

For an empty orbital $a,\sigma$, adding one electron while keeping all other orbitals fixed gives

$$
\begin{aligned}
E_{N+1}^{(a)}
&=
E_{N}
+h_{aa}^{\sigma}
+\sum_{j,\sigma_{j}} J_{aj}^{\sigma\sigma_{j}}
-\sum_{j} K_{aj}^{\sigma},
\end{aligned}
$$

where the apparent self-interaction of the added orbital cancels between the direct and exchange pieces. Hence

$$
E_{N+1}^{(a)}-E_{N}=\varepsilon_{a}^{\sigma}.
$$

This is Koopmans' theorem. Its key assumption is the frozen-orbital approximation: when an electron is added or removed, all remaining orbitals are held fixed. Within that assumption the theorem is exact in Hartree-Fock; if the orbitals are allowed to relax, extra terms appear and the equality is lost.

For occupied states, the eigenvalues are lowered by the exchange term, which cancels the spurious repulsive self-interaction in the Hartree term. To find the energies for addition of electrons, one must compute empty orbitals of the Hartree-Fock equation (3.45). For these states there also is no spurious selfinteraction since both the direct and the exchange potential terms in Eq. (3.45) involve only the occupied states. In general, the gaps between addition and removal energies for electrons are greatly overestimated in the Hartree-Fock approximation because of the neglect of orbital relaxation and dynamical correlation. This overestimate shows that Hartree-Fock includes exchange exactly within a single determinant, but neglects the correlation screening that reduces the true cost of adding or removing an electron.

> [!lesson] Koopmans' theorem and the meaning of eigenvalues
>
> - **Hartree-Fock eigenvalues are frozen-orbital addition and removal energies.** The eigenvalue $\varepsilon_i^\sigma$ equals the energy cost of removing (or adding) an electron from (to) orbital $i$, keeping all other orbitals fixed. This is exact within the frozen-orbital approximation.
> - **The frozen-orbital approximation neglects orbital relaxation and correlation.** In reality, when an electron is removed, the remaining orbitals relax and correlation changes. Koopmans' theorem therefore systematically overestimates band gaps and ionization energies.
> - **Eigenvalues in approximate theories do not always have a simple physical meaning.** The lesson generalizes beyond Hartree-Fock: in Kohn-Sham DFT, eigenvalues are Lagrange multipliers of an auxiliary system and are not rigorously removal energies (except for the highest occupied state). Always check what an eigenvalue means in the specific theory being used.

## 3.6.4 △SCF Methods

> [!question]
>
> (a) What limitation of Koopmans' theorem does the ΔSCF approach address, and why does this yield significantly improved addition and removal energies?
> (b) Why is the ΔSCF method most naturally applied to finite systems such as atoms, and what difficulty arises when trying to extend it to extended (periodic) systems?

In finite systems, such as atoms, it is possible to improve upon the use of the eigenvalues as approximate excitation energies. Significant improvement in the addition and removal energies result from the "delta Hartree-Fock approximation," in which one calculates total energy differences directly from Eq. (3.44), allowing the orbitals to relax and taking into account the exchange of an added electron with all the others. The energy difference approach for finite systems can be used in any self-consistent field method, hence the name " $\triangle \mathrm{SCF}$." In extended (periodic) systems the method is problematic because adding or removing a single electron from an infinite system changes the total energy by an infinitesimal amount per unit cell, making the energy difference $E_{N \pm 1}-E_N$ numerically ill-defined; one must instead work with charged supercells and contend with long-range electrostatic artifacts that require careful correction. Illustrations of the $\Delta$SCF approach for finite systems are given in Section 10.6.

# 3.7 Exchange and Correlation

> [!question]
>
> (a) Why are two-body correlation functions sufficient to determine the interaction energy of a many-electron system, even though the wavefunction depends on all $N$ electron coordinates?
> (b) What does it mean physically for the pair distribution function $g(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ to equal unity, and what does a deviation from unity indicate?
> (c) Why are the remaining correlation terms $\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')$ and $g-1$ short-ranged, vanishing at large $|\mathbf{r}-\mathbf{r}'|$?

The key problem of electronic structure is that the electrons form an interacting manybody system, with a wavefunction, in general, given by $\Psi\left(\left\{\mathbf{r}_{i}\right\}\right) \equiv \Psi\left(\mathbf{r}_{1}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N}\right)$, as discussed in Section 3.1. Since the interactions always involve pairs of electrons, two-body correlation functions are sufficient to determine many properties, such as the energy given by Eq. (3.9). Writing out the form for a general expectation value Eq. (3.7) explicitly, the joint probability $n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ of finding electrons of $\operatorname{spin} \sigma$ at point $\mathbf{r}$ and of $\operatorname{spin} \sigma^{\prime}$ at point $\mathbf{r}^{\prime}$ is given by

[^8]

> [!definition] Joint pair probability (Eq. 3.50)
>
> $$
> \begin{aligned}
> n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) & =\left\langle\sum_{i \neq j} \delta\left(\mathbf{r}-\mathbf{r}_{i}\right) \delta\left(\sigma-\sigma_{i}\right) \delta\left(\mathbf{r}^{\prime}-\mathbf{r}_{j}\right) \delta\left(\sigma^{\prime}-\sigma_{j}\right)\right\rangle \\
> & =N(N-1) \sum_{\sigma_{3}, \sigma_{4}, \ldots} \int \mathrm{~d} \mathbf{r}_{3} \cdots \mathrm{~d} \mathbf{r}_{N}\left|\Psi\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime} ; \mathbf{r}_{3}, \sigma_{3} ; \ldots, \mathbf{r}_{N}, \sigma_{N}\right)\right|^{2}
> \end{aligned}
> $$

assuming $\Psi$ is normalized to unity. For uncorrelated particles, the joint probability is just the product of probabilities so that the measure of correlation is $\Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)= n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)-n(\mathbf{r}, \sigma) n\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)$, so that
$$
n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=n(\mathbf{r}, \sigma) n\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)+\Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) .
$$

It is also useful to define the normalized pair distribution,

> [!definition] Pair distribution function (Eq. 3.52)
>
> $$
> g\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=\frac{n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)}{n(\mathbf{r}, \sigma) n\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)}=1+\frac{\Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)}{n(\mathbf{r}, \sigma) n\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)},
> $$

which is unity for uncorrelated particles so that correlation is reflected in $g\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)-1$. Note that all long-range correlation is included in the average terms so that the remaining terms $\Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ and $g\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)-1$ are short range and vanish at large $\left|\mathbf{r}-\mathbf{r}^{\prime}\right|$.

## 3.7.1 Exchange in the Hartree-Fock Approximation

> [!derivation] Derivation 14: Pair distribution and exchange hole for noninteracting fermions
> Derive the pair distribution function Eq. (3.53) and the exchange hole Eq. (3.54) for a Slater-determinant wavefunction. What are the physical constraints that any exchange hole must satisfy, and can you prove them directly from your result? Why does exchange only affect electrons of the same spin? What does the exchange hole look like for the simplest cases — hydrogen and helium? (Exercises 3.12–3.14, 3.16.)

The Hartree-Fock approximation (HFA) consists of neglecting all correlations except those required by the Pauli exclusion principle; however, the exchange term in Eq. (3.44) represents two effects: Pauli exclusion and the self-term that must be subtracted to cancel the spurious self-term included in the direct Coulomb Hartree energy. The effect is always to lower the energy, which may be interpreted as the interaction of each electron with a positive "exchange hole" surrounding it. The exchange hole $\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ is given by $\Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ in the HFA, where $\Psi$ in Eq. (3.50) is approximated by the single determinant wavefunction $\Phi$ of Eq. (3.43). If the single-particle spin-orbitals $\phi_{i}^{\sigma}=\psi_{i}^{\sigma}\left(\mathbf{r}_{j}\right) \times \alpha_{i}\left(\sigma_{j}\right)$ are orthonormal, it is straightforward (Exercise 3.13) to show that the pair distribution function can be written

$$	
n_{\mathrm{HFA}}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=\frac{1}{2!} \sum_{i j}\left|\begin{array}{ll}
\phi_{i}(\mathbf{r}, \sigma) & \phi_{i}\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right) \\
\phi_{j}(\mathbf{r}, \sigma) & \phi_{j}\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)
\end{array}\right|^{2},
$$

Expanding the determinant,

$$
\begin{aligned}
\left|\begin{array}{ll}
\phi_{i}(\mathbf{r}, \sigma) & \phi_{i}\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right) \\
\phi_{j}(\mathbf{r}, \sigma) & \phi_{j}\left(\mathbf{r}^{\prime}, \sigma^{\prime}\right)
\end{array}\right|
=
\phi_{i}(\mathbf{r}, \sigma)\phi_{j}(\mathbf{r}', \sigma')
-\phi_{i}(\mathbf{r}', \sigma')\phi_{j}(\mathbf{r}, \sigma),
\end{aligned}
$$

so

$$
\begin{aligned}
n_{\mathrm{HFA}}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
&=
\frac{1}{2}\sum_{ij}
\Bigl[
|\phi_i(\mathbf{r},\sigma)|^2 |\phi_j(\mathbf{r}',\sigma')|^2
+|\phi_i(\mathbf{r}',\sigma')|^2 |\phi_j(\mathbf{r},\sigma)|^2 \\
&\qquad
-\phi_i^*(\mathbf{r},\sigma)\phi_j^*(\mathbf{r}',\sigma')\phi_i(\mathbf{r}',\sigma')\phi_j(\mathbf{r},\sigma) \\
&\qquad
-\phi_i^*(\mathbf{r}',\sigma')\phi_j^*(\mathbf{r},\sigma)\phi_i(\mathbf{r},\sigma)\phi_j(\mathbf{r}',\sigma')
\Bigr].
\end{aligned}
$$

The first two terms are equal after interchanging $i$ and $j$, and the last two terms are complex conjugates of one another, so

$$
\begin{aligned}
n_{\mathrm{HFA}}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
&=
\sum_{ij} |\phi_i(\mathbf{r},\sigma)|^2 |\phi_j(\mathbf{r}',\sigma')|^2
-\left|\sum_i \phi_i^*(\mathbf{r},\sigma)\phi_i(\mathbf{r}',\sigma')\right|^2 \\
&=
n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')
-\left|\sum_i \phi_i^*(\mathbf{r},\sigma)\phi_i(\mathbf{r}',\sigma')\right|^2 .
\end{aligned}
$$

Using $\phi_i(\mathbf{r},\sigma)=\psi_i^\sigma(\mathbf{r})\alpha_i(\sigma)$ and orthonormal spin functions,

$$
\sum_i \phi_i^*(\mathbf{r},\sigma)\phi_i(\mathbf{r}',\sigma')
=\delta_{\sigma\sigma'}\sum_i \psi_i^{\sigma *}(\mathbf{r})\psi_i^\sigma(\mathbf{r}'),
$$

so Eq. (3.51) gives

$$
\Delta n_{\mathrm{HFA}}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=n_{\mathrm{HFA}}(\mathbf{r},\sigma;\mathbf{r}',\sigma')-n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')
=-\delta_{\sigma\sigma'}\left|\sum_i \psi_i^{\sigma *}(\mathbf{r})\psi_i^\sigma(\mathbf{r}')\right|^2,
$$

which is Eq. (3.54). Therefore

$$
g_{\mathrm{HFA}}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=1-\delta_{\sigma\sigma'}
\frac{\left|\sum_i \psi_i^{\sigma *}(\mathbf{r})\psi_i^\sigma(\mathbf{r}')\right|^2}{n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')}.
$$

and the exchange hole takes the simple form

> [!definition] Exchange hole (Eq. 3.54)
>
> $$
> \Delta n_{\mathrm{HFA}}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=-\delta_{\sigma \sigma^{\prime}}\left|\sum_{i} \psi_{i}^{\sigma *}(\mathbf{r}) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right)\right|^{2} .
> $$

It is immediately clear from Eq. (3.51) and Eq. (3.54) that the exchange hole of an electron involves only electrons of the same spin and that the probability vanishes, as it must, for finding two electrons of the same spin at the same point $\mathbf{r}=\mathbf{r}^{\prime}$. Note that from Eq. (3.54) and

Eq. (3.41), it follows that in the HFA $\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=-\delta_{\sigma \sigma^{\prime}}\left|\rho_{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)\right|^{2}$, where $\rho_{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ is the density matrix, which is diagonal in spin.

This is an example of the general property [278] that indistinguishability of particles leads to correlations, which in otherwise independent-particle systems can be expressed in terms of the first-order density matrix:

$$
\Delta n_{\mathrm{ip}}\left(\mathbf{x} ; \mathbf{x}^{\prime}\right)= \pm\left|\rho_{\sigma}\left(\mathbf{x}, \mathbf{x}^{\prime}\right)\right|^{2}
$$

or

$$
g_{\mathrm{ip}}\left(\mathbf{x} ; \mathbf{x}^{\prime}\right)=1 \pm \frac{\left|\rho_{\sigma}\left(\mathbf{x}, \mathbf{x}^{\prime}\right)\right|^{2}}{n(\mathbf{x}) n\left(\mathbf{x}^{\prime}\right)}
$$

where the plus (minus) sign applies for bosons (fermions) and $\mathbf{x}$ incorporates all coordinates including position $\mathbf{r}$ and spin (if applicable). Thus $\Delta n_{\mathrm{ip}}\left(\mathbf{x} ; \mathbf{x}^{\prime}\right)$ is always positive for independent bosons and always negative for independent fermions.

There are stringent conditions on the exchange hole: (1) it can never be positive, $\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) \leq 0$ (which means that $g_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) \leq 1$ ), and (2) the integral of the exchange hole density $\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ over all $\mathbf{r}^{\prime}$ is exactly one missing electron per electron at any point $\mathbf{r}$. This is a consequence of the fact that if one electron is at $\mathbf{r}$, then that same electron cannot also be at $\mathbf{r}^{\prime}$. It also follows directly from Eq. (3.54), as shown in Exercise 3.12. The exchange energy, the last term in Eq. (3.44), can be interpreted as the lowering of the energy due to each electron interacting with its positive exchange hole,

The nonpositivity follows immediately because Eq. (3.54) is minus the modulus squared of a quantity. The sum rule follows from orthonormality:

$$
\begin{aligned}
\int \mathrm{d}^{3}r'\,\Delta n_x(\mathbf{r},\sigma;\mathbf{r}',\sigma')
&=
-\delta_{\sigma\sigma'}\int \mathrm{d}^{3}r'\,
\sum_{ij}\psi_i^{\sigma *}(\mathbf{r})\psi_i^\sigma(\mathbf{r}')
\psi_j^\sigma(\mathbf{r})\psi_j^{\sigma *}(\mathbf{r}') \\
&=
-\delta_{\sigma\sigma'}\sum_{ij}\psi_i^{\sigma *}(\mathbf{r})\psi_j^\sigma(\mathbf{r})
\int \mathrm{d}^{3}r'\,\psi_i^\sigma(\mathbf{r}')\psi_j^{\sigma *}(\mathbf{r}') \\
&=
-\delta_{\sigma\sigma'}\sum_i |\psi_i^\sigma(\mathbf{r})|^2 \\
&=
-\delta_{\sigma\sigma'}\,n(\mathbf{r},\sigma).
\end{aligned}
$$

Thus, conditional on an electron of spin $\sigma$ being at $\mathbf{r}$, the integrated hole contains exactly one missing same-spin electron.

> [!equation] Exchange energy from the exchange hole (Eq. 3.57)
>
> $$
> E_{x}=\left[\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_{\mathrm{Hartree}}(n)\right]_{\mathrm{HFA}}=\frac{1}{2} \sum_{\sigma \sigma^{\prime}} \int \mathrm{d}^{3} r \int \mathrm{~d}^{3} r^{\prime} \frac{\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
> $$

In this form it is clear that the exchange energy cancels the unphysical self-interaction term in the Hartree energy.

The simplest example of an exchange hole is a one-electron problem, such as the hydrogen atom. There is, of course, no real "exchange" nor any issue of the Pauli exclusion principle, and it is easy to see that the exchange hole is just minus the one-electron density. Its integral is minus unity, so the conditional missing charge is exactly one electron, as required by the sum rule, and the exchange energy cancels the spurious Hartree term. Because of this cancellation, the Hartree-Fock equation (3.45) correctly reduces to the usual Schrödinger equation for one electron in an external potential.

Indeed, for one occupied orbital $\psi(\mathbf{r})$,

$$
\Delta n_x(\mathbf{r};\mathbf{r}')
=-|\psi(\mathbf{r})|^2|\psi(\mathbf{r}')|^2
=-n(\mathbf{r})n(\mathbf{r}'),
$$

so the conditional hole is just minus the full one-electron density.

The next more complex case is a two-electron singlet such as the ground state of He. In this case (see Exercise 3.16) the two spins have identical spatial orbitals and the exchange term is minus one-half the Hartree term in the Hartree-Fock equation (3.44), so that the Hartree-Fock equation (3.45) simplifies to a Hartree-like equation of the form of Eq. (3.36) with $V_{\text {eff }}$ a sum of the external (nuclear) potential plus one-half the Hartree potential. ${ }^{11}$

If the two electrons occupy the same spatial orbital $\psi(\mathbf{r})$ with opposite spins, then

$$
n(\mathbf{r},\uparrow)=|\psi(\mathbf{r})|^2,
\qquad
n(\mathbf{r},\downarrow)=|\psi(\mathbf{r})|^2,
$$

and

$$
\Delta n_x(\mathbf{r},\uparrow;\mathbf{r}',\uparrow)
=-|\psi(\mathbf{r})|^2|\psi(\mathbf{r}')|^2,
\qquad
\Delta n_x(\mathbf{r},\uparrow;\mathbf{r}',\downarrow)=0,
$$

with analogous expressions for a reference down-spin electron. Thus each electron sees an exchange hole only in its own spin channel; the opposite-spin electron is unaffected by exchange, which is why in helium the exchange contribution removes half of the Hartree self-repulsion but does not cancel the true Coulomb repulsion between the opposite-spin electrons.

[^9]For systems with many electrons the exchange hole must be calculated numerically, except for special cases. The most relevant for us is the homogeneous gas considered in the following section.

> [!lesson] The exchange hole and its physical constraints
>
> - **The exchange hole is always non-positive and integrates to exactly one missing electron.** These are exact constraints that any approximation to exchange must satisfy. The non-positivity follows from the squared-modulus form of Eq. (3.54); the sum rule follows from orthonormality of the orbitals.
> - **Exchange acts only between same-spin electrons.** The Kronecker delta $\delta_{\sigma\sigma'}$ in the exchange hole means opposite-spin electrons are unaffected by exchange. This is why spin-polarized systems (e.g., ferromagnets) have lower exchange energy — more same-spin pairs means a deeper exchange hole.
> - **The exchange energy is the interaction of each electron with its positive exchange hole.** This reinterpretation of the last term in Eq. (3.44) is physically intuitive: each electron digs a hole in the surrounding same-spin density, and the Coulomb attraction to this hole lowers the energy.
> - **For one-electron systems, the exchange hole exactly cancels the Hartree self-interaction.** This is the simplest consistency check: any theory that fails to cancel self-interaction for hydrogen is fundamentally flawed.

## 3.7.2 Beyond Hartree-Fock: Correlation

> [!question]
>
> (a) Why is the correlation energy always negative for the ground state, and what variational theorem guarantees this?
> (b) What are the two standard choices of reference state used to define $E_c$, and why does the distinction matter in principle even if numerically it is often small?
> (c) How does correlation affect both the kinetic and potential energies simultaneously, and what technique from §3.4 provides a unified framework for accounting for both contributions?

The energy of a state of many electrons in the Hartree-Fock approximation Eq. (3.44) is the best possible wavefunction made from a single determinant (or a sum of a few determinants in multireference Hartree-Fock [274] needed for degenerate cases). Improvement of the wavefunction to include correlation introduces extra degrees of freedom in the wavefunction and therefore always lowers the energy for any state, ground or excited, by a theorem often attributed to MacDonald [279]. The lowering of the energy is termed the "correlation energy" $E_{c}$.

This is not the only possible definition of $E_{c}$, which could also be defined as the difference from some other reference state. The definition in terms of the difference from Hartree-Fock is a well-defined choice in the sense that it leads to the smallest possible magnitude of $E_{c}$, since $E_{\mathrm{HFA}}$ is the lowest possible energy neglecting correlation. Another well-defined choice arises naturally in density functional theory, where $E_{c}$ is also defined as the difference between the exact energy and the energy of an uncorrelated state as Eq. (3.44), but with the difference that the orbitals are required to give the exact density (see Section 3.2 and Chapter 7). In many practical cases this distinction appears not to be of great importance; nevertheless, it is essential to define the energies properly, especially as electronic structure methods become more and more powerful in their ability to calculate effects of correlation.

> [!derivation] Derivation 15: Correlation hole sum rule
> Decompose the full exchange-correlation hole into its exchange and correlation parts (Eq. 3.58). What sum rule does the correlation hole satisfy, and can you prove it from conservation laws alone without computing any wavefunctions beyond Hartree-Fock? Physically, what does this sum rule tell you about what correlation does to the charge distribution around an electron? (Exercise 3.22.)

The effects of correlation can be cast in terms of the remaining part of the pair correlation function beyond exchange $n_{c}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ defined in terms of Eqs. (3.50) and (3.51) by

> [!definition] Exchange-correlation hole (Eq. 3.58)
>
> $$
> \Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) \equiv n_{\mathrm{xc}}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)+n_{c}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) .
> $$

The sum rule for the full exchange-correlation hole follows from particle conservation alone. Starting from Eq. (3.50), integrate over the second electron coordinate and spin:

$$
\begin{aligned}
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,
n(\mathbf{r},\sigma;\mathbf{r}',\sigma')
&=
\left\langle
\sum_{i\neq j}
\delta(\mathbf{r}-\mathbf{r}_{i})\delta(\sigma-\sigma_{i})
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,
\delta(\mathbf{r}'-\mathbf{r}_{j})\delta(\sigma'-\sigma_{j})
\right\rangle \\
&=
\left\langle
\sum_{i\neq j}
\delta(\mathbf{r}-\mathbf{r}_{i})\delta(\sigma-\sigma_{i})
\right\rangle \\
&=
(N-1)\,n(\mathbf{r},\sigma).
\end{aligned}
$$

Using Eq. (3.51),

$$
n(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=
n(\mathbf{r},\sigma)n(\mathbf{r}',\sigma')
+
\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma'),
$$

and integrating gives

$$
\begin{aligned}
(N-1)n(\mathbf{r},\sigma)
&=
n(\mathbf{r},\sigma)\sum_{\sigma'}\int \mathrm{d}^{3}r'\,n(\mathbf{r}',\sigma')
+
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma') \\
&=
N\,n(\mathbf{r},\sigma)
+
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma').
\end{aligned}
$$

Therefore

$$
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=-\,n(\mathbf{r},\sigma).
$$

That is, the full exchange-correlation hole contains one missing electron when normalized by the reference density:

$$
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,
\frac{\Delta n(\mathbf{r},\sigma;\mathbf{r}',\sigma')}{n(\mathbf{r},\sigma)}
=-1.
$$

From Derivation 14, the exchange hole by itself obeys the same sum rule,

$$
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,
n_{x}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=-\,n(\mathbf{r},\sigma).
$$

Subtracting this from Eq. (3.58) gives the correlation-hole sum rule

$$
\sum_{\sigma'}\int \mathrm{d}^{3}r'\,
n_{c}(\mathbf{r},\sigma;\mathbf{r}',\sigma')
=0.
$$

Thus correlation does not change the total missing charge around a reference electron; it only redistributes it in space. In other words, exchange already accounts for the fact that one electron excludes exactly one electron's worth of same-spin probability, while correlation reshapes that hole by shifting charge from some regions to others. In general, correlation is most important for electrons of opposite spin, since electrons of the same spin are already kept apart by the exclusion principle. For the ground state the correlation energy is always negative and any approximation should be negative. Excited states involve energy differences from the ground state, e.g., an exciton energy. Depending on the effects of correlation in the two states, the difference can be positive or negative.

The correlation energy is more complicated to calculate than the exchange energy because correlation affects both kinetic and potential energies. Both effects can be taken into account by a "coupling constant integration" using the methods of Section 3.4. The theory of interacting systems is beyond the scope of this book and the reader is referred to the companion volume [1] for an in-depth presentation. Nevertheless, it is essential to take correlation into account in realistic calculations, and the goal here is to show how to understand and use aspects that have an important role in present-day electronic structure
theory and practical calculations. Coupling constant integration is discussed for the model system, the homogeneous gas in Chapter 5, and is a key aspect of ongoing developments of functionals for density functional theory (see especially Sections 8.2, 9.3, and 9.7).

> [!lesson] Correlation: what it does and what it doesn't do
>
> - **The correlation hole integrates to zero.** Unlike the exchange hole (which accounts for one missing electron), the correlation hole only *redistributes* charge — it removes density from some regions and adds it to others, but the total missing charge is unchanged. This is a consequence of particle conservation alone and holds for any wavefunction.
> - **Correlation is most important for opposite-spin electrons.** Same-spin electrons are already kept apart by the Pauli exclusion principle (exchange). The main effect of correlation is to further reduce the probability of finding opposite-spin electrons close together (Coulomb correlation).
> - **The correlation energy is always negative for the ground state.** Adding variational degrees of freedom beyond a single determinant always lowers the energy, by MacDonald's theorem. Any approximation to the ground-state correlation energy should therefore be negative.
> - **Correlation affects both kinetic and potential energy simultaneously.** This is why direct calculation of $E_c$ is difficult — one cannot simply compute a "correlation potential." The coupling constant integration from §3.4 provides a unified framework that accounts for both contributions.

# SELECT FURTHER READING

The companion book [1] also presents the basic theory with an emphasis on the role of correlation beyond Hartree-Fock. In that book, Hartree-Fock plays a larger role because it is the starting point for the development of much of the theory.

See the list of texts at the end of Chapter 2.
Reference for Hartree-Fock:
Szabo, A. and Ostlund, N. S., Modern Quantum Chemistry: Introduction to Advanced Electronic Structure Theory (Dover, Mineola, New York, 1996).

# Exercises

3.1 Show that the many-body Schrödinger equation (3.13) also results from explicit variation of the energy in Eq. (3.9) without use of Lagrange multipliers.
3.2 Show that the independent-particle Schrödinger equation (3.36) is a special case of the manybody solution. Show this first for one particle, then for many noninteracting particles.
3.3 As part of his undergraduate thesis, Feynman showed that the force theorem applied to a nucleus leads to the force being exactly the electric field at the given nucleus due to the charge density of the rest of the system (electrons and other nuclei) times the charge of the given nucleus. Derive this result from Eq. (3.19).
3.4 Derive the additional terms that must be included so that the expression for the force given by the force theorem is identical to the explicit derivative of the energy if the basis depends explicitly on the positions for the nuclei. Show that the contribution of these terms vanishes if the basis is complete.
3.5 Derive the stress theorem Eq. (3.23). Show that this equation reduces to the well-known virial theorem Eq. (3.24) in the case of isotropic pressure and Coulomb interactions.
3.6 Show that the relations for noninteracting particles given in the equations following Eq. (3.36) remain valid if a fully antisymmetric determinant wavefunction like Eq. (3.43) is created from the orbitals. Note that this holds only if the particles are noninteracting.
3.7 Derive the Fermi-Dirac distribution Eq. (3.38) for noninteracting particles from the general definition of the density matrix Eq. (3.32) using the fact that the sum over many-body states in Eq. (3.32) can be reduced to a sum over all possible occupation numbers $\left\{n_{i}^{\sigma}\right\}$ for each of the independent-particle states, subject to the conditions that each $n_{i}^{\sigma}$ can be either 0 or 1 , and $\sum_{i} n_{i}^{\sigma}=N^{\sigma}$.
3.8 Following Exercise 3.7, show that Eq. (3.35) simplifies to Eq. (3.37) for any operator in the independent-particle approximation.
3.9 Why is the independent particle density matrix Eq. (3.41) diagonal in spin? Is this always the case?
3.10 Show that the Hartree-Fock wavefunction Eq. (3.43) is normalized if the independent-particle orbitals are orthonormal.
3.11 Show that the Hartree-Fock wavefunction Eq. (3.43) leads to the exchange term in Eq. (3.44) and that the variational equation leads to the Hartree-Fock equation (3.45) if the independentparticle orbitals are orthonormal. Explain why the forms are more complicated if the independent-particle orbitals are not orthonormal.
3.12 Show explicitly from the definition Eq. (3.54) that the exchange hole around each electron always integrates to one missing electron. Show that, as stated in the text, this is directly related to the fact that "exchange" includes a self-term that cancels the unphysical self-interaction in the Hartree energy.
3.13 Derive the formulas for the pair distribution Eq. (3.53) and the exchange hole Eq. (3.54) for noninteracting fermions by inserting the Hartree-Fock wavefunction Eq. (3.43) into the general definition Eq. (3.50).
3.14 By expanding the $2 \times 2$ determinant in Eq. (3.53), (a) show that

$$
\sum_{\sigma^{\prime}} \int \mathrm{d} r^{\prime} \Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=(N-1) n(\mathbf{r}, \sigma),
$$

where $n(\mathbf{r}, \sigma)$ is the density, and (b) derive the formula Eq. (3.54) for the exchange hole.
3.15 The relation Eq. (3.55) is a general property of noninteracting identical particles [278]. As shown in Eq. (3.54), $\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ is always negative for fermions. Show that for bosons with a symmetric wavefunction, the corresponding exchange term is always positive.
3.16 Derive the results stated after Eq. (3.57) that (a) for a one-electron problem like hydrogen, the exchange term exactly cancels the Hartree term as it should and that (b) for the ground state of two electrons in a spin singlet state, e.g., in helium, the Hartree-Fock approximation leads to a $V_{\text {eff }}$ sum of the external (nuclear) potential plus one-half the Hartree potential.
3.17 Following the exercise above, consider two electrons in a spin triplet state. Show that the situation is not so simple as for the singlet case, i.e., that in the Hartree-Fock approximation there must be two different functions $V_{\text {eff }}$ for two different orbitals.
3.18 Derive Koopmans' theorem by explicitly taking matrix elements of the hamiltonian with an orbital to show that the eigenvalue is the same as the energy difference if that orbital is removed.
3.19 For adding electrons one must compute empty orbitals of the Hartree-Fock equation (3.45). Show that such an empty orbital does not experience a self-contribution to the exchange energy, whereas for a filled state there is a self-term in the exchange. Show that the same result for the addition energy is found if one explicitly includes the state in a calculation with one added electron but keeps the original orbitals unchanged.
3.20 In a finite system Hartree-Fock eigenfunctions have the (surprising) property that the form of the long-range decay of all bound states is the same, independent of binding energy. For example, core states have the same exponential decay as valence states, although the prefactor is smaller. Show that this follows from Eq. (3.45).
3.21 Show that all contributions involving $i$ and $j$ both occupied vanish in the expectation value Eq. (D.4).
3.22 Show that the correlation hole always integrates to zero, i.e., it rearranges the charge correlation. This does not require complex calculations beyond Hartree-Fock theory; all that is needed is to show that conservation laws must lead to this result.
3.23 As an example of the force theorem consider a one-dimensional harmonic oscillator with hamiltonian given by $-\frac{1}{2}\left(\mathrm{~d}^{2} / \mathrm{d} x^{2}\right)+\frac{1}{2} A x^{2}$, where $A$ is the spring constant and the mass is set to unity. Using the exact solution for the energy and wavefunction, calculate the generalized force $\mathrm{d} E / \mathrm{d} A$ by direct differentiation and by the force theorem.


[^0]:    ${ }^{1}$ There are also other ingredients in the fundamental theory that are incorporated later, including spin-orbit interaction $H_{S O}$ in Eq. (O.8) derived from the Dirac equation in Appendix O; electromagnetic fields that can be taken into account by adding a vector potential with the replacement $\mathbf{p} \rightarrow \boldsymbol{\pi}=\mathbf{p}-(e / c) \mathbf{A}$ (see Appendix E); and a Zeeman term in the hamiltonian $\mu_{B} \boldsymbol{\sigma} \cdot \mathbf{B}$, where $\mu_{B}=\hbar e / 2 m$ is the Bohr magneton. These are independent-electron terms that are often small and are ignored in much of this book; however, they are responsible for some of the most interesting phenomena in condensed matter including topological insulators.

[^1]:    2 The method in its present form was developed by Ritz [258] in 1908, but the approach was used previously by Lord Rayleigh (John William Strutt) in several problems described in his 1877 book [259] and earlier work. The methods are described in many more texts, such as [260-262].
    ${ }^{3}$ This is an example of functional derivatives described in Appendix A for the case where the energy functional Eq. (3.9) is linear in both the bra $\langle\Psi|$ and the ket $|\Psi\rangle$ functions. Thus one may vary either or both at the same time with the same result.

[^2]:    ${ }^{4}$ This definition differs from that given in many texts (see Section 3.7) as the difference from Hartree-Fock, since the Hartree-Fock density differs from the true density.

[^3]:    ${ }^{5}$ A clear derivation is given in [272] and an extensive description is given in [273].

[^4]:    ${ }^{6}$ The change in energy can be computed for any ground or excited state. States of different symmetry can be followed uniquely even if they cross. In many cases it is more efficient to solve a matrix equation (the size of the number of states of the same symmetry that are strongly mixed).

[^5]:    ${ }^{7}$ Historically, the first quantitative calculations on many-electron systems were carried out on atoms by D. R. Hartree [50], who solved, numerically, the equation for each electron moving in a central potential due to other electrons and the nucleus. Hartree defined a different potential for each electron because he subtracted a self-term for each electron that depended on its orbital. However, following the later development of the Hartree-Fock method [53], it is now customary to define the effective "Hartree potential" with an unphysical self-interaction term so that the potential is orbital independent. This unphysical term has no effect since it is canceled by the exchange term in Hartree-Fock calculations.

[^6]:    ${ }^{8}$ Spin is introduced at this point because it is necessary to introduce a spin-dependent effective potential in order for the independent-particle equations to describe spin-polarized states. In order to include the spin-orbit interaction, Eq. (3.36) must be generalized to a single equation with two components as in Eq. (O.7) with a term like $H_{S O}$ in Eq. (O.9), and sum over spin replaced by a trace.

[^7]:    ${ }^{9}$ The determinant formulation had been realized by Dirac [24] before Slater's work, but the determinant of spinorbitals is due to Slater [25], who believed this was his most popular work [48] because it replaced difficult group theoretical arguments by this simple form.

[^8]:    ${ }^{10}$ Tjalling Koopmans is famous in chemistry and physics for his theorem [277], but his major work was in economics, for which he was awarded a Nobel prize in 1975.

[^9]:    ${ }^{11}$ This is exactly what D. R. Hartree did in his pioneering work [50]; however, his approach of subtracting a self-term for each electron is not the same as the more proper Hartree-Fock theory for more than two electrons.
