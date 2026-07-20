---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 15
exportFilename: ps211_fall2026_lecture15
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 15: One-Way ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- ==Exam 3== grades are posted.
  - We will go over difficult questions in class if needed.
- No standalone homework this week — keep in mind our second ==Data Write-Up== (ANOVA-based) is due **Monday, December 7**.
- Office hours this week:
  - Tuesday: 12:30 - 1:30 pm (Kate)
  - Thursday: 9:00 - 10:00 am (Kate)
- This week:
  - Lecture 15 (today): One-Way ANOVA
  - Lecture 16 (Thurs): Repeated-Measures ANOVA & Two-Way ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# What's coming up

:: content ::
- Two more "gradeable" assignments left in the course:
  - Data Write-Up #2 (ANOVA-based, due Mon. 12/7)
  - Exam 4 (Thurs. 12/10)
- Next week (11/24):
  - Lecture 17 (Tues): Correlation
  - **No class Wed. 11/25 or Thurs. 11/26 — Thanksgiving break**
- Week of 12/1:
  - Lecture 18 (Tues): Regression
  - Lecture 19 (Thurs): Chi-Square & Non-Parametric Tests

---
layout: section
color: indigo-light
align: lt
---

Moving to our next topic...
# One-Way ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Are We Worse Drivers When on the Phone?

:: content ::

A simple *t*-test compares driving ability when talking vs. not talking on the phone.

<p v-click>

But what if we wanted to compare **more than two conditions**?
</p>


<p v-click>

💭 Possible conditions:
– Driving alone
– With a passenger
– On a cell phone
– On a video call

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Can I Use a *t* Test to Compare >2 Groups?

:: content ::

If you used a *t*-test for every possible combination, you'd run many tests!

- Driving alone vs. passenger
- Driving alone vs. video call
- Driving alone vs. cell phone
- Passenger vs. video call
- Passenger vs. cell phone
- Video call vs. cell phone

That's **6 *t*-tests!**

<p v-click>

Is there any problem with that? 🤔
Yes — it **increases the chance of a Type I error** (false positive).
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why You Can't Do Many *t* Tests

:: content ::
- Each test carries a 5% chance (*α* = .05) of a **Type I error** — falsely rejecting the null.
  - There is a 5% chance of concluding there is a difference when there really isn't one.
  - There is a 95% chance of correctly *failing* to reject the null.
- The more *t*-tests you do, the higher your overall risk of error.
- This problem is called **alpha inflation**.

<p v-click>

With one test → 95% chance of correctly retaining the null & 5% chance of a false positive


With two tests -> 95% chance of correctly retaining the null **twice** → $(0.95)^2 = 0.903$ → 10% chance of error


With three tests → 95% chance of correctly retaining the null **three** times → $(0.95)^3 = 0.857$ → 14% chance of error

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why You Can't Do Many *t* Tests (continued)

:: content ::

<p v-click>

So if you did 6 *t*-tests (like in our example), you'd have **a 54% chance of a Type I error!**
</p>

<p v-click>

<AdmonitionType type="warning" width="100%">
Multiple t-tests inflate the error rate. We need a single test for 3+ groups.
</AdmonitionType>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Solution: Using the *F* Statistic

:: content ::
When we want to compare **3 or more means**, we use the **F distribution** — the foundation of ANOVA.

<p v-click>

Like *z* and *t* tests, the *F* statistic is a **ratio**:

</p>

<p v-click>

$$z = \frac{\text{Difference Between Means}}{\text{Standard Error}}$$

</p>

<br>

<p v-click>

$$t = \frac{\text{Difference Between Means}}{\text{Standard Error}}$$

</p>

<br>


<p v-click>
$$
F = \frac{\text{Between-Groups Variance}}{\text{Within-Groups Variance}}
$$

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Solution: Using the *F* Statistic


:: content ::

$$
F = \frac{\text{Between-Groups Variance}}{\text{Within-Groups Variance}}
$$


<p v-click>

- The **numerator** captures how far apart the group means are.
- The **denominator** captures how much variability exists within each group.
</p>

<p v-click>

