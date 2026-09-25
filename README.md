# EXONOVA — Exoplanet Detection & Visualization

**EXONOVA** is an interactive web-based exoplanet exploration and detection platform that combines **Machine Learning, React, TypeScript, Three.js, and Flask** to provide an immersive visualization of planetary systems and ML-based exoplanet classification.

The application allows users to explore simulated/available exoplanetary systems in an interactive 3D environment, search and filter planets, inspect scientific parameters, and use a trained machine-learning model to predict whether an astronomical observation corresponds to an exoplanet candidate.

---

## 🌌 Features

### 🔭 Interactive Exoplanet Visualization

* Interactive 3D planetary systems using **Three.js** and **React Three Fiber**
* Visual representation of stars and orbiting planets
* Interactive planets that can be selected to view detailed information
* Orbit animation controls
* Camera rotation, zoom, and pan controls
* Dynamic star colors based on stellar temperature
* Planet classification based on planetary radius

### 🪐 Planet Classification

The frontend categorizes planets into four major types:

* **Terrestrial**
* **Super-Earth**
* **Neptune-like**
* **Gas Giant**

Planet type is determined from the planetary radius.

### 🔎 Search & Filtering

Users can:

* Search systems by name
* Search planets by name
* Search using KOI numbers
* Filter planets by planetary type
* Filter systems by discovery method

### 📊 Scientific Planet Information

Selecting a planet displays detailed astronomical parameters including:

* Disposition Score
* Transit Epoch
* Transit Depth
* Stellar Surface Gravity
* TCE Planet Number
* Stellar Effective Temperature
* Transit Signal-to-Noise Ratio
* Equilibrium Temperature
* Right Ascension
* Declination
* Stellar Density
* Transit Duration
* Semi-Major Axis
* Impact Parameter
* Transit Epoch (BKJD)
* Stellar Radius
* Planet-Star Distance / Star Radius
* Kepler-band Magnitude
* Insolation Flux
* Planetary Radius

### 🤖 Machine Learning Prediction

The backend contains a trained ML model for exoplanet classification.

The model accepts **20 astronomical features** and returns:

* Prediction class
* Prediction confidence when supported by the model

The backend supports optional:

* Feature scaler
* Label encoder

### 🌓 Light & Dark Themes

The dashboard supports both:

* Dark space-themed interface
* Light interface

### ⚡ Responsive Interactive Interface

The frontend is built using React and TypeScript with reusable components for:

* Sidebar
* Planet visualization
* Planet details
* Loading screen
* Star field
* Interactive planets

---

# 🏗️ Technology Stack

## Frontend

| Technology        | Purpose                           |
| ----------------- | --------------------------------- |
| React             | User interface                    |
| TypeScript        | Type-safe development             |
| Vite              | Development server and build tool |
| Three.js          | 3D rendering                      |
| React Three Fiber | React integration for Three.js    |
| Drei              | Three.js helper components        |
| Axios             | API communication                 |
| Lucide React      | UI icons                          |
| Tailwind CSS      | Styling                           |

## Backend

| Technology   | Purpose                                      |
| ------------ | -------------------------------------------- |
| Python       | Backend programming                          |
| Flask        | REST API                                     |
| Flask-CORS   | Cross-origin requests                        |
| NumPy        | Numerical processing                         |
| Scikit-learn | Machine learning preprocessing/model support |
| Pickle       | Loading trained ML artifacts                 |

## Machine Learning

The backend uses a trained classification model stored as a serialized Python model.

Included model-related files:

```text
backend/
├── catboost_exoplanet_model3.pkl
├── label_encoder3.pkl
└── scaler3.pkl
```

---

# 📁 Project Structure

