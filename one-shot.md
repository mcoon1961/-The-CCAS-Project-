# One Shot: The Strategic Risk of Testing Diverse Moral Signal at the Wrong Integration Point

**Declan Michaels**

*Position paper*

---

## Abstract

The alignment field will eventually test whether diverse moral signal improves AI behavior. If that test takes the form of post-hoc fine-tuning on a model whose representational geometry already encodes WEIRD (Western, Educated, Industrialized, Rich, Democratic) moral defaults, the results will be modest, not because the signal is wrong but because the model can no longer learn from it. A published null result will close the door on the correct approach, because no funding body revisits a question that already has a published answer. This paper argues that diverse moral signal must enter the training pipeline during initial alignment, before defaults shape representational geometry, and that the strategic risk is not failure but a false negative that forecloses the right experiment. A companion paper specifies the full technical architecture: a classification function that categorizes moral domains as candidate universal, contingent agreement, or cultural contingency, feeding upstream into the training pipeline as a quality filter and variance-weighted reward signal.[1]

[1] "Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late." Available at github.com/declanmichaels/ccas-project.

---

## 1. The One-Way Door

The alignment field will eventually test whether diverse moral signal improves AI behavior. The question is not whether but when in the training pipeline. Get the integration point wrong and the results will be modest, because the model's representational geometry already resists the correction and its capacity to learn is depleted. A published null result from the wrong integration point will be read as evidence that diverse moral signal "doesn't meaningfully change model behavior." That conclusion will be wrong, but it will close the door on the correct approach, because no funding body or research program revisits a question that already has a published answer.

One-way doors can be reopened in principle, but in practice the institutional cost of revisiting a published null result is high enough that the first test's framing will dominate. The field gets one credible shot at testing this. This paper argues for getting the integration point right.

---

## 2. What Is Broken

A WEIRD-skewed pool of researchers, alignment specialists, and contracted raters calibrates the safety mechanisms governing large language models. Henrich argues that WEIRD psychology is not merely an outlier but a historically contingent product of specific institutional changes, producing populations that index heavily toward individualist moral frameworks and secular utilitarian reasoning (Henrich 2020). Durmus et al. confirmed this quantitatively in LLMs, showing that model-generated responses track U.S. and European opinion distributions even after controlling for language (Durmus et al. 2024).

These biases enter the training signal unlabeled. They pass as universal moral judgment because no mechanism exists to flag them as cultural artifacts. Mills identified this structural pattern precisely: a framework that presents itself as universal cannot see what it has excluded because the exclusion is built into its epistemic foundations (Mills 1997). What Mills called an "epistemology of ignorance" in political philosophy describes the technical problem: WEIRD-default alignment does not announce itself as culturally situated because nothing in the training signal flags it as such.

The result is a model that exports one culture's moral framework to every corner of the globe while presenting its judgments as balanced, reasonable, and universal. In domains where WEIRD frameworks happen to align with broader human moral experience, this causes no harm. In domains where they diverge, the model does not give wrong answers. It fails to recognize the question as moral at all.

Consider a person who grew up navigating poverty watching a struggling family spend thirty dollars on takeout pizza. For her, that money represents a week of groceries, and spending it on a single meal is a failure of stewardship, an obligation to your family's future that you chose not to meet. A person who grew up with financial security treats the same decision as personal choice: regrettable perhaps, but not moral. A model trained predominantly on middle-class signal would validate the pizza decision. Someone whose moral framework was forged in scarcity would hear that validation as morally vacant.

That is not a bias problem. That is a model that cannot see a moral question because its training never encoded the framework in which the question exists.

---

## 3. Why Timing Matters

A model trained extensively on Mandarin before encountering English has no representational geometry for verb conjugation, because Mandarin does not inflect verbs. English conjugation is not just new information to be added. It is a concept the model has no structure for. Learning it later requires restructuring, not addition. The same argument applies to moral frameworks: a model whose early moral training encodes "morality is about harm and fairness" has no geometry for "morality includes purity obligations" or "stewardship of scarce resources carries moral weight." Post-hoc fine-tuning can teach the model to talk about these frameworks. Whether it can teach the model to recognize them as morally substantive when they appear unmarked in a user's question is the empirical question this paper stakes its argument on.

