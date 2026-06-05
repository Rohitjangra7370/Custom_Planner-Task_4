# Custom Nav2 Planner Plugin

A custom global path planner implemented as a Nav2 plugin for ROS2. Replaces the default NavFn/Dijkstra planner with a custom algorithm, demonstrating the Nav2 plugin architecture.

## Overview

Nav2 exposes a planner plugin interface that allows custom path planning algorithms to be dropped in without modifying the navigation stack. This package implements that interface with a custom planner that can be swapped into any Nav2-based navigation system.

## Stack

- **ROS2 Humble**
- **Nav2** — navigation stack (planner plugin interface)
- **C++** — planner implementation
- **Gazebo + RViz** — simulation and visualization

## Plugin Architecture

The planner inherits from `nav2_core::GlobalPlanner` and implements:
- `configure()` — initialize with costmap and parameters
- `cleanup()` — release resources
- `activate()` / `deactivate()` — lifecycle management
- `createPlan()` — compute path from start to goal on the costmap

## Usage

```bash
colcon build
source install/setup.bash

# Set planner plugin in nav2_params.yaml
# planner_server:
#   ros__parameters:
#     planner_plugins: ["GridBased"]
#     GridBased:
#       plugin: "custom_planner/CustomPlanner"

ros2 launch custom_planner navigation_launch.py
```

## Robotronics Club — IIT Mandi

Part of the Robotronics Club recruitment task series (Task 4).

## Author

Rohit Jangra · [github.com/Rohitjangra7370](https://github.com/Rohitjangra7370)
