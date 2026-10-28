---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 13
exportFilename: ps211_fall2026_lecture13
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 13: Paired-Samples *t* Tests & Reporting Results in APA Style

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- ==Data Write-Up #1== (t-test-based) is due **Monday, November 9** at 11:59 p.m.
  - **Tomorrow in Discussion 9** you'll run your *t* test, make your figure, and interpret your results, so today ends with a preview of the independent-samples *t* test.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Coming up:
  - Thursday (11/5): Lecture 14 — Independent-samples *t* tests (in R)
  - Tuesday (11/10): Exam 3 Review
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

**Single-sample *t* test** — compares a sample mean to a population mean when **σ is unknown**: the z test with the sample's s standing in for σ.

</div>
<div>

**Estimated standard error** — $s_M = s/\sqrt{n}$. Then $t = (M - \mu)/s_M$: how many estimated SEs the sample mean is from what $H_0$ predicts.

</div>
<div>

**t distribution** — the null world for t. Heavier tails than z (because s is only an estimate), one curve per **degrees of freedom** (df = n − 1). Cutoffs from `qt()`, p values from `pt()` or `t.test()`.

</div>
<div>

**Assumptions of parametric tests** — normality (the CLT usually covers it), equal variance, independence, no extreme outliers.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Today: the same test for <b>before-and-after</b> designs, then how to write any result up the way journals (and your Data Write-Up) expect.</SpeechBubble>
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

Thursday's sleep study, **Drug 1** (the other form of the sedative): the same 10 patients' extra hours of sleep, tested against μ = 0.

```text
t = 1.3257, df = 9, p-value = 0.2176
95 percent confidence interval:
 -0.5297804  2.0297804
mean of x 
     0.75 
```

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

With α = .05, two-tailed, what is the best conclusion?

- **A)** There is a 22% chance that $H_0$ is true.
- **B)** Drug 1 significantly increased sleep, by 0.75 hours.
- **C)** The test is invalid because n = 10 is too small.
- **D)** We did not find evidence that Drug 1 changes sleep; 0 is inside the CI.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** p = .22 > .05 and the CI \[−0.53, 2.03] contains 0. (A) misreads p. \(C): small n is exactly what df = 9 and the wider cutoff (±2.26) account for. Drug 2 worked; Drug 1, we cannot tell.

</Admonition>

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Two single-sample *t* tests: n = 10 and n = 100. Which needs a **larger** t to reject $H_0$?

- **A)** n = 100: more data, stricter standards.
- **B)** Neither; the cutoff is always ±1.96.
- **C)** n = 10: with df = 9 the t distribution has heavier tails, so the cutoff is farther from 0.
- **D)** n = 10: small samples have larger standard errors.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** df = 9 → ±2.26; df = 99 → ±1.98. (D) is true but separate: a larger SE makes t *smaller*, a different reason small studies struggle to reject.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Three types of *t* tests

:: content ::
All three ask the same question: did these means come from the same population? They differ in **where the two means come from**.

1. **Single-sample *t* test** – a sample mean vs. a known population mean, σ unknown.

