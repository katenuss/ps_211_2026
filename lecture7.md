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
- ==Exam 2== covers Lectures 7-10.
- Exam 2 Review is Tuesday, October 20.
- Exam 2 is Thursday, October 22.
- There are no standalone homeworks this semester. Instead, you'll complete **2 Data Write-Ups** (10% of your grade each):
  - Write-Up 1 (t-test based): due Tuesday, November 17 at 11:59 p.m.
  - Write-Up 2 (ANOVA based): due Tuesday, December 8 at 11:59 p.m.
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate)
- Please bring questions to office hours rather than Slack for anything requiring a longer discussion.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Where we are: the road to Exam 2

:: content ::

Before Exam 1 we learned to **describe** data. For the rest of the course we learn to **draw conclusions** from data. The next four lectures build one idea at a time:

<div class="grid grid-cols-4 gap-3 mt-4 text-sm">
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3"><b>Lecture 7 (today)</b><br/>z scores: how unusual is <i>one score</i>?</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 8</b><br/>The Central Limit Theorem and standard error: how much do <i>sample means</i> bounce around?</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 9</b><br/>z tables: turning "how unusual" into a <i>probability</i></div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 10</b><br/>Hypothesis tests and confidence intervals: is this result more than chance?</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Each lecture leans on the one before it. If a term feels shaky, check the "Key terms" slide at the end of each deck before the next class.</SpeechBubble>
</div>

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Quick recap: the vocabulary we will keep using

:: content ::

<div class="grid grid-cols-2 gap-x-8 gap-y-3 text-base">
<div>

**Population** — everyone we want to know about.<br/>
Its numbers are **parameters**: $\mu$, $\sigma$.

</div>
<div>

**Sample** — the people we actually measured.<br/>
Its numbers are **statistics**: $M$, $s$.

</div>
<div>

**Descriptive statistics** summarize the sample.

</div>
<div>

**Inferential statistics** use the sample to draw conclusions about the population.

</div>
<div>

**Null hypothesis ($H_0$)** — no difference; anything we see is chance.

</div>
<div>

**Research hypothesis ($H_1$)** — there is a real difference.

</div>
</div>

<p v-click><StickyNote color="amber-light" title="The one-sentence version" width="100%">We measure a sample, but we care about the population. Everything between now and Exam 2 is about making that leap carefully.</StickyNote></p>

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

$$ s = \sqrt{\frac{\sum (X_i - M)^2}{N-1}} $$

- Remember: for a **sample** we divide by $N-1$. (Why? Lecture 8.)

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
We covered variance and SD in depth a couple lectures ago. Today we build on that foundation to talk about normal distributions and z-scores.
</SpeechBubble>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Warm-up: check your understanding

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

In a sample of 253 college students, sleep per night has M = 8.0 hours and SD = 1.0 hour. What does the SD tell you?

- **A)** Every student sleeps between 7 and 9 hours.
- **B)** A typical student's sleep is about 1 hour away from the mean.
- **C)** The mean is probably wrong by 1 hour.
- **D)** The range of the data is 1 hour.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** The SD is the typical distance between a score and the mean. It describes how much *individual students* differ from each other.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Which pair of symbols describes a **sample**?

- **A)** μ and σ
- **B)** μ and s
- **C)** M and s
- **D)** M and σ

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** Roman letters (M, s) are statistics computed from a sample. Greek letters (μ, σ) are parameters of a population.

</Admonition></p>

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

<div class="text-xs text-gray-500 mt-2">Data: Duggan & Levitt (2002), <i>American Economic Review, 92</i>(5).</div>


:: right ::

<img src="/images/lecture6/sumo_normal.png" alt="Sumo results normal dist" class="w-1/2 mx-auto"/>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why might the sumo results deviate from a normal distribution?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Sumo wrestlers were throwing matches to help wrestlers who had won 7 matches win their 8th (and have a winning season / advance rounds).

</Admonition></p>


<p v-click>

<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="34rem">
This is also called "anomaly detection" and is used in many fields, including fraud detection.
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Another suspicious distribution: movie ratings

:: left ::

- In 2015, a journalist compared ratings for the **same 146 films** across websites.
- On most sites, ratings spread out: some films are great, some are terrible.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Look at Fandango's distribution. What seems off? Why might a site that <i>sells movie tickets</i> have ratings that look like this?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

No film scored below 3 stars. Fandango was rounding ratings *up*, and it profits when people buy tickets. The shape of the distribution gave it away.

</Admonition></p>

:: right ::

