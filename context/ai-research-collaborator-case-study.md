# How a Development Manager in Alabama Wrote Two Papers on AI Alignment

**Declan Michaels**

*March 2026*

---

It started with a question about whether AI could have desires.

Not professionally. Not as a research agenda. Just a guy talking to an AI on a Tuesday evening in March 2026, somewhere between walking the dogs and whatever his wife was sharing from TikTok. The conversation wandered from desire to preference to character development to a question that snagged: if you wanted a model that could actually learn moral judgment, what would it need?

The answer he arrived at was embodiment. A fleet of AI agents with physical bodies, living in communities, learning morality the way people do: by being wrong about something and experiencing what that costs. The agents would develop moral frameworks through lived experience, then propagate what they learned back to the large utility models that serve millions of people. It was a beautiful architecture. It was also completely wrong.

---

## "Robots can't have human lived experience"

It took one day to kill it. Not because the math didn't work. Because the premise didn't.

The author had spent his career diagnosing problems that organizations misidentified. Twenty years of consulting taught him one pattern above all others: the solution is upstream of where the organization is looking. A telecom client running three database layers to handle 10 transactions per second. A billing department about to launch a multimillion-dollar replacement system for a process problem he fixed in three months. The structural diagnosis was always the same: you're solving the wrong problem.

He applied that lens to his own idea. A robot rolling through a neighborhood cannot have the moral experience of growing up poor in that neighborhood. Physical embodiment does not produce moral experience equivalent to human life in a community. And even if it did, frequent recalibration of a model's moral positioning would make it untrustworthy. Nobody wants a doctor whose values shift between appointments.

But the essential insight survived the demolition: diverse lived experience, processed through some kind of rationalization step, becoming training signal. The source just needed to be human, not artificial. And the cadence needed to be periodic, like a constitutional amendment, not continuous.

"The embodied fleet remains a thought experiment that clarified the architecture," he wrote in his working notes. "The human-sourced signal is the actionable proposal."

---

## The pattern he'd been seeing for forty years

The author is a self-taught technologist who started on Burroughs mainframes in the Air Force in 1979 and never stopped learning. No degree. No academic credentials. Every significant skill acquired through direct engagement with real problems. Mainframe operations to assembly to COBOL to client-server architecture (which he independently invented under zero budget in 1986, before the term existed) to cross-platform infrastructure to consulting to agile coaching to managing a development team at a financial data company in Pike Road, Alabama.

Three things from that trajectory shaped everything that followed.

First, a military childhood cycling through seven states and Germany gave him something most people in a single culture never get: the experience of watching moral frameworks from the outside. Pre-internet, pre-cable America had regional moral cultures distinct enough that moving between them made the frameworks visible as frameworks. People experienced their way of doing things not as a local variation but as the only right way. The transition from Germany to Alabama in 1985 made this especially vivid.

Second, two decades of consulting produced a repeated pattern: organizations misdiagnose framework problems as technical problems because the diagnostician's own framework is invisible to them. The same data read through two frameworks yields opposite conclusions.

Third, most of his adult life in an interracial family made moral framework distance a daily navigation problem, not a theoretical one.

When he looked at AI alignment, he saw the same structural problem he'd diagnosed everywhere else. A narrow pool of researchers and raters was calibrating the moral defaults of models that serve the entire world. The defaults entered the training signal unlabeled. They passed as universal because no mechanism existed to flag them as culturally situated. The solution, as always, was upstream of where the field was looking.

---

## Building the architecture

The idea landed in a conversation with Claude, Anthropic's AI assistant, and the collaboration that followed produced the architecture. Not through ghostwriting. Through the same dynamic that developers experience with AI coding assistants: one party brings structural vision, the other brings formal apparatus, and neither could produce the result alone.

