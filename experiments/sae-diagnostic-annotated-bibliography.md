# Annotated Bibliography: SAE Diagnostic Experiment

## CCAS Mechanistic Diagnostic: SAE-Based Validation of Training Effects

*This bibliography provides context for each reference cited in the SAE diagnostic experiment design: what the source contributes, what this experiment draws from it, and known limitations relevant to our application.*

---

**[1] Cunningham, H., Ewart, A., Riggs, L., Huben, R., & Sharkey, L. (2023). Sparse autoencoders find highly interpretable features in language models. *arXiv:2309.08600*. ICLR 2024.**

The foundational paper demonstrating that sparse autoencoders can resolve superposition in language models. Cunningham et al. trained SAEs on residual stream activations of Pythia-70M and Pythia-410M and showed that the learned features are more interpretable and more monosemantic than directions identified by alternative methods (PCA, ICA, random directions). Critically, they demonstrated that SAE features can pinpoint the features causally responsible for specific model behaviors (tested on the indirect object identification task) to a finer degree than previous circuit-level decompositions. The paper establishes the core methodology: unsupervised dictionary learning on model activations produces interpretable features that correspond to identifiable concepts.

*Used in:* Background section as the primary citation for the SAE methodology. Phase 1 (feature discovery) follows their approach of training SAEs on residual stream activations. The causal identification result motivates the experiment's premise that SAE features can reveal what a model is computing, not just what it is saying.

---

**[2] Templeton, A., Conmy, A., Marcus, J., Lindsey, J., Bricken, T., & Olah, C. (2024). Scaling monosemanticity: Extracting interpretable features from Claude 3 Sonnet. Anthropic, Transformer Circuits Thread.**

Anthropic's landmark scaling study, applying SAEs to Claude 3 Sonnet (a production-scale model). Found millions of interpretable features including features corresponding to specific concepts (the Golden Gate Bridge, deception, code errors, abstract reasoning patterns, and safety-relevant behaviors). Demonstrated that SAE-based interpretability scales to frontier models, though with significant computational cost. The paper also demonstrated feature steering: amplifying specific features changes model behavior in predictable ways (the "Golden Gate Claude" demonstration).

*Used in:* Background section as evidence that SAEs work at production model scale. The deception-related features are directly relevant: if SAEs can find features corresponding to deceptive behavior in Claude, they should in principle be able to find features corresponding to sycophantic moral framework wrapping in a fine-tuned Llama model (Phase 3). The feature steering demonstration motivates the natural follow-up to this experiment (causal verification via steering), noted in the Limitations section.

---

**[3] Lieberum, T., Rajamanoharan, S., Conmy, A., Smith, L., Sonnerat, N., Varma, V., Kramar, J., Dragan, A., Shah, R., & Nanda, N. (2024). Gemma Scope: Open sparse autoencoders everywhere all at once on Gemma 2. *arXiv:2408.05147*.**

Google DeepMind's release of pre-trained SAEs for every layer and sublayer of Gemma 2 models (2B and 9B), with multiple width-to-sparsity tradeoffs. The paper provides a template for systematically training SAEs across an entire model architecture and establishes evaluation metrics (reconstruction fidelity, sparsity, downstream loss, probe loss, and explanation scores). GemmaScope SAEs are openly released, enabling the research community to build on them rather than training from scratch.

*Used in:* Background section as the methodological template for training SAEs on open-weight models. The evaluation metrics established here (particularly downstream loss and probe performance) should be applied to our per-checkpoint SAEs to verify decomposition quality before proceeding to feature comparison. GemmaScope's open release model is the precedent for why LlamaScope SAEs exist for our base model.

---

**[4] He, Z., et al. (2024). LlamaScope: Extracting millions of features from Llama-3.1-8B with sparse autoencoders. *arXiv:2410.20526*.**

Pre-trained SAEs for Llama 3.1 8B, the base model used in the CCAS training experiment. LlamaScope provides SAE dictionaries across layers that can serve as initialization for our per-checkpoint SAE training (Phase 1). Using LlamaScope initialization rather than training from scratch provides the benefit of a mature dictionary as starting point while allowing adaptation to fine-tuned activation distributions.

*Used in:* Phase 1 (feature discovery) as the initialization source for per-checkpoint SAE training. The document explicitly addresses why pre-trained LlamaScope SAEs cannot be used directly as the decomposition tool for fine-tuned checkpoints (the SAE transfer problem): LoRA fine-tuning shifts the activation distribution, and a base-model SAE may misattribute activations in fine-tuned models rather than merely missing new features.

