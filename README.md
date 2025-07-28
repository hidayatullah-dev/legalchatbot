# LegalRAG - Legal Document Analysis with AI

A comprehensive legal document analysis web application using RAG (Retrieval-Augmented Generation) architecture. Upload legal documents, get AI-powered summaries, and chat with your documents using advanced language models.

## Features

- **Document Upload**: Support for PDF and DOCX files with drag-and-drop interface
- **AI-Powered Analysis**: Automatic contract summarization with key information extraction
- **Interactive Chat**: Ask questions about your documents with citation-backed responses
- **Professional UI**: Modern, responsive design optimized for legal professionals
- **Real-time Processing**: Live status updates during document processing

## Tech Stack

### Frontend
- React 18 with TypeScript
- Vite for fast development and building
- Tailwind CSS for styling
- shadcn/ui component library
- TanStack Query for state management
- Wouter for routing

### Backend
- Node.js with Express
- Groq API with Llama-3.1-8b-instant model
- In-memory storage for development
- Mammoth for DOCX text extraction
- Document chunking and vector search

## Deployment

### Netlify Deployment

This application is configured for deployment on Netlify with serverless functions.

#### Prerequisites
1. Netlify account
2. Groq API key

#### Deployment Steps

1. **Connect to Netlify**
   - Fork this repository
   - Connect your GitHub repository to Netlify
   - Netlify will automatically detect the `netlify.toml` configuration

2. **Environment Variables**
   Set the following environment variables in your Netlify dashboard:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

3. **Deploy**
   - Push to your main branch or trigger a manual deploy
   - Netlify will automatically build and deploy your application

#### Build Configuration

The application uses:
- **Build Command**: `vite build && esbuild netlify/functions/api.ts --platform=node --packages=external --bundle --format=esm --outdir=netlify/functions --out-extension:.js=.mjs`
- **Publish Directory**: `dist`
- **Functions Directory**: `netlify/functions`

### Local Development

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Set Environment Variables**
   Create a `.env` file with:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

3. **Start Development Server**
   ```bash
   npm run dev
   ```

4. **Open Browser**
   Navigate to `http://localhost:5000`

## Usage

1. **Upload Document**: Drag and drop a PDF or DOCX file
2. **Wait for Processing**: The system will extract text and generate a summary
3. **Review Summary**: View extracted parties, key dates, and obligations
4. **Chat with Document**: Ask questions about your document content
5. **Get Citations**: All responses include source citations

## API Endpoints

- `GET /api/documents` - List all uploaded documents
- `POST /api/documents/upload` - Upload a new document
- `GET /api/documents/:id` - Get document details
- `GET /api/documents/:id/summary` - Get document summary
- `POST /api/documents/:id/chat` - Chat with document
- `GET /api/documents/:id/messages` - Get chat history

## Limitations

- **PDF Processing**: Currently uses placeholder text extraction (for full PDF support, integrate a cloud-based PDF service)
- **Storage**: Uses in-memory storage (data resets on server restart)
- **File Size**: Maximum 10MB per document
- **Rate Limits**: Subject to Groq API rate limits

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

MIT License - see LICENSE file for details

## Support

For issues and questions, please create an issue in the GitHub repository.