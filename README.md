# AI-Driven Beam Management Agent

A production-style MVP for an agentic AI beam management system. The project simulates how a wireless system detects signal degradation caused by user mobility, scans/selects a better beam, and restores link quality using a closed-loop agent workflow.

---

# Project Goal

Build a modular beam management system that demonstrates:

- Signal degradation detection
- Rule-based beam recovery
- Beam scanning and switching
- Signal recovery evaluation
- Backend/frontend separation
- Production-style project structure

---

# Phase 1 Scope

Phase 1 focuses on a rule-based recovery loop.

```text
Sensing Agent
→ Decision Agent
→ Control Agent
→ Evaluator Agent
```

No ML model is used in Phase 1.

---

# Tech Stack

## Backend
- FastAPI
- Python
- Pandas
- Pydantic

## Frontend
- React
- TypeScript
- Vite

---

# Project Structure

```text
beam-management-agent/
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── api/
│   │   ├── core/
│   │   ├── data/
│   │   ├── agents/
│   │   ├── strategies/
│   │   ├── workflow/
│   │   └── evaluation/
│   ├── data/
│   ├── requirements.txt
│   └── README.md
│
├── frontend/
│   ├── src/
│   ├── package.json
│   └── README.md
│
├── docs/
├── experiments/
└── README.md
```

---

# Core Flow

The system simulates this behavior:

```text
User moves
→ signal strength drops
→ sensing agent detects degradation
→ decision agent triggers beam scan
→ control agent switches beam
→ evaluator checks recovery
```

---

# Expected Output

The system should show:

- Current beam
- Target/ideal beam
- Signal strength before recovery
- Selected recovery action
- Signal improvement
- Recovery success/failure
- Agent decision log

---

# Backend Setup

Move into backend folder:

```bash
cd backend
```

Create virtual environment:

```bash
python -m venv .venv
```

Activate environment:

### Mac/Linux

```bash
source .venv/bin/activate
```

### Windows

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run backend server:

```bash
uvicorn app.main:app --reload
```

Backend runs at:

```text
http://127.0.0.1:8000
```

Health check endpoint:

```text
http://127.0.0.1:8000/api/health
```

---

# Frontend Setup

Move into frontend folder:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Run frontend:

```bash
npm run dev
```

Frontend runs at:

```text
http://localhost:5173
```

---

# Dataset Setup

Place the dataset here:

```text
backend/data/beam_direction_dataset.csv
```

The dataset should contain fields such as:

```text
x_pos
y_pos
z_pos
velocity
heading
env_type
LOS
signal_strength
prev_beam
future_beam_angle
```

---

# API Endpoints

## Health Check

```http
GET /api/health
```

Example response:

```json
{
  "status": "ok",
  "service": "beam-management-agent-backend"
}
```

---

## Dataset Preview

```http
GET /api/simulation/dataset-preview
```

Returns:

- total rows
- column names
- sample records

---

# Backend Architecture

## main.py

Responsible for:

- creating FastAPI application
- configuring middleware
- registering routes
- exposing app object

---

## Middleware

Currently used middleware:

### CORS Middleware

Allows React frontend to communicate with FastAPI backend.

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:8000
```

Without CORS middleware, browser blocks requests.

---

# Phase 1 Agents

## Sensing Agent

Detects signal degradation using signal strength threshold.

---

## Decision Agent

Chooses recovery action.

Current strategy:

```text
scan nearby beams
```

---

## Control Agent

Applies selected beam switch.

---

## Evaluator Agent

Measures recovery performance.

Metrics include:

- signal improvement
- beam error reduction
- recovery success

---

# Current Limitations

Phase 1 does not yet include:

- ML-based beam prediction
- Reinforcement learning
- Multi-user beam association
- Resource allocation
- Beam squint modeling
- Real edge deployment

These are planned for future phases.

---

# Future Extensions

Planned upgrades:

- ML-based beam prediction
- Multi-user beam association
- Latency-aware beam switching
- Reliability optimization
- Resource allocation
- Edge-deployable controller simulation

---

# Development Philosophy

This project is intentionally structured like a production-style system:

- backend/frontend separation
- modular architecture
- isolated agents
- clean routing
- reusable workflow structure

The goal is to build a scalable foundation rather than a single-file simulation.

---

# Project Status

Current phase:

```text
Phase 1 — Rule-based closed-loop beam recovery
```
