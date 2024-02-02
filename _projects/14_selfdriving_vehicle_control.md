---
layout: page
title: Self-Driving Vehicle Control
description: Crafted a sophisticated vehicle controller for autonomous navigation through predefined waypoints in the CARLA simulation environment. This controller combines Proportional-Integral-Derivative (PID) methodology for precise longitudinal control with the Stanley controller for lateral management, ensuring smooth and accurate maneuvering of the autonomous vehicle.
img: assets/gifs/carla_vehicle_control.gif
importance: -14
category: Autonomous Vehicles
---

The main goal of this project is to control a vehicle to follow a track by navigating through preset waypoints and reach the end point under a certain time. The vehicle needs to reach these waypoints at certain desired speeds, so both longitudinal and lateral control are required. This project has been taken as the course project of [Introduction to Self-Driving Cars](https://www.coursera.org/programs/minnesota-on-coursera-covid-hjfsl?authProvider=minnesota&currentTab=MY_COURSES&productId=p2jYHVPxEein9xItvIlMSA&productType=course&showMiniModal=true) on Coursera as part of the [University of Minnesota (Consortium)](https://www.coursera.org/minnesota) and offered by the [University of Toronto](https://www.utoronto.ca/). This course and project were completed under the supervision of [Prof. Steven Waslander](https://www.trailab.utias.utoronto.ca/stevenwaslander) and [Prof. Jonathan Kelly](http://stars.utias.utoronto.ca/~jkelly/). This project was simulated on [CARLA simulator](https://carla.org/).

**Tools Used:** Python3.6+, CARLA

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/vid/vehicle_control_carla.mp4" title="CARLA Simulation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Carla Simulation
</div>

