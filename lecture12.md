---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 12
exportFilename: ps211_fall2026_lecture12
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 12: Parametric Assumptions & Intro to *t* Tests

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- Exam 2 grades are posted. We will go over hard questions today. Median: 29/33 (88%).
- A ==grade calculator== has been posted on Slack.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Coming up:
  - Tuesday (11/3): Lecture 13 (paired-samples *t* tests & reporting results in APA style)
  - Thursday (11/5): Lecture 14 (independent-samples *t* tests)
  - Exam 3: **Thursday, November 12** (covers Lectures 11–14)

- ==Data Write-Up #1== (t-test-based) is due **Monday, November 9** at 11:59 p.m.
- ==Course feedback survey== closes tomorrow.

---
layout: section
color: indigo-light
align: lt
---

Before anything new...
# Finishing Lecture 11: statistical power

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# When and how do we use power?

:: content ::

Researchers use ==power analysis== in two ways:

1. ==Before== the study (*a priori*): "I expect a medium effect. How many participants do I need for 80% power?" This is the important one, now required by many journals and funders. It is why papers say "we recruited 128 participants" rather than "as many as we could."

2. ==After== the study (*post hoc*): "Given my n and the effect I expected, what was my power?" Useful for interpreting a null result: if power was 0.25, "not significant" tells you little.

<p v-click>

- The numbers come from software or online calculators. The inputs are always **effect size, sample size, alpha, and tails**. Give it any three and it returns the fourth.

</p>

<div class="flex items-start gap-6 mt-2">
<p v-click>

```r
power_sim(n = 20, d = 0.5)              # 0.61
power_sim(n = 64, d = 0.5)              # 0.98  larger sample
power_sim(n = 20, d = 0.2)              # 0.14  smaller effect
power_sim(n = 20, d = 0.5, alpha = .01) # 0.37  stricter alpha
```

<div class="text-sm text-gray-600 mt-1">In Discussion 8, <code>power_sim()</code> drew 5,000 fake samples with a real effect and counted how often the z test rejected. Can you predict the direction of each change? Exact power numbers come from software, but you should know whether different factors will increase or decrease power.</div>

</p>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: power

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher tests whether a new study app improves grades, with 15 students. The app really does help ($d = 0.3$). She finds $p = .40$. What most likely happened?

- **A)** A Type I error.
- **B)** The app does not work.
- **C)** She should lower alpha to .01 and try again.
- **D)** A Type II error, because the study had low power.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** A real effect that was not detected is a Type II error. With a small effect and n = 15, power is only about 0.2, so this outcome was the *expected* one. Lowering alpha \(C) would reduce power further.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Which change would **increase** the power of a study without increasing the Type I error rate?

- **A)** Recruiting more participants.
- **B)** Raising alpha from .05 to .10.
- **C)** Using a less reliable questionnaire to save time.
- **D)** Switching to a two-tailed test after seeing the data favor one direction.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** More data shrinks the SE. (B) raises power but also raises Type I errors. \(C) adds noise, lowering power. (D) is backwards and, done after seeing the data, is cheating either way.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: putting it together

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Study A: $n = 2{,}000$, $p = .001$, $d = 0.10$. Study B: $n = 40$, $p = .03$, $d = 0.70$. Which statement is best?

- **A)** Study A found the bigger effect, because its p value is smaller.
- **B)** The studies found the same effect.
- **C)** Study B found the bigger effect; Study A's tiny effect was detectable only because of its huge sample.
- **D)** Study B's result cannot be trusted because n = 40 is too small for any conclusion.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** p values depend on n; effect sizes do not. (D) overreaches: with a large effect, n = 40 can give decent power.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

What is the relationship between β and power?

- **A)** They are the same thing.
- **B)** Power = 1 − β.
- **C)** Power = α − β.
- **D)** They are unrelated.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** When the effect is real, we either detect it (power) or miss it (β). Those two possibilities add to 1.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from Lecture 11 (now complete)

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Effect size** — the magnitude of a difference in standardized units. Unaffected by sample size.

</div>
<div>

**Cohen's d** — how many standard deviations apart two means are. For a z test, $d = (M - \mu)/\sigma$. Conventions: 0.2 small, 0.5 medium, 0.8 large. (Two samples, no σ: Lecture 14.)

</div>
<div>

**Significant ≠ big** — p depends on n; d does not. With enough data, any nonzero difference is "significant."

</div>
<div>

**Type II error (β)** — failing to reject $H_0$ when it is false: missing a real effect.

</div>
<div>

**Statistical power** — the probability of detecting an effect that is real: $1 - \beta$. Target: 0.80.

</div>
<div>

**What raises power** — larger n, larger effect, less variability, larger α, one-tailed test. Only the first three are free of cost.

</div>
</div>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="70%">Today: what to do when you do not know σ (which is almost always). The t test is the z test with one ingredient swapped, and effect size comes right back.</StickyNote></p>

---
layout: section
color: indigo-light
align: lt
---

A promise from Lecture 9...
# Statistical assumptions

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Parametric vs. non-parametric tests

:: content ::

