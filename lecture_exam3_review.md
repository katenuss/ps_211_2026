---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Exam 3 Review Session
exportFilename: ps211_fall2026_exam3_review
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Exam 3 Review Session (Lectures 11-14)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- ==Exam 3== is on **Thursday, November 12** during our regular class time.
    - It covers **Lectures 11-14** (effect size & power, parametric assumptions, and single-sample, paired-samples, and independent-samples *t* tests — plus APA-style reporting).
    - A review sheet has been posted.
    - You will *not* need a calculator.
- ==Discussion 10== (Wed. 11/11) is a Data Write-Up 1 work session — bring your dataset and your questions.
- ==Data Write-Up #1== (t-test-based) is due **Tuesday, November 17** at 11:59 p.m. — come to office hours if you want to talk through it.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Effect sizes: Building an intuition

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

The average grade on a recent quiz was 90 with a standard deviation of 5. One hundred students used chatGPT to study for the quiz. Their mean score was 2 standard errors above the class mean. What was their mean score?

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

- First, we need to find the standard error:

$$\sigma_M = \frac{\sigma}{\sqrt{n}} = \frac{5}{\sqrt{100}} \approx 0.5$$

- Now we can find their mean score:
$$M = z*\sigma_M + \mu = 2*0.5 + 90 \approx 91$$

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Effect sizes: Building an intuition

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Is there a significant difference between the mean score of the 100 students who used chatGPT (M = 91) and the class mean (μ = 90, σ = 5)? Use α = .05.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

- We already calculated the z score for this sample mean:
$$z = \frac{M - \mu}{\sigma_M} = \frac{91 - 90}{0.5} = 2$$

- Now we need to find the percentage of scores that fall below this z score. We can use a z table or computer program to find this.
- Using a z table, we find that the percentage of scores below a z score of 2 is approximately 97.72%.
- With α = .05, we would reject the null hypothesis if the percentage of scores below our z score is less than 2.5% or greater than 97.5%. Since 97.72% is greater than 97.5%, we reject the null hypothesis and conclude there is a *significant* difference.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Effect sizes: Building an intuition

:: content ::

- We know there is a *significant* difference between the mean score of the 100 students who used chatGPT (M = 91) and the class mean (μ = 90, σ = 5).
- But is this a **meaningful** difference?
- To answer this, we can consider the *size* of the difference between the two means, while *ignoring* sample size.
- Remember, with a large enough sample size, even a tiny difference can be statistically significant.
- The sample size affects the standard error, which affects the *z* score, which affects the *p* value.
- But the sample size does not affect the **actual** difference between the two means (M - μ).
- So, is a difference of 1 point (91 - 90) meaningful in this context?


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Effect sizes: Computing Cohen's d

:: content ::
- Sometimes, we can use our intuition to determine if a difference is meaningful.
- But other times, we may want a more objective measure of the size of the difference.
- We can use an effect size measure called Cohen's d to quantify the size of the difference between two means.
- Cohen's d is calculated as the difference between two means divided by the standard deviation.

<p v-click>

$$d = \frac{M - \mu}{\sigma} = \frac{91 - 90}{5} = 0.2$$

</p>

<p v-click>
Cohen's d of 0.2 is considered a small effect size. This suggests that while the difference between the two means is statistically significant, it may not be practically meaningful.
</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Effect size tells us how much two populations do not overlap

:: left ::

<img src="/images/lecture9/effect_size.png" alt="Effect size" class="w-1/2 mx-auto"/>

Overlap can be decreased in two ways:

1. When two population ==means are far apart==, the overlap of the distributions is less and the effect size is bigger.

:: right ::

<img src="/images/lecture9/effect_size_var.png" alt="Effect size variance" class="w-3/4 mx-auto"/>
<br>

2. When ==variability within each distribution is smaller==, overlap decreases and effect size increases. 


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Statistical Power

:: content ::
- ==**Statistical Power**== = probability of correctly rejecting $H_0$ when it’s false (avoiding a Type II error).
- In other words, power is the likelihood we will reject the null hypothesis *when we should.*
- Ranges from probability of 0.00 to probability of 1.00
- Probability of 0.80 (80%) is the conventional goal.
  - Many studies in psychology are underpowered!

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Statistical Power (Continued)

:: content :: 

