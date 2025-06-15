# Real-Time Multi-Class Object Detection and Recognition

This repository provides a **real-time object detection system** based on YOLOv3 and its variants, including a modified YOLOv3 configuration with hybrid logic and ResNet-style augmentation. The system is capable of detecting small and distant objects with high precision and is suitable for both image and video input.

## 🚀 Features

* Support for YOLOv1, YOLOv2, and YOLOv3 variants
* Real-time detection on images, videos, and live webcam
* High performance with small object detection capability
* Lightweight `tiny-yolo` and full `yolo-voc` models supported
* Hybrid detection model with ResNet-inspired enhancements

---

## 📅 Citation

If you use this work in your research, **please cite the following publication**:

> **A. A. Nayan**, J. Saha, A. N. Mozumder, K. R. Mahmud, A. K. A. Azad, "Real Time Multi-Class Object Detection and Recognition Using Vision Augmentation Algorithm," *International Journal of Advanced Science and Technology*, vol. 29, no. 05, pp. 14070–14083, 2020, doi: [10.48550/arXiv.2003.07442](https://doi.org/10.48550/arXiv.2003.07442)

---

## 📁 Repository Structure

```bash
├── detect.py              # Image detection script
├── video_demo.py          # Video file detection
├── cam_demo.py            # Live webcam detection
├── darknet.py             # Core YOLO model builder
├── preprocess.py          # Preprocessing utilities
├── util.py, bbox.py       # Utility functions, NMS, IOU, filters
├── cfg/                   # YOLO configuration files
├── yolov3_modified.cfg    # Custom YOLOv3 configuration
├── coco.names             # COCO label set (80 classes)
├── voc.names              # VOC label set (20 classes)
├── README.md              # Project documentation
```

---

## 🛠️ Setup Instructions

### 1. ⚙️ Create Python Environment (Miniconda)

```bash
conda create -n yolo_env python=3.8 -y
conda activate yolo_env
conda install pytorch torchvision torchaudio cpuonly -c pytorch
conda install opencv pandas matplotlib
```

> Optional: Use `pip install` for `opencv-python`, `pillow`, `argparse`, `pickle5` if needed.

### 2. 💾 Clone and Prepare Repository

```bash
git clone https://github.com/alakhirnayan/Customized_YOLO-V3_for_Real_Time_Small_Large_Object_Detection.git
cd Customized_YOLO-V3_for_Real_Time_Small_Large_Object_Detection
```

### 3. 📂 Download Dataset

#### PASCAL VOC:

```bash
wget https://pjreddie.com/media/files/VOCtrainval_11-May-2012.tar
wget https://pjreddie.com/media/files/VOCtrainval_06-Nov-2007.tar
mkdir VOC && cd VOC
tar -xvf ../VOCtrainval_11-May-2012.tar
tar -xvf ../VOCtrainval_06-Nov-2007.tar
```

#### COCO:

```bash
wget http://images.cocodataset.org/zips/train2017.zip
wget http://images.cocodataset.org/zips/val2017.zip
wget http://images.cocodataset.org/annotations/annotations_trainval2017.zip
unzip train2017.zip && unzip val2017.zip && unzip annotations_trainval2017.zip
```

---

## 🚀 Run the Model

### 1. Image Detection:

```bash
python detect.py \
    --images imgs/ \
    --det det/ \
    --cfg cfg/yolov3_modified.cfg \
    --weights yolov3.weights \
    --confidence 0.5 \
    --nms_thresh 0.4 \
    --reso 416
```

### 2. Video Detection:

```bash
python video_demo.py \
    --video path/to/video.avi \
    --cfg cfg/yolov3_modified.cfg \
    --weights yolov3.weights
```

### 3. Live Camera Detection:

```bash
python cam_demo.py --reso 416 --confidence 0.25 --nms_thresh 0.4
```

---

## 📅 Configurations

| Config File           | Description                        |
| --------------------- | ---------------------------------- |
| `tiny-yolo-voc.cfg`   | Lightweight model for edge devices |
| `yolo-voc.cfg`        | Full YOLOv2 trained on VOC         |
| `yolo.cfg`            | Base YOLO model                    |
| `yolov3_modified.cfg` | Custom YOLOv3 with ResNet logic    |

---

## 🌍 Class Labels

* `voc.names` → 20 classes (VOC 2007/2012)
* `coco.names` → 80 classes (MS COCO)

Ensure the correct label file is used in the code (`load_classes()` function).

---

## ✉️ Contact

For questions or collaborations, feel free to reach out to:

* **A. A. Nayan** - [asquiren@gmail.com](mailto:asquiren@gmail.com)

---

---

## 📄 License

This project is open-source and available under the MIT License.
