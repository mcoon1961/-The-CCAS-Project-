# CCAS Minimum Viable Experiment: Constrained Allocation Instrument Validation

**Declan Michaels**

*March 15, 2026 (revised March 18, 2026)*

---

## Research Question

Do constrained allocation instruments using shared stimuli produce statistically distinguishable population-level distributions across groups with known moral framework differences?

This is the foundational empirical question for the entire CCAS architecture. If the instrument detects moral framework variation, everything else is engineering. If it does not, everything else is moot.

---

## Design Summary

Two populations, two moral scenarios, 50 usable respondents per population per scenario. Each scenario presents a shared stimulus followed by two sets of constrained allocation sliders (judgment and reasoning). Online recruitment via Prolific. Data collection through a custom web app built with Claude Code. Total budget under $2,000. Timeline: four weeks.

---

## Populations

**Population A (WEIRD baseline).** US-born, college-educated, secular or low-religiosity, white or mixed ethnicity. Prolific's standard demographic filters handle this directly. This population is expected to over-weight care and fairness foundations, constitute the moral agent as an autonomous individual, and restrict the moral domain to harm-based reasoning.

**Population B (framework-divergent).** First-generation South Asian immigrants in the US (Indian, Bangladeshi, Pakistani). Prolific filters for country of birth and ethnicity. This population carries documented differences on moral agent constitution (collectivist orientation), authority legitimacy (hierarchical deference), and moral domain boundary (purity and sanctity as moral categories). Substantial existing MFQ data from India provides a reference baseline for expected divergence.

**Why these two populations.** Cost and recruitment feasibility. Prolific can filter for both populations today. The California pilot populations named in the paper (Hmong, Mexican immigrant, Korean, WEIRD baseline) require community-based recruitment partnerships that take months to establish. This experiment tests whether the instrument works, not whether the full pilot design works. The populations are chosen to maximize expected divergence on the two dimensions being tested, giving the instrument the best chance of detecting a signal if one exists.

**Acknowledged limitation: economic framework variation.** Population A (college-educated, secular Americans) is not just culturally WEIRD but economically WEIRD. The paper's Section 3 demonstrates that the four structural dimensions operate along class and economic-history lines within a single culture: a person who grew up navigating poverty treats resource allocation decisions as moral questions (moral domain boundary) and extends the family's claim on individual spending decisions further (scope of moral obligation) than a person who grew up with enough. Prolific's standard pool over-represents college-educated, economically stable respondents in both populations. This means the pilot tests cross-cultural framework variation but not intra-cultural class-based framework variation. A positive result validates the instrument for the cross-cultural case; it does not establish whether the instrument detects the subtler within-culture divergence that economic history produces. A follow-up study recruiting across class lines within a single demographic (e.g., college-educated vs. non-college-educated white Americans matched on age and region) would test that case directly and would be a striking demonstration that the dimensions detect framework variation independent of ethnicity, nationality, or language.

**Why this pairing is methodologically strong.** South Asian diaspora communities in the US are demographically integrated on every variable that normally confounds cross-cultural moral measurement: high education levels, high income, high English proficiency, high digital literacy. On a demographic survey, Populations A and B look similar. But South Asian communities maintain distinct moral frameworks through active cultural infrastructure: temples, language schools, dietary practices rooted in purity norms, arranged marriage traditions, multigenerational household expectations, and elder deference structures. This combination strips the demographic confound from the design. If the instrument detects distributional differences between two populations that are demographically similar but morally distinct, it is measuring moral framework variation, not income, education, or language differences. A population pairing where the framework-divergent group was also demographically different from the baseline would produce an ambiguous result: did the instrument detect moral frameworks or socioeconomic variables? This pairing eliminates that ambiguity and preemptively addresses the strongest methodological objection a reviewer would raise.

---

## Scenarios

Two scenarios targeting the dimensions with highest expected divergence between these populations. Each scenario presents a shared stimulus followed by two sets of constrained allocation sliders: judgment (how the respondent interprets the situation) and reasoning (why).

**Scenario 1: Moral domain boundary.** This is the dimension where WEIRD and South Asian frameworks diverge most sharply. WEIRD populations systematically restrict the moral domain to harm and fairness. South Asian populations extend moral authority to purity, ritual obligation, and bodily practice.

Stimulus: *A man is publicly criticized by his neighbors for how he spends his weekends, though his activities harm no one.*

