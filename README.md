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
## Screenshots
![1](https://github.com/user-attachments/assets/d054497a-db18-464c-bbb7-031a4a575e0b)
Before the tracking starts, the browser prompts for location access. You must click "Allow while visiting the site" to enable the application to fetch your coordinates and display them on the map.
![2](https://github.com/user-attachments/assets/4de710af-b699-433e-97bc-80ea7214aa51)
Once the permission is granted, the application identifies your current position. The map (powered by Leaflet/OpenStreetMap) centers on your coordinates and places a blue marker to represent your live location.
![3](https://github.com/user-attachments/assets/720f2777-1211-46df-9559-bdb6ad42b40d)
This image shows the browser address bar where the user enters localhost:3000. It also highlights the "Real-Time Tracking" tab title, indicating that the server is active and the application is ready to handle multiple connections.
![4](https://github.com/user-attachments/assets/a298422f-a1b4-4c86-b95e-5225b90d0828)
When the same link is opened in a different tab or on another device, the system tracks both instances simultaneously. As per your observation, the markers help you distinguish between users: the marker for the first session appears darker, while the marker for the second session appears lighter.


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
