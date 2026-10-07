---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 9
exportFilename: ps211_fall2026_lecture9
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 9: Percentiles & Building Toward Hypothesis Testing

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- ==Exam 2== covers Lectures 7-10.
- Exam 2 Review is Tuesday, October 20.
- Exam 2 is Thursday, October 22.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 - 3:30 p.m. (Rola)
- Reminder: there is **no class** Tuesday, October 13 (substitute Monday schedule).


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

**Distribution of sample means** — what you would get by taking many samples of size $n$ and recording each sample's mean.

</div>
<div>

**Central Limit Theorem** — with a large enough $n$, the distribution of sample means is approximately normal, whatever the population looks like.

</div>
<div>

**Standard error (SE)** — the SD of the distribution of sample means.<br/> $SE = \frac{\sigma}{\sqrt{n}}$

</div>
<div>

**SD vs. SE** — SD is the spread of *scores*. SE is the precision of a *mean*. Only the SE shrinks as $n$ grows.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Two lectures ago: z scores for single scores. Last lecture: how sample means behave. Today we put them together, and that gives us our first statistical test.</SpeechBubble>
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

Song lengths on Spotify have σ = 1 minute. You compute the mean length of a random 100-song playlist. What is the standard error of that mean?

- **A)** 1 / 100 = 0.01
- **B)** 1 / √100 = 0.1
- **C)** 1 × √100 = 10
- **D)** 1, the same as σ

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** SE = σ / √n. Playlist means typically land within about 0.1 minutes of the true mean.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Reaction times are positively skewed. You take 1,000 samples of n = 50 people and plot the 1,000 **sample means**. What do you expect?

- **A)** Positively skewed, centered on μ, SD = σ
- **B)** Approximately normal, centered on μ, SD = σ
- **C)** Approximately normal, centered on μ, SD = σ/√50
- **D)** Approximately normal, centered on 0, SD = 1

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** The CLT gives the shape (normal), the mean of the means is μ, and their spread is the standard error.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: SD or SE?

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A researcher wants to tell readers **how much individual students' stress scores differ from one another**. Which should she report?

- **A)** The standard error
- **B)** The standard deviation
- **C)** The sample size
- **D)** The mean

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Spread of individual scores = SD.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

She wants to show **how precisely she has estimated the average stress score**. Which should she report?

- **A)** The standard error
- **B)** The standard deviation
- **C)** The range
- **D)** The median

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Precision of a mean = SE. This is why error bars on a bar plot of means usually show the SE.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: distributions of means

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Scores have σ = 10. You compute the SE for samples of n = 25. Which equation is set up correctly?

- **A)** 10 / 25 = 0.4
- **B)** 10 / √25 = 2
- **C)** 10 × √25 = 50
- **D)** √10 / 25 = 0.13

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** SD divided by the *square root* of n.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

You build one distribution of means from samples of **n = 10**, and another from samples of **n = 100**, drawn from the same population. How do they differ?

- **A)** Same mean; the n = 10 distribution has a smaller SD.
- **B)** Same mean; the n = 10 distribution has a larger SD.
- **C)** Different means and different SDs.
- **D)** They are identical.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Both are centered on μ. Means of small samples bounce around more, so their distribution is wider (larger SE).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Back to last lecture's question: is a mean of 66 unusual?

:: left ::

<Admonition title="Our example: how funny are you?" color="indigo-light" width="100%">

**Null world:** Students know how funny they are. Population parameters of this null world:

$\mu = 50$, $\sigma = 28.9$.

<br/>**The study:** $n = 65$, $M = 66$.

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">

In the null world, what does the distribution of means of 65 students look like? <br>
(1) What shape? <br>
(2) What SE? <br>
(3) How many SEs is 66 from 50? 

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

(1) Approximately **normal** (CLT), even though the individual scores are uniformly distributed. <br>
(2) $SE = 28.9 / \sqrt{65} = 3.6$ <br>
(3) $66 - 50 = 16$ points: more than **4 SEs** above.

