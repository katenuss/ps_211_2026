---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 7
exportFilename: ps211_fall2026_lecture7
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 7: Normal Distributions, Standardization & Z-Scores

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- ==Exam 2== now covers Lectures 7-12.
- Exam 2 Review is Tuesday, October 27.
- Exam 2 is Thursday, October 29.
- There are no standalone homeworks this semester. Instead, you'll complete **2 Data Write-Ups** (10% of your grade each):
  - Write-Up 1 (t-test based): due Monday, November 16
  - Write-Up 2 (ANOVA based): due Monday, December 7
- Office hours: Tuesday 12:30-1:30pm, Thursday 9:00-10:00am.
- Please bring questions to office hours rather than Slack for anything requiring a longer discussion.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Quick Recap: Variance & Standard Deviation

:: content ::
- **Variance:** the average squared deviation of scores from the mean.
- **Standard deviation (SD):** the square root of variance — it tells us the *typical* distance of a score from the mean.

$$ SD = \sqrt{\frac{\sum (X_i - M)^2}{N}} $$

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
We covered variance and SD in depth a couple lectures ago. Today we build on that foundation to talk about normal distributions and z-scores.
</SpeechBubble>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Review: Normal Curves

:: left ::
- A **normal distribution** is:
  - Bell-shaped: Most scores cluster in the center
  - Symmetrical: Left side mirrors the right
  - Unimodal: Only one “hump”  
- Ends of the curve are called **tails**

<Admonition title="Today's Goal" color="teal-light" width="100%">
Today, we'll learn why normal distributions are so important in statistics.
</Admonition>

:: right ::

<img src="/images/lecture6/normal_dist.png" alt="Normal distribution" class="w-3/4 mx-auto"/>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Cheater Detection Using Normal Curves

:: left ::

- We often expect natural patterns to be normally distributed.  
- Deviations from normality can indicate **cheating** or **manipulation**, or more generally that something is off.

<p v-click>

### Study of sumo wrestlers:
  - 26% finished with 8 wins  
  - 12.2% finished with 7 wins  
  - Expected (if normal): ~19.6% for both outcomes  
</p>

:: right ::

<img src="/images/lecture6/sumo_normal.png" alt="Sumo results normal dist" class="w-1/2 mx-auto"/>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why might the sumo results deviate from a normal distribution?
</Admonition>

</p>

<p v-click>

**Answer:** Sumo wrestlers were throwing matches to help wrestlers who had won 7 matches win their 8th (and have a winning season / advance rounds).

</p>

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
This is also called "anomaly detection" and is used in many fields, including fraud detection.
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# More Scores = More “Normal”

:: left ::

- As sample size increases, samples drawn from normally distributed populations look more normal.
- Larger samples better approximate the true population distribution.
- Small samples can look irregular.  

<img src="/images/lecture6/happiness_small.png" alt="Small normal dist" class="w-3/4 mx-auto"/>


:: right ::


<img src="/images/lecture6/happiness_large.png" alt="Large normal dist" class="w-3/4 mx-auto"/>

<img src="/images/lecture6/happiness_largest.png" alt="Larger normal dist" class="w-3/4 mx-auto"/>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standardization: Comparing Apples and Oranges

:: content ::
- When data are normally distributed, we can compare scores across ==different== distributions.
    - This can be very useful!

- We actually often do this implicitly, without realizing it or using math.
- Example:
    - If a movie critic typically gives 4-star reviews, and another typically gives 2-star reviews, who gave the better review if they both gave a movie 3 stars?
    - You might intuitively say the second critic, because 3 stars is above their average, while it's below the first critic's average.

<p v-click>

**But how much better?**
- We can use math to quantify this!

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Standardization: Comparing Apples and Oranges

:: content ::

- Standardization lets us compare scores across **different distributions**.  
- We accomplish by converting raw scores into a common metric: “number of SDs from the mean.”  
- This common metric is called a **z score**.
- We can then directly compare *z* scores from different distributions.

<p v-click>

<StickyNote color="amber-light" title="Definition" width="100%">
z score: How many standard deviations a score is from the mean of its distribution.
</StickyNote>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: Standard Deviation

<img src="/images/lecture6/i-am-back.png" alt="I am back meme" class="w-1/4 mx-auto"/>

:: content ::
- **Variance:** average squared deviation from the mean  
- **Standard Deviation (SD):** square root of variance  

$$ SD = \sqrt{\frac{\sum (X_i - M)^2}{N}} $$

- SD tells us the **typical deviation** from the mean.  
- Larger SD = more spread.  


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The Z Distribution

