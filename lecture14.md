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
### Lecture 14: Independent-Samples *t*-Tests (in R)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- No standalone homework this week — instead, keep an eye out for our first ==Data Write-Up== (t-test-based), due **Monday, November 16**. You now have both paired- and independent-samples *t* tests in hand for it.
- Office hours this week:
  - Tuesday: 12:30 - 1:30 pm (Kate)
  - Thursday: 9:00 - 10:00 am (Kate)
- Coming up:
  - Tuesday (11/10): Exam 3 Review
  - Thursday (11/12): Exam 3 (covers Lectures 13-14)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Recap: Between- vs. Within-Subjects Designs

:: content ::
- **Within-subjects (paired):** each participant experiences **all** levels of the IV — comparisons are made *within the same people* (covered last class, and back in Lecture 2).
- **Between-subjects (independent):** each participant experiences **only one** level of the IV — comparisons are made *between different people*.
- **Within-groups design** → use a *paired-samples t test*
- **Between-groups design** → use an *independent-samples t test*

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Independent-Samples *t* Tests

:: content ::
- Compares two means from **independent groups.**
- Each group has different people that each experience **only one** level of the independent variable.
- Example: Comparing quiz scores of students who took the quiz with music vs. students who took the quiz in silence.
  - The scores are independent because no student is in both groups. There are no paired scores.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Can you think of another study design where you would use an independent-samples *t* test?
</Admonition>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Paired- vs. Independent-Samples *t* Tests

:: left ::
### Paired-Samples *t* Test
1. Compute difference scores for each participant.
2. Compute mean of these difference scores.
3. Determine probability of observing this mean difference under null hypothesis.

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Here, our null distribution is a distribution of mean differences. We are really working with **one** sample of difference scores — its SE is based on that single sample's SD and n.
</SpeechBubble>

</p>

:: right ::
### Independent-Samples *t* Test
1. Compute mean scores for each group.
2. Compute difference between these group means.
3. Determine probability of observing this mean difference under null hypothesis.

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Here, our null distribution is a distribution of differences between independent group means. We are really working with **two** independent samples — its SE is based on **both** samples' SDs and sample sizes.
</SpeechBubble>

<br>
<img src="/images/lecture10/fried_brain.png"  class="w-1/3 mx-auto"/>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# How do we create the distribution of differences between independent group means?

:: left ::
1. Randomly sample n₁ participants for Group 1 and n₂ participants for Group 2 from the population.
2. Compute the mean for each group.
3. Compute the difference between the two group means (M₁ − M₂).
4. Repeat many times to build a distribution of mean differences between independent groups.
5. Use this distribution to determine the probability of observing a mean difference as extreme as the one in our sample, assuming the null hypothesis is true.


:: right ::
<img src="/images/lecture10/independent_mean_diff_hist_n20_25.png"  class="mx-auto"/>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Note that here we have **two** ns (n₁ and n₂) because the two groups can have different sample sizes.
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# What are the characteristics of the distribution of differences between independent group means?

:: content ::
Remember, **normally we do not have to build this distribution by simulating many samples.** Instead, we can compute its characteristics directly.
- Under H₀, the mean of this distribution is 0.
- The standard error (SE) of this distribution is computed using both groups' sample standard deviations and sample sizes.
- We use both groups' data to estimate the *pooled variance*, which is our best estimate of the population variance.
- From the pooled variance, we can compute the standard error of the difference between independent means.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Steps of an Independent-Samples *t* Test

:: left ::

1. Identify populations, distribution, & assumptions.
2. State null and research hypotheses.
3. Determine characteristics of comparison distribution.
4. Determine critical values (cutoffs).
5. Calculate test statistic.
6. Make a decision.

:: right ::

<p v-click>

*Steps 3-5 are similar to those for paired-samples *t* tests, but the formulas differ slightly because we are dealing with two independent groups.*

<span class="text-blue-600">

3. Determine characteristics of comparison distribution.
4. Determine critical values (cutoffs).
5. Calculate test statistic.

</span>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# How do we compute the standard error for an independent-samples *t* test?

:: content ::