```text
EXODAC/
│
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   ├── catboost_exoplanet_model3.pkl
│   ├── label_encoder3.pkl
│   ├── scaler3.pkl
│   └── README.md
│
├── frontend/
│   ├── App.tsx
│   │
│   ├── components/
│   │   ├── DynamicStarSystem.tsx
│   │   ├── InteractivePlanet.tsx
│   │   ├── LoadingScreen.tsx
│   │   ├── Planet.tsx
│   │   ├── PlanetDetailModal.tsx
│   │   ├── Sidebar.tsx
│   │   └── StarField.tsx
│   │
│   ├── services/
│   │   └── exoplanetApi.ts
│   │
│   ├── types/
│   │   └── exoplanet.ts
│   │
│   ├── index.css
│   ├── main.tsx
│   └── vite-env.d.ts
│
├── index.html
├── package.json
├── eslint.config.js
└── .gitignore
```

---

# 🧠 Machine Learning Model

The backend prediction API uses 20 astronomical parameters as input.

### Input Features

```text
1.  koi_score
2.  koi_time0
3.  koi_depth
4.  koi_slogg
5.  koi_tce_plnt_num
6.  koi_steff
7.  koi_model_snr
8.  koi_teq
9.  ra
10. dec
11. koi_srho
12. koi_duration
13. koi_sma
14. koi_impact
15. koi_time0bk
16. koi_srad
17. koi_dor
18. koi_kepmag
19. koi_insol
20. koi_prad
```

These parameters describe characteristics of the observed star, transit event, orbital properties, and planetary properties.

---

# 🔄 Machine Learning Pipeline

The prediction process follows this general pipeline:

```text
Astronomical Input Data
        │
        ▼
Feature Extraction
        │
        ▼
Numerical Feature Array
        │
        ▼
Feature Scaling
        │
        ▼
Trained ML Model
        │
        ▼
Prediction
        │
        ▼
Prediction Confidence
```

If a scaler is available, the input data is transformed before being passed to the model.

If the trained model supports `predict_proba()`, the API also calculates the maximum class probability as the prediction confidence.

---

# 🚀 Getting Started

## Prerequisites

Make sure the following software is installed:

* **Node.js**
* **npm**
* **Python 3**
* **pip**

You can verify your installations with:

```bash
node --version
npm --version
python --version
pip --version
```

---

# 💻 Frontend Setup

Open a terminal in the project root.

Install the required Node.js dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Vite will provide a local development URL, normally similar to:

```text
http://localhost:5173
```

Open the displayed URL in your browser.

---

# 🐍 Backend Setup

Navigate to the backend directory:

```bash
cd backend
```

Create a Python virtual environment:

### Windows

```bash
python -m venv venv
```

Activate it:

```powershell
venv\Scripts\Activate.ps1
```

If PowerShell blocks script execution, you can use:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then activate the environment again:

```powershell
venv\Scripts\Activate.ps1
```

### Linux/macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## Install Backend Dependencies

```bash
pip install -r requirements.txt
```

The current backend requirements are:

```text
Flask 3.0.0
Flask-CORS 4.0.0
NumPy 1.26.2
Scikit-learn 1.3.2
```

---

# ▶️ Start the Flask Server

From the `backend` directory:

```bash
python app.py
```

The Flask backend runs on:

```text
http://localhost:5000
```

---

# 🔌 Backend API

## Health Check

### GET

```text
/api/health
```

Example:

```bash
curl http://localhost:5000/api/health
```

Example response:

```json
{
  "status": "healthy",
  "model_loaded": true,
  "scaler_loaded": true,
  "encoder_loaded": true
}
```

This endpoint can be used to verify whether the backend and ML artifacts have been loaded.

---

# 🤖 Exoplanet Prediction API

## POST

```text
/api/predict
```

The endpoint accepts the 20 astronomical features used by the model.

Example request:

```json
{
  "koi_score": 0.5,
  "koi_time0": 2454833.0,
  "koi_depth": 500.0,
  "koi_slogg": 4.5,
  "koi_tce_plnt_num": 1,
  "koi_steff": 5778,
  "koi_model_snr": 20.0,
  "koi_teq": 500,
  "ra": 290.0,
  "dec": 45.0,
  "koi_srho": 1.2,
  "koi_duration": 3.0,
  "koi_sma": 0.1,
  "koi_impact": 0.2,
  "koi_time0bk": 100.0,
  "koi_srad": 1.0,
  "koi_dor": 5.0,
  "koi_kepmag": 14.0,
  "koi_insol": 100.0,
  "koi_prad": 1.5
}
```

