# Literature Survey

## 1. Introduction

This project studies Wi-Fi signal quality classification using federated learning. Its dataset contains Wi-Fi signal measurements, while the PHONEID field is used to divide examples into simulated clients. This survey reviews research on federated learning, personalized models, data differences between clients, and the UJIIndoorLoc dataset.

## 2. Research papers

### 2.1 Federated Averaging

McMahan et al. introduced Federated Averaging (FedAvg), a method for training a shared model across devices. Each device trains on its local data and sends model updates to a server, which combines them. Raw training examples stay on the devices. This paper provides the foundation for the FedAvg baseline used in this project.

**Reference:** McMahan, B. et al. (2017). “Communication-Efficient Learning of Deep Networks from Decentralized Data.” AISTATS. [Paper and PDF](https://proceedings.mlr.press/v54/mcmahan17a.html)

### 2.2 UJIIndoorLoc Wi-Fi Dataset

Torres-Sospedra et al. presented UJIIndoorLoc, a public dataset for research using Wi-Fi fingerprints for indoor positioning. A fingerprint records signal strengths from nearby wireless access points. This project uses the dataset’s Wi-Fi signal measurements to create signal-quality classes. It uses PHONEID to form client groups for its federated-learning experiments; this is a project-specific use of the dataset.

**Reference:** Torres-Sospedra, J. et al. (2014). “UJIIndoorLoc: A New Multi-Building and Multi-Floor Database for WLAN Fingerprint-Based Indoor Localization Problems.” IPIN. [IEEE paper page](https://ieeexplore.ieee.org/document/7275492/)

### 2.3 Federated Learning with Personalization Layers (FedPer)

Arivazhagan et al. proposed FedPer, which shares some neural-network layers across clients while keeping personalization layers local to each client. The aim is to account for differences in client data. This paper is directly relevant to this project’s personalized FedPer model.

**Reference:** Arivazhagan, M. G. et al. (2019). “Federated Learning with Personalization Layers.” [Paper](https://arxiv.org/abs/1912.00818)

### 2.4 Federated Optimization in Heterogeneous Networks (FedProx)

Li et al. proposed FedProx to address differences in both the data held by clients and the computing work they can perform. Their research is relevant because the project’s client groups have different sample counts and different class distributions. FedProx is useful background for understanding why ordinary federated averaging can struggle when clients differ.

**Reference:** Li, T. et al. (2020). “Federated Optimization in Heterogeneous Networks.” MLSys. [Paper and PDF](https://proceedings.mlsys.org/paper_files/paper/2020/hash/1f5fe83998a09396ebe6477d9475ba0c-Abstract.html)

### 2.5 Federated Learning on Non-IID Data: A Survey

This survey reviews how non-IID data—data that differs between clients—affects federated-learning methods. It describes approaches for handling those differences and explains why a model that performs well for one client may not perform equally well for another. This supports the project’s analysis of client-level class distributions and personalized models.

**Reference:** (2021). “Federated Learning on Non-IID Data: A Survey.” *Neurocomputing*. [Survey](https://www.sciencedirect.com/science/article/pii/S0925231221013254)

### 2.6 Federated Learning Over Wireless Networks

This survey examines challenges in running federated learning over wireless networks. It discusses communication overhead, energy use, privacy, and practical deployment constraints. It provides wireless-network context for this project, while the project itself evaluates signal-quality classification using a dataset rather than deploying training across live wireless devices.

**Reference:** (2023). “Federated Learning Over Wireless Networks: Challenges and Solutions.” *IEEE Internet of Things Journal*. [IEEE paper page](https://ieeexplore.ieee.org/abstract/document/10153432)

## 3. Summary and connection to this project

The reviewed work establishes three ideas relevant to this project:

1. FedAvg provides a standard way to combine learning from multiple clients.
2. Client data can differ, which may reduce the performance of one shared model.
3. Personalization methods such as FedPer try to adapt models to individual clients.

This project applies these ideas to Wi-Fi RSSI signal-quality classification. It compares centralized learning, FedAvg, and FedPer using client groups formed from PHONEID. The project therefore combines an existing Wi-Fi fingerprint dataset with established federated-learning methods; it should not be described as a new federated-learning algorithm.

## 4. References

1. McMahan, B. et al. (2017). “Communication-Efficient Learning of Deep Networks from Decentralized Data.” AISTATS. [Link](https://proceedings.mlr.press/v54/mcmahan17a.html)
2. Torres-Sospedra, J. et al. (2014). “UJIIndoorLoc: A New Multi-Building and Multi-Floor Database for WLAN Fingerprint-Based Indoor Localization Problems.” IPIN. [Link](https://ieeexplore.ieee.org/document/7275492/)
3. Arivazhagan, M. G. et al. (2019). “Federated Learning with Personalization Layers.” [Link](https://arxiv.org/abs/1912.00818)
4. Li, T. et al. (2020). “Federated Optimization in Heterogeneous Networks.” MLSys. [Link](https://proceedings.mlsys.org/paper_files/paper/2020/hash/1f5fe83998a09396ebe6477d9475ba0c-Abstract.html)
5. (2021). “Federated Learning on Non-IID Data: A Survey.” *Neurocomputing*. [Link](https://www.sciencedirect.com/science/article/pii/S0925231221013254)
6. (2023). “Federated Learning Over Wireless Networks: Challenges and Solutions.” *IEEE Internet of Things Journal*. [Link](https://ieeexplore.ieee.org/abstract/document/10153432)