# Literature-Derived Convergence/Divergence Map
### Beyond WEIRD Defaults — Supplementary Analysis

---

## Purpose and Limitations

This document examines whether the convergence/divergence patterns predicted by the classification function concept in "Beyond WEIRD Defaults" are observable in existing cross-cultural moral psychology literature. It is not a dataset. It is a structured literature synthesis organized around the paper's four framework dimensions — moral agent constitution, authority legitimacy, moral domain boundary, and scope of moral obligation — mapping published empirical findings to the question: where do diverse moral frameworks converge, and where do they systematically diverge?

**What this demonstrates:** The convergence/divergence pattern the classification function would detect is real and already documented — cross-cultural research consistently finds domains of near-universal agreement alongside domains of systematic, culturally-patterned disagreement.

**What this does not demonstrate:** That the constrained allocation instrument specifically captures this signal better than existing survey instruments. That the shared stimuli and slider designs in the paper would produce the predicted population-level distributions. That the classification function's output would be technically translatable into RLHF-compatible training signal. Those remain open questions requiring empirical work and ML formalization.

**Methodological limitations:** This synthesis draws on published findings from survey-based cross-cultural research — precisely the kind of "conclusions stripped of reasoning" that the paper argues is insufficient. The irony is acknowledged. The purpose here is not to replicate the paper's instrument methodology but to establish that the underlying phenomenon (patterned convergence and divergence across moral frameworks) exists in the empirical record, providing grounds for confidence that a richer instrument would detect it.

**Sources:** World Values Survey (WVS, 7 waves, 100+ countries), Moral Foundations Questionnaire (MFQ, cross-cultural administrations), Schwartz Value Survey (SVS, 78 nations), Hofstede/Minkov-Kaasa individualism-collectivism index (102 countries), Moral Machine experiment (233 countries), and targeted cross-cultural moral psychology studies.

---

## Dimension 1: Moral Agent Constitution

**Paper's prediction:** This dimension should show systematic divergence — communities differ fundamentally in how the moral agent itself is constituted (autonomous individual vs. person-in-relation vs. hierarchically embedded), and this difference shapes moral judgment across a wide range of domains.

**What the literature shows:**

*Divergence (strong, systematic, well-documented):*

The individualism-collectivism dimension is the most studied and most validated construct in cross-cultural psychology, with research spanning 40+ years across 100+ countries. The Minkov-Kaasa index, derived from nationally representative World Values Survey samples across 102 countries, shows that the most individualist societies (US, Australia, UK, Netherlands, Nordics) and the most collectivist (many East Asian, South Asian, Latin American, and African nations) occupy genuinely different positions on this dimension, with the divergence correlated to but not reducible to economic development.

Haidt, Koller, and Dias (1993) found that while acts causing physical and psychological harm are prohibited across cultures, judgments about harmless norm violations (e.g., private consensual acts, ritual practices) diverge sharply — individualist cultures tend to restrict moral judgment to harm-based reasoning, while collectivist cultures extend moral authority to domains individualists consider matters of personal choice.

Vauclair and Fischer (2011), using WVS data with multilevel modeling, found that moral issues can be differentiated cross-culturally into two domains: dishonest-illegal behaviors (where cultural values have little predictive power — convergence) and personal-sexual behaviors (where cultural conceptions of the self, specifically independent vs. interdependent, significantly predict moral attitudes — divergence).

Research on collectivists' moral judgments of selfless behavior found that collectivists hold significantly higher moral judgment for selfless prosocial behavior compared to individualists, while individualist moral judgment did not change significantly with behavioral selflessness. The moral significance of selflessness itself varies by framework.

*Convergence:*

Despite deep divergence on the primacy of individual vs. collective, there is convergence on the *existence* of both levels of moral obligation. No studied culture entirely lacks obligations to the collective, and none entirely lacks recognition of individual moral agency. The disagreement is about primacy and scope, not about whether both exist.

**Assessment:** Strong support for divergence. This dimension would reliably produce different slider distributions across framework-diverse populations. An LLM trained only on individualist moral signal would systematically mishandle prompts involving family obligation, community responsibility, and the moral weight of group harmony. The divergence draws on the loyalty, care, and liberty foundations but is not reducible to any single one — it is a framework-level pattern that emerges when these foundations aggregate across populations.

---

## Dimension 2: Authority Legitimacy

**Paper's prediction:** Populations should differ systematically in whether institutional authority is treated as morally legitimate by default, and this should shape moral judgment about rule-following, dissent, and the legitimacy of formal vs. informal governance. This dimension draws on Haidt's authority/subversion and liberty/oppression foundations.

