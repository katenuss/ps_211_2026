---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 10
exportFilename: ps211_fall2026_lecture10
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 10: Hypothesis Testing with Z & Confidence Intervals

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- ==Exam 2== covers Lectures 7-10 — that means today's lecture is the last new material before the exam!
- Exam 2 Review is next Tuesday, October 20.
- Discussion 7 is Wednesday, October 21: Exam 2 review & R practice (hypothesis testing & confidence intervals).
- Exam 2 is next Thursday, October 22.

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

**Comparison distribution** — what results would look like if $H_0$ were true (the "null world").

</div>
<div>

**Alpha (α)** — the proportion of the null world we call "extreme," chosen in advance (usually .05).

</div>
<div>

**Critical value** — the cutoff on the comparison distribution. Two-tailed, α = .05: ±1.96.

</div>
<div>

**Test statistic** — signal ÷ noise. For a z test, $z = \frac{M - \mu}{SE}$.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Last time we built the six steps of a hypothesis test. Today we slow down on Steps 4 and 6 (alpha, critical regions, critical values, and p values), then practice, then confidence intervals.</SpeechBubble>
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

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

IQ scores have μ = 100 and σ = 15. A sample of n = 25 students has M = 106. Which equation gives the z statistic for this sample mean?

- **A)** (106 − 100) / 15 = 0.4
- **B)** (106 − 100) / (15 / √25) = 2.0
- **C)** (106 − 100) / (15 / 25) = 10
- **D)** (100 − 106) / √25 = −1.2

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** It is a *mean*, so divide by the standard error: 15/√25 = 3.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

`pnorm(2.0)` returns .9772. If the students were really just a random sample from the general population, how often would a sample mean land this far **above** μ?

- **A)** About 98% of the time
- **B)** About 50% of the time
- **C)** About 2% of the time
- **D)** Never

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** 1 − .9772 = .0228. Rare, but not impossible. Is "about 2% of the time" rare enough to conclude these students are different? That is the question a hypothesis test answers.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Recap: the six steps of hypothesis testing

:: content ::

<table class="compact-table text-base">
<thead><tr><th></th><th>Step</th><th>The question</th><th>For a z test</th></tr></thead>
<tbody>
<tr><td rowspan="4"><b>Before looking at the result</b></td><td><b>1.</b> Populations, comparison distribution, assumptions</td><td>Who is being compared, and which test fits?</td><td>One sample mean vs. a population with known μ and σ</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td>What are the two competing claims?</td><td>H₀: μ₁ = μ₂ &nbsp; H₁: μ₁ ≠ μ₂ (or &lt;, &gt;)</td></tr>
<tr><td><b>3.</b> Characteristics of the comparison distribution</td><td>If H₀ were true, what results would we expect?</td><td>Center μ, spread SE = σ/√n, normal shape</td></tr>
<tr><td><b>4.</b> Critical values</td><td>How extreme is extreme enough?</td><td>α = .05, two-tailed → ±1.96</td></tr>
<tr><td rowspan="2"><b>With the result</b></td><td><b>5.</b> Test statistic</td><td>How far is our result from what H₀ predicts, compared to chance?</td><td>z = (M − μ) / SE</td></tr>
<tr><td><b>6.</b> Decision</td><td>Is it past the cutoff? What do we conclude?</td><td>Reject or fail to reject H₀, then say it in plain English</td></tr>
</tbody>
</table>

<p v-click><Admonition title="Last time: dating profiles" color="indigo-light" width="100%">

RI sample (n = 30, $M = 2.84$) vs. the U.S. ($\mu = 2.5$, $\sigma = 0.833$): $SE = 0.152$, so $z = 2.24$. That is beyond +1.96, so we **rejected $H_0$**.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Alpha: how rare is "too rare"?

:: left ::

- Even when $H_0$ is true, a few sample means land far from what it predicts, just by chance.
- So before we look at our data, we set a rule: how rare must a result be before we stop believing in the null world?
- ==Alpha (α)== is that rule: the **proportion** of the null world we agree to call "extreme." The convention in psychology is α = .05.

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">Alpha is an <b>area</b> (a proportion), not a z score. And it is a <b>choice</b> we make before the study, not something we compute from the data.</StickyNote></p>

