# Quickstart Guide: AI-Native Textbook Platform

## Prerequisites
- Node.js 18+ for frontend development
- Python 3.12+ for backend development
- Git
- Docker (optional, for local development)
- Access to OpenAI API
- Access to Qdrant Cloud (vector database)
- Access to Neon Postgres (SQL database)

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/madnan-github/robo-learn.git
cd robo-learn
```

### 2. Backend Setup (FastAPI)
```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys and database URLs

# Run the backend server
uvicorn src.main:app --reload --port 8000
```

### 3. Frontend Setup (Docusaurus)
```bash
# Open a new terminal and navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your backend API URL and other configuration

# Run the development server
npm start
```

## Environment Variables

### Backend (.env)
```env
# Database URLs
DATABASE_URL="postgresql://username:password@localhost:5432/textbook_platform"
QDRANT_URL="https://your-cluster.qdrant.tech:6333"
QDRANT_API_KEY="your-qdrant-api-key"

# AI Services
OPENAI_API_KEY="your-openai-api-key"
OPENAI_EMBEDDING_MODEL="text-embedding-ada-002"
OPENAI_CHAT_MODEL="gpt-4o-mini"

# Auth
BETTER_AUTH_SECRET="your-secret-key"
BETTER_AUTH_URL="http://localhost:3000"

# Translation
LIBRETRANSLATE_API_URL="https://libretranslate.com/translate"
```

### Frontend (.env)
```env
# API URLs
REACT_APP_API_BASE_URL="http://localhost:8000"
REACT_APP_BACKEND_URL="http://localhost:8000"

# Auth
REACT_APP_BETTER_AUTH_URL="http://localhost:3000"
```

## Development Workflow

### Adding a New Chapter
1. Create a new MDX file in `frontend/docs/module-x/`
2. Follow the chapter template with Learning Outcomes, Main Content, Assessments, and Further Reading
3. Add the chapter to the appropriate sidebar in `frontend/sidebars.js`
4. Run content ingestion to update the RAG system:
   ```bash
   curl -X POST http://localhost:8000/api/ingest \
   -H "Content-Type: application/json" \
   -d '{"content": "your chapter content", "chapterId": "unique-id"}'
   ```

### Running Tests
```bash
# Backend tests
cd backend
python -m pytest

# Frontend tests
cd frontend
npm test
```

## Key Endpoints

### Backend API
- `POST /api/chat` - Main chat endpoint
- `POST /api/chat/context` - Context-aware chat for selected text
- `GET /api/history/{userId}` - User chat history
- `POST /api/feedback` - Submit feedback on responses
- `POST /api/ingest` - Ingest new content (admin only)

### Frontend Components
- `/src/components/PersonalizeButton` - Content personalization
- `/src/components/TranslateButton` - Urdu translation toggle
- `/src/components/ChatbotWidget` - Integrated chatbot
- `/src/components/BackgroundForm` - User background collection

## Deployment

### Frontend (GitHub Pages)
```bash
cd frontend
npm run build
# The build output will be in the build/ directory
# Configure GitHub Pages to serve from the build directory
```

### Backend (Railway/Vercel/Render)
1. Set up environment variables in your deployment platform
2. Deploy using the platform's standard process
3. Ensure the frontend knows the deployed backend URL

## Troubleshooting

### Common Issues
1. **API Connection Errors**: Verify backend is running and CORS is configured
2. **Authentication Issues**: Check Better-Auth configuration and secret keys
3. **Translation API Errors**: Verify LibreTranslate API access
4. **RAG Chatbot Not Responding**: Check Qdrant connection and content ingestion status

### Development Tips
- Use `npm start` for frontend and `uvicorn --reload` for backend during development
- The Docusaurus live reload is very helpful for content changes
- Check the backend logs for API issues
- Verify all environment variables are properly set