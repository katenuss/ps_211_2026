---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 18
exportFilename: ps211_fall2026_lecture18
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 18: Regression

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::

- Welcome back from Thanksgiving break!
- ==Data Write-Up #2== (ANOVA-based) is due **next Tuesday, December 8** at 11:59 p.m.
- ==Exam 4== (the last exam) is **Thursday, December 10**, in class. **There will be no make-ups.**
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Coming up:
  - Wednesday (12/2): Discussion 12, Data Write-Up #2 work session. Come with questions!
  - Thursday (12/3): Lecture 19 (research ethics & chi-square)
  - Tuesday (12/8): Exam 4 Review
  - Wednesday (12/9): Discussion 13 (course wrap-up & Exam 4 practice)
  - Thursday (12/10, last day of classes): **Exam 4**, covering Lectures 15–19

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Last time: key terms

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Correlation** — an association between two numeric variables, usually observational. Not evidence of causation.

</div>
<div>

**Pearson's *r*** — −1 to +1. Sign = direction; size = strength (small .10, medium .30, large .50). Linear relationships only.

</div>
<div>

**Significance of *r*** — H₀: ρ = 0; *t* with df = N − 2. `cor.test()`; report *r*(df), *p*, 95% CI.

</div>
<div>

***r*²** — the proportion of variance two variables share. **Outliers** can create or hide a correlation: plot first.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Correlation tells us that two variables move together. Today: by how much, and how to use one to predict the other.</SpeechBubble>
</div>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Warm-up: check your understanding

:: left ::

219 students at a Midwestern college: high school GPA and first-year college GPA.

```text
t = 7.3587, df = 217, p-value = 3.783e-12
95 percent confidence interval:
 0.3341081 0.5470507
sample estimates:
      cor 
0.4468873 
```

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Which statement is correct?

- **A)** Students with higher high school GPAs tended to have higher college GPAs, *r*(217) = .45, *p* < .001.
- **B)** High school grades cause college grades.
- **C)** 45% of the variance in college GPA is explained by high school GPA.
- **D)** df should be 218.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** (B) is causal language for observational data. \(C): that would be *r*², .45² = .20, or 20%. (D): df = N − 2 = 217.

</Admonition>

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

A study finds *r* = .05 between two variables, *p* = .02, with N = 2,000. What is the best description?

- **A)** A strong relationship, since it is significant
- **B)** No relationship, since *r* is near 0
- **C)** A real but tiny relationship: *r*² = .0025, so the variables share less than 1% of their variance
- **D)** A calculation error: a tiny *r* can't be significant

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** With N = 2,000, even a trivial *r* can be distinguished from 0. Significance and size are different questions.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

Part 1
# What is Regression?

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# From describing to predicting

:: content ::

- **Correlation** asks: "Are X and Y related, and how strongly?"
- **Regression** asks: "**How much** does Y change when X changes?" and so lets us use X to **predict** Y.

<p v-click>

Imagine monthly ice cream sales and shark attacks are correlated (*r* = .7). Regression would let us say: in a month with $5,000 of ice cream sales, expect about this many shark attacks.

</p>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="30rem" v-click>Ice cream doesn't *cause* shark attacks: both rise in the summer! Regression lets us predict one from the other, but prediction is not causation.</SpeechBubble>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Predictors and outcomes

:: left ::

Regression uses new names for its variables:

- **Predictor variable (X):** the variable we use to make the prediction
- **Outcome variable (Y):** the variable we want to predict

<p v-click>

"Independent" and "dependent" variable suggest an **experiment** in which the IV was manipulated. Regression is often run on **observational** data where nothing was manipulated, so **predictor** and **outcome** avoid implying a cause.

</p>

:: right ::

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

Regression tells us how Y is expected to differ **when X differs**, not **why**. Predictors aren't manipulated, confounds still exist, and observational data is not experimental data.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="excited" color="#FDA7DC" /></div>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Regression in psychology & neuroscience

:: left ::

Regression is behind recommendation algorithms, dating apps, economic and public-health forecasts, and risk-assessment tools. In ==psychology==, it shows how variables **predict** behavior:

<img src="/images/lecture17/regression_example1.jpg" class="w-1/2 rounded-lg mx-auto"/>
<small>*Age predicts whether people choose more uncertain options (Nussenbaum et al., 2023).*</small>