:: right ::

<img src="/images/lecture10/alpha_null_world.png" alt="Alpha as the most extreme 5% of the null world" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">
Suppose H₀ really is true and we use α = .05. How often will our result land in the red anyway?
</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

5% of the time. Rejecting H₀ when it is true is a ==Type I error== (a false positive), so alpha is the Type I error rate we agree to accept.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Critical region: where alpha lives

:: left ::

- The ==critical region== is the part of the comparison distribution that alpha marks off. If our test statistic lands there, it counts as "extreme," and we reject $H_0$.
- Its total area is always α. Its **location** depends on the research hypothesis:

<table class="compact-table text-base">
<thead><tr><th>Research hypothesis</th><th>Test</th><th>Critical region (α = .05)</th></tr></thead>
<tbody>
<tr><td>H₁: μ₁ ≠ μ₂ (different)</td><td>two-tailed</td><td>2.5% in each tail</td></tr>
<tr><td>H₁: μ₁ &gt; μ₂ (higher)</td><td>one-tailed</td><td>5% in the upper tail</td></tr>
<tr><td>H₁: μ₁ &lt; μ₂ (lower)</td><td>one-tailed</td><td>5% in the lower tail</td></tr>
</tbody>
</table>

<p v-click><Admonition title="Question" color="teal-light" width="100%">
Why does a two-tailed test put 2.5% in each tail, and not 5% in each?
</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The total has to stay at α = .05. Either direction counts as extreme, so the two tails share the 5%.

</Admonition></p>

:: right ::

<img src="/images/lecture10/critical_regions_three.png" alt="Critical regions for two-tailed and one-tailed tests" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Critical values: the edge of the critical region

:: left ::

- Alpha is an area. To use it, we need to know where on the x-axis that area begins.
- The ==critical value== is the z score at the edge of the critical region: the cutoff our test statistic has to pass.
- R finds it with `qnorm()`: which z score has this much area below it?

<table class="compact-table text-base">
<thead><tr><th>α</th><th>Test</th><th>Ask R</th><th>Critical value(s)</th></tr></thead>
<tbody>
<tr><td>.05</td><td>two-tailed</td><td><code>qnorm(0.975)</code></td><td>−1.96 and +1.96</td></tr>
<tr><td>.05</td><td>one-tailed, upper</td><td><code>qnorm(0.95)</code></td><td>+1.645</td></tr>
<tr><td>.05</td><td>one-tailed, lower</td><td><code>qnorm(0.05)</code></td><td>−1.645</td></tr>
<tr><td>.01</td><td>two-tailed</td><td><code>qnorm(0.995)</code></td><td>−2.58 and +2.58</td></tr>
</tbody>
</table>

<p v-click><Admonition title="Question" color="teal-light" width="100%">
We switch from α = .05 to α = .01. What happens to the critical values? Is it now easier or harder to reject H₀?
</Admonition></p>

:: right ::

<img src="/images/lecture10/critical_values_alpha.png" alt="Critical values for alpha .05 and .01" class="w-full mx-auto"/>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

They move farther from 0 (±2.58). The critical region is smaller, so a result has to be more extreme to land in it: harder to reject. That means fewer Type I errors, but more missed real effects (Type II errors).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: alpha, critical regions, critical values

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher plans a two-tailed z test with α = .05. Which statement is correct?

- **A)** The critical value is z = .05.
- **B)** The critical values are the z scores that cut off the most extreme 2.5% in each tail: ±1.96.
- **C)** The critical values are the z scores that cut off 5% in each tail: ±1.645.
- **D)** The critical values cannot be found until she computes her sample mean.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Alpha is an area, not a z score, so A is wrong. The two tails share the 5%, so C is wrong. Cutoffs are set before the data, so D is wrong.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

You predict that dating profiles with a dog in the photo are rated **higher** than profiles in general (H₁: μ₁ > μ₂). With α = .05, where is the critical region?

