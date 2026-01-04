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

**GeoSocket-LSS** is a professional-grade, real-time location tracking service. Unlike traditional mapping projects, this application leverages **Service-Oriented Architecture (SOA)** and **WebSockets** to transform hardware-level GPS data into a live synchronization engine. 

The system features a clean separation between the backend orchestration and the reactive frontend, ensuring sub-second latency for location updates. It is designed for high-accuracy tracking, making it ideal for simulating fleet management or social proximity tools.

---

## 🚀 Key Features

* **⚡ Real-Time Broadcasting**: Uses **Socket.io 4.8.1** to sync coordinates across all clients instantly.
* **🎯 High-Precision Tracking**: Configured with hardware-level GPS scaling, including `enableHighAccuracy: true` and `maximumAge: 0` for pinpoint precision.
* **🧹 Smart Garbage Collection**: Automatically purges user markers from the map upon disconnection to optimize performance.
* **📱 Responsive Mapping**: Powered by **Leaflet.js** and **OpenStreetMap** for a smooth, fluid user experience.

---

## 🏗 System Architecture



The application follows a modular **Client-Server-Broadcast** pattern:

1.  **Frontend Logic (`script.js`)**: Captures high-accuracy GPS coordinates and manages the Leaflet map layer.
2.  **Orchestration Layer (`app.js`)**: An Express-based Node.js server that manages WebSocket connections and event relays.
3.  **Real-Time Layer (`Socket.io`)**: Handles the bi-directional communication pipe between the server and all active nodes.
4.  **Presentation Layer (`index.ejs`)**: Serves the dynamic UI structure and handles external library injections.

---

## 🛠 Tech Stack

* **Backend Environment**: Node.js 
* **Web Framework**: Express 5.1.0 
* **Real-Time Engine**: Socket.io 4.8.1 
* **Mapping API**: Leaflet.js
* **View Engine**: EJS (Embedded JavaScript) 
* **DevOps**: Nodemon 3.1.10 

---

## ⚡ Getting Started

### Prerequisites
* Node.js (v18 or newer) 
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
## 📡 Operational Logic
The system functions through a continuous event loop:
* **Emit**: The client's device captures GPS coordinates and emits a `send-location` event.
* **Relay**: The server receives the data, attaches the `socket.id`, and broadcasts a `recieve-location` event globally.
* **Render**: Active clients receive the broadcast and update the corresponding marker position on their Leaflet instance.
* **Disconnect**: Upon window closure, a `user-disconnect` event is emitted, prompting all nodes to remove the stale marker.
---
## 📸 Screenshots

Below is a visual guide to the application flow and its real-time tracking capabilities.

---

### 1. Establishing Connection
When you launch the application and navigate to `localhost:3000`, the server initializes. The browser tab title **"Real-Time Tracking"** confirms that the connection is active and the system is ready to process location data.

![Server Connection] ![3](https://github.com/user-attachments/assets/1c6ab236-d61b-4003-82dc-12eecb8a73d0)

---

### 2. Geolocation Authorization
To ensure privacy and functionality, the application requests permission to access your device's location. Users must select **"Allow while visiting the site"** to enable the Geolocation API to fetch coordinates for the map.

![Permission Request] ![1](https://github.com/user-attachments/assets/32fea9fd-8d44-4821-8f06-c89a3993bb4f)

---

### 3. Real-Time Map Rendering
Once authorized, your current position is instantly identified. The map, powered by **Leaflet.js** and **OpenStreetMap**, centers on your coordinates and places a blue marker to represent your live location.

![Active Tracking] ![2](https://github.com/user-attachments/assets/0b3f1a4c-3e2d-4bb7-8889-45f3e30b178a)

---

### 4. Multi-User Synchronization
The core feature of this project is the ability to track multiple users simultaneously. When a second user joins (via a different device or tab), both markers appear in real-time. 

* **Primary User:** Identified by a **Darker Blue** marker.
* **Secondary User:** Identified by a **Lighter Blue** marker for clear visual distinction.

![Multi-user Sync] ![4](https://github.com/user-attachments/assets/9f1e51f9-e29f-4bca-8cd0-f542b7fe6132)

---

### 🛠️ Technical Features
* **Socket.io:** Facilitates instant, bi-directional communication between the server and clients.
* **Leaflet.js:** Provides a smooth, interactive mapping interface.
* **Dynamic Markers:** Automatically updates, adds, or removes markers as users connect or disconnect.

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
