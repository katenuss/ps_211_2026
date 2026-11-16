---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 17
exportFilename: ps211_fall2026_lecture17
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 17: Correlation

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::

- ==Data Write-Up #2== (ANOVA-based) is due **Tuesday, December 8** at 11:59 p.m.
- ==Exam 4== (the last exam) is **Thursday, December 10**, in class. **There will be no make-ups.**
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- **No discussion Wed. 11/25 and no class Thurs. 11/26. Happy Thanksgiving!** 🦃
- After the break:
  - Tuesday (12/1): Lecture 18 (regression)
  - Wednesday (12/2): Discussion 12, Write-Up #2 work session
  - Thursday (12/3): Lecture 19 (research ethics & chi-square)
  - Exam 4: Thursday, December 10 (Lectures 15–19)

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

**Repeated-measures ANOVA** — 3+ conditions, same people in all of them. Removes **SS<sub>Subjects</sub>** (stable differences between people) from the noise → more power. df = (k − 1, (k − 1)(n − 1)).

</div>
<div>

**Order effects & counterbalancing** — practice, fatigue, carryover; vary the order of conditions across people.

</div>
<div>

**Two-way ANOVA** — two IVs, three *F*s: two **main effects** (from marginal means) and an **interaction** (from cell means).

</div>
<div>

**Interaction** — the effect of one IV depends on the level of the other: non-parallel lines in a plot of cell means.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Every test so far needed groups or conditions. Today, both variables are numeric: no groups at all.</SpeechBubble>
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

Students who slept 4 hours or 8 hours took a memory test with or without caffeine. Mean scores:

<table class="compact-table text-base">
<thead><tr><th></th><th>No caffeine</th><th>Caffeine</th></tr></thead>
<tbody>
<tr><td><b>4 hours</b></td><td>50</td><td>70</td></tr>
<tr><td><b>8 hours</b></td><td>70</td><td>71</td></tr>
</tbody>
</table>

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

What pattern do these (made-up) means show?

- **A)** Only a main effect of sleep
- **B)** An interaction: caffeine helps the sleep-deprived but not the rested
- **C)** No effects at all
- **D)** Only a main effect of caffeine, equal at both sleep levels

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** The caffeine effect is +20 after 4 hours of sleep and +1 after 8: it depends on sleep. Plotted, the lines would not be parallel.

</Admonition>

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

12 people each rate 4 songs, and you run a repeated-measures ANOVA. What are its dfs?

- **A)** (3, 44)
- **B)** (4, 33)
- **C)** (3, 11)
- **D)** (3, 33)

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** k − 1 = 3; (k − 1)(n − 1) = 3 × 11 = 33. (A) is the between-groups df (48 − 4), which ignores that the same people rated every song.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

When both variables are numeric...
# Correlation

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Every test so far had a categorical IV

:: content ::

<table class="compact-table text-base">
<thead><tr><th>Test</th><th>IV (predictor)</th><th>DV (outcome)</th><th>Question</th></tr></thead>
<tbody>
<tr><td><i>t</i> tests</td><td>Categorical, 2 levels</td><td>Numeric</td><td>Do two means differ?</td></tr>
<tr><td>One-way & repeated-measures ANOVA</td><td>Categorical, 3+ levels</td><td>Numeric</td><td>Do 3+ means differ?</td></tr>
<tr><td>Two-way ANOVA</td><td>Two categorical IVs</td><td>Numeric</td><td>Main effects? Interaction?</td></tr>
<tr v-click><td><b>Correlation</b></td><td><b>Numeric</b></td><td><b>Numeric</b></td><td><b>Do two variables go up and down together?</b></td></tr>
</tbody>
</table>

<p v-click>

A **correlation** is a systematic association between two numeric variables: how they **co-vary** ("co-relate"). Each participant contributes a pair of scores, one on each variable.

</p>

<p v-click><StickyNote color="amber-light" title="Don't chop it up" width="70%">You could split hours of sleep into "short," "medium," and "long" and run an ANOVA, but you would throw away information. When both variables are numeric, use them as numbers.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Correlation is not causation (again)

:: left ::

Correlations are usually computed in **observational** studies: both variables are **measured**, neither is manipulated.

**Advantages**
- Some questions **can't be studied experimentally** (it would be unethical to assign children to stressful early environments)
- An efficient way to study **naturally occurring** variables

**Disadvantages**
- **Confounding variables** can create an association
- **Direction is unknown**: does X affect Y, or Y affect X?

:: right ::

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

The statistic doesn't decide whether you can claim causation: the **design** does. A correlation from a randomized experiment can be causal; a *t* test on groups that already existed (owls vs. larks) cannot.

