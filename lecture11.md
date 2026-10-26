---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 11
exportFilename: ps211_fall2026_lecture11
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 11: Effect Size & Statistical Power

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- Exam 2 grades will be posted **Thursday (10/29)**.
- ==Data Write-Up #1== (t-test-based) is due **Monday, November 9** at 11:59 p.m. More on this in a few minutes.
  - Tomorrow in Discussion 8 (Wed. 10/28): practice today's material (effect size & power) in R, then finish your descriptive statistics (Part 4) and trade feedback with another group.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Coming up:
  - Thursday (10/29): Lecture 12 (parametric assumptions & our first *t* test)
  - Exam 3: **Thursday, November 12** (covers Lectures 11–14 — today's material is on Exam 3!)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where we are: the road to Exam 3

:: content ::

Before Exam 2 we built one tool, the z test, and the logic behind every hypothesis test. The next four lectures turn that logic into the tests researchers actually use:

<div class="grid grid-cols-4 gap-3 mt-4 text-sm">
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3"><b>Lecture 11 (today)</b><br/>Effect size & power: how <i>big</i> is an effect, and would our study even <i>find</i> it?</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 12</b><br/>Assumptions & the <i>t</i> test: what to do when you don't know σ (which is almost always)</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 13</b><br/>Paired-samples <i>t</i> tests & APA style: before-and-after designs, and how to write a result up</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 14</b><br/>Independent-samples <i>t</i> tests: two separate groups. The test most of your write-ups use</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">The z test was the skeleton. From here on, every new test is a small change to one of its six steps. And Discussions 8 and 9 are where you run each of them in R, on data you chose.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Data Write-Up #1: what you are producing

:: content ::

You started this in Discussion 4. The assignment is the file `ps211_data_writeup1.Rmd`: your group (2–3 people) fills it in over three discussion sections and submits it once.

- A **real psychology dataset** from the Discussion 4 menu.
- A **research question** that compares two groups or two conditions on a numeric DV.
- **Hypotheses written before you looked at the data.** (Parts 1–3, done in D4.)
- A ***t* test in R**, Cohen's *d*, and one **APA-style results sentence**.
- **One figure** (group means with SE error bars) with a caption.
- An **interpretation**: decision, size of the effect, two limitations, a follow-up question.

<div class="flex items-start gap-6 mt-2">
<p v-click><StickyNote color="amber-light" title="Logistics" width="100%">One knitted HTML file per group, all names at the top, sent on Slack to Kate and Rola by <b>Monday, Nov. 9, 11:59 p.m.</b> Late work loses 3 points per day.</StickyNote></p>
<p v-click><StickyNote color="amber-light" title="The one rule that matters most" width="100%">Your question and hypotheses were written <i>before</i> you saw the data. Don't rewrite them to match the results. That is what makes it a test and not a story.</StickyNote></p>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Data Write-Up #1: how it is graded, and when each part happens

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Part</th><th>What is graded</th><th>Pts</th><th>When</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Dataset</td><td>Named, cited, described; what one row is; n</td><td>5</td><td>D4 ✓</td></tr>
<tr><td><b>2.</b> Question & variables</td><td>Research question; IV and its two levels; DV; which t test and why</td><td>15</td><td>D4 ✓</td></tr>
<tr><td><b>3.</b> Hypotheses</td><td>H₀ and H₁ in words; one- vs. two-tailed, justified; alpha</td><td>10</td><td>D4 ✓</td></tr>
<tr><td><b>4.</b> Descriptives</td><td>M, SD, n per group in a table; shape and SD check</td><td>10</td><td><b>D8 (tomorrow)</b></td></tr>
<tr><td><b>5.</b> The test</td><td>Right test on the right groups; t, df, p, 95% CI, d in APA format</td><td>20</td><td>D9 (Nov. 4)</td></tr>
<tr><td><b>6.</b> Figure</td><td>Group means with error bars; labels; caption</td><td>15</td><td>D9 (Nov. 4)</td></tr>
<tr><td><b>7.</b> Interpretation</td><td>Decision; effect size in plain language; limitations; what next</td><td>15</td><td>D9 (Nov. 4)</td></tr>
<tr><td>Code & writing</td><td>Chunks run and are commented; file knits; proofread; AI statement</td><td>10</td><td>before Nov. 9</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="green-light" title="Where you should be right now" width="80%">Parts 1–3 written, data loaded once, group named. If your group has not settled on a dataset and a question, do it before tomorrow: Discussion 8 starts from Part 4.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why this assignment: it is the whole course in one file

:: content ::

Every part of the write-up is a step of the hypothesis-testing logic we have been building since Lecture 6, applied to data you chose:

<table class="compact-table text-sm">
<thead><tr><th>Write-up part</th><th>Six-steps logic</th><th>Where you learned it</th></tr></thead>
<tbody>
<tr><td><b>2–3.</b> Question, variables, hypotheses, one- vs. two-tailed, alpha</td><td>Steps 1–2 and 4, decided <i>before</i> the data</td><td>Lectures 2, 6, 9–10</td></tr>
<tr><td><b>4.</b> M, SD, n per group; shape; are the SDs similar?</td><td>Step 3's ingredients, plus the test's assumptions</td><td>Lectures 4–5, 8; <b>Lecture 12</b></td></tr>
<tr><td><b>5.</b> t, df, p, 95% CI, Cohen's d, in APA style</td><td>Steps 3–6 with the right <i>t</i> test; how big; how precise</td><td><b>Lectures 11–14</b>, Lecture 10</td></tr>
<tr><td><b>6.</b> Means with SE error bars</td><td>Showing the precision of each mean</td><td>Lectures 8–9, Discussion 6</td></tr>
<tr><td><b>7.</b> Decision, effect size in words, limitations, what next</td><td>Step 6 in plain English; significance vs. size; design and sample</td><td><b>Lecture 11 (today)</b>, Lecture 2</td></tr>
</tbody>
</table>

<p v-click>

- It is **10% of your grade**, and Data Write-Up #2 (ANOVA, due Dec. 8) reuses the same structure, so what you build now you use again.
- It is also what a results section of a real paper looks like: a question committed to in advance, one test, one figure, one honest paragraph about what it does and does not show.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Discussions 8 and 9: where the write-up gets finished

:: left ::

### Discussion 8 — tomorrow (Wed. 10/28)

**First 20 min, worksheet 8:** today's lecture in R.
- Cohen's *d* for the candy data (all 85 candies play the population).
- Why a 1-point IQ difference is "significant" with n = 10,000 but not n = 25.
- **Power by simulation:** a function `power_sim(n, d)` runs 5,000 imaginary studies and counts how often they reject H₀.

**Rest of section, your write-up file:** finish Part 4 (descriptives, histograms, SD check), then **peer review**: another group reads your Parts 1–4 against the rubric, and you read theirs.

:: right ::

### Discussion 9 — Wed. 11/4

**First 20 min, worksheet 9:** all three *t* tests on the Pixar data (single-sample, paired, independent), by hand and with `t.test()`, plus the APA sentence for each.

**Rest of section, your write-up file:** Parts 5–7. Run your test, make your figure, write the interpretation.

<p v-click><StickyNote color="green-light" title="So the plan for the next two weeks" width="100%">Lecture introduces each idea with real data → the next discussion runs it in R → you apply it to your own dataset the same day. Bring your laptop and your group's file to both sections.</StickyNote></p>

<p v-click>

```r
# A taste of tomorrow: power for a medium effect, n = 20
power_sim(n = 20, d = 0.5)
#> [1] 0.61
```

</p>

---
layout: section
color: indigo-light
align: lt
---

Before anything new...
# Finishing Lecture 10: confidence intervals

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Where we stopped: what a confidence interval is

:: left ::

- A sample mean is a **point estimate** of μ: a best single guess, almost never exactly right.
- A ==95% confidence interval== is an **interval estimate**: the values of μ that are plausible given our sample.

$$CI = M \pm 1.96 \times SE$$

- Center the curve on **M**, mark off the middle 95%, convert ±1.96 back to raw scores.

<p v-click><StickyNote color="amber-light" title="What '95%' means" width="100%">About 95% of intervals built this way capture μ. A statement about the <b>procedure</b>, not a 95% chance about this one interval.</StickyNote></p>

:: right ::

<img src="/images/lecture10/ztest_vs_ci.png" alt="The z test centers the curve on mu; the confidence interval centers it on M" class="w-9/12 mx-auto"/>

<p v-click>

- **Same curve, different center.** The z test centers it on μ: did M land in a tail? The CI centers it on M: which values of μ are within 1.96 SEs? So the test rejects exactly when the interval misses μ. That is where we pick up.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Confidence intervals and hypothesis tests agree

:: left ::

Back to Taylor Swift: $M = 57.1$, $n = 24$, $\sigma = 23$, so $SE = 4.69$.

<Admonition title="Question" color="teal-light" width="100%">

Compute the 95% CI for the mean positivity of her songs. Does it contain 51, the mean of all songs?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$57.1 \pm 1.96(4.69) = 57.1 \pm 9.2$ → **47.9 to 66.3**

Yes: 51 is inside the interval. So 51 is a plausible value for her true mean, which matches our test: we failed to reject $H_0$.

</Admonition></p>

:: right ::

<p v-click>

<img src="/images/lecture10/ci_taylor.png" alt="Taylor Swift CI" class="w-full mx-auto"/>

</p>

<p v-click><StickyNote color="amber-light" title="The connection" width="100%">If the 95% CI <b>excludes</b> the null value, a two-tailed test at α = .05 <b>rejects</b> H₀. If it <b>includes</b> the null value, the test fails to reject. The CI also tells you something the test does not: <i>how big</i> the difference might be.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Running a *z* test in R: by hand

:: left ::

Ariana Grande again: do her 43 songs differ in positivity from songs in general?

```r
mu    <- 51   # population mean
sigma <- 23   # population SD

ariana <- filter(songs, artist == "Ariana Grande")
n <- nrow(ariana)
se <- sigma / sqrt(n)
M <- mean(ariana$positivity)
z <- (M - mu) / se
p <- 2 * pnorm(z)
```

<div class="text-base">

- `pnorm(z)` is the area below z. Our z is negative, so that is our tail. `2 *` adds the other tail.

</div>

<p v-click="2"><StickyNote color="amber-light" title="Not exactly our numbers?" width="100%">By hand we got z = −2.17 because we rounded M and the SE along the way. R keeps every decimal. Same decision.</StickyNote></p>

:: right ::

```text
> se
[1] 3.507467
> M
[1] 43.43023
> z
[1] -2.158186
> p
[1] 0.03091335
```

<div v-click="1" class="text-base">

- **se = 3.51**: Step 3. The SD of the distribution of means.
- **M = 43.43**: the sample mean.
- **z = −2.16**: Step 5. Her mean is 2.16 SEs below 51.
- **p = 0.031**: Step 6. Below α = .05, so we reject $H_0$ (Route 2).

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Running a *z* test in R: z.test()

:: left ::

Same test, one function. `z.test()` does every step from the last slide for us.

```r
library(BSDA)   # has z.test()

# ariana = her 43 songs
z.test(ariana$positivity,
       mu = 51, sigma.x = 23)
```

<div class="text-base">

- Give R the sample's scores, the population mean $H_0$ predicts (`mu`), and the population SD (`sigma.x`).
- Same numbers as by hand, plus a CI.

</div>

<p v-click="2"><StickyNote color="amber-light" title="Coming attractions" width="100%">The output of <code>t.test()</code> has this same layout. Learn to read one and you can read the other.</StickyNote></p>

:: right ::

```text
	One-sample z-Test

z = -2.1582, p-value = 0.03091
alternative hypothesis: true mean is not equal to 51
95 percent confidence interval:
 36.55572 50.30474
sample estimates:
mean of x
 43.43023
```

<div v-click="1" class="text-base">

- **z = −2.16**: Step 5. Her mean is 2.16 SEs below 51.
- **p-value = 0.031**: below α = .05, so we reject $H_0$ (Route 2). R prints no alpha and no decision: those are ours.
- **alternative hypothesis**: our $H_1$, a two-tailed test.
- **95% CI**: 36.6 to 50.3. Excludes 51, matching the test.
- **mean of x**: *M* = 43.4.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: confidence intervals

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

You weigh 20 candy bars and find a 95% CI of 57.6 g to 58.4 g. Which interpretation is best?

- **A)** If we repeated this procedure many times, about 95% of the intervals would contain the population mean.
- **B)** 95% of candy bars weigh between 57.6 and 58.4 g.
- **C)** There is a 95% chance that the population mean is between 57.6 and 58.4 g.
- **D)** The population mean is exactly 58 g.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** The confidence is in the procedure. (B) confuses a CI for a mean with the spread of individual scores: that is SD vs. SE again!

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

