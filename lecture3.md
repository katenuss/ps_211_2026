---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 3
exportFilename: ps211_fall2026_lecture3
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 3: Frequency distributions & visual displays of data

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::

- R and R Studio will be used in every ==discussion sections==!
- You should now have them installed. If not, please come to office hours. 
- Office hours: Tuesdays, 8:45 – 10:45 a.m. (Kate); Wednesdays, 2:30 - 3:30 p.m. (Rola)
- By the end of next discussion section, you should be 100% comfortable opening, saving, and using .Rmd files. 
- You can continue to work on the worksheets outside of class. Remember, there is no homework for this course, so this is your practice with the concepts. 
- Exams: Conceptual only, no coding! BUT, you will need to interpret code output.

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">You'll see a little R code in today's slides — it's just a preview. You'll get hands-on practice in discussion section, so no need to memorize anything today.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Review: Two branches of statistics

:: left ::

**Descriptive statistics** 
- Organize, summarize, and communicate numerical information

<p v-click>

<img src="/images/lecture3/tooth_hist.png" alt="tooth hist" class="mx-auto" />

</p>

:: right ::

**Inferential statistics**
- Use sample data to make inferences about a larger population

<p v-click>

<img src="/images/lecture3/tooth_scatter.png" alt="tooth scatter" class="mx-auto" />

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Descriptive statistics

:: content ::

- Descriptive stats allow us to summarize the characteristics or properties of a distribution of data.
    - They enable us to describe our *sample* or *population*.

<br> 

- There are many ==correct== ways to present the same data.
    - Our job is to choose the ways that are most ==useful==.

<p v-click><SpeechBubble color="amber-light" shape="round" position="br" maxWidth="24rem">Today is all about one big question: How do we turn a pile of numbers into something we can actually see and understand?</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# How should we describe data?

:: left ::

## Raw data
- The original measurements or observations collected in a study.
- Have not been transformed, summarized, or analyzed.

<Admonition title="Question" color="teal-light" width="100%">Why is presenting raw data limiting?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

It's hard to see patterns or make comparisons when looking at a list of numbers. It's generally helpful to organize or summarize them in some way.

</Admonition>


:: right ::

<img src="/images/lecture3/raw_data.png" alt="raw data" class="mx-auto w-1/3" />


---
layout: top-title
color: indigo-light
align: lt
---


:: title ::

# How should we make sense of raw data?

:: content ::

## One way: Frequency distributions
- A **frequency distribution** displays the count (or proportion) of each value — or range of values — in a dataset.
- We can display frequency distributions with:
    - Frequency tables (& grouped frequency tables) — we'll look at these ==briefly==
    - **Histograms** — our main focus today!

<p v-click><StickyNote color="amber-light" title="Why the focus on histograms?" width="60%">Histograms are the foundation for one of the most important ideas in this course: the *distribution*. Understanding them now will pay off all semester.</StickyNote></p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---


:: title ::

# Frequency tables

:: left ::

- A **frequency table** shows how often (frequently) each value occurred.
- Values are listed in one column, and the count of individual scores with that value are listed in the second column.
  - All possible values are listed, even if the count is 0.
- A percentage column is sometimes added: (count / total) × 100.

<p v-click><StickyNote color="green-light" title="In discussion section" width="100%">You'll make frequency tables in R with dplyr's count() function — one line of code!</StickyNote></p>

:: right ::

<img src="/images/lecture3/volcano_frequency.png" alt="volcano frequency" class="mx-auto w-2/3" />

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---


:: title ::

# Grouped frequency tables

:: left ::

- Frequency tables break down when data have **many unique values** (i.e., continuous variables).
  - Listing every value is basically the same as displaying the raw data!
- **Grouped frequency tables** solve this: group values into equal-width intervals (or ==**"bins"**==) and count observations in each bin.
  - Example (right): 100 students' hours of sleep, binned by hour → 8 rows instead of ~100.

<Admonition title="Question" color="teal-light" width="100%" v-click>What is an advantage of grouping values into bins? What is a disadvantage?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Advantage: Easier to see patterns in data with many unique values. Disadvantage: Loss of detail about individual values.

</Admonition>

