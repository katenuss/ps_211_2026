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
layout: section
color: indigo-light
align: lt
---

Before anything new...
# Finishing Lecture 12: the single-sample *t* test

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

Tomorrow's worksheet runs all three *t* tests on the Pixar data from Discussions 1–3. The first is a single-sample test: Rotten Tomatoes calls a film "Fresh" at 60 or above. **Is the average Pixar film's score different from 60?**

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

23 films − 1. $t = 9.89$ is far beyond the cutoff for df = 22 (±2.07), and p = 0.0000000015 → reject: Pixar films average well above "Fresh" (89, CI 83 to 95). How to write a p value like that properly comes later today (APA style).

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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from Lecture 12 (now complete)

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

<p v-click><StickyNote color="green-light" title="Coming attractions" width="70%">Next: the same test for <b>before-and-after</b> designs (the paired-samples t test), plus how to write up any result in APA style.</StickyNote></p>

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
  Just now: the sleeping drug, body temperature. (The drug's "extra hours of sleep" were difference scores already: drug night − no-drug night.)
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

Hickey's second finding: each film's page showed its stars and, hidden in the page code, its actual average rating. Paired test on the 146 films: stars shown (*M* = 4.09, *SD* = 0.54) vs. actual rating (*M* = 3.85, *SD* = 0.50), *t*(145) = 19.30, *p* < .001, *d* = 1.60, 95% CI \[0.22, 0.27]. Write the APA sentence.

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