You repeat the study with 80 candy bars instead of 20. What happens to the 95% CI?

- **A)** It gets wider, because there is more data to cover.
- **B)** It stays the same width, because it is still a 95% interval.
- **C)** It becomes a 99% interval.
- **D)** It gets narrower, because the standard error is smaller.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Width = 2 × 1.96 × SE. Four times the data halves the SE, so the interval is half as wide.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from Lecture 10 (now complete)

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**p value** — the probability of a result at least this extreme *if $H_0$ were true*. Not the probability that $H_0$ is true.

</div>
<div>

**Two routes to a decision** — test statistic beyond the cutoff, or p < α. They always agree.

</div>
<div>

**One-tailed vs. two-tailed test** — all of α in one tail (directional $H_1$) vs. split across both tails.

</div>
<div>

**Point estimate vs. interval estimate** — a single best guess (M) vs. a range of plausible values.

</div>
<div>

**95% confidence interval** — $M \pm 1.96 \times SE$. About 95% of intervals built this way capture μ.

</div>
<div>

**Alpha, critical region, critical value** — alpha is an area chosen in advance (the Type I error rate we accept). The critical region is where that area sits. The critical value is the z score at its edge.

</div>
</div>

---
layout: section
color: indigo-light
align: lt
---

New today...
# Effect size and statistical power

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# A puzzle: the same difference, twice

