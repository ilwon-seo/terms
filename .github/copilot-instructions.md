# Copilot instructions for this repository

## Project overview

This repository is a small documentation site of mathematical and ML terms. Content lives in Markdown files, organized by the first letter of each term (for example `N/Norm (mathematics).md`, `C/Cosine similarity.md`, `B/BM25.md`).

The project is documentation-first: there is no application runtime, build system, or test suite in the repository. The main work is authoring or editing term pages so they remain accurate, clear, and consistent with the existing style.

## Repository conventions

- Keep each concept as a standalone Markdown article.
- Use the directory naming pattern `A/`, `B/`, `C/`, ... based on the term's first letter.
- Preserve the existing file naming style: title-cased concept names, usually with the topic in the filename when needed.
- Prefer concise but rigorous explanations, not marketing copy or filler.
- Use mathematical notation naturally with LaTeX-style inline and block syntax, for example `$\mathbf{v}$` and `$$\|\mathbf{v}\|_2 = \sqrt{\sum_i v_i^2}$$`.
- Keep math notation compatible with the repository's GitHub rendering and validation: do not use `\operatorname{...}`. For words or named functions in formulas, use `\text{...}` instead (for example, write `\text{sign}`).
- Use Mermaid diagrams sparingly when they support explanation.

## Required document structure

Each term page should follow the established pattern below.

```yaml
---
title: Example Term
excerpt: Short description of the concept.
category: [Terms, Related Field, Another Field]
tags: [term, concept, area]
author: ilwon-seo
date: 2026-04-26 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---
```

After the front matter, keep a consistent narrative flow:

1. `## Definition`
2. `## Calculation`
3. `## Interpretation`
4. `## Necessity`
5. `## Limitations and Alternatives`
6. `## Derived Subsequent Concepts`

This order should be preserved unless the concept genuinely requires a different structure.

## Writing guidance

- Write for an educated technical audience, not casual readers.
- Prefer accurate mathematical definitions, examples, and intuitive explanations.
- If a concept has multiple variants, describe the standard version first and note important exceptions.
- Use examples to clarify formulas, especially for ML or statistics topics.
- Keep definitions precise and avoid unsupported claims.
- When a term is related to another in this collection, mention the relationship briefly instead of duplicating content.
- Default rule: all repository term content must be written in English. This applies even when a user instruction is written in Korean or another language.
- English is the canonical language for term pages, definitions, examples, headings, and metadata in this project.
- Non-English drafts are allowed only when the user explicitly requests a translation or localization output; in such cases, the output should be clearly labeled as a translation and should not replace the canonical English version in the repository.
- Mandatory factual integrity rule: every term entry must be grounded in a real, authoritative source or established mathematical/technical fact. Do not invent definitions, formulas, examples, applications, or historical claims.
- Before writing or editing a term, verify the content against credible references such as standard textbooks, well-known academic sources, official documentation, or accepted definitions in the relevant field.
- If a fact is uncertain, ambiguous, or not supported by reliable evidence, either omit it or explicitly mark it as a qualified note rather than presenting it as a definitive claim.
- Any statement that is not directly supported by a trustworthy source must be treated as invalid for repository content.
- Avoid introducing external dependencies, frameworks, or build tooling into this repo.

## Editing expectations

- Do not change unrelated files or restructure the repository without a clear reason.
- Maintain a strong Markdown style: headings, lists, code fences, formulas, and diagrams should all be readable.
- Keep examples consistent with the rest of the repository's technical tone.
- Preserve the author/date metadata format when editing existing files.
- When adding a new term, create the appropriate letter-named directory and use a clear filename.

## Validation

Because this is a documentation-only repository, there is no automated build or test suite to run.

For a practical validation step before finishing:

- verify the file remains valid Markdown,
- verify the YAML front matter is intact,
- verify headings and math/diagram syntax are correctly formatted,
- check formulas for unsupported LaTeX macros, including `\operatorname`, and use supported alternatives such as `\text{...}`,
- confirm the new or edited content fits the existing repo conventions.

If a change adds a new term, make sure its name, directory, and structure align with the established pattern used by neighboring files.
