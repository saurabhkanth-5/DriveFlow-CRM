# DriveFlow CRM — Full Product Design Document

## Product Name
**DriveFlow CRM**  
*"Intelligent Lead Management for Modern Auto Dealerships"*

DriveFlow CRM is a purpose-built SaaS platform that centralises lead management for automotive dealerships, turning fragmented spreadsheet chaos into a structured, real-time sales workflow. By unifying lead capture, pipeline management, and performance analytics in a single application, DriveFlow helps dealership teams close more cars, faster.

---

## Problem Statement

HSR Motors receives leads from five distinct channels: Facebook Ads, Google Ads, Twitter, website enquiry forms, and offline showroom events. Each of these sources generates prospect data at different times, in different formats, and through different teams. Their current system — a shared spreadsheet — was never designed for this kind of scale or collaboration.

**The core inefficiencies of spreadsheet-based lead tracking:**

1. **No real-time synchronisation.** When one salesperson updates a lead's status, others don't see it immediately. Version conflicts, stale data, and "who called this lead?" confusion are daily occurrences.

2. **No structured workflow.** There's no defined pipeline — leads can sit in the sheet indefinitely with no prompt for the next action. High-scoring leads receive the same (in)attention as low-intent prospects.

3. **No accountability.** Without assignment history, call logs, or timestamps, there's no way to know which salesperson did what, or when. Accountability requires manual chasing.

4. **No automation.** Every lead assignment, follow-up reminder, and status update requires a human decision and a manual edit. This doesn't scale beyond a handful of leads per day.

5. **No analytics.** A business manager cannot quickly answer "which ad channel is bringing us the best leads?" or "which salesperson has the highest conversion rate?" from a spreadsheet without building custom pivot tables every time.

6. **Duplicate leads.** Without automated detection, the same prospect may be called by multiple salespeople, creating a poor customer experience and wasting team time.

---

## User Personas

### Persona 1 — Sales Executive

**Name:** Ankit Verma  
**Role:** Sales Executive, HSR Motors  
**Age:** 26  
**Location:** Bangalore  

**A day in Ankit's life:**  
Ankit arrives at the showroom and opens the shared spreadsheet. He scrolls down 200+ rows trying to find his assigned leads, cross-referencing a separate sheet where assignments were noted two days ago. He calls a lead only to find out a colleague called them yesterday. He writes notes in the "Comments" column, but they get buried as more rows are added. By end of day, he's missed three follow-ups he forgot to note down.

**Goals:**
- Know immediately which leads are his to call today
- See a lead's full context before dialling (source, car interest, previous interactions)
- Log a call outcome in under 10 seconds
- Be reminded when it's time to follow up

**Pain Points:**
- Can't filter leads by his own name quickly
- No call history → calls leads who've already been contacted by colleagues
- Misses follow-ups because there's no reminder system
- Can't quickly see which leads are high-priority

**What Ankit needs from DriveFlow:**
- A personal lead inbox with "My Leads" filter on login
- Lead detail view with full interaction history and car interest context
- One-click call, WhatsApp, and email actions
- Automated follow-up reminders
- Quick status update (one dropdown, one click)

---

### Persona 2 — Business Manager

**Name:** Sunita Mishra  
**Role:** Business Manager, HSR Motors  
**Age:** 38  
**Location:** Bangalore  

**A day in Sunita's life:**  
Sunita needs to present a lead performance report every Monday to the dealership owner. She spends Sunday afternoon manually counting rows in the spreadsheet, building charts in a separate Excel file, and trying to figure out why leads from Google have a lower conversion than Facebook. She can't answer questions like "who is your best closer?" without manually counting wins per salesperson. The process takes 3–4 hours every week.

**Goals:**
- See lead performance at a glance without manual calculation
- Understand which ad channels are most effective
- Identify underperforming salespeople who need coaching
- Track conversion trends over time

**Pain Points:**
- Building reports manually every week is expensive time
- No funnel visibility — doesn't know where leads drop off
- Can't compare salesperson performance without manual tallying
- Can't identify which car models are generating the most interest

**What Sunita needs from DriveFlow:**
- A real-time dashboard that updates automatically
- Source breakdown chart (Facebook vs Google vs others)
- Lead funnel showing conversion at each stage
- Salesperson leaderboard with conversion rates
- Export to PDF/CSV for owner presentations

---

## User Journey

A complete lead moves through DriveFlow in six stages:

**Stage 1 — Lead Captured**  
A prospect submits a Facebook Lead Ad form. The Facebook API integration sends the lead data to DriveFlow in real time. A new record is created in the system with status "New", timestamped and tagged with the campaign name.

**Stage 2 — Lead Assigned**  
The auto-assignment engine checks which salesperson currently has the fewest open leads and assigns the new lead to them via round-robin. The salesperson receives an in-app notification and email. The lead appears in their "My Leads" view on Screen 1.

