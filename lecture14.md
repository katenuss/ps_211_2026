---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 14
exportFilename: ps211_fall2026_lecture14
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 14: Independent-Samples *t* Tests (in R)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- ==Data Write-Up #1== is due **Monday, November 9** at 11:59 p.m. After today, re-read your APA results sentence (Part 5) and your interpretation (Part 7) before you submit.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Coming up:
  - Tuesday (11/10): Exam 3 Review
  - Wednesday (11/11): Discussion 10 — Exam 3 review & practice
  - Thursday (11/12): Exam 3 (covers Lectures 11–14)

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

**Paired-samples *t* test** — for within-subjects designs: compute one **difference score** per participant, then test whether the mean difference is 0. df = (number of pairs) − 1.

</div>
<div>

**Distribution of mean differences** — the null world: centered on 0, spread $s_M = s_D/\sqrt{n}$, *t* shape.

</div>
<div>

**APA style** — descriptives for each condition, direction in words, then *t*(df) = value, *p*, *d*, 95% CI. Italic symbols; no leading zero on *p*.

</div>
<div>

**Independent-samples *t* test (preview)** — for between-subjects designs: two separate groups. `t.test(group_1$dv, group_2$dv, var.equal = TRUE)`. df = n₁ + n₂ − 2.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Yesterday you ran the independent-samples t test in R. Today: where its standard error comes from, why n matters so much, and a famous study that settled who talks more.</SpeechBubble>
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

Yesterday's Pixar example: 23 films, Rotten Tomatoes vs. Metacritic scores.

```text
t = 5.2032, df = 22, p-value = 3.142e-05
95 percent confidence interval:
  5.543551 12.891232
mean difference 
       9.217391 
```

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which statement is correct?

- **A)** Rotten Tomatoes scores were significantly higher than Metacritic's for the same films, by about 9 points.
- **B)** df should be 44: there are 46 scores.
- **C)** Not significant: 5.2 is less than 22.
- **D)** 95% of films differ by 5.5 to 12.9 points.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Each film has two scores, so df = 23 − 1 = 22 (B). \(C) compares t to df: meaningless. (D) confuses the CI for the *mean* difference with the spread of individual films.

</Admonition>

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Yesterday's third test: Pixar films before 2010 (n = 10) vs. 2010 or later (n = 13) on Rotten Tomatoes: `t = 1.71, df = 21, p-value = 0.10`, 95% CI \[−2.1, 21.6], d = 0.72.

- **A)** The two eras are the same.
- **B)** Significant, because d is large.
- **C)** We could not tell: a sizable difference is plausible, but so is none. Underpowered.
- **D)** df should be 22: there are 23 films.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** Fail to reject, but the CI is wide and d = 0.72. (A) accepts $H_0$. (B) confuses size with significance. (D): two groups → 10 + 13 − 2 = 21.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

Before the new test, one more look at...
# Where a *t* distribution comes from

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# The paired test's null world, built step by step

:: left ::

<div class="text-[15px] leading-snug">

Suppose the drug does **nothing** ($H_0$ is true). Then:

1. **The population.** "With drug" and "without drug" scores come from the same place, so each person's **difference score** $D$ comes from a population centered on $\mu_D = 0$ (top; we gave it $\sigma_D = 2$ hours).
2. **One sample.** Draw $n = 10$ people, measure each twice, compute each person's $D$ (bottom: ten orange dots).
3. **Summarize it.** $M_D$ (the orange line) and $s_D$, the SD of the ten differences, dividing by $n - 1 = 9$. Then $s_M = s_D/\sqrt{10}$.
4. **The test statistic.** $t = M_D / s_M$: how many *estimated* standard errors $M_D$ is from 0.

</div>

:: right ::

<img src="/images/lecture14/paired_null_steps_1to4.png" alt="The population of difference scores under H0, and one sample of ten differences" class="w-11/12 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 5: repeat 20,000 times, and pile up the results

:: content ::

<img src="/images/lecture14/paired_null_step5.png" alt="Histograms of 20,000 sample mean differences and 20,000 t statistics" class="w-full mx-auto"/>

<p v-click>

- **Left:** pile up the 20,000 sample means. A normal curve with SD $\sigma_D/\sqrt{n}$: exactly what the Central Limit Theorem promised in Lecture 8.
- **Right:** pile up the 20,000 $t$ statistics instead. Heavier tails: 8% of them land beyond ±1.96, not 5%. *This* pile is the null world the paired test uses, and it is a $t$ distribution with df = 9.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Why a *t* distribution and not a normal one?

:: left ::

<Admonition title="Question" color="teal-light" width="100%">

The Central Limit Theorem says sample means are normally distributed. Doesn't a *t*-shaped null world contradict it?

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

No. The means **are** normal (left panel): the CLT is a statement about $M_D$. The test statistic is a different quantity, $M_D$ **divided by** $s_M$, and $s_M$ is estimated from the same sample, so it is a little different every time. In samples where $s_D$ happens to come out small, the denominator is too small and $t$ comes out too big. Those extra-large $t$'s are the heavy tails.

</Admonition>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What if we knew $\sigma_D$ and divided by the *true* standard error instead?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Every $t$ would turn into a $z$: same numerator, a fixed denominator. The pile would be exactly the normal curve, which is why the z test could use ±1.96. The $t$ distribution is the price of estimating the SE.

</Admonition></p>

:: right ::

<p v-click><StickyNote color="amber-light" title="No conflict with the CLT" width="100%">The CLT describes the <b>numerator</b>. The t distribution describes numerator ÷ <b>estimated</b> denominator. The df says how many scores went into estimating s<sub>D</sub>, and so how much s<sub>D</sub> can vary from sample to sample: with few df it varies a lot (heavy tails); with many df it hardly varies at all, and t is nearly normal.</StickyNote></p>

