# Data-Generation-using-Modelling-and-Simulation-for-Machine-Learning

## Abstract
This project focuses on generating synthetic data using a discrete-event **MM1 queue simulation** and applying multiple machine learning models to predict system performance (average queue length). Instead of selecting the best model based on a single metric, a **Multi-Criteria Decision Making (MCDM)** approach using **TOPSIS** is applied to rank models across multiple evaluation metrics.

The project integrates:

- Simulation-based synthetic data generation  
- Machine learning regression models  
- Multi-criteria evaluation and model ranking  

---

## 1. Problem Statement
Collecting real-world queue data can be expensive or impractical. Simulation-based modeling allows controlled generation of synthetic datasets.  

Selecting a model based on a single metric (like R²) may be biased. This project aims to:

1. Generate 1000 simulation samples of an MM1 queue.  
2. Train multiple ML regression models.  
3. Evaluate models using multiple performance metrics.  
4. Use **TOPSIS** to rank and select the optimal model.  

---

## 2. Simulation Tool
**Simulation library:** `SimPy` (Python)  

Why SimPy?

- Discrete-event simulation for queues and processes  
- Controlled and reproducible environment  
- Adjustable parameters: arrival rate, service rate, simulation time  
- Generates measurable output (average queue length)  

---

## 3. Methodology

### Step 1: Simulation Data Generation
The MM1 queue simulation involves:

| Parameter | Description | Range |
|-----------|-------------|-------|
| arrival_rate | Customers per time unit | 0.1 – 10 |
| service_rate | Service completions per time unit | 0.1 – 10 |
| sim_time | Total simulation time | 100 – 1000 |

For each simulation:

1. Random initial parameters are generated.  
2. Queue is simulated using `SimPy`.  
3. Average queue length is recorded as the target variable.  
4. Process repeated 1000 times to generate the dataset.  

**Final Dataset Structure:**

| arrival_rate | service_rate | sim_time | avg_queue |
|--------------|--------------|----------|-----------|

---

### Step 2: Machine Learning Models
The following regression models were trained:

1. Linear Regression  
2. Ridge Regression  
3. Lasso Regression  
4. Decision Tree  
5. Random Forest  
6. Gradient Boosting  
7. Support Vector Regressor (SVR)  
8. K-Nearest Neighbors (KNN)  
9. Multi-Layer Perceptron (MLP)  

**Dataset split:** 80% Training, 20% Testing  

---

### Step 3: Evaluation Metrics
Models were evaluated using multiple metrics:

| Metric | Type | Description |
|--------|------|-------------|
| MSE | Cost | Mean Squared Error |
| RMSE | Cost | Root Mean Squared Error |
| R² | Benefit | Coefficient of Determination |
| Training Time | Cost | Computational efficiency |

> Using multiple metrics ensures robust model comparison across accuracy and efficiency.  

---

## 4. TOPSIS for Model Ranking
**Why TOPSIS?**  
TOPSIS ranks alternatives based on distance to the ideal best and worst solution. It considers **all metrics simultaneously**.

**Steps in TOPSIS:**

1. Normalize the evaluation matrix  
2. Apply weights for each metric  
3. Determine ideal best and worst  
4. Compute distance from ideal best/worst  
5. Calculate closeness coefficient  
6. Rank models  

**Criteria Weights Used:**

| Metric | Weight | Impact |
|--------|--------|--------|
| MSE | 0.30 | Minimize |
| RMSE | 0.30 | Minimize |
| R² | 0.30 | Maximize |
| Training Time | 0.10 | Minimize |

---

## 5. Results
**Example Model Evaluation Table:**

| Model | MSE | RMSE | R² | Train Time |
|-------|-----|------|----|------------|
| Gradient Boosting | 0.0017 | 0.041 | 0.996 | 0.243s |
| Random Forest | 0.0018 | 0.042 | 0.995 | 0.495s |
| Decision Tree | 0.0033 | 0.057 | 0.991 | 0.007s |
| MLP | 0.1621 | 0.402 | 0.562 | 0.123s |
| Linear | 0.2332 | 0.483 | 0.370 | 0.002s |

**TOPSIS Ranking Table:**

| Rank | Model | TOPSIS Score |
|------|-------|--------------|
| 1 | Gradient Boosting | 0.948 |
| 2 | Random Forest | 0.904 |
| 3 | Decision Tree | 0.821 |

> Higher score → Closer to ideal solution  

---

## 6. Result Graphs
 <img width="730" height="308" alt="image" src="https://github.com/user-attachments/assets/9ae63b3e-d5c1-47b6-9dc3-a4156a1e1287" />

- Interpretation: Ensemble tree-based methods outperform linear models.  

---

## 7. Discussion
- Tree-based ensembles capture non-linear simulation dynamics effectively.  
- Linear models are less effective for complex queue interactions.  
- Training time introduces trade-offs between performance and efficiency.  
- TOPSIS provides a balanced, multi-metric decision framework.  

---

## 8. Conclusion
This project demonstrates:

- Synthetic data generation via MM1 queue simulation  
- Application of multiple ML regression models  
- Multi-criteria evaluation  
- Scientific model selection using TOPSIS  

**Best model (Gradient Boosting)** balances accuracy, error minimization, and computational efficiency.  

---
## 9. Future Improvements
- Hyperparameter tuning for all models  
- Cross-validation for robust evaluation  
- Automatic weight optimization in TOPSIS  
- Sensitivity analysis for simulation parameters  
- Deep learning model comparisons  

---

## 10. How to Run
1. Open `102316094.ipynb` in Google Colab or Jupyter Notebook  
2. Install required libraries (`simpy`, `scikit-learn`, `pandas`, `matplotlib`, `seaborn`)  
3. Run all cells  
4. Dataset generation, ML training, evaluation, and TOPSIS ranking are automated  

---

**Final Statement:**  
This project integrates **Simulation + Machine Learning + Multi-Criteria Decision Making** to provide a comprehensive framework for data-driven model evaluation and selection.
