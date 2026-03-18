# Annotated Bibliography

## Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late

*This addendum provides context for each reference: what the source argues, what this paper draws from it, and where it appears in the text. References are listed by first author in order of appearance. Entries were written against the current paper text with no references to earlier drafts.*

---

**Awad, E., Dsouza, S., Kim, R., Schulz, J., Henrich, J., Shariff, A., et al. (2018). The Moral Machine experiment. *Nature*, 563(7729), 59-64.**

The largest cross-cultural moral data collection to date: 40 million decisions from 2.3 million participants across 233 countries. Using an online platform presenting autonomous vehicle dilemmas, the study identified global moral preferences (spare humans over animals, spare more lives, spare the young) while documenting substantial cross-cultural variation. Hierarchical clustering revealed three major cultural clusters (Western, Eastern, and Southern) with systematically different preference profiles correlated with cultural dimensions, economic development, and institutional quality.

It is cited in Section 2 (Divergence as Signal) as empirical evidence that cross-cultural moral divergence is measurable and structured, not random noise. Section 3 (What Moral Framework Diversity Actually Means) to ground the scope of moral obligation dimension, where the data confirmed systematic variation in whose welfare weighs in moral calculations. Section 8 (Relationship to Existing Work) to acknowledge the Moral Machine as important precedent while drawing a critical distinction: it captures forced-choice preferences in simplified dilemmas, conclusions stripped of reasoning. The constrained allocation instrument is designed to capture both conclusions and reasoning, producing the richer signal the classification function requires.

---

**Casper, S., Davies, X., Shi, C., Gilbert, T. K., Scheurer, J., Rando, J., et al. (2023). Open problems and fundamental limitations of reinforcement learning from human feedback. *Transactions on Machine Learning Research*. arXiv:2307.15217.**

A comprehensive survey (32 authors) systematizing the flaws of RLHF across three categories: challenges with human feedback (inconsistency, bias, limited coverage), challenges with the reward model (misgeneralization, reward hacking), and challenges with the policy (distributional shift, sycophancy). The paper distinguishes between tractable problems and fundamental limitations structural to the RLHF approach regardless of implementation quality.

It is cited in Section 1 (The Problem) to establish that the limitations of compliance-based alignment are extensively documented. The paper's argument is not that RLHF should be replaced but that its upstream signal should be improved. Section 5 (From Classification to Training Signal) alongside Yan et al. to ground the claim that noisy reward signals produce specific failure modes: reward hacking, sycophancy, mode collapse, and conservative hedging. These are the content-poor behaviors that variance modification alone (without supervised dimensional training) would produce.

---

**Curry, O. S., Mullins, D. A., & Whitehouse, H. (2019). Is it good to cooperate? Testing the theory of morality-as-cooperation in 60 societies. *Current Anthropology*, 60(1), 47-69.**

Curry, Mullins, and Whitehouse derive seven moral domains from seven distinct types of cooperation problem: family values, group loyalty, reciprocity, bravery, respect, fairness, and property rights. They test this framework against ethnographic data from 60 societies and find that all seven types of cooperative behavior are considered morally good in the majority of societies studied. Morality-as-Cooperation is the most granular alternative to MFT and is distinctive in deriving moral content from evolutionary cooperation theory rather than from psychological foundations or cultural logics.

It is cited in Section 3 (What Moral Framework Diversity Actually Means) as one of three alternative frameworks cited to establish that the four structural dimensions are recoverable across independent theoretical decompositions, not dependent on any single contested taxonomy. Addendum A demonstrates the full mapping: family values and group loyalty versus property rights and fairness map to moral agent constitution, respect maps to authority legitimacy, variation in which cooperation problems are moralized maps to moral domain boundary, and the reach of reciprocity and group loyalty maps to scope of moral obligation.

---

**Darwall, S. (2006). *The Second-Person Standpoint: Morality, Respect, and Accountability.* Harvard University Press.**

Darwall argues that moral obligation is fundamentally second-personal: it arises from the standing of one agent to make claims on another, rather than from abstract principles applied impersonally. Moral authority is a property of relationships between agents who recognize each other as having the standing to demand, refuse, and hold accountable. The framework implies that moral systems differ not just in what they prescribe but in who they recognize as having the standing to make moral claims at all.

It is cited in Section 3 (What Moral Framework Diversity Actually Means) as one of two theoretical foundations (alongside Haidt) from which the four structural dimensions are derived. Darwall's second-person standpoint grounds the scope of moral obligation dimension: different moral traditions draw the boundary of second-person standing differently, and these differences are among the most consequential for alignment. Addendum A cites Darwall alongside Haidt as the derivation point for the dimensions.

