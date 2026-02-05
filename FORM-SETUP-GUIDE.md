# CrispClaws™ Lead CRM
## Google Form Setup Guide

### Step 1: Create Your Google Form
Go to **https://forms.google.com** and create a new form:

**Form Title:** CrispClaws - Bot Inquiry

**Questions (in this order):**
1. 📛 Your Name (Short answer)
2. 📧 Email Address (Email validation) ← IMPORTANT: Check "Required"
3. 💬 Tell us about your project (Paragraph text - optional)

**Settings:**
- Click **Settings** (gear icon) → ✅ Collect email addresses
- Click **Confirmation message** → ✅ Show confirmation message
- Add this confirmation text:

> Thanks [Name]! 🙏 We've received your inquiry and will get back to you within 24 hours.

**Get Your Form URL:**
- Click **Send** → **Link** → Copy the URL
- **Form ID** is the part after `/d/e/` → `/viewform?usp=sf_link`

---

### Step 2: Connect to Spreadsheet (Auto CRM)
1. Click **Responses** tab
2. Click **Link to Sheets** icon (📊)
3. Click **Create new spreadsheet**
4. Name it "CrispClaws Leads"

This spreadsheet is your CRM! It auto-captures all submissions.

---

### Step 3: Auto-Respond with Thank You Email

**Option A: Simple Confirmation (No Code)**
- In Form Settings → Confirmation message → Enable
- Text: *"Thanks! We've received your inquiry. Check your inbox for a confirmation."*

**Option B: Automatic Email (Copy-Paste Script)**

1. Open your **Responses Spreadsheet**
2. Click **Extensions** → **Apps Script**
3. Delete any code there and paste this:

```javascript
function onFormSubmit(e) {
  var responses = e.values;
  var timestamp = responses[0];
  var email = responses[1];
  var name = responses[2];
  var project = responses[3] || "No details provided";
  
  var subject = "Thanks for reaching out to CrispClaws™! 🦞";
  var message = `
Hi ${name},

Thanks for your interest in our bot building services!

We've received your inquiry${project !== "No details provided" ? " with details about: " + project : ""}. 
Our team will review it within 24 hours.

💬 Quick tip: The more details you share about your project, the faster we can help!

Talk soon,
Justin & The CrispClaws™ Team
🦞

---
CrispClaws™ | OpenClaw bot builders
https://nemu-crisp.github.io/openclaw-services/5/
`;
  
  GmailApp.sendEmail(email, subject, message);
}
```

4. Click **Save** (floppy disk icon) → Name it "AutoResponder"
5. Click **Run** (▶️) → Authorize access
6. Click **Triggers** (clock icon) → **Add Trigger**
7. Set:
   - Choose which function runs: `onFormSubmit`
   - Select event source: `From spreadsheet`
   - Select event type: `On form submit`
9. Click **Save**

✅ Done! Everyone who submits will get an automatic thank you email.

---

### Step 4: Update Your Landing Page

Replace the form iframe in `lead-form.html`:

```html
<iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true" 
        width="100%" height="500" frameborder="0" marginheight="0" marginwidth="0">
    Loading...
</iframe>
```

Replace `YOUR_FORM_ID` with your actual form ID.

---

### Need Help?

- 📧 Email me your Form ID and I'll finish the setup
- 📹 Google Forms tutorial: youtube.com/watch?v=ShcR4ZfFbDQ
