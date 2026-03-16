## PART V

## FROM ELECTRONIC STRUCTURE TO PROPERTIES OF MATTER

## 19

## Quantum Molecular Dynamics (QMD)

It always seems impossible until it is done.
Nelson Mandela

## Summary

Of all the developments for efficient, quantitative computation of the properties of materials from density functional theory, one stands out: quantum molecular dynamics (QMD) simulations pioneered by Car and Parrinello in 1985 [85]. This work and subsequent developments have led to a revolution in the capabilities of theory to treat real, complex molecules, solids, and liquids including thermal motion (molecular dynamics), with the forces derived from the electrons treated by (quantum) density functional methods. Altogether, four advances created a new approach to electronic structure. These comprise

- optimization methods (instead of variational equations),
- equations of motion (instead of matrix diagonalization),
- fast Fourier transforms (FFTs) (instead of matrix operations), and
- a trace of occupied subspace (instead of eigenvector operations).

Car and Parrinello combined these features into one unified algorithm for electronic states, self-consistency, and nuclear movement. The advances of Car and Parrinello have led to an explosion of alternative approaches that utilize the force theorem, together with efficient iterative methods described in Appendix M. These are referred to as Born-Oppenheimer molecular dynamics and are described in the present chapter as well as the Car-Parrinello method per se.

### 19.1 Molecular Dynamics (MD): Forces from the Electrons

The basic equations for the motion of classical objects are Newton's equations. For a set of nuclei treated as classical masses with an interaction energy $E\left[\left\{\mathbf{R}_{I}\right\}\right]$ dependent on the positions of the particles $\left\{\mathbf{R}_{I}\right\}$, the equations of motion are

$$
M_{I} \ddot{\mathbf{R}}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}=\mathbf{F}_{I}\left[\left\{\mathbf{R}_{J}\right\}\right]
$$

Such equations can be solved analytically only in the small-amplitude harmonic approximation. In general, the solution is done by numerical simulations using discrete time steps based on discrete equations such as the Verlet algorithm, the properties of which are well established (see, e.g., [382, 784]). At each time step $t$ the position of each nucleus is advanced to the next time step $t+\Delta t$ depending on the forces due to the other nuclei at the present time step:

$$
\mathbf{R}_{I}(t+\Delta t)=2 \mathbf{R}_{I}(t)+\mathbf{R}_{I}(t-\Delta t)+\frac{(\Delta t)^{2}}{M_{I}} \mathbf{F}_{I}\left[\left\{\mathbf{R}_{J}(t)\right\}\right]
$$

where the first two terms are just the law of inertia. The key property of the Verlet algorithm, well established in classical simulations, is that the errors do not accumulate. Despite the fact that the equations are only approximate for any finite $\Delta t$, the energy is conserved and the simulations are stable for long runs.

Of course, the forces on the nuclei are determined by the electrons in addition to direct forces between the nuclei. In the past this has been done by effective potentials (such as the Lennard-Jones potential) that incorporate effects of the electrons. These are adequate for many cases like rare gas atoms, but it is clear that one must go beyond such simple pair potentials for real problems of interest in materials. One approach is to use empirical models that attempt to include additional effects and, usually, are parameterized. Advances in electronic structure calculations have made molecular dynamics (MD) simulations possible with forces derived directly from the electrons with no parameters. Such simulations are often termed $a b$ initio or "first principles," but here we shall use the nomenclature "quantum MD (QMD)" simulations. Within the Born-Oppenheimer (adiabatic) approximation ${ }^{1}$ the electrons stay in their instantaneous ground state as the nuclei move. Thus the correct forces on the nuclei are given by the force (Hellmann-Feynman) theorem, Eq. (3.18), which is practical to implement in pseudopotential density functional theory as shown by many examples in previous chapters. We repeat here the basic formulas from Chapter 7 in slightly different notation. Within the Kohn-Sham approach to density functional theory, the total energy of the system of ions and electrons is given by

$$
\begin{gathered}
E\left[\left\{\psi_{i}\right\},\left\{\mathbf{R}_{I}\right\}\right]=2 \sum_{i=1}^{N} \int \psi_{i}^{*}(\mathbf{r})\left(-\frac{1}{2} \nabla^{2}\right) \psi_{i}(\mathbf{r}) \mathrm{d} \mathbf{r}+U[n]+E_{I I}\left[\left\{\mathbf{R}_{I}\right\}\right] \\
U[n]=\int \mathrm{d} \mathbf{r} V_{\mathrm{ext}}(\mathbf{r}) n(\mathbf{r})+\frac{1}{2} \iint \mathrm{~d} \mathbf{r d} \mathbf{r}^{\prime} \frac{n(\mathbf{r}) n\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|}+E_{\mathrm{xc}}[n] \\
n(\mathbf{r})=2 \sum_{i=1}^{N}\left|\psi_{i}(\mathbf{r})\right|^{2} \\
\mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}
\end{gathered}
$$

[^0]where $\psi_{i}$ are the one-electron states, $\mathbf{R}_{I}$ are the positions of the ions, $E_{I I}$ is the ion-ion interaction, $n(\mathbf{r})$ is the electronic charge density, $V_{\text {ext }}(\mathbf{r})$ is the electron-ion interaction, $E_{\mathrm{xc}}[n]$ is the exchange-correlation energy, and $\mathbf{F}_{I}$ is the force given by the force theorem expressed in Eqs. (3.18), (13.3), and other forms.

