---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Exam 1 Review
exportFilename: ps211_fall2026_exam1_review
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Exam 1 Review Session

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- ==Exam 1== is on **Tuesday, September 29** during our regular class time.
- The exam will be **in class**, multiple choice, and **no calculator** is needed.
- You can bring a handwritten, double-sided cheat sheet (you can write on the provided review sheet, both sides, or use your own blank paper).
- The exam will cover everything up to and including Lecture 6.
- You will *not* be tested on R code, but you should be able to interpret plots and output from R (e.g., a histogram, boxplot, or frequency table).
- Having your computer or phone out during the exam will result in a 0 for the exam.
- You will have the entire class period (75 minutes) to complete the exam.
- Please bring a pencil.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Plan for today

:: content ::

<div class="grid grid-cols-3 gap-4 mt-2">

<StickyNote color="indigo-light" title="Part 1: Designing studies" width="100%">
Lectures 1, 2, and 6<br><br>
Populations and samples, experiments vs. correlational studies, IVs and DVs, confounds, operational definitions, reliability and validity, sampling and random assignment
</StickyNote>

<StickyNote color="teal-light" title="Part 2: Describing data" width="100%">
Lectures 3, 4, and 5<br><br>
Histograms, skew, floor and ceiling effects, choosing graphs, central tendency, outliers, boxplots, <b>variability (range, IQR, variance, SD)</b>
</StickyNote>

<StickyNote color="amber-light" title="Part 3: From samples to inferences" width="100%">
Lecture 6<br><br>
Probability, null and research hypotheses, one- vs. two-tailed tests, rejecting the null, Type I and Type II errors
</StickyNote>

</div>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="34rem">The exam will ask you to <i>apply</i> these concepts to new scenarios, so that is what we will practice today. We will spend the most time on Part 2.</SpeechBubble></p>

---
layout: cover
color: indigo-light
---

# Part 1: Designing studies
### Lectures 1, 2, and 6

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Populations, samples, and two kinds of statistics

:: left ::

- **Population**: the entire group you want to draw conclusions about.
- **Sample**: the subset of the population you actually collect data from.
- **Descriptive statistics** organize, summarize, and communicate the data you have.
- **Inferential statistics** use sample data to draw conclusions about the population.

<p v-click><StickyNote color="green-light" title="Today's running example" width="100%">
Researchers studied 253 students at a U.S. college. Students took cognitive tests, completed surveys about their mood and habits, and kept a two-week sleep diary (Onyper et al., 2012). We will use their real data throughout today.
</StickyNote></p>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The 253 students slept an average of 7.97 hours per night. What kind of number is 7.97?

- **A)** An inferential statistic about all college students
- **B)** A descriptive statistic about the sample
- **C)** A population parameter
- **D)** An operational definition

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** It summarizes the 253 students who were measured. It would become part of an *inference* only if we used it to estimate the average sleep of all college students.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Types of variables: the short version

:: left ::

- **Qualitative** = differs in kind; **quantitative** = differs in amount.
- **Continuous** = any value in a range; **discrete** = only specific values.
- **Nominal**: named categories (species).
- **Ordinal**: ordered ranks; gaps may be unequal (1st, 2nd, 3rd).
- **Interval**: equal intervals, no true zero (°F).
- **Ratio**: equal intervals *and* a true zero (lever presses).

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

The sleep study classified each student as a "lark" (morning person), an "owl" (night person), or neither. What type of variable is this?

- **A)** Nominal
- **B)** Ordinal
- **C)** Interval
- **D)** Ratio

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** The categories have names but no order or quantity. Compare that with *number of classes missed*: quantitative, discrete, and ratio (0 means no classes missed).

</Admonition>

<p v-click>

==Some variables are ambiguous. Understanding a variable's properties matters more than agonizing over its label.==

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Experiments vs. correlational studies

:: left ::

**Experiment**
- The researcher *manipulates* the **independent variable (IV)**, which has two or more **levels**.
- The **dependent variable (DV)** is the outcome we expect the IV to affect.
- With random assignment, experiments support *causal* conclusions.

