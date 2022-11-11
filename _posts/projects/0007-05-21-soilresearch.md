---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Computer Vision, Earthquake Simulation"

project:
  title: "Soil Saturation Controller"
  type: "Jekyll"
  url: "https://github.com/javtges/CEES-Automated-Saturation-System"
  logo: "/assets/images/projects/soil_50.jpg"
  tech: "Python, OpenCV, Earthquake Simulation"

youtubeId: k6XsQc-nGOI
---


<p>This project occurred during my time as a Research Assistant in Rensselaer Polytechnic Institute's Center for Earthquake Engineering Simulation.</p>
<br>

<p>In preparing soil models for testing in a geotechincal centrifuge, graduate students require that their soil be saturated with a viscous fluid. However, saturating a large soil model can take multiple days and requires 24/7 supervision, as the viscous fluid, drawn in via a vacuum over the soil, frequently clogs the equipment. Additionally, the diffusion rate of the fluid through the soil is slow, requiring a flow rate of >2 mL/minute, or approximately one drop every 2-3 seconds.</p>
<br>

<p>Finding a balance between preparing the experiments properly (as flow rates too high will ruin the uniform saturation) and preventing nozzles from clogging without constant monitoring was a solution I hoped to achieve with this system. I used a proportional controller to control the position sent to a voltage-modulated valve, and used a camera feed to detect the presence of drops in the system. The vacuum chamber the models were under prohibited the usage of a traditional flow meter or a break-beam sensor, hence the usage of computer vision to look into the chamber and detect the presence of drops.</p>
<br>

<p>The system, run on a Raspberry Pi, uses OpenCV's background separation to determine non-stagnant pixels in the video feed. The program performs an initial calibration to allow flexibility in variant lighting conditions, then modulates the valve until it reaches the setpoint. It uses a moving average to determine the presence of a drop, with a deadband to provide resilience to ripples, should there be any. Video feed is also broadcasted on a local IP, so researchers can check on their experiment preparation, change parameters, and more remotely.</p>
<br>

![A picture of a vacuum chamber for testing. Voltage-controlled valve is out-of-frame.](/assets/images/projects/soil.jpg)
<center><h2>A picture of a vacuum chamber for testing. Voltage-controlled valve is out-of-frame.</h2></center>

{% include youtubePlayer.html id=page.youtubeId %}
<center><h2>Video feed after background subtraction is overlaid over the system. A cropped field of view is used for increased detection accuracy.</h2></center>



<br><br>

