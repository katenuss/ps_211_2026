---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 5
exportFilename: ps211_fall2026_lecture5
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 5: Variability

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- ==Exam 1== is scheduled for **Tuesday, September 29** and covers Lectures 1 - 6. Review session is **Thursday, September 24**.
- If you have exam accommodations, Rola or I have messaged you on Slack to confirm. If you have not heard from us yet, that means we do not have a letter for you, and expect you to take the exam in class. 

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Almost everything we measure varies

:: content ::

<img src="/images/lecture5/many_things_vary.png" alt="four histograms: heights, reaction times, temperatures, sleep" class="mx-auto w-3/5" />

<p v-click>

- Heights, reaction times, temperatures, hours of sleep: measure any of them across people (or days) and you get a ==spread of values==, never a single number.
- If everything we measured came out the same every time, there would be nothing to study.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Even the *same* thing, measured again, varies

:: left ::

<img src="/images/lecture5/same_person_rt.png" alt="one person's reaction time across 40 trials" class="mx-auto w-full" />

:: right ::

- This is **one person** pressing a button when they hear a beep, 40 times in a row.
- Same person, same task, same button — and the reaction times still bounce around (roughly 200 to 420 ms).

<p v-click>

<StickyNote color="amber-light" title="Try it at home" width="100%">
Step on a bathroom scale three times in a row. You will not always get the same number. Variability is everywhere, even when nothing "real" has changed.
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where does variability come from?

:: content ::

Any time we see a spread of values, there are three broad sources mixed together:

<div class="grid grid-cols-3 gap-4 mt-2">
<StickyNote color="indigo-light" title="Differences between people" width="100%">
Some people really are taller, faster, or more anxious than others. These are stable, real differences.
</StickyNote>
<StickyNote color="teal-light" title="Differences within a person" width="100%">
The same person changes from day to day and moment to moment: how much they slept, whether they were paying attention.
</StickyNote>
<StickyNote color="amber-light" title="Measurement noise" width="100%">
The scale, the timer, the survey question — no measurement is perfect, so some spread is just error in how we measured.
</StickyNote>
</div>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">We ask 100 students how many hours they slept last night and get values from 4 to 10. Which of these three sources could be contributing?</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

All three. Some students are habitually short sleepers (between-person), everyone's sleep varies night to night (within-person), and people's memory of when they fell asleep is imperfect (measurement noise).

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Science is the study of variability

:: left ::

- Almost every research question is really a question about ==why something varies==:
  - Why do some people sleep 5 hours and others 9?
  - Why do some children learn to read faster than others?
  - Why does the same person remember a word list better on some days than others?
- Answering a question like this means finding the **sources** of the spread.

:: right ::

<img src="/images/lecture5/sleep_all.png" alt="histogram of sleep hours" class="mx-auto w-full" />

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">
Every bar in this histogram is a person. What makes the people on the left different from the people on the right?
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Explaining some of the variability

:: left ::

<img src="/images/lecture5/sleep_by_caffeine.png" alt="sleep histogram split by caffeine" class="mx-auto w-full" />

- Same histogram, now colored by whether each student had caffeine after 4 p.m.

:: right ::

<p v-click>

- Caffeine drinkers cluster lower, the others higher: ==caffeine may explain part of the spread.==
- In later lectures, we will learn how to use *statistical tests* to determine if we can say that caffeine explains a *significant* part of the spread, or if this pattern may have arisen just by chance.

</p>

<p v-click>

- Also, within each group, sleep still varies a lot!
- There's leftover spread that we *haven't* explained yet.

</p>

<p v-click>

<StickyNote color="indigo-light" title="The key idea" width="100%">
Finding a source of variability means showing that a variable accounts for some of the spread.
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# You already did this in Lecture 2

:: content ::

<Admonition title="Question" color="teal-light" width="100%">In Lecture 2, you all guessed the height of the world's tallest tree, and your guesses were all over the place. What was one source of that variability?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Which anchor you saw first: 1,200 feet or 180 feet. People who saw the high anchor guessed higher, on average. The anchor was our **independent variable**, and it explained *some* of the spread in your guesses.

</Admonition>

<p v-click>

