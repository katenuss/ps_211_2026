---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 19
exportFilename: ps211_fall2026_lecture19
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 19: Research Ethics, Chi-Square & Non-Parametric Tests

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- Reminder: our second ==Data Write-Up== (ANOVA-based) is due **this coming Tuesday, December 8** at 11:59 p.m. — don't leave it to the last minute!
- ==Exam 4== is on **Thursday, Dec. 10** during class.
   - Review sheet will be posted today or tomorrow.
    - Focuses on Lectures 15 - 19.
    - **NO MAKE-UPS**
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate)
- Discussion 13 (Wed. 12/9): course wrap-up & Exam 4 practice.
- ==Course evaluations== are open.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where we are: the last lecture

:: content ::

Eighteen lectures of tools. Today is the last new material, in three parts:

<div class="grid grid-cols-3 gap-3 mt-4 text-sm">
<div class="border-2 border-gray-300 rounded-lg p-3"><b>1. The core idea, one more time</b><br/>Every test statistic is a signal-to-noise ratio. Why that is the thing to remember.</div>
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3"><b>2. When the machinery is misused</b><br/>p-hacking, the replication crisis, and what honest science looks like now. The most important part of today.</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>3. One last family of tests</b><br/>Outcomes that are categories, not numbers: chi-square and other non-parametric tests.</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Tuesday is the Exam 4 review and Wednesday's Discussion 13 is Exam 4 practice, so part 3 stays light. Part 2 is the one to take with you.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: the core idea

::content::

- We use inferential statistics to evaluate whether the patterns we see in our sample data are likely to reflect ==true effects in the population==, or if they could have arisen just by chance due to variability.

<p v-click>

- We can think of all statistical tests as comparing **signal** to **noise**:
    - Signal: the meaningful effect we are trying to detect (e.g., difference between groups, association between variables)
    - Noise: the random variability that obscures the signal (e.g., individual differences, measurement error)

</p>

<p v-click>

- The key question: **Is the signal strong enough relative to the noise to conclude that there is a real effect in the population?**

</p>

<p v-click>

<div class="flex items-center gap-4 mt-1">
<IceCream :size="60" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">If you remember one thing from this course, let it be this: every test statistic we've covered — <i>z</i>, <i>t</i>, <i>F</i>, even <i>r</i> — is a signal-to-noise ratio!</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Review: Standard Deviation and Standard Error

::left::

### **Standard Deviation (SD)**
- One measure of the **spread of individual scores** (variability) in a sample/population
- High SD: lots of variability among individuals
- Low SD: individuals are similar to each other

<p v-click>

- When there is more variability in the data, it is harder to detect true effects (signal) because the noise is larger.

</p>

<p v-click>

*Example: High variability in anxiety levels can make it more challenging to identify whether a treatment is effective, as the noise (individual differences) may obscure the signal (treatment effect).*

</p>

::right::

<p v-click>

### **Standard Error (SE)**
- Equal to the SD of the sampling distribution of the mean.
- Describes **how much sample means vary** across repeated samples. Quantifies uncertainty in our estimate of the population mean.
- Answers the question: *If we took many samples from the same population, how much would their means differ from each other?*

</p>

<p v-click>

- Formula:
  **SE = SD / √n**

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Why Sample Size Matters

:: content ::

- Remember, test statistics depend on both effect size (signal) and variability (noise).
- **Sample size (n)** directly affects the standard error (SE):
  **SE = SD / √n**
- Larger samples reduce the SD of the sampling distribution (SE), making our estimates more precise.
- This reduces noise in our signal-to-noise ratio, and makes it easier to detect true effects.

---
layout: section
color: indigo-light
align: lt
---

Part 2. When the machinery gets misused...
# Research ethics: p-hacking and the replication crisis

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why ethics belongs in a statistics course

:: content ::

- Every test in this course rests on one promise: with α = .05, **if nothing is real, we get fooled only 5% of the time.**
- That promise holds for **one test, planned in advance**. (Lecture 15: running more *t* tests than planned is exactly why post-hoc corrections exist.)

<p v-click>