- Lecture 9's Step 1 said "check the test's assumptions (more on this later!)." It is now later!
- The z test, and every test we will learn until Lecture 19, is a ==**parametric**== test: it works by assuming the data follow a distribution with known **parameters** (for the normal distribution: a mean and a standard deviation).
- That assumption is what lets us draw the null world as a smooth curve and read areas off it. It also means the outcome must be **numeric** (hours, milliseconds, degrees: something with a mean), not categories or rankings. Lecture 19 covers the tests for those.

<p v-click>

- **Parametric** tests generally have more ==power== than **non-parametric** tests *because* they lean on these assumptions. The price: if the assumptions are badly wrong, the p values are wrong too.

</p>

<p v-click><StickyNote color="amber-light" title="The deal" width="80%">Assumptions buy power. Before using a parametric test, check that you can afford them. Most of the time, you can.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Assumption 1: Normality

:: content ::

- The **comparison distribution** should be (roughly) normal.
- For tests about **means**, this is usually safe even when the individual scores are not normal.

<Admonition title="Question" color="teal-light" width="100%">

Why? Which theorem have we already met that guarantees this?

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

The **Central Limit Theorem**: with a large enough n, the distribution of sample means is approximately normal whatever the population looks like. In Lecture 8, single dice rolls were flat (every face equally likely), but means of 30 rolls were bell-shaped.

</Admonition>

<p v-click><StickyNote color="amber-light" title="When to worry" width="80%">Small samples (n under ~30) drawn from a very skewed population, or data with a hard ceiling or floor. Then look at a histogram before you trust a parametric test.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Assumption 2: Equal variance

:: left ::

- When we compare **two groups** (coming Tuesday and Thursday), the groups should have roughly **equal variance**: similar spread of scores.
- The test pools the two spreads into one "noise" estimate. If one group is far more variable, that estimate is wrong for both.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Body temperature, men vs. women; Pixar Rotten Tomatoes scores, before vs. after 2010. Which comparison meets the assumption?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Body temperature, yes: SDs 0.70 and 0.74. Pixar, no: the later films' SD (16.7) is more than twice the earlier films' (7.7), thanks to *Cars 2*. You meet this one in Discussion 9.

</Admonition></p>

:: right ::

<img src="/images/lecture12/equal_variance_two_examples.png" alt="Body temperature by sex, and Pixar Rotten Tomatoes scores before and after 2010" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Data: Shoemaker (1996), 130 adults; pixarfilms R package, 23 films (Discussions 1–3).</div>

<p v-click><StickyNote color="amber-light" title="Rule of thumb" width="100%">If the larger SD is less than about twice the smaller one, you are fine. (And there is a version of the test that drops this assumption. Thursday.)</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Assumptions 3 and 4: Independence and outliers

:: content ::

### 3. Independence
- Each observation should be sampled **independently**: one data point does not influence another.
- Violations are easy to miss: the same person measured twice, students in the same class, one professor rated in several courses.

<p v-click><StickyNote color="amber-light" title="Not always a problem" width="70%">Sometimes the dependence is the <i>design</i>: everyone tested before and after. Tuesday's test is built for that.</StickyNote></p>

<p v-click>

### 4. No extreme outliers
- A single wild score can drag the mean and inflate the SD. One person who sleeps 14 hours in a sample of 20 changes everything.
- Look at your data (histograms, box plots) before testing, and decide what to do with outliers *before* you see whether they help your hypothesis.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which assumptions go with which test?

:: content ::

These are assumptions of the whole **parametric family**, not of the z test alone. Not every test needs every one:

<table class="compact-table text-sm">
<thead><tr><th>Assumption</th><th>z test<br/>(L10)</th><th>Single-sample <i>t</i><br/>(today)</th><th>Paired <i>t</i><br/>(L13)</th><th>Independent <i>t</i><br/>(L14)</th><th>ANOVA<br/>(L15–16)</th></tr></thead>
<tbody>
<tr><td>Outcome is numeric (interval or ratio), so it has a mean</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td></tr>
<tr><td>Comparison distribution is normal</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td></tr>
<tr><td>Observations are independent</td><td>✓</td><td>✓</td><td>✓ (the pairs)</td><td>✓</td><td>✓</td></tr>
<tr><td>Groups have equal variance</td><td>—</td><td>—</td><td>—</td><td>✓</td><td>✓</td></tr>
<tr><td>Population σ is known</td><td>✓</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
</tbody>
</table>

<p v-click>

- The first three rows are the price of admission for every test in this course. Equal variance only matters once there are separate groups to compare. Known σ is the z test's special requirement, and the reason we are about to replace it.
- Outliers are not an assumption so much as a **check you run every time**: one wild score can break any of these tests.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# What if the assumptions are not met?

:: left ::

- Parametric tests are fairly **robust**: if assumptions are *a little* violated, the results are still trustworthy, especially with larger samples.
- If they are badly violated, every parametric test has a ==**non-parametric**== twin that makes fewer assumptions (usually by working with **ranks** instead of raw scores).
- Less power, but honest p values.

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">We cover non-parametric tests in Lecture 19. For now: know <i>why</i> the assumptions matter and what to look for.</StickyNote></p>

:: right ::

<img src="/images/lecture9/parametric_nonparametric.webp" alt="Parametric tests and their non-parametric equivalents" class="w-full mx-auto"/>