<StickyNote color="amber-light" title="Definition" width="100%">
z score: How many standard deviations a score is from the mean of its distribution.
</StickyNote>

:: left ::

- A $z$ distribution is a distribution of $z$ scores.  
- Properties:  
  - Mean = 0  
  - SD = 1  

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why is the mean of a z distribution always 0?
</Admonition>

</p>

<p v-click>

**Answer:** The mean is **0 standard deviations from the mean**!  

</p>


:: right ::
<img src="/images/lecture6/z_dist.png" alt="Z distribution" class="w-full mx-auto"/>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# The Z Distribution (Continued)

<StickyNote color="amber-light" title="Definition" width="100%">
z score: How many standard deviations a score is from the mean of its distribution.
</StickyNote>

:: left ::

- A $z$ distribution is a distribution of $z$ scores.  
- Properties:  
  - Mean = 0  
  - SD = 1  

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why is the SD of a z distribution always 1?
</Admonition>

</p>

<p v-click>

**Answer:** If a raw score is 1 SD above the mean, its z score is 1. If a raw score is 2 SDs above the mean, its z score is 2. And so on. Thus, the SD of the z distribution is always 1. 

</p>


:: right ::
<img src="/images/lecture6/z_dist.png" alt="Z distribution" class="w-full mx-auto"/>


<p v-click>
Understanding a score's relation to the mean of its distribution gives us important information.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# How to Calculate a Z Score

:: content ::
You can sometimes calculate z scores without a calculator.


**Example:**  
- Exam mean = 70  
- SD = 10  
- Your score = 80
- Your friend's score = 75  
- Your enemy's score = 60

<Admonition title="Question" color="teal-light" width="100%">
What is your z score? What is your friend's z score? What is your enemy's z score?
</Admonition>

<p v-click>

**Answer:** Your $z = 1$, friend's $z = 0.5$, enemy's $z = -1$

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt 
---

:: title ::

# How to Calculate a Sample Z Score: Formula

:: left ::

$$z = \frac{X - M}{s}$$

<img src="/images/lecture6/ohno.jpeg" alt="Oh no" class="w-3/4 mx-auto"/>


:: right ::

**Let's break it down:**


**Step 1:** Compute the sample mean ($M$) and standard deviation ($s$).

**Step 2:** Subtract the mean from your raw score ($X - M$).

*This gives us the distance from the mean.*

**Step 3:** Divide by the standard deviation ($s$). 

*This converts the distance into "number of standard deviations."*

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
How would we compute a z score for a population instead of a sample?
</Admonition>

</p>

<p v-click>

**Answer:** Use the population mean ($\mu$) and population standard deviation ($\sigma$).
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Computing a Z Score

:: content ::
- Mean happiness score of 157 countries = 5.382  
- SD = 1.138  
- Australia’s score = 7.313  

*How many SDs above the mean is Australia's level of happiness?*

$$ z = \frac{7.313 - 5.382}{1.138} \approx 1.7 $$

**Interpretation:**  
Australia's happiness level is **1.7 SDs above the mean**.  

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Computing a Z Score

:: content ::
- Mean happiness score of 157 countries = 5.382  
- SD = 1.138 
- Egypt’s score = 4.362  

$$ z = \frac{4.362 - 5.382}{1.138} \approx -0.9 $$

*How many SDs below the mean is Egypt's level of happiness?*

**Interpretation:**  
Egypt's happiness level is **0.9 SDs below the mean**.  

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Reverse: Transforming Z Scores into Raw Scores

:: left ::
- You can also convert $z$ scores back into raw scores.

Formula:  
$$ X = z \times SD + M $$

:: right ::
**Example:**  
- France happiness: $z = 0.963$  
- Mean happiness score of 157 countries = 5.382  
- SD = 1.139  

$$ X = (0.963)(1.139) + 5.382 \approx 6.48 $$  

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why is this useful?

:: content ::
- *Z* scores allow comparison across different scales.  

**Example:**  
- Imagine we are comparing grades across two PS 211 classes, taught by different professors.

- Your grade: 92/100, class mean = 78.1, SD = 12.2  
- Your friend's grade: 8.1/10, class mean = 6.8, SD = 0.74  

*Who did better, you or your friend?*

<p v-click>

- Your $z = \frac{92-78.1}{12.2} = 1.14$  
- Friend’s $z = \frac{8.1-6.8}{0.74} = 1.76$  

</p>

<p v-click>

**Conclusion:** Both of you received above average grades, but your friend did better *relative to their class*.  

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Comparing scores across different scales: Practice!