<img src="/images/lecture7/fandango_stars.png" alt="Fandango vs Rotten Tomatoes user ratings" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Hickey, W. (2015). Be suspicious of online movie ratings, especially Fandango's. <i>FiveThirtyEight</i>.</div>

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

$$ s = \sqrt{\frac{\sum (X_i - M)^2}{N-1}} $$

- Remember: for a **sample** we divide by $N-1$. (Why? Lecture 8.)

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

<p v-click><Admonition title="Answer" color="green-light" width="100%">

The mean is **0 standard deviations from the mean**!

</Admonition></p>


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

<p v-click><Admonition title="Answer" color="green-light" width="100%">

If a raw score is 1 SD above the mean, its z score is 1. If a raw score is 2 SDs above the mean, its z score is 2. And so on. Thus, the SD of the z distribution is always 1.

</Admonition></p>


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

**Example:** Researchers tracked the sleep of 253 college students.
- Mean sleep per night = 8 hours
- SD = 1 hour
- You sleep 9 hours
- Your roommate sleeps 8.5 hours
- Your lab partner sleeps 6 hours

<Admonition title="Question" color="teal-light" width="100%">
What is your z score? What is your roommate's z score? What is your lab partner's z score?
</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Your $z = 1$, roommate's $z = 0.5$, lab partner's $z = -2$

</Admonition>

<div class="text-xs text-gray-500 mt-2">Data: Onyper, Thacher, Gilbert, & Gradess (2012), <i>Chronobiology International</i>. Actual values: M = 7.97 h, SD = 0.96 h.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Seeing z scores: a second ruler under the same data

:: left ::

- A z score does not change the data. It **relabels the x-axis**.
- The top ruler is in hours. The bottom ruler is in "SDs from the mean."
- 9 hours and $z = +1$ are the *same place* on the plot.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
A student has z = −2. About how many hours do they sleep? Are they unusual?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

About 6 hours (2 SDs below the mean). Yes: very few students are that far from the mean.

</Admonition></p>

:: right ::

<img src="/images/lecture7/sleep_hist_z.png" alt="Sleep histogram with z-score axis" class="w-full mx-auto"/>

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

**Step 2:** Subtract the mean from your raw score ($X - M$). *This is the distance from the mean.*

**Step 3:** Divide by the standard deviation ($s$). *This converts the distance into "number of standard deviations."*

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
How would we compute a z score for a population instead of a sample?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Use the population mean ($\mu$) and population standard deviation ($\sigma$).

</Admonition></p>

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

<div class="text-xs text-gray-500 mt-4">Data: Helliwell, J., Layard, R., & Sachs, J. (2016). <i>World Happiness Report 2016</i>. Happiness = average life evaluation on a 0 to 10 scale.</div>

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
- SD = 1.138  

$$ X = (0.963)(1.138) + 5.382 \approx 6.48 $$  

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Why is this useful?

:: left ::
- *Z* scores allow comparison across different scales.

**Example:** *Avengers: Age of Ultron* (2015)
- Rotten Tomatoes critics: **74** out of 100
- IMDb users: **7.8** out of 10

*Relative to how each group rates other movies, who liked it more?*

<p v-click>

- Critics: $z = \frac{74-60.8}{30.2} = 0.44$
- IMDb users: $z = \frac{7.8-6.74}{0.96} = 1.10$

</p>

<p v-click>

**Conclusion:** Both rated it above average, but IMDb users liked it more *relative to the other films they rated*.

</p>

:: right ::

<img src="/images/lecture7/avengers_two_scales.png" alt="Avengers on two rating scales" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: 146 films from 2015; Hickey, W. (2015), <i>FiveThirtyEight</i>.</div>

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

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Critic B's ratings are more spread out (higher SD), so a 7/10 is less impressive relative to their average rating than it is for Critic A.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# One More Practice Problem

:: left ::
- Many psychology graduate programs ask for the GRE. It has two main sections, each scored 130 to 170.
- **Verbal:** $\mu = 151.4$, $\sigma = 8.4$
- **Quantitative:** $\mu = 157.6$, $\sigma = 9.9$
- Imagine you score **160 on both sections**.

<Admonition title="Question" color="teal-light" width="100%">
On which section did you do better, <i>relative to other test takers</i>? Calculate a z score for each section.
</Admonition>

<p v-click>

- Verbal: $z = \frac{160 - 151.4}{8.4} = 1.02$
- Quant: $z = \frac{160 - 157.6}{9.9} = 0.24$

</p>

:: right ::

<p v-click>

