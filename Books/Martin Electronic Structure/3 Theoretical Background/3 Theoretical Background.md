**3**

**Theoretical Background**

**Summary**

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
> Derive the electronic Hamiltonian Eq. (3.2) from the full Hamiltonian Eq. (3.1). What is the small parameter that controls the approximation, and why is it physically reasonable? Under what circumstances does this approximation break down, and what phenomena become inaccessible?

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

$\hat{V}_{\text {ext }}$ is the potential acting on the electrons due to the nuclei,

$$
\hat{V}_{\mathrm{ext}}=\sum_{i, I} V_{I}\left(\left|\mathbf{r}_{i}-\mathbf{R}_{I}\right|\right) ;
$$

$\hat{V}_{\text {int }}$ is the electron-electron interaction,

$$
\hat{V}_{\mathrm{int}}=\frac{1}{2} \sum_{i \neq j} \frac{1}{\left|\mathbf{r}_{i}-\mathbf{r}_{j}\right|}
$$

and the final term $E_{I I}$ is the classical interaction of nuclei with one another and any other terms that contribute to the total energy of the system but are not germane to the problem of describing the electrons. Here the effect of the nuclei upon the electrons is included in a fixed potential "external" to the electrons. This general form is still valid if the bare nuclear Coulomb interaction is replaced by a pseudopotential that takes into account effects of core electrons (except that the potentials are "nonlocal"; see Chapter 11). Also, other "external potentials," such as electric fields and Zeeman terms, can readily be included. Thus, for electrons, the hamiltonian, Eq. (3.2), is central to the theory of electronic structure.

## 3.1.1 Schrödinger Equation for the Many-Body Electron System

The fundamental equation governing a nonrelativistic quantum system is the timedependent Schrödinger equation,

$$
i \hbar \frac{\mathrm{~d} \Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)}{\mathrm{d} t}=\hat{H} \Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)
$$

where the many-body wavefunction for the electrons is $\Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right) \equiv \Psi\left(\mathbf{r}_{1}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N} ; t\right)$, the spin is assumed to be included in the coordinate $\mathbf{r}_{i}$, and, of course, the wavefunction must be antisymmetric in the coordinates of the electrons $\mathbf{r}_{1}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N}$. The eigenstates of Eq. (3.6) can be written as $\Psi\left(\left\{\mathbf{r}_{i}\right\} ; t\right)=\Psi\left(\left\{\mathbf{r}_{i}\right\}\right) \mathrm{e}^{-\mathrm{i}(E / \hbar) t}$. Even though it is not feasible to actually solve the equations for many interacting electrons, it is very useful and instructive to define properties such as the energy, density, forces, and excitations in the full many-body framework before making approximations.

For an eigenstate, the time-independent expression for any observable is an expectation value of an operator $\hat{O}$, which involves an integral over all coordinates,

$$
\langle\hat{O}\rangle=\frac{\langle\Psi| \hat{O}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}
$$

> [!derivation] Derivation 2: Electron density from the density operator
> Derive the integral formula Eq. (3.8) for $n(\mathbf{r})$ from the density operator and the expectation value Eq. (3.7). Where does the prefactor $N$ come from, and what property of the wavefunction is responsible for it?

The density of particles $n(\mathbf{r})$, which plays a central role in electronic structure theory, is given by the expectation value of the density operator $\hat{n}(\mathbf{r})=\sum_{i=1, N} \delta\left(\mathbf{r}-\mathbf{r}_{i}\right)$,

> [!definition] Electron density (Eq. 3.8)
>
> $$
> n(\mathbf{r})=\frac{\langle\Psi| \hat{n}(\mathbf{r})|\Psi\rangle}{\langle\Psi \mid \Psi\rangle}=N \frac{\int \mathrm{~d}^{3} r_{2} \cdots \mathrm{~d}^{3} r_{N} \sum_{\sigma_{1}}\left|\Psi\left(\mathbf{r}, \mathbf{r}_{2}, \mathbf{r}_{3}, \ldots, \mathbf{r}_{N}\right)\right|^{2}}{\int \mathrm{~d}^{3} r_{1} \mathrm{~d}^{3} r_{2} \cdots \mathrm{~d}^{3} r_{N}\left|\Psi\left(\mathbf{r}_{1}, \mathbf{r}_{2}, \mathbf{r}_{3}, \ldots, \mathbf{r}_{N}\right)\right|^{2}},
> $$

