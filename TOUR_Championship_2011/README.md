# **2011 TOUR Championship**
*Author: Declan Costello*

## **Overview**

Welcome to my analysis of the **2011 TOUR Championship**. With an interest in sports analytics, the primary aspiration is to contribute meaningful insights to the golf community. To get a better feel for the visual details, I encourage you to check out the interactive visuals on  [NBViewer!](https://nbviewer.org/github/dec1costello/Golf/tree/main/TOUR_Championship_2011/)

## **Notes**

- The dataset only contains four rounds of golf from the 30 players who participated.

## **Table of Contents**

1. [Part 1, EDA](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/EDA.ipynb)
2. [Part 2, SG per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/StrokesGainedPerRound.ipynb)
3. [Part 3, SG per Hole per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/ImprovedStrokesGainedPerRoundPerHole.ipynb)
4. [Part 4, SG per Player]()
5. [Part 5, Approach Shots]()
6. [Part 6, Acc Distributions]()
7. [Part 7, Mapping Viz]()
8. Bayes (use all above dists and eda for a pymc model)


## **Part 1, [EDA](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/EDA.ipynb)**

In Part 1, I explore the data and start to feature engineer to help understand, clean, and refine the dataset. It guides model choice and assumption validation, while also revealing insights through visualization. By addressing data quality and understanding patterns early, here I establish a strong foundation for the rest of my project.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Baseball/blob/main/Distance-Predictor/Distance-Predictor-Part-1.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/c0c4d275-2596-49ee-b515-b8794c7bead9" />
      </a>
    </td>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Baseball/blob/main/Distance-Predictor/Distance-Predictor-Part-2.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/c0c4d275-2596-49ee-b515-b8794c7bead9" alt="WOBA Heatmap" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **TODO**
- [Rough vs Fairway]()

- [Bayes Putting for this tourney](https://www.pymc.io/projects/examples/en/latest/case_studies/putting_workflow.html#id1)

- [Do Birdies follow Bogies?]()
  - previous shot future shot relationship? make a model