- Today: the ordinary, usually well-intentioned ways researchers break that promise, how much it costs, how common it is, and how the field is fixing it.
- None of it requires fraud. Most of it was standard practice until about 2011, and some of it still is.

</p>

<p v-click><StickyNote color="amber-light" title="Scope" width="80%">There are whole courses on research ethics: consent, deception, privacy, animal research. Today is only the data-analysis slice, the part a statistics course can do something about.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Flexibility 1: testing many outcomes

:: left ::

- Suppose a study measures **ten** outcomes and there is no real effect on any of them.
- Each test is a separate ticket in the 5% lottery. The chance that *at least one* comes up p < .05 is $1 - 0.95^{10} = 40\%$.

<p v-click>

- Reporting only the winner, as if it had been the plan, is ==**p-hacking**==. Writing the paper as if that outcome was the hypothesis all along is ==**HARKing**== (Hypothesizing After the Results are Known).

</p>

:: right ::

<img src="/images/lecture19/many_outcomes.png" alt="Chance of at least one p below .05 as a function of the number of outcomes tested" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Two groups of n = 20, no real effect; 20,000 fake studies per point. Same math as Lecture 15's multiple comparisons.</div>

<p v-click><StickyNote color="green-light" title="Sound familiar?" width="100%">Your Data Write-Ups had exactly one research question, one outcome and one test, chosen before you looked. That was not an accident.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Flexibility 2: peeking at the data

:: content ::

<img src="/images/lecture19/optional_stopping.png" alt="p-value trajectories of fake studies with no real effect, and the false-positive rate as a function of the number of peeks" class="w-11/12 mx-auto"/>

<p v-click>

- **Left:** 12 fake studies, no real effect, checking p after every 5 participants per group. The red ones "found" something and stopped. Four of twelve.
- **Right:** peek 19 times and your 5% false-positive rate is 23%. This is ==**optional stopping**==: collecting data until p < .05, then stopping. The honest version is Lecture 11: choose n in advance with a power analysis, collect all of it, then look once.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Researcher degrees of freedom

:: left ::

==**Researcher degrees of freedom**== are the choices made *during* a study that could reasonably go either way, and that change the result:

- Which outcome measure to report
- When to stop collecting data
- Which participants count as "outliers"
- Which covariates to control for
- Which conditions, or which subgroups, to report
- One-tailed or two-tailed

<p v-click>

- Alone, each looks like ordinary judgment. The problem is **who decides**: someone who knows which branch helps the hypothesis, deciding after seeing the data.

</p>

:: right ::

<p v-click><StickyNote color="amber-light" title="Why this matters" width="100%">Each choice seems harmless on its own. Together they inflate the false-positive rate dramatically: the same alpha-inflation problem as running many t tests (Lecture 15), hidden inside one study.</StickyNote></p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="t" maxWidth="22rem">Gelman and Loken call this the <b>garden of forking paths</b>: you only walked one path, but you would have found a result on many of them.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# A real example: can a song make you younger?

:: left ::

**The study.** 20 Penn undergraduates listened to either the Beatles' *When I'm Sixty-Four* or *Kalimba* (the sample track that came with Windows 7). Afterward they reported their birth date. Controlling for their father's age, the people who had heard *When I'm Sixty-Four* were nearly 1.5 years **younger** (adjusted M = 20.1 vs. 21.5 years), $F(1, 17) = 4.92$, $p = .040$.

<Admonition title="Question" color="teal-light" width="100%">

Published in *Psychological Science*, with a real p value. What is wrong with it?

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Everything. A song cannot change your birth date. The authors ran it on purpose, using only choices that were normal at the time, to show how easily they produce an impossible finding.

</Admonition>

:: right ::

<p v-click>

**What they actually did** (disclosed in the same paper):