**What the literature shows:**

*Divergence (strong, multi-dimensional):*

The WVS's Traditional vs. Secular-Rational dimension captures a major axis of variation in attitudes toward authority. Traditional-values societies emphasize deference to authority, religion, parent-child ties, and national pride. Secular-rational societies place less emphasis on these and are more tolerant of divorce, abortion, euthanasia, and other challenges to traditional authority structures.

Schwartz's cultural mapping identifies seven transnational cultural groupings across 76 nations. The Hierarchy vs. Egalitarianism dimension directly captures variation in whether hierarchical authority systems are accepted as legitimate moral structures or resisted in favor of recognizing all persons as moral equals. West European and English-speaking cultures cluster toward egalitarianism; South Asian, Confucian-influenced, and African/Middle Eastern cultures show more variation, with many clustering toward hierarchy or embeddedness.

Institutional trust itself varies dramatically by cultural context. Schwartz (2007) reports that country-level differences account for 19% of variability in generalized trust. At the individual level, self-direction values (independence, taking responsibility) predict *lower* institutional trust, while conservation values (tradition, conformity, security) predict *higher* trust — but the strength and direction of these relationships varies across countries, suggesting the meaning of institutional trust itself is culturally contingent.

Critically, in contexts where institutions have historically been instruments of extraction rather than protection — colonial and post-colonial settings, communities with histories of state violence — the relationship between institutional authority and moral legitimacy may be inverted. A rule-following orientation that reads as civic virtue in high-trust societies may read as complicity in low-trust ones. This is precisely the kind of divergence the rationalization layer is designed to detect.

*Convergence:*

Across cultures, there is convergence on the principle that *some* form of social coordination is necessary and morally legitimate. The disagreement is about what forms of authority deserve moral deference, not about whether authority per se has moral standing.

There is also near-universal condemnation of dishonest behavior by authorities — corruption, bribery, abuse of power. Vauclair and Fischer's finding that attitudes toward dishonest-illegal behaviors show less cultural variation than personal-sexual behaviors applies here: the moral wrongness of institutional betrayal converges across frameworks, even as the legitimacy of institutional authority diverges.

**Assessment:** Strong support for divergence on the legitimacy and scope of institutional authority, with convergence on the wrongness of authority's betrayal. An LLM that defaults to treating institutional rules as morally legitimate would mishandle prompts from users in low-trust contexts. The rationalization layer would detect this divergence clearly.

---

## Dimension 3: Moral Domain Boundary

**Paper's prediction:** Populations should differ systematically in what counts as a moral question at all — specifically, whether moral judgment extends beyond harm and fairness to include sanctity, purity, ritual obligation, and body-related domains. This is grounded in Haidt's sanctity/degradation foundation and the broader MFT finding that WEIRD populations narrow the moral domain while non-WEIRD populations extend it.

**What the literature shows:**

*Divergence (strong, well-documented, and among the sharpest WEIRD/non-WEIRD splits):*

Haidt, Koller, and Dias (1993) is the foundational study. They presented participants in Philadelphia, Porto Alegre (Brazil), and Recife (Brazil) with stories describing actions that violated social norms but caused no demonstrable harm — for example, cleaning a toilet with a national flag, or eating a pet dog that had been killed by a car. American adults (especially high-SES) consistently judged these acts as disgusting but not morally wrong — "it's their choice." Brazilian participants and American children judged them as genuinely immoral. The divergence was not about different answers to the same moral question but about whether the situation constituted a moral question in the first place. WEIRD adults shrink the moral domain to harm and fairness; other populations include sanctity, pollution, and ritual propriety as morally binding.

Vauclair and Fischer (2011) confirmed this at scale using WVS data: their "personal-sexual behaviors" domain — which includes sanctity-adjacent judgments about sexuality, bodily autonomy, and private conduct — showed strong cultural variation predicted by self-construal (independent vs. interdependent), while their "dishonest-illegal behaviors" domain showed much less cultural variation. The moral domain itself has a culturally variable boundary.

Schwartz's Embeddedness value type — which includes respect for tradition, social order, and propriety — maps onto the same divide. Cultures high on embeddedness treat violations of social and ritual propriety as morally significant; cultures high on intellectual and affective autonomy treat them as matters of personal expression. The difference is not about strictness or conservatism; it is about whether an entire category of human behavior falls inside or outside the moral domain.

Research on moral judgments of sexual behavior, food practices, and religious observance across cultures consistently shows the same pattern: WEIRD populations classify these as "not a moral issue" while many non-WEIRD populations classify them as among the most important moral issues. This is the gap the current alignment signal misses most completely — a model trained on WEIRD signal does not give the wrong answer to sanctity questions; it fails to recognize them as moral questions at all.

