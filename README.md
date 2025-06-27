# Player Re-Identification in Football Match

This project tracks players in real time using object detection and re-identification techniques, ensuring their identities remain consistent across frames—even when they're temporarily out of view or return later.

---

## 📁 Folder Structure
```
project/
├── 15sec_input_720p.mp4
│── best.pt
├── output/
│   ├── detected_frames/
│   ├── detected_video.mp4
│   ├── tracked_frames/
│   └── tracked_video_reid.mp4
├── detect.py
├── track_reid.py
└── README.md
```

## ⚙️ Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/Harshitpandey21/football_player_reid.git
cd football_player_reid
```

### 2. Create and activate a virtual environment (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```
**Or install manually:**
```bash
pip install opencv-python torch torchvision numpy pillow scikit-learn ultralytics torchreid gdown tensorboard
```

### 4. Download YOLOv8 model weights
Download the `best.pt` file from link "https://drive.google.com/file/d/1-5fOSHOSB9UXyP_enOoZNAMScrePVcMD/view" and place it inside the project root directory. This should be your fine-tuned YOLOv8 model for player, referee, goalkeeper, and ball detection.

---

## ▶️ Running the Code

### 1. Basic Detection
```bash
python detect.py
```
- Outputs: `output/detected_frames/` (annotated images) and `detected_video.mp4`

### 2. Tracking with Global Re-ID
```bash
python track_reid.py
```
- Outputs: `output/tracked_frames/` and `tracked_video_reid.mp4`

---

## 🛠 Dependencies
- Python 3.8+
- OpenCV
- Ultralytics (YOLOv8)
- Torch + TorchVision
- Torchreid
- scikit-learn
- Pillow
- gdown 
- tensorboard

---

## ✅ Notes
- Code assumes CUDA GPU availability for Re-ID acceleration. Will fallback to CPU if not available.
- Re-ID consistency is based on cosine similarity between player feature embeddings.
- Detection confidence threshold is set at `0.4`.

