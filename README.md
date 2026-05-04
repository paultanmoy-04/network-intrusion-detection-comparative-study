# network-intrusion-detection-comparative-study
Comparative study of XGBoost, MLP, and CNN-LSTM for Network Intrusion Detection using CICIDS2017 dataset
```markdown
# 🚀 Network Intrusion Detection System (Comparative Study)

## 📌 Overview

This project presents a **comparative study of Machine Learning and Deep Learning models** for Network Intrusion Detection using the **CICIDS2017 dataset**.

We evaluate three architectures:

- 🌲 **XGBoost** (Tree-based Machine Learning)
- 🧠 **MLP (Multi-Layer Perceptron)**
- 🔁 **CNN-LSTM (Hybrid Deep Learning Model)**

The goal is to analyze their effectiveness in detecting modern cyber attacks and understanding trade-offs between **accuracy, temporal modeling, and computational efficiency**.

---

## 📊 Dataset

- **Dataset:** CICIDS2017 (Canadian Institute for Cybersecurity)
- **Total Samples:** ~2.8 Million network flows
- **Features:** 79 statistical features per flow
- **Classes:**
  - Benign Traffic
  - DoS Attacks
  - DDoS Attacks
  - Port Scanning & Brute Force
  - Web-Based Attacks
  - Other Exploits & Infiltration

⚠️ Dataset is not included due to size.  
🔗 Download: https://www.unb.ca/cic/datasets/ids-2017.html

---

## ⚙️ Data Preprocessing

- Removed NaN and infinite values
- Dropped redundant/low-variance features
- Standardized features using **Z-score normalization**
- Consolidated 15 attack classes → 6 major categories
- Handled class imbalance using:
  - SMOTE (XGBoost)
  - Class weighting (MLP, CNN-LSTM)

---

## 🧠 Models Implemented

### 🌲 XGBoost
- Gradient boosting tree-based model
- Used `DMatrix` for optimized computation
- Hyperparameters:
  - max_depth = 8
  - min_child_weight = 5
- Early stopping used for optimal performance

---

### 🧠 MLP (Multi-Layer Perceptron)
- Fully connected deep neural network
- Architecture:
  - 512 → 256 → 128 hidden layers
- Techniques used:
  - Batch Normalization
  - Dropout (0.3)
  - Weighted CrossEntropy Loss
  - Learning rate scheduling

---

### 🔁 CNN-LSTM (Hybrid Model)
- Designed for **spatio-temporal learning**
- Key idea: Convert tabular data → sequence windows

#### Pipeline:
1. **Sliding Window (size = 5)** → time-series conversion  
2. **CNN (1D)** → spatial feature extraction  
3. **LSTM** → temporal pattern learning  
4. **Fully Connected Layer** → classification  

- CNN:
  - Conv1D (64 → 128 filters)
- LSTM:
  - 2 layers, hidden size = 128
- Regularization:
  - Dropout (0.3–0.4)
  - Gradient clipping

---

## 📈 Results

### 🔥 Overall Performance

| Model      | Accuracy | Precision | Recall | F1-Score |
|------------|----------|----------|--------|----------|
| XGBoost    | 99.71%   | 0.9986   | 0.9972 | 0.8725   |
| MLP        | 99.46%   | 0.9807   | 0.9646 | 0.6983   |
| CNN-LSTM   | **99.94%** | **0.9994** | **0.9994** | **0.9994** |

---

### 📊 Key Observations

- **CNN-LSTM achieved the best performance**
  - Captures temporal dependencies across network flows
  - Excellent detection of multi-stage attacks

- **XGBoost is highly efficient**
  - Strong baseline performance
  - Low computational cost

- **MLP shows limitations**
  - Struggles with minority classes
  - Lower Macro F1-score

---

## 🔍 Model Insights

### 🧠 Why CNN-LSTM works best?

- CNN extracts spatial patterns from packet features  
- LSTM captures **temporal relationships between flows**  
- Treats network traffic as **time-series instead of isolated events**

---

## ⚠️ Challenges

- Extreme class imbalance (rare attacks)
- High-dimensional feature space (78+ features)
- Large dataset size (~2.8M samples)
- Temporal dependencies across multiple flows

---

## 🚀 Future Work

- Transformer-based models (TabNet / Attention models)
- Explainable AI (SHAP, LIME)
- Real-time deployment optimization

---

## 📁 Project Structure

```

nids-comparative/
│
├── notebooks/
│   ├── xgboost.ipynb
│   ├── mlp.ipynb
│   ├── cnn_lstm.ipynb
│
├── data/
├── results/
├── README.md
├── requirements.txt

````

---

## ⚙️ Installation

```bash
git clone https://github.com/YOUR_USERNAME/network-intrusion-detection-comparative-study.git
cd network-intrusion-detection-comparative-study
pip install -r requirements.txt
````

---

## ▶️ Usage

Run Jupyter notebooks:

```bash
cd notebooks
jupyter notebook
```

---

## 🛠️ Tech Stack

* Python
* PyTorch
* Scikit-learn
* XGBoost
* NumPy, Pandas
* Matplotlib, Seaborn

---

## 👨‍💻 Author

**Tanmoy Paul**
M.Sc. Data Science & Artificial Intelligence
📧 [paultanmoy408@gmail.com]

---

## ⭐ Support

If you found this project useful:

* ⭐ Star the repo
* 🍴 Fork it
* 📢 Share it

---

## 📌 Conclusion

This study demonstrates that:

* Traditional ML (XGBoost) is efficient and reliable
* Deep learning (CNN-LSTM) significantly improves detection of complex attacks
* Temporal modeling is crucial for modern network intrusion detection

👉 CNN-LSTM is the most effective model for real-world NIDS systems.

```
```
