# Bhoomi Sanket 
### Predictive Analytics System for Early Detection of Land Acquisition Delays (SIH26017)

---

## 📌 Project Overview

**Bhoomi Sanket** is an AI-powered enterprise platform developed under problem statement **SIH26017: Predictive Analytics System for Early Detection of Land Acquisition Delays**. 

Linear infrastructure megaprojects across India (highways, expressways, rail corridors, transmission grids) face frequent bottlenecks during statutory land acquisition stages under the RFCTLARR Act 2013 (Section 11, Section 19, Joint Measurement Surveys, Compensation Disbursements, and Court Litigation). Bhoomi Sanket provides early delay-risk detection and automated mitigation recommendations by pairing:
1. An empirical **XGBoost classification model** trained on 18,444 project records with 43 features.
2. A high-throughput **FastAPI ML inference microservice** providing real-time risk scores, SHAP explanations, and mitigation actions.
3. A modern **Next.js 14 web application** featuring interactive Leaflet GIS risk maps, administrative audit logs, and what-if simulation capabilities.
4. A disciplined **Prompt Engineering Architecture** supporting AI-assisted model development, code debugging, evaluation, and optimization without hallucinating predictions.

---

## 📂 Repository Structure

The repository follows the exact Milestone 2 specifications:

```text
bhoomi-sanket/
│
├── README.md                              # Main project guide & execution documentation
├── CHANGELOG.md                           # Detailed chronological changelog
│
├── prompts/                               # Milestone 2 prompt families (P1, P2, P3, P4)
│   ├── v1/                                # Initial baseline prompts
│   │   ├── P1_dataset_and_model_development.txt
│   │   ├── P2_code_debugging.txt
│   │   ├── P3_model_evaluation.txt
│   │   └── P4_model_optimization.txt
│   ├── v2/                                # Structured multi-step task prompts
│   │   ├── P1_dataset_and_model_development.txt
│   │   ├── P2_code_debugging.txt
│   │   ├── P3_model_evaluation.txt
│   │   └── P4_model_optimization.txt
│   ├── v3/                                # Guardrailed, zero-hallucination prompts
│   │   ├── P1_dataset_and_model_development.txt
│   │   ├── P2_code_debugging.txt
│   │   ├── P3_model_evaluation.txt
│   │   └── P4_model_optimization.txt
│   └── final/                             # Final production-ready prompt candidates
│       ├── P1_dataset_and_model_development.txt
│       ├── P2_code_debugging.txt
│       ├── P3_model_evaluation.txt
│       └── P4_model_optimization.txt
│
├── code/                                  # Full application source code & models
│   ├── app/                               # Next.js 14 App Router (pages, layouts, API routes)
│   ├── components/                        # React UI, GIS maps, risk gauges, dashboards
│   ├── lib/                               # Data stores, i18n, Supabase client, utilities
│   ├── public/                            # Static SVG maps, brand emblems, and images
│   ├── data/                              # District risk, state risk, and project GIS CSVs
│   ├── database/                          # SQL schemas and seed scripts
│   ├── prisma/                            # Prisma ORM schema & backup JSON exports
│   ├── scripts/                           # Migration, showcase generation, and test scripts
│   ├── shared/                            # TypeScript interfaces & ML contract types
│   ├── types/                             # Global TypeScript ambient declarations
│   ├── ml_service/                        # FastAPI ML inference microservice
│   │   ├── artifacts/                     # Serialized XGBoost model & feature artifacts
│   │   │   ├── xgb_model.pkl
│   │   │   ├── feature_columns.pkl
│   │   │   ├── label_encoders.pkl
│   │   │   └── README.md
│   │   ├── main.py                        # FastAPI application endpoints
│   │   ├── predictor.py                   # Model loader, feature encoder & SHAP pipeline
│   │   ├── schemas.py                     # Pydantic v2 validation contracts
│   │   ├── config.py                      # Service configuration & thresholds
│   │   ├── stub.py                        # Fallback stub inference logic
│   │   ├── requirements.txt               # Python package dependencies
│   │   └── test_service.py                # Service test suite & verification tests
│   ├── ML Model Bhoomi Sanket/            # Backup model artifacts & training references
│   ├── package.json                       # Frontend dependencies & scripts
│   ├── tsconfig.json                      # TypeScript configuration
│   ├── tailwind.config.ts                 # Tailwind CSS styling configuration
│   └── .env.example                       # Clean environment template (zero secrets)
│
├── test-data/                             # Project-specific prompt test cases
│   ├── Bhoomi_Sanket_Test_Cases.csv       # 12 test cases (Normal, Edge, Invalid)
│   ├── Bhoomi_Sanket_Test_Cases.docx      # Word formatted test document
│   ├── Bhoomi_Sanket_Test_Cases.json      # Machine-readable test suite
│   └── README.md                          # Test suite summary & matrix
│
└── docs/                                  # Project documentation & engineering guides
    ├── Prompt_Iteration_Log.docx          # Prompt iteration log (DOCX)
    ├── Prompt_Iteration_Log.md            # Prompt iteration log (Markdown)
    ├── Prompt_Engineering_Guide.docx      # Prompt engineering guide (DOCX)
    ├── Prompt_Engineering_Guide.md        # Prompt engineering guide (Markdown)
    ├── Prompt_Workflow_Diagram.docx       # Prompt workflow diagram (DOCX)
    ├── Prompt_Workflow_Diagram.md         # Prompt workflow diagram (Markdown)
    ├── Technical_Report.docx              # Milestone 2 Technical Report (DOCX)
    └── Technical_Report.md                # Milestone 2 Technical Report (Markdown)
```

