# Vehicle design history

The team archive describes eleven labelled builds. The photos below are linked to the team’s original GitHub uploads. Dimensions and outcomes belong to the version in each caption. [Team design archive](https://github.com/strvaeq/Robotek-WRO2026/blob/f16a02ce8040f0c1b6ed20c8ab7860a72ea6a70d/README.md)

## V1 · Cardboard steering prototype

A cardboard base let the team move the front wheels and study the Ackermann linkage before committing to rigid mounting points. The prototype served as a layout reference for the electronics. V2 turned that layout into a powered assembly.

<img src="https://github.com/user-attachments/assets/88cb9f71-715d-41d5-8dcd-54870af7fa87" width="380" alt="Archived team photograph of Sami V1">

## V2 · Acrylic chassis and powered steering

The team cut an acrylic base and printed mounts for the camera and steering. A stepper moved the linkage, one motor drove the car, and a Pi 4 and Arduino Nano connected the webcam and infrared sensing to the prototype. The batteries and power bank now had to share space with the moving mechanism.

<img src="https://github.com/user-attachments/assets/14afa30d-317e-43f8-b6ef-d63897212c88" width="380" alt="Archived team photograph of Sami V2">

## V3 · Two levels and forward-facing infrared sensors

A smaller power bank, higher-current batteries and new wheels accompanied a two-level layout. Moving the infrared sensors forward was intended to improve corner timing. This revision changed both the available current and where the car observed the wall.

<img src="https://github.com/user-attachments/assets/5299a922-0fb3-43a8-9a32-9bdbc77225d7" width="380" alt="Archived team photograph of Sami V3">

## V4 · Modified HiWonder base and ROS

The team switched from infrared sensors to LiDAR, from webcam to monocular camera and from a steering stepper to a servo. A geared two-encoder-motor arrangement and the move away from the Nano introduced a new drive and software architecture. This is the historical V4 drivetrain.

<img src="https://github.com/user-attachments/assets/80568426-a136-48a6-b219-9c05dd3e2584" width="380" alt="Archived team photograph of Sami V4">

## V5 · A clear view for the LiDAR

The team fastened the two bases together, placed the Pi inside and moved the LiDAR to the top to clear its line of sight. A camera housing fixed the camera position. Once horizontal obstructions were addressed, scan height became important.

<img src="https://github.com/user-attachments/assets/fe6757a1-3fe5-4b12-b856-bedcc28a5b50" width="380" alt="Archived team photograph of Sami V5">

## V6 · Matching scan height to the walls

The high scan plane had missed the track walls. Changing wheels adjusted the chassis height. The team also switched the housing from PLA to polycarbonate and reported completing the three-lap Open run on this build.

<img src="https://github.com/user-attachments/assets/7e483e4c-2f35-48e9-8125-00a2123f06a2" width="380" alt="Archived team photograph of Sami V6">

## V7 · Single deck and single geared motor

A smaller custom chassis and purpose-positioned mounting holes accommodated a single geared drive motor. Arranging components on one surface improved access and airflow around the Pi. The team reported its first successful sign detection and avoidance at this stage.

<img src="https://github.com/user-attachments/assets/105155b6-ddb2-4885-aa63-7e07f1468315" width="380" alt="Archived team photograph of Sami V7">

## V8 · Narrower wheels and a vertical steering servo

At a reported 15 × 23 cm, the car still had protruding front wheels. Slimmer printed wheels and a vertical servo mounting freed space. A tilted LiDAR mount addressed poor wall visibility. The next revision exposed a separate clearance issue between the rack and servo.

<img src="https://github.com/user-attachments/assets/5d66a0cd-a12c-4155-ae6f-aa4655cf6e0e" width="380" alt="Archived team photograph of Sami V8">

## V9 · Rack clearance and traction

The reported footprint fell to 15 × 20 cm. The team repositioned the steering to clear the servo, grooved the wheels and added spacers to prevent screw contact. The archive reports a 20-second lap. Several parts changed together, so the lap time cannot isolate one part’s effect.

<img src="https://github.com/user-attachments/assets/312c2e7e-4638-4917-b54a-fff2bb1a2965" width="380" alt="Archived team photograph of Sami V9">

## V10 · Revised gearing and rear wheels

The archive reports 15 × 18 × 16 cm. The team removed the LiDAR housing after visibility trials, printed rear wheels and moved the larger gear onto the motor shaft. It reported a 28-second three-lap run on this revision. Battery, layout and trial count are unspecified.

<img src="https://github.com/user-attachments/assets/03a1e68f-fcf6-40c0-91ea-beff7a2833ab" width="380" alt="Archived team photograph of Sami V10">

## V11 · Lighting and motor electronics

Room lighting affected colour detection. A 16-LED ring supplied local light and the LiDAR moved to a new front mount beneath the chassis. The team replaced the L298N with a TB6612FNG and reported smoother low-speed and reverse control. The later RRC interface changes how the motor receives its speed request.

<img src="https://github.com/user-attachments/assets/deba8088-32d4-4846-b635-17d4c11e2836" width="380" alt="Archived team photograph of Sami V11">

## Current encoder-motor configuration

The team identifies the current motor with encoder as part of the HiWonder kit. The coach baseline routes speed commands to RRC Lite motor port M2. The earlier external driver belongs to the historical assembly. The encoder supplies rotation feedback and the board controls motor power. The installed revision and final dimensions still need a dated vehicle record. [Power and sensing](03-power-and-sensor-architecture.md) · [Calibration](07-calibration.md) · [Next investigations](10-recommendations-and-future-work.md)