## Three steps to compute the standard error:
1. Compute each sample's variance (s²), then combine them into a **pooled variance** — a weighted average of the two sample variances (weighted by degrees of freedom, since n₁ and n₂ can differ).
2. Convert the pooled variance into a squared standard error for each group ($SE^2 = s^2/n$), and add the two together to get the variance of the *difference* between means.
3. Take the square root to get the standard error of the difference between means.

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
This all boils down to one formula (next slide) — you'll rarely compute it by hand, but it's worth seeing where it comes from.
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Putting It All Together

:: content ::

$$s^2_{pooled} = \frac{df_1}{df_{total}}s^2_1 + \frac{df_2}{df_{total}}s^2_2 \qquad SE_{difference} = \sqrt{\frac{s^2_{pooled}}{n_1} + \frac{s^2_{pooled}}{n_2}}$$

which simplifies to:

$$
SE_{difference} =
\sqrt{
\frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}
{(n_1 + n_2 - 2)}
\left(
\frac{1}{n_1} + \frac{1}{n_2}
\right)
}$$

<Admonition type="warning" width="100%">
Are you kidding me?
</Admonition>

<p v-click>

Good news: in practice, you will almost never compute this by hand. It's important to understand where it comes from — but you'll use statistical software (e.g., R) to compute it for you.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Let's Test Our Intuitions

:: content ::

<Admonition title="Question" color="teal-light" width="100%">
If we increase the sample sizes (n₁ and n₂) while keeping the sample variances (s₁² and s₂²) constant, what happens to the standard error of the difference between means (SE_difference)?
</Admonition>

<p v-click>

**Answer:** It decreases. As sample sizes increase, our estimates of the population parameters become more precise, leading to a smaller standard error — just like with the single-sample and paired-samples *t* tests.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Step 4: Determine Critical Values (Cutoffs)

:: content ::

- We now need to determine where the middle 95% of this comparison distribution lies (since we are using an alpha level of .05 for a two-tailed test).
- We are using a *t* distribution to account for our additional uncertainty due to estimating the population standard deviations from our samples.
- We can find out critical values from a t-table or computer program.
- Here our degrees of freedom (df) is computed as:
  - df = (n₁ − 1) + (n₂ − 1) = n₁ + n₂ − 2
- This is because we are estimating the population standard deviation twice (once for each sample).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Step 5: Compute the Test Statistic

:: content ::

- We now need to compute the test statistic (*t*), by subtracting the hypothesized population mean difference (0 under H₀) from the observed mean difference between our two samples, and dividing by the standard error of the difference between means.

$$t = \frac{M_D-\mu_D}{SE}$$

- Here:
  - $M_D$ = observed mean difference between the two samples
  - $\mu_D$ = hypothesized population mean difference (0 under H₀)
  - $SE$ = standard error of the difference between means

- This simplifies to:

$$t = \frac{M_1 - M_2}{SE_{difference}}$$


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Step 6: Make a Decision

:: content ::

- We use exactly the same decision rule as before:
  - If the calculated *t* value falls in the critical region (beyond the critical values), we reject H₀.
  - If the calculated *t* value does not fall in the critical region, we fail to reject H₀.

<img src="/images/lecture11/phew.gif"  class="w-1/3 mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Confidence Intervals for Independent-Samples *t* Tests

:: content ::

- We use exactly the same calculation as before:

$$CI = (M_1 - M_2) \pm (t_{crit} \times SE_{difference})$$

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Effect Sizes for Independent-Samples *t* Tests

:: content ::

- We use exactly the same calculation as before:

$$d = \frac{(M_1 - M_2)}{s}$$

Where s is the pooled standard deviation:
$$s = \sqrt{s^2_{pooled}}$$

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Independent-Samples *t* Test

:: left ::

*A researcher wants to know whether students who exercise regularly sleep more than students who don't. She recruits 5 students who exercise regularly and, separately, 5 students who don't exercise, and asks them to report their average nightly sleep duration.*

- Hours of sleep, **exercisers**: 7.5, 8.0, 6.5, 7.0, 8.5
- Hours of sleep, **non-exercisers**: 6.0, 5.5, 7.0, 6.5, 5.0

<Admonition title="Question" color="teal-light" width="100%">
Do students who exercise regularly sleep a significantly different amount than students who don't?
</Admonition>