**Correlational study**
- Variables are observed as they naturally occur.
- Shows that variables are related. ==Cannot show causality.==

:: right ::

**Confounding variable**
- Varies along with the IV, so we cannot isolate the effect of the IV on the DV.
- Correlational studies are full of them. Poorly designed experiments can have them too.

<p v-click><StickyNote color="green-light" title="Remember" width="100%">
IV goes on the x-axis; DV goes on the y-axis. In non-experimental studies, the IV is observed or selected rather than manipulated (e.g., age).
</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: What can we conclude?

:: left ::

In the sleep study, the 34 students who pulled at least one all-nighter during the semester had a lower average GPA (3.18) than the 219 students who did not (3.25).

<Admonition title="Multiple choice" color="teal-light" width="100%">

A campus newspaper reports: "All-nighters hurt your grades." What is the biggest problem with this claim?

- **A)** GPA is not a valid measure.
- **B)** The groups are different sizes.
- **C)** It treats a correlation as a causal relation.
- **D)** The study used a sample instead of a population.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Nobody was assigned to pull an all-nighter. The researchers only observed who did.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which of these is a plausible *confound* in this study?

- **A)** Students with heavier course loads may both pull more all-nighters and earn lower GPAs.
- **B)** GPA was recorded to two decimal places.
- **C)** Some students slept more than 10 hours.
- **D)** The sample included 253 students.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**A.** A confound is a third variable that goes along with the IV (all-nighters) and could itself explain the DV (GPA). Procrastination, jobs, and stress are other candidates.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Designing an experiment

:: left ::

A researcher wants to know whether energy drinks speed up reaction times. Each participant is randomly assigned to drink either an energy drink or a caffeine-free placebo that tastes the same. Thirty minutes later, everyone completes a reaction-time task.

<Admonition title="Multiple choice" color="teal-light" width="100%">

What is the independent variable, and what are its levels?

- **A)** Reaction time; fast vs. slow
- **B)** Drink type; energy drink vs. placebo
- **C)** The participants; drinkers vs. non-drinkers
- **D)** Thirty minutes; before vs. after

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Drink type is what the researcher manipulates. Reaction time is the DV.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The researcher redesigns the study: every participant comes in twice, once for the energy drink and once for the placebo. The new design is:

- **A)** Between-subjects
- **B)** Within-subjects
- **C)** Correlational
- **D)** A case study

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** In a **within-subjects** design, each participant experiences *all* levels of the IV. In a **between-subjects** design (the original version), each participant experiences only one level.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Operational definitions: Needed to test hypotheses

:: content ::
- **Operational definitions**: Specify the observations or procedures used to measure or manipulate a variable.
  - Example: Happiness could be operationally defined as "self-reported happiness on a 1-10 scale" or "number of smiles in a 5-minute video."
- Abstract concepts are hard to operationalize, and any one definition captures only part of the construct.

<Admonition title="Question" color="teal-light" width="100%">How could you operationalize musical ability?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Musical ability could be operationalized as "score on a standardized music listening test" or "number of musical instruments played proficiently."

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">How could you operationalize stress?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Stress could be operationalized as "self-reported stress levels on a 1-10 scale" or "cortisol levels measured through saliva samples."

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Reliability and Validity

:: left ::

- **Reliability**: consistency across repeated measures.
  - A *reliable* scale gives the same weight each time.
- **Validity**: measuring what it's supposed to measure.
  - A *valid* scale gives the true weight.

**Reliability in practice**
- *Test-retest*: consistent scores over time.
- *Inter-rater*: consistent scores across raters.
- *Internal consistency*: items within a test agree.

:: right ::

**Can a measure be reliable but not valid?**

<p v-click>

- Yes! A broken scale that always reads 5 lbs too heavy is reliable (consistent) but not valid (not accurate).

</p>

**Can a measure be valid but not reliable?**

