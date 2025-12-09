# Data Model: AI-Native Textbook Platform

## Entity: User
**Description**: Represents a student using the platform
**Fields**:
- id: string (UUID) - Unique identifier
- email: string - User's email address
- name: string - User's display name
- createdAt: datetime - Account creation timestamp
- background: JSON object - User's technical background information
  - software_exp: string (beginner/intermediate/expert)
  - hardware_exp: string (beginner/intermediate/expert)
  - robotics_exp: string (beginner/intermediate/expert)
- preferences: JSON object - User's platform preferences
  - language: string (default: 'en', possible: 'en', 'ur')
  - personalization_level: string (beginner/expert)

## Entity: Chapter
**Description**: Represents a textbook chapter with content sections
**Fields**:
- id: string (UUID) - Unique identifier
- moduleId: string - Reference to the module this chapter belongs to
- title: string - Chapter title
- slug: string - URL-friendly identifier
- content: string - Chapter content in MDX format
- learningOutcomes: string[] - List of learning outcomes
- assessments: string[] - List of assessment questions
- furtherReading: string[] - List of further reading references
- createdAt: datetime - Creation timestamp
- updatedAt: datetime - Last update timestamp
- version: integer - Content version for change tracking

## Entity: ChatSession
**Description**: Represents a conversation between a user and the AI assistant
**Fields**:
- id: string (UUID) - Unique identifier
- userId: string - Reference to the user who owns this session
- title: string - Descriptive title for the session
- createdAt: datetime - Session creation timestamp
- updatedAt: datetime - Last activity timestamp

## Entity: Message
**Description**: Represents an individual message in a chat session
**Fields**:
- id: string (UUID) - Unique identifier
- sessionId: string - Reference to the chat session
- userId: string - Reference to the user who sent the message (null for AI responses)
- role: string ('user'/'assistant') - Role of the message sender
- content: string - The actual message content
- contextChunks: JSON array - Array of cited source chunks from textbook
- metadata: JSON object - Additional metadata
  - selectedText: string - Text that was selected when message was sent
  - chapterId: string - Chapter context for the message
  - timestamp: datetime - When the message was sent
- createdAt: datetime - Message creation timestamp

## Entity: Feedback
**Description**: Represents user feedback on chatbot responses
**Fields**:
- id: string (UUID) - Unique identifier
- messageId: string - Reference to the message being rated
- rating: integer (1-5) - Quality rating of the response
- comment: string (optional) - Additional feedback text
- createdAt: datetime - Feedback creation timestamp
- updatedAt: datetime - Last update timestamp

## Entity: Module
**Description**: Represents a course module containing multiple chapters
**Fields**:
- id: string (UUID) - Unique identifier
- title: string - Module title
- description: string - Module description
- order: integer - Display order in the curriculum
- createdAt: datetime - Creation timestamp
- updatedAt: datetime - Last update timestamp

## Relationships

### User → ChatSession
- One-to-Many: A user can have multiple chat sessions
- Foreign Key: ChatSession.userId → User.id
- Cascade: When user is deleted, their chat sessions are deleted

### ChatSession → Message
- One-to-Many: A chat session contains multiple messages
- Foreign Key: Message.sessionId → ChatSession.id
- Cascade: When session is deleted, all messages are deleted

### Message → Feedback
- One-to-One: A message can have one feedback entry
- Foreign Key: Feedback.messageId → Message.id

### Module → Chapter
- One-to-Many: A module contains multiple chapters
- Foreign Key: Chapter.moduleId → Module.id

## Validation Rules

### User
- Email must be a valid email format
- Name must be 1-100 characters
- Background fields must be one of: 'beginner', 'intermediate', 'expert'
- Preferences.language must be one of: 'en', 'ur'

### Chapter
- Title must be 1-200 characters
- Slug must be URL-friendly and unique
- Content must be valid MDX format
- Learning outcomes must be 1-5 items
- Version must be incremented on updates

### ChatSession
- Title must be 1-200 characters
- User reference must exist

### Message
- Content must be 1-10000 characters
- Role must be 'user' or 'assistant'
- Session reference must exist

### Feedback
- Rating must be between 1 and 5
- Message reference must exist
- One feedback per message

## State Transitions

### User
- State: Unauthenticated → Authenticated (on successful login)
- State: Profile incomplete → Profile complete (on background information completion)

### ChatSession
- State: Active (newly created)
- State: Inactive (after 30 minutes of inactivity)
- State: Archived (after 90 days or user action)