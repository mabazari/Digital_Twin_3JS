# Sustainable Power Grid Digital Twin

## Project Overview

This project is an interactive 3D digital twin designed for the real-time monitoring and visualization of a sustainable power grid. It combines a Python Flask backend for data simulation with a sophisticated Three.js frontend to create an immersive, data-rich experience.

The simulation displays a 3D environment featuring key energy assets such as solar panels, a CHP plant, battery storage, a backup generator, a substation, and a central transmission pylon. These assets are interconnected with dynamic, animated power lines that visualize the flow of energy in real-time.

## Key Features

 Real-Time 3D Visualization A fully interactive 3D scene built with Three.js, allowing users to orbit, pan, and zoom.
 Dynamic Data Simulation A Python Flask backend serves simulated power data from `.csv` files, creating a continuous and realistic data stream.
 Animated Power Flow Power lines dynamically change color and animation speed to represent the direction and magnitude of energy transfer between assets and the grid.
 Interactive UI
     A persistent left-hand sidebar displays system-wide total power (P t) and quality (Q t) on live-updating charts.
     Clicking on any asset opens a right-hand details panel.
 Detailed Asset Information The details panel provides an in-depth description of the selected asset, its live data parameters, and individual performance charts for its P(t) and Q(t) values.
 Customizable Scenery The background is populated with multiple instances of building and shed models to create a more immersive and realistic environment.
 Multi-Language Support The entire UI can be toggled between English and Farsi.
 Theming Users can switch between a sleek dark mode and a clean light mode.

## Project Structure

The project is organized into a backend for data handling and a frontend for the user interface and visualization.


your-main-project-folder
│
├── 📂 backend
│   │
│   ├── 📂 data
│   │   ├── 📄 solar.csv
│   │   ├── 📄 chp.csv
│   │   ├── 📄 battery.csv
│   │   └── ... (and other asset data files)
│   │
│   └── 📄 app.py
│
└── 📂 sustainable-power-monitoring-system-main
│
├── 📂 assets
│   └── 📂 models
│       ├── 📄 solar_panel.glb
│       ├── 📄 building.glb
│       └── ... (and other .glb.gltf models)
│
├── 📂 css
│   ├── 📄 style.css
│   ├── 📄 themes.css
│   └── 📄 responsive.css
│
├── 📂 js
│   ├── 📄 main.js           (Application entry point)
│   ├── 📄 sceneManager.js   (Handles all Three.js logic)
│   ├── 📄 uiManager.js      (Manages all UI elements, sidebars, and charts)
│   ├── 📄 dataLogic.js      (Fetches and processes data from the backend)
│   ├── 📄 config.js         (Main configuration for models, layout, etc.)
│   └── 📄 localization.js   (Handles language translations)
│
└── 📄 index.html


## Technologies Used

 Backend
     Python
     Flask (for the web server and API)
 Frontend
     HTML5
     CSS3 (with Custom Properties for theming)
     JavaScript (ES6 Modules)
 3D Graphics & Visualization
     Three.js
     Chart.js
 Libraries
     Moment.js (for datetime handling)

## Setup and Running the Project

To run this project, you need to start the backend server, which will then serve the frontend application.

### Prerequisites

 Python 3 installed on your system.
 A modern web browser that supports WebGL (e.g., Chrome, Firefox, Edge).

### 1. Set Up the Backend

1.  Navigate to the `backend` directory in your terminal
    ```bash
    cd pathtoyour-projectbackend
    ```
2.  It is recommended to use a virtual environment
    ```bash
    python -m venv venv
    source venvbinactivate  # On Windows, use `venvScriptsactivate`
    ```
3.  Install the required Python packages
    ```bash
    pip install Flask Flask-Cors
    ```

### 2. Run the Server

1.  While still in the `backend` directory, run the `app.py` script
    ```bash
    python app.py
    ```
2.  The server will start, and you will see a message indicating it's running, typically on `http127.0.0.15000`.

### 3. Access the Application

1.  Open your web browser and navigate to the address provided by the Flask server
    [http127.0.0.15000](http127.0.0.15000)
2.  The 3D simulation should load and begin fetching data.

## How It Works

 `backendapp.py` This Flask application reads data row-by-row from the `.csv` files in the `data` folder. It creates an API endpoint (`apiassetsasset_iddata`) that the frontend calls to get the latest data point for each asset. It also serves the `index.html` file and all associated frontend assets.
 `jsconfig.js` This is the central configuration file for the frontend. It defines the positions, 3D model paths, and data parameters for each energy asset.
 `jssceneManager.js` This module is the heart of the visualization. It sets up the Three.js scene, loads all the 3D models (including the background scenery), implements the animated power lines, and handles user interaction like clicking on objects.
 `jsdataLogic.js` This module is responsible for fetching data from the backend API for each asset. It calculates the system-wide totals and maintains a history of data points for charting.
 `jsuiManager.js` This module controls the entire user interface. It builds and updates the sidebars, creates all the charts (both global and individual), and manages the display of live data values.
 `jslocalization.js` This file contains the text translations for English and Farsi, including the detailed essay descriptions for each asset.

## Customization

 Change Asset Positions To move the energy assets, simply edit the `THREE.Vector3` position values in the `energyResources` array in `jsconfig.js`.
 Add New Assets To add a new asset, add a new object to the `energyResources` array in `config.js`. You will need to provide a path to its 3D model, its position, and its data parameters.
 Modify Power Line Connections The power line connections are defined in the `initPowerLines` function in `jssceneManager.js`. You can change the waypoints to create different paths.
 Edit Descriptions The detailed text for each asset can be changed in the `translations` object in `jslocalization.js`.
 Change Scenery To adjust the background buildings, modify the `buildingPositions` and `shedPositions` arrays in the `createBackgroundScenery` function in `jssceneManager.js`. You can change their position, rotation, and scale.