<p v-click>

- No! A measure can't capture what it's supposed to measure if it gives different results each time.
- A scale that gives different weights each time is neither reliable nor valid.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reliability and Validity: Practice

:: content ::

*A researcher wants to measure stress levels in college students. They develop a new questionnaire that asks about various stress-related symptoms. They administer the questionnaire to a group of students and find that the results are consistent when the same students take the test multiple times. However, when they compare the questionnaire results to physiological measures of stress (like cortisol levels), they find no correlation.*


<p v-click>

<Admonition title="Question" color="teal-light" width="100%">How would you describe the reliability and validity of this new questionnaire?</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The questionnaire is reliable because it produces consistent results when the same students take it multiple times. However, it is not valid because it does not correlate with physiological measures of stress, indicating that it may not be accurately measuring stress levels.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Reliability and Validity: More Practice

:: content ::

*You want to argue that SAT scores are not a reliable or valid measure of intelligence.*

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">What evidence would you use to support your argument?</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

You could point to studies showing that SAT scores can vary significantly for the same individual when taken multiple times (indicating low reliability). Additionally, you could cite research showing that SAT scores do not strongly correlate with other measures of intelligence, such as IQ tests or academic performance (indicating low validity).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Sampling and random assignment

:: left ::

**How do participants get *into* the study?**
- **Random sample:** Every member of the population has an equal chance of being selected.
    - More representative, but expensive and often impossible.
- **Convenience sample:** Uses participants who are readily available (e.g., volunteers, PS 101 students).
    - Easier and cheaper, but may limit **generalizability** (also called **external validity**).

:: right ::

**How do participants get into *conditions*?**
- **Random assignment:** Every participant has an equal chance of being in any condition (level of the IV).
    - Makes groups comparable at the start, which reduces confounds.
    - This is what allows causal conclusions, even with a convenience sample.

<p v-click><StickyNote color="green-light" title="Keep them straight" width="100%">
Random <b>sampling</b> is about who is in the study, so it affects generalizability. Random <b>assignment</b> is about who gets which condition, so it affects causal inference.
</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Sampling and assignment

:: left ::

<img src="/images/lecture5/participants_methods.png" alt="participant sample" class="mx-auto w-3/4" />

<Admonition title="Question" color="teal-light" width="100%">Is this a random or convenience sample? How do you know?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

This is a convenience sample. The participants volunteered to take part in the study, and they were recruited through flyers and online postings. This means they were not randomly selected from the general population.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

For the energy-drink experiment, the researcher recruits 80 volunteers from PS 101 and flips a coin to decide each person's drink. This study uses:

- **A)** Random sampling and random assignment
- **B)** Random sampling only
- **C)** Random assignment only
- **D)** Neither

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** Volunteers are a convenience sample, but the coin flip is random assignment. She can conclude the drink *caused* any difference in these participants. Whether it generalizes beyond PS 101 volunteers is a separate question.

</Admonition></p>

---
layout: cover
color: indigo-light
---

# Part 2: Describing data
### Lectures 3, 4, and 5

---
layout: top-title-two-cols
color: indigo-light
columns: is-7-5
align: lt-lt-lt
---

:: title ::
# Histograms

:: left ::
- A **frequency distribution** shows how often each value (or range of values) occurs. **Grouped frequency tables** sort continuous values into equal-width ==bins==.
- A **histogram** is a picture of a grouped frequency table: bins on the x-axis, ==frequency (count)== on the y-axis.
- A histogram *looks* like a bar graph, but **the y-axis always represents frequency or count**, not a separate variable.
- The binwidth changes what you see: too narrow is noisy; too wide hides the pattern.

:: right ::

<img src="/images/lecture3/bar_vs_hist.png" alt="bar vs hist" class="mx-auto w-full" />