---
layout: section
color: indigo-light
align: lt
---

The problem with z tests...
# From *z* to *t*

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# What a z test needs

:: left ::

To run a z test we need **two population parameters**:

1. **μ**, the mean $H_0$ predicts. We usually have this: it is the claim we are testing (IQ tests average 100; cookie bags weigh 500 g).
2. **σ**, the population standard deviation. **We almost never have this.**

<p v-click>

- Lectures 9–10: we had σ only because our dataset *was* an entire population (every song on a streaming service), or because the test is built that way (IQ: σ = 15 by design).
- Kruger & Dunning (Lecture 9): σ = 28.9 came from a story about what "no bias" would look like; the researchers never knew σ.

</p>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

You collect reaction times from 20 participants and want to know if their mean differs from 500 ms. You do not know σ. What *do* you have that could stand in for it?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Your **sample's standard deviation**, s. It is our best guess for σ. The ==**t test**== is the z test with s substituted for σ, plus one correction for the fact that s is only an estimate.

</Admonition></p>

<p v-click>

<div class="flex items-center gap-4 mt-2">
<IceCream :size="70" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">This is why real research runs on t tests. They are the workhorse of data analysis, and the next three lectures are about them.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What changes from test to test? Almost nothing.

:: content ::

The six steps and their questions stay the same for every test in this course. Only the answers to **three steps** change:

<table class="compact-table text-base">
<thead><tr><th></th><th>z test</th><th><i>t</i> tests (Lectures 12–14)</th><th>ANOVA (Lectures 15–16)</th></tr></thead>
<tbody>
<tr><td><b>Step 1:</b> which test fits?</td><td>One mean, σ known</td><td>One or two means, σ unknown</td><td>Three or more means</td></tr>
<tr><td><b>Step 3:</b> the comparison distribution</td><td>z distribution. SE = σ/√n</td><td><i>t</i> distribution. SE estimated from the sample, plus degrees of freedom</td><td><i>F</i> distribution. Two degrees of freedom</td></tr>
<tr><td><b>Step 5:</b> signal ÷ noise</td><td>(M − μ) / SE</td><td>(M − μ) / estimated SE</td><td>variance between groups / variance within groups</td></tr>
<tr><td><b>Steps 2, 4, 6</b></td><td colspan="3">Same logic every time: state H₀ and H₁, choose alpha and find the cutoff in the comparison distribution, compare, decide, conclude in plain English.</td></tr>
</tbody>
</table>

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">If you understand the z test, you already understand the skeleton of every test in this course. New tests only swap in a new comparison distribution and a new way to measure noise.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Today's example: a sleeping drug, 10 patients (1905)

:: left ::

Two doctors at a Michigan hospital gave **10 patients** a sedative and recorded how many **extra hours** each one slept, compared with nights without it. Two forms of the drug were tried; today we test **Drug 2**.

Extra hours on Drug 2:

<div class="text-center text-lg my-1">1.9, 0.8, 1.1, 0.1, −0.1, 4.4, 5.5, 1.6, 4.6, 3.4</div>

- $M = 2.33$; &nbsp; $SS = 36.08$, so $s^2 = 36.08/9 = 4.01$ and $s = 2.00$.

==Does Drug 2 change how much people sleep?==

<div class="text-xs text-gray-500 mt-2">Cushny, A. R., &amp; Peebles, A. R. (1905). The action of optical isomers II. Hyoscines. <i>Journal of Physiology, 32</i>, 501–510. The data ship with R as <code>sleep</code>.</div>

:: right ::

<img src="/images/lecture12/sleep_drugs_dots.png" alt="Extra hours of sleep for 10 patients on two drugs" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The claim to test is "no effect": μ = 0 extra hours. Could we run a z test?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

No. We have μ under $H_0$ but no σ: nobody knows the population SD of "extra hours of sleep." All we have is $s = 2.00$, estimated from 10 people. This is exactly the problem the *t* test was invented for (a story in a few slides).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Step 1 of the swap: estimate σ from the sample

:: left ::

- The first thing a *t* test does is estimate the population SD from the sample. You have known how since Lecture 5:

$$s = \sqrt{\frac{\sum (X - M)^2}{n - 1}}$$

- Dividing by $n - 1$ (not $n$) is what makes $s$ an *unbiased* guess for σ: samples tend to be a little less spread out than their population, and $n - 1$ corrects for that.

<p v-click><StickyNote color="amber-light" title="Why n − 1, finally" width="100%">In Lecture 5 we promised to explain the n − 1. Here it is, with its real name: <b>degrees of freedom</b>. More in a few slides.</StickyNote></p>

:: right ::

<img src="/images/lecture9/imback.png" alt="I'm back" class="w-2/3 mx-auto"/>

<p v-click><StickyNote color="green-light" title="In R" width="100%"><code>sd(x)</code> already divides by n − 1. So does <code>var(x)</code>.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 2 of the swap: estimate the standard error

:: left ::

Remember what the SE is: the **spread of the distribution of means**, i.e., how far a sample mean typically lands from μ. It is the "noise" in every test statistic.

