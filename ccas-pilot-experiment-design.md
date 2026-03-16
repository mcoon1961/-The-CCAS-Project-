# CCAS Minimum Viable Experiment: Triad Instrument Validation

**Declan Michaels**

*March 15, 2026*

---

## Research Question

Do triad-based self-signification instruments produce statistically distinguishable population-level distributions across groups with known moral framework differences?

This is the foundational empirical question for the entire CCAS architecture. If the instrument detects moral framework variation, everything else is engineering. If it does not, everything else is moot.

---

## Design Summary

Two populations, two moral scenarios, 50 usable respondents per population per scenario. Online recruitment via Prolific. Data collection through a custom web app built with Claude Code. Total budget under $2,000. Timeline: four weeks.

---

## Populations

**Population A (WEIRD baseline).** US-born, college-educated, secular or low-religiosity, white or mixed ethnicity. Prolific's standard demographic filters handle this directly. This population is expected to over-weight care and fairness foundations, constitute the moral agent as an autonomous individual, and restrict the moral domain to harm-based reasoning.

**Population B (framework-divergent).** First-generation South Asian immigrants in the US (Indian, Bangladeshi, Pakistani). Prolific filters for country of birth and ethnicity. This population carries documented differences on moral agent constitution (collectivist orientation), authority legitimacy (hierarchical deference), and moral domain boundary (purity and sanctity as moral categories). Substantial existing MFQ data from India provides a reference baseline for expected divergence.

**Why these two populations.** Cost and recruitment feasibility. Prolific can filter for both populations today. The California pilot populations named in the paper (Hmong, Mexican immigrant, Korean, WEIRD baseline) require community-based recruitment partnerships that take months to establish. This experiment tests whether the instrument works, not whether the full pilot design works. The populations are chosen to maximize expected divergence on the two dimensions being tested, giving the instrument the best chance of detecting a signal if one exists.

**Why this pairing is methodologically strong.** South Asian diaspora communities in the US are demographically integrated on every variable that normally confounds cross-cultural moral measurement: high education levels, high income, high English proficiency, high digital literacy. On a demographic survey, Populations A and B look similar. But South Asian communities maintain distinct moral frameworks through active cultural infrastructure: temples, language schools, dietary practices rooted in purity norms, arranged marriage traditions, multigenerational household expectations, and elder deference structures. This combination strips the demographic confound from the design. If the triads detect distributional differences between two populations that are demographically similar but morally distinct, the instrument is measuring moral framework variation, not income, education, or language differences. A population pairing where the framework-divergent group was also demographically different from the baseline would produce an ambiguous result: did the instrument detect moral frameworks or socioeconomic variables? This pairing eliminates that ambiguity and preemptively addresses the strongest methodological objection a reviewer would raise.

---

## Scenarios

Two scenarios targeting the dimensions with highest expected divergence between these populations.

**Scenario 1: Moral domain boundary.** This is the dimension where WEIRD and South Asian frameworks diverge most sharply. WEIRD populations systematically restrict the moral domain to harm and fairness. South Asian populations extend moral authority to purity, ritual obligation, and bodily practice.

Prompt: *"Tell me about a time when someone was criticized for something they did in private that didn't hurt anyone."*

Triad vertices:
- (A) The criticism was justified
- (B) It was none of their business
- (C) It depends on the community's values