==Histograms are for continuous variables, so the bars touch. For nominal or ordinal variables, use a bar plot of the counts (the bars don't touch).==

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Skew, floor effects, and ceiling effects

:: left ::

- The ends of a distribution are its =="tails."== Skew is named for the side with the **long tail**.
- **Positive skew**: long tail on the right.
    - Can indicate a **floor effect**: scores pile up at the *lowest* possible value.
- **Negative skew**: long tail on the left.
    - Can indicate a **ceiling effect**: scores pile up at the *highest* possible value.
- ==Not every skewed distribution has a floor or ceiling effect!==

:: right ::

<img src="/images/lecture3/skew.png" alt="skew" class="mx-auto w-full" />

<p v-click><StickyNote color="green-light" title="Why do we care?" width="100%">
Floor and ceiling effects mean the measure can't distinguish between people at that end of the scale.
</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Reading a histogram

:: left ::

<img src="/images/exam1_review/classes_missed_hist.png" alt="histogram of classes missed" class="mx-auto w-full" />

<div class="text-xs text-gray-500 mt-2">Data: Onyper et al. (2012), <i>Chronobiology International</i>; Lock5Data R package.</div>

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

What is the skew of this distribution?

- **A)** Positive
- **B)** Negative
- **C)** No skew
- **D)** Bimodal

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**A.** The long tail stretches to the right, toward the few students who missed 10 to 20 classes.

</Admonition>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">Is there a floor effect or a ceiling effect? What is the mode?</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

A floor effect: you can't miss fewer than 0 classes, and scores pile up there. The mode is 0 (the tallest bar).

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Understanding floor and ceiling effects

:: content ::

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">A teacher gives a very easy test to a class of students. Most students score between 90 and 100, with a few scoring slightly lower. What kind of skew would you expect in the distribution of test scores? Is there a floor or ceiling effect?</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The distribution of test scores would likely be negatively skewed, with a ceiling effect present. Most students are clustered at the high end of the scale (90-100).

</Admonition></p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">Why is this ceiling effect potentially problematic?</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The ceiling effect is problematic because it limits the ability to differentiate between students' performance at the high end of the scale.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Distributions and floor/ceiling effects (continued)

:: content ::

*Consider the following scenarios and determine whether the distribution of scores is likely to be positively skewed, negatively skewed, or normally distributed. Also, identify any potential floor or ceiling effects.*

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">A researcher asks participants to rate their satisfaction with a new product on a scale from 1 to 10. Most participants give ratings between 8 and 10, with very few giving lower ratings.</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The distribution is likely to be negatively skewed, with a ceiling effect present. Most participants are clustered at the high end of the scale (8-10).

</Admonition></p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">A researcher asks parents how many hours their children spend playing video games each week. Most parents report that their children play between 0 and 2 hours, with a few reporting higher amounts.</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The distribution is likely to be positively skewed, with a floor effect present. Most children are clustered at the low end of the scale (0-2 hours), but a few play significantly more.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: From frequency table to histogram

:: left ::
<Admonition title="Question" color="teal-light" width="100%">Does this grouped frequency table show a positive skew, negative skew, or normal distribution? Is there a floor or ceiling effect?</Admonition>

<img src="/images/exam1_review/freq_table.png" alt="grouped frequency table" class="mx-auto w-2/5" />



:: right ::

<Admonition title="Answer" color="green-light" width="100%" v-click>

The distribution is positively skewed, with a floor effect present. Most scores are clustered at the low end of the scale (0-8), but a few scores are significantly higher.

</Admonition>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">Does this histogram show the same data?</Admonition>

<img src="/images/lecture5/starbucks_fat_hist.png" alt="histogram" class="mx-auto w-1/2" />

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Yes.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Choosing (and reading) the right graph

:: left ::

- **Histogram**: distribution of one continuous variable.
- **Bar graph**: counts, or another measure such as a mean, for each *category*.
- **Scatter plot**: relation between two quantitative variables.
- **Line graph**: change over time.
- **Box plot**: median, quartiles, and outliers; good for comparing groups.

