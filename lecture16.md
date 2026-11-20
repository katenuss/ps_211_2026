---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 16
exportFilename: ps211_fall2026_lecture16
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 16: Repeated-Measures ANOVA & Two-Way ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates & Reminders

:: content ::

<div class="text-[15px]">

- ==Data Write-Up #2== (ANOVA-based) is due **Tuesday, December 8** at 11:59 p.m.
- ==Exam 4== (the last exam) is **Thursday, December 10**, in class. **There will be no make-ups.**
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 – 3:30 p.m. (Rola)
- Discussion sections: remember, you need to pass **10 of the 13** sections for full credit.
- Coming up:
  - Tuesday (11/24): Lecture 17 (correlation)
  - **No discussion Wed. 11/25 and no class Thurs. 11/26: Happy Thanksgiving!**
  - Wednesday (12/2): Discussion 12, Write-Up #2 work session

</div>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
Remember, you can use the grade calculator (pinned on Slack) to see how future assignments will affect your final grade!
</SpeechBubble>

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

**One-way between-groups ANOVA** — one test of whether 3+ separate groups have the same mean. H₁: at least one differs.

</div>
<div>

***F* statistic** — MS<sub>Between</sub> ÷ MS<sub>Within</sub>: spread of the group means vs. spread inside the groups. Never negative; one-tailed; df = (k − 1, N − k).

</div>
<div>

**Source table** — SS → df → MS (= SS/df) → *F*, for each source of variability. `summary(aov(dv ~ group))` prints it.

</div>
<div>

**η²** — SS<sub>Between</sub>/SS<sub>Total</sub>: proportion of variability explained by the groups. **Post-hoc tests** (Tukey, Bonferroni) find which groups differ, after a significant *F*.

</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Today, two upgrades to the same F: the same people in every condition (like the paired t test), and two IVs at once.</SpeechBubble>
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

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

A one-way ANOVA reports `F(3, 76) = 2.10, p = .11`. How many groups and how many participants were there?

- **A)** 3 groups, 76 participants
- **B)** 4 groups, 79 participants
- **C)** 4 groups, 80 participants
- **D)** 3 groups, 79 participants

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** df<sub>Between</sub> = k − 1 = 3, so k = 4. df<sub>Within</sub> = N − k = 76, so N = 80. (B) subtracts only one.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

A one-way ANOVA on five groups is **not** significant. A student then runs all 10 pairwise *t* tests without any correction and reports the one with *p* = .03. What is wrong?

- **A)** Post-hoc tests follow only a significant *F*, and 10 uncorrected tests give about a 40% chance of a false positive.
- **B)** Nothing: *p* = .03 is below .05.
- **C)** They should have run 20 tests.
- **D)** They should have used a one-tailed test.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** Alpha inflation, plus reporting only the winner: Lecture 15's preview of p-hacking. With Bonferroni, each test would need *p* < .005.

</Admonition></p>

---
layout: section
color: indigo-light
align: lt
---

Finishing Lecture 15
# One-Way ANOVA: practice
---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice: owls, larks, and missed classes

:: left ::

Our sleep data from Discussions 5–6: **253 college students** who called themselves larks (morning people), owls (night people), or neither. Do they miss different numbers of classes?

<table class="compact-table text-base">
<thead><tr><th></th><th>n</th><th><i>M</i></th><th><i>SD</i></th></tr></thead>
<tbody>
<tr><td>Lark</td><td>41</td><td>1.56</td><td>2.00</td></tr>
<tr><td>Neither</td><td>163</td><td>1.77</td><td>2.36</td></tr>
<tr><td>Owl</td><td>49</td><td>4.20</td><td>5.29</td></tr>
</tbody>
</table>

```text
             Df Sum Sq Mean Sq F value   Pr(>F)    
chronotype    2  243.2  121.62   12.65 5.82e-06 ***
Residuals   250 2402.7    9.61                     
```

<div class="text-xs text-gray-500 mt-1">Data: Onyper, Thacher, Gilbert, & Gradess (2012), <i>Chronobiology International</i>; Lock5Data (<code>SleepStudy</code>).</div>

