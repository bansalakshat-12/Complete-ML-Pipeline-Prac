# 🚀 End-to-End Machine Learning Pipeline using DVC & AWS S3

This project is a complete **MLOps pipeline** implementation inspired by *Day 5 – End-to-End ML Pipeline using DVC & AWS S3* by Vikash Das.  
It demonstrates how to **build, automate, and version-control** a machine learning workflow using modern MLOps tools like **DVC** and **AWS S3**.

---

## 🧠 **Project Overview**

The main goal of this project is to design and execute a **reproducible, automated ML pipeline** — covering everything from data ingestion to model evaluation — while maintaining scalability and traceability.

This project integrates:
- **Data Version Control (DVC)** – for data, model, and pipeline versioning  
- **AWS S3** – as cloud remote storage  
- **YAML Configuration Management** – for parameters and reproducibility  
- **Python** – for ML scripts (data ingestion, preprocessing, model training & evaluation)

---

## ⚙️ **Pipeline Stages**

| Stage | Description |
|--------|--------------|
| 1️⃣ **Data Ingestion** | Loads and splits the raw dataset for training and testing |
| 2️⃣ **Data Preprocessing** | Cleans and transforms the data to prepare it for modeling |
| 3️⃣ **Model Training** | Trains the ML model using the preprocessed data |
| 4️⃣ **Model Evaluation** | Evaluates model performance and logs metrics |
| 5️⃣ **Model Storage & Push** | Saves model artifacts and pushes data versions to AWS S3 |

Each stage is defined and tracked in the `dvc.yaml` file, ensuring the entire workflow is **automated and reproducible**.

---

## 🧩 **Tech Stack**

- **Python 3.x**
- **DVC (Data Version Control)**
- **AWS S3 (Remote Storage)**
- **Git & GitHub**
- **YAML (Configuration Management)**

---

## 📁 **Project Structure**

├── data/
│ ├── raw/ # Raw dataset
│ └── processed/ # Preprocessed data
│
├── src/
│ ├── data_ingestion.py # Data ingestion script
│ ├── data_preprocessing.py# Data preprocessing script
│ ├── model_train.py # Model training script
│ ├── model_evaluate.py # Model evaluation script
│
├── params.yaml # Stores parameters & hyperparameters
├── dvc.yaml # DVC pipeline definition
├── requirements.txt # Python dependencies
└── README.md # Project documentation

## 🧮 **Core DVC Commands Used**

```bash
# Initialize DVC
dvc init

# Track data and stages
dvc add data/raw

# Create pipeline stages
dvc stage add -n data_ingestion -d src/data_ingestion.py -o data/raw python src/data_ingestion.py
dvc stage add -n data_preprocessing -d src/data_preprocessing.py -o data/processed python src/data_preprocessing.py
dvc stage add -n model_train -d src/model_train.py -p model_params -o models/model.pkl python src/model_train.py
dvc stage add -n evaluate -d src/model_evaluate.py -p eval_params python src/model_evaluate.py

# Run complete pipeline
dvc repro


☁️ AWS Integration

Created an IAM user with S3 access policy

Configured AWS CLI with access and secret keys

Set up S3 bucket as the DVC remote for data and model artifacts

This ensures that every new data or model version is stored safely and can be retrieved anytime.

🔍 Results

✅ A completely automated, version-controlled ML workflow
✅ Reproducible experiments using DVC
✅ Scalable data storage on AWS S3
✅ Modular and maintainable ML pipeline