- Ran a **third song condition** and dropped it.
- Measured **many** other outcomes.
- Checked the result after every few participants and **stopped when it worked**.
- Chose the covariate (father's age) **after** looking at the data.

</p>

<p v-click><StickyNote color="amber-light" title="The point" width="100%">Nothing here was fraud. Every step was a researcher degree of freedom. Simmons, Nelson & Simonsohn (2011), <i>Psychological Science</i>.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# How much does flexibility cost?

:: content ::

<img src="/images/lecture19/simmons_table1.png" alt="False-positive rates for four researcher degrees of freedom and their combination, from Simmons et al. 2011" class="w-9/12 mx-auto"/>

<p v-click>

- Simmons et al. simulated each practice on pure noise. Alone, each one roughly **doubles** the false-positive rate. All four together: **61%**. A coin flip, weighted toward a result that is not there.

</p>

<div class="text-xs text-gray-500 mt-1">Simmons, Nelson & Simonsohn (2011), Table 1. Two-sample comparisons, n = 20 per group, α = .05 two-tailed.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# How common is this?

:: left ::

In 2012, John, Loewenstein and Prelec surveyed **2,155 academic psychologists** in the U.S. and asked whether they had ever done each of these things.

<Admonition title="Guess" color="teal-light" width="100%">

What fraction admitted to *not reporting all of a study's outcome measures*?

</Admonition>

<p v-click><StickyNote color="amber-light" title="The real problem" width="100%">Fraud is rare. The everyday practices are not, and in 2012 most researchers did not think of them as cheating.</StickyNote></p>

:: right ::

<p v-click>

<div class="text-sm">

| Practice | Admitted it |
|---|:---:|
| Not reporting all of a study's outcome measures | **63%** |
| Collecting more data after checking whether p < .05 | **56%** |
| Reporting only the studies that "worked" | **46%** |
| Excluding data after seeing the effect of doing so | **38%** |
| Presenting an unexpected finding as predicted (HARKing) | **27%** |
| Rounding p (e.g., .054 reported as "< .05") | **22%** |
| Falsifying data | **0.6%** |

</div>

<div class="text-xs text-gray-500 mt-1">John, Loewenstein & Prelec (2012), <i>Psychological Science</i>; self-admission rates, control condition.</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# The replication crisis

:: left ::

- In 2015, **270 researchers** redid **100 published psychology studies** from 2008, using the original materials and usually larger samples.
- Originals: **97%** significant. Replications: **36%**.
- The replication effect sizes were, on average, **half** the size of the originals.

<p v-click>

- Not all of this is p-hacking: some originals were real but small, some replications differed in details. But a field where a third of its findings hold up has a problem, and the practices on the last few slides are the leading explanation.

</p>

<div class="text-xs text-gray-500 mt-2">Open Science Collaboration (2015), <i>Science</i>.</div>

:: right ::

<img src="/images/lecture19/osc2015.png" alt="Percent significant and mean effect size for original studies versus replications" class="w-full mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Findings you may have heard of

:: content ::

<div class="grid grid-cols-3 gap-4 text-sm">
<div class="border-2 border-gray-300 rounded-lg p-3">
<b>Power posing</b><br/>
Two minutes in an expansive pose raised testosterone and risk-taking (Carney, Cuddy & Yap, 2010; n = 42).<br/><br/>
<span class="text-red-700"><b>Then:</b></span> a replication with n = 200 found no hormonal or behavioral effects; only "feeling more powerful" survived (Ranehill et al., 2015).
</div>
<div class="border-2 border-gray-300 rounded-lg p-3">
<b>Elderly priming</b><br/>
Unscrambling sentences containing words like <i>Florida</i> and <i>bingo</i> made students walk more slowly to the elevator (Bargh, Chen & Burrows, 1996).<br/><br/>
<span class="text-red-700"><b>Then:</b></span> the effect appeared only when experimenters expected it and timed with stopwatches; with automatic timing it vanished (Doyen et al., 2012).
</div>
<div class="border-2 border-gray-300 rounded-lg p-3">
<b>Neonatal imitation</b><br/>
Newborns imitate tongue protrusion and other gestures (Meltzoff & Moore, 1977), a staple of every developmental textbook.<br/><br/>
<span class="text-red-700"><b>Then:</b></span> 106 infants tested at 1, 3, 6 and 9 weeks on 11 gestures showed no imitation (Oostenbroek et al., 2016).
</div>
</div>

<p v-click><StickyNote color="amber-light" title="Small samples, big claims" width="80%">Notice the pattern: tiny original samples, striking findings, large replications that find nothing. Lecture 11 told you why: with low power, a significant result is more likely to be a fluke than a discovery.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Let's p-hack: a fake study, step by step

:: left ::

**The study.** 50 students, randomly assigned to study with lo-fi music or in silence. Ten outcome measures: quiz score, recall, focus, mood, reaction time, creativity, enjoyment, stress, confidence, attention.

<StickyNote color="amber-light" title="The catch" width="100%">Every number was made by a random number generator. There is <b>no real effect of anything on anything</b>. Watch what a researcher who badly wants a result can do with it.</StickyNote>

<p v-click><div class="text-sm text-gray-600 mt-2">Script and data: <code>r_demos/p_hacking_class_demo_2026.R</code>. Run it yourself.</div></p>

:: right ::

```r
# Step 1: the planned test (n = 20 per group)
t.test(quiz_score ~ group, data = first40, var.equal = TRUE)
#> t = -0.4876, df = 38, p-value = 0.6286
```

<p v-click>

Nothing. The honest move: stop here, report it.

```r
# Step 2: "but we measured ten things..."
round(sort(p_values), 2)
#>  creativity reaction_time   stress  confidence   recall
#>        0.08          0.16     0.34        0.37     0.38
#>        mood     attention quiz_score enjoyment    focus
#>        0.40          0.50       0.63      0.67     0.75
```

</p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Creativity is at p = .08. Nobody planned to look at creativity. What does a motivated researcher do next?

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Let's p-hack: steps 3 and 4, and the write-up

:: left ::

```r
# Step 3: "so close!" Recruit 10 more
# students (5 per group) and look again.
t.test(creativity ~ group, data = d, var.equal = TRUE)
#> t = 2.0324, df = 48, p-value = 0.04767
```

<p v-click>

Significant! Ten random participants ago it was .08.

```r
# Step 4: one silence student scored 31.7 on
# creativity, far above the rest. "An outlier."
cleaned <- filter(d, id != 29)
t.test(creativity ~ group, data = cleaned, var.equal = TRUE)
#> t = 2.5325, df = 47, p-value = 0.01473
```

</p>

:: right ::

<p v-click><Admonition title="The published version" color="red-light" width="100%">

"Students who studied with lo-fi music generated more creative uses (M = 21.9, SD = 5.6) than students who studied in silence (M = 18.5, SD = 3.7), t(47) = 2.53, p = .015, d = 0.72."

</Admonition></p>

<p v-click><Admonition title="The honest version" color="green-light" width="100%">

"As preregistered, we tested whether music affected quiz scores; it did not, t(38) = −0.49, p = .63. Exploratory tests of nine other measures found no significant differences (all p > .08)."

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Every number in the first version is true" width="100%">The finding is not. Ten outcomes, peeking, and a convenient outlier turned noise into p = .015.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# The fix: decide before you look

:: left ::

- ==**Preregistration**==: write down the hypothesis, sample size, outcome, exclusion rules and analysis *before* collecting data, on a public registry (OSF, AsPredicted). Every fork in the garden is now closed.
- ==**Registered reports**==: journals review and accept the plan before the results exist, so "it didn't work" gets published too.
- **Report everything**: all conditions, measures and exclusions. Exploratory analyses are fine, labeled as exploratory.
- **Effect sizes and confidence intervals**, not just p (Lecture 11).
- **Share data and code**, so anyone can rerun the analysis.

:: right ::

<p v-click>

**Why it works**

- Transparency: readers can see the forks.
- Reproducibility: the analysis can be checked.
- Honest null results enter the literature.
- Researcher degrees of freedom are spent *before* the data can influence them.

</p>

<p v-click><StickyNote color="green-light" title="You already did this" width="100%">In Discussion 4 you wrote a research question and a hypothesis before running a single test, and you reported one planned test. That is a small preregistration.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: research ethics

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher measures eight outcomes, finds that one differs between groups at $p = .03$, and writes the paper as if that outcome had been the hypothesis from the start. What is the main problem?

- **A)** The test should have been one-tailed.
- **B)** With eight outcomes, the chance of at least one $p < .05$ by luck alone is about 34%, so this is weak evidence, and presenting it as the planned test hides that (HARKing).
- **C)** $p = .03$ is not below $.01$, so the result is not significant.
- **D)** There is no problem as long as the statistics were computed correctly.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** $1 - 0.95^8 = 0.34$. The numbers are all correct; the *story* about them is not.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Which of these would **not** help reduce false positives?

