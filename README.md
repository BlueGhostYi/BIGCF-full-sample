# BIGCF-full-sample
This is the PyTorch implementation for our SIGIR 2024 paper:
> Yi Zhang, Lei Sang, and Yiwen Zhang*. 2024. [Exploring the Individuality and Collectivity of Intents behind Interactions for Graph Collaborative Filtering](https://arxiv.org/abs/2405.09042). In Proceedings of the 47th International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR ’24).

This repo is the full sampling version, and for the corresponding version of the paper see: https://github.com/BlueGhostYi/BIGCF.

## Full sampling version

This version of BIGCF employs the same settings as the mainstream graph recommender system (e.g., LightGCN, SGL, and SimGCL). Specifically, each iteration of the process randomly picks all samples and computes the recommendation metrics with all-ranking. Due to the change in the sampling process, there are some changes in the various hyper-parameter settings of the BIGCF, and the values given in the paper cannot simply be used.

## Environment
```
python == 3.8.18
pytorch == 2.1.0 (cuda:12.1)
torch-sparse == 0.6.18
scipy == 1.10.1
numpy == 1.24.3
```

## Examples to run the codes
Steps to run the code:
1. In the folder . /configure to configure the BIGCF.txt file
2. Set the BIGCF according to the optimal parameters. Using the classic Yelp2018 dataset as an example, here are the corresponding hyperparameter settings (Other parameters can use the default settings):
```
dataset = yelp2018
reg_lambda = 0.0001
intent_size = 128
ssl_lambda = 0.8
ssl_temperature = 0.2
int_temperature = 1.0
```

3. Run main.py.

## Recommended setting range
When running BIGCF on a new dataset, it can be referenced from the following search ranges, where **bold** is the suggested default:
* `learning_rate`: [0.005, **0.001**, 0.0005, 0.0001];
* `reg_lambda`: [0.001, **0.0001**, 0.00001];
* `GCN_layer`: [1, 2, **3**, 4];
* `intent_size`: [32, 64, **128**, 256];
* `ssl_lambda`: [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, **0.8**, 0.9, 1.0, 2.0, 3.0];
* `ssl_temperature`: [0.05, 0.1, **0.2**, 0.3];


## Citation
If you find this work is helpful to your research, please consider citing our paper:
```
@inproceedings{zhang2024exploring,
  title={Exploring the Individuality and Collectivity of Intents behind Interactions for Graph Collaborative Filtering},
  author={Zhang, Yi and Sang, Lei and Zhang, Yiwen},
  booktitle={Proceedings of the 47th International ACM SIGIR Conference on Research and Development in Information Retrieval},
  pages={1253--1262},
  year={2024}
}
```