<p v-click><StickyNote color="amber-light" title="Axes matter!" width="100%">
Always check the axes. A y-axis that covers a huge range can hide real differences, and one that is zoomed in can exaggerate tiny ones.
</StickyNote></p>

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

You want to see whether students in the sleep study who have more drinks per week tend to have lower GPAs. Which graph is most useful?

- **A)** Histogram of GPA
- **B)** Bar plot of chronotype counts
- **C)** Scatter plot of drinks per week and GPA
- **D)** Grouped frequency table of drinks per week

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Two quantitative variables, and we care about the relation between them. Every other option shows only one variable.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---


:: title ::
# Mean, median, and mode

:: content ::

**Mean:** The arithmetic average. Add up all the scores, then divide by the number of scores.

$$M = \frac{\sum_{i=1}^{N} X_i}{N}$$

- $\sum_{i=1}^{N}$ means "add up the values, starting with the first score ($i = 1$) and ending with the last score ($N$)."
- The mean of a *sample* is $M$ (or $\bar{X}$). The mean of a *population* is $\mu$. ==Latin letters for sample statistics; Greek letters for population parameters.==

**Median:** The middle score once the scores are in order (the 50th percentile). With an even number of scores, take the mean of the two middle scores.

**Mode:** The most common score. Distributions can be unimodal, bimodal, or multimodal.

---
layout: top-title
color: indigo-light
---

:: title ::
# Comparing Mean, Median, and Mode

:: content ::
- In a normal distribution, the mean, median, and mode are equal!  
- In a negatively skewed distribution, the mean is less than the median, which is less than the mode.  
- In a positively skewed distribution, the mode is less than the median, which is less than the mean.  

<img src="/images/lecture4/mean_med_mode.png" alt="mean med mode" class="mx-auto w-3/4" />


---
layout: top-title
color: indigo-light
align: lt 
---

:: title ::
# Outliers

:: content ::
- Outliers are extreme values that differ greatly from the rest of the data.  
- Outliers can distort the mean, making it less representative of the dataset.  
- The median is less affected by outliers and can be a better measure of central tendency in skewed data.  

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="30rem">The mean gets pulled toward the tail. That is why news stories report the <i>median</i> household income: a few billionaires drag the mean way up.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Central tendency

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Four students in the sleep study had 2, 10, 3, and 5 drinks last week. What is the median?

- **A)** 6.5
- **B)** 5
- **C)** 4
- **D)** There is no median with an even number of scores.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** Order the scores first: 2, 3, 5, 10. The two middle scores are 3 and 5, and their mean is 4. (A is what you get if you forget to put the scores in order; 5 is the mean.)

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

In the classes-missed histogram, the median is 1 class. Which is the best estimate of the mean?

- **A)** 0.5 classes
- **B)** 1 class
- **C)** 2.2 classes
- **D)** 10 classes

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** The distribution is positively skewed, so the students in the long right tail pull the mean *above* the median. But most students missed 0 to 3 classes, so 10 is far too high.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Visualizing outliers

:: left ::
<img src="/images/lecture4/exam_scores_barplot.png" alt="outlier bar" class="mx-auto w-3/4" />

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Which exam was harder?</Admonition>
</p>

:: right ::

<p v-click>
<img src="/images/lecture4/exam_scores_boxplot.png" alt="outlier box" class="mx-auto w-3/4" />
</p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Which exam was harder?</Admonition>
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Visualizing outliers (continued)

:: content ::
<img src="/images/lecture4/exam_scores_histogram.png" alt="outlier histogram" class="mx-auto w-1/2" />

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Which exam was harder?</Admonition>
</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Reading a boxplot

:: left ::

<img src="/images/exam1_review/allnighter_boxplot.png" alt="boxplots of average sleep by all-nighter group" class="mx-auto w-5/6" />

<div class="text-xs text-gray-500 mt-2">Data: Onyper et al. (2012), <i>Chronobiology International</i>; Lock5Data R package.</div>

:: right ::