:: right ::

<img src="/images/lecture15/chronotype_missed.png" alt="Classes missed by chronotype, individual students and group means with standard-error bars" class="w-11/12 mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What are df<sub>Between</sub> and df<sub>Within</sub>, and what is η²?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

3 − 1 = 2 and 253 − 3 = 250. η² = 243.2 / (243.2 + 2,402.7) = .09.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Owls: what can we conclude?

:: left ::

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

Tukey tests show owls missed more classes than both larks and "neither" (*p*s < .001), who did not differ. Which conclusion is justified?

- **A)** Being a night owl causes students to miss class.
- **B)** Owls should be assigned afternoon classes.
- **C)** Owls missed significantly more classes than the other students; we can't say why.
- **D)** No conclusion: one-way ANOVA needs equal group sizes.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Chronotype was not assigned, so this is observational: owls might differ in many ways (later bedtimes, heavier course loads). (A) and (B) both assume a cause. (D): unequal ns are fine.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

For classes missed, η² = .09. Which statement is correct?

- **A)** 9% of owls missed class.
- **B)** Chronotype accounts for about 9% of the variability in classes missed; the other 91% comes from everything else about the students.
- **C)** The effect is too small to be real.
- **D)** Owls missed 9% more classes than larks.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** η² is a proportion of variability, not of people (A) or of classes (D). \(C): by Cohen's guide .09 is a medium effect, and the significant *F* says it is unlikely to be chance.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# A non-significant ANOVA: GPA by chronotype

:: left ::

Same students. Do larks, owls, and "neither" differ in **GPA**?

<table class="compact-table text-base">
<thead><tr><th></th><th>Lark</th><th>Neither</th><th>Owl</th></tr></thead>
<tbody>
<tr><td><i>M</i> (<i>SD</i>)</td><td>3.33 (0.40)</td><td>3.24 (0.39)</td><td>3.20 (0.44)</td></tr>
</tbody>
</table>

```text
             Df Sum Sq Mean Sq F value Pr(>F)
chronotype    2   0.43   0.215   1.319  0.269
Residuals   250  40.76   0.163               
```

:: right ::

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

What should the researchers do next?

- **A)** Report that they found no significant GPA difference among chronotypes (η² = .01), and stop: no post-hoc tests.
- **B)** Run Tukey tests to find the hidden difference between larks and owls.
- **C)** Conclude that chronotype is unrelated to GPA in every population.
- **D)** Switch to α = .30 so the result is significant.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Post-hoc tests only follow a significant *F* (B). Failing to reject is not proof of no difference \(C), though with 253 students and η² = .01, any difference is likely small. (D) changes the rule after seeing the data.

</Admonition>

---
layout: section
color: indigo-light
align: lt
---

Part 1
# Repeated-Measures ANOVA

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Four tests, two questions

:: content ::

Two questions pick the test, as long as the DV is numeric: **how many conditions?** and **are the same people in each?**

<table class="compact-table text-base mt-2">
<thead><tr><th></th><th>Different people in each condition<br/>(between-groups)</th><th>Same people in every condition<br/>(within-groups, repeated measures)</th></tr></thead>
<tbody>
<tr><td><b>2 conditions</b></td><td>Independent-samples <i>t</i> test (Lecture 14)</td><td>Paired-samples <i>t</i> test (Lecture 13)</td></tr>
<tr><td><b>3+ conditions</b></td><td>One-way between-groups ANOVA (Lecture 15)</td><td><b>Repeated-measures ANOVA (today)</b></td></tr>
</tbody>
</table>

<p v-click>

A **repeated-measures ANOVA** (also called a **within-groups** ANOVA) compares 3+ conditions when every participant does all of them. It still uses *F*, but it removes something the between-groups version cannot: **stable differences between people**.

</p>

<p v-click><StickyNote color="amber-light" title="Déjà vu" width="70%">This is exactly why the paired <i>t</i> test is more powerful than the independent one: each person is their own control.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: which design?

