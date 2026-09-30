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
- Exam 1 grades will be posted next Tuesday (after everyone takes it).
- We will go over difficult questions in class. 
- We will *not* return individual exams, but you are welcome to come to our office hours to see what questions you got wrong.
- The data-writeup assignment was introduced yesterday in your discussions. 
- The due date has shifted -- now due **Nov. 9.** Most work will be completed in discussion section!

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
<div class="border-2 border-indigo-400 bg-indigo-50 rounded-lg p-3"><b>Lecture 7 (today)</b><br/>Z scores: How unusual is <i>one score</i>?</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 8</b><br/>The Central Limit Theorem and standard error: how much do <i>sample means</i> bounce around?</div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 9</b><br/>Z tables: Turning "how unusual" into a <i>probability</i></div>
<div class="border-2 border-gray-300 rounded-lg p-3"><b>Lecture 10</b><br/>Hypothesis tests and confidence intervals: Does this result reflect a true difference in populations?</div>
</div>

<p v-click>

<div class="flex items-center gap-4 mt-6">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="36rem">Each lecture depends on the one before it. If you are still not so sure what a term means, check the "Key terms" slide at the end of each deck before the next class.</SpeechBubble>
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

**Null hypothesis ($H_0$)** — no difference; any difference we observe is due to chance.

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
# Deviations from normality

:: left ::

- We often expect natural patterns to be normally distributed.  
- Deviations from normality can indicate that something is off: *Something* affected the distribution of scores.

:: right ::

<p v-click>

<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="34rem">
Looking for scores that do not fit the expected pattern is called "anomaly detection." It is used in many fields, including fraud detection.
</SpeechBubble>

</p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---


:: title ::
# Cheater detection with normal curves

:: left ::

### Study of sumo wrestlers:
  - In Japanese sumo tournaments, wrestlers compete in 15 bouts each.
  - Wrestlers who finish with a winning record (8 or more wins) rise in the rankings and enjoy greater prestige, higher salaries, etc.

  <p v-click>

  - Over a decade of matches: 
    - 26% finished with 8 wins  
    - 12.2% finished with 7 wins  
  - Expected (if wins are normally distributed): ~19.6% for both outcomes  

</p>

:: right ::

  <p v-click>
<img src="/images/lecture6/sumo_normal.png" alt="Sumo results normal dist" class="w-3/4 mx-auto"/>
<div class="text-xs text-gray-500 mt-2">Data: Duggan & Levitt (2002), <i>American Economic Review, 92</i>(5).</div>

</p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Why might the sumo results deviate from a normal distribution?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Sumo wrestlers were rigging matches to help wrestlers who had won 7 matches win their 8th (and have a winning season).

</Admonition></p>


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
# Seeing z scores: a second ruler under the same data

:: left ::

- Back to the sleep data. What if we convert **every** student's score to a z score?
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

The formula subtracts $M$ from every score, which slides the center of the distribution to 0. The mean is **0 standard deviations from the mean**!

</Admonition></p>


:: right ::
<img src="/images/lecture6/z_dist.png" alt="Z distribution" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">This picture shows raw scores that were normal. Standardizing never changes the shape of a distribution.</div>


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

The formula divides every distance from the mean by $s$. If a raw score is 1 SD above the mean, its z score is 1. If a raw score is 2 SDs above the mean, its z score is 2. And so on. The typical distance from the mean, $s$, becomes $s / s = 1$.

</Admonition></p>


:: right ::
<img src="/images/lecture6/z_dist.png" alt="Z distribution" class="w-full mx-auto"/>


<p v-click>
Understanding a score's relation to the mean of its distribution gives us important information.

</p>

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

<p v-click><StickyNote color="amber-light" title="Heads up" width="100%">You can compute a z score for any distribution. But converting z scores to <i>percentiles</i> (coming up next) only works when the distribution is normal.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# A new question: what percent of scores are below mine?

:: left ::

- ==Percentile==: the percentage of scores **below** a given score.
- You sleep 9 hours. What percent of students sleep less than you?
- When we have the raw data, we can just **count**: 220 of 253 students, or **87%**.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
What if we do not have the raw data? Suppose all we know is that sleep is roughly normal, with M = 8 and SD = 1.
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

We can still get very close, because **every normal distribution has the same shape**. The next four slides build that idea one step at a time.

</Admonition></p>

:: right ::

<img src="/images/lecture7/sleep_percentile_count.png" alt="Sleep histogram with students below 9 hours shaded" class="w-full mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Data: Onyper, Thacher, Gilbert, & Gradess (2012), <i>Chronobiology International</i>.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 1: Every normal distribution has the same shape

:: left ::

- Normal distributions can differ in only two ways:
  - where the center is (the **mean**)
  - how spread out the scores are (the **SD**)
- Measure in "SDs from the mean" and those two differences disappear.
- In **every** normal distribution, about 84% of scores fall below the score that is 1 SD above the mean.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
GRE Verbal scores are roughly normal, with μ = 151.4 and σ = 8.4. About what percent of test takers score below 159.8?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

159.8 is 1 SD above the mean (151.4 + 8.4), so about **84%**. The same answer as for 9 hours of sleep, or for a height of 82.4 inches in the NBA.