<img src="/images/lecture9/power.png" alt="Statistical power" class="w-5/8 mx-auto"/>


- When testing hypotheses, there are two ways we can be correct and two ways we can be wrong:

1. ==Correctly rejecting the null hypothesis (true positive)==
2. Correctly failing to reject the null hypothesis (true negative)
3. Incorrectly rejecting the null hypothesis (Type I error)
4. Incorrectly failing to reject the null hypothesis (Type II error)


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Five factors that influence power

:: content :: 

Power increases when:
1. Alpha **increases** 
- This is usually not a good idea: This is like changing the rules of a basketball game by shortening the basket height, or widening the goalposts in football or soccer
- Increasing the alpha level from 0.05 to 0.1 increases the probability of type I error from 5% to 10%!

<p v-click>

2. Turn a **two-tailed test** into a **one-tailed test**
- This is only appropriate if you have a strong theoretical reason to predict the direction of the effect.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Five factors that influence power (continued)

:: content :: 

Power increases when:

3. Sample size (n) **increases** 
- This is a good idea: More data gives us a clearer picture of the population.
- Larger samples give us more precise estimates of population parameters, reducing standard error and increasing the likelihood of finding a statistically significant effect

<p v-click>

4. Difference in means **increases** 
- This is usually not under our control, but we can try to design studies that maximize effect size.
- For example, we can use extreme groups (e.g., comparing very high vs. very low anxiety individuals) to increase the difference between means.
- We can also make our manipulations stronger: Maybe we are studying how effective group therapy is for public speaking anxiety, so we increase the length of therapy from 3 to 6 months to increase the difference between the means of each therapy vs. no therapy group

</p>

---
layout: top-title
color: indigo-light
align: lt
---


:: title ::
# Five factors that influence power (continued)

:: content :: 

Power increases when:

5. Standard deviation **decreases** 
- This is also a good idea: Populations with less variability make it easier to detect differences between groups.
- Often not under our control, but we can try to use reliable measures and reduce measurement error to decrease variability within groups.
- For example, if we are measuring anxiety, we can use a well-validated questionnaire rather than a single-item measure to reduce measurement error and variability within groups.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# When and how do we use power?

:: content :: 

We use ==power calculators== in two ways:
1. Calculate power ==after== conducting study from several pieces of information (*post hoc*).

2. Conduct power analyses ==before== conducting study to determine sample size necessary to achieve given level of power given estimate of effect size (*a priori*).

*A priori* power calculations are especially useful because they help us determine the sample size needed to achieve 80% power with an alpha level of 0.05

We can use online calculators or packages for R to conduct power analyses.

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Computing power is largely beyond the scope of this course, but it is very important you understand power at a conceptual level.
</SpeechBubble>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Example: Counseling Session Contracts

:: left ::
- We are studying counseling sessions attended by students at a university. We want to know if signing a contract to attend counseling improves attendance.
- We ask students to sign contracts to attend a set number of counseling sessions (10)
  - Sample: Students at this counseling center who sign the contract to attend at least 10 sessions
  - Population: All students who attended counseling sessions at this university and did not sign the contract

:: right ::
- We sample 5 students who sign a contract. They attended 6, 6, 12, 7, and 8 counseling sessions
- The university average of students who did not sign contracts is 4.6 counseling sessions attended.

<Admonition title="Question" color="teal-light" width="100%">
Did students who sign the contract attend a different number of sessions than those who did not?
</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 1: Identify the populations, distributions, and assumptions
**Populations:** Contract sample, non-contract population

**Distributions:** Distributions of *means.* We want to know whether a sample mean is different from a population mean. Our population distribution is a *t* distribution because we do not know the population standard deviation, so we will have to estimate it from the sample. This means we will use a *t* test.

:: right ::
**Assumptions met for a *t* test?:** 
- We don't know anything about the population distribution or how the sample was collected. 
- However, we will assume that the sample was collected randomly and that the population is approximately normal. 
- If the population was not normal, we would need a larger sample size to use a *t* test. (so that the Central Limit Theorem applies)


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 2: State the hypotheses

- **$H_0$: $μ_1 = μ_2$** (Students who sign the contract attend the same number of sessions as those who do not)
- **$H_1$: $μ_1 ≠ μ_2$** (Students who sign the contract attend a different number of sessions than those who do not)

:: right ::

<p v-click>