- **A)** The highest 5% of the comparison distribution.
- **B)** The highest 2.5% and the lowest 2.5%.
- **C)** The lowest 5% of the comparison distribution.
- **D)** The middle 95% of the comparison distribution.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** A directional hypothesis puts all of alpha in the tail it predicts. The cutoff is z = +1.645.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# P values

:: content ::
- The *p* value is the probability of obtaining results at least as extreme as ours if the null hypothesis is true.
- A smaller *p* value indicates stronger evidence against the null hypothesis.

<img src="/images/lecture7/p_val_meme.jpg" alt="P value meme" class="w-1/6 mx-auto"/>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">The p value is NOT the probability that the null hypothesis is true — it's the probability of data this extreme <i>if</i> the null were true. This distinction trips people up constantly, including professional researchers!</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Finding a p value, step by step

:: left ::

Alpha and the critical value are set in advance. The ==p value== comes from our data: it is the area **beyond our test statistic**.

Dating profiles: $z = 2.24$, two-tailed test.

1. Find the area beyond our z in its own tail: `1 - pnorm(2.24)` = .0125
2. A two-tailed test counts results this extreme in **either** direction, so add the matching area in the other tail: .0125
3. $p = .0125 + .0125 = .025$

<p v-click><StickyNote color="amber-light" title="In plain English" width="100%">If RI profiles were really rated the same as U.S. profiles, a sample mean this far from 2.5 would turn up about 2.5% of the time.</StickyNote></p>

:: right ::

<img src="/images/lecture10/p_value_area.png" alt="The p value as the area beyond the test statistic in both tails" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">
What if we had predicted in advance that RI profiles are rated <i>higher</i> (a one-tailed test)? What would the p value be?
</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Only the upper tail counts, so p = .0125. No doubling.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Four terms, one picture

:: left ::

<table class="compact-table text-base">
<thead><tr><th></th><th>Set <b>before</b> the data</th><th>Computed <b>from</b> the data</th></tr></thead>
<tbody>
<tr><td><b>A point</b> on the x-axis<br/>(a z score)</td><td>Critical value<br/>±1.96</td><td>Test statistic<br/>z = 2.24</td></tr>
<tr><td><b>An area</b> under the curve<br/>(a proportion)</td><td>Alpha<br/>.05</td><td>p value<br/>.025</td></tr>
</tbody>
</table>

- Compare the two **points**: is our z beyond the critical value?
- Or compare the two **areas**: is our p smaller than alpha?

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">Never compare a point to an area. "z = 2.24 is bigger than .05" does not mean anything.</StickyNote></p>

:: right ::

<img src="/images/lecture10/p_vs_alpha.png" alt="The p value compared with alpha for two examples" class="w-11/12 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Two routes to the same decision

:: content ::

In Step 6 you can compare **z statistics** or compare **probabilities**. They always agree.

<div class="grid grid-cols-2 gap-6 mt-2 text-base">
<div class="border-2 border-red-300 bg-red-50 rounded-lg p-4">

### Route 1: critical values

- Compare your **test statistic** to the **cutoff**.
- Dating profiles: $z = 2.24$ is beyond $1.96$ → reject $H_0$.
- This is how we work by hand.

</div>
<div class="border-2 border-indigo-300 bg-indigo-50 rounded-lg p-4">

### Route 2: p values

- Compare your **p value** to **alpha**.
- Dating profiles: area beyond $z = 2.24$ is $.0125$ in each tail, so $p = .025 < .05$ → reject $H_0$.
- This is what R reports, and what you will write in your Data Write-Ups.

</div>
</div>

<p v-click><StickyNote color="amber-light" title="They are the same comparison" width="100%">The cutoff ±1.96 is just the z score that leaves .05 in the tails. If your z is past the cutoff, your p is below alpha, every time.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: before or after the data?

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which of these does a researcher choose **before** collecting any data?

- **A)** The p value
- **B)** The test statistic
- **C)** Alpha and the critical values
- **D)** The sample mean

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Alpha, the number of tails, and so the critical values are part of the plan (Steps 2 and 4). The sample mean, the test statistic, and the p value all come from the data.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

