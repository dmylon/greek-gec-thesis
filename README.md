# Development of a Grammatical Error Correction Model for the Greek Language

## Description

This thesis project focuses on the creation of a Grammatical Error Correction System for the Greek Language, using Neural Machine Translation and Transformer-Based models. The main objective is to develop a model that improves the quality of written texts in Greek, by correcting errors regarding spelling, grammar or syntax.

## Contents

The files included in this repository are the following:

- **greek_basic_training.ipynb**: This notebooks contains the code for finetuning the "Greek-T5-GreekSum" model introduced in [Giarelis et al., 2023](https://arxiv.org/pdf/2311.07767). The finetuning process involves two already existing datasets for the Grammatical Error Correction Task in Greek Language, namely GNC and GLC2 introduced in [Korre et al., 2021](https://aclanthology.org/2021.ranlp-1.81.pdf) and [Korre and Pavlopoulos, 2022](https://aclanthology.org/2022.lrec-1.532.pdf) respectively.

- **greek_dataset_production.ipynb**: This notebook contains the code for producing a Synthetic Grammatical Error Correction Dataset in Greek along with some statistics associated with the dataset.

- **greek_synthetic_training.ipynb**: This notebook contains the code for finetuning a model in the new Syntetic dataset created in the previously mentioned notebook.

- **datasets**: A folder containing all necessary synthetic dataset files.
  

