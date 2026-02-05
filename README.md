# 🎯 Habit Tracker

A color belt-themed habit tracker with streak tracking, achievements, and cross-device sync via Firebase.

## Features

- ✅ Unlimited habits
- 🔥 Streak tracking (current & best)
- 📅 28-day visual calendar
- 🟢 Color belt achievements (White → Black Belt)
- ☁️ Cross-device sync with Firebase
- 📱 Mobile-friendly (works great on iOS)

## Deployment Instructions

### 1. Set Up Firebase

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project (or use existing)
3. Enable **Realtime Database**:
   - Go to Build → Realtime Database
   - Click "Create Database"
   - Start in **test mode** (or production mode with rules)
4. Enable **Anonymous Authentication**:
   - Go to Build → Authentication
   - Click "Get Started"
   - Enable "Anonymous" sign-in method
5. Get your Firebase config:
   - Go to Project Settings (gear icon)
   - Scroll down to "Your apps"
   - Click the web icon (`</>`) to add a web app
   - Copy the `firebaseConfig` object

### 2. Update Firebase Configuration

Open `habit-tracker.html` and replace the Firebase config (around line 253) with your values:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    databaseURL: "YOUR_DATABASE_URL",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

### 3. Deploy to Vercel

#### Option A: Deploy via GitHub (Recommended)

1. Create a new GitHub repository
2. Push these files to the repository:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
3. Go to [Vercel](https://vercel.com)
4. Click "Add New Project"
5. Import your GitHub repository
6. Click "Deploy"

#### Option B: Deploy via Vercel CLI

1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in the project directory
3. Follow the prompts

### 4. Firebase Security Rules (Important!)

By default, your database is in test mode (open to anyone). For production, update your Realtime Database rules:

```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```

This ensures users can only read/write their own data.

## Usage

Once deployed:
1. Open the app in your browser
2. Add habits using the input field
3. Mark habits complete each day
4. Watch your streaks grow and unlock achievements!

### On iOS

For a native app experience:
1. Open the deployed site in Safari
2. Tap the Share button
3. Select "Add to Home Screen"

## How Sync Works

- Uses Firebase Anonymous Authentication (no signup required)
- Each device gets a unique ID stored in browser
- Habits sync in real-time across all devices with the same browser/ID
- Falls back to localStorage if Firebase is unavailable

## Achievements

- ⚪ **White Belt** - 3 day streak
- 🟡 **Yellow Belt** - 7 day streak
- 🟠 **Orange Belt** - 14 day streak
- 🟢 **Green Belt** - 30 day streak
- 🔵 **Blue Belt** - 50 day streak
- 🟣 **Purple Belt** - 100 day streak
- ⚫ **Black Belt** - 365 day streak

## Tech Stack

- Vanilla JavaScript (no frameworks needed)
- Firebase Realtime Database
- Firebase Anonymous Auth
- HTML5 + CSS3
- Hosted on Vercel

## License

Free to use and modify!
