# 👁️ GazeTracker

Real-time gaze estimation using a webcam. Detects faces and predicts where a person is looking using deep learning.

## How It Works

1. **RetinaFace** detects and crops the face from each webcam frame
2. **L2CS-Net** (ResNet50 backbone) predicts pitch & yaw gaze angles
3. Gaze direction is rendered as arrows overlaid on the face in real time

## Setup

```bash
# Create and activate a conda environment
conda create -n l2cs python=3.10 -y
conda activate l2cs

# Install dependencies
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
pip install git+https://github.com/edavalosanaya/L2CS-Net.git@main
pip install opencv-python
```

## Download Model

Download the pre-trained weights and place them in the `models/` folder:

🔗 [L2CSNet_gaze360.pkl – Google Drive](https://drive.google.com/drive/folders/1qDzyzXO6iaYIMDJDSyfn6hHQKia3Txa3)

```
GazeTracker/
└── models/
    └── L2CSNet_gaze360.pkl
```

## Run

```bash
python demo.py --snapshot models/L2CSNet_gaze360.pkl --device cpu --cam 0
```

Press `q` to quit.

## Tech Stack

| Component | Role |
|---|---|
| L2CS-Net | Gaze angle prediction (pitch & yaw) |
| RetinaFace | Face detection |
| ResNet50 | Neural network backbone |
| PyTorch | Deep learning framework |
| OpenCV | Camera I/O & rendering |