Example response:

```json
{
  "prediction": 2,
  "confidence": 0.95
}
```

According to the backend documentation:

```text
1 = Non-Exoplanet Star
2 = Exoplanet Detected
```

---

# 📡 Frontend–Backend Communication

The frontend uses Axios to communicate with the backend.

The API base URL is configured through:

```text
VITE_VERCEL_BACKEND_URL
```

The frontend currently uses:

```typescript
const API_BASE_URL =
  import.meta.env.VITE_VERCEL_BACKEND_URL ||
  'https://your-vercel-backend-url.vercel.app';
```

For local development, configure the frontend to point to:

```text
http://localhost:5000
```

---

# 🌟 Exoplanet Visualization

The visualization is implemented using:

```text
React
   │
   └── React Three Fiber
           │
           └── Three.js
```

Each system contains:

```text
Star
 │
 ├── Planet 1
 ├── Planet 2
 ├── Planet 3
 └── ...
```

The star's visual color is determined from its effective temperature.

### Stellar Temperature Classification

The application approximately maps stellar temperature to spectral classes:

```text
O → ≥ 30,000 K
B → ≥ 10,000 K
A → ≥ 7,500 K
F → ≥ 6,000 K
G → ≥ 5,200 K
K → ≥ 3,700 K
M → < 3,700 K
```

---

# 🪐 Planet Type Classification

The frontend determines the visual planet category using planetary radius:

```text
Radius < 1.5 Earth radii
        ↓
Terrestrial

1.5–2.5 Earth radii
        ↓
Super-Earth

2.5–6 Earth radii
        ↓
Neptune-like

≥ 6 Earth radii
        ↓
Gas Giant
```

This classification is used for visualization and filtering.

---

# 🎛️ Dashboard Controls

The dashboard provides several interactive controls.

### Search

Search for:

```text
System name
Planet name
KOI number
```

### Planet Type

Filter by:

```text
All Types
Terrestrial
Super-Earth
Neptune-like
Gas Giant
```

### Discovery Method

Filter systems based on their discovery method.

### Orbit Controls

Users can:

```text
Pause Orbits
Play Orbits
```

The Three.js camera also supports:

```text
Zoom
Pan
Rotate
```

### Theme

Switch between:

```text
Dark Mode
Light Mode
```

---

# 🧪 Mock Data / Fallback

The frontend includes fallback mock data if the exoplanet API request fails.

Example systems included in the fallback dataset include:

* Kepler-90
* TRAPPIST-1

This allows the visualization interface to continue displaying sample planetary systems even when the external API is unavailable.

---

# 📦 Model Files

The project contains the following serialized machine-learning artifacts:

```text
backend/
├── catboost_exoplanet_model3.pkl
├── label_encoder3.pkl
└── scaler3.pkl
```

These files represent the trained model and preprocessing artifacts included with the project.

> **Important:** The current `backend/app.py` expects model files at `backend/model/` with the names `model.pkl`, `scaler.pkl`, and `encoder.pkl`. If using the included `*_model3.pkl` files directly, either rename/copy them into the expected location or update the paths in `app.py`.

---

# ⚠️ Current Integration Notes

The repository contains some components from different stages of development.

### 1. Exoplanet API Endpoint

The frontend currently requests:

```text
/api/exoplanets
```

from:

```text
frontend/services/exoplanetApi.ts
```

However, the included Flask `app.py` currently defines:

```text
/api/predict
/api/health
```

and does not currently define:

```text
/api/exoplanets
```

Therefore, a production deployment should implement the `/api/exoplanets` endpoint or connect the frontend to the intended data source.

### 2. Model File Paths

The backend expects:

```text
backend/model/model.pkl
backend/model/scaler.pkl
backend/model/encoder.pkl
```

