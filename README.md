# Gene Regulatory Network (GRN) Prediction

This project reconstructs Gene Regulatory Networks (GRNs) from simulated gene expression data using supervised machine learning models. The goal is to predict transcription factor (TF)–target gene interactions and evaluate the accuracy of reconstructed GRNs against known bipartite ground truth networks.

---

## File Structure

```plaintext
.
├── 5_mr_50_cond/                   # Example benchmark folder
│   ├── simulated_noNoise.txt       # Simulated gene expression data
│   ├── bipartite_GRN.csv           # Ground truth regulatory edges
│   ├── rf_importance.csv           # Random Forest importance scores
│   ├── nn_importance.csv           # Neural Network importance scores
│   ├── lasso_importance.csv        # Lasso Regression importance scores
│   ├── hybrid_importance.csv       # Averaged hybrid scores
│   └── *.png                       # Evaluation plots
├── baseline_use_correlation.xlsx   # AUROC values from baseline model
├── Main.py                         # Model training, evaluation, and utilities
├── README.md                       # Project documentation
```

---

## Data Description

- **`simulated_noNoise.txt`**: Simulated expression matrix with dimensions `[samples × (TFs + Targets)]`
  - First 100 columns: Transcription Factors (TFs)
  - Next 100 columns: Target genes

- **`bipartite_GRN.csv`**: Ground truth edges formatted as `(TF_id, Target_gene_id)`

- **`baseline_use_correlation.xlsx`**: Baseline AUROC scores using correlation-based feature importance

---

## Models Used

- **Random Forest**  
  Tree-based ensemble model; effective in capturing non-linear interactions

- **Lasso Regression**  
  Sparse linear regression that performs feature selection by penalizing coefficients

- **Neural Network**  
  A shallow fully connected network with one hidden layer (32 ReLU units)

- **Hybrid**  
  Averaged importance scores normalized across all models (RF, Lasso, NN)

---

## Results

Model performance was evaluated using AUROC scores across three benchmark datasets.

| Dataset           | Baseline | Random Forest | Lasso Regression | Neural Network | Hybrid |
|-------------------|----------|----------------|------------------|----------------|--------|
| 5_mr_50_cond      | 0.673    | 0.663          | 0.720            | 0.695          | **0.743** |
| 40_mr_50_cond     | 0.844    | 0.826          | 0.880            | 0.840          | **0.884** |
| 100_mr_100_cond   | 0.916    | 0.903          | **0.946**        | 0.915          | 0.943  |

The Hybrid approach consistently achieves top performance, suggesting it effectively integrates the strengths of individual models.


---

## Contributing

Contributions are welcome! Please open an issue to discuss major changes before submitting a pull request.



