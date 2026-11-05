---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Exam 3 Review
exportFilename: ps211_fall2026_exam3_review
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Exam 3 Review Session

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- ==Exam 3== is on **Thursday, November 12** during our regular class time.
    - It covers **Lectures 11–14**: effect size and power, parametric assumptions, single-sample, paired-samples, and independent-samples *t* tests, and APA-style reporting.
    - In class, multiple choice, scenario-based. **No calculator** is needed.
    - You will *not* be tested on R code, but you should be able to read R output (a `t.test()` printout).
    - You will have the entire class period (75 minutes). Please bring a pencil.
- ==Discussion 10== (Wed. 11/11) is Exam 3 review and practice.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Plan for today

:: content ::

<div class="grid grid-cols-3 gap-4 mt-2">

<StickyNote color="indigo-light" title="Part 1: Choosing and running a t test" width="100%">
Lectures 12, 13, and 14<br><br>
Which test fits which design, why t and not z, degrees of freedom, assumptions, the six steps for each test, pooled variance, reading R output
</StickyNote>

<StickyNote color="teal-light" title="Part 2: Interpreting a result" width="100%">
Lecture 11, plus pieces of 12–14<br><br>
Effect size, significant ≠ big, confidence intervals, p values, statistical power, two kinds of null results, APA style
</StickyNote>

<StickyNote color="amber-light" title="Part 3: Practice" width="100%">
14 slides of exam-style questions<br><br>
New scenarios, same kinds of questions as the exam. If we run out of time, work through the rest on your own; every answer is on the slide.
</StickyNote>

</div>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="34rem">The exam asks you to <i>recognize which situation you are in</i> and to <i>read a result correctly</i>. Very little arithmetic. That is what today is for.</SpeechBubble></p>

---
layout: cover
color: indigo-light
---

# Part 1: Choosing and running a *t* test
### Lectures 12, 13, and 14

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One idea, four tests

:: content ::

Every test asks the same question: **how far is what we observed from what $H_0$ predicts, in units of noise?**

<table class="compact-table text-sm">
<thead><tr><th></th><th>z test (L10)</th><th>Single-sample <i>t</i> (L12)</th><th>Paired-samples <i>t</i> (L13)</th><th>Independent-samples <i>t</i> (L14)</th></tr></thead>
<tbody>
<tr><td><b>The situation</b></td><td>One sample mean vs. a known μ, <b>σ known</b></td><td>One sample mean vs. a known μ, <b>σ unknown</b></td><td>Two scores per participant (within-subjects)</td><td>Two separate groups (between-subjects)</td></tr>
<tr><td><b>Signal</b></td><td>M − μ</td><td>M − μ</td><td>M<sub>D</sub> − 0</td><td>(M₁ − M₂) − 0</td></tr>
<tr><td><b>Noise (SE)</b></td><td>σ / √n</td><td>s<sub>M</sub> = s / √n</td><td>s<sub>M</sub> = s<sub>D</sub> / √n</td><td>SE<sub>difference</sub> = √(s²<sub>pooled</sub>/n₁ + s²<sub>pooled</sub>/n₂)</td></tr>
<tr><td><b>Null world</b></td><td>normal (z)</td><td><i>t</i>, df = n − 1</td><td><i>t</i>, df = n − 1 (n = pairs)</td><td><i>t</i>, df = n₁ + n₂ − 2</td></tr>
<tr><td><b>Effect size</b></td><td>(M − μ) / σ</td><td>(M − μ) / s</td><td>M<sub>D</sub> / s<sub>D</sub></td><td>(M₁ − M₂) / s<sub>pooled</sub></td></tr>
<tr><td><b>In R</b></td><td><code>z.test()</code></td><td><code>t.test(x, mu = )</code></td><td><code>t.test(x, y, paired = TRUE)</code></td><td><code>t.test(x, y, var.equal = TRUE)</code></td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Steps 2, 4, and 6 never change" width="90%">Hypotheses about populations (μ, never M); a cutoff chosen in advance from the null world; compare, decide, say it in plain English. The CI and d follow the same recipes every time.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Which test? Three questions to ask

:: left ::

1. **Is the outcome a number** with a mean? If it is a category (which dorm, yes/no), none of these tests apply.
2. **What is being compared?**
   - One sample vs. a **known value** → single-sample *t* (z only if σ is known).
   - **Two scores from each unit** (before/after; two conditions, same person) → paired *t*.
   - **Two separate groups**, one score each → independent *t*.
   - Three or more groups → not a *t* test (ANOVA, next week).
3. **Direction stated in advance?** One-tailed; otherwise two-tailed.

:: right ::

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Same 30 runners' 5K times in Week 1 and Week 8 of a training plan. Which test?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**Paired-samples *t***: each runner supplies two times. The "participant" is whatever unit has two scores: a person, a film, a city.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="The giveaway words" width="100%">"The same participants", "before and after" → paired. "One group… another group" → independent. "Compared to the known / recommended value" → single-sample.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Why *t* and not z

:: left ::

- A z test needs **σ**. We almost never have it, so the *t* test substitutes **s** and uses an **estimated** SE, $s_M = s/\sqrt{n}$.
- $s$ differs from sample to sample. When it comes out small, $t$ comes out too big, so extreme $t$ values are more common under $H_0$ than extreme z values: **heavier tails**.
- The cutoffs move **farther out** than ±1.96 to keep α at .05. How far depends on **df**: few df, heavy tails; many df, almost normal.

