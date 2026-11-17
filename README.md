# Robotek — WRO 2026 Future Engineers

Engineering repository prepared from the coach baseline. Source code is included; physical evidence and team-specific validation remain incomplete. This is a working engineering draft, not a certified competition submission.

## Team and vehicle

Team members, roles, institution, event, date, vehicle revision and current photographs: PENDING.

## Technical baseline

The team identifies renzodamgo/robotek-learn as the reference for the current car. Reviewed baseline: `c5de794342b5da46725ba9a6994fb73bbebd0ff0`. The motor has an encoder and is controlled through the RRC Lite board; the external TB6612 belongs to an earlier configuration. The encoder measures rotation; power electronics still drive the motor.

The baseline robot.yaml selects `motor_backend: rrc`, `rrc_motor_port: 2`, `motor_rps_per_mps: 7.0`, `motor_max_rps: 3.4` and `wheelbase: 0.1174`. These are source values, not new measurements. Launch files can override them. Historical comments mention several gear ratios; the latest calibration comment identifies 1:1 gears. Confirm the deployed revision before publishing these as final vehicle specifications.

## Documentation

- [Mobility & Mechanical Design](docs/mobility.md)
- [Power & Sensor Architecture](docs/power-and-sensors.md)
- [Software Architecture & Obstacle Strategy](docs/software.md)
- [Systems Thinking & Engineering Decisions](docs/engineering.md)
- [Reproducibility & GitHub Quality](docs/reproducibility.md)
- [Evidence map](docs/rubric-evidence.md)
- [Testing](docs/testing.md)

## Source and reproduction

The complete tracked coach snapshot is included in src/, tools/, course/ and reto/. It includes Open v5 and Obstacle v3. Confirm that its commit matches the vehicle deployment. See [installation](docs/installation.md), [vehicle baseline](docs/current-vehicle.md) and [source map](docs/strategy-map.md). Manufacturing CAD, actual wiring, team evidence and newly recorded results remain pending.

## Credits

Coach reference: https://github.com/renzodamgo/robotek-learn . Preserve original license files and component-specific notices when importing source. Team authorship and modifications must be stated separately.


## Engineering explanation and validation plan


### Mobility & Mechanical Design

Document chassis dimensions, mass, wheelbase, track width, wheel diameter, mounting, steering geometry and transmission. Include editable CAD, manufacturing drawings and assembly photos. Explain component selection and alternatives. Calculate gear ratio with clearly labelled driver/driven gears, wheel speed and torque assumptions. Measure left/right turning radius, speed and braking distance. Compare revisions under the same conditions; discuss backlash, traction and stability.

### Power & Sensor Architecture

Provide a wiring diagram with connector labels, polarity, voltages, signal direction and common grounds. List battery chemistry/capacity, regulators, rated and measured currents, peak loads and runtime. Calculate power per rail (V × A), account for conversion efficiency and compare with source capacity. For each sensor explain function, placement relative to field geometry, blind spots, calibration, uncertainty and failure response. Include camera lighting tests, LiDAR chassis occlusion, IMU axes and encoder limitations.

### Software Architecture & Obstacle Strategy

Map real packages, nodes, topics, units and update rates. Link each algorithm to its implementation. Draw state transitions with conditions, timeouts and stop behavior. Explain Open start, direction detection, wall following, corners, lap count and finish. Explain Obstacle localization, LiDAR/camera association, colour memory, side selection, corner planning, lot exit and final parking. Describe unknown colours, stale sensors and failed maneuvers. Identify the exact launch command and effective parameters, including launch overrides. Distinguish course solutions from deployed strategies.

### Systems Thinking & Engineering Decisions

For every major change record: observed problem, constraints, alternatives, choice, interaction with other subsystems, test, result and remaining limitation. Include changes to motor, gearing, control board, steering and sensor placement. Use measured before/after evidence. Keep a failure register with severity, detection, mitigation and verification. Identify authors and dates; explain coach-provided and team-developed work.

### Reproducibility & GitHub Quality

Include a model-specific bill of materials, editable CAD and manufacturing exports, complete wiring, actual deployed source and configuration, dependencies and versions, installation/build/launch instructions and calibration workflow. Test setup from a clean environment. Record meaningful commits, release notes, test workflow and hardware/software version mapping. Verify all links and media without signing in. Include all programmed components, not just the main strategy.

## Runtime architecture

The Raspberry Pi runs ROS 2 nodes that acquire LiDAR, IMU and camera information, estimate geometric relationships to the field, choose a maneuver and send motion commands to the hardware adapter. The adapter converts motion requests into steering and motor commands for the RRC Lite. Sensor orientation and steering calibration are part of this interface, not optional presentation details. The relevant source paths are indexed in docs/strategy-map.md.

Open v5 uses gyro heading with wall corrections and measures progress toward the front wall. Its corner and finish conditions are part of the mission implementation. Obstacle v3 adds sign position and colour association, remembered observations, side selection, corner planning and parking. The selected parking profile must be stated explicitly because the supplied source includes multiple approaches and field-specific finishing pulses.

## Evidence and performance

No new physical or simulated performance result is claimed by this packaging work. Inherited result files document their original experiments and retain their original context. Before submitting, identify which results match the present hardware, source revision and launch profile. Record all new attempts, including failures, in other/test-results.csv. Include both driving directions, different layouts, sensor conditions and parking outcomes. Present completion counts with denominators, times and failure categories.

## Engineering history and attribution

Earlier Robotek documentation mixed L298N and TB6612 descriptions and linked current-looking media to a 2025 repository. This repository treats the RRC encoder-motor configuration as the coach baseline and keeps historical material in its original context. The source snapshot has not been rewritten to erase its development history. New team changes should identify the problem, alternatives, chosen change, test and measured effect.

Original LICENSE, CREDITS.md and component notices are retained. The RRC-derived components have specific upstream notices; do not assume every third-party component is licensed identically. The documentation preparation does not establish independent student authorship of inherited code. Team members should document their contributions and be able to explain the system.

## Submission readiness

The supplied 2026 rubric assesses five categories of six points. The supplied general rules require English documentation for the international event, at least 5000 characters in README.md, team and six-side vehicle photographs, and a YouTube video per challenge with at least 30 seconds of autonomous driving. The repository also needs meaningful historical commits according to the event deadlines, public access and a printed copy for the international final. Confirm exact event dates and applicable updates with the organizer.

This README exceeds the length threshold, but length alone does not establish compliance. Missing hardware evidence, measurements, identity and reproduction records remain explicit blockers to a final submission. Use docs/rubric-evidence.md to link each criterion to the actual explanation, technical files and validation record. Do not replace missing results with estimates presented as measurements.