<p v-click>

<div class="flex items-center gap-3 mt-4">
<IceCream :size="70" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem">Same story for every t test, including today's: a normal numerator over an estimated standard error.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# n − 1 and √n are doing different jobs

:: left ::

Two divisions, two reasons. Both appear in every *t* test.

- **$n - 1$, inside the SD.** $s_D = \sqrt{SS/(n-1)}$ estimates how spread out *individual* difference scores are. We divide by $n - 1$ rather than $n$ because computing $M_D$ from the same data used up one degree of freedom (Lecture 12); dividing by $n$ would make $s_D$ too small on average. This is a **correction to an estimate**.

<p v-click>

- **$\sqrt{n}$, going from scores to means.** $s_M = s_D/\sqrt{n}$ converts the spread of *scores* into the spread of *means*. A mean of $n$ scores varies less than a single score, by exactly $\sqrt{n}$ (Lecture 8). This is **not a correction**; it is a different quantity.

</p>

:: right ::

<p v-click>

**Drug 2, in order:**

<Admonition title="Step A: the spread of scores" color="green-light" width="100%">

$s_D = \sqrt{SS/(n-1)} = \sqrt{36.08/9} = 2.00$ hours: how far a typical patient's difference sits from the mean difference. The $n - 1$ lives here.

</Admonition>

<Admonition title="Step B: the spread of means" color="green-light" width="100%">

$s_M = s_D/\sqrt{n} = 2.00/\sqrt{10} = 0.63$ hours: how far a sample's mean difference typically lands from the true one. The $\sqrt{n}$ lives here.

</Admonition>

</p>

