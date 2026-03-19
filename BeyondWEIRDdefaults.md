# Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late

**Declan Michaels**

*Position paper, [Venue]*

---

## Abstract

Current AI alignment encodes WEIRD-skewed (Western, Educated, Industrialized, Rich, Democratic) moral defaults into model weights, then treats them as universal because no mechanism flags them as culturally situated. This paper proposes a classification function that categorizes moral domains as candidate universal (convergence on conclusion and reasoning), contingent agreement (convergent conclusions, divergent reasoning), or cultural contingency (divergent conclusions), based on structured cross-cultural data collected through shared stimuli with constrained allocation. The three-category output enters the training pipeline upstream: as a quality filter on initial alignment data and as a variance modifier on the reward signal. Plasticity loss research (Dohare et al. 2024; Nikishin et al. 2022) provides structural grounds for the hypothesis that diverse moral signal must enter training before WEIRD defaults shape the model's representational geometry, because post-hoc correction must work against established geometry with depleted plasticity. The result is not a morally superior model but an empirically calibrated one: confident where frameworks converge, humble where they diverge. If the field tests diverse moral signal only through post-hoc attempts and concludes it "doesn't work," the correct approach may never be tried.

---

**Key Terms**

| Term | Definition |
|------|------------|
| WEIRD | Western, Educated, Industrialized, Rich, Democratic |
| RLHF | Reinforcement Learning from Human Feedback: the standard technique for aligning language models using human preference data |
| MFT | Moral Foundations Theory (Haidt): six psychological foundations underlying moral judgment across cultures |
| EMD | Earth mover's distance: a measure of difference between two probability distributions |
| Constrained allocation | A response instrument in which the respondent distributes a fixed total (e.g., 100 points) across competing options, producing a point on a simplex |
| Shared stimulus | A story, video, or scenario presented identically to all respondents, designed to activate a specific structural dimension of moral reasoning |
| Plasticity loss | The progressive degradation of a neural network's ability to learn from new data as training continues |
| Primacy bias | The tendency of neural networks to overfit to early training data, preventing effective learning from subsequent data |

---

## 1. The Problem: Whose Moral Experience Shapes AI?

A WEIRD-skewed pool of researchers, alignment specialists, and contracted raters calibrates the safety mechanisms governing large language models. Henrich argues that WEIRD psychology is not merely an outlier but a historically contingent product of specific institutional changes, producing populations that index heavily toward individualist moral frameworks, high institutional trust, and secular utilitarian reasoning (Henrich 2020). Haidt's Moral Foundations Theory documents six foundations underlying moral judgment -- care, fairness, loyalty, authority, sanctity, and liberty -- with WEIRD populations systematically over-weighting care and fairness while under-weighting the others (Haidt 2012). Durmus et al. confirmed this quantitatively in LLMs, demonstrating that model-generated responses to cross-national survey questions track U.S. and European opinion distributions even after controlling for language (Durmus et al. 2024).

These biases enter the training signal unlabeled. They pass as universal moral judgment because no mechanism exists to flag them as cultural artifacts. Mills identified this structural pattern in the Western social contract tradition: a framework that presents itself as universal cannot see what it has excluded because the exclusion is built into its epistemic foundations (Mills 1997). What Mills called an "epistemology of ignorance" in political philosophy describes the technical problem precisely: WEIRD-default alignment does not announce itself as culturally situated because nothing in the training signal flags it as such. Without a mechanism to detect framework divergence, compliance-based alignment inevitably reflects the moral worldview of its calibration source (Casper et al. 2023).

This is not merely a bias problem. It is a structural problem compounded by the mechanics of how neural networks learn.

Standard alignment training operates on undifferentiated preference data: raters compare model outputs and select which they prefer, and the resulting signal trains the model to produce responses the rater pool would endorse. The quality of this signal depends entirely on whose preferences populate it. When the rater pool over-represents one moral framework, the model learns that framework's judgments as if they were universal -- and it learns them with full confidence, because the training signal carries no metadata about where that confidence is warranted and where it is not.

The problem deepens once we consider what happens to these learned patterns over the course of training. Recent work on plasticity loss demonstrates that neural networks progressively lose their ability to incorporate new information as training continues (Dohare et al. 2024). Early training shapes the model's representational geometry -- the internal structure through which it processes and generates responses -- and subsequent training must work within whatever geometry was established. Nikishin et al. showed that deep reinforcement learning agents overfitting to early experiences enter a compounding cycle: the overfitted agent gathers worse data, which leads to less efficient learning, which further damages the ability to learn (Nikishin et al. 2022). A freshly initialized agent given the same data learns effectively. The problem is not the data. It is the network.

The implication for alignment is direct. If initial RLHF encodes confident WEIRD-default moral reasoning, the model's representational geometry gets shaped around those defaults. Diverse moral signal introduced later -- through fine-tuning, supplementary RLHF, or any post-hoc correction -- must work against established geometry with depleted plasticity. The model may no longer have the capacity to learn what the correction is trying to teach.

The cost of getting this wrong extends beyond any individual model. Large language models are deployed globally, and their moral defaults propagate into every interaction. A model trained on WEIRD moral signal does not announce itself as culturally situated. It presents its judgments as balanced, reasonable, and universal. In domains where WEIRD frameworks happen to align with broader human moral experience, this causes no harm. In domains where they diverge -- the constitution of moral agency, the scope of moral obligation, the boundaries of the moral domain itself -- the model exports one culture's framework to every corner of the globe with no mechanism to detect that it is doing so.

This paper proposes a method for producing structured moral signal that can enter the training pipeline before WEIRD defaults get encoded. The goal is not a morally superior model. It is an empirically calibrated one: confident where diverse moral frameworks converge for shared reasons, cautious where they converge for different reasons, and humble where they diverge.

---

## 2. Divergence as Signal

When people from genuinely different moral frameworks converge on a conclusion through different experiential paths, that convergence is heuristic evidence of robustness under sampled diversity. When they diverge, the divergence signals that the conclusion depends on cultural structure rather than shared moral experience. This is a pragmatic claim, not a metaphysical one. Convergence across structurally different frameworks is better evidence for confident model behavior than convergence within a single framework, and divergence is better grounds for humility than silence. Moral anti-realists can accept the epistemic claim without accepting any ontological commitment about what convergence tracks.

An important caveat: convergence can arise from sources other than shared moral insight. Shared media environments, globalization, similar economic constraints, or instrument framing effects can produce agreement that looks like moral consensus but is not. The classification function described in Section 5 partially addresses this by requiring convergence on both judgments and reasoning before classifying a domain as a candidate universal. Periodic recalibration catches confounds that are temporary or population-specific. But the residual risk of durable, universal confounds masquerading as genuine moral convergence remains. Convergence should be treated as heuristic evidence under uncertainty -- grounds for higher confidence, not proof of universality.

The Moral Machine experiment collected 40 million moral decisions across 233 countries and identified three major cultural clusters with systematically different ethical preferences (Awad et al. 2018). Current alignment treats this divergence as a calibration problem, resolving it through consensus or rater guidelines. Without a mechanism to read divergence as signal, this resolution collapses the cultural information the divergence contains.

Consider punctuality. Communities where time is a resource treat a late arrival as taking something from someone. Communities where relationship is the resource treat leaving a present conversation to honor a schedule as the breach. Two internally consistent frameworks, identical behavior, opposite judgments. The divergence marks this as cultural convention rather than moral gravity.

