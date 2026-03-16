# Chapter Markup Instructions — Electronic Structure Vault

This document describes how to mark up a chapter source file with Obsidian callouts, vocabulary highlights, exercises, and detailed solutions after the Equation Index and Glossary for that chapter have been completed. The markup makes key equations, theorems, and definitions visually distinct when reading in Obsidian, creates yellow-highlighted vocabulary terms that link back to the glossary, provides guided-reading exercises that walk through the chapter's key results, and supplies complete worked solutions written in a rigorous algebraic chain style that shows every intermediate step.

---

## Prerequisites

Before marking up a chapter, you must have completed:

1. **Equation Index** for the chapter — all entries with callout types assigned, exercise questions, descriptions with term-by-term interpretations, symbol tables, and Connections Forward.
2. **Glossary** for the chapter — alphabetically organized definitions of all vocabulary terms introduced in the chapter.

The Equation Index determines which equations get callouts and what type. The Glossary determines which vocabulary terms get `==highlights==`. Do not start markup until both are finished.

---

## Step 1: Read the Full Chapter and Build a Placement Plan

Read the entire chapter source file and identify two things:

**Callout targets.** For each Equation Index entry that corresponds to a standalone equation, theorem, or functional definition in the chapter text, note the section and equation number where it appears. Not every index entry will get its own callout — some entries describe concepts discussed in prose (e.g., "V-representability," "derivative discontinuity") rather than standalone displayed equations.

A callout is appropriate when the chapter has a displayed equation (centered, on its own line with `$$...$$`) or a formal theorem statement that you want to visually distinguish. Concepts that appear only in running text are handled by highlights, not callouts.

**Highlight targets.** For each Glossary term, find the location in the chapter where that term is first introduced or defined. This is where you place the `==highlight==`. If a term is introduced once early in the chapter and then reappears in a formal definition later (e.g., `N-representability` mentioned briefly in §6.4 and then defined formally in §6.6), highlight it at both locations.

---

## Step 2: Add Callouts

### Callout Type Selection

Use the callout type that matches the entry's category in the Study Methodology (§3.1):

| Callout | Color | Use For | Icon |
|---|---|---|---|
| `[!theorem]` | Deep purple (160, 80, 255) | Exact results with proofs and conditions | Scale |
| `[!equation]` | Blue (66, 135, 245) | Named equations and quantitative results | Sigma |
| `[!functional]` | Teal (0, 180, 180) | Functional forms emphasizing density dependence | Function |
| `[!approximation]` | Orange-red (255, 120, 50) | Physical approximations with validity domains | Alert circle |
| `[!assumption]` | Amber (255, 170, 50) | Load-bearing assumptions | Shield |
| `[!method]` | Steel blue (100, 160, 220) | Algorithms and procedures | Cog |
| `[!parameter]` | Slate (140, 160, 185) | Convergence-controlling settings | Sliders |
| `[!definition]` | Yellow (238, 255, 0) | Definitions of objects and constructions | Book |
| `[!identity]` | Lavender (180, 140, 255) | Mathematical identities | Equal |
| `[!relation]` | Coral (255, 130, 150) | Named relations between quantities | Link |
| `[!figure]` | Orange (255, 184, 108) | Figures and diagrams | Image |
| `[!derivation]` | Purple (142, 68, 173) | Derivation prompts at points where the text derives or hints at a derivation | Pen-line |
| `[!exercise]` | Green (0, 200, 83) | Exercises and worked problems | Pencil |

### Callout Syntax

Wrap the equation in an Obsidian callout block. The label should include the entry name and the equation number from the textbook:

```markdown
> [!functional] Levy-Lieb constrained search functional (Eq. 6.18)
>
> $$
> F_{\text{LL}}[n]=\min_{\Psi \rightarrow n(\mathbf{r})}\langle\Psi| \hat{T}+\hat{V}_{\mathrm{int}}|\Psi\rangle
> $$
```

**Rules for callout content:**

- Include only the equation itself inside the callout — no description paragraphs, symbol tables, or interpretive text. That material lives in the Equation Index.
- For theorem statements (which are prose, not equations), include the formal statement inside the callout:

