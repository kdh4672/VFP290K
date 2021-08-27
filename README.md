# VFP290K: A Large-Scale Benchmark Dataset for Vision-based Fallen Person Detection

This repository is the official documentation & implementation of [VFP290K: A Large-Scale Benchmark Datasetfor Vision-based Fallen Person Detection](https://openreview.net/forum?id=y2AbfIXgBK3). 

![VFP290K](./images/teaser.jpg)

## Requirements

Our pretrained models except YOLO are based on [MMdetection2](https://github.com/open-mmlab/mmdetection) detection framework.
#### 1. Install mmcv-full
```setup
pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/{cu_version}/{torch_version}/index.html
```
Please replace `{cu_version}` and `{torch_version}` in the url to your desired one.

#### 2. clone VFP290K repository
```setup
git clone https://git hub.com/DASH-Lab/VFP290K.git
cd VFP290K-main
pip install -r requirements/build.txt
pip install -v -e .
```
- 모델 구동 환경 설명

## Training & Evaluation

### 1. Benchmark
To train the model(s) in the paper, run this command:

```train
python train.py --input-data <path_to_data> --alpha 10 --beta 20
```
```eval
python eval.py --input-data <path_to_data> --alpha 10 --beta 20
```

### 2. Experimental setting (Ablation study for various features)
To train the model(s) based on experimenta setting to demonstrate the perfomance shift in the paper Table.4, run this command:

- Light conditions
```train
python train.py --input-data <path_to_data> --alpha 10 --beta 20
```

```eval
python eval.py --model-file mymodel.pth --benchmark imagenet
```

- Camera heights
```train
python train.py --input-data <path_to_data> --alpha 10 --beta 20
```
```eval
python eval.py --model-file mymodel.pth --benchmark imagenet
```

- Background
```train
python train.py --input-data <path_to_data> --alpha 10 --beta 20
```
```eval
python eval.py --model-file mymodel.pth --benchmark imagenet
```

## Pre-trained Models
You can download pretrained models here:
- [My awesome model](https://drive.google.com/mymodel.pth) trained on ImageNet using parameters x,y,z. 

- Pre-trained 모델 넣을지 말지 고민중


## Results
Our model achieves the following performance on  Background:
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-c3ow">Backbone</th>
    <th class="tg-c3ow">Training<br></th>
    <th class="tg-c3ow">Street</th>
    <th class="tg-c3ow">Park</th>
    <th class="tg-c3ow">Building</th>
    <th class="tg-c3ow">Street</th>
    <th class="tg-c3ow">Park</th>
    <th class="tg-c3ow">Building</th>
    <th class="tg-c3ow">Street</th>
    <th class="tg-c3ow">Park</th>
    <th class="tg-c3ow">Building</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow">Test</td>
    <td class="tg-c3ow" colspan="3">Street </td>
    <td class="tg-c3ow" colspan="3">Park</td>
    <td class="tg-c3ow" colspan="3">Building </td>
  </tr>
  <tr>
    <td class="tg-c3ow">Faster R-CNN</td>
    <td class="tg-c3ow">mAP<br>AP_50<br>AP_75</td>
    <td class="tg-c3ow">0.742<br>0.910<br>0.829</td>
    <td class="tg-c3ow">0.732<br>0.860<br>0.809</td>
    <td class="tg-c3ow">0.616<br>0.828<br>0.723</td>
    <td class="tg-c3ow">0.620<br>0.786<br>0.690</td>
    <td class="tg-c3ow">0.706<br>0.857<br>0.768</td>
    <td class="tg-c3ow">0.517<br>0.705<br>0.588</td>
    <td class="tg-c3ow">0.748<br>0.876<br>0.813</td>
    <td class="tg-c3ow">0.847<br>0.957<br>0.920</td>
    <td class="tg-c3ow">0.702<br>0.821<br>0.791</td>
  </tr>
  <tr>
    <td class="tg-c3ow">RetinaNet</td>
    <td class="tg-c3ow">mAP<br>AP_50<br>AP_75</td>
    <td class="tg-c3ow">0.770<br>0.922<br>0.843</td>
    <td class="tg-c3ow">0.743<br>0.861<br>0.804</td>
    <td class="tg-c3ow">0.654<br>0.811<br>0.730</td>
    <td class="tg-c3ow">0.664<br>0.830<br>0.720</td>
    <td class="tg-c3ow">0.737<br>0.888<br>0.791</td>
    <td class="tg-c3ow">0.587<br>0.752<br>0.647</td>
    <td class="tg-c3ow">0.828<br>0.932<br>0.901</td>
    <td class="tg-c3ow">0.851<br>0.960<br>0.918</td>
    <td class="tg-c3ow">0.804<br>0.915<br>0.875</td>
  </tr>
  <tr>
    <td class="tg-c3ow">YOLOv3</td>
    <td class="tg-c3ow">mAP<br>AP_50<br>AP_75</td>
    <td class="tg-c3ow">0.610<br>0.817<br>0.689</td>
    <td class="tg-c3ow">0.510<br>0.664<br>0.600</td>
    <td class="tg-c3ow">0.284<br>0.400<br>0.336</td>
    <td class="tg-c3ow">0.416<br>0.578<br>0.468</td>
    <td class="tg-c3ow">0.537<br>0.759<br>0.632</td>
    <td class="tg-c3ow">0.282<br>0.421<br>0.315</td>
    <td class="tg-c3ow">0.610<br>0.817<br>0.689</td>
    <td class="tg-c3ow">0.664<br>0.824<br>0.784</td>
    <td class="tg-c3ow">0.671<br>0.831<br>0.790</td>
  </tr>
  <tr>
    <td class="tg-c3ow">YOLOv5</td>
    <td class="tg-c3ow">mAP<br>AP_50<br>AP_75</td>
    <td class="tg-c3ow">0.669<br>0.783<br>0.729</td>
    <td class="tg-c3ow">0.671<br>0.745<br>0.719</td>
    <td class="tg-c3ow">0.226<br>0.335<br>0.266</td>
    <td class="tg-c3ow">0.398<br>0.465<br>0.428</td>
    <td class="tg-c3ow">0.692<br>0.776<br>0.727</td>
    <td class="tg-c3ow">0.209<br>0.335<br>0.266</td>
    <td class="tg-c3ow">0.675<br>0.743<br>0.727</td>
    <td class="tg-c3ow">0.802<br>0.848<br>0.836</td>
    <td class="tg-c3ow">0.606<br>0.707<br>0.679</td>
  </tr>
</tbody>
</table>

## Contributing
This repository is copyrighted under GPLv3 license 