- The rest of the spread came from everything we didn't manipulate: prior knowledge about trees, how confident people felt, random guessing.
- ==An experiment is an attempt to explain some of the variability in a **dependent variable** using an **independent variable.**== This is the logic behind nearly every statistical test you will learn this semester.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# But first, we have to *describe* variability

:: content ::

- You can't explain a spread you can't measure. Before asking *why* scores vary, we need a number that says *how much* they vary.
- That number is what today is about.

<p v-click>

<StickyNote color="green-light" title="The roadmap" width="100%">
<b>Today:</b> describe variability with a single number (range, variance, standard deviation).<br>
<br>
<b>Rest of the semester:</b> explain variability by comparing the spread an independent variable accounts for versus the spread it does not account for. How much variability does an independent variable explain? 

<br> T-tests, ANOVA, and regression are all different ways of addressing that question.
</StickyNote>

</p>

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem" v-click>If today's numbers feel abstract, remember what they're for. They tell us "how much" spread there is in our measurements in the first place! </SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variability

:: content ::
- **Variability** describes the spread of a distribution. 
- Distributions with higher variability show greater spread between scores.  

<img src="/images/lecture4/variance.jpg" alt="variance" class="mx-auto w-1/3" />

<div class="flex items-center gap-4 mt-2">
<IceCream :size="80" mood="excited" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem" v-click>Remember, you can think of a distribution as a histogram that shows counts of values in a dataset. </SpeechBubble>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why do we care about spread?

:: content ::

<Admonition title="An example" color="teal-light" width="100%">Two sections of PS 211 both average 75% on a quiz. In Section A, every student scored between 70-80%. In Section B, scores ranged from 40% to 100%. Same average — very different experiences!</Admonition>

<img src="/images/lecture5/two_sections_same_mean.png" alt="two sections, same mean, different spread" class="mx-auto w-2/5" />

<p v-click>

- Both sections have the *exact same mean*, but they tell very different stories.
- In Section A, the average is a good description of almost everyone.
- In Section B, the average hides huge differences — some students are struggling, some are acing it.

</p>

<p v-click>

==The mean alone doesn't capture this. We need a way to summarize how spread out scores are.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# What does "spread" look like?

:: content ::

- Here are two distributions with the same mean but very different spread — this is the same idea as our two quiz sections.

<img src="/images/lecture4/high_low_var.svg" alt="variance visual anchor" class="mx-auto w-1/2" />

<p v-click>

- The distribution on the left is more spread out (like Section B). The one on the right is more tightly clustered (like Section A).
- By the end of today, you'll be able to put a **number** on this difference.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variability

:: content ::

<Admonition title="Question" color="teal-light" width="100%">How could we measure spread?</Admonition>

<br> 

Three main **descriptive statistics** are used to measure variability:
1. ==Range==: the difference between the highest and lowest score
2. ==Variance==: average square deviation from the mean
3. ==Standard deviation==: the square root of the variance

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Range

:: content ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>

$$Range = X_{max} - X_{min}$$

<br> 

- The range is the difference between the highest and lowest score.  
- For example, if the highest quiz score is 90 and the lowest is 70, the range is 20.  
- The range is simple to compute, but it only depends on two scores and can be distorted by outliers. 


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Interquartile Range

:: content ::
- The interquartile range (IQR) measures the distance between the 25th percentile (Q1) and 75th percentile (Q3).  
- The IQR represents the middle 50% of the data.  
- Because it is less influenced by outliers, the IQR is often a more robust measure of variability.  


<div class="flex items-center justify-center space-x-4">
  <img src="/images/lecture4/iqr.png" alt="iqr" class="w-2/7" />

  **To compute the IQR:**
    Split the data into two halves at the median. Q1 is the median of the lower half of the data. Q3 is the median of the upper half.

</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Computing the Interquartile Range

:: content ::
- The following are the scores of 9 students on an exam: 55, 60, 65, 70, 75, 80, 85, 90, 95. What is the interquartile range (IQR) of these scores?

<p v-click>

1. Order the scores (they are already ordered).

</p>

<p v-click>

2. Find the median (75).

</p>


<p v-click>
3. Split the data into two halves: lower half (55, 60, 65, 70) and upper half (80, 85, 90, 95).
</p>

<p v-click>
4. Find Q1 (the median of the lower half) = (60 + 65) / 2 = 62.5.