:: right ::

In ==neuroscience==, it shows how variables predict brain activity, and how brain activity predicts behavior:

<img src="/images/lecture17/regression_example2.jpg" class="w-1/2 rounded-lg mx-auto"/>
<small>*Age predicts how the prefrontal cortex responds to high- vs. low-value information during memory encoding (Nussenbaum & Hartley, 2021).*</small>

---
layout: section
color: indigo-light
align: lt
---

Part 2
# Simple Linear Regression

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Our example: predicting college GPA

:: left ::

<img src="/images/lecture18/gpa_line.png" alt="First-year college GPA against high school GPA for 219 students, with the regression line" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Data: 219 first-year students at a Midwestern college (1996); R package <code>Stat2Data</code> (<code>FirstYearGPA</code>).</div>

:: right ::

**Simple linear regression** predicts an outcome (Y) from **one** predictor (X) using the **line of best fit**.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Using the line, about what college GPA would you predict for a student with a 3.5 in high school?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

About 3.1. Find 3.5 on the x-axis, go up to the line, read across. The line is our **best guess** of the average college GPA for students with that high school GPA.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The regression equation

:: left ::

$$\hat{Y} = bX + a$$

- **Ŷ** ("Y-hat"): the **predicted** value of Y
- **b**, the **slope**: ==how much Ŷ changes when X goes up by 1 unit==
  - b > 0: higher X predicts higher Y; b < 0: lower Y; b = 0: X doesn't predict Y
- **a**, the **intercept**: ==the predicted Y when X = 0==

:: right ::

<div v-click>

For our data:

$$\widehat{\text{College GPA}} = 0.555 \times \text{HS GPA} + 1.18$$

</div>

<p v-click>

- A student with a 3.0 in high school: 0.555 × 3.0 + 1.18 ≈ **2.84**
- A student with a 4.0: 0.555 × 4.0 + 1.18 ≈ **3.40**

</p>

<p v-click><StickyNote color="amber-light" title="What you need" width="100%">Interpret b and a in words, and plug one value into an equation. R finds the numbers.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: slope and intercept

:: left ::

$$\widehat{\text{College GPA}} = 0.555 \times \text{HS GPA} + 1.18$$

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

What does the slope (0.555) mean?

- **A)** College GPA is 55.5% of high school GPA.
- **B)** Students whose high school GPA is 1 point higher are predicted to have a college GPA about 0.56 points higher.
- **C)** Raising your high school GPA by 1 point will raise your college GPA by 0.56.
- **D)** The correlation is .555.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** \(C) is causal. (D): the slope and *r* are different numbers (*r* = .45 here).

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

What does the intercept (1.18) mean here?

- **A)** The average college GPA
- **B)** The lowest possible college GPA
- **C)** The college GPA of students who didn't attend high school
- **D)** The predicted college GPA for a high school GPA of 0, which is far outside the data (the lowest was 2.34), so it isn't meaningful on its own

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** The intercept is needed to place the line, but X = 0 is often impossible or outside the data. Interpret it cautiously.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Where the name "regression" comes from

:: left ::

In the 1880s, Francis Galton measured the heights of **934 adult children** and their parents (panel F last week, *r* = .32).

- The slope predicting a child's height from the parents' average height was only **0.64**.
- Parents 3 inches taller than average had children predicted to be only about **2 inches** taller than average. Very short parents had children closer to average, too.

Galton called this "regression toward mediocrity." We call it **regression to the mean**.

:: right ::

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

Whenever two variables are imperfectly correlated, extreme scores on one are paired, on average, with less extreme scores on the other. It's statistics, not biology.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="blissful" color="#FDA7DC" /></div>
</div>

<p v-click><StickyNote color="amber-light" title="Why researchers care" width="100%">Pick people for a study <i>because</i> they scored extremely (the most anxious, the worst readers), and their next scores will tend to be less extreme even with no treatment at all. A control group protects you.</StickyNote></p>

<div class="text-xs text-gray-500 mt-2">Galton (1886), <i>Journal of the Anthropological Institute</i>; R package <code>HistData</code> (<code>GaltonFamilies</code>).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Finding the best line: least squares

