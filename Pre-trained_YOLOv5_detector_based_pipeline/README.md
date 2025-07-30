* In this pipeline A pre-trained YOLOv5-based object detector is used for pedestrian detection.

* DeepSORT is employed to perform multi-object tracking across frames.

* A Rule-based anomaly detection based on velocity and objects is implemented

* Pedestrian crossing a certain velocity_threshold is flagged as anomaly

* Objects such as bicycle, truck are flagged as anomlay