<p v-click><StickyNote color="amber-light" title="In one line" width="100%">n − 1 corrects the estimate of the spread; √n shrinks it to the scale of means. Different jobs, and both happen in every t test.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Every standard error so far, on one slide

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Test</th><th>Signal (numerator)</th><th>Spread of scores</th><th>Standard error (spread of the null world)</th><th>Null world</th></tr></thead>
<tbody>
<tr><td><b>z test</b> (L10)</td><td>M − μ</td><td>σ, <b>known</b></td><td>SE = σ / √n</td><td>normal (z)</td></tr>
<tr><td><b>Single-sample <i>t</i></b> (L12)</td><td>M − μ</td><td>s, estimated (÷ n − 1)</td><td>s<sub>M</sub> = s / √n</td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Paired-samples <i>t</i></b> (L13)</td><td>M<sub>D</sub> − 0</td><td>s<sub>D</sub>, the SD of the difference scores</td><td>s<sub>M</sub> = s<sub>D</sub> / √n &nbsp;(n = number of pairs)</td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Independent-samples <i>t</i></b> (today)</td><td>(M₁ − M₂) − 0</td><td>s₁ and s₂: <b>two</b> sample SDs</td><td><b>?</b> &nbsp;(today's job: one SE built from both groups)</td><td><i>t</i>, df = n₁ + n₂ − 2</td></tr>
</tbody>
</table>

<p v-click>

- Every test statistic is **signal ÷ its row's standard error**. The null world is $t$ whenever the SE was estimated, and normal only when σ was known.
- Rows 2 and 3 are the same test; the paired version just runs it on difference scores. Today's whole job is to fill in the blank in the last row. We will come back to this table once we have.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Independent-samples *t* tests

:: content ::
- Compares the means of **two independent groups.**
- Each group contains different people, and each person experiences **only one** level of the independent variable (a between-subjects design).
- Example: quiz scores of students who studied with music vs. *other* students who studied in silence. No student is in both groups, so there are no pairs.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

Can you think of another study design where you would use an independent-samples *t* test? What about one from your own Data Write-Up?

</Admonition>

</p>

<p v-click><StickyNote color="amber-light" title="Two kinds of between-subjects comparisons" width="80%"><b>Experiments</b> with random assignment (front page vs. inside page of a newspaper) and <b>observational</b> comparisons of groups that already exist (seventh- vs. eighth-graders). Same test; very different causal claims.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Paired vs. independent samples

:: left ::
### Paired-samples *t* test
1. Compute a difference score for each participant.
2. Compute the mean of these difference scores.
3. Ask how far that mean is from 0, in standard errors.

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
The null world is a distribution of mean differences. We are really working with <b>one</b> sample of difference scores: its SE is based on one SD and one n.
</SpeechBubble>

</p>

:: right ::
### Independent-samples *t* test
1. Compute the mean of each group.
2. Compute the difference between the two group means.
3. Ask how far that difference is from 0, in standard errors.

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
The null world is a distribution of differences between <b>two</b> independent group means. Its SE is based on <b>both</b> groups' SDs and sample sizes.
</SpeechBubble>

<img src="/images/lecture10/fried_brain.png" alt="Fried brain" class="w-1/5 mx-auto mt-2"/>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Our example: a memory experiment

:: left ::

<div class="text-[15px] leading-snug">

Until now, every test compared **one set of scores** with a known value (μ, or 0). Now there is no known value, just **two separate samples**.

Friendly & Franklin (1980): **20 people**, each assigned to **one** of two conditions, learned a **40-word list** over several study-then-recall trials. Two separate groups of 10, each person measured once:

- **Standard free recall (SFR, n = 10):** the list reshuffled every trial (the usual procedure).
- **Recalled words first (n = 10):** a *different* 10 people; each new trial showed the words just recalled first, then the ones missed.

==Does seeing your recalled words first help you learn the rest?==

</div>

<div class="text-xs text-gray-500 mt-1">Friendly &amp; Franklin (1980), <i>Memory &amp; Cognition, 8</i>, 265–270; data via the carData R package.</div>

:: right ::

<img src="/images/lecture14/recall_dots.png" alt="Words recalled out of 40 for the two conditions, ten participants each" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The means differ by 6.3 words. Why can't we just conclude that the method helps?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Because means of 10 people bounce around. Two random groups of 10 given the *same* instructions could easily differ by several words. We need the null world for a difference between two means.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# The null world: differences between two group means

:: left ::

Imagine $H_0$ is true (both groups come from populations with the same mean), and we:

1. Randomly sample $n_1$ people for Group 1 and $n_2$ for Group 2.
2. Compute each group's mean and the difference, $M_1 - M_2$.
3. Repeat many times.

<p v-click><StickyNote color="amber-light" title="Two ns, two df lost" width="100%">The groups can be different sizes. And we estimate a standard deviation from <i>each</i> sample, so we lose one degree of freedom per group.</StickyNote></p>

:: right ::

<img src="/images/lecture14/indep_mean_diff_null.png" alt="Simulated null distributions of differences between two means" class="w-full mx-auto"/>

<p v-click>

- **Center 0**: under $H_0$, the means differ only by chance.
- **Spread**: the **standard error of the difference**, built from both SDs and both ns. More people in *either* group → narrower.
- **Shape**: *t*, with $df = n_1 + n_2 - 2$.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six steps for an independent-samples *t* test

:: content ::

==Used to compare the means of two separate groups (between-subjects designs).==

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>The question</th><th>Paired-samples <i>t</i> test</th><th>Independent-samples <i>t</i> test</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Who is being compared, and which test fits?</td><td>Two scores per participant → difference scores</td><td><b>Two groups, one score each</b>. DV numeric, roughly normal in each group, <b>similar variances</b>, independent observations</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>What are the two competing claims?</td><td>H₀: μ<sub>D</sub> = 0 &nbsp; H₁: μ<sub>D</sub> ≠ 0</td><td>H₀: μ₁ = μ₂ &nbsp; H₁: μ₁ ≠ μ₂ (or &lt;, &gt;)</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td>If H₀ were true, what results would we expect?</td><td>Center 0, s<sub>M</sub> = s<sub>D</sub>/√n, <i>t</i> with df = n − 1</td><td>Center 0, <b>SE<sub>difference</sub> from both SDs and both ns</b>, <i>t</i> with <b>df = n₁ + n₂ − 2</b></td></tr>
<tr><td><b>4.</b> Critical values</td><td>How extreme is extreme enough?</td><td colspan="2">α = .05, two-tailed → ±t<sub>crit</sub> for our df. Identical.</td></tr>
<tr><td><b>5.</b> Test statistic</td><td>How far is our result from what H₀ predicts, compared to chance?</td><td>t = M<sub>D</sub> / s<sub>M</sub></td><td>t = <b>(M₁ − M₂)</b> / SE<sub>difference</sub></td></tr>
<tr><td><b>6.</b> Decision</td><td>Is it past the cutoff? What do we conclude?</td><td colspan="2">Reject or fail to reject H₀, then say it in plain English. Identical.</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="What is new" width="90%">Only Step 3's standard error. It has to combine the noise from two separate samples, which takes three small steps (next slide).</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 3: the standard error, in three moves

:: content ::

1. **Pool the two variances.** Combine $s_1^2$ and $s_2^2$ into one ==pooled variance==, a weighted average (weighted by df, because the groups can have different sizes). Our best single estimate of the population variance.

$$s^2_{pooled} = \frac{df_1}{df_{total}}\, s^2_1 + \frac{df_2}{df_{total}}\, s^2_2, \qquad df_1 = n_1 - 1,\ df_2 = n_2 - 1,\ df_{total} = df_1 + df_2$$

<p v-click>

2. **Turn it into the variance of a mean, twice, and add.** Each group's mean has variance $s^2_{pooled}/n$ (the $s^2/n$ move from before). A *difference* between two independent means wobbles more than either mean alone, so the two add. The result is the variance of **mean differences**, not of scores: a squared standard error.

$$SE^2_{difference} = \frac{s^2_{pooled}}{n_1} + \frac{s^2_{pooled}}{n_2}$$

</p>

<p v-click>

3. **Take the square root:** $SE_{difference} = \sqrt{SE^2_{difference}}$. This is the spread of the null world. For one mean, $\sqrt{s^2/n}$ is just $s/\sqrt{n}$ written differently; we go through variances here because **variances add and SDs do not**.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Putting it all together

:: content ::

The three moves collapse into one formula:

$$
SE_{difference} =
\sqrt{
\frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}
{n_1 + n_2 - 2}
\left(
\frac{1}{n_1} + \frac{1}{n_2}
\right)
}$$

<div class="flex items-center gap-4">
<IceCream :size="70" mood="shocked" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem">Are you kidding me?</SpeechBubble>
</div>

<p v-click>

Good news: in practice you will almost never compute this by hand; R does it inside `t.test()`. What matters is what is inside: the two sample variances (**noise**) and the two sample sizes (**how much data**). The same two ingredients as every SE we have seen.

</p>

<p v-click><StickyNote color="amber-light" title="Equal n special case" width="80%">When n₁ = n₂ = n, the pooled variance is just the average of the two variances, and SE<sub>difference</sub> = √(2 s²<sub>pooled</sub> / n). That is the case we will do by hand.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The table, completed

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Test</th><th>Signal (numerator)</th><th>Spread of scores</th><th>Standard error (spread of the null world)</th><th>Null world</th></tr></thead>
<tbody>
<tr><td><b>z test</b> (L10)</td><td>M − μ</td><td>σ, <b>known</b></td><td>SE = σ / √n</td><td>normal (z)</td></tr>
<tr><td><b>Single-sample <i>t</i></b> (L12)</td><td>M − μ</td><td>s, estimated (÷ n − 1)</td><td>s<sub>M</sub> = s / √n</td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Paired-samples <i>t</i></b> (L13)</td><td>M<sub>D</sub> − 0</td><td>s<sub>D</sub>, the SD of the difference scores</td><td>s<sub>M</sub> = s<sub>D</sub> / √n &nbsp;(n = number of pairs)</td><td><i>t</i>, df = n − 1</td></tr>
<tr><td><b>Independent-samples <i>t</i></b> (today)</td><td>(M₁ − M₂) − 0</td><td>s₁ and s₂, pooled into s²<sub>pooled</sub></td><td><b>SE<sub>difference</sub> = √( s²<sub>pooled</sub>/n₁ + s²<sub>pooled</sub>/n₂ )</b></td><td><i>t</i>, df = n₁ + n₂ − 2</td></tr>
</tbody>
</table>

