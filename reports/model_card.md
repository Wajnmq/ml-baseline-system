# Model Card — Week 3 (Draft)

## 1) What is the prediction?
- **Target (y):** is_high_value  
- **Unit of analysis:** one row = one user  
- **Decision supported:** identify users who are likely to be high-value customers

## 2) Data contract (inference)
- **ID passthrough columns:** user_id  
- **Required feature columns (X):** country, n_orders, avg_amount, total_amount  
- **Forbidden columns:** the target column (is_high_value) 
## 3) Evaluation plan
- **Split strategy:** train / holdout split
- **Primary metric:** accuracy 
