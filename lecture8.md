---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 8
exportFilename: ps211_fall2026_lecture8
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 8: The Central Limit Theorem & Standard Error

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

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

**Normal distribution** — bell-shaped, symmetric, unimodal.

</div>
<div>

**Standardization** — putting scores from different distributions on a common scale.

</div>
<div>

**z score** — how many SDs a score is from the mean.<br/> $z = \frac{X - \mu}{\sigma}$

</div>
<div>

**z distribution** — mean = 0, SD = 1, same shape as the raw scores.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">A z score answers one question: how unusual is this <i>one score</i>, compared to the other scores in its distribution?</SpeechBubble>
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

College students sleep M = 8 hours per night, SD = 1 hour. Your friend sleeps 6.5 hours. Which equation gives her z score?

- **A)** (8 − 6.5) / 1 = 1.5
- **B)** 6.5 / 8 = 0.81
- **C)** (6.5 − 8) / 1 = −1.5
- **D)** (6.5 − 1) / 8 = 0.69

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Score minus mean, divided by SD. She is below the mean, so z is negative.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

On an exam, your z score is +0.2. On a quiz, your z score is −1.4. Which is true?

- **A)** You did better on the quiz, because 1.4 is bigger than 0.2.
- **B)** You were slightly above average on the exam and well below average on the quiz.
- **C)** You got 20% on the exam.
- **D)** You cannot compare them, because exams and quizzes use different scales.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** The sign tells you above or below the mean; the size tells you how far, in SDs. Comparing across scales is exactly what z scores are for.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Today's question

:: content ::

- Last time: how unusual is **one score**? → compare it to the distribution of *scores*.
- But psychologists rarely care about one person. We study **groups**, and we summarize a group with its **mean**.

<p v-click>

- So the question becomes: how unusual is a **sample mean**?
- To answer that, we need to know how sample means behave: what shape their distribution has, where it is centered, and **how spread out it is**.

</p>

<p v-click><StickyNote color="amber-light" title="Today's plan" width="100%">1. The Central Limit Theorem: the <i>shape</i> of a distribution of sample means.<br/>2. Why sample variance divides by N − 1.<br/>3. The standard error: the <i>spread</i> of a distribution of sample means.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Central Limit Theorem

:: content ::
- ==The theorem:== Any **distribution of sample means** will be approximately normal if the sample size is sufficiently large.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What is a "distribution of sample means"?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

A "distribution of sample means" is the distribution of the means of multiple samples taken from a population. It shows how the sample means vary and allows us to make inferences about the population mean.

</Admonition></p>

<p v-click>

**Example:** We want to estimate the average height of all PS 211 students. Each class, we measure the height of 5 randomly selected students and calculate the mean height of those 5 students. We repeat this process many times, each time selecting a new random sample of 5 students and calculating the mean height. The distribution of these sample means will be approximately normal, even if the original distribution of individual heights is not normal.
</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Central Limit Theorem: Demo

:: left ::
# Dice Rolls
- Imagine rolling a 6-sided die.
- Roll it once, record the result.
- Repeat many times, plot the distribution of results.

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What does this distribution look like?
</Admonition>

</p>

<p v-click>

<img src="/images/lecture6/dice_roll_hist.png" alt="Dice rolls 1" class="w-full mx-auto"/>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The distribution is ==uniform==, with each outcome (1-6) equally likely.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Central Limit Theorem: Demo (Continued)

:: left ::
# Sampling Dice Rolls
- Now imagine randomly selecting two rolls from this distribution.
- Compute their mean.
- Repeat many times, plot the distribution of means.

<div class="flex items-center gap-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>And this works no matter what shape the original distribution has — that's what makes the Central Limit Theorem so powerful!</SpeechBubble>
</div>

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What does the distribution of means look like?
</Admonition>

</p>

<p v-click>

<img src="/images/lecture6/dice_roll_mean_hist.png" alt="Dice roll means" class="w-full mx-auto"/>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

As the sample size increases, the distribution of means approaches a normal distribution, even though the original distribution is uniform!

</Admonition></p>




---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Central Limit Theorem with real data: Spotify

:: content ::

- Spotify scores every song's **popularity** from 0 to 100. Across 28,356 songs (grey), the distribution is **not normal**: look at the spike of songs nobody plays.
- Draw a random sample of songs, compute its **mean** popularity, repeat 10,000 times (blue).

<img src="/images/lecture8/songs_clt.png" alt="CLT with Spotify popularity" class="w-5/6 mx-auto"/>

<p v-click>

