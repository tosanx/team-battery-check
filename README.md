# Battery Check - Team Retrospective Tool

A modern retrospective tool using the phone battery metaphor to gauge team energy levels.

## Setup Instructions

### Step 1: Firebase Backend Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or use an existing project
3. Enter project name (e.g., "battery-check")
4. Disable Google Analytics (optional)
5. Click "Create project"

#### Configure Firestore Database:

1. In Firebase Console, go to "Build" → "Firestore Database"
2. Click "Create database"
3. Choose "Start in production mode"
4. Select a location closest to your users
5. Click "Enable"

#### Set Firestore Rules:

Go to "Rules" tab and replace with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /battery-check/{document=**} {
      allow read, write: if true;
    }
  }
}
```

**Note:** These are permissive rules for testing. For production, add authentication.

#### Get Firebase Configuration:

1. Go to Project Settings (gear icon)
2. Scroll to "Your apps" → Click web icon (</>) to add a web app
3. Register app (name: "Battery Check")
4. Copy the `firebaseConfig` object
5. Replace the config in `retro-site-modern.html` (lines 9-16):

```javascript
const FIREBASE_CONFIG = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### Step 2: GitHub Pages Deployment

#### Initial Setup:

```bash
# Navigate to project folder
cd /Users/tosan.okegbe/claude-workspace/new-claw

# Initialize git repository
git init

# Add files
git add retro-site-modern.html README.md

# Commit
git commit -m "Initial commit - Battery Check app"

# Create GitHub repository at https://github.com/new
# Then connect it:
git remote add origin https://github.com/YOUR_USERNAME/battery-check.git

# Push to GitHub
git branch -M main
git push -u origin main
```

#### Enable GitHub Pages:

1. Go to your repository on GitHub
2. Click "Settings" tab
3. Click "Pages" in the left sidebar
4. Under "Source", select "main" branch
5. Click "Save"
6. Your site will be live at: `https://YOUR_USERNAME.github.io/battery-check/retro-site-modern.html`

### Step 3: Making Changes After Publishing

```bash
# Edit the file locally
# Then:
git add retro-site-modern.html
git commit -m "Description of changes"
git push

# Changes will appear on your live site within 1-2 minutes
```

## Features

- Session-specific participant data
- Real-time battery level tracking
- Smooth tab transitions (Energy/Mute/Focus)
- Auto-adjusting battery usage percentages
- Draft auto-save per participant
- Update/undo submission functionality
- Team overview with AI-powered Team Read analysis
- Firebase backend with localStorage fallback

## Technology Stack

- Pure HTML/CSS/JavaScript
- Tailwind CSS
- Firebase Firestore
- Wise Design System

## Local Development

Simply open `retro-site-modern.html` in a web browser. Data will be stored in Firebase once configured, with localStorage fallback for offline use.

## Support

For issues or questions, please open an issue on GitHub.