---

##  How to Run the Project

### Prerequisites
- **Node.js**: v18+ (v24 LTS recommended)
- **Python**: v3.10+ (v3.13 tested)
- **Package Managers**: `npm` / `pip`

---

### 1. Running the ML Microservice (FastAPI)

1. Navigate to the ML service directory:
   ```bash
   cd code/ml_service
   ```

2. Create and activate a Python virtual environment:
   ```bash
   python -m venv .venv
   # Windows:
   .venv\Scripts\activate
   # Linux/macOS:
   source .venv/bin/activate
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the automated unit test suite to verify model artifact loading:
   ```bash
   python test_service.py
   ```
   *Expected output: `/predict returned valid response ... All ML service tests passed successfully!*

5. Start the FastAPI development server:
   ```bash
   uvicorn main:app --reload --host 127.0.0.1 --port 8000
   ```
   - Swagger Interactive API Docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
   - Health Check: [http://127.0.0.1:8000/health](http://127.0.0.1:8000/health)

---

### 2. Running the Web Application (Next.js)

1. Navigate to the `code/` directory:
   ```bash
   cd code
   ```

2. Configure environment variables:
   ```bash
   cp .env.example .env.local
   ```
   *(By default, the application runs smoothly in offline mock mode without requiring third-party cloud credentials.)*

3. Install frontend dependencies:
   ```bash
   npm install
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```

5. Open your browser and navigate to:
   - Dashboard: [http://localhost:3000](http://localhost:3000)
   - Interactive GIS Map: [http://localhost:3000/map](http://localhost:3000/map)
   - What-If Risk Simulator: [http://localhost:3000/what-if](http://localhost:3000/what-if)

---

##  Milestone 2: Prompt Engineering Architecture

The prompt engineering suite provides four specialized prompt families designed to assist engineers throughout the ML workflow:

| Prompt Family | Purpose | Primary Guardrail |
|---|---|---|
| **P1: Dataset & Model Development** | Guides Colab data inspection, leak-safe preprocessing, stratification, and model training. | Prevents target data leakage; stops hallucination of column names or accuracy scores. |
| **P2: Code Debugging** | Analyzes runtime stack traces, KeyErrors, shape mismatches, and categorical errors. | Enforces minimal surgical fixes; refuses to guess missing variable names without evidence. |
| **P3: Model Evaluation** | Contextualizes confusion matrices, precision/recall trade-offs, and ROC-AUC for delays. | Enforces positive-class verification; refuses to generate unmeasured evaluation scores. |
| **P4: Model Optimization** | Structures controlled cross-validation hyperparameter search (depth, learning rate, subsample). | Isolates held-out test data; requires baseline vs experiment comparisons. |

### Prompt Versions & Iteration Lifecycle
- **V1 (Baseline)**: Concise initial prompt templates.
- **V2 (Structured)**: Stage-by-stage instructions with explicit parameters.
- **V3 / Final (Guardrailed)**: Production prompts incorporating strict evidence requirements and defensive checks.

---

##  Test Suite & Validation

The prompt suite includes **12 project-specific test scenarios** documented in `test-data/`:
- **Normal Cases** (T01, T02, T03, T04, T06, T09): Standard expected engineering flows.
- **Edge Cases** (T05, T07, T10, T12): Missing class mappings, feature order drift, single-class datasets, and train/val divergence.
- **Invalid Cases** (T08, T11): Requests to fabricate metrics without data or debug KeyErrors without column schemas.

All 12 tests achieve a **100% Pass rate**, demonstrating defensive behavior strictly aligned with Bhoomi Sanket's ground truth.

---

##  Security & Data Governance

- **Zero Secrets**: No production database passwords, Clerk secret keys, or auth tokens are committed to this repository.
- **Zero Hallucination**: No synthetic evaluation metrics or fabricated project numbers are claimed.
- **Model Integrity**: The genuine XGBoost model weights (`xgb_model.pkl`) and label encoders remain preserved and unmodified.

---

##  Documentation

- [Prompt Iteration Log](docs/Prompt_Iteration_Log.md) ([DOCX](docs/Prompt_Iteration_Log.docx))
- [Prompt Engineering Guide](docs/Prompt_Engineering_Guide.md) ([DOCX](docs/Prompt_Engineering_Guide.docx))
- [Prompt Workflow Diagram](docs/Prompt_Workflow_Diagram.md) ([DOCX](docs/Prompt_Workflow_Diagram.docx))
- [Milestone 2 Technical Report](docs/Technical_Report.md) ([DOCX](docs/Technical_Report.docx))