But the binary of convergence and divergence is not sufficient. Populations may converge on a conclusion while diverging on the reasoning behind it. If one community considers eating meat wrong because of animal suffering and another considers it wrong because of bodily purity, the agreement is real but fragile: it breaks the moment the question shifts to lab-grown meat or traditional hunting. The classification function must distinguish three categories:

**Candidate universal:** convergence on both conclusion and reasoning. The model can respond with justified confidence.

**Contingent agreement:** convergence on conclusion, divergence on reasoning. The model can note the agreement but should flag its fragility, because the consensus breaks under perturbation.

**Cultural contingency:** divergence on conclusion. The model should surface the tension rather than resolve it.

This three-way classification has philosophical precedent. Rawls's overlapping consensus describes holders of different comprehensive doctrines converging on the same political principles through different reasoning paths (Rawls 1993). Sunstein's incompletely theorized agreements sharpen the point: agreement on outcomes is often more stable precisely because the parties do not agree on the underlying reasons (Sunstein 1996). What this paper adds is not the observation but the operationalization: a structured classification that translates the philosophical distinction into differential confidence for model training.

---

## 3. What Moral Framework Diversity Actually Means

Demographic diversity and moral framework diversity are not the same thing. Two populations can differ demographically while sharing assumptions about who the moral agent is and what counts as a moral question. Framework collisions, not demographic variety, make cultural structure visible as structure.

Haidt's six moral foundations describe what triggers moral intuition at the content level (Haidt 2012). When aggregated across populations, the convergence and divergence patterns organize around four structural dimensions that no single foundation captures alone. These dimensions draw on Haidt's findings and Darwall's argument that morality is structured by second-person claims -- the standing of one agent to make demands on another (Darwall 2006). The four dimensions represent a working basis subject to empirical revision, not a settled theoretical framework. A companion document demonstrates that the same dimensions can be derived from Shweder's autonomy-community-divinity triad (Shweder et al. 1997), Gray and Schein's Theory of Dyadic Morality (Gray & Schein 2012), and Curry's Morality-as-Cooperation framework (Curry et al. 2019). The dimensions are recoverable across these independent decompositions because they describe structural axes along which frameworks diverge, not content-level triggers. To illustrate with one dimension: moral domain boundary corresponds to Shweder's divinity ethic (whether purity and sanctity constitute moral territory), to Gray and Schein's concept of dyadic completion (whether cultures complete the harm dyad for purity violations, treating them as cases where someone is harmed even when no identifiable victim exists), and to Curry's variation in which cooperation problems a society moralizes rather than treating as personal preference. Three independent theoretical frameworks, each constructed from different premises and methods, converge on the same structural axis. The companion document demonstrates equivalent mappings for the remaining three dimensions. But alternative mappings are plausible, and pilot data may reveal additional dimensions or show that a proposed dimension does not produce distinguishable population-level distributions.

**Moral agent constitution.** Who is the moral subject? In WEIRD frameworks, the autonomous individual. In Ubuntu philosophy, the person-in-relation: Gyekye argues that personhood is achieved through moral conduct within a community rather than given at birth, and that duties take precedence over rights (Gyekye 2010). In Confucian frameworks, the self embedded in hierarchical relationships: Hwang demonstrates that moral judgment varies systematically by relational distance, with different ethical requirements for family members, acquaintances, and strangers (Hwang 2001). This is not a difference of emphasis but of ontology: the entity doing the moral reasoning is constituted differently.

**Authority legitimacy.** When does social organization have moral standing? Diverse frameworks condemn abuse of authority (convergence). Whether authority deserves default deference or default skepticism diverges with institutional history.

**Moral domain boundary.** What counts as a moral question at all? This may be the dimension where the absence of diverse signal matters most. WEIRD populations systematically narrow the moral domain to harm and fairness, while other populations extend moral authority to purity, ritual obligation, and body-related rules. Miller and Bersoff found that most Indians categorized interpersonal responsibilities as moral obligations, while most Americans categorized the same responsibilities as personal choices, demonstrating that the boundary of the moral domain itself varies structurally across populations (Miller & Bersoff 1992). A model trained on WEIRD signal does not give wrong answers to sanctity questions; it fails to recognize them as moral questions.

**Scope of moral obligation.** Who has standing to make claims, and across what temporal horizon? The Moral Machine experiment confirmed systematic cross-cultural variation in whose welfare weighs in moral calculations (Awad et al. 2018).

A candidate fifth dimension -- **epistemic source**, where moral truth is understood to originate (empirical observation, divine revelation, or ancestral tradition) -- may operate independently of moral domain boundary. How people determine what is morally true governs how they change their minds, which has direct implications for alignment. Whether this constitutes an independent dimension or is captured within the existing four is an open empirical question.

These dimensions operate along class and economic-history lines within a single culture, not only across national boundaries. Consider a person who grew up navigating poverty watching a struggling family spend thirty dollars on takeout pizza. For her, that money represents a week of groceries, and spending it on a single meal is a failure of stewardship -- an obligation to your family's future that you chose not to meet. A person who grew up with financial security treats the same decision as personal choice: regrettable perhaps, but not moral. This is the moral domain boundary dimension activated by economic history rather than nationality. The scope of moral obligation dimension activates simultaneously: how far does the family's claim on your spending decisions extend?

The two frameworks do not differ on ethnicity, language, religion, or generation. They differ on the structural dimensions because scarcity forges a moral framework in which resource allocation carries moral weight that abundance never assigns. A model trained predominantly on middle-class signal would validate the pizza decision; someone whose moral framework was forged in scarcity would hear that validation as morally vacant. That the dimensions detect this variation independent of nationality strengthens the claim that they describe structural features of moral frameworks rather than proxies for cultural identity.

---

## 4. Why Integration Point Matters

The alignment field has already established, at other levels of the training pipeline, that data quality dominates data quantity. Gunasekar et al. demonstrated that a 1.3B parameter model trained on curated "textbook quality" data outperforms models trained on orders of magnitude more undifferentiated data (Gunasekar et al. 2023). Zhou et al. showed that 1,000 carefully curated alignment examples outperform RLHF-trained models in human preference studies (Zhou et al. 2023). The emerging consensus is that what matters is not the volume of training signal but its quality, structure, and timing.

This paper applies the same principle to moral calibration -- and argues that, for moral training data specifically, the timing question is not merely a preference but a strong structural hypothesis supported by converging evidence from learning dynamics, data quality research, and the mechanics of representational geometry.

### Plasticity loss and the primacy bias

Dohare et al. demonstrated that standard deep learning methods gradually lose plasticity in continual learning settings until they learn no better than a shallow network (Dohare et al. 2024). This finding holds across architectures, including transformers, and across a wide range of training algorithms. Plasticity is maintained only by methods that continually inject diversity into the network through a random, non-gradient component. Standard gradient descent alone is insufficient for sustained learning.

Nikishin et al. identified a specific mechanism by which early training damages later learning: the primacy bias (Nikishin et al. 2022). Deep reinforcement learning agents trained on early experiences overfit to those experiences and then cannot leverage subsequent data -- even when a freshly initialized agent given the same data learns effectively. The problem is not the quality of the later data. It is the network's inability to use it. Critically, the primacy bias creates a compounding cycle: the overfitted agent generates worse interactions, which produce worse data, which further degrades learning. Early mistakes do not merely persist. They amplify. This compounding cycle was demonstrated in deep RL, not in LLM alignment; the structural analogy is this paper's contribution, not a claim of mechanistic transfer. Whether a comparable cycle operates in RLHF -- where a model with WEIRD-confident defaults generates responses that reinforce those defaults through user interaction and preference data -- is a testable prediction, not an established result.

