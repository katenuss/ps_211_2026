---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Exam 4 Review Session
exportFilename: ps211_fall2026_exam4_review
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Exam 4 Review Session (Lectures 15-19)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::
- Today is our last regular class session before Exam 4!
- Reminder: ==Data Write-Up #2== is due **TONIGHT (Tuesday, December 8) at 11:59 p.m.!**
- ==Exam 4== is on **Thursday, Dec. 10** during class — covers Lectures 15-19.
  - Thursday, Dec. 10 is also the **last day of classes** for the semester.
  - **NO MAKE-UPS**
- Discussion 13 (Wed. 12/9): course wrap-up & Exam 4 practice.
- ==Course evaluations== are open — we'll leave time today to complete them, so bring your computer.
- We will shortly post:
  - Discussion section grades
  - Data Write-Up #2 grades (after tonight's deadline)

- We will post Exam 4 grades and course grades on Thursday afternoon *if* everyone takes the exam on time.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: ANOVA

:: content ::
- Remember, *t* tests compare **two means**.  
- ANOVA allows us to compare **three or more means** while controlling the **Type I error rate**.

<p v-click>


- A significant ANOVA tells us:
  - At least **one group mean differs** from the others  
  - But NOT **which** groups differ  

</p>

<p v-click>

- To find out *which* means differ, we run **post-hoc tests** (e.g., Tukey’s HSD, Bonferroni).

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: One-Way ANOVA

:: content ::

- ANOVA partitions variability into:
  - **Between-groups variability** (signal)
  - **Within-groups variability** (noise)

<p v-click>

<img src="/images/lecture13/anova_var_demo.png"  class="w-1/2 mx-auto"/>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: One-Way ANOVA: The F Statistic

:: content ::
**F statistic**:

$$F = \frac{MS_{\text{Between}}}{MS_{\text{Within}}}$$

Where:

- $SS_{\text{Between}} = \sum_i n_i (M_i - M_G)^2$
- $MS_{\text{Between}} = SS_{\text{Between}} / df_{\text{Between}}$
- $MS_{\text{Within}} = SS_{\text{Within}} / df_{\text{Within}}$


<p v-click>

==*If F is large:*==
  - Between-group variance is large relative to within-group variance.
  - This is evidence that groups differ.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Visualizing ANOVA

:: left ::
- Think of ANOVA as comparing:
  - **How far apart the group means are**  
  - ==relative to== **how spread out scores are within each group**  
- If group means differ *a lot* compared to within-group variability → **big F**.
- If group means overlap heavily → **small F**.

:: right ::

<p v-click>

<img src="/images/lecture13/anova_mean_demo.png"  class="w-4/5 mx-auto"/>

</p>


<p v-click>

<img src="/images/lecture13/anova_var_demo.png"  class="w-4/5 mx-auto"/>

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: One-Way ANOVA

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

If your between-group variability increases while within-group variability stays constant, what happens?

- A. F increases
- B. F decreases
- C. F stays the same
- D. We cannot determine this without knowing our degrees of freedom.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A. Increasing “signal” increases F.

</Admonition>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
We don't know how much F increases without knowing the exact values, but we can say it will increase.
</SpeechBubble></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Interpreting F

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Suppose *F*(2, 45) = 0.89, *p* = .42. What’s the correct conclusion?

- A. At least one mean is different from the other two.
- B. We did not find significant differences between means.
- C. Post-hoc tests will reveal differences between groups.
- D. The critical value was miscalculated; F cannot be less than 1.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

B. Because *p* = .42, we fail to reject the null hypothesis, meaning we did not find significant differences between group means.

</Admonition>

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Even though *F* tests are always one-tailed, *F* **can** be less than 1 when within-group variability exceeds between-group variability.
</SpeechBubble>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Post-Hoc Tests (Tukey & Bonferroni)

:: content ::

==**Key rule:**== 
When the **overall ANOVA is significant**, we can run post-hoc tests to determine which means differ.

Post-hoc tests control for **Type I error** across multiple comparisons.

<p v-click>

#### Tukey’s HSD
- Designed for comparing **all possible pairs** of means.
- Controls overall Type I error.
- Balances power and error control ("safety").

#### Bonferroni correction
- Adjusts α by:  $\alpha_{\text{new}} = \alpha / \text{number of tests}$
- Very conservative → protects Type I error at cost of power.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: When to Use Post-Hocs

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

When are post-hoc tests appropriate?

- A. Whenever there are ≥ 3 groups being compared.
- B. After a significant ANOVA.
- C. Only when within-group variances differ.
- D. When means “look different."

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

B. Post-hoc tests should only be run after a significant overall ANOVA.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Effect Size for ANOVA: η²

:: content ::
Eta-squared:

