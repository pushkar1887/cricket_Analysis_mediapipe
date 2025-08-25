# 🏏 Real-Time Cover Drive Analysis

## 📖 Overview
This project implements a **real-time cricket shot analysis pipeline**, focusing on the **cover drive**.  
It integrates **computer vision**, **pose estimation**, and **biomechanical metrics** to deliver both **frame-level insights** and a **final shot evaluation**.  

The system is designed to:
- Process **entire cricket videos** (not just keyframes).
- Perform **pose estimation per frame** using MediaPipe.
- Overlay **live metrics and feedback** directly on the video.
- Produce a **comprehensive evaluation report** summarizing batting technique.  

---

## 🎯 Objectives
- Build a **Python-based video analysis pipeline** that runs in real time.  
- Extract and track **key biomechanical features** of batting.  
- Provide **actionable feedback** for performance improvement.  
- Demonstrate reproducibility with clear deliverables.  

---

## 🛠️ System Workflow

### 1. Input & Preprocessing
- Accepts **local videos** or **YouTube links** (via `yt-dlp`).
- Normalizes **FPS** and **resolution** to maintain smooth flow.
- Ensures **end-to-end full video processing**.

### 2. Pose Estimation
- Powered by **MediaPipe Holistic** (lightweight and real time).
- Tracks landmarks for:
  - Head, shoulders, elbows, wrists  
  - Hips, knees, ankles  
- Handles **missing detections** with interpolation & fallbacks.

### 3. Biomechanical Metrics
Calculated **per frame** (and logged across time):
1. **Front Elbow Angle** (shoulder–elbow–wrist).  
2. **Spine Lean** (hip–shoulder line vs. vertical).  
3. **Head-over-Knee Alignment** (distance of head projection from front knee).  
4. **Front Foot Direction** (toe angle vs. crease axis).  

### 4. Live Overlays
- **Pose skeleton** drawn on each frame.  
- **Real-time metric readouts** displayed:
  - e.g., `Elbow: 115°`, `Spine Lean: 12°`.  
- **Instant cues**:
  - ✅ *Good elbow elevation*  
  - ❌ *Head not aligned over front knee*  

### 5. Final Evaluation
At the end of the video, system computes **category-wise scores** (1–10) with textual feedback:
- **Footwork**  
- **Head Position**  
- **Swing Control**  
- **Balance**  
- **Follow-through**  

Results exported to `evaluation.json` for downstream use.  

---
# 📂 Repository Structure

.
├── cover_drive_analysis_realtime.py # Main pipeline script
├── requirements.txt # Dependencies list
├── README.md # Documentation
└── output/ # Output directory
├── annotated_video.mp4 # Full-length annotated video with overlays
└── evaluation.json # Final scores & feedback summary        




## 🚀 Installation & Usage

### 1. Clone Repository
```bash
git clone <repo-url>
cd real-time-cover-drive
```

2. Install Dependencies
```
pip install -r requirements.txt
```

## 📌 Assumptions & Limitations
- 🏏 **Bat tracking** is excluded in this scope.  
- 📐 Metrics are **heuristic approximations**; further refinement is possible with cricket biomechanics research.  
- 🎥 Performance depends on **camera angle**:  
  - Works best with a **side-on view** of the batsman.  
- ⚡ Real-time performance requires **mid-to-high spec CPU/GPU**.  

---

## 🔮 Future Improvements
- 🪄 Integration of **bat tracking & swing arc analysis**.  
- 🤖 Machine learning–based **shot classification** (cover drive, pull, cut, etc.).  
- 📊 Use of **3D pose estimation** for more precise biomechanical evaluation.  
- ☁️ Cloud-based **dashboard visualization** for multiple players/videos.  