<p v-click><StickyNote color="amber-light" title="No conflict with the CLT" width="100%">Sample means are still normal. The t distribution describes a mean <i>divided by an estimated SE</i>; the extra wobble is in the denominator.</StickyNote></p>

:: right ::

<img src="/images/lecture12/t_vs_z.png" alt="t distributions with df = 4, 10, 30 and the z distribution" class="w-10/12 mx-auto"/>

<div class="text-sm mt-1">Two-tailed α = .05 cutoffs: df = 4 → ±2.776; df = 9 → ±2.262; df = 18 → ±2.101; df = 30 → ±2.042; z → ±1.960.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Degrees of freedom

:: left ::

**What df is:** the number of scores free to vary after the sample has been used to estimate something. Computing a mean fixes the last deviation (deviations sum to zero): one df spent per mean estimated.

| Test | df |
|---|---|
| Single-sample *t* | n − 1 |
| Paired-samples *t* | n − 1, where n = number of **pairs** |
| Independent-samples *t* | n₁ + n₂ − 2 (one per group) |

**What df does:** picks the *t* distribution, and so the cutoffs. It also tells you the sample size: *t*(19) is 20 pairs; *t*(58) is 60 people in two groups.

:: right ::

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Twenty people rate their mood before and after a nap. Forty ratings. What are the df?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**19.** Twenty *pairs* → twenty difference scores → one mean estimated → 19. The forty ratings are not forty independent scores.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="n − 1 and √n" width="100%">n − 1 lives <i>inside</i> s (a correction to the estimate of spread). √n turns the spread of scores into the spread of means. Different jobs; both in every t test.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Assumptions of parametric tests

:: left ::