To see this, insert the density operator into the expectation value (assuming $\langle\Psi|\Psi\rangle = 1$ for clarity):

$$
\begin{aligned}
n(\mathbf{r})
&= \langle\Psi| \hat{n}(\mathbf{r}) |\Psi\rangle \\
&= \sum_{i=1}^{N} \int \mathrm{d}^{3}r_{1} \cdots \mathrm{d}^{3}r_{N}\; \Psi^{*}(\mathbf{r}_{1},\ldots,\mathbf{r}_{N})\,\delta(\mathbf{r}-\mathbf{r}_{i})\,\Psi(\mathbf{r}_{1},\ldots,\mathbf{r}_{N}).
\end{aligned}
$$

For the $i$-th term in the sum, the delta function $\delta(\mathbf{r}-\mathbf{r}_{i})$ collapses the $\mathbf{r}_{i}$ integration, setting $\mathbf{r}_{i} = \mathbf{r}$. The $i = 1$ contribution, for instance, gives

$$
\int \mathrm{d}^{3}r_{2} \cdots \mathrm{d}^{3}r_{N}\; |\Psi(\mathbf{r}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N})|^{2}.
$$

Because the electrons are identical fermions, $|\Psi|^{2}$ is symmetric under exchange of any two electron coordinates (the antisymmetry of $\Psi$ squares away). Therefore every term in the sum over $i$ gives exactly the same integral — only the label of the "surviving" coordinate differs. Summing all $N$ identical terms produces the factor of $N$ in Eq. (3.8).

> [!derivation] Derivation 3: Total energy expression — external potential reduces to a density integral
> Using the result for $n(\mathbf{r})$ from Eq. (3.8), simplify the total energy expectation value into the form of Eq. (3.9). Which terms in the Hamiltonian can be expressed purely in terms of the density, and which cannot? What is it about the structure of a one-body vs. two-body operator that makes the difference?

The total energy is the expectation value of the hamiltonian. Using $\hat{H} = \hat{T} + \hat{V}_{\text{ext}} + \hat{V}_{\text{int}} + E_{II}$, the linearity of the expectation value gives

$$
E = \langle\hat{H}\rangle = \langle\hat{T}\rangle + \langle\hat{V}_{\text{ext}}\rangle + \langle\hat{V}_{\text{int}}\rangle + E_{II}.
$$

The external potential is a one-body operator, $\hat{V}_{\text{ext}} = \sum_{i} V_{\text{ext}}(\mathbf{r}_{i})$. Its expectation value therefore reduces by the same logic used for the density operator (Derivation 2): each term in the sum over $i$ gives the same integral after exploiting the exchange symmetry of $|\Psi|^{2}$, so

$$
\begin{aligned}
\langle\hat{V}_{\text{ext}}\rangle
&= \sum_{i=1}^{N} \int \mathrm{d}^{3}r_{1} \cdots \mathrm{d}^{3}r_{N}\; |\Psi|^{2}\, V_{\text{ext}}(\mathbf{r}_{i}) \\
&= N \int \mathrm{d}^{3}r\, V_{\text{ext}}(\mathbf{r}) \int \mathrm{d}^{3}r_{2} \cdots \mathrm{d}^{3}r_{N}\; |\Psi(\mathbf{r}, \mathbf{r}_{2}, \ldots, \mathbf{r}_{N})|^{2} \\
&= \int \mathrm{d}^{3}r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}).
\end{aligned}
$$

In the last step we recognized the definition of $n(\mathbf{r})$ from Eq. (3.8). This reduction works for any one-body operator — only one electron coordinate appears in the operator, so the remaining $N-1$ integrations produce the density. The kinetic energy $\langle\hat{T}\rangle$ and the electron-electron interaction $\langle\hat{V}_{\text{int}}\rangle$ cannot be similarly simplified: $\hat{T}$ involves derivatives (not just multiplication), and $\hat{V}_{\text{int}}$ is a two-body operator coupling pairs of coordinates. Thus the total energy takes the form

