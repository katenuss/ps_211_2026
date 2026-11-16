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

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

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

1. Find each **person's mean** across conditions.
2. Subtract the **grand mean** (all scores; here 34).
3. Square, add up, and multiply by **k**, the number of conditions (each person contributes k scores).

$$SS_\text{Subjects} = k \sum (M_\text{person} - M_G)^2$$

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
<tr><td>Subjects</td><td>5,478</td><td>3</td><td><span v-click="1">5,478 / 3 = 1,826.0</span></td><td><span v-click="2">(not tested)</span></td></tr>
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
<tr><td><b>6.</b> Decision</td><td>Reject or not; then Tukey or Bonferroni</td><td>Reject or not; then <b>paired <i>t</i> tests with a Bonferroni correction</b></td></tr>
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

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

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

<p v-click><StickyNote color="amber-light" title="Different from Lecture 15" width="80%">Say <b>repeated-measures</b>. Take both dfs from the lower table (<code>Error: student:music</code>): 2 and 38, not 19. Partial η² = 6889 / (6889 + 3107) = .69, leaving the students' 9,671 out. Post-hoc tests: Bonferroni-corrected paired <i>t</i> tests, not Tukey.</StickyNote></p>

---
layout: section
color: indigo-light
align: lt
---

Part 2: what if we have **two** independent variables?
# Two-Way ANOVA

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Why study two IVs at once?

:: left ::

A **two-way ANOVA** tests two categorical IVs (each with 2+ levels) and one numeric DV in a single analysis. Any design with 2+ IVs is a **factorial design**.

- **Efficient**: two questions from one study
- **Interactions**: does the effect of one IV **depend on** the other? You can only ask this with both in the same study.

:: right ::

Each combination of levels is a **cell**. A **2 × 3** design (IV₁ has 2 levels, IV₂ has 3) has 6 cells:

<table class="compact-table text-base">
<thead><tr><th></th><th>IV₂: level 1</th><th>IV₂: level 2</th><th>IV₂: level 3</th></tr></thead>
<tbody>
<tr><td><b>IV₁: level 1</b></td><td>cell 1</td><td>cell 2</td><td>cell 3</td></tr>
<tr><td><b>IV₁: level 2</b></td><td>cell 4</td><td>cell 5</td><td>cell 6</td></tr>
</tbody>
</table>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

How many cells in a 2 × 2 design? A 3 × 4?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

4 and 12: multiply the numbers of levels.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Our example: who conforms, and to whom?

:: left ::

<div class="text-[15px] leading-snug">

**45 participants** made judgments alongside a partner who kept disagreeing with them. DV: how often they **changed their answer to match the partner** (out of 40 critical trials).

- **IV₁: partner's status**, high or low (randomly assigned)
- **IV₂: participant's authoritarianism** (how much they defer to authority), measured with a questionnaire (the F-scale), split into low, medium, high

A **2 × 3** design.

</div>

<div class="text-xs text-gray-500 mt-1">Data: Moore & Krupat (1971), <i>Sociometry</i>; R package <code>carData</code> (<code>Moore</code>).</div>

:: right ::

Mean conforming responses (n per cell):

<table class="compact-table text-base">
<thead><tr><th>Partner</th><th>Low auth.</th><th>Medium</th><th>High auth.</th></tr></thead>
<tbody>
<tr><td><b>High status</b></td><td>17.4 (5)</td><td>14.3 (11)</td><td>11.9 (7)</td></tr>
<tr><td><b>Low status</b></td><td>8.9 (10)</td><td>7.2 (4)</td><td>12.6 (8)</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="Only one IV was manipulated" width="100%">Partner status was randomly assigned, so its effect is causal. Authoritarianism was measured, so differences between those groups are observational. Many real factorial studies mix the two.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Three questions, three *F*s

:: content ::

A two-way ANOVA produces **three *F* statistics**, one per question:

<div class="grid grid-cols-3 gap-4 mt-3 text-[15px] leading-snug">
<div v-click class="border-2 border-gray-300 rounded-lg p-3">

**1. Main effect of partner status**

Averaging over authoritarianism, do people conform more to high- than to low-status partners?

