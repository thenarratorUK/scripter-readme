# Scripter Changelog

This changelog uses hindsight version numbers.

`v3.0` is the last pre-Codex, legacy-only live version. `v4.0` is the first version with the newer mode selection, including Experimental mode. Later numbers group related production changes from the commit history rather than formal releases that existed at the time.

## v4.33 - Output Fidelity Fixes

Date range: 18 April 2026

- Preserved HTML line breaks more reliably when highlighting quotes.
- Preserved emphasis styling, including italic text, in generated dialogue HTML.
- Improved final-output fidelity for manuscripts where formatting matters to the read.

Relevant commits: `319eba2`, `b0a407a`

## v4.32 - Frequent Speaker And Extraction Fixes

Date range: 18 April 2026

- Restored frequent-speaker button state when saved progress is loaded.
- Counted already assigned speakers correctly when rebuilding frequent-speaker buttons.
- Fixed duplicate dialogue context matching.
- Fixed contraction handling in dialogue extraction.
- Recovered older saved model-source blobs that did not have a manifest.

Relevant commits: `0dcd480`, `a93ec85`, `a65c655`, `236e28b`, `2bd32ce`

## v4.31 - Public UI Polish

Date range: 14-17 April 2026

- Added the terms-and-conditions gate on the entry page.
- Added a favicon and fixed the app header website link.
- Reduced browser autofill interference on the user-key box.

Relevant commits: `d3de225`, `48ce71e`, `f7b6ef4`, `459bf21`, `f4e0b14`

## v4.30 - Active Book Restore And Branding

Date range: 11-13 April 2026

- Fixed active-book restore manifest handling.
- Improved persistent progress reload handling.
- Made the brand header responsive.
- Updated the Scripter title and entry-point naming.
- Added support tooling for quotes-records editing and model-source export.
- Capped some internal review/source exports so they stay manageable.

Relevant commits: `310c13b`, `10af3fb`, `57aee77`, `6a9ef5a`, `696b3a9`, `10db2f5`, `da63ad3`, `c960696`, `6f4f1f2`, `815dcc7`

## v4.21 - Restore, Matching, And Cache Stability

Date range: 10-11 April 2026

- Restored non-legacy autosave before Step 4.
- Persisted Experimental-mode auto-attribution progress per line.
- Moved paragraph caches to temporary storage.
- Fixed Step 2 context occurrence indexing when the match starts after the beginning of the paragraph list.
- Fixed restore ordering so the most recently updated book is preferred.
- Stabilised and pruned dialogue resolver cache keys.
- Fixed straight-quote dialogue extraction.
- Added single-quote dialogue support for production workflows.
- Stopped writing non-legacy working artefacts as loose local files.
- Hid duplicate blue and pink colour options from the colour dropdowns.

Relevant commits: `b09a498`, `140a498`, `4f40d9f`, `3175170`, `51d6aa9`, `b429afe`, `9a087d0`, `4bbb0d0`, `319d046`

## v4.20 - Local-First Encrypted Storage

Date range: 10 April 2026

- Switched modern-mode storage to local-first encrypted blobs.
- Added GitHub sync for pending encrypted blobs.
- Restored manual saved-progress loading after an auto-load experiment proved too aggressive.
- Limited Torch thread usage on Linux/VPS deployments to avoid CPU oversubscription.
- Re-hid candidate diagnostics behind the maintainer diagnostics gate.

Relevant commits: `ed39c0e`, `107d53d`, `91348fa`, `81567c2`, `d572ad3`, `f524031`

## v4.11 - Restore Resilience And Review Controls

Date range: 9 April 2026

- Added restore-by-userkey through an encrypted manifest.
- Added fallbacks for large encrypted blobs and base64 decryption edge cases.
- Improved missing-binary guidance for encrypted storage.
- Added controls for rejecting bad speaker-name candidates.
- Preserved speaker colours when a modern restore colour blob fails.
- Improved state persistence and colour restore reliability.
- Hardened Step 4 encrypted manifest recovery.
- Fixed early-load paragraph-cache errors.
- Fixed console-log restoration after cache clear.

