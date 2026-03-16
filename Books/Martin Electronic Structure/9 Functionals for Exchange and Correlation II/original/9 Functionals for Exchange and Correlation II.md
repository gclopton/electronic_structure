## 9

## Functionals for Exchange and Correlation II

## When it rains it pours.


#### Abstract

Summary The previous chapter is devoted to local density and generalized gradient approximations, which are successful in many ways and are still the bread and butter of many applications to materials. However, this is not the end of the story. It is the start of ongoing research to use physical insights and theory to construct improved functionals that can treat other properties, such as van der Waals dispersion interactions. Excitations can be treated within the framework of generalized Kohn-Sham methods in which the exchange-correlation functional depends on the wavefunctions and response functions, including hybrid functionals with nonlocal exchange, "meta" functionals that involve the kinetic energy density, and SIC and DFU +U methods designed to treat localized $d$ and $f$ orbitals with strong interactions. A theme throughout this book is to consider a set of representative functionals and how they perform for different types of materials and properties. At the end of the chapter is a comparison for atoms and a list of pointers to other places in the book that illustrate applications to solids.


### 9.1 Beyond the Local Density and Generalized Gradient Approximations

There is much activity and a great variety of approaches to develop new functionals that go beyond the local density and generalized gradient approximations. The efforts are fueled by the fact that there is an ever-increasing payoff for development of functionals that are more accurate for important classes of materials and make possible application to new systems. Because there is no one approach to development of functionals, this has led to a plethora of methods with increasingly lengthy acronyms as more features are incorporated, as described in reviews such as [415, 426, 427]. Many of the functionals have been created by fitting to large databases of molecules and these are widely used, especially in chemistry. It is not feasible to cover all the developments; here the focus is on a representative set of functionals that are based on theoretical considerations or using information from model systems.

## Ladder of functionals with increasing complexity and capability

## Functionals of occupied/unoccupied states <br> Random phase approx., ...Section 9.7

## Functionals of occupied states Hybrids, SIC, DFT+U, ...Sections 9.2-9.6

| Meta GGA - Section 9.4 |
| :---: |
| $\epsilon_{x c}(n(\mathbf{r}),\|\nabla n(\mathbf{r})\|, \tau(\mathbf{r}))$ |


| Gen. gradient approx. (GGA) - Section 8.5 |
| :---: |
| $\epsilon_{x c}(n(\mathbf{r}),\|\nabla n(\mathbf{r})\|)$ |

Local approximation (LDA) - Section 8.3

$$
\epsilon_{x c}(n(\mathbf{r}))
$$

Figure 9.1. From bottom to top: classes of functionals with increasing complexity, with the goal of increased capability and accuracy that offset the increased computational requirements. They are arranged as rungs on a ladder that has been termed a "Jacob's ladder" after the biblical story of a ladder reaching to heaven, i.e., extending toward the exact formulation. The van der Waals functionals in Section 9.8 can be placed at various levels. They are derived using many of the features in the more advanced functionals, but they have been formulated as functionals only of the density.

The progression of functionals has been organized on the "density functional ladder" or "Jacob's ladder" [428] that categorizes the classes of functionals described in this chapter, as illustrated in Fig. 9.1. This helps to avoid being overwhelmed by the hundreds of choices by developing a logical, instructive path with typical functionals for each rung of the ladder. The higher rungs can be cast in terms of "generalized Kohn-Sham theory" that provides new avenues for approaches to the problems. Development of functionals is an ongoing field of research and it is not appropriate to try to describe any method in detail. The aim is to bring out the central features in a way that will still be useful as new ideas emerge in the future.

### 9.2 Generalized Kohn-Sham and Bandgaps

The great advance of the Kohn-Sham approach over Thomas-Fermi-type methods is that the kinetic energy Eq. (7.3) is explicitly expressed as a functional of the independentparticle orbitals $\psi_{i}$. It is implicitly a functional of the density, since the orbitals are determined by the potential $V_{\mathrm{KS}}^{\sigma}(\mathbf{r})$, which in turn is a functional of the density $n^{\sigma}(\mathbf{r})$; however,
the functional dependence on $n$ must be highly nontrivial, nonanalytic, and nonlocal. In particular, derivatives of the Kohn-Sham kinetic energy $\mathrm{d} T_{S} / \mathrm{d} n$ are discontinuous functions of $n$ at densities corresponding to filled shells. This is the way in which shell structure occurs in the Kohn-Sham approach, whereas it is missing in Thomas-Fermi-type approximations. An intrinsic part of the Kohn-Sham construction in Section 7.1 is that $V_{\mathrm{KS}}^{\sigma}(\mathbf{r})$ is a local potential that is a function only of the position and spin; otherwise there cannot be a one-to-one relation of the potential and the density $n^{\sigma}(\mathbf{r})$.

There is another approach called "generalized Kohn-Sham theory" (GKS) in which the potential can be a nonlocal operator. The action of an operator can be expressed in a basis so that it acts differently on different wavefunctions, i.e., it is "orbital dependent." An example is the Hartree-Fock equations in Eqs. (3.45)-(3.47), where the action of the exchange term operator $\hat{V}_{x}$ on a wavefunction at point $\mathbf{r}$ depends on an integral over that same wavefunction over all space. The idea of a nonlocal Hartree-Fock-like exchange term is already in the original Kohn-Sham paper, but it was only later that Seidl and coworkers [400] proposed that a family of possible auxiliary systems could be defined with the only requirement that the wavefunction be a single determinant of single-body orbitals $\psi_{i}(\mathbf{r})$. The Kohn-Sham system of noninteracting particles is one choice; another is the Hartree-Fock functional of the orbitals $\psi_{i}$ that incudes interactions in an average sense; and there are many possible choices of systems that include interactions in some way. Thus there are whole ranges of auxiliary systems that in principle lead to the exact density and ground-state energy. To the knowledge of the author there are no formal proofs that the generalized theory is exact for other properties; however, it provides a framework for addressing other properties.

Why would one want to construct a theory that appears to be more difficult? The most direct answer is that it provides a greater range of possibilities. It is potentially more accurate since it can incorporate various physical properties in a form that goes beyond Kohn-Sham and yet is feasible to calculate. The deeper reason is that in the Kohn-Sham approach the $E_{\mathrm{xc}}$ functional has to take into account all the effects of exchange and correlation. If some of the effects can be taken into account by a different auxiliary system, then it may be helpful in constructing the functional. It turns out that for many problems, the added difficulty in solving the equations is worthwhile because the functionals are more accurate and take into account features that are very difficult to build into a functional of only the density.

In many ways GKS is a natural progression: the improvement of Kohn-Sham over Thomas-Fermi was to introduce an orbital-dependent kinetic energy, and the next step is to improve exchange-correlation functionals by expressing $E_{\mathrm{xc}}$ explicitly in terms of the independent-particle orbitals $\psi_{i}$. For example, the true $E_{\mathrm{xc}}$ functional must have discontinuities at filled shells [387, 388, 429], which is essential for a correct description of energy gaps. The "bandgap problem" results from the use of the eigenvalues, even though it is fundamentally unjustified. The generalized theory provides the framework to properly consider the eigenvalues as meaningful, even if they are approximate. There are solid theoretical arguments that a generalized theory can take into account physical effects which are missing in the original Kohn-Sham approach and which can include at least part of the discontinuity using practical functionals [400]. The many-author paper by Perdew et al.
[430] provides an instructive overview of gaps in a generalized theory and the foundations of GKS are discussed in [427, 431].

There are two primary types of functionals of the wavefunction placed on the third and fourth rungs of the ladder in Fig. 9.1. Hybrid functionals on the fourth rung are discussed first because they involve concepts that are well established - a combination of HartreeFock and DFT - and are very important in a large fraction of present-day calculations. Calculations using hybrids can match (or improve) the success of LDA and GGAs for ground state properties and also lead to better estimates for the bands, bandgaps, and excitations. Meta-GGA denotes functionals of the kinetic energy density as well as the density. They are on the third rung of the ladder because they involve only a single added function calculated from information already present in a Kohn-Sham DFT calculation. However, meta-GGAs have not been used as much and are not as well tested as hybrids, and they are presented later in Section 9.4.

### 9.3 Hybrid Functionals and Range Separation

Hybrid functionals are a combination of explicit density-dependent and orbital-dependent Hartree-Fock (or Hartree-Fock-like) functionals. ${ }^{1}$ These are often the method of choice in the chemistry community (see, e.g., [413, 415, 426]) because they lead to marked improvements over semilocal functionals and they were readily incorporated in existing codes since Hartree-Fock and DFT are each well-developed methods for molecules. For solids, Hartree-Fock calculations are more difficult, and the use of hybrids was very limited until efficient methods were developed. More important, the Hartree-Fock approximation is problematic for extended solids where it has disastrous consequences for metals, as discussed in Chapter 5. On the other hand, in insulators it leads to quantitative improvements in many cases and the long-range interaction is essential for excitons (see Chapter 21). One approach is range separation in which a Hartree-Fock-like exchange is included in different ways for the short- and long-range parts of the Coulomb interaction. Here the goal is to bring out the basic ideas and give representative examples; more details and in-depth analysis can be found in review articles such as [415, 426, 427] and sources listed at the ends of this chapter and Chapter 8.

The most striking improvements made possible by hybrid functionals are bandgaps and excitation energies. If the eigenvalues are treated as energies for adding or removing electrons, standard density-dependent functionals like LDA and GGA tend to greatly underestimate gaps whereas Hartree-Fock tends to give gaps that are much too large. An example is the bands of Ge shown in Fig. 2.23 where the LDA leads to a metal and HartreeFock to an insulator with a gap much too large, whereas the hybrid is in much better agreement with experiment. Figure 2.24 shows the improvement for a range of materials.

