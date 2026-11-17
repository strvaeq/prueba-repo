# Assembly, installation and calibration

## Mechanical assembly sequence

The repository contains the software and simulation geometry of the coach reference. The current physical manufacturing drawings and fastener list have not been supplied. The following sequence explains subsystem assembly and verification; it cannot replace those dimensional manufacturing files.

| Stage | Assembly action | Verification before proceeding |
|---|---|---|
| Chassis | Assemble the current frame and mounting points from the matching CAD revision | No twist; wheelbase and track width measured |
| Drivetrain | Fit the driven axle, bearings, motor mount and identified gear pair | Free motion, correct gear mesh and no binding |
| Steering | Fit front pivots, linkage and servo | Symmetric free travel; no hard stop inside commanded range |
| Compute and board | Secure the Pi and RRC with access to connectors and switch | Mounting orientation recorded; no cable strain |
| Sensors | Install LiDAR, camera and rear range where used | Field of view and chassis occlusion checked |
| Power | Connect according to a verified current wiring drawing | Rail voltage, polarity and source capacity checked |
| Calibration | Apply the matching sensor and actuator mappings | Supported-wheel checks, then controlled floor tests |

## Software target

Ubuntu 24.04 arm64 on Raspberry Pi 5, ROS 2 Jazzy. Gazebo is part of the development/simulation route, not a prerequisite for physically mounting the components. The package manifests and setup scripts declare dependencies. Read scripts before running installation commands that modify the operating system.

After placing this repository on the Pi, run from its root:

```bash
bash tools/setup-pi.sh --dry-run
bash tools/setup-pi.sh
source /opt/ros/jazzy/setup.bash
colcon build --symlink-install
source install/setup.bash
bash tools/setup-pi.sh --check
```

If new device groups were added, log out and back in. The teaching-script message about a missing `my_open` is not a reason to replace the included Open v5: this edition uses robotek_open and robotek_obstacle_v3. Helpers that fetch teaching reference tags require the coach Git repository and are not needed to run these included strategies.

## First verification

1. Keep the wheels supported for initial motor/servo tests. Verify neutral stop before driving on the floor.
2. Check `/dev/rrc_lite`, `/dev/ldlidar` and the selected camera. Device identity and group permissions must match the setup.
3. Turn the car left by hand and check gyro sign; place objects ahead and to each side and verify LiDAR bearings.
4. Check servo centre and left/right direction. Verify that a forward request turns the correct motor port in the intended direction.
5. Measure board-command versus actual speed on the floor, then test braking and full-lock starts. Do not infer floor behavior from unloaded wheels.
6. Save the final parameter profile and associate it with the hardware revision and source commit.

## Run one challenge

```bash
bash tools/car-run.sh open
```

Or, in a separate session after stopping the first challenge:

```bash
bash tools/car-run.sh obstacle
```

The wrapper cleans up prior car nodes and autostart. Wait for readiness and use the board's Start button. Button stopping and startup suppression are implemented by the selected wrapper/node path; verify them in the initial controlled test. Ctrl+C terminates the launch, but actual stopped-wheel behavior must also be checked.

## Full-round parking profile

The following is the baseline's field-specific example, not a universally calibrated command. Set the profile path to the extracted repository root:

```bash
PROFILE="$PWD/src/robotek_obstacle_v3/config/car_picam_park_round.yaml"
bash tools/car-run.sh obstacle start_lot:=true \
  strategy_params:="$PROFILE" motor_rps_per_mps:=8.0 motor_min_rps:=2 \
  recover_back:=0.3 lot_exit_speed:=0.2 \
  lot_exit_steps:='L+0.25 R-0.3 L+0.25 R-0.3 L+0.25 R-0.3 C-0.2'
```

This example differs from the baseline robot.yaml conversion of 7.0 and explicitly changes minimum speed and lot exit. Review [parking](05-obstacle-challenge.md) before using it. Record all overrides when reporting a result.

## Record the running configuration

```bash
ros2 node list
ros2 topic list
ros2 launch robotek_course car.launch.py --show-args
```

Use `ros2 param dump` with the actual node name printed by the running system. Save its output with the test's profile and telemetry. Runtime frequencies should be measured with `ros2 topic hz` on the selected topics, not copied from a nominal camera specification.

## Calibration after a modification

| Changed item | Recalibrate / recheck |
|---|---|
| Motor or gear ratio | Command-to-speed conversion, minimum start, reverse and stopping |
| Servo or linkage | Centre, side-specific angle tables, limit and turning radius |
| Board mounting | IMU axes, bias and yaw sign |
| LiDAR mounting | Zero bearing, blind sectors, range validity and wall fit |
| Camera or image pipeline | Field of view, optical offsets, rotation and colour thresholds |
| Battery / regulator | Voltage under load, transients, runtime and fault behavior |

## Simulation and package tests

```bash
source /opt/ros/jazzy/setup.bash
colcon build --symlink-install
source install/setup.bash
ros2 launch robotek_course sim.launch.py
```

Use the source's round launch arguments for the selected strategy and environment. Package tests are retained under each package's test directory. A local pure-logic run can use `python3 -m pytest src/robotek_open/test src/robotek_obstacle_v3/test` after the relevant package imports/dependencies are configured. These commands are documented; they were not executed on a ROS-equipped machine as part of this rebuild.

A clean-machine reconstruction is complete only when another person can install, connect, calibrate and run the documented revision using the supplied artifacts. The missing physical artifacts are tracked in [the evidence register](10-evidence-register.md).
