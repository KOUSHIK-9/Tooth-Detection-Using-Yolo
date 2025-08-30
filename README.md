# Tooth-Detection-Using-Yolo
This repository contains the complete workflow for detecting and numbering teeth in dental images using YOLO (Ultralytics YOLOv8/YOLOv11). The project is based on a dataset of ~500 annotated intraoral images with FDI numbering.

YOLOv11 Object Detection - Training Guide
========================================

This project uses the Ultralytics YOLOv8 model for object detection.

SETUP INSTRUCTIONS
------------------

1. (Optional) Create a virtual environment:

   For Linux/macOS:
       python3 -m venv venv
       source venv/bin/activate

   For Windows:
       python -m venv venv
       venv\Scripts\activate

2. Install dependencies:

       pip install -r requirements.txt

3. (Optional but Recommended) Install PyTorch with GPU support:

   Visit https://pytorch.org/get-started/locally/ for your specific system.
   Example (for CUDA 11.8 users):

       pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

4. Download a pretrained YOLOv8 model (if not already):

       from ultralytics import YOLO
       model = YOLO("yolov8n.pt")  # or yolov8s.pt, yolov8m.pt, yolov8x.pt

5. Train the model:

       model.train(
           data='data.yaml',
           epochs=50,
           imgsz=640,
           batch=8
       )

6. (Optional) Run inference after training:

       results = model('path/to/image.jpg')
       results.show()

DATA FORMAT
-----------

The 'data.yaml' file should look like this:

    path: ./dataset
    train: images/train
    val: images/val

    nc: 2  # Number of classes
    names: ['class1', 'class2']

COMMON ISSUES
-------------

- CUDA Out of Memory:
    Reduce batch size or image size (imgsz), or use a smaller model like yolov8n.pt

- Directory Not Empty:
    If deleting folders in code, use shutil.rmtree instead of os.rmdir

CREDITS
-------

- YOLOv8 by Ultralytics: https://github.com/ultralytics/ultralytics
