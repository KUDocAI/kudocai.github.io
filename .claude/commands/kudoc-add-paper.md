# /kudoc-add-paper

Add a new publication to index.html. Collect all required info, then make the edits atomically.

## Information to collect (ask if not provided in $ARGUMENTS)

1. **Title** — full paper title
2. **Venue** — conference name and year (e.g. ACL 2026, EMNLP 2025)
3. **Track** — MAIN / FINDINGS / INDUSTRY / etc.
4. **Oral?** — yes or no
5. **Authors** — full author list; ask which authors are KUDoc members (they get `<strong>` tags)
6. **Subsection** — "Document AI & Multimodal" or "Others"
7. **International or Domestic?**
8. **Links** — paper URL, GitHub, etc. (optional)
9. **Short description** — 1–2 sentence abstract summary

## Edits to make

### 1. index.html — Publications section
- Add a `<div class="pub-card">` in the correct subsection (Document AI / Others) and subsubsection (International / Domestic)
- Use the correct venue CSS class: `venue-acl`, `venue-emnlp`, `venue-cvpr`, `venue-naacl`, `venue-coling`, `venue-domestic`, `venue-arxiv`, or `venue-other`
- If oral, add `<span class="pub-tag-oral">Oral</span>` immediately after the venue span (no space)
- Bold KUDoc team members in `pub-authors` with `<strong>`

### 2. index.html — Milestone timeline
- Find the matching venue milestone (e.g. the `tl-item` with title "ACL 2026")
- Increment the `tl-expand-count` number by 1
- Add a new `<li>` in `tl-expand-list` with a short paper description

### 3. If no milestone exists for this venue yet
- Add a new `tl-item tl-right` with `data-type="paper"` for the new venue in chronological order

## After edits
- Run /kudoc-push with an appropriate commit message