[^0]There are several approaches to assign the fraction $\alpha$ of the Hartree-Fock and $1-\alpha$ of the Kohn-Sham components of the hybrid, which broadly can be classified as fitting to experimental data versus theoretical considerations. One approach to justify the choice is to use the coupling constant integration formulation in Eq. (8.3), along with information at the end points and the dependence as a function of the coupling constant $\lambda$. In particular, at $\lambda=0$ the energy of the uncorrelated wavefunction is the Hartree-Fock exchange energy, which is easily expressed in terms of the exchange hole that can be calculated from the orbitals (the fourth term in Eq. (3.44)). Becke [432] argued that the potential part of the LDA or GGA functional is most appropriate at full coupling $\lambda=1$ and suggested that the integral Eq. (8.3) can be approximated by assuming a linear dependence on $\lambda$, which leads to the "half-and-half" form that is the average of the density and Hartree-Fock functionals. A closer look at the variation as a function of $\lambda$ led Perdew, Ernzerhof, and Burke [433] to conclude it is nonlinear and they proposed the form

$$
E_{\mathrm{xc}}^{\mathrm{PBE} 0}=E_{\mathrm{xc}}^{\mathrm{PBE}}+\frac{1}{4}\left(E_{x}^{\mathrm{HF}}-E_{\mathrm{x}}^{\mathrm{PBE}}\right),
$$

with $\alpha=1 / 4$ mixing of Hartree-Fock exchange and with correlation energy given by the density functional unchanged. Their reasoning applies to any functional and the "1/4" hybrid with the PBE exchange-correlation functional, called PBE0 [412], is widely used.

There are many parameterized forms for hybrid functionals (see, e.g., [415]). An example is "B3LYP", which uses the Becke B88 exchange functional [410] and the LYP correlation [416],

$$
E_{\mathrm{xc}}=E_{\mathrm{xc}}^{\mathrm{LDA}}+a_{0}\left(E_{x}^{\mathrm{HF}}-E_{x}^{\mathrm{LDA}}\right)+a_{x}\left(E_{x}^{\mathrm{B} 88}-E_{x}^{\mathrm{LDA}}\right)+a_{c}\left(E_{c}^{\mathrm{LYP}}-E_{c}^{\mathrm{LDA}}\right),
$$

with coefficients $a_{0}=0.2, a_{x}=0.72, a_{c}=0.81$. These were empirically adjusted to fit atomic and molecular data, but it turns out that the values are close to $a_{x}=1-a_{0}, a_{c}=1.0$ in which case Eq. (9.2) reduces to the much simpler form in Eq. (9.1) with $a_{0}$ that is in a range around $1 / 4$ depending on which GGA functional is used.

## Variation of the Long-Range Exchange Hybrid Functionals

There are several motivations to go beyond the form of hybrids that use a fixed fraction of Hartree-Fock exchange. (See also related arguments for range separation.) As it stands, any functional with nonzero $\alpha$ cannot be used for a metal. The long-range part of the exchange must be eliminated completely since it gives unphysical results at the Fermi surface, as described in Section 5.2. In addition, it has been observed that larger values of $\alpha$ lead to improved gaps for materials with large gaps and smaller values of $\alpha$ for ones with small gaps. Furthermore, it seems physically reasonable that there should be larger effects of the exchange in wider gap materials. There have been a number of proposals to make $\alpha$ inversely proportional to the dielectric constant. Thus it vanishes for a metal and is small in materials like Si where $\epsilon_{0}=12$ but is large in materials like LiF where $\epsilon_{0}=1.9$, with results that are described in Chapter 21. In [434] can be found physical reasoning
supported by many-body perturbation theory based on works over the decades on screening the long-range fields in solids. A PBE0-like form with $\alpha=1 / \epsilon$ was proposed as a nonempirical "dielectric-dependent hybrid" (DDH) functional in which $\epsilon$ is calculated selfconsistently was proposed in [244], which provided extensive tests. The DDH functional is used in calculations for water as shown in Fig. 2.15 and bandgaps in Fig. 2.24.

## Range-Separated Hybrid Functionals

Range separation denotes schemes in which the exchange energy is separated into contributions due to short- and long-range parts of the Coulomb interaction. Instead of scaling the Hartree-Fock exchange by the dielectric constant, a different approach is based on the idea that screening is dependent on the distance with little screening at short distance and reaching the macroscopic value at large distance. This idea is used in various functionals [415], and we consider the HSE [435-437] and related approaches that are most used in condensed matter applications. A convenient division into short- and long-range parts, adopted in the HSE functional and other works, is the same as used in the Ewald transformation in Section F.2,

$$
\frac{1}{r}=\frac{1-\operatorname{erf}(\eta r)}{r}+\frac{\operatorname{erf}(\eta r)}{r}
$$

where erf is the error function and $\eta$ (called $\omega$ in [435]) is the range parameter. The various ways to choose a functional are generalizations of expressions like Eq. (9.1) to apply separately to the short- and long-range parts,

$$
E_{\mathrm{xc}}=E_{\mathrm{xc}}^{\mathrm{DFT}}+a\left(E_{x}^{\mathrm{HF}, \mathrm{SR}}-E_{\mathrm{x}}^{\mathrm{DFT}, \mathrm{SR}}\right)+b\left(E_{x}^{\mathrm{HF}, \mathrm{LR}}-E_{\mathrm{x}}^{\mathrm{DFT}, \mathrm{LR}}\right)
$$

where DFT stands for any of the local or semilocal density functionals such as PBE.

## Short-Range-Only Functionals

For solids a widely used choice is the HSE functional [437] in which the long-range Hartree-Fock is completely eliminated ( $b=0$ in Eq. (9.4)),

$$
E_{\mathrm{xc}}=E_{\mathrm{xc}}^{\mathrm{PBE}}+\frac{1}{4}\left(E_{x}^{\mathrm{HF}, \mathrm{SR}}-E_{\mathrm{x}}^{\mathrm{PBE}, \mathrm{SR}}\right)
$$

where $a$ is chosen to be $1 / 4$ the same as Eq. (9.1). This form has the great advantage that it can be applied to metals, and it reduces to the PBE GGA for $\eta \rightarrow \infty$ and the PBE0 hybrid for $\eta \rightarrow 0$.

The range-separation length $\eta$ is a parameter chosen to be $0.11 / a_{0}$ in HSE06 in order to provide the best description of a range of materials and properties. HSE06 is one of the characteristic functionals selected in this book, with results shown for many examples: lattice constants and bulk moduli in Table 2.1; phase transition pressures in Fig. 2.4; bandgaps in Fig. 2.24 and various examples; atoms in Table 9.1; and optical spectra in Chapter 21. The choice $\eta=0.11 / a_{0}$ works well for semiconductors and many other cases,
but it is found to be less accurate for wider bandgap insulators. Indeed on physics grounds one expects that effects are more localized in wide-gap materials, i.e., larger $\eta$ in Eq. (9.3).

## Range Separation with Screened Long-Range Exchange

There are fundamental reasons to include some degree of the long-range part of the exchange in insulators, in addition to the fact that hybrid functionals are very successful for quantitative calculations in molecules and insulating solids. Optical spectra calculated using time-dependent perturbation theory are very successful and widely used for molecules. Even though short-range forms like HSE seem to work well for materials like semiconductors, they can never describe excitons in a solid! It is only if there is some fraction of long-range exchange that the functionals can produce a bound state below the gap, as illustrated in Fig. 21.5 for LiF.

## Nonempirical Hybrid Functionals

At this point we have range-separated functionals with two types of parameters that characterize the range and the magnitude of the long-range exchange respectively. There are good physical arguments for the variation of each one for different materials. Does this mean choosing a different functional for each material? If the functional is fitted for each material, this would be an enormous step backward from the goal of a universal functional for all systems. It would go against the history of density functional theory, where approximate functionals have been developed and their quality judged by the degree to which a single function could apply to many materials.

One approach to take advantage of the positive features of the range-separated functionals is to develop the theory in such a way that the parameters $\eta$ and $\alpha$ are predicted by the theory itself, i.e., an internally consistent approach with no empirical input. An example is the dielectric-dependent hybrid (DDH) functional [244]) with long-range exchange reduced by the dielectric function $\epsilon$, which is calculated self-consistently. A related approach involving the dielectric function with no free parameters is in [438]. Such functionals can be viewed as adding a very nonlocal functional of the density - a single parameter $\alpha$ that depends on a global property of the system. (Note, however, that there are issues for systems with different dielectric functions in different regions, e.g., an interface between different materials, a surface or a molecule in vacuum.) Another example is the van der Waals functional in [439] (see Section 9.8), which uses well-known formulas in terms of polarizabilities that are finally expressed in terms of the density determined in the calculation.

In this context the term "tuned" has been introduced as a general approach [440] to finding such functionals who gave a specific approach to finding $\eta$ using the ionization potential and the fact that in an exact Kohn-Sham theory it is equal to the highest occupied eigenvalue. This has the benefit of dealing with the perplexing problems of charge transfer
between weakly coupled systems that depend on the relative eigenvalues. However, there is a difficulty in a solid where the ionization potential is not a well-defined intrinsic property.

### 9.4 Functionals of the Kinetic Energy Density: Meta-GGAs

The third rung of the DFT ladder in Fig. 9.1 is functionals of the kinetic energy density $t(\mathbf{r})=n(\mathbf{r}) \tau(\mathbf{r})$ of noninteracting particles as well as the particle density,

$$
E_{\mathrm{xc}}^{\mathrm{GGA} \tau}=\int \mathrm{d}^{3} r n(\mathbf{r}) \epsilon_{\mathrm{xc}}\left(n^{\uparrow}, n^{\downarrow},\left|\nabla n^{\uparrow}\right|,\left|\nabla n^{\downarrow}\right|, \tau^{\uparrow}, \tau^{\downarrow}\right),
$$

where each term is evaluated at position $\mathbf{r}$. The kinetic energy density $t(\mathbf{r})$ is defined in Section H.1, and the problem is that it is not unique. Two possibilities are given in Eq. (H.8), which can be written