- **A)** Preregistering the analysis plan.
- **B)** Reporting all of the outcomes that were measured.
- **C)** Collecting data until $p$ drops below $.05$, then stopping.
- **D)** Deciding the sample size in advance with a power analysis.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** That is optional stopping; it raises the false-positive rate. (A), (B) and (D) are the fixes.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

Part 3. One last family of tests...
# Categorical outcomes: chi-square and non-parametric tests

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Assumptions of Parametric Tests

:: content ::
The tests we have discussed so far assume that:
- Data are randomly sampled
- Observations are independent
- Distribution of scores (or residuals) in the population is **approximately normal**
- Outcome variable is ==numeric==
    - Interval or ratio scale
    - Not ordinal or categorical

<p v-click>

- When assumptions hold: parametric tests are powerful.
- When badly violated: results can be biased.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Non-parametric tests

:: left ::

- Make **no assumption** that scores follow a normal (or any particular) distribution. They work with **ranks** (which score was biggest, second biggest...) or **counts** instead of raw scores.
- Reach for them when the sample is small and clearly skewed, the outcome is ordinal (rankings, Likert items), there are extreme outliers, or the outcome is a **category** rather than a number.

<p v-click><StickyNote color="amber-light" title="The trade" width="100%">Fewer assumptions, less power. When a parametric test's assumptions hold, use it.</StickyNote></p>