:: right ::

<div class="text-sm w-5/6 mx-auto" style="line-height:1.2">

**Hours of sleep last night (100 students)**

<table class="compact-table border-collapse w-full text-center">
  <thead>
    <tr>
      <th>Hours of sleep (bin)</th>
      <th>Frequency</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>3 up to 4</td><td>3</td></tr>
    <tr><td>4 up to 5</td><td>8</td></tr>
    <tr><td>5 up to 6</td><td>10</td></tr>
    <tr><td>6 up to 7</td><td>36</td></tr>
    <tr><td>7 up to 8</td><td>29</td></tr>
    <tr><td>8 up to 9</td><td>11</td></tr>
    <tr><td>9 up to 10</td><td>2</td></tr>
    <tr><td>10 up to 11</td><td>1</td></tr>
  </tbody>
  <tfoot>
    <tr><td style="text-align:right;"><strong>Total</strong></td><td><strong>100</strong></td></tr>
  </tfoot>
</table>

<p class="text-xs mt-1 opacity-70">Students reported sleep to the nearest minute (~100 unique values). Each bin is 1 hour wide: "7 up to 8" includes 7.0 but not 8.0, so every value lands in exactly one bin.</p>

</div>

<p v-click><SpeechBubble color="amber-light" shape="round" position="tl" maxWidth="22rem">Remember this word — *bins*! It's about to become very important.</SpeechBubble></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Histograms

:: content ::
- A **histogram** is a graphical representation of a grouped frequency table.
- The x-axis shows the ==bins== (intervals of a continuous variable).
- The y-axis shows the ==frequency== (count) of observations in each bin.
- Each bar *is* a row of the grouped frequency table — drawn instead of listed. (This is the sleep table from the previous slide: the "7 up to 8" row with frequency 29 becomes the bar below.)

<img src="/images/lecture3/hist_anatomy.png" alt="histogram anatomy" class="mx-auto w-3/8" />

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Practice: Reading a histogram

:: left ::

<img src="/images/lecture3/hist_anatomy.png" alt="histogram anatomy" class="mx-auto w-full" />

:: right ::

<Admonition title="Question" color="teal-light" width="100%">How many students slept fewer than 5 hours?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

11 (3 students in the 3-4 bin + 8 students in the 4-5 bin).

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">Can you tell *exactly* how long any individual student slept?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

No! Binning loses detail about individual values — the same trade-off as a grouped frequency table.

</Admonition>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Our data: How tall is the tallest tree?

:: left ::

- Last class, 36 of you guessed the height of the tallest tree in the world (after seeing either a **180 ft** or a **1,200 ft** anchor).
- Here is the (abbreviated) **frequency table** of your guesses: 36 guesses, **25 unique values**.
  - Only the values that occurred are listed — a *complete* frequency table listing every whole number from 90 to 3,000 would have 2,911 rows!

<p v-click><Admonition title="Question" color="teal-light" width="100%">Is this table any easier to read than the raw data?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">Barely. Most values occur once, so the table is nearly as long as the data itself. This is exactly the situation where we need to <em>group</em>.</Admonition></p>

:: right ::

<div class="text-xs w-full" style="line-height:1.15">

**Estimated height (ft) — frequency table**

<div class="grid grid-cols-3 gap-x-4">

<table class="compact-table border-collapse w-full text-center">
  <thead><tr><th>Value</th><th>Freq.</th></tr></thead>
  <tbody>
    <tr><td>90</td><td>1</td></tr>
    <tr><td>145</td><td>1</td></tr>
    <tr><td>185</td><td>1</td></tr>
    <tr><td>190</td><td>2</td></tr>
    <tr><td>200</td><td>2</td></tr>
    <tr><td>210</td><td>2</td></tr>
    <tr><td>215</td><td>1</td></tr>
    <tr><td>231</td><td>1</td></tr>
    <tr><td>250</td><td>2</td></tr>
  </tbody>
</table>

