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
### Lecture 9: Z-Tables, Percentiles & Building Toward Hypothesis Testing

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
- Reminder: no standalone homeworks this semester. Instead, you'll complete **2 Data Write-Ups** (10% of your grade each):
  - Write-Up 1 (t-test based): due Tuesday, November 17 at 11:59 p.m.
  - Write-Up 2 (ANOVA based): due Tuesday, December 8 at 11:59 p.m.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate)
- Heads up: there is **no class** next Tuesday, October 13 (substitute Monday schedule).


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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standard Normal Distribution Tables

:: content ::

## How can we convert z scores to percentiles?

- Recall, in a normal distribution:
  - z = 0 is the mean (50th percentile)  
  - z = 1 is 1 standard deviation above the mean (~84th percentile)
  - z = -1 is 1 standard deviation below the mean (~16th percentile)
- What if a z score isn't a whole number?  
- We can use a computer program to find the percentile (like we just did!), or:
  - We use a **standard normal table** to find the percentile.  

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Using the Standard Normal (Z) Table

:: left ::

- Z scores are one way to locate a point in the normal curve.  
- A standard normal distribution (or z) table shows the percentile associated with each z score.
- Usually only positive z values are shown.  
- Negative z values are mirror images (the curve is symmetric).
  - Can compute by subtracting percentile from 1.

:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-7/8 mx-auto"/> 



---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Looking Up a Z Score with the Standard Normal Table

:: left ::

## Steps:  

1. Convert raw score to z score.

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Remember how to do this?
</SpeechBubble>

<br> 

2. Use the *row* for the first two digits 
    and the *column* for the second decimal place.
3. Use the *sign* to determine if you need to subtract from 1.
4. Multiply by 100 to get the percentile.


:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-7/8 mx-auto"/> 


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
#  Z Table Practice:

:: left ::

<Admonition title="Question" color="teal-light" width="100%">
What percentile is z = 0.67? BEFORE looking at the table, ask yourself: Should this be above or below 50%?
</Admonition>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Find row 0.6 and column 0.07 → 0.7486  
2. z is positive, so percentile = 0.7486 = **74.86%**  

</Admonition></p>

<Admonition title="Question" color="teal-light" width="100%">
What percentile is z = -.4?
</Admonition>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Find row 0.4 and column 0.0 -> .6554 
2. z is negative, so percentile = 1 - .6554 = .3446 = **34.46%** 

</Admonition></p>


:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-7/8 mx-auto"/> 


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
#  Z Table Practice (More!):

:: left ::

You take the GRE and score 160 on the Verbal section. Across all test takers, Verbal scores have $\mu = 151.4$ and $\sigma = 8.4$, and they are approximately normally distributed.

<Admonition title="Question" color="teal-light" width="100%">
Approximately what proportion of test takers scored lower than you?
</Admonition>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Compute z: $z = (160 - 151.4)/8.4 = 1.02$  
2. Find row 1.0 and column 0.02 → 0.8461  
3. z is positive, so percentile = 0.8461 = **84.61%**. About 85% of test takers scored lower than you.
4. Reality check: ETS reports that a 160 is actually the 82nd percentile. Close, because GRE scores are close to (not perfectly) normal.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: ETS, <i>GRE General Test Interpretive Data</i> (test takers July 2022 to June 2025).</div>


:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-3/4 mx-auto"/> 

<p v-click>
You can also use R to find percentiles!


```r
# Find percentile for z = 1.02
pnorm(1.02)
# [1] 0.8461358
```
</p>

<p v-click><StickyNote color="green-light" title="In discussion section" width="100%">You'll get hands-on practice with pnorm() and percentiles in R — bring your laptop!</StickyNote></p>

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

1. Top 10% means 90% score lower, so look for **.9000** *inside* the table.
2. The closest entry is .8997 → row 1.2, column .08 → $z = 1.28$
3. Convert z back to a raw score: $X = z \times \sigma + \mu = 1.28 \times 8.4 + 151.4 = 162.2$
4. You need about a **162**. (Score → percentile reads the table from the outside in; percentile → score reads it from the inside out.)

</Admonition></p>

:: right ::

