
# ISAnet:Interpretable Sparse Attention Unsupervised Neural Network for Seismic Uncorrelated Noise Attenuation


**ISAnet** is an unsupervised learning network based on sparse attention, designed to suppress uncorrelated noise in seismic data (e.g., erratic noise and random noise). By embedding a network visualization module, it enables comparative analysis of the denoising performance at different network layers. ISAnet provides an interpretive approach to the working mechanism of unsupervised denoising networks, breaks the black-box effect of neural networks, and enhances researchers’ understanding of the denoising behavior of unsupervised learning networks.

## :star:  Overview

### Current unsupervised denoising methods overlook signal sparsity, suffering from redundant parameters, low interpretability. ISANet, an unsupervised denoising network based on interpretable sparse attention U-Net. This Net is composed of the following parts.
 - Step 1:  A window of size `W_t​` ×`W_x` is adopted to perform patching processing on the data `D` with dimensions `N_t`×`N_x`. Therefore, D_{patch} is obtained.
 - Step 2: All data `D_{patch}` is split at a ratio of 8:2, with 80% allocated to the training set and the remaining 20% to the validation set.
 - Step 3: Noisy data is used for training.` Median Filter`, `ISAnet` and `PatchUnet` are adopted to test and compare the denoising performance.
--The trained network parameters are saved as `xx.pth` file
 - Setp 4: The visualization module is used to analyze patch data of specific features and observe the performance of different output layers of the network, which provides direct evidence for the interpretability of the network.
---
##  :rocket:  File Description

- `data`：All **data** is stored in this folder, including: `seis2dsyn.mat`, `seis3dsyn.mat`, `real2d.mat`, `real3d.mat`

|name     |data size|Patch size|Slid size|Patches|
| :--------|:--- | :----- | :-------- |:-------- |
|seis2dsyn| 512 $\times$ 64   |   25 $\times$ 25   | 1 $\times$ 1   |19520 |
|seis3dsyn| 401 $\times$ 64 $\times$ 64 |  15 $\times$ 15 $\times$ 15 | 4 $\times$ 2 $\times$ 2 |66248 |
|real2d   |512 $\times$ 128   |   35 $\times$ 35   | 1 $\times$ 1   |50752 |
|real3d   |256 $\times$ 64 $\times$ 48 |  10 $\times$ 10 $\times$ 10 | 4 $\times$ 2 $\times$ 2 |35280 |



- `ISAnet`：Both the denoising networks of ISAnet for synthetic data and field data are stored here, including both 2D and 3D versions.
- `PatchUnet`：Both the denoising networks of PatchUnet for synthetic data and field data are stored here, including both 2D and 3D versions.
- `medianFilter`：Both the denoising networks of Median filter for synthetic data and field data are stored here, including both 2D and 3D versions.
- `Visualization module`：`Visualization.ipynb` for the visualization of network parameters.

 :boom: **Note Only one type of seismic data is presented here. If you are interested in other datasets, you can replace the corresponding input `.pth` model parameters and patch data `D_{patch}`.** 
## 
![The network structure of the proposed method is shown below.](https://github.com/furser1/ISAnet/blob/main/1.png)


