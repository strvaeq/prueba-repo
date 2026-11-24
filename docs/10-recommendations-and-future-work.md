# Recommendations and future work

These are proposed experiments for the current assembly. Historical observations explain why each question matters. Record the deployed configuration before comparing runs.

| Priority | Design question and evidence | Next experiment | Result to compare |
|---|---|---|---|
| 1 · Steering | V9 needed rack clearance and the current mapping uses different left/right angle tables. How much room does each turn actually require? | Trace steady circles in both directions on the same surface, marking wheel and outer-body paths. Repeat at the selected Open and Obstacle limits. | Measured body envelope and variation across attempts against available corner clearance. |
| 2 · Parking | The round profile combines minimum motor speed with timed finishing pulses. How sensitive is the final pose to battery state? | Repeat one lot geometry and starting pose at recorded battery levels. Keep the same profile and record contacts and final clearances. | Successful complete parks per attempt, front/rear gaps and sideways offset. |
| 3 · Vision | V11 introduced lighting after room light affected colour detection. Which conditions still cause classification or association errors? | Capture labelled approaches under varied lighting with the installed camera and compare the original frame, mask and assigned sign. | Misses, wrong colours and wrong associations per condition. |
| 4 · Power | The current rail-level load budget needs physical measurements. | Measure idle, startup, steering under load and a complete run. Record the supply voltage at each measurement point. | Minimum rail voltage, peak current and observed runtime against the estimate. |

[Version history](01-vehicle-design-history.md) · [Test protocols](08-testing-and-results.md) · [Trial records](../other/test-results.csv)
