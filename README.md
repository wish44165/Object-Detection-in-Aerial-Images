# [無人機飛行載具之智慧計數競賽](https://tbrain.trendmicro.com.tw/Competitions/Details/25) (TEAM_2054)




## 1. Environment Setup

<details>

<summary>Hardware information</summary>
  
- CPU: i7-11700F
- GPU: GeForce GTX 1660 SUPER™ VENTUS XS OC (6G)

</details>



<details>

<summary>Conda environment</summary>
  
```bash
$ conda create -n uav_yolov5 python=3.7 -y
$ conda activate uav_yolov5
```

</details>




<details>

<summary>Clone Repository</summary>
  
```bash
$ git clone https://github.com/TW-yuhsi/Object-Detection-in-Aerial-Images
$ cd Object-Detection-in-Aerial-Images/
$ pip install -r requirements.txt
```

</details>





<details>

<summary>Folder Structure on Local Machine</summary>

```bash
├── data/
    └── baseline data/
        └── test/
            └── 0/ 1/ 2/ ...
        └── train/
            └── 0/ 1/ 2/ ...
        └── val/
            └── 0/ 1/ 2/ ...
    └── fold1/
        └── test/
            └── 0/ 1/ 2/ ...
        └── train/
            └── 0/ 1/ 2/ ...
        └── val/
            └── 0/ 1/ 2/ ...
    └── fold2/
        └── test/
            └── 0/ 1/ 2/ ...
        └── train/
            └── 0/ 1/ 2/ ...
        └── val/
            └── 0/ 1/ 2/ ...
    └── fold3/
        └── test/
            └── 0/ 1/ 2/ ...
        └── train/
            └── 0/ 1/ 2/ ...
        └── val/
            └── 0/ 1/ 2/ ...
    └── fold4/
        └── test/
            └── 0/ 1/ 2/ ...
        └── train/
            └── 0/ 1/ 2/ ...
        └── val/
            └── 0/ 1/ 2/ ...
├── ViT-Orchids-Classification-main/
    └── apex/
    └── checkpoint/
    └── compare.py
    └── convert.py
    └── models/
    └── utils/
    └── requirements.txt
    └── test.py/
    └── train.py/
    └── submit.py/
```
</details>




## 2. Train and Inference

<details>
 
  <summary>Train</summary>

```bash
$ python train.py --data custom.yaml --cfg yolov5m.yaml --weights yolov5m.pt --batch-size 1 --imgsz 2912
```

</details>

  
  


  
<details>

<summary>Inference</summary>

```bash
$ python detect_csv.py --weights runs/train/exp/weights/best.pt --source ../yolov7/datasets/test --conf-thres 0.3 --iou-thres 0.3 --save-txt --imgsz 2912
```

</details>
  
  
  
  
## 3. Reproduce the Best Result (public: 0.727275, private: 0.749105)
  
  
<details>
  
<summary>Local Machine Version</summary>
  
- Step 0. Follow **1. Environment Setup** step by step.
  
- Step 1. Setup the Folder Structure as follows.
  
  ```
  ├── test/
      └── 0/    # orchid_public_set, 40285
      └── 1/    # orchid_private_set, 41425
  ├── ViT-Orchids-Classification-main/
      └── apex/
      └── checkpoint/
      └── compare.py
      └── convert.py
      └── models/
      └── output/
          └── A1.bin, A2.bin, ID_4.bin, ID_5.bin, ID12.bin, ID27.bin    # ViT-B_16
      └── utils/
      └── requirements.txt
      └── test.py/
      └── train.py/
      └── submit.py/
  ```

- Step 2. Execute [submit.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/submit.py) by using the following command.

  After the setup, ready to execute [submit.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/submit.py), no additional steps are needed.

  ```bash
  python submit.py --model_type ["ViT-B_16","ViT-B_16","ViT-B_16","ViT-B_16","ViT-B_16","ViT-B_16"] --checkpoint ["output/A1.bin","output/A2.bin","output/ID_4.bin","output/ID_5.bin","output/ID12.bin","output/ID27.bin"] --img_size [480,480,480,480,480,480] --use_imagenet_mean_std [0,0,0,0,1,1]
  ```
  
  
  
- Step 3. Execute [convert.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/convert.py) by using the following command.
  
  After executing [submit.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/submit.py), we can get two files named `submit_voteEnsemble.csv` and `submit_meanEnsemble.csv`, respectively.
  
  Now, we are ready to execute [convert.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/convert.py).
  
  ```bash
  python convert.py
  ```
  
  
  
