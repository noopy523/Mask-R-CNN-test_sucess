# Balloon Example

This is an example showing the use of Mask RCNN in a real application.
We train the model to detect balloons only, and then we use the generated 
masks to keep balloons in color while changing the rest of the image to
grayscale. 

## Installation
From the [Releases page](https://github.com/matterport/Mask_RCNN/releases) page:
1. Download `mask_rcnn_balloon.h5`. Save it in the root directory of the repo (the `mask_rcnn` directory).
2. Download `balloon_dataset.p3`. Expand it such that it's in the path `mask_rcnn/datasets/balloon/`.
是下載source code.zip檔案下去修改(https://github.com/matterport/Mask_RCNN/releases)
而非matterport(https://github.com/matterport/Mask_RCNN)。

## Run Jupyter notebooks
Open the `inspect_balloon_data.ipynb` or `inspect_balloon_model.ipynb` Jupter notebooks. 
You can use these notebooks to explore the dataset and run through the detection pipelie step by step.
inspect_balloon_model.ipynb是檢測氣球
test_success.ipynb是檢測one punch man

現在預設的train+val資料夾是檢測one punch man，如果要改回檢測氣球須把balloon_dataset兩個資料夾拉出來，或在code裡面更換讀取位置。
主要更改地都在model.py裡面，有中文註釋改了哪些地方。

## config 
batch size=1
resnet50
顯卡不足，這兩者我都調小，皆可自行更改。

## Train the Balloon model

Train a new model starting from pre-trained COCO weights
```
python  balloon.py train --dataset=./  --weights=coco 
(./ = 指定當地資料夾，可自行更換位址)
```

Resume training a model that you had trained earlier
```
python3 balloon.py train --dataset=/path/to/balloon/dataset --weights=last
```

Train a new model starting from ImageNet weights
```
python3 balloon.py train --dataset=/path/to/balloon/dataset --weights=imagenet
```

The code in `balloon.py` is set to train for 3K steps (30 epochs of 100 steps each), and using a batch size of 2. 
Update the schedule to fit your needs.

## Result
![image](https://github.com/noopy523/Mask-R-CNN-test_sucess/blob/main/test4.jpg))
![image](https://github.com/noopy523/Mask-R-CNN-test_sucess/blob/main/test5.jpg))

