## HolisticNet
This is the code repository for reproducing the results of the paper titled “HolisticNet: Remote Sensing Small Object Detection Algorithm Based on Neighborhood Regression and Dynamic Adjustment.”
![图 1 HolisticNet 网络结构](https://github.com/user-attachments/assets/6044a332-5d6d-4564-ba24-1eca40b79f63)
## Required environment
MMDetection is an open-source object detection toolbox developed based on PyTorch, designed to provide researchers and developers with an easy-to-use and efficient framework. All comparative algorithms in this study were reproduced using MMDetection. The experimental environment was configured with Ubuntu 20.04, CUDA v11.8, cuDNN v8.6.0, and PyTorch 2.2.1, running on two NVIDIA 4090 GPUs. The learning rate was set with a multiplier of 0.008, and stochastic gradient descent (SGD) was employed as the optimizer.
# Installation
We encourage you to create a virtual environment with Anaconda.
Once you have cloned the repository, cd to the root directory and 👇
1. Install dependencies.
Use pip to install the package in requirements. txt: pip install - r requirements. txt
2. Installation environment
conda install pytorch==2.2.1 torchvision==0.17.1 torchaudio==2.2.1 -c pytorch
## Dataset Download
DIOR is a large-scale public dataset designed for object detection in optical remote sensing images. It contains a total of 23,463 remote sensing images and 190,288 object instances, primarily consisting of small objects. The spatial resolution of the image’s ranges from 0.5 meters to 30 meters and covers 20 categories of common remote sensing targets. For our study, we selected ten representative categories of small remote sensing objects from the dataset, including Stadium (ST), Airport (AIR), Chimney (CH), Airplane (AIN), Dam (DA), Overpass (OV), Ship (SH), Harbor (HA), Bridge (BR), and Vehicle (VE). We refer to this subset as DIOR-H.
DIOR-H download link: https://huggingface.co/yeliudev/CATNet/resolve/main/datasets/dior-b162132d.zip
## Evaluation metrics
We evaluate the model’s performance using the COCO evaluation metrics across different IoU thresholds, including AP (IoU=0.5:0.95), AP50 (IoU=0.5), and AP75 (IoU=0.75), as well as the average precision for small, medium, and large objects, denoted as APS, APM, and APL, respectively. In addition, we assess the model’s efficiency using Params, FLOPs, and FPS. For the computation of AP and mAP across all categories, we adopt the PASCAL VOC evaluation protocol, where mAP is calculated as the mean of AP50 (IoU=0.5) across all object classes.
Although both VOC mAP and COCO AP50 evaluate object detection performance at an IoU threshold of 0.5, there are significant differences in their evaluation methodologies. VOC mAP employs an all-point interpolation method to calculate average precision at fixed recall levels, resulting in a relatively lenient assessment. In contrast, COCO AP50 uses a more refined interpolation and integration approach over the entire precision-recall curve, providing a stricter reflection of the model’s detection capability across varying confidence thresholds. Therefore, given the same prediction results, COCO AP50 is generally slightly lower than VOC mAP, yet both metrics effectively measure model performance at the IoU=0.5 criterion.
## Public statement
We fully acknowledge the importance of open-sourcing code in promoting research reproducibility and advancing scientific progress. However, as the paper is currently under review and the algorithm used in this project is part of an ongoing patent application, code release must undergo an internal approval process and therefore cannot be made public at this time. We plan to complete the necessary organization and review procedures as soon as the work is formally published, and will release the source code and key model parameters on the project’s code repository to facilitate reproducibility and further research.