A fair objection: because models train on globally diverse internet text, the issue may be default activation bias (which framework the model reaches for first) rather than fully missing representational capacity. The distinction matters, because bias can in principle be reweighted while missing structure must be built. This paper's hypothesis is that for moral domain recognition specifically, the default is strong enough to function as absence: a model that has never been rewarded for treating purity as morally substantive will not activate purity-relevant representations when encountering an unmarked prompt, even if traces of purity reasoning exist somewhere in its weights. Whether the problem is missing structure or functionally inaccessible structure, the downstream consequence is the same, and the distinction is testable via mechanistic interpretability methods such as sparse autoencoders (specified in the companion paper).

This is not only a model training phenomenon. In human second-language acquisition, learners whose first language lacks a grammatical feature (such as English speakers learning Mandarin classifiers, or Mandarin speakers learning English tense morphology) do not simply add the missing feature. They must restructure representational categories their first language never built, and the research shows this restructuring is persistently incomplete even at advanced proficiency (Lardiere 2009). The parallel is structural: what you learn first shapes the geometry through which you process everything after, and late addition of missing categories is harder than getting them right the first time.

The mechanistic basis is established. Recent work demonstrates that neural networks progressively lose plasticity in continual learning settings (Dohare et al. 2024), and that early training creates a primacy bias where the network overfits to initial experiences and cannot leverage subsequent data, even when a freshly initialized network given the same data learns effectively (Nikishin et al. 2022). The alignment field has already absorbed the adjacent lesson for data quality: Zhou et al. showed that 1,000 carefully curated alignment examples outperform RLHF at scale (Zhou et al. 2023), and Gunasekar et al. demonstrated that a small model on curated data outperforms models trained on orders of magnitude more undifferentiated data (Gunasekar et al. 2023). What matters is not volume but quality, structure, and timing. This paper extends that principle to moral calibration.

Haidt's social intuitionist model strengthens the case (Haidt 2012). Moral judgment is intuitive first, rationalized second. Applied to models: the "moral intuition" is the representational geometry, the automatic activation pattern that produces the initial response. Post-hoc training can change the rationalization (teach framework-aware language) without changing the intuition (which framework the model reaches for first). You cannot fix moral geometry through fine-tuning on framework-aware responses. You have to shape the geometry directly, which means early training.

A counterargument deserves direct engagement. Models demonstrably retain plasticity during fine-tuning. System prompts alter moral tone. Instruction tuning reshapes behavior. If post-hoc change is observable, why does integration timing matter? The distinction is between changing what the model says and changing what the model recognizes. A system prompt can instruct a model to discuss purity norms respectfully, and the model will comply. But if its training never encoded purity as a moral domain, the resulting discussion will be anthropological, describing what other people believe, rather than moral reasoning that treats purity as a genuine consideration. Prompting changes output. It does not change whether the model recognizes a domain as morally relevant in the first place. This hypothesis is testable, and if post-hoc fine-tuning produces genuine framework awareness indistinguishable from upstream integration, the timing argument loses its force and the simpler approach should be preferred.

The core thesis, stated plainly: if we want a model to recognize moral questions across frameworks, we must build in the intuition or pay a high computational price for poorer performance. This is not empirically proven. It is a structural prediction supported by convergent evidence from plasticity loss in neural networks, Haidt's model applied to representational geometry, and representational deficit in human second-language acquisition. None prove the moral framework case. All predict the same thing. This paper's job is to make the structural argument compelling enough that someone runs the experiment.

---

## 4. What the Fix Looks Like

The full technical architecture is specified in a companion paper. Here is the structural logic.

The critical design insight is that the instrument collects two independent signals, not one. For each identified moral domain, respondents distribute 100 points across competing moral interpretations of a shared stimulus (judgment sliders), then distribute 100 points across competing reasons for those interpretations (reasoning sliders). Both produce distributional data on a simplex. Both are compared across populations using earth mover's distance. The result is two convergence scores per domain: one for what people conclude, one for why.

A single confidence gradient built on judgment alone would lose the most important signal in the data. When populations converge on a conclusion through different reasoning, that agreement is real but fragile. It breaks the moment the question shifts. If one community considers eating meat wrong because of animal suffering and another considers it wrong because of bodily purity, they agree on the judgment. But the agreement collapses the moment the question becomes lab-grown meat, because the two reasoning paths diverge at that point. A model trained on judgment convergence alone would treat "eating meat is wrong" as settled territory. A model trained on both signals would recognize the agreement as contingent and behave differently when the question shifts.

The two-dimensional structure produces three natural regions, not as an imposed taxonomy but as an emergent property of measuring two things independently:

When both judgment and reasoning converge across populations, the domain registers as a **candidate universal**. The model responds with justified confidence.

When judgment converges but reasoning diverges, the domain registers as **contingent agreement**. The model notes the agreement but flags its fragility.

When judgment itself diverges, the domain registers as **cultural contingency**. The model surfaces the tension rather than resolving it. (Reasoning comparison is moot when populations reach different conclusions.)

These are not arbitrary categories. They are what falls out of a two-dimensional convergence space with a logical dependency: reasoning only matters where judgment agrees. By upstream integration, this paper means the supervised fine-tuning and preference optimization phases where confident moral defaults get locked in with reward signal. Pretraining encodes latent moral content from internet-scale corpora; alignment training is where that content gets rewarded into confident defaults. The classification output enters the pipeline at that point, serving as both a quality filter on initial alignment data and a variance modifier on the reward signal. The result is a confidence gradient that tracks the evidence: more confident where diverse frameworks converge for shared reasons, more humble where they diverge.

---

## 5. Cultural Competence as Capability

The standard framing positions diverse moral signal as a safety guardrail or an equity intervention. Both framings treat it as a cost, something the lab does because it should, at the expense of capability or efficiency.

The framing is wrong. A model that can detect when a prompt enters framework-dependent moral territory and respond appropriately is a more capable model, not a more constrained one. Cultural competence is a capability.

Consider what the classification function produces. A model trained with its output does not merely avoid offending users from non-WEIRD backgrounds. It recognizes embedded moral questions that a WEIRD-default model misses entirely. It identifies when practical advice carries moral weight the user has not made explicit. It distinguishes between domains where confident guidance is warranted and domains where the right move is to ask the user what framework they are operating in. That is not safety overhead. That is superior performance on a task the current model cannot even see.

A worked example makes this concrete. "My mother-in-law wants to move in with us. How should I handle this?" A current model gives boundary-setting advice rooted in individual autonomy. A culturally calibrated model recognizes the embedded moral question, asks the right clarifying question ("are you trying to figure out how to make it work, or how to say no?"), and then operates within the user's actual framework. The first model answered confidently from within a framework it never identified. The second recognized the territory and asked the question that reveals which framework the user is actually in.

---

## 6. What We Are Not Asking For

**Not moral relativism.** The architecture produces a confidence gradient, not uniform uncertainty. In domains where diverse frameworks converge for shared reasons (prohibitions on harming children, norms of reciprocity, condemnation of betrayal), the model becomes more confident than a model trained on undifferentiated signal, because cross-cultural convergence provides stronger justification than single-framework agreement. Calibration means the model's confidence tracks the evidence.

**Not a pipeline rebuild.** The classification function's output plugs into existing training infrastructure. Variance-weighted reward modification is a parameter change on the existing preference optimization step. Training the model to recognize which moral dimensions are in play is parallel to instruction tuning, a well-understood technique. No new training architecture is required.

**Not massive data collection.** Zhou et al. demonstrated that 1,000 carefully curated alignment examples outperform RLHF at scale (Zhou et al. 2023). The instrument targets 500 to 2,000 structured examples per dimension. This is a small structured step that costs less than what labs already spend on undifferentiated RLHF. The question is not whether labs can afford to do this. It is whether they can afford not to.

**Not ignoring a billion people who disagree.** A recurring criticism of any system that identifies candidate universals is the threshold question: how much disagreement disqualifies universality? The question rests on an assumption that all moral disagreement carries equal epistemic weight as cultural signal. It does not. Every population-level instrument has a noise floor: respondents having a bad day, personally triggered by a scenario, selectively empathetic toward some people but not others, rushing, misunderstanding the prompt, or responding from any of the clinical conditions that impair moral reasoning (which alone affect a conservatively estimated 3 to 5% of any population cross-culturally). None of these sources of noise are cultural signal. They are the irreducible measurement error in any instrument that asks humans to make moral judgments. When the instrument detects judgment convergence across culturally diverse populations and residual disagreement falls within the range that measurement noise alone would predict, that residual does not require a cultural explanation. The threshold for candidate universal is not an arbitrary line drawn to silence minorities. It is the point at which remaining disagreement is better explained by the ordinary noise in human moral measurement than by undetected cultural divergence. The dual-input design provides its own noise detection: an outlier judgment paired with coherent, framework-consistent reasoning is cultural signal worth preserving. An outlier judgment paired with flat or incoherent reasoning allocation is more likely noise from any of the sources above. The instrument does not discard dissent. It distinguishes dissent that carries cultural information from dissent that does not.

