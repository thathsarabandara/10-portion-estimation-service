<div align="center">

# 📐 GlucoVision Portion Estimation Service

**The 3D geometry engine that estimates how much food is in a photo.**  
*Mask R-CNN · Monocular depth · Volume-to-weight · AR overlay · Open3D*

[![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=for-the-badge&logo=pytorch)](#)
[![FastAPI](https://img.shields.io/badge/FastAPI-Python-009688?style=for-the-badge&logo=fastapi)](#)
[![OpenCV](https://img.shields.io/badge/OpenCV-Vision-5C3EE8?style=for-the-badge&logo=opencv)](#)
[![CUDA](https://img.shields.io/badge/NVIDIA-CUDA-76B900?style=for-the-badge&logo=nvidia)](#)
[![Docker](https://img.shields.io/badge/Docker-GPU-2496ED?style=for-the-badge&logo=docker)](#)
[![Status](https://img.shields.io/badge/Status-In%20Development-f59e0b?style=for-the-badge)](#)

</div>

---

## 📌 Purpose

GlucoVision Portion Estimation answers: *"How many grams of this dish?"* It takes food bounding boxes from `09` and uses depth sensing + volume calculation to estimate portion weight — essential for accurate nutrition and glucose impact prediction. Separated from food recognition because RGB-D depth inference and 3D reconstruction are a different engineering domain from 2D classification.

> **Research basis:** Mask R-CNN (94.1% IoU), RGB-D depth estimation, volume-to-weight mapping, AR guidance.

---

## 📁 Project Structure

```
10-portion-estimation-service/
└── (Git repository initialised — structure to be scaffolded)
```

---

## ✨ Planned Features (by phase)

### Phase 1 — Segmentation
- [ ] Mask R-CNN instance segmentation (pixel-level food boundaries)
- [ ] FastAPI portion estimation endpoint

### Phase 2 — Depth & Volume
- [ ] MiDaS / DepthAnything v2 monocular depth estimation
- [ ] 3D point cloud → volume (cm³) → weight (g) conversion
- [ ] Reference object calibration (plate/spoon size)

### Phase 3 — AR & Integration
- [ ] AR overlay data for mobile ARCore/ARKit rendering
- [ ] RGB-D camera support (Intel RealSense / ESP32 ToF)
- [ ] MLflow model versioning

---

## 🚀 Getting Started

### Prerequisites

- Python ≥ 3.11, NVIDIA GPU, Docker & Docker Compose

### Setup (once scaffolded)

```bash
pip install -r requirements.txt
uvicorn main:app --reload --port 8005

# Or via Docker (GPU)
docker compose up --build
```

---

## 🏗️ Planned Tech Stack

| Layer | Technology |
|---|---|
| Framework | FastAPI (Python) |
| Segmentation | Mask R-CNN (Detectron2 / torchvision) |
| Depth Estimation | MiDaS / DepthAnything v2 |
| 3D Processing | Open3D |
| Image Processing | OpenCV, Pillow |
| Deep Learning | PyTorch 2.x |
| Model Registry | MLflow |
| GPU | NVIDIA CUDA |
| Containerisation | Docker + NVIDIA Container Toolkit |

---

## 🔗 Backend Dependencies

| Service | Interaction |
|---|---|
| `09` food-recognition | Bounding boxes + food_id per detected item |
| `05` api-gateway | Request routing + auth |
| `15` recommendation-engine | Consumes portion weight for meal planning |
| `12` glucose-prediction | Portion weight for glucose impact |

---

## 🧪 Testing (Planned)

```bash
pytest tests/model/      # Mask R-CNN IoU > 90%
pytest tests/volume/     # Volume error < 15% vs ground truth
pytest tests/api/        # Image → portion weight response
```

---

<div align="center">

*Part of the [GlucoVision Platform](../01-glucovision-platform-architecture) — 21-Repo AI Diabetes Management System*

</div>
