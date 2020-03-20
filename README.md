# iot-processassistance
## IoT data used for process monitoring and assistance

## Database for IoT-Based Activity Recognition for Process Assistance in Human-Robot Disaster Response


This Database contains 4 different tables concerning data regarding process and activity instances, as well as sensor data generated by a robotic simulation. 

These tables are mostly independent from one another. The mapping between the labeling and the sensor data only happens based on the unix time stamps, which are present in all the tables.




### Table imu
This table contains the IMU sensor data produced by the robot. In the following, its relevant columns are explained:
* **id**: A unique ID given by the database
* **secs**: Time of simulation run in seconds
* **nanosecs**: Corresponding simulation nanoseconds
* **unix_timestamp**: Timestamp in Unix time format, declaring at which time the data was sent. This is (unlikely for unix timestamps) not stored in milliseconds here, but in 0.1 seconds. Therefore, two zeros have to be added to the value before processing it
* **orientation_x , orientation_y, orientation_z**: Contains the measured data concerning the IMU's orientation for each axis of the 3D space
* **angular_velocity_x , angular_velocity_y, angular_velocity_z**:  Contains the measured data concerning the IMU's angular velocity for each axis of the 3D space
* **linear_acceleration_x , linear_acceleration_y, linear_acceleration_z**:  Contains the measured data concerning the IMU's linear acceleration for each axis of the 3D space
* **orientation_cov, angular_velocity_cov, linear_acceleration_cov**: Contains the resulting covariance matrices for each IMU feature (not used directly as a feature)

### Table activityinstance
* **genid**: A unique ID given by the database
* **processid**: The ID of the process instance this activity instance belongs to (refers to genid of the processinstance table
* **activitytypeid**: The id of the executed activity
* **name**: The name of the executed activity
* **startmillis**: The timestamp of each executed activity's begin (in unix time: milliseconds)
* **endmillis**: The timestamp of each executed activity's end (in unix time: milliseconds)

### Table processinstance
* **genid**: A unique ID, similar to process id in activity instance 
* **name**: displays, which set of processes is executed and labeled (high-level:tasks, low-level: activities)
* **startmillis**: The timestamp of the process' beginning (in unix time: milliseconds)
* **endmillis**: The timestamp of the process' ending  (in unix time: milliseconds)
* **processtypeid**: Name of the model in which the process is defined


### (Table joint_states)
The table joint_states is only part of the database for completeness.
It contains the time stamps and the data (position, velocity and effort)  from all robot arm joints, as well as these information about the gripper itself. In our scenario, it was not used for processing.