<table class="compact-table text-base">
<thead><tr><th></th><th>z test</th><th><i>t</i> test</th></tr></thead>
<tbody>
<tr><td>Spread of scores</td><td>σ (known)</td><td>s (estimated from the sample)</td></tr>
<tr><td>Spread of means</td><td>SE = σ / √n</td><td>s<sub>M</sub> = s / √n</td></tr>
</tbody>
</table>

- Same formula. We write $s_M$ instead of $SE$ to flag that it is an **estimate**.

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The 10 patients on Drug 2 have $s = 2.00$. What is the estimated standard error of their mean?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$s_M = 2.00/\sqrt{10} = 0.63$ hours. If we drew 10 new patients, their mean would typically land about 0.63 hours from the true mean.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="SD vs. SE, one more time" width="100%">s describes individual patients (2.0 hours). s<sub>M</sub> describes how precisely we know the <i>mean</i> (0.63 hours). Divide by √n to get from one to the other.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 3 of the swap: the *t* statistic

:: left ::

Signal ÷ noise, exactly as before:

<div class="grid grid-cols-2 gap-4 text-center mt-2">
<div class="border-2 border-indigo-300 bg-indigo-50 rounded-lg p-3">

**z statistic**

$$z = \frac{M - \mu}{\sigma / \sqrt{n}}$$

σ is known

</div>
<div class="border-2 border-amber-300 bg-amber-50 rounded-lg p-3">

***t* statistic**

$$t = \frac{M - \mu}{s / \sqrt{n}}$$

s is estimated

</div>
</div>

<p v-click>

- Both say: *how many standard errors is our sample mean from what $H_0$ predicts?*
- The only difference is the denominator.

</p>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Compute t for Drug 2: $M = 2.33$, $\mu = 0$, $s_M = 0.63$.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$t = (2.33 - 0)/0.63 = 3.68$. The patients' mean extra sleep is 3.7 estimated standard errors above zero. If this were a z, it would be far past ±1.96.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="So are we done?" width="100%">Not quite. If t were just z with a new name, we could use ±1.96 and <code>pnorm()</code>. But s is only an estimate, from 10 people, and that changes the shape of the null world.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Why estimating σ changes the null world

:: left ::

Where the two curves come from. A simulation with $H_0$ true (μ = 0), repeated 20,000 times:

1. Draw a sample of $n = 5$ and compute its mean, $M$.
2. Ask the usual question, *how many standard errors is $M$ from μ?*, **twice with the same $M$**: divide by the **true** SE, $\sigma/\sqrt{5}$, to get a **z**; divide by the SE **estimated from that sample**, $s/\sqrt{5}$, to get a **t**.
3. Pile up the 20,000 z's (left) and the 20,000 t's (right).

:: right ::

<img src="/images/lecture12/t_simulation_n5.png" alt="z statistics vs t statistics from 20,000 samples of n = 5" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Each panel is the same 20,000 sample means. Only the denominator differs.</div>

<p v-click><StickyNote color="amber-light" title="Why divide at all?" width="100%">Dividing by the SE turns "M is 0.8 hours from μ" into "M is 1.6 standard errors from μ", the only scale on which ±1.96 means anything. It is Steps 2 and 3 of the swap, applied 20,000 times.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Same means, different denominators

:: left ::

- **Left panel:** every z uses the *same* denominator, because $\sigma/\sqrt{5}$ never changes. The z's are just the sample means rescaled: a normal curve, 5% beyond ±1.96.
- **Right panel:** every t uses *its own sample's* $s$. The denominator changes from sample to sample.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Why do extreme t values happen more than twice as often as extreme z values?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Some samples happen to have a small $s$. Then the denominator is too small and t comes out inflated, even though $M$ is nothing special. With n = 5 that happens a lot.

</Admonition></p>

:: right ::

<img src="/images/lecture12/t_simulation_n5.png" alt="z statistics vs t statistics from 20,000 samples of n = 5" class="w-full mx-auto"/>

<p v-click><StickyNote color="amber-light" title="The consequence" width="100%">If we used ±1.96 as the cutoff for t with n = 5, we would reject H₀ about <b>12%</b> of the time when it is true, not 5%. The cutoff has to move out.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# The *t* distribution

:: left ::

- The null world for a *t* statistic is a ==***t* distribution**==: centered on 0 and symmetric like z, but with **heavier tails**.
- There is a different *t* distribution for every sample size. The heavier tails reflect the extra uncertainty from estimating σ, which shrinks as n grows.
- As $n \to \infty$, the *t* distribution **becomes** the z distribution.

<p v-click><StickyNote color="amber-light" title="Which t distribution?" width="100%">We pick it by its <b>degrees of freedom</b> (single sample: n − 1). Lecture 9 promised Step 3 would someday need one more number. This is it.</StickyNote></p>

:: right ::

<img src="/images/lecture12/t_vs_z.png" alt="t distributions with df = 4, 10, 30 and the z distribution" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

With df = 30, the t curve is barely distinguishable from z. What does that tell you about a sample of 31 people?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Its s is a good enough estimate of σ that the correction hardly matters. The t test still handles it correctly; it just gives nearly the same answer a z test would.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Degrees of freedom

:: left ::