A two-tailed z test gives z = −2.40. R reports that `pnorm(-2.40)` is .0082. What is the p value, and what do you decide with α = .05?

- **A)** p = .0082; reject H₀.
- **B)** p = .0164; reject H₀.
- **C)** p = .0164; fail to reject H₀, because p is less than alpha.
- **D)** p = .9918; fail to reject H₀.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Two tails, so double the tail area: 2 × .0082 = .0164. That is less than .05, so reject. (With α = .01, it would not be small enough.)

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: p values

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

You run a two-tailed z test and find p = .20. What does this mean?

- **A)** There is a 20% chance that the null hypothesis is true.
- **B)** There is a 20% chance that the research hypothesis is true.
- **C)** If the null hypothesis were true, there is a 20% chance of getting a sample mean at least as extreme as yours.
- **D)** 20% of your participants showed the effect.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** A p value is always a statement about the *data, assuming the null is true*. It is never the probability that a hypothesis is true.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

With α = .05, what should you conclude from p = .20?

- **A)** Reject H₀; the result is statistically significant.
- **B)** Fail to reject H₀; we did not find evidence of a difference.
- **C)** Accept H₀; we have shown there is no difference.
- **D)** Nothing; p values cannot be interpreted without a t test.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** p is larger than alpha, so the result is not extreme enough to reject H₀. But we never "accept" or "prove" the null: absence of evidence is not evidence of absence.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: Santa's Cookies (a one-tailed test)

:: left ::
- Santa Claus claims that the average bag of gingerbread cookies weighs 500g, and the standard deviation across cookie bags is 30g.
- *You are not sure whether what Santa is saying is true. You decide to test a hypothesis that the average weight of one bag of cookies is LESS than 500g.*
- You weigh a sample of 25 bags. Their mean weight is 485 g.

<img src="/images/lecture7/santa_cookies.png" alt="Santa Cookies" class="w-1/2 mx-auto"/>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">
Is this difference extreme enough to reject the null hypothesis, with an alpha level of .05? Start with Steps 1 to 4. Careful: your research hypothesis is <i>directional</i>.
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**Step 1.** Santa's bags vs. the population he claims (μ = 500, σ = 30). We have a sample mean and a known σ → distribution of means, **z test**.

**Step 2.** $H_0$: Average weight of one bag of cookies = 500g. &nbsp; $H_1$: Average weight of one bag of cookies < 500g.

**Step 3.** If $H_0$ is true, means of 25 bags are centered on 500 with $SE = 30/\sqrt{25} = 6$.

**Step 4.** α = .05, **one-tailed**: all 5% goes in the lower tail, so the cutoff is $z = -1.645$.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Santa's Cookies: Steps 5 and 6

:: left ::

<Admonition title="Question" color="teal-light" width="100%">
Compute the test statistic, then make the decision by both routes.
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**Step 5.** $z = (485 - 500)/6 = -2.5$

**Step 6, Route 1.** $-2.5$ is beyond our cutoff of $-1.645$, so we reject $H_0$.

**Step 6, Route 2.** `pnorm(-2.5)` gives the area below our *z* score: $.0062$. One tail, so no doubling: $p = .0062 < .05$, and we reject $H_0$.

Santa's bags weigh significantly less than 500 g on average.

</Admonition></p>

<p v-click>

<AdmonitionType type="warning" width="100%">
Be careful when moving back and forth between decimals and percents! .05 = 5%, but .0062 = .62%
</AdmonitionType>

</p>

:: right ::

<p v-click="1">

<img src="/images/lecture10/null_world_santa.png" alt="Null distribution for Santa's cookies with the one-tailed critical region and the p value" class="w-11/12 mx-auto"/>

</p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">A one-tailed test puts the whole 5% in one tail, so the cutoff is closer to the center (−1.645 instead of −1.96). You must choose the direction <i>before</i> seeing the data.</StickyNote></p>

