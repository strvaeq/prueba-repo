# Source provenance

Technical source: https://github.com/renzodamgo/robotek-learn

Pinned commit: c5de794342b5da46725ba9a6994fb73bbebd0ff0

Included: tracked src/ packages and tools/ utilities, except tools/pi-monitor (the unrelated macOS menu-bar app). The root teaching exercises and course snapshots are not copied into this vehicle repository. ROS launch integration remains in src/robotek_course. All included source paths keep their package layout.

The root documentation is new. .gitignore permits tracking src/my_open and src/my_obstacle. Original LICENSE and per-component license/notice files remain. No control-logic or calibration change was made. Chinese vendor comments were translated, the LiDAR README retains its English section, and one diagnostic string was translated to English.

Language-edited source files:

- `src\ldlidar_stl_ros2\README.md`
- `src\rrc_lite_driver\rrc_lite_driver\rrc_driver.py`
- `src\rrc_lite_driver\rrc_lite_driver\rrc_lite_driver_sdk\board.py`
- `src\ldlidar_stl_ros2\ldlidar_driver\src\core\ldlidar_driver.cpp`
- `src\ldlidar_stl_ros2\ldlidar_driver\src\logger\log_module.cpp`
- `src\ldlidar_stl_ros2\ldlidar_driver\src\networkcom\network_socket_interface_linux.cpp`
- `src\ldlidar_stl_ros2\ldlidar_driver\include\core\ldlidar_datatype.h`
- `src\ldlidar_stl_ros2\ldlidar_driver\include\core\ldlidar_driver.h`
- `src\ldlidar_stl_ros2\ldlidar_driver\include\logger\log_module.h`

The ZIP is a source delivery, not a clone carrying the team's historical commits. Retain existing Git history when integrating it into the destination repository. Source observations are attributed to their original context, not reported as new physical validation.