$$ \eta^2 = \frac{SS_{\text{Between}}}{SS_{\text{Total}}} $$

Interpretation:
- .01 = small  
- .06 = medium  
- .14 = large  

Represents the **proportion of variance explained** by the IV.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: F and Effect Size

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

Which scenario gives the **largest F**?

- A. Large between-group differences + small within-group variability
- B. Small between-group differences + large within-group variability
- C. Small between-group differences + small within-group variability
- D. Identical means across groups with different sample sizes

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A. Large between-group differences increase the numerator ($MS_{Between}$, the ==*signal*==), and small within-group variability decreases the denominator ($MS_{Within}$, the ==*noise*==), resulting in a larger F statistic.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Repeated-Measures ANOVA

:: content ::
Used when:
- Same participants measured across **multiple conditions** or time points.

Advantages:
- Higher power  
- Fewer participants needed  
- Controls for between-subject variability


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Repeated-Measures ANOVA

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Why does a repeated-measures ANOVA have more power than a between-subjects ANOVA?

- A. Repeated-measures ANOVA uses larger sample sizes.
- B. Repeated-measures ANOVA removes between-person variability.
- C. Repeated-measures ANOVA typically is run with a larger α.
- D. Repeated-measures ANOVA has a larger effect size by definition.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

B. Repeated-measures ANOVA removes between-person variability. The "noise" term, $MS_{Within}$, is smaller because the subject-specific variability is accounted for, leading to a larger *F* statistic.

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Factorial ANOVA (Two-Way)

:: content ::
- Factorial ANOVAs test effects of **two or more IVs** simultaneously.
- Each IV is called a **factor**.
- Factors can have **multiple levels**.

<p v-click>

A factorial ANOVA allows testing:
1. **Main effect of A**  
2. **Main effect of B**  
3. **Interaction effect**  
   - Does the effect of A depend on B?

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Visualizing Main Effects and Interactions

:: content ::

<img src="/images/lecture15/interaction_barplot.png" class="w-1/2 mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Main Effects & Interactions

:: left ::
*A researcher examines the influence of price (cheap vs. expensive) and type (red vs. white) on wine ratings. She runs a 2x2 ANOVA and finds:*

- Main effect of price: *p* = .001  
- Main effect of type: *p* = .70  
- Interaction effect: *p* = .02  

:: right ::
<Admonition title="Question" color="teal-light" width="100%">

Which of the following conclusions are correct?

- A. Participants rated cheap wines differently than expensive wines.
- B. Participants rated red and white wines differently.
- C. The effect of price on wine ratings depended on type of wine.
- D. None of the above.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A and C.
- A is correct because the main effect of price is significant (*p* = .001).
- C is correct because the interaction effect is significant (*p* = .02).

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Correlation: Key Ideas

:: content ::
Correlation assesses **linear relationship** between two continuous variables.

Pearson’s *r*:
- Range: –1 to +1  
- Sign: direction of relationship
  - Positive → as X increases, Y increases
  - Negative → as X increases, Y decreases
- Magnitude: strength of relationship
  - Larger absolute value = stronger relationship

<AdmonitionType type="warning" width="100%">
Remember, correlation does NOT imply causation!
</AdmonitionType>
---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interpreting *r*

:: content ::
Guidelines:
- .10 small  
- .30 medium  
- .50 large  

Coefficient of determination:  
$r^2$ = proportion of variance in Y explained by X.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Correlation Strength

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

A researcher finds a correlation between driving experience (years) and accident rate (number of accidents) of *r* = –0.62. Which of the following conclusions are correct?

- A. There is a strong negative relationship between driving experience and accident rate.
- B. As driving experience increases, accident rate decreases.
- C. Driving experience causes accident rates to decrease.
- D. About 38% of the variance in accident rate is explained by driving experience.
- E. About 62% of the variance in accident rate is NOT explained by driving experience.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A, B, D, and E.

</Admonition>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
E is correct because $r^2 = (-0.62)^2 = 0.3844$, so approximately 38% of the variance is explained, meaning about 62% is not explained. The fact that it is exactly .62 is coincidental.
</SpeechBubble></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Third Variables

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

Shoe size and vocabulary correlate in children, $r = .80$. However, when controlling for age, the *partial* correlation drops to $r = .10$. What does this suggest?

- A. Increases in shoe size causes children to walk earlier, which leads to faster language development and vocabulary growth.
- B. There is a direct causal relationship between shoe size and vocabulary, but it is small ($r = .10$).
- C. The original correlation between shoe size and vocabulary was largely due to the influence of a third variable, age.
- D. Age explains all of the variance in children's vocabularies.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

C. The large drop in correlation when controlling for age suggests that age was a confounding variable influencing both shoe size and vocabulary.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Regression: Key Concepts

