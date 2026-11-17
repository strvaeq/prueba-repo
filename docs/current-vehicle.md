# Current vehicle baseline

Source: coach commit c5de794342b5da46725ba9a6994fb73bbebd0ff0. Values below are taken from that source, not newly measured by this documentation project.

| Item | Baseline | Evidence |
|---|---|---|
| Motor interface | RRC Lite, M2, sign -1 | src/robotek_hardware/config/robot.yaml |
| Motor conversion | 7 board rps per m/s | robot.yaml |
| Gearing | latest calibration comment: 1:1 | robot.yaml; upstream README |
| Wheelbase | 0.1174 m | robot.yaml |
| Steering centre | 1403 microseconds | robot.yaml |
| Wheel-angle limit | 19 degrees | robot.yaml |
| Camera | IMX708 car profile; rotated image | upstream README; robot.yaml |
| LiDAR | LD19, front-facing zero | hardware configuration |
| IMU orientation | forward -x, left +z, up +y | robot.yaml |

The motor encoder and the strategy localization have different roles. The board controls the encoder motor; Open v5 estimates straight-line progress from the front wall, and Obstacle v3 uses LiDAR, gyro and camera. Do not call this wheel-encoder localization.

The external TB6612 and L298N are historical configurations. Their presence in inherited files does not mean they are installed in the current vehicle. Software drivers for the LiDAR and RRC board remain necessary.

Launch files override some parameters. The robot.yaml motor cap of 3.4 is not the complete Open runtime configuration. Record the selected profile, launch arguments and effective ROS parameters for each test.

PENDING: confirm the installed commit and any differences from this baseline; attach current photos, actual wiring, measured mass, dimensions and manufacturing CAD.
