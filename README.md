# Scripter

Scripter helps prepare narration manuscripts. You upload a DOCX, tell Scripter who speaks each line of dialogue, choose highlight colours for the speakers, and download a marked-up HTML or PDF version for recording.

Live app: [scripter.thenarrator.co.uk](https://scripter.thenarrator.co.uk)

Changelog: [CHANGELOG.md](CHANGELOG.md)

## What You Need

You need:

- a DOCX manuscript
- a user key
- permission to upload and mark up the document

Optional files:

- a `Quotes Records JSON` file, if you are continuing a modern Scripter project from a downloaded progress file
- a `Speaker Colors JSON` file, if you want to reuse saved speaker colours
- a `Quotes TXT` file, if you are continuing an older Legacy project

If your source is a PDF, convert it to DOCX before using Scripter. The app is built around DOCX input.

## User Key

Your user key is the name Scripter uses to find your saved work. It can be a username, nickname, or passphrase.

Use the same user key when you want to restore progress later. Do not share it with anyone else, because it identifies your working files.

## First Page

On the first page:

1. Read and agree to the terms and conditions.
2. Choose a font for the app and exported HTML.
3. Choose whether the document is a `Book` or a `Script`.
4. Choose a processing mode.
5. Enter your user key and continue.

`Book` is for ordinary prose manuscripts where dialogue is mixed into paragraphs.

`Script` is for speaker-labelled script material. Script projects normally skip the dialogue-attribution review step and go straight to speaker colours.

## Which Mode Should I Use?

If you are not sure, use `Updated`.

### Experimental Mode

Experimental mode is the fastest mode when it works well.

It uses the local speaker-suggestion model and can automatically accept very high-confidence speaker matches. It may pause for a few seconds per line while it works, and if several lines are auto-attributed in a row it can look as if nothing is happening for longer than that.

Use this mode when:

- you want the most automation
- the manuscript has fairly clear speaker context
- you are comfortable checking the results before using the final output

You can still manually correct lines that are not auto-attributed.

### Semi-Automated

Semi-Automated mode gives suggestions but leaves the decision to you.

For each unresolved line, Scripter shows likely speakers. You can click a suggestion, type a different name, skip the line, undo the last change, or exit to colour assignment.

Use this mode when:

- you want help, but do not want Scripter to auto-select speakers
- the manuscript has many repeated speakers
- you want a more cautious workflow than Experimental mode

### Updated

Updated mode is the modern manual workflow.

It uses the current `Quotes Records JSON` structure, current save/restore behaviour, and current exports, but it does not use the local model to suggest speakers.

Use this mode when:

- you want maximum manual control
- the manuscript is unusual or messy
- you do not want to wait for speaker suggestions

### Legacy

Legacy mode is for old projects that were already using `quotes.txt`.

Do not choose Legacy for a new project unless you specifically need the older `Quotes TXT` workflow.

## Step 1: Restore or Upload

To restore saved work, enter the same user key on the first page, then click `Load Saved Progress`.

To start or continue from files:

1. Upload the DOCX.
2. Optionally upload a continuation file.
3. Optionally upload a speaker-colours file.
4. Click `Start Processing`.

If you upload only a DOCX, Scripter extracts the dialogue first. You can download the extracted continuation file, then either continue immediately or save it for later.

If Scripter finds saved progress for the uploaded DOCX, it asks whether to load that progress or wipe it and start fresh.

## Step 2: Review Dialogue

This step appears for Book projects.

Scripter shows unresolved dialogue one line at a time. For each line, enter the speaker name or use one of the available actions:

- `Submit` saves the name you typed
- `Skip` leaves the line unresolved
- `Undo` reverses the last saved attribution
- `Exit` moves on to speaker colours

In Semi-Automated and Experimental modes, Scripter may also show speaker suggestion buttons.

Frequent-speaker buttons appear once a speaker has been assigned often enough. They are there to make repeated speakers faster to select.

## Step 3: Speaker Colours

Choose a highlight colour for each speaker.

Scripter shows speakers that still need colours first. Use `Edit Speaker Colors` if you want to review or change all speaker colours.

`None` means the speaker will not be highlighted. Unresolved dialogue is shown in dark red so it is easy to spot before recording.

## Step 4: Final Output

Step 4 creates the marked-up output.

The HTML preview includes:

- character summary
- speaker ranking
- first substantial lines
- highlighted manuscript body

Downloads can include:

- `Download HTML File`
- `Download PDF File (takes a while!)`
- `Download Updated Speaker Colors JSON`
- `Download Quotes Records JSON`
- `Download Lines CSV`
- `Download Updated Quotes TXT`, in Legacy mode only
- `Download Unmatched Quotes TXT`, when Scripter could not safely match everything back into the final HTML

If something looks wrong, use `Return to Step 2`, make corrections, then come back to Step 4.

## Save And Restore

Modern modes save encrypted progress for the DOCX, dialogue records, and speaker colours.

For the cleanest restore later:

1. Finish or pause at Step 4.
2. Click `Sync Encrypted Blobs to GitHub`.
3. Next time, use the same user key and click `Load Saved Progress`.

If a project was created during an older transition period, Scripter may need you to upload the DOCX once before it can restore everything automatically. After that, syncing again should make future restores cleaner.

Legacy mode uses the older local progress and `quotes.txt` style workflow.

## If You Get Unmatched Quotes

`Unmatched Quotes TXT` means Scripter extracted or reviewed dialogue that it could not safely locate in the final HTML.

Common causes include:

- the DOCX has unusual formatting
- quotation marks changed during conversion
- the same line appears more than once in similar contexts
- the source text was edited after the continuation file was created

Review the unmatched file before relying on the final output.

## Privacy And AI

The app terms explain the storage and usage position before you upload anything.

In short:

- uploaded documents and markup may be stored for future internal learning and training
- stored material is not made accessible outside The Narrator's internal training workflow
- generative AI is not used while marking up or training
- by uploading a document, you confirm you have the right to do so

## Tips

- Use `Updated` for the safest current workflow.
- Use `Semi-Automated` when you want suggestions but still want to confirm each speaker.
- Use `Experimental mode` when speed matters and you are happy to check the result carefully.
- Download `Quotes Records JSON` and `Speaker Colors JSON` from Step 4 if you want portable continuation files.
- Keep the original DOCX unchanged while working on a project.
