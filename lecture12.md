---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 12
exportFilename: ps211_fall2026_lecture12
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 12: Parametric Assumptions & Intro to t-Tests

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- No standalone homework this week — instead, keep an eye out for our two ==Data Write-Ups== this semester:
  - t-test-based, due **Monday, November 16**
  - ANOVA-based, due **Monday, December 7**
- Office hours this week:
  - Tuesday: 12:30 - 1:30 pm (Kate)
  - Thursday: 9:00 - 10:00 am (Kate)
- Coming up:
  - Tuesday (10/27): Exam 2 Review
  - Thursday (10/29): Exam 2 (covers Lectures 7-12)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Parametric vs. Non-Parametric Statistics

<Admonition type="warning" width="100%">
A brief but important aside
</Admonition>

:: content :: 
- We have so far talked about one kind of statistical test: a *z* test.
- This is an example of a **parametric** statistical test, which depends on certain assumptions.
- **Parametric** statistical tests generally have more ==power== than **non-parametric** statistical tests.
- However, they are more powerful in large part because they take advantage of *assumptions* about the distribution of the data. 
- It is important to ensure that these assumptions are largely met before using *parametric* statistics.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Assumptions of parametric statistical tests

:: content :: 
1. ## Normality
- Data within each group are (roughly) normally distributed.
- We can often assume this because of the central limit theorem!


<Admonition title="Question" color="teal-light" width="100%">
Why is the central limit theorem relevant here?
</Admonition>

<p v-click>

<StickyNote color="green-light" title="Answer" width="100%">
The central limit theorem states that the distribution of sample means will be approximately normal. This means that if we are working with sample means, we can assume our sample mean is drawn from a normal distribution.
</StickyNote>

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Assumptions of parametric statistical tests (continued)

:: content :: 
2. ## Equal variance
- Data within each group have approximately equal variance.

<img src="/images/lecture9/unequal_variance.png" alt="unequal variance" class="w-1/4 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Assumptions of parametric statistical tests (continued)

:: content :: 
3. ## Independence
- Data in each group are randomly and *independently* sampled from a population.
- Sampling one data point does not influence the next data point that will be sampled.

<br>

4. ## No extreme outliers
- There should be no extreme outliers.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# What if assumptions are not met?

:: content :: 
- Often, you can still use parametric statistical tests even if assumptions are *a little* violated.
- However, there are also **non-parametric** statistical tests that do not rely on these assumptions and can be used instead.
- For every parametric statistical test, there is a non-parametric equivalent.


<img src="/images/lecture9/parametric_nonparametric.webp" alt="parametric vs. nonparametric tests" class="w-1/2 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Moving from *z* to *t*

:: content :: 
- *z* tests are one way we can compare two distributions to ask: Is the population from which this sample is drawn *different* from this other population?

- However, *z* tests assume we know the **population SD (σ)**.
- In reality, we rarely do!
- **More often, researchers use *t* tests**, which are more versatile than *z* tests.
- ==***t* tests**== are used:
  - when we do not know the population standard deviation (σ)
  - when we want to compare two samples to each other (vs. a sample to a known population)


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Normal distributions vs. *t* distributions

:: content :: 
- For *z* tests, we relied on ==normal distributions==.
- For *t* tests, we will instead use *t* distributions.
- *t* distributions allow us to compare one sample to a population when we don't know all the parameters of the population.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# The *t* Distribution

:: content ::

- There isn't just one *t* distribution — there's one for every sample size.
- As *n* → ∞, the *t* distribution approaches the normal *z* distribution.
- Because we need to estimate *SD*, the *t* distribution is wider and has heavier tails than the *z* distribution. These heavier tails reflect the added uncertainty in our estimate of the population variance and, therefore, in the distribution of sample means.


<img src="/images/lecture9/t_distribution.png" alt="t distribution" class="w-1/2 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# The *t* Distribution

:: content ::

- For smaller samples (n = 2 or 8), *t* distributions are wider and flatter (more variability) than the *z* distribution 
- As sample size increases (e.g., n = 30), the *t* distributions look more like the *z* distribution. 

  - Why? A larger sample size is closer to the entire population. We expect many variables within the entire population to follow a normal distribution.

<img src="/images/lecture9/t_distribution.png" alt="t distribution" class="w-1/2 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why This Matters

:: content ::

<StickyNote color="amber-light" title="Why this matters" width="100%">
Take a moment to appreciate what we just unlocked. *z* tests require knowing the **population standard deviation** — but in real research, this is rare! We almost never know σ for the population we're studying.

*t* tests only require an **estimate** from our sample. This is why *t* tests (not *z* tests) are the tool researchers actually reach for, constantly, in practice. We're about to spend several lectures on *t* tests because they are the workhorse of real-world data analysis.
</StickyNote>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Types of *t* tests