<p v-click>

- The new row follows the same pattern as the others: **spread of scores → spread of means**. The only differences are that the spread of scores comes from two samples (so it is pooled), and that a *difference* between two means collects noise from both (so the two variances-of-a-mean add).
- Signal ÷ noise, as always: $t = (M_1 - M_2) / SE_{difference}$.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Two more things to report: the CI and Cohen's d

:: left ::

Same recipes as for every test so far, with the independent-samples ingredients. We will compute both for the worked example:

$$CI = (M_1 - M_2) \pm t_{crit} \times SE_{difference}$$

$$d = \frac{M_1 - M_2}{s_{pooled}}, \qquad s_{pooled} = \sqrt{s^2_{pooled}}$$

- The CI is a range of plausible values for the **population difference** $\mu_1 - \mu_2$. Excludes 0 ⇔ the test rejects.
- For d, divide by the **pooled SD**, our best estimate of how much individual scores vary.

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Your Data Write-Up template computes d with the pooled SD. Why not the SD of one group, or of all scores lumped together?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

One group's SD ignores half the data. Lumping both groups together inflates the SD with the very difference you are measuring (the two means pull the scores apart). The pooled SD uses all the data while measuring spread *within* groups.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Let's test our intuitions

:: left ::

<Admonition title="Question 1" color="teal-light" width="100%">

We increase both sample sizes ($n_1$ and $n_2$) while the sample variances stay the same. What happens to $SE_{difference}$?

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

It **decreases**: $1/n_1 + 1/n_2$ shrinks. Larger samples → more precise means → a more precise difference. Just like every other SE.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Question 2" color="teal-light" width="100%">

Group 1 has $n_1 = 100$ and Group 2 has $n_2 = 10$. Which group's variance gets more weight in the pooled variance, and why?

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Group 1's: its weight is 99/108 vs. 9/108. A variance estimated from 100 scores is far more trustworthy than one from 10, so it should count for more.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Worked example: five people per group

:: left ::

To do it by hand, take **five people from each group** (all twenty come back in R):

<table class="compact-table text-sm">
<thead><tr><th>Standard order</th><th>X − M₁</th><th>(X − M₁)²</th><th>Recalled first</th><th>X − M₂</th><th>(X − M₂)²</th></tr></thead>
<tbody>
<tr><td>21</td><td>−6</td><td>36</td><td>30</td><td>−7</td><td>49</td></tr>
<tr><td>25</td><td>−2</td><td>4</td><td>38</td><td>1</td><td>1</td></tr>
<tr><td>25</td><td>−2</td><td>4</td><td>39</td><td>2</td><td>4</td></tr>
<tr><td>25</td><td>−2</td><td>4</td><td>39</td><td>2</td><td>4</td></tr>
<tr><td>39</td><td>12</td><td>144</td><td>39</td><td>2</td><td>4</td></tr>
<tr><td><b>M₁ = 27</b></td><td></td><td><b>SS₁ = 192</b></td><td><b>M₂ = 37</b></td><td></td><td><b>SS₂ = 62</b></td></tr>
</tbody>
</table>

<div class="text-sm text-gray-600 mt-1">Sum each group, divide by 5 for the mean; subtract the mean from each score; square; add up.</div>

:: right ::

<p v-click><Admonition title="Step 1: which test, and are the assumptions OK?" color="green-light" width="100%">

Two separate groups, one score each → **independent-samples *t* test**. Words recalled is numeric. Spreads: SDs 6.9 and 3.9, within a factor of two. n = 5 per group is tiny, so we lean on the population being roughly normal.

</Admonition></p>

<p v-click><Admonition title="Step 2: hypotheses" color="green-light" width="100%">

$H_0$: $\mu_1 = \mu_2$ (the method makes no difference). &nbsp; $H_1$: $\mu_1 \neq \mu_2$ (two-tailed).

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Signal, so far" width="100%">The means differ by 37 − 27 = <b>10 words</b>. Steps 3 to 5 ask: is 10 words a lot, relative to how much two groups of five would differ by chance?</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 3, move 1: each group's variance, then pool

:: left ::

Each group's variance is its SS divided by its df, $n - 1 = 4$:

- Standard order: $s_1^2 = 192 / 4 = 48.0$
- Recalled first: $s_2^2 = 62 / 4 = 15.5$

<p v-click>

Pool them. With equal n, the df-weighted average is just the average:

$$s^2_{pooled} = \frac{4 \times 48.0 + 4 \times 15.5}{8} = \frac{48.0 + 15.5}{2} = 31.75$$

</p>

:: right ::

<p v-click><Admonition title="What is this number?" color="green-light" width="100%">

31.75 is our single best estimate of how much **individual scores** vary within a group, using both groups' data. Its square root, $s_{pooled} = \sqrt{31.75} = 5.63$ words, is the pooled SD. We will need it again for Cohen's d.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Check the pooling" width="100%">31.75 sits between 15.5 and 48.0, as a pooled variance always must. If yours does not, something went wrong.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 3, moves 2 and 3: the standard error

:: left ::