<div class="flex items-center gap-4">
<IceCream :size="52" mood="blissful" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>Sorry, Santa.</SpeechBubble>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice with real data: Ariana Grande

:: left ::

Spotify scores every song's **positivity** ("valence"): 0 = sad or angry, 100 = happy and cheerful.
- All 28,356 songs in the dataset: $\mu = 51$, $\sigma = 23$
- The 43 Ariana Grande songs in the dataset: $M = 43.4$

==Does the positivity of Ariana Grande's songs differ from that of songs in general?==

<Admonition title="Question" color="teal-light" width="100%">
Work through all six steps with your neighbors (α = .05, two-tailed). You can use a calculator.
</Admonition>

<div class="text-xs text-gray-500 mt-2">Data: Spotify Web API via the spotifyr R package; compiled for TidyTuesday (January 2020), so songs through 2019 only.</div>

:: right ::

<p v-click><Admonition title="Answer: Steps 1 to 4" color="green-light" width="100%">

**1.** Ariana Grande's songs vs. all songs. Sample mean, known μ and σ → distribution of means, z test.

**2.** $H_0$: $\mu_{AG} = 51$. &nbsp; $H_1$: $\mu_{AG} \neq 51$.

**3.** Center = 51, $SE = 23/\sqrt{43} = 3.51$.

**4.** α = .05, two-tailed → cutoffs ±1.96.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice with real data: Ariana Grande (Continued)

:: left ::

<Admonition title="Answer: Steps 5 and 6" color="green-light" width="100%">

**5.** $z = (43.4 - 51)/3.51 = -2.17$

**6.** −2.17 is beyond −1.96 → **reject $H_0$**. Her songs are significantly less positive than songs in general.

Route 2 gives the same answer: `pnorm(2.17)` = .9850, so $p = 2 \times .0150 = .03 < .05$.

</Admonition>

<p v-click><Admonition title="Question" color="teal-light" width="100%">
What if we had chosen α = .01 (cutoffs ±2.58) before looking?
</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

−2.17 is not beyond −2.58, so we would **fail to reject**. Same data, different decision. This is why alpha must be set in advance.

</Admonition></p>

:: right ::

<img src="/images/lecture10/null_world_ariana.png" alt="Null distribution with Ariana Grande's sample mean" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Multiple choice practice: Taylor Swift

:: left ::

The 24 Taylor Swift songs have $M = 57.1$, so $z = 1.30$ and $p = .19$ (two-tailed).

<Admonition title="Multiple choice" color="teal-light" width="100%">

With α = .05, what is the best conclusion?

- **A)** Her songs are significantly more positive than average.
- **B)** We have shown her songs are exactly as positive as average.
- **C)** We did not find evidence that her songs differ from average.
- **D)** There is a 19% chance that the null hypothesis is true.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** 1.30 is not beyond 1.96, so we fail to reject $H_0$. That is not proof of $H_0$ (B), and p is never the probability that $H_0$ is true (D).

</Admonition>

:: right ::

<img src="/images/lecture10/null_world_taylor.png" alt="Null distribution with Taylor Swift's sample mean" class="w-full mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Point estimates vs. interval estimates

:: content ::

- The best estimate of a population parameter is the corresponding sample statistic. This is called a ==point estimate.==
- However, a point estimate is unlikely to be exactly equal to the population parameter.
- For example, the best estimate of the population mean is the sample mean, but the sample mean is unlikely to be exactly equal to the population mean.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Point estimates vs. interval estimates (Continued)

:: content ::

- To account for this uncertainty, we can compute a range of values that is likely to contain the population parameter. This is called an ==interval estimate.==

<img src="/images/lecture8/point_estimate.jpg" alt="Point vs Interval Estimate" class="w-1/2 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Example: Point estimates vs. interval estimates

:: content ::

- *You ask parents of middle schoolers how many hours their child spends on homework each week. You collect data from a sample of 50 parents. On average, parents report that their child spends 10 hours on homework each week.*
- This is your ==point estimate== of the population mean. For example, you might report, "The average middle schooler spends 10 hours on homework each week."
- But how confident are you that this is the true population mean? You can compute an ==interval estimate== to provide a range of values that likely contains the population mean.
- Your interval estimate might be something like: 9 to 11 hours. You might report, "The average middle schooler spends between 9 and 11 hours on homework each week."

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
But how do we compute this interval estimate?
</Admonition>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Confidence Intervals