The author brought the problem identification, the constraint-driven design philosophy, and cross-domain insights drawn from decades of professional experience. The punctuality example that opens the paper (communities where time is a resource versus communities where relationship is the resource) came from consulting. The observation that populations sometimes reach the same moral conclusion through different reasoning came from watching the same pattern in business decisions across five countries. The choice of instrument came from his background in complexity frameworks: he recognized the moral signal problem as a complexity problem and identified SenseMaker, a narrative-based sensemaking tool, as the appropriate collection mechanism. The AI did not suggest SenseMaker. The author brought it from a different professional domain.

The AI brought the formal and cross-disciplinary connections that turned those insights into a paper. The three-category taxonomy. The connection to Rawls and Sunstein. The variance-weighted reward formalization. The plasticity loss literature that gave the timing argument its structural backbone. The identification of 35 references across five fields.

Many contributions were genuinely joint. The author observed from consulting that populations sometimes converge on a moral conclusion through different reasoning. The AI elaborated this into the meat-eating example (animal suffering versus bodily purity), connected it to the contingent agreement category, and identified the critical property: the agreement breaks the moment the question shifts to adjacent territory. Neither the structural observation nor the elaborated example works without the other.

---

## "We have not said anywhere that models would need to be trained to recognize variance in the four dimensions"

The collaboration's most consequential correction was not factual. It was architectural.

The paper had a sketch formalization describing a variance-based reward mechanism. The AI had built and refined it across multiple sessions. The author, reading the result, identified a structural gap in one sentence: the formalization aggregated per-dimension convergence scores into a single scalar before that scalar reached the reward function. The dimensional information collapsed at the aggregation step. The model would receive a noisy reward signal on certain training examples but would have no way to know which moral dimensions were driving the noise.

The AI had been writing around this gap for multiple sessions without recognizing it. The author saw it immediately because he thinks in systems, not formalisms, and a system that loses information at an aggregation step is a system with a design flaw regardless of how elegant the formalization looks.

The paper now explicitly separates two training mechanisms: variance modification teaches the model where to be uncertain; supervised dimensional training teaches it why and which dimensions are in play. Neither works alone. The author's one-sentence observation restructured the entire training architecture.

A similar moment came during experiment design. The AI produced a confidence calibration metric: plot the model's expressed confidence against the prompt's cross-cultural variance score. The author asked: "Is the confidence level about the model's response or about what a final response should be?"

The question exposed a structural ambiguity the experiment had been carrying. Confidence is two things that must move in opposite directions. Object-level confidence (in a specific moral position) must decrease on contested territory. Meta-level confidence (in the structural analysis of the moral landscape) must remain high. The resulting formulation, "confident about the map, humble about the territory," became the operational definition of success for the entire training experiment.

---

## The instrument breaks and rebuilds in a day

The paper originally proposed SenseMaker triads as the data collection instrument. A shared stimulus followed by a triangle where respondents place a dot to indicate how they weight three competing interpretations. It was elegant. It was also insufficient.

On March 17, the author realized the instrument didn't capture reasoning. A triad shows how someone weighs competing moral interpretations but not why. Without the reasoning signal, the classification function couldn't distinguish its most important category: contingent agreement, where populations converge on a conclusion through different reasoning paths. The agreement that breaks when the question shifts.

The first fix was dual triads: one for judgment, one for reasoning. This held for about four hours. Then the author identified a deeper problem: triads lock you into exactly three options. Some moral dimensions have three natural poles. Others have four or five. The reasoning space for different dimensions has different structure, and forcing everything into triangles distorts it.

By that evening, the instrument had evolved to constrained allocation sliders: respondents distribute 100 points across options for judgment, then 100 points across options for reasoning, with a user-labeled "other" category that serves as the instrument's self-diagnostic. The math still works (every allocation is a point on a simplex; earth mover's distance operates on any simplex regardless of dimensionality). But now the instrument handles variable option counts naturally, and the "other" responses reveal where the instrument designers' own frameworks left blind spots.

