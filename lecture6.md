---
colorSchema: light
routerMode: hash
layout: cover
color: indigo-light
theme: neversink
mdc: true
neversink_slug: PS 211 - Lecture 6
exportFilename: ps211_fall2026_lecture6
---

# PS 211: Introduction to Experimental Design
## Fall 2026 · Section C1
### Lecture 6: Sampling, Probability & Intro to Hypothesis Testing

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders

:: content ::
- Remember: there is no standalone homework this year. Instead, you'll complete two Data Write-Ups later in the semester (the first is t-test based, due Monday, Nov. 16; the second is ANOVA based, due Monday, Dec. 7).
- Discussion sections are using time for in-class R practice — take advantage of it!
- Office hours: Tuesdays 12:30-1:30pm and Thursdays 9:00-10:00am.
- We are going to go over some more information about how to use **R** and **R Studio** today.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Updates and reminders (continued)

:: content ::
- ==Exam 1== is scheduled for **Tuesday, September 29** during our regular class time.
- Exam 1 will cover Lectures 1–6.
- I will post a review sheet with a list of all the topics the exam will cover.
- You can print this review sheet and take hand-written notes on it (both sides) to use during the exam.
- Alternatively, you can write your own notes on a blank sheet of paper (both sides).
- You will *not* be tested on R code, but you should be able to interpret plots and output from R. For example, we may show you a histogram or frequency table created in R and ask you questions about them.
- The class before the exam (**Thursday, September 24**) will be a review session.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Before we begin discussing sampling and probability...

:: content ::
- Resolving key points of confusion about R:
    - Opening and closing R Studio without losing work.
    - Files: .R, .Rmd, .Rproj, .html, .pdf. *What are they and when to use each?*
    - Saving your work: saving code vs. workspace variables.

<img src="/images/lecture5/help_meme.jpg" alt="help" class="mx-auto w-1/3" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Quick recap: Variance and SD