```markdown
> [!theorem] Hohenberg-Kohn Theorem I (§6.3)
>
> **Theorem I.** For any system of interacting particles in an external potential $V_{\text{ext}}(\mathbf{r})$, the potential $V_{\text{ext}}(\mathbf{r})$ is determined uniquely, except for a constant, by the ground-state particle density $n_{0}(\mathbf{r})$.
>
> **Corollary I.** Since the hamiltonian is thus fully determined, except for a constant shift of the energy, it follows that the many-body wavefunctions for all states (ground and excited) are determined. Therefore all properties of the system are completely determined given only the ground-state density $n_{0}(\mathbf{r})$.
```

- If the chapter already has the equation on display lines (`$$ ... $$`), wrap the existing lines inside `> ` blockquote prefixes. Do not change the equation itself.
- If a callout label would be the same as a section heading (e.g., the section is already titled "Spin density functional theory"), that is fine — the callout marks the key equation within that section.

### What Not to Wrap in a Callout

- Intermediate derivation steps (e.g., Eqs. 6.7–6.11 in the Hohenberg-Kohn proof). Only the final named result gets a callout.
- Equations that are not in the Equation Index. The Index is the source of truth for what counts as a key result.
- Prose-only concepts like "V-representability" or "derivative discontinuity" that don't have a standalone displayed equation. These get highlights instead.

---

## Step 3: Add Derivation Callouts

Derivation callouts mark every point in the chapter where the author works through a derivation, sketches a proof, or mentions that something *can* or *should* be derived. They serve a different cognitive purpose than equation callouts or exercises: they test whether you can **reproduce the mathematical reasoning** — "can I work this out?" — as opposed to the Equation Index, which tests whether you understand the **meaning** of a result.

### When to Place a Derivation Callout

Place a `[!derivation]` callout at any point in the chapter where:

- The author explicitly works through a multi-step derivation (e.g., applying the product rule to $\partial E / \partial \mathbf{R}_I$ and simplifying).
- The author states a result and says it "can be shown" or "it is straightforward to show" or refers to an exercise.
- The author mentions that a result "follows from" a previous expression in a way that implies nontrivial algebra.
- A theorem is proved inline rather than merely stated.

Do **not** place a derivation callout on a result that is simply presented as a definition or postulate with no derivation implied.

### Derivation Callout Syntax

```markdown
> [!derivation] Short descriptive title
> Prompt text — a question or set of questions that the reader must answer by working through the derivation.
```

The callout is placed **immediately before** the paragraph where the derivation begins in the chapter text, so the reader encounters the prompt before reading the worked-out steps.

### The `---` Divider Convention

If the chapter text actually works through the derivation in full (not just a passing mention), place a horizontal rule `---` on its own line after the derivation concludes, to mark where the worked material ends and the chapter resumes its narrative flow. If the chapter only mentions a derivation in passing (e.g., "it can be shown that..."), do **not** place a divider — the callout alone is sufficient.

### Prompt-Writing Philosophy

Derivation prompts must be written like good exam questions, not like guided tutorials. The cardinal rules:

**1. Never give away the answer or intermediate steps.** The prompt should state *what* to derive (typically by equation reference) and ask *why* the result is physically meaningful. It must not walk the reader through the method. If the key insight of a derivation is "the wavefunction terms vanish because the energy is at a variational extremum," the prompt must not say this — the reader should discover it.

**2. Never write a recipe.** Prompts like "do X, then do Y, then show Z" are forbidden. The reader should have to figure out the strategy, not just execute pre-planned steps. Compare:

- **Bad (recipe):** "Differentiate $E$ with respect to $\mathbf{R}_I$, obtaining three terms. Show that two vanish because the wavefunction is at a variational extremum. Then show the surviving term gives Eq. (3.19)."
- **Good (open prompt):** "Derive the expression Eq. (3.19) for the force on a nucleus. The result is remarkable: despite the electrons having kinetic energy and mutual interactions that both change as nuclei move, the force depends only on the electron density. What principle causes all other contributions to vanish, and under what circumstances can this cancellation fail?"

**3. Emphasize physical meaning and importance.** Every prompt should contain at least one question that asks *why* or *what does this mean* or *when does this break down*, not just *show that*. The reader should come away understanding the result, not just having verified it mechanically.

**4. Provide only the information that is strictly necessary.** Give equation references so the reader knows the target. Do not give the method, the key trick, the form of the answer, or the names of mathematical tools to use.

**5. Use the same voice as the chapter exercises.** Derivation prompts should feel like they belong in the same document as Exercises 3.1–3.23. They are questions that test understanding, not instructions that guide execution.