The key problem, however, is that the calculations must be very efficient. The development of new efficient algorithms by Car and Parrinello [85] and others [385, 785] has led to the explosion of many forms of QMD simulations since 1985. The bottom line is that different approaches can each be used to great advantage; each works well if used with care, and each has particular advantages that can be utilized in individual situations.

Examples of use of the Born-Oppenheimer and Car-Parrinello methods are illustrated in the examples in Sections 2.10, 2.11, and 19.6.

### 19.2 Born-Oppenheimer Molecular Dynamics

It is appropriate to first consider the types of methods that can be called "BornOppenheimer molecular dynamics" because they are the straightforward application of the Born-Oppenheimer approximation that the electrons remain in their ground state as the atoms move. The key point is that the problem is separated into two parts: calculation of accurate forces at each step and moving the atoms. The step of calculating forces is the same as used for relaxation of atomic position to find the minimum energy structures and the step of moving the atoms uses standard methods of molecular dynamics summarized in Eqs. (19.1) and (19.2). Contemporaneous with the Car-Parrinello work, progress using the Born-Oppenheimer was underway using self-consistent density functional theory methods (e.g., [375]) and simpler tight-binding-type methods (e.g., [786]). There has been great progress in creating efficient iterative algorithms described in Appendix M so that there are now various approaches to efficiently calculate the forces.

These methods are now the most widely used for quantum MD (QMD) simulations (often termed $a b$ initio or "first principles"). Since they only require methods to calculate forces and iterative algorithms described elsewhere in this book, what else is there to specify in a calculation?

- The time step, $\Delta t$ in Eq. (19.2), is the parameter that governs the accuracy and efficiency of the molecular dynamics. A balance must be chosen with steps long enough to make the calculation feasible and short enough to be accurate. The choice is governed by the nuclear dynamics, i.e., it is the same as in an ordinary classical MD calculation. This is longer (by about an order of magnitude) than the step in the Car-Parrinello unified algorithm, which is governed by the electronic time scale, so that the atoms move further in one step.
- At each step, the electrons must be solved accurately. Calculation of forces requires conditions for self-consistency to be much more rigorous than for energy, which is at a variational minimum for electrons in the ground state. The requirements are much more stringent than in the Car-Parrinello method. This requires more cycles of self-consistency at each MD step, roughly an order of magnitude more calculations per MD step than in the Car-Parrinello method. Thus, to a first approximation, the two approaches require similar amounts of computation.
- Different iterative methods (Appendix M) can be chosen to find the eigenvalues and eigenvectors of all the occupied states, or only the occupied subspace that spans the eigenvectors. The latter is in general faster; the former has the advantage that the eigenvalues can be used to calculate the Fermi function needed to treat metals.
- Since the computation needed to reach self-consistency is such an important factor in the iterative methods, there can be significant advantages with algorithms designed to give a better starting guess for the potential and wavefunctions at each MD step and faster convergence to self-consistency. However, one must be careful since using information from a previous step may lead to a bias in the forces that leads to a drift in the total energy.


### 19.3 Car-Parrinello Unified Algorithm for Electrons and lons

The essential feature of the Car-Parrinello approach takes advantage of the fact that the total energy of the system of interacting ions and electrons is a function of both the classical variables $\left\{\mathbf{R}_{I}\right\}$ for the ions and the quantum variables $\left\{\psi_{i}\right\}$ for the electrons. Instead of considering the motion of the nuclei and the solution of the equations for the electrons at fixed $\left\{\mathbf{R}_{I}\right\}$ as separate problems (an approach that is inherent in the flowcharts describing the usual approach in Fig. 7.2 and Fig. M.1), the Car-Parrinello approach considers these as one unified problem. Within the Born-Oppenheimer (adiabatic) approximation, the problem becomes one of minimizing the energy of the electrons and solving for the motion of the nuclei simultaneously. This applies to relaxation of the nuclei to find stable structures as well as to thermal simulations of solids and liquids using MD methods. In one stroke, calculation of the ground-state electronic structure and simulation of material phenomena has been unified. ${ }^{2}$

In the Car-Parrinello approach, the total Kohn-Sham energy is the potential energy as a function of the positions of the nuclei. Molecular dynamics for the nuclei using forces from this energy is the defining criterion for all forms of so-called $a b$ initio MD using density functionals. The special feature of the Car-Parrinello algorithm is that it also solves the quantum electronic problem using MD. This is accomplished by adding a fictitious kinetic energy for the electronic states, which leads to a fictitious lagrangian for both nuclei and electrons $[85]^{3}$

$$
\begin{aligned}
\mathcal{L}= & \sum_{i=1}^{N} \frac{1}{2}(2 \mu) \int \mathrm{d} \mathbf{r}\left|\dot{\psi}_{i}(\mathbf{r})\right|^{2}+\sum_{I} \frac{1}{2} M_{I} \dot{\mathbf{R}}_{I}^{2}-E\left[\psi_{i}, \mathbf{R}_{I}\right] \\
& +\sum_{i j} \Lambda_{i j}\left[\int \mathrm{~d} \mathbf{r} \psi_{i}^{*}(\mathbf{r}) \psi_{j}(\mathbf{r})-\delta_{i j}\right] .
\end{aligned}
$$