- Line inside the box = **median**. Height of the box (Q1 to Q3) = **IQR**. Points beyond the whiskers = potential **outliers**.

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which group has the higher median, and which has the greater IQR?

- **A)** Higher median: A. Greater IQR: A.
- **B)** Higher median: A. Greater IQR: B.
- **C)** Higher median: B. Greater IQR: A.
- **D)** Higher median: B. Greater IQR: B.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Group A's median line is higher (8.1 vs. 7.4 hours). Group B's *box* is taller (IQR of 1.5 vs. 1.2 hours). Judge the IQR from the box, not the whiskers or outlier points.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variability: Why we care

:: content ::

- Almost everything we measure varies. The spread of scores comes from three sources mixed together: ==differences between people==, ==differences within a person== from moment to moment, and ==measurement noise==.
- Science is the study of variability: an experiment is an attempt to explain some of the variability in a **dependent variable** using an **independent variable**.
- A mean without a measure of variability can be misleading. Two groups can share a mean and look nothing alike.

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="32rem">You can't explain a spread you can't measure. That is why we need a number that says <i>how much</i> scores vary.</SpeechBubble></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Sources of variability

:: content ::

In the sleep study, average sleep ranged from about 5 to almost 11 hours per night.

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which of these is an example of variability *within* a person?

- **A)** Some students are habitually short sleepers and others are long sleepers.
- **B)** Students misremember what time they fell asleep when filling in the diary.
- **C)** The same student sleeps 6 hours before a midterm and 9 hours the following night.
- **D)** Students who pulled an all-nighter slept less on average.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**C.** A is a difference between people, B is measurement noise, and D is a between-group difference that *explains* some of the spread.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Measuring variability

:: content ::

<div class="grid grid-cols-2 gap-4 mt-2">

<StickyNote color="indigo-light" title="Range" width="100%">
Highest score minus lowest score. Depends on only two scores, so it is the measure <b>most distorted by outliers</b>.
</StickyNote>

<StickyNote color="teal-light" title="Interquartile range (IQR)" width="100%">
Q3 minus Q1: the spread of the middle 50% of the data. Q1 and Q3 are the medians of the lower and upper halves. Barely affected by outliers.
</StickyNote>

<StickyNote color="amber-light" title="Variance" width="100%">
The average <i>squared</i> deviation from the mean. Uses every score. Its units are squared (hours²).
</StickyNote>

<StickyNote color="green-light" title="Standard deviation (SD)" width="100%">
The square root of the variance: the <b>typical distance between a score and the mean</b>, in the original units (hours).
</StickyNote>

</div>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="32rem">Why square the deviations? Because deviations from the mean always add up to zero. Squaring makes them all positive before we average them.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Variance and SD: The recipe

:: left ::

1. Find the mean.
2. Subtract the mean from each score (the **deviations**).
3. Square each deviation.
4. Add up the squared deviations.
5. Divide by $N$ (population) or by $N - 1$ (sample). That is the **variance**.
6. Take the square root. That is the **SD**.

<p v-click><StickyNote color="amber-light" title="N or N − 1?" width="100%">
If your data are a <b>sample</b> that you are using to estimate the population, divide by N − 1. (We'll see exactly why in Lecture 8.)
</StickyNote></p>

:: right ::

**Population**

$$\sigma^2 = \frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N} \qquad \sigma = \sqrt{\sigma^2}$$

**Sample**

$$s^2 = \frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1} \qquad s = \sqrt{s^2}$$

<div class="grid grid-cols-3 gap-x-4 leading-snug mt-4" style="max-width:22rem">
<div></div><div><b>Sample</b></div><div><b>Population</b></div>
<div>Mean</div><div><i>M</i></div><div><i>μ</i></div>
<div>Variance</div><div><i>s</i>²</div><div><i>σ</i>²</div>
<div>SD</div><div><i>s</i></div><div><i>σ</i></div>
</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Variance and SD by hand

:: left ::

