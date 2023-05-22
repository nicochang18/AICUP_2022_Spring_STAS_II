# AICUP_STAS_II
>The followings are the files I used in AI CUP STAS_II competition. If you have any questions, please comment in the Issues Block.

My score:
-|Public Data|Private Data|
--|--|--|
Rank|5 / 307|6 / 307|
Score|0.918|0.916|

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

# Models
Name|Code File|Weight File|Result|
--|--|--|--|
Label Process|[LabelProcess.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/LabelProcess.ipynb)|-|-|
NFNet + PAN|[Training_nfnet_PAN.ipynb.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/Training_nfnet_PAN.ipynb)|[tu-eca_nfnet_l1_PAN.pth](https://drive.google.com/file/d/1B-a1_T84N81yglrP_BE-Bd7papf6jfFZ/view?usp=sharing)|-|
NFNet + DeepLabV3Plus|[Training_nfnet_deeplab3+.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/9e0fdd11a78758a489932799ccf34c7ce162c49d/Training_nfnet_deeplab3+.ipynb)|[tu-eca_nfnet_l1_DeepLabV3Plus.pth](https://drive.google.com/file/d/18Dg7QImO0dZzj7G13rREsL4mrXWfqN7L/view?usp=sharing)|-|
EfficientNet_V2_s + DeepLabV3Plus|[Training_efficientnet_PAN.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/c60273d1b103c1cba6357babac48d8f02ea2be8f/Training_efficientnet_PAN.ipynb)|[tf_efficientnetv2_s_in21ft1k_PAN.pth](https://drive.google.com/file/d/1kWN7jx7_BrWMRYlOaTHHEEfYf_xLLNZb/view?usp=sharing)|-|
Ensemble|[Ensemble.ipynb](https://github.com/nicochang18/AICUP_STAS_II/blob/df05d434dec3ce15f7e252d151a143f9a063531b/Ensemble.ipynb)|-|[Result](https://github.com/nicochang18/AICUP_STAS_II/blob/051a60e569a6c78d1593adf3da637a1923ad56b1/Ensemble_Result.zip)|

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
**The predict image folders are in the same folder with Ensemble.ipyth**  

# Run Code
Please run the codes with this order:
1. Label Process
2. Train Models
3. Ensemble
