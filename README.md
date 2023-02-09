# Sensor-Fusion-Using-Error-State-Extended-Kalman-Filter-For-Pose-Estimation-of-Self-Driving-Car

## Project Description

In this Project, I have implemented the Error State Extended Kalman Filter (ES-EKF) for multi-sensor fusion (IMU+LIDAR+GNSS) for pose estimation of the self-driving car. The motion model and filter step of the ES-EKF rely on the IMU data to propagate the state forward in time. The GPS and LIDAR data are used for the correction of the estimated state. The estimated trajectory is then compared with the ground truth trajectory generated using the CARLA simulator.

I have also investigated the effect of sensor miscalibration on the pose estimation of the vehicle. For this, I have changed the transformation matrix from LIDAR to the vehicle frame and observed its effect on vehicle pose estimation. To mitigate the sensor calibration, I have tuned the LIDAR noise covariance.

Finally, I have explored the effects of sensor dropout, that is, when all external positioning information (from GPS and LIDAR) is lost for a short period of time to illustrate how the loss of external corrections results in drift in the vehicle position estimate, and also to aid in understanding how the uncertainty in the position estimate changes when sensor measurements are unavailable.

## Result

1. Estimated trajectory and error with uncertainity in all the estimated states

![Trajectory Estimation](https://user-images.githubusercontent.com/90370308/214142271-4b211ed7-4fa1-4260-a92f-ea45464fcb90.png)        ![Error in State Estimation](https://user-images.githubusercontent.com/90370308/214142356-57f7de7e-25d8-4b3a-a708-14c0b19ada0c.png)

2. Effect of the LIDAR miscalibration on the estimated pose

- Pose estimation with LIDAR miscalibration

![Trajectory Estimation after miscalibration](https://user-images.githubusercontent.com/90370308/214143509-0b864519-15de-4911-b47b-6b42d1940d1b.png) ![Error after sensor miscalibration](https://user-images.githubusercontent.com/90370308/214143538-8601e48d-f79c-46e9-88d4-33b23ed509d8.png)

- Pose estimation after tuning LIDAR noise covarinace to account for LIDAR miscalibration

![Trajectory after calibration](https://user-images.githubusercontent.com/90370308/214143566-edc9a979-f875-4ceb-a5e2-2409e829d5a7.png) ![Error after correction](https://user-images.githubusercontent.com/90370308/214143607-5d10c152-0206-4169-bcdf-622b0e9a0271.png)

3. Effect of sensors (LIDAR+GNSS) dropout on the pose estimation
- Effect of sensor dropou on the pose estimation 

![before_traj](https://user-images.githubusercontent.com/90370308/214144542-d1a6dfa8-18a4-4b30-bad0-5d1c3b619abf.png) ![before error](https://user-images.githubusercontent.com/90370308/214144570-8be5fc21-d0c1-4bad-9c89-e0e40b1f7a9a.png)

- Pose estimation after tunning LIDAR and GNSS noise to account for sensor dropout

![after_traj](https://user-images.githubusercontent.com/90370308/214144582-36f680f4-cf4f-4cd7-9208-89fc25a6a731.png) ![after error](https://user-images.githubusercontent.com/90370308/214144598-ff66fa66-d10d-471b-ad7c-ca908d011a99.png)

## How to use this project
1. Store the ground truth, IMU, GPS and LIDAR data in the data folder of the repository in .pkl format

2. Open the solution.ipynb file and change the file path in the below code:

```
with open('data/pt1_data.pkl', 'rb') as file:
    data = pickle.load(file)
```
    
3. Run the file to see the output

## License

 [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Copyright (c) Jan 2023 Pradip Kathiriya