:: left ::

Which of these studies call for a **repeated-measures ANOVA**?

1. Memory performance after 0, 1, and 2 cups of coffee, with the same participants on three days.
2. Test scores of students from three different schools.
3. Reaction times of the same participants under three lighting conditions.
4. Whether hours of sleep per night relate to GPA.

:: right ::

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

**A)** 1 and 3 &nbsp; **B)** 2 and 3 &nbsp; **C)** All four &nbsp; **D)** Only 1

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** Studies 1 and 3 measure the same people in three conditions. Study 2 has different students in each school: a one-way between-groups ANOVA. Study 4 has two numeric variables and no conditions at all: a correlation (Tuesday).

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Our example: caffeine, chocolate & tapping

:: left ::

<div class="text-[15px] leading-snug">

**Four people**, tested on three days. Each day they swallowed a tablet containing **caffeine**, **theobromine** (the caffeine-like chemical in chocolate), or a **placebo**. Two hours later, they tapped a finger as fast as they could.

DV: taps in a fixed interval.

</div>

<table class="compact-table text-base mt-2">
<thead><tr><th>Person</th><th>Placebo</th><th>Caffeine</th><th>Theobromine</th></tr></thead>
<tbody>
<tr><td>I</td><td>11</td><td>26</td><td>20</td></tr>
<tr><td>II</td><td>56</td><td>83</td><td>71</td></tr>
<tr><td>III</td><td>15</td><td>34</td><td>41</td></tr>
<tr><td>IV</td><td>6</td><td>13</td><td>32</td></tr>
<tr><td><b>Mean</b></td><td><b>22</b></td><td><b>39</b></td><td><b>41</b></td></tr>
</tbody>
</table>

<div class="text-xs text-gray-500 mt-1">Data: Scott & Chen (1944), <i>Journal of Pharmacology and Experimental Therapeutics</i>; via Bliss (1967); R package <code>Stat2Data</code> (<code>Fingers</code>).</div>

:: right ::

<img src="/images/lecture16/fingers_lines.png" alt="Each person's tapping rate across the three drugs, with the condition means" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

What stands out about Person II?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Person II taps far faster than everyone else **in every condition**. People differ a lot in baseline speed, and those differences have nothing to do with the drugs.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Removing each person's average, step by step

:: content ::

<div class="grid grid-cols-3 gap-3 text-[14px] leading-snug">
<div>
<img src="/images/lecture16/rm_step1_raw.png" alt="Each person's tapping rate across the three drugs, with a dashed line at each person's average" class="w-full"/>

Dashed lines: each person's **average** (19, 70, 30, 17). Ignore who is who, and these baseline gaps become spread *within* each drug: big error bars.

</div>
<div v-click>
<img src="/images/lecture16/rm_step2_adjusted.png" alt="The same lines after each person's average is subtracted and the overall mean of 34 is added back; the lines now overlap" class="w-full"/>

Subtract each person's own average, add back the overall mean. Person I, placebo: 11 − 19 + 34 = **26**. Everyone now has the same average; only how each person **changed** across drugs is left.

</div>
<div v-click>
<img src="/images/lecture16/rm_step3_bars.png" alt="Mean and standard error for each drug, computed from the adjusted scores, with the adjusted scores shown as dots" class="w-full"/>

Mean and SE for each drug from the step-2 scores. The means don't move (22, 39, 41); the error bars shrink. These are the right-hand bars on the next slide.

</div>
</div>

<div v-click class="text-xs text-gray-500 mt-2">One small extra step: the SE is multiplied by √(k / (k − 1)) = √(3/2), because removing averages slightly shrinks the spread (Morey, 2008).</div>
---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Same data, two analyses

:: content ::

<img src="/images/lecture16/fingers_errorbars.png" alt="Mean taps per drug with standard-error bars: large bars when people's baselines are ignored, small bars after removing each person's average" class="w-4/5 mx-auto"/>

<div class="grid grid-cols-2 gap-8 text-[15px] leading-snug">
<div v-click>

