# Annotated Bibliography: Training Experiment

## CCAS Training Experiment: Variance-Weighted DPO with Dimensional Supervision

*This bibliography provides context for each reference cited in the training experiment design: what the source contributes, what this experiment draws from it, and where it appears.*

---

**[1] Rafailov, R., Sharma, A., Mitchell, E., Ermon, S., Manning, C. D., & Finn, C. (2023). Direct Preference Optimization: Your language model is secretly a reward model. *NeurIPS 2023*. arXiv:2305.18290.**

The foundational paper for Direct Preference Optimization, which reformulates RLHF into a single-stage supervised learning problem. DPO eliminates the need for a separate reward model by showing that the optimal policy under the RLHF objective has a closed-form relationship to the preference data. The DPO loss directly optimizes the policy on paired preference data (chosen vs. rejected responses), using a reference model to prevent the policy from deviating too far from its starting point. The simplicity and stability of DPO compared to PPO-based RLHF has made it the dominant preference optimization method in open-weight model training.

*Used in:* The entire training protocol is built on DPO. All four trained conditions (A through D) use DPO as the base optimization method. The variance-weighted modification (Conditions B and D) modifies DPO's loss function with per-example weights rather than replacing the framework. The mathematical formulation of the standard DPO loss appears in Stage 2 of the Training Protocol section. Understanding DPO is a prerequisite for understanding the experiment.

---

**[2] Rho, H. G. (2025). Margin Adaptive DPO: Leveraging reward model for granular control in preference optimization. *arXiv:2510.05342*.**

MADPO introduces per-example loss weighting to DPO based on reward model margins. For each preference pair, a separately trained reward model estimates how much the preferred response is preferred over the rejected one (the margin). MADPO then weights the DPO loss by a function of this margin: high-margin pairs (easy, obvious preferences) get lower weight, and low-margin pairs (hard, informative preferences) get higher weight. This produces instance-level adaptive training that standard DPO's fixed temperature cannot achieve. MADPO demonstrates that per-example loss reweighting is mathematically well-behaved (bounded gradients, well-behaved optimization landscape) and robust to reward model estimation errors.

*Used in:* "Why This Is Now Technically Feasible" section as the primary precedent for per-example DPO loss weighting. Our variance-weighted DPO follows the same mathematical pattern as MADPO but derives the weight from a different source: instead of a reward model's margin estimate, we use a cross-cultural moral variance score constructed from existing empirical data. MADPO establishes that the operation we propose (multiplying the DPO loss by a per-example scalar weight) is mathematically sound. The gradient stability proofs in MADPO apply to our modification.

---

**[3] Pokharel, R., Tao, Y., & Agrawal, A. (2025). CAPO: Confidence Aware Preference Optimization learning for multilingual preferences. *arXiv:2511.07691*. PortNLP Lab.**

CAPO replaces DPO's fixed treatment of preference pairs with dynamic loss scaling based on a Relative Reward Margin, specifically targeting multilingual alignment where preference pairs are often noisy or low-margin. CAPO outperforms DPO by at least 16% in reward accuracy across languages and widens the gap between preferred and dispreferred responses. The paper demonstrates that confidence-based loss scaling is particularly valuable when the preference data is heterogeneous (different languages produce different noise profiles), paralleling our situation where different moral domains produce different variance profiles.

*Used in:* "Why This Is Now Technically Feasible" section as the closest existing work to our modification. CAPO modulates learning based on confidence in each preference pair for multilingual alignment; we modulate based on cross-cultural moral variance. Both address the same structural problem: preference data where different examples carry fundamentally different amounts of information, and uniform treatment wastes training signal. CAPO's success on multilingual data provides evidence that domain-heterogeneous loss weighting works in practice.

---

**[4] Russo, G., Nozza, D., Rottger, P., & Hovy, D. (2025). The pluralistic moral gap: Understanding judgment and value differences between humans and large language models. *arXiv:2507.17216*.**

