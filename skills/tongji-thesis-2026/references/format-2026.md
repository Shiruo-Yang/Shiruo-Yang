# Tongji University Master's Thesis Format, 2026 Sample

This reference summarizes formatting rules extracted from an approved 2026 Tongji University master's Word thesis sample. It is intended to guide 2026 Tongji master's thesis Word/LaTeX/PDF formatting. When the Word sample conflicts with `TJ-CSCCG/TongjiThesis`, prefer the sample for master's-thesis deliverables.

## Source Template

- Recommended LaTeX base: `TJ-CSCCG/TongjiThesis`
- Checked commit: `1c2e43c73315d25900222e6e3bc048b4e8498dfb`
- Commit date: 2026-05-31
- Useful files:
  - `main.tex`
  - `style/tongjithesis.cls`
  - `style/tongjithesis.cfg`
  - `chapters/metadata.tex`
  - `chapters/00_abstract.tex`
  - `chapters/03_float.tex`
  - `chapters/05_reference.tex`
  - `chapters/ack.tex`

Important caveat: the checked template version declares `degree=bachelor` by default and warns that non-bachelor degree values fall back to bachelor format. Use it as a LaTeX framework, not as the final master's format authority.

## Page Setup

Word sample section settings:

| Item | Value |
|---|---|
| Paper | A4 portrait, 21.0 cm x 29.7 cm |
| Top margin | 2.54 cm |
| Bottom margin | 2.54 cm |
| Left margin | 3.17 cm |
| Right margin | 3.17 cm |
| Gutter | 0 cm |
| Header distance | 1.70-1.80 cm in most sections; 2.00 cm appears in TOC/front matter |
| Footer distance | 1.75 cm in most sections; 1.50 cm appears in first section |

Recommended LaTeX override for master's output:

```tex
\usepackage[a4paper,top=2.54cm,bottom=2.54cm,left=3.17cm,right=3.17cm,headsep=0.6cm,footskip=0.79cm]{geometry}
```

Adjust `headsep`/`footskip` only after visual PDF comparison with the sample.

## Document Order

The sample begins with:

1. Chinese master's cover: `硕士学位论文` and `（学术学位）`.
2. Chinese title.
3. Candidate fields: name, student number, school, discipline, research direction, supervisor.
4. Chinese date, e.g. `二〇二五年十二月`.
5. English cover:
   - `A dissertation submitted to`
   - `Tongji University in conformity with the requirements for`
   - `the degree of Master Engineering`
   - English title
   - Candidate, student number, school/department, discipline, major, research fields, supervisor, date.
6. Chinese abstract.
7. English abstract.
8. Table of contents.
9. Main chapters.
10. References.
11. Acknowledgements and any back matter.

For master's theses, do not use the undergraduate `\MakeCover` and `\MakeInfoPage` output as-is.

## Main Styles Extracted From Word

Word measurements are stored in twentieths of a point and twips; values below are converted where useful.

| Purpose | Word style | Font/size | Paragraph settings | Notes |
|---|---|---|---|---|
| Chapter heading | `heading 1` | 黑体, 16 pt; complex-script size appears 24 pt | centered; before 24 pt; after 18 pt; line auto 12 pt; first-line indent 0 | Examples: `摘要`, `第1章 引言` |
| English abstract heading | English abstract heading style | Arial bold, 16 pt | centered; before 24 pt; after 18 pt | Prefer official spelling `ABSTRACT` unless matching a supplied sample exactly |
| Second-level heading | `heading 2` | 黑体, 15 pt; complex-script size appears 20 pt | before 24 pt; after 6 pt; first-line indent 0 | Examples: `1.1 光聚合技术概述` |
| Third-level heading | `heading 3` | 黑体, 14 pt; complex-script size appears 16 pt | before 12 pt; after 6 pt; first-line indent 0 | Examples: `1.1.1 自由基光聚合` |
| Fourth-level heading | `四级标题` | Times New Roman, 12 pt for Latin; Chinese inherits/uses body font | before 6 pt; exact line 20 pt | Examples: `2.2.3.1 结构表征`; outline level is not a normal TOC level |
| Body paragraph | no named style in sample | Chinese body font; Latin/numbers should be Times New Roman | first-line indent usually 480 twips, about 2 Chinese characters | Main text appears as unnamed paragraphs |
| Figure body paragraph | `图片` | 10.5 pt complex-script size | centered; before 10 pt; line auto 12 pt | Used around figure placements |
| Figure caption | `图注` | 10.5 pt | centered; before 6 pt; after 12 pt; first-line indent 0 | Pattern: `图1.1 标题`; below figure |
| Table caption | `表注` | 12 pt | before 6 pt; after 6 pt | Pattern: `表1.1 标题`; above table |
| Equation paragraph | `公式` | Times New Roman for formula text; 10.5 pt complex-script size | before 6 pt; after 6 pt; first-line indent 0 | Equation numbers like `(2-1)` |
| Bibliography | bibliography paragraph style | 11 pt; Times New Roman for complex-script/Latin | exact line 16 pt; hanging indent; direct paragraphs often left/hanging 440 twips | Entries begin `[1]...` |
| Acknowledgements | `致谢` | 仿宋 for Chinese | direct paragraphs use first-line indent 480 twips | Title itself follows chapter/backmatter heading style |