:: left ::

Taylor Swift's 24 songs: $M = 57.1$, about 6 points happier than the average song ($\mu = 51$, $\sigma = 23$).

- $SE = 23/\sqrt{24} = 4.69$, so $z = 1.30$. **Not significant.**

<p v-click>

Now imagine **240 songs** with exactly the same mean, 57.1.

- $SE = 23/\sqrt{240} = 1.48$, so $z = 4.11$. **Highly significant.**

</p>

<p v-click="4"><StickyNote color="amber-light" title="So what does 'significant' tell us?" width="100%">Only that the difference is probably not zero. With a big enough sample, a <i>tiny</i> difference becomes "significant." Significance says nothing about whether the difference matters.</StickyNote></p>

:: right ::

<img src="/images/lecture11/same_difference_two_n.png" alt="The same 6.1-point difference with n = 24 and n = 240" class="w-full mx-auto"/>

<p v-click="2"><Admonition title="Question" color="teal-light" width="100%">

The difference (6.1 points) is identical in both cases. What changed?

</Admonition></p>

<p v-click="3"><Admonition title="Answer" color="green-light" width="100%">

Only n. More songs → smaller SE → the same difference is more SEs from 51. **Statistical significance depends on sample size.**

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Effect size: how big is the difference?

:: content ::