Step 3: Determine characteristics of the **comparison distribution**

- Here, we ask how "extreme" our sample mean is, *assuming the null hypothesis is true.*
- We have already decided that the distribution is a *t* distribution because we know the population mean but not the population standard deviation.
- So we need to compute the *t* statistic for our sample mean.

</p>



---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 3: Determine characteristics of the **comparison distribution** (continued)

- We know:
  $$t = \frac{M - \mu}{S_M}$$

- We have:
  - Population mean (μ) = 4.6
  - Sample size (n) = 5
  - Sample scores = 6, 6, 12, 7, 8

:: right ::

- We need to estimate:
  - Population standard error ($S_M$)

- First, we need to calculate the sample mean ($M$) and sample standard deviation ($s$):
  - Sample mean ($M$) = (6 + 6 + 12 + 7 + 8) / 5 = 7.8
  - Sample standard deviation ($s$) = 2.49
  - Estimated population standard error ($S_M$) = 2.49 / √5 = 1.11

We also need to calculate:
  - Degrees of freedom (df) = n - 1 = 5 - 1 = 4



---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

<img src="/images/exam2_review/t_dist.png" class="w-3/4 mx-auto"/>

Now we have our *t* distribution for df = 4.



:: right ::


Step 4: Determine critical values or cutoffs

- We need to know how extreme our *t* statistic needs to be to reject the null hypothesis.
- Remember, *t* distributions vary based on degrees of freedom (df = n - 1). Here, df = 5 - 1 = 4.

- We will use α = 0.05 and a two-tailed test (because our alternative hypothesis is that the means are different, not specifically higher or lower).


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 4: Determine critical values or cutoffs

- We will use α = 0.05. This means we will consider the most extreme 5% of the distribution to be in the rejection region.
- **If the null hypothesis is true, we would expect to get a t statistic this extreme or more extreme only 5% of the time.**
- Since this is a two-tailed test, we will split the 5% into two tails (2.5% in each tail).

<img src="/images/exam2_review/t_alpha_05.png" class="w-3/4 mx-auto"/>


:: right ::

==What if we wanted to be more conservative and use α = 0.01?==
- We would consider the most extreme 1% of the distribution to be in the rejection region.
- Since this is a two-tailed test, we would split the 1% into two tails (0.5% in each tail).

<img src="/images/exam2_review/t_alpha_01.png" class="w-3/4 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 4: Determine critical values or cutoffs

- How do we convert α = 0.05 into a critical value for *t*?
- We can use a *t* table or an online calculator to find the critical value for df = 4 and α = 0.05 (two-tailed).

<img src="/images/exam2_review/t_alpha_05.png" class="w-3/4 mx-auto"/>


:: right ::

<img src="/images/exam2_review/t_table.png" class="mx-auto"/>

- The critical value is approximately ==±2.776.==


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 5: Calculate the test statistic

- We can use the formula for the *t* statistic:
  $$t = \frac{M - \mu}{S_M}$$
- Plugging in our values:
  $$t = \frac{7.8 - 4.6}{1.11} = 2.88$$


:: right ::

<img src="/images/exam2_review/t_val.png" class="w-3/4 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Example: Counseling Session Contracts

:: left ::

Step 6: Make a decision

- Our calculated *t* statistic is 2.88.
- Our critical values are ±2.776.
- Since 2.88 is greater than 2.776, we reject the null hypothesis.

:: right ::

<img src="/images/exam2_review/t_val.png" class="w-3/4 mx-auto"/>

*This means that if there is no difference in attendance between students who sign the contract and those who do not, we would expect to get a t statistic this extreme or more extreme less than 5% of the time. So we reject the null hypothesis, and instead we conclude that there is a significant difference in attendance.*

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Degrees of freedom

:: content ::
- To use a *t* table and run a *t* test, we need to determine our **degrees of freedom**. 

<StickyNote color="amber-light" title="Definition" width="100%">
Degrees of freedom = number of scores that are free to vary when we estimate a population parameter from a sample.
</StickyNote>

- Degrees of freedom reflect the amount of **independent information** available.
- More degrees of freedom means more independent information, which means a more accurate estimate of the population parameter.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Degrees of freedom for a single-sample t test

## df = n-1

:: content ::