Default Word document style: 11 pt, complex-script 12 pt, after spacing 8 pt, line auto 278.

## Headings And Numbering

Science/engineering master's sample uses Arabic hierarchy:

- Chapter: `第1章 引言`
- Section: `1.1 光聚合技术概述`
- Subsection: `1.1.1 自由基光聚合`
- Fourth level: `2.2.3.1 结构表征`

Map these in LaTeX as:

```tex
\chapter{引言}
\section{光聚合技术概述}
\subsection{自由基光聚合}
\subsubsection{结构表征}
```

If using `TongjiThesis`, check the generated heading sizes and spacing against this table. The checked template's current `\tjfontchapter` is `\zihao{-3}` and may not exactly match the Word sample's 16 pt chapter heading.

## Front Matter Details

Chinese cover fields observed:

- `硕士学位论文`
- `（学术学位）`
- Thesis title
- `姓    名：...`
- `学    号：...`
- `学    院：...`
- `学科门类：...`
- `研究方向：...`
- `指导教师：...`
- Chinese date

English cover fields observed:

- `A dissertation submitted to`
- `Tongji University in conformity with the requirements for`
- `the degree of Master Engineering`
- English thesis title
- `Candidate: ...`
- `Student Number: ...`
- `School/Department: ...`
- `Discipline: ...`
- `Major: ...`
- `Research Fields: ...`
- `Supervisor: ...`
- English date

Treat repeated running text around the transition to abstract as header/footer or conversion artifact unless visual inspection proves it is intentional.

## Abstracts And Keywords

Chinese abstract:

- Heading: `摘要`, same style as chapter heading.
- Body: first-line indent about 2 Chinese characters.
- Keywords line: `关键词：` followed by comma-separated Chinese keywords.

English abstract:

- Heading: prefer `ABSTRACT` unless the supplied official sample requires otherwise.
- Body: English paragraphs with first-line indent.
- Keywords line: `Keywords: ...`.

## Figures, Tables, Equations

Figures:

- Figure content centered.
- Caption below figure.
- Caption format: `图1.1 标题`.
- Caption font/size: approximately 10.5 pt, centered.
- Caption spacing: 6 pt before, 12 pt after.

Tables:

- Caption above table.
- Caption format: `表1.1 标题`.
- Tables centered.
- Use three-line tables for clean academic tables whenever possible.
- For long tables, repeat the header and use `续表 X` on continuation pages.
- `TongjiThesis` already supports `booktabs`, `tabularx`, `longtable`, `threeparttable`, and `threeparttablex`; reuse these.

Equations:

- Equation paragraphs use centered or aligned formula layout with numbering such as `(2-1)`.
- Spacing is about 6 pt before and after.
- Use chapter-based numbering unless the target department requires another scheme.

## References

The sample uses numeric bracketed references:

```text
[1]Author A, Author B, Author C, et al. Title [J]. Journal, year, volume(issue): pages.
[2]Author A, Author B. Title [J]. Journal, year, volume(issue): pages.
```

Formatting:

- About 11 pt for Latin reference text.
- Exact line spacing about 16 pt.
- Hanging indent is used.
- Prefer GB/T 7714 numeric style.

In `TongjiThesis`, use either:

```tex
\tjbibresource{bib/references.bib}
\makereferences
```

with default `biblatex=true`, or `biblatex=false` for BibTeX/`gbt7714`.

## Header And Footer

Observed Word header/footer relationships include:

- Abstract header: `摘要`.
- English abstract header: English abstract heading.
- TOC header: `目录`, with a `STYLEREF` field.
- Main matter header: current chapter title, e.g. `第1章 引言`, with a `STYLEREF` field.
- Page number fields appear in footers using `PAGE` fields.

For generated LaTeX/PDF, ensure headers do not accidentally show undergraduate wording from `TongjiThesis` such as `毕业设计（论文）`.

## Conversion And Delivery Notes

- When converting Word to LaTeX, extract embedded images and keep stable filenames.
- Use raw XML or `python-docx` for style audits; do not rely only on Pandoc's visual approximation.
- If Word contains EMF/WMF drawings, convert them to PDF/PNG manually if needed for LaTeX.
- Keep source LaTeX, generated PDF, and generated DOCX together in a normal visible output folder.
- After building, check file size and page count; open/read the first pages if possible.
