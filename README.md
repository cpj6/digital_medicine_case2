# [Digital Medicine] Case Presentation 2 



## Background
### **1. Intracranial Hemorrhage**
![](https://i.imgur.com/ymta6NX.jpg)


|名稱| Intraparenchymal | Intraventricular | Subarachnoid |Subdural|Epidural|
|--------| -------- | -------- | -------- | -------- | -------- |
|中文| 顱內出血     | 腦室內出血     | 蛛網膜下腔出血     |硬腦膜下血腫|硬腦膜外出血|
|所在位置| 大腦內   | 腦室(ventricle)內     | 在蛛網膜(arachnoid)和軟腦脊膜(pia mater)之間     |在硬腦膜(Dura)和蛛網膜(arachnoid)之間|在硬腦膜(Dura)和頭骨(skull)之間|
|形狀| 圓     | 符合腦室的形狀     | 腦溝和裂縫的路徑     |新月形|長形|

### **2. Brain CT illustration**<br>
![](https://i.imgur.com/vwzZ2s8.jpg)

---
## Preprocessing
### Windowing
* Create a 3 chanel RGB image where each chanel corresponds to different CT window: brain, subdural, and bone. These 3 windowed image were then stacked to create the final RGB image to feed the model
* A wider window width, will display a wider range of CT numbers. Consequently, the transition of dark to light structures will occur over a larger transition area to that of a narrow window width.<br>
Every part of tissue has different range of HU.Therefore ,we can specify which part to inspect choosing right range of window width and window level.<br>
Window Width(WW)是CT number橫跨的範圍，Window Level(WL)類似CT number的中心點，根據設定不同數值下的WW和WL，我們就可以看到不同的部位。
<br>

![](https://i.imgur.com/yv0nk56.jpg)

![](https://i.imgur.com/u2jM2eo.png)




### Augmentation
* The  transformations are used for data augmentation. We randomly flip, rotate, and crop-rezized the CT image to create modified versions of images, thus expand the size of dataset.(隨機長寬比裁剪 transforms.RandomResizedCrop)
* Remove redundant part of the CT image to enhance the feature of the picture.We randomly rotate, the picture and resize it.
```
data_transforms2 = transforms.Compose([
  transforms.RandomHorizontalFlip(p=0.5),
  transforms.RandomRotation(degrees=15),
  transforms.RandomResizedCrop(input_size, scale=(0.85, 1.0), ratio=(0.8, 1.2)),
  transforms.ToTensor(), # PIL => FloatTensor，[0, 255] => [0., 1.]
])      
```
---

## Model 
### I/O & Environments
* Input : dicom(.dcm) file
* Output Label: 

>     1.Intraparenchymal 
>     2.Intraventricular
>     3.Subarachnoid 
>     4.Subdural
>     5.Epidural
>     6.healthy
* Language: Python 
* Environments: Google Colab


### Hyperparameters


| Hyperparameter | value | 
| -------- | -------- | 
| Batch     | 16     | 
| Loss function     | Cross Entropy     | 
| Optimizer     | Adam     | 
| Learning rate     | 0.0005     | 
| Lr_decay     | 0.7     | 
| Epoch     | 20     | 


### Models and Results
**1.  EfficientNetb4**<br>
Confusion matrix:(Test data)
![](https://i.imgur.com/ZnOthlK.jpg)
**2. InceptionV3**
Result: Very Healthy<br> 
Confusion matrix:
![](https://i.imgur.com/inVHjvN.jpg)



---
## Reference 

[1] RSNA2019 reference code(1): https://github.com/SeuTao/RSNA2019_Intracranial-Hemorrhage-Detection<br>
[2] RSNA2019 reference code(2): https://www.kaggle.com/akensert/rsna-inceptionv3-keras-tf1-14-0<br>
[3] Pixel Scaling : https://blog.csdn.net/m0_37477175/article/details/103803321<br>
[4] CT introducion(1) : https://reurl.cc/j52y3q<br>
[5] CT introduction(2): https://www.oocities.org/dr_ericlin/ct_read/01_introduction.html<br>
[6]  CT introduction(3): https://www.tmuh.org.tw/UploadFile/files/Imaging/OSCE8.pdf<br>
[7]  CT introduction(4): https://reurl.cc/WLgNRx<br>
[8] DiCom Format: https://towardsdatascience.com/understanding-dicoms-835cd2e57d0b<br>
[9] Windowing CT
https://radiopaedia.org/articles/windowing-ct<br>
[10] CT image: https://www.sciencedirect.com/topics/medicine-and-dentistry/hounsfield-scale<br>

---
