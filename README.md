# 🦅 AQUILA — Global Flood Intelligence Platform

**Real‑time flood monitoring · Causal intelligence · Predictive risk mapping · Open‑source**

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green?logo=fastapi)
![Leaflet](https://img.shields.io/badge/Leaflet-1.9+-yellow?logo=leaflet)
![Tailwind](https://img.shields.io/badge/Tailwind-3.0+-skyblue?logo=tailwindcss)
![License](https://img.shields.io/badge/License-MIT-orange)

---

## 🌍 Overview

**AQUILA** is a unified flood intelligence platform that answers not just **WHERE** a flood is, but **WHY** it happened and **WHAT** comes next.

It combines:
- **Live flood tracking** from NASA EONET
- **Historical flood archives** with causal analysis
- **24–72 hour predictive risk assessment**
- **Real‑time simulation** of historical flood events
- **Telegram alerts** for last‑mile delivery
- **Flood Factors** — monsoon, cyclone, river, and GLOF intelligence

> 🧠 **Built for the world** — not just India. Global data sources, configurable regions, and scalable architecture.

---

## 🚀 Features

| Feature | Description |
| :--- | :--- |
| 🌊 **Live Floods** | Real‑time active flood events from NASA EONET + GDACS |
| 📜 **Historical Archives** | 1,000+ flood events with **Primary Cause** (Monsoon, Cyclone, GLOF, Dam Release, etc.) |
| 🔮 **Predict Risk** | Matches current conditions to historical patterns → risk score + recommendation |
| 🎮 **60‑Second Simulation** | Replays any historical flood in real‑time — shows risk progression |
| 📈 **Real‑Time Graphs** | 6 live charts: river levels, alerts by state, event frequency, rainfall, cause breakdown, alert feed |
| 🌧️ **Flood Factors** | Animated paths for monsoons, cyclones, rivers, and GLOF events |
| 🤖 **Telegram Alerts** | Instant notifications to communities — works without internet |
| 📊 **Rich Per‑Event Dossier** | Time‑series charts, computed metrics, similar events, and export |
| 🌍 **Global Coverage** | Open data sources (NASA, GDACS, USGS, OpenStreetMap) — works anywhere |

---

## 🧱 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Backend** | FastAPI (Python) |
| **Frontend** | HTML + Tailwind CSS + Leaflet.js + Chart.js |
| **Maps** | OpenStreetMap (free, no API key) |
| **Data Sources** | NASA EONET, GDACS, USGS, OpenStreetMap |
| **Alerts** | Telegram Bot API |
| **Deployment** | Uvicorn / Docker / Railway / Heroku |

---

## 📊 Data Sources

| Source | Description | Coverage |
| :--- | :--- | :--- |
| **NASA EONET** | Live natural disaster events | Global |
| **GDACS** | Official disaster alerts | Global |
| **USGS** | Earthquake data (flood triggers) | Global |
| **OpenStreetMap** | River networks, terrain | Global |
| **IFI v3.0** | Historical flood events + causes | India (extensible) |
| **IMD / Mausam** | Rainfall data (optional) | India |
| **Open-Meteo** | Flood API (future) | Global |

---

## 🗺️ Data Flow
┌─────────────────────────────────────────────────────────────────────────────┐
│                          AQUILA DATA FLOW                                  │
│                          "Global Flood Intelligence"                       │
└─────────────────────────────────────────────────────────────────────────────┘

                             ┌─────────────────┐
                             │                 │
                             │   USER REQUEST  │
                             │                 │
                             └────────┬────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         DATA INGESTION LAYER                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌────────────┐   ┌────────────┐   ┌────────────┐   ┌────────────┐       │
│   │   NASA     │   │   GDACS    │   │    IFI     │   │ OpenStreet │       │
│   │   EONET    │   │   Alerts   │   │   v3.0     │   │    Map     │       │
│   │  (Global)  │   │  (Global)  │   │  (History) │   │  (Rivers)  │       │
│   └─────┬──────┘   └─────┬──────┘   └─────┬──────┘   └─────┬──────┘       │
│         │                │                │                │               │
│         └────────────────┼────────────────┼────────────────┘               │
│                          │                │                                 │
│                          ▼                ▼                                 │
│               ┌─────────────────────────────────────┐                      │
│               │      DATA NORMALIZER & CACHE        │                      │
│               │       (Unified Event Schema)        │                      │
│               └─────────────────────────────────────┘                      │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PROCESSING LAYER (FastAPI)                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                    │
│   │  Historical  │  │   Pattern    │  │    Risk      │                    │
│   │  Correlator  │─▶│   Matcher    │─▶│  Calculator  │                    │
│   │  (By Cause)  │  │ (Current vs  │  │ (Severity +  │                    │
│   │              │  │  Historical) │  │  Probability)│                    │
│   └──────────────┘  └──────────────┘  └──────────────┘                    │
│                                                                             │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                    │
│   │   Timeline   │  │    Alert     │  │  Simulation  │                    │
│   │   Aggregator │  │   Generator  │  │   Engine     │                    │
│   │  (Year/State)│  │ (Telegram,   │  │  (Replay)    │                    │
│   │              │  │  SMS, Log)   │  │              │                    │
│   └──────────────┘  └──────────────┘  └──────────────┘                    │
│                                                                             │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                    │
│   │   Monsoon    │  │   Cyclone    │  │    GLOF      │                    │
│   │   Tracker    │  │   Tracker    │  │   Tracker    │                    │
│   │  (Paths)     │  │  (Paths)     │  │  (Events)    │                    │
│   └──────────────┘  └──────────────┘  └──────────────┘                    │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                      PRESENTATION LAYER (Frontend)                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────┐      │
│   │                        WEB DASHBOARD                             │      │
│   ├─────────────────────────────────────────────────────────────────┤      │
│   │                                                                 │      │
│   │   ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐          │      │
│   │   │  LIVE   │  │ARCHIVES │  │ FACTORS │  │ GRAPHS  │          │      │
│   │   │  Floods │  │History  │  │Monsoon  │  │Real-time│          │      │
│   │   └─────────┘  └─────────┘  └─────────┘  └─────────┘          │      │
│   │                                                                 │      │
│   │   ┌─────────────────────────────────────────────────────────┐  │      │
│   │   │              LEAFLET MAP (OpenStreetMap)                │  │      │
│   │   │  - Live Pings (Red/Orange)                             │  │      │
│   │   │  - Historical Pins (Color-coded by Cause)              │  │      │
│   │   │  - Animated Paths (Monsoon, Cyclones, GLOF)           │  │      │
│   │   │  - River Network (Thickness = Impact)                 │  │      │
│   │   └─────────────────────────────────────────────────────────┘  │      │
│   │                                                                 │      │
│   │   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐        │      │
│   │   │  Left Panel  │  │  Details     │  │  Graphs      │        │      │
│   │   │  - Filters   │  │  Drawer      │  │  Panel       │        │      │
│   │   │  - Stats     │  │  - Cause     │  │  - 6 Charts  │        │      │
│   │   │  - Timeline  │  │  - Metrics   │  │  - Live Feed │        │      │
│   │   └──────────────┘  └──────────────┘  └──────────────┘        │      │
│   └─────────────────────────────────────────────────────────────────┘      │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                       OUTPUT & ALERTS LAYER                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                    │
│   │   TELEGRAM   │  │   EXPORT     │  │   SIMULATE   │                    │
│   │   BOT        │  │   REPORTS    │  │   FLOOD      │                    │
│   │   (Alerts)   │  │   (PDF/CSV)  │  │   (Replay)   │                    │
│   └──────────────┘  └──────────────┘  └──────────────┘                    │
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────┐      │
│   │                    LAST-MILE DELIVERY                            │      │
│   │   ┌─────────────────────────────────────────────────────────┐  │      │
│   │   │  SMS  │  Telegram  │  Email  │  Dashboard Notification  │  │      │
│   │   └─────────────────────────────────────────────────────────┘  │      │
│   └─────────────────────────────────────────────────────────────────┘      │
└─────────────────────────────────────────────────────────────────────────────┘



┌─────────────────────────────────────────────────────────────────────────────┐
│                          AQUILA 3-LAYER ARCHITECTURE                       │
└─────────────────────────────────────────────────────────────────────────────┘

╔═════════════════════════════════════════════════════════════════════════════╗
║                           LAYER 1: DATA INGESTION                          ║
╠═════════════════════════════════════════════════════════════════════════════╣
║                                                                             ║
║   ┌───────────────────────────────────────────────────────────────────┐    ║
║   │                     EXTERNAL DATA SOURCES                          │    ║
║   ├───────────────┬───────────────┬───────────────┬──────────────────┤    ║
║   │               │               │               │                  │    ║
║   │   NASA EONET  │    GDACS      │   IFI v3.0    │  OpenStreetMap   │    ║
║   │  (Live Floods)│ (Alerts)      │  (Historical) │    (Rivers)      │    ║
║   │               │               │               │                  │    ║
║   │  • Real-time  │  • Severity   │  • 1,006+     │  • River paths   │    ║
║   │  • Global     │  • Population │  • Primary    │  • Global        │    ║
║   │  • Free       │  • Global     │    Cause      │  • Free          │    ║
║   │               │               │  • India      │                  │    ║
║   └───────┬───────┴───────┬───────┴───────┬───────┴───────┬──────────┘    ║
║           │               │               │               │                ║
║           └───────────────┼───────────────┼───────────────┘                ║
║                           │               │                                ║
║                           ▼               ▼                                ║
║               ┌─────────────────────────────────────────────┐              ║
║               │              DATA NORMALIZER                │              ║
║               │  - Converts to Unified Event Schema        │              ║
║               │  - Caches in Memory                        │              ║
║               │  - Indexes by Cause, Year, Location        │              ║
║               └─────────────────────────────────────────────┘              ║
╚═════════════════════════════════════════════════════════════════════════════╝
                                      │
                                      ▼
╔═════════════════════════════════════════════════════════════════════════════╗
║                         LAYER 2: PROCESSING ENGINE                         ║
╠═════════════════════════════════════════════════════════════════════════════╣
║                                                                             ║
║   ┌───────────────────────────────────────────────────────────────────┐    ║
║   │                         FastAPI BACKEND                           │    ║
║   ├───────────────┬───────────────┬───────────────┬──────────────────┤    ║
║   │               │               │               │                  │    ║
║   │  HISTORICAL   │   PREDICT     │  SIMULATE     │   FACTORS        │    ║
║   │  CORRELATOR   │   ENGINE      │  ENGINE       │   ENGINE         │    ║
║   │               │               │               │                  │    ║
║   │  • Filter by  │  • Pattern    │  • Replay     │  • Monsoon       │    ║
║   │    Cause      │    Matching   │    historical │  • Cyclones      │    ║
║   │  • Filter by  │  • Risk       │    floods     │  • Rivers        │    ║
║   │    State      │    Calculation│  • Real-time  │  • GLOF          │    ║
║   │  • Filter by  │  • Confidence │    playback   │                  │    ║
║   │    Year       │    Score      │               │                  │    ║
║   │               │               │               │                  │    ║
║   └───────┬───────┴───────┬───────┴───────┬───────┴───────┬──────────┘    ║
║           │               │               │               │                ║
║           └───────────────┼───────────────┼───────────────┘                ║
║                           │               │                                ║
║                           ▼               ▼                                ║
║               ┌─────────────────────────────────────────────┐              ║
║               │            API ENDPOINTS                    │              ║
║               │  /historical  /live  /analyze  /simulate   │              ║
║               │  /factors/monsoon  /rivers  /cyclones      │              ║
║               └─────────────────────────────────────────────┘              ║
╚═════════════════════════════════════════════════════════════════════════════╝
                                      │
                                      ▼
╔═════════════════════════════════════════════════════════════════════════════╗
║                       LAYER 3: PRESENTATION & OUTPUT                       ║
╠═════════════════════════════════════════════════════════════════════════════╣
║                                                                             ║
║   ┌───────────────────────────────────────────────────────────────────┐    ║
║   │                         FRONTEND                                  │    ║
║   ├───────────────┬───────────────┬───────────────┬──────────────────┤    ║
║   │               │               │               │                  │    ║
║   │   MAP VIEW    │   DASHBOARD   │    GRAPHS     │   ALERTS         │    ║
║   │               │               │               │                  │    ║
║   │  • Leaflet.js │  • Left Panel │  • River      │  • Telegram Bot  │    ║
║   │  • OSM Tiles  │  • Filters    │    Levels     │  • SMS (future)  │    ║
║   │  • Color-     │  • Statistics │  • Alerts by  │  • Email         │    ║
║   │    coded pins │  • Event List │    State      │    (future)      │    ║
║   │  • Animated   │  • Timeline   │  • Frequency  │                  │    ║
║   │    paths      │    Slider     │  • Rainfall   │                  │    ║
║   │               │               │  • Cause      │                  │    ║
║   │               │               │    Breakdown  │                  │    ║
║   │               │               │  • Alert Feed │                  │    ║
║   └───────────────┴───────────────┴───────────────┴──────────────────┘    ║
╚═════════════════════════════════════════════════════════════════════════════╝


┌─────────────────────────────────────────────────────────────────────────────┐
│                      AQUILA USER INTERACTION FLOW                          │
└─────────────────────────────────────────────────────────────────────────────┘

                              ┌─────────────────┐
                              │                 │
                              │   USER OPENS    │
                              │   DASHBOARD     │
                              │                 │
                              └────────┬────────┘
                                       │
                                       ▼
                        ┌─────────────────────────┐
                        │                         │
                        │   SELECT MODE           │
                        │                         │
                        │   ⚡ LIVE  📜 ARCHIVES  │
                        │   🌧️ FACTORS           │
                        │                         │
                        └───────────┬─────────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
              ▼                     ▼                     ▼
     ┌────────────────┐  ┌────────────────┐  ┌────────────────┐
     │                │  │                │  │                │
     │  LIVE MODE     │  │  ARCHIVES MODE │  │  FACTORS MODE  │
     │                │  │                │  │                │
     │  • Show real-  │  │  • Show        │  │  • Select      │
     │    time flood  │  │    historical  │  │    factor      │
     │    pins from   │  │    data from   │  │                │
     │    NASA EONET  │  │    IFI v3.0    │  │  🌧️ Monsoon   │
     │                │  │                │  │  🌊 Rivers     │
     │  • Pulsing     │  │  • Filter by   │  │  🌀 Cyclones   │
     │    red/orange  │  │    Year        │  │  🧊 GLOF      │
     │    markers     │  │  • Filter by   │  │                │
     │                │  │    Cause       │  │  • Animated    │
     │                │  │  • Filter by   │  │    paths on    │
     │                │  │    State       │  │    map         │
     └───────┬────────┘  └───────┬────────┘  └───────┬────────┘
             │                   │                   │
             │                   │                   │
             └───────────────────┼───────────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────────┐
                    │                             │
                    │   INTERACT WITH MAP         │
                    │                             │
                    │   • Click pin → Detail      │
                    │     Drawer opens            │
                    │                             │
                    │   • Toggle Predict Risk     │
                    │     → Risk card appears     │
                    │                             │
                    │   • Click Simulate Flood    │
                    │     → Simulation starts     │
                    │                             │
                    └─────────────┬───────────────┘
                                  │
                                  ▼
                    ┌─────────────────────────────┐
                    │                             │
                    │   TAKE ACTION               │
                    │                             │
                    │   • Send Telegram Alert     │
                    │   • Export Report           │
                    │   • View Similar Events     │
                    │   • Share (future)          │
                    │                             │
                    └─────────────────────────────┘


╔══════════════════════════════════════════════════════════════════════════════╗
║                          DATA FLOW LEGEND                                   ║
╚══════════════════════════════════════════════════════════════════════════════╝

  ┌────────────────────────────────────────────────────────────────────────────┐
  │                               SYMBOLS                                      │
  ├────────────────────────────────────────────────────────────────────────────┤
  │                                                                             │
  │   ┌─────────────────────────────────────────────────────────────────┐       │
  │   │  ┌─────┐    Data Source (External API / File)                    │       │
  │   │  │ API │                                                         │       │
  │   │  └──┬──┘                                                         │       │
  │   │     │                                                             │       │
  │   │     ▼                                                             │       │
  │   │  ┌──────────┐    Processing Engine (Business Logic)              │       │
  │   │  │  Engine  │                                                     │       │
  │   │  └──────────┘                                                     │       │
  │   │     │                                                             │       │
  │   │     ▼                                                             │       │
  │   │  ┌──────────┐    Database / Cache (Memory/File)                  │       │
  │   │  │  Cache   │                                                     │       │
  │   │  └──────────┘                                                     │       │
  │   │     │                                                             │       │
  │   │     ▼                                                             │       │
  │   │  ┌──────────┐    Output / Presentation Layer                     │       │
  │   │  │   UI     │                                                     │       │
  │   │  └──────────┘                                                     │       │
  │   │                                                                     │       │
  │   │  ──────►    Data Flow Direction                                    │       │
  │   │  ◄──────    Request / Response Flow                               │       │
  │   │  │          │    Parallel / Concurrent Flow                        │       │
  │   │  │          │                                                      │       │
  │   │  ┌────────┐                                                      │       │
  │   │  │  NOTE  │    Important Note / Comment                           │       │
  │   │  └────────┘                                                      │       │
  └────────────────────────────────────────────────────────────────────────────┘

╔══════════════════════════════════════════════════════════════════════════════╗
║                     AQUILA DATA FLOW - QUICK REFERENCE                      ║
╚══════════════════════════════════════════════════════════════════════════════╝

  ┌────────────────────────────────────────────────────────────────────────────┐
  │  STEP 1: DATA INGESTION                                                    │
  │  ┌────────────────────────────────────────────────────────────────────┐   │
  │  │  NASA EONET ──►  Live Flood Events                                 │   │
  │  │  GDACS       ──►  Official Alerts                                 │   │
  │  │  IFI v3.0    ──►  Historical Data + Causes                        │   │
  │  │  OSM         ──►  River Networks                                  │   │
  │  └────────────────────────────────────────────────────────────────────┘   │
  │                                   │                                        │
  │                                   ▼                                        │
  │  STEP 2: PROCESSING                                                       │
  │  ┌────────────────────────────────────────────────────────────────────┐   │
  │  │  Correlator  ──►  Pattern Matching                                │   │
  │  │  Risk Calc   ──►  Risk Score (Low → Severe)                       │   │
  │  │  Alert Gen   ──►  Telegram Alerts                                 │   │
  │  │  Sim Engine  ──►  60-Second Replay                                │   │
  │  │  Factors     ──►  Monsoon, Cyclones, GLOF                         │   │
  │  └────────────────────────────────────────────────────────────────────┘   │
  │                                   │                                        │
  │                                   ▼                                        │
  │  STEP 3: PRESENTATION                                                     │
  │  ┌────────────────────────────────────────────────────────────────────┐   │
  │  │  MAP         ──►  Pins, Animated Paths, River Networks             │   │
  │  │  DASHBOARD   ──►  Filters, Stats, Timeline, Event List             │   │
  │  │  GRAPHS      ──►  6 Real-Time Charts + Live Feed                  │   │
  │  │  DETAIL      ──►  Cause, Metrics, Similar Events                  │   │
  │  └────────────────────────────────────────────────────────────────────┘   │
  │                                                                             │
  │  OUTPUT: Users get early warnings, causal intelligence, and predictive     │
  │          risk assessment - ALL FOR FREE.                                   │
  └────────────────────────────────────────────────────────────────────────────┘
  
