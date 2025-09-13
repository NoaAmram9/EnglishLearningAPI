# English Learning Chat App - Setup Guide

## 🎯 Overview
אפליקציה ללימוד אנגלית עם בינת מלאכותית שכוללת זיהוי קול, תיקון דקדוק ושיחות אינטראקטיביות.

## 🛠 Tech Stack
- **Frontend**: React 18 + Vite
- **Backend**: ASP.NET Core 8 + C#
- **AI**: OpenAI GPT-3.5 API
- **Speech**: Web Speech API (Chrome/Edge)
- **Styling**: Tailwind CSS + Lucide Icons

## 📋 Prerequisites

### General Requirements
- Node.js 18+ 
- .NET 8 SDK
- Visual Studio 2022 או VS Code
- Chrome/Edge browser (for Speech API)
- OpenAI API Key

### Getting OpenAI API Key
1. Go to [OpenAI Platform](https://platform.openai.com)
2. Create an account or sign in
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key (keep it secure!)

## 🚀 Backend Setup (C# ASP.NET Core)

### 1. Create the Project
```bash
mkdir EnglishLearningAPI
cd EnglishLearningAPI
dotnet new webapi
```

### 2. Install Required Packages
```bash
dotnet add package Microsoft.AspNetCore.OpenApi
dotnet add package Swashbuckle.AspNetCore
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package System.Text.Json
```

### 3. Project Structure
```
EnglishLearningAPI/
├── Controllers/
│   └── ChatController.cs
├── Models/
│   └── ChatModels.cs
├── Services/
│   ├── OpenAIService.cs
│   └── GrammarCorrectionService.cs
├── Program.cs
├── appsettings.json
└── EnglishLearningAPI.csproj
```

### 4. Configure appsettings.json
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "OpenAI": {
    "ApiKey": "YOUR-OPENAI-API-KEY-HERE",
    "Model": "gpt-3.5-turbo",
    "MaxTokens": 1000
  }
}
```

### 5. Run the Backend
```bash
dotnet run
```
Backend will run on `https://localhost:7000`

### 6. Test the API
Open browser and go to: `https://localhost:7000/swagger`

## 🎨 Frontend Setup (React)

### 1. Create React App
```bash
npx create-react-app english-learning-frontend
cd english-learning-frontend

# Or with Vite (recommended)
npm create vite@latest english-learning-frontend -- --template react
cd english-learning-frontend
npm install
```

### 2. Install Dependencies
```bash
npm install lucide-react
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### 3. Configure Tailwind CSS

**tailwind.config.js:**
```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

**src/index.css:**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 4. Update API Base URL
In the React component, update the API_BASE_URL:
```javascript
const API_BASE_URL = 'https://localhost:7000/api';
```

### 5. Run the Frontend
```bash
npm run dev
```
Frontend will run on `http://localhost:5173` (Vite) or `http://localhost:3000` (CRA)

## 🔧 Development Configuration

### CORS Configuration
The backend is already configured to allow requests from React development servers:
- `http://localhost:3000` (Create React App)
- `http://localhost:5173` (Vite)

### HTTPS in Development
For production, make sure to:
1. Use HTTPS for both frontend and backend
2. Update CORS settings for your production domain
3. Secure your OpenAI API key using environment variables

## 🌟 Features Implemented

### Core Features
- ✅ **Voice Recognition**: Real-time speech-to-text
- ✅ **AI Conversations**: ChatGPT-powered responses
- ✅ **Grammar Correction**: Automatic error detection and correction
- ✅ **Text-to-Speech**: Bot responses are spoken aloud
- ✅ **Random Topics**: Auto-generated conversation starters
- ✅ **Scoring System**: Points for correct messages
- ✅ **Progress Tracking**: Session statistics and streaks

### Advanced Features
- ✅ **Multiple Difficulty Levels**: Beginner, Intermediate, Advanced
- ✅ **Real-time Corrections**: Instant feedback on grammar errors
- ✅ **Conversation History**: Maintains context throughout session
- ✅ **Audio Controls**: Play button for each bot message
- ✅ **Session Management**: Reset and restart capabilities
- ✅ **Feedback System**: User rating and comments
- ✅ **Responsive Design**: Works on desktop and mobile

### Additional Features Added
- 🔥 **Streak Counter**: Track consecutive correct messages
- 📊 **Session Analytics**: Message accuracy percentage
- 💡 **Learning Tips**: Helpful hints for users
- ⚙️ **Settings Panel**: Customize level and preferences
- 🎯 **Topic Variety**: 10+ conversation topics
- 🔊 **Voice Quality**: Natural speech synthesis

## 🐛 Troubleshooting

### Common Issues

**1. Microphone Permission Denied**
- Ensure you're using HTTPS (required for microphone access)
- Check browser permissions for microphone
- Use Chrome or Edge for best compatibility

**2. OpenAI API Errors**
- Verify your API key is correct
- Check if you have sufficient credits
- Ensure API key has proper permissions

**3. CORS Errors**
- Make sure backend CORS is configured correctly
- Check that frontend URL matches CORS settings
- Ensure backend is running before frontend

**4. Speech Recognition Not Working**
- Use Chrome or Edge browsers
- Ensure microphone is connected and working
- Check browser console for error messages

### Development Tips

**Backend Development:**
```bash
# Watch for changes
dotnet watch run

# Check logs
dotnet run --verbosity detailed
```

**Frontend Development:**
```bash
# Check for errors
npm run build

# Development with hot reload
npm run dev
```

## 📱 Mobile Support

The app includes responsive design but speech recognition works best on:
- Chrome for Android
- Safari for iOS (limited support)
- Desktop Chrome/Edge (recommended)


## 📖 Usage Instructions

1. **Start the App**: Allow microphone permissions
2. **Choose Level**: Select beginner/intermediate/advanced
3. **Begin Session**: Click "Start Conversation"
4. **Interact**: Speak or type your responses
5. **Learn**: Receive corrections and continue conversation
6. **Track Progress**: Monitor your score and streak

## 🎓 Learning Features

- **Real-time Corrections**: Immediate grammar and vocabulary feedback
- **Contextual Learning**: Topic-based conversations
- **Progressive Difficulty**: Adapts to your level
- **Speaking Practice**: Voice interaction builds confidence
- **Score Tracking**: Gamified learning experience



---

**Happy Learning! 🎉**

For questions or issues, check the browser console for error messages and ensure all dependencies are properly installed.
