# AICUP_STAS_II
>he followings are the files I used in AI CUP STAS_II competition. If you have any questions, please comment in the Issues Block.

My score:
-|Public Data|Private Data|
--|--|--|
Rank|5|6|
Score|0.92|0.92|

# Environment
Server: NVIDIA DLI envent (Ubuntu 18.04.4 LTS + 16 GB memory + Tesla T4 GPU)\
Laguage: Python 3.6.9\
Pretrained Model: Segmentation Models Pytorch

# Packages
```
!pip install monai
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
Label Process|[DataPreprocess.ipynb]()|-|
NFNet + PAN|[tf_efficientnetv2_m_in21ft1k.ipynb]()|[tf_efficientnetv2_m_in21ft1k.pth]()|[Result 1]()|
NFNet + DeepLabV3Plus|[tu-eca_nfnet_l2_DeepLabV3Plus.ipynb]()|[tu-eca_nfnet_l2_DeepLabV3Plus.pth]()|[Result 2]()|
EfficientNet_V2_s + DeepLabV3Plus|[tu-tf_efficientnet_b6_ns.ipynb]()|[tu-tf_efficientnet_b6_ns.pth]()|[Result 3]()
Ensemble|[Image_ensemble.ipynb]()|-|[Result]()|

# Instruction
Please run the codes with this order:
1. Label Process
2. Train Models
3. Ensemble

### 前處理
需修改資料夾，資料夾內需包含LabelMe之.json檔

```
folder_path = "{YOUR PATH}"

如 : 
folder_path = "SEG_Train_Datasets/Train_Annotations/"
os.listdir(folder_path)[:5]
```

### 模型訓練以及驗證
需修改訓練圖片之資料夾
```
data_path = "{YOUR PATH}"
```

如下之`SEG_Train_Datasets`，資料夾內需放子資料夾`Train_Images`及`Train_Annotations_png`，前者存放訓練Image後者存放訓練Mask
```
data_path = './SEG_Train_Datasets/'

SEG_Train_Datasets
        |-> Train_Images
        |-> Train_Annotations_png
```
>

改驗證圖片路徑
```
tempdir = "{YOUR PATH}"  

如:
tempdir = "./Pravite_Image1/"
```

驗證時除了需確認驗證圖片的檔案位置，還須修改權重路徑到你權重下載的位置

```
model.load_state_dict(torch.load("{YOUR PATH}"))
```



>

此外因為我三個模型各自的預測結果圖都是預設存到同目錄底下`./Predict`資料夾，所以同時跑三個模型時輸出會被蓋掉，可在模型輸出處做修改
```
saverPD = SaveImage(output_dir="{YOUR PATH}", output_ext=".png", output_postfix=f"{Pub_data[i].split('/')[-1].split('.')[0]}",scale=255,separate_folder=False)
saverPD(test_outputs[0].cpu())
```


### Ensemble Code
Ensemble時也需要注意三個的檔案位置

```
path1 = "{Predict Path1}"
path2 = "{Predict Path2}"
path3 = "{Predict Path3}"
```

此外還要注意的是做Ensemble的照片通道數需統一，即 (1716, 942, 1) 或 (1716, 942, 3)，如不是則必須修改程式，建議全部改為單一通道。

1 Channel
```
img1 = Image.open(os.path.join(path1, filename))
img1_ar = np.asarray(img1)
img1_ar = np.where(img1_ar > 0, 1, 0)

```

3 or more Channel
```
img1 = Image.open(os.path.join(path1, filename))
img1_ar = np.asarray(img1)
img1_ar = np.where(img1_ar[:, :, 0] > 0, 1, 0)

```
