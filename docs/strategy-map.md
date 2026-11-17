# Strategy and source map

| Subsystem | Source | Role |
|---|---|---|
| Open mission | src/robotek_open/robotek_open/v5/mission.py | heading control, straight progress, corners and finish |
| Open scene | src/robotek_open/robotek_open/v5/scene.py | geometric observations from scans |
| Open ROS node | src/robotek_open/robotek_open/v5/node.py | runtime integration |
| Open car profile | src/robotek_open/config/car_picam.yaml | vehicle-specific parameters |
| Obstacle ROS interface | src/robotek_obstacle_v3/robotek_obstacle_v3/drive.py | sensor inputs and velocity commands |
| Obstacle mission | src/robotek_obstacle_v3/robotek_obstacle_v3/mission.py | challenge sequencing |
| Localization | src/robotek_obstacle_v3/robotek_obstacle_v3/localizer.py | wall-based localization |
| Perception | src/robotek_obstacle_v3/robotek_obstacle_v3/perception.py | candidate traffic signs |
| Corner planning | src/robotek_obstacle_v3/robotek_obstacle_v3/corner.py | clearance-aware corner path |
| Parking | src/robotek_obstacle_v3/robotek_obstacle_v3/park.py and park_fixed.py | planned and fixed parking modes |
| Hardware calibration | src/robotek_hardware/config/robot.yaml | actuator and sensor configuration |
| Runtime selection | tools/car-run.sh and src/robotek_course/launch/car.launch.py | strategy and launch overrides |

Open v5 integrates gyro heading and corrects it against walls. Straight progress comes from the changing front-wall range. The camera contributes direction selection; the car profile enables a fallback that can be corrected with LiDAR before the first corner. Explain that fallback and its limits rather than claiming perfect direction recognition.

Obstacle v3 combines LiDAR positions with camera colours, remembers signs, selects the required passing side and plans corners. Its documented wrapper waits for stale sensors and has a mission timeout. Parking mode and profile change behavior. The round profile currently includes partial fixed parking followed by calibrated pulses; a general A* description alone would misrepresent that selected configuration.

Use the included tests as implementation references. New team validation must record physical results separately from inherited results and simulated scores.