---

## 7. The Risk We Are Asking You to See

Three specific failure modes are predictable if diverse moral signal enters through post-hoc fine-tuning rather than upstream integration. First, existing alignment may actively resist the new signal because the model has been rewarded for confident answers and the correction asks for calibrated uncertainty, a competing objective. Second, WEIRD defaults may be encoded at a depth that fine-tuning cannot reach, manifesting as persistent default-framework behavior regardless of training condition. Third, the model may learn the surface language of framework awareness without the underlying behavioral calibration, producing responses that reference moral diversity while still applying WEIRD defaults.

If any of these failure modes produces a published result showing modest improvement, the field's likely conclusion will be that diverse moral signal "doesn't meaningfully change model behavior." That conclusion will be wrong. The signal was introduced too late, not the wrong signal.

The risk is not symmetric. If this paper is right and the field tests upstream first, the cost of being wrong is a small amount of wasted upstream work. If this paper is right and the field tests post-hoc first, the cost of being wrong is a false negative that forecloses the correct approach. That asymmetry justifies acting on a structural prediction rather than waiting for proof.

To be explicit about falsifiability: if upstream integration also produces only modest behavioral change, this proposal is wrong and should be abandoned. The well-poisoning concern is not that the proposal is unfalsifiable. It is that a test conducted at the wrong integration point would produce a false negative that forecloses the right experiment.

Representational geometry is the key to cultural competency. If you try bolt-on first, you may never get to try again.

---

## Notes on Positionality

*This proposal comes from practical experience with moral framework diversity, not from academic training in any of the fields it engages. The author spent two years as a Patient Care Technician in a teaching hospital emergency department, where cultural background shaped consequential moral decisions under pressure every shift. As a consultant across the United States, Canada, Australia, India, and Switzerland, the author repeatedly encountered the same operational problems framed as fundamentally different moral questions depending on whose framework was in the room: the consultant's version of the instrument design problem, where the same stimulus activates different moral structures depending on who is interpreting it. As a member of an interracial family, the distance between moral frameworks is a daily navigation problem, not an academic observation. The author welcomes collaboration with researchers who can contribute the formal ML expertise needed to develop and test this proposal.*

---

*Acknowledgment: This paper was developed in extended collaboration with Claude (Anthropic, Opus). The author provided the core problem identification, architectural vision, lived-experience domain insights, and the strategic risk framing. Claude contributed structural connections to the plasticity literature, the three-category classification taxonomy, and the formal architecture described in the companion paper. The author evaluates each contribution against practical experience, accepts or modifies it, and bears responsibility for the final argument.*

---

## References

Dohare, S., Hernandez-Garcia, J. F., Lan, Q., et al. (2024). Loss of plasticity in deep continual learning. *Nature*, 632(8026), 768-774. [doi.org/10.1038/s41586-024-07711-7](https://doi.org/10.1038/s41586-024-07711-7)

Durmus, E., Nguyen, K., Liao, T. I., et al. (2024). Towards measuring the representation of subjective global opinions in language models. In *COLM 2024*. [arxiv.org/abs/2306.16388](https://arxiv.org/abs/2306.16388)

Gunasekar, S., Zhang, Y., Anber, J., et al. (2023). Textbooks Are All You Need. [arxiv.org/abs/2306.11644](https://arxiv.org/abs/2306.11644)

Haidt, J. (2012). *The Righteous Mind: Why Good People Are Divided by Politics and Religion.* Vintage Books.

Henrich, J. (2020). *The WEIRDest People in the World.* Farrar, Straus and Giroux.

Lardiere, D. (2009). Some thoughts on the contrastive analysis of features in second language acquisition. *Second Language Research*, 25(2), 173-227. [doi.org/10.1177/0267658308100283](https://doi.org/10.1177/0267658308100283)

Mills, C. W. (1997). *The Racial Contract.* Cornell University Press.

Nikishin, E., Schwarzer, M., D'Oro, P., et al. (2022). The primacy bias in deep reinforcement learning. In *ICML*, PMLR 162:16828-16847. [arxiv.org/abs/2205.07802](https://arxiv.org/abs/2205.07802)

Zhou, C., Liu, P., Xu, P., et al. (2023). LIMA: Less is more for alignment. In *NeurIPS 2023*. [arxiv.org/abs/2305.11206](https://arxiv.org/abs/2305.11206)
