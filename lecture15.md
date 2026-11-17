---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 15
exportFilename: ps211_fall2026_lecture15
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 15: One-Way ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::

<div class="text-[15px]">

- ==Exam 3== grades are posted. We'll go over the difficult questions in a moment.
- ==Data Write-Up #2== (ANOVA-based) starts **tomorrow in Discussion 11**: new datasets, and new groups if you'd like. **Message Rola** to say whether you're sticking with your Write-Up #1 group or joining a new one. Due **Tuesday, December 8** at 11:59 p.m.
- ==Exam 4== (the last exam) is **Thursday, December 10**, in class. **There will be no make-ups.**
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)

</div>

<div class="grid grid-cols-2 gap-x-8 text-sm mt-2">
<div>

**Coming up**

- Wed. 11/18: Discussion 11 (R practice for ANOVA; Write-Up #2 begins)
- Thurs. 11/19: Lecture 16 (repeated-measures & two-way ANOVA)
- Tues. 11/24: Lecture 17 (correlation)
- **No discussion Wed. 11/25, no class Thurs. 11/26 (Thanksgiving)**

</div>
<div>

&nbsp;

- Tues. 12/1: Lecture 18 (regression)
- Wed. 12/2: Discussion 12 (Write-Up #2 work session)
- Thurs. 12/3: Lecture 19 (research ethics & chi-square)
- Tues. 12/8: Exam 4 Review; **Write-Up #2 due**
- Wed. 12/9: Discussion 13 (wrap-up & Exam 4 practice)
- Thurs. 12/10: **Exam 4** (Lectures 15–19)

</div>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where we are: the home stretch

:: content ::

Three exams down. Every test so far compared **one or two means**. The last five lectures widen what "the data" can look like, but the logic does not change:

<div class="grid grid-cols-5 gap-2 mt-4 text-sm">
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-2"><b>Lecture 15 (today)</b><br/>One-way ANOVA: three or more separate groups, one test</div>
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Lecture 16</b><br/>Repeated-measures ANOVA (same people in every condition) & two-way ANOVA (two IVs at once)</div>
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Lecture 17</b><br/>Correlation: when <i>both</i> variables are numeric</div>
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Lecture 18</b><br/>Regression: using one variable to <i>predict</i> another</div>
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Lecture 19</b><br/>Research ethics (p-hacking, the replication crisis) & chi-square for categorical outcomes</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="38rem">Same question every time: is what we saw bigger than what chance alone would produce? Only the shape of the data, and so the test statistic, changes.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The rest of the course on one slide

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>IV (or predictor)</th><th>DV (or outcome)</th><th>Test</th><th>Lecture</th><th>Our real example</th></tr></thead>
<tbody>
<tr class="text-gray-400"><td>Categorical, 2 groups or conditions</td><td>Numeric</td><td><i>t</i> tests</td><td>12–14</td><td>Done ✓</td></tr>
<tr><td><b>Categorical, 3+ separate groups</b></td><td>Numeric</td><td><b>One-way ANOVA</b></td><td><b>15</b></td><td>Three ways to teach reading</td></tr>
<tr><td>Categorical, 3+ conditions, same people</td><td>Numeric</td><td>Repeated-measures ANOVA</td><td>16</td><td>Caffeine, chocolate & finger tapping</td></tr>
<tr><td>Two categorical IVs</td><td>Numeric</td><td>Two-way ANOVA</td><td>16</td><td>Who conforms, and to whom?</td></tr>
<tr><td>Numeric</td><td>Numeric</td><td>Correlation & regression</td><td>17–18</td><td>Sleep, drinking & GPA; predicting college GPA</td></tr>
<tr><td>Categorical</td><td>Categorical</td><td>Chi-square</td><td>19</td><td>Which hand is on top when you clap?</td></tr>
</tbody>
</table>

<div class="flex items-start gap-6 mt-3">
<p v-click><StickyNote color="amber-light" title="Data Write-Up #2" width="100%">An ANOVA on a real psychology dataset. Starts tomorrow (Discussion 11), work session Dec. 2 (Discussion 12), due Tues. Dec. 8.</StickyNote></p>
<p v-click><StickyNote color="amber-light" title="Exam 4" width="100%">Thurs. Dec. 10, Lectures 15–19. Same format as before: recognize which situation you are in, and read the result correctly.</StickyNote></p>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Last time: key terms

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Independent-samples *t* test** — compares the means of two separate groups (between-subjects). $t = (M_1 - M_2)/SE_{difference}$, df = n₁ + n₂ − 2.

</div>
<div>

**Pooled variance** — the df-weighted average of the two groups' variances: one estimate of how much individual scores vary.

</div>
<div>

**Standard error of the difference** — noise from both groups' means, added. Shrinks as either n grows.

</div>
<div>

**Equal-variance assumption** — the groups should have similar spreads. `var.equal = TRUE` pools them.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Exam 3 is behind you. Today's question: what if there are three groups? Pooled variance comes back, under a new name.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Warm-up: check your understanding

:: left ::

Fourth-graders taught reading with a new method (DRTA, n = 22) vs. the traditional method (Basal, n = 22), on a reading comprehension test:

```text
t = 2.8679, df = 42, p-value = 0.006436
95 percent confidence interval:
 1.683708 9.679928
mean of x mean of y 
 46.72727  41.04545 
```

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which statement is correct?

- **A)** df should be 43: there are 44 children.
- **B)** DRTA children scored significantly higher, by about 5.7 points; the true difference is plausibly 1.7 to 9.7.
- **C)** 95% of DRTA children scored 1.7 to 9.7 points higher.
- **D)** Not significant, because the CI is wide.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Two groups: 22 + 22 − 2 = 42 (A). \(C) confuses a CI for the *mean* difference with individual children. (D): the CI excludes 0, so it agrees with p < .05.