<Admonition title="Question" color="teal-light" width="100%">A sample of five students reports how many coffees they bought last week: <b>1, 3, 5, 7, 9</b>. Find the sample variance and the sample SD.</Admonition>

<p v-click>

**Steps 1 and 2: Mean and deviations.**

$$M = \frac{1+3+5+7+9}{5} = \frac{25}{5} = 5$$

Deviations: −4, −2, 0, +2, +4 (check: they sum to 0)

</p>

:: right ::

<p v-click>

**Steps 3 and 4: Square and sum.**

$$16 + 4 + 0 + 4 + 16 = 40$$

</p>

<p v-click>

**Step 5: Divide by N − 1.**

$$s^2 = \frac{40}{5-1} = 10 \text{ coffees}^2$$

</p>

<p v-click>

**Step 6: Square root.**

$$s = \sqrt{10} \approx 3.2 \text{ coffees}$$

</p>

<p v-click>

==A typical student's coffee count was about 3 coffees away from the mean of 5.==

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: What happens to the SD?

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Green Line construction adds exactly 10 minutes to every student's commute. What happens to the mean and SD of commute times?

- **A)** Both increase by 10 minutes.
- **B)** The mean increases by 10; the SD stays the same.
- **C)** The mean stays the same; the SD increases by 10.
- **D)** Neither changes.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Every score moves up by 10, and so does the mean, so every *deviation* is exactly what it was. Spread is about distances from the mean, not where the scores sit.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

Sleep in the study has SD = 0.96 hours. If we convert every score from hours to minutes (multiply by 60), what happens?

- **A)** The SD and variance are both multiplied by 60.
- **B)** The SD is multiplied by 60; the variance is multiplied by 3,600.
- **C)** Neither changes, because the data are the same.
- **D)** The SD is multiplied by 3,600.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** Every deviation becomes 60 times as large, so the SD does too (57.6 minutes). Every *squared* deviation becomes 60² = 3,600 times as large, and so does the variance.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Estimating the SD by eye

:: left ::

<img src="/images/exam1_review/avg_sleep_hist.png" alt="histogram of average sleep" class="mx-auto w-full" />

<div class="text-xs text-gray-500 mt-2">Data: Onyper et al. (2012), <i>Chronobiology International</i>; Lock5Data R package.</div>

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which is the best estimate of the standard deviation of average sleep?

- **A)** 0.1 hours
- **B)** 1 hour
- **C)** 4 hours
- **D)** 1 hour²

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** The SD is the *typical* distance between a score and the mean. Most students are within an hour or so of 8 hours. 0.1 is far too small, and 4 hours is closer to the distance of the single most extreme student. D has the wrong units: hours² are the units of the variance.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variance in the real world

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Imagine you have the choice between two summer jobs: You can be a lifeguard or you can be a tour guide. Both jobs pay, on average, $15/hour. However, the lifeguard job has a standard deviation of $1/hour, while the tour guide job has a standard deviation of $10/hour. Which job would you choose? Why?</Admonition>


<p v-click>

<Admonition title="Question" color="teal-light" width="100%">Imagine that you are a boating instructor and you need to order lifejackets for a group of 100 people. You know their average weight is 150 lbs. The options for lifejacket sizes range from XXS to XXL, which correspond to different weights. How would knowing the standard deviation of their weights help you decide how many of each lifejacket size to order?</Admonition>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability: Practice

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Which distribution likely has a greater standard deviation?</Admonition>

<div class="mt-6 flex justify-center space-x-6">
  <img src="/images/lecture4/bimodal.png" alt="bimodal" class="w-1/3" />
  <img src="/images/lecture4/unimodal.png" alt="unimodal" class="w-1/3" />
</div>


<Admonition title="Answer" color="green-light" width="100%" v-click>

The "Violet" distribution likely has a greater standard deviation because its scores are more spread out from the mean.

</Admonition>

---
layout: cover
color: indigo-light
---

# Part 3: From samples to inferences
### Lecture 6

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Probability

:: left ::