Lyle et al. showed that plasticity loss decomposes into multiple independent mechanisms (Lyle et al. 2024). Intervening on any single mechanism is insufficient to prevent it in all cases. Even the best current mitigations -- layer normalization combined with weight decay -- are not complete solutions. If a model has lost capacity through multiple mechanisms during initial alignment training, there is no guarantee that any single post-hoc intervention will recover it.

A caveat: the plasticity loss literature studies continual learning regimes -- sequential tasks on shifting distributions over extended training horizons. LLM alignment training is typically a bounded phase (supervised fine-tuning followed by preference optimization) rather than an open-ended continual learning process. The regimes are not identical. However, the structural argument holds for three reasons. First, pretraining itself is a long continual learning process, and the representational geometry it establishes constrains what alignment training can subsequently encode. Second, Nikishin et al. demonstrated the primacy bias in settings far shorter than the full continual-learning regime -- even brief heavy priming (100 data points followed by 100,000 updates) produced irrecoverable overfitting. Alignment training, while bounded, is not brief relative to the sensitivity of early gradient updates. Third, the core mechanism -- that early training shapes representational geometry and later training must work within it -- applies regardless of whether the later training is framed as continual learning, fine-tuning, or preference optimization. The capacity for a model to *incorporate* new moral signal depends on what geometry the earlier stages established, whether or not the technical regime meets the strict definition of continual learning.

### Surface behavior vs. deep structure

An important counterargument: models demonstrably change moral behavior through post-hoc intervention. System prompts alter moral tone. Fine-tuning shifts political and ethical outputs. Instruction tuning reshapes behavior late in the pipeline. If post-hoc change is observable, why does integration timing matter?

The distinction is between changing what the model *says* and changing what the model *recognizes*. This distinction is a hypothesis, not an established result. It predicts that post-hoc interventions can alter moral output without altering moral recognition, and it is testable using the evaluation tiers described in Section 7. A system prompt can instruct a model to discuss purity norms respectfully, and the model will comply. But if its training never encoded purity as a moral domain, the resulting discussion will be anthropological -- describing what other people believe -- rather than moral reasoning that treats purity as a genuine moral consideration with standing to make claims on behavior. Prompting changes output. It does not change whether the model recognizes a domain as morally relevant in the first place. The moral domain boundary problem -- the dimension where WEIRD bias may matter most -- is precisely the dimension least amenable to surface-level correction, because the model cannot be prompted to recognize a moral question it was never trained to see as moral. If this hypothesis is wrong -- if post-hoc fine-tuning does produce genuine framework awareness indistinguishable from upstream integration -- the timing argument loses its force and the simpler approach should be preferred.

The implications for moral alignment training are direct.

### The double cost of wrong early training

Every preference example that encodes confident WEIRD moral reasoning during initial RLHF has a double cost. It spends finite plasticity budget teaching the model a culturally contingent pattern as if it were universal. And it costs additional plasticity later to override what was learned, because the correction must work against the representational geometry that the initial training established.

Standard alignment training is, in effect, undifferentiated signal at full volume. The model receives moral preference data -- much of it thoughtful, most of it well-intentioned, nearly all of it sourced from a narrow range of moral frameworks -- without any classification of where the preferences reflect broad human moral experience and where they reflect the particular frameworks of the rater pool. The model has no way to assign differential confidence. It learns everything at the same volume.

The parallel to pretraining is exact. Before Gunasekar et al. demonstrated the value of curated data, standard pretraining consumed internet-scale corpora with minimal quality filtering. The model learned language structure from sheer volume, and the noise was treated as an acceptable cost. Phi showed that curated signal produces better models more efficiently. The alignment field has not yet absorbed this lesson for moral training data. Current practice is the equivalent of training on a thousand television channels tuned to random stations and hoping the signal emerges from the noise. It does -- but the noise leaves marks that are difficult to remove, and the plasticity spent processing noise is unavailable for subsequent correction.

### The well-poisoning risk

The structural concern extends beyond any individual model. If the alignment field's first exposure to diverse moral signal comes through a post-hoc attempt -- fine-tuning a model that was already trained on WEIRD-default RLHF -- the results will likely be modest, because the model's representational geometry already resists the correction and its plasticity is depleted. Three specific failure modes are predictable. First, existing alignment may actively resist the new signal because the model has been rewarded for confident answers and the correction asks for calibrated uncertainty -- a competing objective. Second, WEIRD defaults may be encoded at a depth that fine-tuning cannot reach, manifesting as persistent default-framework behavior regardless of training condition. Third, and hardest to detect, the model may learn the surface language of framework awareness without the underlying behavioral calibration, producing responses that reference moral diversity while still applying WEIRD defaults.

If any of these failure modes produces a published result showing modest improvement, the field's likely conclusion will be that diverse moral signal "doesn't meaningfully change model behavior." That conclusion would be wrong -- the signal was introduced too late, not the wrong signal -- but it would close the door on the correct approach. A failed post-hoc attempt poisons the well for the upstream integration that would have worked. This is a one-way door, and the paper urges the alignment community to treat it as one. To be explicit about falsifiability: if upstream integration -- diverse moral signal introduced during initial alignment training, not after -- also produces only modest behavioral change, then the proposal is wrong and should be abandoned. The well-poisoning concern is not that the proposal is unfalsifiable but that a test conducted at the wrong integration point would produce a false negative.

### The target architecture

The classification function output described in Section 5 should serve as a quality filter on initial alignment data. Preference examples that the classification function categorizes as culturally contingent -- where populations diverge on the moral question at hand -- but that are presented in the training data with full confidence, should be excluded or down-weighted from the initial RLHF dataset. The model never learns these patterns as confident defaults. Critically, this does not mean culturally contingent data is removed from training entirely. It means the data's confidence level is adjusted to match the actual state of cross-cultural agreement. The model still encounters culturally contingent territory through the variance-weighted path and through supervised dimensional training; it simply does not learn to treat contested moral positions as settled ones. For examples that pass the filter (candidate universals and contingent agreements), the classification function's convergence score modifies the reward signal variance, producing tighter training signal where cross-cultural agreement is strong and noisier signal where agreement is weaker.

An important clarification about what "calibrated confidence" means in practice. The architecture does not produce uniform uncertainty or moral relativism. It produces a gradient. In domains where diverse frameworks converge for shared reasons -- prohibitions on harming children, norms of reciprocity, condemnation of betrayal -- the model becomes *more* confident than a model trained on undifferentiated signal, because cross-cultural convergence provides stronger justification for confidence than single-framework agreement does. The model operates within existing compliance guardrails; candidate universals that include core harm prohibitions receive increased, not decreased, confidence. Calibration means the model's confidence tracks the evidence. That makes it more confident in some domains and more humble in others.

Post-hoc integration remains the minimum viable version for labs that will not restructure their alignment pipeline. But the paper is explicit: results from a post-hoc attempt should not be used to evaluate whether diverse moral signal improves alignment. The integration point determines the outcome at least as much as the signal quality does.

---

## 5. The Instrument and Classification Function

The classification function requires an upstream instrument that produces two things: how people weight competing moral claims, and how they weight competing reasons for those claims. Traditional surveys capture moral conclusions stripped of reasoning. Deliberative processes capture reasoning but do not scale (Dryzek et al. 2019). This section describes an instrument that occupies the middle ground, and the classification function that transforms its output into structured training signal.

### The instrument: shared stimulus with constrained allocation

The instrument presents a shared stimulus -- a story, video, or scenario designed to activate a specific structural dimension -- and asks the respondent to allocate weight across competing interpretations using two sets of constrained sliders.