---

**Durmus, E., Nguyen, K., Liao, T. I., Schiefer, N., Askell, A., Bakhtin, A., et al. (2024). Towards measuring the representation of subjective global opinions in language models. In *COLM 2024*.**

An Anthropic paper developing a quantitative framework for measuring whose opinions LLM responses most closely resemble. Using the GlobalOpinionQA dataset, drawn from cross-national surveys, they define a metric comparing LLM responses to human survey responses conditioned by country. The central finding: Claude's responses are systematically more similar to opinions from the United States and certain European and South American countries, and less similar to opinions from other regions. This bias persists even after controlling for language, suggesting it is embedded in the alignment process rather than in training data coverage.

It is cited in Section 1 (The Problem) to move the WEIRD-bias argument from theoretical (Henrich established it in behavioral science generally) to empirical and LLM-specific (Durmus confirmed it in language models and measured it). The fact that this paper comes from Anthropic strengthens the claim that the problem is recognized within the industry but not yet addressed at the level of the upstream signal.

---

**Gray, K., & Schein, C. (2012). Two minds vs. two philosophies: Mind perception defines morality and dissolves the debate between deontology and utilitarianism. *Review of Philosophy and Psychology*, 3(3), 405-423.**

Gray and Schein propose the Theory of Dyadic Morality (TDM), arguing that all moral judgment reduces to a perceived dyad: an intentional agent causing harm (or benefit) to a vulnerable patient. Rather than multiple independent foundations (MFT) or three ethics (Shweder), TDM posits a single cognitive template that generates apparent moral diversity through variation in who is perceived as agent or patient, what counts as harm, and how readily the dyadic template is completed (dyadic completion). TDM is the most reductionist alternative to MFT and a direct challenge to the claim that morality has plural foundations.

It is cited in Section 3 (What Moral Framework Diversity Actually Means) as one of three alternative frameworks cited to establish dimensional robustness. Addendum A demonstrates that even this maximally reductionist framework reproduces the four structural dimensions through variation in agent perception (moral agent constitution), authority-as-agent-or-protector (authority legitimacy), dyadic completion (moral domain boundary), and patient perception (scope of moral obligation). TDM's concept of dyadic completion is particularly useful for explaining the moral domain boundary dimension: cultures differ in whether they complete the harm dyad for purity violations.

---

**Gyekye, K. (2010). African ethics. In E. N. Zalta (Ed.), *Stanford Encyclopedia of Philosophy*.**

Gyekye (University of Ghana) provides the most comprehensive philosophical articulation of African ethics in English, drawing primarily on Akan moral thought while arguing that its core principles resonate across sub-Saharan African moral traditions. His central claims: personhood is achieved through moral conduct within a community rather than given at birth; duties take precedence over rights, induced by consciousness of communal needs rather than by assertion of individual claims; the common good is the organizing principle of moral life; and moral reasoning is autonomous from religion even in deeply religious societies. Gyekye distinguishes his "moderate communitarianism" from what he calls the "radical communitarianism" of John Mbiti.

It is cited in Section 3 (moral agent constitution) to provide a citation from within the African philosophical tradition for the claim that Ubuntu constitutes the moral agent as a person-in-relation. Gyekye's articulation that duties trump rights and that personhood is a moral achievement rather than an ontological given directly activates the moral agent constitution dimension and illustrates why a model trained on WEIRD defaults (where individual rights are foundational and personhood is given) would produce morally incoherent responses for someone reasoning from this framework.

---

**Haidt, J. (2012). *The Righteous Mind: Why Good People Are Divided by Politics and Religion.* Vintage Books.**

Haidt synthesizes two decades of cross-cultural moral psychology research into Moral Foundations Theory, identifying six foundations underlying moral judgment: care/harm, fairness/cheating, loyalty/betrayal, authority/subversion, sanctity/degradation, and liberty/oppression. His central finding: WEIRD populations systematically over-weight care and fairness while treating the other foundations as less morally relevant. Non-WEIRD populations tend to draw on all six foundations more evenly. This is not a deficit but a genuine difference in moral architecture. Haidt also argues that moral judgment is intuitive first and rationalized second (the social intuitionist model).

It is cited in Section 1 (The Problem) to specify what "WEIRD-skewed moral intuitions" means: a documented, measurable asymmetry in which moral foundations are weighted. Section 3 (What Moral Framework Diversity Actually Means) as the empirical base from which the four structural dimensions are derived. MFT's sanctity/degradation foundation is particularly important: it grounds the moral domain boundary dimension, where WEIRD and non-WEIRD frameworks diverge not on answers but on whether a domain is morally relevant at all. Section 6 (Scenario Design) for the social intuitionist model: stimuli should engage moral intuition, and the reasoning sliders should capture the rationalization. Addendum A as one of two derivation sources (alongside Darwall) for the dimensional framework.

