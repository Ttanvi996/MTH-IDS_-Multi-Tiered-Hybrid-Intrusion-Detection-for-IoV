Overview:-
The exponential growth of Internet of Vehicles (IoV) has heightened the need for intelligent and robust cybersecurity solutions. This project introduces MTH-IDS, a Multi-Tiered Hybrid Intrusion Detection System that integrates both Machine Learning (ML) and Deep Learning (DL) to identify malicious network behaviors across vehicular networks. MTH-IDS is designed to enhance detection accuracy while ensuring scalability and low latency suitable for real-time applications in IoV environments.

 Objective

To develop and evaluate a hybrid, layered IDS model that:
1. Detects intrusions in vehicular ad-hoc networks (VANETs) with high accuracy.
2.Combines the strengths of multiple ML and DL algorithms.
3.Implements tiered filtering for computational efficiency and hierarchical threat detection.
4.Enhances the reliability of smart transportation systems.

Dataset
CICIDS2017 :- A widely-used dataset for evaluating intrusion detection models. It contains realistic network traffic, including benign and attack scenarios (e.g., DDoS, PortScan, Botnet, Infiltration, etc.)

Preprocessing Steps:
1.Null value removal
2.Label encoding for categorical features
3.Feature scaling (MinMaxScaler)
4.One-hot encoding for multiclass labels

Model Architecture
The MTH-IDS architecture consists of three hierarchical layers:

Layer 1: Anomaly Detection (Binary Classification)
Goal : Differentiate between benign and malicious traffic.
Models :Random Forest Classifier and Gradient Boosting Classifier
Output: Flags suspicious entries to be further processed.

Layer 2: Attack Family Classification (Multi-Class)
Goal: Classify detected malicious traffic into broad categories (e.g., DDoS, Web attacks).
Model : XGBoost Classifier
Output: Filters and forwards samples for fine-grained analysis.

Layer 3: Fine-Grained Attack Identification (Multiclass Deep Learning)
Goal: Identify specific attack types within families.
Model: Multi-Layer Perceptron (MLP) using TensorFlow/Keras
Architecture:
1.Input: Preprocessed features
2.Dense layers with ReLU activation
3.Dropout layers for regularization
4.Softmax output for multi-class classification

Each layer is evaluated using:
1.Accuracy
2.Precision, Recall, F1-score
3.Confusion Matrix
4.ROC-AUC (for binary and multiclass settings)

Results :
| Layer        | Accuracy | Precision | Recall | F1-score |
|--------------|----------|-----------|--------|----------|
| Layer 1      | 99.2%    | 0.993     | 0.991  | 0.992    |
| Layer 2      | 98.6%    | 0.985     | 0.986  | 0.985    |
| Layer 3 (MLP)| 97.8%    | 0.978     | 0.977  | 0.977    |