<div class="mt-0 w-full flex justify-center">
<div class="bg-blue-100 border-2 border-blue-300 rounded-lg shadow-md p-3 transform">
  Last Thursday: the sleeping drug, body temperature. (The drug's "extra hours of sleep" were difference scores already: drug night − no-drug night.)
</div>
</div>

<br>

<p v-click>

2. **Paired-samples *t* test** – two measurements of the **same** participants (within-subjects design). ==Today.==
3. **Independent-samples *t* test** – two **different** groups of participants (between-subjects design). Preview today, details Thursday.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Between- vs. within-subjects designs (Lecture 2)

:: left ::
### Within-subjects
- Each participant experiences **all** levels of the independent variable.
- Comparisons are made *over time or across conditions* for the same people.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

What is an advantage of a within-subjects design?

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Every participant is their own control. Differences between people (talent, mood, age) cancel out, which removes a huge source of noise. Fewer participants needed.

</Admonition></p>

:: right ::
### Between-subjects
- Each participant experiences **only one** level of the independent variable.
- Comparisons are made *between different people*.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

What is an advantage of a between-subjects design?

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

No carry-over: nobody practices the task, gets tired, or guesses the hypothesis from seeing both conditions. Sometimes it is the only option (you cannot be both a first-year and a senior at once).

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which *t* test should I use?

:: content ::
- **Within-subjects design** (each participant measured twice) → ==paired-samples *t* test==
- **Between-subjects design** (two separate groups) → ==independent-samples *t* test==

<p v-click>

- For the paired test, the first move is always the same: compute a **difference score** for each participant (after − before, Condition 1 − Condition 2). Then the test is a single-sample *t* test on those differences.

</p>

<p v-click><StickyNote color="amber-light" title="The 'participant' need not be a person" width="80%">A film rated on two websites, a candy tasted by the same panel twice, a city measured in two years: if the same unit produces both scores, the scores are paired.</StickyNote></p>

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="70" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Two designs, two tests, one question to ask first: does each unit have <b>two</b> scores, or does each score come from a <b>different</b> unit?</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Our example: Fandango vs. IMDb (back to Lecture 7)

:: left ::

- In 2015, FiveThirtyEight's Walt Hickey noticed that **Fandango**, which sells movie tickets, seemed to give almost every film 4 or 5 stars.
- He pulled every film with at least 30 Fandango reviews (**146 films**) and compared its Fandango stars with its ratings on other sites.
- In Lecture 7 we looked at the *shape* of Fandango's distribution. Today we can **test** the claim: *are the same films rated higher on Fandango than on IMDb?*

<div class="text-xs text-gray-500 mt-2">Data: Hickey, W. (2015). Be suspicious of online movie ratings, especially Fandango's. <i>FiveThirtyEight</i>. IMDb's 10-point ratings divided by 2 to match Fandango's 5-star scale.</div>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What is the "participant" here? Is this a within- or between-subjects comparison?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Each **film** is a participant, and each film has *two* scores: one from Fandango and one from IMDb. Same units, measured twice → **within-subjects** → paired-samples *t* test.

</Admonition></p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Why not just compare the average Fandango rating with the average IMDb rating as two separate groups?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Because the films are the same. A great film is rated high on both sites and a bad one low on both; that film-to-film variation is noise we can subtract out by looking at each film's *difference*.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# A psychology example: the Stroop task

:: left ::

<img src="/images/lecture13/stroop_task.png" alt="Congruent and incongruent Stroop items: color words printed in matching or mismatching ink" class="w-full mx-auto"/>

<div class="text-sm mt-2">

**Stroop interference**: people are slower to name the ink color when the word is an *incongruent* color name (RED printed in blue) than when it is *congruent* (RED in red). Try the right-hand panel out loud.

</div>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

How would you design this study so that a paired-samples *t* test is the right analysis?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- Have **each participant** do both conditions (counterbalanced order).
- Record each person's mean reaction time in each condition, then compute one difference score per person (incongruent − congruent).
- Test whether the mean of those differences is different from 0.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Why within-subjects here?" width="100%">People differ enormously in baseline speed. Comparing each person to themselves removes that difference entirely, so even a modest interference effect is easy to detect.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# A distribution of mean *differences*

:: left ::

<div class="flex items-center gap-4 mb-2"><span class="text-lg"><b>Another distribution!</b></span><img src="/images/lecture10/ohno.jpg" alt="Oh no" class="w-2/5 rounded-lg"/></div>

The comparison distribution for a paired test is a **distribution of mean differences**. Imagine $H_0$ is true (the sites do not differ) and we:

1. Randomly sample n films.
2. Compute each film's difference score (Fandango − IMDb).
3. Compute the **mean** of those n differences.
4. Repeat many times.

:: right ::

<img src="/images/lecture13/mean_diff_null_n5_n146.png" alt="Simulated null distributions of mean differences for n = 5 and n = 146" class="w-full mx-auto"/>

<p v-click>

- **Center 0**: if the sites did not differ, mean differences scatter around zero.
- **Spread**: $s_M = s_D/\sqrt{n}$, where $s_D$ is the SD of the difference scores.
- **Shape**: a *t* distribution with df = n − 1, since we estimate $s_D$ from the sample.
- Sound familiar? It is the single-sample *t* test's null world, for difference scores, with μ = 0.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six steps for a paired-samples *t* test

:: content ::

==Used to compare two measurements of the same participants (within-subjects designs).==

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>The question</th><th>Single-sample <i>t</i> test</th><th>Paired-samples <i>t</i> test</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Who is being compared, and which test fits?</td><td>One sample mean vs. a population mean, σ unknown</td><td><b>Two scores per participant</b>; we test the <b>difference scores</b> (numeric, roughly normal, no wild outliers)</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>What are the two competing claims?</td><td>H₀: μ = μ₀ &nbsp; H₁: μ ≠ μ₀</td><td>H₀: μ<sub>D</sub> = 0 (no average difference) &nbsp; H₁: μ<sub>D</sub> ≠ 0 (or &lt;, &gt;)</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td>If H₀ were true, what results would we expect?</td><td>Center μ, s<sub>M</sub> = s/√n, <i>t</i> with df = n − 1</td><td>Center <b>0</b>, s<sub>M</sub> = <b>s<sub>D</sub></b>/√n, <i>t</i> with df = n − 1 (n = number of <b>pairs</b>)</td></tr>
<tr><td><b>4.</b> Critical values</td><td>How extreme is extreme enough?</td><td colspan="2">α = .05, two-tailed → ±t<sub>crit</sub> for our df. Identical.</td></tr>
<tr><td><b>5.</b> Test statistic</td><td>How far is our result from what H₀ predicts, compared to chance?</td><td>t = (M − μ) / s<sub>M</sub></td><td>t = (<b>M<sub>D</sub></b> − 0) / s<sub>M</sub></td></tr>
<tr><td><b>6.</b> Decision</td><td>Is it past the cutoff? What do we conclude?</td><td colspan="2">Reject or fail to reject H₀, then say it in plain English. Identical.</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="The only real change" width="90%">Turn two columns of scores into one column of differences; then it is a single-sample t test against μ = 0.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Worked example: five films, by hand

:: left ::

To see the machinery, start with five films most of you know:

<table class="compact-table text-sm">
<thead><tr><th>Film</th><th>IMDb (÷2)</th><th>Fandango</th></tr></thead>
<tbody>
<tr><td>Avengers: Age of Ultron</td><td>3.90</td><td>5.0</td></tr>
<tr><td>Inside Out</td><td>4.30</td><td>4.5</td></tr>
<tr><td>Jurassic World</td><td>3.65</td><td>4.5</td></tr>
<tr><td>Minions</td><td>3.35</td><td>4.0</td></tr>
<tr><td>Mad Max: Fury Road</td><td>4.15</td><td>4.5</td></tr>
</tbody>
</table>

<p v-click><Admonition title="Steps 1 and 2" color="green-light" width="100%">

**1.** Five films, each rated on both sites → paired-samples *t* test on the difference scores. Ratings are numeric; n = 5 is tiny, so we lean on the differences being roughly normal.

**2.** $H_0$: $\mu_D = 0$ (same ratings on both sites). &nbsp; $H_1$: $\mu_D \neq 0$.

</Admonition></p>

:: right ::

<img src="/images/lecture13/fandango_five_films.png" alt="Fandango and IMDb ratings for five films" class="w-11/12 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Direction" width="100%">We will compute Fandango − IMDb, so a positive difference means Fandango rated the film higher. Either direction works, as long as you are consistent and remember which you chose.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Step 3: describe the comparison distribution

:: left ::

Under $H_0$ the center is 0. We estimate the spread from the difference scores, just as in a single-sample *t* test:

<table class="compact-table text-sm">
<thead><tr><th>Film</th><th>IMDb</th><th>Fandango</th><th>D</th><th>D − M<sub>D</sub></th><th>(D − M<sub>D</sub>)²</th></tr></thead>
<tbody>
<tr><td>Avengers</td><td>3.90</td><td>5.0</td><td>1.10</td><td>0.47</td><td>0.2209</td></tr>
<tr><td>Inside Out</td><td>4.30</td><td>4.5</td><td>0.20</td><td>−0.43</td><td>0.1849</td></tr>
<tr><td>Jurassic World</td><td>3.65</td><td>4.5</td><td>0.85</td><td>0.22</td><td>0.0484</td></tr>
<tr><td>Minions</td><td>3.35</td><td>4.0</td><td>0.65</td><td>0.02</td><td>0.0004</td></tr>
<tr><td>Mad Max</td><td>4.15</td><td>4.5</td><td>0.35</td><td>−0.28</td><td>0.0784</td></tr>
<tr><td colspan="3" style="text-align:right"><b>Mean difference M<sub>D</sub></b></td><td><b>0.63</b></td><td style="text-align:right"><b>SS</b></td><td><b>0.533</b></td></tr>
</tbody>
</table>

:: right ::

<p v-click>

- Variance of the differences: $s_D^2 = SS/(n-1) = 0.533/4 = 0.133$
- SD of the differences: $s_D = \sqrt{0.133} = 0.365$
- Standard error of the mean difference:

$$s_M = \frac{s_D}{\sqrt{n}} = \frac{0.365}{\sqrt{5}} = 0.163$$

</p>

<p v-click><StickyNote color="amber-light" title="So the null world is..." width="100%">a t distribution with df = 4, centered on 0, with spread 0.163. "If the sites did not differ, mean differences of 5 films would typically land within about 0.16 stars of zero."</StickyNote></p>

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

df = n − 1 = 4, α = .05, two-tailed → `qt(0.975, 4)` → **±2.776**. (Five pairs is a tiny sample, so the cutoff is far out.)

</Admonition>

<p v-click><Admonition title="Step 5: test statistic" color="green-light" width="100%">

$$t = \frac{M_D - 0}{s_M} = \frac{0.63}{0.163} = 3.86$$

The mean difference is 3.86 standard errors above zero.

</Admonition></p>

<p v-click><Admonition title="Step 6: decision" color="green-light" width="100%">

3.86 is beyond 2.776 → **reject $H_0$**. Route 2: `2 * pt(-3.86, 4)` = .018 < .05. Even with five films, Fandango's ratings are significantly higher than IMDb's.

</Admonition></p>

:: right ::

<img src="/images/lecture13/null_world_fandango_t4.png" alt="The t distribution with df = 4, cutoffs, and the observed t" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Suppose we had subtracted the other way (IMDb − Fandango). What changes?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Only the sign: $M_D = -0.63$, $t = -3.86$, same p, same decision. The conclusion ("Fandango higher") is the same; just read the direction correctly.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Confidence interval and effect size for a paired test

:: left ::

Both work as before, now built around the **mean difference**:

$$CI = M_D \pm t_{crit} \times s_M$$

$$d = \frac{M_D}{s_D}$$

- The CI is a range of plausible values for the **population mean difference**, $\mu_D$. If it excludes 0, the test rejects.
- For d, divide by the SD of the **difference scores**: how many SDs of difference is the average difference?

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Compute both for the five films: $M_D = 0.63$, $s_D = 0.365$, $s_M = 0.163$, $t_{crit} = 2.776$.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

CI: $0.63 \pm 2.776 \times 0.163 = 0.63 \pm 0.45$ → **\[0.18, 1.08]** stars. Excludes 0. Wide, because n = 5.

$d = 0.63/0.365 = 1.73$: a very large effect.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Reading the interval" width="100%">Fandango's bonus is plausibly anywhere from a fifth of a star to a full star. Five films cannot pin it down. 146 films can: next slide.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# All 146 films in R: t.test(..., paired = TRUE)

:: left ::

```r
# films: one row per film, with
# fandango_stars and imdb_stars (IMDb / 2)
t.test(films$fandango_stars,
       films$imdb_stars,
       paired = TRUE)
```

<div class="text-base">

- Give R the two columns and `paired = TRUE`. R computes the differences (first minus second).
- Forget `paired = TRUE` and R treats the 292 ratings as two unrelated groups: the wrong test for this design.

</div>

<p v-click="2">

```r
# Cohen's d for a paired test
d_scores <- films$fandango_stars - films$imdb_stars
mean(d_scores) / sd(d_scores)   # 1.54
```

</p>

:: right ::

```text
	Paired t-test

data:  films$fandango_stars and films$imdb_stars
t = 18.667, df = 145, p-value < 2.2e-16
alternative hypothesis: true mean difference is not equal to 0
95 percent confidence interval:
 0.6442555 0.7968404
sample estimates:
mean difference 
      0.7205479 
```

<div v-click="1" class="text-base">

- **t = 18.67, df = 145**: the mean difference is 18.7 SEs above 0; 146 pairs → 145 df.
- **p-value < 2.2e-16**: the smallest number R prints. Report *p* < .001.
- **95% CI**: films score **0.64 to 0.80 stars** higher on Fandango, on average. Nowhere near 0.
- **mean difference** = 0.72 stars.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# What the 146 difference scores look like

:: left ::

<img src="/images/lecture13/fandango_diff_hist.png" alt="Histogram of Fandango minus IMDb difference scores" class="w-full mx-auto"/>

:: right ::

- Only **10 of 146** films scored lower on Fandango than on IMDb. The typical film got about three-quarters of a star more.
- $d = 1.54$: the average difference is one and a half SDs of difference. Enormous.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Five films gave t = 3.86 and a CI of \[0.18, 1.08]. All 146 gave t = 18.67 and \[0.64, 0.80]. The effect size barely changed (1.73 vs. 1.54). What did the extra films buy us?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**Precision.** The SE fell from 0.163 to 0.039, so the interval is a quarter as wide and the t statistic is five times larger. Lecture 11 again: n changes the test statistic and the CI, not the effect size.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# What if you forget paired = TRUE?

:: left ::

Same 292 ratings, but R now treats them as two unrelated groups of films:

```r
t.test(films$fandango_stars, films$imdb_stars,
       var.equal = TRUE)      # no paired = TRUE
```

```text
	Two Sample t-test

t = 12.053, df = 290, p-value < 2.2e-16
95 percent confidence interval:
 0.6029 0.8382
sample estimates:
mean of x mean of y 
 4.089041  3.368493 
```

<p v-click>

- The means are identical, so the difference is still 0.72. But $t$ fell from **18.67 to 12.05**, the CI is wider, and df doubled to 290 (R thinks there are 292 films).

</p>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Why is the paired test so much stronger when the means are the same either way?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

A great film is rated high on both sites and a bad film low on both. The independent test counts that film-to-film variation as noise in its SE. The paired test subtracts it out: each film is compared only to itself, so the SE comes from how much the *differences* vary (s<sub>D</sub> = 0.47), not from how much films differ from one another.

</Admonition></p>

<p v-click><StickyNote color="green-light" title="In Discussion 9" width="100%">You run exactly this contrast on the Pixar data: Rotten Tomatoes vs. Metacritic for the same 23 films. Paired: t = 5.20 with df = 22, p &lt; .001. Wrong (independent) test: t = 2.36 with df = 44, p = .023. Same means, half the t.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice: does Fandango round up?

:: left ::

Hickey's second finding: Fandango's page showed each film's stars **and**, hidden in the page's code, its actual average rating. The stars seemed to always round *up*.

<img src="/images/lecture13/fandango_roundup.png" alt="Stars displayed minus actual rating for 146 films" class="w-10/12 mx-auto"/>

```text
	Paired t-test: fandango_stars and actual_rating
t = 19.299, df = 145, p-value < 2.2e-16
95 percent confidence interval:
 0.2188638 0.2688075
sample estimates:
mean difference 
      0.2438356 
```

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

With your neighbors: (1) Why is this a paired test? (2) State $H_0$ and $H_1$ in words. (3) Step 6: what do you decide, by Route 2, and what does it mean?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

(1) Each film supplies both numbers: the stars shown and its actual rating. Same unit, two scores.

(2) $H_0$: on average, stars shown = actual rating ($\mu_D = 0$). $H_1$: they differ.

(3) p < .001, so reject $H_0$. Displayed stars are significantly higher than the actual ratings: on average by 0.24 stars (95% CI \[0.22, 0.27]), and never lower for a single film. Fandango was rounding up.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Afterward" width="100%">FiveThirtyEight published this in October 2015. Fandango said the rounding was a bug and fixed it.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: paired-samples *t* tests

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Twenty students study a word list and take a recall test, sleep 8 hours, then take an equivalent test the next day. On average they recall **2.1 more words** after sleeping. A paired *t* test on the 20 difference scores gives $t = 2.40$ with df = 19, $p = .027$. Which statement is correct?

- **A)** Students recalled significantly more words after sleep, by about 2 words on average.
- **B)** df should be 38, because there are 40 test scores.
- **C)** We cannot reject $H_0$ because t is less than 2.776.
- **D)** The result proves that sleep improves memory for everyone.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** df = number of *pairs* − 1 = 19, not 38 (B). The cutoff for df = 19 is ±2.09, not 2.776 \(C). (D) overclaims: the test is about the *mean* difference, and this design has no control group for the retest.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Which of these is **not** a paired design?

