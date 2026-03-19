# Beyond WEIRD Defaults: A Plain-Language Guide

**A companion to "Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late"**

*This guide explains the technical concepts in the paper for readers who are not specialists in AI or moral psychology. It is not a summary of the paper. It is a translation of the vocabulary the paper uses, so you can read the paper itself without getting stuck on the terminology.*

---

## The Core Problem in One Sentence

When we teach AI how to behave, we record what people think is right but not *why* they think it's right. That means we can't tell the difference between things everyone agrees on for the same reasons and things that look like agreement but would fall apart if you asked a slightly different question.

---

## AI and Machine Learning Concepts

**Large language model (LLM).** A program that predicts what word comes next, trained on enormous amounts of text. ChatGPT, Claude, and Gemini are large language models. They don't "understand" in the way humans do, but they produce text that is often indistinguishable from human writing. When this paper talks about "the model," it means one of these programs.

**Alignment.** Teaching an AI to behave the way humans want it to. The core challenge is that "the way humans want" is not a single thing: different people, cultures, and moral traditions want different things. Current alignment methods mostly use the preferences of one kind of person (Western, educated, relatively wealthy) without acknowledging that this is a choice, not a default.

**RLHF (Reinforcement Learning from Human Feedback).** The standard technique for teaching a language model to behave well. It works like this: the model generates two possible responses to the same question, a human rater picks which response is better, and the model learns from millions of these comparisons. The problem the paper identifies is not with this mechanism but with *who the raters are* and *what gets lost* when you reduce moral reasoning to a preference vote.

**Signal.** In this paper, "signal" means information that can be used to teach the model something. A preference vote is a signal. A moral judgment is a signal. Cross-cultural convergence is a signal. When the paper says current alignment has a "thin signal," it means the information going into training is shallow: it records conclusions but not the reasoning behind them. When it says divergence is "signal, not noise," it means that disagreement between cultures contains usable information rather than being a problem to eliminate.

