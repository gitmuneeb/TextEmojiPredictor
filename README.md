# Text Emoji Predictor
A comprehensive emoji sentiment analysis platform that provides intelligent emoji recommendations across multiple platforms, including a web application and browser extension.
## Features
🧠 **Real-time Emotional Tone Detection** - Advanced sentiment analysis that understands context, negations, and emotional intensity
😊 **Smart Emoji Suggestions** - Machine learning-powered emoji recommendations based on detected emotions
🎯 **Continuous Learning** - Training system that improves accuracy through user feedback and corrections
📱 **Browser Extension** - Cross-platform Chrome extension that works on any website with text inputs
💾 **Persistent Storage** - PostgreSQL database that remembers learning patterns and user corrections
⚡ **Real-time Analysis** - Live emoji suggestions as you type with customizable delay settings
🔧 **Professional UI** - Modern React interface with shadcn/ui components and smooth animations
## Quick Start
### Web Application
1. **Install Dependencies**
   ```bash
   npm install
Set up Database

npm run db:push
Start Development Server

npm run dev
Access the Application

Open your browser to the development URL
Start typing messages to see real-time emoji suggestions
Visit the "AI Training" section to improve the model
Browser Extension
Install Extension

Navigate to chrome://extensions/
Enable "Developer mode"
Click "Load unpacked"
Select the browser-extension folder
Use Extension

Go to any website (Gmail, Twitter, Facebook, etc.)
Start typing in text fields
See emoji suggestions appear in floating tooltips
Click emojis to insert them instantly
Architecture
Frontend (React + TypeScript)
Real-time Analysis: Debounced input processing with live emoji display
Chat-like Interface: Instant feedback similar to messaging applications
Training Interface: Dedicated ML training system for user corrections
Modern UI: shadcn/ui components with Tailwind CSS styling
Backend (Express.js + TypeScript)
Advanced Analysis Engine: Context-aware sentiment analysis with negation handling
ML Training System: Dynamic weight adjustment based on user feedback
RESTful API: Comprehensive endpoints for analysis, training, and corrections
Database Integration: Persistent storage with Drizzle ORM
Database (PostgreSQL)
tone_analyses: Stores analysis results with confidence scores
training_data: User-provided training examples for ML improvement
user_corrections: Records incorrect predictions for learning
Browser Extension (Manifest V3)
Content Script: Monitors text inputs across all websites
Local Analysis: Embedded sentiment engine for offline functionality
Popup Interface: Settings and testing functionality
Privacy-First: All processing happens locally
Technology Stack
Frontend: React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui
Backend: Express.js, TypeScript, tsx
Database: PostgreSQL, Drizzle ORM, Neon serverless
State Management: TanStack Query
Routing: Wouter
Validation: Zod schemas
Extension: Chrome Manifest V3, Content Scripts, Service Worker
Sentiment Analysis Algorithm
The system uses a sophisticated multi-layer analysis approach:

Keyword Matching: Three-tier intensity system (strong/medium/light) for nuanced detection
Context Awareness: Full sentence structure analysis and word relationship understanding
Negation Handling: Proper processing of phrases like "not good" vs "good"
Phrase Recognition: Detection of common expressions like "can't wait" and "feel sad"
Punctuation Analysis: Enhanced detection of caps, exclamations, ellipsis, and emoticons
Confidence Scoring: Dynamic confidence based on text length, keyword density, and context clarity
Mixed Emotion Logic: Prioritizes specific emotions over general ones when scores are close
API Endpoints
POST /api/analyze - Analyze text and get emoji suggestions
GET /api/tone-categories - Get available tone categories
POST /api/training-data - Submit training examples
GET /api/training-data - Retrieve training data
POST /api/user-corrections - Report incorrect predictions
GET /api/user-corrections - Get correction history
Development
File Structure
├── client/                 # React frontend
│   ├── src/
│   │   ├── pages/         # Application pages
│   │   ├── components/    # Reusable UI components
│   │   ├── hooks/         # Custom React hooks
│   │   └── lib/           # Utility functions
├── server/                # Express.js backend
│   ├── index.ts          # Server entry point
│   ├── routes.ts         # API routes
│   ├── storage.ts        # Database storage layer
│   └── db.ts             # Database connection
├── shared/               # Shared types and schemas
├── browser-extension/    # Chrome extension
└── browser-extension-simple/  # Simplified extension version
Environment Variables
DATABASE_URL - PostgreSQL connection string
NODE_ENV - Environment (development/production)
Scripts
npm run dev - Start development server
npm run build - Build for production
npm run db:push - Push database schema changes
Browser Extension Features
Universal Compatibility: Works on all websites with text inputs
Real-time Suggestions: Emoji tooltips appear as you type
Click to Insert: One-click emoji insertion into any text field
Customizable Settings: Adjust delay, confidence display, and more
Privacy-Focused: All analysis happens locally in your browser
Offline Functionality: Works without internet connection
Machine Learning Training
The system continuously improves through:

User Corrections: Report incorrect predictions to improve accuracy
Training Examples: Provide correct tone examples for specific text
Feedback Loop: System automatically adjusts weights based on corrections
Persistent Learning: All improvements are saved to the database
Test Interface: Built-in testing to validate model improvements
Deployment
Web Application
Build the application: npm run build
Set up PostgreSQL database with DATABASE_URL
Deploy to your preferred platform (Vercel, Netlify, Railway, etc.)
Browser Extension
Package the browser-extension folder
Submit to Chrome Web Store for review
Users can install directly from the store
Contributing
Fork the repository
Create a feature branch
Make your changes
Test thoroughly (both web app and extension)
Submit a pull request
Privacy & Security
Local Processing: Browser extension processes all text locally
No Data Collection: Personal text is never sent to external servers
Secure Storage: Database uses environment variables for credentials
HTTPS Only: All production deployments should use HTTPS
Performance
Lightweight: Minimal impact on page load times
Efficient: Debounced analysis prevents excessive processing
Scalable: Database design supports high-volume usage
Optimized: Vite build system for fast development and production builds
License
All rights reserved. This project is proprietary software.

Support
For issues, feature requests, or questions:

Check the documentation in this README
Review the browser extension README for extension-specific issues
Test with the simple extension version if the main extension has problems
Check browser console for error messages
Built with ❤️ for better digital communication through intelligent emoji suggestions.

This is the complete README text that you can copy and paste when uploading your project to GitHub. It provides comprehensive documentation about your emoji tone detector platform, including setup instructions, architecture details, and usage guidelines for both the web application and browser extension.
