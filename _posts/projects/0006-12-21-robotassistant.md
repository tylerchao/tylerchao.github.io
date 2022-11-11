---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Computer Vision, ROS, Python, MoveIt, OpenCV"

project:
  title: "Robotic Desk Assistant"
  type: "Jekyll"
  url: https://github.com/javtges/Robotic-Desk-Assistant
  logo: "/assets/images/projects/desk/title.png"
  tech: "Computer Vision, ROS, Python, MoveIt, OpenCV"

youtubeId: q6vao0UIHJs
youtubeId2: mk7GI1-TJjs

---

Using ROS and computer vision, I created a robotic desk assistant - a tool that recognizes objects on a desk, performs hand detection, and determines which object the user points towards. A 4-DoF robotic arm then picks up the selected object and delivers it to the user. <br><br>

{% include youtubePlayer.html id=page.youtubeId %}<br><br>

### Computer Vision

For the computer vision in this project, I use an Intel RealSense camera. This stereo imaging camera with an IR dot pattern is especially useful in this purpose as it provides 3D coordinates relative to the sensor for each pixel in the image. This simplifies the process of controlling the robotic arm, from using a coordinate transformation I'm able to get the object's coordinates in the robot frame - no visual servoing required. <br><br>

The objects are detected using OpenCV, the largest contours in the image are found as objects and their centroids are recognized as the location the robotic arm should grasp. Future work involves using a more robust object detection method such as YOLOv5, though with a top-down video feed the current method works well as the desk provides a stable background. <br><br>

For hand detection, I use Google's <a href="https://google.github.io/mediapipe/solutions/hands.html" target="_blank"><u>MediaPipe Hands</u></a>, which is a fast and robust hand keypoint tracker. It detects 20 keypoints on a person's hand, of which I use the base and tip of the index finger. Using these two points, and the 3D coordinates provided by the RealSense camera, the program finds the vector of the user's pointer finger in three dimensions. This allows them to point across a desk at a specific object, even if other objects are in between. The following video shows the functionality of pointing at an object's center to select it. <br><br>

{% include youtubePlayer.html id=page.youtubeId2 %}<br><br>

### Motion Planning

All of the computer vision is housed within a ROS node, where another node in the custom package performs the control of the robotic arm. Used in this project is the 4-DoF Interbotix PincherX 100 Robot Arm, which is small enough to safely fit on a desk next to a user. <br><br>

When an object is selected, a ROS service commands the arm to follow a series of waypoints. The low-level actions are commanded by MoveIt, though for the case of this 4-DoF arm, there are kinematic constraints which make using OMPL (Open Motion Planning Library)'s more advanced planners (mostly RRT-based planners) problematic. As a result, the motions are preplanned to first turn towards the object to be in-plane with its kinematic chain, then move downwards to grab the object from above. The arm then brings the object back to where it is for the user to take it.<br><br>

Motion of the robot was visualized in RViz, and the manipulation tasks were also simulated in Gazebo during the development of this project. For more details and source code, see the project's <a href="https://github.com/javtges/Robotic-Desk-Assistant" target="_blank"><u>GitHub repository</u></a>. <br><br>