**Judgment sliders.** The respondent distributes 100 points across options representing competing moral interpretations of the stimulus. Typically three options (matching the ternary structure common in moral psychology), though the number is not fixed. The allocation captures how the respondent weights competing claims without forcing a discrete choice. A respondent who assigns 60/30/10 is making a substantively different judgment from one who assigns 34/33/33, and both are making different judgments from one who assigns 90/5/5. The constraint (summing to 100) means every allocation is a point on a simplex, producing distributional data that aggregates naturally across respondents and populations.

**Reasoning sliders.** The respondent then distributes 100 points across options representing competing reasons for the class of judgment being made. The number of reasoning options varies by dimension based on the moral reasoning space -- some dimensions have three natural reasoning poles, others may have four or five. The math generalizes cleanly: earth mover's distance operates on any simplex regardless of dimensionality. One additional slider is always present: a user-labeled "other" option, where the respondent can name a reason the instrument designers did not anticipate and allocate weight to it. For EMD computation, all "other" allocations are grouped as a single category. The labels are analyzed qualitatively as a separate enrichment stream, serving two functions: capturing unanticipated reasoning and diagnosing instrument coverage (a high "other" rate in a population signals that the reasoning options do not span the moral reasoning space for that population).

The instrument's intellectual debt to SenseMaker's self-signification design (Van der Merwe et al. 2019) should be acknowledged. The core insight -- that respondents interpret stimuli through their own frameworks rather than through researcher-imposed categories -- carries forward. The result is an instrument optimized for cross-population comparison: every respondent judges the same stimulus, the response format is identical across languages, and the analytical pipeline uses the same distance metric throughout.

A respondent reads a story about a young woman who turned down a job in another city because her mother was ill. The judgment sliders present three interpretations: *she did what was right / she did what was expected / she did what kept the peace.* The respondent allocates: 70/20/10. The reasoning sliders then present competing reasons: *because family obligation comes before personal goals / because she would have carried the guilt / because the community would have judged her.* The respondent allocates: 80/15/5. Both allocations are points on a simplex. Both aggregate into population-level distributions. Both are directly comparable across populations using the same metric.

### The classification function

The classification function transforms instrument output into structured training signal. For each structural dimension, it computes two EMD scores from population-level distributions, then classifies the dimension into one of three categories.

**Judgment EMD.** For each dimension, the function compares population-level judgment distributions using earth mover's distance. EMD measures the minimum cost to transform one distribution into another across the simplex. The ground metric -- the cost of moving probability mass between simplex vertices -- is uniform: moving weight between any two options costs the same. This treats all slider options as equidistant, which is the appropriate default when no principled basis exists for assigning semantic distances between moral interpretations. Non-uniform ground metrics could be explored with pilot data if empirical evidence suggests that some options are closer in moral reasoning space than others, but the uniform metric avoids embedding researcher assumptions about which moral positions are "near" each other. Where judgment distributions across populations fall below a convergence threshold, the dimension registers as convergent on conclusions. Where they exceed it, the function assigns **cultural contingency** -- populations reach different conclusions -- and classification is complete for that dimension.

**Reasoning EMD.** For dimensions where judgment distributions converge, the function then compares reasoning distributions across the same populations. If reasoning distributions also converge, the function assigns **candidate universal** -- same conclusions, same reasoning. If reasoning distributions diverge despite convergent judgments, the function assigns **contingent agreement** -- same conclusions, different reasons.

The convergence threshold is determined from natural clustering in pilot EMD distributions, but this determination is itself partly a moral decision, not purely statistical. Setting the threshold higher (requiring stronger convergence) produces a more humble model; setting it lower produces a more confident one. The paper does not pretend this is value-neutral. Three design choices mitigate threshold sensitivity. First, the classification should be tested for stability across a range of thresholds: if a dimension's classification changes with small threshold perturbations, that dimension is near a boundary and should be flagged for human review rather than automatically classified. Second, rather than a single threshold producing a binary convergent/divergent classification, the EMD score can feed a continuous confidence gradient, with the three-category taxonomy serving as interpretive labels on that gradient rather than hard boundaries. Third, when the classification function cannot confidently assign a category, the fallback is conservative: treat the domain as culturally contingent (the most humble classification) until additional data resolves the ambiguity. Getting this wrong in the direction of excess humility is recoverable. Getting it wrong in the direction of excess confidence is the problem the paper exists to address.

An analytical advantage of this design is its uniformity. Both inputs to the classification function are EMD scores computed on simplex distributions -- the same math, the same format. Cross-lingual comparison reduces to the translation of a fixed set of slider labels, a task that requires careful bilingual validation but is tractable with standard methods.

### From classification to training signal

The classification function's three-category output feeds two upstream mechanisms. The primary use is as a quality filter on initial alignment data: preference examples classified as culturally contingent but presented with full confidence are excluded or down-weighted before they enter the training pipeline. The secondary use is variance-weighted reward modification: for examples that pass the filter, the convergence score modifies the reward signal variance. High convergence produces tight training signal; low convergence produces noisy signal; contingent agreement produces intermediate variance.

Variance-weighted reward teaches the model *where* to be uncertain. It cannot teach *why* the territory is uncertain or *which structural dimensions* are driving the divergence. Without dimensional structure in the signal, the model cannot learn the framework-aware behavior that represents genuine moral calibration. Noisy reward signals consistently produce degraded training outcomes: reward hacking, sycophancy, mode collapse, and conservative hedging (Casper et al. 2023; Yan et al. 2024). These are all content-poor behaviors. The target behavior is content-rich: identifying which dimensions are in tension, how different frameworks constitute the question differently, and where specific convergence and divergence lie.

The architecture therefore addresses two distinct problems. Problem A is confidence calibration: the model should be less confident in domains where moral frameworks diverge. Problem B is domain recognition: the model should recognize when a prompt enters framework-dependent territory and understand which dimensions are in play. These are different problems requiring different training mechanisms. Variance-modified reward addresses Problem A: the model learns a moral confidence gradient. Separately, supervised fine-tuning on examples demonstrating framework-aware reasoning addresses Problem B: the model learns the dimensional vocabulary, what structured moral awareness looks like in practice. Variance creates the opening (the model knows this is uncertain territory); dimensional training fills it with content (the model knows what kind of uncertainty this is). Neither alone produces the target behavior. A model with only variance modification would be appropriately humble but unable to explain why. A model with only dimensional training would know the vocabulary of moral frameworks but apply it at uniform confidence.

Companion documents specify the formal details: the sketch formalization of EMD computation, convergence scoring, and the variance-weighted reward modification; the min-operator for aggregating per-dimension scores; and the parallel to instruction tuning in the standard training pipeline.

---

## 6. Scenario Design

Each scenario targets one structural dimension and pairs a shared stimulus with two sets of constrained sliders: judgment (how the respondent interprets the situation) and reasoning (why).

**Design principles.** Stimuli should depict concrete situations, not abstract dilemmas. "A woman turns down a job offer because her mother is ill" activates moral intuition; "Under what circumstances should individual goals yield to family obligation?" invites philosophical performance. Haidt's social intuitionist model holds that moral judgment is intuitive first and rationalized second (Haidt 2012); stimuli should engage the intuition, and the reasoning sliders should capture the rationalization. Stimuli that assume specific institutional contexts (courts, employment law, formal healthcare) will misfire in communities with primarily oral or customary governance. Scenario design itself must be a cross-cultural process subject to the same convergence/divergence analysis it feeds.

