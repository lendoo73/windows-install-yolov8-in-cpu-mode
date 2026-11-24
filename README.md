# Install YOLOv8 in CPU Mode on Windows

This project demonstrates object detection with Ultralytics YOLOv8 on a Windows computer without requiring a GPU. The included `detect.sh` runs inference on the bundled sample image; the equivalent commands below can be run in PowerShell.

## Setup

Use Python 3.10 or newer, create and activate a virtual environment, then install the project dependency:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

The project was checked with Ultralytics 8.4.103 and CPU-only PyTorch 2.13.0. Verify that your installation is using CPU PyTorch before running inference:

```powershell
python -c "import torch; print(torch.__version__); print('CUDA available:', torch.cuda.is_available())"
```

## Run detection

Keep the included `bus.jpg` in the project directory and run:

```powershell
yolo detect predict model=yolov8l.pt source=bus.jpg device=cpu save=True
```

Ultralytics downloads the official `yolov8l.pt` model the first time it is needed. The model file is intentionally not included in this repository. Prediction results are written under `runs/` and are excluded from Git.

## Course

This example accompanies the [YOLO Masterclass: Deep Learning and Computer Vision course](https://www.udemy.com/course/yolo-masterclass-deep-learning-computer-vision-course/).
