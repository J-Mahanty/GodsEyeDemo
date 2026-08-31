# GodsEye — City-Wide ANPR Intelligence Platform

## Smart India Hackathon 2026 | Team Prometheus
**Theme:** Transportation & Logistics · Software
**Problem Statement:** City-Wide AI Engine for Multi-Camera ANPR Trajectory Tracking and Urban Traffic Analytics

## About

Most cities already own traffic cameras — what they lack is a unified system that connects them. GodsEye bridges this gap by transforming isolated camera feeds into a city-wide intelligence layer.

Given a single license plate number, GodsEye can reconstruct the full trajectory of a vehicle across the city throughout the day. Simultaneously, it converts the same stream of plate reads into a real-time picture of how the entire city's traffic is moving.

## Core Components

- **ANPR Engine** — A neural plate reader (CRNN + BiGRU with CTC decoding) built to handle real-world conditions: monsoon, fog, night IR, glare, and far-lane captures. Falls back to a classical segment-and-classify engine when PyTorch is unavailable.
- **Burst Fusion** — Each capture produces 5 frames; reads are voted by CTC confidence to maximise accuracy.
- **Trajectory Reconstruction** — Spatial-temporal tracking over a GIS camera network (35 cameras across Kolkata), reconstructing full vehicle routes and detecting cloned plates.
- **Traffic Analytics** — Macro-level congestion scoring, road-level flow rates, and historical trend analysis derived from the same plate reads.
- **Real-Time Alert Queue** — Watchlist matching, clone detection, and anomaly alerts pushed to the control room dashboard.
- **Streamlit Dashboard** — A live control room with network visualisation, plate tracking, ANPR demo, and incident management.
- **FastAPI Backend** — REST API powering the live camera feed, incident injectors, and data access.

## Accuracy

- **73.1%** exact-plate accuracy across all conditions (burst path)
- **96.2%** on high-confidence reads that are stored
- Benchmarked across daylight, monsoon, fog, night IR, dusk, glare, and far-lane scenarios

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Vision & OCR | OpenCV, NumPy, Pillow, scikit-learn |
| Neural Reader | PyTorch (CRNN + BiGRU, CTC loss) |
| Backend API | FastAPI, Uvicorn, Pydantic |
| Dashboard | Streamlit, PyDeck, Altair |
| Database | SQLite |
| Network Analysis | NetworkX, Pandas |

## Contributors

| Name | GitHub |
|------|--------|
| A-Martyr | [@A-Martyr](https://github.com/A-Martyr) |
| J-Mahanty | [@J-Mahanty](https://github.com/J-Mahanty) |