- Step 4. Submit the file named `submit_meanEnsemble_convert.csv`.
  
  After executing [convert.py](https://github.com/TW-yuhsi/ViT-Orchids-Classification/blob/main/convert.py), we can get the file named `submit_meanEnsemble_convert.csv` which has the highest Macro-F$_1$ score.
  
</details>
  

  
  

## 5. Related URLs
### [Competition Link](https://tbrain.trendmicro.com.tw/Competitions/Details/20)
### [Google Drive](https://drive.google.com/drive/folders/1x_rb6bu0riJuouAtK-xjFGDkCP7ZbhbL?usp=sharing)
<details>

<summary>Folder Structure on Google Drive</summary>


```
尋找花中君子 - 蘭花種類辨識及分類競賽 [TBrain]/
├── checkpoints/
    └── ResNet/
        └── ResNeSt269/
        └── ResNet50/
        └── ResNet101/
    └── Swin/
    └── ViT/
        └── R50+ViT-B_16/    # 5 weights
        └── ViT_Linformer/
            └── params1/
            └── params2/
        └── ViT-B_16/    # 59 weights
        └── ViT-B_32/    # 3 weights
        └── ViT-L_16/    # 1 weights
        └── ViT-L_32/    # 3 weights
├── Colab Notebooks/
    └── Images/
    └── Ranger-Deep-Learning-Optimizer/
    └── Attention Map.ipynb
    └── ResNet50_3.ipynb
    └── ResNet101_2_Ranger.ipynb
    └── ResNet101_3.ipynb
    └── ResNet101_Ranger_2.ipynb
    └── SwinT_2.ipynb
    └── SwinT.ipynb
    └── ViT_distilled_params1.ipynb
    └── ViT_Linformer_params1.ipynb
    └── ViT_Linformer_params2.ipynb
├── datasets/
    └── test/
        └── 0/    # orchid_public_set, 40285
        └── 1/    # orchid_private_set, 41425
    └── train/
        └── 4-Fold/
            └── fold1/
            └── fold2/
            └── fold3/
            └── fold4/
        └── baseline data/
        └── training/
├── Reproduce the Best Result/
    └── ViT/
        └── output/
        └── Reproduce.ipynb
├── src/
    └── getInfo/
        └── readLabel.py    # read label.csv file
        └── readImage.py    # get the shape of image
    └── preprocessing/
        └── split.py    # split the training data
    └── statistics/
        └── trainLoss.py    # plot training loss curve
├── Submitted Files/
    └── submit_1.csv    # public: 0.890142
    └── submit_2.csv    # public: 0.901620
    └── submit_3.csv    # public: 0.904925
    └── submit_4.csv    # public: 0.911492, private: 0.809624582
    └── submit_5.csv    # public: 0.909891
├── tables/
    └── Baseline.csv/    # experimental results for baseline models
    └── ViT.csv/    # experimental results for whole ViT trials
    └── ViT_Linformer.csv/    # experimental results for ViT_Linformer
```
</details>






## 6. GitHub Acknowledgement
<details>

<summary>Teammate</summary>  
  
- [Jia-Wei Liao](https://github.com/Jia-Wei-Liao/Orchid_Classification)
  
</details>
  

  

<details>

<summary>Useful Techniques</summary>  

- Augmentation
  - [AutoAugment](https://github.com/DeepVoltaire/AutoAugment), [TTAch](https://github.com/qubvel/ttach)
- Optimizer
  - [Ranger](https://github.com/lessw2020/Ranger-Deep-Learning-Optimizer), [Ranger21](https://github.com/lessw2020/Ranger21), [SAM](https://github.com/davda54/sam)
- Loss function
  - [MCCE](https://github.com/Kurumi233/Mutual-Channel-Loss), [FLSD](https://github.com/torrvision/focal_calibration)
- A PyTorch Extension
  - [Apex](https://github.com/NVIDIA/apex)

</details>


## 7. Reference
- [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://arxiv.org/abs/2010.11929)


## Citation
```
@article{
    title  = {Object Detection in Aerial Images},
    author = {Yu-Hsi Chen},
    url    = {https://github.com/TW-yuhsi/Object-Detection-in-Aerial-Images},
    year   = {2022}
}
```
