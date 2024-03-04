# Wall-Centering Two-Wheeled Differential Bot

This repository contains the necessary files and configurations to simulate a two-wheeled differential robot in Gazebo that is capable of centering itself between two walls using laser scan data, IMU (Inertial Measurement Unit) readings, and odometry. The robot control is implemented in Python using ROS (Robot Operating System).

## Contents

- `m2wr_description/`: Folder containing URDF files and launch configurations for the robot simulation.
- `motion_plan/`: Folder containing Python scripts for robot motion control and wall-centering behavior.

## Robot Description (`m2wr_description`)

The `m2wr_description` folder contains the following files:

- `urdf/gazebo.xacro`: Defines Gazebo properties and plugins for the robot, including materials, differential drive controller, laser sensor, and IMU.
- `urdf/m2wr.xacro`: Main robot description file defining the robot's chassis, wheels, laser sensor, and IMU using URDF.
- `urdf/macro.xacro`: Contains macros for defining common elements such as wheels and joints.
- `urdf/materials.xacro`: Defines material properties used in the visual representation of the robot.
- `launch/spawn.launch`: Launch file for spawning the robot in Gazebo. It sets parameters and launches nodes for joint state publishing, robot state publishing, and model spawning.

## Motion Planning and Control (`motion_plan`)

The `motion_plan` folder contains the following files:

- `pid_final.py`: Python script for controlling the robot's motion and wall-centering behavior. It subscribes to laser scan data, IMU data, and publishes velocity commands to control the robot's motion. A PID (Proportional-Integral-Derivative) controller is used to maintain a desired distance from the walls while navigating.

## Dependencies

Ensure you have the following dependencies installed:

- ROS (Robot Operating System)
- Python 3
- `nav_msgs`, `geometry_msgs`, `sensor_msgs`, and `tf` ROS packages
- `laser_geometry` Python package

## Usage

1. Clone this repository into your ROS workspace:

  ```bash
    git clone https://github.com/geeksahil53/Wall-Centering-Bot.git
    ```

2. **Build your workspace:**

    ```bash
    catkin_make
    ```

3. **Source your workspace:**

    ```bash
    source devel/setup.bash
    ```

4. **Launch Gazebo simulation (if not already running).**

5. **Run the PID control script:**

    ```bash
    rosrun <your_workspace_name> pid_final.py
    ```

    This will start the wall-centering behavior of the robot in the Gazebo simulation environment.

## Customization

- Modify the PID controller parameters (`kp`, `ki`, `kd`) in the `PID` class initialization to achieve desired performance characteristics.
- Adjust the behavior of the robot based on laser scan data by modifying the `take_action` function in the `pid_final.py` script.

## Issues and Contributions

If you encounter any issues or have suggestions for improvements, please create an issue on the repository. Contributions are welcome through pull requests.

Happy robot controlling!