</p>

<p v-click>
5. Find Q3 (the median of the upper half) = (85 + 90) / 2 = 87.5.
</p>

<p v-click>

6. Compute the IQR: IQR = Q3 - Q1 = 87.5 - 62.5 = **25.**

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Boxplots revisited

:: left ::

- Boxplots visually represent the median, quartiles, and potential outliers in a dataset.
- The box represents the interquartile range (IQR), with a line at the median.
- "Whiskers" extend to the smallest and largest values within 1.5 * IQR from the quartiles.
- Points outside this range are considered potential outliers.

:: right ::

```r
#make list of exam scores
exam_scores <- c(55, 60, 65, 70, 75, 80, 85, 90, 95)

#put in dataframe
exam_scores_df <- data.frame(exam_scores)
exam_scores_df$exam <- factor(1)  #add variable for x axis

#use ggplot to make boxplot
ggplot(exam_scores_df, aes(x = exam, y = exam_scores)) +
  geom_boxplot() +
  labs(title = "Boxplot of Exam Scores", y = "Scores")
```
<br>
<img src="/images/lecture4/exam1_boxplot.png" alt="boxplot iqr" class="mx-auto w-1/2" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Variance

:: content ::

<Admonition title="Question" color="teal-light" width="100%">What if we want a measure of spread influenced by ALL scores?</Admonition>


- We can compute the distance each score is from the mean (the deviation), and take the average of that.
- But... if we add up all the deviations, they will always equal zero!

**Example**
- Scores: 70, 80, 90
- Mean: 80; Deviations: -10, 0, +10
- Sum of deviations: -10 + 0 + 10 = 0


<p v-click>

<div class="flex items-center gap-4 mt-2">
<IceCream :size="80" mood="excited" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="40rem" v-click>To solve this, we square each deviation (to make them positive) before summing them! </SpeechBubble>
</div>


</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Variance (continued)

:: left ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>


- The formula for the variance of a population is:

$$\sigma^2 = \frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}$$

:: right ::

<p v-click>

<img src="/images/lecture4/ohno_math.jpg" alt="oh no" class="mx-auto w-3/4" />

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Variance (continued)

:: left ::

<AdmonitionType type="warning" width="100%">Equation time!</AdmonitionType>


- The formula for the variance of a population is:

$$\sigma^2 = \frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}$$

:: right ::


<p v-click>

1. For each score ($X_i$), compute the deviation from the population mean: $X_i - \mu$.

<img src="/images/lecture4/mew.png" alt="mew" class="mx-auto w-1/4" />

</p>

<p v-click>

2. Square each deviation: $(X_i - \mu)^2$.

</p>

<p v-click>

3. Sum the squared deviations: $\sum_{i=1}^{N} (X_i - \mu)^2$.

</p>

<p v-click>

4. Divide by the total number of scores: $N$.

</p>

<p v-click>

5. Now we have our population variance, represented by $\sigma^2$ (the Greek letter "sigma" squared).

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Worked example: Variance, step by step

:: left ::

<img src="/images/lecture5/var_walk_hist.png" alt="histogram of eight quiz scores" class="mx-auto w-full" />

:: right ::

- Eight students take a 15-point quiz. Their scores: **5, 6, 7, 8, 8, 9, 10, 11**
- We care about *these eight students* only, so we'll treat them as a population and use the $\sigma^2$ formula.

<p v-click>

**Step 1: Find the mean.**

$$\mu = \frac{5+6+7+8+8+9+10+11}{8} = \frac{64}{8} = 8$$

</p>

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">
The dashed line on the histogram is the mean. Every step from here on asks: how far is each score from that line?
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Worked example: Deviations

:: left ::

<img src="/images/lecture5/var_walk_deviations.png" alt="deviation of each score from the mean" class="mx-auto w-full" />

:: right ::

**Step 2: Find each score's deviation from the mean** ($X_i - \mu$).

- Score − mean: 5 − 8 = **−3**, 6 − 8 = **−2**, 7 − 8 = **−1**, 8 − 8 = **0**, 8 − 8 = **0**
- 9 − 8 = **+1**, 10 − 8 = **+2**, 11 − 8 = **+3**

<p v-click>