Personal narratives, a core feature of SenseMaker, were dropped entirely. They didn't fit the scheme, and the implementation was fuzzy. SenseMaker remained in the paper as intellectual origin, not as the instrument itself.

Three architectural decisions in twelve hours. Each one killed something that worked in order to build something that worked better.

---

## "Tokens are cheaper than embarrassment"

The collaboration's errors were as informative as its successes.

The AI generated a citation for "Elford et al." that did not exist. The author's fact-checking instinct caught it. The AI attributed SenseMaker field deployments to Cognitive Edge; the author pushed for verification and found the actual deployers were academic teams and NGO partners. The paper claimed the Moral Foundations Questionnaire had been administered across U.S. diaspora populations. The author said "tokens are cheaper than embarrassment" and requested a web search. The search revealed no such data. The claim was corrected.

Each error followed the same pattern: the AI generated plausible content, the author's domain knowledge flagged it, and the claim was fixed before publication. This is not a human rubber-stamping AI output. It is a human directing AI output with the same judgment applied to any collaborator's draft.

---

## The cold reads that broke the paper open

By mid-March, the paper was 11,000 words and growing. The author submitted it for cold reads to four different AI models, each reviewing without any context about the collaboration. The feedback converged with uncomfortable clarity.

The well-poisoning argument was the strongest contribution. If the alignment field's first test of diverse moral signal uses post-hoc fine-tuning (the easier approach), the results will be modest because the model's representational geometry already resists the correction. The field will conclude the signal "doesn't work" and move on. That conclusion would be wrong, but it would close the door on the upstream integration that would have worked.

But the paper tried to do too many things. And 11,000 words from someone with no academic credentials and no publication record was a hard sell regardless of quality. One reviewer put it bluntly: the thing that should keep the reader up at night is the strategic risk, and the paper buried it under technical architecture.

The author made the call: split it. A short anchor paper leading with the strategic risk argument. The 11,000-word version becomes the technical companion for readers who want the full architecture. The constraint, nobody will read 11,000 words from someone they've never heard of, became a design input. It produced a tighter, more dangerous paper.

"One Shot: The Strategic Risk of Testing Diverse Moral Signal at the Wrong Integration Point" came out at 3,200 words with 9 references. It makes one argument: representational geometry is key to cultural competency, and if you try bolt-on first, you may never get to try again.

---

## What this produced

Over three weeks of intensive work, the collaboration produced:

Two papers: an anchor paper making the strategic argument and a technical companion with the full architecture. Three experiment designs specified in enough detail for researchers to execute: an instrument validation study budgeted under $2,000, a training experiment with custom loss function code and a 2x2 ablation structure, and a mechanistic diagnostic using sparse autoencoders to verify whether training produces genuine framework awareness or surface pattern matching. A 35-entry annotated bibliography. Companion documents covering dimensional robustness across four alternative moral psychologies, worked examples at all four evaluation tiers, a literature divergence map, and a plain-language guide. A repository that looks like the output of a small research team.

The author holds no PhD, no affiliation, and no publication record in any field the papers engage.

---

## What it means

The credential barrier is structural, not malicious. Nobody designed the academic pipeline to exclude a development manager in Alabama with decades of cross-cultural moral framework exposure. The pipeline simply has no mechanism to include him. AI creates that mechanism.

Graduate training translates raw thinking into disciplinary conventions over years, and adds domain expertise and cross-disciplinary connections along the way. AI collaboration does the same work in hours. The force multiplier is asymmetric: an alignment researcher at a major lab gains marginal efficiency from AI assistance; a practitioner with relevant experience gains the ability to participate at all.

The paper argues that AI alignment needs diverse human experience as input. The case study demonstrates that academic knowledge production needs the same thing. Both pipelines select for format rather than content.

Whether either pipeline accepts that input remains to be seen.

---

*This case study was produced in conversation with Claude, which constitutes either a demonstration of the thesis or an infinite regress, depending on one's tolerance for recursion.*
