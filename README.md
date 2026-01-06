# Visual SLAM Project — RGB-D Graph-based SLAM(ROS1 / RTAB-Map)

> Task: Deployed RTAB-Map RGB-D SLAM on TurtleBot3 running on Jetson Xavier NX and validated mapping/localization in RViz(visualization tool).

## Overview
This project demonstrates an **RGB-D, graph-based SLAM** pipeline on a mobile robot.
- **SLAM:** RTAB-Map (loop-closure + graph optimization)
- **Visualization:** RViz
- **Deployment:** Jetson Xavier NX (SSH remote), ROS1 environment

## Mapping
https://github.com/user-attachments/assets/424e7ed0-a6dc-4718-93cc-ae7a607b69dc

## System Setup

### Hardware
- Jetson Xavier NX
- TurtleBot3(Waffle Pi)
- openCR
- Intel RealSense RGB-D camera(D455i)

### Software / Libraries
- Ubuntu: 20.04(Jetson)
- ROS: ROS 1(Noetic)
- SLAM: RTAB-Map (`rtabmap_ros`)
- Visualization: RViz
- Sensor driver: `realsense2_camera` (Intel RealSense SDK)

## Graph-based SLAM
<p align="center">
  <img src="https://github.com/user-attachments/assets/553516d8-ecd6-4704-aec5-83d92a6b10a4" width="48%" />
  <img src="https://github.com/user-attachments/assets/f496cf94-7f43-4774-a268-e12da8e2a143" width="48%" />
</p>


## Target Environment for Mapping
![Image](https://github.com/user-attachments/assets/127b760d-c1bf-43c7-803f-473ba0890924)

## Issues

### Topic Synchronization Issue (Early Mapping Problem)
- Problem
  Topics such as `rgb_image`, `aligned_depth_to_color_image`, `color_camera_info`, and `odometry` were published with different timestamps.
  RTAB-Map dropped many messages due to poor synchronization.
- Solution
  Enabled approximate time synchronization `approx sync`
  Tuned subscriber `queue_size`

### Loop Closure Reliability
- Problem
  Loop closure often relies on visual features; it can be weaker in low-texture environments.
  Needed a way to monitor and improve loop-closure acceptance/rejection.
- Actions
  Monitored loop-closure status via RViz/RTAB-Map logs
  Tuned relevant RTAB-Map parameters `thresholds` and `OptimizeMaxError`

## Refined Map Results
![Image](https://github.com/user-attachments/assets/17acc730-f338-46f8-bd03-c066357c3b8d)

## References
https://wiki.ros.org/rtabmap_ros/noetic_and_newer
https://wiki.ros.org/rtabmap_ros/Tutorials/HandHeldMapping
https://wiki.ros.org/rtabmap_ros/Tutorials/MappingAndNavigationOnTurtlebot
https://github.com/introlab/rtabmap/wiki/Change-parameters

## Repository Structure (Recommended)
```txt
.
├─ launch/           # roslaunch 파일
├─ config/           # YAML params (rtabmap, nav, costmap 등)
├─ scripts/          # 실행/자동화 스크립트(optional)
├─ docs/             # 결과 이미지, GIF, 데모 자료
└─ README.md







