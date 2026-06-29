# Tongji University Graduate Thesis Format, 2026 Reference

This reference summarizes formatting rules extracted from the Tongji graduate thesis writing reference example, titled `同济大学研究生学位论文写作参考示例`. It overrides earlier notes extracted from converted thesis drafts. Use thesis draft samples only as secondary evidence when this reference example is silent.

## Parsed Evidence

- File type: legacy Microsoft Word `.doc`.
- Title metadata: `同济大学研究生学位论文写作规范`.
- Last saved by: `学位办`.
- Last saved: 2025-05-28.
- Page count: 19.
- Apache POI confirmed all sections use A4 portrait, top/bottom 2.54 cm, left/right 3.17 cm.
- The document explicitly contains format notes for cover pages, abstracts, TOC, chapters, equations, figure captions, references, appendix, acknowledgements, and resume/publications.

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

Important caveat: the checked template version declares `degree=bachelor` by default and warns that non-bachelor degree values fall back to bachelor format. Use it as a LaTeX framework, not as the final graduate-thesis format authority.

## Page Setup

| Item | Reference value |
|---|---|
| Paper | A4 portrait, 21.0 cm x 29.7 cm |
| Top margin | 2.54 cm |
| Bottom margin | 2.54 cm |
| Left margin | 3.17 cm |
| Right margin | 3.17 cm |

Recommended LaTeX override:

```tex
\usepackage[a4paper,top=2.54cm,bottom=2.54cm,left=3.17cm,right=3.17cm]{geometry}
```

If headers/footers are used, tune `headsep` and `footskip` after visual comparison; the reference example's explicit page geometry is the stable requirement.

## Document Order

Use this order unless the user's college or submission system gives a stricter order:

1. Chinese cover.
2. English cover.
3. Cover explanation page only when producing an instructional/example document; remove it from final thesis.
4. Chinese abstract and keywords.
5. English abstract and key words.
6. Table of contents.
7. Main chapters.
8. References.
9. Appendix.
10. Acknowledgements.
11. Personal resume and academic achievements during study.
12. Originality statement.
13. Copyright authorization.

The reference example states that the uploaded system version, archive version, national library version, and CNKI version must be completely consistent.

## Chinese Cover

The example supports four Chinese cover types:

- Academic degree: `硕/博士学位论文` and `（学术学位）`.
- Professional degree: `硕/博士学位论文` and `（专业学位）`.
- Equivalent academic degree: `硕/博士学位论文` and `（同等学力学术型）`.
- Equivalent professional degree: `硕/博士学位论文` and `（同等学力专业型）`.

Chinese cover formatting notes:

| Element | Format |
|---|---|
| `硕/博士学位论文` | 隶书, 二号, bold, centered, single spacing, 0.5 line before |
| Degree type line | 隶书, 三号, bold, centered, single spacing |
| Tongji logo | 2.6 cm x 10.0 cm, centered |
| Chinese thesis title | 黑体, 二号, bold, centered, single spacing |
| Chinese field block | 仿宋, 三号, single spacing, indent 4.5 characters |
| Date line | 宋体, 三号, centered, single spacing |

Academic-degree fields:

- `姓    名：`
- `学    号：`
- `学    院：`
- `学科门类：`
- `一级学科：`
- `二级学科：`
- `研究方向：`
- `指导教师：`
- `联合培养单位：`

Professional-degree fields:

- `姓    名：`
- `学    号：`
- `学    院：`
- `学科门类：`
- `专业学位类别：`
- `专业领域：`
- `研究方向：`
- `指导教师：`
- `行业导师：`
- `联合培养单位：`

Notes:

- Two advisors may be filled according to actual circumstances.
- Industry advisor and joint training institution are optional and should be omitted or left blank when not applicable.
- Fill discipline/category fields according to the `研究生教育学科专业目录（2022年）`.

## English Cover

English cover wording observed:

```text
A thesis/dissertation submitted to
Tongji University in partial fulfillment of the requirements for
the degree of Master/Doctor of Law/Engineering/Medicine……
```

English cover formatting notes:

| Element | Format |
|---|---|
| Degree-selection text | Times New Roman, 四号, centered, single spacing, 0.5 line before |
| Submission wording | Times New Roman, 四号, centered, single spacing, 0 pt before/after |
| English title | Arial, 小二, bold, centered, single spacing |
| English field block | Times New Roman, 三号, single spacing, indent 4.5 characters |
| English date | Times New Roman, 三号, centered |

English fields:

- `Candidate:`
- `Student Number:`
- `School/Department:`
- `Categories:`
- `First-level Discipline/Degree:`
- `Second-level Discipline/Degree’s Field:`
- `Research Fields:`
- `Supervisor:`
- `Associate Supervisor:`
- `Joint Training Institution:`

## Running Spine / Archive Text

The example includes a spine/archive text line:

```text
中  文  题  目                  姓  名                   同济大学
```

Formatting notes:

- Around 5 cm spacing between the three blocks.
- 仿宋, 四号, bold, 16 pt line spacing, 0 pt before/after.

Use this only when the deliverable requires the printed spine/archive text.

## Abstracts And Keywords

Chinese abstract:

| Element | Format |
|---|---|
| Title `摘要` | 黑体, 三号, bold, centered, single spacing, 24 pt before, 18 pt after |
| Body | 宋体, 小四, fixed 20 pt line spacing, 0 pt before/after, first-line indent 2 characters |
| Keywords | 宋体, 小四, fixed 20 pt line spacing, 0 pt before/after; `关键词` bold |

English abstract:

| Element | Format |
|---|---|
| Title `ABSTRACT` | Arial, 三号, bold, centered, single spacing, 24 pt before, 18 pt after |
| Body | Times New Roman, 小四, fixed 20 pt line spacing, 0 pt before/after |
| Key words | Times New Roman, 小四, fixed 20 pt line spacing, 0 pt before/after; `Key Words` bold |

The reference example uses `Key Words:` with a space, not `Keywords:`.

## Table Of Contents

TOC title:

- `目录`: 黑体, 三号, bold, centered, single spacing, 24 pt before, 18 pt after.

TOC entries:

- 宋体, 小四, fixed 18 pt line spacing.
- 0 pt before/after.
- Page numbers right aligned.
- Include main chapters, references, appendix, acknowledgements, and personal resume/academic achievements when present.

## Main Matter

Chapter title:

- Example: `第1章 引言`.
- 黑体, 三号, bold, centered, single spacing.
- 24 pt before, 18 pt after.
- One Chinese-character space between chapter number and chapter title.

First-level heading:

- Example: `1.1 概述`.
- 黑体, 小三, single spacing.
- 24 pt before, 6 pt after.
- One Chinese-character space between number and title.

Second-level heading:

- Example: `1.1.1 线性随机结构分析`.
- 黑体, 四号, single spacing.
- 12 pt before, 6 pt after.
- One Chinese-character space between number and title.

Body paragraphs:

- Chinese: 宋体, 小四.
- English/numbers: Times New Roman, 小四.
- Justified.
- First-line indent 2 Chinese characters.
- Fixed 20 pt line spacing.
- 0 pt before/after.
- If a paragraph contains mathematical expressions, adjust line spacing as needed for expression legibility.
- The first non-heading body paragraph may use 0.7 line before when matching the reference example's visual spacing.

## Equations And Figures

Equations:

- Equation body centered.
- Equation number right aligned.

Figure captions:

- Placed below the figure.
- 宋体, 五号, centered, single spacing.
- 6 pt before, 12 pt after.
- One Chinese-character space between figure number and caption text.
- Pattern: `图3.2 非线性构形状态转移过程示意图`.

The reference example does not give a separate explicit table-caption note. For tables, keep the conventional thesis placement above tables and mirror the figure-caption typography unless a college-specific source says otherwise.

## References

References title:

- Same as chapter title: 黑体, 三号, bold, centered, single spacing, 24 pt before, 18 pt after.

Reference entries:

- Chinese: 宋体, 五号.
- English: Times New Roman, 五号.
- Hanging indent 2 characters.
- Fixed 16 pt line spacing.
- 0 pt before/after.
- Numeric bracketed entries, e.g. `[1]`.

Examples:

```text
[1] 陈**，车**，陈**. 具有***的工程结构动力优化设计[J]. 计算力学学报，2021，18（1）：74-80.
[2] 吕**，金**，吴**. 钢筋混凝土***理论与应用[M]. 上海：同济大学出版社，2022.
```

Prefer GB/T 7714 numeric style when generating references from BibTeX/BibLaTeX.

## Appendix

Appendix title:

- Same as chapter title.

Appendix body:

- Chinese: 宋体, 小四.
- English/numbers: Times New Roman, 小四.
- Justified, first-line indent 2 Chinese characters.
- Fixed 20 pt line spacing.
- 0 pt before/after.

## Acknowledgements

Acknowledgements title:

- Same as chapter title.

Acknowledgements body:

- 仿宋, 小四.
- Justified.
- Fixed 20 pt line spacing.
- 0 pt before/after.
- First-line indent 2 characters.

## Personal Resume And Academic Achievements

Section title:

- Same as chapter title.

Body:

- Chinese: 宋体, 五号.
- English: Times New Roman, 五号.
- Fixed 16 pt line spacing.
- 0 pt before/after.
- Academic-paper entries follow the same writing format as references.
- Labels such as `个人简历`, `已发表论文`, `待发表论文`, and `研究报告` are bold.

## Originality And Copyright Statements

The reference example includes:

- `同济大学学位论文原创性声明`
- `同济大学学位论文版权使用授权书`

Include these pages when required by the user's deliverable. Preserve official wording from the current school template when provided. Do not substitute older statement text if the user supplies a newer official form.

## Conversion And Delivery Notes

- When converting Word to LaTeX, extract embedded images and keep stable filenames.
- Legacy `.doc` files may include WMF/DWG/Equation objects. Convert these to PDF/PNG or redraw equations when needed for final PDF quality.
- Use raw XML for `.docx` and POI/Tika-style inspection for `.doc` when auditing format.
- Keep source LaTeX, generated PDF, and generated DOCX together in a normal visible output folder.
- After building, check file size and page count; open/read the first pages if possible.
