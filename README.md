# Pre-Delinquency Intervention Engine

AI-powered early warning system that predicts customer delinquency risk, detects financial stress signals, and recommends proactive interventions through a FastAPI backend and React dashboard.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![React](https://img.shields.io/badge/react-19.2.0-blue.svg)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Project Structure](#project-structure)
- [Model Details](#model-details)
- [Contributing](#contributing)

## 🌟 Overview

The Pre-Delinquency Risk Engine is a proactive financial risk management system that analyzes customer behavior patterns to identify early warning signals of potential delinquency. By detecting financial stress before it escalates, the system enables timely interventions that can prevent defaults and improve customer outcomes.

### Key Capabilities

- **Real-time Risk Scoring**: Instant delinquency probability calculation based on behavioral indicators
- **Automated Stress Detection**: AI-powered classification of financial stress levels (Severe, Moderate, Stable)
- **Smart Intervention Routing**: Priority-based action recommendations (P1/P2/P3)
- **Comprehensive Monitoring**: Track active interventions, performance metrics, and team activities
- **Interactive Dashboard**: Modern, dark-mode enabled UI with real-time visualizations

## ✨ Features

### 🔍 Risk Assessment
- Machine learning-based probability prediction
- Multi-factor stress level detection
- Dynamic risk band assignment (High/Medium/Low)
- Business rule engine for policy enforcement

### 📊 Monitoring & Analytics
- Active interventions tracking
- Intervention success rate analysis
- Real-time activity feed
- Team performance metrics
- Risk distribution visualization
- Trend analysis and forecasting

### 🎨 User Interface
- Responsive React-based dashboard
- Dark mode support with theme switching
- Interactive charts powered by Chart.js
- Real-time data updates
- Intuitive navigation and filtering

### 🚀 API Integration
- RESTful FastAPI backend
- CORS-enabled for cross-origin requests
- JSON-based request/response
- Health check endpoints

## 🏗️ Architecture

```
┌─────────────────┐
│   React UI      │  ← User Interface (Vite + React + TailwindCSS)
└────────┬────────┘
         │ HTTP/REST
┌────────▼────────┐
│   FastAPI       │  ← API Layer (CORS, routing, validation)
└────────┬────────┘
         │
┌────────▼────────┐
│ Decision Engine │  ← Business Logic (stress detection, rules)
└────────┬────────┘
         │
┌────────▼────────┐
│   ML Model      │  ← Trained Classifier (scikit-learn)
└─────────────────┘
```

## 🛠️ Tech Stack

### Backend
- **Python 3.8+**
- **FastAPI** - Modern web framework for building APIs
- **scikit-learn** - Machine learning model training and prediction
- **pandas** - Data manipulation and analysis
- **joblib** - Model serialization

### Frontend
- **React 19.2** - UI framework
- **Vite** - Build tool and dev server
- **TailwindCSS 4.1** - Utility-first CSS framework
- **Chart.js** - Data visualization
- **Axios** - HTTP client

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- Node.js 16 or higher
- npm or yarn

### Backend Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Shaunak-8/pre-delinquency-intervention-engine.git
   cd pre-delinquency-intervention-engine
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Python dependencies**
   ```bash
   pip install fastapi uvicorn joblib pandas scikit-learn pydantic
   ```

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

## 🚀 Usage

### Running the Backend

1. **Start the FastAPI server**
   ```bash
   # From project root
   uvicorn api:app --reload --port 8000
   ```

   The API will be available at `http://localhost:8000`

2. **Access API documentation**
   - Swagger UI: `http://localhost:8000/docs`
   - ReDoc: `http://localhost:8000/redoc`

### Running the Frontend

1. **Start the development server**
   ```bash
   # From frontend directory
   npm run dev
   ```

   The UI will be available at `http://localhost:5173` or `http://localhost:5174`

2. **Build for production**
   ```bash
   npm run build
   ```

## 📡 API Documentation

### Health Check
```http
GET /
```

**Response:**
```json
{
  "message": "Pre-Delinquency Model API is running"
}
```

### Score Customer
```http
POST /score
```

**Request Body:**
```json
{
  "week": 4,
  "avg_salary_delay": 3.5,
  "avg_liquidity_ratio": 0.85,
  "liquidity_trend": -1.2,
  "total_failed_autodebits": 2,
  "avg_utility_delay": 5.0,
  "avg_atm_withdrawals": 8.5,
  "total_lending_app_txns": 3
}
```

**Response:**
```json
{
  "probability": 0.6234,
  "base_risk": "High",
  "detected_stress_type": "Severe",
  "final_risk": "High",
  "priority": "P1",
  "decision": "Immediate Intervention",
  "action": "Call within 24 hours",
  "monitoring_flag": false
}
```

## 📁 Project Structure

```
pre_delinquency_engine/
├── api.py                          # FastAPI application
├── decision_engine.py              # Risk scoring and business rules
├── train_model.py                  # Model training script
├── feature_engineering.py          # Feature creation pipeline
├── data_simulation.py              # Synthetic data generation
├── test_decision.py                # Unit tests
├── pre_delinquency_model.pkl       # Trained ML model
├── synthetic_pre_delinquency_data.csv
├── model_ready_data.csv
├── synthetic_weekly_data.csv
├── .gitignore
├── README.md
│
└── frontend/
    ├── src/
    │   ├── components/             # Reusable UI components
    │   │   ├── ActiveInterventionsTable.jsx
    │   │   ├── ActivityFeed.jsx
    │   │   ├── DebtIncomeChart.jsx
    │   │   ├── InterventionSuccessChart.jsx
    │   │   ├── ResultCard.jsx
    │   │   ├── RiskBySegmentChart.jsx
    │   │   ├── RiskChart.jsx
    │   │   ├── RiskDistributionChart.jsx
    │   │   ├── RiskTrendChart.jsx
    │   │   ├── ScoringForm.jsx
    │   │   ├── Sidebar.jsx
    │   │   ├── StatCard.jsx
    │   │   ├── StressSignalsChart.jsx
    │   │   ├── TeamPerformanceGrid.jsx
    │   │   └── WatchlistTable.jsx
    │   ├── pages/                  # Page components
    │   │   ├── Dashboard.jsx
    │   │   ├── LiveScoring.jsx
    │   │   ├── Monitoring.jsx
    │   │   └── RiskOverview.jsx
    │   ├── context/
    │   │   └── ThemeContext.jsx    # Dark mode theme provider
    │   ├── App.jsx
    │   ├── main.jsx
    │   └── index.css
    ├── package.json
    ├── vite.config.js
    ├── tailwind.config.js
    └── postcss.config.js
```

## 🤖 Model Details

### Input Features

| Feature | Description | Type |
|---------|-------------|------|
| `week` | Week number in observation period | Integer |
| `avg_salary_delay` | Average days of salary delay | Float |
| `avg_liquidity_ratio` | Average liquidity ratio | Float |
| `liquidity_trend` | Trend in liquidity over time | Float |
| `total_failed_autodebits` | Count of failed automatic payments | Integer |
| `avg_utility_delay` | Average days of utility payment delay | Float |
| `avg_atm_withdrawals` | Average ATM withdrawal frequency | Float |
| `total_lending_app_txns` | Count of payday loan transactions | Integer |

### Stress Detection Logic

**Severe Stress** (2+ conditions):
- Salary delay ≥ 5 days
- Failed autodebits ≥ 3
- Liquidity ratio < 0.8
- Lending app transactions ≥ 5
- Utility delay ≥ 7 days

**Moderate Stress** (3+ conditions):
- Salary delay ≥ 2 days
- Failed autodebits ≥ 1
- Liquidity ratio < 1.2
- Lending app transactions ≥ 2
- Utility delay ≥ 3 days

**Stable**: Does not meet severe or moderate criteria

### Risk Bands

- **High Risk**: Probability ≥ 50% → P1 Priority → Call within 24 hours
- **Medium Risk**: Probability 30-50% → P2 Priority → Call within 72 hours
- **Low Risk**: Probability < 30% → P3 Priority → Monitor weekly

### Business Rules

1. **Severe Stress Escalation**: Severe stress + probability > 20% → High Risk
2. **Liquidity Crisis**: Liquidity trend < -2 → High Risk
3. **Payment Failures**: Failed autodebits ≥ 3 → Escalate Low to Medium
4. **ATM Spike**: ATM withdrawals > 10 → Set monitoring flag

## 🎨 UI Pages

### Dashboard
- Overview of key metrics and trends
- Quick access to high-priority cases
- System health indicators

### Live Scoring
- Real-time customer risk assessment
- Interactive input form
- Instant results with recommendations

### Risk Overview
- Portfolio-wide risk distribution
- Segment analysis
- Trend visualization

### Monitoring
- Active interventions tracking
- Performance metrics
- Activity feed
- Team performance grid

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Team

**HEISENBUGS - VIT Pune**

## 🙏 Acknowledgments

- Built for early intervention in financial services
- Designed to improve customer outcomes and reduce defaults
- Powered by machine learning and behavioral analytics

---

**Note**: This is a demonstration project. For production use, ensure proper data security, model validation, and regulatory compliance.
