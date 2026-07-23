# Simplified SCUC dataset-match workflow

The recovery project now has two purpose-specific workbooks:

1. `00_scuc_dataset_match_audit.qmd` searches `/Users/D/R Working Directory`, screens for plausible SCUC Snapshot tables, compares their normalized contents with all canonical and pre-canonical references, and writes reports. It is read-only with respect to source data.
2. `01_scuc_stage_classified_copies.qmd` reads the generated manifest and prepares a dry-run copy plan. Set `dry_run <- FALSE` only after reviewing the manifest.

The proposed staging folders are:

- `06 canonical data set matches`
- `07 pre-canonical set matches`
- `08 datasets prior to pre-canonical set matches`

Copies retain their path relative to `/Users/D/R Working Directory`, so identically named files from different projects cannot overwrite one another and their provenance remains visible.

No workbook deletes, moves, or renames originals.

## Dependency and cleanup phase

After staging is verified, render `02_scuc_dependency_scan_cleanup_plan.qmd`. It scans editable source and configuration files for references to the 39 originals and writes a read-only cleanup plan to `05 dependency and cleanup reports`. Resolve the code-replacement queue before archiving originals. The workbook never authorizes deletion.

Implemented and validated a two-workbook workflow.

[00_scuc_dataset_match_audit.qmd](/Users/D/R Working Directory/SCUC Data Recovery/00_scuc_dataset_match_audit.qmd) 
discovers and compares datasets.

[01_scuc_stage_classified_copies.qmd](/Users/D/R Working Directory/SCUC Data Recovery/01_scuc_stage_classified_copies.qmd) 
stages copies after review.

[Workflow README](/Users/D/R Working Directory/SCUC Data Recovery/README_SIMPLIFIED_DATASET_MATCH_WORKFLOW.md) 
explains usage.

Current audit results:
    11 canonical matches
    9 byte-for-byte matches
    2 content-identical matches
    4 byte-for-byte pre-canonical matches
    24 earlier or unmatched Snapshot candidates requiring review
    39 total files proposed for staging

The principal review file is [scuc_dataset_match_manifest.csv](/Users/D/R Working Directory/SCUC Data Recovery/04 project inventory outputs/scuc_dataset_match_manifest.csv). The 24 uncertain files are isolated in [scuc_unmatched_snapshot_review.csv](/Users/D/R Working Directory/SCUC Data Recovery/04 project inventory outputs/scuc_unmatched_snapshot_review.csv).


Important safeguards:

- Nothing was copied, moved, renamed, overwritten, or deleted.
- The staging workbook was validated in dry-run mode.
- Source paths will be preserved beneath folders 06, 07, and 08 to prevent collisions.
- Legacy .xls files are retained for manual review rather than parsed automatically.
- Unrelated SCUC survey, Census, bond, and status-report data are screened out.
- Both QMDs now stop on errors instead of producing apparently successful partial reports.


Rendered reports are also available:

[Audit report](/Users/D/R Working Directory/SCUC Data Recovery/00_scuc_dataset_match_audit.html)

[Dry-run staging report](/Users/D/R Working Directory/SCUC Data Recovery/01_scuc_stage_classified_copies.html)


# Your next step is to gather the files safely—not delete anything yet.

Extract the corrected [workflow ZIP]
(/Users/D/R Working Directory/SCUC Data Recovery/SCUC_simplified_dataset_match_workflow.zip) 

directly into:
/Users/D/R Working Directory/SCUC Data Recovery
Preserve the included 04 project inventory outputs folder.

Open [scuc_unmatched_snapshot_review.csv]
(/Users/D/R Working Directory/SCUC Data Recovery/04 project inventory outputs/scuc_unmatched_snapshot_review.csv). 
These 24 unmatched files are the only group requiring judgment. For each, decide:
- legitimate predecessor worth preserving;
- unrelated SCUC dataset;
- obsolete copy that can eventually be archived or deleted;
- uncertain—retain until investigated.

Open [01_scuc_stage_classified_copies.qmd]
(/Users/D/R Working Directory/SCUC Data Recovery/01_scuc_stage_classified_copies.qmd) in RStudio.

Change:
dry_run <- TRUE

to:
dry_run <- FALSE

Render the QMD. It will copy the 39 identified files into:
06 canonical data set matches
07 pre-canonical set matches
08 datasets prior to pre-canonical set matches
Originals will remain untouched.

Inspect 04 project inventory outputs/scuc_dataset_copy_log.csv. 
Do not clean up originals unless every intended copy says:
  verified_copy = TRUE

After staging:
Replace uses of category 06 duplicates with the named canonical reference.
Preserve category 07 as historical predecessors, but use canonical files for analysis.
Make deletion/archive decisions only for category 08.
Back up the recovery folder before deleting anything elsewhere.

The most useful immediate action is step 2: review the 24 unmatched files. That is the remaining substantive decision; categories 06 and 07 have already been resolved objectively.

README_SIMPLIFIED_DATASET_MATCH_WORKFLOW.md
scuc_dataset_match_manifest.csv
scuc_unmatched_snapshot_review.csv


Edited 3 files

00_scuc_dataset_match_audit.qmd
01_scuc_stage_classified_copies.qmd
README_SIMPLIFIED_DATASET_MATCH_WORKFLOW.md
