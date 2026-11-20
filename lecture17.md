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
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">First, finish ANOVA with two IVs at once. Then: what if both variables are numeric, with no groups at all?</SpeechBubble>
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

Finishing Lecture 16: what if we have **two** independent variables?
# Two-Way ANOVA

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

**45 participants** made judgments on an ambiguous perceptual task alongside a partner. On 40 critical trials, the partner's answer (scripted by the experimenters) disagreed with theirs. DV: how often they **changed their answer to match the partner**.

- **IV₁: partner's status**, randomly assigned. Before the task, participants learned who their partner was: a **physician** (high status) or a **postal clerk** (low status). Only this label differed; the disagreements were the same.
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

<p v-click><StickyNote color="green-light" title="Why would status matter?" width="100%">The task is ambiguous, so the partner's job is a cue to who is more likely to be right. The authors predicted that <b>low</b>-authoritarian people would be the most sensitive to that cue.</StickyNote></p>

<p v-click><StickyNote color="amber-light" title="Only one IV was manipulated" width="100%">Partner status was randomly assigned, so its effect is causal. Authoritarianism was measured, so differences between those groups are observational. Many real factorial studies mix the two.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One study, three questions

:: content ::

<div class="text-[15px] leading-snug">

A two-way ANOVA answers **three separate questions** about the same 45 people, with **three separate *F* tests**:

</div>

<div class="grid grid-cols-3 gap-3 mt-1 text-[14px] leading-snug">
<div v-click>
<img src="/images/lecture16/tw_q1_status.png" alt="Mean conforming responses: high-status partner 14.2, low-status partner 10.0" class="w-full"/>

**1. Main effect of partner status.** Ignoring authoritarianism, do people conform more to a physician than to a postal clerk?

</div>
<div v-click>
<img src="/images/lecture16/tw_q2_auth.png" alt="Mean conforming responses by authoritarianism: low 11.7, medium 12.4, high 12.3" class="w-full"/>

**2. Main effect of authoritarianism.** Ignoring the partner, do low-, medium-, and high-authoritarian people conform differently?

</div>
<div v-click>
<img src="/images/lecture16/tw_q3_cells.png" alt="Mean conforming responses for all six combinations of partner status and authoritarianism" class="w-full"/>

**3. Interaction.** Does the effect of partner status **depend on** the person's authoritarianism?

</div>
</div>
---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The design: 2 × 3 = 6 cells

:: left ::

<div class="text-[15px] leading-snug">

A **two-way ANOVA** has two categorical IVs and one numeric DV. Any design with 2+ IVs is a **factorial design**.

- Partner status has **2** levels; authoritarianism has **3**. That's a **2 × 3** design.
- Each combination of levels is a **cell**: 2 × 3 = **6 cells**, each with its own group of people.

</div>

<table class="compact-table text-sm mt-2">
<thead><tr><th>Partner</th><th>Low auth.</th><th>Medium</th><th>High auth.</th></tr></thead>
<tbody>
<tr><td><b>High status</b></td><td>cell 1 (n = 5)</td><td>cell 2 (n = 11)</td><td>cell 3 (n = 7)</td></tr>
<tr><td><b>Low status</b></td><td>cell 4 (n = 10)</td><td>cell 5 (n = 4)</td><td>cell 6 (n = 8)</td></tr>
</tbody>
</table>

:: right ::

<p v-click><Admonition title="Question" color="teal-light" width="100%">

How many cells in a 2 × 2 design? A 3 × 4?

</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

4 and 12: multiply the numbers of levels.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Why not two one-way ANOVAs?" width="100%">One on status and one on authoritarianism would answer questions 1 and 2, but never question 3. Here, question 3 is the interesting finding: status mattered for some people and not others.</StickyNote></p>
---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Three *F* tests, one shared denominator

:: content ::

<div class="text-[15px] leading-snug">

Each question gets its own H₀ and its own *F*. Same logic as Lecture 15: **signal ÷ noise**.

</div>

<table class="compact-table text-sm mt-1">
<thead><tr><th>Test</th><th>H₀ in words</th><th>Signal: which means it compares</th><th><i>F</i> =</th></tr></thead>
<tbody>
<tr v-click><td><b>1. Partner status</b></td><td>Conformity is the same with either partner, on average</td><td>the 2 status <b>marginal means</b> (14.2 vs. 10.0)</td><td>MS<sub>status</sub> / MS<sub>Within</sub></td></tr>
<tr v-click><td><b>2. Authoritarianism</b></td><td>Low, medium, and high conform the same, on average</td><td>the 3 authoritarianism <b>marginal means</b></td><td>MS<sub>auth</sub> / MS<sub>Within</sub></td></tr>
<tr v-click><td><b>3. Interaction</b></td><td>The effect of status is the same at every level of authoritarianism</td><td>the 6 <b>cell means</b>, beyond what the two main effects predict</td><td>MS<sub>status×auth</sub> / MS<sub>Within</sub></td></tr>
</tbody>
</table>

