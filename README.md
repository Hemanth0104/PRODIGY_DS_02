# PRODIGY_DS_02



---

# 🛳️ Titanic Data Analysis Report

## 📌 Introduction

This project involves a detailed exploratory data analysis of the Titanic dataset from the famous **Kaggle Titanic survival prediction** challenge. The objective was to uncover meaningful insights into **passenger demographics**, **ticket patterns**, and **survival rates** across different groups to inform predictive modeling.

---

## 📥 Data Loading and Preparation

The following datasets were used:

* `train.csv`
* `test.csv`
* `gender_submission.csv`

### ✅ Steps Performed:

* Loaded and concatenated `train.csv` and `test.csv` into a single DataFrame.
* Checked dataset structure using `.shape`, `.columns`, `.info()`.
* Identified missing values with `.isnull().sum()` – found **1698 null values** across the dataset.

---

## 🛠️ Handling Missing Values

* Imputed **categorical** missing values using the **mode**:

  * `Survived`: 0.0
  * `Cabin`: "C23 C25 C27"
  * `Embarked`: 'S'

* Imputed **numerical** missing values using the **mean**:

  * `Age`: 29.8811
  * `Fare`: 35.6272

✅ After imputation, **no missing values** remained in the dataset.

---

## 🧮 Data Type Identification

* **Categorical Columns**: Detected using `select_dtypes(include=['object'])`
* **Numerical Columns**: Detected using `select_dtypes(include=['int64', 'float64'])`

---

## 🔍 Exploratory Data Analysis & Key Findings

### 📊 Gender Distribution

* Counted and visualized the number of male and female passengers.
* `data['Sex'].value_counts()` showed males outnumbered females.

---

### 🎟️ Ticket Analysis

* Most Sold Ticket: **CA.2343** – 11 passengers
* Least Sold Ticket: **SC/PARIS 2159** – 1 passenger

#### Survival Analysis by Ticket:

* **CA.2343**: 0 survived out of 11
* **SC/PARIS 2159**: 0 survived out of 1

✅ **No passengers survived** with the most or least sold ticket.

---

### 👨‍👩‍👧‍👦 Survival by Sex

| Sex    | Survivors | % Survived |
| ------ | --------- | ---------- |
| Male   | 109       | 19.0%      |
| Female | 316       | 72.7%      |

✅ Females had a **much higher** survival rate — consistent with "women and children first" protocol.

---

### 🚢 Embarked Location × Survival × Sex

* Highest passengers embarked from **Southampton (S)**
* **Cherbourg (C)** had a **higher proportion** of male survivors than other ports.
* **Queenstown (Q)** had the **lowest survival rate**, especially among males.

---

### 🪑 Survival by Pclass

| Pclass | Male Survivors | Female Survivors | Male Non-Survivors | Female Non-Survivors |
| ------ | -------------- | ---------------- | ------------------ | -------------------- |
| 1      | 61             | 139              | 118                | 6                    |
| 2      | 25             | 94               | 154                | 13                   |
| 3      | 59             | 151              | 422                | 110                  |

✅ **Pclass 1** had the **highest survival rate**, while **Pclass 3** had the **lowest** — especially for men.

---

### 👶 Age Distribution and Survival

* Created **Age Bins**: `Child`, `Teen`, `Young Adult`, `Adult`, `Senior`
* Plotted Age distribution by Pclass and AgeGroup

✅ **Younger passengers** (children and teens) had better survival odds
✅ **Pclass 3** had more young passengers, but lowest survival rate

---

### 🧾 Family Size and Survival

* Defined new column: `Family_size = SibSp + Parch + 1`
* Analyzed survival across:

  * `Family_size`
  * `SibSp`
  * `Parch`

#### Key Insights:

* **Small families (2–4)** had the **best survival rate**
* **Solo travelers** and **large families (>4)** had **lower survival**

---

### 🏷️ Assumed Family Type (based on Family\_size)

* Not explicitly coded but inferred from chart titles.

Likely mapping:

* `Family_size = 1` → "Alone"
* `2 ≤ Family_size ≤ 4` → "Small Family"
* `Family_size > 4` → "Large Family"

✅ Confirmed: **Small Families > Alone > Large Families** in terms of survival

---

## ✅ Conclusion


From our analysis, several factors were found to be strongly associated with survival on the Titanic. **Sex** emerged as a highly influential factor, with **females significantly more likely to survive** than males—likely due to the “women and children first” evacuation policy. **Passenger class (Pclass)** also showed a strong correlation with survival: passengers in **1st class had the highest survival rates**, followed by those in 2nd and then 3rd class. **Age** played a moderate role, as **younger passengers, particularly children and teens, had a better chance of survival** compared to older individuals. **Family size** was another moderately impactful factor—**passengers traveling with small families (2 to 4 members)** had higher survival rates than those traveling alone or in large families. Finally, the **embarkation point (Embarked)** had a comparatively lower influence, but still showed some variation in survival rates; **passengers who embarked from Cherbourg (C)** had a higher proportion of survivors than those from Queenstown (Q) or Southampton (S).


### 🎯 Factors Most Associated with Survival:

| Factor          | Impact                                             |
| --------------- | -------------------------------------------------- |
| **Sex**         | ✅ High (Females more likely to survive)            |
| **Pclass**      | ✅ High (1st class > 2nd > 3rd)                     |
| **Age**         | ✅ Moderate (Younger passengers had better chances) |
| **Family Size** | ✅ Moderate (Small families survived more)          |
| **Embarked**    | ⚠️ Low/Moderate (C > Q > S for survival rate)      |

---

## 📎 Summary

This project provided a comprehensive overview of the Titanic passengers and uncovered critical survival patterns. These insights will support the next phase — building **ML models** for survival prediction.

---

## 📁 Files Included

* `train.csv`
* `test.csv`
* `gender_submission.csv`
* `titanic_analysis.ipynb`
* `README.md` (this file)

---

## 🧠 Tools & Libraries Used

* **Python**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Plotly**

---


