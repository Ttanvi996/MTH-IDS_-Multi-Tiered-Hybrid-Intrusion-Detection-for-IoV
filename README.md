1)Overview:-
The exponential growth of Internet of Vehicles (IoV) has heightened the need for intelligent and robust cybersecurity solutions. This project introduces MTH-IDS, a Multi-Tiered Hybrid Intrusion Detection System that integrates both Machine Learning (ML) and Deep Learning (DL) to identify malicious network behaviors across vehicular networks. MTH-IDS is designed to enhance detection accuracy while ensuring scalability and low latency suitable for real-time applications in IoV environments.

2)Objective

To develop and evaluate a hybrid, layered IDS model that:
Detects intrusions in vehicular ad-hoc networks (VANETs) with high accuracy. Combines the strengths of multiple ML and DL algorithms. Implements tiered filtering for computational efficiency and hierarchical threat detection. Enhances the reliability of smart transportation systems.

3)Dataset
CICIDS2017 :- A widely-used dataset for evaluating intrusion detection models. It contains realistic network traffic, including benign and attack scenarios (e.g., DDoS, PortScan, Botnet, Infiltration, etc.)

4)Preprocessing Steps:
1.Null value removal :-  Converts categorical string labels into numerical values so they can be used in model.
2.Label encoding for categorical features :- Scales feature values to a standard range (0 to 1), improving model convergence and performance.
3.Feature scaling (MinMaxScaler) :- Scales feature values to a standard range (0 to 1), improving model convergence and performance.
4.One-hot encoding for multiclass labels :- Converts multiclass labels into a binary matrix (one column per class), necessary for neural networks.

5)Model Architecture
The MTH-IDS architecture consists of three hierarchical layers:

Layer 1: Anomaly Detection (Binary Classification)
Goal : Differentiate between benign and malicious traffic. T
Explanation :-  The Label column is transformed into binary classes: 'BENIGN' vs. 'ATTACK'. All non-benign entries are grouped as 'ATTACK'.
Models :Random Forest Classifier and Gradient Boosting Classifier
Output: Flags suspicious entries to be further processed.

Layer 2: Attack Family Classification (Multi-Class)
Goal: Classify detected malicious traffic into broad categories (e.g., DDoS, Web attacks).
Explanation :- This layer deals with multiple attack categories (e.g., DoS Hulk, DDoS, PortScan, etc.). A new subset of the data is created excluding benign traffic. Labels are retained as-is to train a classifier on attack types.
Model : XGBoost Classifier
Output: Filters and forwards samples for fine-grained analysis.

Layer 3: Fine-Grained Attack Identification (Multiclass Deep Learning)
Goal: Identify specific attack types within families.
Explanation :- Layer 3 uses a Deep Learning model (MLP) to classify attack types at a granular level. Labels are one-hot encoded using to_categorical(). Features are scaled.
Output with softmax for multi-class classification
Model: Multi-Layer Perceptron (MLP) using TensorFlow/Keras
Architecture:
1.Input: Preprocessed features
2.Dense layers with ReLU activation
3.Dropout layers for regularization
4.Softmax output for multi-class classification

6) Performnace Metrics :-
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