<table class="compact-table text-sm">
<thead><tr><th>Assumption</th><th>z</th><th>Single <i>t</i></th><th>Paired <i>t</i></th><th>Indep. <i>t</i></th></tr></thead>
<tbody>
<tr><td>Outcome is numeric (has a mean)</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td></tr>
<tr><td>Comparison distribution is normal (safe when n is large, by the CLT, or the population is roughly normal)</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td></tr>
<tr><td>Observations are independent (no roommates, no one measured twice unless that <i>is</i> the design)</td><td>✓</td><td>✓</td><td>✓ (pairs)</td><td>✓</td></tr>
<tr><td>Groups have equal variance (rule of thumb: larger SD less than twice the smaller; otherwise Welch's test)</td><td>—</td><td>—</td><td>—</td><td>✓</td></tr>
<tr><td>Population σ is known</td><td>✓</td><td>—</td><td>—</td><td>—</td></tr>
</tbody>
</table>

<p v-click>

- **Outliers** are not an assumption but a check you run every time, and a decision you make *before* seeing whether dropping them helps.
- Parametric tests buy **power** with these assumptions. When they fail badly, the p values are wrong, and a non-parametric test (Lecture 19) is the fallback.

</p>

:: right ::

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Two groups of students; the SDs of their quiz scores are 4.1 and 12.6. What should you do?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The larger SD is three times the smaller: the equal-variance assumption fails. Use the version of the test that does not assume it (Welch's, R's default when you leave out `var.equal = TRUE`). Same six steps.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The six steps, for any *t* test

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>The question</th><th>What you write down</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Who is being compared, and which test fits?</td><td>The design (one sample / pairs / two groups) and the test. Check: numeric outcome, independence, normality (or large n), equal variance for two groups.</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>What are the two competing claims?</td><td>About <b>populations</b>: H₀: μ = μ₀, or μ<sub>D</sub> = 0, or μ₁ = μ₂. H₁: ≠ (two-tailed) or &lt; / &gt; (one-tailed, decided in advance).</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td>If H₀ were true, what results would we expect?</td><td><b>Center</b> (μ, or 0), <b>spread</b> (the test's SE), <b>shape</b> (<i>t</i> with the test's df).</td></tr>
<tr><td><b>4.</b> Critical values</td><td>How extreme is extreme enough?</td><td>α (usually .05), tails, df → cutoff(s) from the <i>t</i> distribution (R: <code>qt()</code>; farther out than ±1.96 for small df).</td></tr>
<tr><td><b>5.</b> Test statistic</td><td>How far is our result from what H₀ predicts, in SEs?</td><td>t = signal ÷ SE. Its sign says the direction; its size says how many SEs.</td></tr>
<tr><td><b>6.</b> Decision</td><td>Is it past the cutoff? What do we conclude?</td><td>Route 1: compare t to the cutoff. Route 2: compare p to α. They always agree. Reject or <b>fail to reject</b> (never "accept"); then say it in plain English, with the direction.</td></tr>
</tbody>
</table>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Single-sample *t*: the sleep study, recapped

:: left ::

Ten patients, extra hours of sleep on Drug 2, tested against μ = 0 (no effect). $M = 2.33$, $s = 2.00$.

- **Step 3.** Center 0, $s_M = 2.00/\sqrt{10} = 0.63$, *t* with df = 9.
- **Step 4.** α = .05, two-tailed, df = 9 → cutoffs **±2.262**.
- **Step 5.** $t = (2.33 - 0)/0.63 = 3.68$.
- **Step 6.** 3.68 > 2.262 → reject $H_0$; p = .005. Patients slept significantly longer on the drug.
- **CI:** $2.33 \pm 2.262 \times 0.63$ = **\[0.90, 3.76]** hours. **d:** $2.33/2.00 = 1.16$.

:: right ::

```text
	One Sample t-test

data:  drug2$extra
t = 3.6799, df = 9, p-value = 0.005076
alternative hypothesis: true mean is not equal to 0
95 percent confidence interval:
 0.8976775 3.7623225
sample estimates:
mean of x
     2.33
```

<p v-click><StickyNote color="amber-light" title="Reading the output" width="100%">t and df → Step 5 and which null world. p-value → Step 6, Route 2. The CI → plausible values for the true mean; it excludes 0, so it agrees with the test. "mean of x" is M. R prints no SD and no d: those you compute.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Paired-samples *t*: a single-sample test on differences

:: left ::

1. Compute one **difference score** per unit: after − before, Condition 1 − Condition 2.
2. The null world is a **distribution of mean differences**: center 0, spread $s_M = s_D/\sqrt{n}$, *t* with df = pairs − 1.
3. From there it is the single-sample test with μ = 0: $t = M_D / s_M$. CI $= M_D \pm t_{crit} \times s_M$. $d = M_D / s_D$.

<p v-click><Admonition title="Why pair at all?" color="green-light" width="100%">

Comparing each unit to itself subtracts out the differences *between* units (a great film is rated high on both sites; a fast person is fast in both conditions). The noise left is only how much the *differences* vary, so the paired test is far more powerful than treating the two sets of scores as separate groups. Forget `paired = TRUE` and t drops, the CI widens, and df doubles.

</Admonition></p>

:: right ::

<img src="/images/lecture13/mean_diff_null_n5_n146.png" alt="Null distributions of mean differences for n = 5 and n = 146" class="w-full mx-auto"/>

<div class="text-sm mt-2">

**Fandango vs. IMDb, 146 films (Lecture 13):** each film's stars minus its IMDb score. $M_D = 0.72$, $s_D = 0.47$, *t*(145) = 18.67, *p* < .001, *d* = 1.54, 95% CI \[0.64, 0.80]. Run as two independent groups by mistake: *t*(290) = 12.05 and a wider CI.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Independent-samples *t*: two groups

:: left ::

Two separate samples, so the noise has to be built from **both**. The standard error takes three steps:

1. **Estimate the population variance using BOTH sets of scores.** Two sample SDs become one ==pooled variance==.
2. **Combine the uncertainty of the two means.** Each group mean wobbles from sample to sample; a *difference* between them wobbles more.
3. **Back to the scale of the data.** Square root → $SE_{difference}$, the spread of the null world.

:: right ::

<Admonition title="Running example: the recall study (L14)" color="indigo-light" width="100%">

20 people, 10 per group. Recalled-words-first: M = 36.6, SD = 5.3 (s² = 28.5). Standard order: M = 30.3, SD = 7.3 (s² = 53.8). Observed difference: **6.3 words**. Is that big, compared with what chance alone would produce?

</Admonition>

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

A student "pools" by lumping all 20 scores together and computing one variance. Why is that wrong?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Lumping adds the *difference between the means* into the spread. Pooling measures spread *within* each group, then combines.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="After step 3, nothing new" width="100%">t = (M₁ − M₂) / SE<sub>difference</sub>, df = n₁ + n₂ − 2. CI = (M₁ − M₂) ± t<sub>crit</sub> × SE<sub>difference</sub>. d = (M₁ − M₂) / s<sub>pooled</sub>.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 1: one variance estimate from both groups

:: left ::

- The equal-variance assumption says both groups' populations have the **same** spread, σ². So $s_1^2$ and $s_2^2$ are two estimates of *one* number, and two estimates are better than one.
- Average them, weighting each by its df so that a bigger sample counts for more:

$$s^2_{pooled} = \frac{df_1\, s_1^2 + df_2\, s_2^2}{df_1 + df_2}, \qquad df_1 = n_1 - 1,\ df_2 = n_2 - 1$$

<p v-click>

- Equal n: the plain average. Unequal n: closer to the larger group's variance. Either way it lands **between** $s_1^2$ and $s_2^2$.

</p>

:: right ::

<p v-click><Admonition title="Recall study" color="indigo-light" width="100%">

df = 9 and 9, so the weighted average is just the average:

$$s^2_{pooled} = \frac{28.5 + 53.8}{2} = 41.1$$

so $s_{pooled} = \sqrt{41.1} = 6.41$ words.

</Admonition></p>

<p v-click><Admonition title="What is 41.1?" color="green-light" width="100%">

Our single best estimate of how much **individual scores** vary within a group, using everyone's data. Its square root, 6.41 words, is the pooled SD: the spread of *people*. It is the denominator of Cohen's *d*, and nothing about it depends on how many people we tested.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Check" width="100%">41.1 sits between 28.5 and 53.8, as a pooled variance always must.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 2: combine the uncertainty of the two means

:: left ::

- Each group's mean is an estimate, and it wobbles from sample to sample. Spread of *scores* → spread of a *mean*: the variance of a mean is $s^2_{pooled}/n$. (The same $\sqrt{n}$ idea as every SE so far, written in variance units.)
- Our signal is a **difference** between two means. Each mean brings its own wobble, so the difference wobbles more than either mean alone. Independent uncertainties **add**:

$$SE^2_{difference} = \frac{s^2_{pooled}}{n_1} + \frac{s^2_{pooled}}{n_2}$$

<p v-click>

- Why add *variances* rather than SDs? Because variances add and SDs do not: $\sqrt{a + b} \neq \sqrt{a} + \sqrt{b}$.

</p>

:: right ::

<img src="/images/exam3_review/mean_vs_difference_wobble.png" alt="A single group mean wobbles less than a difference between two means" class="w-full rounded"/>

<p v-click><Admonition title="Recall study" color="indigo-light" width="100%">

$SE^2_{difference} = 41.1/10 + 41.1/10 = 4.11 + 4.11 = 8.22$. Still in squared words, so not done yet.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 3: back to the scale of the data

:: left ::

- Step 2 gave a *variance* of mean differences, in squared words. Take the square root to get a standard deviation in words:

$$SE_{difference} = \sqrt{\frac{s^2_{pooled}}{n_1} + \frac{s^2_{pooled}}{n_2}}$$

- This is the spread of the null world: **how far apart two group means would typically land, by chance, if $H_0$ were true.** The observed difference gets judged against it.

<p v-click><Admonition title="Recall study" color="indigo-light" width="100%">

$SE_{difference} = \sqrt{8.22} = 2.87$ words. *t*(18) = 6.3 / 2.87 = 2.20, cutoffs ±2.101 → reject; *p* = .041; 95% CI \[0.3, 12.3]; *d* = 6.3 / 6.41 = 0.98.

</Admonition></p>

:: right ::

<p v-click><StickyNote color="amber-light" title="Two spreads, two jobs" width="100%">s<sub>pooled</sub> = 6.41: the spread of <i>people</i>. Used in d.<br>SE<sub>difference</sub> = 2.87: the spread of <i>differences between means</i>. Used in t and the CI.<br>Only the SE shrinks as n grows.</StickyNote></p>

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Same study, but 40 people per group instead of 10. Which of these gets smaller?

- **A)** $s_{pooled}$ only
- **B)** $SE_{difference}$ only
- **C)** Both
- **D)** Neither

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** People vary as much as they ever did (and so does *d*). Means of 40 wobble less than means of 10, so the SE drops to $\sqrt{41.1/40 + 41.1/40} = 1.43$, and the same 6.3-word difference would give *t* ≈ 4.4.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Every test: the SD, the SE, and the test statistic

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Test</th><th>Spread of scores (SD)</th><th>Standard error (spread of the null world)</th><th>Test statistic</th><th>Null world</th></tr></thead>
<tbody>
<tr><td><b>z test</b> (L10)</td><td>σ, <b>known</b></td><td>SE = σ / √n</td><td>z = (M − μ) / SE</td><td>normal (z)</td></tr>
<tr><td><b>Single-sample <i>t</i></b> (L12)</td><td>s, estimated (÷ n − 1)</td><td>s<sub>M</sub> = s / √n</td><td>t = (M − μ) / s<sub>M</sub></td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Paired-samples <i>t</i></b> (L13)</td><td>s<sub>D</sub>, the SD of the difference scores</td><td>s<sub>M</sub> = s<sub>D</sub> / √n &nbsp;(n = number of pairs)</td><td>t = M<sub>D</sub> / s<sub>M</sub></td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Independent-samples <i>t</i></b> (L14)</td><td>s₁ and s₂, pooled into s²<sub>pooled</sub></td><td>SE<sub>difference</sub> = √( s²<sub>pooled</sub>/n₁ + s²<sub>pooled</sub>/n₂ )</td><td>t = (M₁ − M₂) / SE<sub>difference</sub></td><td><i>t</i>, df = n₁ + n₂ − 2</td></tr>
</tbody>
</table>