</Admonition></p>



:: right ::

<p v-click>

<img src="/images/lecture8/kd_scores_vs_means.png" alt="66 is ordinary for one score but far outside the distribution of means of 65" class="w-4/6 mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Kruger & Dunning (1999), <i>Journal of Personality and Social Psychology, 77</i>(6), Study 1.</div>

</p>

<p v-click><StickyNote color="amber-light" title="Conclusion" width="100%">A mean of 66 almost never happens in the null world, so we can reject the null hypothesis. On average, students <b>overestimate</b> how funny they are.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Putting concepts together

:: left ::

- Are morning people better students? Researchers asked 253 college students whether they are a morning "lark," an evening "owl," or neither, and recorded each student's GPA.

<Admonition title="Question" color="teal-light" width="100%">
What would be a good way to visualize these GPA distributions? Think of two types of plots that could be used for this purpose.
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. **Box plots:** These would allow you to see the median, quartiles, and potential outliers for each group's GPA distribution.
2. **Histograms:** These would show the frequency distribution of GPAs for each group, allowing you to see the shape of the distribution (e.g., normality, skewness).

</Admonition></p>



:: right ::

<Admonition title="Question" color="teal-light" width="100%">
Now imagine you want to compare the mean GPAs of the groups. What would be a good way to quantify your uncertainty in the estimate of these means? How could you visualize the uncertainty in your estimate of the mean GPA for each group?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

You could calculate the **standard error (SE)** for each group's mean GPA.

To visualize the uncertainty in your estimate of the mean GPA for each group, you could use barplots with error bars representing the SE for each group.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: Onyper et al. (2012), <i>Chronobiology International, 29</i>(3).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Putting concepts together (Continued)

:: left ::

# Let's take a look at those plots

<br>

<img src="/images/lecture8/sleepstudy_gpa_barplot.png" alt="Barplot of GPA with error bars" class="w-4/5 mx-auto"/>

:: right ::

<img src="/images/lecture8/sleepstudy_gpa_hist.png" alt="Histograms of GPA" class="w-1/2 mx-auto"/>

<img src="/images/lecture8/sleepstudy_gpa_boxplot.png" alt="Boxplot of GPA" class="w-1/2 mx-auto"/>

<p v-click><StickyNote color="green-light" title="In discussion section" width="100%">You'll practice making plots like these — with error bars — in R during discussion section.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: Reading the error bars

:: left ::

<img src="/images/lecture8/sleepstudy_gpa_barplot.png" alt="Barplot of GPA with error bars" class="w-full mx-auto"/>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">
All three groups have similar SDs (about 0.4 GPA points). So why is the error bar for "Neither" so much smaller?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Sample size. "Neither" has n = 163, so SE = 0.39/√163 = 0.03. Larks have n = 41, so SE = 0.40/√41 = 0.06. Same spread of scores, more data, more precise mean.

</Admonition></p>

<p v-click><Admonition title="Challenge question" color="teal-light" width="100%">

If we repeated this study many times, about what percentage of the time would the error bars (M ± 1 SE) capture the true population mean?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

About 68% of the time: the error bars span ±1 SD of the (normal) distribution of sample means.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Recap: from a z score to a percentile

:: left ::

In a normal distribution, a score's **percentile** is the area under the curve to its left.

- z = 0 → 50th percentile
- z = +1 → about the 84th percentile
- z = −1 → about the 16th percentile

<Admonition title="Question" color="teal-light" width="100%">
What if z is not a whole number, like z = 0.67 or z = −0.4? Before computing anything: is each one above or below the 50th percentile?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

z = 0.67 is above the mean, so its percentile is between 50 and 84. z = −0.4 is below the mean, so its percentile is between 16 and 50. For the exact values, we ask R.

</Admonition></p>

:: right ::

<img src="/images/lecture7/standard_normal_areas.png" alt="Areas under the standard normal curve" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Any z score to a percentile: pnorm()

:: left ::

`pnorm(z)` gives the proportion of the z distribution **below** z.

