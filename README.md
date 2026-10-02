# AVAR (Allan Variance) Web App 
**Analog Devices confidential and proprietary**

> **Note on Confidentiality:** This repository serves as overview of my project. Because this tool processes proprietary hardware data and utilizes internal mathematical algorithms, the source code is kept strictly confidential.

<div align="center">
  <br />
  <img src="https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB" alt="React" />
  &nbsp;&nbsp;&nbsp;➕&nbsp;&nbsp;&nbsp;
  <img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" alt="FastAPI" />
  <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python" />
  <br />
  <p><b>UI/UX DESIGN &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; API MATH COMPUTATION</b></p>
  <br />
</div>

## </> Project Overview
The AVAR Calculation Tool is a full-stack web application designed to automate the characterization and noise analysis of precision inertial sensors. By replacing time-intensive manual data evaluation with an interactive, web-based dashboard, this tool empowers hardware and systems engineers to rapidly visualize error bounds and extract critical operational metrics from large-scale sensor datasets.

This project bridges the gap between complex digital signal processing and intuitive user interfaces, demonstrating scalable software design from concept to deployment.

## </> System Architecture & Tech Stack
To ensure high performance during heavy statistical computations, the application was built using a decoupled, modern web architecture:

### Frontend (Client-Side)
**Framework:** React.js powered by Vite for rapid hot-reloading and optimized production builds.  
**UI/UX:** Component-based architecture ensuring a responsive, state-driven user experience.  
**Data Visualization:** Integrated advanced web charting libraries to render high-fidelity, interactive logarithmic plots (OADEV) that can handle thousands of data points without browser lag.

### Backend (Server-Side & Math Engine)
**Framework:** FastAPI (Python) for asynchronous, high-speed API routing and data handling.  
**Data Processing:** Leveraged `pandas` and `numpy` for efficient memory management and structural manipulation of massive raw data files.  
**Signal Processing:** Implemented a custom mathematical engine utilizing `allantools` to compute Overlapping Allan Deviation and calculate logarithmic derivatives.

### Deployment & DevOps
**Environment Management:** Engineered robust virtual environment (`.venv`) deployment pipelines to ensure seamless transferability across internal engineering workstations.  
**Standalone Compilation:** Successfully navigated complex dependency tracing, dynamic DLL linking (SSL, cryptography), and recursion limits to package the full-stack application into a portable, zero-dependency executable using PyInstaller.

## </> Key Features
- **Automated Data Ingestion & Smart Routing:** The backend dynamically parses raw sensor outputs, automatically detecting target axes (accelerometers vs. gyroscopes) to apply the correct physics unit conversions and scale factors.
- **Dual-Pass Mathematical Engine:** Developed a sophisticated two-tier processing loop:
  1. A high-resolution visual pass (1,000+ points) for UI rendering.
  2. A heavily filtered, smoothed mathematical pass that eliminates high-tau statistical noise (the "fishhook effect") to ensure accurate slope extraction.
- **Intelligent Parameter Extraction:** Automated the detection of fundamental inertial noise profiles by algorithmically isolating specific derivative slopes:
  * Velocity / Angle Random Walk (N)
  * Bias Instability (B)
  * Rate Random Walk (K)
- **Multi-DUT Batch Processing:** Built concurrent analysis capabilities to process 16-DUT (Device Under Test) arrays simultaneously, calculating population means and $1\sigma$ standard deviation envelopes for rapid batch validation.

