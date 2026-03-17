# Security Roadmap Visualizer

A clean, single-page web app to visualize phased security implementation roadmaps for organizations — designed to communicate priorities clearly to both technical and non-technical stakeholders.

---

## Why This Was Created

Security roadmaps often live in dense spreadsheets or lengthy policy documents that are hard to present to management, clients, or non-technical teams. This tool was built to solve that: **drop in your data, get a beautiful, presentation-ready overview instantly.**

Whether you're a CISO presenting to the board, a consultant delivering a security audit, or a student completing an ISO 27005 risk assignment — this visualizer makes your roadmap easy to read and understand at a glance.

---

## What It Does

The app renders a **phased security roadmap** from a simple JSON file. Each phase (e.g. Quick Wins, Short Term, Medium Term) contains measure cards that show:

- 🔑 **Icon** — visual shorthand for the measure type
- **Risk ID(s)** — linked back to your risk register (e.g. R1, R4)
- **Title** — clear, action-oriented measure name
- **Responsible party** — who owns this measure
- **Description** — plain-language explanation of the measure
- **KPI / Result** — measurable success criteria and evidence

The layout automatically **scales to fit any screen size** — great for projectors, laptops, or sharing as a screenshot.

---

## How To Use

### 1. Clone or download the project

```bash
git clone https://github.com/your-username/security-roadmap-visualizer.git
cd security-roadmap-visualizer
```

### 2. Edit `roadmap-data.json`

Open `roadmap-data.json` and fill in your own phases and measures. The structure looks like this:

```json
{
  "phases": [
    {
      "id": 0,
      "badge": "Quick Wins",
      "label": "0 – 30 dagen",
      "sub": "Direct uitvoerbaar, hoge impact",
      "measures": [
        {
          "icon": "🔑",
          "risicoId": "R1, R2",
          "title": "MFA inschakelen voor alle medewerkers",
          "responsible": "IT-beheerder",
          "desc": "Multi-factor authenticatie verplicht stellen voor alle accounts...",
          "kpi": "100% van accounts voorzien van MFA binnen 30 dagen. Bewijs: MFA-rapport uit Azure AD."
        }
      ]
    }
  ]
}
```

You can add up to **3 phases** (ids `0`, `1`, `2`) and **3 measures per phase** for optimal layout.

### 3. Serve locally

Because the page loads `roadmap-data.json` via `fetch()`, you need a local web server (opening `index.html` directly in a browser will cause a CORS error).

**Option A — Python (no install needed):**
```bash
python3 -m http.server 8080
```
Then open [http://localhost:8080](http://localhost:8080)

**Option B — VS Code:**
Use the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension and click **Go Live**.

**Option C — Node.js:**
```bash
npx serve .
```

---

## File Structure

```
security-roadmap-visualizer/
├── index.html          # Main app — layout, styling, render logic
└── roadmap-data.json   # Your roadmap content (edit this)
```

No build tools. No dependencies. No npm install. Just two files.

---

## Customization

| What | Where |
|---|---|
| Phase colors (green / blue / purple) | CSS variables `--accent-0/1/2` and `--tag-0/1/2` in `index.html` |
| Fonts | Google Fonts import at the top of `index.html` |
| Header title & subtitle | `<header>` section in `index.html` |
| Number of phases / measures | `roadmap-data.json` |

---

## Use Cases

-  **Security audits** — present findings and remediation steps to clients
-  **School assignments** — risk analysis and implementation planning
-  **Board presentations** — executive-level security strategy overview

---

## License

MIT — free to use, adapt, and share.