- An ==**effect size**== measures the **magnitude** of a difference in **standardized units**, so that it:
  - is *unaffected* by sample size (unlike z, t, and p),
  - can be compared across studies that use different scales (points, seconds, dollars, ...),
  - tells us **how much two distributions overlap**: the less overlap, the bigger the effect.

<p v-click>

- The most common effect size for comparing two means is ==**Cohen's *d***==: the difference between the means, divided by the **standard deviation of the individual scores**. *How many SDs apart are the two means?*

$$d = \frac{M_1 - M_2}{SD}$$

</p>

<p v-click><StickyNote color="amber-light" title="Heads up: SD, not SE" width="100%">A test statistic divides by the <b>standard error</b> (spread of <i>means</i>), which shrinks as n grows. Cohen's d divides by the <b>standard deviation</b> (spread of <i>scores</i>), which does not. That is why d does not depend on n.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Effect size for our Spotify artists

:: left ::

For a z test, the two means are the sample mean and the population mean, and the SD is σ:

$$d = \frac{M - \mu}{\sigma}$$

<Admonition title="Question" color="teal-light" width="100%">

Compute d for Taylor Swift ($M = 57.1$), Ariana Grande ($M = 43.4$), and Drake ($M = 38$). $\mu = 51$, $\sigma = 23$.

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- Taylor Swift: $(57.1 - 51)/23 = 0.27$
- Ariana Grande: $(43.4 - 51)/23 = -0.33$
- Drake: $(38 - 51)/23 = -0.57$

Drake's songs are about half a standard deviation less positive than the average song.

</Admonition></p>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

If Taylor Swift had 240 songs with the same mean (our puzzle), what would d be?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Still 0.27. The sample size changed z from 1.30 to 4.11, but d does not contain n anywhere. Same difference, same σ, same effect size.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="The sign" width="100%">Negative d just means the first mean is lower. Report the sign, but judge the <i>size</i> by the absolute value.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Effect size tells us how much two distributions overlap