</Admonition></p>

:: right ::

<img src="/images/lecture7/normals_same_shape.png" alt="Three normal distributions in different units, each with 84 percent below one SD above the mean" class="w-3/4 mx-auto"/>

<div class="text-xs text-gray-500 mt-2">Means and SDs: Onyper et al. (2012); ETS GRE interpretive data (2022 to 2025); NBA 2018-19 season (openintro). Curves are idealized normal distributions.</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# Step 2: z scores give us one standard curve

:: left ::

- Convert any normal distribution to z scores and you always get the **same** curve.
- Its name: the ==standard normal distribution== (normal shape, mean = 0, SD = 1).
- "Standard" means there is only **one** of it. It does not depend on the units, the mean, or the SD of the raw scores.

<p v-click>

**Why this matters:** the areas under this one curve only had to be worked out once. We can reuse them for sleep, GRE scores, heights, and anything else that is normal.

</p>

:: right ::

<img src="/images/lecture7/normals_to_standard.png" alt="Three normal distributions converted to one standard normal distribution" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 3: The areas under that curve are known

:: left ::

- Area under the curve = percentage of scores.
- 50% of scores fall below $z = 0$ (the mean).
- 84% fall below $z = 1$; 16% fall below $z = -1$.
- 68% fall between $z = -1$ and $z = +1$.
- 95% fall between $z = -2$ and $z = +2$.

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">
Use the figure: where does the 84% come from?
</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

50% of scores are below the mean. Another 34% are between $z = 0$ and $z = 1$. 50% + 34% = 84%.

</Admonition></p>

:: right ::

<img src="/images/lecture7/standard_normal_areas.png" alt="Standard normal curve with the percentage of scores in each band and the percentile at each z score" class="w-full mx-auto"/>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-6-6
---

:: title ::
# Step 4: From a z score to a percentile

:: left ::

1. Convert the raw score to a z score.
2. Find that z score on the standard normal curve.
3. The area to the **left** of it is the percentile.

<p v-click>

**Our example** (sleep: M = 8, SD = 1)
- You, 9 hours: $z = 1$ → about the **84th percentile**
- Lab partner, 6 hours: $z = -2$ → about the **2nd percentile**

</p>

<p v-click><Admonition title="Reality check" color="indigo-light" width="100%">

Counting the real data gave 87% below 9 hours. The curve says 84%. Close but not identical, because real data are only *approximately* normal.

</Admonition></p>

:: right ::

<img src="/images/lecture7/z_to_percentile_examples.png" alt="Standard normal curves shaded below z = 1 and below z = -2" class="w-2/3 mx-auto"/>

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">What about z = 0.5 or z = 1.37? A <b>z table</b> gives the exact percentile for any z score. We'll practice using z tables in Lecture 9. For now, focus on the idea that a z score tells you where a score sits in its distribution.</StickyNote></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Multiple choice practice: z scores and percentiles

:: left ::

<Admonition title="Multiple choice 1" color="teal-light" width="100%">

Scores on a test are normally distributed. Your z score is −1. About what percent of people scored **below** you?

- **A)** 1%
- **B)** 16%
- **C)** 34%
- **D)** 84%

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

**B.** 50% of scores are below the mean, and 34% of scores sit between $z = -1$ and $z = 0$. 50 − 34 = 16. C is the area *between* −1 and 0. D is the percent below $z = +1$.

</Admonition>

:: right ::

<p v-click>

<Admonition title="Multiple choice 2" color="teal-light" width="100%">

Drinks per week is positively skewed (M = 5.6, SD = 4.1). On a normal curve, about 2% of scores fall below z = −2. What percent of these students are below z = −2?

- **A)** About 2%. The landmarks fit any distribution.
- **B)** 0%. z = −2 would be −2.6 drinks per week.
- **C)** About 16%.
- **D)** Can't tell: skewed data have no z scores.

</Admonition>

</p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

**B.** $X = (-2)(4.1) + 5.6 = -2.6$ drinks, and nobody drinks less than 0. Any distribution has z scores (so not D), but the percentages only apply when the raw scores are roughly normal.

</Admonition></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
columns: is-5-7
---

:: title ::
# The big idea: standard distributions

:: left ::

We just used a recipe that the rest of the course repeats:

1. Start with a result in raw units (hours, points, inches).
2. **Standardize** it: convert it to a number that does not depend on the units.
3. Find it on a **standard distribution**: a reference curve whose areas are already known.
4. Read off a percentage: how unusual is this result?

<p v-click>

Only the reference curve changes. Today it is the standard normal. Later it will be a *t* distribution or an *F* distribution.

</p>

:: right ::

<img src="/images/lecture7/reference_curves.png" alt="Three reference distributions: standard normal, t, and F" class="w-full mx-auto"/>

<p v-click>

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="excited" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="26rem">You don't need to know anything about t or F yet. Just remember the recipe: standardize, find your place on a known curve, read the area.</SpeechBubble>
</div>

</p>

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

- `pnorm(z)` gives the area to the **left** of `z` on the standard normal curve.
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

**Standard normal distribution** — what any normal distribution becomes when converted to z scores: normal, mean = 0, SD = 1. Its areas are known in advance.

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
