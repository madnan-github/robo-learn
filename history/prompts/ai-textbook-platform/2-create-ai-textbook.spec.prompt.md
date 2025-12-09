---
id: 2
title: "Create AI Textbook Platform Specification"
stage: spec
date_iso: "2025-12-09"
surface: "agent"
model: "claude-opus-4-5-20251101"
feature: "ai-textbook-platform"
branch: "1-ai-textbook-platform"
user: "ruser"
command: "/sp.specify"
labels:
  - "specification"
  - "textbook-platform"
  - "ai-education"
  - "robotics"
links:
  spec: "specs/1-ai-textbook-platform/spec.md"
  ticket: null
  adr: null
  pr: null
files_yaml:
  - "specs/1-ai-textbook-platform/spec.md"
  - "specs/1-ai-textbook-platform/checklists/requirements.md"
tests_yaml: []
---

# Create AI Textbook Platform Specification

## Prompt Text

```
AI-Native Textbook Platform for "Physical AI & Humanoid Robotics" Course

Target audience: Hackathon judges evaluating comprehensive AI-native educational platform
Focus: Unified platform combining Docusaurus textbook with integrated RAG chatbot

Success criteria:
1. Complete 4-module textbook with 15+ chapters deployed to GitHub Pages
2. Functional RAG chatbot answering questions based on book content
3. Support for text selection context in chatbot responses
4. User authentication with background profiling
5. Personalization features per chapter
6. Urdu translation capability
7. All bonus features implemented (300+ points potential)

## PHASE 1: AI/Spec-Driven Book Creation
**Goal:** Build Docusaurus textbook following exact course syllabus

**Technical requirements:**
- Framework: Docusaurus v3.4.0
- Content: MDX with React components
- Styling: Tailwind CSS + custom robotics theme
- Deployment: GitHub Pages with GitHub Actions CI/CD

**Content structure (strict adherence to syllabus):**
Module 1: The Robotic Nervous System (ROS 2)
  • Chapter 1: Introduction to Physical AI & Embodied Intelligence
  • Chapter 2: ROS 2 Architecture: Nodes, Topics, Services
  • Chapter 3: rclpy: Bridging Python Agents to ROS
  • Chapter 4: URDF for Humanoid Robot Modeling

Module 2: The Digital Twin (Gazebo & Unity)
  • Chapter 5: Gazebo Physics Simulation Fundamentals
  • Chapter 6: Unity for High-Fidelity HRI (Human-Robot Interaction)
  • Chapter 7: Sensor Simulation: LiDAR, Depth Cameras, IMUs
  • Chapter 8: Environment Building for Training

Module 3: The AI-Robot Brain (NVIDIA Isaac™)
  • Chapter 9: NVIDIA Isaac Sim: Photorealistic Simulation
  • Chapter 10: Isaac ROS: Hardware-Accelerated VSLAM
  • Chapter 11: Nav2: Path Planning for Bipedal Movement
  • Chapter 12: Synthetic Data Generation Pipelines

Module 4: Vision-Language-Action (VLA)
  • Chapter 13: OpenAI Whisper for Voice Commands
  • Chapter 14: LLMs for Cognitive Planning (Language→Actions)
  • Chapter 15: Capstone: Autonomous Humanoid Integration

**Chapter template (non-negotiable):**
Chapter Title
Learning Outcomes:

Bullet point 1

Bullet point 2

Bullet point 3

Main Content
[Content with code examples, diagrams, practical exercises]

Assessments:

Quiz question 1

Practical exercise 1

Discussion question 1

Further Reading:

[Reference 1]

[Reference 2]


**UI Components to build:**
1. `PersonalizeButton`: Captures user background and adapts content
2. `TranslateButton`: Translates chapter content to Urdu
3. `ChatbotWidget`: Container for RAG chatbot integration
4. `BackgroundForm`: Collects software/hardware expertise on signup

**Quality gates for Phase 1:**
- ✓ All 15 chapters completed with Learning Outcomes & Assessments
- ✓ Mobile-responsive design
- ✓ Deployed to GitHub Pages
- ✓ SEO optimized (meta tags, sitemap)
- ✓ All internal links functional
- ✓ Code syntax highlighting working

---

## PHASE 2: Integrated RAG Chatbot Development
**Goal:** Build context-aware Q&A system embedded in textbook

**Technical stack (strict):**
- Backend: Python 3.12+, FastAPI, uv for dependency management
- Vector DB: Qdrant Cloud Free Tier
- SQL DB: Neon Serverless Postgres
- Authentication: Better-Auth
- AI: Gemini or OpenAI Agents SDK (gpt-4o-mini, text-embedding-ada-002)

**Architecture requirements:**

### 1. Text Processing Pipeline
Book Content → Chunking (semantic, 500 tokens) → Embeddings → Qdrant


### 2. Database Schema (Neon Postgres)
users (Better-Auth extended):

id, email, name

background: JSON (software_exp, hardware_exp, robotics_exp)

created_at

chat_sessions:

id, user_id, title, created_at

messages:

id, session_id, role, content

context_chunks: JSON[] (cited sources)

metadata: JSON (selected_text, chapter, timestamp)

feedback:

message_id, rating, comment, created_at


### 3. API Endpoints (FastAPI)
POST /api/chat

Input: {message, session_id?, selected_text?, user_id}

Output: Streaming with citations

POST /api/chat/context

Special endpoint for selected text queries

GET /api/history/{user_id}

Retrieve user's chat history

POST /api/feedback

Rate response quality

POST /api/ingest

Ingest new textbook content (admin only)


### 4. Retrieval Logic
- Hybrid search: semantic + keyword
- Context window: 8K tokens
- Re-ranking: similarity score + recency
- Citation format: [Chapter X, Page Y]

### 5. Frontend Integration
```jsx
<ChatbotWidget
  apiUrl="https://api.yourdomain.com"
  initialMessage="Ask me anything about Physical AI"
  enableTextSelection={true}
  showHistory={true}
