# Cross-Cultural Alignment Signal (CCAS)

### Beyond WEIRD Defaults: Diverse Moral Experience as AI Alignment Signal

A position paper and implementation roadmap for improving AI alignment by treating cross-cultural moral divergence as signal rather than noise.

## The Problem

Current AI alignment relies on a WEIRD-skewed (Western, Educated, Industrialized, Rich, Democratic) pool of researchers and raters. Their moral frameworks enter the training signal unlabeled and read as universal moral judgment because no mechanism exists to flag them as cultural artifacts. The problem is not the RLHF mechanism but what goes into it: a thin, parochial signal that encodes convention as principle.

## The Proposal

Collect narrative-based moral experience across populations with genuinely different moral frameworks using SenseMaker (a triad-based self-signification instrument). Process the data through a rationalization layer that classifies each moral domain into one of three categories:

- **Candidate universal:** populations converge on both conclusion and reasoning. The model can respond with justified confidence.
- **Contingent agreement:** populations converge on conclusion but diverge on reasoning. The model flags the agreement as fragile.
- **Cultural contingency:** populations diverge on conclusion. The model surfaces the tension rather than resolving it.

The rationalization layer's output enters the training pipeline through two mechanisms: supervised fine-tuning that teaches the model a four-dimensional moral framework vocabulary, and variance-weighted preference optimization that calibrates the model's confidence to track the actual state of cross-cultural agreement. The RLHF mechanism itself is unchanged. The innovation is in the upstream signal quality.

## Repository Contents

| File | Description |
|------|-------------|
| [BeyondWEIRDdefaults.md](./BeyondWEIRDdefaults.md) | The position paper. 11 sections + addendum, 23 references across moral psychology, political philosophy, AI alignment, and field methodology. |
| [annotated-bibliography.md](./annotated-bibliography.md) | Detailed annotations for all 23 references, organized by order of first appearance in the paper. |
| [ccas-pilot-experiment-design.md](./ccas-pilot-experiment-design.md) | Instrument validation experiment. WEIRD baseline vs. first-generation South Asian immigrants, two moral scenarios, Prolific recruitment, EMD analysis. Budget: $960-1,780. |
| [pilot-experiment-annotated-bibliography.md](./pilot-experiment-annotated-bibliography.md) | Detailed annotations for all 11 references in the pilot experiment, covering WEIRD psychology, moral foundations theory, SenseMaker methodology, and statistical methods. |
| [ccas-training-experiment-design.md](./ccas-training-experiment-design.md) | Training protocol. Variance-weighted DPO + supervised dimensional training, 2x2 ablation + unmodified baseline, Llama 3.1 8B with QLoRA, custom VarianceWeightedDPOTrainer. Budget: $6,400-11,000. |
| [training-experiment-annotated-bibliography.md](./training-experiment-annotated-bibliography.md) | Detailed annotations for all 12 references in the training experiment, covering DPO methodology, per-example loss weighting precedents, moral reasoning evaluation baselines, and variance score data sources. |
| [ccas-sae-diagnostic-experiment.md](./ccas-sae-diagnostic-experiment.md) | Mechanistic diagnostic using sparse autoencoders to validate whether CCAS training creates genuine moral framework awareness or surface-level pattern matching. Four-phase design: feature discovery, cross-condition comparison, sycophancy diagnostic, superposition check. Budget: $3,000-6,000. |
| [sae-diagnostic-annotated-bibliography.md](./sae-diagnostic-annotated-bibliography.md) | Detailed annotations for all 11 references in the SAE diagnostic experiment, including known limitations of crosscoder model diffing and the SAE faithfulness debate. |
| [ccas-plain-language-guide.md](./ccas-plain-language-guide.md) | Plain-language guide explaining every technical concept in the paper — RLHF, triads, EMD, the four dimensions, the three categories, and more — for non-specialist readers and researchers from adjacent fields. |
| [ai-research-collaborator-case-study.md](./ai-research-collaborator-case-study.md) | Case study documenting the human-AI collaboration that produced this work, with honest accounting of who contributed what. |
| [collaboration-reflection-exchange.md](./collaboration-reflection-exchange.md) | Unedited exchange between the author and Claude on the experience of collaboration. Companion to the case study. |
| [literature-divergence-map.md](./literature-divergence-map.md) | Map of how this proposal relates to and diverges from existing work in the field. |
| [ccas-applications.md](./ccas-applications.md) | Exploration of CCAS applications beyond the core alignment use case. |

## Key Technical Concepts

**Four structural dimensions** of moral framework variation (robust across four independent moral psychology theories; see Addendum A):
1. Moral agent constitution (who is the moral subject?)
2. Authority legitimacy (when does hierarchy have moral standing?)
3. Moral domain boundary (what counts as a moral question at all?)
4. Scope of moral obligation (how far does obligation extend?)

**Variance-weighted reward modification:** R_modified ~ N(r_base, sigma^2 / alpha(q)), where alpha is the minimum convergence score across activated dimensions. High convergence produces tight reward signal (learn confidently). Low convergence produces noisy reward signal (learn that confidence is unwarranted). This teaches calibrated uncertainty as an emergent property of training rather than a compliance flag.

**Two-stage pipeline:** Dimensional SFT establishes the framework vocabulary. Variance-weighted DPO calibrates its deployment. The sequence matters: variance without prior dimensional training produces vague hedging; dimensional training without variance-weighted preferences produces articulate overconfidence.

## How This Was Made

This work was produced in extended collaboration between a non-academic practitioner and Claude (Anthropic, Opus). The author provided the core problem identification, architectural vision, structural constraints, and domain insights from decades of cross-cultural professional experience. Claude provided the formal architecture, cross-disciplinary connections, formalizations, and literature integration. Many contributions were genuinely joint. The case study and paper acknowledgment document the division of labor in detail.

This is not a paper written by a human and formatted by AI, nor a paper generated by AI and approved by a human. It is a collaborative product in which both parties contributed ideas that the other would not have produced alone.

## Status

Position paper complete. Experiment designs specified. No components built, no data collected, no methodology validated. The logic is sound but empirical. Everything that follows requires pilot data, institutional collaboration, and the human infrastructure to collect moral experience from populations currently absent from alignment work.

## Collaboration

The author welcomes collaboration with researchers who can contribute formal ML frameworks, run the pilot experiments, or connect this work to existing alignment research programs. See the paper's Notes on Positionality for full background.

**Declan Michaels** - Pike Road, Alabama
**mcoon1961@gmail.com**
**linkedin.com/in/declanmichaels**

## License

Apache License 2.0. See [LICENSE](./LICENSE).
