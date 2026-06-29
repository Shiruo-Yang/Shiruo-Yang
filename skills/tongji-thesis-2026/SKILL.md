---
name: tongji-thesis-2026
description: Use when formatting, converting, auditing, or generating Tongji University 2026 graduate thesis documents, especially 同济大学研究生学位论文/硕士论文/博士论文/2026格式/Word转LaTeX/PDF/图表/参考文献 tasks. Uses TJ-CSCCG/TongjiThesis as the LaTeX base and the Tongji graduate thesis writing reference example as the highest format authority.
---

# Tongji Thesis 2026

Use this skill for Tongji University graduate thesis formatting work. The recommended LaTeX base is `TJ-CSCCG/TongjiThesis`, checked against commit `1c2e43c73315d25900222e6e3bc048b4e8498dfb` (2026-05-31). The highest format authority is the Tongji graduate thesis writing reference example, titled `同济大学研究生学位论文写作参考示例`.

## Priority

1. Preserve the user's thesis content and scientific meaning.
2. Follow the Tongji graduate thesis writing reference example when any format rule conflicts with older local notes or a converted thesis sample.
3. Use `TJ-CSCCG/TongjiThesis` as the implementation base, but do not trust its defaults blindly: the checked template version is primarily undergraduate-oriented and `degree=master` falls back to bachelor formatting.
4. Apply a project-local 2026 graduate override layer for cover pages, page geometry, headings, body text, captions, references, acknowledgements, resume/publications, and declarations.

## Workflow

1. Inspect the source document structure first: Chinese cover, English cover, cover notes if present, Chinese/English abstracts, TOC, chapters, figures, equations, references, appendices, acknowledgements, resume/publications, originality statement, copyright authorization.
2. If the format authority is `.doc`, convert or inspect it before trusting visual guesses. Useful approaches: Apache Tika for text/HTML and Apache POI HWPF for sections, paragraph styles, fonts, and line spacing.
3. If the input is `.docx`, inspect raw Word XML when formatting matters; use `word/styles.xml`, `word/document.xml`, headers/footers, table properties, and relationships.
4. For LaTeX output, start from `TJ-CSCCG/TongjiThesis` files such as `main.tex`, `style/tongjithesis.cls`, `style/tongjithesis.cfg`, and chapter files. Create a project-local copy or patch layer instead of editing the upstream clone directly unless the user asks for template maintenance.
5. Use `xelatex`/`latexmk -xelatex` with Chinese fonts. Run enough passes for TOC, references, labels, and page numbers.
6. Deliver generated PDF and DOCX together in a visible output directory, usually `thesis_format_converted_outputs/`; do not hide final files in build or `.output` directories.
7. Before final response, verify that the PDF/DOCX exists and report exact paths.

## 2026 Graduate Rules

Read `references/format-2026.md` before formatting a Tongji graduate thesis. Key rules from the reference example:

- Paper: A4 portrait.
- Margins: top 2.54 cm, bottom 2.54 cm, left 3.17 cm, right 3.17 cm.
- Chinese abstract, TOC, chapter, references, appendix, acknowledgements titles: 黑体, 三号, bold, centered, single spacing, 24 pt before, 18 pt after.
- English abstract title: Arial, 三号, bold, centered, single spacing, 24 pt before, 18 pt after.
- Body: 宋体 小四; English and numbers Times New Roman 小四; justified; first-line indent 2 Chinese characters; fixed 20 pt line spacing; 0 pt before/after.
- First-level heading such as `1.1`: 黑体 小三, single spacing, 24 pt before, 6 pt after.
- Second-level heading such as `1.1.1`: 黑体 四号, single spacing, 12 pt before, 6 pt after.
- TOC entries: 宋体 小四, fixed 18 pt line spacing, page numbers right aligned.
- Figure captions: below figures, 宋体 五号, centered, single spacing, 6 pt before, 12 pt after, one-character space between number and caption.
- References: content 宋体 五号; English Times New Roman 五号; hanging indent 2 characters; fixed 16 pt line spacing.
- Acknowledgements body: 仿宋 小四, justified, fixed 20 pt line spacing, first-line indent 2 characters.
- Resume/publications body: 宋体 五号; English Times New Roman 五号; fixed 16 pt line spacing; labels such as `个人简历` and `已发表论文` bold.

## LaTeX Base Notes

- `TongjiThesis` already provides useful figure/table/reference tooling: `booktabs`, `longtable`, `threeparttable`, `caption`, `subcaption`, `biblatex-gb7714-2015` or `gbt7714`.
- The checked template's page geometry is undergraduate-style (`top=4.0cm,bottom=2.7cm,left=3.3cm,right=1.8cm`), so override it for graduate-thesis work.
- The checked template's front matter macros (`\MakeCover`, `\MakeInfoPage`, `\MakeAbstract`, `\MakeAbstractEng`) are undergraduate-specific. For graduate theses, replace or bypass these with Chinese and English graduate cover pages matching the reference example.
- For science/engineering graduate theses, use Arabic chapter numbering: `第1章`, `1.1`, `1.1.1`. Avoid inventing a fourth heading level unless the department's source manuscript already uses one.

## Validation Checklist

- PDF and DOCX are both present in the same visible output directory.
- Cover pages show graduate degree wording (`硕/博士学位论文`) and the correct type: 学术学位, 专业学位, 同等学力学术型, or 同等学力专业型.
- English cover uses `A thesis/dissertation submitted to` and `Tongji University in partial fulfillment of the requirements for`.
- Margins match the reference example: A4, top/bottom 2.54 cm, left/right 3.17 cm.
- Chinese abstract heading is `摘要`; English heading is `ABSTRACT`.
- TOC starts after abstracts and includes references, appendix, acknowledgements, resume/publications when present.
- Figure captions are below figures; equations are centered with right-aligned numbers.
- References use numeric entries and the reference-section font/spacing.
- Originality statement and copyright authorization are included when required by the deliverable.
- No unresolved LaTeX references, missing images, or missing bibliography entries remain.
