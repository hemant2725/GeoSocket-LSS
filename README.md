# 📍 GeoSocket-LSS | Location Synchronization Service

![Node.js](https://img.shields.io/badge/Node.js-v20%2B-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Socket.io](https://img.shields.io/badge/Socket.io-v4.8.1-010101?style=for-the-badge&logo=socketdotio&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-v5.1.0-000000?style=for-the-badge&logo=express&logoColor=white)
![License](https://img.shields.io/badge/License-ISC-blue?style=for-the-badge)

> **"A high-precision, real-time geospatial engine connecting users across a seamless digital map."**

---

## 📖 Table of Contents
- [About the Project](#-about-the-project)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Operational Logic](#-operational-logic)

---

## 💡 About the Project

[cite_start]**GeoSocket-LSS** is a professional-grade, real-time location tracking service. [cite_start]Unlike traditional mapping projects, this application leverages **Service-Oriented Architecture (SOA)** and **WebSockets** to transform hardware-level GPS data into a live synchronization engine. 

The system features a clean separation between the backend orchestration and the reactive frontend, ensuring sub-second latency for location updates. It is designed for high-accuracy tracking, making it ideal for simulating fleet management or social proximity tools.

---

## 🚀 Key Features

* [cite_start]**⚡ Real-Time Broadcasting**: Uses **Socket.io 4.8.1** to sync coordinates across all clients instantly.
* **🎯 High-Precision Tracking**: Configured with hardware-level GPS scaling, including `enableHighAccuracy: true` and `maximumAge: 0` for pinpoint precision.
* **🧹 Smart Garbage Collection**: Automatically purges user markers from the map upon disconnection to optimize performance.
* **📱 Responsive Mapping**: Powered by **Leaflet.js** and **OpenStreetMap** for a smooth, fluid user experience.

---

## 🏗 System Architecture



The application follows a modular **Client-Server-Broadcast** pattern:

1.  **Frontend Logic (`script.js`)**: Captures high-accuracy GPS coordinates and manages the Leaflet map layer.
2.  [cite_start]**Orchestration Layer (`app.js`)**: An Express-based Node.js server that manages WebSocket connections and event relays.
3.  [cite_start]**Real-Time Layer (`Socket.io`)**: Handles the bi-directional communication pipe between the server and all active nodes.
4.  **Presentation Layer (`index.ejs`)**: Serves the dynamic UI structure and handles external library injections.

---

## 🛠 Tech Stack

* [cite_start]**Backend Environment**: Node.js 
* [cite_start]**Web Framework**: Express 5.1.0 
* [cite_start]**Real-Time Engine**: Socket.io 4.8.1 
* **Mapping API**: Leaflet.js
* [cite_start]**View Engine**: EJS (Embedded JavaScript) 
* [cite_start]**DevOps**: Nodemon 3.1.10 

---

## ⚡ Getting Started

### Prerequisites
* [cite_start]Node.js (v18 or newer) 
* Active Internet Connection (for Leaflet CDN)

### Installation

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/your-username/GeoSocket-LSS.git](https://github.com/your-username/GeoSocket-LSS.git)
    cd GeoSocket-LSS
    ```

2.  **Install Dependencies**
    ```bash
    npm install
    ```

3.  **Run the Application**
    ```bash
    # Using Nodemon for development
    npx nodemon app.js
    ```

---

## 📂 Project Structure

```text
GeoSocket-LSS/
├── app.js              # Server orchestration & Socket management
├── package.json        # Dependency & Script manifest
├── .gitignore          # Git exclusion rules (node_modules)
├── public/             # Static Assets
│   ├── css/
│   │   └── style.css   # Map layout & UI styling
│   └── js/
│       └── script.js   # Geolocation & Leaflet logic
└── views/
    └── index.ejs       # Main Application Template
