# abstractive-text-summarization

This repository contains code for in-progress summarization experiments on a subset of the gigaword dataset.

Requirements
---
1. Create conda environment 

`conda env create -f environment.yml`  --gpu

`conda env create -f environment-cpu.yml`  --cpu

2. Install dependencies via:

`pip install -r requirements.txt`

3. Download `spacy` english module

`python -m spacy download en`

Dataset
--

The dataset used is a subset of the gigaword dataset and can be found [here](https://drive.google.com/file/d/0B6N7tANPyVeBNmlSX19Ld2xDU1E/view?usp=sharing).

It contains 3,803,955 parallel source & target examples for training and 189,649 examples for validation.

After downloading, we created article-title pairs, saved in tabular datset format (.csv) and extracted a sample subset (80,000 for training & 20,000 for validation). This data preparation can be found [here]().

An example article-title pair looks like this:

`source: the algerian cabinet chaired by president abdelaziz bouteflika on sunday adopted the #### finance bill predicated on an oil price of ## dollars a barrel and a growth rate of #.# percent , it was announced here .`

`target: algeria adopts #### finance bill with oil put at ## dollars a barrel`


Training on the complete dataset (3M) would take a really long time. So in order to train and experiment faster we use our sample subset of 80,000. 

Current Features
--
* model architecture supports LSTM & GRU (biLSTM-LSTM or biGRU-GRU)
* implements attention mechanism (Bahdanau et al. & Luong et al.(dot))
* implements three way tied embeddings (encoder input, decoder input and decoder output embedding)
* initializes encoder-decoder with pretrained embeddings (e.g. fasttext, glove)
* implements custom callbacks during training (tensorboard visualization for PyTorch, save best model & log checkpoint)

To-Do
--
* implement beam search at inference time
* experiment with transformer network 



