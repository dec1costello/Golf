<a name="readme-top"></a>
# **2011 TOUR Championship**
*Author: Declan Costello*

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#Overview">Overview</a></li>
    <li><a href="#Notes">Notes</a></li>
    <li><a href="#Pending-Questions">Pending Questions</a></li>
    <li><a href="#EDA">EDA</a></li>
    <li><a href="#SG-per-Round">SG per Round</a></li>
    <li><a href="#SG-per-Hole">SG per Hole</a></li>
    <li><a href="#SG-per-Drive">SG per Drive</a></li>
    <li><a href="#Expected-Strokes-Model">Expected Strokes Model</a></li>
    <li><a href="#xS-Model-Preformance">xS Model Preformance</a></li>
    <li><a href="#SG-per-Player">SG per Player</a></li>
    <li><a href="#SG-per-Location">SG per Location</a></li>
    <li><a href="#Roadmap">Roadmap</a></li>
  </ol>
</details>

## **Overview**

Welcome to my analysis of the **2011 TOUR Championship** at [East Lake Golf Club!](https://www.eastlakegolfclub.com/course/) With an interest in sports analytics, the primary aspiration is to contribute meaningful insights to the golf community. To get a better feel for the visual details, I encourage you to check out the interactive visuals on  [NBViewer!](https://nbviewer.org/github/dec1costello/Golf/tree/main/TOUR_Championship_2011/)

## **Notes**

I chose the **2011 TOUR Championship** because it was the only complete shot level data set I could [find](https://github.com/scottflaska/pga-shotlink/tree/main/data/sample_download). If you see a complete shot level dataset floating around feel free to send it my way!

## **Pending Questions**

- [ ] I'm interested in understanding the correct methodology behind predicting expected strokes. Is it the norm to predict expected strokes using data from that same round because the training data is discrete while the predictions are continuous? Or is there a concern about data leakage, so one would only use training data from prior rounds to predict xS on?
- [ ] Regarding the statistic "% Fairways Hit," If a player hits the green on a par 3 hole, is it the norm to consider this shot as hitting a fairway? Guessing it would if a player drives the green on a par 4 or 5, so maybe par 3s are included as well if thats the case.

## [EDA](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/EDA.ipynb)

In Part 1, I explore the data and start to feature engineer to help understand, clean, and refine the dataset. It guides model choice and assumption validation, while also revealing insights through visualization. By addressing data quality and understanding patterns early, here I establish a strong foundation for the rest of my project.

## [SG per Round](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/StrokesGainedPerRound.ipynb)

In Part 2, I explore the distribution of Strokes Gained for each round of the Championship. Round 3 seemed to be the most chaotic, as there was a significant variance in player performance throughout the day.


<div align="center">
  <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb">
    <img src="https://github.com/dec1costello/Golf/assets/79241861/275e7705-7748-49e2-b9c1-e7b24d40066d" alt="Event Scatter" style="width:100%">
  </a>
</div>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## [SG per Hole](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/ImprovedStrokesGainedPerRoundPerHole.ipynb)

In Part 3, I explore the distribution of Strokes Gained for each hole of each round of the Championship.

<div align="center">
  <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb">
    <img src="https://github.com/dec1costello/Golf/assets/79241861/5fb76665-1de7-4d00-a42d-370c6fc5a987" alt="Event Scatter" style="width:100%">
  </a>
</div>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## [SG per Drive](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb)

In Part 4, I explore the distribution of Strokes Gained vs Driving Distance Gained (DG) and Driving Accuracy Gained (AG) for each drive of the Championship. Happy to say my analysis aligns with [Data Golf's Course Fit Tool](https://datagolf.com/course-fit-tool), in that AG appears to be an important facor for preforming at East Lake Golf Club.
<div align="center">
  <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb">
    <img src="https://github.com/dec1costello/Golf/assets/79241861/2eabd308-cee6-4f72-af2b-6dcea8e6bd86" alt="Event Scatter" style="width:100%">
  </a>
</div>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## [Expected Strokes Model](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb)

In Part 5, I explore the relationship between Distance to the Pin & Lie vs Strokes to hole out at the Tour Championship. I Ensemble the top  preforming models together using a [Stack](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.StackingRegressor.html) to minimize [Bias](https://towardsdatascience.com/a-quickstart-guide-to-uprooting-model-bias-f4465c8e84bc) and [Variance](https://x.com/akshay_pachaar/status/1703757251474063861?s=20). This iterative process maximized predictive accuracy of Expected Strokes(xS)

```mermaid
graph TB
      FeatureEngineeredData --> CategoricalTransformer;
      FeatureEngineeredData --> NumericTransformer;
      CategoricalTransformer --> OneHotEncoder;
      OneHotEncoder --> Stratify;
      NumericTransformer --> RobustScaler;
      RobustScaler --> Stratify;

      Stratify-->RandomForestRegressor;
      Stratify-->MLPRegressor;
      Stratify-->GradientBoostingRegressor;
      Stratify--> AdaBoostRegressor;
      Stratify--> LGBMRegressor;

      LGBMRegressor-->GBR_StackingRegressor;
      AdaBoostRegressor-->GBR_StackingRegressor;
      GradientBoostingRegressor-->GBR_StackingRegressor;
      RandomForestRegressor-->GBR_StackingRegressor;
      MLPRegressor-->GBR_StackingRegressor;

      GBR_StackingRegressor --> Prediction;
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>



## [xS Model Preformance](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb)

These charts help evaluate the model by showing how predicted values compare to actual ones and revealing patterns in prediction errors. The "Predicted vs Actual" chart checks overall accuracy, while the "Predicted vs Residual" chart highlights patterns in errors. The histogram in "Normality of Residuals" assesses if errors follow a normal distribution, crucial for reliable predictions.
<div align="center">
  <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb">
    <img src="https://github.com/dec1costello/Golf/assets/79241861/a2d6a9bb-096f-44c5-9534-3e5275921f71" alt="Event Scatter" style="width:100%">
  </a>
</div>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## [SG per Shot](https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/DGvsCG.ipynb)

Now that we have a reliable model, we can use it to identify strengths and weaknesses for a player by subtracting Expected Strokes from the result of each shot. This plot displays Baddeley's strokes gained (SG) by shot type, providing a clear visualization of his performance across different lies and distances.
<div align="center">
  <a href="https://nbviewer.org/github/dec1costello/Golf/blob/main/TOUR_Championship_2011/xSG.ipynb">
    <img src="https://github.com/dec1costello/Golf/assets/79241861/8f8081f4-ed9b-4b79-9da7-76d4ae767f7b" alt="Event Scatter" style="width:100%">
  </a>
</div>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [x] xS Stack Model Refinement
    - [x] Create seperate putting model
    - [ ] MLFlow
        - [ ] [Refer To](https://medium.com/infer-qwak/building-an-end-to-end-mlops-pipeline-with-open-source-tools-d8bacbf4184f)
        - [ ] [Watch](https://www.youtube.com/watch?v=-7XegzgjgM0&list=PLQqR_3C2fhUUkoXAcomOxcvfPwRn90U-g&index=8)
        - [ ] [Utilize](https://community.cloud.databricks.com/?o=5379878152283690)  
    - [ ] Drift Detection
        - [ ] [Evidently](https://www.youtube.com/watch?v=L4Pv6ExBQPM)
        - [ ] [Whylogs](https://github.com/whylabs/whylogs)
- [ ] Add External Data
    - [ ] [Career Earnings](https://www.spotrac.com/pga/rankings/date/2011-01-01/2011-09-20/)
    - [ ] Biometrics
    - [ ] [Weather](https://www.wunderground.com/history/daily/KATL/date/2011-9-22)
- [ ] Data Viz
    - [ ] [SG Distributions](https://baseballsavant.mlb.com/visuals/statcast-pitch-distribution)
    - [ ] [Hole Heatmaps](https://datagolf.com/hole-heatmaps)
    - [ ] [Lie & SG Plinko](https://baseballsavant.mlb.com/visuals/pitch-plinko)
    - [ ] [Drive KDE](https://baseballsavant.mlb.com/player-comparison)
- [ ] Bayesian Integration
    - [ ] [Refer To](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/blob/master/examples/hockey.ipynb#scrollTo=B-c6bb9wO-Cs)
    - [ ] [Watch](https://www.youtube.com/watch?v=Zi6N3GLUJmw)
    - [ ] [Utilize](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
