# Cross-Cultural Alignment Signal (CCAS)

### Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late

A position paper and implementation roadmap for improving AI alignment by treating cross-cultural moral divergence as signal rather than noise.

## The Problem

Current AI alignment relies on a WEIRD-skewed (Western, Educated, Industrialized, Rich, Democratic) pool of researchers and raters. Their moral frameworks enter the training signal unlabeled and pass as universal because no mechanism exists to flag them as cultural artifacts. Plasticity loss research demonstrates that early training shapes representational geometry in ways that resist subsequent correction. A model whose initial alignment encodes confident WEIRD moral defaults may lack the capacity to incorporate diverse moral signal introduced later. The problem is not the RLHF mechanism but what goes into it, and when.

## The Proposal

Collect structured moral judgments and reasoning across culturally diverse populations using shared stimuli with constrained allocation sliders. Process the data through a classification function that categorizes each moral domain into one of three categories:

- **Candidate universal:** populations converge on both conclusion and reasoning. The model can respond with justified confidence.
- **Contingent agreement:** populations converge on conclusion but diverge on reasoning. The model flags the agreement as fragile.
- **Cultural contingency:** populations diverge on conclusion. The model surfaces the tension rather than resolving it.

The classification function's output enters the training pipeline upstream through two mechanisms: a quality filter on initial alignment data (excluding or down-weighting culturally contingent preferences presented with unwarranted confidence), and variance-weighted reward modification that calibrates model confidence to track cross-cultural agreement. Separately, supervised dimensional training teaches the model what structured moral awareness looks like in practice. The RLHF mechanism itself is unchanged. The innovation is in the upstream signal quality and timing.

## Repository Contents

### Core Paper

| File | Description |
|------|-------------|
| [BeyondWEIRDdefaults-v2-draft-revised.md](./BeyondWEIRDdefaults-v2-draft-revised.md) | The position paper. 11 sections + addendum, 35 references across moral psychology, political philosophy, AI alignment, plasticity research, and field methodology. ~11,000 words. |
| [annotated-bibliography-full.md](./annotated-bibliography-full.md) | Detailed annotations for all 35 references, organized by order of appearance. Each entry explains what the source argues, what the paper draws from it, and known limitations. |
| [dimensional-robustness-companion.md](./dimensional-robustness-companion.md) | Demonstrates that the four structural dimensions are recoverable across Shweder's CAD triad, Gray & Schein's TDM, and Curry's Morality-as-Cooperation. Referenced in Addendum A. |

### Experiment Designs

| File | Description |
|------|-------------|
| [ccas-pilot-experiment-design.md](./ccas-pilot-experiment-design.md) | Instrument validation experiment. Within-state pilot with populations showing documented framework differences. Budget: $960-1,780. |
| [pilot-experiment-annotated-bibliography.md](./pilot-experiment-annotated-bibliography.md) | Annotations for pilot experiment references. |
| [ccas-training-experiment-design.md](./ccas-training-experiment-design.md) | Training protocol. Variance-weighted DPO + supervised dimensional training, 2x2 ablation on Llama 3.1 8B. Budget: $4,200-8,400. |
| [training-experiment-annotated-bibliography.md](./training-experiment-annotated-bibliography.md) | Annotations for training experiment references. |
| [ccas-sae-diagnostic-experiment.md](./ccas-sae-diagnostic-experiment.md) | Mechanistic diagnostic using sparse autoencoders to validate whether CCAS training creates genuine moral framework awareness or surface-level pattern matching. Budget: $2,000-4,000. |
| [sae-diagnostic-annotated-bibliography.md](./sae-diagnostic-annotated-bibliography.md) | Annotations for SAE diagnostic references. |

### Companion Documents

| File | Description |
|------|-------------|
| [ccas-plain-language-guide.md](./ccas-plain-language-guide.md) | Plain-language guide explaining every technical concept in the paper for non-specialist readers and researchers from adjacent fields. |
| [ai-research-collaborator-case-study.md](./ai-research-collaborator-case-study.md) | Case study documenting the human-AI collaboration that produced this work, with honest accounting of who contributed what. |
| [collaboration-reflection-exchange.md](./collaboration-reflection-exchange.md) | Unedited exchange between the author and Claude on the experience of collaboration. |
| [literature-divergence-map.md](./literature-divergence-map.md) | Map of how this proposal relates to and diverges from existing work in the field. |

## Key Technical Concepts

**Four structural dimensions** of moral framework variation (robust across four independent moral psychology theories; confirmed through cross-tradition due diligence against Islamic maqasid, Hindu dharma/karma, Buddhist no-self ethics, Confucian relational ethics, and African communitarian ethics):
1. Moral agent constitution (who is the moral subject?)
2. Authority legitimacy (when does hierarchy have moral standing?)
3. Moral domain boundary (what counts as a moral question at all?)
4. Scope of moral obligation (how far does obligation extend?)

Two candidate additional dimensions identified through cross-tradition examination: epistemic source of moral knowledge (fifth), and temporal horizon of moral consequences (sixth).

**Classification function:** Two-stage EMD analysis. Judgment EMD compares population-level moral conclusion distributions. Reasoning EMD compares reasoning distributions for convergent populations. Uniform ground metric. Conservative fallback (culturally contingent when uncertain).

**Two training mechanisms addressing two problems:** Variance-weighted reward (Problem A: confidence calibration) teaches the model where to be uncertain. Supervised dimensional training (Problem B: domain recognition) teaches the model what kind of uncertainty it is encountering. Neither alone produces the target behavior.

**The timing argument:** Plasticity loss (Dohare et al. 2024), the primacy bias (Nikishin et al. 2022), and data quality research (Gunasekar et al. 2023; Zhou et al. 2023) provide converging structural grounds for the hypothesis that diverse moral signal must enter training before WEIRD defaults shape representational geometry. The structural analogy from adjacent regimes is this paper's contribution, not a claim of mechanistic transfer.

## How This Was Made

This work was produced in extended collaboration between a non-academic practitioner and Claude (Anthropic, Opus). The author provided the core problem identification, architectural vision, structural constraints, and domain insights from decades of cross-cultural professional experience. Claude provided the formal architecture, cross-disciplinary connections, formalizations, and literature integration. Many contributions were genuinely joint. The case study and paper acknowledgment document the division of labor in detail.

## Status

Position paper revised (March 2026). Experiment designs specified. No components built, no data collected, no methodology validated. The logic is sound but empirical. Everything that follows requires pilot data, institutional collaboration, and the human infrastructure to collect moral experience from populations currently absent from alignment work.

## Collaboration

The author welcomes collaboration with researchers who can contribute formal ML frameworks, run the pilot experiments, or connect this work to existing alignment research programs. See the paper's Notes on Positionality for full background.

**Declan Michaels** - Pike Road, Alabama
**mcoon1961@gmail.com**
**linkedin.com/in/declanmichaels**

## License

Apache License 2.0. See [LICENSE](./LICENSE).
