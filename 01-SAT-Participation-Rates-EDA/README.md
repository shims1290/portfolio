<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# Project 1: Standardized Test Analysis
## Problem Statement

In this exploratory study, we deep dive into the 2017 and 2019 datasets to study how participation rates in SAT and ACT have changed at the state-level. The findings from this exploratory study serve to identify:

- **States with scope for increase in future SAT participation rates.** This could apply to states with i) an increased participation in SAT and ii) a decreased participation rate for ACT in 2019.
- **States with low average SAT total score.** It will be useful to identify such states so that College Board can better target marketing and/or partnership efforts to improve students' access to the test preparation materials in the relevant states. This effort is aligned with College Board's mandate to expand students' access to higher education. 

## Contents:
- [Background](#Background)
- [Data](#Data)
- [Summary Statistics](#Summary-Statistics)
- [Recommendations](#Recommendations)

### Background

College Board is an American nonprofit organisations formed to expand access to higher education. It develops and administers SAT, a standardised test, to promote college-readiness as part of the college admission process ([*source*](https://en.wikipedia.org/wiki/College_Board)). 

Apart from the SAT, ACT is another major standardized test administered by Act Inc to assess high school students' academic achievement and college readiness. 

Students' test scores from either ACT and/or SAT are used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). Students who fare better on the tests would obtain higher scores. Both tests have different score ranges as listed below:
* SAT total scores range from 400 to 1,600 
* ACT composite scores range from 1 to 36

> #### As of 2019, the SAT is officially more popular than the ACT with 55% of the market share (see graph below). More than 2.2 million students in the class of 2019 took the SAT compared to about 1.8 million students who took the ACT ([*source*](https://theolivebook.com/sat-vs-act-which-is-more-popular/)). 

The increase in market share enjoyed by SAT in years leading up to 2019 may be attributed to SAT's efforts to revamp its test contents. At the same time, SAT's partnership with Kahn Academy to offer free test preps and increased direct-to-state marketing efforts have also seemed to pay off. By 2018, College Board had won ten state contracts, including three formerly held by ACT ([*source*](https://www.zippia.com/college-board-careers-19597/history/)). State partnerships are crucial in influence the state participation rates in both standardised tests. State policies, in terms of mandating the standardised test(s) or providing the test for free can affect the test participation rates significantly.

### Data

We use the following datasets to study how participation rates and mean scores for SAT and ACT have changed across various states from 2017 and 2019. 

State-level ACT participation rates and mean scores data
* [`act_2017.csv`](./data/act_2017.csv)
* [`act_2019.csv`](./data/act_2019.csv)

State-level SAT participation rates and mean scores data
* [`sat_2017.csv`](./data/sat_2017.csv)
* [`sat_2019.csv`](./data/sat_2019.csv)

### Summary Statistics 

**Key Observations for SAT**

- The **average SAT participation rate across states increased by 9%-pts in 2019** (up from 39% in 2017).
- In the same time period, the **average SAT total score fell by 14 pts** (down from 1130 in 2017).

### Recommendation

1) Many states with low participation rates in SAT in 2019 had high participation rates in ACT. To boost participation rates going forward, **College Board can first target marketing or partnership efforts in the states that had shown a notable decline in their ACT participation rates**:

 >Missouri, Alaska, Minnesota, South Dakota
 
2) With the decline in mean SAT test scores across states in 2019, College Board should focus on improving students' access to test preparation resources so that students could achieve better test performance in the future. To start, **College Board can target the states with 100% SAT participation rates in 2019, but lower mean SAT total scores than the overall mean of all states**: 

 >Delaware, Idaho, Rhode Island, Florida, Michigan, Illinois, Colorado, Connecticut
 
