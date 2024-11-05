# GPFQ: Post-Training Quantization On Pre-trained Model with Hyper-parameter Analysis
## Overview
This is the repository for DSC180 Q1 project, for conducting post-training quantization, specifically GPFQ algorithm, on MNIST dataset.

## Guide on Installing Dependencies

The repo would reuqire python version that is greater than `3.8.0` is installed in the user's 
machine.

To install the necessary dependency, one can first start a virtual environment
by doing the following: 
```
python3 -m venv .venv
source .venv/bin/activate
```
Then can install file using the `requirements.txt` file
```
pip3 install -r requirements.txt
```
This should install all the required dependencies of this project. 

## Repo Overview

This repository contains code for replicating GPFQ quantization algorithm and notebook for holding MNIST data and pre-trained model. There are several directories, each serving a specific purpose. Below is an overview of each directory to help you navigate the codebase effectively.

### `Logs`

This is the directory holding the logs data for recording the quantization result. 

- **`init_log.py`**
    This script initializes and creates the log file used to record various quantization metrics and results. The log file format includes several important entries that facilitate detailed analysis and comparison across experiments. Here are some important entry in the log file:
    - `Original Top5 Accuracy`: The Top-5 accuracy before quantization.
    - `Quantized Top5 Accuracy`: The Top-5 accuracy post quantization.
    - `MLP_Alphabet_Scalar`, `CNN_Alphabet_Scalar`: Scalars used for alphabet quantization in MLP and CNN layers.
    - `Regularizer`, `Lambda`: Regularization type and lambda value used in quantization to sparsify weights.

### `quantized_models`

This is the directory holding the quantized model.

### `src`

This is the directory holding the additional resources

- **`data_loaders.py`**
    This is the script for loading data to the GPFQ algorithm

- **`main.py`**
    This is the main function for GPFQ, in charge of taking hyper-parameters including number of bits for quantization and scalars.

- **`quantize_neural_net.py`**
    Contains function for running the quantization algorithm by quantizing layer by layer.

- **`step_algorithm.py`**
    Step algorithm for quantizing each layer

- **`utils.py`**
    Scripts containing helper functions

- **`setup_dataset.ipynb`**
    This is the notebook containing working code for loading MNIST data through keras, and train neural network from pytorch on MNIST data. It also include function to load data into GPFQ for quantization.

### `requirements.txt`

This is the file holding the required package version for the environment.


## Commands to Run
To run GPFQ on CIFAR-10, first cd into `src`, then use the following command:
```
python main.py -ds CIFAR10 -model resnet18 -b 4 -bs 256 -s 1.16
```