The bigger the ratio, the more evidence that not all groups come from the same population.
</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Intuition for the *F* Statistic

:: left ::

- Think of the *F* statistic as an expansion of the *z* and *t* statistics:
  - *z* → can do one thing
  - *t* → can do a few things
  - *F* → can do lots of things
- Each builds on the same idea: comparing variability due to chance vs. systematic differences.

:: right ::

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
The *F* statistic captures both the **differences between groups** and the **noise within them**.
</SpeechBubble>

<p v-click>

*Which part of this equation captures systematic differences between groups?*

Whi*ch part captures "noise" within groups?*

$$
F = \frac{\text{Between-Groups Variance}}{\text{Within-Groups Variance}}
$$

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Characteristics of the *F* Distribution

:: content ::
- *F* is a **ratio of two variances** (between-groups / within-groups).
  - Variances are based on sums of squares (SS), so *F* is always **positive**.
- The *F* distribution is a *series* of distributions (like the *t* distribution)
  - There are **two values for degrees of freedom** in every *F* test:
    - One for the numerator (*df₁* = between-groups)
    - One for the denominator (*df₂* = within-groups)

<p v-click>

Like *t*, the *F* distribution changes shape depending on the sample size and number of groups.
</p>

<p v-click>

To use *F*, your data must be on a **numeric (interval or ratio)** scale.
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The *F* Table and Degrees of Freedom

:: content ::
- The *F* table expands the *t* table by adding **another dimension** for the number of groups.
- There's an *F* distribution for every combination of:
  - Sample size (→ *df₁*, numerator)
  - Number of groups (→ *df₂*, denominator)

<p v-click>

*F*(df₁, df₂) helps us decide whether group differences are larger than expected by chance.
</p>

<p v-click>

*In practice, most people don't use the *F* table directly — statistical software calculates the exact p-value for you!*

The important thing to understand is that your *p* value depends on ==both== degrees of freedom, which are determined by:
1. your sample size and
2. your number of groups.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# ANOVA Overview

:: content ::
==An **ANOVA** (*Analysis of Variance*) compares **differences between 3+ groups using one test.**==

<p v-click>

#### One-way between-groups ANOVA
- Hypothesis test used to compare means across **more than two independent groups**:
  - Groups are defined by a single independent variable (IV) with 3+ levels.
    - These levels are **categorical** (nominal/ordinal).
    - A between-groups ANOVA is used for a design where each participant appears in only one group.
  - The dependent variable (DV) is **numeric** (interval/ratio).

</p>

<p v-click>

Example: Comparing mean driving performance across four phone-use conditions.

</p>

<p v-click>

*Phone-use conditions: Categorical IV with 4 levels*

*Driving performance: Numeric DV*

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# ANOVA: What Are We Analyzing?

:: content ::
Even though the test is called an **analysis of variance**, what we're really doing is comparing **means**.

<p v-click>

We ask:
*Are the differences among group means larger than we would expect from random chance?*

</p>

<p v-click>

If the groups come from the same population, their means should be similar.

If the means are *very different*, that suggests at least one group differs systematically.
</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# The Two Sources of Variability

:: left ::
### 1️⃣ Between-Groups Variance
- How far apart are the **group means**?
- Captures **systematic differences** due to the independent variable.

### 2️⃣ Within-Groups Variance
- How spread out are scores **inside each group**?
- Captures **unsystematic noise** — individual differences or measurement error.

:: right ::
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
When between-group variability ≫ within-group variability, the *F* ratio becomes large → **evidence against the null**.
</SpeechBubble>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# How Do We Compute Between vs. Within Variability?

:: content ::

ANOVA divides the **total variability** in a dataset into two parts:

$$
SS_\text{Total} = SS_\text{Between} + SS_\text{Within}
$$


<p v-click>

#### Recap: Sum of Squares (SS) Refresher

To calculate variance, we compute the **sum of squared deviations** from the mean.

1. Subtract the mean from each score.
2. Square each deviation.
3. Add them up.

$$SS = \sum{(X - \bar{X})^2}$$

- This is the **Sum of Squares (SS)**.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# 1️⃣ Between-Groups Variability (*SS<sub>Between</sub>*)