<StickyNote color="amber-light" title="Definition" width="100%">Degrees of freedom (df) = the number of scores that are <b>free to vary</b> once we have used the sample to estimate something.</StickyNote>

<p v-click>

- Three friends split a dinner bill and you are told the **mean** was $20.
- The first friend could have paid anything. So could the second. Say $15 and $22.
- Now the third is locked in: it *must* be $23 to make the mean $20.
- Three scores, but only **two** of them carry independent information once the mean is known: $df = 3 - 1 = 2$.

</p>

:: right ::

<p v-click>

- Look at the same bill as **deviations from the mean**: −5, +2, and... the third deviation *has* to be +3, because deviations from a mean always add up to zero. Knowing the mean costs you one free number.

</p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

One study has n = 10 patients, another has n = 130 adults. If you knew each sample's mean and all but one of its scores, could you fill in the missing score? How many scores are free to vary in each?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Yes, in both. 9 scores are free in the first study and 129 in the second; the last one is forced by the mean. $df = n - 1$.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Why s divides by n − 1, and why t needs df

:: left ::

- $s$ is built from the deviations $(X - M)$. But we computed $M$ from the *same* scores, so the deviations are not all free: they must add up to zero, and the last one is fixed by the others.
- The n deviations therefore contain only **n − 1 independent pieces of information** about spread. Dividing by n − 1 averages over the information that is actually there. That is the "n − 1" from Lecture 5, explained.

<p v-click><StickyNote color="amber-light" title="In one line" width="100%">Computing M from the data "uses up" one degree of freedom because it forces the last deviation. Divide by what is left: n − 1.</StickyNote></p>

:: right ::

<p v-click>

- A single-sample *t* test estimates σ from one sample, so $df = n - 1$: 9 for the sleep study.
- The df says how much information went into estimating σ, and therefore **which *t* distribution is the null world**: few df, heavy tails; many df, nearly the z distribution.

</p>

<p v-click><StickyNote color="green-light" title="Coming up" width="100%">Tests that estimate more things spend more df. The independent-samples t test estimates two means, so df = n₁ + n₂ − 2 (Lecture 14).</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 4 for a *t* test: critical values depend on df

:: left ::

- For z, the two-tailed α = .05 cutoffs are always ±1.96. For *t*, they come from the *t* distribution with our df. In R, `qt()` is the *t* version of `qnorm()`:

<table class="compact-table text-sm">
<thead><tr><th>df</th><th>Ask R</th><th>Cutoffs (α = .05, two-tailed)</th></tr></thead>
<tbody>
<tr><td>4</td><td><code>qt(0.975, 4)</code></td><td>±2.776</td></tr>
<tr><td>10</td><td><code>qt(0.975, 10)</code></td><td>±2.228</td></tr>
<tr><td>30</td><td><code>qt(0.975, 30)</code></td><td>±2.042</td></tr>
<tr><td>129</td><td><code>qt(0.975, 129)</code></td><td>±1.979</td></tr>
<tr><td>∞</td><td><code>qnorm(0.975)</code></td><td>±1.960</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Reading the table" width="100%">Smaller sample → heavier tails → cutoff <b>farther out</b>. A small study needs a bigger t to reject H₀: the price of estimating σ.</StickyNote></p>

:: right ::

<img src="/images/lecture12/t_crit_vs_df.png" alt="Critical t as a function of degrees of freedom" class="w-full mx-auto"/>

<p v-click><StickyNote color="green-light" title="And for Route 2" width="100%">The p value is the area beyond our t in the t distribution with our df. In R, <code>pt()</code> does for t what <code>pnorm()</code> did for z: <code>2 * pt(-3.68, 9)</code> = .005 for Drug 2. You will never do this by hand; <code>t.test()</code> reports p directly.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# What about *t* tables?

:: left ::

- Textbooks print a ==***t* table**==: one row per df, one column per alpha level and number of tails. The entries are the same numbers `qt()` gives.
- Like the z table, it is a fallback for when you have no computer. Researchers get critical values and p values from software, and so will we.

<p v-click><StickyNote color="amber-light" title="One thing worth seeing" width="100%">Run your eye down any column: the values shrink as df grows and settle at the z value in the bottom row. That is the picture from the last slide, as numbers.</StickyNote></p>

:: right ::

<img src="/images/lecture9/t_table.png" alt="A t table" class="w-10/12 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# A brief aside: why is it called "Student's" *t*?

:: left ::

- The *t* distribution was worked out in 1908 by **William Sealy Gosset**, a chemist at the **Guinness brewery** in Dublin.
- His problem was ours: judging batches of barley and hops from **small samples**, where "σ is known" fails. He needed a test that was honest about estimating σ from a handful of observations.
- Guinness did not let employees publish, so he wrote as **"Student."** The worked example in his 1908 paper: the **same sleep data** we are using today.

<p v-click><StickyNote color="amber-light" title="Moral" width="100%">The t test exists because a brewer wanted to make decisions from small samples without fooling himself. Heavier tails are the honesty.</StickyNote></p>

:: right ::

<img src="/images/lecture11/guinness.jpg" alt="Guinness" class="w-3/4 mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Student. (1908). The probable error of a mean. <i>Biometrika, 6</i>(1), 1–25.</div>

---
layout: section
color: indigo-light
align: lt
---