$$
t^{\sigma(1)}(\mathbf{r})=-\frac{1}{2} \sum_{i=1}^{N} \psi_{i}^{\sigma *}(\mathbf{r}) \nabla^{2} \psi_{i}^{\sigma}(\mathbf{r}) \quad \text { or } \quad t^{\sigma(2)}(\mathbf{r})=\frac{1}{2} \sum_{i=1}^{N}\left|\nabla \psi_{i}^{\sigma}(\mathbf{r})\right|^{2},
$$

where $\operatorname{spin} \sigma$ is indicated explicitly for clarity. It might seem that there is a fundamental problem in using $\tau^{\sigma}(\mathbf{r})$ to construct a functional since there is not a unique expression. However, in Section H. 1 it is shown that it can be considered to be a sum of two terms $t^{\sigma}(\mathbf{r})=t_{n}^{\sigma}(\mathbf{r})+t_{x}^{\sigma}(\mathbf{r})$ (see Eq. (H.9)) where $t_{x}^{\sigma}(\mathbf{r})=n^{\sigma}(\mathbf{r}) \tau_{x}^{\sigma}(\mathbf{r})$ is a well-defined, unique positive-definite function, and all the nonuniqueness is in the term $t_{n}^{\sigma}(\mathbf{r})$ that depends solely on the density $n^{\sigma}(\mathbf{r})$ and its derivatives at point $\mathbf{r}$. Either form for $t(\mathbf{r})$ in Eq. (9.7) can be used to define the unique function $\tau_{x}^{\sigma}(\mathbf{r})$; here we give explicit expressions using the second form (see [415] for works that use the other choice),

$$
\tau_{x}^{\sigma}(\mathbf{r})=\frac{1}{2 n^{\sigma}(\mathbf{r})} \sum_{i=1}^{N}\left|\nabla \psi_{i}^{\sigma}(\mathbf{r})\right|^{2}-\frac{1}{8}\left[\frac{\nabla n^{\sigma}(\mathbf{r})}{n^{\sigma}(\mathbf{r})}\right]^{2} \equiv \tau^{\sigma}(\mathbf{r})-\tau_{W}^{\sigma}(\mathbf{r}),
$$

where we have dropped the superscript (2) to define $\tau^{\sigma}(\mathbf{r})$ and $\tau_{W}^{\sigma}(\mathbf{r})$ is the Weizsacker expression [330] for the kinetic energy (see also Eq. (H.15)), which has been used in many contexts as a correction to the Thomas-Fermi approximation.

There are good reasons [441] to expect $\tau_{x}^{\sigma}(\mathbf{r})$ to be an appropriate variable with which to express the functional. As summarized in Section H.1, $\tau_{x}^{\sigma}(\mathbf{r})$ has a clear physical meaning, the curvature of the exchange hole, which can be shown to be the relative kinetic energy of pairs of electrons. In fact, the properties of the exchange hole including its curvature have been used in creating the GGA functionals [410-412, 442] in Section 8.5, based on the physical reasoning that the large gradient regime is cut off by the extent of the exchange hole. In addition, $\tau_{x}^{\sigma}(\mathbf{r})$ is the basis for the electron localization function (ELF) defined in Eq. (H.21) which is used to analyze the electronic structure.

We have not completely escaped from the problem of nonuniqueness since there are still two possibilities for the part of the kinetic energy denoted $\tau_{n}^{\sigma}(\mathbf{r})$, the Weizsacker form or one in terms of second derivatives as shown in Eq. (H.14). However, the key point is that either expression for $\tau_{n}^{\sigma}(\mathbf{r})$ involves only the density $n^{\sigma}(\mathbf{r})$ and its derivatives. This is the
reason that functionals of the kinetic energy should also involve gradients of the the density (hence the appellation "meta-GGA") and the reason that the combined functional can be physically meaningful.

A meta-GGA functional is an example of an orbital-dependent functional that leads to a generalized Kohn-Sham method like other orbital-dependent functionals (see Section 9.2). However, it depends explicitly only on local variables and it leads to a differential operator in the Kohn-Sham equations in contrast to Hartree-Fock where the exchange is a nonlocal integral operator (see Eq. (3.45)). The Kohn-Sham equations can be derived by variation of the functional with respect the wavefunctions, which leads an operator with the form [243]

$$
\hat{V}_{\mathrm{xc}, \sigma}^{\tau}(\mathbf{r}) \psi_{i}^{\sigma}(\mathbf{r})=\frac{1}{2} \nabla \cdot\left[\frac{\delta E_{\mathrm{xc}}}{\delta \tau^{\sigma}}(\mathbf{r}) \nabla \psi_{i}^{\sigma}(\mathbf{r})\right] .
$$

This term alters the form of the Kohn-Sham equations, but it can be included in ways similar to Eq. (8.19) since it is a derivative operator. One can generate a local optimized effective potential as in Section 9.5, but the resulting equations are more difficult than using the operator in Eq. (9.9).

## The SCAN Meta-GGA Functional

Functionals involving the kinetic energy density have been derived in the 1980s, such as [442], and there are more recent developments that were stimulated by the approach in [443]. Here we describe the functional [444] denoted by the acronym SCAN, which stands for "strongly constrained and appropriately normed" where "constrained" means that it is required to obey certain conditions (including ones previously applied to GGAs) and "appropriate norms" are systems that are argued to be appropriate to use in constructing the functional (for example, the homogeneous gas is used to define the LDA). The SCAN functional is constructed in terms of the dimensionless variable $\alpha(\mathbf{r})=\tau_{x}^{\sigma}(\mathbf{r}) / \tau^{u n i f}(n(\mathbf{r}))$, where $\tau^{\text {unif }}(n(\mathbf{r}))$ is the kinetic energy density of the electron gas with density $n(\mathbf{r})$. The form of exchange energy as a function of the density, gradients and $\alpha$ was determined by the requirement that it satisfies 17 different constraints and it fits as well as possible information from several systems (see the supplementary material for [444]): (a) uniform and slowly varying densities, (b) jellium surface energy, (c) H atom, (d) the He atom and the limit of large atomic number for the rare-gas atoms, plus compressed $\mathrm{Ar}_{2}$, and (e) the $Z \rightarrow \infty$ limit of the two-electron ion. This list may seem arbitrary, but the first two are the same as used for LDA and GGA functionals, the H atom is a one-electron systems already used in a previous kinetic energy functional [443], and the others add new information on inhomogeneous systems with strong gradients in different geometries. Since there is no information about bonded systems in the construction of the functional, the application to molecules and crystals is a test of the predictive power of the functional. This is in contrast to functionals that are fitted to data sets of molecules, which are expected to perform very well for similar systems but may not be as good when applied to different systems.

The SCAN functional has been tested in a number of applications including bandgaps of solids in Fig. 2.24, lattice constants in Table 2.1, phase transitions under pressure in Fig. 2.4,
simulations of water in Fig. 2.15, and atoms in Table 9.1. These are a sample of much more extensive tests for atoms and molecules in the original paper [444], equilibrium structures [112], phase transitions under pressure [128], simulations of water [195] and applications in combination with a van der Waals functional [445].

### 9.5 Optimized Effective Potential

The generalized Kohn-Sham theory in Section 9.2 leads to a nonlocal potential. Is there a way to formulate the original Kohn-Sham theory not with a local potential but with an orbital-dependent functional $E_{\mathrm{xc}}\left[\left\{\psi_{i}\right\}\right.$ ? In fact there is a long history of such methods that predates the work of Kohn and Sham, apparently first formulated in a short paper [446] by Sharp and Horton in 1953 as the problem of finding "that potential, the same for all electrons, such that when ... given a small variation, the energy of the system remains stationary." This approach has come to be known as the optimized effective potential (OEP) method [447-449]. The key point is that if one considers orbitals $\psi_{i}$ that are determined by a potential through the usual independent-particle Schrödinger equation, then it is straightforward, in principle, to define the energy functional of the potential $V$,

$$
E_{\mathrm{OEP}}[V]=E\left[\left\{\psi_{i}[V]\right\}\right] .
$$

The OEP method is fully within the Kohn-Sham approach since it is just the optimization of the potential $V$ that appears in the very first Kohn-Sham equation (7.1). Furthermore, as emphasized in Section 7.3, the usual Kohn-Sham expressions are operationally functionals of the potential; the OEP is merely an orbital formulation of the general idea. The OEP method has been applied primarily to the Hartree-Fock exchange functional, which is straightforward to write in terms of the orbitals (the fourth term in Eq. (3.44)), which is called "exact exchange" or "EXX." However, the OEP approach is more general and applicable to orbital-dependent kinetic energy and correlation functionals as well.

The variational equation representing the minimization of energy Eq. (9.10) can be written using the density formalism as an intermediate step. Since the potential $V$ acts equally on all orbitals, it follows that

$$
V_{\mathrm{xc}}^{\sigma, \mathrm{OEP}^{-}}(\mathbf{r})=\frac{\delta E_{\mathrm{xc}}^{\mathrm{OEP}}}{\delta n^{\sigma}(\mathbf{r})},
$$

which can be written (see Exercise 9.2) using the chain rule [251,449] as

$$
\begin{aligned}
V_{\mathrm{xc}}^{\sigma, \mathrm{OEP}}(\mathbf{r}) & =\sum_{\sigma^{\prime}} \sum_{i=1}^{N^{\sigma^{\prime}}} \int \mathrm{d} \mathbf{r}^{\prime} \frac{\delta E_{\mathrm{xc}}^{\mathrm{OEP}}}{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)} \frac{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)}{\delta n^{\sigma}(\mathbf{r})}+\text { c.c. } \\
& =\sum_{\sigma^{\prime}} \sum_{i=1}^{N^{\sigma^{\prime}}} \int \mathrm{d} \mathbf{r}^{\prime} \int \mathrm{d} \mathbf{r}^{\prime \prime}\left[\frac{\delta E_{\mathrm{xc}}^{\mathrm{OEP}}}{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)} \frac{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)}{\delta V^{\sigma^{\prime}}, K S\left(\mathbf{r}^{\prime \prime}\right)}+\text { c.c. }\right] \frac{\delta V^{\sigma^{\prime}}, K S\left(\mathbf{r}^{\prime \prime}\right)}{\delta n^{\sigma}(\mathbf{r})}
\end{aligned}
$$