[^1]The final term in Eq. (19.7) is essential for orthonormality of the electronic states. This lagrangian leads to MD equations for both classical ionic degrees of freedom $\left\{\mathbf{R}_{I}\right\}$ and electronic degrees of freedom, expressed as independent-particle Kohn-Sham orbitals $\psi_{i}(\mathbf{r})$. The resulting equations of motion are

$$
\begin{aligned}
\mu \ddot{\psi}_{i}(\mathbf{r}, t) & =-\frac{\delta E}{\delta \psi_{i}^{*}(\mathbf{r})}+\sum_{k} \Lambda_{i k} \psi_{k}(\mathbf{r}, t) \\
& =-H \psi_{i}(\mathbf{r}, t)+\sum_{k} \Lambda_{i k} \psi_{k}(\mathbf{r}, t) \\
M_{I} \ddot{\mathbf{R}}_{I} & =\mathbf{F}_{I}=-\frac{\partial E}{\partial \mathbf{R}_{I}}
\end{aligned}
$$

The equations of motion, Eq. (18.8) and Eq. (19.9), are just Newtonian equations for acceleration in terms of forces, subject to the constraint of orthogonality in the case of electrons. The masses of the ions are their physical masses, and the "mass" for the electrons is chosen for optimal convergence of the solution to the true adiabatic solution. Thus the equations can be solved by the well-known Verlet algorithm with the constraints handled using standard methods for holonomic constraints [788]. This can be achieved by solving the equations for $\Lambda_{i k}$ at each time step so that $\psi_{i}$ are exactly orthonormal using an iterative method called SHAKE [788, 789]. The resulting discrete equations for time, $t^{n}=n \delta t$, are

$$
\begin{aligned}
\psi_{i}^{n+1}(\mathbf{r}) & =2 \psi_{i}^{n}(\mathbf{r})-\psi_{i}^{n-1}(\mathbf{r})-\frac{(\Delta t)^{2}}{\mu}\left[\hat{H} \psi_{i}^{n}(\mathbf{r})-\sum_{k} \Lambda_{i k} \psi_{k}^{n}(\mathbf{r}, t)\right] \\
\mathbf{R}_{I}^{n+1} & =2 \mathbf{R}_{I}^{n+1}-\mathbf{R}_{I}^{n-1}+\frac{(\Delta t)^{2}}{M_{I}} \mathbf{F}_{I}
\end{aligned}
$$

Note the similarity to those equations for minimization of electronic energy, e.g., Eq. (M.15). The most time-consuming operation (applying the hamiltonian to a trial vector) is exactly the same in all the iterative methods; the only difference is the way in which the wavefunctions are updated as a function of time $t$ or step $n$.

## The Stationary Solution

The meaning of the equations can be clarified by considering a stationary solution of the equations, which we now show is equivalent to the usual Kohn-Sham variational equations. At steady state, all time derivatives vanish and Eq. (19.9) leads to

$$
H \psi_{i}(\mathbf{r}, t)=\sum_{k} \Lambda_{i k} \psi_{k}(\mathbf{r}, t),
$$

which is the usual solution with $\Lambda_{i k}$ the matrix of Lagrange multipliers. Taking the matrix elements, Eq. (19.11) shows that $\Lambda$ is the transpose of $H\left(\Lambda_{i k}=H_{k i}\right)$, where $H$ is the usual Kohn-Sham hamiltonian. Diagonalizing $\Lambda$ leads to the eigenvalues of the Kohn-Sham equations. Furthermore, this is a self-consistent solution since we have minimized the full Kohn-Sham energy, Eq. (19.3). Thus the solution is stationary if, and

![](./images/a98fc207-a32f-4028-93ee-5d194b2c4edd-06_835_786_243_442.jpg)
Figure 19.1. Eigenvalues at $\mathbf{k}=0$ for crystalline Si calculated by quenching the "fictitious kinetic energy" in the lagrangian to reach the steady state [85].

only if, the Kohn-Sham energy is at a variational minimum (or saddle point). In fact, cooling the system down by reducing the kinetic energy is termed dynamical simulated annealing, which is a way to find the minimum of the nonlinear self-consistent Kohn-Sham equations. This is illustrated in the original paper of Car and Parrinello; their results copied here in Fig. 19.1 show the eigenvalues reaching the values that would also be found in a selfconsistent calculation.

It is instructive to apply the Car-Parrinello algorithm to simplified problems. Examples are described in detail in Exercises 19.2 and 19.3 that illustrate the simplest two-state problem; finding the eigenstates of a simple problem by quenching (the analog of the original calculation of Car and Parrinello in Fig. 19.1), and the equations of motion using the fictitious lagrangian.

## Nuclear Dynamics

The real power of the Car-Parrinello method is found in simulations of the coupled motion of nuclei and electrons. This leads to the ability to include the real dynamics of the nuclei in ab initio electronic structure algorithms, treating, e.g., thermal motion, liquids, thermal phase transitions, etc. Also, by quenching, one can search for stable structures. Examples are given later in Section 19.6.

