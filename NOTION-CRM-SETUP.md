# CrispClaws™ CRM Setup Guide
## Formspree + Notion Integration

---

## Step 1: Create Notion Database (2 min)

1. Go to **https://notion.so** → Log in / Sign up (free)
2. Click **New Page** → Enter "CrispClaws Leads"
3. Click **⊕ Add a view** → **Table**
4. Rename columns to match this:

| Column Name | Type | Description |
|-------------|------|-------------|
| Name | Title | Lead's name |
| Email | Email | Contact email |
| Project | Text | Project details |
| Status | Select | New → Contacted → Qualified → Closed |
| Source | Select | Website, Referral, Other |
| Date | Date | Auto-captured |
| Notes | Text | Follow-up notes |

5. **Important:** Click **Share** → **Invite** → Add `nemu@crispcode.io` as a member

---

## Step 2: Create Formspree Form (2 min)

1. Go to **https://formspree.io** → Sign up
2. Use email: **nemu@crispcode.io**
3. Click **New Form** → Name it "CrispClaws Leads"
4. Add these fields (in order):
   - **Name** (type: text, required)
   - **Email** (type: email, required)
   - **Project Details** (type: textarea)
5. Click **Form Endpoint** → Copy the URL
   - Looks like: `https://formspree.io/f/xwkrvqbl`

---

## Step 3: Connect Formspree to Notion (1 min)

1. In Formspree → Your form → **Integrations** tab
2. Click **Add Integration** → Search **Notion**
3. Click **Connect Notion**
4. A Notion popup will open → Select your "CrispClaws Leads" database
5. Map the fields:
   ```
   Name field → Name column
   Email field → Email column
   Text field → Project column
   ```
6. Click **Save**

---

## Step 4: Update Landing Page (1 min)

In `index.html`, replace `YOUR_FORMSPREE_ID` with your actual Formspree ID:

```html
<!-- Line ~180 -->
<form action="https://formspree.io/f/YOUR_ID_HERE" method="POST">

<!-- Line ~218 -->
const formspreeEndpoint = 'https://formspree.io/f/YOUR_ID_HERE';
```

---

## Step 5: Set Up Auto-Responder (Optional)

**Option A: Formspree Plus ($10/mo)**
- Upgrade in Formspree → Billing
- Enable "Email Response" in form settings
- Write your thank you message

**Option B: Free with Make.com (5 min)**
1. Go to **https://make.com** → Sign up (free)
2. Create new scenario:
   - **Trigger:** Formspree → Watch New Submissions
   - **Action:** Gmail → Send Email
3. Connect nemu@crispcode.io Gmail
4. Set up email template:
   ```
   To: {{email}}
   Subject: Thanks for reaching out to CrispClaws™! 🦞
   
   Hi {{name}},
   
   Thanks for your inquiry! We've received your details and will review your project within 24 hours.
   
   Talk soon,
   Justin & The CrispClaws™ Team
   
   ---
   CrispClaws™ | OpenClaw bot builders
   ```
5. Turn on the scenario

---

## Quick Reference

| What You Need | Where to Find It |
|--------------|-----------------|
| Notion Database | https://notion.so → Your workspace |
| Formspree Form | https://formspree.io → Your form |
| Formspree ID | Formspree → Form → Endpoint URL (last part after `/f/`) |
| Make.com (optional) | https://make.com → Scenarios |

---

## Need Help?

- **Formspree docs:** https://formspree.io/docs
- **Notion docs:** https://notion.so/help
- **Make.com docs:** help.make.com

---

## What Happens Next

1. Visitor fills out form on website
2. Formspree receives submission
3. ✅ Auto-adds to Notion database
4. 🔔 Notifies you (configure in Formspree settings)
5. 💼 You manage leads in Notion