</SpeechBubble>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Our data: drinking and GPA

:: left ::

<img src="/images/lecture17/gpa_drinks.png" alt="Scatterplot of GPA against alcoholic drinks per week for 253 college students" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">The sleep data from Discussions 5–6 and Lecture 15: Onyper, Thacher, Gilbert, & Gradess (2012), <i>Chronobiology International</i>; Lock5Data (<code>SleepStudy</code>).</div>

:: right ::

A **scatterplot**: one dot per student, drinks per week on the x-axis, GPA on the y-axis.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Describe the relationship. Is it strong?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Students who drink more tend to have somewhat **lower** GPAs, but there is a lot of scatter: many heavy drinkers have high GPAs. A **weak negative** relationship. Pearson's *r* = **−.27**.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Pearson's *r*: direction and strength

:: left ::

The **Pearson correlation coefficient (*r*)** summarizes a linear relationship in one number from **−1 to +1**:

- **Sign = direction**
  - **Positive**: high X goes with high Y
  - **Negative**: high X goes with low Y
- **Size (ignoring the sign) = strength**
  - ±1: every point exactly on a line
  - 0: no *linear* relationship

**Assumptions:** both variables numeric; a linear relationship; random sampling; roughly normal distributions.

:: right ::

Cohen's (1988) guidelines:

<table class="compact-table text-base">
<thead><tr><th>Strength</th><th>|<i>r</i>|</th></tr></thead>
<tbody>
<tr><td>Small</td><td>.10</td></tr>
<tr><td>Medium</td><td>.30</td></tr>
<tr><td>Large</td><td>.50</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Behavior is noisy" width="100%">In psychology, correlations above .50 are rare. Drinking and GPA (−.27) is a small-to-medium relationship, and a typical one.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Examples: penguin dimensions

:: content ::

<img src="/images/lecture16/penguins.jpg" class="w-1/4 rounded-lg mx-auto"/>

<div class="flex justify-center items-start gap-4 mt-3">
  <img src="/images/lecture16/corr1.png" class="w-1/3 rounded-lg shadow-md"/>
  <img src="/images/lecture16/corr2.png" class="w-1/3 rounded-lg shadow-md"/>
  <img src="/images/lecture16/corr3.png" class="w-1/3 rounded-lg shadow-md"/>
</div>

<div class="text-xs text-gray-500 mt-2">Data: Gorman, Williams, & Fraser (2014), <i>PLOS ONE</i>; R package <code>palmerpenguins</code>.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: direction

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

Which of these would you expect to show a **negative** correlation?

- **A)** People's heights and weights
- **B)** Hours spent studying and exam scores
- **C)** Distance people live from campus and how many classes they attend
- **D)** Shoe size and GPA

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** The farther away, the fewer classes attended. (A) and (B) should be positive: taller people tend to weigh more; more studying tends to go with higher scores. (D) should be about zero: unrelated variables.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Guess the correlation

:: content ::

<img src="/images/lecture17/guess_r.png" alt="Six scatterplots of real data labeled A to F" class="w-3/4 mx-auto"/>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

Which panel shows the **strongest** correlation? &nbsp; **A)** B (penguins) &nbsp; **B)** D (high school vs. college GPA) &nbsp; **C)** F (parents' and children's heights) &nbsp; **D)** A (sleep and GPA)

</Admonition>



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Guess the correlation: the answers

:: content ::

<img src="/images/lecture17/guess_r_reveal.png" alt="The same six scatterplots with their correlations: A -0.06, B 0.87, C -0.27, D 0.45, E 0.53, F 0.32" class="w-2/3 mx-auto"/>

<div class="grid grid-cols-2 gap-6 text-[15px] leading-snug">
<div>

<Admonition title="Answer" color="green-light" width="100%">

**A.** Penguin flipper length and body mass, *r* = .87: two measurements of the same body. Behavioral correlations look more like C–F.

</Admonition>

</div>
<div v-click>

**Surprise:** in these students, sleep and GPA are nearly unrelated (*r* = −.06). Panel F is Galton's data, where the word "regression" comes from (next week).

</div>
</div>

<div class="text-xs text-gray-500">Data: A, C: Onyper et al. (2012). B: Gorman et al. (2014). D, E: <code>Stat2Data</code> (<code>FirstYearGPA</code>), 219 students at a Midwestern college. F: Galton (1886), <code>HistData</code> (<code>GaltonFamilies</code>).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Correlations measure *linear* relationships

:: left ::

<img src="/images/lecture16/nonlinear.png" class="w-4/5 rounded-lg mx-auto"/>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