Putting the pieces together...
# The single-sample *t* test

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six steps for a single-sample *t* test

:: content ::

==Used to compare a sample mean to a population mean when σ is unknown.==

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>The question</th><th>z test</th><th>Single-sample <i>t</i> test</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Who is being compared, and which test fits?</td><td>One sample mean vs. a population with known μ and σ</td><td>One sample mean vs. a population with known μ, <b>σ unknown</b></td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>What are the two competing claims?</td><td colspan="2">H₀: μ₁ = μ₂ &nbsp; H₁: μ₁ ≠ μ₂ (or &lt;, &gt;). Identical.</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td>If H₀ were true, what results would we expect?</td><td>Center μ, spread SE = σ/√n, normal</td><td>Center μ, spread <b>s<sub>M</sub> = s/√n</b>, <b><i>t</i> distribution, df = n − 1</b></td></tr>
<tr><td><b>4.</b> Critical values</td><td>How extreme is extreme enough?</td><td>α = .05, two-tailed → ±1.96</td><td>α = .05, two-tailed → <b>±t<sub>crit</sub> for our df</b></td></tr>
<tr><td><b>5.</b> Test statistic</td><td>How far is our result from what H₀ predicts, compared to chance?</td><td>z = (M − μ) / SE</td><td><b>t = (M − μ) / s<sub>M</sub></b></td></tr>
<tr><td><b>6.</b> Decision</td><td>Is it past the cutoff? What do we conclude?</td><td colspan="2">Reject or fail to reject H₀, then say it in plain English. Identical.</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Three changes, all in bold" width="90%">Step 1 names the situation (σ unknown), Step 3 adds s<sub>M</sub> and df, Steps 4 and 5 use t instead of z. Everything else is Lecture 9.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Worked example: Drug 2, σ unknown

:: left ::

Ten patients, extra hours of sleep on Drug 2: $M = 2.33$, $s = 2.00$. Does the drug change how much people sleep (μ = 0 means no effect)?

<p v-click><Admonition title="Steps 1 to 4" color="green-light" width="100%">

**1.** These patients vs. a population where the drug does nothing. One sample mean, μ known, σ **unknown** → **single-sample *t* test**. Assumptions: hours are numeric; n = 10 is small, so we rely on the population being roughly normal; no wild outliers (5.5 is the largest).

**2.** $H_0$: $\mu = 0$. &nbsp; $H_1$: $\mu \neq 0$ (two-tailed).

**3.** If $H_0$ is true: center 0, $s_M = 2.00/\sqrt{10} = 0.63$, *t* distribution with $df = 9$.

**4.** α = .05, two-tailed, df = 9 → `qt(0.975, 9)` → cutoffs **±2.262**.

</Admonition></p>

:: right ::

<p v-click><Admonition title="Steps 5 and 6" color="green-light" width="100%">

**5.** $t = (2.33 - 0)/0.63 = 3.68$

**6.** 3.68 is beyond 2.262 → **reject $H_0$**. Route 2: `2 * pt(-3.68, 9)` = .005 < .05. Patients slept significantly longer on Drug 2.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="What changed from a z test" width="100%">Step 3 uses s<sub>M</sub> (estimated) instead of SE (known), and the null world is t with df = 9, so the cutoff is 2.262 rather than 1.96. The same data would have been judged against a looser standard if we had pretended to know σ.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# The two null worlds, side by side

:: left ::

- **Top:** the null world if we treated $s$ as if it were σ: a normal curve, cutoffs ±1.96 × 0.63 = **±1.24 hours**.
- **Bottom:** the honest null world: *t* with df = 9, cutoffs ±2.262 × 0.63 = **±1.43 hours**. Same center and spread, heavier tails.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Drug 2's t = 3.68 is past both cutoffs. Suppose a study of 10 people came out at t = 2.1. What would each world say?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

z world: beyond 1.96, "significant." t world: short of 2.262, not. In that gap, pretending to know σ produces false alarms. With df = 9 the gap matters; with df = 129 it almost vanishes.

</Admonition></p>

:: right ::

<img src="/images/lecture12/sleep_z_vs_t.png" alt="Null worlds for the sleep study using z cutoffs and t cutoffs" class="w-11/12 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Confidence intervals and effect size with *t*

:: left ::

Both work exactly as before, with the *t* ingredients swapped in:

$$CI = M \pm t_{crit} \times s_M$$

$$d = \frac{M - \mu}{s}$$

- $t_{crit}$ comes from `qt()` with our df (not 1.96).
- For d, divide by the **sample SD**, our stand-in for σ.

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Compute the 95% CI and Cohen's d for Drug 2: $M = 2.33$, $s = 2.00$, $s_M = 0.63$, $t_{crit} = 2.262$.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

CI: $2.33 \pm 2.262 \times 0.63 = 2.33 \pm 1.43$ → **\[0.90, 3.76]** extra hours. Excludes 0, matching the test.

$d = (2.33 - 0)/2.00 = 1.16$: a large effect. The drug added more than a full standard deviation's worth of sleep.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Width check" width="100%">With 1.96 in place of 2.262 the interval would be [1.09, 3.57]. The t-based interval is wider: the honest price of estimating σ from 10 people. With a large n the two are nearly identical.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Running a single-sample *t* test in R: t.test()

