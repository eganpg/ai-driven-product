---
name: brand-apply
description: >
  Applies company branding to any document. Use this skill whenever the user says
  "apply branding", "brand this doc", "make this on-brand", or similar. Reads brand
  guidelines from brand/brand-guidelines.md automatically. Accepts documents via
  paste, file path, or Google Drive link. Outputs a branded, reformatted document.
---

# Brand Apply Skill

## Overview

This skill applies company brand standards to any document. It reads guidelines from
`brand/brand-guidelines.md`, accepts a source document from the user, and produces
a branded output that applies typography structure, color notes, logo placement,
and header/footer standards.

---

## Step 0: Load Brand Guidelines

Silently read `brand/brand-guidelines.md` before doing anything else.

If any section is marked TBD, note it internally — you will flag these to the user
at the end rather than blocking the process.

---

## Step 1: Document Intake

Ask:

> "Got it — I've loaded the brand guidelines. Please share the document you'd like
> branded:
>
> - Paste the content directly here
> - Provide a file path (e.g. `sop-docs/my-doc.md`)
> - Share a Google Drive link and I'll read it
>
> Also — what type of document is this? (e.g. SOP, report, proposal, memo)"

---

## Step 2: Confirm Scope

Once the document is received, confirm what will be applied:

> "Here's what I'll apply from the brand guidelines:
> - **Typography** — heading hierarchy, font notes, spacing
> - **Colors** — flag where color should be applied (e.g. headings, callouts)
> - **Logo** — note placement in header or cover
> - **Header & Footer** — apply standard layout and content
>
> Anything you'd like to skip or adjust before I proceed?"

Wait for confirmation or adjustments.

---

## Step 3: Apply Branding

Reformat the document applying all confirmed brand elements:

- Structure headings according to typography guidelines
- Add header and footer per brand standards
- Note logo placement (e.g. `[LOGO — top left, header]`)
- Flag color application inline (e.g. `[PRIMARY COLOR — section heading]`)
- Preserve all original content — do not rewrite or summarize

---

## Step 4: Output

Produce the branded document as a clean markdown file.

At the end, include a **Branding Notes** section listing:
- Any TBD items in the guidelines that could not be applied
- Any color or logo placements that require manual application in Word/Google Docs
- Suggested filename in kebab-case (e.g. `quarterly-conversations-sop-branded.md`)

Say:
> "Here's your branded document. Note that font and color changes will need to be
> applied manually in Word or Google Docs using the brand guidelines as a reference.
> Once pandoc or a branded .docx template is available, this can be automated."

---

## Key Behaviors

- **Always read brand guidelines first** — never apply branding without loading `brand/brand-guidelines.md`
- **Preserve content** — only reformat, never rewrite
- **Flag TBDs** — don't block on incomplete guidelines, flag them at the end
- **Be explicit about manual steps** — clearly note what requires Word/Google Docs to finalize
- **Google Drive** — use the Google Drive tool if a link is provided; if unavailable, ask the user to paste content
