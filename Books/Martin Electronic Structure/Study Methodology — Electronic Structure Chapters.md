# Study Methodology — Electronic Structure Chapters

This document describes how to study electronic structure textbooks in this vault. The material in books like Martin's *Electronic Structure* does not fit cleanly into either the engineering methodology (Anderson) or the formalism methodology (Zettili/Sakurai). It requires a hybrid approach with its own entry categories, symbol table format, and chunking strategy.

---

## 1. General Philosophy

Electronic structure textbooks weave together three kinds of content that rarely appear in isolation:

**Physical theory** — exact theorems, variational principles, and formal constructions that define the framework. The Hohenberg-Kohn theorems, the Kohn-Sham construction, the adiabatic connection formula, and the Hellmann-Feynman theorem are examples. These entries have the flavor of formalism — they are theorems with proofs and conditions — but the objects involved are not abstract operators in Hilbert space. They are energy functionals of the density, constrained search constructions over wavefunctions, and variational statements with direct physical content.

**Approximation physics** — the zoo of approximations that make DFT practical, what each one assumes, what it captures, what it misses, and for which classes of systems it fails. LDA, GGA, DFT+U, hybrid functionals, pseudopotentials, PAW, ultrasoft potentials — each one is an approximation with a specific physical justification, a known domain of validity, and characteristic failure modes. These entries play the same structural role that assumptions play in the engineering methodology: they are the load-bearing walls that determine which downstream results you can trust.

**Computational methodology** — how calculations are actually done. Plane-wave basis sets, energy cutoffs, k-point sampling, SCF convergence, pseudopotential generation, PAW projectors, Pulay stress, smearing methods. These entries have a practical, engineering-like character: there are parameters you set, convergence criteria you check, and things that break when you make the wrong choice. But there is no conservation-equation hierarchy. The structure is: *here is a computational object, here is what it approximates, here are the knobs, here is what breaks.*

The Equation Index for electronic structure must accommodate all three types without forcing them into a single template. The solution is a set of entry categories matched to content type, a flexible symbol table that adapts to whether the entry is theoretical or computational, and a chunking strategy based on the conceptual architecture of DFT rather than on a derivation tree.

**Key principles:**

- **Approximations are first-class entries.** Every approximation — LDA, GGA, +U, pseudopotential, PAW, norm conservation — gets its own entry with a statement of what it assumes, what it captures, what class of systems it fails for, and *why* it fails (the physical mechanism, not just "it doesn't work for strongly correlated systems"). This is the single most important category for your research, because your daily decisions (which functional, which PAW potential, what U value, whether to trust a given total energy) all rest on understanding what each approximation is doing.

- **Physical meaning and computational consequence travel together.** A theorem like Hohenberg-Kohn has both a formal statement ("the density determines the external potential uniquely") and a practical consequence ("you are justified in writing the total energy as a functional of the density alone"). Both must appear in the entry. Similarly, a computational parameter like the plane-wave cutoff has both a mathematical meaning ("the maximum $|\mathbf{G}|$ in the basis expansion") and a physical consequence ("controls the spatial resolution of the charge density and forces"). Both must appear.
- **Failure modes are as important as results.** The most useful thing the Equation Index can tell you is *when not to trust a result*. Every approximation entry should include a "Failure Modes" subsection that describes the class of systems where the approximation breaks down, the physical reason for the failure, and the observable symptoms in a calculation (wrong band gap, metallic ground state for an insulator, SCF divergence, multiple DFT+U minima, etc.).

---

## 2. Master Reference Categories

### Theoretical Foundations

Exact results, existence theorems, variational principles, and formal constructions that define the framework. These are the bedrock — they hold regardless of which approximation you use. The entry should state the theorem, its conditions, and its physical content.

*Examples:* Hohenberg-Kohn Theorem I (density determines potential), Hohenberg-Kohn Theorem II (variational principle for energy functional), Kohn-Sham construction (auxiliary non-interacting system), Levy constrained-search formulation, adiabatic connection formula, Hellmann-Feynman theorem, Janak's theorem, Koopman's theorem (and its failure in DFT).

*Callout type:* `[!theorem]` for proved results with conditions; `[!definition]` for formal constructions.

