# Engineering decisions and system integration

The following decisions are reconstructed from the supplied reference source and previous team documentation. They describe documented engineering reasoning, not newly conducted experiments. Student ownership, dates and new comparisons are captured in the [decision register](../other/decisions.csv).

## D01 — Encoder motor through RRC Lite

The previous documentation alternates between L298N and TB6612. The current source selects RRC motor control and M2. Consolidating motor control in the board changes the command interface from external PWM percentages to board speed requests. The encoder is feedback for that controller, while vehicle localization remains sensor/strategy-specific.

The practical trade-off is a more integrated interface with a board-specific motor/encoder model. The source records attempts involving motor types, signs and zero-speed behavior. The current configuration avoids sending a motor type and disables the earlier alternating-brake/reset workaround. A reproduction procedure must verify actual direction and stopping response rather than transplant an earlier motor-type setting.

## D02 — Gearing selected for the useful speed range

Earlier comments mention speed-up and reduction gear pairs; the latest calibration identifies 1:1. The choice affects start reliability and low-speed parking as well as Open speed. The software conversion and minimum-rps setting must be recalibrated after a physical gear change. Holding the command conversion fixed would mix mechanical and software versions.

An appropriate comparison measures several fixed-distance straight runs, full-lock starts and braking tests with the same battery range. Report both mean behavior and failures to start. This comparison is specified, but no fabricated before/after result is inserted.

## D03 — Measured steering mapping instead of symmetric assumptions

The servo centre and left/right lookup tables reflect non-linearity and asymmetry. The limiting side determines the common usable angle. This reduces the mismatch between a commanded wheel angle and the actual linkage response, at the cost of calibration effort and sensitivity to mechanical reassembly.

Changing the horn position, tie-rod adjustment or servo mount requires a new calibration. A steering table is a property of the assembled mechanism, not merely a reusable software constant.

## D04 — Gyro integration corrected by wall geometry

The gyro offers frequent relative-turn measurements but accumulates error; walls provide an external geometric reference on suitable straights. Bounded wall-heading correction combines them. The gate avoids applying an unreliable fit during an arc or treating a large discrepancy as ordinary drift.

This also demonstrates subsystem interaction: sensor placement and field visibility affect the correction, which affects corner timing and therefore mechanical clearance.

## D05 — Candidate geometry plus camera colour

LiDAR contributes location and clearance; the camera contributes colour. Memory by seat retains observations across laps. Calibration errors or wrong association can contaminate that memory, so accuracy should be evaluated at association level as well as image-classification level.

The design reduces dependence on seeing a perfect colour patch at the instant of passing. Its limitation is the need for consistent localization, bearings and observation timing.

## D06 — Explicit parking profile

The source retains both a geometric search and a fixed-mode solution. The car-round profile adds finish pulses to partial fixed parking. Documenting the actual selected branch avoids attributing a generic algorithm to a calibrated, field-specific maneuver. Compare modes using the same lot dimensions, departure conditions, battery and scoring observations.

## Failure analysis

| Failure or risk | Cross-system cause | Baseline response / remaining verification |
|---|---|---|
| Wrong initial direction | Camera ambiguity and fallback | LiDAR correction before first corner; test both directions |
| Heading accumulation | Gyro bias/scale and delayed wall correction | Stationary bias and bounded straight-wall correction |
| Low-speed stall | Motor dead zone, load and steering lock | Minimum-rps option; measure overspeed consequences |
| Parking variability | Timed pulses, battery and traction | Repeat full-round profile across controlled conditions |
| Stale sensor input | Device/transport gaps | Strategy waiting/watchdog paths; test physical stopping |
| Low battery | Supply peaks or discharge | Board warning is not an automatic cutoff |
| Misleading documentation | Historical code/parts presented as current | One baseline revision, effective profile and evidence IDs |

## Development history

The earlier team README names Sami and documents changes to steering, chassis and motor electronics. That history is retained as a reference link rather than imported as the present wiring description. The current source snapshot records later RRC, gearing and calibration changes. This editorial edition introduces no new physical design revision and creates no artificial historical commits.