<table class="compact-table border-collapse w-full text-center">
  <thead><tr><th>Value</th><th>Freq.</th></tr></thead>
  <tbody>
    <tr><td>300</td><td>4</td></tr>
    <tr><td>350</td><td>1</td></tr>
    <tr><td>360</td><td>1</td></tr>
    <tr><td>400</td><td>2</td></tr>
    <tr><td>600</td><td>2</td></tr>
    <tr><td>700</td><td>1</td></tr>
    <tr><td>800</td><td>1</td></tr>
    <tr><td>900</td><td>1</td></tr>
    <tr><td>1000</td><td>1</td></tr>
  </tbody>
</table>

<table class="compact-table border-collapse w-full text-center">
  <thead><tr><th>Value</th><th>Freq.</th></tr></thead>
  <tbody>
    <tr><td>1127</td><td>1</td></tr>
    <tr><td>1201</td><td>1</td></tr>
    <tr><td>1500</td><td>2</td></tr>
    <tr><td>1700</td><td>1</td></tr>
    <tr><td>2000</td><td>1</td></tr>
    <tr><td>2500</td><td>1</td></tr>
    <tr><td>3000</td><td>2</td></tr>
    <tr><td></td><td></td></tr>
    <tr><td><strong>Total</strong></td><td><strong>36</strong></td></tr>
  </tbody>
</table>

</div>

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Our data: Grouped frequency table

:: left ::

- Same 36 guesses, now grouped into **250-foot bins**.
- 25 rows became 13 — and a pattern appears: most guesses are **under 500 ft**, with a long tail of much bigger guesses.
- Notice that bins with a count of **0** are still listed — the empty stretches are part of the story.

<p v-click><Admonition title="Question" color="teal-light" width="100%">What did we lose by grouping?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">Individual values. The "0 up to 250" row contains 11 guesses ranging from 90 to 231 ft, but the table can't tell you that.</Admonition></p>

:: right ::

<div class="text-xs w-5/6 mx-auto" style="line-height:1.15">

**Estimated height (ft) — grouped frequency table**

<table class="compact-table border-collapse w-full text-center">
  <thead><tr><th>Height (bin)</th><th>Frequency</th></tr></thead>
  <tbody>
    <tr><td>0 up to 250</td><td>11</td></tr>
    <tr><td>250 up to 500</td><td>10</td></tr>
    <tr><td>500 up to 750</td><td>3</td></tr>
    <tr><td>750 up to 1,000</td><td>2</td></tr>
    <tr><td>1,000 up to 1,250</td><td>3</td></tr>
    <tr><td>1,250 up to 1,500</td><td>0</td></tr>
    <tr><td>1,500 up to 1,750</td><td>3</td></tr>
    <tr><td>1,750 up to 2,000</td><td>0</td></tr>
    <tr><td>2,000 up to 2,250</td><td>1</td></tr>
    <tr><td>2,250 up to 2,500</td><td>0</td></tr>
    <tr><td>2,500 up to 2,750</td><td>1</td></tr>
    <tr><td>2,750 up to 3,000</td><td>0</td></tr>
    <tr><td>3,000 up to 3,250</td><td>2</td></tr>
  </tbody>
  <tfoot>
    <tr><td style="text-align:right;"><strong>Total</strong></td><td><strong>36</strong></td></tr>
  </tfoot>
</table>

</div>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Our data: Histogram

:: left ::

<img src="/images/lecture3/tree_hist_all.png" alt="histogram of tallest-tree guesses" class="mx-auto w-full" />

:: right ::

- The grouped frequency table, **drawn**: 13 bins on the x-axis, one bar per row.
- Empty bins show up as gaps.

<p v-click><Admonition title="Question" color="teal-light" width="100%">Where do the guesses cluster? Is the distribution symmetric?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">Most guesses pile up in the two lowest bins (under 500 ft), close to the real answer. The distribution is lopsided: a handful of very large guesses stretch it far to the right.</Admonition></p>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="22rem">But remember — half of you saw a *different anchor*. Can the histogram show that?</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Our data: Histogram, colored by anchor

:: left ::

<img src="/images/lecture3/tree_hist_by_anchor.png" alt="histogram of tallest-tree guesses colored by anchoring condition" class="mx-auto w-full" />

:: right ::

- Same bins, same bars — but now each bar is **split by anchoring condition** (our IV from last class).
- Coloring by a categorical variable lets one histogram show **two distributions** at once.

