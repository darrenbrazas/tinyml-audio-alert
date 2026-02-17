# Firmware Overview

The firmware implements real-time audio inference on an embedded microcontroller using TinyML and Edge Impulse.

## Inference Logic

- Audio is captured by the microphone in fixed window sizes
- Each window is passed through MFCC extraction
- The classifier outputs the class probabilities
- Temporal logic (v2): a rolling window of recent predictions is used to reduce false positives
- If the alarm confidence exceeds the threshold for the required number of detections in the window, an alert is triggered.

## Responsibilities

- Initialize microphone and audio buffers
- Capture aduio frams with PDM interface
- Convert raw audio to floating point signal
- Uses DSP and neural network inference
- Perform confidence thresholding and temporal smoothing (majority-vote logic)
- Trigger hardware alerts via LED signal.
