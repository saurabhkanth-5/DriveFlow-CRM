# 🎨 Figma Build Guide — DriveFlow CRM

Step-by-step instructions to recreate all 4 screens in Figma.  
Use the HTML mockups in the `mockups/` folder as your visual reference — open them in Chrome while you work.

---

## SETUP

### 1. Create a new Figma file
1. Go to https://figma.com → Sign in (free account works)
2. Click **New design file**
3. Rename it: `DriveFlow CRM — HSR Motors`

### 2. Install the Google Fonts plugin
- Figma Menu → Plugins → Browse Plugins
- Search: **Google Fonts** → Install
- You'll need: **DM Sans** and **DM Mono**

### 3. Set up the frame size
All screens are **1440 × 900px** (standard desktop).

1. Press **F** (Frame tool)
2. In the right panel, set Width: `1440`, Height: `900`
3. Duplicate this frame 3 more times (Ctrl+D) — you'll have 4 frames total
4. Name them: `Screen 1 — Lead Listing`, `Screen 2 — Lead Details`, `Screen 3 — Pipeline`, `Screen 4 — Dashboard`
5. Arrange them side by side with 100px gap between each

---

## COLOUR STYLES (set these up first — saves lots of time)

In Figma, create **Colour Styles** so you can reuse them everywhere:

1. In the right panel, click **+** next to Local styles → Colour
2. Add these colours:

| Style Name | Hex Code | Used For |
|---|---|---|
| `Brand/Teal` | `#0D9488` | Primary buttons, active nav, accents |
| `Brand/TealLight` | `#CCFBF1` | Tag backgrounds, hover states |
| `Brand/TealDark` | `#0F766E` | Tag text, dark variant |
| `Neutral/Navy` | `#0F172A` | Sidebar background |
| `Neutral/Dark` | `#1E293B` | Primary text, card headers |
| `Neutral/Body` | `#334155` | Secondary text |
| `Neutral/Gray` | `#64748B` | Muted text, labels |
| `Neutral/GrayLight` | `#94A3B8` | Placeholder text |
| `Neutral/Border` | `#CBD5E1` | Card borders, dividers |
| `Neutral/BG` | `#F8FAFC` | Page background |
| `Status/NewBG` | `#DBEAFE` | New status tag BG |
| `Status/NewText` | `#1D4ED8` | New status tag text |
| `Status/ContactedBG` | `#FEF3C7` | Contacted tag BG |
| `Status/ContactedText` | `#92400E` | Contacted tag text |
| `Status/InterestedBG` | `#D1FAE5` | Interested tag BG |
| `Status/InterestedText` | `#065F46` | Interested tag text |
| `Status/WonBG` | `#DCFCE7` | Closed Won BG |
| `Status/WonText` | `#14532D` | Closed Won text |
| `Status/LostBG` | `#F1F5F9` | Closed Lost BG |
| `Status/LostText` | `#475569` | Closed Lost text |

---

## TEXT STYLES

Create **Text Styles** for consistent typography:

| Style Name | Font | Size | Weight |
|---|---|---|---|
| `Display/H1` | DM Sans | 22px | Bold (700) |
| `Display/H2` | DM Sans | 18px | SemiBold (600) |
| `Display/H3` | DM Sans | 14px | Bold (700) |
| `Body/Large` | DM Sans | 13.5px | Regular (400) |
| `Body/Default` | DM Sans | 13px | Regular (400) |
| `Body/Small` | DM Sans | 12px | Regular (400) |
| `Label/Caps` | DM Sans | 11px | Bold (700) — ALL CAPS, letter-spacing 0.8 |
| `Data/Mono` | DM Mono | 12.5px | Regular (400) |

---

## COMPONENT: SIDEBAR (build once, reuse on all 4 screens)