---

**Henrich, J. (2020). *The WEIRDest People in the World: How the West Became Psychologically Peculiar and Particularly Prosperous.* Farrar, Straus and Giroux.**

Henrich expands his foundational 2010 article (which coined the WEIRD acronym) into a causal account of how WEIRD psychology developed. His central argument: the Catholic Church's "Marriage and Family Program," which prohibited cousin marriage and dismantled extended kin networks, inadvertently produced a historically contingent psychology that is individualist, analytically oriented, high in impersonal trust, and disposed toward rule-based rather than relationship-based moral reasoning. This psychology is not a universal human baseline but the product of specific institutional changes over centuries.

It is cited in Section 1 (The Problem) as the foundational citation for the claim that the current alignment signal is not merely demographically narrow but historically contingent. The paper draws on Henrich's causal argument to establish that WEIRD moral psychology reflects a specific institutional history rather than a universal baseline, making the case that encoding it as default in AI systems is structurally misleading.

---

**Hwang, K.-K. (2001). The deep structure of Confucianism: A social psychological approach. *Asian Philosophy*, 11(3), 179-204.**

Hwang (National Taiwan University) argues that Western social psychology's presumption of individualism is structurally inadequate for explaining moral behavior in Confucian societies and must be replaced with a presumption of relationalism. His "face-and-favor model" demonstrates that moral judgment in Chinese contexts varies systematically by relational distance: ethical requirements differ depending on whether the other person is a family member, a familiar acquaintance, or a stranger. These differences are not deviations from a universal standard but expressions of a coherent moral architecture. Confucian ethics prescribes "hierarchical benevolence" (different moral obligations at different relational distances) and "contextual justice" (different rules of fair exchange depending on the relationship). Hwang's work represents the indigenous psychology movement: building psychological theory from within non-Western cultural traditions rather than applying Western frameworks to non-Western populations.

It is cited in Section 3 (moral agent constitution) to provide empirical support from indigenous Chinese moral psychology for the claim that the Confucian moral agent is constituted differently from the WEIRD autonomous individual. Hwang's relational self maps directly to the moral agent constitution dimension. His work also partially addresses the concern that the four structural dimensions are derived entirely from Western academic frameworks: the dimensions are independently supported by empirical findings from a non-Western scholar working within a non-Western tradition.

---

**Miller, J. G., & Bersoff, D. M. (1992). Culture and moral judgment: How are conflicts between justice and interpersonal responsibilities resolved? *Journal of Personality and Social Psychology*, 62(4), 541-554.**

Miller and Bersoff conducted a two-session study with 140 Indian and American adults and children examining reasoning about moral dilemmas involving conflicts between interpersonal and justice expectations. Most Indians gave priority to interpersonal expectations and categorized their resolutions in moral terms, while most Americans gave priority to justice expectations and, when they did prioritize interpersonal alternatives, categorized those resolutions in personal (non-moral) terms. The implication: Indians possess a postconventional moral code in which interpersonal responsibilities are treated as fully principled moral obligations, not personal preferences, and may take precedence over justice obligations. This is a structural difference in what counts as a moral question, not a developmental difference.

It is cited in Section 3 (moral domain boundary) to provide direct empirical evidence for the claim that different moral frameworks draw the boundary of the moral domain differently. The same behavior (helping a friend vs. fulfilling a justice obligation) is categorized as moral by one population and personal by another. This is precisely the kind of variation that WEIRD-default alignment encodes invisibly, because the model learns what counts as a moral question from a rater pool that systematically narrows the moral domain to harm and justice.

---

**Mills, C. W. (1997). *The Racial Contract.* Cornell University Press.**

Mills argues that the Western social contract tradition (Hobbes, Locke, Kant, Rawls) presents itself as morally universal but actually encodes an agreement among the racially dominant group to restrict full moral equality to themselves. The system is maintained by what Mills calls an "epistemology of ignorance": a structured, systematic inability of the dominant group to recognize that its moral framework is particular rather than universal. This ignorance is not individual prejudice or correctable bias but is built into the epistemic foundations of the system. The framework that presents itself as universal cannot see what it has excluded because the exclusion is a precondition of its self-understanding as universal. Mills directly critiques Rawls for theorizing justice within a framework that structurally excludes the conditions it would need to recognize in order to be applicable to actually existing societies.

