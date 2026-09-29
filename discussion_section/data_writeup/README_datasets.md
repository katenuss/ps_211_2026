# PS 211 (Fall 2026) — Discussion-section datasets

Reference for the CSV files in `discussion_section/`. Every file is real, published data, redistributed from an open source (CRAN package, FiveThirtyEight's CC BY 4.0 repository, or the course's own materials). All files load with `read_csv()` and need no cleaning. Prepared Sept 25–26, 2026.

## At a glance

| File | Topic | Unit (one row =) | n | 2-group IV | Paired? | 3+ group IV | Use |
|---|---|---|---|---|---|---|---|
| `candy_data.csv` | Halloween candy preferences | one candy | 85 | nine 0/1 features | no | none | Discussion 4 teaching example |
| `pixar_data.csv` | Pixar films | one film | 22 | `before_2010`, `film_rating` | (metacritic vs. rotten_tomatoes, loosely) | none | Discussions 1–3 |
| `emotion_films_data.csv` | Emotion induction experiment | one participant | 330 | any two films (via `filter()`) | yes: `_before` vs. `_after` | `film` (4) | Write-Up #1 or #2 |
| `media_influence_data.csv` | Presumed media influence experiment | one participant | 123 | `condition`, `gender` | no | none | Write-Up #1 |
| `big_five_data.csv` | Big Five personality (SAPA) | one adult | 2,185 | `gender` | no | `education` (5) | Write-Up #1 or #2 |
| `kids_cognition_data.csv` | Children's cognitive tests (1939) | one child | 301 | `sex`, `grade`, `school` | no | none | Write-Up #1 |
| `sleep_deprivation_data.csv` | Sleep restriction & reaction time | one participant | 18 | none | yes: any two days | days (repeated measures) | Write-Up #1 (paired) or #2 (RM ANOVA) |
| `course_evals_data.csv` | Beauty in the classroom | one course section | 463 | `gender`, `pic_outfit`, `pic_color`, `cls_level`, `ethnicity`, `language`, `cls_credits` | no | `rank` (3) | Write-Up #1 or #2 |
| `protest_data.csv` | Reactions to protesting discrimination | one participant | 129 | none natural (could collapse protest vs. no protest) | no | `condition` (3) | Write-Up #2 |

Design note for causal language: the emotion, media-influence, protest, and sleep studies randomly assigned (or experimentally manipulated) their conditions; the Big Five, children's cognition, and course-evaluation data are observational.

---

## candy_data.csv — Halloween candy power ranking

- **Source:** Hickey, W. (2017, October 24). The ultimate Halloween candy power ranking. *FiveThirtyEight*. Data file `candy-data.csv` from github.com/fivethirtyeight/data (CC BY 4.0).
- **Design:** About 8,000 online respondents saw two candies at a time and chose the one they would rather receive; roughly 269,000 matchups in total.
- **Preparation:** `competitorname` renamed to `candy_name`; `sugarpercent` and `pricepercent` rounded to 3 decimals, `winpercent` to 2. Nothing removed. Two "candies" are a dime and a quarter, which FiveThirtyEight included as comparison items; they are kept and pointed out in Discussion 4.
- **Columns:** `candy_name` (text). Nine 0/1 features: `chocolate`, `fruity`, `caramel`, `peanutyalmondy`, `nougat`, `crispedricewafer`, `hard`, `bar`, `pluribus` (comes as a bag of many pieces). `sugarpercent`, `pricepercent`: percentile of sugar content / unit price among these candies (0–1). `winpercent`: percentage of its matchups the candy won (22.5–84.2).
- **Notes:** The 0/1 columns are nominal even though they are numeric; this is the point of Discussion 4 Part 2. No column has three or more levels.

## pixar_data.csv — Pixar films

- **Source:** Course dataset used since Discussion 1; matches the `pixarfilms` R package (Eric Leung), which compiles Wikipedia, Metacritic, and Rotten Tomatoes data.
- **Columns:** `film`, `release_year`, `before_2010` (before_2010 / after_2010), `run_time` (minutes), `film_rating` (G / PG), `metacritic` (0–100), `rotten_tomatoes` (0–100). First column is an unnamed row index.
- **Notes:** 22 films. Used for teaching only; not on the write-up menu.

## emotion_films_data.csv — Emotion induction with film clips