where $V^{\sigma^{\prime}}$, KS is the total potential in the independent-particle Kohn-Sham equations that determine the $\psi_{i}^{\sigma^{\prime}}$. Each term has a clear meaning and can be evaluated from well-known expressions:

- The first term is an orbital-dependent nonlocal (NL) operator that can be written

$$
\frac{\delta E_{\mathrm{xc}}^{\mathrm{OEP}}}{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)} \equiv V_{i, \mathrm{xc}}^{\sigma^{\prime}, \mathrm{NL}}\left(\mathbf{r}^{\prime}\right) \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)
$$

For example, in the exchange-only approximation, $V_{i, \mathrm{xc}}^{\sigma^{\prime}, \mathrm{NL}}\left(\mathbf{r}^{\prime}\right)$ is the orbital-dependent Hartree-Fock exchange operator Eq. (3.48).

- The second term can be evaluated by perturbation theory, ${ }^{2}$

$$
\frac{\delta \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}\right)}{\delta V^{\sigma^{\prime}, \mathrm{KS}}\left(\mathbf{r}^{\prime \prime}\right)}=G_{i, 0}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime}, \mathbf{r}^{\prime \prime}\right) \psi_{i}^{\sigma^{\prime}}\left(\mathbf{r}^{\prime \prime}\right),
$$

where the Green's function for the noninteracting Kohn-Sham system is given by (see Eq. (D.6), which is written here with spin explicitly indicated)

$$
G_{i, 0}^{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\sum_{j \neq i}^{\infty} \frac{\psi_{j}^{\sigma}(\mathbf{r}) \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right)}{\varepsilon_{\sigma i}-\varepsilon_{\sigma j}}
$$

- The last term is the inverse of a response function $\chi_{0}$ given by

$$
\chi_{0}^{\sigma, \mathrm{KS}}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\frac{\delta n^{\sigma}(\mathbf{r})}{\delta V^{\sigma^{\prime}, \mathrm{KS}^{\prime}\left(\mathbf{r}^{\prime \prime}\right)}}=\sum_{i=1}^{N^{\sigma}} \psi_{i}^{\sigma *}(\mathbf{r}) G_{i, 0}^{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right) \psi_{i}^{\sigma}\left(\mathbf{r}^{\prime}\right),
$$

where we have used a chain rule and the fact that $n$ is given by the sum of squares of orbitals, Eq. (7.2).