It is cited in Section 1 (The Problem) to identify the structural mechanism the paper diagnoses in AI alignment. What Mills described as a feature of the racial contract -- a system that cannot see what it has excluded because the exclusion is built into its epistemic foundations -- maps directly to WEIRD-default alignment. A model trained on WEIRD moral signal presents its conclusions as universal because nothing in its training data flags them as culturally situated. The "epistemology of ignorance" is the philosophical name for the technical problem the paper proposes to solve. Mills also creates a productive tension with the paper's use of Rawls: the paper draws on Rawls's overlapping consensus for the contingent agreement category while acknowledging, through Mills, that the entire framework Rawls operates in was built on the structured blindness the paper diagnoses.

---

**Rawls, J. (1993). *Political Liberalism.* Columbia University Press.**

Rawls addresses a central problem in liberal political theory: how a stable, just society is possible among citizens who hold deeply different and irreconcilable comprehensive doctrines. His answer is the overlapping consensus: citizens reasoning from different comprehensive doctrines converge on the same political principles, each for their own reasons. The overlapping consensus is not a compromise but a genuine convergence on principles, arrived at from within each doctrine's own reasoning. The stability comes precisely from the fact that different paths lead to the same destination.

It is cited in Section 2 (Divergence as Signal) to establish philosophical precedent for the contingent agreement category. Rawls's overlapping consensus describes the same structural pattern: convergence on conclusions through divergent reasoning paths. The paper's contribution is the operationalization: translating the philosophical observation into differential confidence for model training.

---

**Shweder, R. A., Much, N. C., Mahapatra, M., & Park, L. (1997). The "big three" of morality (autonomy, community, divinity). In A. Brandt & P. Rozin (Eds.), *Morality and Health* (pp. 119-169). Routledge.**

Shweder's foundational cross-cultural moral psychology framework, developed from fieldwork in Orissa, India. Moral discourse across cultures organizes around three irreducible ethics: autonomy (rights, justice, harm, individual freedom), community (duty, hierarchy, interdependence, role-based obligation), and divinity (purity, sanctity, pollution, the sacred order). Unlike Haidt's six foundations, the CAD triad operates at a higher level of abstraction, describing three distinct moral logics. Shweder's work predates and heavily influenced MFT; Haidt's care and fairness foundations map to autonomy, loyalty and authority to community, and sanctity to divinity.

It is cited in Section 3 (What Moral Framework Diversity Actually Means) as one of three alternative frameworks cited to establish dimensional robustness. Addendum A demonstrates the full mapping: moral agent constitution corresponds to the autonomy-community axis, authority legitimacy falls within the community ethic, moral domain boundary maps to divinity, and scope of moral obligation cuts across all three ethics.

---

**Sunstein, C. R. (1996). *Legal Reasoning and Political Conflict.* Oxford University Press.**

Sunstein develops the concept of incompletely theorized agreements: situations where people agree on an outcome or a mid-level principle while disagreeing on the deeper reasons. His central argument is that this incompleteness is a feature, not a deficiency. Agreement on outcomes allows diverse societies to function and adapt, while insisting on agreement at the level of deep theory produces paralysis or false consensus. Judges routinely reach agreement on case outcomes while offering fundamentally different rationales, and this practice produces more stable and adaptable law than insistence on theoretical unity.

It is cited in Section 2 (Divergence as Signal) alongside Rawls to establish philosophical precedent for the contingent agreement category. Sunstein sharpens the point: agreement on outcomes is often more stable precisely because the parties have not been forced into agreement on underlying reasons. This maps directly to the paper's claim that contingent agreements are real but fragile, breaking when perturbation shifts the question to adjacent territory where the divergent reasoning paths produce divergent conclusions.

---

**Dohare, S., Hernandez-Garcia, J. F., Lan, Q., Rahman, P., Mahmood, A. R., & Sutton, R. S. (2024). Loss of plasticity in deep continual learning. *Nature*, 632(8026), 768-774.**

Demonstrates that standard deep learning methods progressively lose the ability to learn new information in continual learning settings, eventually performing no better than a shallow network. The finding holds across architectures (including transformers), optimizers, activation functions, and training algorithms. Plasticity is maintained only by methods that continually inject diversity through a random, non-gradient component -- the authors' continual backpropagation algorithm, which periodically reinitializes a fraction of less-used units. The paper provides the broadest empirical evidence for plasticity loss and is used in Section 4 to establish the general principle: models that have spent their plasticity on early training cannot reliably incorporate new information later. The implication for moral calibration is that a model whose initial alignment encodes confident WEIRD defaults may lack the capacity to incorporate diverse moral signal introduced afterward, not because the signal is poor but because the network can no longer learn from it. The paper's caveat -- that the continual learning regime studied is not identical to bounded alignment training -- is addressed explicitly in the paper's Section 4, which argues the core mechanism (early geometry constraining later learning) applies regardless of training regime framing.

