---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 13
exportFilename: ps211_fall2026_lecture13
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 13: Paired-Samples *t*-Tests & Reporting Results in APA Style

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- No standalone homework this week — instead, keep an eye out for our first ==Data Write-Up== (t-test-based), due **Monday, November 16**. Today and Thursday, you'll have both paired- and independent-samples *t* tests in hand for it.
- Office hours this week:
  - Tuesday: 12:30 - 1:30 pm (Kate)
  - Thursday: 9:00 - 10:00 am (Kate)
- Coming up:
  - Thursday (11/5): Lecture 14 — Independent-Samples *t* Tests (in R)
  - Tuesday (11/10): Exam 3 Review
  - Thursday (11/12): Exam 3 (covers Lectures 13-14)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Types of *t* Tests

:: content ::
There are 3 types of *t* tests, used in different research scenarios:

1. **Single-sample *t* test** – Compare a sample mean to a population mean when the population SD is unknown.

<div class="mt-0 w-full flex justify-center">
<div class="bg-blue-100 border-2 border-blue-300 rounded-lg shadow-md p-3 transform">
  This is what we went over already!
</div>
</div>

<br>

<p v-click>

2. **Paired-sample *t* test** – Compare two samples when every participant is in both samples (within-subjects design).
3. **Independent-samples *t* test** – Compare two samples when participants are in only one group (between-subjects design).

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Between- vs Within-Subjects Designs

:: left ::
### Within-Subjects
- Each participant experiences **all** levels of the independent variable.
- Comparisons are made *over time or conditions* for the same people.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What is an advantage of a within-subjects design?
</Admonition>

</p>


:: right ::
### Between-Subjects
- Each participant experiences **only one** level of the independent variable.
- Comparisons are made *between different people*.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What is an advantage of a between-subjects design?
</Admonition>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which *t* Test Should I Use?

:: content ::
- **Within-groups design** → use a *paired-samples t test*
- **Between-groups design** → use an *independent-samples t test*

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
For the paired *t*, we must first create **difference scores** for each participant (e.g., after – before; Condition 1 - Condition 2).
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What is a Paired-Samples *t* Test?

:: content ::
- Compares two means for a **within-groups** design in which each participant experiences both levels of an independent variable.
- Can also be used for **before-and-after** comparisons.


<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Imagine you want to measure "Stroop Interference" by testing participants' reaction times on a color-naming task where the words are either congruent or incongruent with the ink color. How would you design this study to test for differences in reaction times using a paired-samples *t* test?
</Admonition>

</p>

<p v-click>

<StickyNote color="green-light" title="Answer" width="100%">
- Have each participant complete both the congruent and incongruent conditions of the Stroop task.
- Measure their reaction times for each condition.
- Use a paired-samples *t* test to compare the mean difference in reaction times across all participants to determine if there is a significant effect of condition on reaction time.
</StickyNote>

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Distributions of Mean *Differences*


:: content ::

**Another distribution!**

<img src="/images/lecture10/ohno.jpg"  class="w-1/6 mx-auto"/>


<br>

To start a paired-samples *t*, we must create a **distribution of mean differences** by subtracting the two scores for each participant and then sampling means of those differences repeatedly.

- Step 1: Randomly sample n participants.
- Step 2: Compute each participant's difference score (Condition 2 – Condition 1).
- Step 3: Compute the mean of these differences across all participants in a sample.
- Step 4: Repeat many times to build a distribution of mean differences for a population.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Distribution of Mean Differences

:: content ::

A researcher wants to determine whether students sleep more when internet access in their dorms is restricted at night. She has 30 students report their average nightly sleep duration for one week *with* internet access and one week *without* internet access.

To conduct a paired-samples *t* test, she needs to determine the probability that the observed mean difference in sleep duration occurred by chance, assuming no true difference in sleep duration across conditions.

To do this, she needs to create a **distribution of mean differences** under the null hypothesis:
- Assume no true difference in sleep duration across conditions.
- Randomly sample 30 (or n) students from this (simulated) population and compute the mean difference in sleep duration for each sample.
- Repeat this process many times to build a distribution of mean differences.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Distribution of Mean Differences

:: content ::

<div class="flex justify-center space-x-6">
  <img src="/images/lecture10/mean_diff_sleep_hist_n30_null.png" alt="n30" class="w-1/3" />
  <img src="/images/lecture10/mean_diff_sleep_hist_n10_null.png" alt="n10" class="w-1/3" />
</div>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Will the shape of these null distributions always be normal?
</Admonition>

</p>

