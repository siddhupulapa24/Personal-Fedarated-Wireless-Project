# Exploratory Data Analysis (EDA) Report

## 1. Purpose

Exploratory Data Analysis (EDA) helps us understand a dataset before training a machine-learning model. This report examines the Wi-Fi signal measurements used by the Personalized Federated Wireless project.

## 2. Dataset overview

The project uses the UJIIndoorLoc Wi-Fi fingerprint dataset. Each observation records received signal strength from Wi-Fi access points, along with location and device information.

The project uses the Wi-Fi signal measurements to classify connection quality as Poor, Fair, Good, or Excellent. The PHONEID field is also used to group observations into clients for the federated-learning experiments.

The dataset files included in the project are UJIIndoorLoc trainingData.csv and validationData.csv. The federated-sample chart shows 19,937 samples divided among 16 clients. The client data is split into training, validation, and test portions for the experiments.

## 3. Data preparation

The project treats missing Wi-Fi access-point readings as very weak signals, removes access-point columns that do not vary, and creates seven summary measurements from the RSSI values. These include the strongest, average, and median signal, signal variation, and the number of detected access points. The model uses these summary measurements together with the remaining access-point readings.

## 4. Visual exploration

### 4.1 Class distribution

![Class distribution](../graphs/generated/01_dataset_class_distribution.png)

Excellent is the largest class, with 8,366 samples (42.0%), followed by Good with 7,256 (36.4%), Fair with 3,034 (15.2%), and Poor with 1,281 (6.4%). The classes are imbalanced because Excellent and Good have many more examples than Poor.

### 4.2 RSSI distribution

![RSSI distribution](../graphs/generated/02_rssi_distribution.png)

Most detected Wi-Fi signal readings are between about -95 and -70 dBm, with fewer stronger readings extending toward 0 dBm. The chart shows the project’s quality boundaries at -75, -65, and -55 dBm. A value closer to zero represents a stronger received signal.

### 4.3 Maximum RSSI

![Maximum RSSI distribution](../graphs/generated/03_max_rssi_distribution.png)

The strongest detected signal in each test sample is usually around -65 to -50 dBm. Some samples have much weaker maximum signals, while a small number are near 0 dBm. This shows that signal conditions differ considerably from one sample to another.

### 4.4 Detected access points

![Detected access points](../graphs/generated/04_detected_aps_distribution.png)

The median sample detects 17 Wi-Fi access points. Most samples detect roughly 10 to 25, though some detect fewer or more. The number of visible access points varies between locations and measurements.

### 4.5 Client sample distribution

![Client sample distribution](../graphs/generated/05_client_sample_distribution.png)

The samples are not evenly distributed across the 16 clients. Clients 13 and 14 have the most samples, while client 16 has the fewest. This means some clients contribute much more training data than others.

### 4.6 Client class distribution

![Client class distribution](../graphs/generated/06_client_class_distribution.png)

The mix of Poor, Fair, Good, and Excellent samples differs between clients. For example, some clients contain mostly Good or Excellent samples, while others have a different mix. These differences make the client data non-IID, meaning the clients do not all have the same kind of data.

## 5. Main observations

- Excellent is the most common class (42.0%), while Poor is the least common (6.4%).
- Most detected Wi-Fi signals are weak, but the dataset also includes stronger readings.
- A typical sample detects 17 access points.
- The 16 clients have different sample counts and different class mixes.
- These differences are why the project compares federated-learning methods that can handle clients with different data.

## 6. Conclusion

The EDA helps identify class balance, signal-strength patterns, and differences between client datasets. These observations inform the preprocessing and federated-learning experiments in the project.