> [!theorem] Total energy as expectation value (Eq. 3.9)
>
> $$
> E=\frac{\langle\Psi| \hat{H}|\Psi\rangle}{\langle\Psi \mid \Psi\rangle} \equiv\langle\hat{H}\rangle=\langle\hat{T}\rangle+\left\langle\hat{V}_{\mathrm{int}}\right\rangle+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I}
> $$

where the expectation value of the external potential has been explicitly written as a simple integral over the density function. The final term $E_{I I}$ is the electrostatic nucleus-nucleus (or ion-ion) interaction, which is essential in the total energy calculation but is only a classical additive term in the theory of electronic structure.

> [!derivation] Derivation 4: Rayleigh-Ritz variational principle → Schrödinger equation
> Derive the time-independent Schrödinger equation Eq. (3.13) as a stationarity condition of the energy. Why is the variational formulation more fundamental than the eigenvalue equation for practical electronic structure? Compare the Lagrange-multiplier route (Eqs. 3.10–3.12) with direct variation of the ratio Eq. (3.9) (Exercise 3.1) — why must they agree?

The eigenstates of the many-body hamiltonian are stationary points (saddle points or the minimum) of the energy expression (3.9) if $\Psi$ is regarded as a variable trial function. These may be found by varying the ratio in Eq. (3.9) or by varying the numerator subject to the constraint of orthonormality $(\langle\Psi \mid \Psi\rangle=1)$, which can be done using the method of Lagrange multipliers,

$$
\delta[\langle\Psi| \hat{H}|\Psi\rangle-E(\langle\Psi \mid \Psi\rangle-1)]=0 .
$$

This is equivalent to the well-known Rayleigh-Ritz principle ${ }^{2}$

> [!theorem] Rayleigh-Ritz variational principle (Eq. 3.11)
>
> $$
> \Omega_{\mathrm{RR}}=\langle\Psi| \hat{H}-E|\Psi\rangle,
> $$

which is stationary at any eigensolution $\left|\Psi_{m}\right\rangle .{ }^{3}$ Variation of the bra $\langle\Psi|$ leads to

$$
\langle\delta \Psi| \hat{H}-E|\Psi\rangle=0
$$

Since this must hold true for all possible $\langle\delta \Psi|$, this can be satisfied only if the ket $|\Psi\rangle$ satisfies the time-independent Schrödinger equation

> [!theorem] Time-independent Schrödinger equation (Eq. 3.13)
>
> $$
> \hat{H}|\Psi\rangle=E|\Psi\rangle .
> $$

In Exercise 3.1 it is shown that the same equations result from explicit variation of $\Psi$ in Eq. (3.9) without Lagrange multipliers.

---

The ground-state wavefunction $\Psi_{0}$ is the state with the lowest energy, which can be determined, in principle, by minimizing the total energy with respect to all the parameters in $\Psi\left(\left\{\mathbf{r}_{i}\right\}\right)$, with the constraint that $\Psi$ must obey the particle symmetry and any conservation laws. Excited states are saddle points of the energy with respect to variations in $\Psi$.

## 3.1.2 Ground and Excited Electronic States

The distinction between ground and excited states pointed out in Chapter 2 is equally obvious when approached from the point of view of solving the many-body equations for the electrons. Except in special cases, the ground state must be treated by nonperturbative methods because the different terms in the energy equation are large and tend to cancel. The properties of the ground state include the total energy, electron density, and correlation functions. From the correlation functions one can derive properties that at first sight would not be considered to be ground-state properties, such as whether the material is a metal or an insulator. In any case, one needs to establish which state is the ground state, often comparing states that are very different in character but similar in energy.

On the other hand, excitations in condensed matter are usually small perturbations on the entire system. These perturbations can be classified into variations of the ground electronic state (e.g., small displacements of the ions in phonon modes) or true electronic excitations (e.g., optical electronic excitations). In both cases, perturbation theory is the appropriate tool. Using perturbation techniques, one can calculate excitation spectra and the real and imaginary parts of response functions. Nevertheless, even in this case one needs to know the ground state, since the excitations are perturbations on the ground state.

These approaches apply both in independent-particle and in many-body problems. The ground state is special in both cases and it is interesting that both density functional theory