**Move 2.** Turn the variance of scores into the variance of a *mean*, once per group, and add:

$$SE^2_{difference} = \frac{31.75}{5} + \frac{31.75}{5} = 6.35 + 6.35 = 12.7$$

<p v-click>

**Move 3.** Take the square root:

$$SE_{difference} = \sqrt{12.7} = 3.56 \text{ words}$$

</p>

<p v-click><Admonition title="The null world, described" color="green-light" width="100%">

If the method did nothing: differences between two group means would be centered on **0**, spread out with SD **3.56 words**, shaped like a ***t* distribution with df = 5 + 5 − 2 = 8**.

</Admonition></p>

:: right ::

<p v-click><Admonition title="What does 3.56 words mean?" color="green-light" width="100%">

It is how far apart two groups of five would **typically** land *if the method did nothing*: run the experiment over and over with no real effect, and the difference between the two means would usually be within about 3.6 words of zero. Our observed difference, 10 words, is going to be judged against that.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Compare" width="100%">The pooled SD (5.63) is the spread of <i>people</i>. The SE (3.56) is the spread of <i>differences between means</i>. Smaller, because means average out individual noise, and because there are five people behind each mean.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Steps 4, 5, and 6

:: left ::

<Admonition title="Step 4: cutoffs" color="green-light" width="100%">

df = 8, α = .05, two-tailed → `qt(0.975, 8)` → cutoffs **±2.306**. Small df, so farther out than 1.96.

</Admonition>

<p v-click><Admonition title="Step 5: the test statistic" color="green-light" width="100%">

$$t = \frac{M_2 - M_1}{SE_{difference}} = \frac{37 - 27}{3.56} = 2.81$$

The observed difference is 2.8 standard errors from what $H_0$ predicts.

</Admonition></p>

<p v-click><Admonition title="Step 6: decide" color="green-light" width="100%">

2.81 **is** beyond 2.306 → **reject $H_0$**. Route 2: p = .023 < .05. Seeing their recalled words first helped people learn the rest.

</Admonition></p>

:: right ::

<img src="/images/lecture14/null_world_recall5.png" alt="t distribution with df = 8, cutoffs ±2.306, and the observed t = 2.81" class="w-full mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Reading the picture" width="100%">If the method did nothing, a t this far from 0 would happen about 2.3% of the time. Rare enough that we conclude the method does something.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# The confidence interval, step by step

:: left ::

$$CI = (M_2 - M_1) \pm t_{crit} \times SE_{difference}$$

1. The observed difference: $37 - 27 = 10$ words.
2. The cutoff for our df: $t_{crit} = 2.306$ (the same number as Step 4).
3. The standard error: $3.56$ words (from Step 3).

<p v-click>

$$10 \pm 2.306 \times 3.56 = 10 \pm 8.2 \;\rightarrow\; \textbf{[1.8, 18.2] words}$$

</p>

:: right ::

<p v-click><Admonition title="What it means" color="green-light" width="100%">

The interval is **centered on our observed difference, 10 words**, and stretches 8.2 words either way: the plausible values for the **true** benefit run from about **2 to 18 words**. The observed difference is always inside its own CI; the question is whether **0** is inside too. Here it is not, which is the same verdict as the test (it always is: CI excludes 0 ⇔ reject $H_0$).

</Admonition></p>

<p v-click><Admonition title="Why so wide?" color="green-light" width="100%">

Two groups of five. The interval's half-width is $t_{crit} \times SE$, and both pieces are large when n is small: a far-out cutoff (2.306) times a big SE (3.56). We can say the method helps; we cannot say whether it helps by 2 words or by 18.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Cohen's d, step by step

:: left ::

$$d = \frac{M_2 - M_1}{s_{pooled}}$$

1. The observed difference: $10$ words.
2. The pooled **SD** (not the SE!): $s_{pooled} = \sqrt{31.75} = 5.63$ words, from Step 3.

<p v-click>

$$d = \frac{10}{5.63} = 1.78$$

</p>

<p v-click><StickyNote color="amber-light" title="SD, not SE" width="100%">d divides by how much <i>people</i> differ (5.63), not by how much <i>means</i> differ (3.56). That is why d does not shrink or grow with n, while t and the CI do.</StickyNote></p>

:: right ::

<p v-click><Admonition title="What it means" color="green-light" width="100%">

The two group means are **1.8 standard deviations apart**. By Cohen's conventions (0.2 small, 0.5 medium, 0.8 large) that is very large: the typical person in the recalled-first group remembered more words than almost everyone in the standard group.

</Admonition></p>

<p v-click><Admonition title="Putting the two together" color="green-light" width="100%">

**d says: big.** **The CI says: we are not sure how big.** Both are true. With five per group the estimate of the effect is itself noisy; with all twenty people (next slide) d comes out at 0.98, still large, and the interval narrows.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# All twenty people in R: t.test(..., var.equal = TRUE)

:: left ::

```r
recall <- read_csv("recall_data.csv")
sfr    <- filter(recall, condition == "SFR")
before <- filter(recall, condition == "Before")

t.test(before$correct, sfr$correct,
       var.equal = TRUE)
```

<div class="text-base">

- Two vectors of scores, one per group. No `paired = TRUE`: nothing is paired.
- `var.equal = TRUE`: pool the variances, as we did by hand.

</div>

<p v-click="2">

```r
# Cohen's d with the pooled SD
s_pooled <- sqrt((var(before$correct) +
                  var(sfr$correct)) / 2)
(mean(before$correct) - mean(sfr$correct)) /
  s_pooled                              # 0.98
```

<div class="text-xs text-gray-500">Equal n, so averaging the two variances is the pooled variance. With unequal n, weight by df (next slides).</div>

</p>

:: right ::

