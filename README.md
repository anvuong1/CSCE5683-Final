## An extension of BGNet baseline for CSCE-5683 Final Project

> **Students:**
> Nhat-Tan Bui (011046130),
> An Vuong (011066086)

## Introduction

This repository contains our histogram equalization (HE) extension for the "**Boundary-Guided Camouflaged Object Detection**" [![Arxiv Page](https://img.shields.io/badge/Arxiv-2207.00794-red?style=flat-square)](https://arxiv.org/abs/2207.00794) (BGNet)  baseline.
The original implementation can be found at its <a href="https://github.com/thograce/BGNet">repository</a>. The only difference between our extension and the original implementation lies in the _utils/tdataloader_, where we implement the "_rgb_loader_he_" function. This function is used to load an image given its path, and then apply histogram equalization (HE) to that image.
For the HE operation, we leverage the <a href="https://pillow.readthedocs.io/en/stable/reference/ImageOps.html#PIL.ImageOps.equalize">ImageOps.equalize()</a> function from Pillow library.
This HE operation is used as a preprocessing step for both training and testing to validate its effectiveness in the camouflaged object detection (COD) task.
Although the results of HE for all experiments are _not good_ (please refer to our <a href="[https://drive.google.com/file/d/1BQoDZMORJXoVFHEcnvKdWNUy5g46ckds/view?usp=drive_link](https://drive.google.com/file/d/1B0F7tw3KGfTEHRxgP7YsH_hF647iHW1O/view?usp=sharing)">report</a>), this investigation has expanded our understanding of image processing algorithm, deep learning
architecture, and COD task. We hope this investigation can contribute to the improvement of COD task.

## Usage

1. Installation

```
conda create --name BGNet python=3.6
conda activate BGNet
pip install -r requirement.txt
```

2. Datasets

    + downloading testing dataset and move it into `./data/TestDataset/`, 
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1SLRB5Wg1Hdy7CQ74s3mTQ3ChhjFRSFdZ/view?usp=sharing).
    
    + downloading training dataset and move it into `./data/TrainDataset/`, 
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1Kifp7I0n9dlWKXXNIbN7kgyokoRY4Yz7/view?usp=sharing).

3. Checkpoints
    
    + downloading pretrained weights of all experiments and move it into `./checkpoints/`, 
    which can be found in this [download link (Google Drive)](https://drive.google.com/drive/folders/18C9rtogy8caXHfDNaRtcqp9vpDq7bysd?usp=drive_link).
    This Drive contains three checkpoints: _Exp_1_2_ is the original checkpoint from the authors, _Exp_3_4_ is the checkpoint we retrain the original implementation, _Exp_5_6_ is the checkpoint we
    retrain the original implementation with the histogram equalization (HE) preprocess when training. Experiment 2 uses the same checkpoint as experiment 1, but images are preprocessed with HE during testing; the same applies to experiments 3-4 and 5-6.
    
    + downloading Res2Net weights and move it into `./models/res2net50_v1b_26w_4s-3cf99910.pth`[download link (Google Drive)](https://drive.google.com/file/d/1_1N-cx1UpRQo7Ybsjno1PAg4KE1T9e5J/view?usp=sharing).
      
4. Training/Testing
```
etrain.py
etest.py
```

5. Evaluation
```
pip install pysodmetrics
eval.py
```

## Acknowledgment

This repository is based on the <a href="https://github.com/thograce/BGNet">original implementation</a> of Yujia Sun, Shuo Wang, Chenglizhao Chen, and Tian-Zhu Xiang. We also thank to Prof. Khoa Luu from the University of Arkansas for guiding us in the Image Processing course and this project.