```r
pnorm(0.67)   # 0.7486, the 75th percentile
pnorm(-0.4)   # 0.3446, the 34th percentile
```

You score 160 on GRE Verbal ($\mu = 151.4$, $\sigma = 8.4$, roughly normal).

<Admonition title="Question" color="teal-light" width="100%">
What proportion of test takers scored lower than you? Higher?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Compute z: $z = (160 - 151.4)/8.4 = 1.02$
2. Lower: `pnorm(1.02)` = 0.846, about **85%**.
3. Higher: `1 - pnorm(1.02)` = 0.154, about **15%**.

</Admonition></p>

:: right ::

<img src="/images/lecture9/pnorm_area_left.png" alt="pnorm gives the area to the left of z" class="w-4/5 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Reality check" width="100%">ETS reports that a 160 is actually the 82nd percentile. GRE scores are close to normal, not perfectly normal.</StickyNote></p>

<div class="text-xs text-gray-500 mt-2">Data: ETS, <i>GRE General Test Interpretive Data</i> (test takers July 2022 to June 2025).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Going backwards: from a percentile to a score

:: left ::

A graduate program says it likes applicants in the **top 10%** on GRE Verbal ($\mu = 151.4$, $\sigma = 8.4$).

<Admonition title="Question" color="teal-light" width="100%">
What score do you need?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Top 10% means **90% score lower**.
2. `qnorm(0.90)` = 1.28. That is the z score with 90% of the distribution below it.
3. Convert z back to a raw score: $X = z \times \sigma + \mu = 1.28 \times 8.4 + 151.4 = 162.2$
4. You need about a **162**.

</Admonition></p>

:: right ::

<img src="/images/lecture9/qnorm_top10.png" alt="qnorm finds the z score for a given area" class="w-5/6 mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Opposites" width="100%"><code>pnorm()</code>: z score → proportion below. <code>qnorm()</code>: proportion below → z score.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: areas under the z distribution

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

`pnorm(0.50)` returns .6915. What proportion of scores fall **above** z = 0.50?

- **A)** .6915
- **B)** .5000
- **C)** 1 − .6915 = .3085
- **D)** .6915 − .5000 = .1915

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** `pnorm()` gives the area to the *left*. The total area is 1, so the area to the right is 1 minus that.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Without using R again: what proportion of scores fall **below** z = −0.50?

- **A)** .6915
- **B)** 1 − .6915 = .3085
- **C)** −.6915
- **D)** .5000 − .6915 = −.1915

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** The curve is symmetric: the area below −0.50 equals the area above +0.50. A proportion can never be negative. Sanity check: a negative z must be below the 50th percentile.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# What about z tables?

:: left ::

- Before computers were everywhere, people looked these areas up in a printed **standard normal (z) table**. Textbooks still include one.
- It holds the same numbers as `pnorm()`. Row = z to one decimal place. Column = the second decimal place.
  - Row 1.0, column .02 → .8461 = `pnorm(1.02)`
- Most tables list only positive z scores. For a negative z, use 1 − the entry.

<p v-click><StickyNote color="amber-light" title="Do people still use these?" width="100%">Rarely. A table is a fallback for when you have no computer. Researchers now get these areas from software, and so will we.</StickyNote></p>

:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-7/8 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# From Z Scores to Hypothesis Testing

:: content ::
- Hypothesis tests ask: ==**How extreme is a score?**==  
- When we start testing hypotheses, we want to know if a score is extreme enough to be considered unusual.
- We can use *z* scores to determine this.
- We will more precisely define what we mean by "extreme" and "unusual" soon.

<p v-click><StickyNote color="amber-light" title="Why this matters" width="80%">This question — "how extreme is this result?" — is the engine behind every hypothesis test we'll run for the rest of the course. A z score and the area beyond it are how we answer it precisely.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
#  Building an intuition about "extreme" scores

:: left ::

Your friend's new boyfriend is 6'3" (75 inches). Among U.S. adult men, height is approximately normal with $\mu = 69$ inches and $\sigma \approx 3$ inches.