- Here, we are estimating the population *standard deviation* from our sample data.
- We *know* the mean.
- Our degrees of freedom reflect the number of scores that could vary (amount of independent information we have) when a given parameter is known.
- Because our mean is known, that means all the scores in our dataset could vary, except one. Once we know the values of the first n-1 scores, the last score MUST take on a specific value.

**Example:**
- If we have 5 scores that sum to 40 (mean = 8), and we know the first 4 scores are 6, 8, 10, and 4, what must the last score be?
- The last score must be 12, because 6 + 8 + 10 + 4 + 12 = 40.
- So, with 5 scores, we have 4 degrees of freedom (5 - 1 = 4).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: Parametric Assumptions

:: content ::
- The single-sample *t* test (like the *z* test) is a ==parametric== statistical test — it relies on assumptions about the data.

<Admonition title="The four assumptions" color="teal-light" width="100%">

1. **Normality** — data are (roughly) normally distributed (often reasonable thanks to the Central Limit Theorem).
2. **Equal variance** — groups have approximately equal variance.
3. **Independence** — data points are randomly and independently sampled.
4. **No extreme outliers**

</Admonition>

- If these assumptions are badly violated, a ==non-parametric== test may be a better choice — every parametric test has a non-parametric equivalent.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: APA Style Reporting

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Which of the following is the correct way to report the results of a single-sample *t* test in APA style? Imagine the first part of the sentence read, "A single-sample *t* test revealed that the sample mean (M = 15.2, SD = 4.5) was significantly higher than the population mean (μ = 12), "

- A. *t*(29) = 2.45, *p* < .05, *d* = 0.45
- B. *t* = 2.45, *df* = 29, *p* = .03, *d* = 0.45
- C. *t*(29) = 2.45, *p* = .03, *d* = 0.45
- D. t(29) = 2.45, p = .03, Cohen's d = 0.45

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

C – The correct APA style reporting includes the test statistic, degrees of freedom in parentheses, the *p* value, and the effect size. Optionally, you can also include the confidence interval.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: APA Style Reporting

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

What's wrong with the following APA style reporting of a paired-samples *t* test? "A paired-samples *t* test indicated that the mean score on the post-test was significantly higher than the mean score on the pre-test, *t*(24) = 3.12, *p* = .004, *d* = 0.62, 95% CI \[1.2, 4.5]."

- A. The means and standard deviations should be reported.
- B. The degrees of freedom should not be included.
- C. The *p* value should only be reported to two decimal places.
- D. There is nothing wrong with this reporting.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A – The means and standard deviations for both the pre-test and post-test should be reported to provide context for the results.

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Tests 

:: content ::

- The *t* test is used to compare means when the population standard deviation is unknown.
- ==Types== of *t* tests:
  - Single-sample *t* test: Compares a sample mean to a known population mean.
  - Paired-samples *t* test: Compares means from the same group at different times or under different conditions.
  - Independent-samples *t* test: Compares means from two different groups.
- Key ==assumptions== of *t* tests:
  - The data are numeric.
  - The data are collected from a random sample.
  - The observations are independent (for independent-samples *t* tests).


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Test Formulas

:: content ::

$$ t = \frac{M - \mu}{SE} $$

Where:
-  $M$ is the sample mean
-  $μ$ is the population mean
    - In a single-sample *t* test, this is a known value.
    - In a paired-samples *t* test, this is the mean of the difference scores under the null hypothesis (which is 0).
    - In an independent-samples *t* test, this is the difference between the two sample means under the null hypothesis (which is 0).
-  $SE$ is the standard error of the mean


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Test Formulas

:: content ::

#### Single-Sample *t* Test
$$ t = \frac{M - \mu}{SE} $$

#### Paired-Samples *t* Test
$$ t = \frac{M_D}{SE_{Difference}} $$

#### Independent-Samples *t* Test
$$ t = \frac{M_1 - M_2}{SE_{Difference}} $$


<p v-click>

- Can think of all these equations as representing a ratio of =="signal"== (the difference between the sample mean and population mean) to =="noise"== (the variability in the data, represented by the standard error).
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Test Formulas

:: content ::

#### Single-Sample *t* Test
$$ t = \frac{M - \mu}{SE} $$

#### Paired-Samples *t* Test
$$ t = \frac{M_D}{SE_{Difference}} $$

#### Independent-Samples *t* Test
$$ t = \frac{M_1 - M_2}{SE_{Difference}} $$


