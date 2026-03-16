
Use this workflow when converting book PDFs into Obsidian-ready Markdown.

The default goal is not just to get a `.md` file. The goal is to produce a vault-friendly book structure with chapter folders, local images, Obsidian-compatible math, and cleaned heading levels so the outline sidebar is useful.

## Local toolchain

The standard local tools are:

- Mathpix helper docs: `/Users/gradyclopton/utils/mathpix/README.md`
- PDF splitter: `/Users/gradyclopton/ObsidianVaults/me_510/tools/pdf_process.py`
- Mathpix chapter converter: `/Users/gradyclopton/ObsidianVaults/me_510/tools/mathpix_chapters_to_obsidian.py`

Mathpix credentials must be available in the shell environment:

- `MATHPIX_APP_ID`
- `MATHPIX_APP_KEY`

Use the chapter-based `md.zip` workflow by default. It preserves local `images/` folders and works offline inside Obsidian.

## Expected vault layout

Place converted books under:

```text
<vault>/Books/<Book Folder>/
```

Use a human-readable book folder name and be consistent. Recommended patterns are:

```text
<vault>/Books/<Author> <Short Book Title>/
<vault>/Books/<Author> - <Short Book Title>/
```

Do not leave the top-level folder ambiguous. Decide explicitly whether it is author-based or book-based before conversion, because the choice propagates into resume state, backup paths, and later cleanup.

Inside each book folder, use one folder per front matter, chapter, or back matter section:

```text
<vault>/Books/<Book Folder>/Front Matter/
<vault>/Books/<Book Folder>/Chapter 01 - Title/
<vault>/Books/<Book Folder>/Chapter 02 - Title/
...
<vault>/Books/<Book Folder>/Back Matter/
```

Inside each section folder, keep:

- one Markdown file with the same name as the folder, and
- one `images/` folder for extracted figures.

Example:

```text
<vault>/Books/Zettili Quantum Mechanics/Chapter 03 - Postulates of Quantum Mechanics/
  Chapter 03 - Postulates of Quantum Mechanics.md
  images/
```

Do not flatten all chapters into one folder. Each chapter must remain self-contained.

## Split manifest format

Before conversion, split the PDF into front matter, chapter PDFs, and back matter. Use a JSON file with one object per section:

```json
[
  { "title": "Front Matter", "start_page": 1 },
  { "title": "Chapter 01 - Fundamental Concepts", "start_page": 20 },
  { "title": "Chapter 02 - Quantum Dynamics", "start_page": 85 },
  { "title": "Back Matter", "start_page": 538 }
]
```

Rules:

- `start_page` is 1-based.
- Entries must be sorted by `start_page`.
- The first section must start on page `1`.
- Include `Front Matter` and `Back Matter` when useful.
- Use the real chapter titles in the `title` field because those names become folder and file names.

## Conversion workflow

### 1. Create or identify the destination vault

Use `ocreate` when starting a new vault. The shared Obsidian template already includes:

- the shared `.obsidian` configuration,
- the MathJax preamble file `preamble.sty`, and
- the `Extended MathJax` plugin needed for `\oiint` and `\oiiint`.

### 2. Build the split manifest

Create a `sections.json` file using the format above. Store it in a temporary work directory near the source PDF.

### 3. Split the PDF

Run:

```bash
python3 /Users/gradyclopton/ObsidianVaults/me_510/tools/pdf_process.py split \
  --src "/path/to/Book.pdf" \
  --sections-json "/path/to/sections.json"
```

This creates one PDF per section.

### 4. Convert the split PDFs with Mathpix

Run:

```bash
python3 /Users/gradyclopton/ObsidianVaults/me_510/tools/mathpix_chapters_to_obsidian.py \
  --src-dir "/path/to/split_pdfs" \
  --out-dir "/path/to/vault/Books/<Book Folder>"
```

Optional flags:

- `--include-regex`
- `--exclude-regex`
- `--force`

The converter:

- submits each split PDF to Mathpix,
- downloads `md.zip`,
- keeps local image files in `images/`,
- rewrites MathJax delimiters for Obsidian,
- and stores resume state in `<out-dir>/.mathpix_state.json`.

### 5. Ensure every section folder has an `images/` folder

If Mathpix did not extract any figures for a section, create an empty `images/` folder anyway so the structure stays consistent.

## Heading normalization rules

After Mathpix conversion, clean the headings so the Obsidian outline reflects the actual book structure.

### First principle

The goal is not to preserve Mathpix heading markup mechanically. The goal is to make the outline match the logical section structure of the book.

### General rule

Use numbered section depth to determine Markdown heading level.

For ordinary chapter numbering:

- `1.1` becomes level 1: `#`
- `1.1.1` becomes level 2: `##`
- `1.1.1.1` becomes level 3: `###`
- and so on

For appendix numbering:

- `A.1` becomes level 1: `#`
- `A.1.1` becomes level 2: `##`
- `A.1.1.1` becomes level 3: `###`

### Explicit numbered headings

If Mathpix already produced a numbered heading such as:

```md
## 2.4.5 Uncertainty Relation between Two Operators
```

keep it as a heading, but adjust the number of `#` markers to match the numbering depth.

For many books, the chapter-level numbered sections are the first headings you actually want in the outline. In those cases:

- `1.1` should usually be level 1: `#`
- `1.1.1` should usually be level 2: `##`
- unnumbered topic headings immediately under `1.1` often need to become inferred `1.1.1`, `1.1.2`, etc.

Also normalize OCR punctuation in numbered headings:

- `1.7- WAVE FUNCTIONS ...` -> `1.7 WAVE FUNCTIONS ...`
- `2.7■ POTENTIALS ...` -> `2.7 POTENTIALS ...`
- `A. 1 COULOMB'S LAW ...` -> `A.1 COULOMB'S LAW ...`

Also repair OCR/math corruption when the number and title are fused incorrectly. Example pattern:

- `## $8.2 E_{xc}$ ...` -> `# 8.2 $E_{xc}$ ...`

Preserve inline math in headings when it is meaningful, but normalize the section number outside the math unless the number itself is part of the formula.

### Inferred numbered subsections

Many books, especially Sakurai and Zettili, contain real subsection titles that Mathpix extracts as unnumbered headings.

If a heading-like line is a real content subtopic under the current explicit numbered section, promote it into an inferred numbered subsection.

Examples:

```md
## 1.2.1 Blackbody Radiation
### 1.2.1.1 Wien's energy density distribution
### 1.2.1.2 Rayleigh's energy density distribution
### 1.2.1.3 Planck's energy density distribution
```

and

```md
# 1.1 THE STERN-GERLACH EXPERIMENT
## 1.1.1 Description of the Experiment
## 1.1.2 Sequential Stern-Gerlach Experiments
## 1.1.3 Analogy with Polarization of Light
```

Use this rule:

- find the nearest preceding explicit numbered parent section,
- assign inferred children sequentially as `.1`, `.2`, `.3`, etc.,
- and set the Markdown heading level from the resulting numbering depth.

This is especially important for Mathpix outputs where a numbered section is followed by several unnumbered topical headings. Example:

```md
# 13.5 Supercells: Surfaces, Interfaces, Molecular Dynamics
## 13.5.1 "Frozen" Phonons and Elastic Distortions
## 13.5.2 Interfaces
## 13.5.3 Surfaces
## 13.5.4 Molecular Dynamics
```

Treat these as real subsection titles when they are clearly part of the numbered parent section.

Likewise, if a chapter has top-level numbered headings like `1.1`, `1.2`, etc., and then unnumbered conceptual headings appear before the next explicit numbered sibling, those conceptual headings are often inferred children of the most recent explicit section.