- **Source:** Rafaeli, E., & Revelle, W. (2006). A premature consensus: Are happiness and sadness truly opposite affects? *Motivation and Emotion, 30*(1), 1–12. Also Revelle & Anderson (1997) and Smillie, Cooper, Wilt & Revelle (2012, *JPSP*). Data collected in the Personality, Motivation and Cognition Lab, Northwestern University; distributed as `affect` in the `psychTools` R package (Revelle).
- **Design:** Two studies (`flat`, n = 170; `maps`, n = 160) with the same procedure. Participants completed personality measures (Eysenck Personality Inventory) and a mood questionnaire (Motivational State Questionnaire, MSQ), were randomly assigned to watch one of four 9-minute film clips, then completed the MSQ again.
- **Preparation:** `Film` codes 1–4 relabeled `sad` (Frontline documentary on the liberation of Bergen-Belsen), `horror` (*Halloween*), `neutral` (National Geographic film on the Serengeti), `comedy` (*Parenthood*). Columns renamed from psychTools abbreviations. Dropped: the EPI lie scale, trait and state anxiety, the Beck Depression Inventory (given in one study only), and the morningness questionnaire. No rows removed; no missing values.
- **Columns:** `participant`, `study`, `film`. Personality (EPI subscale scores, count of items endorsed): `extraversion` (0–22 observed), `neuroticism` (0–23), `impulsivity` (0–9), `sociability` (0–13). Mood before and after the film (sums of MSQ items, higher = more): `energetic_arousal_before/after`, `tense_arousal_before/after`, `positive_affect_before/after`, `negative_affect_before/after` (all roughly 0–30).
- **Notes:** True experiment. Independent-samples comparisons use any two films (`filter()` to them); paired comparisons use a `_before` / `_after` pair; Write-Up #2 uses all four films. Group means for `positive_affect_after`: comedy 11.8, neutral 8.8, horror 8.1, sad 7.3.

## media_influence_data.csv — Presumed media influence

- **Source:** Tal-Or, N., Cohen, J., Tsfati, Y., & Gunther, A. C. (2010). Testing causal direction in the influence of presumed media influence. *Communication Research, 37*(6), 801–824 (Study 2). Distributed by Andrew Hayes as `pmi` with *Introduction to Mediation, Moderation, and Conditional Process Analysis* (2018) and as `Tal_Or` in the `psych` R package.
- **Design:** Participants read a news story about an expected sugar shortage and were told (at random) that it would appear on the newspaper's front page or on an inside page, manipulating how much exposure they thought others would have to the story.
- **Preparation:** `cond` 0/1 relabeled `inside_page` / `front_page`; `gender` 1/2 relabeled male / female; other columns renamed. No rows removed.
- **Columns:** `participant`, `condition`, `presumed_media_influence` (mean of 2 items, 1–7: how much the story would influence other people), `issue_importance` (1–7), `intention_to_act` (mean of 4 items, 1–7: intention to buy sugar before the shortage), `gender`, `age` (18–61).
- **Notes:** True experiment, small sample (58 front page, 65 inside page). Effect on `intention_to_act` is modest (3.7 vs. 3.3), a useful contrast to the large emotion-film effects.

## big_five_data.csv — Big Five personality (SAPA project)

- **Source:** 25 IPIP items from the Synthetic Aperture Personality Assessment project (sapa-project.org), distributed as `bfi` in `psychTools`. Cite: Revelle, W., Wilt, J., & Rosenthal, A. (2010). Individual differences in cognition: New methods for examining the personality-cognition link. In A. Gruszka, G. Matthews, & B. Szymura (Eds.), *Handbook of individual differences in cognition* (pp. 27–49). Springer; and the `psychTools` package.
- **Preparation:** Trait scores computed as the mean of five items each (1 = very inaccurate to 6 = very accurate), reverse-keying A1, C4, C5, E1, E2, O2, O5 (7 − x). Kept respondents with all 25 items answered, non-missing gender, education, and age, and age ≥ 18 (2,800 → 2,185). `gender` 1/2 relabeled male / female; `education` 1–5 relabeled some high school / high school graduate / some college / college graduate / graduate degree. `participant` keeps the original row number.
- **Columns:** `participant`, `gender` (1,465 female, 720 male), `education` (5 levels), `age` (18–86), `agreeableness`, `conscientiousness`, `extraversion`, `neuroticism`, `openness` (each 1–6).
- **Notes:** Observational. Large n means small differences are significant; a good place to insist on Cohen's d. Female participants score higher on agreeableness (4.83 vs. 4.40) and neuroticism (3.24 vs. 2.94).

## kids_cognition_data.csv — Holzinger & Swineford (1939)

- **Source:** Holzinger, K. J., & Swineford, F. (1939). *A study in factor analysis: The stability of a bi-factor solution* (Supplementary Educational Monographs No. 48). University of Chicago. Raw scores distributed as `holzinger.raw` in `psychTools` (supplied by Keith Widaman); the nine-test scaled version is `HolzingerSwineford1939` in `lavaan`.
- **Design:** Seventh- and eighth-graders at two schools (Pasteur, Grant-White) took a battery of 26 cognitive tests in 1939.
- **Preparation:** 13 of the 26 tests kept; `school` 0/1 relabeled Pasteur / Grant-White; `female` 1/2 relabeled boy / girl; `age_years` = years + months/12. No rows removed; no missing values in the kept columns.
- **Columns:** `child_id`, `school`, `grade` (7 / 8), `sex`, `age_years` (11.3–16.6). Spatial: `visual_perception`, `cubes`, `lozenges`. Verbal: `general_information`, `paragraph_comprehension`, `sentence_completion`, `word_meaning`. Speeded: `addition_speed`, `counting_dots_speed`. Memory: `word_recognition_memory`, `figure_recognition_memory`. Reasoning: `deduction`, `number_puzzles`. Higher = better on every test. Scores are as recorded in the original study: most are numbers correct, the speeded tests are numbers completed, the memory tests use the study's own scoring, and `deduction` is corrected for guessing (can be negative).
- **Notes:** Observational. No column with three or more groups, so Write-Up #1 only. Eighth-graders outscore seventh-graders on most tests (e.g. `word_meaning` 16.6 vs. 14.1).

