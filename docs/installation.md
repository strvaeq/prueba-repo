# Installation and operation

This repository contains the coach source snapshot, including Open v5 and Obstacle v3. No ROS build or hardware run was performed while preparing this package.

## Platform

The upstream instructions target Ubuntu 24.04 with ROS 2 Jazzy; hardware setup targets Raspberry Pi arm64. Windows is suitable for editing documentation. Run the robot software on the supported Linux platform. Consult [upstream instructions](../UPSTREAM-README.md) for Gazebo and development setup.

## Hardware setup

Extract or clone this repository on the Pi. From its root, inspect tools/setup-pi.sh and follow the hardware documentation. This script installs dependencies and configures the system; it is not required just to read the repository.

```bash
bash tools/setup-pi.sh
source /opt/ros/jazzy/setup.bash
colcon build --symlink-install
source install/setup.bash
bash tools/setup-pi.sh --check
```

If setup changes device groups, log out and back in. Verify steering direction, motor direction, neutral stop and sensor orientation before field driving, using supports for initial actuator checks.

## Included strategies

```bash
bash tools/car-run.sh open
bash tools/car-run.sh obstacle
```

These are alternatives: run one challenge at a time. The wrapper stops autostart and leftover nodes, sources ROS and the workspace, then launches the chosen strategy. Start is controlled by the board button. Read upstream button timing and stopping behavior before testing.

The default Obstacle command does not establish that the final parking profile is selected. Review src/robotek_obstacle_v3/config/car_picam_park_round.yaml and its documented launch arguments. It contains field-specific geometry and finish pulses; verify both directions and actual lot dimensions before claiming general parking reliability.

Teaching helpers that fetch reference tags assume access to the upstream Git repository and its tags. A ZIP has no Git history. They are not needed for the included Open v5 and Obstacle v3 packages.

## Reproduction evidence still needed

Record exact OS image, dependencies, installed commit, launch command, parameter dump, calibration results and a successful clean installation performed by a teammate. Link that record in the evidence map.