It should be emphasized that the fictitious kinetic energy has nothing to do with the real quantum mechanical energy of the electrons and the electron dynamics that result from this lagrangian are also fictitious; it does not represent the real excitations of the electron
system. The purpose of this fictitious kinetic energy is to allow the ground state of the electrons to move efficiently through the space of basis functions, always staying close to the true ground state. This is in fact realized in many cases but is also problematic in other cases as discussed below.

## Difficulties in the Car-Parrinello Unified Algorithm

There are three primary disadvantages in using the Car-Parrinello approach.
First, any effects of the fictitious lagrangian must be examined and reckoned with if they are problematic. The method works well for systems with an energy gap (for all steps in the simulation). The characteristic frequency of the fictitious oscillations of the electron degrees of freedom are $\propto E_{\text {gap }} / \mu$ (Exercise 19.2) and, if all such frequencies are much greater than typical nuclear vibration frequencies, then the electrons follow the nuclei adiabatically as they should. This is tested by checking the conservation of proper energy (not including the fictitious kinetic energy). Simple examples and discussion are given in [787, 790, 791], and the exercises at the end of this chapter. Even in the best cases, however, one still needs to choose the mass so that the adiabatic condition is satisfied to within acceptable accuracy. There has been controversy on this point [792], but a joint study of Car, Parrinello, and Payne [793] concluded that, with care, problems can be avoided.

Second, the time step $\Delta t$ must be short. It is governed by the fictitious electronic degrees of freedom and must be chosen smaller than in typical simulations for ions alone. A typical "mass" for the electrons is $\mu=400 m_{e}$ (as used for carbon [794]). In general, the value depends on the basis functions, and an issue arises in the plane wave method where Eq. (19.14) below reveals a problem for high Fourier components of the wavefunction. Since the diagonal part of the hamiltonian $H(\mathbf{G}, \mathbf{G}) \propto|\mathbf{G}|^{2}$ for large $|\mathbf{G}|$, a coefficient $c_{i}^{n}(\mathbf{G})$ is multiplied by $\left((\Delta t)^{2} / \mu\right)|\mathbf{G}|^{2}$. This endangers one of the desirable properties of plane waves: that the cutoff can be increased indefinitely to achieve convergence. It has been proposed to integrate the high Fourier components over the time step interval (since they obey a very simple harmonic oscillator equation) instead of taking the linear variation [785]. Another approach is to take different masses for different Fourier components [795, 796].

Finally, it was recognized from the beginning that problems occur with level crossing, where the gap vanishes, and in metals. This leads to unphysical transfer energy to the fictitious degrees of freedom (Exercise 19.2). The problem has been sidestepped by use of "thermostats" that pump energy into the ion system and remove it from the fictitious kinetic energy of the electron system. This has been used, e.g., in calculations of metallic carbon at high pressure [797]. ${ }^{4}$ However, problems with metals simulations have led to the widespread use of alternative approaches such as Born-Oppenheimer molecular dynamics (Section 19.2).

[^2]
### 19.4 Expressions for Plane Waves

The Car-Parrinello equations can be made more transparent by choosing an explicit basis. The equations have exactly the same form for any orthonormal basis and we choose plane waves as the best example. For simplicity of notation we consider Bloch states only at the center of the Brillouin zone, $\mathbf{k}=0$, in which case the Bloch functions can be written

$$
u_{i}(\mathbf{r})=\sum_{\mathbf{G}} c_{i}(\mathbf{G}) \frac{1}{\sqrt{\Omega}} \exp (\mathrm{i} \mathbf{G} \cdot \mathbf{r})
$$

where $\Omega$ is the volume of the unit cell. Since each band holds one electron per cell (of a given spin) the $c_{i}(\mathbf{G})$ are orthonormal

$$
\sum_{\mathbf{G}} c_{i}^{*}(\mathbf{G}) c_{j}(\mathbf{G})=\delta_{i j}
$$

The discrete time step equation corresponding to Eq. (19.10) becomes

$$
c_{i}^{n+1}(\mathbf{G})=2 c_{i}^{n}(\mathbf{G})-c_{i}^{n-1}(\mathbf{G})-\frac{(\Delta t)^{2}}{\mu}\left[\sum_{\mathbf{G}^{\prime}} H\left(\mathbf{G}, \mathbf{G}^{\prime}\right) c_{i}^{n}\left(\mathbf{G}^{\prime}\right)-\sum_{k} \Lambda_{i k} c_{k}^{n}(\mathbf{G})\right],
$$

where $\delta t$ denotes the time step. The equation for $\Lambda_{i k}$ is derived by assuming that $c_{i}^{n}(\mathbf{G})$ and $c_{i}^{n-1}(\mathbf{G})$ are each orthonormal and imposing the condition that $c_{i}^{n+1}(\mathbf{G})$ is also orthonormal. The complete solution is then found by updating the electron density at each iteration, finding the new Kohn-Sham effective potential, and, if desired, moving the atoms according to Eq. (19.2) using the force theorem. The procedure then starts over with a new iteration. Thus all the operations have been combined into one unified algorithm.