```text
	Two Sample t-test

data:  before$correct and sfr$correct
t = 2.1963, df = 18, p-value = 0.04141
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
  0.2736935 12.3263065
sample estimates:
mean of x mean of y
     36.6      30.3
```

<div v-click="1" class="text-base">

- **t = 2.20, df = 18**: the same test on all 20 people (by hand, five per group, we got t = 2.81 with df = 8). R put `before` first, so the difference is 36.6 − 30.3 = 6.3.
- **p-value = 0.041** < .05 → **reject $H_0$**.
- **95% CI**: the true benefit is plausibly **0.3 to 12.3 words**: narrower than the five-per-group interval, as more data should give. R prints seven decimals; report two.
- No SDs and no d: compute them yourself, as in your write-up.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: do musicians react faster to sounds?

:: left ::

36 students pressed a key as fast as they could when they heard a tone: **13 musicians** and **23 non-musicians**.

```text
	Two Sample t-test

data:  musician$rt and nonmusician$rt
t = -2.8598, df = 34, p-value = 0.007195
95 percent confidence interval:
 -134.34180  -22.72554
sample estimates:
mean of x mean of y
 165.6846  244.2183
```

<div class="text-xs text-gray-500 mt-1">Data: AudioVisual, Stat2Data R package (Cannon et al., <i>Stat2</i>).</div>

:: right ::

<img src="/images/lecture14/musicians_rt_dots.png" alt="Reaction times for musicians and non-musicians" class="w-10/12 mx-auto"/>

<p v-click><Admonition title="Question 1" color="teal-light" width="100%">

Where does df = 34 come from?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

13 + 23 − 2. Two groups, two SDs estimated, one df lost for each.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Musicians: the decision, and d with unequal n

:: left ::

<Admonition title="Question 2" color="teal-light" width="100%">

What is the decision, and what does the CI add?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

p = .007 < .05 → **reject $H_0$**: musicians were faster, by about 79 ms (244 − 166). The CI says the true advantage is plausibly anywhere from 23 ms to 134 ms: real, but not pinned down.

</Admonition></p>

:: right ::

<p v-click><Admonition title="Question 3" color="teal-light" width="100%">

Musicians: $s_1 = 55.8$ ms; non-musicians: $s_2 = 89.4$ ms. With unequal n, how do you get the pooled SD for Cohen's d?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Weight each variance by its df, then divide by the total df:

$s^2_{pooled} = (12 \times 55.8^2 + 22 \times 89.4^2) / 34 \approx 6{,}270$, so $s_{pooled} \approx 79$ ms and $d = 78.5 / 79 = 0.99$: a large effect. (Simply averaging the two variances gives 1.05: close here, wrong in general.)

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# One R detail: var.equal = TRUE

:: left ::

- R's default `t.test()` runs **Welch's *t* test**, a version that does **not** assume equal variances. Its df comes out as a decimal.
- When the two SDs are similar, Welch and the pooled test give nearly the same answer.
- When one SD is more than about twice the other (Lecture 12's rule of thumb), Welch is the right choice: just leave out `var.equal = TRUE`.
- In this course we add `var.equal = TRUE` so R's output matches what we compute by hand.

:: right ::

```text
	Welch Two Sample t-test

data:  musician$rt and nonmusician$rt
t = -3.2433, df = 33.555, p-value = 0.002674
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -127.76650  -29.30083
sample estimates:
mean of x mean of y
 165.6846  244.2183
```

<p v-click><StickyNote color="amber-light" title="How to tell which you ran" width="100%">The first line of the output says <b>Welch</b>, and the df is not a whole number. If you see that in your write-up output, add <code>var.equal = TRUE</code> and re-run. Same decision here either way.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# A published example: who talks more?

:: left ::

A bestselling book claimed women speak about **20,000 words a day** and men about **7,000**. Nobody had actually counted.

Mehl et al. (2007) had **396 college students** wear a recorder that sampled their speech for several days.

- **Women** (n = 210): $M = 16{,}215$ words/day, $s = 7{,}301$
- **Men** (n = 186): $M = 15{,}669$ words/day, $s = 8{,}633$

<p v-click><Admonition title="The result" color="green-light" width="100%">

$t(394) = 0.68$, $p = .50$, $d = 0.07$, 95% CI for women − men: **\[−1,029, 2,121] words per day**.

</Admonition></p>

<div class="text-xs text-gray-500 mt-1">Mehl, M. R., Vazire, S., Ramírez-Esparza, N., Slatcher, R. B., & Pennebaker, J. W. (2007). Are women really more talkative than men? <i>Science, 317</i>, 82.</div>

:: right ::

<img src="/images/lecture14/mehl_words_per_day.png" alt="Distributions of words per day for women and men" class="w-full mx-auto"/>

<p v-click><StickyNote color="amber-light" title="No arithmetic this time" width="100%">The numbers are too big to do by hand and that is not the point. The next two slides ask what the result <i>means</i>, in the style of the exam.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Talkativeness: the test and the decision

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which test is this, and what is its null world?

- **A)** A z test, because with n = 396 the t distribution is normal anyway.
- **B)** A paired-samples *t* test, because every woman was matched with a man.
- **C)** An independent-samples *t* test: two separate groups, so the null world is centered on 0, with a spread built from both SDs and both ns, and df = 210 + 186 − 2 = 394.
- **D)** A single-sample *t* test of the women against 20,000 words.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Nobody is measured twice, and σ is unknown. With df = 394 the t curve is nearly normal, but it is still a t test.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

$t(394) = 0.68$, $p = .50$. What can the researchers conclude?

- **A)** They fail to reject $H_0$: the data provide no evidence of a difference in talkativeness.
- **B)** Men and women talk exactly the same amount.
- **C)** The study was too small to conclude anything.
- **D)** Women talk more, just not significantly.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** (B) accepts $H_0$, which we never do. (D) treats a 546-word gap that is well inside chance as a finding. \(C): 396 people is not small; what the study could or could not detect is the next question.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Talkativeness: what the CI and d add

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