- Each line in the plot *is* a deviation. Notice they sum to zero: −3 −2 −1 + 0 + 0 + 1 + 2 + 3 = 0.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Worked example: Square, sum, divide

:: left ::

<img src="/images/lecture5/var_walk_squares.png" alt="squared deviations as bars" class="mx-auto w-full" />

:: right ::

**Step 3: Square each deviation** ($(X_i - \mu)^2$).

9, 4, 1, 0, 0, 1, 4, 9

<p v-click>

**Step 4: Sum the squared deviations.**

$$\sum (X_i - \mu)^2 = 9+4+1+0+0+1+4+9 = 28$$

</p>

<p v-click>

**Step 5: Divide by $N$.**

$$\sigma^2 = \frac{28}{8} = 3.5$$

</p>

<p v-click>

<StickyNote color="indigo-light" title="Read the plot" width="100%">
The variance is the <b>average height of the bars</b>: the average squared distance from the mean.
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Same steps, different spread

:: content ::

Three groups of eight students take the same quiz. All three groups have a mean of 8.

<img src="/images/lecture5/var_three_hists.png" alt="three histograms with the same mean and different spread" class="mx-auto w-4/5" />

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Group B is the group we just worked through (variance = 3.5). Without computing anything, which group has the largest variance? The smallest?</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Group C is the most spread out, so it has the largest variance. Group A is the most tightly clustered, so it has the smallest. Let's check by doing the steps.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Same steps, different spread (continued)

:: content ::

<img src="/images/lecture5/var_two_deviations.png" alt="deviations for groups A and C" class="mx-auto w-1/2" />

<div class="grid grid-cols-2 gap-x-10 mt-2">
<div>

**Group A:** 7, 7, 8, 8, 8, 8, 9, 9

<p v-click>

- Deviations: −1, −1, 0, 0, 0, 0, +1, +1
- Squared: 1, 1, 0, 0, 0, 0, 1, 1
- Sum = 4, so σ² = 4 / 8 = **0.5**

</p>

</div>
<div>

**Group C:** 2, 4, 6, 8, 8, 10, 12, 14

<p v-click>

- Deviations: −6, −4, −2, 0, 0, +2, +4, +6
- Squared: 36, 16, 4, 0, 0, 4, 16, 36
- Sum = 112, so σ² = 112 / 8 = **14**

</p>

</div>
</div>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Bigger spread, bigger variance

:: content ::

<img src="/images/lecture5/var_three_hists_labeled.png" alt="three histograms labeled with their variances" class="mx-auto w-2/3" />

<p v-click>

- Wider histogram → bigger deviations → bigger squared deviations → ==bigger variance==.
- Group C's deviations are exactly **twice** Group B's, but its variance is **four times** as large (14 vs. 3.5). That's the squaring at work: variance is in *squared* units.

</p>

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="30rem">
Squared units are awkward ("3.5 points squared"). Shortly we'll take the square root to get back to points — that's the standard deviation.
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Sample variance

:: left ::

- Usually we don't have the whole population, just a **sample** from it.
- The formula for the variance of a **sample** is:

$$s^2 = \frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1}$$

<p v-click>

*What changed?*

1. We use $M$ (the sample mean) instead of $\mu$ (the population mean).
2. We divide by $N-1$ instead of $N$.
3. We call it $s^2$ (sample variance) instead of $\sigma^2$ (population variance).

</p>

:: right ::

<p v-click>

**Why $N-1$?**

<img src="/images/lecture4/but_why.png" alt="why" class="mx-auto w-1/2" />

</p>

<p v-click>

<StickyNote color="amber-light" title="Next lecture" width="100%">
The reason has to do with using a sample to estimate a population — we'll come back to it in Lecture 8, once we've seen how statistics vary from sample to sample. For now: <b>if your data are a sample, divide by N − 1.</b>
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standard Deviation

:: content ::
- The standard deviation is the square root of the variance.

- The formula for the standard deviation of a population is:
$$\sigma = \sqrt{\frac{\sum_{i=1}^{N} (X_i - \mu)^2}{N}}$$

- The formula for the standard deviation of a sample is:
$$s = \sqrt{\frac{\sum_{i=1}^{N} (X_i - M)^2}{N-1}}$$

- It represents the typical amount that each score deviates from the mean.  