:: content ::

<img src="/images/lecture11/effect_size_overlap.png" alt="Two distributions at d = 0.2, 0.5, and 0.8" class="w-11/12 mx-auto"/>

<p v-click>

- When $d = 0.2$, the two groups overlap almost completely: knowing someone's group tells you very little about their score.
- When $d = 0.8$, the groups are visibly shifted, but there is still plenty of overlap: many individuals in the lower group score above many in the higher group.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Two ways to make an effect bigger

:: left ::

Overlap shrinks (and d grows) in two ways:

1. The **means move farther apart** (the numerator of d gets bigger).
2. The **scores within each group are less spread out** (the denominator of d gets smaller).

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Two studies both find a 10-point difference between groups. In Study A, the SD of scores is 5. In Study B, it is 20. Which found the larger effect?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Study A: $d = 10/5 = 2.0$ vs. $d = 10/20 = 0.5$. The same raw difference is a huge effect when scores are tightly clustered and a modest one when they are spread out.

</Admonition></p>

:: right ::

<img src="/images/lecture11/effect_size_two_ways.png" alt="Means farther apart or less spread within groups" class="w-full mx-auto"/>

<p v-click>

<img src="/images/lecture9/height_two_distributions.png" alt="Height among US men and NBA players" class="w-4/5 mx-auto"/>

<div class="text-xs text-gray-500">Lecture 9: NBA players (M = 79.1 in, SD = 3.3) vs. U.S. men (M = 69, SD ≈ 3). d = 10.1/3.2 ≈ 3.2, an enormous effect: almost no overlap.</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Conventions for interpreting d

:: left ::

Jacob Cohen (1988) suggested rough benchmarks. They are **guidelines, not cutoffs**: a d of 0.45 is not "medium" and 0.55 "large" in any meaningful way.

<table class="compact-table text-base">
<thead><tr><th>d</th><th>Label</th><th>Cohen's own example</th></tr></thead>
<tbody>
<tr><td><b>0.2</b></td><td>small</td><td>the height difference between 15- and 16-year-old girls</td></tr>
<tr><td><b>0.5</b></td><td>medium</td><td>between 14- and 18-year-old girls (visible to the eye)</td></tr>
<tr><td><b>0.8</b></td><td>large</td><td>between 13- and 18-year-old girls (obvious)</td></tr>
</tbody>
</table>

<div class="text-xs text-gray-500 mt-2">Cohen, J. (1988). <i>Statistical power analysis for the behavioral sciences</i> (2nd ed.). Erlbaum.</div>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Where do our Spotify artists land? Taylor Swift d = 0.27, Ariana Grande d = −0.33, Drake d = −0.57.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Taylor Swift and Ariana Grande: small effects (and Ariana Grande's was statistically significant, Taylor Swift's was not, mostly because of n = 43 vs. n = 24). Drake: a medium effect.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Context beats conventions" width="100%">In medicine, a d of 0.2 for a drug that prevents heart attacks is a big deal. In a lab reaction-time task, a d of 0.8 can be ordinary. Always ask what the difference means <i>in this context</i>.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Significant ≠ big: a real example

:: content ::

<img src="/images/lecture11/spotify_genres_d.png" alt="Rock vs pop positivity and rap vs rock danceability" class="w-11/12 mx-auto"/>

<p v-click>

- **Left:** rock songs are 3 points more positive than pop songs. With about 4,000–5,000 songs per genre, that is highly significant ($p < .001$). But $d = 0.13$: the distributions sit almost exactly on top of each other. You would never notice this difference on a playlist.
- **Right:** rap is 20 points more danceable than rock, $d = 1.43$. *That* you would notice.

</p>

<div class="text-xs text-gray-500 mt-1">Data: Spotify via spotifyr, TidyTuesday (Jan. 2020). The two-group t test comes in Lecture 14; trust R on p for now.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Significant ≠ big: two famous cases

:: left ::

### Height and IQ

- Cohen (1990) used data on **14,000 children**. Height and IQ were significantly correlated.
- But the effect was tiny: a child would need to grow **3.5 feet** to gain 30 IQ points, or gain **233 IQ points** to grow 4 inches.
- Statistically significant. Practically meaningless.

<div class="text-xs text-gray-500 mt-2">Cohen, J. (1990). Things I have learned (so far). <i>American Psychologist, 45</i>(12), 1304–1312.</div>

