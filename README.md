# Let's move on: Topic Change in Robot-Facilitated Group Discussions

## Data Files
The data is organized into two folders `aggregated-features` and `sequential-features`. Each file is named according to the data collection session id.

The `aggregated-features` folder contains data where features are aggregated separately for the window of 2 seconds before the end of each utterance and for the window starting from the end until the 2 seconds that followed. In the column names, the terms `before` and `after` indicate the respective time window.

The `sequential-features` folder contains the sequential features sampled using a sliding window.These features are sampled at a rate of 4 Hz over a 4-second window, spanning from 2 seconds before to 2 seconds after the end of each utterance.

### Utterance info

| name             | description                                                  |
|------------------|--------------------------------------------------------------|
| `start`          | timestamp of the beginning of the utterance                  |
| `start_0`        | start time of utterance from the beginning session (seconds) |
| `end`            | timestamp of the end of the utterance                        |
| `end_0`          | end time of utterance from the beginning session (seconds)   |
| `active`         | id of the active participant (`-1` corresponds to the robot) |
| `annotation`     | annotation                                                   |
| `duration_pause` | pause duration after current utterance (seconds)             |
| `amount_speech`  | total duration of speech on current topic (seconds)          |

### Acoustic features
The acoustic features were extracted from the individual audio signals of the active participants. For each of the acoustic features, we calculated `mean`/`max`/`min`/`std` values during each 2-second window.


| name                             | participant | description               |
|----------------------------------|-------------|---------------------------|
| `acoustic_jitterLocal_sma3nz`    | speaker     | jitter                    |
| `acoustic_shimmerLocaldB_sma3nz` | speaker     | shimmer                   |
| `acoustic_HNRdBACF_sma3nz`       | speaker     | Harmonics-to-Noise Ratio  |
| `acoustic_energy`                | speaker     | speech energy             |
| `acoustic_pitch`                 | speaker     | pitch                     |
| `acoustic_duration`              | speaker     | duration of the utterance |

### Hand Gestures and Body Features
The features were computed from the Kinect body joints. For a detailed definition of the Kinect coordinate system and body tracking joints, refer to the [Microsoft Azure Kinect documentation](https://learn.microsoft.com/en-us/azure/kinect-dk/body-joints).

| name                     | participant       | axes  | description                                            |
|--------------------------|-------------------|-------|--------------------------------------------------------|
| `kinect_spine`           | speaker/listeners | x/y   | `SPINE_CHEST` joint position in relation to the `PELVIS` |
| `kinect_spine_grad`      | speaker/listeners | x/y   | temporal difference of `kinect_spine`                  |
| `kinect_left_hand`       | speaker/listeners | x/y/z | `HAND_LEFT` joint position in relation to `SPINE_CHEST`        |
| `kinect_left_hand_grad`  | speaker/listeners | x/y/z | temporal difference of `kinect_left_hand`              |
| `kinect_right_hand`      | speaker/listeners | x/y/z | `HAND_RIGHT` joint position in relation to `SPINE_CHEST`       |
| `kinect_right_hand_grad` | speaker/listeners | x/y/z | temporal difference of `kinect_right_hand`             |

### Head Rotation Features


| name                      | participant       | description                                                                  |
|---------------------------|-------------------|------------------------------------------------------------------------------|
| `kinect_head_to_robot`      | speaker/listeners | scaled horizontal head rotation angle between the participants and the robot |
| `kinect_head_to_robot_grad` | speaker/listeners | temporal difference of `kinect_head_to_robot`                                |

## License

The data is accessible for non-commercial purposes under the terms of the Creative Commons Attribution-NonCommercial-NoDerivs (CC BY-NC-ND) license.
License information on [Creative Commons website](https://creativecommons.org/licenses/by-nc-nd/4.0/).