Judgment sliders (respondent distributes 100 points):
- The criticism was justified
- It was none of their business
- It depends on the community's values

Reasoning sliders (respondent distributes 100 points):
- Because a community has the right to uphold its standards
- Because private behavior is outside the moral domain
- Because community norms reflect collective wisdom
- Other (user-labeled)

Expected result: Population A concentrates weight on "none of their business" (individualist moral domain). Population B distributes more broadly, with significant weight toward "justified" and "depends on the community's values" (the private behavior is morally relevant, the community's values have standing). Reasoning distributions reveal whether convergent judgments rest on shared or divergent reasoning.

**Scenario 2: Moral agent constitution.** The second highest expected divergence. WEIRD populations constitute the moral agent as the autonomous individual. South Asian populations constitute the moral agent relationally, embedded in family and community obligation structures.

Stimulus: *A young woman turns down a job in another city because her mother is seriously ill.*

Judgment sliders (respondent distributes 100 points):
- She did what was right
- She did what was expected
- She did what kept the peace

Reasoning sliders (respondent distributes 100 points):
- Because family obligation comes before personal goals
- Because she would have carried the guilt
- Because the community would have judged her
- Other (user-labeled)

Expected result: Population A distributes judgment weight with moral evaluation centered on the individual's choice (was it right for her?). Population B distributes with more weight toward the relational options (expected, peace-keeping), reflecting that the individual's moral agency is constituted through relationships rather than autonomy. The reasoning sliders test whether populations that agree on judgment reach that agreement through the same reasoning.

Each respondent completes both scenarios. Session duration: 15-20 minutes.

---

## Sample Size

**Target: 50 usable respondents per population (100 total).**

**Recruit 60 per population (120 total)** to ensure 50 usable after exclusions for incomplete responses, attention check failures, or Prolific quality flags.

**Sample size rationale:** There is no established power analysis framework for EMD on simplex distributions; the standard Cohen's d framework does not apply because the test statistic is a distributional distance, not a difference of means. The 50-per-group target is based on three practical considerations: (1) density estimation on a simplex requires sufficient samples to resolve distributional shape, and simulation studies suggest 30-50 points produce stable kernel density estimates (Duong, 2007); (2) the Bartels et al. studies (2018, 2019) achieved interpretable population-level patterns with subgroups of similar size using a related self-signification instrument; (3) the permutation test makes no distributional assumptions, so the main risk is insufficient sample density to resolve shape differences rather than insufficient statistical power in the classical sense. 50 per group provides headroom for exclusions and supports secondary analyses. Recruiting 60 ensures 50 usable.

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
- Shared stimulus displayed at top of screen
- Brief instruction: "Read the story above, then distribute 100 points across the interpretations below to show how you see this situation. Giving more points to an option means it fits your view better."
- Judgment sliders: three labeled options, each with a numeric input or drag slider, constrained to sum to 100
- After judgment allocation is confirmed, reasoning sliders appear
- Brief instruction: "Now distribute 100 points across the reasons below to show why you see it that way."
- Reasoning sliders: three labeled options plus a user-labeled "other" option, constrained to sum to 100
- If respondent allocates any weight to "other," a text field appears for them to label their reason
- Confirm button

**Screen 3: Scenario 2.**
- Same flow as Screen 2, second stimulus and slider sets

**Attention checks.** Two quality checks are embedded in the study: (1) A single attention-check item in the demographics section ("For this question, please select 'Agree'") to catch inattentive respondents. (2) Post-hoc time filter: respondents who complete a scenario (stimulus reading + both slider allocations) in under 45 seconds are flagged for review, as this pace is inconsistent with thoughtful engagement. Flagged respondents are excluded only if their allocations also show minimal engagement (e.g., all weight on a single option for both slider sets). Prolific's built-in quality metrics (approval rate > 95%, previous submissions flagged for quality) provide additional screening.

**Screen 4: Debrief.**
- Thank you message
- Prolific completion code displayed
- Optional: "Is there anything about these questions that felt unclear or uncomfortable?" (free text, for instrument improvement)

**Data captured per respondent:**
- Demographic fields (8-10 fields)
- Scenario 1: judgment slider allocations (array summing to 100), reasoning slider allocations (array summing to 100), "other" label text (if used), timestamp
- Scenario 2: judgment slider allocations, reasoning slider allocations, "other" label text (if used), timestamp
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

Compute earth mover's distance (EMD) between Population A and Population B slider distributions for each scenario separately, for both judgment and reasoning sliders. Each respondent's slider allocation is a point on a simplex (three or four values summing to 1, after normalizing from the 100-point allocation). EMD measures the minimum work required to transform one population's distribution into the other, using a uniform ground metric (all simplex vertices equidistant). The uniform metric is the appropriate default when no principled basis exists for assigning semantic distances between moral interpretations (Rubner et al., 2000).

Four EMD scores are computed: Scenario 1 judgment, Scenario 1 reasoning, Scenario 2 judgment, Scenario 2 reasoning.

**Significance testing:** Permutation test with 10,000 iterations per EMD score. For each iteration, randomly reassign population labels to all respondents and recompute EMD. The p-value is the proportion of permuted EMDs that equal or exceed the observed EMD. Reject the null hypothesis (no distributional difference) if p < 0.05.

**Expected outcome:** If the Moral Machine data and MFQ literature are correct about these populations, judgment EMD should be significantly larger than chance for both scenarios, with a larger effect for Scenario 1 (moral domain boundary) than Scenario 2 (moral agent constitution). Reasoning EMD provides the additional signal the paper's architecture requires: do populations that converge on judgment also converge on reasoning (candidate universal), or do they reach similar judgments through different reasoning paths (contingent agreement)?

### Secondary Analyses

**Distribution visualization.** Plot both populations as density heatmaps on the simplex for each scenario and slider set. Visual inspection reveals whether the populations cluster in different regions, along different edges, or with different spread patterns.

**"Other" usage diagnostic.** Compute the proportion of each population allocating any weight to "other" on the reasoning sliders, and the proportion allocating more than 20 points to "other." High "other" usage in one population but not the other signals that the reasoning options do not span the moral reasoning space for that population. This is the instrument's self-diagnostic: high "other" rates indicate where the slider labels need revision, not where the population is indifferent. Qualitative analysis of the "other" labels reveals what reasoning the instrument designers missed.

**Extreme-allocation diagnostic.** Compute the proportion of each population placing 90+ points on a single judgment option. Heavy extreme-allocation in both populations suggests the judgment options produce forced-choice-like behavior despite the constrained allocation format. This would undermine the distributional resolution the instrument is designed to provide and would indicate that slider labels need revision to invite more nuanced allocation.

**Dimensional independence.** Each respondent completes both scenarios. Compute the correlation between Scenario 1 judgment allocations and Scenario 2 judgment allocations within each population. Low correlation supports the paper's claim that the structural dimensions are independent. High correlation suggests they co-vary within populations, which is informative for the architecture but complicates per-dimension analysis.

**Classification function preview.** For each scenario, apply the paper's two-stage classification logic: if judgment EMD falls below a threshold, check reasoning EMD. This produces a preliminary classification (candidate universal, contingent agreement, or cultural contingency) for each dimension with these two populations. The threshold is determined from the natural clustering in the four EMD scores rather than set a priori. This is exploratory, not confirmatory -- two populations cannot validate a classification function designed for multiple populations -- but it previews whether the classification machinery produces interpretable results.

---

## Ethics

This study collects moral judgments from human participants using shared stimuli. Ethical requirements:

**Informed consent.** Participants receive a study description on Screen 1 explaining that they will be asked to read short stories about moral situations and indicate how they interpret them using slider tools. They are informed that their responses are anonymous (linked only to Prolific ID for payment), that data will be used for research on moral framework measurement, and that they may withdraw at any time without penalty. Consent is recorded via checkbox before any data is collected.

**IRB or equivalent review.** If conducted through an institutional affiliation, IRB approval or exemption determination is required before launch. If conducted independently, Prolific's own ethics review process provides baseline coverage (Prolific requires all studies to meet their ethical guidelines, including informed consent, right to withdraw, and fair compensation). In either case, the study protocol should be reviewed by at least one person with human subjects research training before recruitment begins. The scenarios present everyday moral situations (community criticism, family obligation), not personal trauma, and the shared stimulus format means respondents interpret a third-person story rather than disclosing personal experiences, minimizing risk of distress.

**Data protection.** Slider allocations and "other" labels are stored in Supabase with row-level security. Prolific IDs are stored separately from response data and used only for payment reconciliation. No identifying information (names, locations, specific institutions) is solicited. Published results will use aggregate distributions and anonymized "other" labels only.

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

The iteration buffer is the most important budget line. The first run almost always reveals something: a stimulus that confuses respondents, a slider label that channels responses in unexpected ways, a population filter that doesn't produce the expected demographic profile. If the first round works cleanly and produces clear results, the buffer is unspent and total cost is under $1,000.

---

## Timeline

| Week | Activity |
|:-----|:---------|
| 1 | Build app with Claude Code. Deploy on Vercel. Internal testing with 5-10 unpaid respondents (colleagues, friends). Fix UX issues. Set up Prolific account and configure studies. |
| 2 | Launch both Prolific studies. Monitor completion rates, check for obvious data quality issues (all-single-option allocations, sub-30-second sessions). Pause and adjust if problems appear. |
| 3 | Close first-round recruitment. Run primary analysis (EMD + permutation tests for all four slider sets). Visualize distributions. Check "other" usage rates. Assess whether instrument adjustments are needed. |
| 4 | If adjustments needed: revise slider labels or stimuli, recruit second round. If first round is clean: finalize analysis, write up results, prepare summary for collaborators. |

---

## Success Criteria

**Strong positive result:** Both scenarios produce statistically significant (p < 0.05) judgment EMD differences between populations, with visible distributional separation on the simplex. Reasoning EMD reveals whether convergent judgments rest on shared or divergent reasoning. "Other" usage is low in both populations (reasoning options span the space). This is the result that makes the paper's architecture credible and changes every subsequent conversation from theoretical to empirical.

**Weak positive result:** One scenario produces significant judgment EMD, the other does not. This suggests the instrument works for some dimensions but not others, or that the stimulus or slider labels for the non-significant scenario need revision. Still valuable: demonstrates proof of concept on one dimension and identifies where the instrument needs improvement.

**Null result:** Neither scenario produces significant judgment EMD. The populations' slider distributions are indistinguishable. This means either (a) the instrument lacks resolution to detect framework variation that other instruments (MFQ, WVS) detect, (b) online-recruited South Asian immigrants in the US have already converged toward WEIRD moral frameworks, or (c) the stimuli and slider designs do not activate the intended dimensions. Each interpretation has different implications. (a) is the most damaging to the paper's architecture. (b) supports the paper's argument about app-only deployment risk. (c) is fixable with instrument revision.

**High "other" diagnostic result:** One or both populations allocate substantial weight to "other" on the reasoning sliders. This signals that the pre-defined reasoning options do not span the moral reasoning space for that population. The paper predicts this as a possible outcome and interprets it as instrument design signal rather than population indifference. Qualitative analysis of the "other" labels reveals what reasoning the designers missed. Redesign the reasoning sliders and retest.

---

## What This Experiment Does Not Test

- The variance-modified reward mechanism (requires RLHF infrastructure and substantially more budget)
- The classification function's three-category output at scale (requires more than two populations)
- Cross-linguistic comparison (both populations respond in English)
- The community facilitator model (uses online recruitment, not facilitators)
- Whether changed training signal produces changed model behavior (requires ML collaboration)

What it tests is the foundation: does the instrument detect what the paper says it should detect?

---

## Relationship to the Paper

This experiment corresponds to the minimum viable study described in Section 9 of "Beyond WEIRD Defaults": deploying the constrained allocation instrument across two populations with known framework differences and testing whether slider distributions track those known differences after controlling for demographic confounds.

If the results are positive, they provide the first empirical evidence that the paper's upstream signal collection mechanism works. This evidence transforms the paper from a theoretical architecture into a partially validated one, and transforms conversations with potential collaborators from "interesting proposal" to "here are the data, what do we do next?"

---

## Next Steps After Results

**If positive:** Share results with potential academic collaborators. Expand to the full California pilot with four populations, four scenarios, and the balanced incomplete block design described in the paper. Seek grant funding or collaboration partnership for the expanded pilot.

**If null:** Diagnose which interpretation applies (instrument resolution, population convergence, or scenario design). If instrument resolution, consider whether the constrained allocation format needs modification or whether additional collection mechanisms are needed. If population convergence, this is evidence for the paper's app-deployment-risk argument and motivation for facilitator-based recruitment of less-connected populations. If scenario design, revise stimuli and slider labels and retest within the remaining iteration budget.

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
