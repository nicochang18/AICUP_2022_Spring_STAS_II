# AICUP_STAS_II
>The followings are the files I used in AI CUP STAS_II competition. If you have any questions, please comment in the Issues Block.

My score:
-|Public Data|Private Data|
--|--|--|
Rank|5|6|
Score|0.92|0.92|

# Environment
**Server:** NVIDIA DLI envent (Ubuntu 18.04.4 LTS + 16 GB memory + Tesla T4 GPU)  
**Laguage:** Python 3.6.9  
**Pretrained Model:** Segmentation Models Pytorch

# Packages
**MONAI:** version 0.8.1  
**Pytorch:** version 1.11.0a0+17540c5  
**TorchVision:** version 0.12.0a0  
**Segmentation_Models_Pytorch:** version 0.3.0-dev  
**adabelief-pytorch:** version 0.2.0  

### Code
```
!pip install monai
!pip install torch
!pip install torchvision
!pip install -U Setuptools
!pip install git+https://github.com/qubvel/segmentation_models.pytorch
!pip install adabelief-pytorch==0.2.0
!pip install ipywidgets widgetsnbextension
!jupyter nbextension enable --py widgetsnbextension
```
https://github.com/nicochang18/AICUP_STAS_II/blob/c60273d1b103c1cba6357babac48d8f02ea2be8f/Training_efficientnet_PAN.ipynb
# Models
Name|Code File|Weight File|Result|
--|--|--|--|
Label Process|[LabelProcess.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/LabelProcess.ipynb)|-|
NFNet + PAN|[Training_nfnet_PAN.ipynb.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/Training_nfnet_PAN.ipynb)|[tf_efficientnetv2_m_in21ft1k.pth]()|[Result 1]()|
NFNet + DeepLabV3Plus|[Training_nfnet_deeplab3+.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/Training_nfnet_deeplab3+.ipynb)|[tu-eca_nfnet_l2_DeepLabV3Plus.pth]()|[Result 2]()|
EfficientNet_V2_s + DeepLabV3Plus|[Training_efficientnet_PAN.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/c60273d1b103c1cba6357babac48d8f02ea2be8f/Training_efficientnet_PAN.ipynb)|[tu-tf_efficientnet_b6_ns.pth]()|[Result 3]()
Ensemble|[Image_ensemble.ipynb]()|-|[Result]()|

# Before Running
Check the path is correct 

**Data Folder Structure:**  
```
YOUR PATH  
        ├Train_Images  
        ├Train_Annotations_png  
        ├Public_Image  
        ├Private_Image  
        └Predict  
```
**Model and weight files are in same folder**  
Path for ensemble:  
The predict image folders are in the same folder with Ensemble.ipyth

# Run Code
Please run the codes with this order:
1. Label Process
2. Train Models
3. Ensemble