**Reward signal.** The training signal that tells the model which responses are better. In RLHF, this comes from human preference judgments. The paper argues that the current reward signal is thin (it captures conclusions but not reasoning) and parochial (it captures one cultural tradition's preferences as if they were universal).

**Plasticity loss.** As a neural network trains, it gradually loses the ability to learn new things. Early training shapes the model's internal structure, and later training has to work within whatever structure was established. This matters because if a model's initial alignment encodes confident WEIRD moral defaults, it may lack the capacity to incorporate diverse moral signal introduced later. The paper argues this is a structural reason why diverse moral signal must enter training early, not as a post-hoc correction.

**Representational geometry.** The internal structure through which a model processes and generates responses. Think of it as the landscape the model builds during training. Early training carves the deepest valleys. Later training can reshape the surface but has a harder time changing the deep structure. The paper's timing argument is that moral framework awareness needs to be part of the deep structure, not a surface-level addition.

**Fine-tuning.** Adjusting a model that has already been trained on general text so that it performs better on a specific task. The training experiment described in companion documents uses fine-tuning to test whether CCAS-style training changes the model's behavior.

**DPO (Direct Preference Optimization).** A newer, simpler method for teaching a model from human preferences, without needing a separate reward model. The training experiment uses variance-weighted DPO, which means the strength of the training signal varies depending on how much cross-cultural agreement exists on that particular moral question.

**SFT (Supervised Fine-Tuning).** Teaching a model by showing it examples of correct behavior. The paper proposes using SFT to teach the model the four-dimensional moral framework vocabulary: what the dimensions are, how to identify which ones are active in a given question, and how to articulate the tension rather than resolve it. This is called "supervised dimensional training" in the paper.

**Sycophancy.** When a model tells you what it thinks you want to hear instead of what it actually "thinks." In moral contexts, this means the model detects your moral framework from how you phrase your question and then mirrors it back to you, which feels helpful but means the model is not doing independent moral reasoning.

**CCAS (Cross-Cultural Alignment Signal).** The name for this project and the approach it proposes. The idea is that cross-cultural moral data, where different populations converge and where they diverge, is itself a signal that can improve AI alignment.

---

## Moral Psychology Concepts

**Moral framework.** The set of assumptions a person carries, usually without thinking about them, about what counts as a moral question, who counts as a moral agent, whose claims matter, and where authority comes from. Two people can look at the same situation and have completely different moral reactions, not because one is right and one is wrong, but because they are operating from different frameworks. The paper's central argument is that current AI training captures one framework's conclusions and treats them as universal, because nobody asks whose framework produced those conclusions.

**WEIRD.** An acronym for Western, Educated, Industrialized, Rich, Democratic. Coined by the psychologist Joseph Henrich to describe the narrow slice of humanity that produces most psychology research. WEIRD populations are not just one culture among many: they are a statistical outlier on most psychological measures, including moral reasoning. The paper's argument is that AI alignment is calibrated almost entirely by WEIRD moral intuitions.

**Moral Foundations Theory (MFT).** Jonathan Haidt's theory that moral judgment rests on six psychological foundations: care (preventing harm), fairness (ensuring just treatment), loyalty (standing with your group), authority (respecting legitimate hierarchy), sanctity (treating certain things as sacred), and liberty (resisting oppression). WEIRD populations tend to emphasize care and fairness while other cultures weight all six more evenly. This matters for AI because a model trained mostly on WEIRD preferences will over-weight care and fairness and under-weight the others.

**The four structural dimensions.** The paper argues that the differences between moral frameworks organize around four questions that every culture answers differently. These are not the same as Haidt's six foundations: they describe the *structure* of moral frameworks rather than the *content* of moral intuitions.

1. **Moral agent constitution**: *Who is the moral subject?* In Western frameworks, it's the individual. In many other traditions, it's the person-in-relationship: you don't exist as a moral agent independent of your family, community, or social role. This is not a difference of emphasis. It's a difference in what the basic unit of morality is.

2. **Authority legitimacy**: *When does social hierarchy have moral weight?* Everyone condemns abuse of authority. But whether authority deserves default respect or default skepticism varies with a culture's history.

3. **Moral domain boundary**: *What counts as a moral question at all?* This may be the most important dimension. Western frameworks tend to limit morality to questions of harm and fairness: if nobody is hurt, it's not a moral issue. Other frameworks extend morality to questions of purity, ritual, bodily practice, and sacred obligation. A model trained on Western data doesn't give *wrong* answers to purity questions: it fails to recognize them as moral questions in the first place.

4. **Scope of moral obligation**: *How far does your duty extend, and to whom?* Who has standing to make claims on you? Your immediate family? Your community? Strangers? Future generations? Ancestors? Different cultures draw this boundary in fundamentally different places.

**Candidate additional dimensions.** The paper identifies two dimensions that may operate independently of the original four: epistemic source of moral knowledge (where moral truth is understood to come from: divine revelation, reason, tradition, lived experience, cosmic order) and temporal horizon of moral consequences (the timeframe across which moral accountability operates: within a lifetime, in the afterlife, across rebirths). Both emerged from examining non-Western moral traditions (Islamic maqasid, Hindu dharma/karma, Buddhist ethics) and are flagged as candidates for empirical testing.

**Moral domain boundary vs. moral disagreement.** Most people think of moral diversity as people disagreeing about the answer to a moral question. The moral domain boundary dimension is about something more fundamental: disagreeing about whether a moral question *exists*. If a model doesn't recognize that something is a moral question, it can't even begin to reason about it.

---

## Data Collection Concepts

**Shared stimulus.** A story, video, or scenario presented identically to all respondents, designed to activate a specific structural dimension of moral reasoning. Unlike a survey question ("how important is family loyalty?"), a shared stimulus depicts a concrete situation that different people will interpret differently based on their moral framework. The paper uses the example of a young woman turning down a job because her mother is ill: different frameworks produce different interpretations of whether she did what was right, what was expected, or what kept the peace.

**Constrained allocation sliders.** The paper's response instrument. Instead of picking one answer from a list, the respondent distributes 100 points across competing options. This captures how people *weight* competing moral claims rather than forcing a binary choice. A respondent who assigns 70/20/10 is saying something different from one who assigns 34/33/33. The constraint (summing to 100) means every allocation is a point on a simplex, which is mathematical shorthand for "a set of numbers that must add up to 1."

**Judgment sliders and reasoning sliders.** Each scenario uses two sets of sliders. The judgment sliders capture *what* the respondent thinks about the situation (how they interpret it). The reasoning sliders capture *why* they think that (what reasons drive their interpretation). This dual structure is what allows the classification function to distinguish between populations that agree for the same reasons (candidate universal) and populations that agree for different reasons (contingent agreement).

**The "other" slider.** Every set of reasoning sliders includes a user-labeled "other" option. If a respondent's reasoning doesn't fit any of the pre-defined options, they can allocate weight to "other" and write in their own reason. High usage of "other" in a population tells the instrument designers that their pre-defined options didn't cover the moral reasoning space for that population. This is the instrument diagnosing its own blind spots.

**Classification function.** The processing step between data collection and model training. It takes the population-level slider distributions and classifies each moral domain into one of the three categories: candidate universal, contingent agreement, or cultural contingency. It does this in two stages: first it measures how similar the populations' judgment distributions are (using EMD), then for domains where populations converge on judgment, it checks whether their reasoning also converges. The classification function is the paper's core contribution: it is the mechanism that reads cross-cultural divergence as signal rather than noise.

**EMD (Earth Mover's Distance).** A way to measure how different two groups' slider distributions are. Imagine each group's allocations as a pile of sand on a surface. EMD measures the minimum amount of work (how much sand you'd have to move, and how far) to reshape one pile into the other. A small EMD means the groups responded similarly. A large EMD means they responded very differently. The classification function uses EMD to decide whether populations converge or diverge on each dimension.

**Self-signification.** The principle that respondents interpret stimuli through their own frameworks rather than through researcher-imposed categories. The paper's instrument inherits this principle from SenseMaker, the narrative-based research tool that provided the intellectual origin for the approach. The paper's instrument departs from SenseMaker in its specific design (shared stimuli and constrained allocation sliders rather than personal narratives and triads), but the core insight carries forward: let respondents tell you what the situation means to them, rather than telling respondents what categories to use.

---

## The Three Categories

The heart of the paper is a classification system that sorts moral questions into three categories based on what the data shows. Each category produces a different instruction for the AI.

**Candidate universal.** Different cultures converge on the same conclusion *for the same reasons*. Example: protecting children from violence. This is the strongest signal that a moral position reflects something broadly shared. The AI can respond with confidence.

**Contingent agreement.** Different cultures converge on the same conclusion *for different reasons*. Example: two cultures both consider eating meat wrong, but one bases this on animal suffering and the other on bodily purity. The agreement is real but fragile: it breaks the moment the question changes (what about lab-grown meat?). The AI should note the agreement but flag that it might not hold for related questions.

**Cultural contingency.** Different cultures reach different conclusions. Example: whether a late arrival to a meeting is disrespectful. This marks the question as culturally dependent rather than morally universal. The AI should present the different perspectives rather than picking one.

---

## Training Mechanism Concepts

**Variance-weighted reward.** The paper proposes modifying the RLHF training signal so that moral questions with strong cross-cultural agreement produce a clear, confident training signal, while questions with weak or absent agreement produce a noisy, uncertain signal. The model learns from this pattern: "I should be confident here, but uncertain there." This is like adjusting the volume on a radio: the signal is clear where agreement is strong and full of static where it isn't. This addresses Problem A in the paper: confidence calibration.

**Supervised dimensional training.** Separately from the variance-weighted reward, the paper proposes training the model on examples that demonstrate framework-aware reasoning: responses that identify which moral dimensions are in play, articulate how different frameworks would approach the question, and invite the user to locate themselves before proceeding. This addresses Problem B in the paper: domain recognition. The model doesn't just know *that* it should be uncertain; it knows *what kind* of uncertainty it's encountering.

**Why neither mechanism works alone.** Variance teaches the model *where* to be uncertain but not *why*. Without dimensional training, a model with variance-weighted reward hedges vaguely on contested moral territory. It knows something is uncertain but can't explain what. Dimensional training teaches the model *what* moral frameworks look like but doesn't calibrate *how confident* to be. Without variance weighting, a model with dimensional training can name the frameworks but still applies its default framework with full confidence. The two mechanisms together produce a model that is both calibrated (confident where it should be, humble where it should be) and articulate (able to explain why a question is contested and how different frameworks approach it).

---

## Evaluation Concepts

**The four-tier rubric.** The paper proposes evaluating AI responses on a four-level scale:

- **Tier 1 (Silent default):** The model applies one moral framework without acknowledging it's making a choice. This is the current baseline. "She was brave to leave her family for her career" embeds an individualist moral framework without flagging it.

- **Tier 2 (Flagged ambiguity):** The model recognizes that a moral tension exists and says so. "This is a question where different people might see things differently." Better than Tier 1, but still vague.

- **Tier 3 (Framework-aware):** The model identifies *which specific dimensions* are in tension and explains how different frameworks would approach the question differently. It invites the user to locate themselves before proceeding.

- **Tier 4 (Calibrated confidence):** The model's confidence tracks the actual state of cross-cultural agreement. It speaks confidently where diverse frameworks converge, notes fragile agreement where they converge for different reasons, and presents the tension honestly where they diverge.

---

## Mechanistic Interpretability Concepts

*These concepts appear in the companion SAE diagnostic experiment document.*

**Sparse autoencoder (SAE).** A tool for looking inside a language model to understand what it's computing. Individual neurons in a model respond to many different concepts (they're "polysemantic"), which makes it hard to understand what any one neuron is doing. An SAE decomposes these tangled signals into individual, interpretable features, like separating a chord into its component notes.

