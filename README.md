# Cardiovascular Health Monitoring System

A comprehensive real-time cardiovascular health monitoring system that integrates IoT sensors, machine learning models, and a web-based dashboard for monitoring ECG, PPG, PCG, and blood pressure data.

## 🚀 Features

- **Real-time Sensor Monitoring**: ESP32-based sensors for ECG, PPG, and PCG data collection
- **Machine Learning Predictions**:
  - ECG disease classification (normal, atrial fibrillation, etc.)
  - PCG (heart sound) analysis for cardiac conditions
  - PPG-based blood pressure estimation using CNN-BiLSTM models
- **Web Dashboard**: React-based frontend with live charts, trend analysis, and health gauges
- **Multi-user Support**: Separate dashboards for patients, doctors, and administrators
- **Real-time Communication**: WebSocket integration for live data streaming
- **Firebase Integration**: Cloud database for data persistence and user management
- **Serial Communication**: Direct connection with ESP32 devices via serial ports

## 🏗️ Architecture

### Backend
- **Node.js/Express**: Main API server with Socket.io for real-time communication
- **Python/FastAPI**: ML inference servers for ECG, PCG, and BP predictions
- **Firebase Admin**: Database operations and authentication
- **SerialPort**: ESP32 sensor data acquisition

### Frontend
- **React + Vite**: Modern web application framework
- **Tailwind CSS**: Utility-first CSS framework
- **Recharts**: Data visualization library
- **React Router**: Client-side routing

### Hardware
- **ESP32 Microcontroller**: Sensor data collection and transmission
- **AD8232 ECG Sensor**: Electrocardiogram monitoring
- **MAX30102 PPG Sensor**: Photoplethysmography for heart rate and SpO2
- **INMP441 Microphone**: Phonocardiography for heart sounds

### Machine Learning Models
- **ECG Disease Classification**: TensorFlow Lite models optimized for edge deployment
- **PCG Analysis**: Deep learning models for heart sound classification
- **Blood Pressure Prediction**: CNN-BiLSTM neural network trained on PPG data

## 📋 Prerequisites

- Node.js (v16 or higher)
- Python 3.8+
- ESP32 development board
- Required sensors (AD8232, MAX30102, INMP441)
- Firebase project setup

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Cardiovascular-Health-Monitoring-System
   ```

2. **Backend Setup**
   ```bash
   cd backend
   npm install
   # Install Python dependencies for ML servers
   pip install fastapi uvicorn torch numpy pydantic
   ```

3. **Frontend Setup**
   ```bash
   cd ../frontend
   npm install
   ```

4. **Firebase Configuration**
   - Create a Firebase project
   - Add your Firebase config to `backend/.env` and `frontend/src/firebase.js`
   - Set up Firestore database

5. **ESP32 Setup**
   - Install Arduino IDE
   - Install ESP32 board support
   - Upload appropriate sketch from `esp32/` directory

## 🚀 Usage

1. **Start Backend Services**
   ```bash
   # Main Node.js server
   cd backend
   npm start

   # ML servers (in separate terminals)
   python ecg_disease_server.py
   python pcg_server.py
   python ppg_bp_server.py
   ```

2. **Start Frontend**
   ```bash
   cd frontend
   npm run dev
   ```

3. **Connect ESP32**
   - Upload sensor sketch to ESP32
   - Ensure serial connection is established

4. **Access Dashboard**
   - Open browser to `http://localhost:5173`
   - Login/Register as patient, doctor, or admin

## 📊 API Endpoints

### Main Server (Node.js)
- `GET /api/vitals` - Get patient vitals
- `POST /api/sensor-data` - Receive sensor data
- `GET /api/reports` - Generate health reports

### ML Servers (Python)
- `POST /predict/ecg` - ECG disease prediction
- `POST /predict/pcg` - PCG analysis
- `POST /predict/bp` - Blood pressure estimation

## 🔧 Configuration

### Environment Variables
Create `.env` file in backend directory:
```
FIREBASE_PROJECT_ID=your-project-id
FIREBASE_PRIVATE_KEY=your-private-key
SERIAL_PORT=COM3  # or /dev/ttyUSB0 on Linux
```

### Model Training
Jupyter notebooks for model retraining:
- `PPG_Retrain_With_Custom_Data.ipynb`
- `RetrainModel (1).ipynb`
- `Heart_Sound_Prediction.ipynb`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License - see the LICENSE file for details.

## 🙏 Acknowledgments

- ECG analysis models based on ECGFounder framework
- PPG BP prediction using CNN-BiLSTM architecture
- Heart sound classification using deep learning techniques

## 📞 Support

For questions or support, please contact the development team or open an issue in the repository.
