
# Pre-trained Foundation Model for Uncorrelated Noise Attenuation of Seismic Data

[![](https://img.shields.io/badge/Dataset-v1.0-blue.svg)](https://champyin.com)![](https://img.shields.io/badge/python-3.11-green.svg?style=flat)

**Pre-trained Foundation Model** is a seismic denoising method built on foundation models with sparse attention networks. Pre-trained on abundant open seismic datasets, the model has strong generalization. In practical use, it only needs a small amount of data for quick fine-tuning. It cuts model parameters and improves engineering efficiency.

# :star:  Overview

## Current unsupervised denoising methods overlook signal sparsity, suffering from redundant parameters. This model adopts sparse attention and pre-training strategies and mainly includes three modules below.
 - Step 1: A window of size `W_t​` $\times$ `W_x` is adopted to perform patching processing on the data `D` with dimensions `N_t` $\times$ `N_x`. Therefore, D_{patch} is obtained.
 - Step 2: During the pre-training stage, all data` D _patch `is split at a ratio of 8:2, with 80% allocated to the training set and the remaining 20% to the validation set.
 - Step 3: Target noisy data is used for training.` Median Filter`, `Pre-trained Foundation Model` and `PatchUnet` are adopted to test and compare the denoising performance.
--The trained network parameters are saved as `xx.pth` file
---
- `data`：All **data** is stored in this folder, including: `Amirsyn.mat`,`Amirsyn2d.mat`,`seis2dsyn.mat`, `seis3dsyn.mat`, `real2d.mat`, `real3d.mat`

|name     |data size|Patch size|Slid size|Patches|
| :--------|:--- | :----- | :-------- |:-------- |
|Amirsyn2d| 500 $\times$ 700   |   30 $\times$ 30   | 4 $\times$ 4   |20111 |
|Amirsyn| 500 $\times$ 35 $\times$ 40 |  20 $\times$ 15 $\times$ 15 | 4 $\times$ 2 $\times$ 2 |18634 |
|seis2dsyn| 512 $\times$ 64   |   30 $\times$ 30   | 1 $\times$ 1   |16905 |
|seis3dsyn| 401 $\times$ 64 $\times$ 64 |  20 $\times$ 15 $\times$ 15 | 4 $\times$ 2 $\times$ 2 |65572 |
|real2d   |512 $\times$ 128   |   30 $\times$ 30   | 1 $\times$ 1   |47817 |
|real3d   |256 $\times$ 64 $\times$ 48 |  20 $\times$ 15 $\times$ 15 | 2 $\times$ 2 $\times$ 2 |55692 |
#  :rocket:  File Description
- `Fine-tuning`：Both the denoising networks of Pre-trained Foundation Model during the fine-tuning stage for synthetic data and field data are stored here, including both 2D and 3D versions.
- `PatchUnet`：Both the denoising networks of PatchUnet for synthetic data and field data are stored here, including both 2D and 3D versions.
- `medianFilter`：Both the denoising networks of Median filter for synthetic data and field data are stored here, including both 2D and 3D versions.
 :boom: **Note Only one type of seismic data is presented here. If you are interested in other datasets, you can replace the corresponding input `.pth` model parameters and patch data  `D_patch` .** 
 
# The network structure of the proposed method is shown below:
![ISAnet](https://github.com/furser1/ISAnet/blob/main/Fig/1.png)
# :hotsprings: Example
## Loading the .mat Data 
- All data is stored in .mat format. You can run this script to convert the format from` MATLAB `->` Python`.
```makedown
import scipy.io as sio
data = sio.loadmat('syn2dsyn.mat')
Dc = data['DataClean']
Dn = data['DataNoisy']
```
##  Taking synthetic 2D seismic data as an example
- The figure below shows the clean data and the data contaminated by irrelevant noise. It contains one set of horizontal events and two sets of intersecting dipping events.
![syn2d](https://github.com/furser1/ISAnet/blob/main/Fig/3.png)

# :sunrise_over_mountains: Maintainer
Chao Fu

For any questions regarding the dataset, `pth` or scripts, please open an issue in this repository.