- Larger standard deviations indicate greater spread, while smaller ones indicate that scores cluster more closely around the mean.  

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Seeing the standard deviation

:: content ::

<img src="/images/lecture5/var_walk_sd.png" alt="Group B histogram with SD shown as a horizontal distance from the mean" class="mx-auto w-3/5" />

<p v-click>

- Group B's variance was 3.5, so its SD is $\sqrt{3.5} = 1.87$ points.
- Unlike the variance, the SD is a **distance on the x-axis** of the histogram: ==the typical distance between a score and the mean==. Some scores are closer (the 8s), some are farther (5 and 11), but 1.87 points is the typical gap.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Seeing the standard deviation (continued)

:: content ::

<img src="/images/lecture5/var_three_hists_sd.png" alt="three histograms with their SDs drawn as horizontal arrows" class="mx-auto w-4/5" />

<p v-click>

- Same three groups as before. The red arrow reaches one SD on each side of the mean.
- Group A's scores hug the mean, so one SD is less than a point. Group C's spread out to 2 and 14, so one SD is almost 4 points.
- ==Read the SD as a width:== a wider histogram has a longer arrow.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standard deviation vs. variance

:: content ::
- The standard deviation is often more interpretable than the variance because it is in the same units as the original data.
- For example, if exam scores are measured in points, the standard deviation will also be in points, while the variance will be in points squared.
- Both the variance and standard deviation provide valuable information about the spread of a dataset, but the standard deviation is often preferred for its interpretability.

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">When you hear "scores were typically about 10 points from the average" — that's the standard deviation talking. It's the spread number you'll actually report.</SpeechBubble></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability in R


:: content ::

- R actually has built-in functions to compute variance and standard deviation.

```r
# Sample data
scores <- c(70, 75, 80, 85, 90) 

# Compute sample variance
sample_variance <- var(scores)

# Compute sample standard deviation
sample_sd <- sd(scores)
```

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">The `var()` function in R computes the sample variance (dividing by N-1), and the `sd()` function computes the sample standard deviation.</SpeechBubble>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability in R 


:: content ::

<Admonition title="Question" color="teal-light" width="100%">Thought question: Why would the built in 'var' and 'sd' functions compute the sample variance and standard deviation instead of the population versions?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

In practice, we often work with samples rather than entire populations. Therefore, R's built-in functions are designed to compute sample statistics by default.

<img src="/images/lecture4/sample_meme.jpg" alt="sample meme" class="mx-auto w-1/4" />

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability: Practice


:: content ::

<Admonition title="Question" color="teal-light" width="100%">Which histogram displays data with higher variance?</Admonition>

<img src="/images/lecture4/high_low_var.svg" alt="variance practice" class="mx-auto w-2/5" />

<Admonition title="Answer" color="green-light" width="100%" v-click>

The histogram on the left has higher variance because the scores are more spread out from the mean.

</Admonition>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Which measure of variability would be most affected by an outlier?</Admonition>
</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The range would be most affected by an outlier because it only depends on the highest and lowest scores.

</Admonition></p>



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Variability: Practice (Continued)


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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: One by hand

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Five students report how many hours they slept last night: <b>4, 6, 7, 8, 10</b>. Treating them as a sample, find the mean and the sample standard deviation.</Admonition>

<p v-click><StickyNote color="amber-light" title="Try it first" width="60%">Work through it with the person next to you. Hint: the mean is a whole number, so every deviation is too. Check that the deviations add up to zero before you square anything.</StickyNote></p>

<p v-click>

**Step 1: Find the mean.**

$$M = \frac{4+6+7+8+10}{5} = \frac{35}{5} = 7 \text{ hours}$$

</p>

<p v-click>

**Step 2: Find each deviation from the mean.**

$$4-7=-3 \quad\; 6-7=-1 \quad\; 7-7=0 \quad\; 8-7=+1 \quad\; 10-7=+3$$

Check: $-3 - 1 + 0 + 1 + 3 = 0$. The deviations always cancel out, which is exactly why we square them next.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: One by hand (continued)

:: left ::

**Step 3: Square each deviation and add them up.**