:: left ::

One function does Steps 3 to 6:

```r
sleep <- read_csv("sleep_data.csv")
drug2 <- filter(sleep, drug == 2)

t.test(drug2$extra, mu = 0)
```

<div class="text-base">

- Give R the sample's scores and the population mean $H_0$ predicts (`mu`).
- No σ needed. R estimates s, computes $s_M$, finds df, and reports t, p, and a CI.

</div>

<p v-click="2"><StickyNote color="amber-light" title="Same layout as z.test()" width="100%">If you can read the Lecture 10 output, you can read this one. The only new line is <code>df = 9</code>.</StickyNote></p>

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

<div v-click="1" class="text-base">

- **t = 3.68**: Step 5. The mean is 3.68 estimated SEs above 0.
- **df = 9**: which t distribution is the null world (n − 1).
- **p-value = 0.005**: Step 6, Route 2. Below α = .05, so reject $H_0$.
- **95% CI**: 0.90 to 3.76 extra hours. Excludes 0.
- **mean of x**: *M* = 2.33. R does not print s or d; compute them separately.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice: is normal body temperature really 98.6°F?

:: left ::

Everyone "knows" normal body temperature is 98.6°F. The number comes from Carl Wunderlich, who in 1868 compiled over a million armpit readings from 25,000 patients.

In 1992, researchers at the University of Maryland measured the oral temperature of **130 healthy adults**:

- $M = 98.25$°F, $s = 0.73$°F

==Is the true average body temperature 98.6°F, or is the famous number wrong?==

<p v-click><StickyNote color="amber-light" title="How, not what" width="100%">These numbers are not meant for hand calculation. The next two slides ask <i>how</i> you would test this; R does the arithmetic.</StickyNote></p>

<div class="text-xs text-gray-500 mt-2">Data: Mackowiak, P. A., Wasserman, S. S., & Levine, M. M. (1992). <i>JAMA, 268</i>(12), 1578–1580; dataset from Shoemaker (1996), <i>Journal of Statistics Education</i>.</div>

:: right ::

<img src="/images/lecture12/body_temp_hist.png" alt="Histogram of 130 body temperatures" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Body temperature: how would you test it?

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which test, and why?

- **A)** Single-sample *t* test: one sample mean vs. a claimed population mean (98.6), σ unknown.
- **B)** z test: μ = 98.6 is known, so we have what we need.
- **C)** Paired-samples *t* test: each person is compared with 98.6.
- **D)** No test is needed: 98.25 is obviously different from 98.6.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** We know the claimed μ but not σ; 0.73 is the sample's s. (B) confuses knowing μ with knowing σ.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

If $H_0$ is true, what does the comparison distribution look like?

- **A)** Normal, centered on 98.25, spread 0.73.
- **B)** *t* with df = 130, centered on 98.6, spread 0.73.
- **C)** Normal, centered on 98.6, spread $0.73/\sqrt{130}$.
- **D)** *t* with df = 129, centered on 98.6, spread $s_M = 0.73/\sqrt{130} \approx 0.064$.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Centered on what $H_0$ claims, with the spread of *means*, and a *t* distribution because σ was estimated. (A) describes the sample, not the null world. \(C) forgets that σ was estimated.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Body temperature: finishing the test

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

How would you find the cutoffs (α = .05, two-tailed), and roughly what are they?

- **A)** ±1.96, because every two-tailed test at α = .05 uses ±1.96.
- **B)** From the *t* distribution with df = 129 (`qt(0.975, 129)`): ±1.98, almost the same as z because df is large.
- **C)** ±2.262, the same as the sleep study.
- **D)** They depend on M, so they cannot be found until t is computed.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Cutoffs come from the null world, which depends on df, not on the data. With 129 df the t curve is nearly normal.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

R reports `t = -5.45, df = 129, p-value = 2.4e-07`. What does t = −5.45 mean?

- **A)** The sample mean is 5.45 degrees below 98.6.
- **B)** 5.45% of people have a temperature below 98.6.
- **C)** The sample mean is 5.45 *estimated standard errors* below 98.6: far beyond −1.98, so reject $H_0$.
- **D)** The test is invalid because t is negative.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** t counts standard errors, not degrees. The sign only says which direction.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Body temperature: the result

:: left ::

```text
	One Sample t-test

data:  temps$temperature
t = -5.4548, df = 129, p-value = 2.411e-07
alternative hypothesis: true mean is not equal to 98.6
95 percent confidence interval:
 98.12200 98.37646
sample estimates:
mean of x 
 98.24923 
```

<div class="text-base mt-2">

- **Step 6:** −5.45 is far beyond −1.98, and p < .05 → **reject $H_0$**. Normal body temperature is significantly lower than 98.6°F.
- Plausible values for the true mean: 98.12 to 98.38. 98.6 is not among them. Wunderlich's thermometers read high.

</div>

:: right ::