</div>
<div v-click class="border-2 border-gray-300 rounded-lg p-3">

**2. Main effect of authoritarianism**

Averaging over partner status, do low-, medium-, and high-authoritarian people conform differently?

</div>
<div v-click class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3">

**3. Interaction (status × authoritarianism)**

Does the effect of partner status **depend on** the participant's authoritarianism?

</div>
</div>

<p v-click>

Each is still an *F* = MS<sub>effect</sub> / MS<sub>Within</sub>: the variability that effect explains, compared with the noise inside the cells. All three share **the same denominator**, the within-cells noise.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Main effects use marginal means

:: left ::

A **marginal mean** is the mean for one level of an IV, ignoring the other IV: the mean of everyone in that row or column (it sits in the table's *margin*).

<table class="compact-table text-base">
<thead><tr><th>Partner</th><th>Low</th><th>Med.</th><th>High</th><th style="color:#7e57c2">Marginal</th></tr></thead>
<tbody>
<tr><td><b>High status</b></td><td>17.4</td><td>14.3</td><td>11.9</td><td style="color:#7e57c2"><b>14.2</b></td></tr>
<tr><td><b>Low status</b></td><td>8.9</td><td>7.2</td><td>12.6</td><td style="color:#7e57c2"><b>10.0</b></td></tr>
<tr><td style="color:#0d9488"><b>Marginal</b></td><td style="color:#0d9488"><b>11.7</b></td><td style="color:#0d9488"><b>12.4</b></td><td style="color:#0d9488"><b>12.3</b></td><td></td></tr>
</tbody>
</table>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

From the marginal means alone, which main effect looks real?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Partner status: 14.2 vs. 10.0. The authoritarianism margins (11.7, 12.4, 12.3) are nearly identical, so averaged over partners, authoritarianism seems not to matter.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="But look inside the table" width="100%">For high-authoritarian people the status gap is gone (11.9 vs. 12.6). The margins hide that. Cell means show interactions.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Interactions use cell means

:: left ::

<img src="/images/lecture16/moore_interaction.png" alt="Conformity by authoritarianism for high- and low-status partners; the lines converge and cross at high authoritarianism" class="w-full mx-auto"/>

:: right ::

<div class="text-[15px] leading-snug">

An **interaction**: the effect of one IV **changes depending on** the level of the other.

- Low and medium authoritarianism: people conformed **much more** to a high-status partner.
- High authoritarianism: partner status made **no difference**.

</div>

<p v-click><StickyNote color="amber-light" title="Reading the plot" width="100%"><b>Parallel lines</b> → the effect of one IV is the same at every level of the other: no interaction. <b>Lines that converge, diverge, or cross</b> → an interaction. Always plot the cell means; interactions are hard to see in a table of numbers.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-7-5
---

:: title ::
# Two-way ANOVA in R

:: left ::

```r
conform_model <- aov(conformity ~ partner_status * authoritarianism,
                     data = conformity_data)
summary(conform_model)
```

```text
                                Df Sum Sq Mean Sq F value  Pr(>F)   
partner_status                   1  204.3  204.33   9.745 0.00338 **
authoritarianism                 2   11.6    5.81   0.277 0.75956   
partner_status:authoritarianism  2  175.5   87.74   4.185 0.02257 * 
Residuals                       39  817.8   20.97                   
```

The `*` in the formula asks for both main effects **and** their interaction (the row with the colon).

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Which effects are significant at α = .05?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The main effect of partner status (*p* = .003) and the interaction (*p* = .023). Not authoritarianism (*p* = .76).

</Admonition></p>

<p v-click><Admonition title="Question" color="teal-light" width="100%">

Why is the Residuals df 39?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

45 people minus 6 cells: one df spent on each cell's mean, just like N − k in a one-way ANOVA.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where each row of the table comes from

:: content ::

<table class="compact-table text-base">
<thead><tr><th>Row</th><th>df</th><th>Here</th><th>Variability it measures</th></tr></thead>
<tbody>
<tr><td>Main effect of IV₁ (status)</td><td>levels₁ − 1</td><td>1</td><td>between the IV₁ marginal means</td></tr>
<tr><td>Main effect of IV₂ (authoritarianism)</td><td>levels₂ − 1</td><td>2</td><td>between the IV₂ marginal means</td></tr>
<tr><td>Interaction</td><td>df₁ × df₂</td><td>2</td><td>what the cell means do that the two main effects can't explain</td></tr>
<tr><td>Within (Residuals)</td><td>N − number of cells</td><td>39</td><td>scores around their own cell's mean: the shared noise</td></tr>
</tbody>
</table>

<div v-click class="border-l-4 border-indigo-400 pl-4 mt-4 text-[17px] leading-snug">

**APA:** A 2 (partner status) × 3 (authoritarianism) between-groups ANOVA showed that participants conformed more to high-status (*M* = 14.2) than low-status partners (*M* = 10.0), *F*(1, 39) = 9.75, *p* = .003. There was no main effect of authoritarianism, *F*(2, 39) = 0.28, *p* = .760, but there was a status × authoritarianism interaction, *F*(2, 39) = 4.19, *p* = .023: the effect of partner status appeared for low- and medium-authoritarian participants but not for high-authoritarian participants.

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: wrinkly fingers

:: left ::

Why do our fingers wrinkle in water? **20 people** moved small objects from one box to another as fast as they could, with **wrinkled or unwrinkled fingers** (after soaking in warm water, or not) and with **wet or dry objects**.

<img src="/images/lecture16/wrinkle_interaction.png" alt="Time to move objects: dry objects take about 94 seconds either way; wet objects take 118 seconds with unwrinkled fingers but 103 with wrinkled fingers" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-1">Data: Kareklas, Nettle, & Smulders (2013), <i>Biology Letters</i>; R package <code>Stat2Data</code> (<code>Wrinkle</code>).</div>

:: right ::

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

Which description fits the plot?

- **A)** Wrinkled fingers make people faster with every kind of object.
- **B)** Wet objects take longer, and that's all.
- **C)** No interaction: the lines are both straight.
- **D)** An interaction: wet objects slow people down, but much less when their fingers are wrinkled.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**D.** With dry objects, wrinkles make no difference (94 vs. 93 s). With wet ones, they save 15 seconds. Non-parallel lines = interaction, *F*(1, 19) = 45.2, *p* < .001. \(C): "parallel" is what matters, not "straight." The same people did all four conditions here, but main effects and interactions mean the same thing.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: John or Jennifer?