<p v-click="2"><Admonition title="Question" color="teal-light" width="100%">

The Facebook authors argued that at Facebook's scale, d = 0.001 is "not negligible." Do you buy it?

</Admonition></p>

:: right ::

<p v-click>

### Emotional contagion on Facebook

- In 2014, Facebook ran an experiment on **689,003 users**: for a week, it reduced either the positive or the negative posts in their News Feeds.
- People who saw fewer positive posts wrote slightly fewer positive words (and vice versa). All effects were significant.
- Effect sizes: **d = 0.001 to 0.02**. The largest is one-tenth of Cohen's "small."

<div class="text-xs text-gray-500 mt-2">Kramer, A. D. I., Guillory, J. E., & Hancock, J. T. (2014). <i>PNAS, 111</i>(24), 8788–8790.</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: effect size

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher doubles her sample size and re-runs the same study, finding the same means and SDs. What happens?

- **A)** Both the z statistic and Cohen's d get larger.
- **B)** The z statistic gets larger; Cohen's d stays the same.
- **C)** Cohen's d gets larger; the z statistic stays the same.
- **D)** Both stay the same.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** z divides by the SE, which shrinks with n. d divides by the SD, which does not.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

A study of 50,000 people finds that coffee drinkers score significantly higher on a memory test, $p < .001$, $d = 0.05$. What is the best summary?

- **A)** Coffee has a large effect on memory.
- **B)** The result is probably a Type I error.
- **C)** There is likely a real difference, but it is tiny.
- **D)** The study was underpowered.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** With n = 50,000, even a minuscule difference is detectable. The p value says the difference is probably not zero; d says it is about one-twentieth of a standard deviation.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: Halloween candy (your Discussion 4 data)

:: left ::

Treat the **85 candies as a population**: win percentage $\mu = 50.3$, $\sigma = 14.7$. Two groups from it:

- the 37 candies **with chocolate**: $M = 60.9$
- the 38 **fruity** candies: $M = 44.1$

<Admonition title="Question" color="teal-light" width="100%">

Compute d for each group. Which effect is bigger, and what does the sign mean?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Chocolate: $(60.9 - 50.3)/14.7 = 0.72$, medium-to-large. Fruity: $(44.1 - 50.3)/14.7 = -0.42$, small-to-medium. The negative sign: fruity candies win *less* often than candies in general.

</Admonition></p>

<div class="text-xs text-gray-500 mt-1">Data: Hickey, W. (2017). The ultimate Halloween candy power ranking. <i>FiveThirtyEight</i>.</div>

:: right ::

<img src="/images/lecture11/candy_population_d.png" alt="Win percentage for all 85 candies, fruity candies, and chocolate candies" class="w-11/12 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Reading the picture" width="100%">d = 0.72: the chocolate mean sits 0.72 population SDs above μ. Plenty of overlap remains (Starburst and Skittles beat most chocolate bars). A sizable effect is not a clean separation.</StickyNote></p>

<p v-click><StickyNote color="green-light" title="Your write-up has no σ" width="100%">Two samples, no population: which SD is the denominator? That needs one more idea, the <b>pooled SD</b>, which arrives with the independent-samples t test in Lecture 14.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Cohen's *d* in R (tomorrow's Discussion 8)

:: left ::

No special function needed: lines you already know from Discussion 4.

```r
candy <- read_csv("candy_data.csv")

# All 85 candies play the role of the population
mu    <- mean(candy$winpercent)
sigma <- sd(candy$winpercent)

# Our sample: the candies with chocolate
choc <- filter(candy, chocolate == 1)
M    <- mean(choc$winpercent)

# Cohen's d: how many SDs is M from mu?
d <- (M - mu) / sigma
d
```

:: right ::

```text
[1] 0.7207070
```

<p v-click>

- `mu` and `sigma` describe the population; `M` describes the sample; d is their distance in SD units: $(60.9 - 50.3)/14.7 = 0.72$.
- Tomorrow: the same lines for the **fruity** candies (d = −0.42), then you write it yourself for **sugar content**: are chocolate candies sweeter than candies in general?
- Discussion 9: `t.test()` reports t, df, p, and a CI, but not d. You compute d yourself, with the two-sample version from Lecture 14.

</p>

---
layout: section
color: indigo-light
align: lt
---

From "how big is the effect?" to...
# Statistical Power: would we even find it?

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Four things that can happen in a hypothesis test

