# IMU-data-acquisition-and-sensor-fusion
This project focuses on acquiring data from low-cost sensors — MPU9250 (IMU), HMC5883L (magnetometer), and NEO-6M (GPS) — and applying an Extended Kalman Filter (EKF) for sensor fusion. It aims to enhance motion tracking accuracy by overcoming individual sensor limitations such as drift (IMU) and signal loss (GPS).

## Project Objective

* Acquire real-time sensor data from MPU9250, HMC5883L, and NEO-6M
* Calibrate the sensors to eliminate bias and offset
* Implement EKF for fusing accelerometer, gyroscope, magnetometer, and GPS data
* Estimate accurate position, velocity, and orientation in real-time

## Hardware Components

* MPU9250 – 3-axis accelerometer + 3-axis gyroscope
* HMC5883L – 3-axis magnetometer
* NEO-6M – GPS module
* Raspberry Pi – for data acquisition and processing

## Sensor Calibration

To improve accuracy, sensors are calibrated before data fusion:

* Accelerometer & Gyroscope: Offset is calculated using the average of 500 samples.
* Magnetometer: Offset is derived by rotating the sensor in all directions and averaging the readings over 10 seconds.

## Sensor Fusion (Extended Kalman Filter)

An EKF is used to:

* Predict the state (position, velocity, yaw) using IMU data
* Correct the prediction using GPS measurements
* Apply yaw correction using magnetometer data

### State Vector

* x, y – position
* vx, vy – velocity
* yaw – orientation angle

### EKF Flow

1. Read raw sensor values
2. Convert GPS (latitude, longitude) to UTM (meters)
3. Predict motion state from accelerometer and gyroscope
4. Update the state with GPS data
5. Apply yaw correction using magnetometer
6. Save and export the filtered result

<img width="500" alt="image" src="https://github.com/user-attachments/assets/32b8a3a1-a96a-4b50-89ee-15856e678cde" />


## Output and Accuracy

* Red Path – GPS logger path (phone)
* Blue Path – Raw sensor path (MPU9250 + NEO-6M + HMC5883L)
* Green Path – EKF output (filtered path)

Average error between raw GPS and EKF output: **5.13 meters**

## Dataset

* Raw sensor data logs (CSV) - https://drive.google.com/file/d/1MSZc2ri92wEc8Nm7qAl5g8xDtpZ0N0Op/view?usp=drivesdk
* Filtered EKF output - https://drive.google.com/file/d/1MR0PKdPoQW8ihD3Qlb1ICvZ5o_7j_QCj/view?usp=drivesdk
* GPS logger reference data - https://drive.google.com/file/d/1MT03GHJNlI-IB70fbP5GRPpZ1tv4qIla/view?usp=drivesdk

## Applications

* Real-time motion tracking for robots and autonomous vehicles
* Precision agriculture and asset tracking
* Drone localization in GPS-denied environments

## Future Enhancements

* Real-time implementation on microcontrollers
* Integration with additional sensors like barometers or LiDAR
* Adaptive filtering based on terrain and environment

## Hardware setup


![WhatsApp Image 2025-05-29 at 00 14 04_59c62846](https://github.com/user-attachments/assets/166c4480-ce41-40bc-9690-3cf9a7170188)

![WhatsApp Image 2025-05-13 at 23 51 43_ce382a1a](https://github.com/user-attachments/assets/e75d70bf-0391-4017-872f-6ce5162dd92f)



## Result 
![WhatsApp Image 2025-05-03 at 21 07 22_f3f3632b](https://github.com/user-attachments/assets/b3a523c3-86f0-41f0-8157-9af6df867bdf)