:: content ::
- Start with the **mean of each group** (*M₁, M₂, M₃, …*).
- Compute how far each group mean is from the **grand mean** (*M<sub>G</sub>*, the mean of all scores).
- Weight each squared deviation by the **group size** (*n*).
- Add them up.

$$
SS_\text{Between} = \sum n_i (M_i - M_G)^2
$$

This reflects the variability **explained by group membership**.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# 2️⃣ Within-Groups Variability (*SS<sub>Within</sub>*)


:: content ::

- For each group, measure how much each individual score deviates from its group mean.
- Square those deviations and sum them across all groups.

$$
SS_\text{Within} = \sum \sum (X_{ij} - M_i)^2
$$

This captures **unexplained variability** — random noise and individual differences.

<p v-click>

*Why are there ==two== summation symbols?*

- The inner Σ says: For a given group i, sum the squared deviations of each person's score (j) from that group's mean
- The outer Σ says: Now repeat that process for each group, and add them all up.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Converting Sums of Squares to the *F* Statistic

:: content ::

We then divide each sum of squares by its degrees of freedom to obtain **mean squares (MS):**

$$
MS_\text{Between} = \frac{SS_\text{Between}}{df_\text{Between}}, \quad
MS_\text{Within} = \frac{SS_\text{Within}}{df_\text{Within}}
$$

<p v-click>

Where:
- $df_\text{Between} = k - 1$ (k = number of groups)
- $df_\text{Within} = N - k$ (N = total sample size)

</p>


<p v-click>
Finally, we compare the two:

$$
F = \frac{MS_\text{Between}}{MS_\text{Within}}
$$

</p>

<p v-click>

A large *F* value indicates that between-group variability is much greater than within-group variability → evidence against the null hypothesis.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Logic of the *F* Statistic

:: content ::
At its core, ANOVA is a **signal-to-noise ratio**:

$$
F = \frac{\text{Systematic variance (between groups)}}{\text{Random variance (within groups)}}
$$

- **Signal** → variability explained by your independent variable
- **Noise** → variability due to chance

<p v-click>

If *F* ≈ 1 → group differences are about what chance would produce.
If *F* >> 1 → the manipulation explains meaningful variance.
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Comparing *F* to *t*

:: content ::
At its core, the *F* statistic is a **signal-to-noise ratio**.

$$
F = \frac{\text{Systematic variance (between groups)}}{\text{Random variance (within groups)}}
$$

<br>

<p v-click>

==The *t* statistic can also be expressed as a signal-to-noise ratio:==

$$
t = \frac{\text{Difference Between Means}}{\text{Standard Error}}
$$

</p>

<p v-click>

- The measures are different, but the logic is the same.
- The numerator reflects systematic differences between groups, while the denominator reflects random noise.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interpreting *F*

:: content ::
- *F* values can't be negative.
- The **larger the *F***, the stronger the evidence that not all group means are equal.
- Whether an *F* is "large enough" depends on its **critical value** from the *F* distribution (*df₁*, *df₂*).

<p v-click>

If your observed *F* > critical *F*, you reject H₀ and conclude that ==at least one mean== differs from the others.
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The F Statistic Visualized: Between-Group Variance

:: content ::

<img src="/images/lecture13/anova_mean_demo.png"  class="w-3/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The F Statistic Visualized: Within-Group Variance

:: content ::

<img src="/images/lecture13/anova_var_demo.png"  class="w-3/4 mx-auto"/>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Setting Up the Hypotheses

:: left ::

**Null hypothesis (H₀):**
All population means are equal.
$$
\mu_1 = \mu_2 = \mu_3 = \dots
$$

**Research hypothesis (H₁):**
At least one population mean differs.

:: right ::

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Unlike a *t*-test, ANOVA does not tell us *which* means differ — only that **not all of them are the same**.

We are *always* testing if the between-group variance is larger than the within-group variance. Because of this, *F* tests are *always* **one-tailed.**
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why Use ANOVA Instead of Multiple *t* Tests?

