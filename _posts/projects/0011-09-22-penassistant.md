---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "ROS"

project:
  title: "Pen Assistant"
  type: "Jekyll"
  url: "https://github.com/katie-hughes/PenChallenge"
  logo: "/assets/images/projects/redpineapple/logo.png"
  tech: "ROS, Computer Vision"

---





<p>As a part of my orientation before beginning classes at Northwestern, I particpated in a series of coding challenges.The goal of this specific project was to enable a PincherX 100 robot to grab a pen.To do this, I used sensor data from an Intel Realsense D435i and processed it in OpenCV. Since the pen I was using was purple, I performed color masking on the RGB data to create a contour of the pen. Once I located the center of the pen, I examined the depth map data from the Realsense to determine the pen's physical location in the camera frame.</p>
<br>


<!-- ![Description](/assets/images/projects/pen/pentrack1.gif)
<center><h2>Gif1</h2></center> -->


![Description](/assets/images/projects/pen/pentrack2.gif)
<center><h2>My pen tracking algorithm relies on color masking in OpenCV</h2></center>

<!-- 
![Description](/assets/images/projects/pen/pentrack3.gif)
<center><h2>Gif3</h2></center> -->

<p>Once the location of the pen had been confirmed, the next step is to move the robot to that location and grab it. The first step in this procedure is to apply a transformation between the camera frame and the robot frame. which I achieved via a calibration run for a set camera and robot position. I then used the InterbotixManipulatorXS python package to command the arm to the desired end effector position of the pen location. The gripper will grasp the pen, return to the home position, and drop it.</p>
<br>

![Description](/assets/images/projects/pen/grab.gif)
<center><h2>Grabbing the pen!</h2></center>


<!-- <br><br> -->