<p v-click><Admonition title="Question" color="teal-light" width="100%">What does the coloring reveal that the averages (299 ft vs. 1,579 ft) don't?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">The two groups barely overlap: 21 of 23 low-anchor guesses are under 500 ft, while every high-anchor guess is 600 ft or more. The anchor didn't just nudge the average — it shifted the <em>whole distribution</em>.</Admonition></p>


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Why are histograms so useful?

:: left ::

## One picture shows you everything at once:
- Where scores **cluster** (the center)
- How **spread out** they are
- The **shape**: symmetric? lopsided? two humps?
- **Gaps and outliers**

<div class="flex items-center gap-4 mt-4">
<IceCream :size="80" mood="shocked" color="#FDA7DC" v-click/>
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="20rem" v-click>Summary statistics like the average can hide all of this. Always look at your data!</SpeechBubble>
</div>

:: right ::

<img src="/images/lecture3/hist_shapes.png" alt="same mean different shapes" class="mx-auto w-full" />

<p v-click><Admonition title="Question" color="teal-light" width="100%">All three classes average ≈70%. What does each histogram tell you that the average doesn't?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

Class A: scores cluster symmetrically around 70. Class B: most students scored *below* 70, with a few high scores pulling the average up. Class C: two separate groups — almost nobody actually scored near 70!

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Histograms in the wild

:: content ::

<div class="flex items-center justify-center gap-8">
  <img src="/images/lecture3/histogram1.png" alt="histogram" class="w-1/2" />
  <SpeechBubble color="amber-light" shape="round" position="l" maxWidth="18rem">I made this in R for an actual paper.</SpeechBubble>
</div>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Making a histogram: Choosing the bins

:: content ::

- To make a histogram, you make the same choices as for a grouped frequency table: pick a ==binwidth==, create equal-width bins covering the full range, and count observations in each bin.
- The binwidth **changes what you see**:

<img src="/images/lecture3/hist_binwidths.png" alt="binwidth comparison" class="mx-auto w-4/5" />

<p v-click><StickyNote color="amber-light" title="No single 'right' answer" width="60%">Too narrow = noisy; too wide = patterns hidden. In practice, try a few binwidths and pick one that shows the shape clearly.</StickyNote></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Making a histogram in R

:: content ::

- ggplot2 is a popular R library for creating graphs, including histograms.
- Basic idea:
  - Tell R which dataset to use with `ggplot()`.
  - Use `aes()` to "map" the variable you want on the x-axis.
  - Use `geom_histogram()` to create the histogram — and set the binwidth!

```r
library(ggplot2)

ggplot(data, aes(x = hours_of_sleep)) +
  geom_histogram(binwidth = 1)
```

<p v-click><StickyNote color="green-light" title="In discussion section" width="60%">You'll write and run this code yourselves — today, just notice how the code choices (like binwidth) map onto the concepts we just covered.</StickyNote></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Histograms are for continuous variables

:: content ::

- A histogram *looks* like a bar graph, but **the y-axis always represents frequency or count**, not a separate variable.

<img src="/images/lecture3/bar_vs_hist.png" alt="bar vs hist" class="mx-auto w-1/2" />

==Note: Histograms are for continuous variables only. Classically, the bars should touch to show that the bins are connected intervals on a number line.== 

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# What about non-continuous variables?

:: left ::

- Discrete variables (nominal or ordinal) have frequency distributions too!
- We display them with a ==**bar plot**== of the counts: one bar per category.
- The bars **don't touch** — each category is separate, not an interval on a number line.
- For nominal variables, the order of the bars is arbitrary.

<p v-click><StickyNote color="green-light" title="In R" width="100%">Same ggplot2 logic: swap geom_histogram() for geom_bar().</StickyNote></p>

:: right ::

<img src="/images/lecture3/bar_freq_pets.png" alt="bar plot of pet frequencies" class="mx-auto w-full" />

<p v-click><Admonition title="Question" color="teal-light" width="100%">Why can't we make a histogram of pet type?</Admonition></p>

<p v-click><Admonition title="Answer" color="green-light" width="100%">