:: content ::
- A common type of interval estimate is a ==confidence interval.==
- A confidence interval is the range of values within which a population parameter is estimated to fall.
- A confidence interval is usually expressed in terms of a percentage, such as 95% or 99%. This percentage is called the ==confidence level.==
- A 95% confidence interval means that if we were to take many samples and compute a 95% confidence interval for each sample, then approximately 95% of those intervals would contain the true population parameter.

<img src="/images/lecture8/head_explode.jpeg" alt="Head explode" class="w-1/6 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Confidence Intervals (Continued)

:: content ::
- When we compute a 95% confidence interval, we are *not* saying that there is a 95% probability that the population parameter falls within our specific interval. The population parameter is fixed; it either falls within our interval or it does not.
- We **are** saying that we expect to find the population mean within this interval 95% of the time when we conduct the same study with the same sample size

<img src="/images/lecture8/head_explode.jpeg" alt="Head explode" class="w-1/8 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Heads up" width="60%">This subtle interpretation point is a classic exam question — in this course and beyond!</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# What does "95% confident" mean? A simulation

:: left ::

- Population: 28,356 Spotify songs, true mean positivity $\mu = 51$ (dashed line).
- We drew **100 different random samples** of 25 songs and built a 95% CI from each.

<p v-click>

- **95 of the 100 intervals captured μ.** Five (red) missed.
- The "95%" describes the **procedure**: it produces an interval that captures μ about 95% of the time.

</p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">In real research you get <i>one</i> interval, and you never find out whether it is a blue one or a red one. μ is fixed; it is the intervals that bounce around.</StickyNote></p>

:: right ::

<img src="/images/lecture10/ci_100_intervals.png" alt="100 confidence intervals" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Spotify Web API via the spotifyr R package; compiled for TidyTuesday (January 2020).</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Calculating confidence intervals with *z* distributions

:: content ::

You have: 
- Sample mean (M): E.g., 10 hours of homework per week
- Sample size (n): E.g., 50 middle schoolers
- Population standard deviation (SD): E.g., 2 hours

*Note: This is rare in practice! We will learn how to handle unknown population SDs later in the course.*

<br>

You want:
- ==95% Confidence interval (CI)== around the sample mean. 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::

# Calculating confidence intervals with *z* distributions (Continued)

:: left ::

1. Assume your **sample** mean lies in the center of a normal distribution.
2. Determine the area under the normal curve that corresponds to your desired confidence level (e.g., 95%).
- For a 95% CI, this is .95. This leaves .05 in the tails, or .025 in each tail. From this, you can determine the bounds of the CI.
- For a 95% CI, the upper bound is .975. The lower bound is .025.

:: right ::

<img src="/images/lecture10/ci_step_center.png" alt="A normal curve centered on the sample mean with the middle 95% shaded" class="w-5/6 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Why center it on M?" width="100%">We do not know μ, and M is our best estimate of it. Sample means typically miss μ by about one SE, so that is the spread.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::

# Calculating confidence intervals with *z* distributions (Continued)

:: left ::

3. Find the corresponding *z* scores for these bounds using `qnorm()`.
- For the upper bound (.975), the *z* score is approximately 1.96.
- For the lower bound (.025), the *z* score is approximately -1.96.
4. Convert the z statistic to raw scores. 
- Use the formula: $M \pm z \times SE$, where $SE = SD/\sqrt{n}$. (The interval is centered on the **sample** mean.)

5. Now we have our 95% CI!

:: right ::

<img src="/images/lecture10/ci_step_bounds.png" alt="The bounds of the interval at z = -1.96 and z = +1.96, converted to raw scores" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::

# Confidence intervals: finishing the example

:: left ::

You have: $M = 10$ hours, $n = 50$, $\sigma = 2$ hours. You want a 95% CI.

