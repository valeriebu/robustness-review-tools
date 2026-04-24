# AI — Robustness & Transparency Review Suite

A set of browser-based tools and documents for a study-based robustness assessment
of mature medical AI.

---

## What's in this repository

### Browser tools (open in any browser, no installation needed)

| File | What it does |
|---|---|
| `index.html` | Landing page — links to all tools with instructions |
| `review-overview.html` | Map all tools and studies in your review |
| `radar-chart.html` | Visualise robustness & transparency profiles as radar charts |

### Word documents (download and fill in per study)

| File | What it does |
|---|---|
| `AI_Extraction_Codebook_Robustness_Marked.docx` | Full extraction codebook, robustness questions highlighted |
| `Robustness_Transparency_Scoring_Sheet.docx` | Score each study on 7 robustness + 7 transparency dimensions |
| `Robustness_Step1_Population_Comparison.docx` | Compare intended / training / RCT populations |
| `Robustness_Step2_Results_Across_Subgroups.docx` | Record results broken down by subgroup |
| `Tool_Overview_Sheet.docx` | Aggregate findings across RCT + precursors per tool |

---

## How to use

### Option A — Run locally
1. Download or clone this repository
2. Open `index.html` in any browser (Chrome, Firefox, Safari, Edge)
3. No server, no installation, no internet connection needed

### Option B — Host on GitHub Pages (share with your team)
1. Fork or upload this repository to GitHub
2. Go to **Settings → Pages → Source → main branch**
3. GitHub gives you a public URL like `https://yourusername.github.io/your-repo-name`
4. Share that URL — anyone can open the tools in their browser

### Option C — Deploy on Netlify (quickest)
1. Go to [netlify.com](https://netlify.com) and sign up free
2. Drag and drop the entire folder onto the Netlify dashboard
3. You get a URL instantly (e.g. `https://your-site.netlify.app`)

---

## The scoring framework

### Robustness dimensions (R1–R7)
The robustness score asks: *did they actively test whether the tool works reliably?*

| Code | Dimension | Questions (n) |
|---|---|---|
| R1 | Training Data Quality | 6 |
| R2 | Training Data Representativeness | 5 |
| R3 | Model Development Rigour | 4 |
| R4 | Validation Rigour | 9 |
| R5 | Subgroup & Fairness Testing | 8 |
| R6 | Operational Robustness | 9 |
| R7 | Stress-Testing & Sensitivity | 4 |

### Transparency dimensions (T1–T7)
The transparency score asks: *did they report what the tool is and how it was built?*

| Code | Dimension | Questions (n) |
|---|---|---|
| T1 | Tool Description | 8 |
| T2 | Intended Use Reporting | 6 |
| T3 | Training Data Reporting | 6 |
| T4 | Data Processing Reporting | 4 |
| T5 | Validation & Results Reporting | 7 |
| T6 | Study Conduct Reporting | 7 |
| T7 | COI & Limitations | 6 |

All questions are binary (yes = 1, no/blank = 0).
Dimension score = (yes answers / total questions) × 100%.

---

## Customising the tools

All tools are plain HTML + JavaScript — no frameworks, no build step.
Open any `.html` file in a text editor to modify it.

### Change dimension names or questions
In `radar-chart.html`, find the `ROB_DIMS` and `TRA_DIMS` arrays near the top of the `<script>` block:
```js
const ROB_DIMS = [
  { id:"r1", short:"R1", label:"Training Data Quality", color:"#4472C4", n:6 },
  // add, remove, or rename dimensions here
];
```

### Change colours
Each dimension has a `color` hex value. Change it to any hex colour.
The overall theme colour `#1F4E79` (dark blue) appears in the CSS — find and replace it.

### Change study types in the Overview tool
In `review-overview.html`, find:
```js
const STUDY_TYPES = [
  "RCT","Feasibility","Usability","Acceptability",
  "Validation (internal)","Validation (external)","Other"
];
```
Add or remove types as needed. Also update `TYPE_BADGE_MAP` below it to assign colours.

---

## Notes

- **No data is stored** — all tools run entirely in the browser. Closing the tab clears the data.
  If you need persistence, consider copying data out via the CSV export buttons.
- **No internet required** after the initial page load (except for the radar chart tool,
  which loads Chart.js from a CDN — save it locally if you need offline use).
- **Tested in** Chrome, Firefox, Safari, Edge.

---

## Workflow summary

```
1. Review Overview       → map all tools and studies
2. Extraction Codebook   → extract data per study
3. Population Comparison → check population alignment (Step 1)
4. Subgroup Results      → check result consistency (Step 2)
5. Scoring Sheet         → score robustness & transparency per study
6. Radar Chart           → visualise and compare profiles
7. Tool Overview Sheet   → summarise per tool across all studies
```