<p v-click>

**Answer:** Yes, if the sample size is sufficiently large. Due to the Central Limit Theorem, the distribution of the mean differences will approach normality as the sample size increases.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Conducting a Paired-Sample *t* Test

:: left ::

Under the **null hypothesis**, we assume there is no average difference in sleep duration across the population:
$$\mu_1 - \mu_2 = 0$$

<img src="/images/lecture10/mean_diff_sleep_hist_n30_null.png"  class="w-3/4 mx-auto" />

:: right ::

- We can use this distribution of mean differences to determine the **probability of observing a mean difference as extreme as the one in our sample**, assuming the null hypothesis is true.

- If the researcher observes a mean difference in sleep duration of 0.5 hours in her sample of 30 students, she can calculate the *t* statistic to see how many standard errors this observed mean difference is away from the null hypothesis mean difference of 0.



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Steps of a Paired-Sample *t* Test

:: content ::

1. Identify populations, distribution, & assumptions.
2. State null and research hypotheses.
3. Determine characteristics of comparison distribution.
4. Determine critical values (cutoffs).
5. Calculate test statistic.
6. Make a decision.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Example: Sleep and Internet Access

:: left ::
A researcher wants to determine whether students sleep more when internet access in their dorms is restricted at night. She has 5 students report their average nightly sleep duration for one week *with* internet access and one week *without* internet access.

- Hours of sleep **with** internet access:
  - 6.5, 7.0, 6.0, 5.5, 6.0

- Hours of sleep **without** internet access:
  - 7.0, 7.5, 5.5, 6.0, 7.0

:: right ::

<p v-click>

We'll test if mean hours of sleep differ across conditions using a **paired-samples *t test.***

<img src="/images/lecture10/t_test_meme.jpg"  class="w-3/4 mx-auto" />

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 1: Populations & Assumptions

:: content ::
- Group 1: Sleep reports with internet access.
- Group 2: Sleep reports without internet access.
- Distribution: Differences between paired scores.
- Assumptions:
  - DV is numeric.
  - Random sample of students.
  - Population distribution (including SD in average numbers of sleep) is unknown.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 2: Hypotheses

:: content ::
- **Null (H₀):**  μ₁ = μ₂  (no mean difference)
  - or equivalently:  μ₁ − μ₂ = 0
  - In words: Students sleep the same amount with or without internet access.

- **Research (H₁):**  μ₁ ≠ μ₂  (there is a difference)
  - or equivalently:  μ₁ − μ₂ ≠ 0
  - In words: Students sleep different amounts with vs. without internet access.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 3: Determine Characteristics of the Comparison Distribution

:: content ::
Under the null, the mean of the comparison distribution = 0. Because we don't know the population SD, we must estimate the standard deviation from the sample data, just like in a single-sample *t* test.

<div class="text-xs w-2/3 mx-auto mt-2" style="line-height:1.1">

<table class="border-collapse w-full">
 <thead>
    <tr>
      <th>Participant</th>
      <th>With Internet</th>
      <th>Without Internet</th>
      <th>Difference (D)</th>
      <th>D − Mean D (0.4)</th>
      <th>Squared Deviation</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>6.5</td><td>7.0</td><td>0.5</td><td>0.1</td><td>0.01</td></tr>
    <tr><td>2</td><td>7.0</td><td>7.5</td><td>0.5</td><td>0.1</td><td>0.01</td></tr>
    <tr><td>3</td><td>6.0</td><td>5.5</td><td>-0.5</td><td>-0.9</td><td>0.81</td></tr>
    <tr><td>4</td><td>5.5</td><td>6.0</td><td>0.5</td><td>0.1</td><td>0.01</td></tr>
    <tr><td>5</td><td>6.0</td><td>7.0</td><td>1.0</td><td>0.6</td><td>0.36</td></tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sum of Squares (SS)</strong></td>
      <td><strong>1.20</strong></td>
    </tr>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sample Variance (s² = SS / 4)</strong></td>
      <td><strong>0.30</strong></td>
    </tr>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sample SD (√s²)</strong></td>
      <td><strong>0.55</strong></td>
    </tr>
  </tfoot>
</table>

</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 3: Determine Characteristics of the Comparison Distribution

:: content ::
- Now, we can compute the standard error (SE) of the mean differences:
  $$SE = \frac{s}{\sqrt{n}} = \frac{0.55}{\sqrt{5}} = 0.246$$
- Thus, our comparison distribution has:
  - Mean = 0
  - SE = 0.246

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Step 4: Determine the Critical Values (or Cutoffs)