:: content ::
- Regression analyzes the relationship between a dependent variable (the **outcome**) and one or more independent variables (the **predictors**).
- Simple linear regression involves one predictor variable.
- Simple linear regression involves finding the **line of best fit** that minimizes the sum of squared differences between observed and predicted values:


$$\hat{Y} = bX + a$$

Where:
- $b$ is the slope = expected change in Y for each unit X
- $a$ is the intercept = predicted Y when X = 0

<AdmonitionType type="warning" width="100%">
Regression enables prediction, but does not imply causation.
</AdmonitionType>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: R² Interpretation

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

If a model explains 30% of the variance in the outcome variable, what is the value of R²?

- A. R² = .03
- B. R² = .30
- C. R² = $.30^2$ = .09
- D. R² cannot be computed for a regression model.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

B. R² is the proportion of variance explained, so R² = .30.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# APA Reporting: Correlation & Regression

:: content ::

### Correlation

> There was a significant correlation between age and vocabulary, *r*(28) = .45, *p* = .01.

<br> 

### Regression
> A linear regression revealed that increases in hours studied were related to increases in quiz scores, 
> *F*(1, 28) = 9.21, *p* = .005, $R^2 = .25$.

<p v-click><Admonition title="Question" color="teal-light" width="100%">In both of these cases, how many participants were in the study?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

30 participants.

In correlation, degrees of freedom = *n* – 2
Where:
- *n* = number of participants

In regression, degrees of freedom = *n* – *k* – 1.
Where:
- n = number of participants
- k = number of predictors

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Chi-Square Tests

:: content ::
Used for **categorical variables**.

#### Goodness-of-fit  
- Compare observed vs. expected frequencies

#### Test of independence  
- Assess whether two categorical variables are related

#### Assumptions of both:
- Frequencies (not means!) should be used
- Expected counts ≥ 5 in most cells (otherwise, results may be invalid)

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Chi-Square Scenarios

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

Which scenario requires a chi-square test?

- A. Examining GPA vs. average hours slept each night.
- B. Examining students' happiness scores across three different university majors.
- C. Examining whether people who own cats vs. dogs differ in their favorite movie genres.
- D. Examining the relationship between income and education level.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

C. Both variables (pet ownership and favorite movie genre) are categorical.

</Admonition>

<p v-click><Admonition title="Question" color="teal-light" width="100%">Which chi-square test should be used?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Chi-square test of independence — we are asking whether two categorical variables are associated.

</Admonition></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# P-Hacking and Researcher Degrees of Freedom

:: content ::
### Questionable research practices (QRPs)
- **p-hacking:** 
  - Trying multiple analyses and reporting only significant results.
- **HARKing:** (hypothesizing after results known)
  - Presenting post-hoc hypotheses as if they were a priori.
- **Selective reporting:** 
  - Reporting only significant conditions, measures, or studies.
- **Optional stopping:** 
  - Collecting data until significant results are found.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# P-Hacking and Researcher Degrees of Freedom

:: content ::
<p v-click>

## Why are these harmful?
- Inflate Type I error: 
  - Increase false positives
- Undermine replicability: 
  - Results may not be consistent across studies
- Mislead literature: 
  - Create a false impression of support for a theory

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Open Science Practices

:: content ::
- Pre-registration of hypotheses & analysis plans
- Sharing materials, data, & code  
- Transparent reporting  

<p v-click>

These improve **trust**, **rigor**, and **replicability** of scientific findings.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Questionable research practices

:: content ::

<Admonition title="Question" color="teal-light" width="100%">

Testing 12 outcomes and reporting only the significant one is an example of:

- A. Open science.
- B. Exploratory data analysis.
- C. *P*-hacking and selective reporting.
- D. Data fraud.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

C. Testing multiple outcomes and reporting only significant ones is a form of *p*-hacking and selective reporting, which inflates the Type I error rate.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Open Science

:: content ::
<Admonition title="Question" color="teal-light" width="100%">

Why is pre-registration useful?

- A. It helps to prevent *p*-hacking and limits researcher degrees of freedom.
- B. It allows researchers to stop data collection once they achieve significance.
- C. It increases the likelihood of finding significant results.
- D. It eliminates the need for peer review.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A. Pre-registration helps prevent *p*-hacking by specifying hypotheses and analysis plans in advance, reducing researcher degrees of freedom.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Thank you!

:: content ::
- We made it through the semester! (Almost.)
- I hope that you learned something and didn't find this course ==too painful.==
- I really appreciate all of your engagement and effort, especially those of you who consistently participated during class.

<p v-click>

### Thank you also to:
- your TF, for all their hard work this semester!
- everyone who gave feedback that helped shape this version of the course.

</p>



---
layout: cover
color: indigo-light
---

# That’s all for the semester!  
Except: Course evaluations.