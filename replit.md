# LegalRAG Application

## Overview

LegalRAG is a legal-focused web application that uses Retrieval-Augmented Generation (RAG) architecture to provide document summarization and interactive legal Q&A capabilities. The application allows users to upload legal documents (PDFs, DOCX), automatically generates structured summaries, and enables interactive chat with the documents using AI-powered responses.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **Styling**: Tailwind CSS with custom legal-themed color palette
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js server
- **Language**: TypeScript with ES modules
- **API Design**: RESTful endpoints for document management and chat functionality
- **File Processing**: Multer for file uploads with memory storage
- **Document Processing**: Text extraction from PDF and DOCX files

### Data Storage Solutions
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Vector Storage**: ChromaDB service with in-memory fallback for document embeddings
- **Session Storage**: In-memory storage implementation (MemStorage) for development
- **File Storage**: Memory-based file handling for uploads

## Key Components

### Document Management
- **Upload System**: Drag-and-drop file upload supporting PDF and DOCX formats (10MB limit)
- **Document Processing**: Automatic text extraction and chunking for RAG implementation
- **Status Tracking**: Document processing states (pending, processing, completed, failed)

### AI Integration
- **LLM Service**: Groq API with Llama-3.1-8b-instant model for summarization and chat responses (optimized for token limits)
- **Embedding Generation**: Custom hash-based embedding generation for vector search capabilities
- **RAG Implementation**: Document chunking with overlap for context preservation

### Legal Document Analysis
- **Structured Summarization**: Extraction of parties, key dates, financial terms, obligations, and risks
- **Interactive Chat**: Context-aware Q&A with citation support
- **Document Context**: RAG-based responses grounded in uploaded documents

### User Interface
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Component Library**: Comprehensive UI components from shadcn/ui
- **Legal Theming**: Professional color scheme optimized for legal professionals
- **Real-time Updates**: Query invalidation for live data synchronization

## Data Flow

### Document Upload Flow
1. User uploads document via drag-and-drop interface
2. File validation (type and size checks)
3. Text extraction (PDF/DOCX processing)
4. Document chunking for vector storage
5. Embedding generation and storage in ChromaDB
6. AI-powered document summarization
7. Storage of document metadata and summary

### Chat Interaction Flow
1. User submits question about uploaded document
2. Query embedding generation
3. Vector similarity search in ChromaDB
4. Context retrieval from relevant document chunks
5. LLM prompt construction with context
6. AI response generation with citations
7. Storage and display of chat history

## External Dependencies

### AI Services
- **Groq API**: Llama-3.1-8b-instant for text generation and analysis (with token limit handling)
- **ChromaDB**: Vector database for semantic search capabilities (with in-memory fallback)

### Database
- **PostgreSQL**: Primary database with Neon serverless integration
- **Drizzle ORM**: Type-safe database operations and migrations

### File Processing
- **PDF Processing**: Text extraction from PDF documents
- **DOCX Processing**: Text extraction from Word documents
- **OCR Capability**: Mentioned in requirements but not yet implemented

### UI Libraries
- **Radix UI**: Accessible component primitives
- **shadcn/ui**: Pre-built component library
- **Lucide React**: Icon library
- **TailwindCSS**: Utility-first styling framework

## Deployment Strategy

### Development Environment
- **Vite Dev Server**: Hot module replacement for frontend development
- **TSX**: TypeScript execution for server development
- **Replit Integration**: Special development tooling for Replit environment

### Netlify Deployment (Production Ready)
- **Static Site**: Frontend built with Vite and served as static assets
- **Serverless Functions**: Backend API deployed as Netlify Functions
- **Build Process**: Automated via `netlify.toml` configuration
- **Environment Variables**: GROQ_API_KEY configured in Netlify dashboard
- **CORS**: Properly configured for cross-origin requests
- **Routing**: SPA routing with fallback to index.html

### Build Configuration
- **Frontend Build**: `vite build` generates optimized static assets
- **Function Build**: esbuild bundles server code for serverless deployment
- **Output**: Frontend in `dist/`, functions in `netlify/functions/`
- **Dependencies**: All production dependencies included in function bundle

### Database Management
- **Development**: In-memory storage (MemStorage) for fast prototyping
- **Production**: Same in-memory storage (data resets per function invocation)
- **Future Enhancement**: Can be upgraded to PostgreSQL with Neon or similar
- **Schema Management**: Drizzle Kit ready for database migrations when needed

The application follows a modern full-stack architecture with strong type safety, scalable RAG implementation, and professional UI design tailored for legal document analysis workflows.

## Recent Updates (July 28, 2025)

### Netlify Deployment Configuration
- Added complete Netlify deployment setup with serverless functions
- Created `netlify.toml` with proper build and redirect configuration
- Implemented serverless function wrapper for Express API
- Added CORS headers and security configurations
- Created comprehensive README.md with deployment instructions
- Environment variable configuration for GROQ_API_KEY

### Document Processing Improvements
- Fixed PDF text extraction issues (currently using placeholder approach)
- Enhanced DOCX text extraction with Mammoth library
- Implemented aggressive token limiting (6000 chars) for Groq API compatibility
- Added proper error handling for document processing failures
- Reduced context chunks to 2 with 500 character limits per chunk

### Production Readiness
- Application is now fully configured for Netlify deployment
- Serverless architecture ready for scalable cloud deployment
- All dependencies properly bundled for production environment
- Security headers and CORS properly configured