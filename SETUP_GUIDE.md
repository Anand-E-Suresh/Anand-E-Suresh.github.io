# 🚀 Anand E Suresh — Portfolio Setup Guide

## Admin Credentials
- **Username:** `Appu@257368419`
- **Password:** `Appu@120478`
- You can change these anytime from the Admin Panel → 🔒 Security tab
- After Firebase is set up, credentials are stored in Firestore (not in code)

---

## File Structure
```
index.html            ← Home
admin.html            ← Admin Panel (go here to manage everything)
css/style.css
js/app.js             ← ⚠️ YOU MUST EDIT THIS (Firebase config)
pages/
  about.html
  skills.html
  projects.html
  experience.html
  education.html
  travels.html
  activities.html
  contact.html
```

---

## STEP 1 — Firebase Setup (5 mins)

1. Go to https://console.firebase.google.com
2. Click **"Add project"** → name it `anand-portfolio` → Create
3. **Enable Firestore:** Sidebar → Firestore Database → Create database → **Start in test mode** → Region: `asia-south1` → Done
4. **Enable Storage:** Sidebar → Storage → Get started → Test mode → Done
5. **Get config:** Sidebar → Project Settings (⚙️) → Your apps → click `</>` (Web) → Register app → Copy the config object

---

## STEP 2 — Paste Firebase config

Open `js/app.js` and replace lines 4–11:

```js
const firebaseConfig = {
  apiKey: "PASTE_YOUR_API_KEY",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456",
  appId: "1:123:web:abc"
};
```

---

## STEP 3 — Deploy to GitHub Pages

1. Create GitHub account at https://github.com
2. Create a **new repository** named exactly: `yourusername.github.io`
   - Example: if username is `anandsuresh28`, name it `anandsuresh28.github.io`
3. Upload ALL files from this folder (keep folder structure as-is)
4. Go to repo → **Settings** → **Pages** → Source: **Deploy from branch** → `main` → `/ (root)` → Save
5. Wait 2–3 mins. Site is live at: `https://yourusername.github.io`

---

## STEP 4 — First Login & Setup

1. Visit `https://yourusername.github.io/admin.html`
2. **Username:** `Appu@257368419`
3. **Password:** `Appu@120478`
4. From Admin Panel you can:
   - Add/edit all content
   - Upload photos to travel places & activities
   - Change your password anytime (🔒 Security tab)

---

## How to Change Password Later

1. Login to Admin Panel
2. Go to **🔒 Security** tab
3. Enter your current password, new username, new password
4. Click **Update Credentials**
5. You'll be logged out automatically — log in with new credentials

If you ever get locked out, go to:
**Firebase Console → Firestore → Collection: `adminAuth` → Document: `credentials`**
And manually edit the `username` and `password` fields.

---

## Firestore Security Rules (set after testing)

In Firebase Console → Firestore → Rules:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /siteData/{doc} {
      allow read: if true;
      allow write: if true; // Tighten after setup
    }
    match /adminAuth/{doc} {
      allow read, write: if true;
    }
    match /messages/{doc} {
      allow create: if true;
      allow read, write: if false;
    }
  }
}
```

---

## Social Links
- **Instagram:** already added → https://www.instagram.com/_.__anand._._/
- **LinkedIn / GitHub:** add via Admin Panel → Contact tab

## Tips
- Globe: right-click any location on Google Maps to get lat/lng for travel places
- Photos for activities & travels: upload via Admin Panel modal
- Contact form messages appear in Admin Panel → 📬 Messages tab