- As $n$ grows, the means look more **normal**, stay **centered on μ** (dashed line), and get **narrower**.

</p>

<div class="text-xs text-gray-500">Data: Spotify Web API via the spotifyr R package; compiled for TidyTuesday (January 2020).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Distribution of Scores vs. Means

:: left ::

- Even if scores in a population aren’t normally distributed, the distribution of sample means will be approximately normal if the sample size is large enough.
- This is the essence of the Central Limit Theorem.
- A distribution of means is **less variable** than a distribution of raw scores.
- This means it is less spread out.

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why is the distribution of means less variable than the distribution of raw scores?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The distribution of means is less variable because averaging reduces the impact of extreme values. When we take the mean of a sample, we are essentially smoothing out the variability that exists in individual scores.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Central Limit Theorem: Video Explanation

:: content ::
Let's watch someone else explain this!

https://www.youtube.com/watch?v=YAlJCEDH2uY


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: the Central Limit Theorem

:: left ::

Song popularity on Spotify is **not** normally distributed.

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

You randomly sample **100 songs** and make a histogram of their 100 popularity scores. What shape do you expect?

- **A)** Normal, because of the Central Limit Theorem.
- **B)** About the same odd shape as the population.
- **C)** Uniform.
- **D)** Impossible to say.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** A sample of *scores* looks like the population it came from. The CLT is not about scores.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Now you sample 100 songs, record their **mean**, and repeat this 5,000 times. You make a histogram of the 5,000 means. What shape do you expect?

- **A)** Approximately normal.
- **B)** About the same odd shape as the population.
- **C)** Uniform.
- **D)** Impossible to say.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** The CLT is about the distribution of **sample means**. With n = 100, it will be very close to normal, whatever the population looks like.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">This is the most common CLT mistake: a bigger sample does not make the <i>scores</i> normal. It makes the distribution of <i>means</i> normal.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Recall: Sample variance uses N − 1

:: left ::

<AdmonitionType type="info" width="100%">Back in Lecture 5 we said: if your data are a sample, divide by N − 1. Now that you have seen how sample statistics behave across many samples, we can see why.</AdmonitionType>

- The formula for the variance of a **sample** is:

$$s^2 = \frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1}$$

<p v-click>

*What changed from the population formula?*

1. We use $M$ (the sample mean) instead of $\mu$ (the population mean).
2. We divide by $N-1$ instead of $N$. 
3. We use $s^2$ (the sample variance) instead of $\sigma^2$ (the population variance).

</p>

:: right ::


<p v-click>

**Why do we divide by N-1 instead of N?**

<img src="/images/lecture4/but_why.png" alt="why" class="mx-auto w-1/2" />

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Sample statistics are estimates

:: left ::

- We almost never have the whole population. We have a sample, and we use it to **estimate** the population's parameters:
  - The sample mean $M$ is our estimate of $\mu$
  - The sample variance $s^2$ is our estimate of $\sigma^2$
- A good estimate is **unbiased**: any single sample might land too high or too low, but ==across many samples, the estimates average out to the true value.==

<p v-click>

- **The mean passes this test.** Take a sample, compute $M$; repeat thousands of times — exactly what we just did with the dice. The $M$s scatter around $\mu$, but they center on it. So the best guess for $\mu$ is simply $M$. No correction needed.

</p>

:: right ::

<p v-click>

<img src="/images/lecture8/n1_means_unbiased.png" alt="sample means center on the population mean" class="mx-auto w-full" />

</p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">If we compute the variance of a sample the same way we did for a population (deviations from M, divided by N), is that an unbiased estimate of σ²?</Admonition>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The variance estimate is biased. Why?

:: left ::

<Admonition title="Answer" color="green-light" width="100%">

No. Computed that way, the sample variance is ==systematically too small==. It's a **biased** estimate of $\sigma^2$.

</Admonition>

<p v-click>

- The culprit is $M$. We measure deviations from the **sample** mean because we don't know $\mu$.
- But $M$ is computed *from these very scores*, so it sits right in the middle of them: it is the point that makes their squared deviations as small as possible. $\mu$ is somewhere else, so deviations from $\mu$ would be larger.

</p>

<p v-click>

- The sum of squared deviations from $M$ is **always ≤** the sum from $\mu$, so dividing by $N$ gives a variance that is too small on average.

</p>

:: right ::

<p v-click>

<img src="/images/lecture8/n1_M_vs_mu.png" alt="deviations from M are smaller than deviations from mu" class="mx-auto w-full" />

</p>

<p v-click>