while the uploaded project contains:

```text
backend/catboost_exoplanet_model3.pkl
backend/scaler3.pkl
backend/label_encoder3.pkl
```

The filenames and paths should be aligned before deploying the ML prediction service.

### 3. Frontend Entry Path

The repository currently stores frontend source files under:

```text
frontend/
```

while the root `index.html` references:

```text
/src/main.tsx
```

A standard Vite structure would normally place the entry point under:

```text
src/main.tsx
```

or update `index.html` to reference the actual project location.

---

# 🔐 Security Considerations

The project is intended primarily as a demonstration/research application.

Before production deployment:

* Validate all API inputs.
* Avoid exposing sensitive model files unnecessarily.
* Configure CORS for trusted domains instead of unrestricted access.
* Disable Flask debug mode.
* Add authentication if the prediction API is private.
* Add rate limiting for public APIs.
* Validate numerical ranges for astronomical parameters.
* Use environment variables for deployment-specific configuration.

---

# 🛠️ Development Commands

## Frontend

Install dependencies:

```bash
npm install
```

Run development server:

```bash
npm run dev
```

Build production version:

```bash
npm run build
```

Preview production build:

```bash
npm run preview
```

Run ESLint:

```bash
npm run lint
```

Run TypeScript checking:

```bash
npm run typecheck
```

---

## Backend

Install dependencies:

```bash
pip install -r requirements.txt
```

Run server:

```bash
python app.py
```

Backend URL:

```text
http://localhost:5000
```

---

# 📚 Project Use Cases

EXONOVA can be used as a:

* College academic project
* Machine learning demonstration
* Astronomy visualization application
* Exoplanet exploration dashboard
* Full-stack development project
* ML API integration project
* Three.js / WebGL visualization project
* Research and educational prototype

---

# 🎯 Project Objectives

The main objectives of EXONOVA are:

1. Build an interactive platform for exploring exoplanetary systems.
2. Visualize astronomical data in an accessible 3D environment.
3. Present important scientific parameters for individual planets.
4. Apply machine learning to astronomical classification.
5. Provide an API for ML-based exoplanet prediction.
6. Combine frontend visualization with a Python ML backend.
7. Create an educational interface for understanding exoplanet observations.

---

# 🔮 Future Improvements

Potential improvements include:

* Implementing the `/api/exoplanets` backend endpoint.
* Connecting directly to an astronomical database/API.
* Integrating the included CatBoost model with the Flask application.
* Adding a dedicated prediction interface to the frontend.
* Displaying ML prediction results directly on planet details.
* Adding probability distributions for model predictions.
* Adding more confirmed planetary systems.
* Adding orbital-period visualization.
* Adding habitable-zone visualization.
* Adding planetary mass and density visualization.
* Adding historical discovery information.
* Adding real-time astronomical datasets.
* Improving mobile responsiveness.
* Adding user accounts and saved systems.
* Deploying frontend and backend independently.
* Adding automated model evaluation and monitoring.

---

# 👨‍💻 Development

EXONOVA is structured as a full-stack application:

```text
                ┌──────────────────────┐
                │      React UI        │
                │     TypeScript       │
                └──────────┬───────────┘
                           │
                           │ Axios / HTTP
                           ▼
                ┌──────────────────────┐
                │     Flask API        │
                │       Python         │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │ Machine Learning     │
                │       Model          │
                └──────────┬───────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │ Exoplanet Prediction │
                └──────────────────────┘
```

The visualization layer is powered by:

```text
React
  ↓
React Three Fiber
  ↓
Three.js
  ↓
Interactive 3D Exoplanet System
```

---

# 📄 License

No explicit license file is currently included in the repository.

If this project is intended for public distribution, add an appropriate license such as MIT, Apache-2.0, or another license suitable for the project's ownership and dependencies.

---

# 🌌 EXONOVA

**Exoplanet Detection & Visualization**

> Explore planetary systems. Visualize astronomical data. Apply machine learning to exoplanet detection.

