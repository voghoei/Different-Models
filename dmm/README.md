# Deep Markov Models

## Overview 
This repository contains theano code for implementing Deep Markov Models. The code is documented and should be easy to modify for your own applications. 

<p align="center"><img src="model_th/images/dmm.png" alt="Deep Markov Model" width="300"></p>

The code uses variational inference during learning to maximize the likelihood of the observed data:
<p align="center"><img src="model_th/images/ELBO.png" width="500" height="70" alt="Evidence Lower Bound"></p>

* Generative Model
    * The figure depicts a state space model for time-varying data. 
    * The latent variables `z1...zT` and the observations `x1...xT` together describe the generative process for the data.
    * The emission `p(x_t|z_t)` and transition functions `p(z_t|z_{t-1})` are parameterized by deep neural networks
* Inference Model
    * The function `q(z1..zT | x1...xT)` represents the inference network
    * This is a parametric approximation to the variational posterior used for learning at training time
    and for inference at test time. 

## Requirements
This package has the following requirements:
* `python2.7`
* [Theano](https://github.com/Theano/Theano)
    * Used for automatic differentiation
* [theanomodels](https://github.com/clinicalml/theanomodels) 
    * Wrapper around theano that takes care of bookkeeping, saving/loading models etc. Clone the github repository and add its location to the PYTHONPATH environment variable so that it is accessible by python.
* An NVIDIA GPU w/ atleast 6G of memory is recommended.

## Optional
I used the following `~/.theanorc` configuration file:
```
[global]
floatX=float32

[mode]=FAST_RUN

[nvcc]
fastmath=True

[cuda]
root=/usr/local/cuda
```

You can change whether the model is run on the GPU or CPU by modifying the `THEANO_FLAGS`. See [here](http://deeplearning.net/software/theano/library/config.html) for documentation.

## Folders 
* **Model Code**: [`model_th`](model_th/): This folder contains raw theano code implementing the model. See the folder for details on how the DMM was implementation
and pointers to portions of the code. 
* **Datasets**: [`dmm_data`](dmm_data/): This folder contains code to load the polyphonic music data and a synthetic dataset. Add or change code in `load.py`(dmm_data/load.py) to run the model on your own data. 
* **Tutorials**: [`ipynb`](ipynb/): This folder contains some IPython notebooks with examples on loading and running the model on your own data.  
* **Hyperparameters**: [`parse_args.py`](parse_args.py): This file contains hyperparameters used by the model. Run `python parse_args.py -h` 
for an explanation of what the various choices of parameters change in the generative model and inference network.  
* **Modeling Polyphonic Music**: [`expt`](expt/): Experimental setup for running the DMM on the [polyphonic music dataset](http://www-etud.iro.umontreal.ca/~boulanni/icml2012) 
* **Template Folder for Training DMMs**: [`expt_template`](expt_template/) : Experimental setup for running the DMM on synthetic real-valued observations. 

## Running the model on your data
* A general purpose tutorial for setting up and running the model can be found in the [IPython Notebooks](ipynb/).
* The code currently supports binary and real-valued data. An example of modeling binary data may be found in [`expt/`](expt/). 

## References: 
Please cite the following paper if you find the code useful in your research: 
```
@inproceedings{krishnan2016structured,
  title={Structured Inference Networks for Nonlinear State Space Models},
  author={Krishnan, Rahul G and Shalit, Uri and Sontag, David},
  booktitle={AAAI},
  year={2017}
}
```
This paper subsumes the work in : [Deep Kalman Filters] (https://arxiv.org/abs/1511.05121)
