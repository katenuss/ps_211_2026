---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 5
exportFilename: ps211_fall2026_lecture5
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 5: Variability

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::

- Remember: there is no standalone homework this year. Instead, you'll complete two Data Write-Ups later in the semester (the first is t-test based, due Monday, Nov. 16; the second is ANOVA based, due Monday, Dec. 7).
- Discussion sections are using time for in-class R practice — take advantage of it!
- Office hours: Tuesdays 12:30-1:30pm and Thursdays 9:00-10:00am.
- ==Exam 1== is scheduled for **Tuesday, September 29** and covers Lectures 1 - 6. Review session is **Thursday, September 24**.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variability

:: content ::
- Besides a dataset's center or ==central tendency==, we also often want to know how spread out the values are.
- **Variability** describes the spread of a distribution. 
- Distributions with higher variability show greater spread between scores.  

<img src="/images/lecture4/variance.jpg" alt="variance" class="mx-auto w-1/4" />

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">How could we measure spread?</Admonition>
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why do we care about spread?

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Two sections of PS 211 both average 75% on a quiz. In Section A, every student scored between 70-80%. In Section B, scores ranged from 40% to 100%. Same average — very different experiences!</Admonition>

<p v-click>

- Both sections have the *exact same mean*, but they tell very different stories.
- In Section A, the average is a good description of almost everyone.
- In Section B, the average hides huge differences — some students are struggling, some are acing it.

</p>

<p v-click>

==The mean alone doesn't capture this. We need a way to measure how spread out scores are.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What does "spread" look like?

:: content ::

- Here are two distributions with the same mean but very different spread — this is the same idea as our two quiz sections.

<img src="/images/lecture4/high_low_var.svg" alt="variance visual anchor" class="mx-auto w-1/2" />

<p v-click>

- The distribution on the left is more spread out (like Section B). The one on the right is more tightly clustered (like Section A).
- By the end of today, you'll be able to put a **number** on this difference.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variability

:: content ::

<Admonition title="Question" color="teal-light" width="100%">How could we measure spread?</Admonition>

<br> 

Three main **descriptive statistics** are used to measure variability:
1. ==Range==: the difference between the highest and lowest score
2. ==Variance==: average square deviation from the mean
3. ==Standard deviation==: the square root of the variance

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Range

:: content ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>

$$Range = X_{max} - X_{min}$$

<br> 

- The range is the difference between the highest and lowest score.  
- For example, if the highest quiz score is 90 and the lowest is 70, the range is 20.  
- The range is simple to compute, but it only depends on two scores and can be distorted by outliers. 



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interquartile Range

:: content ::
- The interquartile range (IQR) measures the distance between the 25th percentile (Q1) and 75th percentile (Q3).  
- The IQR represents the middle 50% of the data.  
- Because it is less influenced by outliers, the IQR is often a more robust measure of variability.  


<div class="flex items-center justify-center space-x-4">
  <img src="/images/lecture4/iqr.png" alt="iqr" class="w-2/7" />

  **To compute the IQR:**

  <SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
    Split the data into two halves at the median. Q1 is the median of the lower half of the data. Q3 is the median of the upper half.
  </SpeechBubble>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Computing the interquartile Range

:: content ::
- The following are the scores of 9 students on an exam: 55, 60, 65, 70, 75, 80, 85, 90, 95. What is the interquartile range (IQR) of these scores?

<p v-click>

1. Order the scores (they are already ordered).

</p>

<p v-click>

2. Find the median (75).

</p>


<p v-click>
3. Split the data into two halves: lower half (55, 60, 65, 70) and upper half (80, 85, 90, 95).
</p>

<p v-click>
4. Find Q1 (the median of the lower half) = (60 + 65) / 2 = 62.5.

</p>

<p v-click>
5. Find Q3 (the median of the upper half) = (85 + 90) / 2 = 87.5.
</p>

<p v-click>

6. Compute the IQR: IQR = Q3 - Q1 = 87.5 - 62.5 = **25.**

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Boxplots revisited

:: left ::

- Boxplots visually represent the median, quartiles, and potential outliers in a dataset.
- The box represents the interquartile range (IQR), with a line at the median.
- "Whiskers" extend to the smallest and largest values within 1.5 * IQR from the quartiles.
- Points outside this range are considered potential outliers.

:: right ::