- **A)** Each participant's anxiety before and after a 6-week mindfulness course.
- **B)** Reaction times of 30 students who drank coffee vs. 30 other students who drank water.
- **C)** Each candy's win percentage in 2017 and again in a 2024 rerun of the matchups.
- **D)** Each professor's evaluation score in a lower-level and an upper-level course.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Different people in the two groups: nobody has two scores, so there is nothing to pair. That is an independent-samples design (Thursday). In A, C, and D the same unit supplies both scores.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

You have a result. Now...
# Reporting results in APA style

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What is APA style, and why use it?

:: content ::

- **APA** = *American Psychological Association*. Its style guide sets a standard format for reporting statistics, so that any reader can see **what test you ran, what you found, and how sure you are** in one sentence.
- Required by nearly every psychology journal, and by your Data Write-Up.

<p v-click>

<StickyNote color="amber-light" title="APA style tells us how to..." width="70%">• write numbers and statistics (italics, decimals, leading zeros)<br/>• report the result of a test (<i>t</i>, <i>z</i>, <i>F</i>, df, <i>p</i>)<br/>• report effect sizes and confidence intervals</StickyNote>

</p>

<p v-click><StickyNote color="green-light" title="Why this matters for you" width="70%">Part 5 of Data Write-Up #1 is one APA-style sentence. Today's templates are exactly what you will use tomorrow in Discussion 9.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Always include these elements