The algorithm as presented is still too slow to be useful because of the matrix multiplication in Eq. (19.14), for which the number of operations scales as the square of the number of plane waves $N_{\mathrm{PW}}^{2}$. To circumvent this bottleneck, Car and Parrinello used fast Fourier transforms (FFTs) to reduce the scaling to $N_{\mathrm{PW}} \log N_{\mathrm{PW}}$. The ideas have very general applicability and are described in Sections 12.7 and M.11, where the algorithms are summarized in Figs. 12.4 and M.2. The key steps are the operation $\hat{H} \psi$ and calculation of the density. The kinetic energy operation is a diagonal matrix in Fourier space, whereas multiplication by $V$ is simple in real space where $V$ is diagonal. By the use of the FFT, the operations can be carried out, respectively, in Fourier and real spaces, and the results collected in either space. The limiting factor is the FFT, which scales as $N_{\mathrm{PW}} \log N_{\mathrm{PW}}$. The sequence of steps is described in Fig. M.2.

Finally, at every step the energy and force on each nucleus can be calculated using the force theorem expressed in plane waves, Eq. (13.3). A variant of this form, however, may be more convenient for simulations with large cells. As explained in Section F. 3 and [748], the force on an ion due other ions (the Ewald term) can be combined with the local pseudopotential term, leading to a combined expression in reciprocal space plus correction terms expressed as short-range forces between ions, Eq. (F.17). The last are easily included in a standard MD simulation.

The method can be extended to "ultrasoft" pseudopotentials [603] and to the PAW method [542, 544], which is very useful for simulations with atoms that require high plane wave cutoffs using norm-conserving pseudopotentials, e.g., transition metals. The basic idea is that in any such approach the same general formulation can be used for updating the plane wave coefficients, calculating forces, etc. The difference is that there are additional terms rigidly attached to the nuclei that must be added in the expressions [542, 544, 603].

### 19.5 Non-self-consistent QMD Methods

Much simpler (and faster computationally) simulation methods can be devised if there is no requirement for the full self-consistent Kohn-Sham equations to be solved. The simplest approach uses the empirical tight-binding method (Chapter 14) in which the hamiltonian is given strictly in terms of matrix elements that are simple functions of the positions of the atoms. Since the basis set is also small (several orbitals per atom) it may be more efficient simply to diagonalize the matrices rather than use an iterative method. Then eigenvectors, energies, and forces can be calculated for all positions of the atoms, usually much faster than a typical self-consistent plane wave algorithm. This approach [786] was developed simultaneously with the Car-Parrinello work and still enjoys widespread use because of its speed and simplicity.

Another approach is to solve the electronic problem within a basis using an approximate non-self-consistent form of the hamiltonian. Such methods are $a b$ initio since they are not parameterized and the approximation forms have been used effectively for many problems with a total potential that is a sum of atomic-like potentials [630, 632]. Together with the explicit functional for the energy in terms of the input density, Eq. (7.22), and the usual expressions for the forces, this enables a complete, albeit approximate, DFT QMD algorithm. Self-consistency can be added in limited ways that still preserve efficiency, as done, e.g., in [798].

### 19.6 Examples of Simulations

Because of advances in QMD simulations, it is now possible to determine equilibrium thermodynamic phases and dynamics of the nuclei as a function of temperature and pressure. Three examples in Section 2.10 show the power of the methods to treat important problems.

- One is the challenge to understand the composition and dynamics of the Earth, including the mantle made of minerals and core made of iron with other elements in solid and liquid phases, at pressures and temperatures that vary greatly. First-principles calculations of equations of state and QMD can provide crucial information, and an example is simulations of liquid iron under conditions like those in the core, which are illustrated in Fig. 2.13.
- The other is liquid water and aqueous solutions, which are very difficult problems because of the hydrogen bonding that leads to a plethora of structures and intricate correlations in
the liquid. In this case there are vast numbers of experiments and measured properties; however, there are still many aspects not understood. There is no sense in which we can address the issues in any depth. The brief description in Section 2.10 is meant to convey the enormous progress made to even start attacking such problems, and the fact that density functional methods are just now being developed to the point where it may be possible to make definitive predictions.
- QMD methods provide a general approach to calculations of reaction paths and catalysis. This is far too great a subject to attempt to cover in this book. The example of the ZieglerNatta reaction shown in Fig. 2.16 illustrates the ways that QMD can provide insight into the nature of atomic-scale reactions and clarify proposed mechanisms [201, 202]. However, a word of caution is in order: reaction barriers are particularly sensitive to electronic correlations and functionals for exchange and correlation often are simply not accurate enough for many problems.


## Carbon at High Temperature and Pressure

Carbon is of great interest in many fields of science, with technical, geological, and astrophysical implications, as indicated by the conditions expected inside the Earth and the gaseous planets. Previous to the advent of molecular dynamics based on density functional theory there were wildly divergent proposals for the phase diagram [802]. The graphitediamond boundary is known from thermodynamic arguments [802], but there were many remaining questions. Does the melting temperature of diamond increase with pressure as in most materials or does it decrease as in Si and Ge ? If it increases is there a maximum melting temperature, i.e., a pressure where the slope of the melting curve changes sign? Is liquid C a metal or an insulator? Since the electrons are treated with quantum Kohn-Sham theory as the atoms move, the simulations also yield information on the nature of liquid carbon and can answer such questions.