<p v-click><Admonition title="Question" color="teal-light" width="100%">What happened to the population mean (μ) in the paired-samples and independent-samples *t* test formulas?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The population mean (μ) is replaced by the mean of the difference scores (for paired-samples) or the difference between the two sample means (for independent-samples) under the null hypothesis, which is assumed to be 0.

</Admonition></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Test Formulas

:: content ::

$$ t = \frac{M - \mu}{SE} $$


<p v-click><Admonition title="Question" color="teal-light" width="100%">

Which of the following changes would increase the value of the *t* statistic?

- A. Increase the difference between the sample mean and population mean of the null hypothesis.
- B. Increase the standard error.
- C. Decrease the sample size.
- D. Increase the variability in the data.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

A – Increasing the difference between the sample mean and population mean of the null hypothesis increases the numerator of the *t* statistic, leading to a larger *t* value.

</Admonition></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: *t* Tests

:: content ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

If you run a *t* test and do not observe a significant effect, in which cases would you expect your confidence interval to include 0?

- A. Paired-samples *t* test, independent-samples *t* test, and single-sample *t* test.
- B. Paired-samples *t* test only.
- C. Independent-samples *t* test only.
- D. Paired-samples *t* test and independent-samples *t* test only.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

D – The confidence interval for the mean difference in paired-samples *t* tests and the difference between means in independent-samples *t* tests is constructed around the observed ==difference.== If the observed difference is not statistically significant, the confidence interval is likely to include 0, indicating no difference. In a single-sample *t* test, the confidence interval is constructed around the sample mean, so it may not include 0 even if the result is not significant.

</Admonition></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests

:: content ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

In which of the following cases would you use a paired-samples *t* test?

- A. When comparing heights of children and adults.
- B. When comparing test scores of the same students at three different time points.
- C. When comparing blood pressure before and after administering a medication to the same group of patients.
- D. When comparing how number of hours spent studying relates to the number of hours spent sleeping.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

C – A paired-samples *t* test is appropriate when comparing measurements taken from the same group of participants under two different conditions or at two different times, such as before and after administering a medication.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests

:: content ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What type of distribution is used to determine the critical values for a paired-samples *t* test?

- A. Distribution of sample means
- B. Distribution of mean differences.
- C. Distribution of individual scores.
- D. Distribution of differences between independent observations.

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

B – The distribution of mean differences is used to determine the critical values for a paired-samples *t* test, as it focuses on the differences between paired observations.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests: The Comparison Distribution

:: content ::

- When we run a paired-samples *t* test, we are comparing our distribution of sample mean differences to a comparison distribution.
- The comparison distribution is the distribution of mean differences that we would expect to see if the null hypothesis were true.
  - Because this distribution reflects the ==null hypothesis==, **its mean will *always* be 0.**

  <p v-click>

  - However, the spread of this distribution (i.e., its standard error) will depend on the variability in our data and our sample size.
    - Why? Because even if the null hypothesis were true, ==we would still see some variability in the mean differences due to random sampling error.==
    - The amount of variability we would expect to see in the mean differences is captured by the standard error of the difference scores, which takes into account both the variability in the difference scores and the sample size.

  </p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests: The Comparison Distribution

:: content ::

- Imagine that we want to determine whether students run faster after drinking a cup of coffee.
- Now imagine that the null hypothesis is true: **drinking coffee has no effect on run times.**
- If we were to conduct our study with three students, we might still observe some differences in their run times before and after drinking coffee, just due to random chance.
- If student run times were highly variable, we would expect to see even larger differences in their run times before and after drinking coffee, again just due to random chance.
- However, if we increased our sample size to 300 students, we would expect the differences in run times to become more consistent and less influenced by random chance.
- ==This is why the standard error of our comparison distribution depends on both our sample size and the variability of the data.==


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests: The Comparison Distribution

:: content ::

- Our *t* statistic tells us where (how many standard errors away from mean) in this comparison distribution our observed mean difference falls.
- A larger absolute value of *t* indicates that our observed mean difference is further away from the mean of the comparison distribution.
- If our *t* statistic is large enough (i.e., falls in the critical region), we can reject the null hypothesis and conclude that there is a significant difference between the two conditions.

