# /kudoc-update-milestone

Recalculate and sync all milestone expand panel paper counts with the current publications list.

## Steps

1. Read index.html
2. For each `tl-item` with `data-type="paper"`, identify the venue + year (e.g. "ACL 2026", "EMNLP 2025")
3. Count how many `pub-card` elements in the publications section have a matching venue badge
4. Compare the count against the current `tl-expand-count` text in the milestone
5. Update any that are out of sync
6. Also verify that every paper listed in `tl-expand-list` has a corresponding pub-card (and vice versa) — report any gaps without auto-fixing them
7. Run /kudoc-push "Sync milestone paper counts" if any counts were changed