**Treat the 12 scores as 3 separate groups** (one-way ANOVA): the huge differences between people count as noise. *F*(2, 9) = 0.68, *p* = .53. Nothing.

</div>
<div v-click>

**Use the fact that the same 4 people did everything** (repeated-measures ANOVA): remove each person's average first. *F*(2, 6) = 7.88, *p* = .021. **Significant.**

</div>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why is each score far from the grand mean?

:: content ::

<div class="text-[15px] leading-snug">

Every score = grand mean + **drug piece** + **person piece** + **leftover**. Person II on caffeine: 83 = 34 + <span class="text-pink-600 font-bold">5</span> + <span class="text-gray-500 font-bold">36</span> + <span class="text-teal-600 font-bold">8</span>. Each SS adds up the squared lengths of one kind of piece.

</div>

<div class="grid grid-cols-4 gap-2 mt-1">
<img src="/images/lecture16/ss_step1_total.png" alt="Each of the 12 scores as a line from the grand mean of 34; SS total 6,682" class="w-full"/>
<img v-click src="/images/lecture16/ss_step2_drug.png" alt="Each score replaced by its drug's mean; short lines; SS drug 872" class="w-full"/>
<img v-click src="/images/lecture16/ss_step3_person.png" alt="Each score replaced by its person's mean; Person II far above 34 in every condition; SS person 5,478" class="w-full"/>
<img v-click src="/images/lecture16/ss_step4_leftover.png" alt="What is left after removing drug and person pieces; short lines; SS leftover 332" class="w-full"/>
</div>

<p v-click><Admonition title="Why is the person piece so big?" color="green-light" width="100%">

The drug pieces are short (−12, +5, +7). The person pieces are long, and each one appears in **all three** conditions: Person II alone is 36 above 34 three times, 3 × 36² = 3,888 of the 5,478. Most of what made the scores differ was **who** was tapping, not which pill they took.

</Admonition></p>
---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where the individual differences go

:: content ::

The between-groups ANOVA splits variability into two parts. Repeated measures adds **a third**:

$$SS_\text{Total} = SS_\text{Between} + SS_\text{Subjects} + SS_\text{Within}$$

<img src="/images/lecture16/ss_split.png" alt="Stacked bars: the same total sum of squares split two ways; in the repeated-measures version most of the within-groups part becomes subjects" class="w-4/5 mx-auto"/>

<div class="text-[15px] leading-snug">

- **SS<sub>Subjects</sub>**: stable differences between people (Person II is fast in every condition).
- **SS<sub>Within</sub>** (often called **error**): what is left, the noise that is *not* explained by drug or by person. It becomes the denominator of *F*.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Computing SS<sub>Subjects</sub>

:: left ::

<div class="text-[15px] leading-snug">

1. Find each **person's mean** across conditions.
2. Subtract the **grand mean** (all scores; here 34).
3. Square, add up, and multiply by **k**, the number of conditions (each person contributes k scores).

</div>

$$SS_\text{Subjects} = k \sum (M_\text{person} - M_G)^2$$

<img src="/images/lecture16/subjects_dev.png" alt="Each person's three scores, their average, and the distance from the grand mean of 34: minus 15, plus 36, minus 4, minus 17" class="w-3/4 mx-auto"/>

:: right ::

<table class="compact-table text-base">
<thead><tr><th>Person</th><th>Mean</th><th>Mean − 34</th><th>Squared</th></tr></thead>
<tbody>
<tr><td>I</td><td>19</td><td>−15</td><td>225</td></tr>
<tr><td>II</td><td>70</td><td>36</td><td>1,296</td></tr>
<tr><td>III</td><td>30</td><td>−4</td><td>16</td></tr>
<tr><td>IV</td><td>17</td><td>−17</td><td>289</td></tr>
<tr><td colspan="3"><b>Sum</b></td><td><b>1,826</b></td></tr>
</tbody>
</table>

<p v-click>