[^1]and quantum Monte Carlo are primarily ground-state methods. The role of perturbation theory is rather different in independent-particle and many-body problems - in the latter, it plays a key role in the basic formulation of the problem in diagrammatic perturbation series and in suggesting the key ideas for summation of appropriate diagrams.

# 3.2 Coulomb Interaction in Condensed Matter

It is helpful to clarify briefly several points that are essential to a proper definition of energies in extended systems with long-range Coulomb interaction. For a more complete analysis see Appendix F. The key points are as follows:

- Any extended system must be neutral if the energy is to be finite.
- Terms in the energy must be organized in neutral groups for actual evaluation.

> [!derivation] Derivation 5: Grouping the total energy into neutral classical Coulomb terms
> The individual terms in Eq. (3.9) are separately divergent in an extended system. Rewrite the total energy so that all long-range Coulomb contributions are collected into a single, well-defined classical energy. What condition on the system is required for this grouping to be finite? What is the physical character of the residual non-classical piece, and why is it short-ranged?

In Eq. (3.9) the most convenient approach is to identify and group together terms representing the classical Coulomb energies,

> [!equation] Classical Coulomb energy grouping (Eq. 3.14)
>
> $$
> E^{\mathrm{CC}}=E_{\mathrm{Hartree}}+\int \mathrm{d}^{3} r V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+E_{I I},
> $$

where $E_{\text {Hartree }}$ is the self-interaction energy of the density $n(\mathbf{r})$ treated as a classical charge density

> [!definition] Hartree energy (Eq. 3.15)
>
> $$
> E_{\text {Hartree }}=\frac{1}{2} \int \mathrm{~d}^{3} r \mathrm{~d}^{3} r^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} .
> $$

Since $E_{I I}$ is the interaction among the positive nuclei and $\int \mathrm{d}^{3} r V_{\text {ext }}(\mathbf{r}) n(\mathbf{r})$ is the interaction of the electrons with the nuclei, Eq. (3.14) is a neutral grouping of terms so long as the system is neutral. The evaluation of classical Coulomb energies is an intrinsic part of quantitative electronic structure calculations; methods for dealing with long-range Coulomb interaction are described in Appendix F.

It then follows that the total energy expression, (3.9), can be rearranged by adding and subtracting $E_{\text{Hartree}}$:

$$
\begin{aligned}
E &= \langle\hat{T}\rangle + \langle\hat{V}_{\text{int}}\rangle + \int \mathrm{d}^{3}r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II} \\
&= \langle\hat{T}\rangle + \langle\hat{V}_{\text{int}}\rangle + \bigl(\underbrace{E_{\text{Hartree}} + \int \mathrm{d}^{3}r\, V_{\text{ext}}(\mathbf{r})\, n(\mathbf{r}) + E_{II}}_{E^{\text{CC}}}\bigr) - E_{\text{Hartree}} \\
&= \langle\hat{T}\rangle + \bigl(\langle\hat{V}_{\text{int}}\rangle - E_{\text{Hartree}}\bigr) + E^{\text{CC}}.
\end{aligned}
$$

That is,

> [!equation] Total energy decomposition with exchange-correlation (Eq. 3.16)
>
> $$
> E=\langle\hat{T}\rangle+\left(\left\langle\hat{V}_{\text {int }}\right\rangle-E_{\text {Hartree }}\right)+E^{\mathrm{CC}},
> $$

where each of the three terms is well defined. The middle term in brackets, $\left\langle\hat{V}_{\text {int }}\right\rangle-E_{\text {Hartree }}$, is the difference between the Coulomb energies of interacting, correlated electrons with density $n(\mathbf{r})$ and that of a continuous classical charge distribution having the same density, which is defined to be the potential part of the exchange-correlation energy $E_{\mathrm{xc}}$ in density functional theory (see Sections 6.4 and 8.2, especially the discussion related to Eq. (8.3)). ${ }^{4}$ Thus all long-range interactions cancel in the difference so that effects of exchange and correlation are short ranged. This is a point to which we will return in Chapter 7 and Appendix H.

[^2]
# 3.3 Force and Stress Theorems

