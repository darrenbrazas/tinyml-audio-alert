# Dataset Overview (V1)

The dataset consists of short 2-5 second audio clips recorded at 16kHZ and organized using two labels (noise and alarm).

## Classes (Sounds)

### Alarm

Audio samples containing the target sound (e.g. fire alarm beeps)
These clips vary in sound and pitch, they represent the positive detection class.

### Background Noise

All non-target enviromental sounds used for negative training data.
Includes ambient room noises, keys jingling, keyboard typing, distant talking, and all other non-alarm events.

The background class is crucial for reducing false positives during real world deployment.