The integral form of the OEP equations (see Exercise 9.2) can be found by multiplying Eq. (9.13) by $\chi_{0}^{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ and integrating:

$$
\sum_{i=1}^{N^{\sigma}} \int \mathrm{d} \mathbf{r}^{\prime} \psi_{i}^{\sigma *}\left(\mathbf{r}^{\prime}\right)\left[V_{\mathrm{xc}}^{\sigma, \mathrm{OEP}}\left(\mathbf{r}^{\prime}\right)-V_{i, \mathrm{xc}}^{\sigma, \mathrm{NL}}\left(\mathbf{r}^{\prime}\right)\right] G_{i, 0}^{\sigma}\left(\mathbf{r}^{\prime}, \mathbf{r}\right) \psi_{i}^{\sigma}(\mathbf{r})+\text { c.c. }=0
$$

This form shows the physical interpretation that $V_{\mathrm{xc}}^{\sigma, \mathrm{OEP}}(\mathbf{r})$ is a particular weighted average of the nonlocal orbital-dependent potentials.

The integral form is the basis for useful approximations for which the potential can be given explicitly, e.g., as proposed by Krieger, Li, and Iafrate (KLI) [449-452]. Although KLI gave a more complete derivation, a heuristic derivation [446, 449, 450] is to replace the energy denominator in the Green's function by a constant $\Delta \varepsilon$. Then the value of $\Delta \varepsilon$ drops out of Eqs. (9.17) and (9.15) becomes

$$
G_{i, 0}^{\sigma}\left(\mathbf{r}, \mathbf{r}^{\prime}\right) \rightarrow \sum_{j \neq i}^{\infty} \frac{\psi_{j}^{\sigma}(\mathbf{r}) \psi_{j}^{\sigma *}\left(\mathbf{r}^{\prime}\right)}{\Delta \varepsilon}=\frac{\delta\left(\mathbf{r}-\mathbf{r}^{\prime}\right)-\psi_{i}^{\sigma}(\mathbf{r}) \psi_{i}^{\sigma *}\left(\mathbf{r}^{\prime}\right)}{\Delta \varepsilon}
$$

[^1]As discussed in Exercise 9.5, the KLI approximation leads to the simple form

$$
V_{\mathrm{xc}}^{\sigma, \mathrm{KLI}}(\mathbf{r})=V_{\mathrm{xc}}^{\sigma, S}(\mathbf{r})+\sum_{i=1}^{N^{\sigma}} \frac{n_{i}^{\sigma}(\mathbf{r})}{n^{\sigma}(\mathbf{r})}\left[\bar{V}_{i, \mathrm{xc}}^{\sigma, \mathrm{KLI}}-\bar{V}_{i, \mathrm{xc}}^{\sigma, \mathrm{NL}}\right]
$$

where $V_{\mathrm{xc}}^{\sigma, S}(\mathbf{r})$ is the density-weighted average proposed by Slater [453]

$$
V_{\mathrm{xc}}^{\sigma, S}(\mathbf{r})=V_{\mathrm{xc}}^{\sigma}(\mathbf{r})+\sum_{i=1}^{N^{\sigma}} \frac{n_{i}^{\sigma}(\mathbf{r})}{n^{\sigma}(\mathbf{r})} \bar{V}_{i, \mathrm{xc}}^{\sigma, \mathrm{NL}}
$$

and the $\bar{V}$ are expectation values

$$
\bar{V}_{i, \mathrm{xc}}^{\sigma, \mathrm{KLI}}=\left\langle\psi_{i}^{\sigma}\right| V_{\mathrm{xc}}^{\sigma, \mathrm{KLI}}\left|\psi_{i}^{\sigma}\right\rangle \quad \text { and } \quad \bar{V}_{i, \mathrm{xc}}^{\sigma, \mathrm{NL}}=\left\langle\psi_{i}^{\sigma}\right| V_{i, \mathrm{xc}}^{\sigma, \mathrm{NL}}\left|\psi_{i}^{\sigma}\right\rangle .
$$

Finally, by taking matrix elements of Eq. (9.19), the equations become a set of linear equations for the matrix elements $\bar{V}_{i, \text { xc }}^{\sigma, \text { KLI }}$, which can be solved readily. The KLI approximation, including only exchange, has been shown to be quite accurate in many cases [449].

## Slater Local Approximation for Exchange

An interesting detour is the difference between the Kohn-Sham formula for the exchange potential Eq. (8.16) and the local form Slater had proposed earlier [453] based on his approach of finding a local potential that is a weighted average of the nonlocal Hartree-Fock exchange operators Eq. (9.20). By averaging the exchange potential of the homogeneous gas, Slater found $V_{x}=2 \epsilon_{x}$, rather than the factor $4 / 3$ in Eq. (8.16) found by Kohn and Sham from the derivative of the exchange energy. In the context of the nonlocal exchange energy functional, it is not immediately clear which is the better approximation to carry over to an inhomogeneous system. Only recently has this issue been resolved [448, 451] by careful treatment of the reference for the zero of energy in transferring the potential from the gas to an inhomogeneous system and the second factor in Eq. (9.19). The result is the Kohn-Sham form Eq. (8.16).

It has been observed that the Slater local approximation for exchange often gives eigenvalues in better agreement with experiment than does the Kohn-Sham form. This has led to the "X $\alpha$ " approximation with an adjustable constant. In hindsight, this can be justified in part by the fact that gradient corrections lead to typical increases of similar magnitude, as shown in Fig. 8.6.

### 9.6 Localized-Orbital Approaches: SIC and DFT+U

Many of the most interesting problems in condensed-matter physics involve materials in which the electrons tend to be localized and strongly interacting, such as transition metal
oxides and rare earth elements and compounds with partially occupied $d$ and $f$ states. ${ }^{3}$ Often the usual functionals, such as the LDA and GGAs, find the system to be a metal whereas it is in fact a magnetic insulator. Even if the ground state is correct, the KohnSham bands may be very far from the true spectra. Various methods have been developed to extend the functional approach to treat localized $d$ and $f$ orbitals differently from the more diffuse $s$ and $p$ band-like states. A fundamental problem is that there is not a unique way to identify local orbitals in an extended system. Nevertheless, there are often very reasonable choices and in many cases the results do not depend on the details. The challenge is to use the methods in ways that bring insight and understanding - and often quantitative results for interesting problems!

## Self-Interaction Correction (SIC)

SIC denotes methods that add corrections to attempt to correct for the unphysical selfinteraction in the Hartree potential. This interaction of an electron with itself in the Hartree interaction is canceled in the exact treatments of exchange in Hartree-Fock and EXX discussed in Section 9.5. However, this is not the case for approximations to $E_{\mathrm{xc}}$, and the errors can be significant since these terms involve large Coulomb interactions. There is a long history to such approaches, the first by Hartree himself [50] in his calculations on atoms. As noted in Section 3.6, Hartree defined a different potential for each occupied state by subtracting a self-term due to the charge density of that state, literally the first SIC. An example of density functional calculations for $\mathrm{d} \rightarrow \mathrm{s}$ promotion energies for electrons in the 3d transition metal series is shown in Fig. 10.2, which shows a striking improvement when SIC is included. For an extended state in a solid, the correction vanishes since the interaction scales inversely with the size of the region in which the state is localized. Thus, in extended systems the value depends on the choice of the localized orbital much like the DFT+U method.

An approach to extended systems has been developed in which a functional is defined with self-terms subtracted; minimization of the functional in an unrestricted manner allows the system of electrons to minimize the total energy by delocalizing the states (in a crystal, this is the usual Kohn-Sham solution with vanishing correction) or by localizing some or all of the states to produce a different solution [313, 454]. This approach has an intuitive appeal in that it leads to atomic-like states in systems like transition metal oxides and rare earth systems, where the electrons are strongly interacting. Studies using the SIC and related approaches have led to an improved description of the magnetic state and magnetic order in transition metal oxides [455], high $T_{c}$ materials [456], and 4f occupation in rare earth compounds [457], which are discussed in more detail in [1].

[^2]![](./images/e6377f92-b320-4847-b808-c9b917cdf25a-14_382_1016_243_326.jpg)
Figure 9.2. Schematic for calculation of interaction parameter $U$ for electrons on a site (the central site show at the left) in a molecule or solid. The calculation is the same as for an atom in Section 10.6 except that the localized function must be chosen by some criterion and the interaction is screened by the surrounding system. The energy varies with the occupation $N$ as shown at the right: black dots denote $E(N)$, the slope of heavy dashed lines are the addition energies $\Delta E$ which vary discontinuously, and the light dashed lines indicate the eigenvalues at half-occupation which approximate $\Delta E$ (Slater transition rule). The interaction $U$ is the difference in eigenvalues as given in Eq. (10.22). The same approach can be used to determine exchange energies $J$ and other terms.

## Adding Hubbard-Like Interactions: DFT+U

The quaint acronym "LDA+U" is often used to denote methods that involve LDA- or GGAtype calculations coupled with an additional orbital-dependent interaction [458, 459], but we use the more general term "DFT+U." The additional interaction is usually considered only for highly localized atomic-like orbitals on the same site, i.e., of the same form as the "U" interaction in Hubbard models [460, 461]. The effect of the added term is to shift the localized orbitals relative to the other orbitals, which attempts to correct errors known to be large in the usual LDA or GGA calculations. For example, the promotion energies in transition metal atoms in Fig. 10.2 illustrate the fact that the relative energies shift depending on the approximation for exchange. The other effect occurs in partially filled d and f states, where occupation of one orbital raises the energy of the other orbitals, with the result that it favors magnetic states. Because the effects are critical for many problems involving 3d transition metal oxides and other materials, DFT+U calculations are an essential part of present-day methods.

One way to calculate the on-site interaction $U$ parameter is the "constrained density functional" approach, which is an adaptation of the $\triangle \mathrm{SCF}$ calculations for atoms in Section 10.6 and shown schematically in Fig. 9.2. For an isolated system like an atom it is straightforward to calculate the energy for different integer occupations of the states and determine energies to add, subtract, or promote electrons from differences of the total energy like in Eqs. (10.21) and (10.22). Since these involve ground-state energies the energy differences are in principle exact, unlike the Kohn-Sham eigenvalues. In addition, those equations also define the way that the Slater transition rule can be used to calculate the energy differences from the eigenvalue of the state at one-half integer occupation. As described in Section 10.6 the results can be quite accurate for atoms.

Many examples of "DFT+U" calculations are given in [1] and [459]. The prototypical examples are the transition metal oxides. Perhaps the best-known examples are the parent compounds of the CuO superconductors, which are found to be nonmagnetic metals in the usual LDA and GGA calculations (see Chapter 17), whereas "DFT+U" calculations find the correct antiferromagnetic insulator solution [459]. The usual spin density theory for materials like MnO and NiO finds the correct spin states and an energy gap, but the value of the gap is much too small as shown in Fig. 2.24. The gap is much better with hybrid functionals; however, it is often easier and more intuitive to correct the gap by a "U" term that increases the gap between the filled and empty 3d states and shifts the states relative to the oxygen states to agree much better with experiment.

## Generalized Koopmans' Functionals

A different formulation of the problem has been made starting from the fact that for a localized state the electron addition and removal energies as a function of electron number are the straight lines that join with discontinuous slope (piecewise linear) as depicted in Fig. 9.2. The linearity means that the energy of an orbital is independent of the occupation of that orbital itself, which is the very definition of having no self-interaction, and the discontinuities occur at the points where the orbitals change. ${ }^{4}$ This occurs at integer occupations and the energy of an orbital is shifted, as indicated in Fig. 9.2, by interaction with electrons in the other orbitals. This condition that the addition energies in a localized system are piecewise linear has been termed a generalization of Koopmans' theorem [462]; the original Koopmans' theorem (see Section 3.6) is that the addition energy for a electron in a particular state in Hartree-Fock is equal to its eigenvalue if all the states are rigid and do not relax. The generalization is the requirement that the energy of a state does not depend on its own occupation but may depend on the form and occupation of other orbitals.

This has been used to develop "Koopmans-compliant" functionals [463] that correct the smooth curvature in a continuous functional by adding a term to make it piecewise linear. Such a functional has features like SIC and DFT+U; however, it is more general in the sense that there may be different ways to choose the orbitals. For an extended system the eigenstates of the independent-particle hamiltonian are delocalized and the consequence of the occupation of one orbital vanishes as the size increases. The proposal in [463] is to define orbitals that are linear combinations of occupied states, which can vary from delocalized in which corrections vanish to localized with the piecewise linear behavior of the Koopmanscompliant functional, and to choose the degree of localization by minimizing the energy. The concepts have much in common with the earlier work on the unrestricted SIC method [313, 454], but it is more general and has been applied to a wide range of semiconductors and insulators [463].

[^3]
### 9.7 Functionals Derived from Response Functions

The next rung on the DFT ladder is to include information about the excited states. In the previous sections we have seen how to treat the exchange energy in the exact exchange and hybrid functional methods. However, in those methods correlation is not calculated from theory but is included as an LDA or GGA functional, where it is derived from some other source, such as calculations on two-electron atoms, the homogeneous gas, etc. Great insight and ingenuity was needed to invent the functionals of the density that have proven so useful; however, there are no systematic derivations that allow one to understand what is included, what is not, and what are steps toward further improvement.

The approach in this section is very different. In many ways it is a systematic application of exact relations and approximations using perturbation theory. Thus it is more straightforward to understand, but the price to be paid is that the calculations are much more involved and computationally intensive. The methods build on the many-body theory of excitations, which is covered in much more detail in the companion book [1]. However, it is not essential to go into the details of the many-body methods because work over the decades has built up much experience and approximations that can be understood using only methods developed in the previous sections and knowledge of response functions in Appendix D and the relation to the dielectric function in Section E.4.

The theoretical formulation is called the "adiabatic coupling fluctuation dissipation (ACFD) theorem," which can in understood in two parts. The first is the coupling-constant integration, which is also termed an "adiabatic connection" between a noninteracting problem and the full interacting system, with the interaction scaled by a $\lambda$ that varies from 0 to 1 (see Section 3.4) and the density constrained to be constant. This is an exact relation for the exchange-correlation energy as explained in Sections 5.3 and 8.2, and it is used in an approximate way to create hybrid functionals in Section 9.3. The other part is "fluctuation dissipation theorem," which is a well-known relationship given in Appendix D between the correlated fluctuations in a system to the response to a driving force (a response function). The result is that the correlation energy $E_{c}$ can be calculated by an integral over $\lambda$ and frequency of the density-density response function $\chi_{\lambda}(\omega)$ that depends on $\lambda$. It is in this sense that ground-state correlation energy is related to the frequency-dependent excitations of the system; the integral over all frequencies is needed to find the correlation at the same time that determines $E_{c}$.

The result is the ACFD theorem: ${ }^{5}$

$$
\begin{aligned}
E_{\mathrm{c}} & =-\frac{1}{2 \pi} \int_{0}^{1} d \lambda \int_{0}^{\infty} d u \operatorname{Tr}\left[v_{c}\left(\chi_{\lambda}(i u)-\chi_{0}(i u)\right)\right] \\
& =-\frac{1}{2 \pi} \int_{0}^{1} d \lambda \int d \mathbf{r} d \mathbf{r}^{\prime} v_{c}\left(\mathbf{r}-\mathbf{r}^{\prime}\right) \int_{0}^{\infty} d u\left[\chi_{\lambda}\left(\mathbf{r}^{\prime}, \mathbf{r} ; i u\right)-\chi_{0}\left(\mathbf{r}^{\prime}, \mathbf{r} ; i u\right)\right]
\end{aligned}
$$

[^4]where the first line reveals the elegant simplicity of the relation, and the second line is written out in real space. In Eq. (9.22) $u$ is an imaginary frequency, $v_{c}$ is the Coulomb interaction, $\chi_{0}$ is the response function for the independent-particle Kohn-Sham auxiliary system given in Eq. (9.24) below, and $\chi_{\lambda}$ is the response of a system with scaled interaction $\lambda v_{c}$, and with ground-state density required to be the same as $\lambda$ changes. This is an exact relation, but of course $\chi_{\lambda}$ for an interacting system is not known. When $\chi_{\lambda}$ is approximated in the RPA, $\chi_{\lambda}=\chi_{0} /\left(1-\lambda v_{c} \chi_{0}\right)$, the $\lambda$-integration can be done analytically and expressed as a logarithm or equivalently as a power series:
$$
E_{\mathrm{c}}^{\mathrm{RPA}}=\frac{1}{2 \pi} \int_{0}^{\infty} d u \operatorname{Tr}\left[\ln \left(1-v_{c} \chi_{0}\right)-v_{c} \chi_{0}\right]=\frac{-1}{2 \pi} \int_{0}^{\infty} d u \sum_{n=2}^{\infty} \frac{1}{n} \operatorname{Tr}\left[\left(v_{c} \chi_{0}\right)^{n}\right]
$$

The calculations can be done since $\chi_{0}(\omega)$ is given in terms of independent-particle wavefunctions. The general form is in Section D. 4 and it is instructive to note that the frequency-dependent expressions needed here are analogous to the static OEP equations. Expressed in real space $\chi_{0}\left(\mathbf{r}, \mathbf{r}^{\prime}, \omega\right)$ is given by the generalization of the static $\chi$ Eqs. (9.15) and (9.16) (see also Section D.4),

$$
\chi_{0}\left(\mathbf{r}, \mathbf{r}^{\prime}, \omega\right)=2 \sum_{i=1}^{\text {occ }} \sum_{j}^{\text {empty }} \frac{\psi_{i}(\mathbf{r}) \psi_{j}(\mathbf{r}) \psi_{j}\left(\mathbf{r}^{\prime}\right) \psi_{i}\left(\mathbf{r}^{\prime}\right)}{\varepsilon_{i}-\varepsilon_{j}+\omega+i \eta},
$$

where the factor of 2 is for spin, and there are similar expressions in momentum space. The calculations are much more computationally intensive than those for standard DFT since they involve sums over excited states. ${ }^{6}$ In general the wavefunctions and eigenvalues are determined by a nonlocal operator, similar to Hartree-Fock or a hybrid method. Alternatively, the energy in Eq. (9.23) can be calculated from the output of Kohn-Sham calculation or as a self-consistent procedure to minimize the total energy for wavefunctions that are generated by a local Kohn-Sham potential, where the latter amounts to finding an optimized effective potential (OEP) for the RPA formulation. References for methods and many results can be found in reviews [465, 466], and extensive benchmarks for RPA and related functionals for solids in [467].

One of the great advantages of the RPA is that it can treat dispersion interactions (see Section 9.8) since the interaction between two separated systems is due only to the longrange Coulomb interaction. The first term in the expansion in Eq. (9.23) is second order in the polarizability and it includes the leading term for weak interactions between pairs of atoms $\propto 1 / R^{6}$, even though the coefficient $C_{6 A B}$ is not exact in the RPA. Examples of applications are given in [466] where there is also a demonstration that for weak interactions, the system can be treated efficiently as coupled effective harmonic oscillators. The RPA formalism also provides the basis for one of the methods to develop the van der Waals functional in Section 9.8. The second-order expansion used in [468] is closely related

[^5]to the power series expansion in Eq. (9.23) and, in order to construct a density functional, those methods use a single-pole approximation at a plasma frequency that is determined by the density of electrons.

### 9.8 Nonlocal Functionals for van der Waals Dispersion Interactions

A major deficiency of all local and semilocal functionals is that they cannot describe the van der Waals interaction that is ubiquitous in weakly bonded atomic and molecular systems. Aside from the average Coulomb interaction that is included in the nuclear and Hartree terms, the longest-range interaction is purely a correlation effect due to quantum fluctuations of the electric dipole on one atom or molecule that induces dipoles on another, oriented such that the energy is lowered. The attraction between two atoms or molecules is often called the dispersion or London interaction, where the longest-range part of the interaction can be expressed as $C_{6} / R^{6}$ (see Exercise 9.6). The challenge in density functional theory is to develop a nonlocal functional that captures the effects of the longrange correlation on the energy, describes the intermediate-range interactions, and merges seamlessly into the regime where shorter-range effects are described by well-developed functionals. This is essential to describe important cases such as molecules on metal surfaces that require a method that can handle many types of bonding within the same framework.

The different approaches can be grouped into two types. One starts with long-range pairwise interactions between atoms that are modified at short range in such a way that they can be added to standard density functionals with little or no change in the short-range behavior. The other starts with the homogeneous gas and develops functionals that describe nonlocal correlation in such a way that it describes the long-range dispersion interactions in systems that are so inhomogeneous that they separate into nonoverlapping regions. Of course, there are connections between these approaches since each strives to have the same behavior at large distance, and each is designed to take advantage of the successes of local and semilocal approximations for metallic, covalent, and ionic bonding.

The van der Waals functionals could be grouped with the functionals in Chapter 8 since they are functionals only of the density. They are presented here because the underlying phenomena and the theory are fundamentally related to polarizability, which is a response function that depends on the occupied and unoccupied states, the topic of Section 9.7.

## Pair-Wise Additive Contributions to the Energy

The theory of the dispersion interactions can be formulated in terms of the Casimir-Polder [469] formula for the two non-overlapping atoms with frequency-dependent polarizability $\alpha(\omega)$,

$$
C_{6 A B}=\frac{3}{\pi} \int_{0}^{\infty} d u \alpha_{A}(i u) \alpha_{B}(i u)
$$

where $i u$ is an imaginary frequency. ${ }^{7}$ Expressions for higher-order terms ( $C_{8} / R^{8}$, etc.) are given by algebraic expressions in terms of $C_{6}$ and the fourth moment $\left\langle r^{4}\right\rangle$ of the dipole distribution of each atom [470]. In order to have a form that can be added to a standard DFT functional, the divergence at short distance must be eliminated, which can be accomplished by introducing a damping function $f(R)$ so that the interaction becomes a sum over pairs of atoms of terms with the form

$$
E_{d i s p}=-\frac{1}{2} \sum_{A B} \frac{C_{6 A B}}{\left(R_{A B}\right)^{6}} f\left(R_{A B}\right)
$$

where $f(R)$ varies smoothly from 0 at $R=0-1$ at large $R$. Convenient forms are Pade [470] and Fermi [439] functions, which are determined by the characteristic range and the rapidity of the variation.

One approach is to carry out the integral in Eq. (9.25) directly for each pair of atoms. This has been developed by Grimme and coworkers [470] using $\alpha(\omega)$ calculated by timedependent DFT, which has proven very useful for atoms, molecules, and clusters (see Sections 21.2 and 21.4). It is most desirable to find the constituent $\alpha(\omega)$ for atoms in an environment similar to that in the molecule or solid, and the choice in [470] is a hydride molecule in which the atom is attached to hydrogens so that it forms a closed-shell system, which has been done for all 94 elements from H to Pu . It turns out that the $C_{8} / R^{8}$ term is quite important at intermediate range and should be included explicitly or incorporated in the form of the damping function $f(R)$. In order to apply the results as an add-on to DFT functionals, the approach in [470] is to adjust the damping function $f(R)$ with two parameters that are different for each functional, and it has been shown to be very useful as a general method to treat systems from weakly interacting molecules to strongly bonded solids.

There are other approaches that aim to develop simpler more universal forms using approximations to the frequency dependence of the polarizability. It is instructive to consider the method of Tkatchenko and Scheffler (TS) [439] where the atomic realizability $\alpha(\omega)$ is approximated by a single pole at an effective frequency $\omega_{0}$, so that

$$
\alpha(\omega)=\frac{\alpha^{0} \omega_{0}^{2}}{\omega_{0}^{2}-\omega^{2}} \quad \text { and } \quad \alpha(i u)=\frac{\alpha^{0} \omega_{0}^{2}}{\omega_{0}^{2}+u^{2}}
$$

The integral is readily done, and one consequence is the relation (Exercise 9.7)

$$
C_{6 A B}=\frac{2 C_{6 A A} C_{6 B B}}{\frac{\alpha_{B}^{0}}{\alpha_{A}^{0}} C_{6 A A}+\frac{\alpha_{A}^{0}}{\alpha_{B}^{0}} C_{6 B B}},
$$

which is equivalent to formulas derived by London [97] and Slater-Kirkwood [95]. This vastly simplifies the problem and has been tested for large data sets for molecules. The

[^6]only inputs are the homopolar $C_{A A}$ and $C_{B B}$, which in turn are determined by only two parameters per atom, the static polarizability $\alpha^{0}$ and the effective frequency $\omega_{0}$.

The approach of TS is to turn this into a functional of the density by using the relation of polarizability and volume ${ }^{8}$ and the Hirshfeld partitioning [472] of the density $n(\mathbf{r})$ to assign a volume for each atom in the molecule or solid. Values of $\alpha^{0}, \omega_{0}$ and the homopolar $C_{6}$ are taken from previous work for a set of closed-shell atoms in free space, and the values of $C_{6}$ for each pair of atoms in a molecule or solid is found from the difference of the volumes from free atoms. The damping function $f\left(R_{A B}\right)$ is chosen to be a Fermi function with a form that is fitted to a set of data on selected systems, when it is used as an addition to the PBE functional. Although this route to a functional may seem to be based on many approximations, each one is tested separately on well-known systems and the resulting form has been applied to many problems.

## Functionals Based on Theories of Nonlocal Correlation

A different approach has been developed by Langreth and Lundqvist and their coworkers in a series of papers (see [468] and references to earlier work given there). The goal is to formulate a general theory of the correlation energy as a sum of local and nonlocal terms,

$$
E_{c}[n]=E_{c}^{L D A}[n]+E_{c}^{n l}[n]
$$

where $E_{c}^{L D A}[n]$ is the local density expression in terms of the correlation energy for the homogeneous gas, and the nonlocal part can be expressed as

$$
E_{c}^{n l}=\frac{1}{2} \int d^{3} r d^{3} r^{\prime} n(\mathbf{r}) \phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right) n\left(\mathbf{r}^{\prime}\right)
$$