/>
Special feature: Selected Text Context

typescript
// When user selects text:
const selectedText = window.getSelection().toString();
// Send with chat query for context-aware answers
Deployment requirements:

Backend: Deployed to Railway/Vercel/Render

CORS: Configured for GitHub Pages domain

Environment variables: Secure management

Monitoring: Health checks at /health

Quality gates for Phase 2:

✓ RAG answers questions from textbook accurately

✓ Selected text context works correctly

✓ Chat history persists per user

✓ Response time < 3 seconds

✓ API documented with Swagger/OpenAPI

✓ Integration tests passing

BONUS FEATURES IMPLEMENTATION
Feature 1: Authentication & Background Profiling
Integrate Better-Auth with custom signup form

Collect: programming experience, hardware familiarity, robotics background

Store in users.background JSON field

Use for content personalization

Feature 2: Content Personalization
PersonalizeButton at chapter start

Adjusts content based on user.background

Examples:

Beginner: More fundamentals, simpler examples

Expert: Advanced topics, complex implementations

Software-only: Emphasis on simulation

Hardware-focused: Real-world deployment details

Feature 3: Urdu Translation
TranslateButton at chapter start

Uses Google Translate API or LibreTranslate

Toggle between English/Urdu

Preserves code blocks and technical terms

Stores preference in user settings

HACKATHON DELIVERABLES CHECKLIST
Mandatory (100 points):
Public GitHub Repo with complete code

Textbook deployed to GitHub Pages

RAG chatbot functional and embedded

Demo video (< 90 seconds)

Bonus Features:
+50 pts: Reusable Claude Code Subagents/Skills

+50 pts: Better-Auth with background questions

+50 pts: Chapter personalization buttons

+50 pts: Urdu translation buttons

Submission requirements:
GitHub Repo Structure:


/frontend          # Docusaurus textbook
/backend           # FastAPI RAG chatbot
/specs             # All specification files
/docs              # Documentation
docker-compose.yml # Local development
README.md          # Setup instructions
Live Demo Capabilities:

Show textbook navigation

Demonstrate RAG chatbot with textbook Q&A

Show selected text context feature

Demonstrate personalization/translation

Show user authentication flow

Documentation:

Architecture diagrams

Setup instructions

API documentation

User guide

TIMELINE (7-Day Sprint)
Day 1-2: Foundation

Setup Docusaurus project

Create chapter templates

Setup FastAPI backend skeleton

Configure databases

Day 3-4: Core Content

Write Chapters 1-8

Implement RAG ingestion pipeline

Build chat API endpoints

Integrate authentication

Day 5: Integration

Embed chatbot in Docusaurus

Implement text selection context

Add personalization buttons

Add translation buttons

Day 6: Polish & Testing

Write remaining chapters

Test RAG accuracy

Optimize performance

Fix bugs

Day 7: Deployment & Demo

Deploy to GitHub Pages

Deploy backend API

Record demo video

Prepare submission

CONSTRAINTS & ASSUMPTIONS
Technical constraints:

Use free tiers of all services (Qdrant, Neon, etc.)

OpenAI API for embeddings/completions (gpt-4o-mini)

Docusaurus for static site generation

React 18+ for frontend components

Content constraints:

Follow exact syllabus structure

Include practical code examples

All claims technically accurate

Balance theory and practice

Not included (scope boundaries):

Mobile applications

Offline functionality

Advanced analytics dashboard

Custom LLM training

Physical robot control code (simulation only)

VALIDATION METRICS
Textbook quality:

Completeness: All syllabus topics covered

Clarity: Technical concepts explained accessibly

Practicality: Hands-on exercises provided

Structure: Logical progression through modules

Chatbot performance:

Accuracy: >80% correct answers on test questions

Speed: <3 second response time

Relevance: Citations match query context

Usability: Intuitive interface

Platform stability:

Uptime: 99% during evaluation period

Security: No exposed API keys

Scalability: Handles concurrent users

Maintainability: Clean, documented code
```

## Response Text

Successfully created a comprehensive specification for the AI-Native Textbook Platform for Physical AI & Humanoid Robotics. The specification includes:

- 5 detailed user stories covering core platform functionality (textbook access, RAG chatbot, personalization, Urdu translation, and authentication)
- 10 functional requirements covering all platform features
- 10 measurable success criteria that are technology-agnostic
- Key entities identified (User, Chapter, ChatSession, Message, UserProfile)
- Edge cases addressed for system resilience
- Quality checklist validation completed

The specification follows the template structure and maintains focus on user value without implementation details. It covers all requested features including the 4-module textbook with 15+ chapters, RAG chatbot with context-aware responses, user authentication with background profiling, content personalization, and Urdu translation capability.

## Outcome

Created complete feature specification at specs/1-ai-textbook-platform/spec.md with accompanying quality checklist. Branch 1-ai-textbook-platform created and committed with all necessary files.

## Evaluation

The specification successfully captures all requirements from the feature description while maintaining focus on user value and business needs. All mandatory sections are completed, requirements are testable and unambiguous, and success criteria are measurable and technology-agnostic. The specification is ready for the next phase of development.