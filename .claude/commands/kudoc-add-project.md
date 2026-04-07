# /kudoc-add-project

Add a new project card to the Projects section in index.html.

## Information to collect (ask if not provided in $ARGUMENTS)

1. **Title** — project name
2. **Subtitle** — one-line description
3. **Period** — e.g. "2024.03 — Present" or "2023.09 — 2024.08"
4. **Funding type** — Government-funded / Industry / University / Consortium / Collaboration
5. **Subsection** — "Document AI & Multimodal" or "Others"
6. **Description** — 2–4 sentence explanation of what the project does
7. **Role** — e.g. Research · Development · Collaboration
8. **Award/publication tie-in** — e.g. "EMNLP 2025 & CVPR 2026" (optional)

## Edits to make

Add a `<div class="proj-card">` in the correct subsection inside the Projects section:

```html
<div class="proj-card">
  <div class="proj-meta">
    <span class="proj-tag">{period}</span>
    <span class="proj-tag proj-tag--funded">{funding}</span>  <!-- or proj-tag--research -->
  </div>
  <h3 class="proj-title">{title}</h3>
  <p class="proj-subtitle">{subtitle}</p>
  <p class="proj-desc">{description}</p>
  <div class="proj-footer">
    <span class="proj-role">{role}</span>
    <!-- optional: <span class="proj-award">{award}</span> -->
  </div>
</div>
```

Tag classes:
- `proj-tag--funded` → government-funded or formal industry contract
- `proj-tag--research` → university or consortium collaboration

## After edits
- Run /kudoc-push with an appropriate commit message