:: content ::
- **Variance** = the average squared deviation of scores from the mean.
- **Standard deviation (SD)** = the square root of the variance — the typical amount scores deviate from the mean.
- For **samples**, we divide by $N-1$ instead of $N$ (Bessel's correction) to get an unbiased estimate of the population variance.

<SpeechBubble color="amber-light" shape="round" position="bl" maxWidth="24rem">
We covered variance and SD in depth last time — if any of this feels shaky, review Lecture 5 before the exam!
</SpeechBubble>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# New stuff! Sampling and probability

:: content ::
- Now that we understand variance and SD, we can see **why sampling matters.**
- We will also discuss **probability**, which is the foundation of inferential statistics.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Why do we sample?

:: content ::
- We usually want to know about a **population** (e.g., all college students).
- But we can't measure everyone, so we take a **sample** (e.g., 20 BU students who participate in a study).
- We use the sample to estimate population parameters (e.g., mean, variance).
- We also use samples to test general hypotheses about broader populations. Inferential statistics lets us do this!


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Two main types of samples in Psychological Science

:: left ::
- **Random Sample:** Every member of the population has an equal chance of being selected.
    - Advantage: More representative.
    - Disadvantage: Expensive, often impossible.

:: right ::
- **Convenience Sample:** Uses participants who are readily available.
    - Common in psychology (e.g., Psych 101 students).
    - Easier and cheaper, but may introduce bias.


---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Examples: Samples in Psychological Studies

:: left ::

<img src="/images/lecture5/participants_methods.png" alt="participant sample" class="mx-auto w-3/4" />

<Admonition title="Question" color="teal-light" width="100%">Is this a random or convenience sample? How do you know?</Admonition>

<p v-click>

**Answer:** This is a convenience sample. The participants volunteered to take part in the study, and they were recruited through flyers and online postings. This means they were not randomly selected from the general population.
</p>

:: right ::

<p v-click>

*A researcher wants to study whether giving BU students free coffee improves their mood. They randomly select 50 students from the entire BU student directory to participate in the study.*

</p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">Is this a random or convenience sample? How do you know?</Admonition>
</p>

<p v-click>

**Answer:** This is a random sample. The researcher randomly selected participants from the entire BU student directory, giving every student an equal chance of being chosen.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Random Sampling: One way to do it

:: content ::
- Use a computer program to generate random numbers.
- Use those numbers to select participants from a list.

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">You use a computer program to randomly select 10 students from your 100-person Psych 101 class to participate in a study. Your computer spits out the following numbers: 1, 2, 3, 4, 44, 56, 57, 58, 83, 99. They don't look very random to you. Should you re-run the program to get a different set of numbers?</Admonition>
</p>

<p v-click>

**Answer:** No! Randomness can produce streaks or clusters of numbers. The set of numbers you got is just as random as any other set.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Convenience Sampling

:: content ::
- In practice, true random samples are rare.
- Psychologists often rely on **convenience samples**.
- Example: Volunteer samples (people who sign up for studies).
    - Benefits: Motivated and willing participants.
    - Downsides: Self-selection bias. The people who volunteer may differ from those who don't.

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Generalizability & External Validity

:: left ::
- **Generalizability** = how well findings from a sample apply to a population.
- Also called **external validity.**
- Critical for psychology: a study that doesn't generalize may have little impact.
- Convenience samples may limit generalizability.

:: right ::

<img src="/images/lecture5/weird_science.png" alt="weird psychology" class="mx-auto w-1/2" />

<p v-click>

Stats from Arnett (2008):
- From 2003‐2007, ==68%== of subjects in psychology studies in top journals came from the US.
- ==96%== came from from Western industrialized countries.  
- In the *Journal of Personality and Social Psychology*, ==67%== of the American samples were composed of undergraduates in psychology courses.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Modern Sampling Techniques

:: content ::
- Online crowdsourcing solicits input from a large group of people.
- There are many online platforms for this:
    - e.g., Amazon Mechanical Turk (MTurk), Prolific, Qualtrics Panels.
- Participants sign up to complete surveys or tasks for pay.
- These platforms provide access to large, diverse samples quickly and cheaply.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Crowdsourcing

:: content ::

<Admonition title="Question" color="teal-light" width="100%">What are some potential advantages and disadvantages of using crowdsourcing platforms for research?</Admonition>

<p v-click>

**Advantages:**
- Access to a large and diverse participant pool.
- Cost-effective and time-efficient.
- Ability to reach participants from various geographic locations.

**Disadvantages:**
- Potential for low-quality data (e.g., inattentive respondents).
- Limited control over the research environment.
- Limited types of data can be collected (e.g., no brain imaging)

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Random Assignment

:: content ::
- **Random sampling**: Selecting participants for a study.
- **Random assignment**: Assigning participants to conditions within a study.
- Ensures every participant has an equal chance of being in any condition (i.e., level of the independent variable).

<Admonition title="Question" color="teal-light" width="100%">Why should researchers care about random assignment if they don't seem to care about random sampling?</Admonition>

<p v-click>

**Answer:** Random assignment helps to reduce the risk of confounding variables by ensuring that the groups are comparable at the start of an experiment. This is important for understanding causality even if the sample itself is not representative of the broader population.

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Example: Random Assignment

:: content ::
- Imagine you want to run a between-subjects version of the Stroop task.
- You decide to run this experiment on your PS 211 classmates.
- You divide the class into two groups:
    - Group 1: Congruent condition. (e.g., the word "red" printed in red ink).
    - Group 2: Incongruent condition. (e.g., the word "red" printed in blue ink).
- You assign the first 10 students who arrive to Group 1, and the next 10 to Group 2.

<Admonition title="Question" color="teal-light" width="100%">Is this a good method of random assignment? Why or why not?</Admonition>

<p v-click>

**Answer:** No, this is not a good method of random assignment. Assigning students based on their arrival order can introduce bias, as early arrivers may differ systematically from later arrivers (e.g., in motivation or punctuality). 

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Review: Descriptive vs. Inferential Statistics

:: content ::
- **Descriptive stats:** Summarize data from a sample. "Describe" the sample.
    - Examples: "The average amount of sugar in the five drinks I tried from Starbucks is 30 grams."

- **Inferential stats:** Allow us to draw conclusions about populations from samples.
    - Examples: "Based on my sample, I estimate that the average amount of sugar in all Starbucks drinks is between 20 and 50 grams."


<p v-click>

- But ... how do we ensure that these inferences are valid? **Probability!**

<img src="/images/lecture5/coin_flip.jpg" alt="coin" class="mx-auto w-1/3" />

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability

:: content ::
- **Probability** = the likelihood that a specific outcome will occur, out of all possible outcomes.
- Ranges from 0 (impossible) to 1 (certain).
- Example: Probability of flipping heads on a fair coin = 0.5.
- Probability helps us understand and quantify uncertainty.
- **Experimental probability** = relative frequency of an outcome in repeated trials.
- **Theoretical probability**= based on known possible outcomes (e.g., coin flips, dice rolls).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability Terms

:: content ::
- **Trial:** Each repetition of an event or each occasion a procedure is carried out (e.g., a dice roll).
- **Outcome:** Result of the trial.
- **Success:** The outcome of interest (e.g., heads).

<Admonition title="Question" color="teal-light" width="100%">If you want to determine the probability of a coin landing on heads, what is a trial, an outcome, and a success?</Admonition>

<p v-click>

**Answer:**
- Trial: Each flip of the coin.
- Outcome: The result of the coin flip (either heads or tails).
- Success: The coin landing on heads.
</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Independent Trials

:: content ::
- Independent = one trial's outcome does not affect another.
- Example: slot machines, coin flips.
- Yes, rare streaks can occur!

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability: Our intuitions are bad!

:: content ::
- We are generally bad at intuitively grasping probability.
- We see patterns where none exist (e.g., gambler's fallacy).
- We overestimate the likelihood of vivid events (e.g., shark attacks).
- We underestimate the likelihood of common events (e.g., car accidents).
- We notice evidence that confirms our beliefs, and ignore contrary evidence (confirmation bias).

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability intuitions: The birthday paradox

:: content ::
- What's the probability that two people in this class of 45 have the same birthday (out of 365 days)?

<Admonition title="Question" color="teal-light" width="100%">What do you think the answer is closest to: 1%, 10%, 30%, 50%, 70%, or 90%?</Admonition>

<p v-click>

**Answer:** The probability is surprisingly high! It's actually 94.1%. 

Probability that at least two people share a birthday in a group of 45 is calculated using the complementary probability that no one shares a birthday, which is then subtracted from 1.

- Probability that no one shares a birthday:
  $$ P(\text{no shared birthday}) = \frac{365}{365} \times \frac{364}{365} \times \frac{363}{365} \times ... \times \frac{321}{365} $$ 

</p>


---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability is important for ... hypothesis testing!

:: content ::
- Hypothesis-testing: Using sample data to evaluate two competing hypotheses about a population.

*Example: Are students who take PS 211 happier than other BU students?*

Experiment: 
- Administer survey measuring happiness (scale 1-10) to a random sample of 10 PS 211 students and a random sample of other BU students.
- Results: PS 211 students: ${8, 7, 9, 6, 8, 7, 9, 10, 8, 7}, M = 8.0$ 
- Other BU students: ${5, 6, 4, 5, 6, 5, 4, 5, 6, 5}, M = 5.0$

<Admonition title="Question" color="teal-light" width="100%">Are the 10 students in PS 211 on average happier than the 10 other BU students?</Admonition>

<p v-click>

**Answer:** Yes, we can draw that conclusion about the sample based on the sample means (assuming we believe our survey is valid and reliable).

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Probability is important for ... hypothesis testing!

:: content ::

<Admonition title="Question" color="teal-light" width="100%">Can we conclude that PS 211 students are happier than other BU students? Why or why not?</Admonition>

<p v-click>

**Answer:** We cannot conclude that PS 211 students are happier than other BU students based solely on this sample. The observed difference in means could be due to random chance, especially given the small sample sizes. We need to conduct a hypothesis test to determine if a real difference likely exists in the population.

</p>

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
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Hypothesis Testing: Examples

:: content ::

<Admonition title="Question" color="teal-light" width="100%">In the PS 211 happiness example, what are the null and research hypotheses?</Admonition>

<p v-click>

**Answer:**
- Null Hypothesis (H₀): There is no difference in happiness levels between PS 211 students and other BU students.
- Research Hypothesis (H₁): PS 211 students are happier than other BU students.
</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Hypothesis Testing: Examples (Continued)

:: content ::

<Admonition title="Question" color="teal-light" width="100%">In the Stroop task example, what are the null and research hypotheses?</Admonition>

<p v-click>

**Answer:**
- Null Hypothesis (H₀): There is no difference in reaction times between the congruent and incongruent conditions.
- Research Hypothesis (H₁): Reaction times are slower in the incongruent condition compared to the congruent condition.

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Hypothesis Directions

:: content ::
- Both of these examples had ==directional== research hypotheses (PS 211 students are happier; Stroop incongruent is slower).
- Sometimes, we have ==non-directional== research hypotheses (e.g., there is a difference, but we don't know the direction).
- The type of hypothesis affects the type of *significance test* we use. We will cover *significance testing* in more detail later.

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# One-tailed vs. Two-tailed Tests

:: content ::
- **One-tailed test:** Tests for an effect in one direction (e.g., PS 211 students are happier).
- **Two-tailed test:** Tests for an effect in either direction (e.g., there is a difference in happiness, but we don't know which group is happier).
- One-tailed tests have more statistical power, but can miss effects in the opposite direction.

<img src="/images/lecture5/tail_meme.jpg" alt="one two tailed" class="mx-auto w-1/3" />

---
layout: top-title-two-cols
color: indigo-light
align: lt-lt-lt
---

:: title ::
# Rejecting the Null Hypothesis

:: left ::
**The goal of statistics is to determine whether we can reject the null hypothesis.**

- We either reject or fail to reject H₀ based on the data.
- If the data are very unlikely under H₀, we reject H₀ in favor of H₁.
- If the data are not unlikely under H₀, we fail to reject H₀
- We never "accept" H₀, because we can't prove it true.
- We use probability to assess how likely our data are under H₀.


:: right ::
<Admonition title="Question" color="teal-light" width="100%">What's wrong with this statement of experiment results: "PS 211 students are equally as happy as other BU students."?</Admonition>

<p v-click>

**Answer:** This statement suggests that we have proven the null hypothesis (H₀) to be true, which is not possible. We can only fail to reject H₀.

</p>

<p v-click>
<Admonition title="Question" color="teal-light" width="100%">How should we fix it?</Admonition>

</p>

<p v-click>

**Answer:** A better way to state the results would be: "We did not find evidence that PS 211 students are happier than other BU students."    

</p>

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Two ways to be wrong: Type I and Type II Errors

:: content ::
- **Type I error:** Rejecting H₀ when it is true (false positive).
    - "You said PS 211 students are happier, but they aren't."
- **Type II error:** Failing to reject H₀ when it is false (false negative).
    - "You said PS 211 students aren't happier, but they are."
- Both errors have consequences.

<img src="/images/lecture5/errors.png" alt="type 1 type 2" class="mx-auto w-1/2" />

---
layout: top-title
color: indigo-light
align: lt
---

:: title ::
# Type I and Type II Errors: Example

:: content ::

<Admonition title="Question" color="teal-light" width="100%">You have a cough and decide to take a covid test. What is your null and alternative hypothesis?</Admonition>

<p v-click>

**Answer:**
- Null Hypothesis (H₀): You do not have COVID-19. (i.e., you are not 'different' from your usual healthy state)
- Alternative Hypothesis (H₁): You have COVID-19. (i.e., you are 'different' from your usual healthy state)

</p>

<p v-click>

<Admonition title="Question" color="teal-light" width="100%">If the test comes back positive, but you actually don't have COVID-19, what type of error is this?</Admonition>

</p>

<p v-click>

**Answer:** This is a Type I error (false positive). You rejected the null hypothesis (you do not have COVID-19) when it was actually true.

</p>

---
layout: cover
color: indigo-light
---

# That's all for today!
See you Thursday -- we will combine probability with hypothesis testing and inference.