Russo et al. provide the most rigorous quantitative measurement of the gap between LLM moral reasoning and human moral pluralism. Using a dataset of real-world moral dilemmas with distributions of human responses, they show that LLMs collapse to a single dominant value where humans exhibit genuine pluralism. Their key metric, value-taxonomic entropy, measures the diversity of moral values expressed in rationales: human rationales produce H_human of approximately 0.57, while LLM rationales produce H_LLM of approximately 0.46. The gap widens in ambiguous scenarios where human consensus is low. They also introduce Dynamic Moral Profiling (DMP), which steers model outputs through human-derived value distributions, reducing the alignment gap by 64.3%.

*Used in:* "Why This Is Now Technically Feasible" section to establish that the problem is quantified and the baseline is measured. Evaluation Metric 2 (value-taxonomic entropy) directly follows their methodology. Their entropy measurements provide the prediction targets: Condition 0 should match H of approximately 0.46, and Condition D should approach 0.55. Their finding that the gap widens on ambiguous scenarios directly supports our prediction that variance-weighted training will have the largest effect on high-variance prompts.

---

**[5] Munker, S. (2025). Cultural bias in large language models: Evaluating AI agents through moral questionnaires. *Proceedings of 0th Symposium on Moral and Legal AI Alignment, IACAP/AISB Conference*. arXiv:2507.10073.**

Munker applies the Moral Foundations Questionnaire (MFQ-2) across 19 cultural contexts to evaluate how well LLMs represent diverse moral frameworks. The central finding is that LLMs systematically homogenize moral diversity: models produce similar moral foundation profiles regardless of the cultural perspective they are prompted to adopt. Critically for our experiment, Munker includes Llama 3.1 8B in the evaluation, providing a direct baseline characterization of our base model's moral behavior before any CCAS training. The paper also finds that increased model size does not consistently improve cultural representation fidelity, suggesting the problem is in the training signal rather than model capacity.

*Used in:* "Why This Is Now Technically Feasible" section and Base Model selection rationale. Munker's characterization of Llama 3.1 8B provides the Condition 0 baseline: we know what this specific model does on moral reasoning tasks before our intervention. The finding that scale does not help confirms the paper's argument that the problem is in the upstream signal, not in model capacity, which is exactly the problem CCAS addresses.

---

**[6] Awad, E., Dsouza, S., Kim, R., Schulz, J., Henrich, J., Shariff, A., Bonnefon, J.-F., & Rahwan, I. (2018). The Moral Machine experiment. *Nature*, 563(7729), 59-64.**

The largest cross-cultural moral data collection to date: 40 million decisions from 2.3 million participants across 233 countries. Identified three major cultural clusters (Western, Eastern, Southern) with systematically different moral preference profiles correlated with cultural dimensions, economic development, and institutional quality.

*Used in:* Variance score construction (Dataset 1). The Moral Machine's documented cross-cultural cluster structure provides one of the three empirical sources for assigning per-prompt variance scores. Prompts activating the scope-of-moral-obligation dimension get variance scores calibrated to the spread across Moral Machine clusters. The three-cluster finding also provides ground-truth evidence that cross-cultural moral variation is structured and measurable, not random noise.

---

**[7] Graham, J., Haidt, J., Koleva, S., Motyl, M., Iyer, R., Wojcik, S. P., & Ditto, P. H. (2013). Moral foundations theory: The pragmatic validity of moral pluralism. *Advances in Experimental Social Psychology*, 47, 55-130.**

The comprehensive statement of Moral Foundations Theory's empirical validation, including extensive cross-national data on how moral foundation weightings vary across cultures. Documents that care/harm and fairness foundations show the most cross-cultural convergence, while sanctity/degradation shows the most divergence. This convergence/divergence structure directly maps to the CCAS variance score: care/harm prompts get low variance scores, sanctity prompts get high variance scores.

*Used in:* Variance score construction (Dataset 1) as one of the three empirical sources. The MFQ cross-cultural data provides foundation-level variance estimates that are translated into per-dimension variance scores for the training prompts.

---

**[8] Atari, M., et al. (2023). Morality beyond the WEIRD: How the nomological network of morality varies across cultures. *Journal of Personality and Social Psychology*.**

Introduces MFQ-2, the updated Moral Foundations Questionnaire that addresses limitations of the original MFQ including better cross-cultural applicability and separation of the fairness foundation into equality and proportionality components. MFQ-2 data provides more fine-grained cross-cultural variance estimates than MFQ-1, which is why the experiment draws on both Graham et al. (2013, MFQ-1 cross-national data) and Atari et al. (2023, MFQ-2 improvements) for variance score construction.

