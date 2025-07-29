# Anomaly Detection in Pedestrian Surveillance Videos
Seasons of Code 2025, Web and Coding Club, IIT BOMBAY




This project implements a real-time pipeline for detecting anomalies in surveillance footage using object detection (YOLOv5), tracking (DeepSORT), and custom rule-based logic. Applied on the UCSD Ped2 and Avenue datasets.

---

### 📌 Features

* 🧠 **YOLOv5** trained on **MOT17** for pedestrian detection
* 🧭 **DeepSORT** for multi-object tracking across frames
* 🚨 **Rule-based anomaly detection** based on velocity and motion patterns
* 🎥 **Video output with bounding boxes** (Green = normal, Red = anomaly)
* 📊 Easily tunable parameters: velocity threshold, smoothing, warmup

---

### 📁 Project Structure

```bash
.
├── yolov5/                          # YOLOv5 repo (cloned or submodule)
├── deep_sort_realtime/             # DeepSORT package (from pip)
├── utils/
│   └── anomaly_logic.py            # Custom rule-based logic
├── input_videos/                   # UCSD/Avenue test clips
├── output_videos/                  # Output anomaly-labeled videos
├── detect_and_track.py             # Full end-to-end pipeline
├── requirements.txt
└── README.md
```

---

### 🧪 Datasets Used

* [MOT17](https://motchallenge.net/data/MOT17/) — for training the pedestrian detector
* [UCSD Ped2](http://www.svcl.ucsd.edu/projects/anomaly/dataset.htm) and [Avenue Dataset](http://www.cse.cuhk.edu.hk/leojia/projects/detectabnormal/dataset.html) — for testing anomaly detection

---

### 🚀 Running the Pipeline

#### 1. Clone YOLOv5 and install requirements

```bash
git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt
```

#### 2. Run full detection + tracking + anomaly detection:

```bash
python detect_and_track.py --video input_videos/avenue_01.mp4 --output output_videos/result_01.mp4
```

Arguments:

* `--video`: input video path
* `--output`: output video with anomaly labels

---

### ⚙️ Key Logic

* **Anomaly = high velocity**
  Track object motion over frames using DeepSORT. If speed exceeds a set threshold → mark as anomaly.

* **New/reappearing objects**
  Add warmup period to avoid false positives when a person reappears or enters the scene.

* **Smoothing**
  Keep anomaly flag active for a few frames after detection to avoid flickering.

---

### 📷 Example Output

![example\_frame](https://github.com/yourusername/yourrepo/raw/main/assets/sample_frame.png)

---

### 📌 TODO / Extensions

* Add temporal models (e.g. ConvLSTM)
* Extend rule-based logic (size, trajectory deviation)
* Add GUI to adjust parameters live

---

### ✍️ Authors

* Your Name – *Project Lead & Developer*
* SOC 2025, Web and Coding Club, IIT Bombay

---

Let me know if you want help generating sample frames, badges, or inserting live demo videos via Colab!