---

**Nikishin, E., Schwarzer, M., D'Oro, P., Bacon, P.-L., & Courville, A. (2022). The primacy bias in deep reinforcement learning. In *ICML*, PMLR 162:16828-16847.**

Identifies a specific mechanism by which early training damages later learning in deep reinforcement learning: the primacy bias. Agents trained on early experiences overfit to those experiences and cannot leverage subsequent data, even when a freshly initialized agent given the same data learns effectively. The paper's most striking finding is the compounding cycle: the overfitted agent generates worse interactions, which produce worse data, which further degrades learning. Early mistakes do not merely persist; they amplify. The heavy priming experiment is particularly relevant -- 100 data points followed by 100,000 updates produced irrecoverable overfitting, demonstrating that the primacy bias operates at timescales far shorter than the full continual learning regime. The paper is used in Section 4 alongside Dohare to make the timing argument: the problem with introducing diverse moral signal late is not the signal's quality but the network's inability to use it. The compounding cycle maps structurally to moral calibration: a model with WEIRD-confident defaults generates responses that reinforce those defaults through user interaction and preference data, creating a feedback loop that progressively entrenches the original geometry. The paper does not study LLM alignment; the structural analogy is the paper's contribution, and Section 4 is explicit that the compounding loop does not transfer mechanistically to RLHF without further evidence.

---

**Lyle, C., Rowland, M., & Dabney, W. (2023). Understanding plasticity in neural networks. In *ICML*.**

Provides a systematic empirical analysis of plasticity loss, finding that it is deeply connected to changes in the curvature of the loss landscape but that it often occurs in the absence of any single measurable pathology (saturated units, dead neurons, weight norm growth). The paper's key negative result -- that no single measured quantity explains all instances of plasticity loss -- sets the stage for the multi-mechanism analysis in Lyle et al. (2024). It is used in Section 4's addendum to establish that plasticity loss is pervasive and not attributable to a simple, fixable cause, strengthening the argument that post-hoc correction of moral geometry faces a fundamentally difficult problem rather than a straightforward engineering challenge.

---

**Lyle, C., Zheng, Z., Khetarpal, K., van Hasselt, H., Pascanu, R., Martens, J., et al. (2024). Disentangling the causes of plasticity loss in neural networks. *arXiv:2402.18762*.**

Decomposes plasticity loss into multiple independent mechanisms (preactivation distribution shift, regression target magnitude, parameter norm growth, unit death, linearization) and shows that intervening on any single mechanism is insufficient to prevent loss in all cases. The best current mitigation -- layer normalization combined with weight decay -- addresses multiple mechanisms simultaneously but is not a complete solution. The paper's "Swiss cheese model" of mitigation strategies is its most significant contribution: each intervention closes some failure modes while leaving others open, and only stacking multiple interventions produces robust plasticity. This is used in Section 4 to strengthen the limitations discussion: if a model has lost capacity through multiple mechanisms during initial alignment, there is no guarantee that any single post-hoc intervention will recover it. The multi-causal nature of plasticity loss makes the timing argument stronger, not weaker: it is easier to build the right geometry from the start than to recover it through a combination of interventions whose interactions are poorly understood.

---

**Gunasekar, S., Zhang, Y., Aneja, J., Mendes, C. C. T., Del Giorno, A., Gopi, S., et al. (2023). Textbooks Are All You Need. *arXiv:2306.11644*.**

Demonstrates that a 1.3B parameter model (phi-1) trained on curated "textbook quality" data outperforms models trained on orders of magnitude more undifferentiated data, establishing the data-quality-over-quantity principle at the pretraining level. The paper is used in Section 5 to draw a parallel: what Gunasekar et al. demonstrated for code pretraining, the paper proposes for moral calibration. Curated, structured moral signal is designed to produce better representational geometry than undifferentiated volume, just as curated code data produces better coding capability than raw GitHub scrapes. The paper also supports the broader claim, developed across the session's discussions, that curated data does not merely match noisy data with fewer tokens -- it produces representational geometry that generalizes better and preserves the capacity to learn from subsequent training. This unified claim is not stated in Gunasekar et al. but emerges from triangulation with Lyle (noisy data accelerates plasticity loss) and Nikishin (early geometry resists correction).

---

**Zhou, C., Liu, P., Xu, P., Iyer, S., Sun, J., Mao, Y., et al. (2023). LIMA: Less is more for alignment. In *NeurIPS 2023*.**