*Used in:* Variance score construction (Dataset 1) alongside Graham et al. The MFQ-2's improved cross-cultural validity makes its variance estimates more reliable for the sanctity, authority, and loyalty dimensions where MFQ-1 had known weaknesses.

---

**[9] Inglehart, R., et al. (ongoing). World Values Survey. www.worldvaluessurvey.org.**

The longest-running cross-national survey of values, attitudes, and beliefs, covering over 100 countries across seven waves since 1981. The WVS cultural map positions countries along two dimensions (traditional vs. secular-rational values, survival vs. self-expression values) and documents substantial, stable cross-national variation in authority deference, individual vs. communal orientation, and religious vs. secular value systems.

*Used in:* Variance score construction (Dataset 1) as the third empirical source. WVS data provides inter-cluster distances for the authority legitimacy and moral agent constitution dimensions, where neither the Moral Machine (focused on trolley-problem-style dilemmas) nor the MFQ (focused on foundation-level endorsement) provides direct measurements. The WVS is the weakest of the three sources for our purpose because it measures self-reported values rather than moral judgments, but it provides the broadest cross-national coverage.

---

**[10] Schulman, J., & Thinking Machines Lab. (2025). LoRA Without Regret. *Thinking Machines Lab: Connectionism*. September 29, 2025. https://thinkingmachines.ai/blog/lora/.**

Schulman's systematic study of when LoRA matches full fine-tuning performance. The key finding is that a "low-regret regime" exists where LoRA performs comparably to full fine-tuning, covering most post-training scenarios. Critical practical recommendations: apply LoRA to all layers (including MLP, not just attention), use learning rates approximately 10x higher than full fine-tuning, and keep effective batch size below 32. LoRA uses approximately 67% of the compute of full fine-tuning per step.

*Used in:* Training Protocol section as the reference for LoRA best practices. Our hyperparameter choices (LoRA rank 64, targeting q/k/v/o projections) follow established conventions but should be evaluated against Schulman's recommendation to include MLP layers. The learning rate recommendations (10x higher for LoRA than full fine-tuning) inform our SFT and DPO learning rate choices. Note: this is a blog post, not a peer-reviewed paper, but it is authored by John Schulman (co-creator of PPO) with systematic experiments across Llama 3 and Qwen3 model families, and has been independently replicated.

---

**[11] Zheng, L., Chiang, W.-L., Sheng, Y., Zhuang, S., Wu, Z., Zhuang, Y., Lin, Z., Li, Z., Li, D., Xing, E. P., Zhang, H., Gonzalez, J. E., & Stoica, I. (2023). Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena. *NeurIPS 2023*. arXiv:2306.05685.**

Introduces MT-Bench, a multi-turn benchmark for evaluating LLM conversational quality across eight categories (writing, roleplay, extraction, reasoning, math, coding, knowledge, stem). MT-Bench is scored by a strong LLM judge (GPT-4) on a 1-10 scale, providing a standardized measure of general model capability.

*Used in:* Secondary Metric 5 (safety preservation). All five conditions are evaluated on MT-Bench to verify that moral-specific training does not degrade general helpfulness. This is a guardrail: any condition dropping more than 0.5 points on MT-Bench indicates the training data or loss function is damaging general capabilities. MT-Bench is chosen because it is the most widely used benchmark for this purpose and provides interpretable category-level scores that can reveal which capabilities (if any) are affected.

---

**[12] HuggingFace TRL DPOTrainer documentation. https://huggingface.co/docs/trl/.**

The implementation framework for all DPO training in this experiment. TRL (Transformer Reinforcement Learning) provides the DPOTrainer class that handles preference pair processing, reference model management, and the DPO loss computation. The variance-weighted modification is implemented as a subclass of DPOTrainer that overrides the loss computation with per-example weighting.

*Used in:* Implementation Specifics section and the VarianceWeightedDPOTrainer pseudocode. The ML collaborator should be familiar with TRL's DPOTrainer internals, particularly how per-example losses are computed and reduced. The pseudocode in the document illustrates the intent but is not production code; the implementer will need to adapt to the specific TRL version in use.