where $\phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ is a functional of the density. ${ }^{9}$ In order to describe dispersion interactions between two systems with densities that do not overlap, $\phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ must include the long-range Coulomb interaction and incorporate information on the polarizability of each system. The challenge is to find a single-function $\phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ that describes the correlation energy for systems that range from the homogeneous gas (where $\phi$ must vanish) to van der Waals bonding solely in terms of the density.

The methods to find useful approximations for $E_{c}^{n l}$ and $\phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right)$ build on the long history of many-body methods to treat correlation, which have been developed to the point where there are simple forms that provide approximate but time-tested methods. The quintessential example is the random phase approximation (RPA), which is described in detail in the companion book [1], and the most relevant aspects can be found in Section 9.7. Calculation of the correlation energy can be done with the adiabatic coupling dissipation fluctuation

[^7](ACFD) method as described in Section 9.7, which leads to the correct long-range $1 / R^{6}$ form of the dispersion interaction. The value of the coefficient $C_{6}$ is not exact, but there is much experience in using the RPA to calculate accurate practicabilities $\alpha(\omega)$. At the other extreme is the homogeneous electron gas described in Section 5.3. Figure 5.4 shows that the RPA is not very accurate, but it provides a good description of the change in the correlation energy as a function of density, which is the information needed to calculate corrections to the LDA.