<img src="/images/exam3_review/t_dist_n_example.png"  class="w-3/4 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Paired-Samples *t* Tests: The Comparison Distribution

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Why are we more likely to find a significant effect with a larger sample size?

- A. Larger sample sizes will both increase our *t* statistic AND change the shape of the *t* distribution, decreasing the critical value needed to reach significance.
- B. Larger sample sizes will increase our *t* statistic, but will not change the shape of the *t* distribution.
- C. Larger sample sizes will change the shape of the *t* distribution, decreasing the critical value needed to reach significance, but will not affect our *t* statistic.
- D. Larger sample sizes will increase our effect size.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A – Larger sample sizes decrease the standard error, which increases the *t* statistic. Additionally, larger sample sizes lead to a *t* distribution that more closely resembles the normal distribution, which has lower critical values for significance.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Independent-Samples *t* Tests: The Comparison Distribution

:: content ::

- Independent-samples *t* tests compare means from two different groups.
- The comparison distribution for an independent-samples *t* test is the distribution of differences between sample means that we would expect to see if the null hypothesis were true.
- Because this distribution reflects the ==null hypothesis==, **its mean will *always* be 0.**
- However, the spread of this distribution (i.e., its standard error) will depend on the variability in our data and our sample sizes in both groups.
- The standard error of the difference between means takes into account both the variability in each group and the sample sizes of each group.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: How do we compute the standard error for an independent-samples *t* test?

:: content ::

## Five steps to compute the standard error:
1. Compute each sample's variance (s²).  
2. Compute the pooled variance (s²pooled).
3. Convert the pooled variance from the squared standard deviation (SD²) to the squared standard error (SE²). Remember the squared SD IS the pooled variance.  
4. Add the two squared standard errors together to get the variance of the difference between means (SE²difference).
5. Take the square root of the variance of the difference to get the standard error of the difference between means (SEdifference).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Independent-Samples *t* Tests

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Which of the following is NOT a computation involved in conducting an independent-samples *t* test?

- A. Compute each sample's variance (s²).
- B. Compute the pooled variance (s²pooled).
- C. Compute the mean of the two sample means.
- D. Convert the pooled variance from the squared standard deviation (SD²) to the squared standard error (SE²).

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

C – There is no reason to compute the mean of the two sample means when conducting an independent-samples *t* test. The focus is on the difference between the two means, not their average.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Independent-Samples *t* Tests

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Why do we compute the pooled variance in an independent-samples *t* test?

- A. We have two different samples, so we need to combine their variances to get a better estimate of the population variance.
- B. This enables us to calculate the difference between the sample means.
- C. We need the pooled variance so we know which sample has more variability.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A – In an independent-samples *t* test, we compute the pooled variance to combine the variances from both samples, providing a more accurate estimate of the population variance when the two groups are assumed to have equal variances.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Independent-Samples *t* Tests

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

In which of these scenarios would you use an independent-samples *t* test?

- A. You want to know if there is a difference in SAT scores between students at BU, BC, Northeastern, and Harvard.
- B. You want to know if the number of shark attacks each month relates to the average monthly temperature.
- C. You want to know if student responses on an ordinal scale measuring satisfaction with library services (e.g., strongly agree to strongly disagree) differs between undergraduate and graduate students.
- D. None of the above.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

D – None of the above:
- A involves more than two independent groups.
- B involves two *continuous* variables, not two groups.
- C involves an ordinal variable, which violates a key assumption of the *t* test: that the data are numeric.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Review: Independent-Samples *t* Tests

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

If you decide to run a one-tailed independent-samples *t* test instead of a two-tailed test, which of the following is TRUE?

- A. You will need a larger *t* statistic to reach significance.
- B. You will need a smaller *t* statistic to reach significance.
- C. The shape of the *t* distribution will change.
- D. None of the above.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

B – In a one-tailed test, all of the alpha level is allocated to one tail of the distribution, making it easier to reach significance in that direction, which means you will need a smaller *t* statistic to reach significance. For example, if you are using an alpha level of .05, the critical value for a two-tailed test would be split between both tails (i.e., .025 in each tail), whereas in a one-tailed test, the entire .05 would be in one tail. This means you would need to find a *t* statistic above the 95th percentile, instead of above the 97.5th percentile, to reject the null hypothesis.

</Admonition>



---
layout: cover
color: indigo-light
---

# That’s all for today!
Good luck on Exam 3!