:: content ::
- df = N – 1 = 4
- The critical values are determined by the t-distribution with 4 degrees of freedom.
- We will use an alpha level of .05 for a two-tailed test.
- We can find out critical values from a t-table or computer program:
→ $t_{crit}= ± 2.776$

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Steps 5: Calculate the Test Statistic

:: content ::
- We calculate our *t* value using the formula:
  $$t = \frac{M_{diff}-\mu_D}{SE}$$
  where:
  - $M_{diff}$ = sample mean difference
  - $\mu_D$ = hypothesized population mean difference (0 under H₀)
  - SE = standard error of the mean differences

$$t = \frac{M_{diff}-0}{SE} = \frac{0.4}{0.246} = 1.63$$



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Steps 6: Make a Decision

:: content ::
- Compare calculated *t* to critical values:
  - Calculated *t* = 1.63
  - Critical values = ± 2.776

1.63 < 2.776 → **Fail to Reject H₀**

<img src="/images/lecture10/p_meme.jpg"  class="w-1/4 mx-auto" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Confidence Intervals for Paired-Sample *t* Tests

:: content ::

- A **confidence interval (CI)** provides a range of values within which we are fairly certain the true population parameter lies.
- For a paired-samples *t* test, we can construct a CI around the sample mean difference to estimate the range of plausible values for the true mean difference in the population.
- A 95% CI means that if we were to take many samples and construct a CI for each sample, approximately 95% of those intervals would contain the true population mean difference.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Computing a 95% Confidence Interval for the Mean Difference

:: content ::
- To compute a 95% confidence interval for the mean difference, we can use the following formula:
  $$CI = M_{diff} \pm t_{crit} \times SE$$

<p v-click>

*Why can we use this formula?*
- This formula is similar to the one used for single-sample *t* tests, but here we are using the mean difference and the standard error of the mean differences.

</p>

<p v-click>

- Plugging in our values:
  $$CI = 0.4 \pm 2.776 \times 0.246$$
- This gives us:
  $$CI = 0.4 \pm 0.683 = [-.283, 1.083] $$

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interpreting the Confidence Interval

:: content ::
- The sample mean (0.4) is centered within CI [-0.283, 1.083].
- If we repeated this study many times, ≈ 95% of CIs would contain the true population mean difference.
- Because the CI includes 0, we cannot rule out the possibility that there is no true difference in sleep duration across conditions.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Beyond Hypothesis Testing: Effect Size

:: content ::
- The effect size indicates the magnitude of the difference between conditions in standard deviation units.

- For paired-samples *t* tests, we can use **Cohen's d** to quantify effect size:
  $$d = \frac{M_{diff} - 0}{s}$$
  where:
  - $M_{diff}$ = sample mean difference
  - $s$ = sample standard deviation of the differences

- Using our example:
  $$d = \frac{0.4}{0.55} = 0.73$$

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Beyond Hypothesis Testing: Effect Size

:: content ::

 $$d = \frac{0.4}{0.55} = 0.73$$

- Interpretation:
- $d = 0.2$ → small effect.
- $d = 0.5$ → medium effect.
- $d = 0.8$ → large effect.

*If this study were repeated with a larger sample size, we might find a significant (and meaningful) effect!*


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Paired-Samples *t* Test

:: left ::

*Students complete a short quiz twice — once with music, once in silence. The instructor wants to know if background music helps or hurts performance.*

- Scores with music: 7, 6, 5, 8, 7
- Scores without music: 8, 6, 7, 9, 8

<Admonition title="Question" color="teal-light" width="100%">
What would you tell the instructor about the effect of background music on quiz performance?
</Admonition>

:: right ::

<p v-click>

**Hint 1:** You will need to compute:
- The difference in each pair of scores
- The mean and standard deviation of the differences
- The standard error of the mean differences
- The *t* statistic

</p>


<p v-click>

**Hint 2:** Using an alpha level of .05 for a two-tailed test, the critical values for df = 4 are ± 2.776.

</p>

<p v-click>

**Hint 3:** It doesn't matter whether you subtract "with music - without music" or "without music - with music," as long as you are consistent. The magnitude of the *t* statistic will be the same; only the sign will differ.

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Paired-Samples *t* Test (Solution)

:: left ::

1. Step 1: Populations & Assumptions
- Group 1: Quiz scores with music.
- Group 2: Quiz scores without music.
- Distribution: Differences between paired scores.
- Assumptions:
  - DV is numeric.
  - Random sample of students.
  - Population distribution (including SD in quiz scores) is unknown.

