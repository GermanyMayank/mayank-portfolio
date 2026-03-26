# Mayank Vekariya — Project Portfolio

A clean, dark-themed personal project portfolio page built as a single HTML file.
Hosted free on GitHub Pages. No frameworks, no build tools, no backend required.

---

## What This Page Does

- Shows all your projects as cards with photos, tags, status, and dates
- Each project card has a **photo carousel** (swipe/click through multiple images)
- Clicking a card opens a **detail modal** with full description, outcomes, tools, team, and links
- Photos in the modal can be opened in a **fullscreen lightbox**
- Filter projects by category and sort by date or featured status
- Fully mobile responsive

---

## File Structure

Your GitHub repo should look like this:

```
your-repo/
├── index.html          ← the portfolio page (do not rename)
├── README.md           ← this file
├── Mayank_Vekariya_CV.pdf   ← your CV (optional, linked in header)
├── solar-site-1.jpg    ← project photos go here, same folder as index.html
├── solar-site-2.jpg
├── motor-project.jpg
└── ...
```

All image files must be in the **same folder as `index.html`**. Do not put them in subfolders unless you update the image paths in the code.

---

## Step 1 — Host on GitHub Pages (One-Time Setup)

### 1.1 Create a GitHub account
Go to [github.com](https://github.com) and sign up if you do not have an account.

### 1.2 Create a new repository
1. Click the **+** button in the top right, then **New repository**
2. Name it something like `portfolio` or `project-portfolio`
3. Set visibility to **Public**
4. Click **Create repository**

### 1.3 Upload your files
1. On your new repo page, click **Add file** > **Upload files**
2. Drag and drop `index.html`, `README.md`, your CV PDF, and any project photos
3. Scroll down and click **Commit changes**

### 1.4 Enable GitHub Pages
1. Go to your repo **Settings** (top menu)
2. Scroll down to **Pages** in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, select `main` and folder `/ (root)`
5. Click **Save**

Your portfolio will be live at:
```
https://YOUR_GITHUB_USERNAME.github.io/REPO_NAME/
```

It may take 1-2 minutes the first time. After that, updates go live within 30 seconds.

---

## Step 2 — How to Add a New Project

Open `index.html` in any text editor (Notepad, VS Code, etc.).

Find this section near the bottom of the file:

```javascript
const PROJECTS = [
  { ... },
  { ... },   // existing projects
];
```

To add a new project, paste a new block inside the array **after the last `},`** and before the closing `]`:

```javascript
{
  id: 7,
  title: "Your Project Title",
  description: "Short 2-3 sentence summary shown on the card.",
  fullDesc: "Full detailed description shown inside the modal. Write as much as you want here. Describe the context, your role, the approach, and the outcome.",
  images: [],
  emoji: "🚀",
  tags: ["Engineering"],
  date: "Jan 2025 – Mar 2025",
  dateSort: "2025-01",
  status: "completed",
  featured: false,
  outcomes: [
    "First key achievement with a number if possible",
    "Second key achievement",
    "Third key achievement"
  ],
  tools: ["MS Project", "Excel", "SharePoint"],
  team: ["Engineering Team", "Procurement", "Client"],
  links: [
    { label: "Case Study", url: "https://...", primary: true },
    { label: "GitHub Repo", url: "https://..." }
  ],
  filterKey: "engineering"
},
```

### Field reference

| Field | What to put |
|-------|-------------|
| `id` | A unique number. Just increment from the last project. |
| `title` | The project name |
| `description` | 2-3 sentences for the card (kept short) |
| `fullDesc` | Full paragraph(s) for the modal detail view |
| `images` | Array of image filenames (see Step 3 below) |
| `emoji` | Shown on the card when no images are provided |
| `tags` | Array of tag labels. Must exist in `TAG_COLORS` (see Step 4) |
| `date` | Display string, e.g. `"Jan 2021 – Dec 2021"` |
| `dateSort` | `"YYYY-MM"` format for sorting, use the start date |
| `status` | `"completed"` or `"ongoing"` or `"planned"` |
| `featured` | `true` shows a yellow "Featured" badge on the card |
| `outcomes` | Array of bullet-point achievements shown in modal |
| `tools` | Array of tool/method names shown as chips in modal |
| `team` | Array of team/department names shown in modal |
| `links` | Buttons at the bottom of the modal (set `primary: true` for the main CTA) |
| `filterKey` | Lowercase string, no spaces. Used by the filter buttons. |

---

## Step 3 — How to Add Photos to a Project

### 3.1 Upload your photos to GitHub
1. Go to your repo on GitHub
2. Click **Add file** > **Upload files**
3. Upload your image files (JPG, PNG, WebP all work)
4. Use simple filenames with no spaces, e.g. `solar-site-1.jpg`, `motor-project.jpg`
5. Click **Commit changes**

### 3.2 Add the filenames to your project
In `index.html`, find the project you want to update and edit the `images` field:

```javascript
// Before (no photos):
images: [],

// After (with photos):
images: ["solar-site-1.jpg", "solar-site-2.jpg", "solar-commissioning.jpg"],
```

You can add as many photos as you want. The page will automatically:
- Show a carousel on the card with left/right arrows
- Show a photo count badge (e.g. "3 photos")
- Show a thumbnail strip in the detail modal
- Enable fullscreen lightbox when you click any photo

### 3.3 Photo tips

- Landscape orientation (wider than tall) works best for the card carousel
- Recommended size: at least 800px wide, ideally 1200-1600px
- Keep file sizes under 500KB per image for fast loading (use [squoosh.app](https://squoosh.app) to compress)
- If you only have one photo, the carousel arrows and dots are hidden automatically

---

## Step 4 — How to Add a New Category/Tag

### Add a new tag color
Find this section near the top of the JavaScript:

```javascript
const TAG_COLORS = {
  "Solar Energy":   "green",
  "Engineering":    "",
  "Strategy":       "orange",
  ...
};
```

Add your new tag:

```javascript
"Your New Tag": "pink",
```

Available colors: `"green"` (yellow-green), `"pink"` (pink), `"orange"` (orange), `""` (blue, default)

### Add a new filter button label
Find this inside the `buildFilters()` function:

```javascript
const labelMap = {
  solar: 'Solar Energy',
  engineering: 'Engineering',
  ...
};
```

Add your new filterKey and its display label:

```javascript
your_key: 'Your Category Name',
```

Then use `filterKey: "your_key"` in any project that should appear under that filter.

---

## Step 5 — Update Personal Details

At the top of the `index.html`, update these values:

### Header links
```html
<a class="hl" href="mailto:YOUR_EMAIL">...</a>
<a class="hl" href="https://linkedin.com/in/YOUR_PROFILE" ...>...</a>
<a class="hl" href="https://github.com/YOUR_USERNAME" ...>...</a>
<a class="hl" href="YOUR_CV_FILENAME.pdf" ...>...</a>
```

### Name and title in the subtitle
```html
<p class="sub">Your Name &mdash; Your Title &mdash; Your City, Country</p>
```

### Stats row
The stats row auto-calculates totals from your projects. To update the "Budget Managed" stat, find this section in `renderStats()`:

```javascript
{ val: '€500K+', label: 'Budget Managed' },
```

Change the value to match your experience.

---

## How to Make Updates After Publishing

1. Edit `index.html` locally on your computer
2. Go to your GitHub repo
3. Click on `index.html` in the file list
4. Click the **pencil icon** (Edit this file) in the top right
5. Paste your updated code
6. Click **Commit changes**

Your live site updates within 30 seconds.

Alternatively, if you use VS Code or GitHub Desktop, you can edit and push files normally.

---

## Troubleshooting

**Photos not showing:**
- Check the filename matches exactly, including uppercase/lowercase (GitHub is case-sensitive)
- Make sure the image file is in the same folder as `index.html`, not in a subfolder
- Check the filename has no spaces (use hyphens instead)

**Page not loading after enabling GitHub Pages:**
- Wait 2-3 minutes, then refresh
- Make sure your file is named exactly `index.html` (not `Index.html` or `index.HTML`)
- Make sure GitHub Pages is set to deploy from `main` branch, `/ (root)` folder

**Filter button not appearing:**
- Check that `filterKey` in your project matches a key in `labelMap` inside `buildFilters()`
- Keys are case-sensitive and must have no spaces

**Modal not opening:**
- Make sure each project has a unique `id` number
- Check there are no missing commas between project objects in the `PROJECTS` array

---

## Quick Checklist for Adding a New Project

- [ ] Add a new object to the `PROJECTS` array with a unique `id`
- [ ] Fill in `title`, `description`, `fullDesc`, `date`, `dateSort`, `status`
- [ ] Add `outcomes`, `tools`, and `team` arrays
- [ ] Set `filterKey` (and add to `labelMap` and `TAG_COLORS` if it is a new category)
- [ ] Upload photo files to GitHub repo
- [ ] Add photo filenames to the `images` array
- [ ] Commit and push changes
- [ ] Check the live site after 30 seconds

---

*Built and maintained by Mayank Vekariya. Contact: germanymayank@gmail.com*
