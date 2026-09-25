# Multipurpose Autonomous Hexacopter for Crop Disease Detection & Precision Spraying

**Team:** The Equanimites — IIM Sirmaur
**Member:** Sambit Kumar Meher
**Event:** Global Innovation Hackathon 2026 — Bharat Academix

## Overview

An integrated, multipurpose hexacopter UAV system for autonomous crop health
monitoring and real-time precision spraying, built to address the limitations
of single-purpose drones and cloud-dependent decision-making in precision
agriculture.

- **Airframe:** Carbon fiber hexacopter (~680–750mm class), >1.5 kg payload target, motor redundancy
- **Flight controller:** Pixhawk 2.4.8 running ArduPilot, with IMU/barometer + external GPS/GNSS
- **Companion computer:** Raspberry Pi (3B+/4) processing a 1080p Arducam feed in real time
- **Disease detection:** YOLOv8n, hybrid transfer learning (COCO → PlantDoc → custom drone dataset), deployed as TensorFlow Lite, optionally accelerated with an Intel Movidius Neural Compute Stick
- **Actuation:** Geo-referenced, confidence-thresholded detections trigger a precision spray mechanism via MAVLink over serial, controlled through Pixhawk auxiliary outputs
- **Control/telemetry:** RadioLink AT10 RC + SiK telemetry links

### Results (from the report)
- mAP@0.5: **0.85**
- Precision: **0.90** | Recall: **0.82** (disease class)
- Onboard inference: ~**30 FPS** (Raspberry Pi + Neural Compute Stick)

## Repository Structure

```
├── docs/                 Full project report (PDF)
├── hardware/             Wiring references, BOM, checklists (Appendix A)
├── flight_control/       ArduPilot / Pixhawk configuration & parameters
├── companion_computer/   Raspberry Pi inference & MAVLink automation scripts
├── ml_model/             YOLOv8n training, dataset prep, TFLite conversion
```

## Report

The complete report (abstract, methodology, results, and appendices) is in
[`docs/Project_Report.pdf`](docs/Project_Report.pdf).

## Status

This repository currently holds the project documentation. Code for the
flight control configuration, companion-computer inference pipeline, and
ML model training is being added incrementally into the folders above.
