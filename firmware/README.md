# Firmware Overview

The firmware implements the real time audio interference on an embedded microcontroller using TinyML and Edge Impulse.

## Inference Logic

- Audio is captured by the microphone in fixed window sizes
- Each window is passed through MFCC extraction
- The classifier outputs the class probabilities
- If the alarm confidence exceeds the specified threshold an alert is triggered.

## Responsibilities

- Initialize microphone and audio buffers
- Capture aduio frams with PDM interface
- Convert raw audio to floating point signal
- Uses DSP and neural network inference
- Apply confidence thresholding(if target confidence exceeds .8)
- Trigger hardware alerts via LED signal.
