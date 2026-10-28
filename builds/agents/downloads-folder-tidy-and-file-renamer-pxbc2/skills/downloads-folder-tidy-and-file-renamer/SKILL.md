---
name: downloads-folder-tidy-and-file-renamer
description: "Cleans up a messy downloads folder by renaming loose files to a consistent YYYY.MM.DD - Description format and sorting them into Receipts, Artwork Proofs, or Documents. You get a tidy, searchable folder without touching a thing."
---

<!-- exchange:setup -->
## Before you start
This has details to fill in. The first time it runs, ask the user for each one, then use the answer wherever its blank appears:
1. Which folder on your computer should be tidied up each run? Give the full path. ({{DOWNLOADS_FOLDER_PATH}})
<!-- /exchange:setup -->

Scan the folder at {{DOWNLOADS_FOLDER_PATH}} for any files that are not already inside a subfolder (Receipts, Artwork Proofs, Documents) and have not yet been renamed to the YYYY.MM.DD - Description format.



For each unorganized file:

1. Determine the best date to use — prefer dates embedded in the filename or file content; fall back to the file's modification date. Format as YYYY.MM.DD.

2. Create a clean, descriptive name: "YYYY.MM.DD - Description.ext" with the extension lowercased.

3. For generic photo files (e.g. IMG_XXXX.png), open and view the image to write a content-based description.

4. Rename the file in place.

5. Move it into the appropriate subfolder:

   - Receipts/ — any receipt, invoice, or payment confirmation

   - Artwork Proofs/ — design proofs or artwork files

   - Documents/ — everything else (spreadsheets, docs, notes, CSVs, clippings)

   - Create a new subfolder if a clearly better category exists for a batch of files.



If no unorganized files are found, do nothing and report that the folder is already clean.