<p v-click><StickyNote color="amber-light" title="The shared denominator" width="85%">MS<sub>Within</sub> is the noise: how far each person's score is from <b>their own cell's mean</b>, pooled over all 6 cells. It doesn't depend on which question you're asking, so all three <i>F</i>s divide by the same number. In R's output: three rows with an <i>F</i>, plus <code>Residuals</code>.</StickyNote></p>
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

The effect of status (high − low) at each level of authoritarianism:

| Low auth. | Medium | High auth. |
|:---:|:---:|:---:|
| 17.4 − 8.9 = **+8.5** | 14.3 − 7.2 = **+7.1** | 11.9 − 12.6 = **−0.7** |

With no interaction, these three differences would be about equal. A **difference of differences** is what the interaction tests.

</div>

<p v-click><StickyNote color="amber-light" title="Reading the plot" width="100%"><b>Parallel lines</b> → the effect of one IV is the same at every level of the other: no interaction. <b>Lines that converge, diverge, or cross</b> → an interaction. Always plot the cell means; interactions are hard to see in a table of numbers.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reading main effects and interactions from a plot

:: content ::

<div class="text-[15px] leading-snug">

A made-up study: does **caffeine** (x-axis) or **sleep** (separate lines) affect exam scores? Ask three questions:

</div>

<div class="grid grid-cols-3 gap-3 text-[14px] leading-snug mt-1">
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Main effect of sleep (the lines):</b> is one line higher than the other <i>on average</i>? Compare the midpoints of the two lines.</div>
<div class="border-2 border-gray-300 rounded-lg p-2"><b>Main effect of caffeine (the x-axis):</b> average the two points above "No caffeine," then above "Caffeine." Do those averages differ?</div>
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-2"><b>Interaction:</b> are the lines <b>parallel</b>? If not, the effect of caffeine depends on how much you slept.</div>
</div>

<img v-click src="/images/lecture16/int_read.png" alt="Four example plots of exam scores: main effect of sleep only, main effect of caffeine only, both main effects with parallel lines, and an interaction only where the lines cross" class="w-5/6 mx-auto mt-1"/>

<div v-click class="text-[14px] text-gray-600">Each of the three can be present or absent independently. A plot shows the pattern; the ANOVA says whether it is bigger than chance.</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: what do you see?

:: content ::

<img src="/images/lecture16/int_practice.png" alt="Four practice plots of cell means for a 2 by 2 design" class="w-4/5 mx-auto"/>

<div class="grid grid-cols-2 gap-6 mt-1">
<div>

<Admonition title="Question" color="teal-light" width="100%">

Same made-up study. For each plot: is there a main effect of sleep? Of caffeine? An interaction?

</Admonition>

<p v-click="2"><StickyNote color="amber-light" title="The tricky ones" width="100%">Plot 3: the averages above "No caffeine" and "Caffeine" are both 80, so no main effect of caffeine, even though both lines slope. Plot 4: everything averages out, yet caffeine matters a lot, in opposite directions for rested and sleep-deprived students.</StickyNote></p>

</div>
<div v-click="1">

<table class="compact-table text-sm">
<thead><tr><th></th><th>Sleep</th><th>Caffeine</th><th>Interaction</th></tr></thead>
<tbody>
<tr><td>Plot 1</td><td>Yes</td><td>Yes</td><td>Yes</td></tr>
<tr><td>Plot 2</td><td>Yes</td><td>Yes</td><td>No</td></tr>
<tr><td>Plot 3</td><td>Yes</td><td>No</td><td>Yes</td></tr>
<tr><td>Plot 4</td><td>No</td><td>No</td><td>Yes</td></tr>
</tbody>
</table>

</div>
</div>
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
<tr><td>Main effect of partner status</td><td>2 levels − 1</td><td>1</td><td>between the 2 status marginal means</td></tr>
<tr><td>Main effect of authoritarianism</td><td>3 levels − 1</td><td>2</td><td>between the 3 authoritarianism marginal means</td></tr>
<tr><td>Interaction</td><td>1 × 2 (multiply the two dfs above)</td><td>2</td><td>what the cell means do that the two main effects can't explain</td></tr>
<tr><td>Within (Residuals)</td><td>45 people − 6 cells</td><td>39</td><td>scores around their own cell's mean: the shared noise</td></tr>
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

<Admonition title="Multiple choice 3" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 4" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 5" color="teal-light" width="100%">

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

