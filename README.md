# ATmega328 Line-Following RC Car

An autonomous line-following RC car developed as a Microcontrollers project. The system uses an **ATmega328
microcontroller**, a **5-sensor IR reflectance array**, and an **L298N motor driver** to detect and follow a line while maintaining smooth and reliable motion.



##  Overview

The project is an autonomous mobile platform designed to follow a predefined track using infrared sensors.

The IR sensor array detects the contrast between the dark line and the lighter surface. The sensor readings are processed by the ATmega32 to determine the car's position relative to the center of the track. Based on this error, the controller adjusts the speed and direction of the two motors using PWM.

If the line is lost, the system enters a recovery state to attempt to regain the track.

##  System Features

* 5-sensor IR reflectance array for line detection
* ATmega32 microcontroller for processing and control
* L298N H-bridge motor driver
* Independent control of two DC geared motors
* PWM-based motor speed control
* PID-Lite approach for smoother turning
* Finite State Machine (FSM) for system states
* Line-loss recovery state
* Start/stop safety switch
* Status LED for system feedback

##  Control Strategy

The project follows a modular development approach divided into three main phases:

### Phase A — Hardware Integration & Calibration

The IR sensors are integrated and calibrated to normalize their readings under different lighting conditions and surface reflectivities.

### Phase B — Control Logic

A **PID-Lite** control approach is used to calculate the required correction and achieve smoother turns.

Instead of completely stopping the inner wheel during a turn, PWM is used to reduce its speed, helping to minimize shaking and improve motion.

### Phase C — State Management

A **Finite State Machine (FSM)** manages the main operating states of the vehicle, including:

* Active line tracking
* Line-loss recovery
* Manual start/stop control

## 🔧 Hardware Components

| Component            | Quantity |
| -------------------- | -------: |
| ATmega32             |        1 |
| 10 MHz Crystal       |        1 |
| AVR Programmer       |        1 |
| L298N Motor Driver   |        1 |
| Geared DC Motors     |        2 |
| Servo Motor          |        1 |
| IR Sensors           |        5 |
| 65 mm Wheels         |        2 |
| Caster Wheel         |        1 |
| Plywood Board        |        1 |
| Li-ion Batteries     |        3 |
| Resistors/Capacitors |       17 |
| Breadboard           |        1 |
| Jumper Wires         |       30 |

## 🔌 System Architecture

```text
        ┌──────────────────┐
        │   IR Sensors     │
        │   5-Sensor Array │
        └────────┬─────────┘
                 │
                 ▼
        ┌──────────────────┐
        │     ATmega32     │
        │                  │
        │ Sensor Processing│
        │ Error Calculation│
        │ PID-Lite Control │
        │   FSM / Recovery │
        └────────┬─────────┘
                 │ PWM
                 ▼
        ┌──────────────────┐
        │      L298N       │
        │   Motor Driver   │
        └───────┬───┬──────┘
                │   │
                ▼   ▼
             Motor  Motor
              Left   Right
```

## 🎯 Design Constraints

### Detection Reliability

The car should reliably distinguish the line from the surrounding surface under different ambient lighting conditions.

### Smooth Motion

Shaking during movement should be minimized by controlling motor speed through PWM, particularly during turns.

### Power Management

A dedicated Li-ion battery source is used to reduce the possibility of microcontroller resets caused by motor current spikes.

### Sensor Geometry

The physical spacing of the five IR sensors must correspond to the width of the black track.



## 🚀 Future Development

The project development will focus on:

* Completing IR sensor calibration
* Implementing and tuning the PID-Lite controller
* Implementing the FSM
* Testing line-loss recovery
* Testing the robot under different lighting and track conditions
* Improving overall movement stability



## 👩‍💻 Course Project

**Course:** Microcontrollers spring 2026
**Project:** Line-Following RC Car
**Team:** Error 404: team not found
