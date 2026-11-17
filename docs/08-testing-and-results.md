# Testing, results and interpretation

## What is and is not a result

This edition contributes documentation, language cleanup and packaging checks. It contributes no new physical driving result. The coach source includes calibration comments and experimental records; those remain source observations with their original revision, field and profile context. A result on different gearing, a lab simulation or a parking-only trial cannot be relabelled as a full current-vehicle round.

The registers in [other](../other/README.md) are intentionally empty of trial outcomes until the team supplies observations. This avoids making a polished repository look more experimentally complete than its evidence.

## Reproducible protocols

| ID | Question | Method | Report |
|---|---|---|---|
| M01 | Does it travel straight? | Fixed distance, several commanded speeds, repeated runs | Lateral deviation, battery, direction and speed |
| M02 | What radius can it achieve? | Constant steering/speed left and right; mark the actual path | Radius, body clearance, speed and slip |
| M03 | Where does it stop? | Fixed approach speed, visible stop trigger and floor marks | Detection delay, travel after trigger and final pose |
| P01 | Can supplies support the load? | Measure idle, compute/sensor load, start and steering peaks | Rail voltage/current and any resets |
| S01 | Are ranges and bearings correct? | Known reference positions at several bearings | Error, invalid returns and occlusion |
| S02 | Is colour reliable? | Labelled images across lighting with negative examples | Correct labels, missed signs and false positives |
| S03 | Is yaw correctly interpreted? | Stationary bias then known left/right rotations | Sign, drift and scale disagreement |
| O01 | Can Open finish reliably? | Both directions and multiple corridor layouts | Valid rounds / attempts, time, contacts and final pose |
| B01 | Can it obey signs? | Multiple layouts including signs near corners | Wrong-side passes, moved signs and completion |
| B02 | Can it park after a round? | Full route with selected lot-exit/parking profile | Entry alignment, completion time and final body clearance |
| F01 | What happens when data stops? | Controlled sensor/command interruption in an appropriate test setup | Detection time, wheel response and recovery |

Choose repetition counts before comparing variants and retain failed attempts. There is no trial count that automatically guarantees a rubric level. A small number of passes should be described with its denominator and tested conditions, not as proof of general reliability.

## Trial record

Each row records timestamp, operator, physical revision, code commit, complete profile, challenge, direction, layout, battery, lighting, surface, result, time, contacts, wrong-side passages, parking and video/log reference. Define a valid round using the event's applicable rules before testing. If the team calculates a score, label it as a team estimate.

Keep planned tests, simulated runs and real-car runs separate. A run may complete its laps and still have a parking or rule failure. That distinction is why the CSV uses separate outcome fields.

## Comparing revisions

Change one material variable where possible and keep field, battery range and measurement procedure comparable. Report completion rate and timing together: a faster best run can hide more failures. Use speed-conditioned braking and turning measurements to explain a changed trajectory rather than adjusting parameters without a record.

STORMS' mechanical measurements are a useful reference for connecting velocity to observed deviation and stopping behavior. The procedures here adopt that style of reasoning; their numbers are not copied into Sami's results.

## Telemetry and media

The launch wrapper reports the run folder. Preserve the relevant telemetry and events before deleting or reorganizing runs. Video timestamps help relate a physical contact to sensor/mission events. Video links must be readable without the owner's login. See [video/video.md](../video/video.md) for the presentation format.

## Current result summary

| Evidence class | Available in this edition | Meaning |
|---|---|---|
| Source and package tests | Included | Implementation and upstream test assets |
| Configuration/calibration history | Included with source attribution | Baseline observations, not new trials |
| Editorial/source validation | [Validation report](../VALIDATION.md) | Packaging, language and source-preservation checks |
| Newly recorded physical trials | Not supplied | Required to support current performance claims |
| Current full-round videos | Not supplied | Required physical demonstration evidence |