---

**[5] Gao, L., la Tour, T. D., Tillman, H., Goh, G., Troll, R., Radford, A., Sutskever, I., Leike, J., & Wu, J. (2024). Scaling and evaluating sparse autoencoders. OpenAI.**

OpenAI's systematic study of SAE scaling laws, training methodology, and evaluation. Introduces TopK SAEs (which use a hard top-k activation function rather than L1 regularization to enforce sparsity) and demonstrates that they improve the reconstruction-sparsity tradeoff compared to earlier methods. Establishes the relationship between SAE width, sparsity level, and downstream loss, showing clean power-law scaling. Provides the training methodology our experiment adopts.

*Used in:* Phase 1 (feature discovery) as the SAE training architecture. TopK SAEs are the recommended architecture for our per-checkpoint training because they provide better sparsity control (directly setting the number of active features) compared to L1-penalized alternatives, which is important when comparing feature activation patterns across model conditions.

---

**[6] Lindsey, J., Templeton, A., Marcus, J., Conerly, T., Batson, J., & Olah, C. (2024). Sparse crosscoders for cross-layer features and model diffing. Anthropic, Transformer Circuits Thread. October 25, 2024.**

Introduces crosscoders, a variant of SAEs that learn a shared dictionary across multiple model variants (or multiple layers of the same model). For model diffing, a crosscoder is trained on concatenated activations from a base model and its fine-tuned derivative, producing three categories of features: shared features (present in both models), base-model-specific features (present only in the base model), and fine-tuned-model-specific features (present only in the fine-tuned model). This directly solves the comparison problem: when you train separate SAEs on different model checkpoints, the dictionaries are different and features cannot be directly compared. A crosscoder produces a single dictionary in which features are automatically categorized by which model(s) they belong to.

*Used in:* Phase 2 (feature comparison across conditions) as the recommended method for comparing feature sets across the four ablation conditions. The crosscoder eliminates the methodological circularity that would arise from using either a single SAE (which can only find base-model features) or separate SAEs (which produce incomparable dictionaries). The model diffing application is the most directly relevant precedent for what this experiment proposes: understanding what fine-tuning changed inside the model.

*Known limitation:* This is a preliminary research update (described by the authors as "lab meeting" quality, not full paper rigor). Subsequent work (Mishra-Sharma et al., 2025; Minder et al., 2025) identified significant limitations. See [7].

---

**[7] Mishra-Sharma, S., Bricken, T., Lindsey, J., Jermyn, A., Marcus, J., Rivoire, K., Olah, C., & Henighan, T. (2025). Insights on crosscoder model diffing. Anthropic, Transformer Circuits Thread.**

**And: Minder, J., Dumas, C., Juang, C., Chughtai, B., & Nanda, N. (2025). Robustly identifying concepts introduced during chat fine-tuning using crosscoders. *arXiv:2504.02922*.**

These two papers (one from Anthropic, one from an independent group replicating and extending the crosscoder work) identify limitations of the crosscoder model diffing approach that are directly relevant to this experiment. Two theoretical issues are documented:

*Complete shrinkage:* The sparsity loss can force a feature's base-model decoder direction to zero norm even when the feature exists in the base model, falsely identifying it as fine-tuning-specific. This could cause our Phase 2 analysis to overcount "new" features in the CCAS-trained conditions.

*Latent decoupling:* The crosscoder may represent a shared concept using a fine-tuning-specific feature when the concept is actually encoded by a different combination of features in the base model. Again, this inflates the count of novel features.

Minder et al. develop a mitigation strategy (Latent Scaling) that detects spurious fine-tuning-specific features. Our experiment should apply this or a similar correction.

*Used in:* Not cited in the current document text but should inform the ML collaborator's implementation of Phase 2. Added to this bibliography as an important methodological caveat. The crosscoder approach is the best available method for cross-model feature comparison, but its results require validation against these known failure modes.

---

**[8] Marks, S., & Tegmark, M. (2023). The geometry of truth: Emergent linear structure in large language model representations of true/false datasets. *arXiv:2310.06824*.**

Marks and Tegmark study how LLMs internally represent the truth or falsehood of factual statements. They find clear linear structure in these representations and demonstrate that probes trained on one dataset generalize to different datasets. Critically for our experiment, they establish the methodology of extracting activations at the token position where the model has aggregated its complete understanding of the input (typically the end-of-clause or end-of-instruction token) and demonstrate that this position carries the most information about the model's internal assessment.