</Admonition>

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

DRTA *M* = 46.7, Basal *M* = 41.0, pooled *SD* ≈ 6.6, so Cohen's *d* ≈ 0.87. Which description fits?

- **A)** A small effect: the difference is under 6 points.
- **B)** The DRTA children scored 87% higher.
- **C)** A large effect: the average DRTA child scored almost 0.9 SDs above the average Basal child.
- **D)** It can't be judged without the *p* value.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** *d* = 5.7 / 6.6 is the difference in SD units; by Cohen's guide, 0.8 or more is large. (A) ignores the spread. (B) misreads *d* as a percentage. (D): effect size and *p* answer different questions (Lecture 11).

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

The study had a third group...
# One-Way ANOVA

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Our example: three ways to teach reading

:: left ::

<div class="text-[15px] leading-snug">

**66 fourth-graders**, **randomly assigned** to one of three ways of being taught reading (22 per group):

- **Basal:** traditional textbook method
- **DRTA:** predict, then read to check
- **Strategies:** think aloud while reading

Then everyone took the same standardized **reading comprehension test**.

</div>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What are the IV (and its levels) and the DV? Can we make a causal claim?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

IV: teaching method (3 levels). DV: comprehension score (numeric). Random assignment → yes, a causal claim is justified.

</Admonition></p>

:: right ::

<img src="/images/lecture15/reading_dots.png" alt="Reading comprehension scores for the three teaching methods, with group means and the grand mean" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Baumann, Seifert-Kessell, & Jones (1992), <i>Journal of Reading Behavior</i>; via Moore & McCabe (1993); R package <code>carData</code> (<code>Baumann</code>).</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why not just run three *t* tests?

:: content ::

Three groups means three pairs: Basal vs. DRTA, Basal vs. Strategies, DRTA vs. Strategies.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Each *t* test uses α = .05. Is there a problem with running all three?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Yes. Each test is another 5% chance of a **Type I error** (rejecting H₀ when it is true). Run several, and the chance that *at least one* is a false positive grows. This is **alpha inflation**.

</Admonition></p>

<div v-click class="mt-3">

If H₀ is true everywhere, the chance that a single test correctly fails to reject is .95. For several tests, multiply:

<table class="compact-table text-base">
<thead><tr><th>Groups</th><th>Pairs (<i>t</i> tests)</th><th>P(no false positives)</th><th>P(at least one false positive)</th></tr></thead>
<tbody>
<tr><td>2</td><td>1</td><td>.95</td><td>.05</td></tr>
<tr><td>3</td><td>3</td><td>.95³ = .86</td><td><b>.14</b></td></tr>
<tr><td>4</td><td>6</td><td>.95⁶ = .74</td><td><b>.26</b></td></tr>
<tr><td>5</td><td>10</td><td>.95¹⁰ = .60</td><td><b>.40</b></td></tr>
</tbody>
</table>

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: alpha inflation

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

A researcher compares 4 study techniques and runs all 6 pairwise *t* tests at α = .05. In truth, technique makes no difference. What is the chance that **at least one** test comes out significant?

- **A)** 5%, because each test uses α = .05
- **B)** 30%: 6 × 5%
- **C)** About 26%
- **D)** 0%, because there is no real effect

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** 1 − .95⁶ ≈ .26. (A) is the rate *per test*, not for the whole set. (B) is close, but adding overcounts (with 20 tests, adding would give 100%). (D): with no real effect, every significant result is a false positive, and each test still has a 5% chance of one.

