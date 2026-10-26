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
columns: is-5-7
---

:: title ::
# Our example: a memory experiment

:: left ::

So far: one sample vs. a **known population**. Usually there is none, just **two samples**.

Friendly & Franklin (1980): participants learned a **40-word list** over several study-then-recall trials.

- **Standard order (SFR, n = 10):** reshuffled every trial.
- **Recalled words first (n = 10):** each new trial showed the words you had just recalled first, then the ones you missed.

==Does seeing your recalled words first help you learn the rest?==

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
# Step 3: the standard error of the difference, in three moves

:: content ::

1. **Pool the two variances.** Combine $s_1^2$ and $s_2^2$ into one ==pooled variance==, a weighted average (weighted by df, because the groups can have different sizes). Our best single estimate of the population variance.

$$s^2_{pooled} = \frac{df_1}{df_{total}}\, s^2_1 + \frac{df_2}{df_{total}}\, s^2_2, \qquad df_1 = n_1 - 1,\ df_2 = n_2 - 1,\ df_{total} = df_1 + df_2$$

<p v-click>

2. **Turn it into the variance of a mean, twice, and add.** Each group's mean has variance $s^2_{pooled}/n$. A *difference* between two independent means wobbles more than either mean alone, so the two uncertainties add:

$$s^2_{difference} = \frac{s^2_{pooled}}{n_1} + \frac{s^2_{pooled}}{n_2}$$

</p>

<p v-click>

3. **Take the square root:** $SE_{difference} = \sqrt{s^2_{difference}}$. This is the spread of the null world.

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
# Worked example: ten people per group

:: left ::

<table class="compact-table text-xs">
<thead><tr><th>Standard order</th><th>X − M</th><th>(X − M)²</th><th>Recalled first</th><th>X − M</th><th>(X − M)²</th></tr></thead>
<tbody>
<tr><td>39</td><td>8.7</td><td>75.69</td><td>40</td><td>3.4</td><td>11.56</td></tr>
<tr><td>25</td><td>−5.3</td><td>28.09</td><td>38</td><td>1.4</td><td>1.96</td></tr>
<tr><td>37</td><td>6.7</td><td>44.89</td><td>39</td><td>2.4</td><td>5.76</td></tr>
<tr><td>25</td><td>−5.3</td><td>28.09</td><td>37</td><td>0.4</td><td>0.16</td></tr>
<tr><td>29</td><td>−1.3</td><td>1.69</td><td>39</td><td>2.4</td><td>5.76</td></tr>
<tr><td>39</td><td>8.7</td><td>75.69</td><td>24</td><td>−12.6</td><td>158.76</td></tr>
<tr><td>21</td><td>−9.3</td><td>86.49</td><td>30</td><td>−6.6</td><td>43.56</td></tr>
<tr><td>39</td><td>8.7</td><td>75.69</td><td>39</td><td>2.4</td><td>5.76</td></tr>
<tr><td>24</td><td>−6.3</td><td>39.69</td><td>40</td><td>3.4</td><td>11.56</td></tr>
<tr><td>25</td><td>−5.3</td><td>28.09</td><td>40</td><td>3.4</td><td>11.56</td></tr>
<tr><td><b>M₁ = 30.3</b></td><td></td><td><b>SS₁ = 484.1</b></td><td><b>M₂ = 36.6</b></td><td></td><td><b>SS₂ = 256.4</b></td></tr>
</tbody>
</table>

<p v-click><Admonition title="Steps 1 and 2" color="green-light" width="100%">

**1.** Two separate groups, one score each → independent-samples *t* test. Words recalled is numeric; spreads are similar-ish (SDs 7.3 and 5.3); n = 10 per group is small, so we lean on normality.

**2.** $H_0$: $\mu_1 = \mu_2$. &nbsp; $H_1$: $\mu_1 \neq \mu_2$ (two-tailed).

</Admonition></p>

:: right ::