### Headings that should not stay in the outline

Demote these to bold text instead of headings unless there is a strong reason to keep them as part of the section structure:

- chapter banners like `CHAPTER 3`
- standalone chapter titles like `Theory of Angular Momentum`
- `Example ...`
- `Solution`
- `Problem ...`
- `Exercise ...`
- most `Remark` or `Remarks` labels
- Mathpix-generated chapter number lines like `## 13`
- standalone chapter-title lines like `## Plane Waves and Real-Space Methods: Full Calculations`
- `Abstract`
- `Summary`
- part banners like `PART IV` or `OVERVIEW AND BACKGROUND TOPICS`
- raw image-only headings
- alphabetized index letters like `A`, `B`, `C`

Examples:

```md
**CHAPTER 7**
**Problems**
**Example 2.4**
**Solution**
```

For Mathpix chapter conversions, it is usually best to demote the chapter-opening banner material to bold text:

```md
**PART IV**
**DETERMINATION OF ELECTRONIC STRUCTURE: THE BASIC METHODS**
**13**
**Plane Waves and Real-Space Methods: Full Calculations**
**Abstract**
**Summary**
```

Then let the first real numbered section, e.g. `13.1`, begin the outline.

### Judgment-call audit

After the first heading pass, manually review the deepest inferred headings.

This matters because a line may be a sibling topic rather than a child topic. For example, in Zettili, `Parity operator` belonged under `3.7.3` as `3.7.3.2`, not as a child of `3.7.3.1`.

Martin exposed another common case: a topic line may look like a free-standing heading but is actually one item in a numbered cluster under the current parent section. In those cases, keep the cluster parallel rather than nesting one item under another just because it appears later in the text.

So after automatic cleanup:

- review the deepest inferred headings,
- check them against the nearby section flow and table of contents,
- and manually adjust misnested cases.

## Verification checklist

Before rewriting headings, create a backup folder such as:

```text
<Author>/_backup_before_heading_fix_YYYY-MM-DD/
```

For chapter-based book conversions, prefer a local backup inside each chapter folder:

```text
<Book Folder>/Chapter 07 - Title/
  Chapter 07 - Title.md
  original/
    Chapter 07 - Title.md
  images/
```

This is the preferred method for manual cleanup because it keeps the backup adjacent to the edited file and makes chapter-by-chapter auditing straightforward.

After rewriting:

- verify that every edited file has the same line count as its backup,
- verify that content changes are limited to heading formatting and inferred numbering,
- verify that any math appearing in headings is still present after normalization,
- and spot-check representative chapters plus the deepest inferred headings.

Do not delete content during heading cleanup.

## Book-specific notes from prior conversions

### Zettili

- Mathpix often promoted `Example`, `Solution`, `Problem`, `Exercise`, and `Remark` lines into headings.
- Some unnumbered conceptual titles were real subsections and needed inferred numbering.
- Appendix numbering also needed cleanup.

### Sakurai

- Main numbered sections were usually present already.
- Most cleanup involved inferring numbered child subsections beneath those explicit section headings.
- `Problems` headings were better as bold text rather than numbered sections.
- OCR inserted stray characters like `■` and `-` into some numbered headings; normalize them.

### Martin

- Mathpix often emitted chapter-opening material as a stack of headings: part title, chapter number, chapter title, `Abstract`, and `Summary`.
- Those chapter-opening headings were usually better demoted to bold text so the first real outline entry was `n.1`.
- Many unnumbered topical headings inside a numbered section were true inferred subsections and should be renumbered sequentially, e.g. `13.5.2`, `13.5.3`, `13.5.4`.
- Some numbered headings containing inline math were malformed by OCR and needed repair without removing the math.
- Per-chapter `original/` backups worked well for verifying that heading cleanup did not remove content.

## Default expectation

When asked to convert a book PDF into Obsidian Markdown, use this workflow unless the user explicitly asks for a different structure.