*Convergence:*

There is convergence on the principle that some behaviors are morally significant regardless of whether they cause measurable harm — even WEIRD populations recognize a residual category of "taboo" behaviors that provoke moral judgment absent harm (e.g., incest between consenting adults). The disagreement is about how large and how morally weighty this category is, not about whether it exists.

**Assessment:** Strong support for divergence, and arguably the most consequential dimension for AI alignment. The classification function detects a distinctive pattern here: not divergence in how populations weight competing moral claims within a shared moral domain, but divergence in whether a domain registers as morally relevant in the first place. This is where a calibrated model would behave most differently from a WEIRD-defaulting one — recognizing embedded moral dimensions that its default framework does not see as moral. This is the Tier 1 → Tier 4 behavioral shift the evaluation rubric targets.

---

## Dimension 4: Scope of Moral Obligation

**Paper's prediction:** Cultures should differ in who counts as a moral subject — who has standing to make claims, whose welfare weighs in moral calculations, where the boundary of moral community falls, and how far forward in time moral obligation extends. This dimension absorbs temporal horizon as scope extended through time rather than a separate structural feature.

**What the literature shows:**

*Divergence (strong, multifaceted):*

The Moral Machine experiment's three cultural clusters (Western, Eastern, Southern) showed systematic variation in the relative moral weight given to different categories of beings — the young vs. the old, high-status vs. low-status individuals, humans vs. animals, those following rules vs. those violating them. These preferences correlated with Hofstede's individualism scores, Inglehart's cultural map dimensions, and institutional quality indicators.

Haidt's Moral Foundations Theory documents that the loyalty, authority, and sanctity foundations — which effectively define the *boundaries* of the moral community — vary dramatically across cultures. WEIRD populations narrowly define the moral community around individual rights-bearers; non-WEIRD populations more commonly include extended kin networks, community structures, ancestral obligations, and in some cases non-human entities as morally relevant.

Schwartz's Universalism value type (tolerance, social justice, equality, protection for all people and nature) shows significant cross-cultural variation in emphasis. Cultures high on embeddedness tend to draw tighter boundaries around the moral community (in-group focused), while cultures high on intellectual autonomy tend toward more expansive boundaries.

The temporal extension of scope shows meaningful cross-cultural variation. Confucian-influenced cultures place explicit moral weight on intergenerational obligation — filial piety extends backward to ancestors and forward to descendants. Indigenous cultures with relational and land-based moral structures often embed obligations that extend across generations and to non-human entities. Western moral philosophy has historically treated intergenerational obligation as a special case rather than a foundational moral category. Research on environmental moral reasoning shows significant cross-cultural variation in willingness to accept present costs for future benefits, correlated to cultural dimensions (collectivism, long-term orientation) as well as economic development. Temporal horizon is not a separate structural dimension; it is scope of moral obligation extended through time.

*Convergence:*

There is near-universal convergence on the moral status of close kin — obligations to children and immediate family are recognized across essentially all studied cultures. The moral weight of harm to children specifically shows the strongest convergence in the Moral Machine data.

There is also convergence on the principle that the scope of moral consideration is *not unlimited* — every culture draws boundaries, even if those boundaries are drawn very differently. The disagreement is about where the boundaries fall and how far forward in time they extend, not about whether boundaries exist. Similarly, there is broad convergence that present actions have future consequences and that some consideration of the future is morally relevant.

**Assessment:** Strong support for divergence on where the moral community's boundaries are drawn — in social space and in time — with convergence on the moral status of close kin and especially children. The integration of temporal horizon into this dimension resolves a previous weakness: temporal reasoning was less cleanly measured as a standalone axis but is well-grounded as a feature of scope. An LLM that defaults to a Western individual-rights framework for moral consideration would systematically mishandle prompts from users operating within Ubuntu, Confucian, or Indigenous moral frameworks where obligation extends across generations and relational networks.

---

## Cross-Dimension Pattern: What Converges, What Diverges

**Domains of convergence (candidate universals):**
- Harm to children is wrong
- Betrayal of trust by those in authority is wrong
- Some obligation to close kin exists
- Both individual and collective moral obligations exist (disagreement is about constitution and primacy)
- Some behaviors are morally significant beyond measurable harm (disagreement is about scope)
- Present actions have morally relevant future consequences
- The scope of moral obligation has boundaries (disagreement is about where and how far forward)
- Unfairness is wrong (disagreement is about what constitutes unfairness — a derived judgment contingent on the structural dimensions)

