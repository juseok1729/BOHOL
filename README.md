# Custom-YOLO
#BOHOL #Philippines #Scuba diving #Sea ecology #App #Flask
<p align="center"><img src="/detection/1.gif" width="600"\></p>

## My Custom weights
Download : https://drive.google.com/file/d/1-L5U2JCJG73HMfHJNIBsK9123N1yaHqf/view

## Classes = 16

Class_id  |                 Name                |
--------- | :---------------------------------: |
0         |      Green_sea_turtle               |
1         |      Anthias                        |
2         |      Blonde_naso_tang               |
3         |      Blue_damsel                    |
4         |      Brown_tang                     |
5         |      Domino_damsel                  |
6         |      Foxface_rabbitfish             |
7         |      Jackfish                       |
8         |      Lionfish                       |
9         |      Regal_angelfish                |
10        |      Scissortail_sergeant_major_fish        |
11        |      Sergeant_major_fish            |
12        |      Snowflake_moray                |
13        |      Three_stripes_damsel           |
14        |      Tomato_clown                   |
15        |      Yellow_boxfish                 |

## mAP (mean average precision)
<p align="left"><img src="/mAP/7.PNG" width="520"\></p>

## **Test images**
```bash
python detect.py --weights ./checkpoints/bohol-416 --size 416 --model yolov4 --images ./data/images/img1.jpg
```
<p align="center">
  <img src="/detection/detection1.png" width="440"/>
  <img src="/detection/detection2.png" width="440"/>
</p>

<p align="center">
  <img src="/detection/detection3.png" width="440"/>
  <img src="/detection/detection4.png" width="440"/>
</p>

<p align="center">
  <img src="/detection/detection5.png" width="440"/>
  <img src="/detection/detection6.png" width="440"/>
</p>

<p align="center">
  <img src="/detection/detection7.png" width="440"/>
  <img src="/detection/detection8.png" width="440"/>
</p>

## **Test videos**
<p align="center">
  <img src="/detection/2.gif" width="440"/>
  <img src="/detection/3.gif" width="440"/>
</p>

<p align="center">
  <img src="/detection/4.gif" width="440"/>
  <img src="/detection/6.gif" width="440"/>
</p>

<p align="center">
  <img src="/detection/5.gif" width="440"/>
  <img src="/detection/7.gif" width="440"/>
</p>

<p align="center">
  <img src="/detection/8.gif" width="440"/>
  <img src="/detection/9.gif" width="440"/>
</p>