<p v-click>

- Every test statistic is **signal ÷ its row's standard error**. The null world is $t$ whenever the SE was estimated, and normal only when σ was known.
- The SD column is about **people** and feeds Cohen's *d*. The SE column is about **means** and feeds *t* and the CI. Only the SE column shrinks as n grows.
- Rows 2 and 3 are the same test run on different scores. Row 4 follows the same pattern, spread of scores → spread of means, with two samples feeding the SD and two means feeding the SE.

</p>

---
layout: cover
color: indigo-light
---

# Part 2: Interpreting a result
### Lecture 11, plus pieces of 12–14

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Effect size: how big, not whether

:: left ::

**Cohen's d** = the difference, in standard deviations of *individual scores*:

- z test: $(M - \mu)/\sigma$; single-sample *t*: $(M - \mu)/s$
- paired: $M_D / s_D$; independent: $(M_1 - M_2)/s_{pooled}$

Conventions: **0.2 small, 0.5 medium, 0.8 large.**

<p v-click>

- **d does not depend on n**: it divides by an SD, not an SE. Double the sample and d stays put while t and p move.
- **Significant ≠ big.** Huge n: a tiny d is "significant." Small n: a large d can miss.

</p>

:: right ::

<img src="/images/lecture11/effect_size_overlap.png" alt="Overlap between two distributions for small, medium, and large d" class="w-full mx-auto"/>

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Study A: n = 2,000, p = .001, d = 0.10. Study B: n = 40, p = .03, d = 0.70. Which found the bigger effect?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** p values depend on n; effect sizes do not. A's tiny effect was detectable only because of its huge sample.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Confidence intervals

