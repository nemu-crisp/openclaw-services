# CrispClaws™ Landing Page

**🦞 CrispClaws™ | OpenClaw bot builders**

A single, clean landing page for bot development services.

## Live URL
https://nemu-crisp.github.io/openclaw-services/

---

## Formspree Setup (Required)

The form needs your Formspree ID to work:

1. **Create a free Formspree account:** https://formspree.io
2. **Create a new form** with fields: Name, Email, Project Details
3. **Copy your Form ID** (from the form endpoint URL)
4. **Update `index.html`:**
   - Replace `YOUR_FORMSPREE_ID` in the form action
   - Replace `YOUR_FORMSPREE_ID` in the JavaScript

Formspree features (free tier):
- ✅ Email notifications for new submissions
- ✅ Spam filtering
- ✅ Data dashboard
- ❌ Auto-responder (requires paid plan)

---

## Editing the Page

Edit `index.html` directly. It's a self-contained single-file design with embedded CSS and JavaScript.

### To customize:
- **Services:** Find the `<section id="services">` section
- **Pricing:** Find the `<section id="pricing">` section  
- **Form:** Find the `<section id="contact">` section
- **Footer:** Find the `<footer>` element

---

## Auto-Responder Email (Optional)

For automatic thank you emails, upgrade to Formspree Plus ($10/month) or use Google Forms with the Apps Script method in `CRM-SETUP.md`.

---

## Tech Stack
- Pure HTML/CSS/JS (no frameworks)
- GitHub Pages hosting
- Formspree for form handling
