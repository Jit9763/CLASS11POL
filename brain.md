# 🧠 CLASS11POL Master Brain & Architecture Specification

## 📌 Project Overview
**Class 11 Political Science (NCERT) Master Educational Portal**
A high-performance, visually rich, interactive web application designed for students and teachers. Features 100+ page equivalent comprehensive notes (`copy_master_ch*.html`), interactive Q&A banks (`qa_master_ch*.html`), projector-optimized typography, and custom 16:9 2D vector educational visual cards.

---

## 📁 Directory & File Architecture

```
CLASS11POL/
├── index.html                    # Main Portal Page (Chapter Grid & Search)
├── notes_html_view.html          # Dynamic Master Reader for Notes (fetches copy_master_ch*.html)
├── qa_html_view.html             # Dynamic Master Reader for Q&A (fetches qa_master_ch*.html)
├── css/
│   └── styles.css                # Global Portal Styling (Dark Theme, Glassmorphism, Gold Accents)
├── js/
│   └── main.js                   # Navigation & Dynamic Chapter Card Rendering
├── images/                       # Educational Visual Assets
│   ├── ch11/                     # Chapter 11 WebP Teaching Cards
│   ├── ch14/                     # Chapter 14 WebP Teaching Cards
│   ├── ch15/                     # Chapter 15 WebP Teaching Cards
│   ├── ch16/                     # Chapter 16 WebP Teaching Cards
│   ├── ch17/                     # Chapter 17 WebP Teaching Cards
│   └── ch18/                     # Chapter 18 WebP Teaching Cards
├── copy_master_ch1.html .. ch18.html  # Production Notes Content Files (Chapters 1 to 18)
├── qa_master_ch1.html .. ch18.html    # Production Q&A Bank Files (Chapters 1 to 18)
├── .gitignore                    # Clean Repository Rules (Excludes build/test artifacts)
└── brain.md                      # [THIS FILE] Central Project Architecture & System Reference
```

---

## 🚫 File Governance & Exclusions Rules

### Production-Only Git Policy
Only core web assets required for live browser deployment are tracked in Git:
- ✅ `index.html`, `notes_html_view.html`, `qa_html_view.html`
- ✅ `copy_master_ch*.html` & `qa_master_ch*.html`
- ✅ `css/`, `js/`, `images/`
- ✅ `.gitignore`, `brain.md`

### Ignored / Excluded Items (`.gitignore`)
The following working/test files must **never** be committed or pushed to GitHub:
- `test_master_ch*.html` (Redundant test files - Permanently deleted)
- `*.json` (Local prompt engineering & temporary metadata)
- `*.zip`, `temp_*` (Raw working archives)
- `*.log` (Development runtime logs)
- `class11_backup/` (Local workspace backups)

---

## 🎨 UI/UX & CSS Design System

### 1. Typography & Contrast (Projector Optimization)
- **Primary Fonts**: `'Noto Sans Devanagari'`, `'Outfit'`, sans-serif.
- **Projector Text Stroke**: `font-weight: 900 !important; -webkit-text-stroke: 1.1px #000000; text-shadow: 0 0 1px #000;` for ultra-sharp classroom visibility.
- **Base Size & Spacing**: `font-size: 28pt !important; line-height: 1.8 !important;`.

### 2. Card & Content Containers
- `.part-container`: White card with rounded corners (`16px`), top accent border (`10px solid #2563eb`), elevation shadow (`box-shadow: 0 10px 25px rgba(0,0,0,0.08)`).
- `.part-container h2`, `.part-header`: Styled blue gradient banners (`linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%)`) with dark blue text (`#1e3a8a`).
- `.cartoon-card`: Styled image wrapper with `.cartoon-caption` highlighting key educational takeaways.

### 3. Interactive Features
- **One-Click Google Docs Clipboard Copy**: Fixed header button (`#mainCopyBtn`) in every `copy_master_ch*.html` executing `copyToGoogleDoc()` to transfer styled rich HTML straight into Google Docs.
- **Font & Layout Resizing**: Built-in keyboard shortcuts (`+` / `-` / `w` / `W`) on viewer pages.

---

## 📚 Course Curriculum Mapping (18 Chapters)

### Book 1: भारत का संविधान: सिद्धांत और व्यवहार (Constitution at Work)
1. `ch1`: संविधान: क्यों और कैसे?
2. `ch2`: भारतीय संविधान में अधिकार
3. `ch3`: चुनाव और प्रतिनिधित्व
4. `ch4`: कार्यपालिका
5. `ch5`: विधायिका
6. `ch6`: न्यायपालिका
7. `ch7`: संघवाद
8. `ch8`: स्थानीय शासन
9. `ch9`: संविधान एक जीवंत दस्तावेज
10. `ch10`: संविधान का राजनीतिक दर्शन

### Book 2: राजनीतिक सिद्धांत (Political Theory)
11. `ch11`: राजनीतिक सिद्धांत: एक परिचय
12. `ch12`: स्वतंत्रता (Freedom)
13. `ch13`: समानता (Equality)
14. `ch14`: सामाजिक न्याय (Social Justice)
15. `ch15`: अधिकार (Rights)
16. `ch16`: नागरिकता (Citizenship)
17. `ch17`: राष्ट्रवाद (Nationalism)
18. `ch18`: धर्मनिरपेक्षता (Secularism)

---

## 🤖 Image Generation Skill Integration
Image automation protocol is maintained in the Global Skill:
`educational_visual_notes` (`C:\Users\jiten\.gemini\config\skills\educational_visual_notes\`)
Script Path: `C:\Users\jiten\.gemini\config\skills\educational_visual_notes\scripts\generate_educational_visuals.py`

Whenever generating educational visual cards:
1. 16:9 minimalist clean 2D vector educational illustrations on pure solid white background.
2. Single top header per card, zero card numbers in titles/labels.
3. DOM Canvas base64 extraction via Playwright CDP (`http://localhost:9222`).
4. Save directly as compressed WebP into `images/ch<ID>/`.
