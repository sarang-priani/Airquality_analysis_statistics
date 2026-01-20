# Airquality_analysis_statistics
Learn Probability Density Functions using Roll-Number-Parameterized Non-Linear Model
# Learning a Probability Density Function from Transformed NO₂ Data

## Project Overview

This project focuses on learning the parameters of a probability density function (PDF) from air quality data.  
A nonlinear transformation is applied to NO₂ values, and the parameters of the following PDF are learned:

p̂(z) = c · exp(−λ (z − μ)²)

The solution is implemented using a Google Colab notebook and uploaded to GitHub.

---

## Dataset

- The dataset is provided in CSV format (`data 3.csv`) Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data.
- It contains air quality measurements for different pollutants.
- The NO₂ (Nitrogen Dioxide) column is used for this assignment.
- Missing values are removed before processing.

---

## Methodology

### Data Preprocessing

1. The CSV file is loaded using Pandas.
2. Column names are cleaned to remove extra spaces.
3. The NO₂ column is identified and extracted.
4. Missing values are removed to ensure valid numerical input.

---

### Nonlinear Transformation

The following transformation is applied to each NO₂ value:

z = x + aᵣ sin(bᵣ x)

where:
- x is the original NO₂ value  
- r is the university roll number  
- aᵣ = 0.05 × (r mod 7)  
- bᵣ = 0.3 × ((r mod 5) + 1)  

This transformation introduces roll-number-specific variation.

---

### Probability Density Function Model

The transformed variable z is modeled using:

p̂(z) = c · exp(−λ (z − μ)²)

This form resembles a Gaussian distribution and allows parameter estimation using closed-form expressions.

---

### Parameter Estimation

The parameters are estimated using Maximum Likelihood Estimation (MLE).

- μ = (1/N) Σ zᵢ  
- σ² = (1/N) Σ (zᵢ − μ)²  
- λ = 1 / (2σ²)  
- c = √(λ / π)

These equations give the exact maximum likelihood estimates.

---

## Results

### Learned Parameters

| Parameter | Value |
|---------|-------|
| μ (Mean) | 25.8041 |
| λ (Lambda) | 0.001459 |
| c | 0.021553 |

(Values are rounded for clarity.)

---

### Result Graph

- A histogram of the transformed data represents the empirical probability density.
- The learned PDF is plotted on top of the histogram.
- The plot shows good agreement near the mean, with expected deviations in the tails.

This confirms that the learned PDF reasonably models the transformed data.

---

## Conclusion

The assignment requirements are satisfied by applying the given nonlinear transformation and learning the PDF parameters using maximum likelihood estimation. The approach follows standard statistical principles and produces a valid probability density function.