What is the correlation between these two variables? Are they related?

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

*r* ≈ 0.02, but they are **strongly** related: the pattern is a U. Pearson's *r* only measures how well a **straight line** fits. A curved relationship needs a different method (e.g., nonlinear regression).

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Lesson" width="100%">r ≈ 0 means "no linear relationship," not "no relationship." Plot first.</StickyNote></p>

---
layout: section
color: indigo-light
align: lt
---

Part 2
# Calculating and testing *r*

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Pearson correlation coefficient

:: content ::

$$
r = \frac{\sum(X - M_X)(Y - M_Y)}{\sqrt{\sum (X - M_X)^2 \,\sum(Y - M_Y)^2}}
$$

<div class="grid grid-cols-2 gap-8 mt-2 text-[15px] leading-snug">
<div v-click>

**Numerator: how X and Y move together** (covariation)

For each person, multiply their deviation on X by their deviation on Y, then add up the products.
- Both above their means, or both below → **positive** product
- One above, one below → **negative** product

</div>
<div v-click>

**Denominator: how much X and Y vary on their own**

The square root of (SS<sub>X</sub> × SS<sub>Y</sub>). Dividing by it puts *r* on a −1 to +1 scale, whatever the units.

</div>
</div>

<p v-click><StickyNote color="amber-light" title="Signal ÷ noise, once more" width="70%">Numerator = shared movement (signal); denominator = total variability (noise). You will not compute <i>r</i> by hand; know what each part does.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# The numerator in a picture

:: left ::

<img src="/images/lecture17/quadrants.png" alt="GPA vs drinks per week split at the two means; points with negative products outnumber those with positive products" class="w-full mx-auto"/>

:: right ::

<div class="text-[15px] leading-snug">

The dashed lines are the two means. Every student falls in one of four quadrants:

- **Top right / bottom left** (teal): both above or both below their means → positive product
- **Top left / bottom right** (pink): one above, one below → negative product

</div>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

153 pink, 100 teal. What sign will *r* have?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Negative: the products are mostly negative, so their sum is too. (Strictly, the *sizes* of the products matter, not just the counts.)

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which points push *r* up, and which push it down?

:: content ::

<div class="flex justify-center items-start gap-4">
<img src="/images/lecture16/pearson_r_1.png" class="w-1/2 rounded-lg"/>
<img src="/images/lecture16/pearson_r_2.png" class="w-1/2 rounded-lg"/>
</div>

<div class="text-[15px] mt-2">

Bigger dots contribute bigger products. Points **far from both means** matter most, which is why a single extreme point can change *r* a lot (more on outliers soon).

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Is the correlation significant?

:: left ::

**H₀:** in the population, the correlation is 0 (ρ = 0). **H₁:** it is not 0.

The null world: if ρ = 0, sample *r*s bounce around 0, and this ratio follows a ***t* distribution with df = N − 2**:

$$t = \frac{r\sqrt{N-2}}{\sqrt{1 - r^2}}$$

==You don't need to memorize this formula.== Know what moves it:

- Larger |*r*| → larger *t*
- Larger N → larger *t*, and more df → a lower cutoff

:: right ::

<div v-click>

**Drinking and GPA:** *r* = −.27, N = 253

*t*(251) = −4.43, *p* < .001. Reject H₀.

</div>

<div v-click class="mt-3">

**Sleep and GPA:** *r* = −.06, N = 253

*t*(251) = −0.96, *p* = .34. Fail to reject.

</div>

<p v-click><StickyNote color="amber-light" title="Same t, new job" width="100%">This is a different test from the <i>t</i> tests for means. Only the null distribution is borrowed. Why N − 2? Next week: it comes from fitting a line, which needs two numbers (a slope and an intercept).</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: sample size

:: left ::

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

Two studies both find *r* = .30 between social media use and loneliness. Study 1 has N = 20; Study 2 has N = 200. Which is true?

- **A)** Both are significant, since *r* is the same.
- **B)** Study 2 is significant (*p* < .001) and Study 1 is not (*p* = .20), even though the relationship is equally strong in both.
- **C)** Study 1 has the stronger relationship because it is significant.
- **D)** Neither can be significant: .30 is below .50.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** *r* is the effect size; significance also depends on N. With 20 people, an *r* of .30 is well within what chance produces when ρ = 0; with 200, it is not. (D) confuses Cohen's guidelines with a significance cutoff.

</Admonition>

<p v-click><StickyNote color="amber-light" title="Familiar?" width="100%">Same lesson as <i>d</i> and η²: report the effect size, not just <i>p</i>. A huge N can make a trivial <i>r</i> significant.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Shared variance: *r*²