<Admonition title="Question" color="teal-light" width="100%">
How "extreme" is a height of 75 inches?
</Admonition>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Compute z: $z = (75 - 69)/3 = 2.0$  
2. Find the percentile: `pnorm(2)` = 0.9772, so **97.7%** of men are shorter.
3. 2.3% of men are taller (100 − 97.7). That is about 1 man in 44.
4. Tall, but not shocking. You probably saw someone that tall today.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: Fryar et al. (2021), CDC/NCHS, <i>Anthropometric reference data: United States, 2015–2018</i>. SD approximated.</div>

:: right ::

<img src="/images/lecture9/height_75_us_men.png" alt="A height of 75 inches among U.S. men" class="w-full mx-auto"/> 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
#  Building an intuition about "extreme" scores

:: left ::

Now consider an NBA center who is 7'4" (88 inches), compared to the same population of U.S. adult men.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
How extreme is a height of 88 inches?
</Admonition>

</p>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Compute z: $z = (88 - 69)/3 = 6.33$.
2. Area beyond it: `1 - pnorm(6.33)` = 0.0000000001
3. On this curve, about **1 man in 8 billion** is that tall. That is *extremely* extreme.
4. We'll come back to this idea later!

</Admonition></p>

:: right ::

<img src="/images/lecture9/height_88_us_men.png" alt="A height of 88 inches among U.S. men" class="w-4/5 mx-auto"/>

<div class="flex items-center gap-4">
<IceCream :size="70" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>The curve is nearly flat by z = 3. A z of 6 almost never happens by chance!</SpeechBubble>
</div> 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Extreme compared to what?

:: left ::

Same 7'4" player. But now compare him to **other NBA players** (2018–19 season: $\mu = 79.1$ inches, $\sigma = 3.3$).

<Admonition title="Question" color="teal-light" width="100%">
What is his z score now? How extreme is he?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$z = (88 - 79.1)/3.3 = 2.70$ and `pnorm(2.70)` = .9965. He is taller than 99.65% of NBA players. Still extreme, but no longer off the charts.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Why this matters" width="100%">The same score can be wildly extreme in one distribution and only fairly unusual in another. "How extreme?" always means "compared to which distribution?" In hypothesis testing this is called the <b>comparison distribution</b>.</StickyNote></p>

:: right ::

<img src="/images/lecture9/height_two_distributions.png" alt="Height among US men and NBA players" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: NBA player heights, 2018–19 season (openintro R package, n = 494); U.S. men from CDC/NCHS (Fryar et al., 2021).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Two kinds of z: one score vs. one mean

:: left ::

Is **one score** extreme? Compare it to the distribution of **scores**:

$$z = \frac{X - \mu}{\sigma}$$

<p v-click>

Is a **sample mean** extreme? Compare it to the distribution of **means**:

$$z = \frac{M - \mu}{SE}, \quad SE = \frac{\sigma}{\sqrt{n}}$$

</p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">Same distance from μ, very different z. Means bounce around less than scores, so a <i>mean</i> of 57 is far more surprising than one <i>score</i> of 57. Dividing by σ when you have a mean is a very common mistake.</StickyNote></p>

:: right ::

<img src="/images/lecture9/two_kinds_of_z.png" alt="z for a score vs z for a mean" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: "valence" (musical positivity, rescaled 0–100) of 28,356 Spotify songs: μ = 51, σ = 23.</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Z Statistics for Distribution of *Means*

:: content ::
If we want to think about the *z* statistic for a **group**, we need to change a few things:

1. We use ==means== instead of raw scores.
2. We calculate the mean and ==standard error== for the distribution of means.
3. Then we calculate a *z* statistic for the sample mean.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
When might this be useful?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**All the time!**

*We often want to know if a sample is different from a population.*

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Example: Dating Profiles

:: left ::
Researchers are studying online dating profile ratings.
- They have a sample of 30 profiles from Rhode Island (RI).
- RI sample (n=30): $M = 2.84$
- U.S. population: $\mu = 2.5$, $SD = 0.833$  
- **Is the RI sample mean different from the U.S. mean?**

