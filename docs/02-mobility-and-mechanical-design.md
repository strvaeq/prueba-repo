# Mechanical design and mobility

[Project overview](../README.md) · [Next: power and sensing](03-power-and-sensor-architecture.md)

## Why Ackermann steering?

Rule 11.3 in the supplied 2026 international rules calls for four wheels, a driving axle and one steering actuator. Ackermann geometry is a design choice. In a bend, the inner front wheel follows a smaller circle and needs a larger steering angle than the outer wheel. The linkage couples both front wheels to one servo. Its benefit depends on the actual tie-rod geometry and available wheel clearance.

Renkay first explored wheel movement with cardboard. On V8 the servo was mounted vertically to gain room and steering travel. On V9 the rack position changed because it contacted the servo. These physical changes explain why packaging and linkage travel matter for Sami. A paired left/right turning test connects the design to the clearance available at a corner. [Version photographs](01-vehicle-design-history.md) · [Test protocol](08-testing-and-results.md)

## Layout and steering model

The reference vehicle separates propulsion from steering: a geared DC motor supplies traction and a servo moves the front linkage. Ackermann-type steering reduces the conflict between the paths of the inner and outer front wheels in a turn. A single-track bicycle model is used by the controllers; it represents the pair of front wheels by one equivalent steering angle, not two independently commanded wheel angles.

For a wheelbase L and equivalent steering angle δ, the ideal centreline radius is `R = L / tan(δ)` and the yaw rate is `ω = v / R`. This relationship gives a useful connection between a turn request and the motor/servo commands. It assumes rolling without lateral slip. At full lock, tyre scrub and the linkage's true geometry can make the measured radius differ from the calculation.

## Geometry linked to implementation

| Quantity | Source value | Interpretation |
|---|---:|---|
| Hardware/common wheelbase | 0.1174 m | Vehicle model and base adapter |
| Obstacle planning wheelbase | 0.11883 m | Geometry used to precompute its corner model |
| Effective wheel limit | 19° | Hardware lookup-table limit |
| Obstacle profile steering limit | 0.3054 rad, about 17.5° | Selected strategy parameter |
| Steering centre | 1403 μs | Baseline straight-running servo centre |
| Servo command bounds | 1000–2050 μs | Electrical command limits, not wheel angles |

The two wheelbases differ by about 1.22%. This is not resolved by replacing a number blindly: the Obstacle corner table was generated from its own geometry, while the ROS interface converts using the common model. The source explicitly retains that distinction. A future geometry update should regenerate or validate the associated planner data and measure its effect on the real trajectory.

The common model also retains REAL_STEER_LIMIT = 0.30718 rad (about 17.6°), which Open imports as its mission steering clamp. The hardware's 19° mapping limit is therefore not proof that Open commands 19°. At the common clamp and 0.1174 m wheelbase the ideal radius is about 0.370 m. Distinguish a hardware ceiling from each strategy's actual requested limit.

With 0.1174 m and 19°, the ideal radius is approximately 0.341 m. With 0.11883 m and 0.3054 rad it is about 0.377 m. These are model calculations at different steering limits, not contradictory measurements of the same test. Neither radius includes the whole swept vehicle envelope. Parking clearance must account for body corners and overhangs.

## Servo calibration

The hardware configuration maps servo deflection to real wheel angle through separate left/right lookup tables. This matters because equal pulse changes do not necessarily yield equal wheel deflections, especially near mechanical limits. A nominal 1500 μs neutral would be wrong for this recorded assembly: the source centre is 1403 μs.

The sign convention is left-positive steering. The board's pulse direction and the geometry conversion are handled by the adapter. To reproduce the calibration, first establish straight running, then record several command points on each side. Measure wheel angle or infer an equivalent angle from a controlled radius/yaw-rate experiment, documenting speed, surface, battery and uncertainty. Keep extrapolated points distinct from measured ones.

## Motor, gearbox and external gears

The coach configuration identifies a JGA27-310R motor, a 20:1 gearbox and a 7.4 V nominal specification. Its comments record several external gear arrangements during development. The latest baseline motor conversion is annotated for 1:1 external gears; 54:30 and 30:54 refer to earlier configurations.

Let N_motor be the teeth on the motor-output gear and N_axle the teeth on the driven axle gear. Then `n_axle = n_output × N_motor / N_axle`, and ideal axle torque scales by the inverse ratio. Gear losses and motor loading reduce real output. A 54-tooth motor gear driving 30 teeth speeds the axle up by 1.8; reversing that arrangement reduces speed. The same numerical pair must never be written without identifying which shaft owns each gear.

Linear speed follows `v = 2πr × n_axle` when n is in revolutions per second. The encoder model inside the board can make its reported/requested rps differ from the physical output-shaft rate for this motor combination. The car therefore uses an empirically calibrated command-to-speed conversion. The source value `motor_rps_per_mps = 7.0` is a board-command conversion, not an encoder-resolution specification.

## Design trade-offs

More gearing reduction can improve low-speed control and available axle torque, while reducing maximum speed. A fast Open round and a slow parking maneuver therefore place different demands on the same drivetrain. The motor must start reliably at turning load, not only with its wheels unloaded. A minimum board-rps command can overcome a dead zone, but also makes a nominal slow parking request faster than expected.

Battery position and component mounting affect load transfer, tyre grip and steering repeatability. The reference source notes aggressive starts and hard stops causing unwanted motion or slip; acceleration/deceleration limits reduce the requested rate of change. They do not replace physical stability measurements.

## Verification and fabrication

The manufacturing register is in [models](../models/README.md). The provided URDF and STL meshes support simulation and geometry inspection. They do not establish the fasteners, tolerances, material or editable design needed to reproduce the physical vehicle.

Use test M01 to measure straight deviation, M02 for left/right turning radius and M03 for braking distance at multiple speeds. Repeat after a gear, servo-linkage or tyre change. The [test chapter](08-testing-and-results.md) defines the procedures and the [evidence register](../other/evidence.md) records the still-unavailable physical artifacts.

## Source

- [Common vehicle model](../src/robotek_common/robotek_common/vehicle.py)
- [Obstacle planning geometry](../src/robotek_obstacle_v3/robotek_obstacle_v3/car.py)
- [Measured hardware mappings](../src/robotek_hardware/config/robot.yaml)
- [Adapter conversion logic](../src/robotek_hardware/robotek_hardware/mapping.py)


## Design choices and trade-offs

### Gearing selected for the useful speed range

Earlier comments mention speed-up and reduction gear pairs; the latest calibration identifies 1:1. The choice affects start reliability and low-speed parking as well as Open speed. The software conversion and minimum-rps setting must be recalibrated after a physical gear change. Holding the command conversion fixed would mix mechanical and software versions.

An appropriate comparison measures several fixed-distance straight runs, full-lock starts and braking tests with the same battery range. Report both mean behavior and failures to start. This comparison is specified, but no fabricated before/after result is inserted.

### Measured steering mapping instead of symmetric assumptions

The servo centre and left/right lookup tables reflect non-linearity and asymmetry. The limiting side determines the common usable angle. This reduces the mismatch between a commanded wheel angle and the actual linkage response, at the cost of calibration effort and sensitivity to mechanical reassembly.

Changing the horn position, tie-rod adjustment or servo mount requires a new calibration. A steering table is a property of the assembled mechanism, not merely a reusable software constant.
