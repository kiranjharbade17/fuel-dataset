# Global Fuel Pricing, Taxation, and Subsidy Trends

A project analyzing weekly fuel prices, taxation, regions, income categories, and subsidies across 84 countries from January 2020 through April 2026. The folder contains the source dataset, a local Tableau workbook, a responsive Flask dashboard, SQL preparation scripts, and assignment documentation.

## Project files
- `data/global_fuel_prices_Dataset.csv` — source data (27,468 records, 10 fields)
- `Global_Fuel_Pricing_Trends.twb` — local Tableau workbook with five starter worksheets, a dashboard, and a saved seven-point Story
- `web/` — interactive local Flask dashboard with KPI cards, global maps, trend charts, tax analysis, and filters; optional Tableau Public embeds
- `sql/fuel_project_clean.sql` — MySQL import and quality checks
- `sql/fuel_project_original.sql` — supplied SQL retained for reference
- `docs/project_story.md` — seven-scene narrative and findings
- `docs/project_process_and_status.md` — assignment workflow and implementation status
- `docs/development_procedure.md` — step-by-step project workflow
- `docs/demo_video_script.md` — end-to-end demo narration outline
- `docs/tableau_build_guide.md` — specification for the ten requested Tableau views and Story points
- `docs/tableau_public_publishing.md` — publishing steps
- `docs/data_dictionary.md` — field definitions and interpretation limits

## Open the web dashboard
From the project root in PowerShell:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
py -m pip install -r .\web\requirements.txt
py .\web\app.py
```

Then open `http://127.0.0.1:5000`. Plotly charts load from a CDN, so the browser needs internet access. More details are in `web/README.md`.

## Tableau workbook status
The saved workbook contains five starter worksheets, a dashboard titled “Global Fuel Prices Dashboard,” and a seven-point Story. The Story still needs alignment with the required scene sequence and a subsidy assessment point. The Flask companion implements the specified KPI cards, two maps, four trends, tax pie, top-tax bar, top-three fuel comparison, and Country, Year, and fuel-measure filters. The Tableau workbook still needs the full set of requested Tableau views and filters before it is ready for Tableau Public publishing.

The project brief describes “nine” visualization types but lists ten view entries. The project preserves all ten. The top-three comparison ranks countries by mean petrol price and displays the selected Petrol, Diesel, and LPG measures.

## Dataset and findings
The 27,468 rows contain 84 countries and 327 weekly observations per country. No missing values or duplicate country-week keys were found in the supplied CSV. The CSV is approximately 1.9 MB on disk.

- Overall averages: petrol $2.282/L, diesel $2.134/L, and LPG $1.711/L.
- Europe has the highest regional mean petrol price ($3.702/L); the Middle East has the lowest ($1.226/L).
- Annual mean petrol prices were $1.485/L in 2020, $2.505/L in 2022, $2.234/L in 2023, and $2.647/L through April 6, 2026 (partial year).
- Country-level average tax and petrol price have a positive correlation (Pearson r ≈ 0.836). This is descriptive, not causal.
- Mean petrol price is lower in higher subsidy categories in this dataset. The comparison does not isolate subsidy effects from other country differences.

No new source columns or calculated fields are added. The data has no household spending or purchasing-power measures, so it cannot directly measure affordability. The unit for Brent crude is not specified in the source and should be confirmed before reporting as USD/barrel.