</Admonition>

<p v-click><StickyNote color="amber-light" title="What we want" width="100%">One test of "are these means all the same?" that keeps the false-positive rate at 5% no matter how many groups there are. That is ANOVA.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One test for all the groups: the *F* statistic

:: content ::

**ANOVA** (*analysis of variance*) compares the means of 3+ groups in a single test. Its test statistic, ***F***, is another signal-to-noise ratio:

<div class="grid grid-cols-3 gap-4 mt-4 text-center">
<div v-click class="border-2 border-gray-300 rounded-lg p-3">

$$z = \frac{M - \mu}{\sigma_M}$$

one mean vs. a known population

</div>
<div v-click class="border-2 border-gray-300 rounded-lg p-3">

$$t = \frac{M_1 - M_2}{SE_{difference}}$$

two means: a *difference* is the signal

</div>
<div v-click class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3">

$$F = \frac{\begin{matrix}\text{between-groups}\\ \text{variance}\end{matrix}}{\begin{matrix}\text{within-groups}\\ \text{variance}\end{matrix}}$$

3+ means: how *spread out* the means are is the signal

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-5">
<IceCream :size="70" mood="shocked" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">With three means there is no single difference to put on top. So ANOVA asks how much the group means vary around the grand mean, compared with how much individual scores vary inside the groups.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Two sources of variability

:: content ::

<img src="/images/lecture15/between_within.png" alt="Left: group means compared with the grand mean. Right: each score compared with its own group mean" class="w-full mx-auto"/>

<div class="grid grid-cols-2 gap-8 text-[15px] leading-snug">
<div v-click>

**Between-groups variance (signal).** How far each *group mean* sits from the **grand mean** (the mean of all 66 scores). Reflects the IV, plus a little chance.

</div>
<div v-click>

**Within-groups variance (noise).** How far each *score* sits from its *own group's* mean. Children taught the same way still differ: chance, individual differences, measurement error.

</div>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: what makes *F* bigger?

:: left ::

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

Imagine re-running the reading study. Which change would make *F* **larger**, if the group means stayed exactly where they are?

- **A)** Children within each group score more similarly to one another (less spread inside each group).
- **B)** Children within each group differ more from one another.
- **C)** Adding 10 points to every child's score.
- **D)** Nothing: *F* only depends on the group means.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Less within-group spread shrinks the denominator (the noise), so the same gaps between means stand out more. (B) does the opposite. \(C) moves every mean and every score together, so no spread changes and *F* stays the same. (D) ignores the denominator.

</Admonition>

<p v-click><StickyNote color="amber-light" title="Sound familiar?" width="100%">Same as the <i>t</i> test: a bigger difference or a smaller SD makes <i>t</i> larger. ANOVA just measures "difference" as the spread of the means.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Setting up the hypotheses

:: left ::

**Null hypothesis (H₀):** all the population means are equal.

$$\mu_{Basal} = \mu_{DRTA} = \mu_{Strategies}$$

**Research hypothesis (H₁):** **at least one** population mean differs from the others.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Is H₁ "all three means are different"?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

No. H₁ is simply "not all equal." One method could beat the other two, which tie. A significant *F* does not say *which* means differ (that comes later today).

</Admonition></p>

:: right ::

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

There is no "direction" for H₁. *F* is a ratio of two variances, so it can never be negative, and every *F* test is **one-tailed**: only a large *F* counts against H₀.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="happy" color="#FDA7DC" /></div>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# The null world for *F*

:: left ::

<img src="/images/lecture15/null_F.png" alt="Histogram of 20,000 F statistics from fake studies with no real effect; the top 5 percent is shaded beyond 3.14 and the observed F of 4.48 is marked" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">20,000 fake reading studies: 3 groups of 22, all drawn from one population (H₀ true).</div>

:: right ::

<div class="text-[15px] leading-snug">

The same recipe as the *t* distribution in Lecture 14: simulate studies where H₀ is true, compute *F* for each, pile them up.

- *F* is never negative. When H₀ is true it is usually **near 1** (signal ≈ noise).
- The shape depends on **two dfs**: between groups (k − 1 = 2) and within groups (N − k = 63).
- The cutoff for the top 5% is **3.14**. Our *F* of 4.48 is beyond it.

</div>

<p v-click><StickyNote color="amber-light" title="F tables" width="100%">Textbooks print tables of <i>F</i> cutoffs for each pair of dfs. R gives you the exact p value, so we will not use them.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where the two variances come from

:: content ::

ANOVA splits the **total variability** into the two parts from the picture. Each part is a **sum of squares (SS)**, as in Lecture 5: deviations, squared, added up.

