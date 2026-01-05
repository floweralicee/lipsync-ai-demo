---
layout: default
title: "Prompt-Level Controls for Prosody-Aligned Facial Performance"
---

# Prompt-Level Controls for Prosody-Aligned Facial Performance

<div class="tldr">
<strong>TL;DR:</strong> Speech-driven facial animation often feels unnatural even with correct lip sync because accents hit at uniform intervals with low stress contrast. I introduce a <strong>prompt-level control layer</strong> that snaps accents to speech emphasis and adds intentional holds, without retraining the model.
</div>

<div class="nav-links">
<a href="paper.html">Paper</a>
<a href="https://floweralice.substack.com/p/when-can-we-make-a-pixar-level-movie">Substack</a>
<a href="https://twitter.com/flower_alicee">X</a>
<a href="https://linkedin.com/in/floweralice">LinkedIn</a>
</div>

---

## Results Gallery

> **Controlled setup:** Same base model, same audio, same transcript. Only the prompt/control layer differs.

<table>
<tr>
<td align="center" width="33%">
<video src="baseline.mp4" controls width="100%"></video>
<br><strong>Baseline</strong>
</td>
<td align="center" width="33%">
<video src="real_animation.mp4" controls width="100%"></video>
<br><strong>Realistic animation prompt with AI audio enhanced with Animini</strong>
</td>
<td align="center" width="33%">
<video src="withaudio.mp4" controls width="100%"></video>
<br><strong>Pixar/Disney styled animation with real voice audio prompt enhanced with Animini</strong>
</td>
</tr>
<tr>
<td align="center" width="33%">
<video src="mocha_example_baseline.mp4" controls width="100%"></video>
<br><strong>Baseline</strong>
</td>
<td align="center" width="33%">
<video src="veo3_aiaudio.mp4" controls width="100%"></video>
<br><strong>Prompt with AI audio enhanced with Animini</strong>
</td>
<td align="center" width="33%">
<video src="anime_withaudio.mp4" controls width="100%"></video>
<br><strong>Real voice audio prompt enhanced with Animini</strong>
</td>
</tr>
</table>

---

## The Problem: Even Timing

Speech-driven facial animation has a long lineage, from early audio-to-control approaches to modern neural and 3D face models conditioned on speech audio. Yet character performance in dialogue closeups frequently fails in predictable ways:

- **Timing is flat** — accents occur at near-uniform intervals
- **Stillness is missing** — no holds to make beats readable
- **Accents don't land on meaning** — motion doesn't align with stressed words
- **Constant micro-motion** — low-amplitude noise that feels "busy" but dead

The result: faces that are technically animated but feel lifeless, even when lip sync is correct.

---

## The Method: Prompt-Level Control Layer

Instead of retraining models, this work introduces instruction-level controls that translate an animator's diagnosis loop into structured constraints:

**Control Primitives:**
- **Rhythm of emphasis** — assign accents to stressed words and beat boundaries; suppress filler-word motion
- **Holds** — insert short stillness before key beats to increase contrast and readability
- **Stress contrast** — amplify motion near stressed words, reduce motion elsewhere

This fits a broader pattern in generative modeling: prompt/instruction changes and auxiliary conditioning can steer pretrained models without full retraining, as seen in instruction-following diffusion editing, prompt-to-prompt attention control, and conditional control modules such as ControlNet.

---

## Key Terms

| Term | Definition |
|------|------------|
| **Beat** | A change in intention/thought the audience should notice (new idea, realization, emotional turn) |
| **Accent** | A motion peak that marks a beat or stressed word (head nod/tilt, brow pop, lid change, jaw "hit") |
| **Hold** | Intentional stillness (or near-stillness) that creates contrast and makes the next accent readable |
| **Even timing** | Accents at near-uniform intervals with low stress/unstress contrast |
| **Micro-motion noise** | Continuous small movement that does not communicate intention |

---

## Proxy Metrics

Four metrics quantify temporal structure without claiming "objective Disney":

| Metric | Abbr. | What it measures | Goal |
|--------|-------|------------------|------|
| Accent Alignment Error | AAE | Distance between motion peaks and stress anchors | ↓ Lower |
| Even Timing Score | ETS | Coefficient of variation of accent gaps | ↑ Higher (less uniform) |
| Hold Ratio | HR | % frames below motion threshold | ↑ Higher (more stillness) |
| Contrast Ratio | CR | Motion magnitude on stressed vs unstressed words | ↑ Higher |

---

## Evaluation Protocol

**Controlled Comparison Design:**
- Same audio
- Same base generation pipeline/model
- Same sampling/seed where possible
- **Only change:** baseline instruction vs control-layer instruction

This isolation allows causal attribution: improvements come from the control layer, not confounding variables.

**Human Evaluation:** Paired A/B (baseline vs control), randomized order, identical audio, raters blinded. Report preference rate + rubric deltas with uncertainty estimates.

---

## Citation

```bibtex
@misc{chen2026prosody,
  title   = {Prompt-Level Controls for Prosody-Aligned Facial Performance},
  author  = {Alice Chen},
  year    = {2025},
  howpublished = {\url{https://floweralicee.github.io/lipsync-ai-demo}}
}
```
