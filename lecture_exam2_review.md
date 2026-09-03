---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Exam 2 Review
exportFilename: ps211_fall2026_exam2_review
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Exam 2 Review Session 

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- No standalone homework this week — instead, keep an eye out for our first ==Data Write-Up== (t-test-based), due **Tuesday, November 17** at 11:59 p.m.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders (Exam 2)

:: content ::
==Exam 2== is this Thursday, October 22.
- The exam will focus on Lectures 7 - 10 (normal distributions & z-scores, the Central Limit Theorem & standard error, z-tables & percentiles, hypothesis testing with z tests & confidence intervals), but may also include some cumulative content from earlier in the course.
- The exam will consist of 31 multiple choice questions. You will only need to answer 30 questions correctly to get 100%.
- You will not need a calculator.
- You can bring one 8.5"x11" sheet of handwritten notes (front and back).
- If you need to use a z table, we will provide the table.
- Please bring a pencil or dark pen.
- Having your computer or phone out during the exam will result in a 0 for the exam.
- You will have the entire class period (75 minutes) to complete the exam.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Review: Z Scores and Z Tests

:: left ::
- A z score tells us how many standard deviations a score is from the mean.
- Formula: $z = \frac{X - \mu}{\sigma}$
  - X = score
  - μ = population mean
  - σ = population standard deviation

:: right ::
- A z test compares a sample mean to a population mean, when we know the population standard deviation.
- Formula: $z = \frac{\bar{X} - \mu}{\frac{\sigma}{\sqrt{n}}}$
  - $\bar{X}$ = sample mean
  - μ = population mean
  - σ = population standard deviation
  - n = sample size

*Remember, when we are dealing with distributions of means, we use the standard error ($\frac{\sigma}{\sqrt{n}}$).*

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: The Central Limit Theorem & Standard Error

:: content ::
- The ==Central Limit Theorem (CLT)== tells us that the distribution of sample means will be approximately normal, even if the underlying population is not — as long as sample size is large enough.
- This is why we're able to use normal (and *t*) distributions when working with sample means!
- The ==standard error (SE)== is the standard deviation of the distribution of sample means:

$$SE = \frac{\sigma}{\sqrt{n}}$$

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
As sample size (n) increases, standard error decreases — our estimate of the population mean gets more precise, which is part of why larger samples make it easier to find statistically significant effects.
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: Raw Scores, Z Scores, and Percentiles

:: content ::

- A raw score is the original score (e.g., 85 on a test).
- A *z* score tells us how many standard deviations a score is from the mean.
- A percentile tells us the percentage of scores that fall below a given score.
- We can convert between raw scores, z scores, and percentiles using the mean and standard deviation of the distribution.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores

:: content ::

- To convert a raw score to a z score:
  $$z = \frac{X - \mu}{\sigma}$$

<p v-click>

- To convert a z score to a raw score, we do some algebra to solve for X! 

$$z = \frac{X - \mu}{\sigma}$$

$$z*\sigma = X - \mu$$

$$z*\sigma + \mu = X$$

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores

:: content ::

- Let's practice. The average grade on a recent quiz was 90 with a standard deviation of 5. Your grade was 85. What is your z score?

- To convert a raw score to a z score:
  $$z = \frac{X - \mu}{\sigma}$$

<p v-click>

$$z = \frac{85 - 90}{5} = -1$$

You scored 1 standard deviation below the mean.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores

:: content ::

- Let's practice. The average grade on a recent quiz was 90 with a standard deviation of 5. Your friend scored .5 standard deviations above the mean ($z = .5$). What was their raw score?

- To convert a *z* score to a raw score:
  $$z*\sigma + \mu = X$$

<p v-click>

$$X = 0.5*5 + 90 = 92.5$$

Your friend scored 92.5 on the quiz.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores for means

:: content ::

- To convert a sample mean to a z score:
  $$z = \frac{M - \mu}{\sigma_M}$$

Where $\sigma_M$ is the standard error: $\sigma_M = \frac{\sigma}{\sqrt{n}}$

<p v-click>

- To convert a z score to sample mean, we do some algebra to solve for M! 

$$z = \frac{X - \mu}{\sigma_M}$$

$$z*\sigma_M = M - \mu$$

$$z*\sigma_M + \mu = M$$

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores for means: Practice

:: content ::

- Let's practice. The average grade on a recent quiz was 90 with a standard deviation of 5. A sample of 25 students had a mean score of 85. What is the z score for this sample mean?

<p v-click>

- First, we need to find the standard error:

$$\sigma_M = \frac{\sigma}{\sqrt{n}} = \frac{5}{\sqrt{25}} = 1$$

- Now we can find the z score:

$$z = \frac{M - \mu}{\sigma_M} = \frac{85 - 90}{1} = -5$$

This sample of students scored 5 standard errors below the mean.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores and z scores for means: Practice

:: content ::

