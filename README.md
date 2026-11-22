# Medi-Scribe-Sage - Clinical EHR Transcription & Grounded RAG Platform

<p align="center">
  <a href="https://sohail.devsil.com"><strong>Portfolio</strong></a> | 
  <a href="https://github.com/sohailahmed-bsrh"><strong>GitHub Profile</strong></a> | 
  <a href="https://github.com/sohailahmed-bsrh/medi-scribe-sage"><strong>Source Repository</strong></a>
</p>

---

## Executive Summary & Problem Statement

Physicians spend up to two hours documenting medical records for every hour of direct patient care. This administrative burden causes physician burnout and delays electronic health record (EHR) updates. Furthermore, automated clinical summarizers often introduce hallucinations, presenting unacceptable risks in healthcare environments.

Medi-Scribe-Sage resolves this documentation dilemma. Combining clinical speech processing, strict medical ontology chunking (ICD-10 / SNOMED-CT references), and a grounded RAG retrieval pipeline, the platform transforms doctor-patient dialogue into structured, audit-ready SOAP notes (Subjective, Objective, Assessment, Plan) backed by verified medical knowledge retrieval.

---

## Real-World Industry Applications

- **Inpatient & Outpatient Consultation**: Translates real-time patient-physician conversations into formatted clinical SOAP notes.
- **Clinical EHR Integration**: Ingests clinical notes directly into relational hospital schemas using Drizzle ORM and Supabase PostgreSQL.
- **Medical Audit & Compliance**: Provides exact source citations for clinical assertions, allowing healthcare administrators to audit documentation trails.
- **Clinical Decision Support**: Enables semantic querying over institutional clinical guidelines and pharmacological databases.

---

## Technical Architecture & Engineering Walkthrough

The platform integrates a Python-based clinical RAG pipeline with a modern Bun and TypeScript clinical workstation:

```
[Clinical Audio / Consultation Record]
                  │
                  ▼
   [Clinical Audio Diarization & Ingestion]
                  │
                  ▼
 [Domain-Specific Medical Chunking & Cleaning]
(rag_pipeline/src/chunker.py & cleaner.py)
                  │
                  ▼
   [High-Dimensional Vector Embeddings]
        (rag_pipeline/src/embedder.py)
                  │
                  ▼
     [Vector Similarity Search & Index]
                  │
                  ▼
[Grounded Clinical SOAP Synthesis & Validation]
  (Subjective, Objective, Assessment, Plan)
                  │
                  ▼
[Drizzle ORM Relational Storage & Supabase Auth]
(drizzle/schema.ts & migrations/0000_migration.sql)
                  │
                  ▼
   [Interactive Clinical Workstation Dashboard]
```

### Step 1: Medical Document Cleaning & Extraction
The ingestion engine (`rag_pipeline/src/reader.py`, `extractor.py`, `cleaner.py`) strips clinical formatting artifacts, anonymizes protected patient identifiers, and extracts consultation dialogue.

### Step 2: Semantic Clinical Chunking
Unlike generic prose, clinical records contain dense medical terminology and hierarchical relationships. The chunker (`rag_pipeline/src/chunker.py`) isolates clinical observations, vital signs, symptom timelines, and medication regimens into structured segments.

### Step 3: Vector Embeddings & Search
The embedder (`rag_pipeline/src/embedder.py`) maps clinical terminology into semantic vector space. The search module (`rag_pipeline/src/search.py`) queries indexed clinical references to match patient symptom profiles against standardized diagnostic criteria.

### Step 4: SOAP Note Synthesis
The synthesis engine structures dialogue into standardized healthcare reporting:
- **Subjective**: Patient history, symptoms, and timeline.
- **Objective**: Vital statistics, lab reports, and physical examination findings.
- **Assessment**: Primary and differential diagnostic evaluations.
- **Plan**: Prescriptions, lab orders, therapies, and follow-up schedules.

### Step 5: Database Schema & Authentication
Data persistence is handled by Drizzle ORM (`drizzle/schema.ts`, `drizzle.config.ts`), managing migrations, relational patient-encounter schemas, and audit logs. Supabase Auth ensures role-based access control (RBAC) across clinical roles.

---

## Technology Stack & Implementation Specifications

| Component | Technology | Version | Architectural Function |
| :--- | :--- | :--- | :--- |
| **Runtime Environment** | Bun Runtime | Latest | High-performance JavaScript execution and package manager |
| **Backend / Client** | TypeScript / Vite / React | Production | Reactive clinical workstation frontend |
| **ORM & Database** | Drizzle ORM / PostgreSQL | 0.30+ | Type-safe schema definitions and migration tracking |
| **Authentication** | Supabase Auth | Latest | Secure role-based access control for medical staff |
| **Clinical RAG Engine** | Python | 3.10+ | Text extraction, semantic chunking, and embedding generation |
| **Vector Indexing** | Scikit-Learn / FAISS | Latest | Fast similarity matching across clinical protocols |
| **Testing Suite** | Vitest | Latest | Automated unit and integration testing across frontend modules |

---

## Installation & Setup Guide

### 1. Clinical RAG Pipeline
```bash
cd rag_pipeline
python -m venv venv
# Windows: venv\Scriptsctivate | Unix: source venv/bin/activate
pip install -r ../requirements.txt
python run.py
```

### 2. Workstation Client & Database Setup
```bash
# In the repository root:
bun install
bun run db:push     # Run Drizzle migrations
bun run dev         # Launch development server
```

---

## Author & Contact Information

<table width="100%">
  <tr>
    <td width="150" align="center" valign="middle">
      <img src="https://avatars.githubusercontent.com/u/231165170?v=4" width="120" style="border-radius: 50%;" alt="Sohail Ahmed"/>
    </td>
    <td>
      <h3>Sohail Ahmed</h3>
      <p><strong>Senior Software Engineer & AI Systems Architect</strong></p>
      <p>Specializing in Full-Stack AI Application Development, Computer Vision, Deep Learning Pipelines, and Scalable Automation Architectures.</p>
      <p>
        <a href="https://sohail.devsil.com"><strong>Portfolio Website</strong></a> | 
        <a href="https://github.com/sohailahmed-bsrh"><strong>GitHub Profile</strong></a> | 
        <a href="https://www.linkedin.com/in/sohail-ahmed-devsil/"><strong>LinkedIn</strong></a> | 
        <a href="https://www.kaggle.com/sohail2411126"><strong>Kaggle</strong></a> | 
        <a href="https://x.com/ahmed241126"><strong>Twitter/X</strong></a> | 
        <a href="mailto:se906403@gmail.com"><strong>Email Contact</strong></a>
      </p>
    </td>
  </tr>
</table>