## 3.3.1 Force (Hellmann-Feynman) Theorem

One of the beautiful theorems of physics is the "force theorem" for the force conjugate to any parameter in the hamiltonian. This is a very general idea perhaps formulated first in 1927 by Ehrenfest [263], who recognized that it is crucial for the correspondence principle of quantum and classical mechanics. He established the relevant relation by showing that the expression for force given below equals the expectation value of the operator corresponding to acceleration $\left\langle\mathrm{d}^{2} \hat{x} / \mathrm{d} t^{2}\right\rangle$. The ideas are implicit in the 1928 work of Born and Fock [264], and the explicit formulas used today were given by Güttiger [265] in 1932. The formulas were included in the treatises of Pauli [266] and Hellmann [267], the latter reformulating them as a variational principle in a form convenient for application to molecules. In 1939, when he was an undergraduate, Feynman [268] derived the force theorem and explicitly pointed out that the force on a nucleus is given strictly in terms of the charge density, independent of the electron kinetic energy, exchange, and correlation. Thus as an "electrostatic theorem," it should apparently be attributed to Feynman. The nomenclature "Hellmann-Feynman theorem" has been widely used, apparently originating with Slater [48]; however, we will use the term "force theorem."

> [!derivation] Derivation 6: Force (Hellmann-Feynman) theorem
> Derive the expression Eq. (3.19) for the force on a nucleus. The result is remarkable: despite the electrons having kinetic energy and mutual interactions that both change as nuclei move, the force depends only on the electron density. What principle causes all other contributions to vanish, and under what circumstances can this cancellation fail?

The force conjugate to any parameter describing a system, such as the position of a nucleus $\mathbf{R}_{I}$, can always be written

$$
\mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}
$$

From the general expression for the total energy Eq. (3.9), the derivative can be written using first-order perturbation theory (the normalization does not change and we assume $\langle\Psi \mid \Psi\rangle=1$ for convenience),

$$
-\frac{\partial E}{\partial \mathbf{R}_{I}}=-\langle\Psi| \frac{\partial \hat{H}}{\partial \mathbf{R}_{I}}|\Psi\rangle-\left\langle\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\right| \hat{H}|\Psi\rangle-\langle\Psi| \hat{H}\left|\frac{\partial \Psi}{\partial \mathbf{R}_{I}}\right\rangle-\frac{\partial E_{I I}}{\partial \mathbf{R}_{I}} .
$$

Using the fact that at the exact ground-state solution the energy is extremal with respect to all possible variations of the wavefunction, it follows that the middle two terms in Eq. (3.18) vanish and the only nonzero terms come from the explicit dependence of the nuclear position. Furthermore, using the form of the energy in Eq. (3.9), it follows that the force depends only on the density $n$ of the electrons and the other nuclei,

> [!theorem] Force (Hellmann-Feynman) theorem (Eq. 3.19)
>
> $$
> \mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}=-\int \mathrm{d}^{3} r n(\mathbf{r}) \frac{\partial V_{\mathrm{ext}}(\mathbf{r})}{\partial \mathbf{R}_{I}}-\frac{\partial E_{I I}}{\partial \mathbf{R}_{I}} .
> $$

Here $n(\mathbf{r})$ is the unperturbed density and the other nuclei are held fixed, as shown schematically in the left-hand side of Fig. I.1. Since each nucleus interacts with the electrons and other nuclei via Coulomb interactions, the right-hand side of Eq. (3.19) can be shown (Exercise 3.3) to equal the nuclear charge times the total electric field, which is the electrostatic theorem of Feynman. Thus even though the kinetic energy and internal interactions change as the nuclei move, all such terms cancel in the force theorem.

---

In the case of nonlocal potentials (such as pseudopotentials), the force cannot be expressed solely in terms of the electron density. However, the original expression is still valid and useful expressions can be directly derived from

$$
-\frac{\partial E}{\partial \mathbf{R}_{I}}=-\langle\Psi| \frac{\partial \hat{H}}{\partial \mathbf{R}_{I}}|\Psi\rangle-\frac{\partial E_{I I}}{\partial \mathbf{R}_{I}}
$$

