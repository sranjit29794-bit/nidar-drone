# NIDAR (Autonomous Drone / Cinewhoop CAD & System Design)

NIDAR is an autonomous search-and-rescue quadcopter system engineered for GPS-denied indoor/confined exploration, real-time 2D/3D SLAM mapping, obstacle avoidance, and survivor detection.

---

## 🚁 Project Overview

- **Vehicle Type:** 5–6 inch Ducted Cinewhoop / Quadcopter
- **Primary Mission:** Autonomous exploration, survivor localisation, and hazard detection in GPS-denied environments
- **Flight Control:** PX4 Autopilot on Holybro Pixhawk 6C / Holybro Kakute F7
- **Companion Compute:** NVIDIA Jetson Orin Nano / Raspberry Pi 5
- **Perception & Sensing:**
  - **LiDAR:** RPLIDAR A1 for 2D SLAM and planar boundary mapping
  - **Depth Camera:** Intel RealSense D435i (RGB-D) for obstacle perception and target identification
  - **Proximity:** STMicroelectronics VL53L1X Time-of-Flight (ToF) distance sensors (downward/landing altitude & proximity)
- **Power & Propulsion:**
  - 4S 2200–2250mAh high-discharge LiPo battery
  - Racerstar RS20Ax4 4-in-1 ESC / EMAX ECO brushless motors
  - Holybro PM02 / PM07 Power Management Board (PDB)

---

## 📁 Repository Structure

```
NIDAR/
├── arm.SLDPRT / arm_new.SLDPRT              # Custom quadcopter frame arm designs
├── hub_deck_1.SLDPRT / hub_deck_new.SLDPRT  # Central hub plates & mounting decks
├── HUB_TOP.SLDPRT / hub_deck_Top.SLDPRT     # Top electronics deck & protective cover
├── Pixhawk6C(コネクタ有Ver.) v4.SLDASM      # Pixhawk 6C flight controller assembly
├── Raspberry-Pi-5.SLDASM                    # Raspberry Pi 5 companion computer CAD
├── Drawings/                                # Technical 2D drafting and dimensional prints
├── Fastners/                                # M3/M4 hardware, standoffs, spacers, bolts
│   ├── screw/
│   └── standoff/
├── hardik's component/                      # Avionics, sensors, and compute CAD models
│   ├── battery/                             # 4S LiPo battery pack CAD
│   ├── camera module/                       # Intel RealSense D435i camera mount
│   ├── companion computer/                  # Jetson Orin Nano & Raspberry Pi 5 models
│   ├── holybro Pixhawk 6c/                  # Pixhawk 6C & PM02 power module models
│   ├── lidar/                               # RPLIDAR A1 CAD package
│   ├── pdb pm07/                            # Holybro PM07 power distribution board
│   ├── propellor/                           # 5-inch drone propeller models & pullers
│   ├── ST VL53L1X.../                       # ToF optical ranging sensor models
│   └── time of fligth sensor/               # Sensor datasheet documentation
├── cube-orange-pixhawk-1.snapshot.4/        # Cube Orange flight controller CAD
├── emax-eco-micro-1404.../                  # EMAX ECO micro brushless motor model
├── holybro-kakute-f7-flightcontroller.../   # Holybro Kakute F7 flight controller CAD
├── racerstar-rs20ax4-esc-4-in-1.../         # 4-in-1 ESC model & renders
├── structures and airframes/                # Research papers & design guides for drone frames
├── components.pdf                           # Complete domain-wise hardware checklist
└── NIDAR_AirMouse_—_Team_Learning...pdf     # Team roadmap & practice guide
```

---

## 🛠️ Software & Autonomy Architecture

1. **PX4 Autopilot Firmware:**
   - Real-time attitude stabilization, motor mixing, safety geofencing, and emergency recovery failsafes.
2. **ROS 2 (Humble / Jazzy):**
   - High-level autonomy middleware running on the companion computer (Jetson Orin Nano / RPi5).
   - Sensor drivers: `rplidar_ros`, `realsense2_camera`, ToF ranging nodes.
3. **Mapping & SLAM:**
   - `slam_toolbox` for real-time 2D occupancy grid generation from planar LiDAR scans.
4. **Perception & Survivor Localization:**
   - Lightweight onboard object detection model identifying survivors and hazards.
   - Coordinate transform (`tf2`) converting detections into global map coordinates.
5. **GCS & Visualization:**
   - Foxglove Studio / RViz 2 telemetry dashboard over local Wi-Fi / telemetry link.

---

## 📄 License & Attribution

Designed and maintained for the NIDAR Autonomous Drone Project. All component models and research references belong to their respective manufacturers and authors.