:: right ::
<Admonition title="Question" color="teal-light" width="100%">
What is the standard error for the distribution of means?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$SE = SD/\sqrt{n} = 0.833/\sqrt{30} \approx 0.152$

</Admonition></p>

<Admonition title="Question" color="teal-light" width="100%">
What does this standard error tell us?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

A typical sample mean computed from samples of size $n=30$ will be about 0.152 away from the population mean ($\mu$) of 2.5.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Dating Profiles (Continued)

:: left ::
Researchers are studying online dating profile ratings.
- They have a sample of 30 profiles from Rhode Island (RI).
- RI sample (n=30): $M = 2.84$
- U.S. population: $\mu = 2.5$, $SD = 0.833$  
- **Is the RI sample mean different from the U.S. mean?**

<p v-click="3"><StickyNote color="green-light" title="Coming up today" width="100%">After a little more practice, we'll formalize exactly this: the z test, null hypotheses, and what "statistically significant" really means.</StickyNote></p>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">
How would we calculate a z statistic to determine how "extreme" the RI sample mean is?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Calculate standard error: $SE = 0.833/\sqrt{30} \approx 0.152$
2. Calculate z statistic for the sample mean, using the population mean and standard error:

$z = (M - \mu) / SE$

$z = (2.84 - 2.5) / 0.152 \approx 2.24$

</Admonition></p>


<p v-click>
The RI sample mean is more than 2 standard errors above the U.S. mean.  

We need to conduct a formal hypothesis test to determine if this difference is **statistically significant**.  
</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Are Taylor Swift's songs happier than average?

:: left ::
Spotify scores every song's **positivity** ("valence"): 0 = sad or angry, 100 = happy and cheerful.
- All 28,356 songs: $\mu = 51$, $\sigma = 23$
- Her 24 songs in the dataset: $M = 57.1$
- **Is a mean of 57.1 extreme for a sample of 24 songs?**

<Admonition title="Question" color="teal-light" width="100%">
Compute the standard error, then the z statistic for her sample mean.
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

$SE = 23/\sqrt{24} = 4.69$

$z = (57.1 - 51)/4.69 = 1.30$

</Admonition></p>

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
If you drew 24 songs at random from all of Spotify, how often would their mean positivity be this high or higher?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

`pnorm(1.30)` = .9032. So 1 − .9032 = .0968: about **10% of the time**. Her mean is a bit above average, but a random playlist would do this fairly often. Not very extreme.

</Admonition></p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">Individual song positivity is not normal at all. We can still use the z distribution, because we are asking about a <i>mean</i>. Thank you, Central Limit Theorem!</SpeechBubble></p>

<div class="text-xs text-gray-500 mt-2">Data: Spotify Web API via spotifyr; TidyTuesday (January 2020), so only her songs through 2019.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: z for a sample mean

:: left ::

All Spotify songs: positivity $\mu = 51$, $\sigma = 23$. The 68 Drake songs in the dataset have $M = 38$.

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Your friend computes z = (38 − 51) / 23. What is wrong?

- **A)** Nothing. That is the right place to start.
- **B)** The numerator should be 51 − 38.
- **C)** The denominator should be 23/√68, because we are asking about a mean, not a single score.
- **D)** The denominator should be 23 − 1, because this is a sample.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** For a sample mean, divide by the **standard error**: z = (38 − 51)/(23/√68) = −13/2.79 = −4.66.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

What is the correct **comparison distribution** for Drake's sample mean?

- **A)** The distribution of positivity scores for all 28,356 songs.
- **B)** The distribution of positivity scores for Drake's 68 songs.
- **C)** The distribution of means of all possible 68-song samples.
- **D)** The distribution of song lengths for all 28,356 songs.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** A mean gets compared to a distribution of *means*, built from samples of the same size. It is centered on μ = 51 and its SD is the SE, 2.79.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: Hypotheses