<p v-click><StickyNote color="green-light" title="Coming attractions" width="60%">Every test in this table has a <b>categorical</b> IV. Next: what to do when both variables are numeric (correlation).</StickyNote></p>

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

<div class="flex flex-col items-start">
<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">

The statistic doesn't decide whether you can claim causation: the **design** does. A correlation from a randomized experiment can be causal; a *t* test on groups that already existed (owls vs. larks) cannot.

</SpeechBubble>
<div class="ml-2 -mt-1"><IceCream :size="60" mood="happy" color="#FDA7DC" /></div>
</div>

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

Students who drink more tend to have somewhat **lower** GPAs, but there is a lot of scatter: many heavy drinkers have high GPAs. A **weak negative** relationship.

</Admonition></p>

<p v-click><StickyNote color="amber-light" title="Up next" width="100%">"Weak" and "somewhat" are judgment calls. How do we actually <b>quantify</b> the strength of this relationship?</StickyNote></p>

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

<Admonition title="Multiple choice 6" color="teal-light" width="100%">

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

<Admonition title="Question" color="teal-light" width="100%">

Which panel shows the **strongest** correlation? Which shows the **weakest**? Guess *r* for each panel.

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

**Strongest: panel B.** Penguin flipper length and body mass, *r* = .87: two measurements of the same body. **Weakest: panel A**, *r* = −.06. Behavioral correlations look more like C–F.

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
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Building *r*, steps 1–3: do X and Y move together?

:: left ::

<div class="text-[15px] leading-snug">

Eight students from our sample. The dashed lines are the two means.

<div v-click="1">

**Step 1: deviations.** For one student: how far from the mean on X, and on Y?
$$X - M_X \qquad Y - M_Y$$

</div>
<div v-click="2">

**Step 2: multiply** the two deviations: the area of a rectangle.
$$(X - M_X)(Y - M_Y)$$
Same side of both means → positive (teal). Opposite sides → negative (pink).

</div>
<div v-click="3">

**Step 3: add up** everyone's products.
$$\sum (X - M_X)(Y - M_Y)$$
More pink area than teal → a negative total.

</div>
</div>

:: right ::

<v-switch>
<template #0><img src="/images/lecture17/r_step0.png" alt="Eight students' GPA against drinks per week, with dashed lines at the two means" class="w-full"/></template>
<template #1><img src="/images/lecture17/r_step1.png" alt="One student's deviation from the mean on drinks (plus 5.88) and on GPA (minus 0.93), drawn as arrows" class="w-full"/></template>
<template #2><img src="/images/lecture17/r_step2.png" alt="The same student's two deviations multiplied, drawn as a pink rectangle with area minus 5.49" class="w-full"/></template>
<template #3><img src="/images/lecture17/r_step3.png" alt="Rectangles for all eight students, mostly pink; the products add up to minus 6.96" class="w-full"/></template>
</v-switch>
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
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Building *r*, steps 4–5: put it on a −1 to +1 scale

:: left ::

<div class="text-[15px] leading-snug">

The sum of products (−6.96) depends on the **units** (drinks, GPA points) and on **how many people** there are, so it can't say how strong the relationship is.

<div v-click="1">

**Step 4: how much X and Y vary on their own.** The familiar sums of squares:
$$SS_X = \sum (X - M_X)^2 \quad SS_Y = \sum (Y - M_Y)^2$$

</div>
<div v-click="2">

**Step 5: divide.** Movement together, relative to movement at all:
$$r = \frac{\sum(X - M_X)(Y - M_Y)}{\sqrt{SS_X \cdot SS_Y}}$$
The units cancel, so *r* always lands between −1 and +1.

</div>
</div>

<p v-click="3"><StickyNote color="amber-light" title="Signal ÷ noise, once more" width="100%">You will not compute <i>r</i> by hand. Know what each part does.</StickyNote></p>

:: right ::

<v-switch>
<template #0-1><img src="/images/lecture17/r_step3.png" alt="Rectangles for all eight students; the products add up to minus 6.96" class="w-full"/></template>
<template #1><img src="/images/lecture17/r_step4.png" alt="Each student's deviation on drinks alone (SS X = 106.9) and on GPA alone (SS Y = 1.54)" class="w-full"/></template>
<template #2-4><img src="/images/lecture17/r_step5.png" alt="The eight students with a best-fit line; r = minus 6.96 divided by the square root of 106.9 times 1.54, which is minus 0.54" class="w-full"/></template>
</v-switch>
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

<Admonition title="Multiple choice 7" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 8" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 9" color="teal-light" width="100%">

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

<Admonition title="Multiple choice 10" color="teal-light" width="100%">

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