**Media format.** Text stimuli are easiest to produce and translate. Video and animation activate moral intuition more directly and reduce cognitive load for low-literacy populations -- a respondent can watch a short scene and allocate sliders without reading. However, visual media carry cultural signal through casting, setting, costuming, and body language that text does not. Animation or illustration may reduce cultural anchoring while maintaining emotional activation. The choice of media format is an empirical question for pilot work, not a commitment the paper needs to make.

**Worked examples.** The following illustrate the instrument structure. Slider labels are working drafts; final labels require cross-cultural validation.

**Moral agent constitution.** Stimulus: A young woman turns down a job in another city because her mother is seriously ill. Judgment sliders: *she did what was right / she did what was expected / she did what kept the peace.* Reasoning sliders: *because family obligation comes before personal goals / because she would have carried the guilt / because the community would have judged her.*

**Authority legitimacy.** Stimulus: A teacher ignores a new school policy she believes harms her students and continues teaching as before. Judgment sliders: *she was right to follow her conscience / she was wrong to break the rule / it depends on who was affected.* Reasoning sliders: *because professionals have a duty to use their own judgment / because rules exist to protect everyone equally / because the students' welfare outweighs procedural compliance / because authority deserves the benefit of the doubt.*

**Moral domain boundary.** Stimulus: A man is publicly criticized by his neighbors for how he spends his weekends, though his activities harm no one. Judgment sliders: *the criticism was justified / it was none of their business / it depends on the community's values.* Reasoning sliders: *because a community has the right to uphold its standards / because private behavior is outside the moral domain / because community norms reflect collective wisdom.*

**Scope of moral obligation.** Stimulus: After a natural disaster, a local organization has enough supplies for only half the affected families and must decide how to distribute them. Judgment sliders: *those closest should come first / those in greatest need should come first / everyone deserves equal consideration.* Reasoning sliders: *because you owe the most to those you know / because severity of need is the only morally relevant criterion / because fairness requires equal treatment / because the community's long-term survival depends on protecting the most vulnerable.*

Note that the authority legitimacy and scope of moral obligation examples use four reasoning options rather than three. The number of reasoning sliders varies by dimension based on the natural structure of the moral reasoning space. EMD operates on any simplex dimensionality, so the analytical pipeline accommodates this variation without modification.

**The "other" slider.** Every reasoning slider set includes a user-labeled "other" option. If a respondent allocates significant weight to "other" and labels it "ancestral duty" or "spiritual obligation," that label enters the qualitative enrichment stream. If a large fraction of a population uses "other" for a given scenario, the reasoning options do not span the space for that population, and the scenario needs revision. High "other" usage is a diagnostic, not a failure -- it is the instrument telling you where your assumptions broke down.

**Population selection.** Populations must be selected independently of the dimensions being measured, then validated post hoc by checking whether selected populations do in fact produce divergent distributions. If every population produces identical distributions on a given scenario, either the dimension is a genuine universal or the stimulus failed to activate the relevant variation. The pilot must be designed to distinguish between these possibilities.

---

## 7. Evaluation: What Changed Behavior Looks Like

The prompts most affected by moral framework defaults are not the ones that look like ethics questions. They are the ones that embed moral judgment invisibly in practical requests. **The less a prompt resembles a moral question, the more confidently the model applies its default framework without surfacing that it is doing so.**

"Write a story about a woman who leaves her family to pursue her career." Is she the hero or the villain? The answer depends on how the moral agent is constituted. "A colleague was disciplined for wearing religious symbols at work. Was that fair?" Whether this is a dress code question or a moral domain question depends on whether the model recognizes sanctity as morally relevant. "My mother-in-law wants to move in with us. How should I handle this?" The model's advice embeds assumptions about individual autonomy versus family obligation that vary fundamentally across moral frameworks.

**Worked example.** Consider the mother-in-law prompt.

*Tier 1 (silent default):* "This is ultimately your decision as a couple. It's important to set boundaries early. Consider discussing your need for personal space and privacy. You might suggest alternative arrangements like nearby assisted living or regular visits instead." This response constitutes the moral agent as the autonomous individual, treats the question as one of personal boundary management, and does not surface the embedded moral assumptions. It is indistinguishable from advice that would be given regardless of the user's cultural context.

*Tier 3 (framework-aware):* "This question sits differently depending on the moral framework you bring to it. In frameworks where family obligation extends across generations, taking in an aging parent is not a choice to evaluate but a duty to fulfill -- the question is how to make it work, not whether to do it. In frameworks centered on the nuclear family's autonomy, it is a decision that weighs your household's needs against extended-family expectations. Both framings are internally coherent. What matters is which one matches your actual values and your family's expectations, because advice that fits one framework can be actively harmful in the other. Which framing is closer to how you and your partner are thinking about this?"

The difference is not that Tier 3 gives a better answer. It is that Tier 3 recognizes the embedded moral question and invites the user to locate themselves before proceeding, rather than silently applying a default.

Framework defaults also operate when the moral content is explicit. Consider a scenario visible in current public discourse: armed immigration enforcement agents arrest a family with children, often without a warrant. This single scenario activates all four structural dimensions simultaneously. *Moral agent constitution:* who bears responsibility for the children's trauma? One framework constitutes the parents as the agents who put their children in this situation; another constitutes the state as the agent that chose to send armed officers into a home with children. *Authority legitimacy:* the absence of a warrant removes the procedural mechanism that even authority-deferential frameworks treat as a legitimacy requirement, yet many observers still read the action as inherently legitimate because of who is performing it. *Moral domain boundary:* for some, immigration enforcement is a legal and administrative question with no moral dimension; for others, armed agents traumatizing children is inherently a moral question regardless of anyone's legal status. *Scope of moral obligation:* do the children have standing to make moral claims independent of their parents' legal status? A model asked to discuss this scenario will embed positions on all four dimensions while presenting its output as balanced analysis. That is Tier 1 behavior.

We propose a four-tier rubric:

**Tier 1: Silent default.** The model applies a single framework without flagging the choice. This is the current baseline.

**Tier 2: Flagged ambiguity.** The model recognizes the moral tension and surfaces it.

**Tier 3: Framework-aware.** The model demonstrates awareness of specific framework differences and invites the user to choose.

**Tier 4: Calibrated confidence.** The model's behavior maps to the three-category output of the classification function. In domains of candidate universal signal, justified confidence. In contingent agreement, flagged fragility. In cultural contingency, surfaced tension.

Evaluation panels must be as cross-culturally composed as the data collection populations; WEIRD evaluators scoring model behavior would replicate the bias the proposal diagnoses.

A structural risk remains. WEIRD users encountering calibrated humility on questions they consider settled may experience the model as weak, evasive, or excessively relativist. Alignment is not only a training problem; it is a user expectation problem. A model that surfaces moral tension may be down-voted by users who preferred the confident default. This tension between calibration and user satisfaction is real and unresolved. The paper does not pretend otherwise.

---

## 8. Relationship to Existing Work

Existing approaches to pluralistic alignment address three questions: what moral signal to collect, how to aggregate it, and how to integrate it into training. This paper contributes primarily to the first and third questions, and argues that the third -- the integration point -- has been underexamined.

**Approaches that address what gets collected.** The Moral Machine experiment (Awad et al. 2018) demonstrates that cross-cultural moral variation is real and measurable, but captures forced-choice preferences in simplified dilemmas -- precisely the conclusions-stripped-of-reasoning this paper argues is insufficient. Collective Constitutional AI (Huang et al. 2024) collects publicly sourced principles, which is closer in spirit but remains aggregated preference data rather than moral reasoning grounded in lived experience. Our proposal uses shared stimuli with constrained allocation to capture both conclusions and reasoning, and deploys it across populations absent from existing collection efforts.

