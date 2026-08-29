# Titanic Survival Factor Analysis:

<p align="center">
  <img src="titanic.png" width="30%">
</p>

## Prerequisites
* pandas
* matplotlib
* seaborn

To install dependencies:
```
bash pip install pandas matplotlib seaborn
```

### Dataset Size:
```
The volume of the dataset is fully compatible and suitable for in-memory processing with Pandas.

!ls -lh   ----rwxrwxrwx 1  5.8M Aug 27 21:20  titanic_large.csv
```


## Initial Hypotheses (Prior to Analysis)
- Sex: Male have a higher survival rate compared to Female.
- Pclass: First-class passengers have a higher survival rate than other classes.
- Family Status: Solo passengers have a higher survival rate than passengers traveling with   family.
- Age_category: Children and the elderly have a higher survival rate compared to adults.

## Results of Analysis:
- Female survived more than Male
- Pclass has effect on survival , first class survived more than others
- Family status effect on survival:
To analyze family status, we initially  computed  mean, std, and count for each category with respect to survival. The results demonestrate survival rates in descending order: Alone > Small > Medium > Big. However, due to the narrow gap between means, we calculated the Standard Error (SE) in the second step. The SE revealed that this ranking is  inconclusive for the Big family group.
- Age_category : results indicate  survival are more in order child > young > adults > middlde_age > old

## Statistical Results

|***Factor***|***Statistical Results*** |***Confitmed or Rejected*** |
|---|---|---|
| **Sex**|*PC1*:female: 0.514302> Men:0.514302<br>*PC2*: female: 0.514302> Men: 0.441886     <br>*PC3*: Female 0.568593> Men 0.431407 |❌*Rejected*
|**Pclass**|*PC1*: 0.541205> *PC2*: 0.541205> *PC3*: 0.541205|✅*Confirmed*|
|**Family Status**|**Alone:** Mean: 0.4028 \| Std: 0.4905 \| Count: 36,793 <br> **Small:** Mean: 0.3944 \| Std: 0.4887 \| Count: 55,180 <br> **Medium:** Mean: 0.3784 \| Std: 0.4850 \| Count: 7,966 <br> **Big:** Mean: 0.3770 \| Std: 0.4887 \| Count: 61 |⚠️ Partly|
|**Age_Category**|*Child*: 0.514036 > *Young*: 0.410626> Adults :0.379811> *Middle_age*: 0.378482>*old*: 0.343856 | ✅*Confirmed*

```
                  mean        SE  ci_lower  ci_upper
family_status
alone          0.402767  0.002557  0.397755  0.407778
small          0.394400  0.002081  0.390322  0.398478
medium         0.378358  0.005434  0.367707  0.389009
big            0.377049  0.062568  0.254416  0.499682


```
### Other Steps:
- Imputing Missing Values in Age , Filling with mean Age in each Class
- Constructing Categorical Column for family as StatusFamily
- Creating Categorical Column for Age as Age_categorical
- Summary statistics through describe method for numerical data
- Count- plot for Survival
- Heatmap plot for correlation Numerical
- Summary analysis based on
    -'Age':['min', 'max', 'mean'],
    - 'Fare': 'mean',
    - 'Survived': 'mean'
    - calculating Count for SibSp   Parch
- Some other Anlysis  steps in the sources for detecting better (titanic.ipynb)