# Full Results on MNIST

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


### Batch=256
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 95.85 | 98.73 | 97.05 | 99.00 | **99.12** | Just ordinary Adam |
| AdamW | 95.40 | 98.67 | 97.75 | **99.05** | 98.92 | Used in BERT |
| **LAMB** | **97.88** | **99.13** | **98.02** | 98.88 | 98.76 | New optimizer for large batch |


### Batch=512
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 94.49 | 98.49 | 98.01 | 98.99 | **98.87** | Just ordinary Adam |
| AdamW | 94.76 | 98.36 | 97.92 | **99.00** | 98.78 | Used in BERT |
| **LAMB** | **98.13** | **99.11** | **98.08** | 98.55 | 98.47 | New optimizer for large batch |


### Batch=1024
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 93.05 | 97.92 | 98.10 | **98.94** | 98.67 | Just ordinary Adam |
| AdamW | 93.67 | 98.00 | 98.19 | 98.86 | **98.82** | Used in BERT |
| **LAMB** | **97.68** | **98.82** | **98.27** | 98.61 | 98.47 | New optimizer for large batch |


### Batch=2048
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 92.21 | 97.63 | 98.05 | **98.77** | 98.54 | Just ordinary Adam |
| AdamW | 92.46 | 97.75 | 97.85 | 98.47 | **98.73** | Used in BERT |
| **LAMB** | **96.13** | **98.62** | **98.10** | 98.54 | 98.21 | New optimizer for large batch |



### Batch=4096
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 91.66 | 97.12 | **97.87** | **98.72** | 98.35 | Just ordinary Adam |
| AdamW | 92.21 | 97.31 | 97.64 | 98.69 | **98.43** | Used in BERT |
| **LAMB** | **95.53** | **98.37** | 97.75 | 98.58 | 97.74 | New optimizer for large batch |


### Batch=8192
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 90.68 | 96.54 | 97.04 | 98.50 | 98.01 | Just ordinary Adam |
| AdamW | 92.16 | 96.98 | **97.08** | **98.69** | **98.36** | Used in BERT |
| **LAMB** | **94.22** | **98.26** | 96.82 | 96.73 | 94.70 | New optimizer for large batch |


### Batch=16384
| Optimizer | MLP | CNN | Bi-RNN | Bi-GRU | Bi-LSTM | Note | 
| :------ | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| Adam | 88.46 | 95.06 | 95.98 | 97.81 | 97.74 | Just ordinary Adam |
| AdamW | 91.46 | 96.57 | **96.34** | **98.45** | **98.39** | Used in BERT |
| **LAMB** | **93.23** | **97.89** | 93.76 | 87.60 | 80.36 | New optimizer for large batch |