$d = 0.07$ and the 95% CI for the difference (women − men) is \[−1,029, 2,121] words per day. Which statement is best?

- **A)** The CI including 0 proves there is no difference.
- **B)** $d = 0.07$ means women say 7% more words than men.
- **C)** The null result is uninformative, as null results always are.
- **D)** The interval is centered on the observed difference (546 words) and also includes 0: any true difference is plausibly between about 1,000 words *fewer* and 2,100 *more* per day for women, out of roughly 16,000. The 20,000-vs-7,000 claim is ruled out.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** A CI is built around the observed difference, so that is always inside; a non-significant result is one whose CI contains 0 too. The claimed gap ($d \approx 1.6$) is far outside it.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

With these sample sizes, power to detect an effect as small as $d = 0.07$ is only about 0.11. Why is that not a problem for the study's conclusion?

- **A)** Because power only matters when a result is significant.
- **B)** Because the question was whether women talk *far* more than men ($d \approx 1.6$), and the study had plenty of power for a difference that big. What it could not detect is a tiny difference, which nobody had claimed.
- **C)** Because a sample of 396 is always enough.
- **D)** It is a problem: the study should not have been published.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Power is always relative to an effect size. Detecting d = 0.07 with 80% power would take about 3,250 people per group.

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
<b>Pixar before vs. after 2010 (Discussion 9)</b><br/>
Not significant: t(21) = 1.71, p = .10. But d = 0.72 and the CI runs from −2 to +22 points.<br/><br/>
<span class="text-indigo-700"><b>Lesson: "we could not tell."</b></span> The effect may well be real; 23 films was not enough to find out.
</div>

<div class="border-2 border-gray-300 rounded-lg p-3 text-sm mt-3">
<b>Mehl et al.: women vs. men</b><br/>
Not significant: t(394) = 0.68, p = .50. d = 0.07 and the CI sits tightly around 0.<br/><br/>
<span class="text-indigo-700"><b>Lesson: "if there is a difference, it is small."</b></span> The study answers the question.
</div>

:: right ::

<p v-click><Admonition title="Multiple choice 5" color="teal-light" width="100%">

The Pixar difference (after − before) was 10 points, 95% CI \[−2, 22]. Which statement is correct?

- **A)** The CI contains 0, so the true difference is 0.
- **B)** The CI contains 0 *and* the observed difference of 10 (it is centered on 10). Because 0 is inside, the result is not significant; because 22 is inside, a large effect is still plausible.
- **C)** The CI should not contain the observed difference.
- **D)** A CI that contains 0 is an error in the calculation.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Every CI is built around the observed difference, so it is always inside. What varies is whether 0 is inside too (not significant) or outside (significant), and how wide the interval is. "Fail to reject" on its own tells you almost nothing; the CI and d separate "could not tell" from "the effect is small."

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: the logic of the test

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A study compares sleep quality (1–10) in 30 students who use a screen before bed and 30 who read a paper book. Why does this test need a *pooled* variance when the paired test did not?

- **A)** There are two separate groups, so two sample SDs; the test needs one combined noise estimate. The paired test had one set of difference scores and one SD.
- **B)** Because the two groups have different means.
- **C)** Because pooling makes the result more likely to be significant.
- **D)** Because the paired test has no variance to estimate.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Pooling is bookkeeping for having two samples, nothing more. (B) describes the signal, not the noise. \(C) is backwards: pooling is about estimating noise honestly.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Which of these violates an assumption of the independent-samples *t* test?

- **A)** The 30 screen users were recruited as roommate pairs who keep the same hours.
- **B)** The two groups have different sizes.
- **C)** One group's mean is higher than the other's.
- **D)** Sleep quality was rated on a 1–10 scale.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Roommates' scores are not independent of each other. (B) is fine: df and the pooled variance handle unequal n. \(C) is the hypothesis, not a problem. (D) is a numeric outcome.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: reading the output

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

For the sleep study, R reports `t = -2.3, df = 58, p-value = 0.025`. What does df = 58 tell you?

- **A)** 58 participants in total.
- **B)** 60 participants in total: 30 + 30 − 2, one df spent estimating each group's SD.
- **C)** 58 pairs of participants.
- **D)** That the cutoff is ±1.96.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Two groups, two SDs estimated, two df lost. \(C) would be a paired design. (D): with df = 58 the cutoff is ±2.00, close to but not 1.96.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

Before running the test you notice the SDs are 1.1 (screen) and 3.9 (book). What should you do?

- **A)** Nothing; the *t* test is robust to everything.
- **B)** Switch to a paired-samples *t* test.
- **C)** Use the version of the test that does not assume equal variances (Welch's, R's default), because the larger SD is more than twice the smaller.
- **D)** Drop the group with the larger SD.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** Lecture 12's rule of thumb: SDs within a factor of two are fine; these are not. (B) needs two scores per person, which this design does not have.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting an independent-samples *t* test

:: content ::

**Template** (the same as for the other *t* tests)

Group 1 (*M* = X₁, *SD* = Y₁) scored \[higher/lower] than Group 2 (*M* = X₂, *SD* = Y₂), *t*(df) = T.TT, *p* = .PPP, *d* = D.DD, 95% CI \[LL, UL].

**Example**

Participants shown their recalled words first remembered more words (*M* = 36.60, *SD* = 5.34) than participants given the standard order (*M* = 30.30, *SD* = 7.33), *t*(18) = 2.20, *p* = .041, *d* = 0.98, 95% CI \[0.27, 12.33].

✅ State the means and SDs for **both** groups, and say which group was higher.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

A paper reports *t*(38) = 4.11 for an independent-samples test. How many participants were in the study?

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

