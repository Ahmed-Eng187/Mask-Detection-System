Markdown
# 😷 Face Mask Detection API (v2.0)

A production-ready Deep Learning Face Mask Detection system built using **PyTorch**, **FastAPI**, and **Streamlit**. The project leverages **MobileNetV2 Transfer Learning** to classify faces into **WithMask** (✅ Allowed Entry) or **WithoutMask** (❌ Access Denied), featuring fully containerized services and an optimized image processing pipeline.

---

## 🚀 Key Features

* **Dual-Core Architecture:** High-performance REST API backend powered by **FastAPI** coupled with a modern cyberpunk UI frontend powered by **Streamlit**.
* **Advanced Computer Vision:** Automatic face detection, multi-face localization, and precision cropping using **OpenCV** before running neural inference.
* **Lightweight Deep Learning:** Powered by a customized **MobileNetV2** architecture optimized for edge devices, ultra-low latency, and real-time computer vision tasks.
* **Production-Ready MLOps:** Fully dockerized deployment infrastructure supporting simultaneous multi-port routing (`8000` & `8501`).
* **Automated QA Testing Suite:** Includes comprehensive test scenarios (invalid files, empty requests, file compatibility, and performance benchmarking).
* **Real-Time Predictions:** Support for both secure image file uploads and real-time live webcam capture pipelines.

---

## 🛠️ Tech Stack & Dependencies

* **Deep Learning Framework:** PyTorch, Torchvision
* **API Development:** FastAPI, Uvicorn, Python-Multipart, Requests
* **Dashboard & Web UI:** Streamlit, Pillow, NumPy
* **Computer Vision Processing:** OpenCV (`opencv-python-headless`)
* **Infrastructure Layer:** Docker, Containerization Utilities

---

## 🖼️ Image Processing Pipeline

To guarantee maximum inference precision, every uploaded frame passes through the following lifecycle:
1. **Face Detection:** OpenCV Haar Cascade algorithm localizes the facial region.
2. **Auto-Cropping:** Isolates the detected face bounding box to eliminate background noise.
3. **CLAHE Enhancement:** Contrast Limited Adaptive Histogram Equalization normalizes illumination inconsistencies.
4. **Tensor Conversion:** Resizes to $224 \times 224$ pixels, converts to PyTorch floating tensors, and applies standard normalization matrices.
5. **Inference Execution:** Forward pass runs under `torch.no_grad()` optimization block using MobileNetV2.

---

## 📊 API Endpoints Specification

### 🟢 `GET /`
Returns the global API deployment status.
```json
{
  "message": "Face Mask Detection API is running",
  "docs": "/docs"
}
🔵 GET /health
Returns infrastructure health metrics and active computing device (cpu / cuda).

JSON
{
  "status": "ok",
  "device": "cpu"
}
🔴 POST /predict
Accepts a multipart image stream (file=image.jpg) and returns probability classifications.

JSON
{
  "status": "mask_on",
  "action": "Allow entry",
  "class": "WithMask",
  "confidence": 0.9821,
  "probabilities": {
    "WithMask": 0.9821,
    "WithoutMask": 0.0179
  }
}
💻 Installation & Quickstart
Clone the Repository & Navigate:

Bash
git clone [https://github.com/Ahmed-Eng187/face-mask-detection.git](https://github.com/Ahmed-Eng187/face-mask-detection.git)
cd face-mask-detection
Initialize Environment & Dependencies:

Bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install strict package requirements
pip install -r requirements.txt
Launch Microservices (Local Development):

Bash
# Terminal 1: Run FastAPI Backend
python app.py

# Terminal 2: Run Streamlit Frontend Web App
streamlit run streamlit_app.py
Launch via Docker Containerization:

Bash
docker build -t mask-ai .
docker run -p 8000:8000 -p 8501:8501 mask-ai
📁 Project Structure
Plaintext
face-mask-detection/
│
├── Advanced_ML_Project.ipynb   # Deep learning training and evaluation notebook
├── app.py                      # FastAPI microservice backend core logic
├── streamlit_app.py            # Streamlit dashboard interface code
├── test_api.py                 # Automated unit and performance test suite
├── mask_detector.pth           # Evaluated and saved PyTorch model weights
├── requirements.txt            # Python environment dependencies matrix
├── Dockerfile                  # Application service multi-stage containerization
└── README.md                   # Enterprise system documentation
🏁 Conclusion
This system successfully demonstrates the integration of Deep Learning with lightweight architectures like MobileNetV2, proving that real-time computer vision classifiers can be built with minimal compute footprints, packaged via Docker, and prepared for robust scalable cloud native frameworks.

👤 Author
Ahmed Hamdy

🎯 Aspiring Machine Learning Engineer & Data Analyst

🛠️ NLP | Deep Learning | Computer Vision | MLOps | Cloud Engineering