- The average grade on a recent quiz was 90 with a standard deviation of 5. Nine students used chatGPT to study for the quiz. Their mean score was 2 standard errors above the class mean. What was their mean score?

<p v-click>

- First, we need to find the standard error:

$$\sigma_M = \frac{\sigma}{\sqrt{n}} = \frac{5}{\sqrt{9}} \approx 1.67$$

- Now we can find their mean score:

$$M = z*\sigma_M + \mu = 2*1.67 + 90 \approx 93.34$$

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Moving between raw scores, z scores, and percentiles for means

:: content ::

- To convert between z scores and percentiles, we can use a *z* table or computer program.
- This will enable us to find the percentage of scores below a given z score, or the z score that corresponds to a given percentile.
- We can also use this to find critical values for hypothesis tests or confidence intervals.
- We can then convert between z scores and raw scores using the formulas from the prior slides.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Moving between raw scores, z scores, and percentiles for means: Practice

:: content ::

- Is there a significant difference between the mean score of the 9 students who used chatGPT (M = 93.34) and the class mean (μ = 90, σ = 5)?
 Use α = .05.

<p v-click>

- We already calculated the z score for this sample mean:
$$z = \frac{M - \mu}{\sigma_M} = \frac{93.34 - 90}{1.67} \approx 2$$

- Now we need to find the percentage of scores that fall below this z score. We can use a z table or computer program to find this.
- Using a z table, we find that the percentage of scores below a z score of 2 is approximately 97.72%.

</p>

<p v-click>

With α = .05, we would reject the null hypothesis if the percentage of scores below our z score is less than 2.5% or greater than 97.5%. Since 97.72% is greater than 97.5%, we reject the null hypothesis.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Finding confidence intervals for means

:: content ::

*What is the 95% confidence interval for the mean score of the 9 students who used chatGPT (M = 93.34)?*

<p v-click>

- First, we can imagine that this **sample mean** lies in the center of a **sampling distribution of means**. 
- Because we know the population standard deviation, we can compute the standard error of the mean directly and use a *z* distribution.
- To find the 95% confidence interval, we need to find the z scores that correspond to the middle 95% of the distribution.
- Second, we need to determine what percentiles correspond to the middle 95%. This means we need to leave 2.5% in each tail.
- Our lower percentile is 2.5% and our upper percentile is 97.5%.
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Finding confidence intervals for means (continued)

:: content ::

- Using a z table, we find that the z score that corresponds to 2.5% is approximately -1.96 and the z score that corresponds to 97.5% is approximately 1.96.
- Now we can convert these z scores to raw scores using the formula: $M = z*\sigma_M + \mu$


<p v-click>

- For the lower bound:
$$M = -1.96*1.67 + 93.34 \approx 90.06$$
- For the upper bound:
$$M = 1.96*1.67 + 93.34 \approx 96.62$$

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: A Full Z Test, Start to Finish

:: left ::

**Scenario:** The average grade on a recent quiz was 90 with a standard deviation of 5 (treat these as the population mean and SD). A sample of 25 students who attended a new review session scored a mean of 92.5.

<Admonition title="Question" color="teal-light" width="100%">
Using α = .05 (two-tailed), did the review-session students score significantly differently from the class? Work through all the steps: standard error, z statistic, critical values, decision, and conclusion.
</Admonition>

:: right ::

**Work this one out yourself before we go through it together!**

- What is the standard error, $\sigma_M = \frac{\sigma}{\sqrt{n}}$?
- What is the z statistic, $z = \frac{M - \mu}{\sigma_M}$?
- What are the critical z values for α = .05, two-tailed?
- Do you reject the null hypothesis? What do you conclude?

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: A Full Z Test, Start to Finish (Answers)

:: left ::

**Scenario:** The average grade on a recent quiz was 90 with a standard deviation of 5 (treat these as the population mean and SD). A sample of 25 students who attended a new review session scored a mean of 92.5.

<Admonition title="Question" color="teal-light" width="100%">
Using α = .05 (two-tailed), did the review-session students score significantly differently from the class?
</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%">

**Step 1:** Standard error:
$$\sigma_M = \frac{\sigma}{\sqrt{n}} = \frac{5}{\sqrt{25}} = 1$$

**Step 2:** Z statistic:
$$z = \frac{M - \mu}{\sigma_M} = \frac{92.5 - 90}{1} = 2.5$$

**Step 3:** Critical values for α = .05, two-tailed: $z = \pm 1.96$

**Step 4:** Since $2.5 > 1.96$, our z statistic falls in the critical region — we **reject the null hypothesis**.

**Conclusion:** The review-session students scored significantly differently from (specifically, higher than) the class average. A sample mean this extreme would occur less than 5% of the time if the null hypothesis were true.

</Admonition>

---
layout: cover
color: indigo-light
---

# That’s all for today!
See you Thursday, October 22 for Exam 2!