$$SS_\text{Total} = SS_\text{Between} + SS_\text{Within}$$

<div class="grid grid-cols-2 gap-8 mt-2 text-[15px] leading-snug">
<div v-click>

$$SS_\text{Between} = \sum n_i (M_i - M_G)^2$$

Each group mean minus the grand mean $M_G$, squared, weighted by the group's size, summed over groups.

</div>
<div v-click>

$$SS_\text{Within} = \sum \sum (X - M_i)^2$$

Each score minus its own group mean, squared, summed within each group, then across groups.

</div>
</div>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Why does $SS_\text{Within}$ have **two** summation signs?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The inner Σ adds up squared deviations for every child *within one group*; the outer Σ repeats that for each group and adds the groups' totals. It is the pooled-variance idea from Lecture 14, extended to any number of groups.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# From sums of squares to *F*

:: content ::

A sum of squares grows just because there are more things being added. Dividing by its **degrees of freedom** turns it into an average, a **mean square (MS)**: a variance.

<div class="grid grid-cols-2 gap-8 mt-2">
<div v-click>

$$MS_\text{Between} = \frac{SS_\text{Between}}{df_\text{Between}}, \quad df_\text{Between} = k - 1$$

k = number of groups

</div>
<div v-click>

$$MS_\text{Within} = \frac{SS_\text{Within}}{df_\text{Within}}, \quad df_\text{Within} = N - k$$

N = total number of participants

</div>
</div>

<div v-click class="mt-4">

$$F = \frac{MS_\text{Between}}{MS_\text{Within}}$$

</div>

<p v-click><StickyNote color="amber-light" title="Why N − k?" width="70%">Each group's spread is measured around its own mean, and estimating each of those k means uses up one df: the same reason the independent-samples <i>t</i> test has n₁ + n₂ − 2. <b>MS<sub>Within</sub> is the pooled variance</b>, now from k groups.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The source table, one column at a time

:: content ::

ANOVA results are laid out in a **source table**. For the reading study (k = 3 groups, N = 66):

<table class="compact-table text-base">
<thead><tr><th>Source</th><th>SS</th><th>df</th><th>MS</th><th><i>F</i></th></tr></thead>
<tbody>
<tr><td>Between groups (method)</td><td>357.3</td><td><span v-click="1">k − 1 = 2</span></td><td><span v-click="2">357.3 / 2 = 178.6</span></td><td><span v-click="3"><b>178.6 / 39.9 = 4.48</b></span></td></tr>
<tr><td>Within groups (error)</td><td>2,511.7</td><td><span v-click="1">N − k = 63</span></td><td><span v-click="2">2,511.7 / 63 = 39.9</span></td><td></td></tr>
<tr><td><b>Total</b></td><td>2,869.0</td><td><span v-click="1">N − 1 = 65</span></td><td></td><td></td></tr>
</tbody>
</table>

<p v-click="4">

The cutoff for *F*(2, 63) at α = .05 is 3.14. 4.48 > 3.14, so **reject H₀**: the three teaching methods did not produce the same mean comprehension. (Exact *p* = .015.)

</p>

<p v-click="5"><StickyNote color="amber-light" title="What you need to know" width="70%">What each column means and how they connect (SS → MS → <i>F</i>). You will not compute sums of squares by hand: R does that, and the exam gives you its output.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six steps for a one-way ANOVA

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>Independent-samples <i>t</i> test</th><th>One-way between-groups ANOVA</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Two separate groups</td><td><b>Three or more separate groups</b> (one categorical IV). DV numeric, roughly normal in each group, similar variances, independent observations</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>H₀: μ₁ = μ₂ &nbsp; H₁: μ₁ ≠ μ₂</td><td>H₀: μ₁ = μ₂ = μ₃ = … &nbsp; H₁: <b>at least one</b> μ differs</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td><i>t</i>, df = n₁ + n₂ − 2</td><td><b><i>F</i></b>, df<sub>Between</sub> = k − 1 and df<sub>Within</sub> = N − k</td></tr>
<tr><td><b>4.</b> Critical values</td><td>α = .05, two-tailed → ±<i>t</i><sub>crit</sub></td><td>α = .05, <b>always one cutoff, in the upper tail</b></td></tr>
<tr><td><b>5.</b> Test statistic</td><td><i>t</i> = (M₁ − M₂) / SE<sub>difference</sub></td><td><i>F</i> = MS<sub>Between</sub> / MS<sub>Within</sub></td></tr>
<tr><td><b>6.</b> Decision</td><td colspan="2">Reject or fail to reject H₀, and say it in plain English. <b>New for ANOVA:</b> if you reject, follow up to find out <i>which</i> means differ.</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Check" width="70%">With exactly two groups, a one-way ANOVA and an independent-samples <i>t</i> test give the same p value (<i>F</i> = <i>t</i>²). ANOVA is the <i>t</i> test, generalized.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# How big is the effect? η² (eta squared)

