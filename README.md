# 🥬 GreenClassify v2

**Latest Technology Stack - Production Ready**

Modern vegetable classification system using deep learning with the latest packages and best practices.

## 🚀 What's New in v2

### Updated Technology Stack
- **TensorFlow 2.18+** - Latest stable version
- **NumPy 2.0+** - Improved performance
- **Flask 3.1+** - Latest web framework
- **Python 3.12+** - Modern Python features

### New Features
- ✅ Modern .keras model format support (with .h5 fallback)
- ✅ RESTful API endpoint (`/api/predict`)
- ✅ Health check endpoint
- ✅ Top 3 predictions display
- ✅ Low confidence warnings
- ✅ Drag & drop file upload
- ✅ Real-time image preview
- ✅ Responsive modern UI
- ✅ Better error handling

## 📦 Installation

### 1. Create Virtual Environment

```bash
cd collegeproject_v2
python -m venv venv
```

### 2. Activate Virtual Environment

**Windows:**
```bash
venv\\Scripts\\activate
```

**Linux/Mac:**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 🎯 Running the Application

```bash
python app.py
```

Then open: http://localhost:5000

## 🔧 API Usage

### Predict Endpoint

```bash
curl -X POST http://localhost:5000/api/predict \\
  -F "file=@path/to/image.jpg"
```

**Response:**
```json
{
  "vegetable": "Tomato",
  "confidence": 95.67,
  "all_predictions": {
    "Bean": 0.23,
    "Tomato": 95.67,
    ...
  }
}
```

### Health Check

```bash
curl http://localhost:5000/health
```

**Response:**
```json
{
  "status": "healthy",
  "model_loaded": true,
  "tensorflow_version": "2.18.0"
}
```

## 📁 Model File

Place your trained model in the project root:
- **Preferred:** `vegetable_model.keras` (new format)
- **Legacy:** `vegetable_model.h5` (fallback)

## 🌟 Supported Vegetables

1. Bean
2. Bitter Gourd
3. Bottle Gourd
4. Brinjal
5. Broccoli
6. Cabbage
7. Capsicum
8. Carrot
9. Cauliflower
10. Cucumber
11. Papaya
12. Potato
13. Pumpkin
14. Radish
15. Tomato

## 🚢 Deployment

### Render / Railway

```bash
# Files included:
# - requirements.txt
# - Procfile (for Gunicorn)
# - runtime.txt (Python version)
```

### Docker (Optional)

```bash
docker build -t greenclassify-v2 .
docker run -p 5000:5000 greenclassify-v2
```

## 📊 Project Structure

```
collegeproject_v2/
├── app.py              # Main Flask application
├── requirements.txt    # Dependencies
├── README.md          # Documentation
├── templates/         # HTML templates
│   ├── index.html
│   ├── prediction.html
│   └── result.html
├── static/            # Static files
├── uploads/           # Uploaded images
└── venv/             # Virtual environment
```

## 🎓 Academic Information

- **Project:** MCA Final Year
- **Version:** 2.0 (Latest Stack)
- **Framework:** TensorFlow 2.18+
- **Architecture:** ResNet50 Transfer Learning

## 📝 License

MIT License

---

**Made with ❤️ using latest technology**