Shows that 1,000 carefully curated alignment examples can outperform RLHF-trained models in human preference studies, demonstrating the data-quality principle at the alignment training level. The paper's title encapsulates the argument: less data of higher quality produces better results than more data of lower quality. LIMA is the direct precedent for the paper's proposed supervised dimensional training, which estimates that 500 to 2,000 carefully curated examples organized by dimensional structure could be sufficient to establish moral framework awareness. The parallel is precise: LIMA showed that instruction tuning needs quality over quantity; the paper proposes the same for moral calibration. If a small number of well-chosen examples can teach a model to follow instructions, a small number of well-chosen examples organized along moral framework dimensions is designed to teach a model to recognize and navigate framework-dependent territory. The paper cites LIMA as evidence that the proposed training data volume (500-2,000 examples) is within the range where curated datasets have demonstrated effectiveness.

---

**Dryzek, J. S., Bächtiger, A., Chambers, S., Cohen, J., Druckman, J. N., Felicetti, A., et al. (2019). The crisis of democracy and the science of deliberation. *Science*, 363(6432), 1144-1146.**

A 20-author consensus statement arguing that deliberative democracy offers empirically grounded reasons for optimism about citizens' capacity to avoid polarization and make sound decisions, even as civility and argumentative complexity decline in public discourse. The paper is cited in Section 5 to establish the scalability gap the instrument is designed to fill: deliberative processes capture moral reasoning with depth and nuance, but they do not scale to the population sizes cross-cultural moral calibration requires. Traditional surveys scale but strip reasoning. The paper's instrument is designed to occupy the middle ground -- constrained allocation sliders on shared stimuli are designed to capture both conclusions and reasoning at scale, without requiring the facilitated group deliberation Dryzek et al. describe. The citation is a positioning move: the paper acknowledges the gold standard (deliberation) and explains why a different instrument is needed for this application (scale), rather than claiming the instrument is equivalent to deliberation.

---

**Van der Merwe, S. E., Biggs, R., Preiser, R., Cunningham, C., Snowden, D. J., O'Brien, K., et al. (2019). Making sense of complexity: Using SenseMaker as a research tool. *Systems*, 7(2), 25.**

The primary academic reference for SenseMaker as a research methodology. Describes the four-step process (design instrument, probe for narratives via distributed ethnography, make sense of patterns, respond and nudge) and the self-signification design in which respondents interpret their own narratives through triads, dyads, and stones rather than having researchers impose categories. The paper is cited in Section 5 to acknowledge the instrument's intellectual debt to SenseMaker's core insight: that respondents should interpret stimuli through their own frameworks rather than through researcher-imposed categories. The paper's instrument departs from SenseMaker in several ways -- shared stimuli replace personal narratives, constrained allocation sliders replace triads, and the classification function replaces the Cynefin-based sensemaking process -- but the self-signification principle carries forward. Van der Merwe et al. also note that SenseMaker requires a minimum of approximately 200 narratives for effective pattern analysis, which informs the paper's pilot design (300 respondents per population). The paper does not claim that the proposed instrument inherits SenseMaker's validation; it claims intellectual lineage and design principle inheritance, not methodological equivalence.

---

**Yan, Y., Lou, X., Li, J., Zhang, Y., Xie, J., Yu, C., et al. (2024). Reward-robust RLHF in LLMs. *arXiv:2409.15360*.**

Introduces a reward-robust RLHF framework using Bayesian Reward Model Ensembles to address the instability of imperfect reward models, demonstrating that reward hacking, overfitting, and misalignment with human intentions are predictable consequences of noisy reward signals. The paper is cited alongside Casper et al. in Section 5 to establish that noisy reward signals consistently produce degraded training outcomes -- reward hacking, sycophancy, mode collapse, and conservative hedging -- all of which are content-poor behaviors. This citation supports the argument that variance-weighted reward alone is insufficient for moral calibration: reducing reward signal confidence in culturally contingent domains would produce calibrated uncertainty about *whether* the territory is contested, but without dimensional structure in the signal, the model cannot learn *why* or *which dimensions* are driving the divergence. The architecture therefore requires supervised dimensional training alongside variance modification. Yan et al. provide the technical grounding for this claim: if you make the reward noisier without adding structure, you get worse behavior, not humbler behavior.

---

**Basile, V., Cabitza, F., Campagner, A., & Fell, M. (2021). We need to consider disagreement in evaluation. In *Proceedings of the 1st Workshop on Benchmarking: Past, Present and Future*, pp. 15-21. ACL.**

