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
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Standard Error of the Mean

:: left ::

- The ==standard error (SE)== is the name for the standard deviation of a distribution of sample means.

- The formula for the standard error is:
$$ SE = \frac{s}{\sqrt{n}} $$
where $s$ is the sample standard deviation and $n$ is the sample size.

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
# Practice: Putting concepts together

:: left ::

- Imagine you want to determine whether Psychology majors or Biology majors have higher GPAs. You randomly sample 30 students from each major and record their GPAs.

<Admonition title="Question" color="teal-light" width="100%">
What would be a good way to visualize these GPA distributions? Think of two types of plots that could be used for this purpose.
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

1. **Box plots:** These would allow you to see the median, quartiles, and potential outliers for each major's GPA distribution.
2. **Histograms:** These would show the frequency distribution of GPAs for each major, allowing you to see the shape of the distribution (e.g., normality, skewness).

</Admonition></p>



:: right ::

<Admonition title="Question" color="teal-light" width="100%">
Now imagine you want to compare the mean GPAs of the two groups. What would be a good way to quantify your uncertainty in the estimate of these means? How could you visualize the uncertainty in your estimate of the mean GPA for each major?
</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

You could calculate the **standard error (SE)** for each group's mean GPA.

To visualize the uncertainty in your estimate of the mean GPA for each major, you could use barplots with error bars representing the SE for each group.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Putting concepts together (Continued)

:: left ::

# Let's take a look at what those plots might look like

<br>

<img src="/images/lecture6/gpa_barplot.png" alt="Barplot of gpa with error bars" class="w-1/2mx-auto"/>

<p v-click><Admonition title="Challenge question" color="teal-light" width="100%">

If the SE represents +/- 1 SD of the distribution of sample means, what is the probability that the true population mean falls within the error bars shown in the barplot?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Approximately 68% of the time, since the error bars represent +/- 1 SD of the distribution of sample means.

</Admonition></p>


:: right ::

<img src="/images/lecture6/gpa_hist.png" alt="Histogram of gpa" class="w-3/5 mx-auto"/>

<br>

<img src="/images/lecture6/gpa_boxplot.png" alt="Boxplot of GPA" class="w-3/5 mx-auto"/>

<p v-click><StickyNote color="green-light" title="In discussion section" width="100%">You'll practice making plots like these — with error bars — in R during discussion section.</StickyNote></p>


---
layout: cover
color: indigo-light
---

# That's all for today!
Next time: using z scores and the z table to compute percentiles — and our first hypothesis tests!
