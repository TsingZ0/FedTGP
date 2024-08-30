# Introduction

This is the implementation of our paper *[FedTGP: Trainable Global Prototypes with Adaptive-Margin-Enhanced Contrastive Learning for Data and Model Heterogeneity in Federated Learning](https://arxiv.org/abs/2401.03230)* (accepted by AAAI 2024). 

*Key words: federated learning, data heterogeneity, model heterogeneity, communication overhead, intellectual property (IP) protection*

Take away: We enhance the typical HtFL method FedProto with Trainable Global Prototypes (TGP) and Adaptive-margin-enhanced Contrastive Learning (ACL), making it more versatile and resilient to various model heterogeneities. 

- [Slides](./[AAAI]%20FedTGP.pdf)
- [Poster](./FedTGPPoster.pdf)

**Citation**

```
@inproceedings{zhang2024fedtgp,
  title={FedTGP: Trainable Global Prototypes with Adaptive-Margin-Enhanced Contrastive Learning for Data and Model Heterogeneity in Federated Learning},
  author={Zhang, Jianqing and Liu, Yang and Hua, Yang and Cao, Jian},
  booktitle={Proceedings of the AAAI Conference on Artificial Intelligence},
  year={2024}
}
```

![](./fig2.png)
The global and client prototypes in FedProto and our FedTGP. Different colors and numbers represent classes and clients, respectively. Circles represent the client prototypes and triangles represent the global prototypes. The black and yellow dotted arrows show the inter-class separation among the client and global prototypes, respectively. Triangles with dotted borders represent our Trainable Global Prototypes (TGP). The red arrows show the inter-class intervals between TGP and the client prototypes of other classes in our Adaptive-margin-enhanced Contrastive Learning (ACL).


# Dataset

Due to the file size limitation, we only upload the statistics (`config.json`) of the Cifar10 dataset in the practical setting ($\beta=0.1$). Please refer to our popular repository [PFLlib](https://github.com/TsingZ0/PFLlib) and [HtFLlib](https://github.com/TsingZ0/HtFLlib) to generate all the [datasets](https://github.com/TsingZ0/PFLlib?tab=readme-ov-file#datasets-and-scenarios-updating) and create the required python [environment](https://github.com/TsingZ0/HtFLlib?tab=readme-ov-file#environments). 


# System

Learning reasonable global prototypes can be challenging in some cases, particularly due to the limited number of client prototypes and the introduced adaptive margin during ACL. To address this, consider setting a larger `top_cnt` and ensuring that the global communication iteration number is larger than 1000, which should result in a `Server loss` smaller than 0.001. The best accuracy is typically achieved when a minimal `Server loss` is obtained. In most of our experiments, we achieved a `Server loss` of 0.0. 

- `main.py`: system configurations. 
- `run_me.sh`: command lines to run experiments. It is advisable to retune hyperparameters on new tasks.
- `flcore/`: 
    - `clients/`: the code on clients. See [HtFL](https://github.com/TsingZ0/HtFL) for baselines.
    - `servers/`: the code on servers. See [HtFL](https://github.com/TsingZ0/HtFL) for baselines.
    - `trainmodel/`: the code for some heterogeneous client models. 
- `utils/`:
    - `data_utils.py`: the code to read the dataset. 
    - `mem_utils.py`: the code to record memory usage. 
    - `result_utils.py`: the code to save results to files. 