<StickyNote color="amber-light" title="Same sample, two reference points" width="100%">
Sample 70, 75, 85 from a population with μ = 80. Measured from M = 76.67 the squared deviations sum to 116.67; measured from μ they sum to 150. Using M shrinks the spread.
</StickyNote>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Fixing the bias: divide by N − 1

:: left ::

- Dividing by $N-1$ instead of $N$ makes each estimate a little bigger — by just the right amount, on average, to undo the shrinkage from using $M$.

<p v-click>

- **Simulation:** 20,000 samples of 3 scores from a population with $\sigma^2 = 50$.
  - Divide by $N$: the estimates average **33.4**. Biased low.
  - Divide by $N-1$: the estimates average **50.1**. Unbiased.

</p>

<p v-click>

<StickyNote color="indigo-light" title="Another way to see it" width="100%">
Deviations from M always sum to zero. So once you know N − 1 of them, the last one is fixed — only N − 1 deviations carry independent information about spread. We divide by the number of <i>free</i> deviations.
</StickyNote>

</p>

:: right ::

<p v-click>

<img src="/images/lecture8/n1_simulation.png" alt="variance estimates with N vs N-1" class="mx-auto w-full" />

</p>

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">
N − 1 doesn't make any single estimate correct. It makes the estimates correct <i>on average</i>. And notice the bias matters most when N is small: 1/3 is a big correction, 1/300 is not.
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Why N-1? (Continued)

:: left ::

*Suppose we have a population with the following scores: 70, 75, 80, 85, 90.*

1. Compute the population mean.
2. Compute the population variance.


*Now imagine we take a sample of 3 scores from this population: 70, 75, 85.*

3. Compute the sample mean.
4. Compute the sample variance using N in the denominator.
5. Compute the sample variance using N-1 in the denominator.


:: right ::

<img src="/images/lecture4/mathmeme.jpg" alt="math" class="mx-auto w-3/4" />


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Code to the rescue!

:: content ::

```r
# Population data
population_scores <- c(70, 75, 80, 85, 90)
population_mean <- mean(population_scores)
population_variance <- sum((population_scores - population_mean)^2) / length(population_scores)

# Sample data
sample_scores <- c(70, 75, 85)
sample_mean <- mean(sample_scores)
sample_variance_N <- sum((sample_scores - sample_mean)^2) / length(sample_scores)
sample_variance_N_minus_1 <- sum((sample_scores - sample_mean)^2) / (length(sample_scores) - 1)
```

<p v-click>

- Population Variance: 50
- Sample Variance (N): 38.89
- Sample Variance (N-1): 58.33

</p>

<p v-click><StickyNote color="green-light" title="In discussion section" width="60%">You'll write R code like this yourselves — today, just focus on how the code mirrors the formulas.</StickyNote></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# A new question: how much can I trust my sample mean?

:: content ::

- You want to know: **how long is the average song?** You can't listen to every song ever made, so you hit shuffle, play 25 songs, and compute the mean: **3.9 minutes**.
- Your friend does the same thing with a different 25 songs and gets **3.6 minutes**.

<Admonition title="Question" color="teal-light" width="100%">
Who is right? Did one of you make a mistake?
</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Neither of you made a mistake. Different random samples give different means. This is called **sampling error**, and it happens in every study ever run.

</Admonition>

<p v-click>

- The useful question is not "is my sample mean exactly right?" (it never is). It is: ==**how far off is a sample mean likely to be?**==
- If sample means usually land within 0.2 minutes of the truth, 3.9 is a good estimate. If they bounce around by 2 minutes, it is nearly useless.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Thought experiment: run the study 10,000 times

:: left ::

A computer can do what we can't. Population: 28,356 real Spotify songs.

1. **Population:** $\mu = 3.78$ min. Songs differ a lot: $\sigma = 1.02$ min.

<p v-click>

2. Draw a random 25-song playlist and compute its **mean**. Repeat. Each mean lands somewhere slightly different.

</p>

<p v-click>

3. Collect 10,000 means: a **distribution of sample means**. Centered on $\mu$, much narrower than the population.

</p>

<p v-click><StickyNote color="amber-light" title="Definition" width="100%">The SD of a distribution of sample means is called the <b>standard error (SE)</b>. Here, SE = 0.20 min.</StickyNote></p>

:: right ::

<img src="/images/lecture8/se_thought_experiment.png" alt="Population, samples, distribution of means" class="w-5/6 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Standard Error of the Mean

:: left ::

- The ==standard error (SE)== is the name for the standard deviation of a distribution of sample means.

