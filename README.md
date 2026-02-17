# tinyml-audio-alert

## Current Version
Version 2 (Look at branches for prev version info)

## Repository Structure

This repository is organized to separate data, firmware, and
documentation for clarity and future extensibility.

- `data/`  
  Dataset structure and class definitions used during model training.
  Raw audio samples are excluded.

- `firmware/`  
  Embedded C++ code running on the microcontroller, including audio
  capture, inference logic, and alert handling.
  - `v1/` – Base version (original implementation).

  - `v2/` – Enhanced version with temporal logic to reduce false positives.

- `model/`  
  Model architecture details, training configuration, and performance
  metrics.

- `docs/`  
  System architecture diagrams, experimental notes, and design decisions.

## Overview

This project is a real time embedded hardware system that detects specific enviromental sounds (ex. alarms, noise) using a TinyML model running on a microcontroller.
Audio is captured on an integrated microphone, processed using digital signal processing (DSP) and MFCC and classified using a quantized neural network deployed on an ARM Cortex M4.
When a target sound is heard, the system triggers a hardware alert (LED ON). Version 2 focusses on temporal logic, ensuring the right sound is detected and reducing false positive, more information can be found in the subfolders.

## Objectives

- Design and implement an end to end embedded Machine Learning System.
- Learning the TinyML workflow: data collection -> training -> deployment.
- Apply digital signal processing concepts (sampling, MFCC/FFT)
- Deploy a machine learning model under strict memory (small device).
- Build a foundation for future system upgrades such as wireless IoT alerts.


## Tools and Technologies

- **Programming Language**: C/C++
- **Microcontoller**: Arduino Nano 33 BLE Sense Rev2 (ARM Cortex M4 Processor)
- **Machine Learning**: TinyML, TensorFlow Lite
- **DSP/AUDIO**: Mel Frequency Cepstral Coefficients (MFCC), real audio samples.
- **Platform**: Edge Impulse
- **IDE**: Arduino IDE
- **Version Control**: Git, Github

## Version History (Version 1)

- Base implementation of audio alert system
- Real time audio capture for integrated microphone
- On device feature extraction (MFCC)
- Sound classification using TensorFlow Lite
- LED based alert triggered when target sound confidence exceeds threshold (.8)
- No cloud audio streaming as of version 1.

## (Version 2)

- Introduced temporal logic, a majority vote window is used to dictate an alarm sound.
- Handles intermittent sounds more reliably.
- Keeps a 7 window history of the alarm confidence.
- 3 of the 7 alarm probabilities must be above threshold to correctly predict alarm sound.
- All v1 features retained.
- Ready foundation for additional sound classes and IoT alerts.

## Limitations

- Alert output limited to LED
- No wireless notifications
- Limited dataset size (nano microcontroller)
- Version 2 still only handles a single type of alert logic (windowed majority vote)

## Planned Improvements

- Further reduce false positives 
- Expanded Sounds Classes (more sounds)
- Advanced DSP & Feature Extraction
- Real time Alerts
- Dataset Expansion
- Future version control for v3+ features



