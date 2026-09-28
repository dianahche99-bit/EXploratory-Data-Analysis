# Titanic Survival — Exploratory Data Analysis

Applying core exploratory data analysis (EDA) techniques (univariate, bivariate, multivariate, and target-variable analysis) to the Kaggle Titanic dataset, to identify which passenger characteristics were most associated with survival.

## Overview

Rather than jumping straight to modeling, this project works through the dataset step by step to understand its structure, quality, and patterns first. The goal was to answer one question: **who survived the Titanic, and why?**

**Tools:** Python, Kaggle Notebooks
**Libraries:** `pandas`, `numpy` (data handling), `matplotlib`, `seaborn` (visualization), `scipy.stats` (Z-score outlier detection), `missingno` (missing data visualization)
**Dataset:** Kaggle Titanic `train.csv` (891 rows, 12 columns)

## Process

1. **Initial exploration** — Inspected the data with `.shape`, `.info()`, `.describe()`, `.nunique()`, and a duplicate check
2. **Missing values and outliers** — Handled missing values in Age, Cabin, and Embarked (imputing Age and Embarked, flagging Cabin instead of guessing); checked outliers using the IQR method (Fare) and Z-score (Age)
3. **Univariate analysis** — Distributions of Age, Fare, Sex, Pclass, and Embarked
4. **Bivariate analysis** — Age vs Fare, Fare vs Pclass, Age vs Survived, and Pclass/Embarked vs Survived/Sex
5. **Multivariate analysis** — Pairplot, FacetGrid, and a correlation heatmap
6. **Target variable analysis** — Survival rate by Sex, Pclass, Embarked, and Age group, plus cross-tabulations

## Key Findings

- **Univariate:** Age is roughly bell-shaped, centered in the 20s–30s. Fare is heavily right-skewed, with a few expensive 1st-class tickets pulling the mean well above the median. Most passengers were male, traveled 3rd class, and boarded at Southampton.
- **Bivariate:** Fare rises clearly with class — 1st-class tickets are far more expensive and variable, while 3rd-class fares are cheap and tightly clustered. Survivors skewed only slightly younger, a minor effect.
- **Multivariate:** Pclass (-0.34) and Fare (+0.26) were the two features most correlated with survival, and they are strongly correlated with each other (-0.55) — essentially the same "wealth/class" signal. Age barely correlated with survival (-0.06).
- **Target variable:** Sex was the single strongest driver of survival, with Pclass second. Combined, they show the sharpest pattern in the data: **women in 1st/2nd class survived almost always, while men in 3rd class almost never did.**

## Conclusion

Age consistently showed only a weak relationship with anything else, while Fare and Pclass repeatedly emerged as strongly linked to each other and to survival. The analysis confirms the "women and children first" story, but shows it was heavily shaped by class and wealth rather than applying equally to everyone. Extreme fares were kept in the data since they represent real 1st-class prices rather than errors.

## Links

- [Full notebook (Kaggle)](https://www.kaggle.com/code/dianahcheloti/notebook7c9c179d0c)