:: right ::

2. Step 2: Hypotheses
- **Null (H₀):**  μ₁ = μ₂  (no mean difference)
  - or equivalently:  μ₁ − μ₂ = 0
  - In words: Music does not affect quiz performance.

- **Research (H₁):**  μ₁ ≠ μ₂  (there is a difference)
  - or equivalently:  μ₁ − μ₂ ≠ 0
  - In words: Music affects quiz performance.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Practice: Paired-Samples *t* Test (Solution)

:: content ::

3. Step 3: Determine Characteristics of the Comparison Distribution

<div class="text-xs w-2/3 mx-auto mt-2" style="line-height:1.1">

<table class="border-collapse w-full">
  <thead>
    <tr>
      <th>Participant</th>
      <th>With Music</th>
      <th>Without Music</th>
      <th>Difference (D)</th>
      <th>D − Mean D (-1)</th>
      <th>Squared Deviation</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>7</td><td>8</td><td>-1</td><td>0</td><td>0</td></tr>
    <tr><td>2</td><td>6</td><td>6</td><td>0</td><td>1</td><td>1</td></tr>
    <tr><td>3</td><td>5</td><td>7</td><td>-2</td><td>-1</td><td>1</td></tr>
    <tr><td>4</td><td>8</td><td>9</td><td>-1</td><td>0</td><td>0</td></tr>
    <tr><td>5</td><td>7</td><td>8</td><td>-1</td><td>0</td><td>0</td></tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sum of Squares (SS)</strong></td>
      <td><strong>2.00</strong></td>
    </tr>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sample Variance (s² = SS / 4)</strong></td>
      <td><strong>0.50</strong></td>
    </tr>
    <tr>
      <td colspan="5" style="text-align:right;"><strong>Sample SD (√s²)</strong></td>
      <td><strong>0.71</strong></td>
    </tr>
  </tfoot>
</table>

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Paired-Samples *t* Test (Solution)

:: left ::

3. Step 3: Determine Characteristics of the Comparison Distribution (continued)
- Now, we can compute the standard error (SE) of the mean differences:
  $$SE = \frac{s}{\sqrt{n}} = \frac{0.71}{\sqrt{5}} = 0.318$$
- Thus, our comparison distribution has:
  - Mean = 0
  - SE = 0.318

:: right ::
4. Step 4: Determine the Critical Values (or Cutoffs)
- df = N – 1 = 4
- The critical values are determined by the t-distribution with 4 degrees of freedom.
- We will use an alpha level of .05 for a two-tailed test.
- We can find out critical values from a t-table or computer program (and were told it here):
→ $t_{crit}= ± 2.776$


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Paired-Samples *t* Test (Solution)

:: left ::

5. Step 5: Calculate the Test Statistic
- We calculate our *t* value using the formula:
  $$t = \frac{M_{diff}-\mu_D}{SE}$$
  where:
  - $M_{diff}$ = sample mean difference
  - $\mu_D$ = hypothesized population mean difference (0 under H₀)
  - SE = standard error of the mean differences

$$t = \frac{M_{diff}-0}{SE} = \frac{-1}{0.318} = -3.14$$

:: right ::

<p v-click>

6. Step 6: Make a Decision

- Compare calculated *t* to critical values:
  - Calculated *t* = -3.14
  - Critical values = ± 2.776
  - -3.14 < -2.776 → **Reject H₀**

<StickyNote color="green-light" title="Answer" width="100%">
The results suggest that background music has a significant effect on quiz performance, with students performing *worse* when music is played during the quiz.
</StickyNote>

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting Results in APA Style

:: content ::
APA style tells us **how to clearly report statistics** so others can understand and replicate our work.
It ensures clarity and consistency across psychology and related sciences.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# What is APA Style?

:: content ::

- **APA** = *American Psychological Association*
- A standardized format for writing and reporting scientific results
- Ensures clarity, transparency, and consistency across research papers

<StickyNote color="amber-light" title="APA style guides how we..." width="100%">
• write numbers and statistics
• report results of tests (*t*, *z*, *F*, etc.)
• format p-values, CIs, and effect sizes
</StickyNote>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Why Use APA Style?

:: content ::
- Helps readers quickly interpret results.
- Makes research **replicable** and **comparable**.
- Prevents ambiguity — everyone reports in the same format.
- Required by most psychology journals and conferences.

<div class="mt-3 italic text-gray-700">
Think of APA as the "grammar rules" of scientific writing.
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Always Include These Elements

