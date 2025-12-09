# Research: AI-Native Textbook Platform

## Decision: Technology Stack Selection
**Rationale**: Selected based on project requirements and constitution compliance. Docusaurus for static site generation and content management, FastAPI for backend services, with Qdrant and Neon Postgres for data storage needs.
**Alternatives considered**:
- Next.js vs Docusaurus: Chose Docusaurus for its superior documentation features and MDX support
- Express vs FastAPI: Chose FastAPI for built-in OpenAPI docs and Pydantic integration
- PostgreSQL vs Neon Postgres: Chose Neon for serverless capabilities and ease of deployment

## Decision: Architecture Pattern
**Rationale**: Web application with separate frontend/backend to allow independent scaling and development. Frontend handles static content and user interactions, backend manages dynamic features like chatbot, auth, and content processing.
**Alternatives considered**:
- Monolithic architecture: Rejected for lack of scalability and team development flexibility
- Microservices: Rejected as overkill for hackathon scope

## Decision: RAG Implementation Approach
**Rationale**: Using OpenAI embeddings (text-embedding-ada-002) with Qdrant vector database for textbook content retrieval. This provides accurate semantic search capabilities for the chatbot.
**Alternatives considered**:
- Local embeddings (SentenceTransformers): Rejected due to potential accuracy concerns
- Alternative vector DBs (Pinecone, Weaviate): Chose Qdrant for open-source nature and free tier availability

## Decision: Authentication Strategy
**Rationale**: Using Better-Auth for its simplicity and integration capabilities. It supports custom fields needed for background collection during signup.
**Alternatives considered**:
- Auth.js/NextAuth: Would require more custom implementation for background collection
- Firebase Auth: Overkill for hackathon scope and potential cost concerns

## Decision: Content Personalization Implementation
**Rationale**: Personalization applied at chapter/section level as specified in clarifications. Implementation will use conditional rendering based on user profile data.
**Alternatives considered**:
- Server-side personalization: Would add complexity and reduce performance
- Individual paragraph personalization: Rejected as specified in clarifications for consistency

## Decision: Urdu Translation Approach
**Rationale**: Using LibreTranslate API for translation functionality. Provides good accuracy for technical content while being free to use.
**Alternatives considered**:
- Google Translate API: Potential cost concerns for hackathon project
- Manual translation: Time prohibitive for hackathon timeline
- DeepL API: Cost concerns and API limitations

## Decision: Deployment Strategy
**Rationale**: GitHub Pages for frontend (static Docusaurus site), with backend deployed to Railway/Vercel/Render for API services. This meets the requirement for public accessibility while keeping costs minimal.
**Alternatives considered**:
- Self-hosted solutions: Would add operational complexity beyond hackathon scope
- Other static hosting: GitHub Pages offers best integration with GitHub workflow

## Decision: Textbook Content Structure
**Rationale**: Following the exact syllabus structure with 4 modules and 15 chapters. Each chapter will follow the specified template with Learning Outcomes, Main Content, Assessments, and Further Reading.
**Alternatives considered**:
- Different content organization: Would violate curriculum alignment requirements
- Fewer chapters: Would not meet feature requirements

## Decision: Chatbot Context Handling
**Rationale**: Implementing text selection context feature to allow users to select text and ask questions about that specific content. This requires JavaScript to capture selected text and send it with the query.
**Alternatives considered**:
- Only whole-page context: Would limit functionality
- Manual text input for context: Would be less user-friendly