There are three separate calculations that all agree on the general conclusions and they provide instructive examples of the use of Born-Oppenheimer and Car-Parrinello methods and three different approaches to calculation of the melting temperature. The first QMD calculations for carbon [797, 803] used the LDA approximation and the Car-Parrinello unified algorithm for the simulations of the liquid. The result was a prediction that the melting temperature of diamond increases with pressure (opposite to Si and Ge ), which has been confirmed by experiments [802, 804]. The melting curve was not directly observed in the simulation, but it was inferred from the Claussius-Clapyron equation that relates the slope $\mathrm{d} P_{\text {melt }} / \mathrm{d} T_{\text {melt }}$ to the change in specific volume at the transition. At low $P$ the liquid is less dense than diamond [797, 803] but for $P>\approx 500 \mathrm{GPa}$ [794], the nature of molten carbon changes to a higher coordination ( $>4$ ) dense phase, so that the slope of melting curve must change to be like that known to occur in molten Si and Ge at $P=0$. This method was used to infer a maximum in the melting temperature of $\approx 8000 \mathrm{~K}$ at $\approx 500 \mathrm{GPa}$. At still higher pressure, static total energy calculations [118, 119] have found transitions to dense tetrahedrally coordinated structures (BC8, ST12, etc.) and to

![](./images/a98fc207-a32f-4028-93ee-5d194b2c4edd-11_700_1023_241_321.jpg)
Figure 19.2. Calculated phase diagram of carbon as a function of pressure and temperature omitting the graphite stability region for simplicity. Results indicated by triangles were found using the two-phase method where there is an interface between solid and liquid in the simulation cell [799]. The dashed line was determined by separate calculations of solid and liquid free energies [800]. The light dashed line is the slope of the transition curve calculated independently using the Clausius-Clapeyron equation. Experimental data from [801] is shown as dots with error bars. Adapted from figure provided by A. Correa

the simple cubic metallic phase at $P \approx 30 \mathrm{Mbar}$. This last prediction was confirmed by the QMD simulations, where the phase boundary could be determined directly by melting and solidification as the temperature is raised or lowered [794].

Two more recent calculations determine the melting curve directly in two very different ways. Each uses the PBE approximation for the density functional. The work of Correa et al. [799] uses the Born-Oppenheimer approach and a simulation cell that contains both solid and liquid phases. The procedure is to observe whether the solid or the liquid tends to grow as the simulation proceeds. The results are shown in Fig. 19.2 where the melting of the diamond and BC8 phases is determined. The triangle symbols indicate the change from favoring the solid to favoring the liquid. They pin down the transition in a narrow range, and the simulations can detect the melt line for diamond and BC8 even in regions where they are metastable, as shown by the continuation of the curves beyond the triple point. The solid-solid transition is not observed directly. The transition pressure from diamond to the more dense BC8 phase is known at $T=0$ from total energy calculations, and this work determined the triple point where diamond, $\mathrm{BC8}$, and the liquid converge. The diamond/ BC 8 transition line shown in the figure is an interpolation between the two end points.

The work of Wang et al. [800] used the Car-Parrinello method and determined the melting temperature by computing the free energies of the solid and liquid. Calculation of
the entropy was done by a two-step process following the same method as used previously for Si [805], which involves a two-stage approach with a gradual adiabatic switching of the Kohn-Sham hamiltonian to an intermediate reference system (in this case a model interatomic potential) and then to a system (an Einstein crystal for the solid and an ideal gas for the liquid) with known entropy (see [800] for details). The BC8 phase was not considered. The results shown in Fig. 19.2 are similar to the those found by Correa et al. [799], but the melting temperature is somewhat higher at all pressures considered, and there is a smaller decrease in the melting temperature at high pressure.

After the theoretical work, there have been tour de force experiments [801] in which high pressure and temperature were generated by laser-induced shock waves. In general, as the shock energy increases, the temperature and pressure increases following a Hugoniot equation of state. This is observed for higher temperatures beyond the range in the figure, but there is a region in which an anomalous temperature pressure relation is shown. This indicates a change of phase with a large latent heat and was interpreted as the melting curve. The results are close to the calculations of Wang et al. [800]. Given the difficulty of the calculations (and even more difficulty of the experiments!) the agreement with both calculations is impressive and it shows the value of calculations that can be done for systems in regimes beyond any pervious measurements.

A great advantage of QMD methods is that both electronic and thermal nuclear properties are accessible in the same calculation. One can determine properties like whether liquid carbon is insulating (diamond like) or metallic. The time-averaged electronic density of states does not answer the question. As shown on the left-hand side of Fig. 19.3, the

![](./images/a98fc207-a32f-4028-93ee-5d194b2c4edd-12_613_1230_1300_221.jpg)
Figure 19.3. Electronic properties of liquid carbon at $P \approx 0$ and $T=5,000 \mathrm{~K}$. Left: time-averaged density of states, which is close to the free-electron parabola (dashed line). Right: conductivity $\sigma(\omega)$ calculated for a given ionic configuration using Eq. (E.11) and averaged over configurations. The form of $\sigma(\omega)$ is similar to the Drude form, expected for metal, and the dc conductivity can be estimated from the extrapolation $\omega \rightarrow 0$. From [797].

