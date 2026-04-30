# Learning Log

A rolling, append-only log of what I'm picking up. Newest entries at the top.

---

## 2026-04-29 — Day 1

**What I learned**

- 3D Slicer ships with a Sample Data module; `MRHead` is a real T1 MRI you can load in two clicks. No DICOM hunting needed to get started.
- The four standard views are color-coded: **Red = axial, Green = coronal, Yellow = sagittal, and the 4th (top-right) is the 3D view**. Each colored slider scrubs through that plane.
- Segmentation in Slicer is a two-layer concept: a **Segmentation** node holds one or more **Segments**. A Segment is a labeled region (e.g., "Brain"). The Segment Editor module is where you actually paint/threshold them.
- The **Segment Editor** effects (Threshold, Paint, Erase, Islands, Smoothing, Scissors, Margin, etc.) are tools you click into, configure, and then **Apply**. The Apply button only appears *inside* the effect's options panel — it doesn't exist as a global button. This is non-obvious if you're used to typical desktop UI.
- Threshold is the most common "first cut" tool — you slide a min/max range until the tissue you want lights up, then Apply. For T1 brain MRI, brain tissue lives roughly in the 30–120 intensity range on the MRHead sample (eyeball, not principled).
- The **Segmentations module** (different from Segment Editor!) is where you manage display, representations (binary labelmap vs closed surface mesh), and export. "Closed surface" is the 3D mesh representation; you toggle it on to render in 3D.
- A 3D model in the top-right viewport only appears once you've enabled "Show 3D" in Segment Editor OR generated a Closed surface representation in the Segmentations module.

**What confused me**

- I created a Threshold effect and looked for an Apply button at the top or bottom of the whole Segment Editor panel. It's actually inside the effect's own options sub-panel, which appears *below* the effect icon row. I was hunting in the wrong place.
- I ended up with multiple segments (`Brain`, `Segment_1`, `Segment_2`) without meaning to — easy to accidentally hit "+ Add" twice. Cleanup with "Remove selected" works.
- The 3D view initially showed only a small piece of green near the bottom. I think this is because my Threshold range only captured part of the brain (or because Show 3D was rendering before I'd done Islands/Smoothing). Need to re-run the pipeline more carefully next session.

**Outstanding questions for next session**

- What threshold range actually captures the full brain on MRHead? Should I be using a histogram-driven choice rather than eyeballing?
- Why was the 3D output so small after Show 3D — is it the threshold, or did I segment a tiny region without realizing?
- How do I delete a segment cleanly vs. "Remove selected"?
- What's the right order: Threshold → Islands → Smoothing → Scissors? Or Smoothing last?

**Next session (Session 02) plan**

1. Reload MRHead from a clean slate (File → Close Scene first).
2. Add a single segment named `brain`.
3. Threshold with a deliberate range (try 30–120, then refine using the histogram in the effect panel).
4. Apply Islands → "Keep largest island."
5. Apply Median Smoothing, kernel 3mm.
6. Use Scissors to manually remove obvious skull/eye remnants.
7. Show 3D and capture screenshots.
8. Export to `.stl` into `exports/`.
9. Write up `sessions/session-02.md`.

Target time: 60 minutes.
