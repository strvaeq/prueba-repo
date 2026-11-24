# Calibration

Record hardware revision, software commit, profile, units and date in the [calibration log](../other/calibration-records.csv). Save the effective configuration from the running node. The [hardware profile](../src/robotek_hardware/config/robot.yaml) provides starting values for the reference assembly.

| Adjustment | Procedure and acceptance check |
|---|---|
| Steering centre and travel | Support the wheels, command neutral and mark the rack position. On a straight marked course adjust centre until tracking is repeatable. Sweep each side separately, record wheel angles and stop before binding. Repeat the left/right radius test on the floor. |
| Motor speed conversion | Mark a known distance. Time steady straight runs at several board requests and compute metres per second. Check starting and reversing under load. Record battery condition, gear pair, conversion and lowest reliable request. |
| IMU | Keep the vehicle still for bias estimation. Rotate left by a known angle and verify the sign and integrated heading. Repeat after changing the board mount. |
| LiDAR | Put a flat target ahead and then to each side at measured distances. Check zero bearing, orientation and blind sectors from a scan. Confirm the scan intersects the wall at ride height before adjusting software filters. |
| Camera | Use the installed camera, orientation and processing pipeline. Record labelled red and green images at different bearings and lighting levels. Compare the detected region and predicted bearing with the original frame. Keep false detections and missed signs for comparison. |
| Parking | Record the selected mode, minimum motor request, lot geometry and finish settings. Start from repeatable poses and measure final body clearances. Repeat after a change to gearing or steering. |

A calibration session produces settings. Use a separate set of runs to evaluate those settings with the [test protocols](08-testing-and-results.md).