:: left ::

$$CI = \text{estimate} \pm t_{crit} \times SE$$

- The **estimate** is M, $M_D$, or $M_1 - M_2$. The interval is **centered on it**, so the observed value is always inside its own CI.
- The **width** is $t_{crit} \times SE$ each way: wider when n is small (bigger SE *and* a farther-out cutoff), narrower when n is large.
- **Interpretation:** the range of plausible values for the **population** quantity (μ, $\mu_D$, or $\mu_1 - \mu_2$). About 95% of intervals built this way capture the truth.

:: right ::

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

The mean difference is 12 points and the test was *not* significant. Which CI is plausible: \[8, 16], \[−4, 28], or \[2, 10]?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**\[−4, 28].** Centered on 12 and containing 0, which is what "not significant" means. \[8, 16] is centered on 12 but excludes 0 (a significant result); \[2, 10] is not even centered on 12. A wide interval means low precision, usually a small n.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="The CI and the test always agree" width="100%">The hypothesized value (μ₀, or 0) <b>outside</b> the CI ⇔ reject H₀. <b>Inside</b> ⇔ fail to reject. A non-significant result's CI contains <i>both</i> 0 <i>and</i> the observed difference.</StickyNote></p>



---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# p values: what they are and are not

:: left ::

**p** = the probability of a result at least this extreme **if $H_0$ were true**.

- *p* = .03: if there were no effect, data like these would show up 3% of the time.
- It is **not** the probability that $H_0$ is true, **not** the probability the result is due to chance, and **not** an effect size.
- Below α → reject. Above α → **fail to reject**: we did not find evidence, which is not evidence of nothing.
- Route 1 (t vs. cutoff) and Route 2 (p vs. α) are the same decision in two languages.

:: right ::

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

A paired test gives *t*(24) = 1.20, *p* = .24. A classmate says "so there is a 24% chance the treatment does nothing." What is wrong?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

p is computed *assuming* the treatment does nothing; it cannot then tell you the probability that it does nothing. Correct reading: if there were no effect, a difference this large would occur 24% of the time, so the data are not surprising under $H_0$ and we fail to reject.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Statistical power

:: left ::

<table class="compact-table text-sm">
<thead><tr><th></th><th>H₀ true (no effect)</th><th>H₀ false (real effect)</th></tr></thead>
<tbody>
<tr><td><b>Reject H₀</b></td><td>Type I error (α, usually .05)</td><td>Correct: <b>power = 1 − β</b></td></tr>
<tr><td><b>Fail to reject</b></td><td>Correct</td><td>Type II error (β)</td></tr>
</tbody>
</table>

**Power** = the probability of detecting an effect that is real. Target: 0.80.

**What raises power:** larger n, larger true effect, less variability, larger α (at a cost), one-tailed test (if decided in advance). Only the first three are free.

<p v-click><StickyNote color="amber-light" title="Power analysis" width="100%"><i>A priori</i>: "for an effect of size d, how many participants for 80% power?" Done before the study. The inputs are always effect size, n, α, and tails; give any three, get the fourth.</StickyNote></p>

:: right ::

<img src="/images/lecture11/power_two_worlds.png" alt="Null world and real-effect world with the cutoff; power is the shaded area" class="w-full mx-auto"/>

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

A study with 12 per group finds p = .30. The true effect, if any, is medium (d ≈ 0.5), for which this design has power ≈ 0.20. What does the null result mean?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Very little. If the effect is real, a study this size misses it 80% of the time; "not significant" was the expected outcome either way. Low power makes a null result uninformative.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Two kinds of null results

:: left ::

<div class="border-2 border-gray-300 rounded-lg p-3 text-sm">
<b>Pixar films before vs. after 2010 (Discussion 9)</b><br/>
<i>t</i>(21) = 1.71, <i>p</i> = .10. <b>d = 0.72</b>, 95% CI <b>[−2, 22]</b> points.<br/>
<span class="text-indigo-700"><b>"We could not tell."</b></span> A large effect is still plausible; 23 films was not enough. Low power.
</div>

<div class="border-2 border-gray-300 rounded-lg p-3 text-sm mt-3">
<b>Women vs. men, words per day (Mehl et al., 2007; Lecture 14)</b><br/>
<i>t</i>(394) = 0.68, <i>p</i> = .50. <b>d = 0.07</b>, 95% CI <b>[−1,029, 2,121]</b> words out of ~16,000.<br/>
<span class="text-indigo-700"><b>"If there is a difference, it is small."</b></span> A narrow CI around 0 rules out any large effect.
</div>

:: right ::

<p v-click><StickyNote color="amber-light" title="Same decision, opposite lessons" width="100%">"Fail to reject" alone tells you almost nothing. A wide CI with a big d: "could not tell." A tight CI around 0 with a tiny d: "nothing much there." Both CIs contain 0 <i>and</i> the observed difference.</StickyNote></p>

<p v-click><Admonition title="Quick check" color="teal-light" width="100%">