The problem is that the expressions in Section 9.7 involve integrals over dynamical density response functions $\chi(\omega)$, whereas the goal is a functional of only the ground-state density. It has proven to be possible to find very useful forms by building on previous experience with RPA in solids. It is useful to recall the relation to the dielectric function in Eq. (E.15), which can be written in schematic form as $\epsilon^{-1}(\omega)=1-v_{c} \chi(\omega)$ where $\chi(\omega)=\left(\chi_{0}(\omega) /\left(1-v_{c} \chi_{0}(\omega)\right)\right.$ in the RPA. The inverse function $\epsilon^{-1}(\omega)$ describes charge response and has peaks at the plasma frequency; for many purposes it is well approximated by a single pole at the plasma frequency $\omega_{P}$, which is determined by the electron density in analogy to Eq. (9.27) and the relation of the polarizability to volume in atoms.

The problem is more difficult in a solid since $\omega_{P}$ varies with momentum and the dielectric function is a matrix in momenta $\mathbf{q}$ and $\mathbf{q}^{\prime}$. The formulation proposed in [468], based on earlier works, is a single-pole approximation in terms of $S=1-\epsilon^{-1}=v_{c} \chi$ that can be expressed as

$$
S_{\mathbf{q}, \mathbf{q}^{\prime}}(\omega)=\int d^{3} r e^{\left(\mathbf{q}-\mathbf{q}^{\prime}\right) \cdot \mathbf{r}} \frac{\omega_{P}(\mathbf{r})}{\left(\omega_{\mathbf{q}}(\mathbf{r})+\omega\right)\left(\omega_{\mathbf{q}^{\prime}}(\mathbf{r})-\omega\right)},
$$

where $\omega_{P}(\mathbf{r})=4 \pi n(\mathbf{r}) e^{2} / m$ is the long-wavelength plasma frequency for a uniform system with density $n(\mathbf{r})$, i.e., a local approximation, and $\omega_{\mathbf{q}}(\mathbf{r})$ and $\omega_{\mathbf{q}^{\prime}}(\mathbf{r})$ have parameterized forms that interpolate between long and short wavelength limits, and they are assumed to depend only on the density and its gradients at the point $\mathbf{r}$. The nonlocal part of the correlation energy $E_{c}^{n l}[n]$ can be found by expanding the RPA formula in Eq. (9.23) to second order in $S$ [468],

$$
E_{c}^{n l}=\frac{1}{4 \pi} \int_{0}^{\infty} d u \operatorname{Tr}\left[S^{2}-\left(\frac{\nabla S \cdot \nabla v_{C}}{4 \pi}\right)^{2}\right]
$$

which vanishes for a uniform system. For nonoverlapping densities, integration by parts leads to $\nabla^{2} v_{c} \propto 1 / R^{3}$ and thus a $1 / R^{6}$ dependence of the last term in Eq. (9.32) [474]. Various functionals can be made by different choices for the $\omega_{\mathbf{q}}(\mathbf{r})$, for example, the simple analytic form called VV10 due to Vydrov and Voorhis [475], which can be expressed in the form of Eq. (9.30) with

$$
\phi\left(\mathbf{r}, \mathbf{r}^{\prime}\right)=\frac{3 e^{4}}{2 m^{2} g g^{\prime}\left(g+g^{\prime}\right)},
$$

where $g$ and $g^{\prime}$ are analytic functions of the density and its gradient as points $\mathbf{r}$ and $\mathbf{r}^{\prime}$ respectively.

It is not appropriate to attempt to compare functionals here because there are so many combinations of short-range and long-range dispersion functionals. An extensive review by

Mardirossian and Head-Gordon [415] compares the performance of 200 functionals applied to large data sets of molecules. Among all the functionals considered they concluded that the most promising overall is the VV10 form combined with a range-separated hydrid metaGGA. However, it is important to consider also the computational effort required and to examine carefully how well a chosen functional performs when applied to specific types of systems and phenomena.

### 9.9 Modified Becke-Johnson Functional for $\boldsymbol{V}_{\mathbf{x c}}$

A remarkably simple effective local potential for exchange was derived by Becke and Johnson (BJ) [476]. Its value at a point $\mathbf{r}$ depends only on densities evaluated at that same point and yet it is a good approximation to the potential derived from the nonlocal Fock operator. The goal was to describe the shell structure that is characteristic of the exact exchange potential and also to reproduce the uniform gas limit and be correct for hydrogenic systems (the same requirements as used in other functionals such as SCAN in Section 9.4). This was accomplished by including a term that involves the kinetic energy density $t$ (r), which is chosen to be the positive symmetric form defined in Eq. (9.7); the way it incorporates the shell structure is discussed in Section H. 4 and illustrated in Fig. H.2. The BJ form was subsequently modified by Tran and Blaha [477] to add a parameter $c$ giving the form

$$
V_{x}^{M B J}(\mathbf{r})=c V_{x}^{B R}(\mathbf{r})+(3 c-2) \frac{1}{\pi} \sqrt{\frac{5}{12}} \sqrt{\frac{2 t(\mathbf{r})}{n(\mathbf{r})}},
$$

where $V_{x}^{B R}(\mathbf{r})$ is the local potential defined by Becke and Roussel [442], which is close to the Slater potential (see Eq. (9.20)), and $c=1$ corresponds to the original BJ potential.

Since $V_{x}^{M B J}(\mathbf{r})$ is a semilocal potential it is much less expensive to calculate than hybrid functionals. Note, however, the formulation provides a potential, not an energy functional. There is no way to minimize a total energy and the procedure is to use another functional, such as LDA or a GGA, to find a self-consistent solution for the density and eigenfunctions, which are then used to construct the MBJ potential $V_{x}^{M B J}(\mathbf{r})$. in Eq. (9.34), and finally to compute the bands with $V_{x}^{M B J}(\mathbf{r})$.

By choosing a value of $c$ in the range 1.1-1.3, it was found that the resulting gaps are in remarkable agrement with experiment; however, the band widths are too narrow. Extensive comparisons with other methods and experiment can be found in [477] and [478]. For example, the gaps in Ge and NiO shown in Figs. 2.23 are 0 and $\approx 0.4 \mathrm{eV}$ in the LDA, but the MBJ potential starting from the LDA yields gaps 0.85 and 4.16 respectively [477] in good agreement with experiment and the hybrid HSE calculations shown in the figures.

### 9.10 Comparison of Functionals

It is instructive to examine the consequences of different approximations for the exchangecorrelation functional in various ways. In this section are results for a few selected atoms, chosen because they have nondegenerate ground states, which avoids the complications of
open-shell systems. Comparisons for solids are given in many places in this book, which are summarized in a list near the end of this section.

## One-Electron Problems: Hydrogen

The results for hydrogen are a special case. For any one-electron problem, Hartree-Fock is exact. In the calculation there are Hartree and exchange terms, each of which is unphysical since there are no electron-electron interactions, but they cancel exactly, leading to the exact solution. Exact exchange (EXX) involves the Hartree-Fock orbital-dependent exchange functional as described in, Section 9.5. For one electron, it is the same as Hartree-Fock and so it is also exact. However, one-particle problems are severe tests for functionals of the density, such as the LDA and GGAs, and for the other functionals, except for BLYP and SCAN, which are constructed to be exact for hydrogen. The functionals are designed to deal with many electrons, such as the homogeneous gas, and their application to a one-particle problem introduces unphysical nonzero values for the correlation energy and a local or other approximation for exchange that does not cancel the Hartree term. The results for various functionals are given in Table 9.1 and the most obvious result is that there are large errors in the LSDA that are considerably improved by the GGA and hybrid functionals. Note that the separate errors in exchange and correlation in the LSDA tend to cancel, so that the final LSDA energy is $\approx 0.48 \mathrm{Ha}$, in surprisingly good agreement with the exact value, 0.5 Ha . Although there is no such cancellation for the GGAs, their final results for the total energy are much improved over LSDA.

## Many-Electron Atoms

For more than one electron, the quantity called exchange is not a physically measurable energy. It is usually defined to be the Hartree-Fock value and correlation is defined to be the remaining energy beyond Hartree-Fock. There are quantitative differences (usually very small) for exact exchange EXX; here it is chosen since it may be considered more appropriate for comparison of functionals. The results shown in Table $9.1^{10}$ show the calculated values for exchange and correlation energies separately, and one sees immediately two important conclusions:

- Exchange is the dominant effect. Even though the fractional error in correlation may be larger, it is usually the error in the exchange that determines the final accuracy of the functional.

[^8]Table 9.1. Magnitude of exchange and correlation energies in Ha for selected spherically symmetric atoms for functionals described in the text. "Exact" denotes exact exchange (EXX) and correlation energies taken from [479]. Other energies are from [479], calculated with the same EXX density, except HSE06 (provided by Johannes Voss) and SCAN (provided by Biswajit Santra). See footnote in the text concerning the differences. The last row is the mean absolute relative error (MARE).
| Atom | Exact | LSDA | PBE | HSE06 | BLYP | SCAN |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Exchange |  |  |  |  |  |  |
| H | 0.3125 | 0.2680 | 0.3059 | 0.3088 | 0.3098 | 0.3125 |
| He | 1.0258 | 0.8840 | 1.0136 | 1.0193 | 1.0255 | 1.0306 |
| Be | 2.6658 | 2.3124 | 2.6358 | 2.6464 | 2.6578 | 2.6602 |
| N | 6.6044 | 5.908 | 6.5521 | 6.5764 | 6.5961 | 6.4114 |
| Ne | 12.1050 | 11.0335 | 12.0667 | 12.098 | 12.1378 | 12.1636 |
| MARE \% | 0 | 12.1 | 1.1 | 0.61 | 0.32 | 0.82 |
| Correlation |  |  |  |  |  |  |
| H | 0.0000 | 0.0222 | 0.0060 | 0.0055 | 0.0000 | 0.0000 |
| He | 0.0420 | 0.1125 | 0.0420 | 0.0409 | 0.0438 | 0.0379 |
| Be | 0.0950 | 0.2240 | 0.0856 | 0.0881 | 0.0945 | 0.0827 |
| N | 0.1858 | 0.4268 | 0.1799 | 0.1775 | 0.1919 | 0.1809 |
| Ne | 0.3929 | 0.7428 | 0.3513 | 0.3432 | 0.3835 | 0.3448 |
| MARE \% | 0 | 130 | 59 | 6.8 | 2.7 | 9.4 |
| Total Exchange-Correlation |  |  |  |  |  |  |
| H | 0.3125 | 0.2902 | 0.3143 | 0.3104 | 0.3098 | 0.3125 |
| He | 1.0678 | 0.9965 | 1.0602 | 1.0553 | 1.0663 | 1.0685 |
| Be | 2.7608 | 2.5364 | 2.7345 | 2.7349 | 2.7439 | 2.7429 |
| N | 6.7902 | 6.3348 | 6.7539 | 6.7384 | 6.7766 | 6.5923 |
| Ne | 12.498 | 11.7763 | 12.441 | 12.4069 | 12.5043 | 12.5084 |
| MARE \% | 0 | 6.9 | 0.85 | 0.65 | 0.31 | 0.74 |


- There are very large errors for LDA, more than $100 \%$ in the correlation energy! The other functionals are much better and hybrid functionals are the most accurate. For hybrids this is understandable since they involve the Hartree-Fock exchange in addition to the improvements due to the GGA, for example, HSE is built on the PBE functional plus a fraction of Hartree-Fock exchange. The SCAN functional also incorporates properties of GGA functionals and adds additional constraints.

It is often stated that errors in exchange and correlation tend to cancel. However, except for LDA where errors are very large, this is not a major factor and it is not always the case.

## Pointers to Places in This book with Comparisons of Functionals for Solids

- Lattice constants, bulk moduli for selected elements and compounds in Table 2.1 extracted from a set of 64 solids in [112], and the magnetization of Fe.
- Phase transitions under pressure for Si and $\mathrm{SiO}_{2}$ in Section 2.5.
- Phase transition in $\mathrm{MgSiO}_{3}$ potentially important for the lower mantel of the Earth comparing LDA and PBE in Fig. 2.12.
- Radial density distribution function for water in Fig. 2.15.
- Band structure of Ge in Fig. 2.23, which compares LDA, HSE and Hartree-Fock.
- Plot of gaps for selected elements in Fig. 2.24 comparing LDA, SCAN, and the hybrid functionals BLYP, HSE, and DDH.
- Optical spectra comparing LDA and HSE in the independent-particle approximation are shown in the left side of Fig. 2.25. Time-dependent DFT in Figs. 2.26 and 21.5 shows that long range functionals are essential to describe excitons.
- Bands near the $\Gamma$ point for CdTe and the inverted bands of HgTe , comparing PBE and HSE are shown in Fig. 27.10.

There are many places where much more extensive comparison of functionals can be found. One referred to earlier is the compendium by Mardirossian and Head-Gordon [415], which gives an overview and extensive assessment of 200 density functionals. An assessment of functionals applied to an important problem, water in many form - molecular interactions, liquid water, ices, etc. - can be found in [197].

## SELECT FURTHER READING

The functionals in this chapter rely heavily on many-body theory, amd many of the aspects are discussed in depth in the companion book [1].
See references at the end of Chapters 6 and 7 for general references for density functional theory and at the end of Chapter 8 for references on functionals. Almost all the reading on functionals includes hybrid functionals, which are widely used.

Reviews that foucus on functionals in this chapter:
Anisimov, V. I., Aryasetiawan, F., and Lichtenstein, A. I., "First principles calculations of the electronic structure and spectra of strongly correlated systems: The LDA + U method," J. Phys.: Condensed Matter 9:767-808, 1997.
Becke, A. D., "Perspective: Fifty years of density-functional theory in chemical physics," J. Chem. Phys. 140:301, 2014.
Grabo, T., Kreibich, T., Kurth, S., and Gross, E. K. U., "Orbital functionals in density functional theory: The optimized effective potential method," in Strong Coulomb Correlations in Electronic Structure: Beyond the Local Density Approximation, edited by V. I. Anisimov (Gordon \& Breach, Tokyo, 1998).
Kummel, S. and Kronik, L., "Orbital-dependent density functionals: Theory and applications," Rev. Mod. Phys. 80:3-60, 2008.

## Exercises

9.1 It is interesting to note that the construction of a kinetic energy functional of the density is a "fermion problem." See Section H. 1 and Exercise H. 1 and H.2. For noninteracting bosons, construct explicitly a practical, exact density functional theory.
9.2 Derive the general OEP expression, (9.11), using the chain rule, and show that it leads to the compact integral expression, (9.17).
9.3 Write out explicit expressions for the inversion of the response function needed in Eq. (9.11) by expressing the response function in a basis. Consider appropriate bases for two cases: a radially symmetric atom (with the potential and density on a one-dimensional radial grid) and a periodic crystal (with all quantities represented in Fourier space).
9.4 An impediment in actual application of the OEP formula, Eq. (9.11) is the fact that the response function is singular. Show that this is the case since a constant shift in the potential causes no change in the density. Describe how such a response function can be inverted. Hint: one can define a nonsingular function by projecting out the singular part. This may be most transparent in the case of a periodic crystal where trouble arises from a constant potential that is undetermined.
9.5 Show that the approximation, Eq. (9.18), substituted into the integral equation, (9.17), leads to the KLI form, Eq. (9.19), and discuss the ways in which this is a much simpler expression than the integral equation, (9.17).
9.6 Derive the power law for the London dispersion interaction, using a model with two oscillators, each with a charged particle attached to a spring, that are coupled by the Coulomb interaction. The longest-range term results from using the lowest nonzero term in a perturbation expansion. Is this sufficient to establish the result for any problem approximated by a single pole?
9.7 Derive the relation in Eq. (9.28) using the expression for a coefficient in Eq. (9.25) and the single-pole approximation in Eq. (9.27).
9.8 Show that the polarizability in Eq. (21.7) has units of volume. Show also that the polarizability of a perfectly conducting sphere is equal to its volume. This is derived in [480] and other books, but it is a good exercise to do it yourself.
9.9 See Exercise 8.6 and 8.7 for exchange and correlation (fictitious) terms in the LDA for H. Compare with the results in Table 9.1. Discuss the extent to which the results are improved in the hybrid functionals.


[^0]:    ${ }^{1}$ The arguments in this section relate to the exchange. What about correlation? The reason for so much emphasis on exchange is that it is usually the larger effect and the approximations are often more important quantitatively. However, there must ultimately be a reckoning with the difficult problem of correlation!

[^1]:    ${ }^{2}$ Note that $G_{0}$ and the derivative in Eq. (9.14) are diagonal in spin since they involve the noninteracting KohnSham system.

[^2]:    ${ }^{3}$ Extensive discussion of the interesting phenomena and theoretical methods can be found in [1], especially in chapters 19 and 20 . Calculation of the interaction $U$ from many-body methods and subtleties regarding the use of the "U" term are also discussed there.

[^3]:    ${ }^{4}$ Note that here an orbital denotes the spatial state and spin, e.g., a d shell consists of 10 orbitals. The idea of the energy as a function of $N$ can be realized by considering the localized system in contact with a reservoir with Fermi energy $\mu$. As $\mu$ varies the energy of the orbital relative to $\mu$ varies linearly; its occupation changes abruptly when the energy crosses $\mu$ but its energy does not change.

[^4]:    ${ }^{5}$ Clear discussions can be found in the early references [272, 464] and the reviews [465, 466], which also give many references, and there is extensive discussion of the RPA in [1]. Here we consider only the case with equal spin up and down; correlation involves both spins and there are nontrivial changes for a polarized system.

[^5]:    ${ }^{6}$ There are more efficient methods that do not require explicit sums over excited states as described in Sections 20.4 and 21.5, but they are still more costly than DFT with standard density functionals.

[^6]:    ${ }^{7}$ Imaginary frequencies are often used in many-body theory where they provide compact expressions like Eq. (9.25). For our purposes we only need to know that it is a straightforward integral if there is an analytic form for $\alpha(\omega)$, e.g., in the model in Eq. (9.27).

[^7]:    ${ }^{8}$ Exercise 9.8 is to show that polarizability has units of volume and that the polarizability of a conducting sphere of radius $R$ is equal to its volume. It follows from the general expression in (21.7) that an effective volume can be defined for atoms and molecules. Ways to determine the effective volume are described, for example, in [471].
    ${ }^{9}$ As it stands, Eq. (9.30) scales as $N^{2}$, where $N$ is the number of atoms; however, methods [473] have been developed using FFTs to reduce the computation to $\propto N \ln N$.

[^8]:    10
    It should be noted that the values are not all taken from the same reference and they are computed using different definitions, but the differences are not large and do not change the primary conclusions. The results for LDA, PBE, and BLYP are from [479] and used the same EXX density and wavefunctions to calculate the energies for each functional. The SCAN calculations used Hartree-Fock wavefunctions, which should be very close to EXX but are not identical. The HSE calculations were self-consistent with HSE wavefunctions, which lead to differences that are very small but significant for the detailed comparisons. A correction has been included, the same as the correction needed to bring the PBE calculations into agreement with the values from [479] quoted in the table, which is justified by the fact that HSE and PBE are closely related.