:: content ::
- Imagine you want to decide which of two new restaurants to go to.
- Restaurant A was reviewed by Critic A, who gave it a 7/10.
- Restaurant B was reviewed by Critic B, who gave it a 7/10.

<p v-click>

- You have the smart idea to take a *sample* of each critic's past restaurant ratings to see how harsh or lenient they are.
- Critic A's ratings: $6, 6, 7, 8, 4$
- Critic B's ratings: $4, 5, 5, 9, 8$

</p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Which restaurant should you go to, based on the critics' reviews? Explain your reasoning!
</Admonition>

**Take 10 minutes to work this out with your neighbors. You can use a calculator and refer to your past notes! There is a lot of computation involved!**

</p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Comparing scores across different scales: Practice (Continued)

:: left ::
- Critic A's ratings: $6, 6, 7, 8, 4$
- Critic B's ratings: $4, 5, 5, 9, 8$


<p v-click>

**Step 1:** Calculate the mean and SD for each critic's ratings.
- Critic A: $M = 6.2$, $SD \approx 1.48$
- Critic B: $M = 6.2$, $SD \approx 2.17$

</p>


<p v-click>

**Step 2:** Calculate the z score for each restaurant's rating.
- Restaurant A: $z = \frac{7 - 6.2}{1.48} \approx 0.54$
- Restaurant B: $z = \frac{7 - 6.2}{2.17} \approx 0.37$

</p>



:: right ::
<p v-click>

**Conclusion:** Based on the z scores, Restaurant A is a better choice relative to its critic's past ratings.

</p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why does the standard deviation matter in this comparison?
</Admonition>

</p>

<p v-click>

**Answer:** Critic B's ratings are more spread out (higher SD), so a 7/10 is less impressive relative to their average rating than it is for Critic A. 

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One More Practice Problem

:: content ::
- Imagine you took two different exams this semester, graded on different scales.
- **Exam 1:** class mean = 75, SD = 8. Your score = 87.
- **Exam 2:** class mean = 68, SD = 5. Your score = 76.

<Admonition title="Question" color="teal-light" width="100%">
On which exam did you perform better, *relative to your classmates*? Calculate a z score for each exam to find out.
</Admonition>

<p v-click>

**Step 1:** Calculate your z score on Exam 1.
$$ z_1 = \frac{87 - 75}{8} = 1.5 $$

</p>

<p v-click>

**Step 2:** Calculate your z score on Exam 2.
$$ z_2 = \frac{76 - 68}{5} = 1.6 $$

</p>

<p v-click>

<StickyNote color="green-light" title="Answer" width="100%">
You did slightly better, relative to your classmates, on Exam 2 (z = 1.6) than on Exam 1 (z = 1.5) — even though your raw score was higher on Exam 1! Standardizing lets us compare performance across two exams with different means and SDs.
</StickyNote>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Z Scores, Normal Distributions, and Percentiles

:: left ::


- $z$ scores allow us to determine **percentiles**.  
- ==Percentile==: percentage of scores below a given score.
- Normal distributions are standard, so we know the percentage of scores below any $z$ score.


<img src="/images/lecture6/z_percentile.png" alt="Z scores percentiles" class="w-full mx-auto"/>



:: right ::

- 100% of scores fall below $z = +\infty$; 0% fall below $z = -\infty$.
- 50% of scores fall below $z = 0$ (the mean).
- 84% of scores fall below $z = 1$ (1 SD above the mean).
- 68% of scores fall between $z = -1$ and $z = +1$ (within 1 SD of the mean).

- **Can use a z table to find exact percentiles for any z score.** 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# R Demo: Z Scores and Percentiles

:: left ::
- Let's do a quick demo in R to calculate z scores and percentiles.


```r
# Sample data: Happiness scores of countries
happiness_scores <- c(7.313, 6.48, 4.362, 5.5, 3.8, 6.9, 4.12)

# Calculate mean and standard deviation
mean_happiness <- mean(happiness_scores)
sd_happiness <- sd(happiness_scores)

# Calculate z scores
z_scores <- (happiness_scores - mean_happiness) / sd_happiness
z_scores

# Convert z scores to percentiles with the 'pnorm' function
percentiles <- pnorm(z_scores) * 100
percentiles
```


:: right ::

- Now let's try some R practice! 
- We will use the dataset "quakes" which contains information about earthquakes, including their magnitudes.
- Imagine you experience an earthquake of magnitude 6. What percentage of earthquakes off the coast of Fiji are less severe than the one you experienced?

---
layout: cover
color: indigo-light
---

# Next time: The Central Limit Theorem & Standard Error!