:: left ::

There is a true state of the world (we never see it) and a decision we make. That gives four outcomes:

<table class="compact-table text-base">
<thead><tr><th></th><th>H₀ is actually true</th><th>H₀ is actually false</th></tr></thead>
<tbody>
<tr><td><b>We reject H₀</b></td><td class="text-red-700"><b>Type I error</b><br/>false positive<br/>probability = α</td><td class="text-green-700"><b>Correct!</b><br/>true positive<br/>probability = <b>power</b></td></tr>
<tr><td><b>We fail to reject H₀</b></td><td class="text-green-700"><b>Correct</b><br/>true negative<br/>probability = 1 − α</td><td class="text-red-700"><b>Type II error</b><br/>false negative<br/>probability = β</td></tr>
</tbody>
</table>

:: right ::

<p v-click>

- ==**Statistical power**== is the probability of correctly rejecting $H_0$ **when it is false**: the chance that a study detects an effect that really exists.
- Power ranges from 0 to 1. Power $= 1 - \beta$.
- The conventional target is **0.80**: an 80% chance of finding the effect if it is there.

</p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

A study has power = 0.30. The effect it is looking for is real. What happens if the researchers run it?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Seven times out of ten, they fail to reject $H_0$ and conclude (wrongly) that they found nothing. Low power makes "not significant" almost uninformative.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Power in a picture: two worlds, one cutoff

:: content ::

<img src="/images/lecture11/power_two_worlds.png" alt="Null distribution and the distribution when the effect is real, with alpha, beta and power" class="w-9/12 mx-auto"/>

<p v-click>

- **Indigo:** the null world we have been drawing since Lecture 9. Alpha is set here.
- **Amber:** the world where the effect is real. Results in this world are centered on the *true* mean, not on what $H_0$ predicts. The green share lands past the cutoff: that is power. The grey share does not: those are Type II errors.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Power, step 1: draw the null world and its cutoffs

:: left ::

A real example. Suppose Taylor Swift's songs really are about 6 points happier than average: true mean **57.1** ($d = 0.27$). We test **n = 24** songs, α = .05, two-tailed.

1. **Draw the null world**: the distribution of sample means if $H_0$ is true. Center μ = 51, $SE = 23/\sqrt{24} = 4.69$.
2. **Mark the cutoffs**: ±1.96 SEs → $51 \pm 9.2$ → **41.8 and 60.2**. To reject $H_0$, our sample mean has to land beyond one of them.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Before we draw anything else: would you guess the power is high or low?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Low. A d of 0.27 is a small effect and 24 is a small sample. Let's see *how* low.

</Admonition></p>

:: right ::

<img src="/images/lecture11/power_steps_1.png" alt="Null distribution of sample means for n = 24 with the two cutoffs" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Power, step 2: the world where the effect is real

:: left ::

3. **Draw the second world.** If the research hypothesis is true, sample means come from a distribution with the *same* SE (4.69) but centered on the true mean, **57.1**. Shift the curve over by 6.1 points.

- The cutoffs do not move: they were set by the null world and α. Our actual result is one draw from this amber curve.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Look at where the amber curve sits relative to the cutoff at 60.2. Where will most sample means land if the effect is real?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Around 57.1. Most of the amber curve is *below* 60.2: even when the effect is real, most 24-song samples miss the cutoff.

</Admonition></p>

:: right ::

<img src="/images/lecture11/power_steps_2.png" alt="Null distribution and the distribution of sample means if the true mean is 57.1" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Power, step 3: shade past the cutoff

:: left ::

4. **Shade the amber curve beyond the cutoff.** That area is power: the chance that a sample from the real-effect world rejects $H_0$.
5. **Find the area.** The cutoff 60.2 is $(60.2 - 57.1)/4.69 = 0.66$ SEs above the true mean, so power = the area beyond z = 0.66: `1 - pnorm(0.66)` = **0.25**. (The lower cutoff adds almost nothing.)

<p v-click>

- **Power ≈ 0.25**, so **β ≈ 0.75**. Even if her songs really are happier, a 24-song sample finds a significant difference about **one time in four**.

</p>

:: right ::

<img src="/images/lecture11/power_steps_3.png" alt="Power shaded in green beyond the cutoff, beta in grey" class="w-full mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Re-reading our Lecture 10 result" width="100%">We failed to reject H₀ for Taylor Swift. With power of 0.25, that is what we would expect <i>even if the effect is real</i>. "Not significant" here means "we could not tell," not "there is no difference."</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Power, step 4: the puzzle, resolved (n = 240)

