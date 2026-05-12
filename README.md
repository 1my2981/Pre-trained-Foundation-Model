
# ISAnet:Interpretable Sparse Attention Unsupervised Neural Network for Seismic Uncorrelated Noise Attenuation

[![](https://img.shields.io/badge/Dataset-v1.0-blue.svg)](https://champyin.com)![](https://img.shields.io/badge/python-3.11-green.svg?style=flat)

**ISAnet** is an unsupervised learning network based on sparse attention, designed to suppress uncorrelated noise in seismic data (e.g., erratic noise and random noise). By embedding a network visualization module, it enables comparative analysis of the denoising performance at different network layers. ISAnet provides an interpretive approach to the working mechanism of unsupervised denoising networks, breaks the black-box effect of neural networks, and enhances researchers’ understanding of the denoising behavior of unsupervised learning networks.

# :star:  Overview

## Current unsupervised denoising methods overlook signal sparsity, suffering from redundant parameters, low interpretability. ISANet, an unsupervised denoising network based on interpretable sparse attention U-Net. This Net is composed of the following parts.
 - Step 1:  A window of size `W_t​` $\times$ `W_x` is adopted to perform patching processing on the data `D` with dimensions `N_t` $\times$ `N_x`. Therefore, D_{patch} is obtained.
 - Step 2: All data` D _patch `is split at a ratio of 8:2, with 80% allocated to the training set and the remaining 20% to the validation set.
 - Step 3: Noisy data is used for training.` Median Filter`, `ISAnet` and `PatchUnet` are adopted to test and compare the denoising performance.
--The trained network parameters are saved as `xx.pth` file
 - Setp 4: The visualization module is used to analyze patch data of specific features and observe the performance of different output layers of the network, which provides direct evidence for the interpretability of the network.
---
#  :rocket:  File Description

- `data`：All **data** is stored in this folder, including: `seis2dsyn.mat`, `seis3dsyn.mat`, `real2d.mat`, `real3d.mat`

|name     |data size|Patch size|Slid size|Patches|
| :--------|:--- | :----- | :-------- |:-------- |
|seis2dsyn| 512 $\times$ 64   |   25 $\times$ 25   | 1 $\times$ 1   |19520 |
|seis3dsyn| 401 $\times$ 64 $\times$ 64 |  15 $\times$ 15 $\times$ 15 | 4 $\times$ 2 $\times$ 2 |66248 |
|real2d   |512 $\times$ 128   |   35 $\times$ 35   | 1 $\times$ 1   |50752 |
|real3d   |256 $\times$ 64 $\times$ 48 |  10 $\times$ 10 $\times$ 10 | 4 $\times$ 2 $\times$ 2 |35280 |

# :floppy_disk: Download 


- `ISAnet`：Both the denoising networks of ISAnet for synthetic data and field data are stored here, including both 2D and 3D versions.
- `PatchUnet`：Both the denoising networks of PatchUnet for synthetic data and field data are stored here, including both 2D and 3D versions.
- `medianFilter`：Both the denoising networks of Median filter for synthetic data and field data are stored here, including both 2D and 3D versions.
- `Visualization module`：`Visualization.ipynb` for the visualization of network parameters.

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

- Taking a trained model to analyze the data within a certain patch window, the results are presented as follows. It can be observed from the figure that with the increase of network depth, the sparse patch attention mechanism can better capture the difference between effective signals and noise.
![synint](https://github.com/furser1/ISAnet/blob/main/Fig/12.png)

- By analyzing the discreteness of features extracted from different layers, we find that the data discreteness becomes increasingly obvious as the network depth increases. This indicates that the network can effectively identify and distinguish valid signals from irrelevant noise.
![synint](https://github.com/furser1/ISAnet/blob/main/Fig/13.png)
# :sunrise_over_mountains: Maintainer
Chao Fu

For any questions regarding the dataset or scripts, please open an issue in this repository.
