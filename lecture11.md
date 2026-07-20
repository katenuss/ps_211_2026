---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 11
exportFilename: ps211_fall2026_lecture11
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 11: Effect Size & Statistical Power

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and Reminders

:: content ::
- No standalone homework this week — instead, keep an eye out for our first ==Data Write-Up== (t-test-based), due **Monday, November 16**.
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
# Quick Recap: Z Tests & Confidence Intervals

:: content ::
- Last time, we covered ==*z* tests== and ==confidence intervals (CIs)== in depth — today builds directly on that.

### Quick recap
- A ***z* test** compares a sample mean to a population mean when we know the population SD.
- A ==confidence interval== gives a range of plausible values for the population mean, built around our sample mean.
- CIs and hypothesis tests agree: if the population mean falls **outside** our CI, we reject $H_0$.

<Admonition title="Formula refresher" color="teal-light" width="100%">

$$z = \frac{M-\mu}{SE}, \quad SE = \frac{SD}{\sqrt{n}}, \quad CI = M \pm z_{crit}(SE)$$

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Example: Screen Time of Teens vs. Adults

:: left ::
- Nielsen (2018): U.S. adults spend **11  hours/day** on screens ($\mu=11$, $SD=2$)
- We measure a sample of **20  teens** → $M=9$

==Do teens and adults differ in how much time they spend on screens?==


- Compute the probability (*p* value) that the teen population distribution and the adult population distribution are the same.

- Compute a 95% CI for the *population mean* of teens.

:: right ::

<p v-click>

==For the *p* value (*z*-test)==
1. Convert 9 to *z* score:
$$\frac{(9-11)}{2/\sqrt(20)}= - 4.47$$
2. Use *z* table to convert to percentile / probability: $< .001$

</p>

<p v-click>

==For the 95% CI==
1. Compute $SE$:  $2 / \sqrt{20} = 0.447$
2. Find $z_{crit}=1.96$
3. Compute bounds:  $9 \pm 1.96(0.447)$ → [8.12, 9.88]

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Confidence Intervals and Significance

:: content ::
- CI and hypothesis testing give consistent conclusions.
- If the **population mean** (e.g., 11 hours) **falls outside** the 95% CI, we reject the null hypothesis.
- If it **falls inside**, we fail to reject.

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
A CI provides more information than a simple reject/fail‑to‑reject decision — it is an ==interval estimate== that shows the range of plausible effects.
</SpeechBubble>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Effect Size

:: content ::
- Statistical significance depends on the sample size.
- The larger the sample size, the more likely it is that a statistically significant result will be found.

<Admonition title="Question" color="teal-light" width="100%">
Based on what we know about *z* tests, why is this the case?
</Admonition>

<p v-click>

**Answer:** Larger sample sizes provide more "certain" estimates of the population parameters, reducing the standard error and increasing the likelihood of finding a statistically significant effect.

</p>

<p v-click>

- The ==**effect size**== tells us *how big* the effect actually is.
- It measures the ==magnitude of a difference== in standardized units.
</p>

<p v-click>

**Example:** Researchers examine standardized math test scores in over 500,000 students across the country. They find that, on average, girls score .3 points lower than boys. This effect is *statistically significant.* But is it meaningful?
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What is effect size?

:: content ::
- Tells us the size of a difference that is *unaffected* by sample size.
- Allows standardization across studies
- Tells how much two populations do not overlap – the less overlap, the bigger the effect size
- Said in another way, the effect size is a ==quantitative measure of the magnitude of the experimental effect.==
  - The larger the effect size, the stronger the relationship between two variables.


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
# Calculating effect size

:: content ::
- ==Cohen's d== is a common statistical measure of effect size.
- We calculate Cohen's d by taking the difference between two means and dividing by the data's standard deviation.
- Cohen (1990) used the small but statistically significant correlation between height and IQ to explain the difference between statistical significance and practical importance.
  - His sample size was big: 14,000 children!
  - Cohen calculated that a person would have to grow by 3.5 feet to increase her IQ by 30 points (2 standard deviations)
  - Or, to increase her height by 4 inches, she would have to increase her IQ by 233 points!
  - Height may have been statistically significantly related to IQ, but there was no practical real-world application.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Calculating effect size (continued)

:: content ::
- To calculate Cohen's d, we use the same formula as for the *z* statistic, but we substitute the standard deviation for the standard error:


**Cohen's _d_:**
$$d = \frac{M_1 - M_2}{SD}$$

- This way, the effect size (Cohen's d) is based on the spread of the distribution of individual scores (standard deviation), not the distribution of means (standard error).

<Admonition title="Question" color="teal-light" width="100%">
What is the effect size for the difference in teens' vs. adults' screen time?

$M1 = 11; M2 = 9; SD = 2$
</Admonition>


<p v-click>

<Admonition color="green-light" title="Answer" width="100%" v-click>
d = 1. This tells us that on average, teens' screen time is 1 full standard deviation below that of adults'. This is a *large* effect.
</Admonition>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Practice: Study Hours

:: content ::
- Let's practice calculating Cohen's d with another example.
- A tutoring center wants to know if students who use their weekly study group study more than students who don't.
- Students who attend the study group study an average of **9 hours/week** ($M_1 = 9$).
- Students who don't attend study an average of **7 hours/week** ($M_2 = 7$).
- The standard deviation of study hours across all students is **4 hours** ($SD = 4$).

<Admonition title="Question" color="teal-light" width="100%">
What is Cohen's d for this comparison? How would you interpret it?
</Admonition>

<p v-click>

<Admonition color="green-light" title="Answer" width="100%" v-click>

$$d = \frac{9-7}{4} = 0.5$$

A d of 0.5 is a *medium* effect size (using Cohen's conventions, coming up next) — noticeably smaller than the large effect (d = 1) we saw with screen time, even though both differences were "only" 2 units on their own scales.
</Admonition>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Conventions for interpreting effect sizes

:: content ::
- Jacob Cohen published guidelines (or conventions) based on the overlap between two distributions to help researchers determine whether an effect is small, medium, or large.
- These numbers are not cutoffs; they are merely rough guidelines to help researchers interpret results.
- If the difference between two groups' means is less than 0.2, the difference is not important, even if it's significant.


<img src="/images/lecture9/cohens_d.jpeg" alt="Effect size interpretation" class="w-1/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Statistical Power

:: content ::
- ==**Statistical Power**== = probability of correctly rejecting $H_0$ when it's false (avoiding a Type II error).
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
layout: cover
color: indigo-light
---

# That's all for today!
See you next time, when we'll talk about parametric assumptions and get our first look at *t* tests.