:: left ::

<img src="/images/lecture18/residuals.png" alt="Each student's distance from the regression line, drawn as vertical segments" class="w-full mx-auto"/>

:: right ::

Each vertical segment is a **residual** (prediction error): actual Y minus predicted Y.

**Ordinary least squares (OLS)** chooses the line that makes the **sum of squared errors** as small as possible:

$$\text{SSE} = \sum (Y - \hat{Y})^2$$

<p v-click>

Why square the errors?
- Positive and negative errors can't cancel out
- Large errors are penalized more than small ones
- There is always exactly one best line

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: least squares

:: left ::

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

Which describes, in words, the regression line that OLS finds?

- **A)** The line that makes the sum of squared differences between actual and predicted Y as small as possible
- **B)** The line through the two most extreme points
- **C)** The line with an equal number of points above and below it
- **D)** The line with the largest slope

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** "Least squares" means the smallest SSE. (B) ignores every other point. \(C) describes a median-type line, not OLS.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# How far off are the predictions?

:: left ::

Predictions are never perfect: people differ for reasons the predictor doesn't capture, and measurement is noisy.

The **standard error of the estimate** is roughly the typical distance of the points from the line:

$$SE_\text{estimate} = \sqrt{\frac{SSE}{N - 2}}$$

N − 2 because the line uses up two df: one for the slope, one for the intercept (the reason for last week's df = N − 2).

<p v-click>

For our GPA data, *SE*<sub>estimate</sub> = **0.42**: a typical prediction is off by about four-tenths of a GPA point.

</p>

:: right ::

<img src="/images/lecture17/regression_standard_error.png" class="w-full rounded-lg mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

In which panel would predictions from the line be more accurate?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The left: points hug the line, so the standard error of the estimate is small. (The slopes are similar; only the scatter differs.)

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# How much better than guessing the mean?

:: content ::

<img src="/images/lecture18/pre.png" alt="Left: errors when predicting everyone gets the mean GPA, SSE 47.2. Right: errors from the regression line, SSE 37.8" class="w-3/4 mx-auto"/>

Without a predictor, the best guess for everyone is the **mean**. The **proportionate reduction in error (PRE)** says how much the line improves on that:

$$PRE = \frac{SSE_\text{mean} - SSE_\text{regression}}{SSE_\text{mean}} = \frac{47.2 - 37.8}{47.2} = .20 = R^2$$

<p v-click>

**R²**, the coefficient of determination: knowing high school GPA cuts prediction error by **20%**. (Check: *r* = .45, and .45² = .20.)

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# R² is an effect size, just like η²

:: left ::

<div class="text-[15px] leading-snug">

Regression:
$$R^2 = \frac{SSE_\text{mean} - SSE_\text{regression}}{SSE_\text{mean}}$$

ANOVA:
$$\eta^2 = \frac{SS_\text{Between}}{SS_\text{Total}}$$

Both: **variance explained by the model ÷ total variance in the outcome**.

</div>

:: right ::

- **R² = 0**: the predictor doesn't improve on the mean
- **R² = 1**: perfect prediction
- **R² = .20**: 20% of the variance explained

<p v-click><StickyNote color="amber-light" title="One idea, many names" width="100%">η² for groups, R² for a numeric predictor, <i>d</i> for two means. Each says how big, not how unlikely.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Is the prediction better than chance?

:: left ::

R² describes our sample. Is it bigger than 0 in the **population**, or could it be chance?

- An ***F* test** for the whole model: does it explain a significant amount of variance? (Same logic as ANOVA.)
- A ***t* test** for each slope: H₀: the population slope is 0.

With one predictor, these ask the same question, and give the same *p* as the correlation test (*t* = 7.36 in both).

:: right ::

<p v-click><StickyNote color="amber-light" title="Size vs. significance, again" width="100%">With a large enough sample, even a small R² can be significant. Report R² (how much is explained) along with the <i>p</i> value.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Simple regression in R: `lm()`

:: left ::

```r
gpa_model <- lm(college_gpa ~ hs_gpa, data = gpa_data)
summary(gpa_model)
```

```text
Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  1.17985    0.26194   4.504 1.09e-05 ***
hs_gpa       0.55501    0.07542   7.359 3.78e-12 ***
---
Residual standard error: 0.4174 on 217 degrees of freedom
Multiple R-squared:  0.1997,	Adjusted R-squared:  0.196 
F-statistic: 54.15 on 1 and 217 DF,  p-value: 3.783e-12
```

`lm` stands for **linear model**. The formula reads "college GPA as predicted by high school GPA," the same `~` as in `aov()`.

:: right ::

<div class="text-[15px] leading-snug">

- **`(Intercept)` Estimate:** a = 1.18
- **`hs_gpa` Estimate:** the slope, b = 0.555, with its *t* test
- **Residual standard error:** the standard error of the estimate, 0.42, df = N − 2
- **Multiple R-squared:** R² = .20
- **F-statistic:** the test of the whole model

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Speed dating: predicting who gets a "yes"

:: left ::

<img src="/images/lecture18/speeddate_yes_attr.png" alt="Percent of dates who wanted to see each person again against that person's average attractiveness rating, with the regression line and its equation" class="w-full mx-auto"/>

```r
yes_model <- lm(pct_yes ~ attractiveness, data = daters)
summary(yes_model)
```

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

Predict the % of dates who say yes to someone whose dates rated them a 7, on average. What do the slope and R² mean?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

−67.5 + 17.6 × 7 ≈ **56%**. Each extra point of rated attractiveness predicts about 18 percentage points more yeses. R² = .60: rated attractiveness explains 60% of the variance in how many yeses people got.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="The intercept" width="100%">−67.5% at a rating of 0. No one was rated below 3.2, so the intercept has no sensible meaning here.</StickyNote></p>

<div class="text-xs text-gray-500 mt-2">One dot per person (N = 102, 5–20 dates each). Fisman et al. (2006), <i>QJE</i>; R package <code>sdamr</code> (<code>speeddate</code>).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: reading `lm()` output

:: left ::

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

In the output, what does `Pr(>|t|) = 3.78e-12` in the `hs_gpa` row test?

- **A)** Whether the intercept is 0
- **B)** Whether college GPA is normally distributed
- **C)** Whether the model predicts perfectly
- **D)** Whether the population slope for high school GPA is 0; it almost certainly isn't

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** Each row's *t* test asks whether that coefficient is 0 in the population. (A) is the `(Intercept)` row.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