<img src="/images/lecture7/z_table.png" alt="Z Table" class="w-7/8 mx-auto"/> 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: z tables

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

For z = 0.50 the table entry is .6915. What proportion of scores fall **above** z = 0.50?

- **A)** .6915
- **B)** .5000
- **C)** 1 − .6915 = .3085
- **D)** .6915 − .5000 = .1915

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** The table gives the area to the *left*. The total area is 1, so the area to the right is 1 minus the table entry.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

What proportion of scores fall **below** z = −0.50?

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

<p v-click><StickyNote color="amber-light" title="Why this matters" width="80%">This question — "how extreme is this result?" — is the engine behind every hypothesis test we'll run for the rest of the course. Z tables are how we answer it precisely.</StickyNote></p>


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
2. Find percentile: row 2.0, column 0.00 → 0.9772 = **97.72%**.
3. 97.72% of men are shorter than z = 2.0  
4. 2.28% of men are taller (100 − 97.72 = 2.28). That is about 1 man in 44.
5. Tall, but not shocking. You probably saw someone that tall today.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: Fryar et al. (2021), CDC/NCHS, <i>Anthropometric reference data: United States, 2015–2018</i>. SD approximated.</div>

:: right ::

<img src="/images/lecture7/z_table_2.gif" alt="Z Table 2" class="w-3/4 mx-auto"/> 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
#  Building an intuition about "extreme" scores

:: left ::

Now consider an NBA center who is 7'4" (88 inches). Same population: U.S. adult men, $\mu = 69$, $\sigma \approx 3$.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
How extreme is a height of 88 inches?
</Admonition>

</p>


<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. Compute z: $z = (88 - 69)/3 = 6.33$.
2. Find percentile: the table stops at 3.4. (**Off the table!**)
3. More than 99.99999% of men are shorter than z = 6.33. A height of 88 inches is *extremely* extreme.
4. We'll come back to this idea later!

</Admonition></p>

<div class="flex items-center gap-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>A z of 6 is so extreme it's not even on the table — scores like that almost never happen by chance!</SpeechBubble>
</div>


:: right ::

<img src="/images/lecture7/z_table_2.gif" alt="Z Table 2" class="w-3/4 mx-auto"/> 

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

$z = (88 - 79.1)/3.3 = 2.70$ → table: .9965. He is taller than 99.65% of NBA players. Still extreme, but now he is *on the table*.

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

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">Same distance from μ, very different z. Means bounce around less than scores, so a <i>mean</i> of 57 is far more surprising than one <i>score</i> of 57. Dividing by σ when you have a mean is a very common Exam 2 mistake.</StickyNote></p>

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

<p v-click="3"><StickyNote color="green-light" title="Coming attractions" width="100%">Next lecture we'll formalize exactly this: the z test, null hypotheses, and what "statistically significant" really means.</StickyNote></p>

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
- The 24 Taylor Swift songs in the dataset: $M = 57.1$
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
Use the z table. If you drew 24 songs at random from all of Spotify, how often would their mean positivity be this high or higher?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Row 1.3, column .00 → .9032. So 1 − .9032 = .0968: about **10% of the time**. Her mean is a bit above average, but a random playlist would do this fairly often. Not very extreme.

</Admonition></p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">Individual song positivity is not normal at all. We can still use the z table, because we are asking about a <i>mean</i>. Thank you, Central Limit Theorem!</SpeechBubble></p>

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
- **D)** The z table.

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
# Key terms from today

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Standard normal (z) table** — gives the proportion of a normal distribution that falls below each z score.

</div>
<div>

**Percentile** — table entry × 100. For a negative z, use 1 − the entry for the positive z.

</div>
<div>

**"Extreme" score** — one far out in a tail, with only a small proportion of scores beyond it.

</div>
<div>

**Comparison distribution** — the distribution we compare our result against. Scores for a single score; *means* for a sample mean.

</div>
<div>

**z for a score:** $z = \frac{X - \mu}{\sigma}$

</div>
<div>

**z statistic for a mean:** $z = \frac{M - \mu}{SE}$, where $SE = \frac{\sigma}{\sqrt{n}}$

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Next time: more on **hypothesis testing**
