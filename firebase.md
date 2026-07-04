# Connecting Firebase (Google sign-in + cross-device progress)

Right now progress tracking (`public/progress-store.js`) is local-only: it lives in
each learner's browser via `localStorage`, keyed `lsa_progress_v1`. It already
tracks `visited` and `completed` per topic and powers the checkmarks on the
Chemistry map and the `/progress.html` page. To upgrade it to real Google
accounts + cross-device sync, do this:

## 1. Create the Firebase project
1. Go to https://console.firebase.google.com → **Add project**. Any name is fine
   (e.g. "lizard-spock-stem").
2. Skip Google Analytics unless you want it — not needed here.

## 2. Enable Google sign-in
1. In the left nav: **Build → Authentication → Get started**.
2. Under **Sign-in method**, enable **Google**. Pick a support email.
3. Under **Settings → Authorized domains**, add every domain this site will be
   served from — your production domain, and (while testing here) the
   sandbox preview domain shown in your browser's address bar. Google sign-in
   fails silently on unlisted domains, so this step is the #1 cause of
   "nothing happens when I click sign in."

## 3. Enable Firestore (where progress gets stored per account)
1. **Build → Firestore Database → Create database**.
2. Start in **production mode** (we'll add rules below).
3. Pick any region close to your users.
4. Once created, go to **Rules** and paste:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /progress/{uid} {
         allow read, write: if request.auth != null && request.auth.uid == uid;
       }
     }
   }
   ```
   This lets a signed-in user read/write only their own progress document —
   nobody else's.

## 4. Register a Web App and grab the config
1. Project Settings (gear icon) → **Your apps → Add app → Web** (`</>` icon).
2. Give it any nickname, skip Firebase Hosting unless you want it.
3. Copy the `firebaseConfig` object it shows you — looks like:
   ```js
   const firebaseConfig = {
     apiKey: "AIza...",
     authDomain: "your-project.firebaseapp.com",
     projectId: "your-project",
     storageBucket: "your-project.appspot.com",
     messagingSenderId: "...",
     appId: "1:...:web:..."
   };
   ```
   This config is safe to embed in client-side code (it's not a secret) —
   the Firestore rules above are what actually protects the data.

## 5. Send me the config
Paste that object into the chat. I'll then:
- Load the Firebase Auth + Firestore SDKs (via `<script>` in each page's
  `<helmet>`, same pattern already used for other shared includes).
- Swap `progress-store.js`'s storage layer from `localStorage` to Firestore,
  keyed by the signed-in user's `uid`, while keeping the exact same
  `Progress.markVisited / markCompleted / get / onChange` API — so nothing
  else on the site needs to change.
- Wire the "Sign in with Google" button on `/progress.html` (currently a
  disabled stub) to a real Google popup sign-in, with a signed-out fallback
  that keeps using local storage so the site still works without an account.
- Merge any local progress into the account on first sign-in, so testing
  done before login isn't lost.

## Things worth deciding when you're ready
- Whether anonymous/guest use should remain fully supported (recommended —
  not every 10-year-old has a Google account) or whether sign-in becomes
  required at some point.
- Whether a teacher/parent view of a learner's progress is wanted later —
  that would need a small amount of extra Firestore structure (e.g. a
  "classroom" or "linked accounts" collection), not just per-user documents.
