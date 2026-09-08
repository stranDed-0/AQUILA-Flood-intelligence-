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
