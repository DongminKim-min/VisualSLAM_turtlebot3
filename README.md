# Intelligent Robot Demo — RGB-D Graph-based SLAM + Navigation (ROS1 / RTAB-Map)

> TODO: 한 줄 소개 (예: Jetson Xavier NX 기반 TurtleBot3에서 RTAB-Map으로 mapping/localization을 수행하고 move_base로 navigation을 구현)

## Overview
본 프로젝트는 RGB-D 기반 Graph-based SLAM(+ Navigation)을 목표로 합니다.
- **SLAM:** RTAB-Map (loop closure 기반 graph optimization)
- **Navigation:** move_base
- **Visualization:** RViz

### Goal
- **Mapping:** 환경 지도 생성 및 loop closure를 통한 pose drift 감소
- **Navigation:** 생성된 map 기반 주행 및 목표점 이동

---

## Demo
- 🎥 Demo video: TODO (YouTube/Drive 링크)
- 🖼️ Screenshots / results: `docs/` 폴더 참고

> TIP: GitHub에는 `docs/` 폴더에 이미지/GIF를 넣고 README에서 상대경로로 링크하는 게 관리가 쉬움.

---

## System Setup

### Hardware
- Jetson Xavier NX (SSH remote 사용, NVIDIA GPU/CUDA)
- TurtleBot3 + OpenCR
- Intel RealSense RGB-D Camera
- (Optional) LiDAR
- (Optional) Raspberry Pi

> TODO: 사용한 TurtleBot3 모델(Burger/Waffle) 및 카메라 모델(D435/D455 등) 명시

### Software / Libraries
- Ubuntu: 20.04 (Jetson)
- ROS: ROS 1 (Noetic)
- SLAM: RTAB-Map (`rtabmap_ros`)
- Navigation: `move_base`
- Visualization: RViz
- Sensor driver: `realsense2_camera` (Intel RealSense SDK)

---

## Repository Structure (Recommended)
```txt
.
├─ launch/           # roslaunch 파일
├─ config/           # YAML params (rtabmap, nav, costmap 등)
├─ scripts/          # 실행/자동화 스크립트(optional)
├─ docs/             # 결과 이미지, GIF, 데모 자료
└─ README.md