```r
#make list of exam scores
exam_scores <- c(55, 60, 65, 70, 75, 80, 85, 90, 95)

#put in dataframe
exam_scores_df <- data.frame(exam_scores)
exam_scores_df$exam <- factor(1)  #add variable for x axis

#use ggplot to make boxplot
ggplot(exam_scores_df, aes(x = exam, y = exam_scores)) +
  geom_boxplot() +
  labs(title = "Boxplot of Exam Scores", y = "Scores")
```
<br>
<img src="/images/lecture4/exam1_boxplot.png" alt="boxplot iqr" class="mx-auto w-1/2" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variance

:: content ::

<Admonition title="Question" color="teal-light" width="100%">What if we want a measure of spread influenced by ALL scores?</Admonition>


- We can compute the distance each score is from the mean (the deviation), and take the average of that.
- But... if we add up all the deviations, they will always equal zero!

**Example**
- Scores: 70, 80, 90
- Mean: 80; Deviations: -10, 0, +10
- Sum of deviations: -10 + 0 + 10 = 0


<p v-click>

<Admonition title="Question" color="teal-light" width="100%">To solve this, we square each deviation (to make them positive) before summing them!</Admonition>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Variance (continued)

:: left ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>


- The formula for the variance of a population is:

$$\sigma^2 = \frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}$$

:: right ::

<p v-click>

<img src="/images/lecture4/ohno_math.jpg" alt="oh no" class="mx-auto w-3/4" />

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Variance (continued)

:: left ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>


- The formula for the variance of a population is:

$$\sigma^2 = \frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}$$

:: right ::


<p v-click>

1. For each score ($X_i$), compute the deviation from the population mean: $X_i - \mu$.

<img src="/images/lecture4/mew.png" alt="mew" class="mx-auto w-1/4" />

</p>

<p v-click>

2. Square each deviation: $(X_i - \mu)^2$.

</p>

<p v-click>

3. Sum the squared deviations: $\sum_{i=1}^{N} (X_i - \mu)^2$.

</p>

<p v-click>

4. Divide by the total number of scores: $N$.

</p>

<p v-click>

5. Now we have our population variance, represented by $\sigma^2$ (the Greek letter "sigma" squared).

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Sample Variance 

:: left ::

<AdmonitionType type="warning" width="100%">Things are about to get tricky...</AdmonitionType>


- The formula for the variance of a **SAMPLE** is:

$$s^2 = \frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1}$$

<p v-click>

*What changed?*

</p>

<p v-click>

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

# Why N-1?

:: left ::

**Why do we divide by N-1 instead of N?**

<img src="/images/lecture4/but_why.png" alt="why" class="mx-auto w-1/2" />


:: right ::

- When we use the sample mean (M) instead of the population mean (μ), we are using an estimate that is **based on the sample data.**
- The sample mean tends to be closer to the sample scores than the true population mean would be.
- This can lead to an underestimation of the true population variance.
- Dividing by N-1 instead of N provides a better estimate of the population variance, especially for small sample sizes.

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


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standard Deviation

:: content ::
- The standard deviation is the square root of the variance.

- The formula for the standard deviation of a population is:
$$\sigma = \sqrt{\frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}}$$

- The formula for the standard deviation of a sample is:
$$s = \sqrt{\frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1}}$$

- It represents the typical amount that each score deviates from the mean.  

- Larger standard deviations indicate greater spread, while smaller ones indicate that scores cluster more closely around the mean.  

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standard deviation vs. variance

:: content ::
- The standard deviation is often more interpretable than the variance because it is in the same units as the original data.
- For example, if exam scores are measured in points, the standard deviation will also be in points, while the variance will be in points squared.
- Both the variance and standard deviation provide valuable information about the spread of a dataset, but the standard deviation is often preferred for its interpretability.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability in R


:: content ::

- R actually has built-in functions to compute variance and standard deviation.

```r
# Sample data
scores <- c(70, 75, 80, 85, 90) 

# Compute sample variance
sample_variance <- var(scores)

# Compute sample standard deviation
sample_sd <- sd(scores)
```

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">The `var()` function in R computes the sample variance (dividing by N-1), and the `sd()` function computes the sample standard deviation.</SpeechBubble>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability in R 


:: content ::

<Admonition title="Question" color="teal-light" width="100%">Thought question: Why would the built in 'var' and 'sd' functions compute the sample variance and standard deviation instead of the population versions?</Admonition>

<p v-click>