### Approximations & Their Failures

Every approximation used in practical DFT calculations. Each entry must include not just what the approximation is, but *what physics it captures*, *what physics it misses*, and *for which systems it fails*. This category is the analog of Assumptions in the engineering methodology, but richer: an assumption in gas dynamics either holds or doesn't, while an approximation in DFT can be partially valid, producing qualitatively correct results for some properties and wrong results for others in the same calculation.

*Examples:* Local Density Approximation (LDA), Generalized Gradient Approximation (GGA-PBE), DFT+U (Hubbard correction), hybrid functionals (PBE0, HSE), self-interaction error, pseudopotential approximation, frozen-core approximation, norm conservation condition, PAW transformation, ultrasoft pseudopotentials.

*Callout type:* `[!approximation]` (a new callout type for this vault).

### Energy Expressions & Functionals

The quantitative expressions for the total energy and its components — kinetic energy functional, Hartree energy, exchange-correlation energy, external potential energy, ion-ion interaction, and the decompositions used in different contexts (Thomas-Fermi, Kohn-Sham, coupling-constant integration). These are the "equations" of electronic structure, analogous to conservation equations in gas dynamics.

*Examples:* Thomas-Fermi energy functional, Kohn-Sham total energy expression, exchange-correlation energy in terms of the xc-hole, coupling-constant averaged xc energy, LDA exchange energy, GGA exchange enhancement factor, Hubbard correction energy.

*Callout type:* `[!equation]` for named energy expressions; `[!functional]` when the emphasis is on the functional form and its dependence on the density.

### Computational Machinery

How calculations are actually implemented: basis sets, convergence parameters, algorithms, and the relationship between computational choices and physical accuracy. Each entry should specify what the parameter or method controls, what happens when it is set too low or too high, and how to test for convergence.

*Examples:* Plane-wave basis set and cutoff energy, k-point sampling and Monkhorst-Pack grids, SCF self-consistency cycle, mixing schemes (linear, Pulay/DIIS, Kerker), Fermi-Dirac smearing, Methfessel-Paxton smearing, pseudopotential generation (Hamann, Troullier-Martins, RRKJ), PAW sphere radii, Pulay stress.

*Callout type:* `[!method]` for algorithms and procedures; `[!parameter]` for computational settings with convergence implications.

### Definitions & Building Blocks

Quantities, objects, and concepts that recur across multiple chapters and entry types. These are the vocabulary — you need to recognize them instantly and know what space they live in.

