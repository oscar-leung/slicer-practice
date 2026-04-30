# slicer-practice

Self-directed practice with [3D Slicer](https://www.slicer.org/) — learning medical image segmentation from a software-engineering background. This repo documents the journey honestly: what I tried, what I got working, what confused me, and what I'm doing next.

> **Status:** Beginner. Just started. This repo will grow as I do.

---

## Why this exists

I came across a "Medical Imaging & 3D Slicer Specialists" role and realized I had no idea whether I'd enjoy this kind of work. Rather than apply blind or scroll past it, I'm spending real hours in the tool, on real(ish) data, building artifacts I can show. This repo is the receipt.

I'm a technical person (software / general computing background) with no formal medical-imaging training. The goal of this repo is not to fake expertise — it's to make my actual learning curve visible.

---

## What's in here

```
slicer-practice/
├── README.md           ← you are here
├── LEARNING_LOG.md     ← rolling log of what I'm learning
├── sessions/
│   └── session-01.md   ← per-session notes (what I did, what stuck, what didn't)
├── screenshots/        ← screenshots from each session
└── exports/            ← .stl / .nrrd files I produce
```

---

## Session log (one-line summary)

| # | Date | Focus | Output |
|---|------|-------|--------|
| 01 | 2026-04-29 | Install, load MRHead sample, first contact with Segment Editor and Threshold effect | Partial brain segmentation (small region) |

(More to come.)

---

## What I can do as of the latest session

- [x] Install Slicer 5.10 on macOS
- [x] Load the built-in `MRHead` sample dataset
- [x] Navigate Red/Yellow/Green slice views (axial / sagittal / coronal)
- [x] Add a named segment to a segmentation
- [x] Find and operate the Segment Editor effects panel
- [x] Use the Threshold effect to seed a brain segment
- [x] Render a 3D model from a segmentation (Show 3D)
- [ ] Produce a clean full-brain segmentation (current attempt is partial)
- [ ] Use Islands → "Keep largest island" effectively
- [ ] Use Smoothing (median) to clean boundaries
- [ ] Use Scissors to remove non-brain tissue
- [ ] Export a segmentation to `.stl` and `.nrrd`
- [ ] Repeat the workflow on a chest CT (lungs)
- [ ] Open and segment real DICOM data (not just sample data)
- [ ] Drive Slicer from the Python Console
- [ ] Compare manual segmentation against a pretrained model (TotalSegmentator)

I'll keep this list honest as I go. Crossed-off items must have an artifact in this repo.

---

## Honest scope and caveats

- All work is on **public sample data** shipped with Slicer or from open datasets — never on real patient imaging.
- These are practice exercises, not validated clinical or research output.
- Numbers like threshold ranges are eyeballed, not principled.
- I'm learning the tool; I'm not claiming domain expertise in radiology, neuroanatomy, or oncology.

If a recruiter is reading this: please weigh this repo as evidence of *self-directed learning and tool familiarity*, not as evidence of clinical or research credentials.

---

## Tools

- 3D Slicer 5.10.0 (macOS)
- Sample datasets via Slicer's built-in Sample Data module
- Git for version-controlling notes and exports

---

## Next session plan

See [LEARNING_LOG.md](./LEARNING_LOG.md) for the rolling next-up list.