What does `Multiple R-squared: 0.1997` tell you?

- **A)** High school GPA causes 20% of college GPA.
- **B)** Predictions using high school GPA have 20% less squared error than just guessing the mean college GPA.
- **C)** Predictions are right 20% of the time.
- **D)** 20% of students were predicted correctly.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** That is the PRE definition of R². (A) is causal; \(C) and (D) treat it as an accuracy rate.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

Part 3
# Multiple Regression

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# More than one predictor

:: left ::

**Multiple regression** predicts an outcome from **2+ predictors**:

$$\hat{Y} = b_1X_1 + b_2X_2 + \dots + a$$

==Each slope is the relationship between that predictor and Y, **holding all the other predictors constant**.==

That is what makes it different from a set of separate correlations.

:: right ::

**Why use more than one predictor?**
- Better predictions (higher R²)
- Ask whether a predictor matters **over and above** the others, the same idea as a partial correlation
- Statistically control for possible confounds

<p v-click><StickyNote color="amber-light" title="Still not an experiment" width="100%">Controlling for the confounds you measured doesn't rule out the ones you didn't. Only random assignment does that.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Multiple regression in R

:: left ::

Add verbal SAT score and the number of humanities credits taken in high school:

```r
gpa_model2 <- lm(college_gpa ~ hs_gpa + sat_verbal + hum_credits,
                 data = gpa_data)
summary(gpa_model2)
```

```text
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 0.5963144  0.2839042   2.100 0.036859 *  
hs_gpa      0.4664270  0.0724238   6.440 7.68e-10 ***
sat_verbal  0.0011192  0.0003249   3.445 0.000687 ***
hum_credits 0.0161896  0.0036911   4.386 1.81e-05 ***
---
Multiple R-squared:  0.3079,	Adjusted R-squared:  0.2983 
F-statistic: 31.89 on 3 and 215 DF,  p-value: < 2.2e-16
```

:: right ::

