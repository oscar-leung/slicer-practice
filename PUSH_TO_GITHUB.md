# Pushing this repo to GitHub

The repo is already initialized with an initial commit on `main`. You just need to put it on GitHub.

## Option A: with the GitHub CLI (`gh`) — fastest

If you have `gh` installed and logged in:

```bash
cd ~/path/to/slicer-practice   # wherever you put the folder on your Mac
gh repo create slicer-practice --public --source=. --remote=origin --push
```

Done — your repo is live at `https://github.com/<your-username>/slicer-practice`.

## Option B: GitHub website + plain git

1. Go to https://github.com/new
2. Repository name: `slicer-practice`
3. Public.
4. **Do not** initialize with a README, .gitignore, or license (you already have those).
5. Create the repository.
6. Copy the URL it gives you (e.g., `https://github.com/<you>/slicer-practice.git`).

Then in your terminal:

```bash
cd ~/path/to/slicer-practice
git remote add origin https://github.com/<your-username>/slicer-practice.git
git push -u origin main
```

## After it's live

1. Add the repo URL to your LinkedIn profile (Featured section, or under Experience as a project).
2. When you fill out the Helix / Handshake survey, paste the GitHub URL into the **portfolio** field.
3. Be honest in any follow-up about scope: "self-directed practice repo, started [date], focused on learning the Slicer toolchain from a software-engineering background."

## Adding screenshots to the repo

The screenshots from your Slicer sessions don't live in this scaffolded folder yet — you'll need to drop them in manually. From your Mac:

```bash
# Copy your two screenshots from Desktop (or wherever) into the repo
cp ~/Desktop/slicer-screenshot-1.png ~/path/to/slicer-practice/screenshots/session-01-segment-editor.png
cp ~/Desktop/slicer-screenshot-2.png ~/path/to/slicer-practice/screenshots/session-01-3d-output.png

cd ~/path/to/slicer-practice
git add screenshots/
git commit -m "Add session 01 screenshots"
git push
```

Then update `sessions/session-01.md` so the image references actually render:

```markdown
![Segment Editor](../screenshots/session-01-segment-editor.png)
![3D output](../screenshots/session-01-3d-output.png)
```

Commit and push that change too.

## Per-session workflow going forward

After each Slicer session:

```bash
cd ~/path/to/slicer-practice
# Add screenshots to screenshots/
# Add any .stl exports to exports/
# Write sessions/session-NN.md
# Update LEARNING_LOG.md (newest entry on top)
# Update README.md status table

git add -A
git commit -m "Session NN: <one-line summary>"
git push
```

That's it. Consistency matters more than perfection — a repo with 6 honest sessions over 6 weeks beats a repo with 1 polished one.
