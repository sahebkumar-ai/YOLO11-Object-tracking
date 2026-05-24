![Screenshot 2024-10-14 154109](https://github.com/user-attachments/assets/809809cc-7501-4760-8adf-6fb759212a0e)

# 🚀 YOLO11 Real-Time Object Tracking System

An advanced real-time multi-object tracking system powered by YOLO11 and ByteTrack, designed for high-performance computer vision applications such as surveillance, traffic monitoring, smart analytics, and AI-powered video processing.

---

## 📌 Project Overview

This project implements a professional-grade real-time object tracking pipeline using the latest YOLO11 model from Ultralytics combined with the ByteTrack tracking algorithm.

The system detects and tracks objects across video frames while maintaining persistent object identities, providing smooth and efficient tracking performance with live FPS monitoring and frame-processing analytics.

The project demonstrates practical applications of:
- Computer Vision
- Deep Learning
- Real-Time Video Analytics
- Object Detection & Tracking
- AI System Optimization

---

## ✨ Key Features

✅ Real-time object detection and tracking  
✅ Persistent object ID assignment across frames  
✅ YOLO11-powered high-accuracy detection  
✅ ByteTrack multi-object tracking integration  
✅ Live FPS monitoring  
✅ Frame processing time analysis  
✅ Video annotation and visualization  
✅ Optimized inference pipeline  
✅ Scalable architecture for future deployment  

---

## 🧠 Technologies Used

### Programming Language
- Python

### AI / Deep Learning
- YOLO11 (Ultralytics)
- PyTorch

### Computer Vision
- OpenCV

### Tracking Algorithm
- ByteTrack

### Development Tools
- VS Code
- Git & GitHub

---

## 📂 Project Architecture

```bash
YOLO11-Object-Tracking/
│
├── test_videos/
│   └── 2.mp4
│
├── runs/
│   └── track/
│
├── main.py
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation Guide

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/YOLO11-Object-Tracking.git
cd YOLO11-Object-Tracking
```

---

### 2️⃣ Create Virtual Environment

```bash
python -m venv venv
```

---

### 3️⃣ Activate Environment

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
source venv/bin/activate
```

---

### 4️⃣ Install Dependencies

```bash
pip install ultralytics opencv-python
```

---

## ▶️ Running the Project

Execute the following command:

```bash
python main.py
```

The system will:
- Load the YOLO11 model
- Process the input video
- Detect and track objects
- Display live tracking output
- Save annotated results automatically

---

## 💻 Core Implementation

```python
import cv2
import time
from ultralytics import YOLO

# Load YOLO11 model
model = YOLO("yolo11m.pt")

# Open input video
video_path = "test_videos/2.mp4"
cap = cv2.VideoCapture(video_path)

frame_count = 0
start_time = time.time()

while cap.isOpened():

    success, frame = cap.read()

    if success:

        frame_start_time = time.time()

        # Perform tracking
        results = model.track(
            frame,
            classes=0,
            persist=True,
            save=True,
            tracker="bytetrack.yaml"
        )

        # Visualize detections
        annotated_frame = results[0].plot()

        # Processing metrics
        frame_process_time = time.time() - frame_start_time

        frame_count += 1
        elapsed_time = time.time() - start_time

        fps = frame_count / elapsed_time

        # Display FPS
        cv2.putText(
            annotated_frame,
            f"FPS: {fps:.2f}",
            (10, 30),
            cv2.FONT_HERSHEY_SIMPLEX,
            1,
            (0, 255, 0),
            2
        )

        # Display processing time
        cv2.putText(
            annotated_frame,
            f"Processing Time: {frame_process_time:.4f} s",
            (10, 70),
            cv2.FONT_HERSHEY_SIMPLEX,
            1,
            (0, 255, 0),
            2
        )

        cv2.imshow("YOLO11 Tracking", annotated_frame)

        if cv2.waitKey(1) & 0xFF == ord("q"):
            break

    else:
        break

cap.release()
cv2.destroyAllWindows()
```

---

## 📊 System Performance Metrics

The application provides real-time performance monitoring:

| Metric | Description |
|--------|-------------|
| FPS | Frames processed per second |
| Processing Time | Time required to process each frame |
| Persistent IDs | Consistent tracking identities |

---

## 🎯 Real-World Applications

This system can be extended for:

- Smart Surveillance Systems
- Traffic Monitoring
- Autonomous Vehicles
- Crowd Analytics
- Retail Customer Tracking
- Sports Analytics
- Security Monitoring
- Industrial Automation

---

## 📸 Output Results

Processed videos with object tracking annotations are automatically saved inside:

```bash
runs/track/
```

The output contains:
- Bounding boxes
- Object labels
- Persistent tracking IDs
- FPS statistics
- Processing-time visualization

---

## 📈 Technical Highlights

### YOLO11 Advantages
- High detection accuracy
- Faster inference speed
- Real-time performance optimization
- Scalable architecture

### ByteTrack Advantages
- Stable multi-object tracking
- Robust identity preservation
- Improved tracking consistency
- Efficient tracking pipeline

---

## 🔥 Future Enhancements

- Real-time webcam support
- Multi-camera tracking system
- GPU acceleration (CUDA)
- Streamlit/FastAPI deployment
- Object counting analytics
- Speed estimation system
- Cloud deployment
- Custom dataset training
- Dashboard integration

---

## 🧪 Skills Demonstrated

This project showcases practical experience in:

- Deep Learning
- Computer Vision
- Real-Time AI Systems
- Video Processing
- Object Tracking
- Performance Optimization
- Python Development
- AI Model Integration

---

## 🤝 Contributing

Contributions, feature requests, and improvements are welcome.

### Contribution Workflow

```bash
Fork → Clone → Commit → Push → Pull Request
```

---

## 📜 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

### Saheb Kumar
AI/ML Engineer | Computer Vision Enthusiast | CSE Student

Passionate about building intelligent AI-powered systems focused on real-world impact, scalable architecture, and performance optimization.

---

## ⭐ Support

If you found this project useful, consider giving it a ⭐ on GitHub to support the project.
