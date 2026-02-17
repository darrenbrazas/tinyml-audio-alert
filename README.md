# tinyml-audio-alert

## VERSION-2 (Look at branches for prev version info)

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
When a target sound is heard, the system triggers a hardware alert (LED ON).

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

## Current Features (Version 1)

- Base implementation of audio alert system
- Real time audio capture for integrated microphone
- On device feature extraction (MFCC)
- Sound classification using TensorFlow Lite
- LED based alert triggered when target sound confidence exceeds threshold (.8)
- No cloud audio streaming as of version 1.

## Limitations

- Alert output limited to LED
- No wireless notifications
- Limited dataset size (nano microcontroller)
- single window interference (no temporal smoothing)

## Planned Improvements

- False Positive Reduction
- Expanded Sounds Classes (more sounds)
- Advanced DSP & Feature Extraction
- Model Optimization
- Real time Alerts
- Dataset Expansion



