# Cross-Cultural Alignment Signal (CCAS)

### One Shot: The Strategic Risk of Testing Diverse Moral Signal at the Wrong Integration Point

A position paper arguing that diverse moral signal must enter the AI training pipeline during initial alignment, before WEIRD defaults shape representational geometry, and that the strategic risk is not failure but a false negative that forecloses the right experiment.

## Start Here

| File | Description |
|------|-------------|
| [one-shot.md](./one-shot.md) | **The anchor paper.** The strategic argument: why integration timing matters, what the fix looks like, and what happens if the field tests this at the wrong point. ~3,200 words, 9 references. Start here. |
| [BeyondWEIRDdefaults.md](./BeyondWEIRDdefaults.md) | **The technical companion.** Full architecture: instrument design, classification function, scenario design, evaluation tiers, deployment, risks. ~11,000 words, 35 references. |
| [annotated-bibliography-full.md](./annotated-bibliography-full.md) | Detailed annotations for all 35 references in the technical companion. Each entry explains what the source argues, what the paper draws from it, and known limitations. |

## The Problem

Current AI alignment relies on a WEIRD-skewed (Western, Educated, Industrialized, Rich, Democratic) pool of researchers and raters. Their moral frameworks enter the training signal unlabeled and pass as universal because no mechanism exists to flag them as cultural artifacts. Plasticity loss research demonstrates that early training shapes representational geometry in ways that resist subsequent correction. The result is not that the model gives wrong answers. It fails to recognize certain questions as moral at all.

## The Proposal

Collect structured moral judgments and reasoning across culturally diverse populations using shared stimuli with constrained allocation sliders. The instrument collects two independent signals per domain: what people conclude (judgment) and why (reasoning). The two-dimensional convergence structure produces three natural categories:

- **Candidate universal:** convergence on both judgment and reasoning. The model responds with justified confidence.
- **Contingent agreement:** convergence on judgment, divergence on reasoning. The model flags the agreement as fragile.
- **Cultural contingency:** divergence on judgment. The model surfaces the tension rather than resolving it.

The classification output enters the training pipeline at the supervised fine-tuning and preference optimization phases, serving as a quality filter on initial alignment data and a variance modifier on the reward signal. The result is a confidence gradient that tracks the evidence.

## Experiment Designs

| File | Description |
|------|-------------|
| [ccas-pilot-experiment-design.md](./experiments/ccas-pilot-experiment-design.md) | Instrument validation. Within-state pilot with populations showing documented framework differences. Budget: $960-1,780. |
| [pilot-experiment-annotated-bibliography.md](./experiments/pilot-experiment-annotated-bibliography.md) | Annotations for pilot experiment references. |
| [ccas-training-experiment-design.md](./experiments/ccas-training-experiment-design.md) | Training protocol. Variance-weighted DPO + supervised dimensional training, 2x2 ablation on Llama 3.1 8B. Budget: $4,200-8,400. |
| [training-experiment-annotated-bibliography.md](./experiments/training-experiment-annotated-bibliography.md) | Annotations for training experiment references. |
| [ccas-sae-diagnostic-experiment.md](./experiments/ccas-sae-diagnostic-experiment.md) | Mechanistic diagnostic using sparse autoencoders to validate whether training creates genuine moral framework awareness or surface-level pattern matching. Budget: $2,000-4,000. |
| [sae-diagnostic-annotated-bibliography.md](./experiments/sae-diagnostic-annotated-bibliography.md) | Annotations for SAE diagnostic references. |

## Companion Documents

| File | Description |
|------|-------------|
| [dimensional-robustness-companion.md](./companions/dimensional-robustness-companion.md) | Demonstrates that the four structural dimensions are recoverable across Shweder's CAD triad, Gray & Schein's TDM, and Curry's Morality-as-Cooperation. |
| [tier-1-4-worked-examples.md](./companions/tier-1-4-worked-examples.md) | 15 prompts with responses at all four evaluation tiers. Covers all four dimensions plus multi-dimensional prompts. Usable as SFT training data examples. |
| [literature-divergence-map.md](./companions/literature-divergence-map.md) | Map showing where existing cross-cultural research predicts convergence and divergence on each dimension. |
| [ccas-plain-language-guide.md](./companions/ccas-plain-language-guide.md) | Plain-language guide explaining every technical concept for non-specialist readers. |
| [ai-research-collaborator-case-study.md](./context/ai-research-collaborator-case-study.md) | Case study documenting the human-AI collaboration that produced this work. |
| [collaboration-reflection-exchange.md](./context/collaboration-reflection-exchange.md) | Unedited exchange between the author and Claude on the experience of collaboration. |

## Status

Position paper revised (March 2026). Anchor paper drafted (March 2026). Experiment designs specified. No components built, no data collected, no methodology validated. The logic is sound but empirical. Everything that follows requires pilot data, institutional collaboration, and the human infrastructure to collect moral experience from populations currently absent from alignment work.

## Collaboration

The author welcomes collaboration with researchers who can contribute formal ML frameworks, run the pilot experiments, or connect this work to existing alignment research programs. See the anchor paper's Notes on Positionality for full background.

**Declan Michaels** — Pike Road, Alabama
**DeclanVMichaels@gmail.com**
**[linkedin.com/in/declanmichaels](https://linkedin.com/in/declanmichaels)**

## License

Apache License 2.0. See [LICENSE](./LICENSE).