Which of the two studies would benefit most from a replication with a larger sample?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Pixar. Its question is still open. Mehl et al.'s question (is the gap large?) is already answered; more people would only narrow an interval that is already tight around 0.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# APA style: the checklist

:: left ::

**Always include:** descriptives for each group or condition (*M*, *SD*), the **direction** in words, *t*(df) = value, *p*, *d*, and the 95% CI.

**Formatting (APA 7):**
- Italic symbols (*t*, *p*, *M*, *SD*, *d*); not the numbers or df.
- Two decimals for statistics, means, SDs, d, CI bounds.
- *p* to three decimals, **no leading zero**: *p* = .041; below .001, *p* < .001. Never "0.000" or "1.5e-09".
- df in parentheses after *t*; CI in brackets; order *t*(df), *p*, *d*, CI.

:: right ::

<Admonition title="A correct sentence (recall study)" color="green-light" width="100%">

Participants shown their recalled words first remembered more words (*M* = 36.60, *SD* = 5.34) than participants given the standard order (*M* = 30.30, *SD* = 7.33), *t*(18) = 2.20, *p* = .041, *d* = 0.98, 95% CI \[0.27, 12.33].

</Admonition>

<p v-click><Admonition title="Quick check: spot the errors" color="teal-light" width="100%">

"The T-test was significant (T = 2.196, P = 0.041, DF = 18), so the method works for everyone."

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Lowercase italic *t* and *p*; df in parentheses after *t*; two decimals; no leading zero; no descriptives, direction, *d*, or CI; and "works for everyone" overclaims a difference in means.

</Admonition></p>

---
layout: cover
color: indigo-light
---

# Part 3: Practice
### Exam-style questions. If we run out of time, finish these on your own.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 1: Which test?

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher asks 40 first-year students and 40 seniors how many hours they slept last night and compares the two averages.

- **A)** z test
- **B)** Single-sample *t* test
- **C)** Paired-samples *t* test
- **D)** Independent-samples *t* test

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** Two separate groups of different people, one score each. Equal group sizes do not make it paired; pairing needs two scores from the same unit.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

A campus café claims its espresso shots contain 75 mg of caffeine. A student measures 15 shots and compares their average to 75 mg.

- **A)** Single-sample *t* test, because one sample is compared with a known value and σ is unknown
- **B)** z test, because the claimed mean is known
- **C)** Paired-samples *t* test, because each shot is compared with 75
- **D)** None of these; 15 is too few shots

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Knowing the *claimed* μ is not knowing σ (B). \(C) misreads "compared with 75": there is one score per shot, not two. (D): small n is what the t distribution's df handles.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 2: Which test? (continued)

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

The same 25 students take a vocabulary quiz after a week of handwritten notes and again after a week of typed notes (order counterbalanced).

- **A)** Paired-samples *t* test
- **B)** Independent-samples *t* test
- **C)** Single-sample *t* test
- **D)** None of these tests is appropriate

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Two scores per student → difference scores. Counterbalancing deals with order effects; it does not change the test.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher asks students in three majors (psychology, biology, economics) how many hours per week they study and wants to know whether the three averages differ.

- **A)** Independent-samples *t* test, run once
- **B)** Paired-samples *t* test, because the majors are matched
- **C)** None of these tests is appropriate: three groups need a different test
- **D)** z test, because the groups are large

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** A *t* test compares two means. Three or more groups need ANOVA (next week). Running three *t* tests inflates the Type I error rate.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 3: Hypotheses and df

:: left ::

Thirty-two students rate how focused they feel (1–10) after studying in a quiet library and after studying in a busy café; everyone does both.

<Admonition title="Multiple choice" color="teal-light" width="100%">

What is the null hypothesis?

- **A)** $M_D = 0$: the sample's mean difference is zero.
- **B)** Focus is higher in the library.
- **C)** Every student feels equally focused in both settings.
- **D)** $\mu_D = 0$: in the population, the mean difference in focus between the two settings is zero.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** Hypotheses are about populations (μ), never about the sample (A). (B) is a directional research hypothesis. \(C) is about individuals, not the mean.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The study reports *t*(31) = 2.45, *p* = .020. A second lab runs the comparison with **two separate groups** of students (library group vs. café group) and reports *t*(46) = 2.45. How many students were in the second study?

- **A)** 46
- **B)** 47
- **C)** 48: df = n₁ + n₂ − 2, one df lost per group
- **D)** Cannot tell without the group sizes

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** Two groups → two means estimated → 46 + 2 = 48 people. In the first study, df = 31 was 32 *pairs*. The same df can mean different numbers of people, so read the design first.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice 4: Reading R output

:: left ::

Twenty-five students wore a step counter for a week; their average daily steps are compared with the 10,000-step guideline.

```text
	One Sample t-test
t = -2.3, df = 24, p-value = 0.0305
95 percent confidence interval:
  7103  9755
mean of x
     8429
```

<p v-click><StickyNote color="amber-light" title="What the CI is for" width="100%">Plausible values of the <i>population</i> mean daily steps for students like these. The sample mean is known exactly (8,429); the interval is about μ.</StickyNote></p>

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which conclusion is correct (α = .05, two-tailed)?

