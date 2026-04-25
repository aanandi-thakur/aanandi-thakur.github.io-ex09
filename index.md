---
# Do not edit the text between these lines!
layout: default
---

# EX09: COMP110 Continuous Improvement Analysis

<!-- This is a comment. Below, you'll see code for inserting an image. To make this image appear, update <custom-path>. To add an image, save it inside the imgs folder of this repository. -->
<img src="/aanandi-thakur.github.io-ex09/static/imgs/logo.png" alt="Image of Comp110 rainbow logo. "  width="500"/>

## The idea I'm proposing

**The course should offer an optional one-week pre-semester bootcamp** for students who enter COMP110 with little or no prior programming experience.

The reason is because students who report "None to less than one month" of prior programming experience are by far the single largest group in the class, so any improvement aimed at them touches the majority of students.

## Summary of the analysis

I combined the responses from `survey_izzi.csv` and `survey_alyssa.csv` (764 total responses), narrowed the table down to the columns relevant to this question (`prior_exp`, `difficulty`, `understanding`, `pace`, `would_recommend`, `ls_effective`, `oh_visits`), and used the `data_utils` functions I implemented (`read_csv_rows`, `columnar`, `concat`, `select`, `head`, `count`, plus a custom helper `group_average`) to prep the data for plotting and to print numeric summaries.

The analysis question: **do students entering COMP110 with no (or very little) prior programming experience report a meaningfully harder experience than students with more background?** 

## Visualizations

### 1. Where students start: distribution of prior programming experience

The "None to less than one month" bucket dominates the class with 478 of 764 respondents (≈63%). The next largest bucket, "2-6 months," accounts for 184 responses. So the "typical" COMP110 student is essentially a beginner, and an intervention aimed at beginners is not a niche fix.

<img src="/aanandi-thakur.github.io-ex09/static/imgs/01_prior_exp_distribution.png" alt="Bar chart showing that the 'None to less than one month' bucket is the largest group of COMP110 respondents, with 478 students out of 764 total." width="800"/>

### 2. Perceived difficulty drops as prior experience grows

A box plot of the 1–7 difficulty rating against `prior_exp` shows a clear  trend. Mean difficulty falls from **4.56** for the no-experience group to **2.20** for the "Over 2 years" group, with every intermediate bucket also stepping down. The students with the least background are the ones reporting the hardest experience.

<img src="/aanandi-thakur.github.io-ex09/static/imgs/02_difficulty_by_prior_exp.png" alt="Box plot of difficulty rating by prior programming experience, showing the median difficulty drops as prior experience increases." width="800"/>

### 3. Self-reported understanding moves the opposite direction

A bar plot of mean understanding (1–7) by `prior_exp` shows the inverse pattern. Mean understanding climbs from **4.01** for the no-experience group to **5.87** for the most experienced group. So beginners find the course harder *and* feel they understand it less.

<img src="/aanandi-thakur.github.io-ex09/static/imgs/03_understanding_by_prior_exp.png" alt="Bar chart showing that mean self-reported understanding increases steadily with more prior programming experience." width="800"/>

### 4. Pace and understanding, jointly

A scatter of `pace` vs. `understanding`, colored by `prior_exp`, lets us look at the two patterns together. Beginner responses cluster in the lower-right (high pace, low understanding) corner of the chart; the most experienced students cluster in the upper-left (comfortable pace, high understanding) corner. My custom `group_average` helper confirms this numerically: mean pace is **4.77** for beginners versus **3.13** for the most experienced group.

<img src="/aanandi-thakur.github.io-ex09/static/imgs/04_pace_vs_understanding.png" alt="Scatter plot of pace rating against understanding rating, colored by prior programming experience, showing beginners cluster in the high-pace, low-understanding region." width="800"/>

## Final conclusions

Across four independent views (distribution of experience, difficulty, understanding, and pace) students who enter with little or no prior programming experience consistently report the toughest version of the course. Because that group is also the majority of the class, my proposed intervention has a wide reach.

**Extensions worth exploring.** A follow-up is to pair this analysis with `oh_visits`, `ls_effective`, and `tutoring_effective` to see whether beginners who already engage with existing support close some of the gap on their own. This would tell us whether expanding existing resources is enough, or whether a new beginner-focused program is actually needed. 

**Costs and trade-offs.** A pre-semester bootcamp costs staff time, TA hours, and student time before classes begin, which may not be feasible for students who work, commute, or arrive on campus late. Also, this analysis is based on self-reported survey data, so students who felt most lost may also have been less likely to finish the survey, which would understate (rather than overstate) the size of the gap.