<div class="grid grid-cols-3 gap-x-6 text-sm leading-snug" style="max-width:18rem">
<div><b>Score</b></div><div><b>Deviation</b></div><div><b>Squared</b></div>
<div>4</div><div>-3</div><div>9</div>
<div>6</div><div>-1</div><div>1</div>
<div>7</div><div>0</div><div>0</div>
<div>8</div><div>+1</div><div>1</div>
<div>10</div><div>+3</div><div>9</div>
</div>

$$SS = 9 + 1 + 0 + 1 + 9 = 20$$

:: right ::

<p v-click>

**Step 4: Divide by N − 1 to get the variance.**

$$s^2 = \frac{20}{5-1} = \frac{20}{4} = 5 \text{ hours}^2$$

</p>

<p v-click>

**Step 5: Take the square root to get the SD.**

$$s = \sqrt{5} = 2.24 \text{ hours}$$

</p>

<p v-click>

==A typical student's sleep was about 2.2 hours away from the mean of 7 hours.==

</p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="l" maxWidth="24rem">That is the entire computation. Every dataset, no matter how big, goes through these same five steps.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
columns: is-5-7
align: lt-lt-lt
---

:: title ::
# Practice: Same range, different spread

:: left ::

<Admonition title="Question" color="teal-light" width="100%">Two datasets:<br><b>Dataset 1:</b> 1, 1, 1, 9, 9, 9<br><b>Dataset 2:</b> 1, 3, 5, 5, 7, 9<br>Both have a mean of 5 and a range of 8. Without computing anything, which has the larger standard deviation?</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**Dataset 1.** Every one of its scores sits 4 points from the mean. In Dataset 2, two scores sit right on the mean and two are only 2 points away, so the typical distance is smaller (SD ≈ 4.4 vs. 2.8).

</Admonition></p>

:: right ::

<div v-click>

<img src="/images/lecture5/var_same_range.png" alt="deviations from the mean for two datasets with the same range" class="mx-auto w-full" />

</div>

<p v-click>

- ==The range only looks at the two endpoints. The SD looks at every score.==
- Two datasets can share a min, a max, and a mean and still have very different spreads.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Guess the SD

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Three sections took the same 20-point quiz, and every section averaged 12. Estimate each section's standard deviation by eye. Hint: the SD is the typical distance between a score and the dashed mean line.</Admonition>

<img src="/images/lecture5/var_guess_sd.png" alt="three histograms of quiz scores with the same mean" class="mx-auto w-4/5" />

<p v-click><StickyNote color="amber-light" title="Commit to a number" width="60%">Write down one guess per section before we reveal the answers. Being roughly right is the skill here.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Guess the SD (continued)

:: content ::

<img src="/images/lecture5/var_guess_sd_answer.png" alt="the same three histograms with SD arrows" class="mx-auto w-4/5" />

<p v-click>

- Section 1's scores are all within a point of the mean, so its SD is under 1. Section 3's scores stretch from 4 to 20, so a typical score is almost 5 points from the mean.
- Section 2's SD (2.4) is about half of Section 3's (4.8), and its histogram is about half as wide.
- ==If your guess was within a point of each answer, you understand what the SD measures.== The arithmetic is the computer's job.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# A bigger dataset: let R do the bookkeeping

:: content ::

- Ten students report how many hours they slept last night: **5, 6, 6, 7, 7, 7, 8, 8, 9, 9**.
- The mean is 7.2, so every deviation is a decimal. Ten decimal deviations by hand is a chore, and the steps are exactly the ones you just did with five scores. This is what `var()` and `sd()` are for.

```r
sleep <- c(5, 6, 6, 7, 7, 7, 8, 8, 9, 9)

mean(sleep)   # 7.2
var(sleep)    # 1.73   (sum of squared deviations = 15.6, divided by 9)
sd(sleep)     # 1.32
```

<p v-click>

==On average, students' sleep differed from the mean of 7.2 hours by about 1.3 hours.==

</p>

<p v-click><StickyNote color="teal-light" title="In discussion section" width="60%">You'll compute these yourself in R, and check that R's answers match the five-step recipe.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
columns: is-5-7
align: lt-lt-lt
---

:: title ::
# Practice: Everyone sleeps one more hour

:: left ::