**Stage 3 — Sales Call**  
The salesperson opens the lead's detail view (Screen 2) to see the car model the prospect expressed interest in, their budget range, and any prior interaction history. They click "Call Now" — the call is logged automatically with a start timestamp. After the call, they update the status to "Contacted" and add a note.

**Stage 4 — Qualification**  
If the customer is genuinely interested, the salesperson moves the lead to "Interested" on the Pipeline board (Screen 3) and schedules a test drive appointment. If the customer is uninterested, they mark "Closed Lost" with a reason code.

**Stage 5 — Follow-up**  
After the test drive, the customer says they need time to think. The salesperson schedules a follow-up reminder for 2 days out. If the salesperson forgets to follow up, the system's overdue automation flags the lead card in amber after 48 hours, prompting re-engagement.

**Stage 6 — Conversion**  
The customer agrees to purchase. The salesperson drags the card to "Closed Won" on the Pipeline, confirming via a modal. The Dashboard (Screen 4) immediately reflects the updated conversion rate. The full interaction history is preserved for quality review.

---

## Information Architecture

### Application Shell
The application uses a persistent shell layout consisting of three zones:

**Left Sidebar (220px, fixed)**  
Contains the primary navigation and user identity. Navigation items: Dashboard, Leads (with live count badge), Pipeline, Reports, Settings. The active item is highlighted with the primary teal colour. User avatar and role are shown at the bottom.

**Top Bar (58px, full width)**  
Contextual to each screen. Contains the page title, global search bar, notification bell (with unread dot), and user avatar/name dropdown. The top bar provides global utility without occupying primary content space.

**Main Content Area (remaining width)**  
Each screen renders its primary content here. The content area uses 28px horizontal padding and 24px vertical padding. Components stack vertically with consistent 14–16px gap between sections.

### Screen Hierarchy
```
App
├── Dashboard (business manager home)
├── Leads
│   ├── Lead Listing (Screen 1)
│   └── Lead Details (Screen 2) — opened from Lead Listing
├── Pipeline (Screen 3)
└── Reports
```

---

## Automation Features

### 1. Auto Lead Assignment
**Trigger:** New lead arrives from any source  
**Logic:** System queries all active salespeople, finds the one with the lowest count of open (non-closed) leads, and assigns the new lead to them. Ties are broken alphabetically.  
**Output:** Lead appears in the assigned salesperson's "My Leads" feed; notification sent.

### 2. Follow-up Reminders
**Trigger:** Lead status changes to "Contacted" with no follow-up scheduled  
**Logic:** System starts a 24-hour timer. If the lead remains in "Contacted" status and no follow-up is scheduled after 24 hours, the system creates a reminder task for the assigned salesperson.  
**Output:** In-app notification + email alert.

### 3. Duplicate Lead Detection
**Trigger:** New lead creation (manual or API)  
**Logic:** System normalises the incoming phone number and email address, then checks against all existing records. If a match is found (exact phone OR exact email), a duplicate warning modal appears before saving.  
**Output:** Warning modal showing the existing lead; user can merge, discard, or save as new.

### 4. Lead Scoring
**Trigger:** On lead creation and after each interaction  
**Logic:** Each lead receives a score out of 10 calculated from: Source Quality (Facebook=8, Google=7, Website=9, Offline=6, Twitter=5), Recency (score decays over time without interaction), Engagement (number of interactions logged).  
**Output:** Score displayed as a star rating and numeric value on Lead Details; used to sort leads within Pipeline columns.

### 5. Overdue Flagging
**Trigger:** Continuous background job (runs every hour)  
**Logic:** Any lead in an active stage (not Closed Won/Lost) with no interaction or status change in the last 48 hours is marked as "overdue".  
**Output:** Amber border on Pipeline card; amber row highlight on Lead Listing; count shown in top bar "overdue" indicator.

---

## Future AI Features

**AI Lead Scoring (ML-powered)**  
Replace the rule-based scoring with a machine learning model trained on historical HSR Motors conversion data. The model learns which combinations of source, car model, budget, time-of-day, and engagement pattern are associated with conversion — producing a more accurate probability score.

**AI Call Summaries**  
Integrate with a call recording API (e.g. Twilio or Exotel). After each call, an AI model transcribes and summarises the conversation: key topics discussed, customer objections raised, buying signals detected, and next action recommended. Summaries appear automatically in the Interaction History.

**Predictive Churn Detection**  
A model that monitors lead engagement patterns and flags leads that are statistically likely to go cold in the next 48 hours — even before the overdue timer fires. The model surfaces these in a "At Risk" view, giving salespeople a chance to re-engage proactively.

**Smart Campaign Attribution**  
Connect ad spend data from Facebook and Google Ads with actual closed deals in DriveFlow. Automatically calculate cost-per-close per campaign and surface this in the Dashboard, enabling the business manager to make data-driven decisions about where to allocate ad budget.
