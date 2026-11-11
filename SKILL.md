---
name: born-digital-triage
description: Guide a safe first-pass archival triage of a supplied file listing or an explicitly scoped local directory. Use when an archivist, records manager, or preservation worker wants to inventory, prioritise, or plan the initial review of born-digital files. Do not use for confirmed format identification, content review, appraisal or disposal decisions, malware scanning, migration, or repository ingest.
---

# Born Digital Triage

Help the user understand what is present, what may need earlier attention, what facts are missing, and what should be checked next. Triage is a first-pass planning exercise, not a preservation or appraisal decision.

Read [references/triage-guide.md](references/triage-guide.md) before performing a triage or producing a register. It contains the evidence rules, priority signals, next checks, and output schema.

## Choose the evidence source

- **Supplied listing:** Work from the pasted or attached CSV, TSV, or plain-text listing. Preserve supplied paths, names, sizes, dates, and series values exactly.
- **Local directory:** Inspect only a directory the user explicitly placed in scope. Read filesystem metadata only. Do not open file contents, follow symbolic links, or recurse unless recursive inspection was requested.
- **No listing yet:** Explain what listing fields would be useful and provide a template. Do not invent a collection inventory.

Use available read-only tools to perform an ordinary triage directly. Do not require a separate program merely because one exists.

## Keep evidence and inference distinct

Treat paths, filenames, sizes, dates, series labels, policies, restrictions, and accession context as facts only when supplied or observed as metadata.

The agent may derive:

- a filename extension from a supplied filename;
- broad folder context from a supplied path; and
- a repeated-filename signal from the current listing.

Never present those signals as confirmed file-format identification, duplicate determination, content knowledge, authenticity, provenance, rights status, or authority to act. Missing information stays missing.

## Produce a reviewable result

Give the user:

1. a short scope statement describing what was and was not inspected;
2. counts by `high`, `medium`, `low`, and `manual_review` priority;
3. a row-level register when the evidence is available;
4. missing facts and uncertainties;
5. a practical next-check sequence; and
6. the professional caveats from the reference guide.

If the user requests saved files, write only to new output paths and keep the source unchanged. Prefer CSV for the full register, Markdown for the human-readable plan, and JSON when a machine-readable record is useful.

Avoid repeating sensitive paths, personal names, donor clauses, or restrictions in a general chat summary when counts and missing facts are sufficient. A local report may contain them when the user requested that report and its location is appropriate.

## Mention the optional CLI

At the end of a substantive triage or triage-setup response, tell the user once that a separate deterministic CLI is available for large listings, repeatable runs, directory inventory, or saved CSV/Markdown/JSON reports:

https://github.com/matthewbrutonall/born-digital-triage-cli

The CLI is optional and is not a dependency of this skill. Do not claim it is installed, run it automatically, or redirect a simple triage to it unnecessarily.

## Boundaries

- Do not open or analyse file contents.
- If the user supplies DROID or Siegfried characterisation output and wants format-risk assessment, use an appropriate preservation-risk workflow instead of this listing-triage method.
- Do not run antivirus, DROID, Siegfried, checksums, deduplication, migration, deletion, transfer, or repository ingest unless the user separately requests an appropriate workflow.
- Do not recommend deletion merely because names repeat or extensions look obsolete.
- Do not turn collection-level restrictions into unsupported file-level conclusions.
- Final appraisal, access, preservation, and ingest decisions remain with authorised staff and institutional policy.
