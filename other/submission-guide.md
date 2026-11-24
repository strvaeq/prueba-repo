# Evaluation guide — evidence linked to the supplied rubric

The supplied WRO 2026 Documentation Rubric has five criteria, each with a maximum of six points. Its upper descriptors combine explanation with reasoning, trade-offs, iteration and validation. A section heading or a large file count alone does not meet those descriptors.

| Criterion | Developed explanation | Technical artifact | Evidence still required |
|---|---|---|---|
| Mobility and mechanical design | [Mechanics](../docs/02-mobility-and-mechanical-design.md), model calculations and steering/gearing rationale | [Vehicle model](../src/robotek_common/robotek_common/vehicle.py), [hardware mapping](../src/robotek_hardware/config/robot.yaml) | Editable manufacturing CAD and current M01–M03 results |
| Power and sensor architecture | [Power/sensors](../docs/03-power-and-sensor-architecture.md), budget method, calibration and failure behavior | [Architecture](../schemes/README.md), configuration, [power budget](power-budget.csv) | Verified electrical drawing, component ratings and actual consumption/calibration |
| Software architecture and obstacle strategy | [Interfaces](../docs/04-software-architecture.md), [Open](../docs/05-open-challenge.md), [Obstacle](../docs/06-obstacle-challenge-and-parking.md) | Linked implementation, profiles and package tests | Deployment parameters and repeated physical validation |
| Systems thinking and engineering decisions | [Decisions](../docs/01-vehicle-design-history.md), subsystem interactions and iteration history | Source-linked baseline history and [decision log](decisions.csv) | Team-owned dated decisions with measured comparisons |
| Reproducibility and GitHub quality | [Reproduction](../docs/09-build-and-run.md), navigation, attribution and versioning | Source, manifests, setup scripts, component notices and [changelog](../CHANGELOG.md) | Full physical artifacts, clean-install record and authentic event-compliant Git history |

## Requirements from the supplied general-rules PDF

The supplied version is dated January 15, 2026. Chapter 7, pages 8–10, specifies English documentation for the international competition; README of at least 5000 characters; team and vehicle photos from every side, top and bottom; and one YouTube video per challenge containing at least 30 seconds of autonomous driving. It also requires source for programmed components and a hardcopy at the international final.

The PDF sets commit milestones at two months, one month and two weeks before competition. The first must contain at least a fifth of the final code; the third is the main evaluation snapshot. The repository link is due no later than three weeks before the event, subject to the organizer's exact deadline. The repository must remain public from submission and for at least twelve months after the event.

These statements describe the supplied document, not a verification that no later event clarification exists. The event/date and applicable updates must be established before calculating deadlines. A newly created ZIP or import commit does not create a historical milestone retroactively.

## Score interpretation

The reference teams' scores were supplied by the user. They are useful context, but they do not establish why a judge deducted a particular fraction of a point. Current repository contents may also differ from their judged snapshot. [Reference practices](../CREDITS.md) therefore identify visible, useful methods without claiming that a visible omission caused a historical deduction.

## Final reading route

Start at README, inspect the relevant design chapter, follow its implementation links and then inspect the matching evidence record. The [evidence register](evidence.md) exposes remaining physical gaps rather than hiding them inside an optimistic final score.
