# KaryaSetu — Planning-to-Execution Bridge for Infrastructure Project Management

## About the Project

**KaryaSetu** is an intelligent enterprise infrastructure project execution platform designed to bridge high-level baseline project scheduling (e.g., Primavera P6 / MS Project) with ground-level field progress updates across multi-discipline engineering scopes (Civil, Piping, Electrical, Mechanical, Instrumentation, HSE).

---

### Tech Stack

- **Frontend**: React + Vite (Modular Vanilla CSS Design System, Lucide React icons)
- **Backend**: FastAPI (Python, Uvicorn, Pydantic v2)
- **Database**: SQLAlchemy ORM with SQLite prototype database
- **AI Intelligence**: Google Gemini API (`google-genai` SDK v2.22.0) with server-bound deterministic python tool validation
- **Authentication**: JWT Bearer Tokens with bcrypt password hashing and Role-Based Access Control (`PLANNER` / `SUPERVISOR`)

---

### Platform Architecture & Capabilities (Phases 1–14)

1. **Authentication & RBAC (Phase 2)**: Secure bcrypt password hashing, JWT Bearer tokens, and strict role segregation between **Lead Planners** and **Field Supervisors**.
2. **Project Baseline Management & Teams (Phase 3)**: Planners create and manage infrastructure projects, assign supervisors with designated engineering disciplines (`CIVIL`, `PIPING`, `ELECTRICAL`, `MECHANICAL`, `INSTRUMENTATION`, `HSE`, `OTHER`).
3. **L5/L6 Baseline Schedule Import (Phase 4)**: Planners import Primavera P6 / MS Project exports (.csv, .xlsx) with auto-column mapping, validation, and read-only schedule navigation.
4. **Actual Execution & Field Progress Tracking (Phase 5)**: Field execution reporting via `ActivityExecution` and append-only audit trail in `ProgressUpdate`. State machine controls valid status transitions (`START`, `PROGRESS`, `COMPLETE`, `ON_HOLD`, `RESUME`) with supervisor discipline enforcement.
5. **Real Project Dashboard (Phase 6)**: 100% database-derived project control dashboard metrics (overall progress, status distribution, overdue tracking, planned vs actual finish, discipline progress).
6. **Project AI Assistant (Phase 7)**: Real-time, project-scoped operational assistant executing safe server-bound Python tools for schedule inspection, progress summary, and overdue analysis.
7. **Natural-Language Progress Reporting (Phase 8)**: Authorized supervisors report site execution via natural language in Project AI with fuzzy activity matching and explicit confirmation.
8. **Batch Progress Report Ingestion (Phase 9)**: Spreadsheet ingestion (.csv, .xlsx) and pasted free-text DPR ingestion with multi-item review and transactional apply.
9. **Planner Review Center (Phase 10)**: Centralized command center for Lead Planners to inspect, resolve, re-match, reject, or mark as unplanned any low-confidence progress updates with zero silent updates and immutable baseline protection.
10. **Schedule Sync & Actuals Export Bridge (Phase 11)**: Canonical export bridge allowing Lead Planners to preview, change-detect, and export schedule-linked actuals datasets (Full Baseline Snapshot or Changes Since Last Export) as formatted Excel (.xlsx) workbooks or flat .csv files with immutable export audits.
11. **Project Analytics & Forecasting (Phase 12)**: 100% deterministic database-derived project analytics engine with activity-count progress, linear expected progress, schedule variance, historical trend replay, rule-based risk classification, and velocity-based completion forecasting.
12. **Document & Scanned Report Ingestion (Phase 13)**: Multi-format document ingestion for text PDFs, scanned DPR sheets, and site photos (.pdf, .jpg, .jpeg, .png) with page provenance tracking and multimodal Gemini fallback.
13. **Institutional Project Memory (Phase 14)**: Project-scoped audit history and historical intelligence engine with searchable event timelines, delay & variance analysis, physical evidence inspection, structured notes recording, and cross-phase query integration in Project AI.

---

## Local Development Configuration

### 1. Backend Server
```bash
cd backend
python -m uvicorn app.main:app --reload --host 0.0.0.0 --port 8001
```
- Base URL: `http://127.0.0.1:8001`
- Interactive Swagger Docs: `http://127.0.0.1:8001/docs`
- Health Check: `http://127.0.0.1:8001/api/health`

### 2. Frontend Application
```bash
cd frontend
npm run dev
```
- Local URL: `http://localhost:5173`
- Production Build: `npm run build`

---

## Environment Variables

### Backend (`backend/.env`)
```ini
HOST=0.0.0.0
PORT=8001
CORS_ORIGINS=http://localhost:5173,http://127.0.0.1:5173
DATABASE_URL=sqlite:///./sih26122.db
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440
APP_TIMEZONE=Asia/Kolkata
GEMINI_MODEL=gemini-2.5-flash
```

### Frontend (`frontend/.env`)
```ini
VITE_API_BASE_URL=http://localhost:8001
```
## Hackathon

This project was developed as part of **Smart India Hackathon** by our team.

For details about our participation and contributions, see [HACKATHON.md](HACKATHON.md).