- The formula for the standard error is:
$$ SE = \frac{\sigma}{\sqrt{n}} $$
where $\sigma$ is the standard deviation of the scores and $n$ is the sample size.

- We usually don't know $\sigma$, so in practice we estimate it with the sample standard deviation, $s$.

:: right ::

<p v-click>

<AdmonitionType type="warning" width="100%">
Where does this formula come from?
</AdmonitionType>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The formula for the standard error comes from the fact that the variability of sample means is related to the variability of individual scores and the sample size. As we increase the sample size, the standard error decreases, reflecting the increased precision of our estimate of the population mean.

*We can derive it mathematically, but that is beyond the scope of this class.*

</Admonition></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# SD vs. SE: two different questions

:: content ::

Both are standard deviations. They describe the spread of **different things**.

<div class="grid grid-cols-2 gap-6 mt-2 text-base">
<div class="border-2 border-red-300 bg-red-50 rounded-lg p-4">

### Standard deviation (SD)

- Spread of **individual scores**.
- *"How much do songs differ from each other?"*
- Songs: SD = 1.02 min.
- More data does **not** make it smaller.

</div>
<div class="border-2 border-indigo-300 bg-indigo-50 rounded-lg p-4">

### Standard error (SE)

- Spread of **sample means**: the precision of an estimate.
- *"If I re-ran my study, how much would my mean change?"*
- Means of 25 songs: SE = 0.20 min.
- More data **does** make it smaller.

</div>
</div>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="44rem">SD is about <i>people</i> (or songs). SE is about <i>means</i>. You only collect one sample, so you never see the distribution of means. The SE tells you how wide it must be.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Bigger samples, smaller standard error

:: left ::

- Same songs every time ($\sigma = 1.02$, grey). Only $n$ changes.

<p v-click>

- $n = 4$: one long song drags the mean way up. Means bounce a lot.
- $n = 100$: long and short songs cancel out. Means barely move.

</p>

<p v-click>

- The simulated spread matches the formula:

$$SE = \frac{\sigma}{\sqrt{n}}$$

</p>

**Two ingredients:** less variable scores (small σ) or a larger sample (big n) → smaller SE.

:: right ::

<img src="/images/lecture8/se_by_n.png" alt="Distributions of sample means for n = 4, 25, 100" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: what happens when you collect more data?

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

You have sampled 25 songs. You keep going until you have 400. What happens to the **sample SD** and to the **SE** of your mean?

- **A)** Both shrink.
- **B)** SD stays about the same; SE shrinks.
- **C)** SD shrinks; SE stays about the same.
- **D)** Both stay about the same.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Songs don't become more similar to each other because you sampled more of them, so the SD just settles near σ. But your *mean* keeps getting more precise, so the SE keeps shrinking.

</Admonition>

:: right ::

<p v-click>

<img src="/images/lecture8/sd_vs_se_growing_n.png" alt="Sample SD and SE as n grows" class="w-full mx-auto"/>

</p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">"A bigger sample has a smaller SD" is one of the most common mistakes on Exam 2. A bigger sample has a smaller <b>SE</b>.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Why the square root? Diminishing returns

:: left ::

- Each extra song helps, but less than the one before it.

<Admonition title="Multiple choice" color="teal-light" width="100%">

With n = 25 songs, SE = 0.20 min. How many songs do you need to cut the SE in half, to 0.10?

- **A)** 50
- **B)** 75
- **C)** 100
- **D)** 625

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Because of the square root, you need **4 times** the data to halve the SE. Precision is expensive.

</Admonition>

:: right ::

<img src="/images/lecture8/se_curve.png" alt="SE as a function of n" class="w-full mx-auto"/>

---
layout: center
color: amber-light
---

<StickyNote color="amber-light" title="Why this matters" width="80%">

The standard error is one of the most important ideas in this entire course.

Every sample mean we compute "bounces around" the true population mean just by chance. The standard error lets us **quantify how much bounce to expect.**

Very soon, we'll use exactly this idea to:
- Build **z-tests** that ask "is our sample mean far enough from what we'd expect by chance?"
- Construct **confidence intervals** around sample means
- Run **hypothesis tests** more generally, across many different statistical tests

Understanding standard error now will make everything else in this course click into place.

</StickyNote>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Standard Error of the Mean

:: left ::

- The standard error tells us how much variability we can expect in sample means from one sample to another.
- As sample size ($n$) increases, the standard error decreases.
- This means that larger samples yield more ==precise== estimates of the population mean.
- The **standard deviation** tells us the spread of individual data points, while the **standard error** helps quantify the uncertainty in our estimate of the population mean.


