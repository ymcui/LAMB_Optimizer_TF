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
The implementation is based on [BERT repository](https://github.com/google-research/bert), which uses `AdamWeightDecayOptimizer` (appears in [`optimization.py`](https://github.com/google-research/bert/blob/master/optimization.py)).

- Just use it as a regular optimizer in TensorFlow, similar to `Adam` or `AdamWeightDecayOptimizer`.
- Find LAMB optimizer in `optimization.py`.


## Results on MNIST
- I don't have TPU Pod to test its scalability on large batch 😂, but tested on MNIST for verify its effectiveness on small batch.
- Here are the numbers on several three classical neural networks **(MLP, CNN, Bi-RNN, Bi-GRU, Bi-LSTM)**. 
- All optimizers use an initial learning rate of **0.001** (default settings).
- All experiments are carried out for **5 times** and we report `MAX (AVG±STD)`. You know the GPU/TPU won't get exactly the same results even we use fixed random seed.

@NVIDIA TESLA T4
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | - | - | - | - | - | Just ordinary Adam |
| AdamW | - | - | - | - | - | Used in BERT |
| **LAMB** | - | - | - | - | - | New optimizer for large batch |

**Reproducibility: Check [`mnist_tensorflow.ipynb`](https://github.com/ymcui/LAMB_Optimizer_TF/blob/master/mnist_tensorflow.ipynb) for details.**


## References
- Large Batch Optimization for Deep Learning: Training BERT in 76 minutes. https://arxiv.org/abs/1904.00962v3
- BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding. https://arxiv.org/abs/1810.04805

## Issues
For help or issues, please submit a GitHub issue.