SS<sub>Subjects</sub> = 3 × 1,826 = **5,478**: most of the total variability (6,682) is just who the person was.

</p>

<p v-click><StickyNote color="amber-light" title="Look familiar?" width="100%">The same recipe as SS<sub>Between</sub> (group means vs. the grand mean, weighted by how many scores each mean is based on), applied to people instead of conditions.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Degrees of freedom for repeated measures

:: content ::

k = number of conditions (3), n = number of people (4), N = n × k = total number of scores (12)

<table class="compact-table text-base mt-2">
<thead><tr><th>Source</th><th>df</th><th>Tapping study</th><th>Why</th></tr></thead>
<tbody>
<tr v-click><td>Between (conditions)</td><td>k − 1</td><td>2</td><td>3 condition means around one grand mean</td></tr>
<tr v-click><td>Subjects</td><td>n − 1</td><td>3</td><td>4 person means around one grand mean</td></tr>
<tr v-click><td><b>Within (error)</b></td><td><b>(k − 1)(n − 1)</b></td><td><b>6</b></td><td>what is left once conditions and people are accounted for</td></tr>
<tr v-click><td>Total</td><td>N − 1</td><td>11</td><td>12 scores around one grand mean</td></tr>
</tbody>
</table>

<p v-click>

Check: 2 + 3 + 6 = 11. The *F* test uses **df<sub>Between</sub> and df<sub>Within</sub>**: *F*(2, 6).

</p>

<p v-click><StickyNote color="amber-light" title="The price of removing people" width="70%">The between-groups ANOVA on the same 12 scores had df<sub>Within</sub> = 9. Repeated measures spends 3 of those on SS<sub>Subjects</sub>. Fewer df means a higher cutoff, but here the noise shrank so much (5,810 → 332) that it is well worth it.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The source table for the tapping study

:: content ::

<table class="compact-table text-base">
<thead><tr><th>Source</th><th>SS</th><th>df</th><th>MS</th><th><i>F</i></th></tr></thead>
<tbody>
<tr><td>Between (drug)</td><td>872</td><td>2</td><td><span v-click="1">872 / 2 = 436.0</span></td><td><span v-click="2"><b>436.0 / 55.3 = 7.88</b></span></td></tr>
<tr><td>Subjects</td><td>5,478</td><td>3</td><td><span v-click="1">5,478 / 3 = 1,826.0</span></td><td></td></tr>
<tr><td>Within (error)</td><td>332</td><td>6</td><td><span v-click="1">332 / 6 = 55.3</span></td><td></td></tr>
<tr><td><b>Total</b></td><td>6,682</td><td>11</td><td></td><td></td></tr>
</tbody>
</table>

<p v-click="3">

The cutoff for *F*(2, 6) at α = .05 is 5.14. 7.88 > 5.14, so **reject H₀**: tapping speed was not the same under the three drugs (*p* = .021).

</p>

<p v-click="4"><Admonition title="Question" color="teal-light" width="100%">

Why is there no *F* for Subjects?

</Admonition></p>

<p v-click="5"><Admonition title="Answer" color="green-light" width="100%">