:: content ::
- **Null hypothesis ($H_0$):** There is no real difference. The populations from which samples are drawn are the same / equal. Any observed difference is due to chance.

==The goal of hypothesis testing is to determine how likely our sample data would be if the null hypothesis were true.==

**We do statistics to either: reject or fail to reject the null hypothesis.**

We do not "prove" that the null hypothesis is true. We can only fail to reject it if we don't have enough evidence against it.

*Absence of evidence is not evidence of absence. There could still be a difference that we just didn't detect.*

<p v-click>

- **Research hypothesis or alternative hypothesis ($H_1$):** What the researcher expects to find. Sometimes states the direction of the effect (e.g., group A will have a higher mean than group B).

*The research hypothesis is the hypothesis that would be true if the null hypothesis is false.*

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Hypothesis Testing

:: content ::
- We use statistics to formally test hypotheses.
- Statistical analyses are based on certain assumptions about the dataset.
- ==Statistical assumptions== describe the ideal conditions for hypothesis testing. (More on this later!)
- We want to ensure these assumptions are (mostly) met so that we can make accurate inferences.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The logic behind every hypothesis test

:: content ::

Every test in this course, from today through December, runs on the same three ideas:

1. **Assume nothing is going on.** Pretend the null hypothesis is true.
2. **Picture the "null world."** If $H_0$ were true and we ran this study thousands of times, what results would we get? That is the **comparison distribution**.
3. **Find our result in that world.** If a result like ours would be very rare in the null world, we stop believing in the null world: we reject $H_0$.

<p v-click>

And every test statistic is the same kind of number:

$$\text{test statistic} = \frac{\text{what we observed} - \text{what } H_0 \text{ predicts}}{\text{how much results bounce around by chance}}$$

</p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="40rem">Signal divided by noise. For a z test: the signal is M − μ, and the noise is the standard error. The six steps just organize this logic so that nothing gets skipped.</SpeechBubble></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six Steps of Hypothesis Testing: at a glance

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

<p v-click><StickyNote color="amber-light" title="Why the order matters" width="100%">Steps 1 to 4 come <i>before</i> you look at your result. Choosing the cutoff after seeing the data is like drawing the target around the arrow.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 1: Populations, comparison distribution, and assumptions

:: content ::

**The question:** Who is being compared, and which test fits?

**In every test:**
- Name the **populations** being compared: the one your sample represents, and the one you compare it to.
- Name the kind of **comparison distribution**. This is what picks the test.
- Check the test's **assumptions**. (More on this later!)

**In a z test:** we compare one sample *mean* to a population whose μ and σ we know. A mean gets compared to a **distribution of means**.

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

Population 1: all Rhode Island profiles. Population 2: all U.S. profiles. We have a sample **mean** (n = 30) and we know the U.S. μ and σ, so the comparison distribution is a **distribution of means**, and the test is a **z test**.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 2: Null and research hypotheses

:: content ::

**The question:** What are the two competing claims?

**In every test:**
- $H_0$ says nothing is going on: the populations do not differ. $H_1$ says they do.
- Both are claims about **populations**, not samples. We already know what our sample did. We want to make inferences about populations!
- Decide now whether $H_1$ names a direction (one-tailed) or not (two-tailed).

**In a z test:** $H_0$: $\mu_1 = \mu_2$. &nbsp; $H_1$: $\mu_1 \neq \mu_2$ (or $<$, or $>$).

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

$H_0$: RI profiles are rated the same as U.S. profiles on average: $\mu_{RI} = 2.5$. &nbsp; $H_1$: they are rated differently: $\mu_{RI} \neq 2.5$ (non-directional, so two-tailed).

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 3: Characteristics of the comparison distribution

:: content ::

**The question:** If $H_0$ were true, what results would we expect?

**In every test:**
- The comparison distribution is the "null world": the results we would get if $H_0$ were true.
- Step 1 *named* it. Step 3 *describes* it with numbers: its **center** (what $H_0$ predicts), its **spread** (how much results bounce around by chance), and its **shape**.