<img src="/images/lecture7/gre_same_score.png" alt="GRE verbal and quant distributions" class="w-full mx-auto"/>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Verbal. The same raw score (160) is 1 SD above the mean on Verbal but barely above the mean on Quant. A raw score means little until you know the mean and SD of its distribution.

</Admonition></p>

<div class="text-xs text-gray-500 mt-2">Data: ETS, <i>GRE General Test Interpretive Data</i>, test takers July 2022 to June 2025 (N ≈ 790,000).</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Multiple choice practice: Halloween candy

:: left ::

FiveThirtyEight had people choose between pairs of candies 269,000 times. Across 85 candies, win percentage has **M = 50.3** and **SD = 14.7**. Candy corn won **38.0%** of its matchups.

<Admonition title="Multiple choice" color="teal-light" width="100%">

Which equation gives candy corn's z score?

- **A)** (50.3 − 38.0) / 14.7 = 0.84
- **B)** (38.0 − 50.3) / 14.7 = −0.84
- **C)** 38.0 / 14.7 = 2.59
- **D)** (38.0 − 50.3) / 85 = −0.14

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Score minus mean, divided by the SD. The sign matters: candy corn is *below* average, so z is negative. (On the exam you will not need to do the arithmetic, only judge whether the equation is set up correctly.)

</Admonition>

:: right ::

<img src="/images/lecture7/candy_winpercent.png" alt="Candy win percentages" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Hickey, W. (2017). The ultimate Halloween candy power ranking. <i>FiveThirtyEight</i>.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Multiple choice practice: Halloween candy (continued)

:: left ::

<Admonition title="Multiple choice" color="teal-light" width="100%">

Reese's Peanut Butter Cups have z = 2.31. Skittles have z = 0.87. Which statement is correct?

- **A)** Reese's won 2.31% more matchups than the average candy.
- **B)** Reese's win percentage is 2.31 SDs above the mean of all candies.
- **C)** Reese's won 2.31 times as often as Skittles.
- **D)** Skittles are below average because 0.87 is less than 1.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** A z score is a number of SDs from the mean. It is not a percentage or a ratio. Any positive z is above average, so Skittles are above average too.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice" color="teal-light" width="100%">

A candy has a win percentage exactly equal to the mean. What is its z score?

- **A)** 1
- **B)** 50.3
- **C)** 0
- **D)** It cannot be computed.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**C.** The mean is 0 SDs from the mean.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Practice: does standardizing change the shape?

:: left ::

The same 253 college students reported how many alcoholic drinks they have per week. The distribution is **positively skewed**.

<Admonition title="Multiple choice" color="teal-light" width="100%">

If we convert every student's score to a z score, what will the distribution of z scores look like?

- **A)** Normal, because z distributions are normal.
- **B)** Positively skewed, with mean 0 and SD 1.
- **C)** Negatively skewed, because the signs flip.
- **D)** Uniform.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** Standardizing moves the mean to 0 and rescales the SD to 1. It does **not** change the shape. A skewed distribution stays skewed.

</Admonition>

:: right ::

<p v-click>

<img src="/images/lecture7/zscore_same_shape.png" alt="Raw and z-scored drinks distributions" class="w-full mx-auto"/>

</p>

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">You can compute a z score for any distribution. But converting z scores to <i>percentiles</i> (next slide) only works when the distribution is normal.</StickyNote></p>

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

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">We'll practice using z tables to find exact percentiles in an upcoming lecture — for now, focus on the idea that a z score tells you where a score sits in its distribution.</StickyNote></p>

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

<p v-click><StickyNote color="green-light" title="In discussion section" width="100%">You'll get hands-on practice computing z scores and percentiles in R — no need to memorize this code today.</StickyNote></p>

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

**Normal distribution** — bell-shaped, symmetric, unimodal.

</div>
<div>

**Standardization** — converting raw scores to a common scale so we can compare across distributions.

</div>
<div>

**z score** — how many SDs a score is from the mean.<br/> Sample: $z = \frac{X - M}{s}$ &nbsp; Population: $z = \frac{X - \mu}{\sigma}$

</div>
<div>

**z distribution** — a distribution of z scores. Mean = 0, SD = 1. Same shape as the raw scores.

</div>
<div>

**Raw score from z** — $X = z \times SD + M$.

</div>
<div>

**Percentile** — the percentage of scores below a given score. If the distribution is normal, a z score tells you the percentile.

</div>
</div>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">Today, z scores told us how unusual <i>one score</i> is. Next time: how unusual is a <i>sample mean</i>? That requires one new idea, the standard error.</StickyNote></p>

---
layout: cover
color: indigo-light
---

# Next time: The Central Limit Theorem & Standard Error!
