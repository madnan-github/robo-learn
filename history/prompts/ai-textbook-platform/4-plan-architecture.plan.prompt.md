---
id: 4
title: "Plan AI Textbook Platform Architecture"
stage: plan
date_iso: "2025-12-09"
surface: "agent"
model: "claude-opus-4-5-20251101"
feature: "ai-textbook-platform"
branch: "001-ai-textbook-platform"
user: "ruser"
command: "/sp.plan"
labels:
  - "planning"
  - "architecture"
  - "textbook-platform"
  - "ai-education"
links:
  spec: "specs/001-ai-textbook-platform/spec.md"
  plan: "specs/001-ai-textbook-platform/plan.md"
  research: "specs/001-ai-textbook-platform/research.md"
  data_model: "specs/001-ai-textbook-platform/data-model.md"
  ticket: null
  adr: null
  pr: null
files_yaml:
  - "specs/001-ai-textbook-platform/plan.md"
  - "specs/001-ai-textbook-platform/research.md"
  - "specs/001-ai-textbook-platform/data-model.md"
  - "specs/001-ai-textbook-platform/contracts/openapi.yaml"
  - "specs/001-ai-textbook-platform/quickstart.md"
tests_yaml: []
---

# Plan AI Textbook Platform Architecture

## Prompt Text

```
Project: AI-Native Textbook Platform for "Physical AI & Humanoid Robotics"

Core Goal: Build a unified platform combining a Docusaurus-based digital textbook with an integrated, context-aware RAG chatbot. Target is a complete hackathon submission with all bonus features.

PHASE 1: The Textbook (Docusaurus)
Content: 4 Modules, 15 Chapters exactly per provided syllabus.
Tech: Docusaurus v3.4.0, MDX, Tailwind CSS, GitHub Pages deployment.
UI Components to Build:

PersonalizeButton: Adapts chapter content based on user background.

TranslateButton: Toggles chapter content between English and Urdu.

ChatbotWidget: Embeds the RAG chatbot.

BackgroundForm: Collects user expertise on signup (software/hardware/robotics).

Quality Gate: 15 complete chapters deployed and live.

PHASE 2: Integrated RAG Chatbot
Goal: Chatbot that answers questions using textbook content, with a special feature for using selected text as context.
Tech Stack:

Backend: FastAPI (Python)

AI: OpenAI (gpt-4o-mini, text-embedding-ada-002)

DBs: Qdrant Cloud (vector store), Neon Postgres (user data, chat history)

Auth: Better-Auth

Key Features:

Text Processing: Book content chunked, embedded, and stored in Qdrant.

Chat API: Endpoint (POST /api/chat) accepts message and optional selected_text for context-aware responses.

History & Feedback: Stores user chat sessions and allows response rating.

Frontend Integration: ChatbotWidget enables text selection; selected text is sent with the query.

Quality Gate: Accurate, cited answers in <3 seconds.

BONUS FEATURES (All Required for Max Points)
Auth & Profiling: Better-Auth with custom BackgroundForm.

Content Personalization: PersonalizeButton tweaks explanations based on user's background (e.g., beginner vs. expert).

Urdu Translation: TranslateButton translates chapter content to Urdu via API.

Deliverables & Timeline
Repo Structure: /frontend (textbook), /backend (chatbot), /specs, /docs.
Live Demo Must Show: Textbook nav, Chatbot Q&A, Selected-text context, Personalization, Translation, Auth flow.
7-Day Sprint: Days 1-2 (Foundation), Days 3-4 (Core Content/API), Day 5 (Integration), Day 6 (Polish), Day 7 (Deploy & Demo).

Success Criteria
Complete: All 15 chapters live + functional chatbot.

Integrated: Chatbot embedded in textbook with selected-text context.

Bonus Features: Auth/profiling, personalization, and translation all implemented.

Stable: Deployed, secure, and performs under evaluation.
```

## Response Text

Successfully completed the planning phase for the AI-Native Textbook Platform. The following artifacts were created:

1. Implementation Plan (plan.md): Detailed architecture plan with technical context, constitution compliance check, and project structure.

2. Research Document (research.md): Comprehensive research on technology choices, architecture patterns, and implementation approaches with rationale for each decision.

3. Data Model (data-model.md): Complete data model with entities (User, Chapter, ChatSession, Message, Feedback, Module), relationships, validation rules, and state transitions.

4. API Contracts (contracts/openapi.yaml): Complete OpenAPI specification for all backend APIs including chat, authentication, feedback, and content management endpoints.

5. Quickstart Guide (quickstart.md): Step-by-step setup instructions for development environment, deployment, and troubleshooting.

6. Agent Context Update: Updated CLAUDE.md with the new technology stack information.

The plan follows the constitution requirements with proper compliance checks, uses the specified technology stack (Docusaurus, FastAPI, Neon Postgres, Qdrant, Better-Auth), and includes provisions for all required bonus features. The architecture supports the 4-phase development approach with clear separation between frontend and backend components.

## Outcome

Planning phase complete with all required artifacts generated. The implementation plan is ready for the task generation phase (/sp.tasks). The architecture supports all required features including the RAG chatbot, content personalization, Urdu translation, and user authentication.

## Evaluation

The planning phase successfully identified and documented all architectural requirements. The solution is compliant with the project constitution, uses the specified technology stack, and addresses all functional requirements from the specification. The data model and API contracts provide a solid foundation for implementation.