:: left ::

Same true mean (57.1), same σ. Only n changed, so only the **SE** changed: $23/\sqrt{240} = 1.48$.

- Both curves get narrower. The cutoffs move in: $51 \pm 2.9$ → **48.1 and 53.9**.
- The amber curve, still centered on 57.1, now sits almost entirely beyond 53.9. **Power ≈ 0.98.**

<p v-click><Admonition title="Question" color="teal-light" width="100%">

How many songs would we need for the usual target, 80% power?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

About **108**. For a small effect, you need a lot of data. (With 24 songs, we never had a fair chance.)

</Admonition></p>

:: right ::

<img src="/images/lecture11/power_steps_4.png" alt="The same two worlds with n = 240: narrow curves, power 0.98" class="w-full mx-auto"/>

<p v-click>

<div class="flex items-center gap-4 mt-2">
<IceCream :size="70" mood="shocked" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">A study with power = 0.25 is like a smoke detector that goes off for one fire in four. You would not trust its silence.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Five things that change power

:: left ::

Power increases when:

1. **Alpha increases** (.05 → .10). *Usually a bad idea*: like widening the goalposts. More Type I errors.
2. **Two-tailed → one-tailed.** Only if you predicted the direction *before* seeing the data.
3. **Sample size increases.** The honest route: more data → smaller SE.
4. **Difference between means increases.** Strong manipulations and extreme groups help.
5. **Variability decreases.** Reliable measures and consistent procedures reduce noise.

:: right ::

<p v-click><StickyNote color="amber-light" title="In the picture" width="100%">Each one either moves the cutoff (1, 2), or narrows the curves (3, 5), or pushes the amber curve farther from the indigo one (4). All three put more of the amber curve past the cutoff.</StickyNote></p>

<p v-click><StickyNote color="green-light" title="Notice" width="100%">Factors 3, 4, and 5 are the ingredients of the test statistic: signal (the difference) ÷ noise (SD/√n). Power is high when the signal-to-noise ratio is high.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Five things that change power, in pictures

:: content ::

<img src="/images/lecture11/power_five_factors.png" alt="Six panels showing how power changes with n, the difference, the SD, alpha, and tails" class="w-11/12 mx-auto"/>

<div class="text-sm text-gray-600 mt-1">Start: a 5-point difference, SD = 10, n = 20, α = .05, two-tailed. Each other panel changes one thing. Green = power.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# How many participants do you need?

:: left ::

It depends on the **effect size** you are trying to detect. For 80% power (α = .05): about **13** participants for a large effect, **32** for a medium one, **200** for a small one.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Most effects in psychology are small to medium, and many published studies have 20–30 participants per group. What does the figure say about them?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Underpowered, unless the effect was large. Button et al. (2013) estimated the **median power in neuroscience at 21%**. Low power means missed effects, and exaggerated effect sizes when something does reach significance.

</Admonition></p>

<div class="text-xs text-gray-500 mt-1">Button, K. S., et al. (2013). Power failure. <i>Nature Reviews Neuroscience, 14</i>, 365–376.</div>

:: right ::

<img src="/images/lecture11/power_curves.png" alt="Power as a function of sample size for small, medium and large effects" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">One-sample z test, α = .05, two-tailed, computed exactly. Tomorrow's <code>power_sim()</code> gets the same numbers by simulation. Comparing two groups needs roughly these numbers <i>per group</i>.</div>

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

<div class="text-sm text-gray-600 mt-1">Tomorrow: <code>power_sim()</code> draws 5,000 fake samples with a real effect and counts how often the z test rejects. Predict the direction of each change before you run it. Exact power numbers come from software. What is fair game for Exam 3 is the picture: draw the two worlds, say where power lives, and say what moves it.</div>

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
# Key terms from today

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

<p v-click><StickyNote color="green-light" title="Coming attractions" width="70%">Thursday: what to do when you do not know σ (which is almost always). The t test is the z test with one ingredient swapped, and effect size comes right back.</StickyNote></p>

---
layout: cover
color: indigo-light
---

# That's all for today!
See you Thursday for parametric assumptions and our first *t* test. Tomorrow in Discussion 8: effect size and power in R, then back to your Data Write-Up.