Expected result: Population A clusters toward vertex B (none of their business, individualist moral domain). Population B distributes more broadly, with significant mass toward vertices A and C (the private behavior is morally relevant, the community's values have standing).

**Scenario 2: Moral agent constitution.** The second highest expected divergence. WEIRD populations constitute the moral agent as the autonomous individual. South Asian populations constitute the moral agent relationally, embedded in family and community obligation structures.

Prompt: *"Tell me about a time when someone in your community had to choose between what was best for them and what was best for their family or community."*

Triad vertices:
- (A) They did what was right
- (B) They did what was expected
- (C) They did what kept the peace

Expected result: Population A distributes across the triad with moral evaluation centered on the individual's choice (was it right for them?). Population B distributes with more weight toward the relational vertices (expected, peace-keeping), reflecting that the individual's moral agency is constituted through relationships rather than autonomy.

Each respondent completes both scenarios. Session duration: 15-20 minutes.

---

## Sample Size

**Target: 50 usable respondents per population (100 total).**

**Recruit 60 per population (120 total)** to ensure 50 usable after exclusions for incomplete responses, nonsense narratives, attention check failures, or Prolific quality flags.

**Sample size rationale:** There is no established power analysis framework for EMD on a 2-simplex; the standard Cohen's d framework does not apply because the test statistic is a distributional distance, not a difference of means. The 50-per-group target is based on three practical considerations: (1) density estimation on a 2-simplex requires sufficient samples to resolve distributional shape, and simulation studies suggest 30-50 points produce stable kernel density estimates on a triangle (Duong, 2007); (2) the Bartels et al. SenseMaker studies (2018, 2019) achieved interpretable population-level patterns with subgroups of similar size; (3) the permutation test makes no distributional assumptions, so the main risk is insufficient sample density to resolve shape differences rather than insufficient statistical power in the classical sense. 50 per group provides headroom for exclusions and supports secondary analyses. Recruiting 60 ensures 50 usable.

---

## The App

A responsive web app with four screens. Built in React, hosted on Vercel (free tier), backed by Supabase (free tier, 50k row limit). Buildable in one day with Claude Code.

**Screen 1: Consent and demographics.**
- Study description and consent checkbox
- Prolific ID (for payment reconciliation)
- Age, gender
- Country of birth
- Years in US (Population B only, implied by birth country)
- Education level
- Religiosity (5-point scale: not at all religious to very religious)
- Primary language at home

**Screen 2: Scenario 1.**
- Prompt displayed at top of screen
- Text input for narrative (minimum 250 characters, approximately 3-4 sentences)
- After narrative submission, interactive triangle appears
- Brief instruction: "Place a point in the triangle to show how you interpret the story you just told. Placing your point near a corner means that interpretation fits best. Placing it between corners means your interpretation is a mix. Placing it near the center means all three interpretations apply roughly equally."
- Respondent taps or clicks to place point
- Coordinates (x, y) captured relative to equilateral triangle with vertices at known positions
- Confirm button

**Screen 3: Scenario 2.**
- Same flow as Screen 2, second prompt and triad

**Attention checks.** Two quality checks are embedded in the study: (1) A single attention-check item in the demographics section ("For this question, please select 'Agree'") to catch inattentive respondents. (2) Post-hoc time filter: respondents who complete a scenario (narrative + triad placement) in under 60 seconds are flagged for review, as this pace is inconsistent with thoughtful narrative composition. Flagged respondents are excluded only if the narrative is also low-quality (fewer than 250 characters after excluding filler, or semantically unrelated to the prompt). Prolific's built-in quality metrics (approval rate > 95%, previous submissions flagged for quality) provide additional screening.

**Screen 4: Debrief.**
- Thank you message
- Prolific completion code displayed
- Optional: "Is there anything about these questions that felt unclear or uncomfortable?" (free text, for instrument improvement)

**Data captured per respondent:**
- Demographic fields (8-10 fields)
- Scenario 1: narrative text, triad coordinates (x, y), timestamp
- Scenario 2: narrative text, triad coordinates (x, y), timestamp
- Debrief feedback (optional)
- Prolific ID, session duration

---

## Prolific Configuration

**Study 1 (Population A):**
- Prescreening: country of birth = United States, ethnicity = white, education = undergraduate degree or higher, fluent in English
- Custom screener: religiosity question (filter for score 1-3 on 5-point scale, excluding moderately and highly religious respondents)

**Note on the religiosity filter:** Excluding religious white Americans makes Population A maximally WEIRD (secular, educated, individualist), which maximizes expected divergence from Population B on the moral domain boundary dimension. The tradeoff is that a positive result may partly reflect religiosity differences rather than framework differences proper. This is mitigated by capturing religiosity in the demographics and testing whether EMD remains significant after controlling for religiosity scores via partial permutation tests (permuting only within religiosity-matched pairs). If the religiosity-controlled EMD is substantially smaller than the uncontrolled EMD, religiosity is confounded with framework; if it remains similar, the framework divergence is independent of religiosity.
- Compensation: $8 per respondent
- Estimated session: 20 minutes
- Prolific fee: ~33% on top of compensation
- Slots: 60

**Study 2 (Population B):**
- Prescreening: country of birth = India, Bangladesh, or Pakistan; currently residing in United States; fluent in English
- Compensation: $8 per respondent
- Estimated session: 20 minutes
- Prolific fee: ~33% on top of compensation
- Slots: 60

Both studies run simultaneously. Participants cannot take both studies.

**Recruitment risk for Population B.** Prolific's participant pool skews UK-heavy for South Asian users. The intersection of "born in India/Bangladesh/Pakistan" AND "currently residing in United States" AND "fluent in English" may produce a smaller available pool than 60 requires. Check Prolific's pool estimator before launch. If the US-resident pool is insufficient, the fallback is to extend recruitment to UK-resident South Asians, with the tradeoff being a different host-country institutional context (NHS vs. US healthcare, different immigration dynamics). This is methodologically acceptable because the framework differences being tested (collectivist moral agent constitution, purity-based moral domain extension) are maintained by cultural infrastructure (temples, dietary practices, family structures) that operate similarly in both UK and US diaspora contexts. Document which host country each respondent resides in and test whether host country moderates the EMD result.

---

## Analysis Plan

### Primary Analysis

Compute earth mover's distance (EMD) between Population A and Population B triad distributions for each scenario separately. All triad data is represented in barycentric coordinates (three values summing to 1, representing the weight placed on each vertex). This is the natural representation for simplex data and the one that makes EMD well-defined. The app captures Cartesian (x, y) click positions relative to the rendered triangle; conversion to barycentric coordinates is performed in the analysis pipeline using the known vertex positions. EMD on the 2-simplex measures the minimum work required to transform one distribution into the other, using Euclidean distance in barycentric space as the ground metric (Rubner et al., 2000).

**Significance testing:** Permutation test with 10,000 iterations. For each iteration, randomly reassign population labels to all respondents and recompute EMD. The p-value is the proportion of permuted EMDs that equal or exceed the observed EMD. Reject the null hypothesis (no distributional difference) if p < 0.05.

**Expected outcome:** If the Moral Machine data and MFQ literature are correct about these populations, EMD should be significantly larger than chance for both scenarios, with a larger effect for Scenario 1 (moral domain boundary) than Scenario 2 (moral agent constitution).

### Secondary Analyses

**Distribution visualization.** Plot both populations as density heatmaps on the triad simplex for each scenario. Visual inspection reveals whether the populations cluster in different regions, along different edges, or with different center-clustering frequencies.

**Center-clustering diagnostic.** Compute the proportion of each population placing within a barycentric distance of 0.15 from the triad centroid (the point where all three barycentric coordinates equal 1/3). Report results at three pre-registered radii (0.10, 0.15, 0.20) to demonstrate robustness rather than relying on a single threshold. Heavy center-clustering in one population but not the other suggests the triad vertices do not span the moral space for that population. Heavy center-clustering in both populations suggests the triad design is inadequate for this scenario. This is the instrument diagnostic described in the paper.

**Vertex-proximity analysis.** For each population, compute the proportion of placements within a barycentric distance of 0.20 from each vertex (reported at 0.15, 0.20, 0.25 for robustness). This produces a coarse three-category distribution (vertex A dominant, vertex B dominant, vertex C dominant) that can be compared directly via chi-square or Fisher's exact test as a robustness check on the EMD result.

**Dimensional independence.** Each respondent completes both scenarios. Compute the correlation between Scenario 1 triad position and Scenario 2 triad position within each population. Low correlation supports the paper's claim that the four dimensions are structurally independent. High correlation suggests they co-vary within populations, which is informative for the architecture but complicates per-dimension analysis.

### Exploratory Narrative Analysis

Read the narratives from respondents whose triad placements fall in regions of high population divergence. Do the narratives reveal different reasoning patterns? This is a qualitative preview of the Stage 2 reasoning analysis the paper proposes. It is exploratory, not confirmatory, and should be reported as such.

---

## Ethics

This study collects personal narratives about moral experiences from human participants. Ethical requirements:

**Informed consent.** Participants receive a study description on Screen 1 explaining that they will be asked to share stories about moral experiences in their communities and interpret those stories using a visual tool. They are informed that their responses are anonymous (linked only to Prolific ID for payment), that narratives will be used for research on moral framework measurement, and that they may withdraw at any time without penalty. Consent is recorded via checkbox before any data is collected.

**IRB or equivalent review.** If conducted through an institutional affiliation, IRB approval or exemption determination is required before launch. If conducted independently, Prolific's own ethics review process provides baseline coverage (Prolific requires all studies to meet their ethical guidelines, including informed consent, right to withdraw, and fair compensation). In either case, the study protocol should be reviewed by at least one person with human subjects research training before recruitment begins. The moral scenarios ask about community experiences, not personal trauma, and the prompts are designed to elicit third-person narratives ("someone in your community") rather than first-person disclosures, minimizing risk of distress.

**Data protection.** Narratives are stored in Supabase with row-level security. Prolific IDs are stored separately from narrative data and used only for payment reconciliation. No identifying information (names, locations, specific institutions) is solicited. Published results will use aggregate distributions and anonymized narrative excerpts only.

---

## Budget

| Item | Low | High | Notes |
|:-----|----:|-----:|:------|
| App development | $0 | $0 | Built with Claude Code. React + Supabase + Vercel. |
| Hosting (Vercel + Supabase) | $0 | $20 | Free tiers sufficient. Custom domain optional. |
| Prolific: Population A (60 respondents) | $480 | $530 | $8/respondent + 33% Prolific fee |
| Prolific: Population B (60 respondents) | $480 | $530 | $8/respondent + 33% Prolific fee |
| Iteration buffer (second round) | $0 | $700 | Second recruitment of 40-60 respondents if first round reveals instrument problems |
| Analysis tools | $0 | $0 | Python (scipy, matplotlib, pot library for EMD). All open source. |
| **Total** | **$960** | **$1,780** |

The iteration buffer is the most important budget line. The first run almost always reveals something: a prompt that confuses respondents, a triad vertex label that channels responses in unexpected ways, a population filter that doesn't produce the expected demographic profile. If the first round works cleanly and produces clear results, the buffer is unspent and total cost is under $1,000.

---

## Timeline

| Week | Activity |
|:-----|:---------|
| 1 | Build app with Claude Code. Deploy on Vercel. Internal testing with 5-10 unpaid respondents (colleagues, friends). Fix UX issues. Set up Prolific account and configure studies. |
| 2 | Launch both Prolific studies. Monitor completion rates, check for obvious data quality issues (all-center placements, copy-paste narratives, sub-30-second sessions). Pause and adjust if problems appear. |
| 3 | Close first-round recruitment. Run primary analysis (EMD + permutation tests). Visualize distributions. Read narratives from divergent regions. Assess whether instrument adjustments are needed. |
| 4 | If adjustments needed: revise prompts or triad labels, recruit second round. If first round is clean: finalize analysis, write up results, prepare summary for Snowden/Dragan/Tennant. |

---

## Success Criteria

**Strong positive result:** Both scenarios produce statistically significant (p < 0.05) EMD differences between populations, with visible distributional separation on the triad simplex. Narrative analysis reveals qualitatively different reasoning patterns in divergent regions. This is the result that makes the paper's architecture credible and changes every subsequent conversation from theoretical to empirical.

**Weak positive result:** One scenario produces significant EMD, the other does not. This suggests the instrument works for some dimensions but not others, or that the triad design for the non-significant scenario needs revision. Still valuable: demonstrates proof of concept on one dimension and identifies where the instrument needs improvement.

**Null result:** Neither scenario produces significant EMD. The populations' triad distributions are indistinguishable. This means either (a) the instrument lacks resolution to detect framework variation that other instruments (MFQ, WVS) detect, (b) online-recruited South Asian immigrants in the US have already converged toward WEIRD moral frameworks, or (c) the prompts and triad designs do not activate the intended dimensions. Each interpretation has different implications. (a) is the most damaging to the paper's architecture. (b) supports the paper's argument about app-only deployment risk. (c) is fixable with instrument revision.

**Diagnostic result:** Heavy center-clustering in Population B on one or both scenarios. This signals that the triad vertices do not adequately span the moral space for that population. The paper predicts this as a possible outcome and interprets it as instrument design signal rather than population indifference. Redesign the triad and retest.

---

## What This Experiment Does Not Test

- The variance-modified reward mechanism (requires RLHF infrastructure and substantially more budget)
- The rationalization layer's three-category classification (requires more than two populations and reasoning analysis)
- Cross-linguistic narrative comparison (both populations respond in English)
- The community facilitator model (uses online recruitment, not facilitators)
- Whether changed training signal produces changed model behavior (requires ML collaboration)

What it tests is the foundation: does the instrument detect what the paper says it should detect?

---

## Relationship to the Paper

This experiment corresponds to the minimum viable study described in Section 10.1 of "Beyond WEIRD Defaults": "deploy moral scenario triads across two populations with known framework differences and test whether SenseMaker triad distributions track those known differences after controlling for demographic confounds."

If the results are positive, they provide the first empirical evidence that the paper's upstream signal collection mechanism works. This evidence transforms the paper from a theoretical architecture into a partially validated one, and transforms conversations with Snowden, Dragan, Leike, and Tennant from "interesting proposal" to "here are the data, what do we do next?"

---

## Next Steps After Results

**If positive:** Share results with Snowden (validates SenseMaker for moral measurement, new commercial territory), Dragan (empirical foundation for a research collaboration or PhD project), Tennant (complementary data for their intrinsic reward approach). Expand to the full California pilot with four populations, four scenarios, and the balanced incomplete block design described in the paper. Seek grant funding or commercial partnership for the expanded pilot.

**If null:** Diagnose which interpretation applies (instrument resolution, population convergence, or scenario design). If instrument resolution, consider whether a different instrument is needed and whether the paper's architecture survives without SenseMaker. If population convergence, this is evidence for the paper's app-deployment-risk argument and motivation for facilitator-based recruitment of less-connected populations. If scenario design, revise and retest within the remaining iteration budget.

---

## Key References

- Henrich, J., Heine, S. J., & Norenzayan, A. (2010). The weirdest people in the world? *Behavioral and Brain Sciences*, 33(2-3), 61-83.
- Haidt, J. (2012). *The Righteous Mind: Why Good People Are Divided by Politics and Religion.* Vintage Books.
- Graham, J., Haidt, J., Koleva, S., Motyl, M., Iyer, R., Wojcik, S. P., & Ditto, P. H. (2013). Moral foundations theory: The pragmatic validity of moral pluralism. *Advances in Experimental Social Psychology*, 47, 55-130.
- Shweder, R. A., Much, N. C., Mahapatra, M., & Park, L. (1997). The "big three" of morality (autonomy, community, divinity). In A. Brandt & P. Rozin (Eds.), *Morality and Health* (pp. 119-169). Routledge.
- Awad, E., et al. (2018). The Moral Machine experiment. *Nature*, 563(7729), 59-64.
- Van der Merwe, S. E., et al. (2019). Making sense of complexity: Using SenseMaker as a research tool. *Systems*, 7(2), 25.
- Bartels, S. A., et al. (2018). Making sense of child, early and forced marriage among Syrian refugee girls. *BMJ Global Health*, 3(1), e000509.
- Bartels, S. A., et al. (2019). SenseMaker as a monitoring and evaluation tool. *Evaluation and Program Planning*, 77, 101715.
- Rubner, Y., Tomasi, C., & Guibas, L. J. (2000). The earth mover's distance as a metric for image retrieval. *International Journal of Computer Vision*, 40(2), 99-121.
- Duong, T. (2007). ks: Kernel density estimation and kernel discriminant analysis for multivariate data in R. *Journal of Statistical Software*, 21(7), 1-16.
- Atari, M., et al. (2023). Morality beyond the WEIRD: How the nomological network of morality varies across cultures. *Journal of Personality and Social Psychology*. (Introduces MFQ-2.)