Relevant commits: `99a1c4c`, `26ae6a8`, `a7b563e`, `9facee1`, `ce0523f`, `0cd3135`, `671f42b`, `9cdcf49`, `0d19f52`, `c880378`, `eb4efe0`, `7e6e0f9`

## v4.10 - Encrypted Persistence

Date range: 9 April 2026

- Added encrypted persistence for modern-mode Step 4 data.
- Added encrypted GitHub blob storage for modern progress.
- Added a single diagnostics switch for maintainer-only troubleshooting.
- Gated bulk context tools and diagnostics so ordinary users do not see maintenance controls.

Relevant commits: `aa01f41`, `8ed9a30`, `7cfb52d`, `d62fa8d`

## v4.03 - Experimental Scoring Fix

Date range: 8 April 2026

- Fixed the Experimental-mode auto-pick threshold so it uses the raw top score.
- Updated Step 4 README coverage for the then-current workflow.

Relevant commits: `1e67580`, `46fdf2c`

## v4.02 - Context And Formatting Improvements

Date range: 8 April 2026

- Constrained context matching to quoted or italic dialogue.
- Added a conservative fuzzy fallback for long context matching.
- Improved cascaded italic detection when building context HTML.
- Fixed logo rendering after Streamlit restarts.
- Suppressed noisy Streamlit watcher traceback output.
- Cleaned up dialogue matching in the Streamlit flow.

Relevant commits: `640fcf9`, `4a0d2a8`, `e51438b`, `d0734bb`, `2f94f3d`, `8ce44a0`

## v4.01 - Semi-Automated Model Improvements

Date range: 7-8 April 2026

- Added the local speaker-ranking model files.
- Added Semi-Automated speaker suggestions.
- Improved candidate generation using nearby context, named-entity information, verb boosts, and stateful candidate pools.
- Added `NotDialogue` to the model candidate pool.
- Improved ranking input formatting and context budgets.
- Batched and cached ranking work for better speed.
- Tightened fallback criteria so the model does less unnecessary work.
- Removed noisy candidate-generation details from the normal public UI.

Relevant commits: `c80e106`, `dbda7fd`, `8dc68ee`, `239317c`, `3e667ee`, `a287a40`, `6bb2547`, `e1105ca`, `a9f76fd`, `5c4739d`, `6ecbd52`, `82a4a64`, `fbfc7ee`, `f2c7013`

## v4.00 - Mode Selection And Experimental Mode

Date range: 7 April 2026

- Added the mode selector to the first page.
- Added the modern mode set: Experimental mode, Semi-Automated, Updated, and Legacy.
- Added the Book/Script content-type selector.
- Normalised speaker-colour filename handling through the user-key helper.

Relevant commits: `e2a5018`, `8594b9f`

## v3.11 - Context Lookup And Continuation Exports

Date range: 2-3 April 2026

- Fixed review-selection and index-migration regressions after the structured-records work.
- Exported canonical quote records from Step 4.
- Fixed occurrence targeting when lookup starts part-way through a document.
- Added the ability to populate context for quote records.
- Prevented context lookup misses from cascading too aggressively.
- Removed an obsolete canonical-map download from Step 4.

Relevant commits: `77300a6`, `0a2fc35`, `c8aacfd`, `624422e`, `b25ebdc`, `be695d3`, `3f774b1`

## v3.10 - Structured Quote Records Foundation

Date range: 2 April 2026

- Refactored the review flow around canonical `quotes_records` state.
- Added migration support from older line-based quote state.
- Laid the foundation for the modern `Quotes Records JSON` continuation file.

Relevant commits: `5fca485`, `8c7c1e6`

## v3.01 - Font And Header Improvements

Date range: 1 April 2026

- Fixed Open Dyslexic font selection propagation.
- Applied the selected font to Streamlit UI components as well as exported HTML.
- Added and refined the font preview list.
- Added the public README link to the app header.
- Fixed start-page font-selection lag.

Relevant commits: `2818bff`, `189520a`, `e8b2444`, `5deb948`, `b45c0af`, `2a75600`, `ecabc91`

## v3.00 - Legacy Baseline

Date range: before 1 April 2026

- Legacy-only workflow.
- DOCX plus `quotes.txt` continuation files.
- Manual speaker attribution.
- Speaker colour export and highlighted manuscript output.
- Local progress files tied to the user key.