:: content ::

- When we run *t* tests, we are asking if two means likely came from the same population distribution. ==Just like *z* tests!==

1. ## Single-sample *t* test: 
Used when comparing a sample mean to a population mean when the population standard deviation is not known.


2. ## Paired-sample *t* test: 
Used when comparing two samples and every participant is in both samples. Common for *within-group* designs.

3. ## Independent-samples *t* test: 
Used when comparing two samples and every participant is in only one sample. Common for *between-groups* designs.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# How to compute a *t* statistic

:: content ::

- The first step to conducting a single-sample *t* test is to estimate the ==population standard deviation.==

- The population standard deviation is based on the sample SD.

- This step is the only practical difference between conducting a z test with the *z* distribution vs. a *t* test with a *t* distribution! 

The sample standard deviation formula is:
$$ s = \sqrt{\frac{\sum{(X - M)^2}}{n - 1}} $$


<img src="/images/lecture9/imback.png"  class="w-1/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# How to compute a *t* statistic (continued)

:: content ::

- Now that we have an estimate of the population standard deviation, we need an estimate of the spread of the distribution of means.
- We need this because:
  - We are comparing means, rather than individual scores.
  - The distribution of means is less variable than the distribution of scores.
  - Remember, when we did *z* tests, we used the ==standard error==, not the standard deviation, which tells us the spread of sample ==means.==
- We need to calculate ==standard error== here too:

$$S_M = \frac{s}{\sqrt{N}}$$

- We use $S_M$ to reflect the fact that we are using the *estimated* population standard deviation around the sample mean, based on the sample SD.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# How to compute a *t* statistic (continued)

:: content ::

- Now we can calculate our *t* statistic!

$$t = \frac{M-\mu_M}{S_M}$$

<Admonition type="warning" width="100%">
Look familiar?
</Admonition>

<p v-click>

This is very similar to the *z* statistic calculation:

$$z = \frac{X-\mu}{\sigma} $$

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Conducting a single-sample *t* test

:: content ::

- The single-sample *t* test is a hypothesis test in which we compare a sample (data we collected) to a population.

- We know the mean of the population, but not the standard deviation.

- When we are using *t* distributions, we use a *t* table instead of the *z* table.
 The *t* table takes our sample size into account.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# A *t* table

:: content ::


<img src="/images/lecture9/t_table.png"  class="w-3/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Degrees of freedom

:: content ::
- To use a *t* table and run a *t* test, we need to determine our **degrees of freedom**. 

<StickyNote color="amber-light" title="Definition" width="100%">
Degrees of freedom = number of scores that are free to vary when we estimate a population parameter from a sample.
</StickyNote>

- Degrees of freedom reflect the amount of **independent information** available.


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
- Our degrees of freedom reflect the number of scores that could vary when a given parameter is known.
- Because our mean is known, that means all the scores in our dataset could vary, except one. Once we know the values of the first n-1 scores, the last score MUST take on a specific value.

**Example:**
You know the mean of 3 exam scores is 90. The first two scores could be anything! But once you know them, there is only one possible score for the third exam to make the mean 90. If one score is 85 and the other score is 92, the third score **must** be 93.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Using a t table

:: content ::

- To use the *t* table, we look up the df to find the critical value of the *t* statistic at a given alpha level 
- If the *t* statistic from our *t* test calculation is greater than the critical value, we reject the null hypothesis.


<img src="/images/lecture9/t_table.png"  class="w-3/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Degrees of freedom and critical *t* values

:: content ::

- The more degrees of freedom, the lower the critical *t* value

<img src="/images/lecture9/t_table.png"  class="w-3/4 mx-auto"/>



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Comparing the *z* table and the *t* table

:: content ::

- As the degrees of freedom in the *t* table get very large (larger sample sizes), the *t* statistic for the 95th percentile approaches 1.96
- This is the same as the *z* statistic for the 95th percentile
- Why? The central limit theorem! 
- The larger the sample, the more the *t* distribution looks like the *z* distribution (the more 'normal' it becomes)
- The *t* statistic merges with the *z* statistic as the sample size increases.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Recap: Conducting single‑sample *t* tests

:: content ::
==Used when comparing a **sample mean** to a **population mean** when population SD is unknown.==

<br>

Six Steps:
1. Identify populations & assumptions.
2. State $H_0$ and $H_1$.
3. Determine characteristics of comparison distribution.
4. Find critical *t* values (using df = n − 1).
5. Calculate test statistic.
6. Make a decision.

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
layout: cover
color: indigo-light
---

# That's all for today!
See you next time for the Exam 2 review session!
