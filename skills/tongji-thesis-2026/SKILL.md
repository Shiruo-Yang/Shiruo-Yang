---
name: tongji-thesis-2026
description: Use when formatting, converting, auditing, or generating Tongji University 2026 master's thesis documents, especially 同济大学硕士论文/学位论文/2026格式/Word转LaTeX/PDF/图表/参考文献 tasks. Uses TJ-CSCCG/TongjiThesis as the LaTeX base and an approved 2026 master's Word sample as the format authority.
---

# Tongji Thesis 2026

Use this skill for Tongji University 2026 thesis formatting work. The recommended LaTeX base is `TJ-CSCCG/TongjiThesis`, checked against commit `1c2e43c73315d25900222e6e3bc048b4e8498dfb` (2026-05-31). The 2026 master's format rules below were extracted from an approved Tongji master's Word thesis sample.

## Priority

1. Preserve the user's thesis content and scientific meaning.
2. Match the 2026 approved Word sample for master's-thesis page geometry, front matter, headings, body text, captions, tables, references, and acknowledgements.
3. Use `TJ-CSCCG/TongjiThesis` as the implementation base, but do not blindly trust its defaults: the checked template version is primarily undergraduate-oriented and `degree=master` falls back to bachelor formatting.
4. Prefer local template patterns and macros over one-off LaTeX hacks, but apply a 2026 master's override layer when the sample and template differ.

## Workflow

1. Inspect the source document structure first: title pages, Chinese/English abstracts, table of contents, chapters, figures, tables, equations, references, appendices, acknowledgements.
2. If the input is `.docx`, inspect raw Word XML when formatting matters; use `word/styles.xml`, `word/document.xml`, headers/footers, table properties, and relationships rather than visual guesses.
3. For LaTeX output, start from `TJ-CSCCG/TongjiThesis` files such as `main.tex`, `style/tongjithesis.cls`, `style/tongjithesis.cfg`, and chapter files. Create a project-local copy or patch layer instead of editing the upstream clone directly unless the user asks for template maintenance.
4. Use `xelatex`/`latexmk -xelatex` with Chinese fonts. Run enough passes for TOC, references, labels, and page numbers.
5. Deliver generated PDF and DOCX together in a visible output directory, usually `thesis_format_converted_outputs/`; do not hide final files in build or `.output` directories.
6. Before final response, verify that the PDF/DOCX exists and report exact paths.

## 2026 Master's Rules

Read `references/format-2026.md` for the extracted rules. Key defaults from the approved sample:

- Paper: A4 portrait.
- Margins: top 2.54 cm, bottom 2.54 cm, left 3.17 cm, right 3.17 cm.
- Header/footer distance: usually header 1.70-1.80 cm, footer 1.75 cm; cover/front matter may vary slightly.
- Main Chinese chapter heading: centered 黑体 16 pt, e.g. `第1章 引言`.
- Second-level heading: 黑体 15 pt, numbering `1.1`.
- Third-level heading: 黑体 14 pt, numbering `1.1.1`.
- Fourth-level heading: 12 pt, numbering `1.1.1.1`; not part of TOC outline in the sample.
- Body: first-line indent 2 Chinese characters, Chinese text in Song-style body font, English/numbers in Times New Roman when possible.
- Figure captions: below figures, centered, 10.5 pt, pattern `图1.1 标题`.
- Table captions: above tables, pattern `表1.1 标题`; tables should usually be centered and use clean three-line table styling where possible.
- References: numeric GB/T 7714-style list, hanging indent, approximately 11 pt Times New Roman for Latin text.

## LaTeX Base Notes

- `TongjiThesis` already provides useful figure/table/reference tooling: `booktabs`, `longtable`, `threeparttable`, `caption`, `subcaption`, `biblatex-gb7714-2015` or `gbt7714`.
- The checked template's page geometry is undergraduate-style (`top=4.0cm,bottom=2.7cm,left=3.3cm,right=1.8cm`), so override it for 2026 master's work.
- The checked template's front matter macros (`\MakeCover`, `\MakeInfoPage`, `\MakeAbstract`, `\MakeAbstractEng`) are undergraduate-specific. For master's theses, replace or bypass these with Chinese and English master's cover pages matching the 2026 sample.
- For science/engineering master's theses, use Arabic chapter numbering: `第1章`, `1.1`, `1.1.1`, `1.1.1.1`.

## Validation Checklist

- PDF and DOCX are both present in the same visible output directory.
- Cover pages show master's degree wording, not undergraduate `毕业设计（论文）`.
- Margins match the 2026 sample.
- Chinese abstract heading is `摘要`; English heading in the sample may contain a typo, but prefer the school-required spelling if the user or official template requires `ABSTRACT`.
- TOC starts after abstracts and uses chapter/section numbering consistently.
- Figure captions are below figures; table captions are above tables.
- References are numeric and ordered by citation/list convention required by the user.
- No unresolved LaTeX references, missing images, or missing bibliography entries remain.
