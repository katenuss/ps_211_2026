---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 4
exportFilename: ps211_fall2026_lecture4
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 4: Central Tendency

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::

- Remember: there is no standalone homework this year. Instead, you'll complete two Data Write-Ups later in the semester (the first is t-test based, due Monday, Nov. 16; the second is ANOVA based, due Monday, Dec. 7).
- Please make sure you know how to use R Markdown and that you can successfully knit a document to an html file.
- Discussion sections are using time for in-class R practice — take advantage of it!
- Office hours: Tuesdays 12:30-1:30pm and Thursdays 9:00-10:00am.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders (continued)

:: content ::

- ==Exam 1== is scheduled for **Tuesday, September 29** during our regular class time.
    - Exam 1 will cover material from Lectures 1 - 6 and consist of multiple choice questions.
    - After Lecture 6, I will post a review sheet on Slack that has all the topics that will be covered on the exam.
    - The exam will be closed book/notes, but you may print the provided review sheet (and write on it with your own notes) or you may bring one 8.5" x 11" sheet of paper with handwritten notes (both sides).
    - No calculator is needed.
- We will have a review session for Exam 1 on Thursday, September 24 during our regular class time. Please bring your questions!


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Central Tendency

:: content ::

- The central tendency describes the “center” of a dataset.  
- It identifies the value that scores cluster around.  
- The three common measures of central tendency are mean, median, and mode.  

==These are descriptive statistics.==

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Mean, median, and mode

:: content ::

**Mean:** The arithmetic average

**Median:** The middle score

**Mode:** The most common score

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Mean: The Arithmetic Average

:: content ::

<AdmonitionType type="warning" width="100%">Equation incoming!</AdmonitionType>

<p v-click>

The formula for the mean is:
$$M = \frac{\sum_{i=1}^{N} X_i}{N}$$

</p>

<p v-click>

==Let's break this down:==

</p>

<p v-click>

$M$ = the mean. This is what we are trying to calculate.

</p>

<p v-click>

$\sum$ = the summation symbol. This means "add up all the following values."

</p>

<p v-click>

$\sum_{i=1}^{N}$ = this tells us to start with the first score (i=1) and continue adding scores until we reach the Nth score (the last score).

</p>

<p v-click>

$X_i$ = the value of the ith score.

</p>

<p v-click>

$N$ = the total number of scores.

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Calculating the mean
$$M = \frac{\sum_{i=1}^{N} X_i}{N}$$

:: left ::

1. Add up all the scores.
2. Count the total number of scores.
3. Divide the sum of the scores by the total number of scores.

:: right ::


<img src="/images/lecture4/mean.png" alt="mean" class="mx-auto w-3/8" />

==Some people like to think of the mean as a fulcrum balancing the two sides of a distribution.==

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The mean: Practice
$$M = \frac{\sum_{i=1}^{N} X_i}{N}$$

:: left ::

<Admonition title="Question" color="teal-light" width="100%">Five students take an exam and receive the following scores: 80, 85, 90, 95, 100. What is the mean exam score?</Admonition>

<p v-click>


**Answer:** 90. 80 + 85 + 90 + 95 + 100 = 450. There are 5 scores, so 450 / 5 = 90.

</p>


:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
A sixth student takes the exam and receives a score of 80. You compute the mean again:

90 + 80 = 170
170 / 2 = 85

Is the mean now 85?
</Admonition>

</p>

<p v-click>

**Answer:** No. The new mean is 86.7:
 
$$80 + 85 + 90 + 95 + 100 + 80 = 520$$

$$520/ 6 = 86.7$$

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The mean: Symbols
:: content ::

- The mean of a sample is a **statistic**.
- The mean of a population is an estimated **parameter**.
- Typically:
    - Symbols are *italicized*. Numbers are not.
    - Latin letters are used for statistics (numbers calculated from samples).
    - Greek letters are used for parameters (numbers estimated for populations).
- The mean of a sample is denoted by $M$ or $\bar{X}$ (X-bar).
- The mean of a population is denoted by $\mu$ (the Greek letter "mu").

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The mean: Symbols

:: left ::

<img src="/images/lecture4/m.jpeg" alt="m" class="mx-auto w-1/2" />

==Sample Mean== (but capitalize it!)
- Can be calculated directly. 

:: right::

<img src="/images/lecture4/mew.png" alt="mew" class="mx-auto w-1/2" />

==Population Mean==
- Usually estimated.


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Median

:: content ::
- The median is the middle score when all scores are ordered from lowest to highest (ascending).
- If there is an odd number of scores, the median is the middle score.
- If there is an even number of scores, the median is the mean of the two middle scores.  
- The median represents the 50th percentile of the data.  


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Median

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Five students take an exam and receive the following scores: 92, 85, 90, 95, 100. What is the median exam score?</Admonition>

<p v-click>

**Answer:** 92. 

First, we order the scores: 85, 90, 92, 95, 100. 

The middle score is 92.

</p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">A sixth student takes the exam and receives a score of 0. What is the median exam score now?</Admonition>

</p>

<p v-click>

**Answer:** 91. The ordered scores are now: 0, 85, 90, 92, 95, 100. The two middle scores are 90 and 92, and their mean is 91.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Mode

:: content ::
- The mode is the most common score in the dataset.  
- A distribution may be unimodal (one mode), bimodal (two modes), or multimodal (many modes).  
- The mode is not always useful if many values occur with the same frequency.  

---
layout: top-title
color: indigo-light
---

:: title ::
# The Mode

:: content ::

- A **unimodal** distribution has one mode.
- A **bimodal** distribution has two modes.
- A **multimodal** distribution has multiple modes.


---
layout: top-title
color: indigo-light
---

:: title ::
# Example: Bimodal distribution

:: content ::
- In bimodal and multimodal distributions, the mean and median are *not* representative of the data.

<img src="/images/lecture4/bimodal.png" alt="bimodal" class="mx-auto w-1/2" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Mean, median, and mode

:: content ::

<Admonition title="Question" color="teal-light" width="100%">If a distribution is positively skewed, which measure of central tendency will be the largest? Which will be the smallest?</Admonition>


<p v-click>

**Answer:** The mean will be the largest, and the mode will be the smallest.

<img src="/images/lecture4/mean_med_mode.png" alt="mean med mode" class="mx-auto w-3/4" />

</p>



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
layout: cover
color: indigo-light
---


# That's all for today!
Next time, we'll dig into **variability** — how spread out scores are, not just where they center.