Because the force theorem depends on the requirement that the electronic states are at their variational minimum, it follows that there must be a continuum of "force theorems" that corresponds to the addition of any linear variation in $\Psi$ or $n$ to the above expression. Although such terms vanish in principle, they can have an enormous impact upon the accuracy and physical interpretation of resulting formulas. The most relevant example in electronic structure is the case of core electrons: It is more physical and more accurate computationally to move the electron density in the core region along with the nucleus rather than holding the density strictly fixed. Methods to accomplish this are described in Appendix I and illustrated in Figure I.1.

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

where the prefactor preserves the normalization. Since the wavefunction also depends on the nuclear positions (either explicitly, treating the nuclei as quantum particles, or implicitly, as parameters in the Born-Oppenheimer approximation discussed after Eq. (3.1)), so also must the nuclear positions be scaled. Of course, the wavefunction and the nuclear positions actually change in other ways if the system is compressed or expanded; however, this has no effect on the energy to first order because the wavefunction and the nuclear positions are at variational minima.

Substituting $\Psi_{\epsilon}\left(\left\{\mathbf{r}_{i}\right\}\right)$ into expression (3.9) for the energy, changing variables in the integrations, and using Eq. (3.21) leads directly to the expression [162]

> [!theorem] Stress tensor (Eq. 3.23)
>
> $$
> \sigma_{\alpha \beta}=-\langle\Psi| \sum_{k} \frac{\hbar^{2}}{2 m_{k}} \nabla_{k \alpha} \nabla_{k \beta}-\frac{1}{2} \sum_{k \neq k^{\prime}} \frac{\left(\mathbf{x}_{k k^{\prime}}\right)_{\alpha}\left(\mathbf{x}_{k k^{\prime}}\right)_{\beta}}{x_{k k^{\prime}}}\left(\frac{\mathrm{d}}{\mathrm{~d} x_{k k^{\prime}}} \hat{V}\right)|\Psi\rangle,
> $$

where the sum over $k$ and $k^{\prime}$ denotes a double sum over all particles, nuclei, and electrons, where the interaction is a function of the distance $x_{k k^{\prime}}=\left|\mathbf{x}_{k k^{\prime}}\right|$. The virial theorem for pressure $P=-\sum_{\alpha} \sigma_{\alpha \alpha}$ is the trace of Eq. (3.23), which follows from isotropic scaling of space, $\epsilon_{\alpha \beta}=\epsilon \delta_{\alpha \beta}$. If all interactions are Coulombic and the potential energy includes all terms due to nuclei and electrons, the virial theorem leads to

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

> [!theorem] Generalized force theorem (Eq. 3.25)
>
> $$
> \frac{\partial E}{\partial \lambda}=\left\langle\Psi_{\lambda}\right| \frac{\partial \hat{H}}{\partial \lambda}\left|\Psi_{\lambda}\right\rangle
> $$

[^3]and
$$
\Delta E=\int_{\lambda_{1}}^{\lambda_{2}} \mathrm{~d} \lambda \frac{\partial E}{\partial \lambda}=\int_{\lambda_{1}}^{\lambda_{2}} \mathrm{~d} \lambda\left\langle\Psi_{\lambda}\right| \frac{\partial \hat{H}}{\partial \lambda}\left|\Psi_{\lambda}\right\rangle
$$

For example, if a parameter such as the charge squared of the electron $e^{2}$ in the interaction energy in the hamiltonian is scaled by $e^{2} \rightarrow e^{2} \lambda$, then $\lambda$ can be varied from 0 to 1 to vary the hamiltonian from the noninteracting limit to the fully interacting problem. Since the hamiltonian involves the charge only in the interaction term, and Eq. (3.5) is linear in $e^{2}$ (the nuclear term is treated separately as the "external potential"), it follows that the change in energy can be written

> [!theorem] Coupling constant integration (Eq. 3.27)
>
> $$
> \Delta E=\int_{0}^{1} \mathrm{~d} \lambda\left\langle\Psi_{\lambda}\right| V_{\mathrm{int}}\left|\Psi_{\lambda}\right\rangle
> $$