:: right ::

<div class="text-sm">

**Rank-based twins of the tests you know** (do not memorize; just know they exist)

- Independent-samples *t* → Mann–Whitney *U*; paired-samples *t* → Wilcoxon signed-rank
- One-way ANOVA → Kruskal–Wallis; repeated-measures ANOVA → Friedman
- Pearson *r* → Spearman's ρ

**For categorical outcomes** (the rest of today)

| Question | Test |
|---|---|
| One categorical variable: do the counts match a prediction? | **Chi-square goodness-of-fit** |
| Two categorical variables: are they related? | **Chi-square test of independence** |

</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Chi-square tests: counts instead of means

:: content ::

- Used when the **outcome is a category**: which dining hall, which hand, yes or no. The data are **counts** in each category, not scores.
- The test compares the counts we **observed** with the counts we would **expect** if $H_0$ were true:

$$\chi^2 = \sum \frac{(\text{observed} - \text{expected})^2}{\text{expected}}$$

<p v-click>

- Same shape as every test so far: a **signal** (how far the observed counts are from $H_0$'s prediction) over **noise** (how big the expected counts are). Big discrepancies give a big $\chi^2$ and a small p.
- The null world is the **chi-square distribution**; its df come from the number of categories, not the number of people.

</p>

<p v-click><StickyNote color="green-light" title="Six steps, again" width="60%">State hypotheses, choose α, find the null world, compute the statistic, compare, decide. Only the arithmetic changed.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Goodness-of-fit: which hand ends up on top?

:: left ::

Clap your hands. Which hand is on top: left, right, or neither?

**Real data:** 236 statistics students at the University of Adelaide were asked exactly this (Venables & Ripley; R's `MASS::survey`).

| | Left | Neither | Right |
|---|:---:|:---:|:---:|
| Observed | 39 | 50 | 147 |
| Expected if $H_0$ (all equal) | 78.7 | 78.7 | 78.7 |

<Admonition title="Question" color="teal-light" width="100%">

$H_0$: the three answers are equally common. Before running it: does the table look like $H_0$?

</Admonition>

:: right ::

<p v-click>

```r
chisq.test(table(survey$Clap))
#>  Chi-squared test for given probabilities
#> X-squared = 89.805, df = 2, p-value < 2.2e-16
```

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Reject $H_0$: the counts are nowhere near equal, $\chi^2(2) = 89.8$, $p < .001$. Most people put the right hand on top. df = 3 categories − 1.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Try it in this room" width="100%">Count the room, then compare to Adelaide. (45 people, expected 15 each.)</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Independence: does your writing hand predict it?

:: left ::

Same students, two categorical variables: **writing hand** and **hand on top**.

| | Left on top | Neither | Right on top |
|---|:---:|:---:|:---:|
| Left-handed (18) | 9 | 5 | 4 |
| Right-handed (217) | 29 | 45 | 143 |

$H_0$: which hand ends up on top is **unrelated** to which hand you write with. If so, the two rows should have the same *proportions*.

:: right ::

<p v-click>

```r
chisq.test(table(survey$W.Hnd, survey$Clap))
#>  Pearson's Chi-squared test
#> X-squared = 19.252, df = 2, p-value = 6.598e-05
#> Warning: Chi-squared approximation may be incorrect
```

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Reject $H_0$: $\chi^2(2) = 19.3$, $p < .001$. Half of the left-handers put the left hand on top; one in eight right-handers do. df = (rows − 1) × (columns − 1).

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="About that warning" width="100%">Only 18 left-handers, so two <i>expected</i> counts are below 5, and the chi-square null world is a rough approximation. The fix is Fisher's exact test, <code>fisher.test()</code>: p = .0001, same conclusion. An assumption check, like Lecture 12's.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Limitations of Non-Parametric Tests

:: left ::

### Disadvantages
- Lower power
- Cannot model complex designs easily
- Harder to interpret effect sizes


::right::

### Advantages
- Fewer assumptions
- More robust to outliers
- Useful for ordinal or categorical variables
- Still allow valid inference in messy real-world data

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: which test?

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher asks 200 BU students which dining hall they prefer (Marciano, Warren, West) and wants to know whether the three are equally popular. Which test?

- **A)** Chi-square goodness-of-fit.
- **B)** One-way ANOVA.
- **C)** Independent-samples *t* test.
- **D)** Chi-square test of independence.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** One categorical variable, counts in three categories, compared with a prediction (equal thirds). No means anywhere, so no *t* or *F*.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