**Answer:** In practice, we often work with samples rather than entire populations. Therefore, R's built-in functions are designed to compute sample statistics by default.

<img src="/images/lecture4/sample_meme.jpg" alt="sample meme" class="mx-auto w-1/4" />


</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability: Practice


:: content ::

<Admonition title="Question" color="teal-light" width="100%">Which histogram displays data with higher variance?</Admonition>

<img src="/images/lecture4/high_low_var.svg" alt="variance practice" class="mx-auto w-1/2" />

<p v-click>

**Answer:** The histogram on the left has higher variance because the scores are more spread out from the mean.

</p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Which measure of variability would be most affected by an outlier?</Admonition>
</p>

<p v-click>

**Answer:** The range would be most affected by an outlier because it only depends on the highest and lowest scores.
</p>



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability: Practice (Continued)


:: content ::

<Admonition title="Question" color="teal-light" width="100%">Which distribution likely has a greater standard deviation?</Admonition>

<div class="mt-6 flex justify-center space-x-6">
  <img src="/images/lecture4/bimodal.png" alt="bimodal" class="w-1/3" />
  <img src="/images/lecture4/unimodal.png" alt="unimodal" class="w-1/3" />
</div>


<p v-click>

**Answer:** The "Violet" distribution likely has a greater standard deviation because its scores are more spread out from the mean.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Sleep hours

:: content ::

Ten students report how many hours they slept last night:

$$5, 6, 6, 7, 7, 7, 8, 8, 9, 9$$

<p v-click>

**Step 1: Find the mean.**

$$M = \frac{5+6+6+7+7+7+8+8+9+9}{10} = \frac{72}{10} = 7.2 \text{ hours}$$

</p>

<p v-click>

**Step 2: Find the range.**

$$Range = X_{max} - X_{min} = 9 - 5 = 4 \text{ hours}$$

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Sleep hours (continued)

:: content ::

**Step 3: Find the sample standard deviation.**

<p v-click>

First, find each deviation from the mean (7.2) and square it:

| Score | Deviation | Squared |
|---|---|---|
| 5 | -2.2 | 4.84 |
| 6 | -1.2 | 1.44 |
| 6 | -1.2 | 1.44 |
| 7 | -0.2 | 0.04 |
| 7 | -0.2 | 0.04 |
| 7 | -0.2 | 0.04 |
| 8 | 0.8 | 0.64 |
| 8 | 0.8 | 0.64 |
| 9 | 1.8 | 3.24 |
| 9 | 1.8 | 3.24 |

</p>

<p v-click>

Sum of squared deviations = 15.6

$$s^2 = \frac{15.6}{N-1} = \frac{15.6}{9} = 1.73$$

$$s = \sqrt{1.73} = 1.32 \text{ hours}$$

</p>

<p v-click>

==On average, students' sleep durations differ from the mean (7.2 hours) by about 1.32 hours.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Discussion: Anxiety scores

:: content ::

<StickyNote color="teal-light" title="Discussion" width="100%">
Two groups of students both report an average anxiety score of 5 (on a 0-10 scale) before an exam. Group A has a standard deviation of 0.5. Group B has a standard deviation of 3.5. What does this difference in SD tell us about each group, even though their average is identical?
</StickyNote>

<p v-click>

**Possible answer:** In Group A, almost everyone feels about the same, moderate amount of anxiety — the mean of 5 describes the group well. In Group B, the same average of 5 is hiding a lot of variability: some students may feel almost no anxiety, while others may feel extremely anxious. 

</p>

<p v-click>

- This matters practically! If you were designing an intervention, Group B might need a more individualized approach, while a single approach might work well for Group A.
- ==A mean without a measure of variability can be misleading.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Looking ahead

:: content ::

<StickyNote color="amber-light" title="Looking ahead" width="100%">
Variance and standard deviation aren't just standalone descriptive statistics — they're the foundation for almost everything else we'll do this semester.
</StickyNote>

<p v-click>

- Soon, we'll use the standard deviation to **standardize scores into z-scores**, letting us compare scores from totally different scales.
- Later, we'll learn about **standard error** — how much sample means bounce around from sample to sample — which depends directly on variability.
- If today's material feels shaky, now is the time to review it, since z-scores, standard error, and effect size all build directly on variance and SD.

</p>

---
layout: cover
color: indigo-light
---


# That's all for today!
Next time: standardizing scores and the normal curve.
