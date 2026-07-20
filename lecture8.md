---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 8
exportFilename: ps211_fall2026_lecture8
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 8: The Central Limit Theorem & Standard Error

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- ==Exam 2== covers Lectures 7-12.
- Exam 2 Review is Tuesday, October 27.
- Exam 2 is Thursday, October 29.
- Reminder: no standalone homeworks this semester. Instead, you'll complete **2 Data Write-Ups** (10% of your grade each):
  - Write-Up 1 (t-test based): due Monday, November 16
  - Write-Up 2 (ANOVA based): due Monday, December 7
- Office hours: Tuesday 12:30-1:30pm, Thursday 9:00-10:00am.
- Heads up: there is **no class** next Tuesday, October 13 (substitute Monday schedule).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Central Limit Theorem

:: content ::
- ==The theorem:== Any **distribution of sample means** will be approximately normal if the sample size is sufficiently large.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What is a "distribution of sample means"?
</Admonition>

</p>

<p v-click>

**Answer:** A "distribution of sample means" is the distribution of the means of multiple samples taken from a population. It shows how the sample means vary and allows us to make inferences about the population mean.

</p>

<p v-click>

**Example:** We want to estimate the average height of all PS 211 students. Each class, we measure the height of 5 randomly selected students and calculate the mean height of those 5 students. We repeat this process many times, each time selecting a new random sample of 5 students and calculating the mean height. The distribution of these sample means will be approximately normal, even if the original distribution of individual heights is not normal.
</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Central Limit Theorem: Demo

:: left ::
# Dice Rolls
- Imagine rolling a 6-sided die.
- Roll it once, record the result.
- Repeat many times, plot the distribution of results.

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What does this distribution look like?
</Admonition>

</p>

<p v-click>

<img src="/images/lecture6/dice_roll_hist.png" alt="Dice rolls 1" class="w-full mx-auto"/>

</p>

<p v-click>

**Answer:** The distribution is ==uniform==, with each outcome (1-6) equally likely.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Central Limit Theorem: Demo (Continued)

:: left ::
# Sampling Dice Rolls
- Now imagine randomly selecting two rolls from this distribution.
- Compute their mean.
- Repeat many times, plot the distribution of means.

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What does the distribution of means look like?
</Admonition>

</p>

<p v-click>

<img src="/images/lecture6/dice_roll_mean_hist.png" alt="Dice roll means" class="w-full mx-auto"/>

</p>

<p v-click>

**Answer:** As the sample size increases, the distribution of means approaches a normal distribution, even though the original distribution is uniform!
</p>



---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Distribution of Scores vs. Means

:: left ::

- Even if scores in a population aren’t normally distributed, the distribution of sample means will be approximately normal if the sample size is large enough.
- This is the essence of the Central Limit Theorem.
- A distribution of means is **less variable** than a distribution of raw scores.
- This means it is less spread out.

:: right ::

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why is the distribution of means less variable than the distribution of raw scores?
</Admonition>

</p>

<p v-click>

**Answer:** The distribution of means is less variable because averaging reduces the impact of extreme values. When we take the mean of a sample, we are essentially smoothing out the variability that exists in individual scores.
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# The Central Limit Theorem: Video Explanation

:: content ::
Let's watch someone else explain this!

https://www.youtube.com/watch?v=YAlJCEDH2uY


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Standard Error of the Mean

:: left ::

- The ==standard error (SE)== is the name for the standard deviation of a distribution of sample means.

- The formula for the standard error is:
$$ SE = \frac{s}{\sqrt{n}} $$
where $s$ is the sample standard deviation and $n$ is the sample size.

:: right ::

<p v-click>

<AdmonitionType type="warning" width="100%">
Where does this formula come from?
</AdmonitionType>

</p>

<p v-click>

**Answer:** The formula for the standard error comes from the fact that the variability of sample means is related to the variability of individual scores and the sample size. As we increase the sample size, the standard error decreases, reflecting the increased precision of our estimate of the population mean.

*We can derive it mathematically, but that is beyond the scope of this class.*

</p>


---
layout: center
color: amber-light
---

<StickyNote color="amber-light" title="Why this matters" width="80%">

The standard error is one of the most important ideas in this entire course.

