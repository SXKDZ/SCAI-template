# ScAI LaTeX Template

A clean, single-column LaTeX paper template for the [UCLA ScAI Lab](https://scai.cs.ucla.edu/).

## Features

- **Fonts**: Arial/Helvetica for titles and headings, Times New Roman for body text, Computer Modern for math
- **UCLA blue** section headings (#2774AE)
- **Left-aligned** title and author block
- **Light blue abstract box** with inline metadata fields (correspondence, code, data, etc.)
- **Flexible author system** with affiliations and contribution notes
- **Appendix support** with `\makeappendixtitle`, supplementary counters (S1, S2, ...), and appendix-only table of contents
- **Anti-orphan headings** via `\needspace` + `\@startsection`

## Quick Start

```latex
\documentclass[10pt]{article}
\usepackage{scai}
```

## File Structure

```
scai-template/
├── scai.sty          % The template package
├── main.tex          % Sample document
├── references.bib    % Sample bibliography
└── logo/
    ├── UCLA.pdf
    └── ScAI.png
```

## Usage

### Authors and Affiliations

```latex
\contribnote{equal}{Equal contribution.}              % auto-assigned symbol: *
\contribnote{corr}{\ddag}{Corresponding author.}      % explicit symbol: ‡

\scaiauthor{1,equal}{First Author}
\scaiauthor{1,2,equal}{Second Author}    % multiple affiliations
\scaiauthor{2}{Third Author}
\scaiauthor{1,corr}{Corresponding Author}

\affiliation{1}{University of California, Los Angeles}
\affiliation{2}{Another University}
```

`\contribnote` supports two formats:
- `\contribnote{key}{description}` — auto-assigns footnote symbols (*, &dagger;, &Dagger;, &sect;, ...)
- `\contribnote{key}{\symbol}{description}` — explicit symbol

### Metadata

```latex
\scaikeywords{Keyword One, Keyword Two}
\correspondence{Author Name}{email@example.com}   % supports multiple calls
\metadata[Date]{\today}
\metadata[Code]{\url{https://github.com/your-repo}}
\metadata[Data]{\url{https://your-data-url}}
\metadata[Website]{\url{https://your-website}}
```

### Appendix

```latex
\makeappendixtitle                          % default title: "Supplementary Materials"
\makeappendixtitle[Custom Title]            % custom title

\section{Additional Details}                % numbered A, B, C, ...
\subsection{Hyperparameters}                % numbered A.1, A.2, ...
```

`\makeappendixtitle` handles page break, counter resets (figures, tables, equations, algorithms all become S1, S2, ...), centered title, and appendix table of contents.

### Review Annotators

```latex
\annotator{alice}{red}
\annotator{bob}{blue}

\alice{This needs revision.}         % [Alice: This needs revision.] in red
\alice[r]{Remove this sentence.}     % [Alice: R̶e̶m̶o̶v̶e̶ ̶t̶h̶i̶s̶.̶] in red (strikethrough)
\alice[h]{Needs a citation.}         % [Alice: Needs a citation.] in red (highlighted)
\bob{Looks good to me.}              % [Bob: Looks good to me.] in blue
```

Use `\usepackage[final]{scai}` to silently remove all annotations from the output.

## Requirements

- pdfLaTeX
- Standard TeX Live or MiKTeX installation