There's no number line to divide into bins — the values are categories with no inherent order or spacing.

</Admonition></p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# From histograms to distributions

:: content ::

- A **distribution** describes how the values of a variable are spread or clustered.
- A histogram is a ==picture of a distribution==.
- Imagine collecting more and more data and making the bins narrower and narrower — the jagged bars smooth out into a curve:

<img src="/images/lecture3/hist_to_dist.png" alt="histogram to distribution" class="mx-auto w-4/5" />


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# From histograms to distributions (continued)

:: content ::

<div class="flex items-center gap-4">
<IceCream :size="100" mood="blissful" color="#FDA7DC" />
<SpeechBubble color="amber-light" shape="round" position="l" maxWidth="28rem">This is one of the most important ideas in the whole course: whenever you see a smooth distribution curve, picture the histogram hiding underneath it.</SpeechBubble>
</div>

<br>

- The height of the curve over a range of values ≈ how frequently those values occur.
- Everything we say about distributions from now on — their center, spread, and shape — you can read off a histogram.

<p v-click><StickyNote color="green-light" title="Coming attractions" width="100%">Next week we'll talk about the *normal distribution*. It's just the smooth-curve version of a very common histogram shape!</StickyNote></p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Normal distributions

:: content ::
- A **normal distribution** is a specific type of distribution that is symmetric and bell-shaped.
- We are going to discuss normal distributions much more extensively later in the course.
- For now, just know that many variables in nature and social science tend to follow a normal distribution.

<img src="/images/lecture3/normal_distribution.png" alt="normal distribution" class="mx-auto w-1/2" />



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Skew

:: content ::
- When data are not symmetrically distributed, we say they are **skewed**.
- The ends of the distribution are called the =="tails."==
- **Positively skewed** (or right-skewed) distributions have a long tail on the right side.
- **Negatively skewed** (or left-skewed) distributions have a long tail on the left side.

<img src="/images/lecture3/skew.png" alt="skew" class="mx-auto w-1/2" />


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Positive skew and floor effects

:: content ::
- **Positive skew**: The ==tail== of the distribution extends to the right.
- Sometimes a positive skew can indicate a **floor effect**.
- A **floor effect** occurs when a large number of observations cluster at the lower end of the scale, with few observations at the higher end.


<img src="/images/lecture3/income_dist.jpeg" alt="income distribution" class="mx-auto" style="max-height: 16.5rem" />


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Negative skew and ceiling effects

:: content ::
- **Negative skew**: The ==tail== of the distribution extends to the left.
- Sometimes a negative skew can indicate a **ceiling effect**.
- A **ceiling effect** occurs when a large number of observations cluster at the higher end of the scale, with few observations at the lower end.


<img src="/images/lecture3/retirement_age.png" alt="retirement age distribution" class="mx-auto w-1/2" />



---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Practice: Skew

:: content ::

Consider these three variables: finishing times in a marathon of recreational runners, number of university dining hall meals eaten in a day, and scores on a scale of extroversion from a randomly sampled population.

<Admonition title="Question" color="teal-light" width="100%">Which variable do you think would be most likely to show a positive skew?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Finishing times in a marathon are likely to show a positive skew, as many runners may finish within a certain time range, but a few may take much longer.

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">Which variable do you think would be most likely to be normally distributed?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Scores on a scale of extroversion are often normally distributed in a randomly sampled population, as most people tend to fall in the middle range of extroversion, with fewer people being extremely introverted or extremely extroverted.

</Admonition>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# More practice

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Can nominal variables have a skewed distribution? Why or why not?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

No, nominal variables cannot have a skewed distribution because they represent categories without any inherent order or ranking. Skewness applies to the distribution of ordinal or continuous variables, where the data can be arranged along a scale. (Think of the pet bar plot: rearranging the bars would change its "shape"!)

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">You want to visualize the distribution of ages in a sample of adults. Would you use a frequency table, a grouped frequency table, or a histogram?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A histogram is usually the best choice: age is continuous, and a histogram makes the shape of the distribution visible at a glance. A grouped frequency table contains the same information but is harder to read patterns from.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Moving beyond histograms: More on data visualization