:: right ::

<p v-click>

<AdmonitionType type="warning" width="100%">
Why is this value important in psychological research?
</AdmonitionType>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The standard error is important because it helps researchers understand how much their sample mean might vary from the true population mean.

</Admonition></p>

<p v-click>
<img src="/images/lecture6/barplot_sem.png" alt="Error bars" class="w-3/4 mx-auto"/>
</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Calculating Standard Error

:: left ::

- If the SD of a distribution of individual scores = 5
- If we take samples of size $n = 25$, then the SE of the distribution of sample means is:
$$ SE = \frac{5}{\sqrt{25}} = \frac{5}{5} = 1 $$

<Admonition title="Question" color="teal-light" width="100%">
What if we take samples of size $n = 9$? What if we take samples of size $n = 100$? Which will have a smaller SE? Why?
</Admonition>


:: right ::

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- For $n = 9$:
$$ SE = \frac{5}{\sqrt{9}} = \frac{5}{3} \approx 1.67 $$

- For $n = 100$:
$$ SE = \frac{5}{\sqrt{100}} = \frac{5}{10} = 0.5 $$

The sample size of $n = 100$ will have a smaller SE because the standard error decreases as the sample size increases. This reflects the increased precision of our estimate of the population mean with larger samples.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# In real life you only get one sample

:: left ::

- We never actually run a study 10,000 times. We have **one sample**, and we don't know $\sigma$.
- So we estimate the SE from the sample itself, using $s$ in place of $\sigma$:

$$SE = \frac{s}{\sqrt{n}}$$

<p v-click>

**Example:** Researchers measured the sleep of 253 college students.
- $M = 7.97$ hours, $s = 0.96$ hours

$$SE = \frac{0.96}{\sqrt{253}} = 0.06 \text{ hours}$$

</p>

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
The SD is about 1 hour, but the SE is about 0.06 hours (under 4 minutes). Put each number into a sentence. What does each one tell us?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**SD:** Individual students differ a lot. A typical student sleeps about an hour more or less than the average.

**SE:** Our estimate of the *average* is very precise. If we repeated the study with 253 new students, the new mean would typically land within a few minutes of 7.97.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: Onyper, S. V., Thacher, P. V., Gilbert, J. W., & Gradess, S. G. (2012). Class start times, sleep, and academic performance in college. <i>Chronobiology International, 29</i>(3), 318–335.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: uncertainty about a mean

:: left ::

You sample three scores: **4, 5, 6**. You estimate that the population mean is 5.

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which value best describes your **uncertainty about the population mean**?

- **A)** The sample variance: s² = 1
- **B)** The sample SD: s = 1
- **C)** The standard error: 1/√3 = 0.58
- **D)** The sample mean: M = 5

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Variance and SD describe how spread out the *scores* are. The SE describes how far the *sample mean* is likely to be from the population mean.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Suppose you had instead sampled **3, 5, 7**. The mean is still 5. Compared with 4, 5, 6, your uncertainty about the population mean should be:

- **A)** Higher, because the scores are more variable.
- **B)** Lower, because the scores are more variable.
- **C)** The same, because the mean is the same.
- **D)** The same, because n is the same.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Now s = 2, so SE = 2/√3 = 1.15. More variable scores mean a bouncier mean. SE depends on **both** ingredients: the spread of the scores and the sample size.

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

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">Next lecture: z = (M − μ) / SE. A very common Exam 2 error is dividing by the SD when you should divide by the SE.</StickyNote></p>

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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from today

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Distribution of sample means** — the distribution you would get by taking many samples of size $n$ and recording each sample's mean.

</div>
<div>

**Central Limit Theorem** — with a large enough $n$, the distribution of sample means is approximately normal, whatever the shape of the population.

</div>
<div>

**Sampling error** — the natural difference between a sample mean and the population mean.

</div>
<div>

**Unbiased estimate** — right on average across many samples. $M$ is unbiased for $\mu$; $s^2$ needs $N-1$ to be unbiased for $\sigma^2$.

</div>
<div>

**Standard error (SE)** — the SD of the distribution of sample means.<br/> $SE = \frac{\sigma}{\sqrt{n}}$, estimated by $\frac{s}{\sqrt{n}}$

</div>
<div>

**SD vs. SE** — SD is the spread of scores; it does not shrink as $n$ grows. SE is the precision of a mean; it does.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Next time: using z scores and the z table to compute percentiles — and our first hypothesis tests!
