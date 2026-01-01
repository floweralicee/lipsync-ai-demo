# Animini Results: Emphasis-Controlled Facial Acting (No Model Training)

**TL;DR:** I improve AI facial acting **without retraining the model** by treating prompting as a **model-agnostic control layer** that maps speech emphasis to **accents + holds**, reducing “even timing” and making performance more intentional.

**Links:**  
[Paper (2–4 pages)](X) · [Code](X) · [Eval/Benchmark](X) · [Results Gallery](#results-gallery) · [Citation](#citation) · Contact: @flower_alicee

---

## Results Gallery (watch first)

> **Controlled setup:** same base model + same audio + same transcript. Only the prompt/control layer differs.

### Example 1 — “X”  
- **Transcript:** X  
- **Target emphasis:** X  
- **Expected primitives:** hold → accent → recovery  
- **Baseline diagnosis:** even timing (accents near-uniform; low stress/unstress contrast)  
- **Animini change:** accents land on emphasized words + clearer holds/contrast  

**Baseline:** X (mp4/gif)  
**Animini:** X (mp4/gif)

---

### Example 2 — “X”
(Repeat until you have 6–12 pairs)

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

## Definitions (so we’re not hand-wavy)

- **Even timing:** motion accents occur at near-uniform intervals with low contrast between stressed and unstressed words.
- **Accent:** a localized peak in motion (head/face/eyes/brows) that marks emphasis.
- **Hold:** intentional stillness that increases readability and sets up the next accent.
- **Contrast:** stressed vs unstressed words differ meaningfully in motion magnitude/changes.
- **Emphasis track:** word timestamps + emphasis score over time (from prosody and/or transcript heuristics).
- **Pixar-style acting (operationalized):** rhythm of emphasis + contrast + intentional holds (not constant motion).

---

## Controls (MoCha-style sections)

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

## Evaluation Protocol (How I avoided cherry-picking)

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

I treat performance as measurable behavior, not taste.

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
  howpublished = {\url{X}}
}