:: content ::

<div class="text-[15px] leading-snug">

**127 science professors** rated an application for a lab manager job. The application was identical, but was randomly labeled **"John"** or **"Jennifer."** Both male and female professors rated "John" as more competent than "Jennifer." Faculty gender made no difference.

</div>

<div class="flex justify-center items-start gap-4 mt-2">
  <div class="flex flex-col items-center w-1/3"><img src="/images/lecture15/anova_interaction_A.png" class="h-44 w-auto object-contain rounded-lg shadow-md"/><p class="mt-1 font-semibold">Plot A</p></div>
  <div class="flex flex-col items-center w-1/3"><img src="/images/lecture15/anova_interaction_B.png" class="h-44 w-auto object-contain rounded-lg shadow-md"/><p class="mt-1 font-semibold">Plot B</p></div>
  <div class="flex flex-col items-center w-1/3"><img src="/images/lecture15/anova_interaction_C.png" class="h-44 w-auto object-contain rounded-lg shadow-md"/><p class="mt-1 font-semibold">Plot C</p></div>
</div>

<Admonition title="Multiple choice 9" color="teal-light" width="100%">

Which plot matches the finding? &nbsp; **A)** Plot A &nbsp; **B)** Plot B &nbsp; **C)** Plot C &nbsp; **D)** None of them

</Admonition>

<div class="text-xs text-gray-500">Moss-Racusin, Dovidio, Brescoll, Graham, & Handelsman (2012), <i>PNAS</i>. The plots are illustrations, not the study's data.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# John or Jennifer: the answer

:: left ::

<Admonition title="Answer" color="green-light" width="100%">

**B.** Plot B shows a **main effect of applicant gender** (male applicant higher, whichever professor rated him) and no main effect of faculty gender and no interaction. Plot A shows a main effect of *faculty* gender. Plot C shows an interaction.