**Domains of systematic divergence (cultural contingency):**
- How the moral agent is constituted — autonomous individual, person-in-relation, or hierarchically embedded (Dimension 1)
- Whether institutional authority is morally legitimate by default (Dimension 2)
- Whether a given domain — sanctity, purity, ritual, body-related behavior — constitutes a moral question at all (Dimension 3)
- Who counts as a moral subject, where the moral community's boundaries fall, and how far forward in time obligation extends (Dimension 4)
- Whether selflessness is a moral imperative or a supererogatory virtue (Dimensions 1 and 4)
- Which cultural framework should accommodate which in cross-cultural encounters (all dimensions)
- What constitutes "fair" treatment — equal treatment, relational balance, hierarchical allocation, or need-based distribution (derived from positions on Dimensions 1–4)

**The pattern:** Convergence clusters around harm, betrayal, and protection of the vulnerable. Divergence clusters around the *structure* of moral reasoning — how the moral agent is constituted, what counts as a moral domain, where authority is legitimate, and how far moral obligation extends. The MFT foundations produce the content-level signal; the four dimensions describe the framework-level patterns the classification function detects when that signal aggregates across populations. Fairness emerges as a derived judgment: universal as a principle, culturally contingent in its content, with the contingency tracking the structural dimensions. This is precisely the distinction the classification function is designed to detect: convergence as candidate universal signal, divergence as cultural contingency requiring humility rather than confident defaults.

---

## Implications for the Paper

This literature synthesis supports three claims:

1. **The convergence/divergence pattern is real.** It is not an artifact of the paper's theoretical framework. Multiple independent research programs using different instruments across different populations find the same basic pattern: near-universal agreement on core harm-based principles, systematic and culturally-patterned disagreement on the structural features of moral reasoning.

2. **The divergence is not noise.** It maps to identifiable cultural, historical, and institutional factors. It clusters geographically and correlates with validated cultural dimensions. It is exactly the kind of structured information the classification function is designed to preserve rather than collapse.

3. **Existing instruments undercount the divergence.** The richest divergence is in the *structure* of moral reasoning — who is a moral agent, what counts as a moral matter — rather than in conclusions about specific cases. Survey instruments that present specific cases and ask for judgments capture the conclusions but miss the underlying framework differences. This supports the paper's argument that an instrument capturing both judgment and reasoning (constrained allocation sliders on shared stimuli) would produce richer signal than conclusions-only instruments, though it does not empirically demonstrate it.

The strongest honest claim: the literature provides grounds for confidence that the classification function would have real signal to work with. The weakest honest claim: this synthesis cannot demonstrate that the proposed instrument would capture that signal more effectively than existing instruments, because no one has tried it.

---

## Key Sources

- World Values Survey, Waves 1–7 (1981–2022). 100+ countries, nationally representative samples. Inglehart-Welzel cultural map dimensions (Traditional/Secular-Rational, Survival/Self-Expression).
- Schwartz, S. H. (1994, 2004, 2006). Theory of cultural value orientations. 78 nations, 7 transnational cultural groupings, 3 bipolar cultural dimensions (Embeddedness/Autonomy, Hierarchy/Egalitarianism, Mastery/Harmony).
- Hofstede/Minkov-Kaasa individualism-collectivism index (2023 update). 102 countries, derived from nationally representative WVS samples.
- Haidt, J. (2012). Moral Foundations Theory. Six foundations varying in emphasis across cultures.
- Haidt, J., Koller, S. H., & Dias, M. G. (1993). Affect, culture, and morality. Cross-cultural study of moral judgments about harmless norm violations.
- Vauclair, C.-M., & Fischer, R. (2011). Do cultural values predict individuals' moral attitudes? Multilevel analysis using WVS MDBS items. Two moral domains with different cultural sensitivity.
- Awad, E., et al. (2018). The Moral Machine experiment. 40M decisions, 233 countries, 3 cultural clusters.
- Schwartz, S. H. (2007). European Social Survey analysis. Country-level vs. individual-level predictors of generalized trust.
- Santos, H. C., Varnum, M. E. W., & Grossmann, I. (2017). Individualistic practices and values increasing around the world. 78 countries, 51 years of data.

---

*This document is a working supplement. It should be updated as the paper develops and if pilot data becomes available.*

*Last updated: March 19, 2026 — Axes renamed to dimensions, grounded in MFT. Temporal horizon absorbed into scope. Moral domain boundary (sanctity/degradation) added as Dimension 3. Fairness treated as derived judgment. Cross-dimension pattern updated. Terminology updated: rationalization layer → classification function, triad → slider distributions.*
