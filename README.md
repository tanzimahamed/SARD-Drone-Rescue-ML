#  SARD-Drone-Rescue-ML

**A Compact Search-and-Rescue Drone with a Custom Flight Controller, Motor Driver and ML-Based Victim Detection**

![Status](https://img.shields.io/badge/status-in%20progress-orange)
![License](https://img.shields.io/badge/license-MIT-green)
![Hardware](https://img.shields.io/badge/hardware-STM32%20%2F%20ESP32-blue)
![ML](https://img.shields.io/badge/ML-YOLO--Nano%20%2F%20MobileNet--SSD-purple)

>  **Project Status: Under Development.** This project is currently in progress. Specifications below are *targets*, and the code, design files and results will be added to this repository as each phase is completed.

---

##  Overview

**S&R-DRONE** is a compact quadcopter designed for first-response search and rescue. It flies on our own electronics and finds people automatically using machine learning.

Floods, earthquakes and landslides trap people in hard-to-reach places. Manual search is slow, risky and costly, and a human operator can miss a victim in long video feeds. Commercial drones are expensive and closed-source. Our goal is a **low-cost, fully customizable** alternative with open design files and datasets for other students.

**Pipeline:** `Fly → Sense → Detect → Alert`

| Step | What happens |
| --- | --- |
| **Fly** | IMU-based flight stabilization |
| **Sense** | Capture camera and thermal data |
| **Detect** | ML-based person detection |
| **Alert** | Notify rescuers when a person is detected |

---

##  Objectives

- Design a compact quadcopter frame
- Develop a custom flight controller (IMU + MCU + PID)
- Develop a custom motor driver (3-phase BLDC ESC with protection)
- Add a camera and thermal sensor for live video
- Train and deploy an ML model for automatic person detection
- Test stability, flight time and detection accuracy

### Target Specifications

| Metric | Target |
| --- | --- |
| Weight | Under 500 g |
| Flight time | 10–15 min |
| Stable hover | Within ±___ cm *(to be measured)* |
| Detection accuracy | Above 85% (precision and recall) |
| Detection speed | At least 10 FPS |

**Out of scope:** Fully autonomous flight and automatic path planning are future work.

---

##  System Design

### Flight Controller
- MCU: STM32 / ESP32 *(final choice pending)*
- 6-axis IMU, barometer, GPS
- Sensor fusion (complementary filter) → cascaded PID control
- Failsafe and return-to-home

### Motor Driver (ESC)
- 3-phase MOSFET bridge + gate driver
- Sensorless back-EMF commutation (6-step BLDC)
- PWM speed control
- Over-current and over-temperature protection

### ML Victim Detection
- **Datasets:** public datasets (HERIDAL, VisDrone, FLIR thermal) + our own mock-test images
- **Model:** lightweight CNN (YOLO-Nano / MobileNet-SSD) with transfer learning
- **Training:** laptop / Google Colab
- **Deployment:** companion computer (Raspberry Pi Zero 2 W or similar)

---

## Why Not Existing Solutions?

| Criterion | Commercial drone | Pixhawk (open-source) | **S&R-DRONE** |
| --- | --- | --- | --- |
| Cost | High | Medium | Low (target) |
| Size | Large | Medium | Compact |
| Customizable | No | Partly | Fully |
| Hardware design | Closed | Standard board | Our own design |
| Victim detection | Manual or costly add-on | Not included | Built-in ML model |

---

##  Roadmap (10 Weeks)

| Week | Milestone | Status |
| --- | --- | --- |
| 2 | Design freeze | ⏳ Planned |
| 4 | Boards ready | ⏳ Planned |
| 7 | First trained ML model | ⏳ Planned |
| 8 | First flight | ⏳ Planned |
| 10 | Final testing and demo | ⏳ Planned |

**Phases:** Study/design/simulation → Hardware (frame, PCB) → Firmware → ML (dataset, training, testing) → Payload (camera, thermal, video) → Integration and testing → Report and demo

> Update the Status column (✅ Done / 🔄 In progress / ⏳ Planned) as work moves forward.

---

##  Planned Deliverables

- Working drone prototype
- Custom flight controller and motor driver PCBs
- Trained ML model with dataset and accuracy report
- Test report and project report
- Demo video
- Design files and source code
- Live demo (hover and person detection), poster and final slides

---

##  Risks and Mitigation

| Risk | Solution |
| --- | --- |
| PCB error | Simulation and design review first |
| Motor heating | Protection circuit |
| Crash | Tethered test, spare parts |
| Low accuracy or slow model | Smaller model, more data, thermal images |

**Estimated budget:** ৳10,000–৳10,500 BDT (frame, motors, battery, PCBs, sensors, companion computer, spare parts).

---

##  Repository Structure *(planned)*

```
SARD-Drone-Rescue-ML/
├── hardware/        # Schematics, PCB, CAD files (frame, flight controller, ESC)
├── firmware/        # Flight controller and motor driver code
├── ml/              # Dataset scripts, training notebooks, trained models
├── ground-station/  # Ground station and alert system
├── docs/            # Reports, proposal, diagrams
├── LICENSE
└── README.md
```

---

##  Team

**Department of Information and Communication Engineering (ICE), Daffodil International University (DIU)**

| Member | Responsibility |
| --- | --- |
| Waliul Islam Nabil, Khandakar Nafis Hasnain Rami | Team lead, integration, testing |
| Ritu Mony | Frame design (CAD, 3D print) |
| Umme Kulsum | Flight controller hardware and firmware |
| Md Shah Paran | Motor driver hardware |
| Md Ehsanul Hoque Badhon | Motor driver firmware |
| Tanzim Ahamed | ML model (dataset, training, deployment), documentation |
| Saad Talukder | Documentation and ground station |

> Responsibilities are shared across members; see the project proposal for the detailed assignment table.

**Guide:** Dipto Biswas, Lecturer (Senior Scale), Department of ICE, DIU

---

##  Contributing

This is an academic project, but suggestions and feedback are welcome. Feel free to open an issue.

##  License

This project is licensed under the [MIT License](LICENSE).