df = n₁ + n₂ − 2 = 38, so n₁ + n₂ = 40 total. (For a paired test, t(38) would mean 39 pairs.)

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: independent-samples *t* tests

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A study compares reaction times of 25 gamers and 25 non-gamers: $M_1 = 310$ ms, $M_2 = 350$ ms, $SE_{difference} = 16$. What is t, and what are the df?

- **A)** t = 2.5, df = 24
- **B)** t = 40, df = 48
- **C)** t = 0.4, df = 49
- **D)** t = 2.5, df = 48

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** $t = (310 - 350)/16 = -2.5$ (sign aside), df = 25 + 25 − 2 = 48. Beyond ±2.01, so gamers were significantly faster.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Your friend runs the same gamer study but computes the SE from the gamers' SD only, ignoring the non-gamers. What is wrong?

- **A)** Nothing; one SD is enough.
- **B)** Both groups' means wobble, so the SE of the difference must include noise from both samples.
- **C)** She should have used the SD of all 50 scores together.
- **D)** She should have run a paired test.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Pooling uses both variances. \(C) lumps the groups together, inflating the SD with the group difference itself. (D) is wrong: different people in each group.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice (continued)

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

Two studies compare the same two conditions and find the same means and SDs. Study A has 10 per group; Study B has 100 per group. Which is true?

- **A)** Study B has a larger t and a larger d.
- **B)** Study A has a larger t because small samples are more variable.
- **C)** Study B has a larger t, a narrower CI, and the same d.
- **D)** Both studies have the same t; only the df differ.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Same difference and same pooled SD → same d. More data → smaller $SE_{difference}$ → larger t and narrower CI. (Lecture 11, one more time.)

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

R output for an independent-samples test reads: `t = 1.62, df = 58, p-value = 0.11`, 95% CI \[−0.4, 3.9]. Which conclusion is best?

- **A)** The groups are the same.
- **B)** The result is significant because t > 1.
- **C)** The study should have used a one-tailed test to get p < .05.
- **D)** We did not find a significant difference; the CI includes 0, so a true difference of zero is plausible, but so is a difference of 3.9.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Fail to reject, and read the CI for what remains plausible. (A) accepts $H_0$. \(C) is choosing the test after seeing the data: not allowed.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What changed from test to test? Still almost nothing.

:: content ::

<table class="compact-table text-sm">
<thead><tr><th></th><th>z test</th><th>Single-sample <i>t</i></th><th>Paired-samples <i>t</i></th><th>Independent-samples <i>t</i></th><th>ANOVA (next week)</th></tr></thead>
<tbody>
<tr><td><b>Step 1:</b> which test fits?</td><td>One mean, σ known</td><td>One mean, σ unknown</td><td>Two scores per participant</td><td>Two separate groups</td><td>Three or more groups</td></tr>
<tr><td><b>Step 3:</b> center</td><td>μ</td><td>μ</td><td>0</td><td>0</td><td>—</td></tr>
<tr><td><b>Step 3:</b> noise (SE)</td><td>σ/√n</td><td>s/√n</td><td>s<sub>D</sub>/√n</td><td>from both SDs and both ns</td><td>variance within groups</td></tr>
<tr><td><b>Step 3:</b> shape</td><td>z</td><td><i>t</i>, df = n − 1</td><td><i>t</i>, df = n − 1</td><td><i>t</i>, df = n₁ + n₂ − 2</td><td><i>F</i>, two dfs</td></tr>
<tr><td><b>Step 5:</b> signal ÷ noise</td><td>(M − μ)/SE</td><td>(M − μ)/s<sub>M</sub></td><td>M<sub>D</sub>/s<sub>M</sub></td><td>(M₁ − M₂)/SE<sub>diff</sub></td><td>between ÷ within</td></tr>
<tr><td><b>In R</b></td><td><code>z.test()</code></td><td><code>t.test(x, mu = )</code></td><td><code>t.test(x, y, paired = TRUE)</code></td><td><code>t.test(x, y, var.equal = TRUE)</code></td><td><code>aov()</code></td></tr>
<tr><td><b>Steps 2, 4, 6</b></td><td colspan="5">Identical every time: hypotheses about populations, a cutoff chosen in advance, compare and conclude in plain English. CI and effect size follow the same recipes.</td></tr>
</tbody>
</table>

<p v-click>

<div class="flex items-center gap-4 mt-3">
<IceCream :size="70" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">Four tests, one idea: how far is what we saw from what H₀ predicts, in units of noise? Exam 3 is about recognizing which situation you are in and reading the result correctly.</SpeechBubble>
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

**Independent-samples *t* test** — compares the means of two separate groups (between-subjects). $t = (M_1 - M_2)/SE_{difference}$, df = n₁ + n₂ − 2.

</div>
<div>

**Pooled variance** — the df-weighted average of the two groups' variances: one estimate of how much individual scores vary. Its square root is the pooled SD used in Cohen's d.

</div>
<div>

**Standard error of the difference** — $\sqrt{s^2_{pooled}/n_1 + s^2_{pooled}/n_2}$. Noise from both groups' means, added. Shrinks as either n grows.

</div>
<div>

**Equal-variance assumption** — the two groups should have similar spreads. `var.equal = TRUE` pools them; leaving it out gives Welch's test, which does not assume this.

</div>
<div>

**Two kinds of null result** — a wide CI with a sizable d ("could not tell") vs. a narrow CI around 0 with a tiny d ("any difference is small"). Report the CI and d so readers can tell which you have.

</div>
<div>

**Reporting** — both groups' M and SD, direction in words, *t*(df), *p*, *d*, 95% CI for the difference.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Next class: Exam 3 Review (covers Lectures 11–14). Data Write-Up #1 is due Monday at 11:59 p.m.