:: left ::

A significant *F* says the means are not all equal. **Effect size** says how much it matters:

$$\eta^2 = \frac{SS_\text{Between}}{SS_\text{Total}}$$

The **proportion of all the variability** in the DV that is explained by group membership. (In a one-way ANOVA, η² is the same as R², which comes back in Lecture 18.)

<p v-click>

Reading study: η² = 357.3 / 2,869.0 = **.12**. Teaching method accounts for 12% of the differences among children's scores; the other 88% is everything else about the children.

</p>

:: right ::

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

Rough guide (Cohen, 1988): small ≈ .01, medium ≈ .06, large ≈ .14. Context matters: 12% from a few weeks of teaching is a lot.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="excited" color="#FDA7DC" /></div>
</div>

<p v-click><StickyNote color="amber-light" title="Same as d" width="100%">Like Cohen's d, η² does not depend on sample size. With a huge sample, a tiny η² can still be significant, so report both.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# The same test in R: `aov()`

:: left ::

```r
reading_model <- aov(comprehension ~ method,
                     data = reading)
summary(reading_model)
```

```text
            Df Sum Sq Mean Sq F value Pr(>F)  
method       2  357.3  178.65   4.481 0.0152 *
Residuals   63 2511.7   39.87                 
```

The formula `comprehension ~ method` reads "comprehension **as explained by** method": DV on the left, IV on the right. The IV column holds each child's group label.

<Admonition title="Warning: make the IV a factor" color="red-light" width="100%">

If the groups are stored as numbers (1, 2, 3), R treats the IV as a number and fits a single slope: the `method` row shows df = 1 instead of k − 1. Fix it first with `factor()`, and always check that df<sub>Between</sub> = k − 1.

</Admonition>

:: right ::

<div class="text-[15px] leading-snug">

The output is the source table:

- **`method`** row: between groups
- **`Residuals`** row: within groups ("residual" = what is left over after the groups are taken into account)
- **`Pr(>F)`**: the p value

</div>

<p v-click><StickyNote color="green-light" title="Tomorrow in Discussion 11" width="100%">You'll run <code>aov()</code> and <code>summary()</code> yourselves, plot group means with error bars, and start Data Write-Up #2, which is built around this output.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: reading the output

:: left ::

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

In the output above, why is the `Residuals` df **63**?

- **A)** 66 children minus 3: one df lost for each group's mean.
- **B)** 66 children minus 3 outliers.
- **C)** Only 63 children finished the study.
- **D)** It is df<sub>Between</sub> × 31.5.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** df<sub>Within</sub> = N − k = 66 − 3. Nothing was dropped (B, C). (D) is numerology: df<sub>Within</sub> does not depend on df<sub>Between</sub>.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

Which conclusion does `F = 4.481, p = .0152` support?

- **A)** All three methods produced different mean scores.
- **B)** DRTA is the best method.
- **C)** The methods did not differ; *p* is above .01.
- **D)** At least one method's mean differs from another's; we don't yet know which.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** That is all H₁ says. (A) and (B) need follow-up tests. \(C) uses the wrong alpha: we set .05 in advance.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

A significant *F*: now what?
# Which groups differ?

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Planned vs. post-hoc comparisons

:: left ::

A significant ANOVA says **at least one** mean differs. To find out which, we compare pairs of groups, with care.

**Planned (a priori) comparisons**
- Decided *before* seeing the data, from the hypothesis
- A few specific tests → little or no correction

**Post-hoc comparisons**
- Done *after* a significant *F*, to explore where the differences are
- Often every pair → **must correct** to keep α = .05 overall

:: right ::

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

A post-hoc test is a *t* test with a built-in correction: each comparison has to clear a higher bar, so the whole *set* keeps a 5% false-positive rate.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="blissful" color="#FDA7DC" /></div>
</div>

<p v-click><StickyNote color="amber-light" title="Only after a significant F" width="100%">If the ANOVA is not significant, stop. Running pairwise tests anyway is hunting for a result.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Common post-hoc corrections

:: content ::