:: content ::

<table class="compact-table text-base">
<thead><tr><th>Element</th><th>What it tells the reader</th><th>Example</th></tr></thead>
<tbody>
<tr><td><b>Descriptive statistics</b></td><td>What the data looked like: mean and SD for each group or condition</td><td><i>M</i> = 4.09, <i>SD</i> = 0.54</td></tr>
<tr><td><b>Test statistic and df</b></td><td>Which test you ran and how big the sample was</td><td><i>t</i>(145)</td></tr>
<tr><td><b>Test value</b></td><td>Signal ÷ noise</td><td><i>t</i>(145) = 18.67</td></tr>
<tr><td><b>p value</b></td><td>Probability of a result this extreme if H₀ were true</td><td><i>p</i> = .004, or <i>p</i> &lt; .001</td></tr>
<tr><td><b>Direction</b></td><td>Which group or condition was higher: a plain-English verb</td><td>"were rated higher on Fandango than..."</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Strongly recommended, and required in this course" width="100%"><b>Effect size</b> (<i>d</i> = 1.54) tells the reader how big. <b>Confidence interval</b> (95% CI [0.64, 0.80]) tells them how precise. Most journals now require both. There is no reason to leave them out.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Formatting rules (APA 7th edition)

:: content ::

- **Italicize** statistical symbols: *t*, *z*, *p*, *M*, *SD*, *F*, *r*, *d*. Not the numbers, not the df.
- **Two decimal places** for test statistics, means, SDs, effect sizes, and CI bounds (unless the scale calls for more or fewer).
- ***p* values:** three decimal places with **no leading zero**, because p cannot exceed 1: *p* = .027, not *p* = 0.027. Below .001, write *p* < .001.
- **Confidence intervals** in brackets: 95% CI \[0.64, 0.80].
- **Degrees of freedom** in parentheses right after the symbol: *t*(145).
- **Order** within the sentence: statistic with df, *p*, *d*, CI. Commas between them.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Spot the errors: "The t-test was significant (T = 18.667, P = 0.000, DF = 145)."

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Lowercase italic *t* and *p*; df in parentheses after *t*; two decimals; *p* is never exactly 0, write *p* < .001; and no descriptives, direction, *d*, or CI anywhere. → *t*(145) = 18.67, *p* < .001.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a *z* test

