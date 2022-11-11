---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Deep Learning, Computer Vision, Pytorch"

project:
  title: "Deep Learning for Gesture Recognition"
  type: "Jekyll"
  url: "https://github.com/javtges/dronegesturecontrol"
  logo: "/assets/images/projects/gesture/fist_gesture.png"
  tech: "Deep Learning, Computer Vision, Python, Pytorch, Tensorflow"


images:
  - image:
    url: "/assets/images/projects/gesture/fist_gesture.png"
    alt: "Depth and color fist gesture"
  - image:
    url: "/assets/images/projects/gesture/dataset_image.png"
    alt: "Infrared image from a dataset"
  - image:
    url: "/assets/images/projects/gesture/drone.png"
    image:

youtubeId: BBnZKu9_Neg
---



{% include youtubePlayer.html id=page.youtubeId %}

<p>Gestures are a common and especially alluring method of human-computer interaction. In this project, I experiment with multiple manners of detecting hand gestures within a video stream. </p>
<br>

<!-- <p>Time-series data struggles with a fundamental challenge in live inference tasks - that is, the problem of segmentation. In a live video stream, there's no definite beginning or end of the gesture, and the time the gesture takes to be performed can be variable.</p>
<br>
<p>
Various solutions to this temporal classification problem exist in the deep learning space, most prominently recurrent neural networks (RNNs) which take multiple inputs - a more traditional input for a CNN layer, and a previous state of the RNN. This is used in models such as LTSMs, wherein memory of previous states is kept, and specific loss functions have been developed for use with these networks, such as CTC: Connectionist Temporal Classification loss, all of which were experimented with in this project.</p>
<br> -->

### 3D Convolutional Neural Network Experiments

<p>
Two different 3DCNNs, used for classifying video rather than a 2DCNN which is used on images, were implemented on Pytorch and trained on the nvGesture dataset. The two networks that were implemented were <a href="https://arxiv.org/abs/1412.0767" target="_blank"><u>C3D</u> </a> and <a href="https://arxiv.org/pdf/1711.11248.pdf" target="_blank"><u>Resnet 2+1d</u></a>. Both networks extract spatiotemporal features, useful for classifying gestures.</p>
<br>

<p>
Here, these networks (principally C3D) were used to emulate the results in a <a href="https://research.nvidia.com/sites/default/files/pubs/2016-06_Online-Detection-and/NVIDIA_R3DCNN_cvpr2016.pdf" target="_blank"><u>2016 paper by NVIDIA</u></a> to classify gestures in the nvGesture dataset, a dataset with 25 loosely segmented classes of gestures over 1050 videos. The spatiotemporal features from the neural networks were then inputted into a LSTM layer before classification. As shown below, implementing the networks from literature yielded training results were not as expected, this was still a great introduction to Pytorch by attempting to solve a difficult problem. </p> <br>

![Tensorboard results for experiments on the nvGesture dataset](/assets/images/projects/gesture/tensorboard.png)
<center><h2>Tensorboard results for experiments on the nvGesture dataset</h2></center>


### 1D Parallelized Convolutional Neural Network <br>

<p> Additionally, a parallelized 1DCNN was implemented to classify dynamic hand gestures in the <a href="http://www-rech.telecom-lille.fr/shrec2017-hand/" target="_blank"><u>DHG-14 dataset</u></a>, using the XYZ coordinates of skeletal points on a hand as detected through softwares such as Mediapipe. This included a real-time inference wrapper around <a href="https://github.com/guillaumephd/deep_learning_hand_gesture_recognition" target="_blank"><u>this network</u></a>. While training and validation accuracies were strong, this suffers from the same segmentation problem as before. </p>
<br>

### 2D Convolutional Neural Network 

<p>
Finally, a dataset of static images of hands in an infrared camera was used to classify static gestures from a <a href="https://www.kaggle.com/gti-upm/leapgestrecog" target="_blank"><u>leap motion camera</u></a>. Given the nature of the images, this can be approximated by depth data too, with background removal. A 2D CNN was implemented in Pytorch, with parsing of the dataset files courtesy of <a href="https://www.kaggle.com/kageyama/keras-hand-gesture-recognition-cnn/notebook" target="_blank"><u>kaggle</u></a>. The implemented classifier works on single frames in a video stream, and is accurate enough to achieve high performance in real time with a framerate of 30 FPS.
</p> <br>

![An infrared image from the dataset](/assets/images/projects/gesture/fist_gesture.png)
<center><h2>An infrared image from the dataset</h2></center>


### Controlling the Drone

<p>
This project uses a Dji Tello Edu drone, as it provides an easy-to-interface software development kit. Commands that can be sent to the drone are listed in the <a href="https://djitellopy.readthedocs.io/en/latest/tello/" target="_blank"> <u>SDK documentation</u></a>. Each gesture will correspond to a movement in this SDK. </p> <br>

<p>
The final demonstration as of March 17th uses the Depth/Infrared Classifier, to differentiate between 10 static hand gestures in a depth or infrared video stream. While training and validation accuracy exceeds 99% on the training dataset, the real-time recognition capability is significantly diminished - being able to reliably differentiate between four or five of the classes.
</p> <br>
<p>
This has to do with the input datatype, where the hands in the dataset are clearly segmented opposed to more loosely segmented hands in the live video. (Show picture of dataset image) This is improved by removing pixels with depth values greater than a threshold of 0.5m, though can still stand to be improved.
</p> <br>
<p>
Controlling the drone is accomplished by sending commands to the drone corresponding to the gesture detected, provided the decision probability is greater than a threshold of 0.7. Once a gesture is found, the next N frames are ignored.
</p> <br>

<p> More information and the source code for this project can be found on its <a href="https://github.com/javtges/dronegesturecontrol" target="_blank"> <u>GitHub Repository</u> </a>.</p> <br>
