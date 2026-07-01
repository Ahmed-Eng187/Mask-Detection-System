Markdown# Face Mask Detection API 😷

A production-ready Deep Learning Face Mask Detection system built using PyTorch, FastAPI, and Streamlit.
The project uses MobileNetV2 Transfer Learning to classify faces into:
* ✅ **WithMask**
* ❌ **WithoutMask**

---

## 📂 Project Structure

```text
.
├── app.py                      # FastAPI backend
├── streamlit_app.py            # Streamlit frontend
├── mask_detector.pth           # Trained model weights
├── requirements.txt            # Python dependencies
├── Dockerfile                  # Docker configuration
├── start.sh                    # Linux/Mac startup script
├── run.bat                     # Windows startup script
├── test_api.py                 # Automated API testing
├── Advanced_ML_Project.ipynb   # Training notebook
└── README.md
🧠 Model ArchitectureThis project utilizes the MobileNetV2 lightweight CNN architecture, which is highly optimized for:Fast inference speedLow latency on edge devicesReal-time computer vision tasksFlawless 100% classification accuracy on balanced validation data  🖼️ Image Processing PipelineThe uploaded image passes through several structural preprocessing steps before prediction:Face Detection using OpenCV Haar CascadeFace Cropping around the detected regionCLAHE Enhancement for brightness and contrast normalizationResize to $224 \times 224$ pixelsTensor Conversion & NormalizationInference Prediction using MobileNetV2📦 Installation & Setup1. Clone the RepositoryBashgit clone [https://github.com/YOUR_USERNAME/face-mask-detection.git](https://github.com/YOUR_USERNAME/face-mask-detection.git)
cd face-mask-detection
2. Create a Virtual EnvironmentWindows:Bashpython -m venv venv
venv\Scripts\activate
Linux / Mac:Bashpython3 -m venv venv
source venv/bin/activate
3. Install DependenciesBashpip install -r requirements.txt
▶️ Running the ProjectRun FastAPI BackendBashpython app.py
Server URL: http://localhost:8000Interactive Swagger Docs: http://localhost:8000/docsRun Streamlit FrontendOpen another terminal tab, activate your virtual environment, and run:Bashstreamlit run streamlit_app.py
Frontend URL: http://localhost:8501🐳 Docker Deployment1. Build Docker ImageBashdocker build -t mask-ai .
2. Run ContainerBashdocker run -p 8000:8000 -p 8501:8501 mask-ai
📡 API EndpointsGET /Returns the API status.Response Example:JSON{
  "message": "Face Mask Detection API is running",
  "docs": "/docs"
}
GET /healthReturns server health and computing device information.Response Example:JSON{
  "status": "ok",
  "device": "cpu"
}
POST /predictUpload an image file for real-time mask detection.Request: Multipart form-data (Key: file)Response Example:JSON{
  "status": "mask_on",
  "action": "Allow entry",
  "class": "WithMask",
  "confidence": 1.0,
  "probabilities": {
    "WithMask": 1.0,
    "WithoutMask": 0.0
  }
}
🎨 Streamlit UI Features🌟 Futuristic cyberpunk design with neon animations📊 Real-time dynamic confidence tracking bars📷 Live webcam frame capture support🖼️ Drag-and-drop local image upload🧍 Auto face-crop toggle switch🖥️ Live container status monitoring🧪 Automated TestingRun the automated API test suite to verify endpoint stability:Bashpython test_api.py
Tests Covered:API health validationValid image prediction flowInvalid file and empty request handlingPNG/JPG format compatibilityLarge image resolution handling & performance benchmarks📈 Performance & OptimizationsArchitectural efficiency: Utilizes MobileNetV2 for rapid inference.Image Normalization: CLAHE preprocessing for optimal lightning adjustment.Speed: Implements Torch no_grad() to bypass gradient tracking during inference.Accuracy: Pre-inference face cropping isolates crucial facial features.🔐 Future Improvements[ ] JWT Authentication for API security[ ] Multi-face detection within a single frame[ ] Continuous video stream processing[ ] GPU acceleration support[ ] Database logging & History dashboard☁️ Deployment OptionsThis containerized application can be seamlessly deployed on:Render / RailwayAWS EC2 / Azure / Google CloudHugging Face Spaces🧑‍💻 DeveloperDeveloped by: Ahmed HamdyRole: AI & Data Science Student
