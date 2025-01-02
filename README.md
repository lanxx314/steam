<h1 align="center">Steam: Sparse Transformer and Explicit Attention Module 
    for Multimodal Object Detection</h1>
<div align='center'>
    <strong>Xiaoxiong Lan</strong><sup> 1</sup>&emsp;
    <strong>Shenghao Liu</strong><sup> 1</sup>&emsp;
    <strong>Sude Zhang</strong><sup> 1</sup>&emsp;
    <strong>Zhiyong Zhang</strong><sup> 1</sup>&emsp;
</div>


<div align='center'>
    <sup>1 </sup>Sun Yat-Sen University
</div>


## **Intro**

Official Code for [Steam: Sparse Transformer and Explicit Attention Module for Multimodal Object Detection](https://github.com/lanxx314/steam)

The code will be released after our paper is accepted !



## **Overview**
A novel multimodal object detection framework with sparse transformer and explicit attention module.
The illustration of our proposed multimodal object detection framework is shown in the following figure.

<p align="center">
  <img src="imgs\img.png" alt="overview" width="98%">
</p>



## **Getting Started**

Training and testing environments：

* Ubuntu 20.04.5 LTS
* NVIDIA GeForce RTX 3090


**Step 1: Clone the steam repository:**

To get started, first clone the our repository and navigate to the project directory:

```bash
git clone https://github.com/lanxx314/steam
cd steam
```

**Step 2: Create a conda virtual environment and activate it**

Steam recommends setting up a conda environment. Use the following commands to set up your environment:

```bash
conda create -n steam python=3.9 -y
conda activate steam
pip install -r requirements.txt
conda install pytorch==1.10.1 cudatoolkit==11.3.1 torchvision==0.11.2 -c pytorch
cd utils/nms_rotated
python setup.py develop  # or "pip install -v -e ."
```

**Step 3: Install DOTA_devkit**  

It's just a tool to split the high resolution image and evaluation the obb, you can clone the latest version of the YOLO_OBB repository:

```bash
cd yolo_obb/DOTA_devkit
sudo apt-get install swig
swig -c++ -python polyiou.i
python setup.py build_ext --inplace
```

**Step 4: Prepare the dataset**

You can organize your dataset as the following directory:

```
root
├── DataSet
│   ├── rgb
│   │   ├── train
│   │   │   ├── images
│   │   │   ├── labels
│   │   ├── val
│   │   │   ├── images
│   │   │   ├── labels
│   │   ├── test
│   │   │   ├── images
│   │   │   ├── labels
│   ├── ir
│   │   ├── train
│   │   │   ├── images
│   │   │   ├── labels
│   │   ├── val
│   │   │   ├── images
│   │   │   ├── labels
│   │   ├── test
│   │   │   ├── images
│   │   │   ├── labels
```

**Step 5: Train**

You can train on public data or customer data by the following command:

```bash
python train.py --batch--size 16
```

**Step 6: Test**

Evaluate the performance on the test set:

```bash
python test.py --save-json --name 'test'
```

Evaluate the performance on the validation set:

```bash
python val.py --save-json --name 'val'
```

## **Acknowledgment**

Our code mainly improves on [ultralytics](https://github.com/ultralytics) and [yolo_obb](https://github.com/CVHub520/yolov5_obb.git) . Many thanks to the authors!