<Admonition title="Question" color="teal-light" width="100%">Same ten students (mean 7.2, range 4, SD 1.32). Suppose every one of them sleeps exactly one more hour tomorrow night. What happens to the mean, the range, and the SD?</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- **Mean: 7.2 → 8.2.** It moves up with the scores.
- **Range: still 4.** The lowest and highest scores both moved up by one.
- **SD: still 1.32.** Every score moved up by one, and so did the mean, so ==every deviation is exactly what it was.==

</Admonition></p>

:: right ::

<div v-click>

<img src="/images/lecture5/var_shift.png" alt="dot plots of sleep hours before and after adding one hour to every score" class="mx-auto w-full" />

</div>

<p v-click>

- The whole picture slides to the right. The SD arrow doesn't change length, because spread is about distances *between* scores and the mean, not *where* the scores sit.

</p>

---
layout: top-title-two-cols
color: indigo-light
columns: is-5-7
align: lt-lt-lt
---

:: title ::
# Practice: Everyone's hours are doubled

:: left ::

<Admonition title="Question" color="teal-light" width="100%">Now suppose every student's sleep is doubled instead (5 becomes 10, 9 becomes 18, and so on). What happens to the mean, the range, the SD, and the variance?</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- **Mean: 7.2 → 14.4** (doubled).
- **Range: 4 → 8** (doubled).
- **SD: 1.32 → 2.63** (doubled). Every deviation is twice as big.
- **Variance: 1.73 → 6.93** (quadrupled!). Every *squared* deviation is four times as big.

</Admonition></p>

:: right ::

<div v-click>

<img src="/images/lecture5/var_scale.png" alt="dot plots of sleep hours before and after doubling every score" class="mx-auto w-full" />

</div>

<p v-click>

- The dots spread out and the SD arrow gets twice as long. ==This is why we take the square root:== the SD grows with the data, in its units; the variance grows with the square.

</p>

---
layout: top-title-two-cols
color: indigo-light
columns: is-5-7
align: lt-lt-lt
---

:: title ::
# Practice: One extreme score

:: left ::

<Admonition title="Question" color="teal-light" width="100%">Back to the original data. One student who reported 9 hours actually slept 14. Which changes more, the range or the SD?</Admonition>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

- **Range: 4 → 9.** More than doubled, because the range is determined entirely by that one score.
- **SD: 1.32 → 2.50.** It grows too (squaring makes a deviation of +6.3 count a lot), but the other nine scores still anchor it.
- **Mean: 7.2 → 7.7.**

</Admonition></p>

:: right ::

<div v-click>

<img src="/images/lecture5/var_outlier.png" alt="dot plots of sleep hours before and after one score becomes an outlier" class="mx-auto w-full" />

</div>

<p v-click>

- One score can move the range as far as it likes. The SD moves too, but every other score has a say. ==That is what it means for the range to be the measure most sensitive to outliers.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Discussion: Anxiety scores

:: content ::

<StickyNote color="teal-light" title="Discussion" width="100%">
Two groups of students both report an average anxiety score of 5 (on a 0-10 scale) before an exam. Group A has a standard deviation of 0.5. Group B has a standard deviation of 3.5. What does this difference in SD tell us about each group, even though their average is identical?
</StickyNote>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

In Group A, almost everyone feels about the same, moderate amount of anxiety — the mean of 5 describes the group well. In Group B, the same average of 5 is hiding a lot of variability: some students may feel almost no anxiety, while others may feel extremely anxious.

</Admonition></p>

<p v-click>

- This matters practically! If you were designing an intervention, Group B might need a more individualized approach, while a single approach might work well for Group A.
- ==A mean without a measure of variability can be misleading.==

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Looking ahead

:: content ::

<StickyNote color="amber-light" title="Looking ahead" width="100%">
Variance and standard deviation aren't just standalone descriptive statistics — they're the foundation for almost everything else we'll do this semester.
</StickyNote>

<p v-click>

- Soon, we'll use the standard deviation to **standardize scores into z-scores**, letting us compare scores from totally different scales.
- Later, we'll learn about **standard error** — how much sample means bounce around from sample to sample — which depends directly on variability.
- If today's material feels shaky, now is the time to review it, since z-scores, standard error, and effect size all build directly on variance and SD.

</p>

---
layout: cover
color: indigo-light
---


# That's all for today!
Next time: sampling, probability, and an introduction to hypothesis testing.