</Admonition>

The study's actual competence ratings (1–7 scale):

<table class="compact-table text-base">
<thead><tr><th></th><th>Male professors</th><th>Female professors</th></tr></thead>
<tbody>
<tr><td><b>"John"</b></td><td>4.01</td><td>4.10</td></tr>
<tr><td><b>"Jennifer"</b></td><td>3.33</td><td>3.32</td></tr>
</tbody>
</table>

:: right ::

<div class="text-[15px] leading-snug">

The 2 × 2 ANOVA found a significant effect of applicant gender (*p* < .01); faculty gender and the interaction were not significant (*p*s > .19). Follow-up: "Jennifer" was rated less competent, *t*(125) = 3.89, *p* < .001, *d* = 0.71.

</div>

<p v-click><StickyNote color="amber-light" title="Why it matters" width="100%">Random assignment of the name makes this causal: the same application got lower ratings with a woman's name on it, from women and men alike. That is a finding only an experiment could show.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Mixed designs and more IVs

:: left ::

A **mixed-design ANOVA** has at least one between-groups IV and at least one within-groups IV. The calculations are beyond this course; the logic is the same.

<Admonition title="Multiple choice 10" color="teal-light" width="100%">

Which study needs a mixed design?

1. Students in two sections of PS 211 take Exams 1, 2, and 3.
2. First-years and sophomores each rate three dining halls.

**A)** Only 1 &nbsp; **B)** Only 2 &nbsp; **C)** Both &nbsp; **D)** Neither

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Section and class year are between-groups (each person has one); exam and dining hall are within-groups (each person does all three).

</Admonition>

:: right ::

<p v-click>

More IVs → many more *F*s. A **three-way** ANOVA has 3 main effects, 3 two-way interactions, and 1 three-way interaction: **7 *F*s**. A **four-way** has **15**.

</p>

<p v-click>

Each extra IV multiplies the number of cells, so the number of participants you need grows fast, and so does the number of tests. Remember alpha inflation.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Which test? The story so far

:: content ::

<table class="compact-table text-sm">
<thead><tr><th>Test</th><th>IVs</th><th>Levels</th><th>Same people in every condition?</th><th>DV</th><th>Example from class</th></tr></thead>
<tbody>
<tr><td><i>z</i> test / one-sample <i>t</i></td><td>0</td><td>—</td><td>—</td><td>Numeric</td><td>Is 98.6°F the average body temperature?</td></tr>
<tr><td>Independent-samples <i>t</i></td><td>1</td><td>2</td><td>No</td><td>Numeric</td><td>Musicians vs. non-musicians' reaction times</td></tr>
<tr><td>Paired-samples <i>t</i></td><td>1</td><td>2</td><td>Yes</td><td>Numeric</td><td>Fandango vs. IMDb ratings of the same films</td></tr>
<tr><td>One-way between-groups ANOVA</td><td>1</td><td>3+</td><td>No</td><td>Numeric</td><td>Three ways to teach reading</td></tr>
<tr><td>Repeated-measures ANOVA</td><td>1</td><td>3+</td><td>Yes</td><td>Numeric</td><td>Caffeine, chocolate & tapping; music & time</td></tr>
<tr><td>Two-way (factorial) ANOVA</td><td>2</td><td>2+ each</td><td>No (yes, or mixed, in other designs)</td><td>Numeric</td><td>Partner status × authoritarianism</td></tr>
</tbody>
</table>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="60%">Every test in this table has a <b>categorical</b> IV. Tuesday: what to do when both variables are numeric (correlation).</StickyNote></p>

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
<div>

**Two-way (factorial) ANOVA** — two IVs, one numeric DV; three *F*s: two main effects and an interaction. Cells = levels₁ × levels₂.

</div>
<div>

**Main effect** — the effect of one IV averaged over the other, judged from **marginal means**.

</div>
<div>

**Interaction** — the effect of one IV depends on the level of the other; seen in **cell means** as non-parallel lines. **Mixed design**: one between- and one within-groups IV.

</div>
</div>

---
layout: cover
color: indigo-light
---

# That's all for today!
Tuesday: Correlation. No discussion or class during Thanksgiving week after Tuesday.
