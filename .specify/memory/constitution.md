<!-- SYNC IMPACT REPORT
Version change: N/A → 1.0.0
Modified principles: N/A (new constitution)
Added sections: All sections (new constitution)
Removed sections: N/A
Templates requiring updates:
  - ✅ .specify/templates/plan-template.md - Constitution Check section will automatically incorporate new principles
  - ✅ .specify/templates/spec-template.md - No direct dependencies to update
  - ✅ .specify/templates/tasks-template.md - No direct dependencies to update
  - ✅ .specify/templates/adr-template.md - Aligns with constitution ADR requirements
  - ✅ .specify/templates/checklist-template.md - No direct dependencies to update
Follow-up TODOs: None
-->
# Physical AI & Humanoid Robotics Textbook Constitution

## Core Principles

### Spec-First, AI-Augmented Development
We do not write code or chapters without a clear spec. All development follows the Spec-Kit Plus methodology with atomic tasks under 2 hours.

### Technical Stack Compliance
Frontend/Content: Docusaurus, React, TypeScript, MDX. Backend/AI: Python 3.12+, FastAPI. Database: Neon Serverless Postgres, Qdrant. Auth: Better-Auth.

### Quality Standards Compliance
Python: mypy compliant type hints, Google-style docstrings, pytest. Frontend: TypeScript strict mode, reusable components. Content: Learning Outcomes + Assessments.

### Architecture Decision Records (ADRs) Requirement
ADRs required for RAG retrieval logic, Urdu translation pipeline, and User Personalization data schema.

### Curriculum Alignment Validation
No code is committed without passing tests; no content is committed without passing a 'Curriculum Alignment' check following the syllabus modules.

### Hackathon Speed with Stability
Speed is key, but stability is mandatory. The platform must support the 4 bonus features: RAG Chatbot, Auth, Personalization, and Urdu Translation.

## Course Module Standards
Module 1: The Robotic Nervous System (ROS 2). Module 2: The Digital Twin (Gazebo & Unity). Module 3: The AI-Robot Brain (NVIDIA Isaac™). Module 4: Vision-Language-Action (VLA). Capstone: The Autonomous Humanoid.

## Development Workflow
Work performed in atomic tasks (<2 hours). All outputs strictly follow user intent. Prompt History Records (PHRs) created automatically for every user prompt.

## Governance
Constitution supersedes all other practices. Amendments require documentation and approval. All work follows the Spec-First methodology with explicit error paths and constraints. Architectural decisions that meet significance criteria must be documented as ADRs.

**Version**: 1.0.0 | **Ratified**: 2025-12-09 | **Last Amended**: 2025-12-09