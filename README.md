# 🛡️ SafeDrive AI

SafeDrive AI is a real-time driver monitoring system that uses Computer Vision and AI to detect driver fatigue and distraction. When a critical event is detected, the system automatically triggers an emergency response workflow through WhatsApp, sending:

* 📍 Live Location
* 📸 Three Incident Photos
* 🎥 Five-Second Video Recording
* 🚨 Emergency Alert Message

---

## 🏗️ Architecture

| Service            | Technology             | Purpose                                   |
| ------------------ | ---------------------- | ----------------------------------------- |
| Frontend Dashboard | Next.js                | Driver interface and monitoring dashboard |
| AI Backend         | FastAPI + MediaPipe    | Fatigue and distraction detection         |
| WhatsApp Bridge    | Node.js + WhatsApp Web | Emergency alert delivery                  |

---

## 📋 Prerequisites

Install the following before running the project:

* Node.js (v18 or higher)
* Python (3.10 – 3.12)
* FFmpeg

### Arch Linux

```bash
sudo pacman -S ffmpeg unzip
```

### Ubuntu / Debian

```bash
sudo apt install ffmpeg unzip
```

### Windows

Install FFmpeg and ensure it is available in your system PATH.

---

## 🚀 1. Start the WhatsApp Bridge

Navigate to the bridge directory and install dependencies:

```bash
cd whatsapp-bridge
npm install
```

Start the bridge:

```bash
node index.js
```

Scan the generated QR code using WhatsApp.

Expected output:

```text
WhatsApp Bridge READY
```

---

## 🧠 2. Start the AI Backend

Navigate to the backend directory:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment:

### Linux / macOS

```bash
source venv/bin/activate
```

### Windows

```powershell
venv\Scripts\activate
```

Install dependencies:

```bash
pip install fastapi uvicorn opencv-python numpy httpx
pip install mediapipe==0.10.13
```

Start the backend server:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Backend URL:

```text
http://localhost:8000
```

---

## 💻 3. Start the Frontend Dashboard

Navigate to the frontend directory:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

---

## 🎯 Usage

### Initial Setup

Provide:

* Driver Name
* Driver Phone Number
* Guardian Phone Number (`923XXXXXXXXX`)

Choose one of the following modes:

#### System Number

Uses a pre-configured WhatsApp account.

#### Personal Number

Allows the driver to link their own WhatsApp account.

---

### Start Monitoring

1. Click **Initialize**
2. Click **Start Driving**

The AI facial landmark mesh should appear on the driver's face.

---

### Emergency Triggers

#### Manual SOS

Click **Initiate SOS**.

#### Automatic SOS

An alert is triggered when fatigue conditions are detected.

---

## 📦 Emergency Packet

When an incident is detected, the guardian receives:

* Emergency alert message
* Live Google Maps location
* Three captured images
* Five-second incident video

---

## 🛠️ Troubleshooting

### Webcam Not Detected

Ensure no other application is currently using the webcam.

Examples:

* Zoom
* Discord
* OBS Studio
* Google Meet

---

### WhatsApp Video Delay

Video processing may take several seconds.

Wait until:

```text
✅ Video sent
```

appears in the bridge logs.

---

### QR Code Not Appearing

Verify that:

* The WhatsApp Bridge is running
* Port `3001` is available
* Localhost requests are not blocked

---

## 🔧 Technical Notes

* MediaPipe is pinned to `0.10.13` for compatibility and stability.
* FFmpeg is required for video processing before WhatsApp delivery.
* The WhatsApp Bridge uses the system-installed Chrome/Chromium browser.

---

## ✅ Status

* WhatsApp Bridge Running
* AI Backend Running
* Frontend Dashboard Running

SafeDrive AI is ready for monitoring.