average density of states is almost free-electron-like. On the other hand, there is very strong scattering of the electrons by the ions, which might lead to localization. Theory can avoid semantics and directly calculate the conductivity $\sigma(\omega)$ given by Eq. (E.11) and the well-known Eq. (21.9) in terms of momentum matrix elements. This yields $\sigma(\omega)$ at any configuration of the nuclei and the final results are found by averaging over configurations in the MD simulation. The result shown in Fig. 19.3 is a conductivity at $T=5,000 \mathrm{~K}$ that has typical Drude form [280, 285] with a very short mean free path of the order of the interatomic spacing. This is borne out by later experiments [801] that observed metalliclike reflectivity of the liquid for temperatures above $10,000 \mathrm{~K}$.

## Structures of Defects, Surfaces, Clusters

An ever-expanding area of research involves nanoclusters, where theory has much to add since information about such structures is difficult to determine experimentally. Examples of Si clusters shown in Fig. 2.20 have all been determined by relaxation or MD. An instructive example is $\mathrm{Si}_{13}$, where there is competition between a symmetric structure with 12 outer atoms surrounding a central atom [224] and a low-symmetry structure found by quenching finite temperature MD simulations [223]. In fact, quantum Monte Carlo calculations [225, 226] confirm that the low-symmetry structure is lower in energy.

As an example involving magnetism, Fig. 19.4 shows predicted structures of $\mathrm{Fe}_{3}$ and $\mathrm{Fe}_{5}$ molecules [357]. This work used ultrasoft pseudopotentials and plane waves, and, most importantly, used noncollinear formalism (Section 8.3) to predict the spin density shown in the figure. Such molecules can be treated with other methods that have also found noncollinear spin density. Furthermore, noncollinear formalism is essential for treating bulk magnetism at finite temperature [355, 356].

![](./images/a98fc207-a32f-4028-93ee-5d194b2c4edd-13_517_614_1431_529.jpg)
Figure 19.4. Equilibrium structures and magnetic moments of small Fe clusters as calculated [357] using plane waves and ultrasoft pseudopotentials. Of particular note are the predicted noncollinear spin states. Such calculations with the noncolinear spin formalism are needed for treating magnetism at finite temperature [355, 356]. From [357].

## SELECT FURTHER READING

Original work:
Car, R. and Parrinello, M., "Unified approach for molecular dynamics and density functional theory," Phys. Rev. Lett. 55:2471-2474, 1985.

Books:
Allen, M. and Tildesley, D., Computer Simulation of Liquids (Oxford University Press, Oxford, U.K., 1989).

Marx, D. and Hutter, J., Ab Initio Molecular Dynamics: Basic Theory and Advanced Methods (Cambridge University Press, Cambridge, U.K., 2009).
Thijssen, J. M. Computational Physics (Cambridge University Press, Cambridge, U.K., 2000).
Reviews and tutorial articles:
Remler, D. K. and Madden, P. A., "Molecular dynamics without effective potentials via the Car-Parrinello approach," Mol. Phys. 70:921, 1990.
Pastore, G. Smargiassi, E., and Buda, F., "Theory of ab initio molecular-dynamics calculations," Phys. Rev. A 44:6334, 1991.
Payne, M. C., Teter, M. P., Allan, D. C., Arias, T. A., and Joannopoulos, J. D., "Iterative minimization techniques for $a b$ initio total-energy calculations: molecular dynamics and conjugate gradients," Rev. Mod. Phys. 64:1045-1097, 1992.
Special issue, "Techiniques for simulations," Comput. Mater. Sci. 12, 1998.

## Exercises

19.1 In the text it was stated that the "SHAKE" algorithm [788, 789] maintains constraints in a holonomic manner, i.e., with no energy loss. An alternative might be the Gram-Schmidt procedure, in which one updates the wavefunctions with $\hat{H} \psi_{i}$ and then orthonormalizes starting with the lowest state.
(a) Show that this will cause energy loss. Hint: one way is to consider the two-state problem in Exercise 19.2. Treat the wavefunctions explicitly and show that there is a difference from the equations given below in which the constraint is imposed analytically.
(b) Read the references for SHAKE [788, 789] and summarize how it works.
19.2 Car-Parrinello-type simulation for one electron in a two-state problem is the simplest case and is considered in the tutorial-type paper by Pastore, Smargiassi, and Buda [791]. In this case, the wavefunction can always be written as a linear combination of any two orthonormal states $\phi_{1}$ and $\phi_{2}$,

$$
\psi=\cos \left(\frac{\theta}{2}\right) \phi_{1}+\sin \left(\frac{\theta}{2}\right) \phi_{2}
$$

With this definition orthogonality and normalization are explicitly included and we can consider $\theta$ to be the variable in the fictitious lagrangian (written for simplicity in the case where $\phi_{1}$ and $\phi_{2}$ are eigenvectors):

$$
L=\mu\left|\frac{\mathrm{d} \theta}{\mathrm{~d} t}\right|^{2}+\epsilon_{1} \cos ^{2}+\epsilon_{2} \sin ^{2}
$$

Solving the Lagrange equations gives

$$
\mu \frac{\mathrm{d}^{2} \theta(t)}{\mathrm{d} t^{2}}=\left(\epsilon_{2}-\epsilon_{1}\right) \sin \left(\theta(t)-\theta_{0}\right),
$$