1. Press **R** → draw a rectangle: `220 × 900` → fill: `#0F172A`
2. **Logo area** (top section, 70px tall):
   - Draw `32 × 32` rounded rectangle (radius 8), fill `#0D9488` → This is the logo icon
   - Inside: add an icon (use Figma's built-in icons or an SVG — search "layers" icon)
   - Add text "DriveFlow" — DM Sans Bold 15px, white
   - Add text "CRM" below — DM Sans 10px, `#94A3B8`, ALL CAPS, letter-spacing 1
   - Add a bottom border line: `1 × 220` rectangle, fill `rgba(255,255,255,0.07)`

3. **Navigation items** (in the `nav` section, starting y=86):
   - Each nav item is a frame: `196 × 36px`, rounded corners 8px
   - For active state: fill `#0D9488`
   - For inactive: fill transparent, hover state `rgba(255,255,255,0.07)`
   - Add an icon (16×16) + label text (DM Sans 13.5px Medium)
   - For "Leads": add a badge pill on the right — `#CCFBF1` fill, `#0F766E` text, "248"

4. **User card** (bottom):
   - Bottom of sidebar, 60px from bottom
   - Avatar circle `32 × 32`, teal fill, initials text
   - Name: DM Sans 13px Bold white
   - Role: DM Sans 11px `#94A3B8`

5. **Select all sidebar elements** → Right-click → **Group** → **Create Component** (Ctrl+Alt+K)
   - Name it: `Sidebar/Default`

---

## COMPONENT: TOP BAR

1. Draw `1220 × 58` rectangle, fill white, add bottom border (effect: inner shadow or use a line)
2. **Left:** Page title — DM Sans Bold 16px `#1E293B`
3. **Center:** Search input
   - Rectangle `280 × 36`, border `1.5px #CBD5E1`, radius 8, fill `#F8FAFC`
   - Add a search icon SVG (16×16, `#94A3B8`) at x+12
   - Add placeholder text "Search leads…" — DM Sans 13px `#94A3B8`
4. **Right:**
   - Bell icon button: `36 × 36`, border `1.5px #CBD5E1`, radius 8
   - Add red dot `7 × 7` circle, `#F43F5E`, offset top-right
   - User avatar + name chip: border `1.5px #CBD5E1`, rounded 8

---

## SCREEN 1 — LEAD LISTING

**Reference file:** `mockups/screen1-lead-listing.html`

### Layout Structure
```
Sidebar (220px) | Main Area (1220px)
                  Top Bar (58px full width)
                  Content area (padding 24px 28px)
                    Page header row
                    Filter bar
                    Table (flex: remaining height)
```

### Step-by-step

**Page Header:**
- "All Leads" — H1 style
- Count badge pill: `#CCFBF1` background, `#0F766E` text, "248 leads"
- "Export CSV" button: border `1.5px #CBD5E1`, white bg, DM Sans 13px SemiBold
- "+ Add Lead" button: `#0D9488` bg, white text, DM Sans 13.5px SemiBold, radius 8

**Filter Bar:**
- White card, border `1.5px #CBD5E1`, radius 10, padding `12px 16px`
- 4 dropdown selects + 1 text input + "Clear filters" link
- Each dropdown: `32px` height, border `1.5px #CBD5E1`, radius 7, chevron icon right

**Table:**
- White card, border `1.5px #CBD5E1`, radius 12
- **Header row:** `#F8FAFC` background, 11px BOLD CAPS labels, border-bottom
- Grid columns: `40px | 1fr | 1fr | 110px | 130px | 140px | 140px`
- **Data rows:** 44px height each, 1px bottom border `#F8FAFC`
  - Hover state: `#F0FDF4` background
- **Checkbox column:** 16×16 square, 2px border `#CBD5E1`, radius 4
- **Lead name:** Bold 13.5px + muted email below 11.5px
- **Phone:** DM Mono 12.5px
- **Source badge:** pill shape, colour per source (see colour guide)
- **Status tag:** pill shape, colour per status (see colour styles)
- **Assign column:** 22×22 avatar circle + name text
- **Actions column:** 3 icon buttons (28×28 each, border `1.5px #CBD5E1`, radius 7)

**Pagination:**
- 46px height, border-top `1.5px #CBD5E1`
- Left: "Showing 1–7 of 248 leads" muted text
- Right: page number buttons + rows-per-page select

---

## SCREEN 2 — LEAD DETAILS

**Reference file:** `mockups/screen2-lead-details.html`

### Layout
```
Sidebar | Main (Top Bar + Content)
Content = Detail Header (lead name + action buttons)
        + Two-column layout:
          Left col (55%) | Right col (45%)
```

### Key Components

**Detail Header:**
- Avatar `48 × 48`, radius 12, gradient teal
- H1 lead name, status badge, score stars, source chip
- Action buttons row: Call (teal), WhatsApp (green `#22C55E`), Email (white with border)

**Left Column Cards:**
1. Customer Info + Car Interest (side by side, 2-col grid)
   - Each: white card, border, radius 12, padding 16px
   - Labels: 11px bold `#94A3B8` ALL CAPS
   - Values: 13.5px `#1E293B`
2. Interaction History (timeline)
   - Each event: circle icon (28×28) + vertical line connector + body text
   - Circle colours: teal-light (call), green-light (whatsapp), blue-light (email), slate (created)
3. Notes (editable area + save button)

**Right Column Cards:**
1. Assigned To — avatar + name + role + reassign dropdown
2. Lead Stage — dropdown + Update button
3. Follow-up Scheduler — date picker + time picker + notes area + Set Reminder button
4. Upcoming Follow-up — teal-light background card
5. Lead Score Breakdown — label + progress bar + value for each dimension

---

## SCREEN 3 — PIPELINE

**Reference file:** `mockups/screen3-pipeline.html`

### Layout
```
Sidebar | Main (Top Bar + Page Header + Kanban Board)
Kanban = horizontal scroll of 7 columns
```

### Column Construction
Each column is `170px` wide, radius 12, column-specific background (see design system).

**Column Header:**
- Title in 12px bold caps, colour matches column theme
- Count badge pill on right

**Lead Card:**
- White card, border `1.5px transparent`, radius 9
- Hover: border `1.5px #0D9488`, shadow
- Overdue state: border `1.5px #F59E0B`, background `#FFFBEB`
- Structure: Lead name (bold 13px) | Model (teal 11.5px) | Phone (mono 11px) | Source icon + Avatar row

**7 Columns with their colour themes:**

| Column | BG | Title Color | Badge BG |
|---|---|---|---|
| New Leads | `#EFF6FF` | `#1D4ED8` | `#DBEAFE` |
| Contacted | `#FFFBEB` | `#92400E` | `#FEF3C7` |
| Interested | `#F0FDF4` | `#065F46` | `#D1FAE5` |
| Test Drive | `#F5F3FF` | `#5B21B6` | `#EDE9FE` |
| Negotiation | `#FFF1F2` | `#9F1239` | `#FFE4E6` |
| Closed Won | `#F0FDF4` | `#14532D` | `#DCFCE7` |
| Closed Lost | `#F8FAFC` | `#475569` | `#F1F5F9` |

**Drag interaction (for prototype):**
- Add a drag interaction from each card to the next column's drop zone
- Or simply show the "while dragging" variant with the card slightly lifted (shadow + rotate 2°)

---

## SCREEN 4 — DASHBOARD

**Reference file:** `mockups/screen4-dashboard.html`

### Layout
```
Sidebar | Main
Content:
  Row 1: 4 metric cards (equal width grid)
  Row 2: 2 chart cards (40/60 split)
  Row 3: 2 table cards (50/50 split)
```

### Metric Cards (×4)
- White card, border, radius 12
- 3px top border accent (colour varies per card: teal, blue, green, amber)
- Label: 11px caps muted
- Value: 36px bold, letter-spacing -1.5px
- Trend: 12px, green (▲ up) or red (▼ down) or gray (→ neutral)

### Leads by Source Chart
- CSS/SVG donut chart OR use Figma's built-in chart plugin
- If manual: draw concentric rings using stroke on circles
  - Circle: cx/cy center, radius 40, stroke-width 18
  - Each segment is a separate circle with stroke-dasharray
- Legend: colour dot + source name + percentage

### Lead Funnel Chart
- 6 horizontal bars, each shorter than the previous
- Colours progress from blue → teal → green
- Bar heights: 20px, rounded corners
- Labels on left (110px width), numbers on right inside bar

### Top Salespeople Table
- Standard data table with rank | name | leads | won | conv%
- Rank in teal bold
- Conv% as a mini progress bar + percentage label
- Alternating row highlight optional

### Car Models Chart
- Horizontal bar chart, 6 bars
- Different colour per bar (teal, blue, purple, amber, green, sky)
- Model name on left (120px), bar stretches right, count inside bar

---

## PROTOTYPING (add interactions)

1. Select Screen 1 frame → In Prototype panel, set as **Starting Frame**
2. **Screen 1 → Screen 2:** Select any lead name text → Add interaction → "On Click" → "Navigate to" → Screen 2
3. **Screen 2 → Screen 1:** Select "Back to Leads" button → "On Click" → Navigate to Screen 1
4. **Sidebar → all screens:** Select each nav item → wire to respective screen
5. **Pipeline drag:** Select a card → "On drag" → Navigate to next column (simplified)

---

## SHARING YOUR FIGMA FILE

1. Click **Share** button (top right in Figma)
2. Under "Anyone with the link" → change from "can view" access → select **"can view"**  
   _(Make sure it's set to view — not edit, not restricted)_
3. Copy the link
4. Add it to:
   - Your `README.md` (replace the placeholder)
   - Your Google Doc submission template under "Other Links"

---

## QUICK TIPS

- Use **Auto Layout** for the sidebar nav items and table rows — makes spacing consistent
- Use **Components** for the sidebar, top bar, and lead cards so you only design them once
- The **Figma Color Picker** can pick colours directly from the HTML mockups if you open them in a browser and screenshot them
- Use **Constraints** (right panel) to make elements "stick" to edges when the frame resizes
- **Ctrl+G** to group, **Ctrl+Alt+K** to make a component, **Alt+drag** to duplicate

---

*Happy designing! Open the HTML mockups in Chrome while building in Figma — they're your blueprint.*
