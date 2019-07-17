# LAMB Optimizer (TensorFlow)
This is a simple implementation of LAMB Optimizer, which appeared in the paper [**"Large Batch Optimization for Deep Learning: Training BERT in 76 minutes"**](https://arxiv.org/abs/1904.00962v3). 

The older name of the paper was ["Reducing BERT Pre-Training Time from 3 Days to 76 Minutes"](https://arxiv.org/abs/1904.00962v1)


## Notes
- **This is NOT an official implementation.**
- LAMB optimizer changes slightly from arXiv v1 ~ v3.
- We implement v3 version (which is the latest version on June, 2019.).
- Some uncertain parts are clarified by consulting original authors (such as `scaling function`).


## Algorithm
LAMB optimizer is originally designed for large batch learning in neural networks, but could also used in small batch size as indicated by authors.

![algorithm.png](https://github.com/ymcui/LAMB_Optimizer_TF/blob/master/algorithm.png)


## Usage
The implementation is based on BERT [repository](https://github.com/google-research/bert), which uses `AdamWeightDecayOptimizer` (appears in [`optimization.py`](https://github.com/google-research/bert/blob/master/optimization.py)) for pre-training and fine-tuning.

- Just use `LAMBOptimizer` as a regular optimizer in TensorFlow, similar to `Adam` or `AdamWeightDecayOptimizer`.
- Find LAMB optimizer in `optimization.py`.
- There is nothing special to tune other than initial `learning_rate`.


## Results on MNIST
- I don't have TPU Pod to test its scalability on BERT with large batch 😂, but tested on MNIST for verify its effectiveness.
- All optimizers use an initial learning rate of **0.001** (default settings), and did **NOT** scale to the batch size (may bring another gain, but leave it for you to test).
- All the experiments are done on NVIDIA TESLA T4.

Here are the numbers on several three classical neural networks **(MLP, CNN, Bi-RNN, Bi-GRU, Bi-LSTM)** with different optimizers **(Adam, AdamW, LAMB)**. 

I only list results of batch={64, 128, 1024, 16384}. For full results, please see [`FULL_RESULTS.md`](https://github.com/ymcui/LAMB_Optimizer_TF/blob/master/FULL_RESULTS.md).


### Batch=64
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 97.03 | 98.93 | 96.24 | 98.92 | **99.04** | Just ordinary Adam |
| AdamW | 97.11 | 99.01 | 96.50 | **99.11** | **99.04** | Used in BERT |
| **LAMB** | **98.27** | **99.33** | **97.73** | 98.83 | 98.94 | New optimizer for large batch |


### Batch=128
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 96.38 | 98.76 | 97.73 | **99.08** | **99.09** | Just ordinary Adam |
| AdamW | 96.57 | 98.72 | **98.05** | 98.96 | 99.00 | Used in BERT |
| **LAMB** | **97.90** | **99.20** | 98.04 | 98.87 | 98.76 | New optimizer for large batch |


### Batch=1024
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 93.05 | 97.92 | 98.10 | **98.94** | 98.67 | Just ordinary Adam |
| AdamW | 93.67 | 98.00 | 98.19 | 98.86 | **98.82** | Used in BERT |
| **LAMB** | **97.68** | **98.82** | **98.27** | 98.61 | 98.47 | New optimizer for large batch |


### Batch=16384
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 88.46 | 95.06 | 95.98 | 97.81 | 97.74 | Just ordinary Adam |
| AdamW | 91.46 | 96.57 | **96.34** | **98.45** | **98.39** | Used in BERT |
| **LAMB** | **93.23** | **97.89** | 93.76 | 87.60 | 80.36 | New optimizer for large batch |


### Several Conclusions
**Note: The conclusions are only made by the results above.**

- LAMB consistently outperforms `Adam` and `AdamW` in most of the times, and shows consistent results among different batch sizes.
- LAMB shows big advantage than `Adam` and `AdamW` on large batch, showing its excellent scalability.
- LAMB failed to outperform than `Adam` and `AdamW` on complex RNN-based models, despite batch size.


## Reproducibility
Check [`mnist_tensorflow.ipynb`](https://github.com/ymcui/LAMB_Optimizer_TF/blob/master/mnist_tensorflow.ipynb) for details.

Note: You know the GPU/TPU won't get exactly the same results even we use fixed random seed.


## References
- Large Batch Optimization for Deep Learning: Training BERT in 76 minutes. https://arxiv.org/abs/1904.00962v3
- BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. https://arxiv.org/abs/1810.04805

## Issues
For help or issues, please submit a GitHub issue.
