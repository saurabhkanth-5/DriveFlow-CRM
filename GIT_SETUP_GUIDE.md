# 🛠️ Git Setup Guide — DriveFlow CRM

This guide tells you **exactly** what to do with these files, step by step.  
No prior Git experience needed.

---

## WHAT YOU'LL END UP WITH

- A public GitHub repository at: `https://github.com/YOUR_USERNAME/DriveFlow-CRM`
- All 4 HTML mockups viewable live via GitHub Pages
- A professional README that impresses reviewers
- A link you can add to your assignment doc and portfolio

---

## PART 1 — Install Git (if not already installed)

### Check if Git is installed
Open Terminal (Mac/Linux) or Command Prompt (Windows) and type:
```
git --version
```
If you see a version number (e.g. `git version 2.39.0`), skip to Part 2.

### Install Git
- **Windows:** Download from https://git-scm.com/download/win — install with default settings
- **Mac:** Run `xcode-select --install` in Terminal, or install from https://git-scm.com/download/mac
- **Linux:** Run `sudo apt install git` (Ubuntu) or `sudo yum install git` (Fedora)

### Configure your identity (one-time setup)
```bash
git config --global user.name "Your Full Name"
git config --global user.email "your@email.com"
```

---

## PART 2 — Create the GitHub Repository

1. Go to **https://github.com** and sign in (or create a free account)
2. Click the **+** button (top right) → **New repository**
3. Fill in:
   - **Repository name:** `DriveFlow-CRM`
   - **Description:** `Product design for an intelligent lead management CRM for auto dealerships`
   - **Visibility:** ✅ Public  ← IMPORTANT for DeltaX to view it
   - **Add a README file:** ❌ Leave UNCHECKED (we have our own)
4. Click **Create repository**
5. You'll see a page with a URL like: `https://github.com/YOUR_USERNAME/DriveFlow-CRM`
   **Copy this URL** — you'll need it in the next step.

---

## PART 3 — Upload the Files

### Option A: Upload via GitHub Website (easiest — no Terminal needed)

1. On your new empty repo page, click **"uploading an existing file"** (or drag files directly)
2. Open the `DriveFlow-CRM` folder on your computer
3. **Drag ALL files and folders** into the GitHub upload area:
   - `README.md`
   - `GIT_SETUP_GUIDE.md`
   - `mockups/` folder (with all 4 HTML files)
   - `product-design/` folder
   - `wireframes/` folder
4. At the bottom, add a commit message: `Initial commit — product design files`
5. Click **Commit changes**

✅ Done! Your repo is live.

---

### Option B: Upload via Terminal (recommended — looks more professional)

**Step 1: Navigate to your files**
```bash
# On Mac/Linux:
cd ~/Downloads/DriveFlow-CRM

# On Windows (Command Prompt):
cd C:\Users\YourName\Downloads\DriveFlow-CRM
```

**Step 2: Initialise Git**
```bash
git init
```

**Step 3: Add all files**
```bash
git add .
```
The `.` means "add everything in this folder". You should see no errors.

**Step 4: Create your first commit**
```bash
git commit -m "Initial commit: DriveFlow CRM product design"
```

**Step 5: Link to GitHub**
```bash
git remote add origin https://github.com/YOUR_USERNAME/DriveFlow-CRM.git
```
Replace `YOUR_USERNAME` with your actual GitHub username.

**Step 6: Push to GitHub**
```bash
git branch -M main
git push -u origin main
```
GitHub may ask for your username and password. If password doesn't work, use a **Personal Access Token** instead (see below).

---

### Getting a GitHub Personal Access Token (if password fails)

1. GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
2. Click **Generate new token (classic)**
3. Set expiry: 90 days; check the **repo** scope checkbox
4. Click **Generate token** and **copy it immediately** (it won't show again)
5. Use this token as your "password" when Git asks

---

## PART 4 — Enable GitHub Pages (make HTML mockups viewable live)

This lets anyone open your mockups in a browser just from a URL — great for your portfolio.

1. Go to your repo on GitHub
2. Click **Settings** tab (top of repo)
3. Scroll down to **Pages** (in the left sidebar)
4. Under **Source**, select **Deploy from a branch**
5. Branch: `main`, Folder: `/ (root)` → Click **Save**
6. Wait ~60 seconds, then refresh

Your mockups will be live at:
```
https://YOUR_USERNAME.github.io/DriveFlow-CRM/mockups/screen1-lead-listing.html
https://YOUR_USERNAME.github.io/DriveFlow-CRM/mockups/screen2-lead-details.html
https://YOUR_USERNAME.github.io/DriveFlow-CRM/mockups/screen3-pipeline.html
https://YOUR_USERNAME.github.io/DriveFlow-CRM/mockups/screen4-dashboard.html
```

---

## PART 5 — Add Figma Link to README

Once you've built your Figma prototype:

1. In Figma: Share → Change to "Anyone with the link" → Copy link
2. Edit your `README.md` on GitHub (click the pencil icon)
3. Replace `_[Add your Figma link here]_` with your actual Figma URL
4. Scroll down → click **Commit changes**

---

## PART 6 — Add the GitHub Link to Your Assignment Doc

In your Google Doc submission, add a line like:

> **GitHub Repository:** https://github.com/YOUR_USERNAME/DriveFlow-CRM  
> **Live Mockups:** https://YOUR_USERNAME.github.io/DriveFlow-CRM/mockups/screen3-pipeline.html

---

## PART 7 — Take Screenshots for the Assignment Template

The DeltaX template requires you to drop in screenshots of your screens.

1. Open each HTML file in your browser (Chrome recommended):
   - Double-click `screen1-lead-listing.html` to open it
   - Or use the GitHub Pages live URLs from Part 4
2. Make sure your browser window is at full width (1440px ideally)
3. **Take a full-page screenshot:**
   - **Chrome:** Right-click → Inspect → Ctrl+Shift+P → "Capture full size screenshot"
   - **Mac:** Cmd+Shift+4 (drag to select area)
   - **Windows:** Snipping Tool or Win+Shift+S
4. Save the screenshots and paste them into your Google Doc template

> 💡 **Tip for Chrome full-size screenshots:**
> 1. Open Chrome DevTools (F12)
> 2. Click the device toolbar icon (looks like a phone/tablet)
> 3. Set dimensions to 1440 × 900
> 4. Press Ctrl+Shift+P (or Cmd+Shift+P on Mac)
> 5. Type "screenshot" → click "Capture full size screenshot"

---

## COMMON ERRORS

| Error | Fix |
|---|---|
| `git: command not found` | Install Git (see Part 1) |
| `remote origin already exists` | Run `git remote remove origin` then add it again |
| `Authentication failed` | Use a Personal Access Token instead of password (see Part 3) |
| `error: failed to push` | Run `git pull origin main --allow-unrelated-histories` then push again |
| GitHub Pages shows 404 | Wait 2–3 minutes; GitHub Pages takes time to deploy |

---

## CHECKLIST — Before Submitting

- [ ] GitHub repo is **public**
- [ ] All 4 screen HTML files are in the `mockups/` folder
- [ ] README.md has your Figma link filled in
- [ ] Figma file is set to **"Anyone with the link can view"**
- [ ] GitHub Pages is enabled (mockups viewable via URL)
- [ ] Screenshots of all 4 screens taken and added to Google Doc template
- [ ] GitHub repo link added to the Google Doc under "Other Links"
- [ ] Google Doc shared as **"Anyone with the link"**
- [ ] Submitted via the Google Form before deadline

---

*If anything breaks, just use the GitHub website upload method (Option A in Part 3) — it's the most reliable.*