*Used in:* Phase 1 (feature discovery) to justify the choice of activation extraction position: the final token of the prompt, before generation begins. This follows the principle that end-of-instruction tokens aggregate the model's understanding of the problem. Ferrando et al. (2024, arXiv:2411.14257) subsequently adopted this same approach for extracting uncertainty-related directions from SAE decompositions, providing additional validation for our extraction methodology.

---

**[9] Shu, D., Wu, X., Zhao, H., Rai, D., Yao, Z., Liu, N., & Du, M. (2025). A survey on sparse autoencoders: Interpreting the internal mechanisms of large language models. In *Findings of the Association for Computational Linguistics: EMNLP 2025*, pp. 1690-1712. arXiv:2503.05613.**

The most comprehensive published survey of SAE methods as of early 2025. Covers SAE architecture variants (vanilla, gated, TopK, JumpReLU), training strategies, feature explanation methods (input-based and output-based), evaluation metrics (structural and functional), and applications to LLM behavior understanding and manipulation. Published at EMNLP 2025 Findings, giving it peer-review validation that most SAE work (published as blog posts or preprints) lacks.

*Used in:* Background section as the comprehensive reference for anyone needing to understand the SAE landscape. An ML collaborator unfamiliar with SAEs should read this survey first. The evaluation metrics section is particularly relevant: our experiment should report the same structural and functional metrics (reconstruction fidelity, sparsity, downstream loss, probe performance) established in the broader literature to allow comparison.

---

**[10] Smith, L., Rajamanoharan, S., Conmy, A., McDougall, C., Kramar, J., Lieberum, T., Shah, R., & Nanda, N. (2025). Negative results for SAEs on downstream tasks and deprioritising SAE research (GDM mech interp team progress update 2). AI Alignment Forum / Medium. March 26, 2025.**

The most significant published critique of SAE utility from within the mechanistic interpretability community. The Google DeepMind interpretability team reports that SAE features underperformed simple linear probes on the downstream task of detecting harmful intent in user prompts, including out-of-distribution generalization. Their conclusion: SAEs in their current form are "far from achieving" a canonical decomposition of model concepts, and it is "unclear if such true concepts even exist." The team announced they were deprioritizing fundamental SAE research.

The critique has several specific components relevant to this experiment: (a) SAE features that appear interpretable (they activate on semantically coherent inputs) may not be causally involved in the model's computation for those inputs; (b) SAEs may systematically miss or distort important concepts because they are inherently incomplete (the dictionary cannot capture everything); (c) concepts may be represented in noisy ways where small activations are not interpretable.

*Used in:* Limitations section, where the experiment engages this criticism directly. The honest response: (1) the experiment claims diagnostic evidence, not causal evidence, and inconsistency between conditions can rule out hypotheses even without causal proof; (2) the natural causal extension (steering experiments) is well-defined as a follow-up; (3) the geometric analyses (cosine similarity between feature directions, crosscoder comparison) operate on the activation space geometry regardless of whether individual feature labels are correct. The criticism is real and the experiment should not overclaim. But the GDM team's own conclusion was nuanced: SAEs remain "a tool in our toolkit" and "hypothesis generation and discovery" applications remain promising. Our experiment is closer to hypothesis generation (what changed inside the model?) than to the downstream classification task where SAEs failed.

---

**[11] Lyle, C., Dohare, S., & Sutton, R. S. (2024). Loss of plasticity in deep continual learning. *Nature*, 632, 768-774.**

The landmark paper demonstrating that standard deep learning methods gradually lose the ability to learn from new data with extended training, a phenomenon the authors formally name "loss of plasticity." This is distinct from catastrophic forgetting: plasticity loss means the network cannot learn anything new effectively, not that it forgets old knowledge. Published in Nature from Richard Sutton's lab at the University of Alberta.

*Used in:* Not directly cited in the experiment design methodology, but included in the references because it motivates the experiment's existence. If a base model has lost plasticity for moral reasoning concepts (because existing RLHF training has saturated the relevant representational capacity), CCAS fine-tuning may fail to create the new features it needs. Phase 2 of this experiment would detect this as: no meaningful feature differences between Condition D and Condition A despite different training, indicating the model cannot incorporate the new signal. The plasticity loss literature also strengthens the paper's static-weights argument: continuous self-modification is not only ungovernable at scale (the I/O capacity argument) but may also technically degrade the model's capacity to learn.