## sleep_deprivation_data.csv — Sleep restriction and reaction time

- **Source:** Belenky, G., Wesensten, N. J., Thorne, D. R., Thomas, M. L., Sing, H. C., Redmond, D. P., Russo, M. B., & Balkin, T. J. (2003). Patterns of performance degradation and restoration during sleep restriction and subsequent recovery: A sleep dose-response study. *Journal of Sleep Research, 12*(1), 1–12. Distributed as `sleepstudy` in the `lme4` R package (Bates, Mächler, Bolker & Walker).
- **Design:** The most sleep-deprived group of the original study (3 hours time in bed per night), first 10 days. Days 0–1 were adaptation and training, day 2 was the baseline, and sleep restriction began after day 2. The DV is the average reaction time (ms) on a psychomotor vigilance task each day.
- **Preparation:** Reshaped from long (180 rows) to wide (18 rows, one per participant); reaction times rounded to 0.1 ms; subjects relabeled S1–S18.
- **Columns:** `subject`, `reaction_day0` … `reaction_day9` (ms).
- **Notes:** The menu's clean paired design: compare two days within participants (baseline `reaction_day2` vs. `reaction_day9` is the natural contrast; means 265 vs. 351 ms). For Write-Up #2, days form a repeated-measures factor. Only 18 participants.

## course_evals_data.csv — Beauty in the classroom

- **Source:** Hamermesh, D. S., & Parker, A. (2005). Beauty in the classroom: Instructors' pulchritude and putative pedagogical productivity. *Economics of Education Review, 24*(4), 369–376. Distributed as `evals` in the `openintro` R package (Çetinkaya-Rundel, Diez & Barr).
- **Design:** End-of-semester student evaluations for 463 course sections taught by 94 professors at the University of Texas at Austin. Six students (three male, three female; upper- and lower-level) rated each professor's physical attractiveness from a photograph.
- **Preparation:** Kept 14 of the original 23 columns (dropped the six individual beauty raters and the evaluation-count columns); `bty_avg` rounded to 2 decimals. No rows removed.
- **Columns:** `course_id`, `prof_id` (1–94), `score` (mean evaluation, 1 = very unsatisfactory to 5 = excellent), `bty_avg` (mean of six beauty ratings, 1–10), `rank` (teaching / tenure track / tenured), `gender`, `ethnicity` (minority / not minority), `language` (professor's degree from an English-speaking school: english / non-english), `age`, `cls_students` (class size), `cls_level` (lower / upper), `cls_credits` (one credit / multi credit), `pic_outfit` (formal / not formal), `pic_color` (color / black&white).
- **Notes:** Observational. The same professor contributes several rows, so rows are not fully independent; worth a sentence in the limitations part of a write-up.

## protest_data.csv — Reactions to a woman who protests discrimination

- **Source:** Garcia, D. M., Schmitt, M. T., Branscombe, N. R., & Ellemers, N. (2010). Women's reactions to ingroup members who protest discriminatory treatment: The importance of beliefs about inequality and response appropriateness. *European Journal of Social Psychology, 40*(5), 733–745. Distributed by Hayes (2018) as `protest` and as `Garcia` in the `psych` R package.
- **Design:** 129 women read about a female lawyer (Catherine) passed over for promotion in favor of a less-qualified man, then were randomly assigned to read that she did nothing (`no_protest`), protested on her own behalf (`individual_protest`: "They are treating me unfairly"), or protested on behalf of women (`collective_protest`: "The firm is treating women unfairly").
- **Preparation:** `protest` 0/1/2 relabeled as above; columns renamed; the redundant two-level recoding dropped. No rows removed.
- **Columns:** `participant`, `condition` (41 / 43 / 45), `modern_sexism` (participant's own score on an 8-item Modern Sexism Scale, 1–7; higher = more sexist beliefs), `anger` (anger toward Catherine, 1–7), `liking` (mean of 6 liking items, 1–7), `response_appropriateness` (mean of 4 items, 1–7).
- **Notes:** True experiment with a three-level IV, intended for the Write-Up #2 menu. The published result is an interaction with `modern_sexism`, so simple group differences in `liking` are modest.

---

## How the files were built

All write-up datasets were produced in R (Sept 25–26, 2026) from the package objects named above, with the relabeling, column selection, and row filters described under each file; nothing was edited by hand. `candy_data.csv` came from the FiveThirtyEight GitHub repository. Random subsampling was not used for any file on the current menu.

Files moved out of the menu on Sept 26 (now in `_to_delete/unused_writeup_csvs/`): `penguins_data.csv` (palmerpenguins), `bechdel_data.csv` (FiveThirtyEight), `fastfood_data.csv` (openintro), `spotify_data.csv` (TidyTuesday 2020-01-21 sample). They are clean and could return as non-psychology options.