<div class="text-[15px] leading-snug">

- All three predict college GPA **over and above** the other two (every *p* < .001).
- Holding SAT and humanities credits constant, each extra point of high school GPA predicts **0.47** more points of college GPA.
- R² rose from .20 to **.31**.

</div>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

The `sat_verbal` slope is 0.0011. Does SAT barely matter?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Not necessarily: it's per **one SAT point**, on a scale with an SD of 83. 100 more SAT points predicts about 0.11 more GPA points. Slopes depend on units.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Unstandardized vs. standardized slopes

:: left ::

**Unstandardized slopes (b)** are in the variables' **original units** ("0.47 GPA points per high school GPA point"). Easy to use for predictions; hard to compare across predictors measured on different scales.

**Standardized slopes (β, "beta")** come from z-scoring every variable first, so they're in **SD units**: "a 1-SD increase in X predicts a β-SD change in Y." Easy to compare; less concrete.

:: right ::

<table class="compact-table text-base">
<thead><tr><th>Predictor</th><th>b</th><th>β</th></tr></thead>
<tbody>
<tr><td>High school GPA (0–4)</td><td>0.466</td><td><b>0.38</b></td></tr>
<tr><td>Humanities credits (0–40)</td><td>0.016</td><td><b>0.25</b></td></tr>
<tr><td>Verbal SAT (200–800)</td><td>0.001</td><td><b>0.20</b></td></tr>
</tbody>
</table>

<p v-click>

On the b's alone, SAT looks hundreds of times weaker than high school GPA. In SD units, it's about half as strong.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: which predictor?

:: left ::

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

Using the table on the previous slide, which predictor has the strongest relationship with college GPA, holding the others constant?

- **A)** Verbal SAT, because its scale has the largest numbers
- **B)** Humanities credits, because its *t* value is in the middle
- **C)** High school GPA: it has the largest standardized slope (β = .38)
- **D)** Can't tell: the b's are in different units, so there's no way to compare

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Standardized slopes put the predictors on the same scale. (A) confuses the size of the units with the strength of the relationship. (D) is right about the b's, which is exactly why we standardize.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Overlapping predictors

:: left ::

The verbal SAT slope, with and without high school GPA in the model:

<table class="compact-table text-base">
<thead><tr><th>Model</th><th>SAT slope (b)</th><th><i>p</i></th></tr></thead>
<tbody>
<tr><td>SAT alone</td><td>0.0017</td><td>&lt; .001</td></tr>
<tr><td>SAT + high school GPA</td><td>0.0012</td><td>&lt; .001</td></tr>
</tbody>
</table>

<Admonition title="Multiple choice 9" color="teal-light" width="100%">

Why did the SAT slope shrink when high school GPA was added?

- **A)** SAT and high school GPA overlap (*r* = .21): part of what SAT "explained" alone is also explained by high school GPA.
- **B)** SAT stopped predicting college GPA.
- **C)** High school GPA causes SAT scores.
- **D)** Adding predictors always makes slopes smaller.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Holding high school GPA constant removes the shared part. SAT still predicts college GPA over and above high school GPA (*p* < .001), so (B) is wrong. (D): if predictors don't overlap, slopes barely change.

</Admonition>

<p v-click><StickyNote color="amber-light" title="When a slope disappears" width="100%">If a predictor's slope becomes non-significant once another is added, the two explain mostly the <b>same</b> variance. It doesn't mean the first predictor is unrelated to Y.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interactions in regression

:: content ::

An **interaction** occurs when the effect of one predictor **depends on** the level of another: ==the relationship between X₁ and Y changes depending on X₂==. The same idea as in two-way ANOVA.

<p v-click>

**Example:** the relationship between stress and depression may depend on social support. Stress may predict depression strongly for people with little support and weakly for people with a lot (support "buffers" stress).

</p>

<p v-click>

To test it, add an **interaction term**, the product of the two predictors:

$$\hat{Y} = b_1X_1 + b_2X_2 + b_3(X_1 \times X_2) + a$$

If b₃ is significant, the slope for X₁ differs depending on X₂. In R: `lm(depression ~ stress * support)`, the same `*` as in `aov()`.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Regression: practice questions

:: left ::

<Admonition title="Multiple choice 10" color="teal-light" width="100%">