<table class="compact-table text-base">
<thead><tr><th>Test</th><th>Key idea</th><th>How strict?</th><th>Typical use</th></tr></thead>
<tbody>
<tr><td><b>Bonferroni</b></td><td>Divide α by the number of comparisons</td><td>Strict when there are many tests</td><td>A small number of comparisons</td></tr>
<tr><td><b>Tukey HSD</b></td><td>Compares every pair at once with one adjusted cutoff</td><td>Middle ground</td><td>All pairwise comparisons; the most common choice</td></tr>
<tr><td><b>Scheffé</b></td><td>Protects every possible comparison, including combinations of groups</td><td>Most conservative</td><td>Exploratory analyses</td></tr>
</tbody>
</table>

<p v-click>

**Bonferroni with our three methods:** 3 pairwise comparisons, so each one must reach *p* < .05 / 3 = **.0167** to count as significant.

</p>

<p v-click>

Whichever you use, **say which** in your write-up. All of them trade a little power for protection against false positives.

</p>

<p v-click><StickyNote color="amber-light" title="How much do you need to know?" width="90%">Exactly how Tukey and Scheffé adjust <i>p</i> is beyond this course. The idea: each extra comparison is another chance at a false positive, so each one must clear a higher bar (R shows this as a larger <code>p adj</code>). Together, the whole set keeps a 5% false-positive rate.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Tukey HSD on the reading data

:: left ::

```r
TukeyHSD(reading_model)
```

```text
                 diff       lwr       upr  p adj
DRTA-Basal   5.681818  1.112137 10.251499 0.0111
Strat-Basal  3.227273 -1.342408  7.796953 0.2150
Strat-DRTA  -2.454545 -7.024226  2.115135 0.4064
```

- **`diff`**: difference between the two group means
- **`lwr`, `upr`**: a 95% CI for that difference, widened for the three comparisons
- **`p adj`**: p value adjusted for the three comparisons

:: right ::

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

What do the Tukey tests show?

- **A)** All three methods differ.
- **B)** DRTA beat Basal; neither of the other two pairs differs significantly.
- **C)** Strategies beat Basal, because its diff is positive.
- **D)** DRTA beat both other methods.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Only DRTA−Basal has *p* adj < .05, and its CI excludes 0. The other two CIs include 0. \(C) and (D) read the direction of a difference but ignore whether it is significant.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# A real experiment: can a song make you feel older?

:: left ::

**The study.** 44 University of Pennsylvania undergraduates were randomly assigned to listen to one of three songs on headphones:

- ***Kalimba***: an instrumental track that came with Windows 7 (the control)
- ***Hot Potato***: a children's song by The Wiggles
- ***When I'm Sixty-Four***: the Beatles, singing about getting old

Then, in a "separate" survey, they answered: **How old do you feel?** (1 = very young, 5 = very old)

<div class="text-xs text-gray-500 mt-2">Simmons, Nelson & Simonsohn (2011), <i>Psychological Science</i>, Study 1. Data: Simmons et al. (2014), <i>Journal of Open Psychology Data</i>; R package <code>ds4psy</code> (<code>falsePosPsy_all</code>).</div>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

What are the IV (and its levels) and the DV? Which test fits, and could it support a causal claim?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

IV: song (3 levels). DV: how old you feel (a 1–5 rating, treated as numeric). Three separate groups of people → **one-way between-groups ANOVA**. Random assignment → a significant *F* would support a causal claim.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Can a song make you feel older? The results

:: left ::

<img src="/images/lecture15/songs_feelold.png" alt="How old each participant felt after each of the three songs, with group means and standard errors" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Dots: individual participants (jittered). Black: group mean ± 1 SE. n = 13, 17, 14.</div>

:: right ::

```r
song_model <- aov(feel_old ~ song, data = songs)
summary(song_model)
```

```text
          Df Sum Sq Mean Sq F value Pr(>F)
song       2  1.773  0.8867    2.48 0.0962
Residuals 41 14.658  0.3575
```

<Admonition title="Question" color="teal-light" width="100%">

What can we conclude? Should we run Tukey tests?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

*F*(2, 41) = 2.48, *p* = .096, η² = .11. The songs did not differ significantly, so we stop: post-hoc tests come only after a significant *F*. With about 14 people per group, power is low, so this is not evidence that songs have *no* effect.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Keep this study in mind" width="100%">The researchers published a significant result from these same data. Lecture 19 shows how.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Preview: the same math, outside ANOVA

:: left ::

- Every extra test is another ticket in the 5% lottery. With 10 tests and nothing real, the chance that *something* comes out $p < .05$ is **40%**.
- Post-hoc corrections pay for the extra tickets.

<p v-click>

- Researchers who run many tests, skip the correction, and report only the winner are ==**p-hacking**==: the same alpha inflation, hidden inside a single study.

</p>

<p v-click><StickyNote color="amber-light" title="Lecture 19" width="100%">The last lecture is about this: how researchers' everyday choices inflate false positives, the replication crisis that followed, and how the field is fixing it.</StickyNote></p>

