# Maple Leaf Detector 
Custom object detection using implemenetation of Yolov3 ([paper](https://pjreddie.com/media/files/papers/YOLOv3.pdf)) trained on 800 images of *Acer rubrum* for 3500 batches, starting with the pre-trained `yolov3.weights`. Training set images downloaded from [iNaturalist](https://www.inaturalist.org/taxa/48098-Acer-rubrum) and labeled with [LabelImg](https://github.com/tzutalin/labelImg). 

![Image with bounding boxes](predictedleaf.jpg)

## Installation 
```
$ git clone https://github.com/etowahs/darknet.git
$ cd darknet
$ make                   <-- for Linux only
```
If you have CUDA installed on your computer, you may want to have `GPU=1` in Makefile to have faster detection. See addtional instructions for [Linux](https://github.com/AlexeyAB/darknet#how-to-compile-on-linux-using-make) and [Windows](https://github.com/AlexeyAB/darknet#how-to-compile-on-windows-using-cmake-gui). 

Download trained weights from [here](https://drive.google.com/file/d/16cxN0TKj6n5eOaUaXQd-R6DWVL-rE9Mi/view?usp=sharing) (235MB) and place it in the darknet folder. 

## Detecting Leaves 
To run the detector on a single image:

```
$ cd darknet 
$ ./darknet detector test custom/darknet.data custom/yolov3.cfg leaf.weights -ext_output my-image.jpg
```
To run the detector on an entire folder of images, create a .txt file containing the file locations of all the images. Ex. my-imgs.txt
```
$ ./darknet detector test custom/darknet.data custom/yolov3.cfg leaf.weights -ext_output < my-imgs.txt > output.txt
```