# 🐞 InsectDex – AI-Powered Insect Recognition & Learning App

## 📌 Overview

**InsectDex** is an AI-powered application designed to help users **identify, learn, and collect insects** through image recognition.
By simply capturing an image (from real life or books), the system detects the insect and provides detailed educational information.

This project combines **Computer Vision, Mobile Development, and Gamification** to create an interactive learning experience.

---

## 🎯 Objectives

* Build an AI model to recognize common insects from images
* Develop a mobile-friendly system for real-time insect scanning
* Provide educational content (life cycle, habitat, benefits/harms)
* Create a gamified collection system to enhance learning

---

## 🐜 Supported Insects (MVP)

* Ant
* Butterfly
* Cockroach
* Dragonfly
* Fly
* Grasshopper
* Honeybee
* Ladybug
* Mosquito
* Spider

---

## 🧠 Features

### 🔍 AI Recognition

* Detect insects from:

  * Camera input
  * Images (books, photos, real-world)
* Bounding box + label + confidence score

### 📚 Learning Module

Each insect includes:

* Scientific name
* Life cycle
* Habitat
* Benefits / Harms

### 🎮 Collection System

* Collect insects like a "Pokédex"
* Track discovered species
* Unlock achievements (future)

### 📱 Multi-platform (Planned)

* Mobile App (Flutter / React Native)
* Web Dashboard

### 🧊 Future Features

* AR visualization (3D insects)
* Quiz / learning games
* Multi-language support

---

## 🏗️ System Architecture

```
Mobile / Web App
        ↓
   Backend API (FastAPI)
        ↓
   AI Model Service (YOLO / RF-DETR)
        ↓
     Database
```

---

## 🤖 AI Model

* Models:

  * YOLO (baseline)
  * RF-DETR (experimental)
* Tasks:

  * Object Detection
* Output:

  * Label
  * Confidence
  * Bounding Box

---

## 📦 Tech Stack

* **AI / ML**: PyTorch, YOLO, RF-DETR
* **Backend**: FastAPI
* **Frontend**: React / Flutter
* **Database**: PostgreSQL / MongoDB
* **Deployment**: Docker
* **Data Analysis**: Databricks (planned)

---

## 📂 Project Structure

```
InsectDex/
│── data/               # Dataset (images, labels)
│── models/             # Trained models
│── backend/            # API server
│── ai_service/         # Inference service
│── frontend/           # Web / Mobile app
│── docs/               # Documentation
│── notebooks/          # Experiments (training, analysis)
```

---

## 🚀 Getting Started

### 1. Clone repository

```bash
git clone https://github.com/your-username/insectdex.git
cd insectdex
```

### 2. Setup environment

```bash
pip install -r requirements.txt
```

### 3. Run AI service

```bash
python app.py
```

### 4. Run backend

```bash
uvicorn main:app --reload
```

---

## 📊 Model Evaluation (Planned)

* mAP@50 / mAP@50-95
* Precision / Recall
* Confusion Matrix

---

## ⚠️ Challenges

* Detecting small insects
* Recognizing images from books (low quality, angle distortion)
* Handling unknown insect classes

---

## 🧭 Roadmap

* [x] Dataset preparation
* [ ] Model training & evaluation
* [ ] API deployment (Docker)
* [ ] Mobile app development
* [ ] Collection system
* [ ] AR / 3D features
* [ ] Gamification

---

## 🤝 Contribution

Contributions are welcome!
Feel free to open issues or submit pull requests.

---

## 📜 License

This project is for educational purposes.
