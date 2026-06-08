<div align="center">

# Tamil Anbu — Developer Portfolio
### ⚡ Built with HTML · CSS · JavaScript · Firebase · EmailJS

[![Live Site](https://img.shields.io/badge/🌐_Live_Site-Visit_Portfolio-0a0a0a?style=for-the-badge)](https://tamil-anbu.github.io/tamil-anbu-portfolio/)
[![Made With](https://img.shields.io/badge/Made_With-HTML%2FCSS%2FJS-f0ede8?style=for-the-badge&logo=html5&logoColor=0a0a0a)](https://github.com/tamil-anbu/tamil-anbu-portfolio)
[![Firebase](https://img.shields.io/badge/Database-Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com)
[![EmailJS](https://img.shields.io/badge/Email-EmailJS-4A90E2?style=for-the-badge)](https://emailjs.com)

<br/>

> *A modern, minimal developer portfolio inspired by [Studio Namma](https://studionamma.com/) — featuring a hidden admin inbox, real-time Firebase messaging, and EmailJS-powered replies.*

<br/>

![Portfolio Preview](https://img.shields.io/badge/Status-Live%20%26%20Active-2d7a4f?style=flat-square)
![Theme](https://img.shields.io/badge/Theme-Light%20%2F%20Dark-888?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-f0ede8?style=flat-square)

</div>

---

## 📌 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Setup & Deployment](#-setup--deployment)
- [Admin Inbox](#-admin-inbox--secret-access)
- [Firebase Setup](#-firebase-setup)
- [EmailJS Setup](#-emailjs-setup)
- [Security](#-security)
- [Contact](#-contact)

---

## 👤 About

This is the personal portfolio of **Tamil Anbu**, an entry-level Java Developer based in Erode, Tamil Nadu. The portfolio is designed to showcase projects, skills, and experience in a clean, editorial style — and includes a fully functional contact system with a hidden admin inbox.

```
Name     : Tamil Anbu
Role     : Java Developer (Entry Level)
Location : Erode, Tamil Nadu, India
Email    : tamilanbu2204@gmail.com
LinkedIn : linkedin.com/in/tamil-anbu
```

---

## ✨ Features

| Feature | Description |
|--------|-------------|
| 🎨 **Studio Namma Design** | Editorial layout with outlined/filled hero type, scroll ticker, and accordion skills |
| 🌙 **Dark / Light Mode** | One-click theme toggle, persists across the session |
| 🖱️ **Custom Cursor** | Animated dot + trailing ring cursor |
| 📩 **Contact Form** | Slide-in panel with full validation |
| 🔥 **Firebase Inbox** | All messages saved to Firestore in real time |
| 📬 **EmailJS Notifications** | Instant email alert when someone contacts you |
| 🔐 **Hidden Admin Panel** | Secret keyboard shortcut reveals a private inbox |
| 💬 **Reply System** | Reply to messages directly from the portfolio |
| 🗑️ **Delete Messages** | Remove messages from Firestore with one click |
| 📱 **Scroll Animations** | Smooth reveal animations on scroll |

---

## 🛠 Tech Stack

```
Frontend      →  HTML5, CSS3, Vanilla JavaScript (ES Modules)
Database      →  Firebase Firestore (NoSQL, real-time)
Email         →  EmailJS (contact form + reply system)
Fonts         →  Syne (Google Fonts)
Hosting       →  GitHub Pages
```

---

## 📁 Project Structure

```
tamil-anbu-portfolio/
│
├── index.html          ← Main portfolio file (everything in one file)
└── README.md           ← You are here
```

> The entire portfolio is a **single HTML file** — no build tools, no frameworks, no dependencies to install. Just open and it works.

---

## 🚀 Setup & Deployment

### Option 1 — Run Locally
1. Download `index.html`
2. Open it in any browser
> ⚠️ Firebase features require a live URL to work. Use a local server like VS Code Live Server for local testing.

### Option 2 — Deploy to GitHub Pages (Recommended)

```bash
# 1. Create a new repo on GitHub named:
tamil-anbu-portfolio

# 2. Upload index.html to the repo root

# 3. Go to Settings → Pages → Branch: main → Save

# 4. Your live URL:
https://<your-username>.github.io/tamil-anbu-portfolio/
```

### Option 3 — Netlify Drop
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `index.html`
3. Get a live URL instantly — no account needed

---

## 🔐 Admin Inbox — Secret Access

The portfolio has a **completely hidden admin inbox** — invisible to all visitors.

### How to open it:

```
Press:  Ctrl + Shift + A
```

A login screen appears. Enter your credentials to access the inbox.

### What you can do inside:
- 📥 View all incoming messages in real time
- 📖 Read full message content (name, email, subject, message)
- 🔴 Unread messages are highlighted with a white indicator
- ✉️ Reply directly to the sender via EmailJS
- 🗑️ Delete messages from Firestore

> **No link, no button, no hint** exists anywhere on the public portfolio. Only you know the shortcut.

---

## 🔥 Firebase Setup

This portfolio uses **Cloud Firestore** to store contact form submissions.

### Messages Collection Structure:

```
messages/
└── {auto-id}/
    ├── name        : string   — sender's full name
    ├── email       : string   — sender's email address
    ├── subject     : string   — message subject
    ├── message     : string   — full message body
    ├── read        : boolean  — true after you open it
    └── timestamp   : timestamp — auto-set on submission
```

### Firestore Security Rules (update before 30-day test mode expires):

Go to **Firebase Console → Firestore → Rules** and paste:

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Anyone can create a message (contact form)
    match /messages/{messageId} {
      allow create: if request.resource.data.keys()
        .hasAll(['name','email','message','timestamp']);
      // Only allow read/update/delete from your app
      allow read, update, delete: if true;
    }
  }
}
```

> 💡 For production, replace `allow read, update, delete: if true` with proper auth rules.

---

## 📧 EmailJS Setup

EmailJS handles all outbound emails — contact form notifications and admin replies.

### Services Used:

| Key | Value |
|-----|-------|
| Service ID | `service_50qj2ue` |
| Template ID | `template_q87lftp` |
| Public Key | `cJ7DD02K6rASG7zzN` |

### Email Template Variables:

```
{{from_name}}    — sender's name
{{from_email}}   — sender's email
{{to_name}}      — recipient name
{{subject}}      — email subject
{{message}}      — email body
{{reply_to}}     — reply-to address
```

---

## 🔒 Security

| Concern | Status |
|---------|--------|
| Admin panel visibility | ✅ Hidden — no public link or button |
| Admin credentials | ✅ Hardcoded, not exposed in UI |
| Firebase test mode | ⚠️ Expires in 30 days — update rules before expiry |
| API keys in HTML | ⚠️ Firebase & EmailJS keys are client-side (standard for these services) |
| HTTPS | ✅ Enforced by GitHub Pages |

> **Note:** Firebase and EmailJS keys being in client-side HTML is standard practice for these services. Firebase security is enforced via Firestore Rules, and EmailJS limits sending to your registered domain.

---

## 📬 Contact

Have a question or want to collaborate?

- **Email:** [tamilanbu2204@gmail.com](mailto:tamilanbu2204@gmail.com)
- **LinkedIn:** [linkedin.com/in/tamil-anbu](https://www.linkedin.com/in/tamil-anbu)
- **Portfolio:** [tamil-anbu.github.io/tamil-anbu-portfolio](https://tamil-anbu.github.io/tamil-anbu-portfolio/)

---

<div align="center">

**Designed & Built by Tamil Anbu**

*Inspired by [Studio Namma](https://studionamma.com/)*

⭐ If you like this portfolio, give it a star on GitHub!

</div>