:: content ::
- Keeps the **Type I error rate** at 5%.
- Tests all group differences **in one analysis**.
- Provides the foundation for **multi-factor and repeated-measures** designs.
  - We will talk about repeated-measures designs soon.

<p v-click>

ANOVA is the statistically correct, efficient way to ask:
<br>

==“Are these group means different enough that it's unlikely to be chance?”==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Assumptions of One-Way ANOVA

:: content ::
Every ANOVA relies on three key assumptions, which represent the ideal conditions for valid results:

1. **Random selection** of participants
2. **Normality** — each group's population is roughly normal
3. **Homogeneity of variance** — groups have similar spread
  - ==Homoscedastic== populations are those that have the same variance.
  - ==Heteroscedastic== populations are those that have different variances.

<p v-click>

When these hold, *F* is robust and trustworthy.
If they're violated, be cautious in interpreting results, or may need to use non-parametric alternatives.
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Example: One-Way ANOVA (Source Table)

:: content ::
Imagine we conduct a one-way ANOVA comparing driving performance across four driving conditions: 1. No phone, 2. Passenger, 3. Cell phone, and 4. Video call.

In total, we have 40 participants divided among the four groups (n = 10 per group).

The between-groups and within-groups sums of squares are:
| Source          | SS      | df  | MS       | F      |
|-----------------|---------|-----|----------|--------|
| Between Groups  | 450.0   |    |    |    |
| Within Groups   | 100.0  |  |     |        |
| **Total**       | 550.0  |  |          |        |

<p v-click>

**What should go in the DF column?**

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Example: One-Way ANOVA (Source Table)

:: content ::

The between-groups and within-groups sums of squares are:
| Source          | SS      | df  | MS       | F      |
|-----------------|---------|-----|----------|--------|
| Between Groups  | 450.0   | K-1 = 3   |    |    |
| Within Groups   | 100.0  | N-K = 36 |     |        |
| **Total**       | 550.0  | 39 |          |        |

<p v-click>

**What should go in the MS column?**
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Example: One-Way ANOVA (Source Table)

:: content ::

The between-groups and within-groups sums of squares are:
| Source          | SS      | df  | MS       | F      |
|-----------------|---------|-----|----------|--------|
| Between Groups  | 450.0   | K-1 = 3   | SS/df = 150.0   |    |
| Within Groups   | 100.0  | N-K = 36 |  SS/df = 2.78   |        |
| **Total**       | 550.0  | 39 |          |        |

<p v-click>

**What should go in the F column?**
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Example: One-Way ANOVA (Source Table)

:: content ::

The between-groups and within-groups sums of squares are:
| Source          | SS      | df  | MS       | F      |
|-----------------|---------|-----|----------|--------|
| Between Groups  | 450.0   | K-1 = 3   | SS/df = 150.0   | MS_Between / MS_Within = 54.0  |
| Within Groups   | 100.0  | N-K = 36 |  SS/df = 2.78   |        |
| **Total**       | 550.0  | 39 |          |        |

<p v-click>

**Final ANOVA result: *F*(3, 36) = 54.0**

*We need to look up the critical F value for (3, 36) df to determine significance, or use software to get the exact p-value.*

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Beyond Significance: Measuring Effect Size

:: content ::
A significant *F* tells us that not all group means are equal —
but **how big** is that difference in practical terms?

<p v-click>

That's where **effect size** comes in.
For ANOVA, we most often report **η² (eta squared)** or **R²**. (In a one-way ANOVA, they are equivalent.)

$$
\eta^2 = \frac{SS_\text{Between}}{SS_\text{Total}}
$$

It represents the **proportion of total variance** in the dependent variable that is explained by the independent variable.
</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Understanding η² and R² Conceptually

:: left ::
- Think of *η²* like a “percentage of variance explained.”
- *η² = .20* means 20 % of the variability in your data is accounted for by your experimental manipulation (group membership).
- Larger *η²* → stronger effect.

:: right ::
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
🧠  Quick interpretation guide (Cohen, 1988):
• Small ≈ .01 • Medium ≈ .06 • Large ≈ .14

These cutoffs are rough — context matters.
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Reporting Effect Size

