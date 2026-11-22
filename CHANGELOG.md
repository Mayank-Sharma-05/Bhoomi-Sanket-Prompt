# Changelog

---

## [Milestone 2] - 2026-11-22

### Summary of Restructuring
Organized the complete Bhoomi Sanket codebase and Milestone 2 prompt engineering assets into the exact required repository hierarchy:
```text
bhoomi-sanket/
├── README.md
├── prompts/ (v1, v2, v3, final)
├── code/
├── test-data/
├── docs/
└── CHANGELOG.md
```

### Added
  - Added repository-level `.gitignore` and `code/.gitignore` configured to exclude sensitive files (`.env`, `.env.local`), build artifacts (`.next/`, `node_modules/`, `*.tsbuildinfo`), Python virtual environments (`.venv/`, `__pycache__/`), local database state (`*.sqlite`, `*.db`), OS metadata (`.DS_Store`, `Thumbs.db`), and compressed archives (`*.zip`).
  - Included the supplied Milestone 2 Student Guidelines PDF (`Milestone_2_Student_Guidelines.pdf`) and Prompt Engineering Guidelines PDF (`Prompt_Engineering_Mini_Project_Guidelines_2026.pdf`) in `docs/`.
- **Milestone 2 Prompt Files** (`prompts/`):
  - Added **P1: Dataset and Model Development** (`P1_dataset_and_model_development.txt`) across `v1/`, `v2/`, `v3/`, and `final/`.
  - Added **P2: Code Debugging** (`P2_code_debugging.txt`) across `v1/`, `v2/`, `v3/`, and `final/`.
  - Added **P3: Model Evaluation** (`P3_model_evaluation.txt`) across `v1/`, `v2/`, `v3/`, and `final/`.
  - Added **P4: Model Optimization** (`P4_model_optimization.txt`) across `v1/`, `v2/`, `v3/`, and `final/`.
  - Implemented progressive iterative enhancements: V1 (baseline concise) -> V2 (structured procedural) -> V3/Final (guardrailed, zero-hallucination, evidence-first).
- **Test Data & Validation Suite** (`test-data/`):
  - Created `Bhoomi_Sanket_Test_Cases.csv` featuring 12 project-specific test cases (exceeding the minimum 10 requirement).
  - Included **Normal** (6), **Edge** (4), and **Invalid** (2) test scenario coverage.
  - Included complete fields: Test No., Prompt Family, Type, Input, Expected Output, Actual Response, and Result.
  - Added `Bhoomi_Sanket_Test_Cases.docx` for formal word processor viewing.
  - Added `Bhoomi_Sanket_Test_Cases.json` for automated verification and programmatic parsing.
  - Added `test-data/README.md` detailing test matrix, methodology, and pass/fail criteria.
- **Documentation Suite** (`docs/`):
  - Added `Prompt_Iteration_Log.docx` and `Prompt_Iteration_Log.md` documenting rationale, prompts, inputs, responses, and iteration decisions.
  - Added `Prompt_Engineering_Guide.docx` and `Prompt_Engineering_Guide.md` providing developer usage instructions and prompt boundaries.
  - Added `Prompt_Workflow_Diagram.docx` and `Prompt_Workflow_Diagram.md` illustrating prompt interactions across the ML development lifecycle.
  - Added `Technical_Report.docx` and `Technical_Report.md` providing a comprehensive engineering report covering problem context, model architecture, test results, security governance, and Milestone 3 roadmap.
- **Root Repository Files**:
  - Created root `README.md` with full project overview, architecture diagram, execution guides for Next.js and FastAPI, and Milestone 2 prompt summary.
  - Created root `CHANGELOG.md` recording all structural movements, prompt additions, and verification tests.

### Changed & Consolidated
- **Application Source Code** (`code/`):
  - Consolidated complete Next.js 14 frontend (`app/`, `components/`, `lib/`, `public/`) into `code/`.
  - Restored static graphic assets into `code/public/` (`india-map.svg`, `highway.svg`, `bhoomi-sanket-logo.png`, `bhoomi-sanket-brand.jpg`, etc.).
  - Consolidated Prisma ORM schema (`code/prisma/schema.prisma`) and database migration scripts (`code/scripts/`).
  - Consolidated TypeScript shared definitions (`code/shared/types/ml-contract.ts`) and global declarations (`code/types/declarations.d.ts`).
  - Preserved FastAPI ML microservice (`code/ml_service/`) and validated predictor stack.
  - Enhanced `code/ml_service/predictor.py` with `STATE_NAME_MAP` to cleanly handle both state codes ('MH', 'UP', 'GJ') and full state names ('Maharashtra', 'Uttar Pradesh', 'Gujarat').
  - Preserved serialized model artifacts (`code/ml_service/artifacts/xgb_model.pkl`, `feature_columns.pkl`, `label_encoders.pkl`) and reference models (`code/ML Model Bhoomi Sanket/`).
  - Sanitized configuration files: provided clean `code/.env.example` with zero secrets, and updated `.gitignore` to prevent secret leakage.

### Verified
- Executed `code/ml_service/test_service.py` unit test suite against live model artifacts. Verified `GET /health`, `GET /model-info`, and `POST /predict` endpoints return HTTP 200 with 100% test pass rate.
