# **2011 TOUR Championship**
*Author: Declan Costello*

## **Overview**

Welcome to my analysis of the **2011 TOUR Championship** at [East Lake Golf Club](https://www.eastlakegolfclub.com/course/). With an interest in sports analytics, the primary aspiration is to contribute meaningful insights to the golf community. To get a better feel for the visual details, I encourage you to check out the interactive visuals on  [NBViewer!](https://nbviewer.org/github/dec1costello/Golf/tree/main/TOUR_Championship_2011/)

## **Notes**

- The dataset only contains four rounds of golf from the 30 players who participated.

## **Table of Contents**

1. [Part 1, EDA](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/EDA.ipynb)
2. [Part 2, SG per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/StrokesGainedPerRound.ipynb)
3. [Part 3, SG per Hole per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/ImprovedStrokesGainedPerRoundPerHole.ipynb)
4. [Part 4, SG vs Driving Distance & Accuracy](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb)
5. [Part 5, Distance to Pin vs Strokes to Hole Out](https://github.com/dec1costello/Golf/blob/main/TOUR_Championship_2011/ApproachShots.ipynb)
6. Bayes, approach shot, how close to hole, hiearchal model


## **Part 1, [EDA](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/EDA.ipynb)**

In Part 1, I explore the data and start to feature engineer to help understand, clean, and refine the dataset. It guides model choice and assumption validation, while also revealing insights through visualization. By addressing data quality and understanding patterns early, here I establish a strong foundation for the rest of my project.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Baseball/blob/main/Distance-Predictor/Distance-Predictor-Part-1.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/33e03408-c0f8-485f-88b0-03f1ebc9f143" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **Part 2, [SG per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/StrokesGainedPerRound.ipynb)**

In Part 2, I explore the distribution of Strokes Gained for each round of the Championship. Round 3 seemed to be the most chaotic, as there was a significant variance in player performance throughout the day.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Baseball/blob/main/Distance-Predictor/Distance-Predictor-Part-1.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/09ac3622-d0b1-4f07-b34d-cc907db7a4d5" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **Part 3, [SG per Hole per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/ImprovedStrokesGainedPerRoundPerHole.ipynb)**

In Part 3, I explore the distribution of Strokes Gained for each hole of each round of the Championship.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Baseball/blob/main/Distance-Predictor/Distance-Predictor-Part-1.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/f2c315ab-df87-4b4f-ac78-8ff09e71e66a" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **Part 4, [SG vs Driving Distance & Accuracy](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb)**

In Part 4, I explore the distribution of Strokes Gained vs Driving Distance & Accuracy for each hole of each round of the Championship. Happy to say my analysis aligns with [Data Golf's Course Fit Tool](https://datagolf.com/course-fit-tool) for East Lake Golf Club.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/d08949ca-cf85-450b-b1a8-1054115a4781" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **Part 5, [Distance to Pin vs Strokes to Hole Out](https://github.com/dec1costello/Golf/blob/main/TOUR_Championship_2011/ApproachShots.ipynb)**

In Part 5, I explore the relationship between Distance to the Pin & Lie vs Strokes to hole out at the Tour Championship.

<table>

<tbody>
  <tr>
    <td>
      <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb">
        <img src="https://github.com/dec1costello/Golf/assets/79241861/5f10c32c-7854-47ad-b78e-fab15c3450d1" />
      </a>
    </td>
</tr>
</tbody>
</table>

## **TODO**
- lazy predict
- optuna
- stack
- player and holes plottable, greens in reg
- streamlit
