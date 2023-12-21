# Introduction

This is the implementation of our paper *FedTGP: Trainable Global Prototypes with Adaptive-Margin-Enhanced Contrastive Learning for Data and Model Heterogeneity in Federated Learning* (accepted by AAAI 2024). 


# Dataset

Due to the file size limitation of the supplementary material, we only upload the statistics (`config.json`) of the Cifar10 dataset in the practical setting ($\beta=0.1$). Please refer to the popular repository [PFLlib](https://github.com/TsingZ0/PFLlib) to generate all the datasets and create the required python environment. 


# System

- `main.py`: system configurations. 
- `run_me.sh`: command lines to run experiments. 
- `flcore/`: 
    - `clients/`: the code on clients. See [HtFL](https://github.com/TsingZ0/HtFL) for baselines.
    - `servers/`: the code on servers. See [HtFL](https://github.com/TsingZ0/HtFL) for baselines.
    - `trainmodel/`: the code for models. 
- `utils/`:
    - `data_utils.py`: the code to read the dataset. 
    - `mem_utils.py`: the code to record memory usage. 
    - `result_utils.py`: the code to save results to files. 