:: content ::
- Histograms and bar plots of frequencies are just some of many ways to visualize data.
- There are **many** other types of graphs that can be useful for different purposes.
- We are going to go through some of them now.
- We will also discuss some general principles of effective data visualization.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Bar graphs

:: left ::

- We've seen bar graphs display *frequencies* of categorical (nominal or ordinal) variables.
- But bar graphs can also display **other measures** on the y-axis — like the average of another variable for each category.
- Each bar represents a category, and the length or height of the bar corresponds to the value it represents.

:: right ::

<img src="/images/lecture3/barplot.png" alt="bar graph" class="mx-auto w-3/4" />

<Admonition title="Question" color="teal-light" width="100%">What is one advantage of using a bar graph? What is one disadvantage?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

One advantage of using a bar graph is that it can display data for different categories side by side, making it easy to compare them. A disadvantage is that it may not show the full distribution of the data.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Scatter plots

:: left ::

- Scatter plots are used to visualize the relationship between two variables.
  - Usually continuous variables, but can also be used with ordinal variables.
- Each point on the graph represents an observation, with its position determined by the values of the two variables.
- Trendlines can be added to show the best-fitting line through the data points, indicating the overall direction of the relationship.
  - We will discuss how to calculate and interpret trendlines later in the course.


:: right ::

<img src="/images/lecture3/scatter_plot.png" alt="scatter plot" class="mx-auto w-1/2" />

<img src="/images/lecture3/scatter_plot2.png" alt="scatter plot" class="mx-auto w-1/2" />


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Scatter plots

:: left ::

<Admonition title="Question" color="teal-light" width="100%">What is one advantage of using a scatter plot?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

One advantage of using a scatter plot is that it can show the relationship between two variables, making it easy to identify trends and correlations. 

</Admonition>

<Admonition title="Question" color="teal-light" width="100%">What is one disadvantage of using a scatter plot?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

A disadvantage is that it can be difficult to interpret when there are many overlapping points, especially without a trendline.

</Admonition>

:: right ::

<img src="/images/lecture3/scatter_plot.png" alt="scatter plot" class="mx-auto w-1/2" />

<img src="/images/lecture3/scatter_plot2.png" alt="scatter plot" class="mx-auto w-1/2" />

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Line graphs

:: left ::

- Some people consider trendlines on scatter plots to be a type of line graph.
- Line graphs are typically used to show ==changes over time== or the relationship between two continuous variables.
- Points are connected by lines to show the trend or pattern in the data.

:: right ::
<img src="/images/lecture3/line_graph.png" alt="line graph" class="mx-auto w-5/6" />

<Admonition title="Question" color="teal-light" width="100%">When does it make sense to connect the points on a graph with lines?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

In psychology, it often makes sense to connect points with lines when the data represent measurements taken over time, such as in longitudinal studies or time-series analyses. 

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Box plots

:: left ::

- Box plots are a standardized way of displaying the distribution of data based on a five-number summary (minimum, first quartile (Q1), median, third quartile (Q3), and maximum).
- They are particularly useful for comparing distributions between several groups or categories.
- Box plots can reveal outliers, which are data points that fall far outside the typical range.
- They provide a visual summary of the central tendency, variability, and skewness of the data.

==Note: We will discuss some of these concepts (like median) in more detail later.==


:: right ::

<img src="/images/lecture3/boxplot.png" alt="box plot" class="mx-auto w-5/6" />

<Admonition title="Question" color="teal-light" width="100%">What is one advantage of using a box plot?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

One advantage of using a box plot is that it provides a clear summary of the distribution of the data, including the median and quartiles. 

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Other visualizations

:: content ::

- There are other ways to visualize data, including:
  - Violin plots
  - Pie charts
  - Heatmaps
  - And many more!


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Principles of effective data visualization

:: content ::

- Choose the right type of graph for your data and the message you want to convey.
- Keep it simple and avoid unnecessary elements that can distract from the main message.

<img src="/images/lecture3/keepitsimple.jpeg" alt="keep it simple" class="mx-auto w-1/2" />


==Graphs can be very misleading! Your goal is to present the data honestly and clearly.== 


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Principles of effective data visualization (continued)