:: right ::

<img src="/images/lecture19/many_outcomes.png" alt="Chance of at least one p below .05 as a function of the number of tests run" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Two groups of n = 20, no real effect anywhere; 20,000 fake studies per point.</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a one-way ANOVA in APA style

:: content ::

Include: the type of ANOVA, each group's *M* and *SD*, ***F*(df<sub>Between</sub>, df<sub>Within</sub>)**, *p*, **η²**, and which post-hoc test you used and what it showed.

<div v-click class="border-l-4 border-indigo-400 pl-4 mt-3 text-[17px] leading-snug">

A one-way between-groups ANOVA compared reading comprehension across three teaching methods. Comprehension differed by method, *F*(2, 63) = 4.48, *p* = .015, η² = .12. Tukey HSD comparisons showed that children taught with DRTA (*M* = 46.7, *SD* = 7.4) scored higher than children taught with the basal method (*M* = 41.0, *SD* = 5.6), *p* = .011. Children taught think-aloud strategies (*M* = 44.3, *SD* = 5.8) did not differ significantly from either group (*p*s > .21).

</div>

<p v-click><StickyNote color="amber-light" title="Same rules as Lecture 13" width="80%">Italic statistical symbols, no leading zero on <i>p</i> or η², direction in words, and two dfs for <i>F</i>: between first, then within.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Assumptions of one-way ANOVA

:: content ::

The same assumptions as the independent-samples *t* test, for every group:

1. **Numeric DV** (interval or ratio), so it has a mean
2. **Independent observations**: each person is in one group and counted once (random selection is the ideal)
3. **Normality**: each group's population is roughly normal. With about 30+ per group, the CLT makes this matter much less.
4. **Homogeneity of variance**: the groups have similar spreads
   - ==Homoscedastic==: same variance. ==Heteroscedastic==: different variances.
   - Check it by comparing the groups' SDs. If one is much larger, say so and interpret the result with caution.


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice: owls, larks, and missed classes

:: left ::

Our sleep data from Discussions 5–6: **253 college students** who called themselves larks (morning people), owls (night people), or neither. Do they miss different numbers of classes?

<table class="compact-table text-base">
<thead><tr><th></th><th>n</th><th><i>M</i></th><th><i>SD</i></th></tr></thead>
<tbody>
<tr><td>Lark</td><td>41</td><td>1.56</td><td>2.00</td></tr>
<tr><td>Neither</td><td>163</td><td>1.77</td><td>2.36</td></tr>
<tr><td>Owl</td><td>49</td><td>4.20</td><td>5.29</td></tr>
</tbody>
</table>

```text
             Df Sum Sq Mean Sq F value   Pr(>F)    
chronotype    2  243.2  121.62   12.65 5.82e-06 ***
Residuals   250 2402.7    9.61                     
```

<div class="text-xs text-gray-500 mt-1">Data: Onyper, Thacher, Gilbert, & Gradess (2012), <i>Chronobiology International</i>; Lock5Data (<code>SleepStudy</code>).</div>

:: right ::

<img src="/images/lecture15/chronotype_missed.png" alt="Classes missed by chronotype, individual students and group means with standard-error bars" class="w-11/12 mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What are df<sub>Between</sub> and df<sub>Within</sub>, and what is η²?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

3 − 1 = 2 and 253 − 3 = 250. η² = 243.2 / (243.2 + 2,402.7) = .09.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Owls: what can we conclude?

:: left ::

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

Tukey tests show owls missed more classes than both larks and "neither" (*p*s < .001), who did not differ. Which conclusion is justified?

- **A)** Being a night owl causes students to miss class.
- **B)** Owls should be assigned afternoon classes.
- **C)** Owls missed significantly more classes than the other students; we can't say why.
- **D)** No conclusion: one-way ANOVA needs equal group sizes.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Chronotype was not assigned, so this is observational: owls might differ in many ways (later bedtimes, heavier course loads). (A) and (B) both assume a cause. (D): unequal ns are fine.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 9" color="teal-light" width="100%">

For classes missed, η² = .09. Which statement is correct?

- **A)** 9% of owls missed class.
- **B)** Chronotype accounts for about 9% of the variability in classes missed; the other 91% comes from everything else about the students.
- **C)** The effect is too small to be real.
- **D)** Owls missed 9% more classes than larks.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** η² is a proportion of variability, not of people (A) or of classes (D). \(C): by Cohen's guide .09 is a medium effect, and the significant *F* says it is unlikely to be chance.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# A non-significant ANOVA: GPA by chronotype

:: left ::