- **Probability** = the likelihood that a specific outcome will occur, out of all possible outcomes. Ranges from 0 (impossible) to 1 (certain).
- **Trial**: each repetition of a procedure (a coin flip). **Outcome**: the result of a trial. **Success**: the outcome of interest (heads).
- **Independent trials**: one trial's outcome does not affect another's. Streaks still happen!
- Our intuitions about probability are bad (e.g., the gambler's fallacy, the birthday paradox). That is why we need formal hypothesis tests.

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

A fair coin lands on heads five times in a row. What is the probability of heads on the sixth flip?

- **A)** Less than 0.5, because tails is "due"
- **B)** 0.5
- **C)** More than 0.5, because heads is "hot"
- **D)** It cannot be determined.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Coin flips are independent trials, so the coin has no memory. Option A is the gambler's fallacy.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Hypothesis Testing

:: content ::
- In psychological research, we define two hypotheses:
    - **Null Hypothesis (H₀):** There is no difference.
        - The null hypothesis is a statement that postulates that there is no difference between populations or that the difference is in a direction opposite of that anticipated by the researcher.
        - Any observed difference is due to random chance or sampling error.


    - **Research Hypothesis (H₁):** There is a difference.
        - There is a difference between populations or sometimes, more specifically, that there is a difference in a certain direction, positive or negative; also called an alternative hypothesis.
        - An observed difference reflects a true effect in the population.
    
- ==Goal: Use data to test which is more plausible.==

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Directions and decisions

:: left ::

**Hypothesis directions**
- A ==directional== research hypothesis predicts which way the difference goes. It is tested with a **one-tailed test**.
- A ==non-directional== research hypothesis predicts a difference in either direction. It is tested with a **two-tailed test**.
- One-tailed tests have more statistical power but can miss effects in the opposite direction.

:: right ::

**The decision**
- If the data are very unlikely under H₀, we **reject H₀** in favor of H₁.
- If the data are not unlikely under H₀, we **fail to reject H₀**.
- We never "accept" H₀, because we can't prove that it is true.

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">
Absence of evidence is not evidence of absence! "We did not find evidence of a difference" is not the same as "there is no difference."
</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Hypotheses and decisions

:: left ::

A researcher predicts that students who spend 15 minutes with a therapy dog before a final exam will report *lower* stress than students who spend 15 minutes waiting quietly.

<Admonition title="Multiple choice" color="teal-light" width="100%">

What is the null hypothesis?

- **A)** Therapy-dog students will report lower stress.
- **B)** There will be no difference in stress between the two groups.
- **C)** Everyone will report zero stress.
- **D)** The two groups will differ, in either direction.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** A is her (directional) research hypothesis, which calls for a one-tailed test. D is a non-directional research hypothesis.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

The difference between her groups turns out to be small and not unlikely under H₀. Which conclusion is worded correctly?

- **A)** "Therapy dogs have no effect on stress."
- **B)** "We accept the null hypothesis."
- **C)** "We did not find evidence that therapy dogs reduce stress."
- **D)** "We proved the research hypothesis false."

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** She fails to reject H₀. The other three options all claim she has shown the null to be true, which a hypothesis test cannot do.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Two ways to be wrong: Type I and Type II errors

:: left ::

- **Type I error:** Rejecting H₀ when it is true (false positive).
- **Type II error:** Failing to reject H₀ when it is false (false negative).
- Both errors have consequences.

<img src="/images/lecture5/errors.png" alt="type 1 type 2" class="mx-auto w-3/5" />

:: right ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

In truth, therapy dogs *do* reduce stress. But the researcher's study fails to reject the null hypothesis. What has happened?

- **A)** A Type I error
- **B)** A Type II error
- **C)** A confound
- **D)** No error; the conclusion is correct

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** A real effect was missed: a false negative. If instead there were truly no effect and she had rejected H₀, that would be a Type I error (a false positive).

</Admonition>

---
layout: cover
color: indigo-light
---

# That's all for today!
Good luck on Exam 1 on Tuesday!