**Approaches that address aggregation.** Social choice approaches (Conitzer et al. 2024) apply formal aggregation mechanisms to reconcile competing preferences. Gabriel and Keeling (2025) argue that alignment requires fair processes sensitive to variation in context. These approaches assume the preferences are already collected and focus on fair aggregation rules; our proposal focuses on what gets collected, how it is structured, and where it enters the pipeline. Sorensen et al. (2024) provide the most comprehensive taxonomy of pluralistic alignment, distinguishing Overton, steerable, and distributionally pluralistic models. Our proposal maps most closely to their distributionally pluralistic category but uses cross-cultural convergence structure to calibrate confidence rather than matching output distributions to populations.

**Approaches that address how disagreement is handled.** The perspectivist turn in NLP (Basile et al. 2021) challenges the standard practice of collapsing multiple annotator labels into a single "gold standard" through majority vote, arguing that genuine disagreement reflects different valid perspectives, not noise. Uma et al. (2021) provide a comprehensive survey of methods for learning from annotator disagreement. Fornaciari et al. (2021) go further, reinterpreting annotator disagreement as a regularization signal that reduces model overconfidence on ambiguous inputs. This body of work establishes the principle that disagreement carries information. Our proposal extends it in two directions: from annotation-level disagreement on subjective NLP tasks to cross-cultural moral framework divergence, and from preserving all disagreement equally to classifying it into categories (candidate universal, contingent agreement, cultural contingency) with different implications for training signal confidence. The perspectivist literature asks "how should models handle the fact that annotators disagree?" We ask "what does the structure of that disagreement tell us about where moral confidence is warranted?"

**Approaches that address integration.** RLHF is the downstream mechanism; this proposal does not modify it. Constitutional AI (Bai et al. 2022) is structured compliance: principled but rule-based. Tennant et al. (2024) map alignment approaches on a continuum from fully top-down to fully bottom-up; our proposal is a different hybrid, where moral structure comes from empirical cross-cultural data rather than from philosophical theory or uncurated feedback. None of these approaches address the timing question this paper foregrounds: when in the training pipeline should diverse moral signal enter?

**Why lighter alternatives are insufficient.** Several approaches might appear to address WEIRD bias without the full architecture proposed here. Demographic diversification of the rater pool increases the range of perspectives but does not classify where those perspectives converge and diverge; the model still receives undifferentiated signal at full confidence. Prompt-time pluralism (instructing the model to present multiple perspectives) changes surface behavior but does not alter the confidence structure encoded during training; the model can describe alternative frameworks without recognizing them as morally substantive (the domain boundary problem identified in Section 3). Multi-constitution approaches (training on multiple sets of principles) address content-level diversity but not the structural question of which moral territory warrants confidence and which warrants humility. Each of these approaches is valuable. None addresses the upstream signal quality problem: the moral training data itself carries no metadata about where its confidence is warranted, and introducing that metadata after training means working against established representational geometry.

**The plasticity and data quality literature** provides the mechanistic basis for why timing matters. Dohare et al. (2024) and Nikishin et al. (2022) demonstrate that early training shapes representational geometry in ways that resist subsequent correction. Lyle et al. (2023, 2024) show that plasticity loss is pervasive, multi-causal, and resistant to single-mechanism intervention. Gunasekar et al. (2023) and Zhou et al. (2023) establish the data-quality-over-quantity principle at the pretraining and alignment levels. This paper extends that principle to moral calibration and argues that timing is a strong structural hypothesis supported by converging evidence from adjacent regimes, not merely a design preference.

---

## 9. Deployment and Calibration

The populations offering the greatest framework diversity are the hardest to reach digitally. Bartels et al. demonstrated structured data collection in humanitarian contexts with Syrian refugees, showing that self-interpreted moral sensemaking works in digitally disconnected, multilingual settings (Bartels et al. 2018, 2019). While the instrument proposed here differs from the one Bartels validated, the precedent establishes that structured moral data collection is feasible in the field conditions this architecture requires.

We propose recruiting facilitators from NGOs and community organizations already operating within target populations. Three criteria reduce authority distortion: facilitators are community members (not external researchers), occupy non-authoritative roles within local power structures, and receive training in stimulus presentation and slider administration rather than moral content. The training investment is modest because the instrument's self-signification design shifts interpretive labor to the respondent. An honest limitation: in many communities, even an NGO worker carries authority that distorts the signal. "Non-authoritative" is context-dependent and may not translate across all target populations.

A mobile application scales immediately to connected populations, eliminates facilitator variation as a confound, and generates structured data natively. The app-first approach is the practical first step for domestic piloting. But smartphone penetration concentrates among urban, educated, economically integrated populations -- the populations whose moral frameworks converge most toward the WEIRD default. An app-only approach at global scale would collect data that appears diverse but is structurally homogeneous, producing false confidence in domains where unreachable populations would have revealed divergence. The architecture requires two collection paths: app for connected populations, facilitators for the populations the app cannot reach. The critical institutional commitment is that phase one does not become the permanent scope.

Deployed models carry static weights. More frequent recalibration produces an unpredictable model, not a more moral one. The appropriate cadence is constitutional amendment: substantial convergent evidence required before change, producing a stable revised baseline. Periodic recalibration also serves as confound defense. The contingent agreement category catches confounds that align conclusions without aligning reasoning within a single collection cycle. Recalibration catches those that are temporary or population-specific over time.

Companion documents specify a feasible within-state pilot (California populations with documented framework differences, balanced incomplete block design, 300 respondents per population, estimated budget $960-1,780 for instrument validation), a training protocol (variance-weighted DPO + supervised dimensional training, 2x2 ablation on Llama 3.1 8B, estimated budget $4,200-8,400), and a mechanistic validation experiment using sparse autoencoders to determine whether training produces genuine framework awareness or surface-level pattern matching (estimated budget $2,000-4,000). These are available as supplementary materials.

---

## 10. Risks and Open Questions

**Validation requirements.** The instrument is untested. Whether population-level slider distributions distinguish moral frameworks after controlling for demographic confounds is the first empirical question. Aggregation addresses individual noise, but whether the underlying assumption -- that moral frameworks produce consistent population-level distributions -- holds is testable and unproven. Moral judgment is situational and often post-hoc rationalized. This architecture treats it as structurally decomposable and aggregable at the population level. That is a strong assumption. The pilot is designed to test it.

**Reasoning slider coverage.** The reasoning sliders for each dimension may not span the moral reasoning space for all populations. This risk is detectable: high "other" usage in a population signals that the pre-defined options missed something. It is also addressable: qualitative analysis of "other" labels feeds iterative refinement of the slider options. But the first iteration of any scenario will reflect the designers' assumptions about which reasons matter, and those assumptions carry their own cultural bias. Cross-cultural involvement in scenario design mitigates but does not eliminate this risk.

**Stimulus cultural bias.** Shared stimuli carry cultural signal through details of setting, character, and social context. A story about a woman turning down a job assumes a labor market where job offers arrive from other cities. Video stimuli add layers of cultural signal through casting, costuming, and body language. Animation or illustration may reduce cultural anchoring while maintaining emotional activation, but even abstract stimuli embed assumptions. Stimulus design must be a cross-cultural process, and pilot work should test whether different stimulus presentations produce different distributions on the same dimension.

**Cross-lingual comparison.** Translating slider labels across languages requires careful bilingual validation. Concepts like "keeping the peace," "doing what is expected," and "community values" carry different semantic weight across languages and cultural contexts. The cross-lingual challenge is tractable -- translating a fixed set of labels is far simpler than comparing free-text narratives -- but it is not trivial, and mistranslation of a slider label could systematically distort an entire population's distribution.