### Relationship to Other Callout Types

Derivation callouts are **independent** of equation/theorem callouts and exercises:

- An equation can have both a `[!equation]` callout (marking its visual prominence) and a `[!derivation]` callout upstream (marking the derivation that produces it). These serve different purposes.
- A derivation callout may reference an Exercise (e.g., "Exercise 3.5") if the textbook exercise asks for the same derivation.
- Derivation callouts do **not** appear in the Equation Index. The Index is for meaning; derivations are for working ability.

### CSS Setup

The `[!derivation]` callout requires a custom CSS snippet in the vault's `.obsidian/snippets/` folder:

```css
/* Derivation callout — purple */
.callout[data-callout="derivation"] {
    --callout-color: 142, 68, 173;
    --callout-icon: lucide-pen-line;
}
```

Enable it in Obsidian: Settings → Appearance → CSS Snippets → toggle on the snippet file.

---

## Step 4: Add Vocabulary Highlights

### Highlight Syntax

Obsidian renders `==text==` with a yellow background. Wrap glossary terms in `==` delimiters at the point in the chapter where they are introduced or defined:

```markdown
the ==Thomas-Fermi-Dirac approximation==, proposed in 1927
```

### What to Highlight

Highlight every term that has an entry in the chapter Glossary, at the location where it is first introduced or most clearly defined. Specifically:

- **Vocabulary terms and named concepts** — Thomas-Fermi-Dirac approximation, Dirac exchange, external potential, Hartree energy, universal functional, constrained search, N-representability, V-representability, derivative discontinuity, etc.
- **Named quantities when first defined** — electron density, spin density, chemical potential, Fermi energy, grand potential, etc.

### What NOT to Highlight

- **Equations, theorems, or functionals that already have callout blocks.** If Hohenberg-Kohn Theorem I is wrapped in a `[!theorem]` callout, do not also put `==` around the theorem name. The callout provides the visual distinction. However, if the same theorem is *mentioned by name in running text elsewhere* (not in its own callout), a highlight there is appropriate.
- **Every occurrence of a term.** Highlight only at the point of introduction/definition. If "external potential" appears 30 times in the chapter, highlight it once — where it is first defined or where the reader first encounters it as a named concept. Exception: if a term is mentioned briefly in an early section and then formally defined in a later section, highlight both.
- **Generic mathematical notation.** Do not highlight $n(\mathbf{r})$ or $V_{\text{ext}}$ in isolation — highlight the *named concept* ("==electron density==", "==external potential==") when it is being defined, not every symbolic occurrence.

### Handling LaTeX Inside Highlights

When a glossary term includes math symbols, place the `==` delimiters around the full term including the LaTeX:

```markdown
==$N$-representability==
==$V$-representability==
==Mermin functional==
```

The `==` and `$...$` work together in Obsidian — the highlight renders around the rendered math.

### Highlight Placement in Context

Place highlights so they read naturally. The `==` delimiters should wrap a noun phrase, not break mid-sentence in an awkward way:

**Good:**
```markdown
the ==Thomas-Fermi-Dirac approximation==, proposed in 1927
```

**Awkward:**
```markdown
the ==Thomas-Fermi-Dirac== approximation, proposed in 1927
```

If the chapter uses a slightly different form than the glossary entry (e.g., the chapter says "Weizsäcker correction" and the glossary is "Weizsäcker correction"), match the chapter's wording in the highlight.

---

## Step 5: Work Section by Section

Process the chapter in order, one section at a time:

1. Read the section.
2. Identify which Equation Index entries fall in this section.
3. Wrap the corresponding displayed equations in callouts.
4. Identify which Glossary terms are introduced in this section.
5. Add `==highlights==` to those terms.
6. Move to the next section.

This keeps the work organized and prevents you from missing items in long chapters. Track progress explicitly (e.g., "§6.2 done, §6.3 done, ...").

---

## Step 6: Verify Completeness

After marking up all sections, run a verification pass:

### Callout Verification

Go through every Equation Index entry and check:

- If the entry corresponds to a standalone displayed equation or theorem statement in the chapter, does it have a callout?
- Is the callout type correct (matching the entry's category)?
- Is the callout label accurate (correct equation number, correct name)?

Not every entry will have a callout. Entries for concepts discussed only in prose (like "V-representability vs. N-representability" or "derivative discontinuity") may appear only as highlights. This is expected.

### Highlight Verification

Go through every Glossary term and check:

- Does the term appear somewhere in the chapter text with `==` delimiters?
- If the term genuinely does not appear as a phrase in the chapter (e.g., "self-interaction error" may be a concept discussed in the Equation Index but never used as an explicit term in the chapter), note this — you cannot highlight a term that doesn't appear in the source text.

### Common Issues

- **Triple equals `===`**: This is a typo. Obsidian highlight syntax uses exactly two equals signs on each side: `==term==`. Triple equals will not render correctly.
- **Highlight inside a callout block**: If a glossary term appears inside a callout (e.g., "==universal functional==" in a theorem statement), the highlight will render inside the callout, which can look cluttered. Prefer to highlight the term where it appears in running text *outside* the callout. If the only occurrence is inside the callout, the highlight is acceptable.
- **Math-only lines**: Do not put `==` around an entire displayed equation. Highlights are for vocabulary terms in prose, not for equations.

---

## Step 7: Write Exercises

After callouts and highlights are in place, write exercises for the chapter. Exercises are placed inline in the chapter file (one per major section) and also collected into a standalone companion document.

### Exercise Style

The exercise style follows the pattern established in Anderson's *Modern Compressible Flow* (see `me_510/Books/Anderson/3 One-Dimensional Flow/3 One-Dimensional Flow.md` for the reference implementation). Key features:

**Physical setup paragraph.** Each exercise opens with a 2–4 sentence paragraph that sets the physical context — what system is being considered, what formalism is at play, what the reader should have in mind. This is not a question; it is framing that makes the exercise feel like a guided reading problem rather than a problem set.

**Multi-part structure.** Each exercise has 4–5 parts labeled (a) through (e). The parts build sequentially — early parts establish definitions and derivations, later parts ask for physical interpretation and connections forward.

**Question types.** Use a deliberate mix of:

- "Write the [equation/functional]..." — asks the reader to reproduce a key result and identify its components
- "Show that..." — asks for a derivation, usually sketching a proof or performing a constrained minimization
- "Explain why..." / "Explain in words..." — asks for physical interpretation in the reader's own language
- "What does this tell you about..." — asks the reader to draw a conclusion or identify a limitation that motivates later developments

**Tone.** Questions should read as a knowledgeable instructor guiding the student through the chapter's logic, not as terse homework prompts. Each part should be a full sentence or two that makes clear exactly what is being asked.

### Exercise Formatting

Each exercise uses the `> [!exercise]` callout:

```markdown
> [!exercise] Descriptive Title Reflecting the Section Content
> Physical setup paragraph establishing context. Consider a system...
>
> (a) First question. This part asks the reader to...
>
> (b) Second question, building on (a). Show that...
>
> (c) Third question. Explain why...
>
> (d) Fourth question. What does this tell you about...
```

**Title convention:** The title should name the main concepts covered — e.g., "The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization" — not a generic label like "Exercise 1."

### Exercise Placement

Place one exercise per major section, positioned directly after the section heading and before the body text:

```markdown
# 6.2 Thomas-Fermi-Dirac Approximation

> [!exercise] The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization
> ...

The earliest density functional approach to the electronic structure...
```

The exercises serve as "guided reading" problems — the student reads the exercise, then reads the section, and the section text provides the working needed to answer the questions.

**Section mapping.** Not every section needs an exercise. The introductory overview section (e.g., §6.1) does not get an exercise. One exercise per substantive section (e.g., §6.2 through §6.7) is the target.

### Mapping Equation Index Entries to Exercises

Each exercise should cover the Equation Index entries that fall in its section. Aim for complete coverage: every Equation Index entry should appear in at least one exercise. A single exercise can reference multiple entries (e.g., Exercise 6.2 covers Entries 1–4 and 16–17). Keep a running tally to verify that all entries are covered.

### Creating the Standalone Exercises Document

After all exercises are written inline in the chapter, create a companion document:

**Filename:** `Exercises — Martin, Chapter N.md` (in the same folder as the chapter file)

**Structure:**

```markdown
# Exercises — Martin, Chapter N: Chapter Title

Electronic Structure Vault

---

# Exercise N.X — Exercise Title

> [!exercise] Exercise Title
> ...

---

# Exercise N.Y — Exercise Title

> [!exercise] Exercise Title
> ...
```

Copy each exercise verbatim from the chapter file into the companion document. The exercises remain in both locations — inline in the chapter (for guided reading) and in the standalone document (for focused study or review).

---

## Step 8: Write Solutions

After exercises are in place and the standalone exercises document exists, write detailed solutions for each exercise. Solutions live in the exercises document, directly below each exercise's `> [!exercise]` callout. Solutions may also be placed inline in the chapter file beneath the exercise callout (for guided reading), but the exercises document is the primary location.

### Solution Style: Algebraic Chains with Connective Prose

The defining feature of a good solution is the **algebraic chain style**. Every derivation that involves more than one algebraic manipulation must be written as a `\begin{aligned}` equation block showing every intermediate step on its own line, connected by `&=` alignment. Prose appears *between* chains to explain the physical reasoning behind each step — why you are doing what you are doing. The reader should never have to fill in algebraic gaps.

**The pattern:**

1. A sentence or two of prose explaining the strategy or motivation for the next manipulation.
2. A `\begin{aligned}` block showing every algebraic step on its own line.
3. A sentence or two interpreting the result or setting up the next chain.
4. Repeat.

**Example — varying a power-law functional:**

Prose: "Factor out $n^{5/3}$ and use the binomial expansion $(1+x)^\alpha \approx 1 + \alpha x$ for small $x = \delta n / n$:"

```latex
$$
\begin{aligned}
(n+\delta n)^{5/3}
&= n^{5/3}\left(\frac{n+\delta n}{n}\right)^{5/3} \\
&= n^{5/3}\left(1+\frac{\delta n}{n}\right)^{5/3} \\
&\approx n^{5/3}\left(1+\frac{5}{3}\frac{\delta n}{n}\right) \\
&= n^{5/3} + \frac{5}{3}\,n^{2/3}\,\delta n
\end{aligned}
$$
```

Prose: "Therefore, subtracting the unperturbed term and integrating: ..."

**What to avoid:**

- **Describing algebra in words instead of showing it.** Do not write "expanding to first order gives $\frac{5}{3}n^{2/3}\delta n$" without the intermediate steps. The whole point is to show *how* you get there.
- **Single-line derivations that skip steps.** If a result requires factoring, expanding, simplifying, and canceling, show each operation on its own line in the aligned block.
- **Orphaned equations.** Every equation block should have prose before it (explaining the strategy) and after it (interpreting the result). Bare equation → equation → equation with no connective text is unacceptable.

### Solution Formatting

**Part headers.** Separate each part's solution with a level-5 header (`#####`). This keeps the Obsidian sidebar table of contents uncluttered — level 5 headers do not appear in the sidebar.

```markdown
##### Part (a) — Short Descriptive Title

Solution text...

##### Part (b) — Short Descriptive Title

Solution text...
```

**Inline in the chapter file.** When placing a solution inline in the chapter (beneath the exercise callout), use the same `#####` part headers. Do not use any header above level 5 within an exercise solution in the chapter file.

**In the exercises document.** Exercise division headers use level 1 (`# Exercise N.X — Title`). Part-level headers within solutions use level 5 (`##### Part (a) — Title`). This gives clean top-level navigation between exercises and keeps solution substructure out of the sidebar.

### Solution Content Guidelines

**Completeness.** Every part of every exercise gets a full solution. "Show that..." parts must show every step, not just state the result. "Explain why..." parts must give the physical argument in full sentences, not just name the concept.

**Definitions and notation.** State all relevant definitions and write out all relevant equations before using them. The reader should not need to flip back to the chapter while reading a solution.

**Physical interpretation.** For parts that ask "what does this mean physically" or "explain why," devote at least a full paragraph to the interpretation. Connect the mathematical result to physical intuition — e.g., after deriving the Thomas-Fermi equation, explain that $\mu$ is the chemical potential, that it equals the Fermi energy at zero temperature, and that regions where $V > \mu$ are classically forbidden.

**Dimensional analysis and scaling arguments.** When a result can be understood through dimensional analysis (e.g., $n^{4/3}$ scaling of exchange energy), include this as a complementary check, even if the derivation already proves the result algebraically.

**Boxed final results.** Key final equations — the ones the exercise asks the reader to derive — should be boxed with `\boxed{...}` to make them visually distinct from intermediate steps.

### Avoiding Answer Giveaways in Exercise Prompts

Exercise prompts must not state the answer within the question. This is the single most common error in exercise writing and it completely defeats the pedagogical purpose. Before finalizing any exercise, audit every part for giveaways:

**Severity levels:**

- **Worst offenders** — the prompt walks through the entire derivation or gives both sides of an identity. The student has nothing to do.
- **Moderate** — the prompt names all the components or gives the construction method. The student can pattern-match without understanding.
- **Mild** — the prompt gives a strong hint that narrows the answer. Sometimes acceptable for scaffolding, but should be deliberate.

**The fix:** Remove the giveaway content while preserving the question structure. Replace "The four terms are the kinetic energy $C_1\int n^{5/3}$, the external potential..." with "It contains four terms. Identify each by name..." The student should have to do the intellectual work of identifying, not just confirming.

**Always audit both files.** Any fix to an exercise prompt must be mirrored between the chapter file and the exercises document, since the exercises appear in both locations.

### Creating Standalone Solution Documents

For complex exercises where the solution is worked out in full before being inserted into the exercises document, create a standalone solution file:

**Filename:** `Solution — Exercise N.X.md` (in the same folder as the chapter file)

This file serves as a drafting space and reference copy. It uses `##` headers for parts (since sidebar clutter is not a concern in a standalone document) and can include additional commentary, verification steps (e.g., SymPy checks), and extended discussion that may be trimmed for the exercises document.

---

## Summary Checklist

- [ ] Equation Index and Glossary are complete before starting
- [ ] Every standalone key equation/theorem has a callout with correct type and label
- [ ] Callouts contain only the equation or theorem statement — no descriptions or tables
- [ ] Every Glossary term has `==highlights==` at its point of introduction
- [ ] Highlights wrap complete noun phrases, not partial terms
- [ ] No highlights on terms that already live inside their own callout block (unless also mentioned in running text)
- [ ] LaTeX inside highlights uses `==$...$-term==` syntax
- [ ] No triple-equals typos
- [ ] Verification pass confirms all Index entries and Glossary terms are accounted for
- [ ] Every derivation or "can be shown" passage has a `[!derivation]` callout placed before it
- [ ] Derivation prompts do not give away answers, intermediate steps, or methods — written like exam questions
- [ ] Derivation prompts emphasize physical meaning (every prompt has at least one "why" or "what does this mean" question)
- [ ] Full derivations in the text have a `---` divider after them; passing mentions do not
- [ ] Derivation callouts are independent of equation callouts (both may exist for the same result)
- [ ] One exercise per major section, placed after heading and before body text
- [ ] Exercises follow the physical-setup + multi-part + interpretation style
- [ ] Every Equation Index entry is covered by at least one exercise
- [ ] Exercise prompts audited for answer giveaways — no part states its own answer
- [ ] Standalone exercises companion document created with all exercises (using `#` headers for exercise divisions)
- [ ] Solutions written for all exercise parts using algebraic chain style (`\begin{aligned}` blocks)
- [ ] Solutions use `#####` part headers to avoid cluttering sidebar TOC
- [ ] Every derivation shows every intermediate step — no algebraic gaps
- [ ] Prose between equation chains explains the motivation for each manipulation
- [ ] Key final results boxed with `\boxed{...}`
- [ ] Solutions consistent between chapter file and exercises document

---

## Worked Example: Martin Chapter 6

The markup of Chapter 6 (Density Functional Theory: Foundations) serves as the reference implementation. Here is what was placed:

### Callouts (11 total)

| Callout Type | Label | Section |
|---|---|---|
| `[!approximation]` | Thomas-Fermi-Dirac energy functional (Eq. 6.1) | §6.2 |
| `[!equation]` | Particle number constraint (Eq. 6.2) | §6.2 |
| `[!approximation]` | Weizsäcker gradient correction | §6.2 |
| `[!equation]` | Many-body Hamiltonian (Eq. 6.6) | §6.3 |
| `[!theorem]` | Hohenberg-Kohn Theorem I (§6.3) | §6.3.1 |
| `[!theorem]` | Hohenberg-Kohn Theorem II (§6.3) | §6.3.2 |
| `[!functional]` | Hohenberg-Kohn energy functional (Eq. 6.12) | §6.3.2 |
| `[!functional]` | Universal functional (Eq. 6.13) | §6.3.2 |
| `[!functional]` | Levy-Lieb constrained search functional (Eq. 6.18) | §6.4 |
| `[!theorem]` | Spin density functional theory (Eq. 6.19) | §6.5 |
| `[!functional]` | Mermin grand potential functional (Eq. 6.20) | §6.5.1 |

### Highlights (24 of 25 glossary terms)

All glossary terms were highlighted except "self-interaction error," which does not appear as an explicit phrase anywhere in the Chapter 6 source text. The concept is discussed implicitly in the Hartree energy context, but Martin never uses that exact label in this chapter.

### Entries Without Standalone Callouts

These Equation Index entries describe concepts in prose rather than standalone equations, so they are covered by highlights and/or by their presence within other callouts:

- Entry 2 (External potential) — highlighted as `==external potential==` in §6.2
- Entry 4 (Particle number constraint / chemical potential) — the constraint has its own callout; chemical potential and Fermi energy are highlighted in prose
- Entry 7 (V-representability vs. N-representability) — highlighted in §6.4 and §6.6.1
- Entry 15 (Nonanalyticity of the exact functional) — discussed in §6.7 prose; derivative discontinuity highlighted in §6.5.1

### Exercises (6 total, 25 question parts)

| Exercise | Section | Title | Parts | Index Entries Covered |
|---|---|---|---|---|
| 6.2 | §6.2 | The Thomas-Fermi-Dirac Energy Functional and Constrained Minimization | (a)–(e) | 1–4, 16–17 |
| 6.3 | §6.3 | The Hohenberg-Kohn Theorems and the Energy Functional | (a)–(d) | 5, 8–11 |
| 6.4 | §6.4 | The Levy-Lieb Constrained Search and the Domain of the Functional | (a)–(d) | 7, 12 |
| 6.5 | §6.5 | Extensions: Spin Density, Finite Temperature, and the Derivative Discontinuity | (a)–(d) | 6, 13–14 |
| 6.6 | §6.6 | Allowed Densities and Properties of the Exact Functional | (a)–(d) | 7 (revisited) |
| 6.7 | §6.7 | Nonanalyticity of the Exact Functional and the Limits of Explicit Density Functionals | (a)–(d) | 15 |

All 17 Equation Index entries are covered across the 6 exercises. The standalone companion document is at `6 Density Functional Theory: Foundations/Exercises — Martin, Chapter 6.md`.

---

## Worked Example: Martin Chapter 3 — Derivation Callouts

The markup of Chapter 3 (Theoretical Background) serves as the reference implementation for derivation callouts. Here is what was placed:

### Derivation Callouts (15 total)

| Title | Section | Full/Mention | `---` Divider |
|---|---|---|---|
| Born-Oppenheimer reduction of the full Hamiltonian | §3.1 | Mention | No |
| Electron density from the density operator | §3.1.1 | Mention | No |
| Total energy expression — external potential reduces to a density integral | §3.1.1 | Mention | No |
| Rayleigh-Ritz variational principle → Schrödinger equation | §3.1.1 | Full | Yes |
| Grouping the total energy into neutral classical Coulomb terms | §3.2 | Mention | No |
| Force (Hellmann-Feynman) theorem | §3.3.1 | Full | Yes |
| Stress (generalized virial) theorem from scaling of space | §3.3.2 | Full | Yes |
| Coupling constant integration (adiabatic connection) | §3.4 | Full | Yes |
| Equilibrium density matrix from free energy minimization | §3.5 | Mention | No |
| Fermi-Dirac distribution from the grand canonical ensemble | §3.6.1 | Mention | No |
| Hartree-Fock energy from the Slater determinant | §3.6.2 | Mention | No |
| Hartree-Fock equations from constrained variational minimization | §3.6.2 | Mention | No |
| Koopmans' theorem — eigenvalues as addition/removal energies | §3.6.3 | Mention | No |
| Pair distribution and exchange hole for noninteracting fermions | §3.7.1 | Mention | No |
| Correlation hole sum rule | §3.7.2 | Mention | No |

### Prompt Style Notes

All 15 prompts were audited against the prompt-writing philosophy in Step 3. None give away intermediate steps or read as recipes. Each prompt: (a) states the target result by equation reference only, (b) asks at least one interpretive or physical-meaning question, and (c) does not reveal the method or key insight the reader must discover. The Chapter 3 prompts can be used as templates when marking up subsequent chapters.