which is the equation for a pendulum. For small deviations $\theta-\theta_{0}$, the solution is simple harmonic oscillations of frequency $\omega_{e}^{2}=\Delta E / \mu$. Thus so long as the oscillations are small, the electronic degrees of freedom act like simple oscillators.
Pastore et al. [791] have analyzed the two-state model and large cell calculations to identify the key features, as illustrated in the figures from their paper. If $\mu$ is chosen so that the fictitious electronic frequencies are well above all lattice frequencies and motions are small, then there is only slow energy transfer and the Car-Parrinello method works well. This can be done in an insulator. But level crossing, metals, etc. give interesting difficulties.
The exercise is to analyze the algorithm for three cases in which the system is driven by an external perturbation of frequency $\omega_{0}$ :
(a) For the case of small amplitudes and $\mu$ chosen so that $\omega_{e} \gg \omega_{0}$, show that the electrons respond almost instantaneously adiabatically following the driving field.
(b) For the more difficult case with $\omega_{e}$ of order $\omega_{0}$, show that the electrons couple strongly with large nonlinear oscillations. (Note: this fictitious dynamics is not the correct quantum dynamics.)
(c) For the case where there is a level crossing and $\Delta E$ changes sign, show that the electrons can undergo real transitions. (See note in (b).)
19.3 Project for simulation of quantum systems with Car-Parrinello methods. The purpose of this problem set is to write programs and carry out calculations in simple cases for the Car-Parrinello method for simulation of quantum systems by molecular dynamics techniques. Ignore the spin of the electron, which only adds a factor of 2 in paramagnetic cases with even numbers of electrons per cell.
(a) For the case of an "empty lattice" where the potential energy is a constant set equal to zero, write down the Car-Parrinello equations of motion for the electrons. Work in atomic units.
(i) Set up the problem on a one-dimensional lattice, where the wavefunctions are required to be periodic with length $L$. Write a program that iterates the Verlet equation for a single wavefunction expressed in terms of Fourier coefficients up to $M \times(2 \pi / L)$.
(ii) Choose $L=10$ a.u., $\mu=300$ a.u., and $M=16$, which are reasonable numbers for solids.

Start with a wavefunction having random coefficients, velocities zero, and iterate the equations.
Choose a time step and show that the fictitious energy is conserved for your chosen time step. Show that you can carry out the exercise equivalent to the original calculation of Car and Parrinello in Fig. 19.1. Extract energy from the system by rescaling the velocities at each step. Show that the system approaches the correct ground state with energy zero. Make a graph of the energy versus time analogous to Fig. 19.1.
(iii) Now consider several states. Add the orthogonalization constraints, and find the ground state for two, three, and four filled states. Verify that you find the correct lowest states for a line with periodic boundary conditions.
Make a graph of the total energy and fictitious kinetic energy as a function of time. Show the variation in total energy on a fine scale to verify that it is well conserved.
(b) Now add a potential $V(x)=A \sin (2 \pi x / L)$. Use an FFT to transform the wavefunction to real space, multiply by the potential, and the inverse FFT to transform back to Fourier space.
(i) For two electrons per cell (up and down) one has a filled band with a gap to the next band. Find the ground wavefunction and electron density for a value of $A=1$ Hartree, a reasonable number for a solid. (All results can be verified by using the plane wave methods and diagonalization as described in Chapter 12.)
(c) Consider a system with the electrons coupled to slow classical degrees of freedom; let A be coupled to an oscillator, $A=A_{0}+A_{1} x$, and the energy of the oscillator $E=0.5 M \omega_{0}^{2} x^{2}$. Choose values typical for ions and phonon frequencies (Chapter 20).
(i) Choose a fictitious mass $\mu$ so that all the electronic frequencies are much greater than $\omega_{0}$. See Exercise 19.2.
(ii) Start the system at $x=0$, which is not the minimum, and let it evolve. Does the oscillator go through several periods before significant energy is transferred to the electron state? Plot the total energy of the system and the fictitious kinetic energy as a function of time. Show that the total energy is accurately conserved, and the fictitious kinetic energy is much less than the oscillator kinetic energy for several cycles.
(iii) The oscillator should oscillate around the minimum. Check, by calculating the total energy by the quenching method, for fixed $x$, for several values of $x$ near the minimum. Is the minimum in energy found this way close to the minimum found from the oscillations of the dynamic system?


[^0]:    ${ }^{1}$ This is an excellent approximation for many properties such as phonon energies, as discussed in Chapter 3 and Appendix C.

[^1]:    ${ }^{2}$ It is essential to emphasize that the Car-Parrinello algorithm does not treat the real dynamics of electrons, which requires a time-dependent Schrödinger equation, (21.3). The algorithm is designed to find the ground state (adiabatic or Born-Oppenheimer) solution for the electrons as the nuclei move.
    ${ }^{3}$ Note the similarity to the lagrangian in Eq. (M.14), except that here the signature ingredient of the Car-Parrinello method, the "fictitious electronic mass," is added. Such fictitious lagrangians are also used in other quantum field theories [787].

[^2]:    ${ }^{4}$ It is also possible to treat the occupations as dynamical variables in a way related to the ensemble density functional theory method [370], which can potentially allow the Car-Parrinello unified algorithm to apply directly to metals.