:: left ::

Square the correlation and you get the **coefficient of determination**, ***r*²** (often written *R*²): the **proportion of the variance** in one variable that is shared with, or accounted for by, the other.

- Drinking and GPA: *r* = −.27 → *r*² = **.07**. 7% of the differences in GPA go along with drinking; 93% do not.
- High school and college GPA: *r* = .45 → *r*² = **.20**.

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

If *r* = .90, what share of the variance is shared, and what is the rest?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

*r*² = .81: 81% shared. The other 19% comes from everything else (other variables, measurement error, chance).

</Admonition></p>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">The same idea as η² in ANOVA, and the heart of next week's regression: how much better can we predict Y once we know X?</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Correlation in R

:: left ::

```r
cor(sleep_data$drinks_per_week, sleep_data$gpa)
```

```text
[1] -0.2693046
```

```r
cor.test(sleep_data$drinks_per_week, sleep_data$gpa)
```

```text
	Pearson's product-moment correlation

t = -4.4303, df = 251, p-value = 1.407e-05
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.3800114 -0.1509915
sample estimates:
       cor 
-0.2693046 
```

:: right ::

<div class="text-[15px] leading-snug">

- `cor()` gives *r* only.
- `cor.test()` adds the test: *t*, df = N − 2, the *p* value, and a **95% CI for the population correlation**.

</div>

<p v-click><StickyNote color="amber-light" title="Plot it too" width="100%"><code>ggplot(data, aes(x = drinks_per_week, y = gpa)) + geom_point()</code> makes the scatterplot. Look at it before you trust <i>r</i>.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Speed dating: do you know how you come across?

:: left ::

<img src="/images/lecture17/speeddate_self_others.png" alt="Two scatterplots: self-rated attractiveness against average attractiveness rating from dates, and self-rated intelligence against average intelligence rating from dates" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Each dot is one person (102 Columbia graduate students, 5–20 four-minute dates each). Before the event, they rated themselves; after each date, their partner rated them. Fisman, Iyengar, Kamenica & Simonson (2006), <i>Quarterly Journal of Economics</i>; R package <code>sdamr</code> (<code>speeddate</code>).</div>

:: right ::

<Admonition title="Question" color="teal-light" width="100%">

Which self-rating tracks how dates saw people? Is either correlation significant? (N = 101 with both ratings.)

</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Attractiveness: *r*(99) = .28, *p* = .005, a weak positive correlation. Intelligence: *r*(99) = .01, *p* = .88, essentially zero. People have some idea how attractive others find them, and none about how smart they seem after four minutes.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Look at the x-axes" width="100%">88% of people rated their own intelligence 8–10. With so little spread in X, a strong <i>r</i> is hard to get.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a correlation in APA style

:: content ::

**Template:** *r*(df) = .XX, *p* = .XXX, 95% CI \[LL, UL], with the direction in words. df = N − 2.

<div v-click class="border-l-4 border-indigo-400 pl-4 mt-3 text-[17px] leading-snug">

Among 253 college students, those who drank more alcohol per week tended to have lower GPAs, *r*(251) = −.27, *p* < .001, 95% CI \[−.38, −.15].

</div>

<div v-click class="border-l-4 border-indigo-400 pl-4 mt-3 text-[17px] leading-snug">

Average hours of sleep per night were not significantly correlated with GPA, *r*(251) = −.06, *p* = .337, 95% CI \[−.18, .06].

</div>

<p v-click><StickyNote color="amber-light" title="No causal verbs" width="70%">"Tended to," "was associated with," "was correlated with." Not "drinking lowered GPA": these students weren't assigned to drink.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Multiple choice practice: reading the output

:: left ::

Same students: number of **classes missed** and **GPA**.

```text
t = -2.9248, df = 251, p-value = 0.003762
95 percent confidence interval:
 -0.29819423 -0.05954787
sample estimates:
       cor 
-0.1815426 
```

:: right ::

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

Which is the best summary?

- **A)** Missing class causes lower grades.
- **B)** A strong negative correlation: *r*(253) = −.18.
- **C)** Students who missed more classes tended to have lower GPAs, *r*(251) = −.18, *p* = .004; a small relationship.
- **D)** Not significant, because *r* is close to 0.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** (A) is causal language for observational data. (B): −.18 is small, and df = 251. (D): significance depends on N too; with 253 students, −.18 is significant.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Partial correlations

:: left ::

A **partial correlation** is the correlation between two variables after removing the influence of a **third** variable.

**Example:** people who play more tennis tend to live longer. Part of that could be education: more educated people play more tennis *and* live longer.

