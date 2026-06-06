# 🐞 InsectDex – AI Insect Recognition & Learning App for Kids

![React](https://img.shields.io/badge/React-Frontend-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-Language-3178C6?logo=typescript)
![Capacitor](https://img.shields.io/badge/Capacitor-Android-119EFF?logo=capacitor)
![Supabase](https://img.shields.io/badge/Supabase-Database%20%26%20Storage-3ECF8E?logo=supabase)
![YOLO](https://img.shields.io/badge/YOLO-Object%20Detection-purple)
![Gemini](https://img.shields.io/badge/Gemini-AI%20Fallback-blue)
![MLOps](https://img.shields.io/badge/Cloud-MLOps-orange)

**InsectDex** is an AI-powered Android application that helps children identify insects from images, learn biological information, and collect discovered species like a digital insect Pokédex.

The project combines **mobile development**, **computer vision**, **cloud database**, **AI inference**, **gamification**, and a **Cloud MLOps pipeline** for continuously improving the recognition model with unknown insect data.

> Academic project for the course **Service-Oriented Architecture and Cloud Computing**  
> Industrial University of Ho Chi Minh City – Faculty of Information Technology

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Project Highlights](#-project-highlights)
- [Demo Screenshots](#-demo-screenshots)
- [My Role](#-my-role)
- [Key Features](#-key-features)
- [Supported Insects](#-supported-insects)
- [System Architecture](#-system-architecture)
- [AI Recognition Flow](#-ai-recognition-flow)
- [Cloud MLOps Pipeline](#-cloud-mlops-pipeline)
- [Database Design](#-database-design)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Results](#-results)
- [Limitations](#-limitations)
- [Future Work](#-future-work)
- [Team](#-team)

---

## 📖 Overview

InsectDex allows users to capture or upload an insect image from a mobile device. The image is processed by an AI recognition service, and the app returns the predicted insect, confidence score, and educational information such as Vietnamese name, English name, scientific name, habitat, ecological role, and life cycle.

The application is designed for children, parents, and teachers. Besides image recognition, it includes a collection system where users can save discovered insects, view their scan history, earn points, and explore insect information in a more interactive way.

A key technical component of this project is the **unknown insect improvement loop**. When the main YOLO model cannot confidently recognize an insect, the image can be stored in cloud storage, processed by AI-assisted labeling, converted into YOLO training data, and used to fine-tune future model versions.

---

## ✨ Project Highlights

- Built an Android-oriented insect recognition app using **ReactJS**, **TypeScript**, and **Capacitor**.
- Integrated a **YOLO-based object detection API** for insect recognition.
- Added **Gemini API fallback** to handle uncertain images, unknown insects, and non-insect inputs.
- Designed a **Supabase PostgreSQL schema** for users, insects, collections, observations, auto-labels, datasets, and model versions.
- Implemented a gamified learning experience with insect cards, collection history, user points, and exploration records.
- Designed a **Cloud MLOps pipeline** to process unknown insects, generate labels, create bounding boxes, export YOLO datasets, fine-tune candidate models, and manage model versions.
- Connected multiple cloud platforms including **Supabase**, **Hugging Face**, **Kaggle**, **Databricks**, and **GitHub Actions**.

---

## 📸 Demo Screenshots

> Add your real app screenshots to `docs/images/` and update the paths below.

| Home | Camera Scan | Recognition Result | Collection |
|---|---|---|---|
| ![Home](docs/images/app_home.png) | ![Camera](docs/images/app_camera.png) | ![Result](docs/images/app_result.png) | ![Collection](docs/images/app_collection.png) |

| System Architecture | Cloud MLOps Pipeline |
|---|---|
| ![System Architecture](docs/images/system_architecture.png) | ![MLOps Pipeline](docs/images/mlops_pipeline.png) |

---

## 👨‍💻 My Role

In this project, I was mainly responsible for the AI and Cloud MLOps side of the system:

- Designed the AI recognition workflow using **YOLO inference** and **Gemini fallback**.
- Designed the **unknown insect handling flow** for low-confidence or out-of-distribution images.
- Built and refined the **Supabase database schema** for observations, auto-labels, dataset versions, model versions, and promotion logs.
- Implemented the data processing logic from unknown image upload to auto-labeling and bounding box generation.
- Designed the **Cloud MLOps pipeline** using Supabase, GitHub Actions, Kaggle, Databricks, and Hugging Face.
- Prepared the YOLO dataset export and model fine-tuning workflow for candidate model updates.
- Wrote technical documentation, report content, architecture diagrams, and pipeline explanations.

---

## 🚀 Key Features

### 🔍 AI Insect Recognition

- Capture an image using the mobile camera.
- Upload an image from the device.
- Send image data to a cloud AI inference endpoint.
- Return predicted class, confidence score, and bounding box.
- Handle three result types:
  - Known insect.
  - Unknown insect.
  - No insect detected.

### 📚 Learning Module

Each insect profile can include:

- Vietnamese name.
- English name.
- Scientific name.
- Description.
- Habitat.
- Role in nature.
- Life cycle stages.
- Illustration or cartoon image.

### 🎮 Collection and Gamification

- Collect insects after successful recognition.
- Save captured insect photos to the user collection.
- Track discovered species.
- Award points for new discoveries and repeated scans.
- Show ranking based on total points.

### 🗺️ Exploration History

- Store recognition history in Supabase.
- Save photo path, insect ID, user ID, timestamp, and optional location.
- Support future map-based visualization of discovered insects.

### 🧠 Unknown Insect Handling

If the YOLO model is uncertain, the system can classify the image as an unknown insect. These images are stored in Supabase Storage under `unknown_pool` and can be processed later by the MLOps pipeline to improve the model.

---

## 🐜 Supported Insects

The initial YOLO model supports 10 common insect classes:

| No. | Class ID | English Name | Vietnamese Name |
|---:|---|---|---|
| 1 | `ant` | Ant | Kiến |
| 2 | `butterfly` | Butterfly | Bướm |
| 3 | `cockroach` | Cockroach | Gián |
| 4 | `dragonfly` | Dragonfly | Chuồn chuồn |
| 5 | `fly` | Fly | Ruồi |
| 6 | `grasshopper` | Grasshopper | Châu chấu |
| 7 | `honeybee` | Honeybee | Ong mật |
| 8 | `ladybug` | Ladybug | Bọ rùa |
| 9 | `mosquito` | Mosquito | Muỗi |
| 10 | `spider` | Spider | Nhện |

---

## 🏗️ System Architecture

```text
User
 │
 ▼
Android App
ReactJS + TypeScript + Capacitor
 │
 ▼
Cloud Services
 ├── Supabase Auth
 ├── Supabase Database
 ├── Supabase Storage
 ├── Hugging Face YOLO API
 └── Gemini API
 │
 ▼
AI & MLOps Layer
 ├── YOLO Inference
 ├── Gemini Semantic Validation
 ├── YOLO-World AutoBox on Kaggle
 ├── Databricks YOLO Dataset Export
 ├── Kaggle YOLO Fine-tuning
 └── Hugging Face Model Repository
```

The mobile app handles user interaction, image capture, result display, and collection features. Supabase stores structured data and uploaded images. YOLO performs the primary object detection task, while Gemini supports uncertain cases. The MLOps layer processes unknown insect images and prepares future model updates.

---

## 🤖 AI Recognition Flow

```text
User captures or uploads an image
        │
        ▼
Mobile app sends image to YOLO API
        │
        ▼
YOLO returns class + confidence
        │
        ├── High confidence
        │       ▼
        │   Display known insect result
        │
        └── Low confidence / no detection / error
                ▼
            Gemini validates image content
                │
                ├── Known insect candidate
                ├── Unknown insect
                └── No insect detected
```

YOLO is used as the main recognition model because it is suitable for object detection and returns both class predictions and object locations. Gemini is used as a fallback layer to reduce false positives and handle images that are outside the known training classes.

---

## 🔄 Cloud MLOps Pipeline

The MLOps pipeline is designed to improve the model using unknown insect images collected from real usage.

```text
Unknown insect image
        │
        ▼
Supabase Storage: observations/unknown_pool
        │
        ▼
GitHub Actions / Processing Script
        │
        ▼
Gemini auto-labeling
        │
        ▼
Supabase observations + auto_labels
        │
        ▼
Kaggle AutoBox with YOLO-World
        │
        ▼
Bounding box quality gate
        │
        ▼
approved_for_training data
        │
        ▼
Databricks exports YOLO dataset
        │
        ▼
Kaggle fine-tunes YOLO candidate model
        │
        ▼
Hugging Face stores model versions
        │
        ▼
Candidate model evaluation and promotion
```

### MLOps Data States

| Table | Status | Meaning |
|---|---|---|
| `observations` | `unknown_candidate` | New unknown image waiting for processing. |
| `observations` | `auto_labeled` | Image has a suggested label and waits for bbox or grouping. |
| `observations` | `need_review` | Image needs manual review due to uncertainty or detector failure. |
| `observations` | `approved_for_training` | Image has valid label and bbox and can be exported to YOLO dataset. |
| `observations` | `rejected` | Image is not suitable for training. |
| `auto_labels` | `suggested` | Label is suggested but not accepted yet. |
| `auto_labels` | `accepted` | Label and bounding box are accepted for training. |
| `auto_labels` | `outlier` | Image or bounding box is abnormal and should not be used directly. |

### Dataset Export Conditions

Only images that satisfy all conditions are exported into a YOLO dataset:

- `observations.mlops_status = 'approved_for_training'`
- `auto_labels.status = 'accepted'`
- `auto_labels.bbox_json IS NOT NULL`
- `observations.predicted_insect_id IS NOT NULL`
- Valid image path in Supabase Storage
- Minimum number of samples per class

---

## 🧱 Database Design

The system uses **Supabase PostgreSQL** as the main database and **Supabase Storage** for image files.

### Main Tables

| Table | Purpose |
|---|---|
| `users` | Stores user profile, role, avatar, and total points. |
| `insects` | Stores insect information and class metadata. |
| `insect_lifecycles` | Stores life cycle stages for each insect. |
| `collections` | Stores insects collected by users. |
| `observations` | Stores recognition records, uploaded images, prediction data, and MLOps status. |
| `auto_labels` | Stores suggested labels, confidence, bounding boxes, and label status. |
| `dataset_versions` | Stores metadata of exported YOLO datasets. |
| `model_versions` | Stores model version information and metrics. |
| `promotion_logs` | Stores candidate-to-production promotion history. |

The exported database schema is stored in:

```text
database/schema.sql
```

---

## 📦 Tech Stack

| Layer | Technologies |
|---|---|
| Mobile App | ReactJS, TypeScript, Capacitor, Android Studio |
| Authentication | Supabase Auth |
| Database | Supabase PostgreSQL |
| Storage | Supabase Storage |
| AI Detection | YOLO / Ultralytics |
| AI Fallback | Gemini API |
| Inference Hosting | Hugging Face API / Space |
| AutoBox | YOLO-World, Kaggle GPU |
| Dataset Export | Databricks |
| Model Training | Kaggle Notebook / GPU |
| Model Versioning | Hugging Face Model Repository |
| Automation | GitHub Actions, scheduled notebooks |
| Version Control | Git, GitHub |

---

## 📂 Project Structure

```text
InsectDex/
│
├── android/                    # Android project generated by Capacitor
├── public/                     # Static assets
├── src/                        # ReactJS application source code
│   ├── components/             # Reusable UI components
│   ├── pages/                  # App screens
│   ├── services/               # API, Supabase, and recognition services
│   ├── hooks/                  # Custom React hooks
│   └── utils/                  # Utility functions
│
├── mlops/                      # Cloud MLOps scripts and notebooks
│   ├── scripts/                # Unknown pool and auto-label processing scripts
│   ├── kaggle/                 # AutoBox and training notebooks/scripts
│   ├── databricks/             # YOLO dataset export notebooks/scripts
│   └── configs/                # Pipeline configuration files
│
├── database/
│   ├── schema.sql              # Exported Supabase schema
│   └── README.md               # Database notes
│
├── docs/
│   ├── images/                 # Screenshots and architecture diagrams
│   └── report.pdf              # Project report, if included
│
├── models/                     # Model references or local artifacts
├── package.json
├── capacitor.config.ts
├── vite.config.ts
└── README.md
```

---

## ⚙️ Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/NguyenViet2004/InsectDex.git
cd InsectDex
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file based on your local configuration:

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_YOLO_API_URL=your_yolo_api_url
VITE_GEMINI_API_KEY=your_gemini_api_key
```

> Do not expose service-role keys in frontend code. Sensitive credentials must be stored in secure environments such as GitHub Secrets, Kaggle Secrets, Databricks Secrets, or backend-only environment variables.

### 4. Run the app locally

```bash
npm run dev
```

### 5. Build the production app

```bash
npm run build
```

### 6. Sync with Android

```bash
npx cap sync android
```

### 7. Open Android project

```bash
npx cap open android
```

Then build and run the app using Android Studio.

---

## 📊 Model Evaluation Plan

Before promoting a candidate model to production, the model should be evaluated using:

- mAP@50
- mAP@50-95
- Precision
- Recall
- Confusion matrix
- Regression testing on old classes
- Manual review for new or uncertain classes

Candidate models should not replace the production model unless they pass the defined quality gate.

---

## ✅ Results

- Built an Android-oriented mobile app using ReactJS, TypeScript, and Capacitor.
- Implemented authentication and user session flow.
- Integrated Supabase Database and Storage.
- Integrated YOLO inference through a cloud API.
- Added Gemini fallback for uncertain recognition cases.
- Implemented insect collection, scan history, and point-based gamification.
- Designed a Supabase schema for both app features and MLOps metadata.
- Designed and tested a Cloud MLOps workflow for unknown insect data.
- Prepared the process for auto-labeling, bounding box generation, YOLO dataset export, candidate model fine-tuning, and model versioning.

---

## ⚠️ Limitations

- The initial model supports only a limited number of insect classes.
- Recognition accuracy depends on image quality, lighting, object size, camera angle, and background complexity.
- Some difficult images may return `unknown_insect` or require manual review.
- Auto-generated bounding boxes may be incorrect and should be reviewed before training.
- The MLOps pipeline was tested at demo scale and needs more validation before full production automation.
- Candidate models are not automatically promoted to production without evaluation.
- The system depends on cloud services, API quotas, and network connectivity.

---

## 🧭 Future Work

- Expand the dataset with more insect species and more diverse real-world images.
- Improve bounding box quality using stronger open-vocabulary detectors such as Grounding DINO or OWLv2.
- Build an admin dashboard for reviewing unknown images, labels, and bounding boxes.
- Add stricter model evaluation gates before promotion.
- Automate safe model promotion and rollback.
- Add quizzes, missions, badges, and more learning activities for children.
- Improve map-based exploration and species distribution visualization.
- Research lightweight on-device inference for faster recognition and reduced cloud dependency.

---

## 🔐 Security Notes

- Never commit `.env` files or secret keys.
- Never expose `SUPABASE_SERVICE_ROLE_KEY` in frontend code.
- Use GitHub Secrets, Kaggle Secrets, Databricks Secrets, or backend environment variables for private credentials.
- Apply Supabase Row Level Security policies where appropriate.
- Validate uploaded images before using them for model training.
- Avoid committing real user data or private storage files to the repository.

---

## 👥 Team

| Name | Student ID |
|---|---|
| Nguyễn Quốc Việt | 22715451 |
| Ngô Bình Xuyên | 22717111 |

**Supervisor:** Nguyễn Hữu Vũ  
**Course:** Service-Oriented Architecture and Cloud Computing  
**University:** Industrial University of Ho Chi Minh City

---

## 📜 License

This project is developed for educational and academic purposes.

---

## 🙏 Acknowledgements

The team would like to thank the Faculty of Information Technology at Industrial University of Ho Chi Minh City and the project supervisor for guidance and support during the development of InsectDex.
