# CSE 153/253 — Assignment 2

### Two Sides of the Symbolic–Audio Boundary

This project implements **two** of the four assignment tasks, chosen as deliberate opposites:

| | Task 1 | Task 2 |
|---|---|---|
| **Type** | Symbolic, *unconditioned* generation | Symbolic, *conditioned* generation |
| **What** | An LSTM learns **Raga Bhairav** and composes new melodies (sitar + tanpura + tabla) | **Music transcription**: sung audio → MIDI, a CRNN trained on MIR-1K |
| **Direction** | symbols → music | audio → symbols |

Each task is presented across the four components **Data/EDA → Modeling → Evaluation → Related work**.

---

## 📍 For graders — where the deliverables are

- **`workbook.html`** — *start here.* Open it in any browser. It is the complete, executed notebook
  for **both** tasks (read top-to-bottom; you do not need to run anything). The presentation walks
  through this notebook.
- **Generated music** (play these):
  - `symbolic_unconditioned.mid` — Task 1, the generated Raga Bhairav performance.
  - `symbolic_conditioned.mid` — Task 2, a transcription output (singing → MIDI).
- **`video_url.txt`** — link to the ~20-minute presentation video.

> The presentation is meant to be watched while following `workbook.html`.

---

## Repository layout

```
README.md                     this file
workbook.html                 ← MAIN ARTIFACT: both tasks, executed, exported (open in a browser)
workbook.ipynb                source notebook for workbook.html
symbolic_unconditioned.mid    ← Task 1 generated music
symbolic_conditioned.mid      ← Task 2 transcription output
video_url.txt                 ← presentation video link

task1_raga_bhairav/           Task 1 source & artifacts
  raga_bhairav_full.ipynb       the Task 1 notebook
  run_task1_local.py            standalone runner (reproduces the model + figures)
  training_curves_raga.png      training curves
  task1_pc_anchor.png           pitch-class distribution vs real Bhairav
  task1_numbers.txt             evaluation numbers

task2_transcription/          Task 2 source & artifacts
  task2.ipynb                   the Task 2 notebook
  task2.html                    executed HTML (reference)
  input.wav / output.wav        live demo: hummed input + resynthesized transcription

tools/merge_workbook.py       builds workbook.ipynb from the two task notebooks
archive/                      superseded earlier files
```

---

## Reproduce (optional)

`workbook.ipynb` is **Colab-targeted** (Task 2 downloads the MIR-1K dataset and uses a GPU). On
Colab: *Runtime → Run all*, then export with
`jupyter nbconvert --to html workbook.ipynb --output workbook.html`.

Task 1 alone also runs locally: `python task1_raga_bhairav/run_task1_local.py` (writes
`symbolic_unconditioned.mid` to the repo root plus the figures/numbers in `task1_raga_bhairav/`).
