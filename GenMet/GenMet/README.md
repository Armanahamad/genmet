# GenMet — Community Messaging Platform
### Made with 💓 by @arman.site

---

## 🚀 Quick Start (2 steps)

### Step 1 — Set up Firebase (FREE, takes 5 minutes)

Firebase gives you a **free** real-time database so all users see messages instantly across every device.

1. Go to **https://console.firebase.google.com**
2. Click **"Add Project"** → Name it `GenMet` → Continue → Disable Analytics → **Create Project**
3. Click the **`</>`** (Web) icon → Register app as `GenMet` → Copy the `firebaseConfig` object shown
4. Go to **Build → Realtime Database → Create Database** → Choose your region → **Start in Test Mode** → Enable
5. Go to **Build → Storage → Get Started** → **Test mode** → Done

### Step 2 — Fill in your config

Open **`firebase-config.js`** and replace all `YOUR_*` placeholders with your actual values from Firebase:

```js
const FIREBASE_CONFIG = {
  apiKey: "AIzaSy...",           // ← your value
  authDomain: "genmet-xyz.firebaseapp.com",
  databaseURL: "https://genmet-xyz-default-rtdb.firebaseio.com",
  projectId: "genmet-xyz",
  storageBucket: "genmet-xyz.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc..."
};
```

Save the file. **That's it.** Open `index.html` in any browser — it will be fully real-time.

---

## 📁 File Structure

```
GenMet/
├── index.html          ← The entire app (UI + logic)
├── firebase-config.js  ← Your Firebase keys + admin credentials
└── README.md           ← This file
```

---

## 🔐 Admin Credentials

| Field    | Value       |
|----------|-------------|
| User ID  | `P13843`    |
| Password | `arman.site`|

Change these in `firebase-config.js` if you want.

---

## ✨ Features

### Landing Page
- Animated GenMet wordmark with gradient text
- Live "Registered Members" counter (updates in real-time)
- "Made with 💓 by @arman.site" with Instagram link

### User Sign-Up
- Enter name, about, profile photo, and password
- System generates a unique GenMet ID (e.g. `G84K9`)
- Credential reveal screen with **IMPORTANT NOTE** to save ID + password
- Cannot use "admin" as a name

### User Sign-In
- Login with GenMet ID + password from any device
- Full message history and communities preserved

### Communities
- Browse all communities, join any of them
- Real-time chat: text, images, video, audio, documents (up to 20MB)
- Leave communities anytime
- Emoji picker built-in

### Profile
- Change display name (blocked for admin — stays "admin")
- Update About section
- Upload/change profile photo
- Shows your GenMet ID

### Admin Panel
- **Control tab:**
  - View all members → block / unblock / delete
  - Manage communities → add / edit / delete
  - Broadcast messages → to a specific community, all communities, or a specific member
  - Add admin (only primary admin can do this)
- **Chat tab:**
  - Admin can browse and chat in any community as "admin"
  - Admin messages are highlighted with a crown 👑

### Real-Time
- All messages, media, and admin actions sync instantly to every connected device via Firebase Realtime Database
- Registered member count on landing updates live

---

## 🌐 Hosting (Make it public)

To share GenMet with others:

**Option A — Firebase Hosting (free)**
```bash
npm install -g firebase-tools
firebase login
firebase init hosting   # select your project, set public dir to current folder
firebase deploy
```

**Option B — Netlify (free, easiest)**
1. Go to https://netlify.com
2. Drag-and-drop the `GenMet` folder onto the deploy area
3. Done — you get a live URL instantly

**Option C — GitHub Pages (free)**
1. Push the folder to a GitHub repo
2. Enable Pages in repo Settings → Pages → Deploy from main branch

---

## 🛡️ Security (Before going public)

When you're ready to open to real users, update Firebase Database Rules:

```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "auth != null",
        ".write": "auth != null && auth.uid == $uid"
      }
    },
    "communities": {
      ".read": "auth != null",
      ".write": "auth != null"
    },
    "messages": {
      ".read": "auth != null",
      ".write": "auth != null"
    },
    "memberships": {
      ".read": "auth != null",
      ".write": "auth != null"
    }
  }
}
```

> For now Test Mode works fine while you're setting up and testing.

---

## ⚡ Without Firebase

If you don't configure Firebase, GenMet still works — it uses browser localStorage as a fallback. This means:
- Data is saved only in the current browser
- No real-time sync across devices
- Great for local testing

---

*GenMet — Where Communities Breathe*