:: content ::

- Use clear labels, titles, and legends to help the audience understand the graph.
- When possible, display the full distribution of data rather than just summary statistics.
  - This is increasingly become a requirement at many journals.

<img src="/images/lecture3/line_graph_individual_points.png" alt="indiv points" class="mx-auto w-1/2" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Keep it simple!

:: content ::

<img src="/images/lecture3/chartjunk1.png" alt="chart junk 1" class="mx-auto w-1/2" />

<Admonition title="Question" color="teal-light" width="100%">What is wrong with this graph?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

The graph is overly complicated and includes unnecessary elements (chart junk) that distract from the main message. As one example: There is no reason for the bars to be different colors.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Keep it simple!

:: content ::

<img src="/images/lecture3/chartjunk2.jpg" alt="chart junk 2" class="mx-auto w-1/3" />

<Admonition title="Question" color="teal-light" width="100%">What is wrong with this graph?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Almost everything. The 3D effect distorts the data and the visuals are distracting.

</Admonition>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Keep it simple!

:: content ::

<img src="/images/lecture3/chartjunk3.png" alt="chart junk 3" class="mx-auto w-1/2" />

<Admonition title="Question" color="teal-light" width="100%">What is wrong with this graph?</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

The visuals are distracting, the grid lines are unnecessary, there is no y-axis label, it is unclear how the image size relates to the data.

</Admonition>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Practice: Choosing the right graph

:: left ::

*For each of the following scenarios, decide which type of graph would be most appropriate (bar graph, scatter plot, or line graph) and explain your choice.*

<Admonition title="Question" color="teal-light" width="100%">Visualizing the relation between hours studied and exam scores for a group of students.</Admonition>

<Admonition title="Question" color="teal-light" width="100%">Visualizing the average monthly temperatures over a year in a specific city.</Admonition>

<Admonition title="Question" color="teal-light" width="100%">Visualizing the number of students in different majors at a university.</Admonition>

:: right ::

<br>
<br>
<br>
<br>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Scatter plot - because both variables (hours studied and exam scores) are continuous, and we want to see the relationship between them.

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Line graph - because we are looking at changes over time (monthly temperatures).

</Admonition>

<Admonition title="Answer" color="green-light" width="100%" v-click>

Bar graph - because we are comparing counts across different categories (majors).

</Admonition>




---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Axes matter!


:: content ::

## Axes can be extremely misleading.
- The choice of scale and range on the axes can dramatically affect how data are perceived.
- Always check the axes to ensure they accurately represent the data.

<br>

**Good website for examples:**

https://callingbullshit.org/tools/tools_misleading_axes.html




---
layout: top-title
color: indigo-light
align: lt
---

:: title ::

# Axes matter: Examples


:: content ::


- Here are some examples of how axes can be manipulated to mislead viewers:

<Admonition title="Question" color="teal-light" width="100%">What is misleading about each of these graphs?</Admonition>

<img src="/images/lecture3/misleading_axes.png" alt="misleading axes" class="mx-auto mt-2" style="max-height: 10rem" />

<Admonition title="Answer" color="green-light" width="100%" v-click>

The y-axis covers a very large range, making differences appear non-existent.

</Admonition>

<p v-click><SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">This is part of why we need statistical tests to determine if differences are "real" or not.</SpeechBubble></p>

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::

# Axes matter: Examples (continued)


:: left ::

<img src="/images/lecture3/misleadingaxes2.png" alt="misleading axes2" class="mx-auto w-3/4" />

<Admonition title="Answer" color="green-light" width="100%" v-click>

The x-axis changes the scale, making the top 1% look more like the top 20%.

</Admonition>

:: right ::

<img src="/images/lecture3/nothing_on_the_axis.jpg" alt="misleading axes3" class="mx-auto w-3/4" />

<Admonition title="Answer" color="green-light" width="100%" v-click>

The y axis is completely meaningless.

</Admonition>

---
layout: cover
color: indigo-light
---

# That's all for Lecture 3!

See you next week. Please remember to:
- Come to office hours if you need help!
- Fill out the anonymous feedback form if you want to share how things are going so far!