She then asks whether dining-hall preference is related to whether the student lives on East or West Campus. Which test?

- **A)** Repeated-measures ANOVA.
- **B)** Pearson correlation.
- **C)** Chi-square goodness-of-fit.
- **D)** Chi-square test of independence.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Two categorical variables (preference, campus); the question is whether they are associated. Correlation needs two numeric variables.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from today

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**p-hacking** — trying analyses until one gives p < .05 and reporting only that one. Breaks the 5% promise.

</div>
<div>

**Researcher degrees of freedom** — the choices made during a study (outcomes, stopping, outliers, covariates) that can each nudge the result.

</div>
<div>

**HARKing and optional stopping** — presenting a post-hoc hypothesis as the original one; collecting data until p < .05.

</div>
<div>

**Replication crisis** — most published psychology findings tested in 2015 did not replicate (36 of 100). Preregistration, registered reports and open data are the response.

</div>
<div>

**Non-parametric test** — a test that does not assume a normal distribution; uses ranks or counts. Fewer assumptions, less power.

</div>
<div>

**Chi-square tests** — observed vs. expected *counts*. Goodness-of-fit: one categorical variable. Test of independence: are two categorical variables related?

</div>
</div>

<p v-click><StickyNote color="green-light" title="Next" width="70%">Tuesday: Exam 4 review (Lectures 15–19). Bring your laptop for course evaluations.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Statistical Tests: Recap

:: left ::
- We have covered a variety of parametric inferential tests.
    - *z*-tests, *t*-tests, ANOVA, correlation, regression
- We have also discussed non-parametric alternatives.

<p v-click>

- And you have now seen how the toolkit gets misused, and what honest use looks like: decide first, report everything, share the data.

</p>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="blissful" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>You now have a full statistical toolkit — from histograms all the way to regression. That's the whole course!</SpeechBubble>
</div>


:: right ::

<p v-click>

<img src="/images/lecture18/power_responsibility.jpg" class="w-3/4  rounded-lg mx-auto"/>


</p>

---
layout: cover
color: indigo-light
---

# That's all for today!
See you Tuesday for Exam 4 Review!