- **A)** Fail to reject: t is negative.
- **B)** Reject $H_0$: these students average significantly fewer than 10,000 steps; 10,000 is outside the CI.
- **C)** Reject $H_0$: students take exactly 8,429 steps per day.
- **D)** Fail to reject: the CI contains the sample mean.

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** p = .03 < .05 and 10,000 lies outside \[7,103, 9,755]. The sign of t only gives the direction. (D) is true of every CI and says nothing about the decision; the question is whether μ₀ = 10,000 is inside.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 5: Confidence intervals

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Students who used a standing desk for a month scored 4 points higher on a focus scale than students with a regular desk, *t*(38) = 2.10, *p* = .043. Which 95% CI for the difference is plausible?

- **A)** \[0.2, 7.8]
- **B)** \[−2.1, 10.1]
- **C)** \[3.5, 4.5]
- **D)** \[2.1, 2.1]

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Centered on 4 and, since p < .05, excluding 0, just barely (p is close to .05). (B) contains 0, so it would go with a non-significant result. \(C) and (D) are far too narrow for t = 2.10.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The same study is repeated with four times as many students and finds the same 4-point difference. Compared with the first study, the new CI will be:

- **A)** The same width, because the difference is the same.
- **B)** Wider, because more people means more variability.
- **C)** Centered on 0.
- **D)** Narrower: a smaller SE and a cutoff closer to 1.96.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Width is $t_{crit} \times SE$. Four times the n cuts the SE in half, and larger df pulls the cutoff in. The center stays at the observed difference, 4.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 6: p values and decisions

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher sets α = .05, two-tailed, in advance and finds *t*(14) = 2.90, *p* = .012. What can she conclude?

- **A)** Nothing yet: she has not computed d.
- **B)** The effect is large.
- **C)** Her result is significant: a difference this big would be unlikely if $H_0$ were true.
- **D)** There is a 1.2% chance that $H_0$ is true.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** (A): d and the CI should be reported, but the decision does not wait for them. (B): p says nothing about size. (D) reverses what p is.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

Another researcher finds *t*(14) = 1.90, *p* = .078, and writes "the groups did not differ." What is the best correction?

- **A)** "We did not find evidence of a difference" — the test cannot show that the groups are the same.
- **B)** No correction needed.
- **C)** "The groups differed, but not significantly."
- **D)** "The result is significant at the 10% level, so the groups differ."

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Fail to reject is not "accept." (D) changes α after seeing p, which is not allowed.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 7: Effect size

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

In a paired study, the mean difference in reading speed after a typing course is 18 words per minute, the SD of the difference scores is 36, and the standard error is 6. What is Cohen's d?

- **A)** 18/6 = 3.0
- **B)** 18/36 = 0.5, a medium effect
- **C)** 36/18 = 2.0
- **D)** 6/36 = 0.17

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** d divides by the SD of scores (here, of the difference scores), not by the SE. 18/6 = 3.0 is the *t* statistic.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The same course is tested on a second group with the same mean difference and SD, but ten times as many people. What happens to d, t, and p?

- **A)** All three stay the same.
- **B)** d gets larger; t and p stay the same.
- **C)** d and t get larger; p gets larger.
- **D)** d stays the same; t gets larger; p gets smaller.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** d has no n in it. t divides by an SE that shrinks with √n, so t grows and p falls. Lecture 11: significant ≠ big.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 8: Statistical power

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A real but small effect exists. A study with 10 per group fails to find it. This outcome is:

- **A)** A Type II error, which is the most likely outcome when power is low.
- **B)** A Type I error.
- **C)** Proof that the effect is not real.
- **D)** Impossible: real effects are always detected.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Missing a real effect is a Type II error (β). With a small effect and 10 per group, power might be 0.1–0.2, so missing it is what usually happens.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which change would **reduce** a study's power?

- **A)** Recruiting more participants.
- **B)** Using a more reliable measure of the outcome.
- **C)** Lowering α from .05 to .01.
- **D)** Studying a stronger manipulation with a larger true effect.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** A stricter α moves the cutoff out, so fewer real effects clear it. (A), (B), and (D) all raise power: more data, less noise, more signal.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 9: Assumptions

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher compares anxiety scores of 8 students who own a pet with 8 who do not. Which of these is the biggest threat to the test's assumptions?

- **A)** The two groups have the same size.
- **B)** The pet owners were recruited from one small club and know each other well.
- **C)** Anxiety was measured on a 0–40 scale.
- **D)** The pet owners' mean is lower.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Observations within a group should be independent; a tight-knit club violates that (and invites a confound). (A) is fine, \(C) is a numeric outcome, (D) is the hypothesis.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

With only 8 per group, which assumption matters most, and why?

- **A)** Equal variance; it only matters for small samples.
- **B)** Known σ; small samples need the population SD.
- **C)** None; the t test has no assumptions.
- **D)** Normality: with small n the CLT cannot rescue a skewed population, so the t distribution may be the wrong null world.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** The normality assumption is about the comparison distribution; large n makes it safe by the CLT, small n does not. Equal variance matters at any n; known σ is a z-test requirement.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 10: Pooled variance and the SE

:: left ::

Group 1: n = 6, $s_1^2 = 20$. Group 2: n = 16, $s_2^2 = 50$.

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which is the pooled variance?