Hours studied (X) predicts final exam score (Y): b = 4.2, *p* < .01. What does this mean?

- **A)** Students who study score exactly 4.2 points higher than students who don't.
- **B)** For each extra hour studied, predicted exam scores are 4.2 points higher on average.
- **C)** Each extra hour raises scores by 4.2%.
- **D)** Students who study more tend to do worse.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** The slope is the change in predicted Y per one-unit change in X.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 11" color="teal-light" width="100%">

Years of experience predicts job performance with R² = .32. Which interpretation is most accurate?

- **A)** Experience causes 32% better performance.
- **B)** 32% of employees are high performers.
- **C)** Performance can be predicted with 32% accuracy.
- **D)** Experience explains 32% of the variance in performance.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** R² is the proportion of variance explained.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Regression: one more practice question

:: left ::

<Admonition title="Multiple choice 12" color="teal-light" width="100%">

Daily exercise duration predicts happiness: b = 1.4, *p* = .28. Which conclusion is correct?

- **A)** Exercise has no effect on happiness.
- **B)** Exercise decreases happiness.
- **C)** We failed to find evidence that exercise duration predicts happiness.
- **D)** The effect size is zero.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** A non-significant slope is a failure to reject H₀, not proof that the slope is 0 (A, D). The estimate is even positive; it's just not distinguishable from 0 in this sample.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which test? The whole map

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Predictor / IV</th><th>Outcome / DV</th><th>Design</th><th>Test</th><th>Effect size</th><th>R</th></tr></thead>
<tbody>
<tr><td>Categorical, 2 levels</td><td>Numeric</td><td>Separate groups / same people</td><td>Independent / paired <i>t</i></td><td><i>d</i></td><td><code>t.test()</code></td></tr>
<tr><td>Categorical, 3+ levels</td><td>Numeric</td><td>Separate groups</td><td>One-way ANOVA</td><td>η²</td><td><code>aov(dv ~ group)</code></td></tr>
<tr><td>Categorical, 3+ levels</td><td>Numeric</td><td>Same people</td><td>Repeated-measures ANOVA</td><td>partial η²</td><td><code>aov(... + Error(...))</code></td></tr>
<tr><td>Two categorical IVs</td><td>Numeric</td><td>Factorial</td><td>Two-way ANOVA</td><td>η²</td><td><code>aov(dv ~ a * b)</code></td></tr>
<tr><td>Numeric</td><td>Numeric</td><td>Describe the association</td><td>Correlation</td><td><i>r</i>, <i>r</i>²</td><td><code>cor.test()</code></td></tr>
<tr><td>Numeric (one or more)</td><td>Numeric</td><td>Predict</td><td>Regression</td><td>R², β</td><td><code>lm()</code></td></tr>
<tr class="text-gray-400"><td>Categorical</td><td>Categorical</td><td>Counts</td><td>Chi-square (Thursday)</td><td></td><td></td></tr>
</tbody>
</table>

<p v-click>

<div class="flex items-center gap-4 mt-3">
<IceCream :size="70" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem">Every row is signal ÷ noise, an effect size, and a decision. Thursday: what happens when researchers bend those decisions, and what to do when the outcome isn't a number at all.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Key terms from today

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Simple linear regression** — predicts an outcome (Y) from one predictor (X): Ŷ = bX + a. Predictor and outcome, not IV and DV; not causal.

</div>
<div>

**Slope (b) and intercept (a)** — b: change in predicted Y per 1-unit increase in X. a: predicted Y when X = 0 (often not meaningful).

</div>
<div>

**Least squares (OLS)** — the line that minimizes the sum of squared residuals (SSE). **Standard error of the estimate**: typical size of a prediction error.

</div>
<div>

**R² / proportionate reduction in error** — how much the line reduces error compared with predicting the mean; the proportion of variance explained.

</div>
<div>

**Multiple regression** — 2+ predictors; each slope holds the others constant. Overlapping predictors share variance.

</div>
<div>

**Standardized slope (β)** — slope in SD units, for comparing predictors. **Regression to the mean**: extreme scores tend to be followed by less extreme ones.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Tomorrow: Discussion 12 (Data Write-Up #2 work session). Thursday: research ethics & chi-square.
