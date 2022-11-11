---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "ROS, Computer Vision, Robotic Manipulation"

project:
  title: "Robotic Pancake Chef"
  type: "Jekyll"
  url: "https://github.com/javtges/robot-pancake-chef"
  logo: "/assets/images/projects/pancake/pancake_flip.jpg"
  tech: "ROS, Python, OpenCV, MoveIt, Manipulation"


images:
  - image:
    url: "/assets/images/projects/pancake/IMG_6158.jpg"
    alt: "An overhead view of the robot"
  - image:
    url: "/assets/images/projects/pancake/pancake_flip2.jpg"
    alt: "Flipping a pancake with chocolate chips"
  - image:
    url: "/assets/images/projects/pancake/pancake_flip.jpg"
    alt: "A finished pancake deposited onto a plate"

youtubeId: 0hqedCQbExo
---



{% include youtubePlayer.html id=page.youtubeId %}

<p>In this project, a Franka Emika Panda robot arm was programmed to autonomously cook pancakes.</p>
<br>

<p>Given a spatula and a bottle of pancake batter, the robot is able to manipulate the tools, flip the pancake, and serve it onto a plate.</p>
<br>
<p>My primary role in this project was to design and implement the perception pipeline that senses where tools are located, the pancake location to assist with flipping & lifting the pancake, and autonomously determining when the pancake should be flipped.</p>
<br>

<p>The perception pipeline begins with an Intel Realsense D435i camera, which provides an RGB-D image. This depth data allows the pancake to be found using OpenCV contour recognition, in 3-Dimensions relative to the camera. The camera's coordinate frame (and the coordinate frames of the bottle and spatula) is linked to the robot's coordinate frame via an AprilTag a fixed distance from the robot base. The tools are located via AprilTags as well, provided the tag is visible the pipeline is able to determine the 6-DOF pose of the AprilTag without any depth data. This provides additional resilience towards varying backgrounds, lighting, and other camera issues. From the linked transformation tree, the perception pipeline is able to determine the locations of the tools and pancake in the robot's frame, eliminating the need for visual servoing and simplifying path planning</p>
<br>

![Flipping a pancake with chocolate chips](/assets/images/projects/pancake/IMG_6158.jpg)
<center><h2>An overhead view of the workspace, tools, and AprilTags for object identification.</h2></center>


<p>Once the pancake is put onto the griddle, the perception pipeline aims to determine an appropriate time to flip the pancake much like a human would. By counting the contours on the griddle's surface, the program is able to determine the number of  bubbles that appear on the pancake's surface. Empirical testing shows that for the pancakes created by the squeeze bottle, the number of bubbles rises, plateaus, and declines around the right time to flip - when the robot then moves to pick up the spatula.</p>
<br>

<p>This perception pipeline is integrated into ROS Noetic, which controls the arm using the MoveIt! control package. Motion planning is accomplished by specifying a target pose and using the RRT (Rapidly-exploring Random Tree) planner in OMPL (Open Motion Planning Library) to plan a set of joint states that bring the robot to the pose while abiding by planning scene constraints (the table, the camera, etc). The motion planning is aided by preprogrammed waypoints for the end effector pose and collision objects in RViz, to guarantee that the planner took an appropriate path</p>
<br>

<p>Final results yield a program that is able to successfully make pancakes with high rates of success. Future work may involve adding toppings, or flipping the pancake in the air with a frying pan rather than a spatula.</p>
<br>

![A finished pancake deposited onto a plate](/assets/images/projects/pancake/pancake_flip2.jpg)
<center><h2>Finishing a pancake with chocolate chips!</h2></center>


<br><br>