:: content ::

**Template**

Group (*M* = X, *SD* = Y) was \[higher/lower/did not differ] than the population (μ = Z), *z* = Z.ZZ, *p* = .PPP, *d* = D.DD, 95% CI \[LL, UL].

**Example (Lecture 9's dating profiles)**

Rhode Island dating profiles (*M* = 2.84, *n* = 30) were rated significantly higher than profiles nationwide (μ = 2.50, σ = 0.83), *z* = 2.24, *p* = .025, *d* = 0.41, 95% CI \[2.54, 3.14].

<p v-click>

- No **degrees of freedom** for a z test: it uses the known population σ rather than an estimate, so there is no df.
- Here *d* uses σ = 0.83 and the CI is the z-based interval, M ± 1.96 × SE (SE = 0.152). We report σ because that is what the test used; the sample *SD* goes in too when you have it.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a single-sample *t* test

:: content ::

**Template**

Sample (*M* = X, *SD* = Y) was \[higher/lower/did not differ] than the comparison value (Z), *t*(df) = T.TT, *p* = .PPP, *d* = D.DD, 95% CI \[LL, UL].

**Example (Lecture 12)**

The mean oral temperature of 130 healthy adults (*M* = 98.25°F, *SD* = 0.73) was significantly lower than the textbook value of 98.6°F, *t*(129) = −5.45, *p* < .001, *d* = −0.48, 95% CI \[98.12, 98.38].

<p v-click>

- State the **comparison value** (98.6) and the sample's **M and SD**.
- The CI here is for the population **mean** (98.12 to 98.38), which is what R's `t.test()` reports.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a paired-samples *t* test

:: content ::

**Template**

Scores were \[higher/lower] in Condition 1 (*M* = X₁, *SD* = Y₁) than in Condition 2 (*M* = X₂, *SD* = Y₂), *t*(df) = T.TT, *p* = .PPP, *d* = D.DD, 95% CI \[LL, UL].

**Example (today)**

Films were rated higher on Fandango (*M* = 4.09, *SD* = 0.54) than on IMDb (*M* = 3.37, *SD* = 0.48), *t*(145) = 18.67, *p* < .001, *d* = 1.54, 95% CI \[0.64, 0.80].

<p v-click>

- Report the **M and SD of both conditions**, not just the difference, so readers can see the raw numbers.
- The CI is for the **mean difference** (0.64 to 0.80 stars), so it should exclude 0 whenever the test rejects.
- *d* = mean difference ÷ SD of the differences.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# APA practice

:: left ::

<Admonition title="Practice 1: rewrite in APA style" color="teal-light" width="100%">

"Patients on Drug 2 slept 2.33 extra hours on average (s.d.=2.00) which was significantly more than zero. The T test was significant (P = .005; t = 3.68; DF=9). Cohen's D = 1.16 and the 95% confidence interval was (0.90 , 3.76)."

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Patients given Drug 2 slept significantly longer than on nights without it (*M* = 2.33 extra hours, *SD* = 2.00; μ = 0), *t*(9) = 3.68, *p* = .005, *d* = 1.16, 95% CI \[0.90, 3.76].

*Fixed:* italic symbols; *SD* not s.d.; *t*(df) = value; *p* with no leading zero; standard order (*t*, *p*, *d*, CI); brackets for the CI; one sentence.

</Admonition></p>

:: right ::

<p v-click><Admonition title="Practice 2: write the sentence" color="teal-light" width="100%">

Fandango's rounding: stars shown (*M* = 4.09, *SD* = 0.54) vs. actual rating (*M* = 3.85, *SD* = 0.50), *t*(145) = 19.30, *p* < .001, *d* = 1.60, 95% CI \[0.22, 0.27]. Write the APA sentence.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The stars Fandango displayed (*M* = 4.09, *SD* = 0.54) were significantly higher than the films' actual average ratings (*M* = 3.85, *SD* = 0.50), *t*(145) = 19.30, *p* < .001, *d* = 1.60, 95% CI \[0.22, 0.27].

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Then interpret" width="100%">The APA sentence reports. The next sentence <i>interprets</i>: "On average, Fandango rounded ratings up by about a quarter of a star, and no film was rounded down." That is Part 7 of your write-up.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why does a standardized style matter?

:: content ::

- **Readers find the key numbers instantly.** Every paper puts the test, df, *p*, effect size and CI in the same place, in the same order. A reader can scan a results section in seconds.
- **Nothing gets left out.** The template forces you to report the sample size (df), the direction, how big (*d*) and how precise (CI), not just "it was significant."
- **Results can be checked.** From *t*(145) = 18.67 a reader can recompute *p* and judge the sample size; from *d* and the CI they can judge whether the effect matters.
- **Results can be compared and combined.** Meta-analyses pool hundreds of studies, which only works because they all report the same quantities the same way.
- **It signals care.** Sloppy reporting makes readers doubt the analysis behind it.

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">A warning: we <b>WILL</b> be sticklers about you sticking to this <b>EXACT</b> style in your Data Write-Up. Typos <b>WILL</b> be penalized. Make sure you hand in something extremely polished!</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Preview: independent-samples *t* tests

:: content ::
- So far today, every participant (film) was in **both** conditions (within-subjects) → paired-samples *t* test.
- Most of your Data Write-Up datasets compare **two separate groups of people** (between-subjects) → ==independent-samples *t* test==.
- You will run this test **tomorrow in Discussion 9**. On Thursday, we will go through where its formulas come from.

<p v-click><StickyNote color="amber-light" title="The goal for the next 10 minutes" width="70%">Know <strong>when</strong> to use an independent-samples <em>t</em> test, how to <strong>run</strong> it in R, and how to <strong>read</strong> and <strong>report</strong> the output. The math comes Thursday.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Same logic, different standard error

:: content ::
Every *t* test asks: how far is what we observed from what $H_0$ predicts, in standard error units?

$$t = \frac{\text{observed difference} - \text{difference under } H_0}{SE}$$

<p v-click>

| | Paired samples | Independent samples |
|---|---|---|
| **Design** | Within-subjects | Between-subjects |
| **We analyze** | One set of difference scores | Two separate sets of scores |
| **Observed difference** | $M_D$ | $M_1 - M_2$ |
| **Standard error** | From one *SD* and one *n* | From **both** *SD*s and **both** *n*s |
| **df** | $n - 1$ | $n_1 + n_2 - 2$ |

</p>

<p v-click>

Everything else works the same way: *p* value, decision, confidence interval, Cohen's *d*.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Thursday: where that standard error comes from

:: left ::

- With two separate groups there is no difference score to take. Each group has its own mean, its own spread, and its own $n$.
- The signal is $M_1 - M_2$. The noise must describe how much *that difference* would bounce around if we drew two new samples, so the SE has to combine the **spread of both groups** and the **size of both samples**.

<p v-click>

- On Thursday we build that SE step by step: how to **combine two sample variances into one noise estimate**, how that becomes the standard error of a difference between two means, and why $df = n_1 + n_2 - 2$.

</p>

:: right ::

<p v-click><StickyNote color="amber-light" title="A preview of the logic" width="100%">Paired test: one sample of differences → one SD → one SE. Independent test: two samples → two SDs → one SE built from both. Same idea, one more ingredient.</StickyNote></p>

<p v-click><StickyNote color="green-light" title="For tomorrow" width="100%">In Discussion 9 you only need to <b>run and read</b> the test; R computes the SE for you.</StickyNote></p>

<p v-click>

<div class="flex items-center gap-3 mt-3">
<IceCream :size="70" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem">The six steps do not change. Only Step 3's recipe for the noise does.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: which *t* test?

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Forty students are randomly assigned to study with music or in silence, and then everyone takes the same quiz. Which test compares the two conditions?

**A.** Single-sample *t* test &nbsp;&nbsp; **B.** Paired-samples *t* test &nbsp;&nbsp; **C.** Independent-samples *t* test

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Each student is in only one condition, so the two sets of quiz scores come from different people.

</Admonition>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

Eighteen participants complete a reaction-time task after a normal night of sleep and again after a night of restricted sleep. Which test compares the two nights?

**A.** Single-sample *t* test &nbsp;&nbsp; **B.** Paired-samples *t* test &nbsp;&nbsp; **C.** Independent-samples *t* test

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Every participant is measured in both conditions, so we analyze one set of difference scores.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: degrees of freedom

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

A researcher compares the anxiety scores of 20 first-year students and 22 seniors with an independent-samples *t* test. What are the degrees of freedom?

**A.** 19 &nbsp;&nbsp; **B.** 21 &nbsp;&nbsp; **C.** 40 &nbsp;&nbsp; **D.** 42

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** df = n₁ + n₂ − 2 = 20 + 22 − 2 = 40. We lose one degree of freedom for each group, because we estimate a standard deviation from each sample.

</Admonition>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">

What if the same 20 students were measured as first-years and again as seniors?

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Now it is a paired-samples *t* test on 20 difference scores, so df = n − 1 = 19.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Running an independent-samples *t* test in R

:: left ::
Do candies with chocolate win more matchups than candies without? (This is the worked example posted with your Data Write-Up.)

```r
# group_1 = chocolate candies
# group_2 = non-chocolate candies
t.test(group_1$winpercent,
       group_2$winpercent,
       var.equal = TRUE)
```

- Give R the DV for each group.
- `var.equal = TRUE` tells R to combine the two groups' variability into one estimate (Thursday!).
- For a paired test, you would use `paired = TRUE` instead.

:: right ::

```text
	Two Sample t-test

t = 7.5187, df = 83, p-value = 5.86e-11
95 percent confidence interval:
 13.81121 23.74649
sample estimates:
mean of x mean of y
 60.92135  42.14250
```

<p v-click>

- **t = 7.52**: the difference between the means (18.78) is 7.5 standard errors from 0.
- **df = 83**: 37 + 48 − 2.
- **p-value = 5.86e-11**: scientific notation for .0000000000586, so *p* < .001.
- **95% CI**: plausible values for the population difference; it does not include 0.

</p>

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

Candies containing chocolate won a higher percentage of their matchups (*M* = 60.92, *SD* = 12.81) than candies without chocolate (*M* = 42.14, *SD* = 10.22), *t*(83) = 7.52, *p* < .001, *d* = 1.62, 95% CI \[13.81, 23.75].

✅ State the means and SDs for **both** groups, and say which group was higher.

<p v-click><StickyNote color="green-light" title="For tomorrow" width="70%">Bring your group's Data Write-Up file to Discussion 9. You'll practice all three <em>t</em> tests in R, then run the test for your own dataset.</StickyNote></p>

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

**Paired-samples *t* test** — for within-subjects designs: two scores per participant. Compute a **difference score** for each, then run a single-sample *t* test on the differences against μ = 0.

</div>
<div>

**Distribution of mean differences** — the null world: mean difference scores centered on 0, spread $s_M = s_D/\sqrt{n}$, *t* with df = (number of pairs) − 1.

</div>
<div>

**Effect size and CI for a paired test** — $d = M_D / s_D$; $CI = M_D \pm t_{crit} \times s_M$, a range of plausible values for the true mean difference.

</div>
<div>

**APA style** — one sentence with descriptives for each condition, direction in words, *t*(df) = value, *p*, *d*, and the 95% CI. Italic symbols, no leading zero on *p*.

</div>
</div>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="70%">Thursday: where the independent-samples t test's standard error comes from, and a published study that settled who talks more.</StickyNote></p>

---
layout: cover
color: indigo-light
---

# That's all for today!
Tomorrow in discussion: run your own *t* test. Thursday: how independent-samples *t* tests work under the hood.
