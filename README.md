# [Digital Medicine] Case Presentation 2 

:warning: **Modify this, modify README**


---

* 2019 Winner reference code: https://github.com/SeuTao/RSNA2019_Intracranial-Hemorrhage-Detection
* Reference code: https://www.kaggle.com/akensert/rsna-inceptionv3-keras-tf1-14-0
* Pixel Scaling : https://blog.csdn.net/m0_37477175/article/details/103803321
* CT introducion(1) : https://blog.csdn.net/u013635029/article/details/72957944?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param
* CT introduction(2): https://www.oocities.org/dr_ericlin/ct_read/01_introduction.html
*  CT introduction(3): https://www.tmuh.org.tw/UploadFile/files/Imaging/OSCE8.pdf
* DiCom Format: https://towardsdatascience.com/understanding-dicoms-835cd2e57d0b

---

## 1.Brain Layer

![](https://i.imgur.com/uKs2y4f.jpg =500x)


## 2.Intracranial Hemorrhage
![](https://i.imgur.com/TJPzN3v.jpg =1300x)

|名稱| Intraparenchymal | Intraventricular | Subarachnoid |Subdural|Epidural|
|--------| -------- | -------- | -------- | -------- | -------- |
|中文| 腦實質性出血     | 腦室內出血     | 蛛網膜下腔出血     |硬腦膜下血腫|硬腦膜外出血|
|所在位置| 大腦內   | 腦室(ventricle)內     | 在蛛網膜(arachnoid)和軟腦脊膜(pia mater)之間     |在硬腦膜(Dura)和蛛網膜(arachnoid)之間|在硬腦膜(Dura)和頭骨(skull)之間|
|形狀| 圓     | 符合腦室的形狀     | 腦溝和裂縫的路徑     |新月形|長形|

## 3.Brain CT illustration
![](https://i.imgur.com/VLJ5wuG.jpg =300x)   ![](https://i.imgur.com/2N4hWU3.jpg =220x)


---

## 4. TODO

- [ ] Windowing 
- [ ] Cropping 
- [ ] Thoughts
- [ ] InceptionV3 Model explanation
- [ ] EfficientNet Model explanation
- [ ] Res50 Model explanation
- [ ] AUC explanation