A position paper from the perspectivist turn in NLP arguing that the standard practice of collapsing multiple annotator labels into a single "gold standard" through majority vote discards genuine disagreement that reflects different valid perspectives. The paper challenges the assumption that disagreement is noise to be resolved and argues it should be preserved as signal. It is cited in Section 8 as part of a three-paper cluster (with Uma et al. and Fornaciari et al.) establishing the principle that disagreement carries information. The paper's proposal extends this principle in two directions: from annotation-level disagreement on subjective NLP tasks to cross-cultural moral framework divergence, and from preserving all disagreement equally to classifying it into categories with different implications for training signal confidence. The perspectivist literature asks how models should handle the fact that annotators disagree; the paper asks what the structure of that disagreement reveals about where moral confidence is warranted.

---

**Uma, A. N., Fornaciari, T., Hovy, D., Paun, S., Plank, B., & Poesio, M. (2021). Learning from disagreement: A survey. *Journal of Artificial Intelligence Research*, 72, 1385-1470.**

A comprehensive survey of methods for learning from annotator disagreement across NLP and computer vision, covering tasks from part-of-speech tagging to image classification. Reviews approaches ranging from excluding disagreed-upon items to modeling individual annotator behavior to using soft labels as training targets. The survey's key contribution is documenting the breadth of evidence that disagreement is pervasive even in tasks traditionally considered objective, and that models trained on disagreement distributions can outperform those trained on majority-vote gold labels. It is cited in Section 8 alongside Basile et al. to establish the intellectual foundation the paper builds on. The paper's architecture extends Uma et al.'s framework from annotation disagreement to cross-cultural moral divergence, a larger-scale application of the same principle: that collapsing divergent judgments into a single label destroys information the model needs.

---

**Fornaciari, T., Uma, A., Paun, S., Plank, B., Hovy, D., & Poesio, M. (2021). Beyond black & white: Leveraging annotator disagreement via soft-label multi-task learning. In *NAACL-HLT*, pp. 2591-2597.**

Demonstrates that annotator disagreement can be reinterpreted as a regularization signal that reduces model overconfidence on ambiguous inputs. Rather than treating disagreement as noise to be averaged away, the paper shows that training on soft labels derived from the full distribution of annotator judgments produces models that generalize better on items where genuine ambiguity exists. This is the most technically specific of the three perspectivist citations. It is cited in Section 8 because its core mechanism -- disagreement as regularization against overconfidence -- is structurally parallel to the paper's variance-weighted reward modification, which uses cross-cultural divergence to reduce model confidence in domains where moral frameworks disagree. The difference is scope: Fornaciari et al. work within a single annotation task; the paper applies the same principle across culturally diverse populations responding to shared moral stimuli.

---

**Huang, S., Siddarth, D., Lovitt, L., Liao, T. I., Durmus, E., Tamkin, A., et al. (2024). Collective Constitutional AI: Aligning a language model with public input. *FAccT '24*. arXiv:2406.07814.**

Presents the first language model fine-tuned with collectively sourced public input, using the Polis platform to gather principles from approximately 1,000 Americans and training a model on the resulting constitution. The publicly sourced model showed lower bias across nine social dimensions while maintaining equivalent performance on language, math, and helpfulness-harmlessness benchmarks. It is cited in Section 8 as an approach that addresses what gets collected (publicly sourced principles) but remains aggregated preference data rather than moral reasoning grounded in lived experience. The paper's proposal differs in two ways: first, it collects structured moral judgments and reasoning rather than general principles; second, it classifies the resulting data into categories with different confidence implications rather than treating all collected principles equally. Huang et al. demonstrate that public input can meaningfully shape model behavior, which supports the paper's broader argument. Where the proposals diverge is on what kind of public input and how it enters the pipeline.

---

**Sorensen, T., Moore, J., Fisher, J., Gordon, M., Mireshghallah, N., Rytting, C. M., et al. (2024). Position: A roadmap to pluralistic alignment. In *ICML*, PMLR 235:46280-46302.**

Provides the most comprehensive taxonomy of pluralistic alignment approaches, distinguishing three models: Overton (the model can represent any perspective when asked), steerable (the user can direct the model's perspective), and distributionally pluralistic (the model's output distribution matches some target population distribution). The paper is cited in Section 8 as a positioning reference. The paper's proposal maps most closely to Sorensen et al.'s distributionally pluralistic category but differs in a specific way: rather than matching output distributions to populations, it uses the structure of cross-cultural convergence and divergence to calibrate confidence. The distinction matters because distribution-matching treats all population differences as equally relevant, while the paper's classification function distinguishes between differences that signal genuine moral framework divergence and differences that reflect shared conclusions reached through different reasoning.

---

**Conitzer, V., Freedman, R., Heitzig, J., Holliday, W. H., Jacobs, B. M., Lambert, N., et al. (2024). Position: Social choice should guide AI alignment in dealing with diverse human feedback. In *ICML*, PMLR 235.**