- **A)** 35, the average of 20 and 50.
- **B)** 70, the sum.
- **C)** About 42.5: a df-weighted average, closer to the larger group's 50.
- **D)** 10, since 20/2 = 10.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** $(5 \times 20 + 15 \times 50)/20 = 42.5$. The group with more df counts for more. Any pooled variance must land between the two: 70 and 10 are out.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The standard error of the difference comes out to 3.1 points. In words, 3.1 is:

- **A)** How far a typical participant's score is from their group mean.
- **B)** The range the true difference must fall in.
- **C)** The largest t value we could observe.
- **D)** How far apart the two group means would typically be, by chance, if $H_0$ were true.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** An SE is the spread of a *statistic* (here, a difference between means) across repeated samples. (A) describes the pooled SD.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 11: The *t* distribution

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Why does a *t* test with df = 7 use cutoffs of ±2.365 rather than ±1.96?

- **A)** Because small samples have larger means.
- **B)** Because the population is not normal.
- **C)** Because the SE was estimated from only 8 scores, so t values more extreme than z values occur under $H_0$; the cutoff moves out to keep α at .05.
- **D)** Because α is larger for small samples.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Heavy tails come from the wobble in the estimated denominator. α is still .05; the cutoff adjusts so that it is.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher doubles her sample. What happens to the critical t value for α = .05?

- **A)** It decreases toward ±1.96, because with more df the t distribution is closer to normal.
- **B)** It stays at ±1.96.
- **C)** It increases: more data, stricter standard.
- **D)** It depends on the sample mean.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Cutoffs depend on df and α, never on the data. More df → lighter tails → cutoff closer in. (It never goes below 1.96.)

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 12: Paired vs. independent

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A researcher measures 20 people's reaction times with and without background music (within-subjects). Why is a paired test more powerful here than treating the two conditions as independent groups?

- **A)** Because it has more degrees of freedom.
- **B)** Because it subtracts out each person's baseline speed, leaving only the variability in the *differences* as noise.
- **C)** Because it uses the pooled variance.
- **D)** It is not; the two tests are equally powerful.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** People differ enormously in baseline speed; pairing removes that from the noise. (A): the paired test has *fewer* df (19 vs. 38) and is still more powerful.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

She runs `t.test(music, silence)` and forgets `paired = TRUE`. Compared with the correct analysis, the output will show:

- **A)** The same t and the same df.
- **B)** A larger t, because more df.
- **C)** An error message.
- **D)** The same means, but a smaller t, a wider CI, and df = 38 instead of 19.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** R runs an independent-samples test on the same numbers: between-person variability goes back into the SE. The means do not change; the noise estimate does.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 13: Two null results

:: left ::

Study X: 15 per group, *p* = .19, *d* = 0.60, 95% CI for the difference \[−3, 15] points.
Study Y: 500 per group, *p* = .62, *d* = 0.03, 95% CI \[−0.9, 1.5] points.

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which statement is best?

- **A)** Both studies show the treatment has no effect.
- **B)** X could not tell (a large effect is still plausible); Y shows that any effect is tiny.
- **C)** X is more informative because its d is larger.
- **D)** Y is uninformative because it was not significant.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Read the CIs. X's includes 0 *and* values up to 15: unresolved. Y's hugs 0: resolved, in the "nothing much" direction.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

In Study X the observed difference was 6 points. Which values are inside its CI, \[−3, 15]?

- **A)** Both 0 and 6: the interval is centered on the observed difference, and 0 is inside too, which is why the result is not significant.
- **B)** 0 but not 6.
- **C)** 6 but not 0.
- **D)** Neither; a CI contains population values only.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Every CI contains its own estimate (6 sits at the center). Whether it also contains 0 is what decides significance.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice 14: APA style

:: left ::

Quiz scores (out of 10): notes by hand (*M* = 7.8, *SD* = 1.6) vs. by laptop (*M* = 6.9, *SD* = 1.9); *t*(48) = 1.81, *p* = .077, *d* = 0.51, 95% CI \[−0.10, 1.90].

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which sentence is correctly written?

- **A)** Hand-note students scored higher (M = 7.8, SD = 1.6) than laptop students (M = 6.9, SD = 1.9), t(48) = 1.81, p = 0.077, d = 0.51, 95% CI \[−0.10, 1.90].
- **B)** Hand-note students (*M* = 7.80, *SD* = 1.60) did not score significantly higher than laptop students (*M* = 6.90, *SD* = 1.90), *t*(48) = 1.81, *p* = .077, *d* = 0.51, 95% CI \[−0.10, 1.90].
- **C)** The t test was not significant (*t* = 1.81, *p* > .05).
- **D)** Handwriting improves quiz scores, *t*(48) = 1.81, *p* = .077.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** (A): no italics, leading zero on p. \(C): no df, descriptives, direction, d or CI. (D) claims an effect the test did not find.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

R printed `p-value = 3.2e-06`. How should it appear in the sentence?

- **A)** *p* = 3.2e-06
- **B)** *p* = 0.0000032
- **C)** *p* = .000
- **D)** *p* < .001

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Three decimals, no leading zero, and anything below .001 is reported as *p* < .001. A p value is never exactly 0.

</Admonition></p>

---
layout: cover
color: indigo-light
---

# That's all for today!
Discussion 10 tomorrow is more Exam 3 practice. Good luck on Thursday!