- Region **B** + **A**: the plain correlation of tennis and longevity
- Region **A** alone: the **partial** correlation, controlling for education

If *A* is still significant, tennis and longevity are related **above and beyond** education.

:: right ::

<img src="/images/lecture16/partial_correlation.png" class="w-7/8 rounded-lg mx-auto"/>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Always plot your data

:: content ::

<img src="/images/lecture17/anscombe.png" alt="Anscombe's quartet: four datasets with the same correlation and regression line but very different patterns" class="w-4/5 mx-auto"/>

All four datasets have the **same** *r* (.82), the same means, and the same best-fitting line. Only the first suits a correlation.

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What goes wrong in datasets 2, 3, and 4?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

2: a curve, not a line. 3: a perfect line spoiled by one outlier. 4: no relationship, except one extreme point that creates the whole correlation.

</Admonition></p>

<div class="text-xs text-gray-500">Anscombe (1973), <i>The American Statistician</i>; built into R as <code>anscombe</code>.</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Outliers can make or break *r*

:: content ::

<div class="flex justify-center items-start gap-4">
<img src="/images/lecture16/outlier.png" class="w-1/2 rounded-lg"/>
<img src="/images/lecture16/outlier2.png" class="w-1/2 rounded-lg"/>
</div>

<div class="grid grid-cols-2 gap-6 text-[15px]">
<div>

**Left:** one point far from the others **deflates** *r* (.81 → .40).

</div>
<div>

**Right:** one point **creates** a correlation from nothing (0 → .82).

</div>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Outliers: what should you do?

:: left ::

An **outlier** is a data point far from the rest. It can come from:
- **Measurement or data-entry errors** (a GPA of 34.0)
- **Genuine extreme values** (a student who really does miss 20 classes)
- **Sampling issues** (one person from a different population)

**Finding them:** look at the scatterplot first. Formal rules exist, such as flagging values more than 1.5 × IQR beyond the quartiles (or Grubbs' and Dixon's tests).

:: right ::

**Drop** a point if it is clearly an error.

**Keep** it if it is real variation.

**Other options:**
- Report results **with and without** the outlier
- Use a method that is robust to outliers, such as **Spearman's rank correlation** (Lecture 19's non-parametric tests)

<p v-click><StickyNote color="amber-light" title="Decide before you look" width="100%">The rule for dropping outliers should be set <b>before</b> you see how it changes <i>p</i>. Dropping points until the result is significant is p-hacking (Lecture 19).</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: strength

:: left ::

Hill (1990) studied final exam grades in a sociology course:

<table class="compact-table text-base">
<thead><tr><th>Variable</th><th><i>r</i> with exam grade</th></tr></thead>
<tbody>
<tr><td>Overall GPA</td><td>.72</td></tr>
<tr><td>Number of absences</td><td>−.51</td></tr>
<tr><td>Hours spent studying</td><td>.31</td></tr>
</tbody>
</table>

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

Which variable has the **strongest** relationship with exam grade?

- **A)** Hours spent studying
- **B)** Number of absences, because −.51 is the most extreme
- **C)** All three are equally strong
- **D)** Overall GPA

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** Strength is the size of *r* ignoring its sign: .72 > .51 > .31. The minus sign on absences only gives the direction.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: causation

:: left ::

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

A survey finds *r* = −.45 between daily screen time and sleep quality. Which interpretation is most appropriate?

- **A)** People with more screen time tend to report worse sleep quality.
- **B)** Screen time causes poor sleep.
- **C)** Poor sleep causes more screen time.
- **D)** A third variable (e.g., stress) must explain both.

</Admonition>

:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** A correlation describes an association. (B) and \(C) are both possible directions, and (D) is a possible confound, but nothing in the data tells us which. An experiment (for example, randomly assigning people to put their phones away at night) could.

</Admonition>

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

**Correlation** — an association between two numeric variables, usually observational. Not evidence of causation.

</div>
<div>

**Pearson's *r*** — −1 to +1. Sign = direction; size = strength (small .10, medium .30, large .50). Measures **linear** relationships only.

</div>
<div>

**Significance of *r*** — H₀: ρ = 0. Tested with *t*, df = N − 2. Depends on both |*r*| and N. `cor.test()` in R; report *r*(df), *p*, 95% CI.

</div>
<div>

***r*² (coefficient of determination)** — the proportion of variance two variables share.

</div>
<div>

**Partial correlation** — the correlation between two variables after removing a third.

</div>
<div>

**Outliers** — extreme points that can create or hide a correlation. Plot first; decide how to handle them before testing.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Happy Thanksgiving! Next class (Tues. 12/1): Regression.