<p v-click><Admonition title="Step 3: describe the null world" color="green-light" width="100%">

Each group's variance: its SS ÷ its df (9):

- Standard order: $s_1^2 = 484.1/9 = 53.8$
- Recalled first: $s_2^2 = 256.4/9 = 28.5$

Pool (equal n, so just average): $s^2_{pooled} = (53.8 + 28.5)/2 = 41.1$

$$SE_{difference} = \sqrt{\frac{41.1}{10} + \frac{41.1}{10}} = \sqrt{8.23} = 2.87$$

Null world: center 0, spread 2.87, *t* with df = 10 + 10 − 2 = 18.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Check the pooling" width="100%">41.1 sits between 28.5 and 53.8, as a pooled variance always must. If yours does not, something went wrong.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Steps 4, 5, and 6

:: left ::

<Admonition title="Step 4" color="green-light" width="100%">

df = 18, α = .05, two-tailed → `qt(0.975, 18)` → cutoffs **±2.101**.

</Admonition>

<p v-click><Admonition title="Step 5" color="green-light" width="100%">

$$t = \frac{M_2 - M_1}{SE_{difference}} = \frac{36.6 - 30.3}{2.87} = 2.20$$

</Admonition></p>

<p v-click><Admonition title="Step 6" color="green-light" width="100%">

2.20 **is** beyond 2.101 → **reject $H_0$**. Route 2: p = .041. Showing people their recalled words first helped them learn the rest.

</Admonition></p>

<p v-click><Admonition title="CI and effect size" color="green-light" width="100%">

CI: $6.3 \pm 2.101 \times 2.87$ → **\[0.3, 12.3]** words. Excludes 0, barely.

$d = 6.3 / \sqrt{41.1} = 6.3/6.41 = 0.98$: a large effect.

</Admonition></p>

:: right ::

<img src="/images/lecture14/null_world_recall.png" alt="t distribution with df = 18, cutoffs, and the observed t" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The effect is large (d ≈ 1) and significant, yet the CI runs from a third of a word to twelve words. What does that tell us?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The study is precise enough to say the method helps, not how *much*. With 10 per group, power for an effect this size is only about **0.55**: a near coin flip. A replication could easily land on "not significant." Small samples give wide intervals.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# The same test in R: t.test(..., var.equal = TRUE)

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

- **t = 2.20, df = 18**: exactly our hand computation. R put `before` first, so the difference is 36.6 − 30.3.
- **p-value = 0.041** < .05 → **reject $H_0$**.
- **95% CI**: the true benefit is plausibly **0.3 to 12.3 words**. R prints seven decimals; report two.
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

Musicians: $s_1 = 55.8$; non-musicians: $s_2 = 89.4$.

<div class="text-xs text-gray-500 mt-1">Data: AudioVisual, Stat2Data R package (Cannon et al., <i>Stat2</i>).</div>

:: right ::

<img src="/images/lecture14/musicians_rt_dots.png" alt="Reaction times for musicians and non-musicians" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Where does df = 34 come from? What is the decision? And with unequal n, how do you get the pooled variance for d?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

13 + 23 − 2. p = .007 → reject: musicians were about 79 ms faster. Weight each variance by its df: $s^2_{pooled} = (12 \times 55.8^2 + 22 \times 89.4^2)/34 = 6{,}263$, so $s_{pooled} = 79.1$ and $d = 78.5/79.1 = 0.99$. (Simply averaging the variances would give 1.05: close here, wrong in general.)

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# What if you forget var.equal = TRUE?

:: left ::

R's default is **Welch's *t* test**, which does *not* assume equal variances. It uses each group's own variance in the SE and adjusts the df downward (usually to a decimal).

```r
t.test(musician$rt, nonmusician$rt)   # no var.equal
```

<p v-click>

