# CrispClaws™ Lead Capture CRM Setup

## Quick Overview
This setup captures leads (name + email) via Google Forms and sends automatic thank you emails.

---

## Step 1: Create Google Form

1. Go to **forms.google.com**
2. Create a new form with fields:
   - **Name** (Short answer)
   - **Email** (Email validation)
   - **Project Description** (Paragraph text - optional)
3. Click **Responses** tab → **Link to Sheets** → **Create new spreadsheet**
4. **Copy the Form URL** (you'll need it below)

---

## Step 2: Enable Auto-Responder Email

In your Google Form:
1. Click **Settings** (top)
2. Enable **Collect email addresses**
3. Click **Responses** → **Get email notifications for new responses** (enable)

For automatic thank you emails, use Google Apps Script:

### Option A: Built-in Response Email (Simple)
1. In Google Forms → Settings → **Confirmation message**
2. Enable **Show confirmation message**
3. Add: *"Thanks [Name]! We've received your inquiry. We'll be in touch within 24 hours."*

### Option B: Auto-Respond via Apps Script (Advanced)

```javascript
// In Google Sheets connected to your form:
// Extensions → Apps Script

function onFormSubmit(e) {
  var responses = e.values;
  var email = responses[1];  // Email field (2nd column)
  var name = responses[2];   // Name field (3rd column)
  
  var subject = "Thanks for reaching out to CrispClaws™!";
  var message = `
Hi ${name},

Thanks for your interest in our bot building services!

We've received your inquiry and our team will review it within 24 hours.

In the meantime, feel free to:
• Browse our portfolio
• Check out our pricing

Talk soon,
The CrispClaws™ Team
🦞

---
CrispClaws™ | OpenClaw bot builders
https://crispclaws.com
`;
  
  GmailApp.sendEmail(email, subject, message);
}

// Save and click ▸ Run once to authorize
// Click Clock icon → Triggers → onFormSubmit → Save
```

---

## Step 3: Update Your Landing Page

Replace `YOUR_FORM_ID` in `lead-form.html` with your actual Google Form ID:

```
https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true
```

Your Form ID is the part after `/d/e/` in your form URL.

---

## Step 4: Update Your Contact Section

Add this CTA to your main landing page to link to the form:

```html
<a href="lead-form.html" class="btn btn-primary">Get a Free Quote</a>
```

---

## Alternative: Use Formspree (No Google Account Required)

If you prefer not to use Google Forms:

1. Sign up at **formspree.io** (free tier includes email notifications)
2. Create a new form
3. Replace the iframe in `lead-form.html` with:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
  <div class="form-group">
    <label class="form-label">Your Name</label>
    <input type="text" name="name" class="form-input" required>
  </div>
  <div class="form-group">
    <label class="form-label">Email Address</label>
    <input type="email" name="email" class="form-input" required>
  </div>
  <button type="submit" class="submit-btn">Send Inquiry</button>
</form>
```

**Formspree automatically:**
- Sends you email notifications
- Can send auto-responders (paid feature)
- Stores submissions in your dashboard

---

## CRM Spreadsheet Structure

Your Google Sheet will have columns:
| Timestamp | Email | Name | Project Description |
|-----------|-------|------|---------------------|
| 2026-02-04 21:18:00 | john@example.com | John Smith | Discord bot for my community |

Use this to:
- Track leads
- Prioritize follow-ups
- Export to other tools

---

## Need Help?

- **Google Forms help:** support.google.com/docs
- **Google Apps Script:** developers.google.com/apps-script
- **Formspree:** formspree.io/help
