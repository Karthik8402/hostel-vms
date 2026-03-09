# 🏨 Vizito — Hostel Visitor Management System

A lightweight, fully frontend-based **Visitor Management System (VMS)** built for hostels. It enables visitors to self-register, generates printable visitor passes with QR codes, and allows wardens to view and export the visitor log — all backed by **Google Sheets** as the database.

---

## 📸 Pages Overview

| Page | Description |
|------|-------------|
| `index.html` | Landing page with hero section and feature highlights |
| `add-visitor.html` | Visitor self-registration form |
| `login.html` | Warden login portal |
| `log.html` | Protected visitor log with pagination and PDF export |
| `rules.html` | Hostel visitor rules and guidelines |

---

## ✨ Features

### For Visitors
- **Self-registration form** — collects Full Name, Email, Phone, Purpose of Visit, and Photo
- **Math CAPTCHA** — simple bot prevention on form submission
- **Auto-generated Visitor ID** — sequential ID stored in `localStorage`
- **Printable Visitor Pass** — opens a popup with visitor photo, details, and a scannable **QR code**
- **Google Sheets integration** — visitor data is automatically submitted to a Google Sheet via Apps Script

### For Wardens
- **Secure login** — credentials validated with a 30-minute session timeout (via `localStorage`)
- **Visitor Log** — paginated table (10 records/page) fetched live from Google Sheets
- **PDF Export** — download the full visitor log as a formatted PDF
- **Refresh** — reload the latest data from Google Sheets on demand
- **Logout** — clears session and redirects to the home page

### General
- Fully **responsive** layout with mobile hamburger navigation
- Smooth **AOS (Animate on Scroll)** entry animations throughout
- **SweetAlert2** popups for feedback, errors, and confirmations

---

## 🗂️ Project Structure

```
hostel-vms/
├── index.html          # Home / landing page
├── add-visitor.html    # Visitor registration form
├── login.html          # Warden login
├── log.html            # Visitor log (warden-protected)
├── rules.html          # Hostel rules & guidelines
├── tailwind.config.js  # Tailwind CSS configuration
└── libs/
    ├── tailwind.js         # Tailwind CSS (local CDN build)
    ├── sweetalert2.all.min.js
    ├── sweetalert2.min.css
    ├── aos/
    │   ├── aos.js
    │   └── aos.css
    └── images/
        ├── logo.jpg
        ├── index.jpeg
        ├── index1.jpeg
        └── rules.jpg
```

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| HTML5 / CSS3 | Page structure and styling |
| Vanilla JavaScript | All interactivity and logic |
| [Tailwind CSS](https://tailwindcss.com/) | Utility-first styling framework |
| [SweetAlert2](https://sweetalert2.github.io/) | Modal dialogs and toast notifications |
| [AOS](https://michalsnik.github.io/aos/) | Scroll-based entry animations |
| [jsPDF](https://github.com/parallax/jsPDF) + AutoTable | PDF generation and export |
| [QRCode.js](https://github.com/nicktindall/cyclon.p2p-rtc-session) | QR code generation on visitor pass |
| [Lucide Icons](https://lucide.dev/) | SVG icon set (used in log pagination) |
| Google Apps Script | Serverless backend — reads/writes Google Sheets |

---

## 🚀 Getting Started

This is a **static web app** — no build step or server required.

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/hostel-vms.git
   cd hostel-vms
   ```

2. **Open in a browser**
   - Simply open `index.html` in any modern browser, or
   - Use a local server (e.g., VS Code Live Server extension) for best results

3. **Configure Google Sheets backend** *(optional — required for live data)*
   - Create a Google Sheet and deploy a Google Apps Script Web App
   - Replace the Apps Script URLs in `add-visitor.html` and `log.html` with your own endpoints

---

## 🔐 Authentication

The warden login uses **localStorage-based session management**:
- On successful login, `wardenLoggedIn = "true"` and a `loginTime` timestamp are stored
- The visitor log page checks for a valid session on load; sessions expire after **30 minutes**
- Logging out clears session data and redirects to the home page

> ⚠️ This is a client-side only auth mechanism suitable for educational/demo use. For production, replace with a proper server-side authentication system.

---

## 📄 Visitor Pass

On successful registration, a new browser window opens displaying:
- Visitor photo (circular crop)
- Auto-generated Visitor ID
- Full visitor details (name, email, phone, purpose, date & time)
- Scannable **QR code** containing all visitor information
- A **Print** button for physical badge issuance

---

## 📦 Dependencies (CDN — used in `log.html`)

```
https://unpkg.com/lucide@latest
https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js
https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.28/jspdf.plugin.autotable.min.js
https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js  (loaded in visitor pass popup)
```

All other libraries (Tailwind, SweetAlert2, AOS) are bundled locally under `libs/`.

---

## 📜 License

This project was created as a **college Web Programming assignment**.  
© 2025 Vizito Company. All rights reserved.