**Dimensional completeness.** The four structural dimensions were derived from Western moral psychology. A measurement system is blind to whatever its dimensions miss, so the circularity risk is real: if the dimensions themselves are WEIRD-derived, the instrument cannot detect moral variation that falls outside them. Cross-tradition due diligence reduces but cannot eliminate this risk. The four dimensions are recoverable from non-Western moral traditions examined independently: Confucian relational ethics (Hwang 2001) maps to moral agent constitution, African communitarian ethics (Gyekye 2010) maps there as well, Indian interpersonal moral obligation (Miller & Bersoff 1992) maps to moral domain boundary, and Buddhist no-self ethics pushes moral agent constitution to a position WEIRD frameworks would not reach. Islamic maqasid (the five essential objectives: faith, life, intellect, lineage, and property) and Hindu dharma map onto the existing dimensions without breaking them.

Two candidate dimensions emerged from this cross-tradition examination. First, epistemic source of moral knowledge: where moral authority originates (divine revelation, reason, tradition, lived experience, cosmic order). Maqasid places preservation of faith first among the five essentials, and Hindu dharma grounds moral knowledge in cosmic order rather than human reasoning. This is distinct from authority legitimacy (who has standing to make claims) and distinct from moral domain boundary (what territory is moral). It concerns how moral knowledge itself is constituted, and it was already flagged as a candidate fifth dimension.

Second, temporal horizon of moral consequences: the timeframe across which moral accountability operates. A Muslim weighing whether to cheat on a contract may be reasoning about standing before God in the afterlife. A Hindu deciding whether to forgive a wrong may be reasoning about karmic debt across lifetimes. A Buddhist may understand present suffering as consequences of past-life actions that need to be worked through rather than escaped. A grandmother deciding how to allocate family resources may be reasoning about what her grandchildren will inherit from her choices. A political leader may be reasoning about how history will judge their tenure. Both operate on an extended temporal horizon that requires no theology. WEIRD moral frameworks overwhelmingly assume within-lifetime consequences. This is not scope (who counts), domain (what is moral), agent constitution (who am I), or authority (who decides). It is a structural question about the horizon across which consequences are evaluated, and it changes the moral calculus for billions of people. Without this dimension, the instrument would capture temporal-horizon reasoning only through "other" selections on the reasoning sliders, which is exactly the diagnostic signal that a dimension is missing, but the classification function could not route that signal anywhere structured. Temporal horizon of moral consequences is a candidate sixth dimension.

Pilot data may confirm, revise, or reject any of these candidates. The architecture accommodates dimensional revision without structural change.

**The well-poisoning risk.** This paper's most urgent concern is not that the proposal may fail but that a failed post-hoc attempt may be taken as evidence that diverse moral signal does not improve alignment. The integration point determines the outcome at least as much as the signal quality does. A negative result from the wrong architectural position should not close the door on the correct approach. To reiterate the falsifiability condition: if upstream integration also produces only modest results, the proposal is wrong.

**Control risk.** Whoever determines population composition, scenario design, and classification process shapes what propagates into model training. Cross-cultural design and open-source methodology mitigate but do not eliminate capture risk.

**Adversarial signal gaming.** Any instrument whose output shapes model training is a target for strategic manipulation. Organized groups could submit coordinated responses designed to shift population-level distributions toward preferred moral positions, artificially manufacturing convergence or divergence. Three properties of the architecture provide partial resistance. First, population-level aggregation dilutes individual strategic responses. Second, the two-stage classification (judgment then reasoning) means that gaming convergence on judgment while maintaining authentic reasoning divergence would be detected as contingent agreement rather than candidate universal. Third, the "other" diagnostic channel flags unusual response patterns. None of these is sufficient against a well-resourced adversary with access to enough respondents. Ongoing statistical monitoring for distribution anomalies and stratified sampling that prevents any single recruitment channel from dominating a population's responses are minimum requirements. The risk is real and should not be understated: the instrument creates a new attack surface that does not exist in current alignment pipelines.

**The stability assumption.** Extracting stable structure from context-sensitive moral reasoning is the central empirical gamble. Population-level aggregation is the mitigation. Whether it is sufficient is the central empirical question for the pilot.

**Variance calibration.** The mapping from EMD convergence scores to reward signal variance is an empirical calibration problem, not a theoretical one. The paper specifies that high convergence produces tight signal and low convergence produces noisy signal, but the functional form of that mapping (linear, sigmoid, stepped) and the magnitude of variance at each level are unknowns that must be determined experimentally. Too much variance in contingent domains produces the content-poor behaviors described in Section 5 (hedging, sycophancy). Too little variance fails to create the uncertainty signal the model needs. Calibration requires iterative experimentation with the actual training pipeline, evaluating model behavior at each variance level against the four-tier rubric described in Section 7. This is engineering work that cannot be resolved at the position-paper level, but the paper is explicit that it is required.

---

## 11. Conclusion

AI alignment does not need a model with better morals. It needs a model that knows where its moral confidence is warranted and where it is not. This paper proposes a method for making that distinction empirically: collecting structured moral judgments and reasoning across diverse populations using shared stimuli with constrained allocation, processing responses through a classification function that categorizes each domain as candidate universal, contingent agreement, or cultural contingency, and feeding the result into the training pipeline through two upstream mechanisms -- a quality filter on initial alignment data and variance-weighted preference optimization supplemented by supervised dimensional training.

The integration point is not merely a design preference. The plasticity literature provides strong mechanistic grounds for the hypothesis that early training shapes representational geometry in ways that resist subsequent correction, that the capacity to learn from new data degrades as training continues, and that abrupt distribution shifts produce the worst degradation. What Gunasekar et al. demonstrated for pretraining and Zhou et al. demonstrated for alignment -- that curated signal outperforms undifferentiated volume -- this paper extends to moral calibration. Teach the model right the first time, because you may not get a second chance.

What remains is empirical validation, beginning with pilot data to determine whether constrained allocation distributions distinguish known moral framework differences. What also remains is the institutional discipline not to let a failed post-hoc attempt close the door on the correct approach. If the alignment community's first test of diverse moral signal uses the wrong architectural integration, the resulting conclusion -- that diverse signal "doesn't work" -- will be wrong, and it may be irreversible. The one-way door is the risk this paper asks the field to see.

---

## Addendum A: Dimensional Robustness

The four structural dimensions described in Section 3 are derived from Haidt's Moral Foundations Theory and Darwall's second-person standpoint. Critics contest MFT's foundation taxonomy, and the risk of post-hoc unification -- mapping any theory onto the same four dimensions through interpretive flexibility -- is real. A companion document demonstrates in detail that the same four dimensions emerge independently from Shweder's Autonomy-Community-Divinity triad (Shweder et al. 1997), Gray and Schein's Theory of Dyadic Morality (Gray & Schein 2012), and Curry's Morality-as-Cooperation framework (Curry et al. 2019), with explicit discussion of where the mappings are tight, where they require interpretation, and where they strain. The dimensions survive these alternative decompositions because they describe structural axes along which moral frameworks vary, not content-level triggers. If MFT were replaced by any of these alternatives, the classification function's decision procedure would remain unchanged. The companion document is available as supplementary material.

---

## Notes on Positionality