**In a z test:** center = $\mu$. &nbsp; Spread = $SE = \sigma/\sqrt{n}$. &nbsp; Shape = normal.

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

If $H_0$ is true, means of 30 profiles are normally distributed with center $\mu_M = 2.5$ and $SE = 0.833/\sqrt{30} = 0.152$.

</Admonition></p>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">In later tests, the shape also depends on a number called <i>degrees of freedom</i>. Same step, one more number.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Step 4: Critical values (cutoffs)

:: left ::

**The question:** How extreme is extreme enough?

**In every test:**
- Choose ==alpha==: the proportion of the null world we will call "extreme." The standard in psychology is .05, or 5%.
- The ==critical value== is the test statistic that marks off that proportion. The area beyond it is the **critical region**.
- Two-tailed test: split alpha across both tails (2.5% in each). One-tailed test: put all of it in one tail.

**In a z test:** the cutoffs are z scores.

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

α = .05, two-tailed → 2.5% in each tail → critical values of **−1.96 and +1.96**. In R: `qnorm(0.975)` = 1.96.

</Admonition></p>

:: right ::

<img src="/images/lecture7/z_critical.png" alt="Critical Regions" class="w-full mx-auto"/>

<p v-click><StickyNote color="amber-light" title="Reading the picture" width="100%">A test statistic in a pink tail is in the critical region: reject H₀. Anywhere in the green: fail to reject.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 5: Test statistic

:: content ::

**The question:** How far is our result from what $H_0$ predicts, compared to chance?

**In every test:**

$$\text{test statistic} = \frac{\text{what we observed} - \text{what } H_0 \text{ predicts}}{\text{how much results bounce around by chance}}$$

- Signal divided by noise. Both pieces of the null world come from Step 3.
- This is the first step that uses our sample's result.

**In a z test:** $z = (M - \mu)/SE$

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

$z = (M - \mu)/SE = (2.84 - 2.5)/0.152 = 2.24$. The RI mean is 2.24 standard errors above what $H_0$ predicts.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 6: Decision

:: content ::

**The question:** Is our result past the cutoff, and what do we conclude?

**In every test:**
- Test statistic beyond the cutoff → **reject $H_0$**. The result is ==statistically significant==.
- Test statistic not beyond the cutoff → **fail to reject $H_0$**. We never "accept" it.
- Then say what that means in plain English, in terms of the study.

**Statistically significant**: Data are more extreme than what we would expect by chance if there truly were no actual difference.

<p v-click><Admonition title="Our example: dating profiles" color="indigo-light" width="100%">

2.24 is beyond +1.96, so we **reject $H_0$**. In plain English: Rhode Island profiles are rated significantly higher than U.S. profiles on average.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from today

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-2 text-sm">
<div>

**`pnorm()` and `qnorm()`** — `pnorm(z)` gives the proportion below z (its percentile). `qnorm(p)` gives the z score with proportion p below it.

</div>
<div>

**z statistic for a mean** — $z = \frac{M - \mu}{SE}$, where $SE = \frac{\sigma}{\sqrt{n}}$. For one score, divide by σ instead.

</div>
<div>

**Comparison distribution** — what results would look like if $H_0$ were true (the "null world"). For a sample mean, a distribution of *means*.

</div>
<div>

**Alpha (α)** — the proportion of the null world we call "extreme," chosen in advance (usually .05).

</div>
<div>

**Critical value / critical region** — the cutoff(s) on the comparison distribution, and the tail area beyond them. Two-tailed, α = .05: ±1.96.

</div>
<div>

**Test statistic** — signal ÷ noise: how far our result is from what $H_0$ predicts, compared to chance.

</div>
<div>

**Statistically significant** — test statistic beyond the cutoff, so we reject $H_0$.

</div>
<div>

**Six steps** — populations and test, hypotheses, comparison distribution, cutoffs, test statistic, decision.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Next time: **p values**, more hypothesis testing practice, and **confidence intervals**