Nobody's hypothesis is "people differ from one another"; of course they do. SS<sub>Subjects</sub> is computed only so it can be taken *out* of the noise.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Six steps for a repeated-measures ANOVA

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Step</th><th>One-way between-groups ANOVA</th><th>Repeated-measures ANOVA</th></tr></thead>
<tbody>
<tr><td><b>1.</b> Populations, distribution, assumptions</td><td>3+ separate groups</td><td><b>The same people in 3+ conditions.</b> DV numeric, roughly normal; order effects handled (counterbalancing)</td></tr>
<tr><td><b>2.</b> Hypotheses</td><td colspan="2">H₀: μ₁ = μ₂ = μ₃ = … &nbsp; H₁: at least one μ differs. Identical.</td></tr>
<tr><td><b>3.</b> Comparison distribution</td><td><i>F</i>, df = (k − 1, N − k)</td><td><i>F</i>, df = (k − 1, <b>(k − 1)(n − 1)</b>)</td></tr>
<tr><td><b>4.</b> Critical value</td><td colspan="2">α = .05, one cutoff in the upper tail. Identical.</td></tr>
<tr><td><b>5.</b> Test statistic</td><td><i>F</i> = MS<sub>Between</sub>/MS<sub>Within</sub></td><td><i>F</i> = MS<sub>Between</sub>/MS<sub>Within</sub>, <b>after SS<sub>Subjects</sub> is removed from the noise</b></td></tr>
<tr><td><b>6.</b> Decision</td><td>Reject or not; then Tukey or Bonferroni</td><td>Reject or not; then <b>paired <i>t</i> tests with a correction</b></td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Effect size: partial η²" width="70%">Leave the people out of the denominator too: partial η² = SS<sub>Between</sub> / (SS<sub>Between</sub> + SS<sub>Within</sub>) = 872 / (872 + 332) = <b>.72</b>. Of the variability <i>within</i> each person, 72% is explained by the drug.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Repeated-measures ANOVA in R

:: left ::

```r
taps_model <- aov(taps ~ drug + Error(person / drug),
                  data = tapping)
summary(taps_model)
```

```text
Error: person
          Df Sum Sq Mean Sq F value Pr(>F)
Residuals  3   5478    1826               

Error: person:drug
          Df Sum Sq Mean Sq F value Pr(>F)  
drug       2    872   436.0    7.88  0.021 *
Residuals  6    332    55.3                 
```

:: right ::

<div class="text-[15px] leading-snug">

- `Error(person / drug)` tells R that each **person** experienced every level of **drug**.
- The first block is SS<sub>Subjects</sub>, set aside.
- The second block is the test: the `drug` row over the leftover `Residuals` (error).

</div>

<p v-click><StickyNote color="amber-light" title="Long format" width="100%">R needs one row per person per condition (12 rows here), with a column saying who the person is. A table with one row per person and one column per condition has to be reshaped first.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Within-groups designs: pros and cons

:: left ::

**Advantages**
- **Removes individual differences** from the noise: every participant is their own control
- **More power** with the same number of people
- **Fewer participants** needed

<img src="/images/lecture15/dejavu_meme.jpeg" class="w-1/2 mx-auto mt-2"/>

:: right ::

**Disadvantages**
- **Order effects**: performance changes because of *when* a condition came
  - **Practice effects**: getting better with familiarity
  - **Fatigue effects**: getting worse from tiredness or boredom
- **Carryover effects**: one condition lingers into the next (a drug that hasn't worn off)

<p v-click><StickyNote color="amber-light" title="The fix" width="100%"><b>Counterbalancing</b>: vary the order of conditions across participants, so order effects are spread evenly over conditions instead of piling onto one. It can't remove carryover; a gap between sessions can.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: order effects

:: left ::

*Participants memorize word lists after drinking 0, 1, or 2 cups of coffee, one condition per day, always in that order. Everyone improves from day to day, whatever the dose.*

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

Which disadvantage of within-groups designs does this show?

- **A)** Individual differences
- **B)** Practice effects
- **C)** Fatigue effects
- **D)** Low power

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** People got better at memorizing lists. Because the order was always 0 → 1 → 2 cups, practice is completely confounded with dose.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

What is the best way to fix the design?

- **A)** Recruit more participants.
- **B)** Ask participants not to practice between sessions.
- **C)** Switch to a between-groups design, since within-groups designs can't be fixed.
- **D)** Counterbalance: different participants get the three doses in different orders.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**D.** Practice still happens, but now it helps every dose equally. (A) doesn't change the confound. (B) can't stop learning the task. \(C) would work but gives up the power advantage.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Practice: does music change your sense of time?

:: left ::

<div class="text-[15px] leading-snug">

**20 students** each said "stop" when they thought 45 seconds had passed, three times: in **silence**, with an **upbeat** song (David Guetta), and with a **calm** piece (Bach). The order of conditions was **randomized** for each student.

</div>

