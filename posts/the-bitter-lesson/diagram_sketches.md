# Diagram Sketches for "The Bitter Lesson Keeps Winning"

Reference these to draw PNGs. White background, hand-drawn Excalidraw style.
Save as `01_bitter_lesson_framework.png`, `02_scaling_axes.png`, `03_rl_post_training_scale.png`.

---

## Diagram 1: The Two Paths

Two-column layout with a dashed VS divider in the center.

```
            The Two Paths
  Encoding Knowledge vs. Building Meta-Methods

 ┌─────────────────────────┐     ┌─────────────────────────┐
 │  ❌ Encode What We Know │     │  ✅ Build Meta-Methods   │
 │     (red tones)         │     │     (green tones)        │
 └───────────┬─────────────┘     └───────────┬─────────────┘
             │                               │
             ▼                               ▼
 ┌─────────────────────────┐  ┊  ┌─────────────────────────┐
 │ Researcher encodes      │  ┊  │ Design general learning  │
 │ domain knowledge into   │  ┊  │ mechanisms + reward      │
 │ the system              │  ┊  │ signal                   │
 └───────────┬─────────────┘  ┊  └───────────┬─────────────┘
             │                ┊               │
             ▼               VS               ▼
 ┌─────────────────────────┐  ┊  ┌─────────────────────────┐
 │ Works well short-term,  │  ┊  │ Optimizer discovers      │
 │ feels productive        │  ┊  │ structure from data      │
 └───────────┬─────────────┘  ┊  └───────────┬─────────────┘
             │                ┊               │
             ▼                ┊               ▼
 ┌─────────────────────────┐  ┊  ┌─────────────────────────┐
 │ Hits a ceiling           │  ┊  │ Scales with compute     │
 │ Complexity blocks        │  ┊  │ No hand-crafted ceiling │
 │ scaling                  │  ┊  │                         │
 └─────────────────────────┘  ┊  └─────────────────────────┘

 Blocked by researcher            Complexity emerges from
 assumptions                      search + learning
```

**Colors:**
- Left column: red/pink fills (`#ffc9c9` bg, `#ef4444` border)
- Right column: green fills (`#b2f2bb` bg, `#22c55e` border)
- Divider: dashed gray line with "VS" text

---

## Diagram 2: Five Scaling Axes

Stacked rows, each with a colored left accent bar. Each row has a title + one-line description.

```
        Five Scaling Axes in Modern LLMs
  Each row is the same principle: more compute + general method wins

 ▌ Pre-training Scaling                                    (blue)
 │ More data + compute = better base model.
 │ Chinchilla laws still hold at frontier.
 ├──────────────────────────────────────────────────────────

 ▌ Domain Pre-training                                     (blue)
 │ Same principle, narrower data.
 │ Optimizer extracts structure > encoded ontologies.
 ├──────────────────────────────────────────────────────────

 ▌ RLHF / RLVR                                           (purple)
 │ Scalable feedback signal, not encoded preferences.
 │ Ground truth > human taste.
 ├──────────────────────────────────────────────────────────

 ▌ Inference-Time Scaling                                 (amber)
 │ More test-time compute = better answers.
 │ o1, R1, DeepSeek: search beats encoded strategy.
 ├──────────────────────────────────────────────────────────

 ▌ RL Duration Scaling                              ┌─────┐(green)
 │ Training time itself is an axis.                  │ NEW │
 │ OLMo, Qwen3, Kimi K2 show no saturation.        └─────┘
 └──────────────────────────────────────────────────────────
```

**Colors per row:**
- Rows 1-2: Blue accent (`#4a9eed` bar, `#dbe4ff` bg)
- Row 3: Purple accent (`#8b5cf6` bar, `#e5dbff` bg)
- Row 4: Amber accent (`#f59e0b` bar, `#fff3bf` bg)
- Row 5: Green accent, thicker border (`#22c55e` bar, `#d3f9d8` bg), "NEW" badge

---

## Diagram 3: RL Duration Performance Curve

X-Y chart with two curves: a dashed red line (conventional) flattening out, and a solid green curve that keeps climbing.

```
  RL Post-Training Duration as a Scaling Axis

  Performance                    ┌───────────────────────┐
  (Hard Evals)                   │ OLMo 3 32B (Nov 2025) │
       │                         │ Released — same RL job │
       │                         │ kept running           │
       │                         └───────────┬───────────┘
       │                 ┌─────────────────────────────────┐
       │                 │ OLMo 3.1 Think 32B              │
       │                 │ ~125K H100 hrs, still not sat.  │
       │                 └──────────┬──────────────────────┘
       │                            │            ↗ still
       │                ·           │          ·    climbing
       │              ·    +3wks    ·        ·
       │  - - - - · - - - - - - - - - - - - (red dashed)
       │        ·         conventional view:
       │      ·           RL is a fixed step, then ship
       │    ·
       │  ·  <── both curves start here
       │
       └──────────────────────────────────────── RL Training
                                                 Duration

  ---- Conventional assumption (red dashed)
  ──── Actual performance trajectory (green solid)

                        ┌──────────────────────────────┐
                        │ Same story at other labs:     │
                        │ • Qwen3.5 — 4-stage RL,      │
                        │   20+ task domains            │
                        │ • Kimi K2 — long-horizon RL   │
                        │ • Hybrid architectures give   │
                        │   optimizer more room         │
                        └──────────────────────────────┘
```

**Colors:**
- Conventional curve: red dashed (`#ef4444`)
- Actual curve: green solid, thicker (`#22c55e`)
- Data points (OLMo 3, OLMo 3.1): green dots with dashed annotation lines
- "Other labs" box: blue-tinted background (`#dbe4ff`)
- Axis labels: gray (`#555555`)