Every sample mean we compute "bounces around" the true population mean just by chance. The standard error lets us **quantify how much bounce to expect.**

Very soon, we'll use exactly this idea to:
- Build **z-tests** that ask "is our sample mean far enough from what we'd expect by chance?"
- Construct **confidence intervals** around sample means
- Run **hypothesis tests** more generally, across many different statistical tests

Understanding standard error now will make everything else in this course click into place.

</StickyNote>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Standard Error of the Mean

:: left ::

- The standard error tells us how much variability we can expect in sample means from one sample to another.
- As sample size ($n$) increases, the standard error decreases.
- This means that larger samples yield more ==precise== estimates of the population mean.
- The **standard deviation** tells us the spread of individual data points, while the **standard error** helps quantify the uncertainty in our estimate of the population mean.


:: right ::

<p v-click>

<AdmonitionType type="warning" width="100%">
Why is this value important in psychological research?
</AdmonitionType>

</p>

<p v-click>

**Answer:** The standard error is important because it helps researchers understand how much their sample mean might vary from the true population mean.
</p>

<p v-click>
<img src="/images/lecture6/barplot_sem.png" alt="Error bars" class="w-3/4 mx-auto"/>
</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Calculating Standard Error

:: left ::

- If the SD of a distribution of individual scores = 5
- If we take samples of size $n = 25$, then the SE of the distribution of sample means is:
$$ SE = \frac{5}{\sqrt{25}} = \frac{5}{5} = 1 $$

<Admonition title="Question" color="teal-light" width="100%">
What if we take samples of size $n = 9$? What if we take samples of size $n = 100$? Which will have a smaller SE? Why?
</Admonition>


:: right ::

<p v-click>

**Answer:**
- For $n = 9$:
$$ SE = \frac{5}{\sqrt{9}} = \frac{5}{3} \approx 1.67 $$

- For $n = 100$:
$$ SE = \frac{5}{\sqrt{100}} = \frac{5}{10} = 0.5 $$

The sample size of $n = 100$ will have a smaller SE because the standard error decreases as the sample size increases. This reflects the increased precision of our estimate of the population mean with larger samples.

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Putting concepts together

:: left ::

- Imagine you want to determine whether Psychology majors or Biology majors have higher GPAs. You randomly sample 30 students from each major and record their GPAs.

<Admonition title="Question" color="teal-light" width="100%">
What would be a good way to visualize these GPA distributions? Think of two types of plots that could be used for this purpose.
</Admonition>

<p v-click>

1. **Box plots:** These would allow you to see the median, quartiles, and potential outliers for each major's GPA distribution.
2. **Histograms:** These would show the frequency distribution of GPAs for each major, allowing you to see the shape of the distribution (e.g., normality, skewness).

</p>



:: right ::

<Admonition title="Question" color="teal-light" width="100%">
Now imagine you want to compare the mean GPAs of the two groups. What would be a good way to quantify your uncertainty in the estimate of these means? How could you visualize the uncertainty in your estimate of the mean GPA for each major?
</Admonition>

<p v-click>

**Answer:** You could calculate the **standard error (SE)** for each group's mean GPA. 

To visualize the uncertainty in your estimate of the mean GPA for each major, you could use barplots with error bars representing the SE for each group. 

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Putting concepts together (Continued)

:: left ::

# Let's take a look at what those plots might look like

<br>

<img src="/images/lecture6/gpa_barplot.png" alt="Barplot of gpa with error bars" class="w-1/2mx-auto"/>

<p v-click>

**Challenge question:** If the SE represents +/- 1 SD of the distribution of sample means, what is the probability that the true population mean falls within the error bars shown in the barplot?

</p>

<p v-click>

<StickyNote color="green-light" title="Answer" width="100%">
Approximately 68% of the time, since the error bars represent +/- 1 SD of the distribution of sample means.
</StickyNote>

</p>


:: right ::

<img src="/images/lecture6/gpa_hist.png" alt="Histogram of gpa" class="w-3/4 mx-auto"/>

<br>

<img src="/images/lecture6/gpa_boxplot.png" alt="Boxplot of GPA" class="w-3/4 mx-auto"/>


---
layout: cover
color: indigo-light
---

# That's all for today!
Next time: using z scores and the z table to compute percentiles — and our first hypothesis tests!