```text
Error: student
          Df Sum Sq Mean Sq F value Pr(>F)
Residuals 19   9671     509               

Error: student:music
          Df Sum Sq Mean Sq F value   Pr(>F)    
music      2   6889    3444   42.13 2.28e-10 ***
Residuals 38   3107      82                     
```

<div class="text-xs text-gray-500 mt-1">Data collected by Ksenia Vlasov at Oberlin College; R package <code>Stat2Data</code> (<code>MusicTime</code>).</div>

:: right ::

<img src="/images/lecture16/music_time.png" alt="Each student's time estimate in silence, upbeat music, and calm music; means rise from 37 to 53 to 63 seconds" class="w-full mx-auto"/>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Where do df = 2 and df = 38 come from?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

k − 1 = 3 − 1 = 2; (k − 1)(n − 1) = 2 × 19 = 38. The 19 on top is n − 1 for the students.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Music and time: interpreting the result

:: left ::

<Admonition title="Multiple choice 9" color="teal-light" width="100%">

Mean "45 seconds": silence 37 s, upbeat 53 s, calm 63 s. Paired *t* tests with a Bonferroni correction show every pair differs (all *p* < .001). Which conclusion is correct?

- **A)** Music makes everyone worse at judging time.
- **B)** The *F* test alone showed that all three conditions differ.
- **C)** At least one condition differed; follow-up tests show all three did. With calm music, students let the most time pass before saying 45 seconds were up.
- **D)** The result can't be trusted, because the same students did all three conditions.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** (A): the lines show some students moved the other way. (B): *F* says only "not all equal"; the follow-ups say which. (D): that is the design's strength.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 10" color="teal-light" width="100%">

Why did the researcher randomize the order of conditions for each student?

- **A)** To get more df
- **B)** So practice or boredom effects are spread across all three conditions instead of piling onto one
- **C)** So that the conditions are independent groups
- **D)** Because R requires it

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Randomizing the order is one way to counterbalance. It doesn't change the df (A) or the design \(C).

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reporting a repeated-measures ANOVA in APA style

:: content ::

Include: the type of ANOVA, each condition's *M* and *SD*, ***F*(df<sub>IV</sub>, df<sub>Residuals</sub>)**, *p*, **partial η²**, and which post-hoc test you used and what it showed.

<div v-click class="border-l-4 border-indigo-400 pl-4 mt-3 text-[17px] leading-snug">

A one-way repeated-measures ANOVA compared students' estimates of 45 seconds across three listening conditions. Estimates differed by condition, *F*(2, 38) = 42.13, *p* < .001, partial η² = .69. Bonferroni-corrected paired *t* tests showed that estimates were shortest in silence (*M* = 37.05 s, *SD* = 12.11), longer with upbeat music (*M* = 52.85 s, *SD* = 12.98), and longest with calm music (*M* = 63.10 s, *SD* = 18.90); every pair differed (all *p*s < .001).

</div>

<p v-click><StickyNote color="amber-light" title="Different from Lecture 15" width="80%">Say <b>repeated-measures</b>. Take both dfs from the lower table (<code>Error: student:music</code>): 2 and 38, not 19. Partial η² = 6889 / (6889 + 3107) = .69, leaving the students' 9,671 out. Post-hoc tests: paired <i>t</i> tests with a correction, not Tukey; name the correction you used.</StickyNote></p>

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

**Repeated-measures (within-groups) ANOVA** — compares 3+ conditions when the same people do all of them. *F* = MS<sub>Between</sub>/MS<sub>Within</sub>, df = (k − 1, (k − 1)(n − 1)).

</div>
<div>

**SS<sub>Subjects</sub>** — variability due to stable differences between people, k Σ(M<sub>person</sub> − M<sub>G</sub>)². Removed from the noise, which is why repeated measures has more power.

</div>
<div>

**Order effects & counterbalancing** — practice, fatigue, and carryover; varying the order across participants spreads them evenly over conditions.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Tuesday: two-way ANOVA, then correlation. No discussion or class during Thanksgiving week after Tuesday.