where $V_{\text {int }}$ is the full interaction term Eq. (3.5) and $\Psi_{\lambda}$ is the wavefunction for intermediate values of the interaction ${ }^{6}$ given by $e^{2} \rightarrow e^{2} \lambda$. The disadvantage of this approach is that it requires the wavefunction at intermediate (unphysical) values of $e$; nevertheless, it can be very useful, e.g., in the construction of density functionals in Section 9.7.

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
\hat{\rho}=\frac{1}{Z} \mathrm{e}^{-\beta \hat{H}}
$$

with the partition function given by

$$
Z=\mathrm{Tre}^{-\beta \hat{H}}=\mathrm{e}^{-\beta F}
$$

In a basis of eigenstates $\Psi_{i}$ of $\hat{H}, \hat{\rho}$ has only diagonal matrix elements,

$$
\rho_{i i} \equiv\left\langle\Psi_{i}\right| \hat{\rho}\left|\Psi_{i}\right\rangle=\frac{1}{Z} \mathrm{e}^{-\beta E_{i}} ; Z=\sum_{j} \mathrm{e}^{-\beta E_{j}}
$$

[^4]where $\rho_{i i}$ is the probability of state $i$. Since the $\Psi_{i}$ form a complete set, the operator $\hat{\rho}$ in Eq. (3.29) can be written
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

# 3.6 Independent-Electron Approximations

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
> [!equation] Independent-particle energy at finite temperature (Eq. 3.39)
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

What is the meaning of the eigenvalues of the Hartree-Fock equation (3.45)? Of course, Hartree-Fock is only an approximation to the energies for addition and removal of
electrons, since all effects of correlation are omitted. Nevertheless, it is very valuable to have a rigorous understanding of the eigenvalues, which is provided by Koopmans' theorem ${ }^{10}$ [277]:

> [!theorem] Koopmans' theorem (§3.6.3)
>
> The eigenvalue of a filled (empty) orbital is equal to the change in the total energy Eq. (3.44) if an electron is subtracted from (added to) the system, i.e., decreasing (increasing) the size of the determinant by omitting (adding) a row and column involving a particular orbital $\phi_{j}\left(\mathbf{r}_{i}, \sigma_{i}\right)$, keeping all the other orbitals the same.

Koopmans' theorem can be derived by taking matrix elements of Eq. (3.45) with the normalized orbital $\psi_{i}^{\sigma *}(\mathbf{r})$ (see Exercise 3.18). For occupied states, the eigenvalues are lowered by the exchange term, which cancels the spurious repulsive self-interaction in the Hartree term. To find the energies for addition of electrons, one must compute empty orbitals of the Hartree-Fock equation (3.45). For these states there also is no spurious selfinteraction since both the direct and the exchange potential terms in Eq. (3.45) involve only the occupied states. In general, the gaps between addition and removal energies for electrons are greatly overestimated in the Hartree-Fock approximation because of the neglect of relaxation of the orbitals and other effects of correlation.

## 3.6.4 △SCF Methods

In finite systems, such as atoms, it is possible to improve upon the use of the eigenvalues as approximate excitation energies. Significant improvement in the addition and removal energies result from the "delta Hartree-Fock approximation," in which one calculates total energy differences directly from Eq. (3.44), allowing the orbitals to relax and taking into account the exchange of an added electron with all the others. The energy difference approach for finite systems can be used in any self-consistent field method, hence the name " $\triangle \mathrm{SCF}$." Illustrations are given in Section 10.6.

# 3.7 Exchange and Correlation

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

> [!equation] Exchange energy from the exchange hole (Eq. 3.57)
>
> $$
> E_{x}=\left[\left\langle\hat{V}_{\mathrm{int}}\right\rangle-E_{\mathrm{Hartree}}(n)\right]_{\mathrm{HFA}}=\frac{1}{2} \sum_{\sigma \sigma^{\prime}} \int \mathrm{d}^{3} r \int \mathrm{~d}^{3} r^{\prime} \frac{\Delta n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}
> $$

In this form it is clear that the exchange energy cancels the unphysical self-interaction term in the Hartree energy.

The simplest example of an exchange hole is a one-electron problem, such as the hydrogen atom. There is, of course, no real "exchange" nor any issue of the Pauli exclusion principle, and it is easy to see that the "exchange hole" is exactly the electron density. Its integral is unity, as required by the sum rule, and the exchange energy cancels the spurious Hartree term. Because of this cancellation, the Hartree-Fock equation (3.45) correctly reduces to the usual Schrödinger equation for one electron in an external potential.