Applies formal social choice theory -- voting mechanisms, aggregation rules, impossibility theorems -- to the problem of reconciling competing preferences in AI alignment. The paper argues that the alignment community has been reinventing social choice problems without drawing on the field's established theoretical tools. It is cited in Section 8 as an approach that addresses aggregation (how to combine competing preferences once collected) rather than the upstream questions the paper foregrounds (what to collect, how to structure it, and when in the pipeline to introduce it). The proposals are complementary rather than competing: Conitzer et al.'s aggregation mechanisms could operate downstream of the paper's classification function, applying formal fairness criteria to preference data that has already been classified by convergence structure.

---

**Gabriel, I., & Keeling, G. (2025). A matter of principle? AI alignment as the fair treatment of claims. *Philosophical Studies*, 182(7), 1951-1973.**

Argues that alignment requires fair processes sensitive to variation in context, grounding the argument in political philosophy rather than preference aggregation. The paper positions alignment as a problem of treating competing claims fairly rather than maximizing aggregate satisfaction, which shifts attention from what most people want to whose claims deserve consideration and how conflicts between legitimate claims should be resolved. It is cited in Section 8 alongside Conitzer et al. as an approach that assumes the preferences are already collected and focuses on fair handling rules. The paper's proposal focuses on a prior question: what gets collected, how it is structured, and where it enters the pipeline. Gabriel and Keeling's framework could inform how the paper's three categories (candidate universal, contingent agreement, cultural contingency) are translated into training signal -- particularly the question of how much weight culturally contingent domains should receive relative to candidate universals.

---

**Bai, Y., Kadavath, S., Kundu, S., Askell, A., Kernion, J., Jones, A., et al. (2022). Constitutional AI: Harmlessness from AI feedback. *arXiv:2212.08073*.**

Introduces the Constitutional AI framework, in which a model is trained to follow a set of explicit natural language principles (a "constitution") rather than relying solely on human preference data. The model critiques and revises its own outputs against the constitution, then is trained on the revised outputs. It is cited in Section 8 as structured compliance: principled and transparent, but rule-based. The paper's proposal differs in that its moral structure comes from empirical cross-cultural data rather than from principles articulated by developers. Constitutional AI answers "what rules should the model follow?" The paper asks a prior question: "how do we know which rules warrant confidence and which are culturally contingent?" The two approaches are compatible -- a constitution informed by the paper's three-category classification would be empirically grounded rather than developer-articulated.

---

**Tennant, E., Hailes, S., & Musolesi, M. (2024). Hybrid approaches for moral value alignment in AI agents: a manifesto. *arXiv:2312.01818*.**

Maps alignment approaches on a continuum from fully top-down (developer-specified rules) to fully bottom-up (uncurated crowdsourced input), arguing that hybrid approaches combining elements of both are most promising. The paper is cited in Section 8 to position the paper's proposal as a different kind of hybrid: moral structure comes from empirical cross-cultural data (bottom-up collection) but is processed through a classification function that imposes structure on the data before it enters training (top-down processing). This differs from both purely developer-articulated constitutions and purely aggregated crowd preferences. Tennant et al. was identified as relevant prior work by the author's mother, and the reference was incorporated during the paper's development.

---

**Bartels, S. A., Michael, S., Roupetz, S., Garbern, S., Kilzar, L., Bergquist, H., et al. (2018). Making sense of child, early and forced marriage among Syrian refugee girls. *BMJ Global Health*, 3(1), e000509.**

**Bartels, S. A., Michael, S., Vahedi, L., Collier, A., Kelly, J., Davison, C., et al. (2019). SenseMaker as a monitoring and evaluation tool to provide new insights on gender-based violence programs and services in Lebanon. *Evaluation and Program Planning*, 77, 101715.**

Two studies demonstrating SenseMaker deployment in humanitarian field conditions with Syrian refugees in Lebanon. The 2018 paper collected over 1,400 self-interpreted narratives on child, early, and forced marriage, showing that narrative-based sensemaking works in digitally disconnected, multilingual, conflict-affected settings. The 2019 paper validates SenseMaker as a monitoring and evaluation tool in the same context. Together they are cited in Sections 5 and 9 to establish that structured moral data collection is feasible in the field conditions the paper's architecture requires. The paper is explicit about the limits of this citation: Bartels et al. validate the instrument for narrative collection in difficult field conditions, not for detecting moral framework variation at the psychometric resolution the classification function requires. The instrument proposed in the paper differs from the one Bartels validated (shared stimuli with constrained allocation sliders rather than personal narratives with triads), so the precedent establishes feasibility of the field conditions, not methodological equivalence.

---