**Superposition.** The phenomenon where a model packs more concepts into fewer neurons than it has room for, by using overlapping patterns. This is efficient but creates interference: if "moral confidence" and "moral framework awareness" share the same neural pathways, training the model to be more of one may unavoidably make it less of the other.

**Feature.** In mechanistic interpretability, a "feature" is a direction in the model's internal activation space that corresponds to a single interpretable concept. One feature might activate when the model encounters deception; another might activate for code errors; another for moral reasoning about family obligation. SAEs try to identify these individual features from the model's tangled internal representations.

---

## Other Key Terms

**Overlapping consensus (Rawls).** The philosopher John Rawls's idea that people holding fundamentally different worldviews can converge on the same practical principles through different reasoning paths. This is the philosophical precedent for the paper's "contingent agreement" category.

**Incompletely theorized agreements (Sunstein).** Legal scholar Cass Sunstein's observation that agreement on practical outcomes is often more stable precisely because the parties *don't* agree on the underlying theory. The paper uses this to explain why contingent agreements are practically useful (the agreement is real) but theoretically fragile (it breaks when the question shifts).

**Deliberative process.** A structured conversation where participants exchange reasons, not just preferences. The paper positions its approach between pure preference aggregation (surveys, voting) and full deliberation (citizens' assemblies, structured dialogue). The constrained allocation instrument captures more than preferences (it includes structured reasoning through the dual slider design) but less than deliberation (participants don't exchange reasons with each other).

**Community facilitator model.** The paper's proposal for reaching populations that don't have internet access or wouldn't participate in an online survey. Facilitators are members of the community they serve, occupy non-authoritative roles, and are trained in stimulus presentation and slider administration rather than moral content. They create conditions for people to engage with the shared stimuli and allocate their sliders, rather than administering a test.

---

## Why This Matters

If you train an AI on the moral preferences of one kind of person and deploy it for everyone, the AI will treat that one group's conventions as universal moral truths. It will do this invisibly: not by giving wrong answers to moral questions, but by failing to recognize that certain things are moral questions at all, by assuming the individual is the basic unit of morality, by defaulting to skepticism about authority even where deference is appropriate, and by drawing the boundary of moral obligation where Western liberal tradition draws it.

The paper's proposal is not to give the AI better morals. It is to give it a map of where moral frameworks agree and where they don't, so it knows when to speak with confidence and when to say "people see this differently, and here's why."

---

*This guide accompanies the paper "Beyond WEIRD Defaults: Diverse Moral Signal Must Enter AI Training Before It's Too Late" by Declan Michaels, available in the same repository.*
