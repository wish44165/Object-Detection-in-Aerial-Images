# [無人機飛行載具之智慧計數競賽](https://tbrain.trendmicro.com.tw/Competitions/Details/25) (TEAM_2054)

## Overview
Nowadays, with the rapid development of deep neural networks and the computing power of graphic cards, the performance of object detection has been greatly improved. Even though this field looks very mature, there are still some intractable problems, such as a lack of labeled data and a lack of understanding of species. Here, I use YOLOv5 as my object detection model. Using this method, my final scores are $0.727275$ and $0.749105$ in public and private leaderboards, respectively. In addition, my overall ranking is $11$ th out of $236$ teams.


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


  
  
  
  
## 2. Reproduce the Best Result (public: 0.727275, private: 0.749105)



<details>
 
<summary>Folder Structure</summary>

- [best.pt](https://drive.google.com/file/d/1Kn6FOV-Ho06Lz8ROc2nowd88Xkc6Gxnp/view?usp=sharing)

```bash
Object-Detection-in-Aerial-Images/
    ├── best.pt
    ├── datasets/
        └── private/    # img1501.png, img1502.png, img1503.png, ...
```

</details>



  
<details>

<summary>Inference</summary>

```bash
$ python detect_csv.py --weights best.pt --source datasets/private --conf-thres 0.3 --iou-thres 0.3 --save-txt --imgsz 2912
```

</details>




## 3. GitHub Acknowledgement
- [YOLOv5](https://github.com/ultralytics/yolov5)
- [Data Augmentation For Object Detection](https://github.com/Paperspace/DataAugmentationForObjectDetection)




## Information
```
@article{
    title  = {Object Detection in Aerial Images},
    author = {Yu-Hsi Chen},
    url    = {https://github.com/TW-yuhsi/Object-Detection-in-Aerial-Images},
    year   = {2022}
}
```