*Examples:* Electron density $n(\mathbf{r})$, exchange-correlation hole $n_{\text{xc}}(\mathbf{r},\mathbf{r}')$, Kohn-Sham orbitals, Kohn-Sham eigenvalues (and what they do and do not mean), exchange-correlation potential $V_{\text{xc}}(\mathbf{r})$, phase shift $\eta_l(\varepsilon)$, scattering amplitude, pseudowavefunction, projector functions, augmentation charges.

*Callout type:* `[!definition]`

---

## 3. Entry Structure

Each entry has the following components in order:

1. **Heading:** `## N. Entry Name`
2. **Exercise Questions:** `> [!question]` callout with parts (a), (b), (c), etc.
3. **Main Result Callout:** The theorem, approximation, equation, method, or definition.
4. **Expository Paragraph(s):** Physical interpretation — what the result means, not how it was derived.
5. **Symbol Table:** Adapted to the entry type (see §4).
6. **Optional Subsections:** Conditions, Failure Modes, Practical Consequences, Connections Forward.

### 3.1 Callout Types

| Callout | Use For | Example |
|---|---|---|
| `[!theorem]` | Exact results with proofs and conditions | Hohenberg-Kohn theorems, variational principle |
| `[!definition]` | Definitions of objects and constructions | Kohn-Sham orbitals, xc-hole, phase shift |
| `[!equation]` | Named energy expressions and quantitative results | Kohn-Sham total energy, Thomas-Fermi functional |
| `[!functional]` | Functional forms emphasizing density dependence | LDA xc energy, GGA enhancement factor |
| `[!approximation]` | Physical approximations with validity domains | LDA, GGA, DFT+U, pseudopotential, frozen core |
| `[!method]` | Algorithms and computational procedures | SCF cycle, Pulay mixing, pseudopotential generation |
| `[!parameter]` | Convergence-controlling computational settings | Plane-wave cutoff, k-point grid, smearing width |

### 3.2 Optional Subsections

Different entry types benefit from different optional subsections:

| Subsection | Use With | Purpose |
|---|---|---|
| **Conditions** | `[!theorem]` | Under what conditions does this result hold? (e.g., non-degenerate ground state, v-representability) |
| **Failure Modes** | `[!approximation]` | For which systems/properties does this approximation fail, and why? Observable symptoms in calculations. |
| **Practical Consequences** | `[!theorem]`, `[!equation]` | What does this exact result tell you about your calculations? How does it constrain what approximations can or should do? |
| **Convergence Behavior** | `[!parameter]`, `[!method]` | How does the result change as this parameter is increased? What is the expected convergence rate? What are typical production values? |
| **Special Cases** | Any | Important limiting cases, reductions, or specializations. |
| **Connections Forward** | Any | Where this result recurs in later chapters, other books in the reading plan, or your research. |

### 3.3 The Description Paragraph

Same principle as in both the engineering and formalism methodologies: the description conveys **physical meaning**, not derivation history. But electronic structure entries often need to do something neither Anderson nor Zettili entries do: explain **what an approximation is physically getting right and what it is physically getting wrong**. This requires discussing the real many-body physics (exchange, correlation, self-interaction, charge transfer, localization) in terms that connect to observable consequences in your calculations.

For approximation entries in particular, the description should answer: *If I use this approximation for my CeO₂ system, what am I assuming about the electrons, and where might that assumption fail?*

#### Term-by-Term Interpretation

The most important function of the description paragraph is to **teach you to read the equation as meaning, not as symbols.** Every equation — whether a definition, a theorem statement, or an energy functional — is built from sub-expressions that each carry their own physical meaning. The description must break the equation into these chunks and interpret each one.

The goal is that after studying an entry, you can look at any piece of the equation and immediately say what it represents physically — not just name the symbol, but describe the role it plays. When you see $n(\mathbf{r})\,n(\mathbf{r}')$ in the Hartree energy, you should think "uncorrelated pair density — treating the charge at $\mathbf{r}$ and $\mathbf{r}'$ as independent," not just "density times density."

**How to write term-by-term interpretations:**

- **Start with a reading instruction.** Use phrasing like "Read this equation as...", "Read this from the inside out...", or "The three terms represent..." to orient the reader before diving into details.
- **Name each chunk.** Every meaningful sub-expression — a prefactor, an integrand, a summation, a ratio — gets a name and a one-sentence physical interpretation. For example: "The prefactor $\frac{1}{2}$ corrects for double-counting: the integral counts the pair $(\mathbf{r}, \mathbf{r}')$ and the pair $(\mathbf{r}', \mathbf{r})$ separately."
- **Explain what changes and what is fixed.** In an integral like $\int V_{\text{ext}}(\mathbf{r})\,n(\mathbf{r})\,d^3r$, explain that $V_{\text{ext}}$ is the fixed potential landscape and $n$ is the variable being optimized — the interplay between them is the physics.
- **Connect chunks to limiting behavior.** If a term vanishes in some limit, say so: "In regions where the density is nearly uniform, $|\nabla n|$ is small and the Weizsäcker correction is negligible."
- **Highlight what each term captures vs. misses.** For energy functionals with multiple terms, identify which physical effect each term represents and what physics is absent: "The first term captures the mean-field kinetic energy; it misses quantum interference (shell structure, bonding)."

This term-by-term style applies to all entry types, not just equations. A theorem statement like "the ground-state density uniquely determines $V_{\text{ext}}$ up to a constant" should be unpacked: what does "uniquely determines" mean operationally? What does "up to a constant" exclude? Why is the density the object that has this power?

### 3.4 Approximation Entries

Approximation entries have a richer internal structure than other entry types:

```markdown
## N. Approximation Name

> [!question]
>
> (a) Write the mathematical form of this approximation.
> (b) What physical picture or limit justifies it?
> (c) For what class of systems does it work well, and why?
> (d) For what class of systems does it fail, and what is the physical mechanism of failure?

> [!approximation] Approximation Name
>
> Mathematical statement of the approximation.

Description paragraph: physical interpretation.

### Failure Modes

| System Class | Symptom | Physical Reason |
|---|---|---|
| Strongly correlated oxides (e.g., CeO₂) | Metallic ground state, wrong band gap | Self-interaction error delocalizes f-electrons |
| Van der Waals complexes | No binding or wrong geometry | LDA/GGA cannot capture nonlocal correlation |
| ... | ... | ... |

### Practical Consequences

What this means for your calculations — when to use this approximation,
when to choose something else, what to check.
```

The Failure Modes table is the most important part. It is what you consult when a calculation gives you an unexpected result: you look at your approximation's known failure modes and check whether your system falls into one of them.

---

## 4. Symbol Table

### 4.1 The Hybrid Problem

Electronic structure straddles two worlds. Some quantities carry physical units (energies in eV or Hartree, lengths in Å or Bohr, forces in eV/Å). Others are functional objects — maps from function spaces to the reals — that don't have "units" in the same sense. And some are computational parameters (integers, dimensionless ratios) that control the calculation.

A single fixed symbol table format cannot serve all three. Instead, use the format that matches the entry type.

### 4.2 For Theoretical Foundations and Energy Expressions

Use a five-column format that tracks both physical dimensions and mathematical type:

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|

Where:

- **Symbol:** The mathematical notation.
- **Type:** What kind of object is this? Scalar field, functional of the density, operator, energy (scalar), wavefunction, etc. This is the electronic-structure analog of the QM formalism's Type column — it prevents you from confusing a functional with a function, or an orbital with a density.
- **Units:** Physical dimensions where applicable (eV, Hartree, Å⁻³, etc.), or "—" for dimensionless, or "functional" for objects that map functions to numbers.
- **Name:** Bold name.
- **Description:** Physical meaning.

#### Composite Sub-Expressions

Symbol tables should include not just individual variables, but also **composite sub-expressions** — meaningful chunks of the equation that carry their own physical identity. These are the conceptual units you want to recognize on sight.

For example, in the Hartree energy $E_{\text{Hartree}} = \frac{1}{2}\int d^3r\,d^3r'\,n(\mathbf{r})n(\mathbf{r}')/|\mathbf{r}-\mathbf{r}'|$, the symbol table should include:

- $n(\mathbf{r})\,n(\mathbf{r}')$ — "Uncorrelated pair density: treats charge at two points as independent."
- $1/|\mathbf{r}-\mathbf{r}'|$ — "Coulomb kernel: weights each pair by the inverse of their separation."
- $\frac{1}{2}\int d^3r\,d^3r'$ — "Pair summation with double-counting correction."

These composite entries are where most of the learning happens. When you see $|\nabla n|^2/n$ in a gradient correction, you should be able to name it ("reduced density gradient") and say what it measures ("how rapidly the density varies relative to its local value") without pausing. The symbol table is the tool that builds this fluency.

**When to include a composite sub-expression:** If a cluster of symbols has its own name, its own physical interpretation, or appears as a recognizable unit in other equations, it belongs in the symbol table as its own row. If it is merely an algebraic intermediate with no independent meaning, leave it out.

### 4.3 For Approximation Entries

Use the same five-column format, but include the key approximation-specific quantities: the parameters you set, the quantities being approximated, and the exact quantity they replace.

### 4.4 For Computational Machinery

Use a format tuned for parameters and convergence:

| **Parameter** | **Typical Values** | **Controls** | **Too Low** | **Too High** |
|---|---|---|---|---|

Where:

- **Parameter:** The VASP tag, input keyword, or conceptual name.
- **Typical Values:** Production-quality ranges for your class of system (e.g., "520 eV for Ce-O with hard O PAW").
- **Controls:** What physical aspect of the calculation this parameter governs.
- **Too Low:** What goes wrong — unconverged forces, wrong energies, missing physics.
- **Too High:** Cost implications — excessive computation time, memory, or (rarely) numerical issues.

This format does not exist in either the QM or engineering methodologies because neither deals with convergence parameters. It is specific to computational methods textbooks.

### 4.5 Example: LDA Exchange-Correlation Energy

**Theoretical symbol table (for the exact expression being approximated):**

| **Symbol** | **Type** | **Units** | **Name** | **Description** |
|---|---|---|---|---|
| $E_{\text{xc}}[n]$ | Functional: $n(\mathbf{r}) \mapsto \mathbb{R}$ | Hartree | **Exchange-correlation energy** | The exact xc energy; a functional of the density. Includes kinetic energy correction. |
| $n(\mathbf{r})$ | Scalar field: $\mathbb{R}^3 \to \mathbb{R}^+$ | Å⁻³ (or Bohr⁻³) | **Electron density** | The ground-state electron number density. |
| $\epsilon_{\text{xc}}^{\text{hom}}(n)$ | Function: $\mathbb{R}^+ \to \mathbb{R}$ | Hartree | **XC energy per electron of homogeneous gas** | The xc energy density of a uniform electron gas at density $n$. Known from QMC (Ceperley-Alder). |
| $\bar{n}_{\text{xc}}(\mathbf{r},\mathbf{r}')$ | Two-point function | Å⁻³ | **Coupling-constant averaged xc-hole** | The hole in the pair density averaged over the adiabatic connection. Integrates to $-1$. |

---

## 5. Exercise Questions

### 5.1 Emphasis

Exercise questions in electronic structure chapters serve a different purpose than in either QM formalism or gas dynamics. In QM, the core skill is *manipulating the formalism*. In gas dynamics, it is *applying equations to flow configurations*. In electronic structure, the core skill is **judgement**: knowing which approximation to use, what to trust, what to check, and how to diagnose when a calculation is giving you artifacts rather than physics.

Questions should therefore emphasize:

- **Write the expression** — at least one recall question per entry.
- **Physical meaning** — what does this functional/theorem/approximation actually tell you about electrons?
- **Diagnostic use** — "Your DFT+U calculation gives a metallic ground state for CeO₂. Using what you know about [this entry], what is the most likely cause?"
- **Approximation comparison** — "Why would LDA get the lattice constant of CeO₂ roughly right but the band gap completely wrong?"
- **Connecting exact theory to approximate practice** — "The Hohenberg-Kohn theorem guarantees that the exact functional exists. How does this constrain what properties a good approximate functional should have?"

Questions should NOT:

- Focus on derivation steps ("Starting from Eq. 6.3, derive...")
- Test trivia ("In what year was the Hohenberg-Kohn paper published?")
- Ask about topics the entry doesn't illuminate

### 5.2 Pacing

Work chapter by chapter, following the critical-path order from `pedagogy.md`:

**Ch 6 → Ch 7 → Ch 8 → Ch 9 → Ch 11 → Ch 13 → Ch 10 → Ch 19**

Within each chapter, chunk by conceptual unit (see §6).

---

## 6. Chunking Strategy

The chunking principle for electronic structure chapters follows the conceptual architecture of DFT, not a derivation tree (engineering) or a formalism web (QM). Each chunk should answer one major question.

**How to identify chunks:** Ask "what question does this section answer?" If two adjacent sections answer the same question from different angles, they are one chunk. If a single section answers two distinct questions, it is two chunks.

**Example — Martin Chapter 6 (DFT Foundations):**

1. **Thomas-Fermi as motivation** (6.2): What does a naive density functional look like, and why isn't it good enough?
2. **Hohenberg-Kohn theorems** (6.3): What exact statements can we make about density functionals?
3. **Levy constrained search** (6.4): Is there a more intuitive and general way to define the functional?
4. **Extensions and subtleties** (6.5–6.7): Finite temperature, v-representability, degenerate ground states — when do the theorems need modification?

**Example — Martin Chapter 8 (XC Functionals I):**

1. **The xc-hole and what it means** (8.2): What physical object determines the xc energy?
2. **LDA** (8.3–8.4): What does the local approximation assume, why is it justified, and what are its limits?
3. **GGA** (8.5): What does adding gradient information buy you, and where does it still fail?
4. **Results and reality checks** (8.6–8.7): How do LDA and GGA actually perform for real systems?

**Example — Martin Chapter 11 (Pseudopotentials):**

1. **Scattering and the pseudopotential idea** (11.1–11.2): What physical principle allows you to replace the all-electron problem with a softer one?
2. **Norm conservation** (11.4–11.5): What condition makes pseudopotentials transferable, and how are they generated?
3. **Nonlocal and separable forms** (11.6–11.8): How are pseudopotentials made computationally efficient?
4. **Ultrasoft and PAW** (11.11–11.12): How do modern methods go beyond norm-conserving pseudopotentials, and what does VASP actually use?

**Example — Martin Chapter 13 (Plane Waves, Full Calculations):**

1. **Plane-wave basis mechanics** (13.1–13.3): How does the basis work, what controls its size, and how are matrix elements computed?
2. **Convergence and practical choices** (13.4–13.5): Cutoff energy, k-points, FFT grids — what sets production values?
3. **Forces, stress, and structural optimization** (13.6–13.7): How are forces calculated, what is Pulay stress, and how do you optimize geometry?
4. **SCF algorithms** (13.8): How does the self-consistency cycle work, what mixing schemes exist, and what controls convergence?

---

## 7. Connections to Your Research

The electronic structure vault is not an academic exercise — it directly serves your DFT+U calibration on the CeO₂ reduction series, your MLIP training data generation, and ultimately your TTM-MD track simulations. Every entry's Connections Forward field should link to your research where applicable.

Some recurring connection patterns:

- **Approximation entries → DFT+U troubleshooting:** When your SCF doesn't converge for AFM Ce₇O₁₂, the Failure Modes tables on LDA, GGA, and DFT+U will tell you which approximation-related pathologies to check first.
- **Theoretical foundation entries → MLIP training data quality:** The Hohenberg-Kohn theorems and the Kohn-Sham construction tell you what your DFT reference energies actually *are* — variational minima of an approximate energy functional. When your Allegro potential reproduces your DFT training data perfectly but gives unphysical forces for a new configuration, the problem may be in the training data, not the potential.
- **Computational machinery entries → production calculation settings:** The entries on cutoff energy, k-points, and PAW potentials directly inform the convergence tests you should run before generating training data.
- **XC hole and coupling constant integration → physical interpretation:** When you need to explain *why* your U_eff acts differently on CeO₂ vs. Ce₂O₃, the xc-hole picture gives you the physical language to describe what's happening to the Ce 4f self-interaction.

---

## 8. Relationship to Other Vaults

The electronic structure vault is one node in a network. Key cross-vault connections:

- **QM vault (Zettili, Sakurai):** The electronic structure formalism assumes you know QM — Hilbert spaces, operators, eigenvalue problems, variational principles. When Martin says "the wavefunction is a functional of the density," you need the QM vault's formalism entries to know precisely what that means.
- **ME 510 vault (Anderson, Laney):** No direct content overlap, but the *methodology* transfers. The engineering approach to assumptions (first-class entries with validity conditions) is exactly what you need for DFT approximations. The symbol table's dimensional-analysis habit transfers directly to checking units in energy expressions.
- **Condensed Matter / Correlated Oxides (future books — Khomskii, Cox):** The physics of *why* DFT+U is needed for ceria lives in those books, not in Martin. Martin tells you *what* DFT+U does computationally; Khomskii and Cox tell you *what physics* it is trying to capture. Cross-reference heavily.

---

## 9. Quality Checklist

Before considering an Equation Index complete for a chapter, verify:

- [ ] Every major theorem, energy expression, and approximation has its own entry
- [ ] Every approximation entry has a Failure Modes subsection
- [ ] Computational machinery entries include convergence behavior and typical production values
- [ ] Symbol tables use the correct format for the entry type (theory vs. computation)
- [ ] Symbol tables include composite sub-expressions as named rows, not just individual variables (§4.2)
- [ ] Exercise questions emphasize judgement and diagnostic use, not derivation recall
- [ ] Description paragraphs include term-by-term interpretation of every equation (§3.3)
- [ ] Description paragraphs focus on physical meaning and computational consequence
- [ ] Connections Forward fields link to your research context and to other vaults
- [ ] Entry numbering is consecutive within each chapter's index
- [ ] Chunks follow the conceptual architecture, not the section numbering
