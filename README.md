# Scripter

Scripter is a Streamlit app for marking up narration manuscripts from DOCX files: extracting dialogue, attributing speakers, assigning colours, and exporting a highlighted HTML or PDF-ready version for performance prep.

Hosted app: [scripter.streamlit.app](https://scripter.streamlit.app)

If your source is a PDF or a DOCX using British/single speech marks, use [quotescript.streamlit.app](https://quotescript.streamlit.app) first to convert it into a suitable DOCX.

## Version Guide

- `v3` in this README means the old legacy-only workflow:
  DOCX + `quotes.txt`, manual attribution, local file-style continuation, and partial font application.
- `v4` means the current workflow:
  multiple processing modes, canonical `quotes_records` JSON for modern paths, encrypted save/restore, richer exports, and the newer UI/data model.

Legacy mode still exists in v4 for ongoing `quotes.txt` projects.

## What v4 Does

- Supports `Book` and `Script` content types.
- Supports four processing modes:
  `Updated`, `Semi-Automated`, `Experimental mode`, and `Legacy`.
- Lets you review unresolved dialogue line by line.
- Can suggest likely speakers using a local model.
- Can auto-select very high-confidence suggestions in Experimental mode.
- Preserves and reapplies speaker colours per book.
- Generates highlighted HTML, optional PDF, JSON, CSV, and other continuation exports.
- Stores encrypted non-legacy progress and can restore the latest synced book from the user key alone.

## Quick Start

### Step 0: User Key, Font, Content Type, Mode

- Enter a user key.
- Pick a font for both the Streamlit UI and exported HTML.
- Pick `Book` or `Script`.
- Pick a mode:
  - `Updated`: recommended default for fully manual review with current data structures.
  - `Semi-Automated`: local model suggestions, you confirm the speaker.
  - `Experimental mode`: same model pipeline, but high-confidence results can be auto-selected.
  - `Legacy`: for older `quotes.txt` continuation workflows only.

### Step 1: Restore or Upload

- In non-legacy modes, Step 1 does not auto-load saved progress.
- To restore a saved book, click `Load Saved Progress`.
- If you do not want to restore, just upload a DOCX and continue normally.

For a new book:

- Upload the DOCX.
- Optionally upload:
  - `Quotes Records JSON` in non-legacy modes.
  - `Quotes TXT` in Legacy mode.
  - `Speaker Colors JSON`.

If you upload only a DOCX:

- Scripter can extract the dialogue first.
- You can download the extracted file and continue immediately or return later.

### Step 2: Attribution

Behaviour depends on mode.

- `Updated`
  - Manual review of unresolved lines with context.
- `Semi-Automated`
  - The local model proposes likely speakers.
  - You can click a suggestion or type a speaker manually.
- `Experimental mode`
  - Uses the same suggestion/ranking pipeline as Semi-Automated.
  - Very high-confidence top candidates can be auto-selected in sequence.
- `Legacy`
  - Continues the older `quotes.txt`-based workflow.

Common review actions:

- Enter a speaker name.
- `skip` to leave the line unresolved.
- `undo` to revert the last change.
- `exit` to move on to colour assignment.

Additional v4 review helpers:

- frequent-speaker quick buttons
- console log panel
- suggestion buttons with confidence display
- “This is not a name” blocklist for bad candidate names in AI-assisted modes

### Step 3: Speaker Colours

- Assign colours to speakers.
- Only speakers without a chosen colour are shown first.
- `Edit Speaker Colors` lets you review all colour assignments.

Special colour behaviours:

- `None`
  - no highlight
  - unresolved text shows in dark red
- `Do Not Read`
  - used for text intentionally excluded from narration
- `Error`
  - used when detected dialogue should not actually be treated as dialogue

### Step 4: Final Output

Step 4 generates the final preview and export set.

Outputs include:

- `Download HTML File`
- `Download PDF File (takes a while!)` when PDF dependencies are available
- `Download Updated Speaker Colors JSON`
- `Download Quotes Records JSON`
- `Download Lines CSV`
- `Download Updated Quotes TXT` in Legacy mode only
- `Download Unmatched Quotes TXT` when needed

Other Step 4 actions:

- `Return to Step 2`
- `Sync Encrypted Blobs to GitHub`
- `Clear Cache for This User`

The final HTML includes:

- `Character Summary`
- `Speaker Ranking`
- `First Substantial Lines`
- highlighted manuscript body with original formatting preserved as closely as possible

## Save and Restore

### Legacy Mode

- Uses the older local-file-style continuation flow.
- Best suited only for existing `quotes.txt` projects.

### Non-Legacy Modes

Current v4 behaviour is:

- encrypted local-first storage for DOCX, quotes/progress, and colours
- optional GitHub sync for encrypted blobs
- automatic restore attempts from the user key
- manifest-based “latest book” lookup so the app can recover the saved DOCX before restoring progress

In practice:

- enter the user key in Step 0
- go to Step 1
- click `Load Saved Progress` if you want the latest synced saved book
- if not, upload the DOCX once and continue normally
- after processing, use `Sync Encrypted Blobs to GitHub` in Step 4 so future restore-by-userkey works cleanly

Important note:

- Books saved during the brief v4 transition window when manifests were not being written may need one manual DOCX upload plus one GitHub sync to seed the manifest.
- After that, later restores can work from the user key again.

## Exports and Continuation Files

Recommended continuation files by workflow:

- non-legacy workflows:
  `Quotes Records JSON` + `Speaker Colors JSON`
- legacy workflows:
  `quotes.txt` + `Speaker Colors JSON`

Additional outputs:

- `Lines CSV` for line-level downstream work
- `Unmatched Quotes TXT` for review of lines that could not be mapped back into the final HTML
- HTML and optional PDF for actual narration markup use

## Deployment Notes

- PDF export relies on WeasyPrint and its system dependencies.
- Encrypted save/restore relies on `age` being available in the runtime.
- Semi-Automated and Experimental modes rely on the local model files in `models/`.
- Torch thread limits are now applied outside macOS so VPS/Linux deployments do not oversubscribe CPU threads unnecessarily.

## Changelog: v3 to v4

This is the practical v3 -> v4 change list.

### Workflow Model

- `v3` was effectively one workflow:
  legacy DOCX + `quotes.txt`.
- `v4` keeps that as `Legacy` mode but adds three modern modes:
  `Updated`, `Semi-Automated`, and `Experimental mode`.
- `v4` adds a `Book` / `Script` content-type selector.
- `v4` uses `quotes_records` JSON as the canonical state format for non-legacy workflows.

### Save, Restore, and Storage

- Added encrypted non-legacy persistence for:
  - DOCX
  - quotes/progress
  - speaker colours
- Added local-first encrypted blob storage.
- Added optional GitHub sync for encrypted blobs.
- Added restore of the latest saved book from the user key alone.
- Added manifest-based “active/latest book” lookup so the app can fetch the saved DOCX before restoring quotes and colours.
- Added book-hash-aware speaker-colour restoration so colours are tied to the correct manuscript.
- Added more resilient restore paths and diagnostics for corrupt or malformed saved blobs.

### Attribution and Review

- Added `Updated` mode as the modern manual review path.
- Added `Semi-Automated` mode with local-model speaker suggestions.
- Added `Experimental mode` with high-confidence auto-selection.
- Added candidate ranking diagnostics and comparison blocks behind the debug gate.
- Added frequent-speaker quick buttons.
- Added “This is not a name” controls to exclude bad candidates from future suggestions.
- Added more robust undo/skip/exit handling and console logging.

### Context and Matching

- Improved DOCX italic detection and formatting interpretation.
- Improved dialogue/context matching in Step 2.
- Added conservative fuzzy fallback for long dialogue when exact matching fails.
- Improved paragraph JSON caching and restore behaviour.
- Improved handling of unmatched quotes.

### Outputs

- Added canonical `Quotes Records JSON` export for non-legacy workflows.
- Added `Lines CSV` export.
- Added optional PDF export when environment support exists.
- Kept HTML export and speaker-colour export.
- Kept `Updated Quotes TXT` as a Legacy-only continuation output.

### Fonts and UI

- Font selection now applies to the whole Streamlit UI as well as exported HTML.
- Fixed the earlier issue where font changes did not fully apply immediately on the start page.
- Added better handling for font naming and propagation.
- Added/cleaned support for:
  - `Open Dyslexic`
  - `Gentium Basic`
  - `Lexend`
- Improved button styling and general UI consistency.

### Reliability and Operational Changes

- Added a single master debug flag model.
- Synced the production file with the test file so the only intended difference is:
  `DEBUG_MODE = False` in production and `DEBUG_MODE = True` in test.
- Added VPS/Linux-specific torch thread limits while leaving macOS alone.
- Improved state restoration, cache clearing, and step-to-step transitions.

### Compatibility

- `Legacy` mode still exists for old projects.
- Existing non-legacy work can now use encrypted restore and GitHub sync.
- Projects created during the short manifest-less v4 window may need one upload-and-sync pass before userkey-only restore works again.

## Practical Notes

- Use consistent speaker names throughout a project.
- Names are normalized, so capitalization variants collapse to one speaker label.
- If you print the final HTML or PDF, ensure background colours are enabled in print settings or the highlights may disappear.
- If Step 2 context ever looks obviously wrong, export your current files, refresh, and restore or re-upload the current DOCX plus continuation files.