:: content ::
| Element | Description | Example |
|----------|--------------|----------|
| **Test statistic** | Which test you ran (*t*, *z*, *F*) | *t* |
| **Degrees of freedom (df)** | Indicates sample size info | *t*(28)|
| **Test value** | The computed statistic | *t*(28) = 2.45 |
| **p value** | Probability under H₀ | *p* = .004 or *p* < .001 |
| **Descriptive stats** | Means, SDs for each group | *M* = 5.3, *SD* = 1.2 |

✅ These should appear in **every** statistical report.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Technically optional (but strongly recommended)

:: content ::
| Element | Why Include It | Example |
|----------|----------------|----------|
| **Effect size** | Shows *magnitude* of difference | *d* = 0.68 |
| **Confidence interval (CI)** | Range of plausible values | 95% CI \[0.12, 1.24] |
| **Exact p value** | More informative than *p* < .05 | *p* = .037 |

<div class="mt-3 text-gray-600">

- Including these helps readers understand *how strong* and *how precise* your findings are.
- Many journals now require effect sizes, CIs, and exact p-values.
- There is no reason *not* to include them!
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Formatting Rules (APA 7th Edition)

:: content ::
- Italicize *t*, *z*, *p*, *M*, *SD*, *F*, *r*
- Use **two decimal places** for statistics (except *p*)
- Report *p* values as:
  - *p* = .042 (no leading zero)
  - *p* < .001 (for very small values)
- Match decimal precision across CIs and descriptive stats

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Reporting a *z* Test

:: content ::

**Template**

$M = X, \ SD = Y, \ z = Z, \ p = P, \ d = D,  \text{ 95\% CI [LL, UL]}$

**Example**

Students' average rent (*M* = $920, *SD* = $192) was significantly higher than the population mean of $500, *z* = 9.39, *p* < .001, *d* = 4.20, 95% CI \[$832, $1008].

✅ No *degrees of freedom* are reported for *z* tests. *Z* tests are based on known population parameters, not sample estimates, so df are not applicable.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a One-Sample *t* Test

:: content ::

**Template**

$t(df) = X.XX, \ p = P, \ d = D, \text{ 95\% CI [LL, UL]}$

**Example**

The sample's mean reaction time (*M* = 312 ms, *SD* = 28) was significantly faster than the population mean of 350 ms, *t*(14) = −5.68, *p* < .001, *d* = 1.47, 95% CI \[−50.1, −21.9].

<br>

✅ State the **known or hypothesized** population mean and the sample mean and SD.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Reporting a Paired-Samples *t* Test

:: content ::
**Template**

$t(df) = X.XX, \ p = P, \ d = D, \text{ 95\% CI [LL, UL]}$

**Example**

Participants recalled more words after caffeine (*M* = 12.3, *SD* = 2.1) than without caffeine (*M* = 9.8, *SD* = 2.5), *t*(19) = 3.42, *p* = .003, *d* = 0.76, 95% CI \[0.92, 4.11].

<br>

✅ State the means and SDs for **both** conditions.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Putting It All Together

:: content ::
<div class="grid grid-cols-2 gap-6">

<div>

### Always Include
- Test type and statistic (*t*, *z*, etc.)
- df (for *t* tests)
- *p* value
- Descriptive stats (*M*, *SD*)

</div>

<div>

### Usually Include
- Effect size (*d*, *r*, etc.)
- Confidence interval
- Directional phrasing ("significantly greater than…")

</div>

</div>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# APA Reporting: Practice 🧠

:: content ::
**Rewrite in APA style:**

Participants slept on average 7.6 hours (s.d.=0.8) which was not significantly different from the national mean of 7.5. The T test was not significant (P = .66; t = .45; DF=19). Cohen's D = 0.06 and the 95% confidence interval was (-0.42 , 0.62).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Answer

:: content ::

#### 😴 Correct Example — One-Sample *t*

> Participants slept an average of 7.6 hours (*SD* = 0.8), which did not differ significantly from the national mean of 7.5,
> *t*(19) = 0.45, *p* = .66, *d* = 0.06, 95% CI \[−0.42, 0.62].

*What was fixed?*
- Italicize statistical symbols (*t*, *p*, *d*, *M*, *SD*).
- Write numbers and units clearly ("7.6 hours").
- Keep *p* = .66 (not *P* = 0.66), and report *t*(df) = value, *p*, *d*, and 95% CI in this order.
- Report CI in brackets.

---
layout: cover
color: indigo-light
---

# That's all for today!
We will continue with independent-samples *t* Tests (in R) on Thursday!
