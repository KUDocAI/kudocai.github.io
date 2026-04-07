# /kudoc-add-member

Add a new team member to the Core Researchers section in index.html.

## Information to collect (ask if not provided in $ARGUMENTS)

1. **Name** — English name (and Korean name if known)
2. **Role** — e.g. Member, Co-Lead, Team Lead
3. **Affiliation** — degree + institution (e.g. "M.S. · Korea University NLP&AI Lab")
4. **Profile URL** — personal website or lab page to fetch photo and bio from
5. **Position in grid** — who should they appear after?

## Steps

1. Fetch the provided profile URL to find:
   - Profile photo URL (prefer lab website photo; fall back to GitHub avatar)
   - Research interests
   - Links: Website, Google Scholar, GitHub, LinkedIn

2. Edit index.html — Team section:
   - Add a `<div class="team-card">` in the correct grid position
   - Use `<img class="team-avatar" src="...">` for the photo
   - Apply correct role badge class: `role-lead`, `role-pi`, `role-prof`, or plain `team-role` for Member
   - If photo is local (in `images/`), commit the image file too

3. Increment the Team Members stat counter in the hero section

4. Update CLAUDE.md — Profile photos table with the new member's photo source

5. Run /kudoc-push with an appropriate commit message