<img src="/images/lecture12/null_world_bodytemp.png" alt="The t distribution with df = 129 and the observed t" class="w-10/12 mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The difference is only 0.35 degrees. How can that be so significant? And is it a big effect?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Lecture 11: n = 130 makes $s_M$ tiny (0.064), so a small difference is 5.5 SEs from 98.6. The effect size is $d = -0.35/0.73 = -0.48$: medium. Real, and big enough to matter when you decide whether someone has a fever.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Preview: Discussion 9, test 1 of 3

:: left ::

Next Wednesday's worksheet runs all three *t* tests on the Pixar data from Discussions 1–3. The first is a single-sample test: Rotten Tomatoes calls a film "Fresh" at 60 or above. **Is the average Pixar film's score different from 60?**

```r
pixar <- read_csv("pixar_data.csv")

# By hand first (you fill in SE and t)
M <- mean(pixar$rotten_tomatoes)
s <- sd(pixar$rotten_tomatoes)
n <- nrow(pixar)

# Then let R do it
t.test(pixar$rotten_tomatoes, mu = 60)
```

<div class="text-xs text-gray-500 mt-1">Data: 23 Pixar films; pixarfilms R package (Wikipedia, Metacritic, Rotten Tomatoes).</div>

:: right ::

```text
	One Sample t-test

data:  pixar$rotten_tomatoes
t = 9.8852, df = 22, p-value = 1.489e-09
alternative hypothesis: true mean is not equal to 60
95 percent confidence interval:
 83.05332 95.29451
sample estimates:
mean of x 
 89.17391 
```

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Where does df = 22 come from? What is the decision?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

23 films − 1. $t = 9.89$ is far beyond the cutoff for df = 22 (±2.07), and p = 0.0000000015 → reject: Pixar films average well above "Fresh" (89, CI 83 to 95). How to write a p value like that properly is Tuesday's topic (APA style).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: z or *t*?

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A coffee chain claims its lattes contain 150 mg of caffeine on average. You test 12 lattes and find $M = 162$ mg, $s = 18$ mg. Which test, and why?

- **A)** z test, because you know the population mean.
- **B)** z test, because you have the standard deviation.
- **C)** *t* test, because you are comparing a sample mean to a population mean and do not know σ.
- **D)** Neither; n = 12 is too small for any test.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** The 18 mg is the *sample's* SD, an estimate. (D) is wrong: small n is exactly what the t distribution is for; it just uses a wider cutoff (df = 11 → ±2.20).

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Your friend computes $t = (162 - 150)/18 = 0.67$ and concludes the claim holds. What is wrong?

- **A)** Nothing; the conclusion is correct.
- **B)** The denominator should be $18/\sqrt{12} = 5.2$, the estimated standard error, giving $t = 2.31$.
- **C)** The numerator should be 150 − 162.
- **D)** She should have divided by 11 instead of 18.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** A *mean* is compared with the spread of *means* (the standard error), not with the spread of individual scores. With $t = 2.31$ and a cutoff of ±2.20 (df = 11), we reject: these lattes have more caffeine than claimed.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: the *t* distribution

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Compared with the z distribution, a *t* distribution with df = 6 has:

- **A)** The same shape; t and z are just different names.
- **B)** Lighter tails, so the cutoffs are closer to 0 than ±1.96.
- **C)** A different center.
- **D)** Heavier tails, so the α = .05 cutoffs are farther from 0 than ±1.96.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** Estimating σ from 7 scores adds uncertainty, so extreme t values are more common under $H_0$ and the cutoffs move out (to ±2.45).

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

R reports: `t = 2.10, df = 24, p-value = 0.046`. With α = .05, two-tailed, what do you conclude?

- **A)** Reject $H_0$: p < .05, so the sample mean differs significantly from μ.
- **B)** Fail to reject: 2.10 is not beyond 1.96.
- **C)** Fail to reject: the sample had only 24 people.
- **D)** Accept $H_0$: the difference is small.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Route 2: p = .046 < .05. (B) uses the wrong cutoff: with df = 24 the cutoff is ±2.06, and 2.10 is beyond it, so Route 1 agrees. \(C) confuses n with df. We never "accept" $H_0$.

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

**Parametric test** — assumes the data follow a distribution with known parameters (normality, equal variance, independence, no extreme outliers). More power, if the assumptions hold.

</div>
<div>

**Single-sample *t* test** — compares a sample mean to a population mean when **σ is unknown**. The z test with s in place of σ.

</div>
<div>

**Estimated standard error** — $s_M = s/\sqrt{n}$. The spread of the distribution of means, estimated from the sample.

</div>
<div>

**t statistic** — $t = (M - \mu)/s_M$. How many estimated SEs the sample mean is from what $H_0$ predicts.

</div>
<div>

**t distribution** — the null world for t: like z but with heavier tails, one curve per df. Approaches z as n grows. Cutoffs from `qt()`, p values from `pt()`.

</div>
<div>

**Degrees of freedom** — scores free to vary after estimating from the sample. Single sample: df = n − 1. Picks which t distribution is the null world.

</div>
</div>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="70%">Tuesday: the same test for <b>before-and-after</b> designs (the paired-samples t test), plus how to write up any result in APA style.</StickyNote></p>

---
layout: cover
color: indigo-light
---

# That's all for today!
See you Tuesday (11/3) for paired-samples *t* tests and APA style. Wednesday in Discussion 9: run the *t* test for your own data.