:: right ::

<p v-click>

**Hint 1:** These are two independent groups of students (nobody is in both groups), so use an **independent-samples *t* test**.

</p>

<p v-click>

**Hint 2:** $n_1 = n_2 = 5$, so $df = n_1 + n_2 - 2 = 8$. Using an alpha level of .05 for a two-tailed test, $t_{crit}(8) = \pm 2.306$.

</p>

<p v-click>

**Hint 3:** $M_1 = 7.5$, $M_2 = 6.0$, $s^2_1 = s^2_2 = 0.625$.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Practice: Independent-Samples *t* Test (Solution)

:: content ::

**Steps 1-2:** Group 1 = exercisers, Group 2 = non-exercisers; distribution of differences between independent group means; DV (hours of sleep) is numeric, random samples, population SD unknown.
- **H₀:** μ₁ = μ₂ (no difference in sleep between groups)
- **H₁:** μ₁ ≠ μ₂ (sleep differs between groups)

**Step 3:** Because $n_1 = n_2 = 5$ and $s^2_1 = s^2_2 = 0.625$, the pooled variance is also $s^2_{pooled} = 0.625$.

$$SE_{difference} = \sqrt{\frac{0.625}{5} + \frac{0.625}{5}} = \sqrt{0.25} = 0.5$$

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Practice: Independent-Samples *t* Test (Solution)

:: content ::

**Step 4:** df = $n_1 + n_2 - 2 = 8$ → $t_{crit} = \pm 2.306$

**Step 5:**
$$t = \frac{M_1 - M_2}{SE_{difference}} = \frac{7.5 - 6.0}{0.5} = 3.00$$

**Step 6:** $3.00 > 2.306$ → **Reject H₀**

<p v-click>

<StickyNote color="green-light" title="Answer" width="100%">
Students who exercise regularly slept significantly more than students who don't, *t*(8) = 3.00, *p* < .05. The 95% CI is $1.5 \pm (2.306)(0.5) = [0.35, 2.65]$ hours, and the effect size is large: $d = 1.5/\sqrt{0.625} = 1.90$.
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Conducting *t* tests in R

:: content ::

- To conduct a *t* test in R, you can use the `t.test()` function.
- Here's a basic example:

```r
# Sample data
group1 <- c(5, 6, 7, 8, 9)
group2 <- c(10, 11, 12, 13, 14)

# Conducting the t-test
t.test(group1, group2, var.equal = TRUE, paired = FALSE)
```

- This will give you the t-statistic, degrees of freedom, and p-value for the test.
- Let's open R and see what this looks like.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Worksheet time!

:: content ::

- The shared worksheet walks you through the steps of an independent-samples *t* test.
- Work through it with a partner or small group.
- We will go over the solution together next class.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Reporting an Independent-Samples *t* Test

:: content ::

**Template**

$t(df) = X.XX, \ p = P, \ d = D, \text{ 95\% CI [LL, UL]}$

**Example**

Participants in the study-group condition had higher quiz scores (*M* = 84.6, *SD* = 4.2) than participants in the individual condition (*M* = 78.3, *SD* = 5.0), *t*(38) = 4.11, *p* < .001, *d* = 1.30, 95% CI \[3.21, 9.59].

✅ State the means and SDs for **both** groups.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
How many participants were in this study?
</Admonition>

</p>

<p v-click>

**Answer:** df = n₁ + n₂ − 2 = 38, so n₁ + n₂ = 40 total participants.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# A Brief Aside: Where Did *t* Tests Come From?

:: content ::
- *t* tests were developed by William Sealy Gosset in 1908 while working at the Guinness Brewery in Dublin, Ireland. Gosset wanted to monitor the quality of raw materials (e.g., barley) used in brewing, but he had only small samples to work with.
- To address this problem, he developed the *t* distribution and the *t* test, which allowed him to make inferences about population means from small samples.
- He published his work under the pseudonym "Student" to avoid conflicts with Guinness's policy against employees publishing research.

<img src="/images/lecture11/guinness.jpg"  class="w-1/4 mx-auto"/>

---
layout: cover
color: indigo-light
---

# That's all for today!
Next class: Exam 3 Review (covers Lectures 13-14)