The next more complex case is a two-electron singlet such as the ground state of He. In this case (see Exercise 3.16) the two spins have identical spatial orbitals and the exchange term is minus one-half the Hartree term in the Hartree-Fock equation (3.44), so that the Hartree-Fock equation (3.45) simplifies to a Hartree-like equation of the form of Eq. (3.36) with $V_{\text {eff }}$ a sum of the external (nuclear) potential plus one-half the Hartree potential. ${ }^{11}$

[^9]For systems with many electrons the exchange hole must be calculated numerically, except for special cases. The most relevant for us is the homogeneous gas considered in the following section.

## 3.7.2 Beyond Hartree-Fock: Correlation

The energy of a state of many electrons in the Hartree-Fock approximation Eq. (3.44) is the best possible wavefunction made from a single determinant (or a sum of a few determinants in multireference Hartree-Fock [274] needed for degenerate cases). Improvement of the wavefunction to include correlation introduces extra degrees of freedom in the wavefunction and therefore always lowers the energy for any state, ground or excited, by a theorem often attributed to MacDonald [279]. The lowering of the energy is termed the "correlation energy" $E_{c}$.

This is not the only possible definition of $E_{c}$, which could also be defined as the difference from some other reference state. The definition in terms of the difference from Hartree-Fock is a well-defined choice in the sense that it leads to the smallest possible magnitude of $E_{c}$, since $E_{\mathrm{HFA}}$ is the lowest possible energy neglecting correlation. Another well-defined choice arises naturally in density functional theory, where $E_{c}$ is also defined as the difference between the exact energy and the energy of an uncorrelated state as Eq. (3.44), but with the difference that the orbitals are required to give the exact density (see Section 3.2 and Chapter 7). In many practical cases this distinction appears not to be of great importance; nevertheless, it is essential to define the energies properly, especially as electronic structure methods become more and more powerful in their ability to calculate effects of correlation.

> [!derivation] Derivation 15: Correlation hole sum rule
> Decompose the full exchange-correlation hole into its exchange and correlation parts (Eq. 3.58). What sum rule does the correlation hole satisfy, and can you prove it from conservation laws alone without computing any wavefunctions beyond Hartree-Fock? Physically, what does this sum rule tell you about what correlation does to the charge distribution around an electron? (Exercise 3.22.)

The effects of correlation can be cast in terms of the remaining part of the pair correlation function beyond exchange $n_{c}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ defined in terms of Eqs. (3.50) and (3.51) by

> [!definition] Exchange-correlation hole (Eq. 3.58)
>
> $
> \Delta n\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) \equiv n_{\mathrm{xc}}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)=n_{x}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)+n_{c}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right) .
> $

Since the entire exchange-correlation hole obeys the sum rule that it integrates to one, the correlation hole $n_{c}\left(\mathbf{r}, \sigma ; \mathbf{r}^{\prime}, \sigma^{\prime}\right)$ must integrate to zero, i.e., it merely redistributes the density of the hole. In general, correlation is most important for electrons of opposite spin, since electrons of the same spin are automatically kept apart by the exclusion principle. For the ground state the correlation energy is always negative and any approximation should be negative. Excited states involve energy differences from the ground state, e.g., an exciton energy. Depending on the effects of correlation in the two states, the difference can be positive or negative.

The correlation energy is more complicated to calculate than the exchange energy because correlation affects both kinetic and potential energies. Both effects can be taken into account by a "coupling constant integration" using the methods of Section 3.4. The theory of interacting systems is beyond the scope of this book and the reader is referred to the companion volume [1] for an in-depth presentation. Nevertheless, it is essential to take correlation into account in realistic calculations, and the goal here is to show how to understand and use aspects that have an important role in present-day electronic structure
theory and practical calculations. Coupling constant integration is discussed for the model system, the homogeneous gas in Chapter 5, and is a key aspect of ongoing developments of functionals for density functional theory (see especially Sections 8.2, 9.3, and 9.7).

**SELECT FURTHER READING**

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

