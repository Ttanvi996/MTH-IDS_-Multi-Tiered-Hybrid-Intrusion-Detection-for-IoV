 1)Overview:-
The exponential growth of Internet of Vehicles (IoV) has heightened the need for intelligent and robust cybersecurity solutions. This project introduces MTH-IDS, a Multi-Tiered Hybrid Intrusion Detection System that integrates both Machine Learning (ML) and Deep Learning (DL) to identify malicious network behaviors across vehicular networks. MTH-IDS is designed to enhance detection accuracy while ensuring scalability and low latency suitable for real-time applications in IoV environments.

2)Objective

To develop and evaluate a hybrid, layered IDS model that:
Detects intrusions in vehicular ad-hoc networks (VANETs) with high accuracy. Combines the strengths of multiple ML and DL algorithms. Implements tiered filtering for computational efficiency and hierarchical threat detection. Enhances the reliability of smart transportation systems.

3)Dataset
CICIDS2017 :- A widely-used dataset for evaluating intrusion detection models. It contains realistic network traffic, including benign and attack scenarios (e.g., DDoS, PortScan, Botnet, Infiltration, etc.)

4)Preprocessing Steps:

  + Null value removal :-  Converts categorical string labels into numerical values so they can be used in model.

  + Label encoding for categorical features :- Scales feature values to a standard range (0 to 1), improving model convergence and performance.

  + Feature scaling (MinMaxScaler) :- Scales feature values to a standard range (0 to 1), improving model convergence and performance.

  + One-hot encoding for multiclass labels :- Converts multiclass labels into a binary matrix (one column per class), necessary for neural networks.

5)Model Architecture
The MTH-IDS architecture consists of three hierarchical layers:

+ Layer 1: Anomaly Detection (Binary Classification)

+ Goal : Differentiate between benign and malicious traffic. 

+ Explanation :-  The Label column is transformed into binary classes: 'BENIGN' vs. 'ATTACK'. All non-benign entries are grouped as 'ATTACK'.

+ Models :Random Forest Classifier and Gradient Boosting Classifier

+ Output: Flags suspicious entries to be further processed.

+ Layer 2: Attack Family Classification (Multi-Class)

+ Goal: Classify detected malicious traffic into broad categories (e.g., DDoS, Web attacks).

Explanation :- This layer deals with multiple attack categories (e.g., DoS Hulk, DDoS, PortScan, etc.). A new subset of the data is created excluding benign traffic. Labels are retained as-is to train a classifier on attack types.

Model : XGBoost Classifier

Output: Filters and forwards samples for fine-grained analysis.

Layer 3: Fine-Grained Attack Identification (Multiclass Deep Learning)

Goal: Identify specific attack types within families.

Explanation :- Layer 3 uses a Deep Learning model (MLP) to classify attack types at a granular level. Labels are one-hot encoded using to_categorical(). Features are scaled. Output with softmax for multi-class classification

Model: Multi-Layer Perceptron (MLP) using TensorFlow/Keras

Architecture:

1.Input: Preprocessed features

2.Dense layers with ReLU activation

3.Dropout layers for regularization

4.Softmax output for multi-class classification

+ 6)Why Multiple Models Were Used
   
In this multi-tiered intrusion detection system (IDS) for Internet of Vehicles (IoV), a hybrid ensemble approach was employed to maximize accuracy, robustness, and generalization across different layers of classification. Here's why multiple models were used:

1. Decision Tree Classifier :-Acts as a simple, interpretable baseline. Useful for benchmarking and understanding data splits.

2. Random Forest Classifier :- An ensemble of decision trees. Reduces overfitting and improves stability. Used for binary classification in the first layer.

3. Extra Trees Classifier :- Similar to Random Forest but more randomized. Provides faster training and better variance reduction.

4. XGBoost Classifier :- Gradient boosting model known for speed and performance. Used in multiclass scenarios for detecting specific attack families.

5. Stacking Classifier :- Meta-ensemble that combines multiple base models. Trains a final classifier on the predictions of previous models. Used to capture complementary strengths of different models and improve overall prediction accuracy.
   

* Note: - This project is a replication and exploration of the research work titled "Multi-Tiered Hybrid Intrusion Detection System (MTH-IDS) for the Internet of Vehicles (IoV)".  I am not the original author of this research or the model architecture. I was highly intrigued by the methodology and effectiveness of the proposed system. Therefore, I chose to replicate the project using publicly available datasets and libraries, primarily for learning, experimentation, and further exploration.

You can find the original research paper here for reference:- https://arxiv.org/pdf/2105.13289



