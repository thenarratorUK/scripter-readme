# Scripter

Scripter helps prepare narration manuscripts. You upload a DOCX, identify who speaks each line of dialogue, choose speaker highlight colours, and download a marked-up file for recording.

Live app: [scripter.thenarrator.co.uk](https://scripter.thenarrator.co.uk)

Changelog: [CHANGELOG.md](CHANGELOG.md)

## Quick Start

1. Open Scripter.
2. Read and accept the terms.
3. Choose the app font.
4. Choose `Book` or `Script`.
5. Choose a processing mode. If you are unsure, choose `Updated`.
6. Enter your user key.
7. Upload your DOCX.
8. Work through the speaker review if Scripter asks you to.
9. Choose speaker colours.
10. Download the finished HTML or PDF.
11. Download the progress files before you close the page.

## What You Need

You need:

- a DOCX manuscript
- a user key you will remember
- permission to upload and mark up the document

Optional files:

- `Quotes Records JSON`, for continuing a modern Scripter project
- `Speaker Colors JSON`, for reusing saved speaker colours
- `Quotes TXT`, for continuing an older Legacy project

If your source is a PDF, convert it to DOCX first. Scripter is built around DOCX input.

## User Key

Your user key is how Scripter finds your saved work. It can be a name, nickname, project code, or passphrase.

Use the same user key when you want to restore progress later. Do not share it casually, because it identifies your saved projects.

If you forget the key, Scripter cannot reliably know which saved work belongs to you.

## Book Or Script

Choose `Book` for ordinary prose manuscripts where dialogue is mixed into paragraphs.

Choose `Script` for speaker-labelled script material.

Book projects usually include a dialogue review step. Script projects normally skip most of that review and go more directly to speaker colours.

## Which Mode Should I Use?

If you are not sure, use `Updated`.

### Updated

`Updated` is the safest current workflow.

Use it when:

- you want full manual control
- the manuscript is unusual or messy
- you do not want speaker suggestions
- accuracy matters more than speed

### Semi-Automated

`Semi-Automated` shows speaker suggestions, but you still make the choice.

Use it when:

- the book has repeated speakers
- you want help moving faster
- you still want to confirm each speaker yourself

You can click a suggestion, type a different speaker, skip the line, undo the last change, or move on to colours.

### Experimental Mode

`Experimental mode` is the fastest option when it works well.

It can accept very confident speaker matches automatically and pause on lines that still need review.

Use it when:

- you want the quickest route through a clear manuscript
- you are willing to check the final results carefully
- the speaker context is fairly obvious

If it pauses or seems slow, give it a moment. It may be working through several lines.

### Legacy

`Legacy` is only for older projects that already use a `quotes.txt` workflow.

Do not choose Legacy for a new project unless you specifically need that older file format.

## Step 1: Restore Or Upload

You have two ways to continue work.

To restore saved work:

1. Enter the same user key as before.
2. Click `Load Saved Progress`.
3. If Scripter asks for the DOCX as well, upload the same source DOCX you used before.

To start or continue from files:

1. Upload the DOCX.
2. Optionally upload a `Quotes Records JSON` file.
3. Optionally upload a `Speaker Colors JSON` file.
4. For Legacy projects only, optionally upload a `Quotes TXT` file.
5. Click `Start Processing`.

If Scripter finds saved progress for the uploaded DOCX, it may ask whether to load that progress or wipe it and start fresh. Choose carefully. Wiping is for when you deliberately want to restart that project.

## Extracted Dialogue Files

When you upload a fresh DOCX, Scripter extracts the dialogue.

Download the extracted records if the app offers them. They are useful continuation files if you need to pause, move device, or recover later.

For modern projects, the important continuation file is:

```text
Quotes Records JSON
```

For older Legacy projects, the continuation file is:

```text
Quotes TXT
```

## Step 2: Review Dialogue

This step appears for Book projects.

Scripter shows one unresolved line at a time. Your job is to tell it who is speaking.

For each line, you can:

- type a speaker name and submit it
- choose a suggested speaker, if suggestions are available
- skip the line for now
- undo the last saved change
- move on to speaker colours

Speaker names should be consistent. `John`, `JOHN`, and `Jon` may be treated as different speakers, so pick one form and stick to it.

Frequent-speaker buttons appear after a speaker has been used enough times. They are there to save typing.

If you are unsure about a line, skip it rather than guessing. Unresolved dialogue is easier to spot later than a confident wrong label.

## Step 3: Speaker Colours

Choose a highlight colour for each speaker.

Scripter shows speakers that still need colours first. Use `Edit Speaker Colors` if you want to review or change all colours.

`None` means that speaker will not be highlighted.

Unresolved dialogue is shown in dark red so you can find it before recording.

Before continuing, check:

- major speakers have distinct colours
- minor speakers are still readable
- unresolved lines are either deliberately unresolved or fixed

## Step 4: Final Output

Step 4 creates the marked-up output.

The preview can include:

- a character summary
- speaker ranking
- first substantial lines
- highlighted manuscript body

Download the files you need before closing the page.

Common downloads:

- `Download HTML File`
- `Download PDF File (takes a while!)`
- `Download Updated Speaker Colors JSON`
- `Download Quotes Records JSON`
- `Download Lines CSV`
- `Download Unmatched Quotes TXT`, if anything could not be safely matched
- `Download Updated Quotes TXT`, in Legacy mode only

If something looks wrong, use `Return to Step 2`, fix the issue, then come back to Step 4 and download again.

## Save And Restore

For the cleanest pause-and-return workflow:

1. Reach Step 4 if you can.
2. Download `Quotes Records JSON`.
3. Download `Speaker Colors JSON`.
4. Download the HTML or PDF output if it is usable.
5. Click `Sync Encrypted Blobs to GitHub` if that button is available.
6. Next time, use the same user key and click `Load Saved Progress`.

If restore does not find everything automatically, upload the original DOCX and the saved JSON files manually.

Keep the original DOCX unchanged while you are working. If the source text changes after you create continuation files, matching may become less reliable.

## Unmatched Quotes

`Unmatched Quotes TXT` means Scripter reviewed or extracted dialogue that it could not safely place back into the final marked-up output.

Common reasons:

- the DOCX has unusual formatting
- quotation marks changed during conversion
- the same line appears more than once
- the source DOCX was edited after the continuation file was created
- a line is split strangely across paragraphs or styles

Do not ignore the unmatched file. Open it, check the listed lines, and decide whether the final output is still safe to use.

## Safe Working Habit

1. Keep the original DOCX.
2. Use `Updated` unless you have a reason to choose another mode.
3. Save progress files from Step 4.
4. Check the final HTML or PDF before recording.
5. Keep the progress JSON files with the project until the recording is finished.

## If Something Goes Wrong

- If restore does not work, use the same user key and upload the original DOCX again.
- If colours look wrong, return to the colour step and download fresh colour JSON afterwards.
- If the wrong speaker appears repeatedly, undo where possible or correct the speaker name before final output.
- If many quotes are unmatched, check whether the DOCX changed after the continuation file was made.
- If the PDF takes a while, wait before clicking again. Large manuscripts can be slow to export.
- If the PDF fails, download the HTML file first so you still have a marked-up output.

## Privacy And Upload Rights

The app terms explain storage and usage before you upload anything.

Only upload documents you have the right to process. Do not upload someone else's manuscript unless you have permission.

During the Scripter workflow, generative AI is not used to write, rewrite, or mark up your manuscript. You stay in charge of speaker names, colours, and the final check.

## What Scripter Is Not

Scripter prepares a marked-up narration manuscript. It does not replace a human check of speaker names, context, formatting, or final recording notes.