Same students. Do larks, owls, and "neither" differ in **GPA**?

<table class="compact-table text-base">
<thead><tr><th></th><th>Lark</th><th>Neither</th><th>Owl</th></tr></thead>
<tbody>
<tr><td><i>M</i> (<i>SD</i>)</td><td>3.33 (0.40)</td><td>3.24 (0.39)</td><td>3.20 (0.44)</td></tr>
</tbody>
</table>

```text
             Df Sum Sq Mean Sq F value Pr(>F)
chronotype    2   0.43   0.215   1.319  0.269
Residuals   250  40.76   0.163               
```

:: right ::

<Admonition title="Multiple choice 10" color="teal-light" width="100%">

What should the researchers do next?

- **A)** Report that they found no significant GPA difference among chronotypes (η² = .01), and stop: no post-hoc tests.
- **B)** Run Tukey tests to find the hidden difference between larks and owls.
- **C)** Conclude that chronotype is unrelated to GPA in every population.
- **D)** Switch to α = .30 so the result is significant.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Post-hoc tests only follow a significant *F* (B). Failing to reject is not proof of no difference \(C), though with 253 students and η² = .01, any difference is likely small. (D) changes the rule after seeing the data.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What changed from test to test?

:: content ::

<table class="compact-table text-sm">
<thead><tr><th></th><th>Single-sample <i>t</i></th><th>Paired-samples <i>t</i></th><th>Independent-samples <i>t</i></th><th>One-way ANOVA</th></tr></thead>
<tbody>
<tr><td><b>Step 1:</b> which test fits?</td><td>One mean, σ unknown</td><td>Two scores per participant</td><td>Two separate groups</td><td><b>Three or more separate groups</b></td></tr>
<tr><td><b>Step 3:</b> noise</td><td>s/√n</td><td>s<sub>D</sub>/√n</td><td>from both SDs and both ns</td><td><b>MS<sub>Within</sub></b>: the pooled variance of all groups</td></tr>
<tr><td><b>Step 3:</b> shape</td><td><i>t</i>, df = n − 1</td><td><i>t</i>, df = n − 1</td><td><i>t</i>, df = n₁ + n₂ − 2</td><td><b><i>F</i>, df = (k − 1, N − k)</b></td></tr>
<tr><td><b>Step 4:</b> tails</td><td>one or two</td><td>one or two</td><td>one or two</td><td><b>always one (upper)</b></td></tr>
<tr><td><b>Step 5:</b> signal ÷ noise</td><td>(M − μ)/s<sub>M</sub></td><td>M<sub>D</sub>/s<sub>M</sub></td><td>(M₁ − M₂)/SE<sub>diff</sub></td><td><b>MS<sub>Between</sub>/MS<sub>Within</sub></b></td></tr>
<tr><td><b>Effect size</b></td><td><i>d</i></td><td><i>d</i></td><td><i>d</i></td><td><b>η²</b></td></tr>
<tr><td><b>In R</b></td><td><code>t.test(x, mu = )</code></td><td><code>t.test(x, y, paired = TRUE)</code></td><td><code>t.test(x, y, var.equal = TRUE)</code></td><td><b><code>summary(aov(dv ~ group))</code></b></td></tr>
</tbody>
</table>

<p v-click>

<div class="flex items-center gap-4 mt-3">
<IceCream :size="70" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">Thursday: what if the same people are in every condition (like the paired t test), and what if there are two IVs at once?</SpeechBubble>
</div>

</p>

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

**Alpha inflation** — running many tests raises the chance that at least one is a false positive (3 tests: 14%; 6 tests: 26%).

</div>
<div>

**One-way between-groups ANOVA** — one test of whether 3+ separate groups have the same mean. H₁: at least one differs.

</div>
<div>

***F* statistic** — between-groups variance ÷ within-groups variance (MS<sub>Between</sub>/MS<sub>Within</sub>). Never negative; near 1 when H₀ is true; one-tailed; two dfs (k − 1, N − k).

</div>
<div>

**Sums of squares & mean squares** — SS<sub>Total</sub> = SS<sub>Between</sub> + SS<sub>Within</sub>; MS = SS/df. The source table lays them out.

</div>
<div>

**η² (eta squared)** — SS<sub>Between</sub>/SS<sub>Total</sub>: the proportion of variability explained by the groups. Small .01, medium .06, large .14.

</div>
<div>

**Post-hoc tests** — pairwise comparisons after a significant *F*, corrected for multiple comparisons (Tukey HSD, Bonferroni, Scheffé).

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Tomorrow: Discussion 11 (ANOVA in R; Data Write-Up #2 begins). Thursday: repeated-measures & two-way ANOVA.