- Same decision, different numbers: $t = -3.24$, df = 33.6, $p = .003$ (vs. $-2.86$, 34, $.007$). The two differ most when the SDs *and* the ns differ, as here. For the recall study (equal n) Welch gives t = 2.20, df = 16.4: nearly identical.
- Welch is a perfectly good test; many statisticians prefer it. We use `var.equal = TRUE` because it matches the formulas we learn and the df is a whole number.

</p>

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

<p v-click><StickyNote color="amber-light" title="How to tell which you ran" width="100%">The first line of the output says <b>Welch</b>, and the df is not a whole number. If you see that in your write-up output, add <code>var.equal = TRUE</code> and re-run.</StickyNote></p>

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

<Admonition title="Question" color="teal-light" width="100%">

Set up Steps 1–4, then compute $SE_{difference}$, t, and d. (Hints: $s_1^2 = 53{,}304{,}601$, $s_2^2 = 74{,}528{,}689$, $1/210 + 1/186 = 0.01014$.)

</Admonition>

:: right ::

<img src="/images/lecture14/mehl_words_per_day.png" alt="Distributions of words per day for women and men" class="w-11/12 mx-auto"/>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**1–2.** Two separate groups → independent-samples *t*. $H_0$: $\mu_W = \mu_M$; $H_1$: $\mu_W \neq \mu_M$.
**3.** $s^2_{pooled} = (209 \times 53{,}304{,}601 + 185 \times 74{,}528{,}689)/394 = 63{,}270{,}226$; $s_{pooled} = 7{,}954$; $SE = \sqrt{63{,}270{,}226 \times 0.01014} = 801$.
**4.** df = 394 → ±1.97. **5.** $t = 546/801 = 0.68$. **6.** Not beyond 1.97; p = .50 → **fail to reject**. $d = 546/7{,}954 = 0.07$; 95% CI \[−1,029, 2,121].

</Admonition></p>

<div class="text-xs text-gray-500 mt-1">Mehl, M. R., Vazire, S., Ramírez-Esparza, N., Slatcher, R. B., & Pennebaker, J. W. (2007). Are women really more talkative than men? <i>Science, 317</i>, 82.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Interpreting the talkativeness result

:: left ::

<Admonition title="Question" color="teal-light" width="100%">

Does this study show that men and women talk the same amount?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Not quite: we never accept $H_0$. What it shows is that any difference is **tiny**: $d = 0.07$, and the CI says the true difference is somewhere between women talking ~1,000 words *less* and ~2,100 words *more* per day, out of about 16,000. The 20,000-vs-7,000 claim (a difference of roughly $d = 1.6$) is ruled out completely.

</Admonition></p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

n = 396 is a decent sample. Why was it not enough to detect a difference, if one exists?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

For d = 0.07, power with these ns is about **0.11**. Detecting an effect that small with 80% power would take about 3,250 people *per group*. The study was more than adequate for the question that mattered: is the difference large?

</Admonition></p>

:: right ::

<p v-click><StickyNote color="amber-light" title="Two kinds of null results" width="100%"><b>Pixar before vs. after 2010 (Discussion 9):</b> not significant, but d = 0.72 and a CI from −2 to +22 points. "We could not tell." <br/><b>Mehl et al.:</b> not significant, d = 0.07, CI tightly around 0. "If there is a difference, it is small." Same decision, opposite lessons. The CI and d are what separate them.</StickyNote></p>

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="70" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">The most talkative participant said about 47,000 words a day; the least talkative, about 500. Both were men.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# CI and effect size for independent samples

:: left ::

Same recipe, with the independent-samples ingredients:

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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Worksheet time!

:: content ::

- The shared worksheet walks you through the steps of an independent-samples *t* test, by hand and then in R.
- Work through it with a partner or small group.
- We will go over the solution together in the review session.

<p v-click><StickyNote color="amber-light" title="Checklist for the by-hand part" width="70%">Means of both groups → variance of both groups → pooled variance → SE<sub>difference</sub> → df = n₁ + n₂ − 2 → cutoff → t → decision → CI and d.</StickyNote></p>

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
