# Born-Digital Triage Guide

Use this guide when performing the triage, constructing a register, or checking whether a conclusion is supported.

## What triage establishes

Triage establishes an initial review order from listing evidence. It can show that a file needs a particular next check; it cannot establish what is inside the file or authorise an archival action.

Keep three categories visible:

- **Supplied or observed metadata:** path, filename, size, modified date, supplied series, and user-provided collection context.
- **Derived signals:** extension, parent-folder context, and repeated basename within this listing.
- **Unknown:** content, actual format identity, software dependency, whether two files are byte-identical, rights, sensitivity, authenticity, and preservation condition.

## Suggested priority signals

Apply the highest relevant signal and explain the reason. Priorities sequence review; they are not risk scores or disposal recommendations.

### High

Use `high` when the extension suggests that early technical review is prudent.

- Legacy-format signals: `wpd`, `wk1`, `wk3`, `qxd`, `p65`, `fm`, `mdb`, `dbf`, `swf`, `rm`, `ra`, `dv`, `wmv`, `flv`, `sit`.
- Container, email, or processing-sensitive signals: `pst`, `ost`, `mbox`, `eml`, `msg`, `zip`, `rar`, `7z`, `exe`, `bat`.

Recommended next check:

- For a legacy signal, review DROID or Siegfried results and software dependencies before ingest.
- For container or email material, plan extraction, preserve context and original order, and consider privacy and preservation-copy handling.
- For executables or scripts, follow the institution's isolated technical-review and malware-scanning procedure. Do not execute them.

An extension is only a clue. Do not call it a confirmed format or claim that the file is damaged, obsolete, or unsafe.

### Medium

Use `medium` when:

- the same case-insensitive filename occurs more than once in the current listing; or
- size metadata is missing.

Recommended next check:

- Repeated names: compare paths, dates, sizes, and—only in a separately authorised fixity workflow—checksums or byte-level evidence. They may be versions or unrelated records.
- Missing size: collect size information before storage estimation, sampling, or transfer planning.

### Manual review

Use `manual_review` when no usable extension is present or the name cannot support even a provisional extension signal.

Recommended next check: confirm the filename and obtain trusted format-identification evidence. Do not guess a format from folder context.

### Low

Use `low` when the listing contains an extension, size, and no higher-priority signal. Say only that no immediate signal was detected from the supplied listing. Keep the file in the ordinary processing queue and verify it against accession context and collection policy.

Low does not mean safe, accessible, appraised, preserved, or ready for ingest.

## Missing facts

Check for:

- project title or collection reference;
- collection policy or collecting scope;
- accession or transfer context;
- known rights, access, or privacy restrictions;
- size for every listed file; and
- modified date for every listed file.

Record missing facts without filling them from filenames or assumptions. A collection-level restriction should be noted for later review, not applied automatically to every row.

## Listing template

The path or filename is the only required listing value. Size, modified date, and series make the triage more useful:

```csv
path,size,modified,series
records/minutes.docx,1024,2020-01-01,Minutes
legacy/notes.wpd,2048,1998-03-02,Working papers
```

Plain text with one path per line is also acceptable. Never fill missing sizes, dates, or series from guesswork.

## Register fields

Use these columns when producing a row-level register:

| Field | Meaning |
|---|---|
| `source_row` | Original listing row where available |
| `path` | Supplied or metadata-observed relative path |
| `filename` | Filename derived from that path |
| `extension` | Lowercase extension signal, blank if absent or unusable |
| `supplied_size` | Supplied or metadata-observed size; do not estimate |
| `supplied_modified_date` | Supplied or metadata-observed date; do not normalise uncertain dates silently |
| `likely_series` | Supplied series or broad parent-folder context, clearly provisional |
| `duplicate_signal` | Repeated-filename signal or `none detected from supplied listing` |
| `triage_priority` | `high`, `medium`, `low`, or `manual_review` |
| `rationale` | Evidence-based reason for the priority |
| `recommended_next_check` | One proportionate next check |

Preserve exact paths in the full register. When creating CSV intended for spreadsheet use, neutralise cells beginning with `=`, `+`, `-`, or `@` so filenames cannot be interpreted as formulas; preserve the exact raw value in JSON when one is also produced.

## Summary shape

A privacy-conscious chat summary normally needs only:

- number of listed files;
- counts by priority;
- whether project context, policy, and restrictions were supplied;
- missing facts; and
- a short next-check sequence.

Do not repeat paths or sensitive contextual notes unless doing so is necessary for the user's requested review.

## Practical next-check sequence

Adapt the order to the evidence rather than treating it as an automated workflow:

1. confirm the inventory scope and preserve the original listing;
2. gather missing sizes, dates, accession context, policy, and restriction facts;
3. obtain trusted format-identification evidence for high-priority and manual-review rows;
4. investigate repeated filenames as possible versions or separate records;
5. plan container or email extraction without losing original order or context; and
6. record authorised preservation, appraisal, access, and ingest decisions in their proper workflows.

## Required caveats

- The triage used listing data or filesystem metadata only; file contents were not inspected.
- Extensions, names, and paths are signals, not confirmed format identifications.
- Repeated filenames are not confirmed duplicates.
- No preservation, access, appraisal, deletion, migration, deduplication, transfer, or ingest action was completed.
- Final decisions remain with authorised staff and institutional policy.
