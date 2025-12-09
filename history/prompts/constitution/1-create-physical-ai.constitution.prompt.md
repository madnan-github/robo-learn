---
id: 1
title: "Create Physical AI & Humanoid Robotics Textbook Constitution"
stage: constitution
date_iso: "2025-12-09"
surface: "agent"
model: "claude-opus-4-5-20251101"
feature: "none"
branch: "master"
user: "ruser"
command: "/sp.constitution"
labels:
  - "constitution"
  - "spec-driven-development"
  - "physical-ai"
  - "robotics"
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files_yaml:
  - ".specify/memory/constitution.md"
tests_yaml: []
---

# Create Physical AI & Humanoid Robotics Textbook Constitution

## Prompt Text

```
Act as the Lead Architect for the "Physical AI & Humanoid Robotics Textbook" project. We are winning a hackathon using the Spec-Kit Plus methodology.

Create a strict Project Constitution that defines the immutable standards for this project.

1. Project Vision & Scope
Goal: Build an AI-native textbook platform that teaches Physical AI, ROS 2, and Isaac Sim.

Nature: Hybrid project containing a Docusaurus frontend (the book) and a Python FastAPI backend (the RAG chatbot/agent).

Core Philosophy: "Spec-First, AI-Augmented." We do not write code or chapters without a clear spec.

2. Technical Stack (Non-Negotiable)
Frontend/Content: use (Docusaurus, React, TypeScript), MDX for content.

Backend/AI: Python 3.12+ (managed via uv), FastAPI.

Database: Neon Serverless Postgres (for logs/history), Qdrant (Vector DB).

Auth: Better-Auth.

Orchestration: Claude Code CLI + Spec-Kit Plus.

3. Global Quality Standards
Code (Python):

Strict type hints (mypy compliant).

Google-style docstrings.

pytest for all backend logic.

Code (Frontend):

TypeScript strict mode.

Components must be reusable (for buttons like "Translate" and "Personalize").

Content (Markdown):

Every chapter must start with "Learning Outcomes."

Every chapter must end with "Assessments."

Structure must strictly follow the "Physical AI & Humanoid Robotics" syllabus modules.

4. Architecture & Methodology Rules
ADRs: We must create an Architectural Decision Record (ADR) for:

The RAG retrieval logic.

The Urdu translation pipeline design.

The User Personalization data schema.

Checkpoints: Work is performed in atomic tasks (<2 hours).

Validation: No code is committed without passing tests; no content is committed without passing a "Curriculum Alignment" check.

5. Hackathon Constraints
Speed is key, but stability is mandatory.

The platform must support the 4 bonus features: RAG Chatbot, Auth, Personalization, and Urdu Translation.
Course Modules
Module 1: The Robotic Nervous System (ROS 2)
Focus: Middleware for robot control.
ROS 2 Nodes, Topics, and Services.
Bridging Python Agents to ROS controllers using rclpy.
Understanding URDF (Unified Robot Description Format) for humanoids.
Module 2: The Digital Twin (Gazebo & Unity)
Focus: Physics simulation and environment building.
Simulating physics, gravity, and collisions in Gazebo.
High-fidelity rendering and human-robot interaction in Unity.
Simulating sensors: LiDAR, Depth Cameras, and IMUs.
Module 3: The AI-Robot Brain (NVIDIA Isaac™)
Focus: Advanced perception and training.
NVIDIA Isaac Sim: Photorealistic simulation and synthetic data generation.
Isaac ROS: Hardware-accelerated VSLAM (Visual SLAM) and navigation.
Nav2: Path planning for bipedal humanoid movement.
Module 4: Vision-Language-Action (VLA)
Focus: The convergence of LLMs and Robotics.
Voice-to-Action: Using OpenAI Whisper for voice commands.
Cognitive Planning: Using LLMs to translate natural language ("Clean the room") into a sequence of ROS 2 actions.
Capstone Project: The Autonomous Humanoid. A final project where a simulated robot receives a voice command, plans a path, navigates obstacles, identifies an object using computer vision, and manipulates it.

Please generate the constitution.md file reflecting these rules.
```

## Response Text

Created a comprehensive Project Constitution for the "Physical AI & Humanoid Robotics Textbook" project based on the specified requirements. The constitution includes:

- Six core principles covering Spec-First development, technical stack compliance, quality standards, ADR requirements, curriculum alignment validation, and hackathon constraints
- Course Module Standards section outlining the four modules and capstone project
- Development Workflow section describing atomic tasks and PHR creation
- Governance section with amendment procedures and compliance requirements
- Version 1.0.0, ratified on 2025-12-09

The constitution enforces the "Spec-First, AI-Augmented" philosophy and establishes clear standards for code quality, technical stack usage, and validation processes.

## Outcome

Successfully generated the project constitution file at `.specify/memory/constitution.md` with all required principles and standards as specified in the user requirements.

## Evaluation

The constitution accurately reflects all specified requirements including technical stack, quality standards, ADR requirements, and course module structure. The document is properly formatted and includes a sync impact report.