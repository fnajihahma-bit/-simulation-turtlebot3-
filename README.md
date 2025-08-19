# Simulation: TurtleBot3

## Task 1: Installation of ROS2 Simulation using TurtleBot3

---

## Directory Structure

```text
/simulation/turtlebot3/
├── README.md
├── rviz/
│   └── Task1_ROS2.rviz       # (optional saved RViz config)
└── img/
    ├── gazebo_spawn.png      # Screenshot of Gazebo with robot
    ├── rviz2_laserscan.png   # Screenshot of RViz2
    ├── teleop_running.png    # Terminal running teleop
    └── topic_list.png        # Screenshot of ros2 topic list
```
---

## Tested With:

- **OS:** Ubuntu 22.04 LTS  
- **ROS2:** Humble Hawksbill  
- **Gazebo:** Classic (via ROS2 integration)

---

## Step-by-Step Installation Guide

### 0. System Update

```bash
sudo apt update && sudo apt upgrade -y
```


### 1. Install ROS2 Humble

```bash
sudo apt install ros-humble-desktop -y
```

Add ROS2 environment to your shell:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Verify installation:

```bash
echo $ROS_DISTRO
# Output should be: humble
```

### 2. Install Gazebo and TurtleBot3 Simulation Packages

```bash
sudo apt install -y ros-humble-gazebo-ros-pkgs ros-humble-gazebo-ros
sudo apt install -y ros-humble-turtlebot3 ros-humble-turtlebot3-simulations
```

### 3. Choose Your TurtleBot3 Model

```bash
echo "export TURTLEBOT3_MODEL=waffle" >> ~/.bashrc
source ~/.bashrc
```

### 4. Launch TurtleBot3 in Gazebo

```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

### 5. Visualize in RViz2 (separate terminal)

```bash
rviz2
```

Add these displays in RViz2:

- **TF**
- **LaserScan** → topic: `/scan`
- **Odometry** → topic: `/odom`
- **RobotModel**


(Optional) Save your RViz config:
File → Save Config As… → Task1_ROS2.rviz

> **Note:**  
> If you get an error like Global Frame 'map' does not exist, change the Fixed Frame (top-left) to `odom` or `base_link`.


### 6. Teleoperate the Robot (separate terminal)

```bash
ros2 run turtlebot3_teleop teleop_keyboard
```

### 7. Inspect ROS2 Topics (separate terminal)

List all topics:

```bash
ros2 topic list
```

View LaserScan data once:

```bash
ros2 topic echo /scan --once
```

View Odometry data once:

```bash
ros2 topic echo /odom --once
```

### 8. Notes and Troubleshooting

- **RViz2 Error:** Global Frame 'map' does not exist  
  Change Fixed Frame in RViz2 to `odom` or `base_link`.

- **Gazebo does not show the robot**  
  Verify that the `TURTLEBOT3_MODEL` environment variable is set and sourced.

- **ros2 command not found**  
  Source ROS2 environment manually:

  ```bash
  source /opt/ros/humble/setup.bash
  ```

---

