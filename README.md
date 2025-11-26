# Credit Risk Scorecard (Rebuild Project)

This is a **rebuild version** of my 3rd–year credit scoring project.
The previous version had weak performance and unstable modeling steps, so this project aims to **redo everything cleanly and correctly** using a fully bank-style pipeline.

## **1. Objective**

* Build a **credit risk scorecard** using **WOE + Logistic Regression**
* Produce a **300–900 score** for customers
* Ensure the model is **stable, interpretable, and production-ready**

## **2. Modeling Pipeline (Simple Version)**

1. **Load FE data**
2. **Train/Validation split** (time-based if possible)
3. **Variable filtering**

   * remove ID columns
   * remove constant/invalid variables
4. **Optimal Binning + WOE transformation**

   * monotonic bins
   * IV filtering (0.02–0.50)
5. **Train Logistic Regression** on WOE features
6. **Score transformation**

   * PDO = 50
   * Score range 300–900
7. **Evaluate model**

   * AUC, Gini, KS
   * PSI (DEV vs VAL)

## **3. Model Performance**

| Set | AUC   | KS    | Gini  | PSI      |
| --- | ----- | ----- | ----- | -------- |
| DEV | 0.771 | 0.408 | 0.543 | —        |
| VAL | 0.768 | 0.404 | 0.536 | 0.000174 |

**Summary:**

* AUC ~0.77 → good
* KS ~0.40 → strong separation
* Gini ~0.54 → stable scorecard quality

This rebuilt version performs far better and is fully consistent between Dev/Val.

## **4. Outputs**

* WOE bins
* IV table
* Logistic Regression coefficients
* Scorecard table
* Customer scores (300–900)
* AUC / KS plots

## **5. Reason for Rebuilding**

* The old project had:

  * unstable bins
  * incorrect score transformation
  * inconsistent Dev/Val results
  * weak evaluation