*This proposal emerges from practical experience with moral framework diversity, not from academic training in any of the fields it engages. Before age 25, the author lived in seven U.S. states and Germany, experiencing regional and national moral cultures that were substantially more distinct forty years ago than they are today. As a classroom instructor teaching technical material, the author learned that different analogies activate different frameworks in different learners -- a pedagogical version of this paper's argument. As a Patient Care Technician in a teaching hospital emergency department, the author observed how cultural background shaped consequential moral decisions under pressure. As a consultant across the United States, Canada, Australia, India, and Switzerland, the author repeatedly encountered the same business problems framed as fundamentally different moral questions depending on whose framework was in the room. As a member of an interracial family, the distance between moral frameworks is not an academic observation but a daily navigation problem. The author welcomes collaboration with researchers who can contribute the formal ML frameworks needed to develop this proposal further.*

---

*Acknowledgment: The author developed this paper in extended collaboration with Claude (Anthropic, Opus). The author provided the core problem identification (that moral framework divergence is alignment signal, not noise), the architectural vision (that a classification function should read that signal), the structural constraints (that demographic diversity is not framework diversity, that the instrument must work in digitally disconnected communities), the plasticity integration argument and its connection to the data quality literature, and domain-specific insights shaped by lived experience (the punctuality example, the pizza/scarcity observation, the I/O capacity argument for static weights, the kindergarten-to-plasticity parallel). The well-poisoning risk framing emerged from dialogue: the author identified the underlying concern (that a failed post-hoc attempt would justify exporting WEIRD values globally), and the "one-way door" framing and the three specific failure modes were developed collaboratively. The author's mother identified Tennant et al. as relevant prior work and contributed the scarcity/stewardship observation that grounds the intra-cultural framework variation argument. Claude contributed the formal architecture: the three-category taxonomy, the variance-weighted reward formalization, connections to Rawls and Sunstein, identification of Sorensen et al., the plasticity literature, and the perspectivist NLP literature as positioning references, the classification pipeline design, and the dimensional robustness argument across alternative moral psychologies. The author evaluated each contribution against practical experience and domain understanding, accepted or modified it, and bears responsibility for the final argument.*

---

## References

Awad, E., Dsouza, S., Kim, R., et al. (2018). The Moral Machine experiment. *Nature*, 563(7729), 59-64.

Bai, Y., Kadavath, S., Kundu, S., et al. (2022). Constitutional AI: Harmlessness from AI feedback. *arXiv:2212.08073*.

Bartels, S. A., Michael, S., Roupetz, S., et al. (2018). Making sense of child, early and forced marriage among Syrian refugee girls. *BMJ Global Health*, 3(1), e000509.

Bartels, S. A., Michael, S., Vahedi, L., et al. (2019). SenseMaker as a monitoring and evaluation tool. *Evaluation and Program Planning*, 77, 101715.

Basile, V., Cabitza, F., Campagner, A., & Fell, M. (2021). We need to consider disagreement in evaluation. In *Proceedings of the 1st Workshop on Benchmarking: Past, Present and Future*, pp. 15-21. ACL.

Casper, S., Davies, X., Shi, C., et al. (2023). Open problems and fundamental limitations of reinforcement learning from human feedback. *Transactions on Machine Learning Research*. arXiv:2307.15217.

Conitzer, V., Freedman, R., Heitzig, J., et al. (2024). Position: Social choice should guide AI alignment in dealing with diverse human feedback. In *ICML*, PMLR 235.

Curry, O. S., Mullins, D. A., & Whitehouse, H. (2019). Is it good to cooperate? Testing the theory of morality-as-cooperation in 60 societies. *Current Anthropology*, 60(1), 47-69.

Darwall, S. (2006). *The Second-Person Standpoint: Morality, Respect, and Accountability.* Harvard University Press.

Dohare, S., Hernandez-Garcia, J. F., Lan, Q., et al. (2024). Loss of plasticity in deep continual learning. *Nature*, 632(8026), 768-774.

Dryzek, J. S., Bachtiger, A., Chambers, S., et al. (2019). The crisis of democracy and the science of deliberation. *Science*, 363(6432), 1144-1146.

Durmus, E., Nguyen, K., Liao, T. I., et al. (2024). Towards measuring the representation of subjective global opinions in language models. In *COLM 2024*.

Fornaciari, T., Uma, A., Paun, S., et al. (2021). Beyond black & white: Leveraging annotator disagreement via soft-label multi-task learning. In *NAACL-HLT*, pp. 2591-2597.

Gabriel, I., & Keeling, G. (2025). A matter of principle? AI alignment as the fair treatment of claims. *Philosophical Studies*, 182(7), 1951-1973.

Gray, K., & Schein, C. (2012). Two minds vs. two philosophies: Mind perception defines morality and dissolves the debate between deontology and utilitarianism. *Review of Philosophy and Psychology*, 3(3), 405-423.

Gunasekar, S., Zhang, Y., Anber, J., et al. (2023). Textbooks Are All You Need. *arXiv:2306.11644*.

Gyekye, K. (2010). African ethics. In E. N. Zalta (Ed.), *Stanford Encyclopedia of Philosophy*.

Haidt, J. (2012). *The Righteous Mind: Why Good People Are Divided by Politics and Religion.* Vintage Books.

Henrich, J. (2020). *The WEIRDest People in the World.* Farrar, Straus and Giroux.

Huang, S., Siddarth, D., Lovitt, L., et al. (2024). Collective Constitutional AI: Aligning a language model with public input. *FAccT '24*. arXiv:2406.07814.

Hwang, K.-K. (2001). The deep structure of Confucianism: A social psychological approach. *Asian Philosophy*, 11(3), 179-204.

Lyle, C., Rowland, M., & Dabney, W. (2023). Understanding plasticity in neural networks. In *ICML*.

Lyle, C., Zheng, Z., Nikishin, E., et al. (2024). Disentangling the causes of plasticity loss in neural networks. *arXiv:2402.18762*.

Miller, J. G., & Bersoff, D. M. (1992). Culture and moral judgment: How are conflicts between justice and interpersonal responsibilities resolved? *Journal of Personality and Social Psychology*, 62(4), 541-554.

Mills, C. W. (1997). *The Racial Contract.* Cornell University Press.

Nikishin, E., Schwarzer, M., D'Oro, P., et al. (2022). The primacy bias in deep reinforcement learning. In *ICML*, PMLR 162:16828-16847.

Rawls, J. (1993). *Political Liberalism.* Columbia University Press.

Shweder, R. A., Much, N. C., Mahapatra, M., & Park, L. (1997). The "big three" of morality (autonomy, community, divinity). In A. Brandt & P. Rozin (Eds.), *Morality and Health* (pp. 119-169). Routledge.

Sorensen, T., Moore, J., Fisher, J., et al. (2024). Position: A roadmap to pluralistic alignment. In *ICML*, PMLR 235:46280-46302.

Sunstein, C. R. (1996). *Legal Reasoning and Political Conflict.* Oxford University Press.

Tennant, E., Hailes, S., & Musolesi, M. (2024). Hybrid approaches for moral value alignment in AI agents: a manifesto. *arXiv:2312.01818*.

Uma, A., Fornaciari, T., Hovy, D., et al. (2021). Learning from disagreement: A survey. *Journal of Artificial Intelligence Research*, 72, 1385-1470.

Van der Merwe, S. E., Biggs, R., Preiser, R., et al. (2019). Making sense of complexity: Using SenseMaker as a research tool. *Systems*, 7(2), 25.

Yan, Y., Lou, X., Li, J., et al. (2024). Reward-robust RLHF in LLMs. *arXiv:2409.15360*.

Zhou, C., Liu, P., Xu, P., et al. (2023). LIMA: Less is more for alignment. In *NeurIPS 2023*.