:: content ::
Imagine we find:
> *F*(2, 36) = 5.47, *p* = .008, *η²* = .23

That means **23 %** of the variance in scores is explained by our independent variable.

<p v-click>

Including effect sizes helps readers judge:
- whether the difference is **meaningful**, not just statistically significant,
- and whether findings might replicate with new samples.
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# When *F* Is Significant: What's Next?

:: content ::
- A significant ANOVA tells us that **at least one group differs**, but not *which* ones.

<p v-click>

- To find out *which* groups differ, we use **follow-up tests** called *post-hoc comparisons*.
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why Not Just Run More *t*-Tests?

:: content ::
Because each extra *t*-test increases the risk of **Type I error** (false positives).

<p v-click>

Post-hoc procedures control that risk by adjusting the critical value or significance threshold.
When we run "post-hoc tests," we are essentially running *t* tests with built-in corrections for multiple comparisons.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Planned vs. Post-Hoc Comparisons

:: left ::
**Planned (a priori)**
- Decided *before* data collection
- Test specific hypotheses
- Fewer tests → no need for strong correction

**Post-hoc**
- Done *after* seeing results
- Explore where the differences lie
- Need corrections to keep α = .05 overall

:: right ::
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Think of post-hoc tests as “honest ways to peek under the hood” after finding a significant overall *F*.

In general, with post-hoc tests, we adjust the size of the effect needed to declare significance to control for multiple comparisons.
</SpeechBubble>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Common Post-Hoc Test Corrections

:: content ::

| Test | Key Idea | Conservative? | Typical Use |
|------|-----------|---------------|--------------|
| **Scheffé** | Controls α for all possible contrasts | Most conservative | Exploratory analyses |
| **Tukey HSD** | Tests all pairwise mean comparisons equally | Moderate | Balanced designs |
| **Bonferroni** | Divides α by number of comparisons | Flexible | Small number of tests |

<p v-click>

All aim to protect against **false positives** while allowing fair comparisons among multiple groups.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Conceptual Takeaway

:: content ::
- **Scheffé:** “Play it safe” — harder to reach significance
- **Tukey HSD:** “Middle ground” — good balance of safety and power
- **Bonferroni:** “Divide and conquer” — simple, but can be overly strict when many tests


<p v-click>

Different journals or software packages may default to different methods —  always report which you used.
</p>

<p v-click>

**Bonferroni example:** You run an ANOVA with 4 groups (6 pairwise comparisons) and find a significant effect. You now want to know *which* groups differ. To keep overall α = .05, each *t* test must meet *p* < .0083 (.05/6) to be significant.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting One-Way ANOVA Results in APA format

:: content ::
When reporting ANOVA results, include:
- The type of ANOVA (e.g., one-way between-groups)
- The *F* statistic with degrees of freedom
- The *p* value
- Effect size (e.g., *η²* or *R²*)
- Results of post-hoc tests if applicable

<p v-click>

==Example write-up:==
A one-way between-groups ANOVA was conducted to compare the effect of phone use on driving performance. There was a significant effect of phone use condition on driving performance, *F*(3, 36) = 54.0, *p* < .001, *η²* = .82. Post-hoc comparisons using the Tukey HSD test indicated that the video call condition resulted in significantly worse driving performance compared to the no phone condition (*p* = .023) and the passenger condition (*p* < .001). No other comparisons were significant (*p*s > .05).

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One-Way ANOVA in R

:: content ::

To perform a one-way ANOVA in R, you can use the `aov()` function. Here's a basic example:

```r
# Example data
data <- data.frame(
  performance = c(85, 90, 78, 88, 92, 80, 75, 95, 89, 84,
                  70, 65, 72, 68, 74, 66, 69, 71, 73, 67),
  condition = factor(rep(c("No Phone", "Passenger", "Cell Phone", "Video Call"), each = 5))
)
# Perform one-way ANOVA
anova_result <- aov(performance ~ condition, data = data)

# View summary
summary(anova_result)

```


---
layout: cover
color: indigo-light
---

# That's all for today!
Thursday: Repeated-Measures ANOVA & Two-Way ANOVA
