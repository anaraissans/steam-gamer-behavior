# Steam Gamer Behavior — Pattern Discovery & Segmentation

Behavioral analysis of ~200k Steam user interactions (purchases and playtime), from exploration and player personas to an interactive Power BI dashboard.

---

## Overview

This project answers how Steam users **buy**, **play**, and **engage** with games, and which **patterns** support discovery and recommendation.

**Highlights:**

- **EDA** — purchases vs. playtime, long-tail catalog, top titles  
- **User personas** — rule-based segments (Collectors, Casual, Hardcore, Specialists, …)  
- **Clustering** — K-Means on behavioral features  
- **Game segments** — popularity vs. average engagement  
- **Association rules** — co-purchase patterns (lift) among top games  
- **Power BI** — star-schema CSV exports + multi-page report  

**Source data:** [Steam Video Games (Kaggle)](https://www.kaggle.com/datasets/tamber/steam-video-games) — `user_id`, `game_name`, `behavior_name` (`purchase` | `play`), `hours_play`.

---

## Repository layout

This folder is the **project root** (clone / open this repository as-is).

```text
├── README.md
├── requirements.txt
├── .env.example
├── steam_gamer_behavior_analysis.ipynb   # main analysis
├── data/                                 # steam-200k.csv (not in git)
├── exports/powerbi/                      # CSVs for Power BI (generated)
└── PowerBI/                              # Power BI project (report + semantic model)
    ├── Steam Gamer Behavior.Report/
    └── Steam Gamer Behavior.SemanticModel/
```

**Dashboard pages (report):** Overview → Personas → Clusters → Games → Co-purchase.

---


## Power BI model (star schema)

| Table | Role |
|-------|------|
| `fact_user_game` | Fact — user × game (purchases, hours, segments) |
| `dim_user` | Player metrics & personas |
| `dim_game` | Game metrics & tiers |
| `fact_persona_game_matrix` | Persona × game-segment aggregates |
| `fact_association_rules` | Co-purchase rules (Apriori) |

Relationships: `dim_user[user_id]` and `dim_game[game_name]` → `fact_user_game` (one-to-many).

More detail: `exports/powerbi/README_powerbi.txt`.

---

## Portfolio tips

---

## License & attribution

Dataset: [Steam Video Games on Kaggle](https://www.kaggle.com/datasets/tamber/steam-video-games) (see license on the Kaggle page).  
Analysis and dashboard: this repository