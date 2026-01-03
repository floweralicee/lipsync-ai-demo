---
layout: default
title: "Animini: Emphasis-Controlled Facial Acting"
---

# Emphasis-Controlled Facial Acting (No Model Training)

<div class="tldr">
<strong>TL;DR:</strong> I improve AI facial acting <strong>without retraining the model</strong> by treating prompting as a <strong>model-agnostic control layer</strong> that maps speech emphasis to <strong>accents + holds</strong>, reducing "even timing" and making performance more intentional.
</div>

<div class="nav-links">
<a href="#results-gallery">Results Gallery</a>
<a href="#key-results-v1">Key Results</a>
<a href="https://floweralice.substack.com/p/when-can-we-make-a-pixar-level-movie">Substack</a>
<a href="#citation">Citation</a>
<a href="https://twitter.com/flower_alicee">X</a>
<a href="https://linkedin.com/in/floweralice">LinkedIn</a>
</div>

---

## Results Gallery

> **Controlled setup:** same base model + same audio + same transcript. Only the prompt/control layer differs.

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

## Key Results (v1)

- **Blind A/B (N=39 working animators):** **92.3%** preferred Animini prompts for timing + emphasis placement.
- **Metric:** **78%↓ “even timing” score** on **1,000 generations** (same model/audio; only prompt changes).
- **Traction:** RedNote **16k impressions**, **100 users** week one; **X% returned within 3 days**.

| Condition | Even Timing Score ↓ | Human Preference ↑ | N generations |
|---|---:|---:|---:|
| Baseline prompt | X | — | 1000 |
| Animini prompt | X (**78%↓**) | **92.3%** | 1000 |

---

## Definitions

- **Even timing:** motion accents occur at near-uniform intervals with low contrast between stressed and unstressed words.
- **Accent:** a localized peak in motion (head/face/eyes/brows) that marks emphasis.
- **Hold:** intentional stillness that increases readability and sets up the next accent.
- **Contrast:** stressed vs unstressed words differ meaningfully in motion magnitude/changes.
- **Emphasis track:** word timestamps + emphasis score over time (from prosody and/or transcript heuristics).
- **Pixar-style acting (operationalized):** rhythm of emphasis + contrast + intentional holds (not constant motion).

---

## Controls

### Timing Control (Emphasis + Holds + Contrast)
- **What I change:** X  
- **Knobs:** emphasis strength (X), hold duration (X), head energy (X)
- **Demos:** link to examples above / add more here

### (Optional) Emotion / Intention Control
- **Definition:** X  
- **Demos:** X

### (Optional) Camera / Shot Control
(Only include if you truly have it)
- **Definition:** X  
- **Demos:** X

---

## Evaluation Protocol

### Controlled Comparison Setup
- Same base model
- Same audio + transcript
- Same settings (seed when available / multiple seeds otherwise)
- Only change: baseline prompt vs Animini structured prompt

### Human Study (Blind A/B)
- **Participants:** 39 working animators
- **Design:** blind randomized A/B (raters don’t know which is which)
- **Question asked:** “X”
- **Outcome:** 92.3% preferred Animini prompts

---

## Metrics

### Even Timing Score (primary)
- **Definition:** penalizes near-uniform spacing between motion accents.
- **Accent peak extraction:** X (e.g., head rotation velocity peaks / manual timestamps / motion magnitude peaks)
- **Result:** 78%↓ on 1,000 generations.

### Optional (v2 / planned)
- **Accent alignment:** % motion peaks within ±X ms of emphasized words
- **Contrast ratio:** mean motion magnitude on stressed vs unstressed segments
- **Hold coverage:** % time under motion threshold + distribution of hold durations

---

## Ablations (Causality Checks)

Ablation = remove one component to test what actually causes improvement.

- Remove holds → X
- Remove emphasis control → X
- Head-only vs head+face coupling → X

---

## Animation-as-Data (Pixar/Disney analysis background)

Performance as measurable behavior, instead of pure taste.

- **Scenes analyzed:** ~1,250
- **Frames annotated:** ~1,840,000
- **Artifact:** acting-event taxonomy + annotation protocol

### Acting Event Taxonomy (v1)
- **Blink triggers:** impact-flinch, gaze shift, emotional transition, micro-freeze, reveal, turn-taking
- **Beat change:** shift in intention/thought that should cause timing contrast
- **Emphasis placement:** which words get accents vs holds
- **Timing primitives:** hold, snap, overshoot, settle (X)

### Key takeaways applied to Animini
- Holds do the heavy lifting (readability comes from stillness).
- Accents cluster on emphasized words; unstressed words often get almost nothing.
- Blink timing often coincides with beat changes and gaze shifts.

---

## Why this matters for Sora / video generation

In Sora-style video generation, performance must remain coherent across frames while still being steerable. Word-level emphasis is a natural control handle for speech-driven acting, and this work provides a model-agnostic baseline: a control representation + evaluation protocol that can guide future model-level conditioning for controllable performance in video.

---

## Reproducibility

- Baseline prompt template: X  
- Animini prompt template: X  
- Sample dataset schema (JSON): X  
- Metric code / notebook: X  
- Demo asset list: X  

---

## Citation

```bibtex
@misc{chen2026animini,
  title   = {Animini: Emphasis-Controlled Facial Acting via Prompt-Based Control Layers},
  author  = {Alice Chen},
  year    = {2026},
  howpublished = {\url{https://floweralicee.github.io/lipsync-ai-demo}}
}
```