<Admonition title="Question" color="teal-light" width="100%">
Compute the standard error, then the lower and upper bounds of the 95% confidence interval.
</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

- $SE = \sigma/\sqrt{n} = 2/\sqrt{50} = 0.28$
- Lower bound: $M - 1.96 \times SE = 10 - 1.96(0.28) = 9.45$
- Upper bound: $M + 1.96 \times SE = 10 + 1.96(0.28) = 10.55$
- **95% CI: 9.45 to 10.55 hours**

</Admonition>

<p v-click>

$$CI = M \pm z_{crit} \times SE$$

</p>

:: right ::

<p v-click="1">

<img src="/images/lecture10/ci_homework.png" alt="The 95% confidence interval for the homework example, from 9.45 to 10.55 hours" class="w-11/12 mx-auto"/>

</p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="40rem">Look at what sets the width: the standard error. A larger sample means a smaller SE, which means a narrower interval and a more precise estimate.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Why do 95% of these intervals capture μ?

:: left ::

1. **95% of sample means land within 1.96 SEs of μ.** That is what ±1.96 marks off: the middle 95% of the distribution of means.
2. **Distance works both ways.** If M is within 1.96 SEs of μ, then μ is within 1.96 SEs of M.
3. **So M ± 1.96 SE reaches μ whenever M landed in the middle 95%.** That happens for 95% of samples.

<p v-click><StickyNote color="amber-light" title="And the other 5%?" width="100%">Sometimes a sample mean lands in a tail, and its interval misses μ. With one sample, we cannot tell which kind we drew.</StickyNote></p>

:: right ::

<img src="/images/lecture10/ci_why_95.png" alt="Intervals built around sample means in the middle 95% reach the population mean; an interval built around a sample mean in the tail misses" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Each dot is one sample's mean. Each bar is that sample's interval, M ± 1.96 SE.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# z test vs. CI: same curve, different center

:: left ::

**z test.** Center the curve on **μ**, the value $H_0$ predicts. Ask: did our M land in the middle 95%, or in a tail?

**Confidence interval.** Center the same curve on **M**, the value we observed. Ask: which values of μ are within 1.96 SEs of it?

- Ariana Grande: $M = 43.4$, $\mu = 51$, $SE = 3.51$, so $1.96 \times SE = 6.9$.
- Same SE, same ±1.96. Only the center changes.

<p v-click><StickyNote color="amber-light" title="Why they must agree" width="100%">M is more than 1.96 SEs from μ exactly when μ is more than 1.96 SEs from M. So the test rejects exactly when the interval misses.</StickyNote></p>

:: right ::

<img src="/images/lecture10/ztest_vs_ci.png" alt="The z test centers the curve on mu; the confidence interval centers it on M" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Spotify Web API via the spotifyr R package; compiled for TidyTuesday (January 2020).</div>

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
---

:: title ::
# Multiple choice practice: confidence intervals

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

You weigh 20 candy bars and find a 95% CI of 57.6 g to 58.4 g. Which interpretation is best?

- **A)** There is a 95% chance that the population mean is between 57.6 and 58.4 g.
- **B)** 95% of candy bars weigh between 57.6 and 58.4 g.
- **C)** If we repeated this procedure many times, about 95% of the intervals would contain the population mean.
- **D)** The population mean is exactly 58 g.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** The confidence is in the procedure. (B) confuses a CI for a mean with the spread of individual scores: that is SD vs. SE again!

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

You repeat the study with 80 candy bars instead of 20. What happens to the 95% CI?

- **A)** It gets wider, because there is more data to cover.
- **B)** It gets narrower, because the standard error is smaller.
- **C)** It stays the same width, because it is still a 95% interval.
- **D)** It becomes a 99% interval.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Width = 2 × 1.96 × SE. Four times the data halves the SE, so the interval is half as wide.

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
layout: cover
color: indigo-light
---

# That's all for today!
Next up: **Exam 2 Review** on Tuesday, October 20 — then **Exam 2** on Thursday, October 22. Bring your questions!
