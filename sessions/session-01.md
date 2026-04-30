# Session 01 — First Contact

**Date:** 2026-04-29
**Duration:** ~1 hour
**Slicer version:** 5.10.0 (macOS)
**Dataset:** `MRHead` (built-in sample T1 MRI)

---

## Goal

Install Slicer, load a real MRI, and produce a first attempt at a brain segmentation. Document everything honestly, including the parts that didn't work.

## What I did, in order

1. **Installed 3D Slicer 5.10.0** from https://download.slicer.org on macOS.
2. **Loaded the MRHead sample** via Modules → Sample Data → MRHead. Real T1 MRI, ~5 MB, loads in seconds.
3. **Explored the Red / Yellow / Green slice views.** Scrolled through axial, sagittal, and coronal planes. Got my bearings on the anatomy (eyes, brainstem, cerebellum visible).
4. **Switched to the Segment Editor module.** Source volume = MRHead.
5. **Added a segment named `Brain`.** Accidentally added a second one (`Segment_1`) — kept it for later cleanup.
6. **Tried to use the Threshold effect.** Got stuck looking for an Apply button. Realized the Apply button is inside the effect's own options sub-panel, not at the top or bottom of the Segment Editor module. (Lesson learned, won't trip on this again.)
7. **Switched to the Segmentations module** to look at the segmentation as a whole — saw "Brain", "Segment_1", "Segment_2", and a small green 3D fragment in the top-right viewport.
8. **Captured screenshots** of both states.

## What worked

- Install and data load were friction-free.
- Navigating the four-view layout felt natural after a minute or two.
- The mental model "Segmentation node contains Segments contains Effects-applied-via-Segment-Editor" clicked.

## What didn't work

- **Threshold output was too small / too partial.** The 3D render shows only a small fragment of green where I'd expected most of the brain. Likely causes (in order of suspicion):
  1. Threshold range was set too narrow — I didn't actually verify the green overlay covered the brain across all slices before clicking Apply.
  2. I may have applied Threshold with the wrong segment selected, leaking the result into `Segment_1` or `Segment_2` instead of `Brain`.
  3. I didn't run Islands → "Keep largest island" or Smoothing — the model is raw threshold output.
- **Multiple unwanted segments.** Easy to over-click "+ Add."

## Screenshots

(To be added — drop your screenshots into `screenshots/` and reference them here.)

- `screenshots/session-01-segment-editor.png` — Segment Editor view with `Brain` segment selected.
- `screenshots/session-01-3d-output.png` — Segmentations module showing the partial 3D output.

## Artifacts produced

- None exported yet (no `.stl` written). Will produce one in Session 02 after a cleaner segmentation.

## Honest takeaway

This was 80% UI navigation and 20% segmentation. That's appropriate for Day 1 — you can't do real segmentation work in a tool you haven't oriented to. Next session is where the actual work starts: a clean run of Threshold → Islands → Smoothing → Scissors → Show 3D → Export, on a single named segment, no accidents.

## What I want to remember next time

- File → Close Scene before starting fresh, so you don't accumulate junk segments across sessions.
- Verify the green overlay in the slice views *before* clicking Apply on Threshold.
- The Apply button is inside the effect panel, which appears below the effect icon row. Scroll the panel if needed.
- Effects have an order: Threshold (seed) → Islands (keep largest) → Smoothing (clean boundaries) → Scissors (manual cleanup) → Margin (shrink/grow). Generally apply in that order.
