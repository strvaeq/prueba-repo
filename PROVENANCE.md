# Source provenance

Technical source: https://github.com/renzodamgo/robotek-learn

Pinned commit: c5de794342b5da46725ba9a6994fb73bbebd0ff0

The current-vehicle chapters follow the pinned runtime packages under src/. Earlier teaching materials remain in the destination repository. The vehicle launch integration is in src/robotek_course.

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

The documentation update follows the existing commit history of strvaeq/prueba-repo. Source observations are attributed to their original context, not reported as new physical validation.
