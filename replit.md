# Emoji Tone Detector

## Overview

This is a full-stack web application that analyzes text messages in real-time to detect emotional tone and suggests relevant emojis. The app uses a React frontend with shadcn/ui components and an Express.js backend. It features a keyword-based sentiment analysis system that categorizes text into different emotional tones and provides instant emoji recommendations as users type, similar to a chat application.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a modern full-stack architecture with clear separation between client and server code, plus a browser extension for cross-platform access:

- **Frontend**: React with TypeScript, built using Vite
- **Backend**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM for persistent data storage
- **Browser Extension**: Manifest V3 Chrome extension with local analysis engine
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query for server state management

## Key Components

### Frontend Structure
- **React Router**: Uses Wouter for client-side routing
- **UI Components**: shadcn/ui components for consistent design system
- **Real-time Processing**: Debounced input handling for live analysis
- **State Management**: TanStack Query for API calls and caching
- **Chat-like Interface**: Live emoji display with instant feedback
- **Styling**: Tailwind CSS with custom CSS variables for theming

### Backend Structure
- **Express Server**: RESTful API with middleware for logging and error handling
- **Tone Analysis Engine**: Machine learning-enhanced sentiment analysis system
- **Data Storage**: PostgreSQL database with training data and user corrections persistence
- **API Routes**: Multiple endpoints for analysis, training, corrections, and feedback
- **Machine Learning**: Dynamic weight adjustment based on user feedback and training data
- **Training Data Management**: Comprehensive storage and retrieval of learning examples

### Database Schema
- **tone_analyses table**: Stores analysis results with fields for text, detected tone, confidence, keywords, and emojis
- **training_data table**: Stores user-provided training examples with correct tones and feedback
- **user_corrections table**: Records incorrect predictions and their corrections for learning
- **Drizzle ORM**: Configured for PostgreSQL with migration support for all tables

## Data Flow

1. **Real-time Input**: User types message in textarea component with live analysis
2. **Debounced Processing**: Text changes trigger debounced analysis after 800ms pause
3. **Client Validation**: Zod schema validates input (1-500 characters, minimum 3 chars for analysis)
4. **API Request**: POST to `/api/analyze` endpoint for qualifying text
5. **Tone Analysis**: Server processes text using keyword matching algorithm
6. **Emoji Selection**: System selects relevant emojis based on detected tone
7. **Instant Response**: Primary emoji appears immediately in chat-like interface
8. **Live UI Update**: Emoji updates as user types, with additional options displayed below

### Tone Detection Algorithm
- **Keyword Matching**: Scans text for predefined emotional keywords
- **Scoring System**: Assigns scores based on keyword frequency and matches
- **Confidence Calculation**: Determines confidence level based on keyword density
- **Fallback Logic**: Defaults to neutral tone for ambiguous text

## External Dependencies

### Frontend Dependencies
- **React Ecosystem**: React 18, React DOM, React Hook Form
- **UI Library**: Radix UI primitives, shadcn/ui components
- **Styling**: Tailwind CSS, class-variance-authority, clsx
- **State Management**: TanStack Query
- **Routing**: Wouter
- **Utilities**: date-fns, lucide-react icons

### Backend Dependencies
- **Server**: Express.js, tsx for TypeScript execution
- **Database**: Drizzle ORM, @neondatabase/serverless
- **Validation**: Zod for schema validation
- **Development**: Vite for build tooling, esbuild for production builds

### Development Tools
- **Build System**: Vite with React plugin
- **TypeScript**: Configured for both client and server
- **Replit Integration**: Cartographer plugin and runtime error overlay

## Deployment Strategy

### Development Mode
- **Server**: Started with tsx for hot reloading
- **Client**: Vite dev server with HMR
- **Database**: Configured for PostgreSQL but using in-memory storage

### Production Build
- **Client Build**: Vite builds optimized React bundle to `dist/public`
- **Server Build**: esbuild compiles TypeScript server code to `dist/index.js`
- **Asset Serving**: Express serves static files from build directory
- **Environment**: Requires `DATABASE_URL` environment variable for database connection

### Database Setup
- **Migration**: `db:push` script runs Drizzle migrations
- **Connection**: Uses Neon serverless PostgreSQL driver
- **Schema**: Centralized in `shared/schema.ts` for type safety across client and server

## Recent Changes

### Real-time Emoji Analysis (January 24, 2025)
- **Live Processing**: Implemented real-time text analysis with 800ms debouncing
- **Chat Interface**: Redesigned UI to show instant emoji feedback as users type
- **Performance**: Optimized analysis to trigger only for text longer than 2 characters
- **User Experience**: Removed manual "Analyze" button, making interaction seamless like chat apps
- **Visual Feedback**: Added "thinking" emoji (🤔) during analysis processing
- **Enhanced Layout**: Primary emoji displays prominently with additional options below

### Enhanced Sentiment Analysis (January 24, 2025)
- **Context-Aware Processing**: Advanced algorithm considers full sentence structure and word relationships
- **Negation Handling**: Detects negative phrases like "not good" and flips sentiment appropriately
- **Intensity Levels**: Three-tier keyword system (strong/medium/light) for nuanced emotion detection
- **Sentence Patterns**: Recognizes common phrases like "can't wait" and "feel sad" for better accuracy
- **Punctuation Analysis**: Enhanced detection of caps, multiple exclamations, ellipsis, and emoticons
- **Smart Confidence Scoring**: Dynamic confidence based on text length, keyword density, and context clarity
- **Mixed Emotion Logic**: Prioritizes specific emotions over general ones when scores are close

### Machine Learning Training System (January 24, 2025)
- **Training Interface**: Dedicated page for training the AI with user-provided examples
- **User Corrections**: System to report and learn from incorrect predictions
- **Feedback Loop**: Real-time feedback mechanism to improve accuracy over time
- **Dynamic Learning**: Algorithm automatically updates weights based on training data
- **Training Statistics**: Dashboard showing learning progress and correction patterns
- **Dual-Mode Navigation**: Added navigation between live chat and training interfaces
- **Learning Memory**: System stores and applies learned patterns from user corrections
- **Test Interface**: Built-in testing tool to validate model improvements

### Database Integration (January 24, 2025)
- **PostgreSQL Database**: Migrated from in-memory storage to persistent PostgreSQL database
- **Data Persistence**: All training data, corrections, and analysis results now stored permanently
- **Drizzle ORM**: Complete database schema with tables for tone analyses, training data, and user corrections
- **Database Migration**: Successfully pushed schema changes to PostgreSQL using Drizzle migrations
- **Persistent Learning**: Machine learning improvements now survive server restarts and deployments

### Browser Extension (January 24, 2025)
- **Cross-Platform Extension**: Created full-featured browser extension for Chrome/Edge
- **Real-time Analysis**: Works on any website with text input fields
- **Tooltip Interface**: Shows emoji suggestions in floating tooltips as users type
- **Click-to-Insert**: One-click emoji insertion into any text field or contenteditable element
- **Popup Settings**: Comprehensive settings panel with testing interface
- **Local Analysis**: Embedded sentiment analysis engine for offline functionality
- **Privacy-First**: All processing happens locally, no data sent to servers
- **Content Script Integration**: Seamlessly integrates with existing websites without interference

The application is designed to be easily deployable on platforms that support Node.js applications, with environment-based configuration for different deployment targets. The browser extension provides a complementary cross-platform experience that works on any website, making the emoji detection available wherever users type text online.