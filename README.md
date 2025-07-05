# YOLOv11-Based Vehicle Counting and Direction Detection

This project uses **YOLOv11**, **OpenCV**, and **Supervision** to perform real-time vehicle detection, counting, and directional analysis from a video feed. It identifies vehicles crossing defined lines and tracks their movement direction (incoming vs. outgoing) across two virtual lines.

---

## 🚀 Features

- Detects vehicles (cars, motorcycles, buses, trucks) using YOLOv11
- Tracks direction (incoming/outgoing) based on bounding box movement
- Counts vehicle classes crossing designated lines
- Annotates each frame with:
  - Vehicle bounding boxes
  - Direction labels
  - Red center points
  - Line overlays
  - Dynamic class-based counters (left and right side of frame)
- Saves an annotated output video

---

## 📦 Requirements

Install required Python libraries:

```bash
pip install ultralytics opencv-python supervision
```

---

## 🧠 Model

- **YOLOv11 Medium** (`yolo11m.pt`) is used for accurate real-time object detection.
- Vehicle detection is based on **COCO dataset** classes:
  - `car`, `motorcycle`, `bus`, `truck`

---

## 🎬 Input & Output

- **Input:** A video file (`test2.mp4`) placed in your working directory
- **Output:** A processed and annotated video (`output_video.mp4`) with:
  - Line crossings
  - Vehicle IDs
  - Confidence scores
  - Direction info

---

## 📈 Line Logic

Two horizontal lines are drawn:
- **Yellow Line:** Marks 60% height of the video
- **Blue Line:** 100px below the yellow line

**Logic:**
- **Incoming (Left half):** Yellow → Blue
- **Outgoing (Right half):** Blue → Yellow
- Bounding box center point movement across lines determines direction

---

## 🛠 Usage

1. Set your input video path:
    ```python
    input_video_path = "/content/test2.mp4"
    ```
2. Set the output video path:
    ```python
    output_video_path = "/content/output_video.mp4"
    ```
3. Run the script in a Python environment (e.g., Colab or local Jupyter).
4. After processing, download the output video or use it for further analysis.

---

## 📊 Sample Output

At the end of processing, the console will print total vehicle counts like:

```
Incoming Vehicle Counts (Left Half, Yellow -> Blue):
car: 12
bus: 2

Outgoing Vehicle Counts (Right Half, Blue -> Yellow):
truck: 3
motorcycle: 6
```

---

## 📁 File Structure

```
├── yolo_vehicle_counter.py        # Main script
├── test2.mp4                      # Input video file
├── output_video.mp4               # Output video with annotations
├── yolo11m.pt                     # Pretrained YOLOv11 model
```

---

## 🧾 Notes

- Ensure `yolo11m.pt` is available in your environment. If not, download it via the [Ultralytics Model Zoo](https://github.com/ultralytics/ultralytics).
- For best results, use high-resolution input videos.

---

## 📜 License

This project is provided for academic and research purposes. All models and external dependencies are subject to their respective licenses.

---

## 🤝 Acknowledgments

- [Ultralytics YOLOv11](https://github.com/ultralytics/ultralytics)
- [Supervision Library](https://github.com/roboflow/supervision)
- [OpenCV](https://opencv.org/)
