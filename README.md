# 使用MATLAB提供的YOLOv4模型進行車輛偵測

檔案介紹
---
main.mlx : 主程式檔

validateInputData.m : 主程式會使用到的函式檔，主要用來檢查DataSet資料集

vehicleDatasetGroundTruth.mat : DataSet裡面影像的路徑與每張影像車輛的Bounding Box資訊

license.txt : Copyright (c) 2021, The MathWorks, Inc.

vehicleDatasetImages.zip : 訓練網路所使用的車輛影像

訓練
---
將doTraining變數改為true即可訓練，訓練完畢後會進行準確度計算。改為false為直接使用預先訓練好的權重檔進行後續的準確度計算
```
doTraining = true; %%%%%%%%%%%%這裡做更改!! true 或者 false
if doTraining       
    % Train the YOLO v4 detector.
    [detector,info] = trainYOLOv4ObjectDetector(augmentedTrainingData,detector,options);
    save('YOLOv4.mat','detector'); %訓練完畢後將模型儲存下來
else
    pretrained = load("trained_weights.mat");%%直接讀取已經訓練好的模型
    detector = pretrained.detector;
end
```

參考
---

[](https://www.mathworks.com/help/vision/ug/object-detection-using-yolov4-deep-learning.html)https://www.mathworks.com/help/vision/ug/object-detection-using-yolov4-deep-learning.html
[](https://www.mathworks.com/help/vision/ref/yolov4objectdetector.html)https://www.mathworks.com/help/vision/ref/yolov4objectdetector.html

Copyright 2021 The MathWorks, Inc.

