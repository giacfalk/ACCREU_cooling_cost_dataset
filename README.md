# ACCREU_cooling_cost_dataset
This public folder contains country-level projections of the **cost of residential space cooling** (air-conditioning investment and electricity expenditure), together with **AC penetration rates and cooling electricity consumption** by country and by European NUTS region, under ACCREU climate and adaptation scenarios.

**Author:** Giacomo Falchetta, CMCC Foundation (RFF-CMCC EIEE) ([giacomo.falchetta@cmcc.it](mailto:giacomo.falchetta@cmcc.it))
**Produced within:** ACCREU (Assessing Climate Change Risk in EUrope), Horizon Europe
**Version:** 1.0 (model outputs of 10 April 2026)

**Data access:** files are hosted on the [IIASA Accelerator](https://accelerator.iiasa.ac.at/); direct download links are in the [file tables below](#1-files).

## Summary

Bottom-up projections of the cost of space cooling in the **residential sector**, by country and year, under three ACCREU adaptation intensity variants, three climate scenarios, and a no-climate-change counterfactual for each.

The estimates cover upfront investment in the air-conditioning (AC) stock (**extensive margin**) and the electricity expenditure for operating it (**intensive margin**), reported as four separate cost components so users can select those relevant to their application. Companion files report the underlying **AC penetration rate** and **residential cooling electricity consumption** by country and by NUTS region.

The projections come from a bottom-up cooling-cost model built on a non-linear, non-parametric machine-learning estimate of AC ownership and cooling needs as a function of cooling and heating degree days and socioeconomic drivers (Falchetta et al., 2024).

| Dimension | Cooling-cost files | AC penetration & electricity files |
|---|---|---|
| **Sector** | Residential only (services and industry not covered) | Residential only |
| **Spatial** | 133 countries (ISO3) | 187 countries (ISO3); 37 European countries at NUTS levels 0–3 (NUTS 2021) |
| **Temporal** | 2020–2100, annual, cumulative from 2020 | 2030, 2050, 2100 |
| **Climate** | SSP2 with RCP2.6, RCP4.5, RCP7.0, plus a no-climate-change counterfactual | SSP2 with RCP2.6, RCP4.5, RCP7.0 |
| **Adaptation** | `base`, `mid`, `high` | `base`, `mid`, `high` |
| **Unit** | 2021 USD at market exchange rates, undiscounted | Penetration: share (0–1); energy: EJ/yr (see [§3](#3-ac-penetration-and-cooling-electricity-files)) |

Countries or regions not in the files, or reported with zero energy and no penetration, are outside the model domain, **not** zero-cost or zero-demand.

## Citation

> Falchetta, Giacomo. (2026). *Cost of residential space cooling by country under climate and adaptation scenarios* (Version 1.0). Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

**Methodology reference:**
> Falchetta, G., De Cian, E., Pavanello, F., & Wing, I. S. (2024). Inequalities in global residential cooling energy use to 2050. *Nature Communications*, 15. https://doi.org/10.1038/s41467-024-52028-8

## License

- **Data:** This dataset is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

## Repository Contents (Metadata only)

This GitHub repository hosts **only** the metadata (this README). The data files reside on the IIASA Accelerator platform (see link above).

## Folder Structure (on Accelerator)

```text
CMCC_energy/
└─ ac_investments/
   ├─ README.md
   ├─ cost_cooling_bycountry_scenario_base.csv
   ├─ cost_cooling_bycountry_scenario_mid.csv
   ├─ cost_cooling_bycountry_scenario_high.csv
   ├─ cost_cooling_bycountry_scenario_base_nocc.csv
   ├─ cost_cooling_bycountry_scenario_mid_nocc.csv
   ├─ cost_cooling_bycountry_scenario_high_nocc.csv
   ├─ ac_penetr_rate_ely_TWH_country.csv
   └─ ac_penetr_rate_ely_TWH_EU_NUTs.csv
```

---

# Dataset Documentation

## 1. Files

File names link to the direct download on the IIASA Accelerator.

### Cooling cost files

| File | Adaptation intensity | Climate |
|---|---|---|
| [`cost_cooling_bycountry_scenario_base.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_base.csv) | base | with climate change |
| [`cost_cooling_bycountry_scenario_mid.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_mid.csv) | mid | with climate change |
| [`cost_cooling_bycountry_scenario_high.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_high.csv) | high | with climate change |
| [`cost_cooling_bycountry_scenario_base_nocc.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_base_nocc.csv) | base | no climate change |
| [`cost_cooling_bycountry_scenario_mid_nocc.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_mid_nocc.csv) | mid | no climate change |
| [`cost_cooling_bycountry_scenario_high_nocc.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/cost_cooling_bycountry_scenario_high_nocc.csv) | high | no climate change |

### AC penetration and cooling electricity files

| File | Content |
|---|---|
| [`ac_penetr_rate_ely_TWH_country.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/ac_penetr_rate_ely_TWH_country.csv) | AC penetration rate and residential cooling electricity consumption by country (ISO3), wide format |
| [`ac_penetr_rate_ely_TWH_EU_NUTs.csv`](https://recon.iiasa.ac.at/accreu/user-uploads/CMCC_energy/ac_investments/ac_penetr_rate_ely_TWH_EU_NUTs.csv) | Same variables by European NUTS region (levels 0–3), long format |

## 2. Cooling Cost Files

### Variables

Long (tidy) format, comma-separated, UTF-8, quoted character fields, no missing values. The first column is an unnamed row index (header `""`, written by R's `write.csv`) and can be dropped.

| Column | Type | Description |
|---|---|---|
| `yr` | integer | Year, 2020–2100, annual. |
| `variable` | character | Cost component (see below). |
| `value` | numeric | **Cumulative** cost since 2020, in **2021 USD at market exchange rates** (not PPP). Unit is single dollars (not thousands or millions). Undiscounted. |
| `ISO3` | character | ISO 3166-1 alpha-3 country code. |
| `SSP` | character | Climate scenario: `26`, `45`, `70` = **SSP2-RCP2.6, SSP2-RCP4.5, SSP2-RCP7.0** (ACCREU protocol). Socioeconomics follow SSP2 throughout; only the forcing level varies. |

### Cost components

The four components are **mutually exclusive and additive**: their sum is the total cumulative cooling cost for a given country, year and scenario.

| `variable` value (exact string, incl. leading spaces) | Type | Description |
|---|---|---|
| `"   Increasing penetration"` | investment | Purchase of AC equipment for dwellings entering the cooled stock (extending AC access). |
| `" Retrofitting"` | investment | Refurbishment and replacement of equipment in the pre-existing cooled stock. |
| `"  Retrofitting of new penetration"` | investment | Refurbishment and replacement in the newly cooled stock. |
| `"  Electricity"` | expenditure | Cost of electricity consumed for space cooling. |

> **Tip:** the strings contain leading spaces. Trim them before filtering, e.g. `df["variable"].str.strip()` in Python or `trimws()` in R.

## 3. AC Penetration and Cooling Electricity Files

> **Units: read before using.** Both files are documented here exactly as stored on the Accelerator.
> - Penetration rate rows have `Unit = "%"`, but the values are **fractions between 0 and 1** (e.g. `0.55` = 55% of households).
> - Cooling energy is in **EJ/yr**, as stated in the `Unit` column, despite `TWH` in the file names. Multiply by 277.78 to convert to TWh/yr.

### Variables (both files)

| `Variable` (exact string) | `Unit` as stored | Description |
|---|---|---|
| `Appliances\|Air Conditioning\|Residential\|Penetration rate` | `%` (values are a 0–1 share) | Share of households with air conditioning. |
| `Final Energy\|Residential and Commercial\|Residential\|Cooling` | `EJ/yr` | Annual electricity consumption for residential space cooling. |

### `ac_penetr_rate_ely_TWH_country.csv`

Wide format: one row per country × scenario × adaptation variant × variable, one column per year.

| Column | Description |
|---|---|
| `""` (unnamed) | Row index; can be dropped. |
| `ISO3` | ISO 3166-1 alpha-3 country code. |
| `Scenario` | Climate scenario: `SSP226`, `SSP245`, `SSP270` (see [§4](#4-scenario-dimensions)). |
| `adapt` | Adaptation intensity: `base`, `mid`, `high`. |
| `2030`, `2050`, `2100` | Value in that year. |
| `Variable` | Variable name (see above). |
| `Unit` | Unit label (see above). |

The file lists 246 ISO3 codes. 59 of them (small territories and island states, including Malta, Singapore and Bahrain) have zero energy and no penetration rows: they are outside the model domain. Data are effectively available for **187 countries**, which include all 133 countries of the cooling-cost files.

### `ac_penetr_rate_ely_TWH_EU_NUTs.csv`

Long format: one row per region × scenario × adaptation variant × variable × year.

| Column | Description |
|---|---|
| `...1` | Row index; can be dropped. |
| `NUTS_ID` | NUTS region code (NUTS 2021 classification). |
| `LEVL_CODE` | NUTS level: `0` (country), `1`, `2`, `3`. |
| `CNTR_CODE` | Two-letter Eurostat country code. Note `EL` = Greece and `UK` = United Kingdom (not ISO 3166-1 `GR`/`GB`). |
| `NAME_LATN` | Region name in Latin script. |
| `Scenario` | Climate scenario: `SSP226`, `SSP245`, `SSP270`. |
| `adapt` | Adaptation intensity: `base`, `mid`, `high`. |
| `Variable` | Variable name (see above). |
| `Unit` | Unit label (see above). |
| `Year` | `2030`, `2050`, `2100`. |
| `Value` | Numerical value. |

**Coverage:** 37 countries: the EU27 plus Albania, Iceland, Liechtenstein, Montenegro, North Macedonia, Norway, Serbia, Switzerland, Türkiye and the United Kingdom (37 NUTS0, 125 NUTS1, 334 NUTS2, 1,514 NUTS3 regions).

Penetration rows are missing for **Malta** (all levels) and for **26 further NUTS3 regions**, where the energy value is zero. Treat these as not modelled.

<details>
<summary>NUTS3 regions without penetration rows</summary>

DE945 Wilhelmshaven · DK011 Byen København · EL304 Notios Tomeas Athinon · EL307 Peiraias, Nisoi · EL413 Chios · EL421 Kalymnos, Karpathos, Kasos, Kos, Rodos · EL422 Andros, Thira, Kea, Milos, Mykonos, Naxos, Paros, Syros, Tinos · EL623 Ithaki, Kefallinia · EL624 Lefkada · ES531 Eivissa y Formentera · ES533 Menorca · ES630 Ceuta · ES640 Melilla · ES703 El Hierro · ES704 Fuerteventura · ES705 Gran Canaria · ES706 La Gomera · ES708 Lanzarote · FRY20 Martinique · FRY40 La Réunion · FRY50 Mayotte · MT001 Malta · MT002 Gozo and Comino · NO0B1 Jan Mayen · NO0B2 Svalbard · UKJ21 Brighton and Hove · UKK41 Plymouth · UKM65 Orkney Islands

</details>

### Aggregation and consistency

- **Energy is additive.** NUTS3, NUTS2 and NUTS1 values sum to the NUTS0 total.
- **Penetration is a share.** Do not sum it across regions; weight it (e.g. by number of households) when aggregating.
- **NUTS0 rows are close to, but not identical to, the country file.** Median difference is 0.3% for penetration and 2% for energy, larger in countries with very low cooling demand (e.g. Sweden). Use one file consistently within an analysis.

## 4. Scenario Dimensions

### Climate scenarios

Socioeconomics follow SSP2 throughout; only the forcing level varies. The two file groups code scenarios differently:

| Climate scenario | Cooling-cost files (`SSP`) | Penetration files (`Scenario`) |
|---|---|---|
| SSP2-RCP2.6 | `26` | `SSP226` |
| SSP2-RCP4.5 | `45` | `SSP245` |
| SSP2-RCP7.0 | `70` | `SSP270` |

### Adaptation intensity: `base`, `mid`, `high`

The three ACCREU adaptation intensity variants, defined in **ACCREU Deliverable D2.2**. Costs increase with intensity (`base` < `mid` < `high`). In the cooling-cost files the variant is part of the file name; in the penetration files it is the `adapt` column.

### Climate: main files vs `_nocc`

`_nocc` files are a **no-climate-change counterfactual**: population, income and urbanisation follow SSP2, but the climate signal is removed. This counterfactual is available for the cooling-cost files only.

Subtracting the `_nocc` file from its matching main file (same adaptation variant, component, country, year and `SSP`) gives the **cost attributable to climate change**, net of socioeconomic drivers:

```text
climate-attributable cost = base − base_nocc   (likewise for mid and high)
```

---

## Notes for Users

- **Cumulative values.** Each cost `value` is the cost accumulated from 2020 up to and including `yr`; series never decrease. The three investment components are zero in 2020, while `Electricity` already includes 2020 spending. For the **annual cost**, take the first difference from the previous year within each country × component × `SSP` group; for 2020, the annual cost is the 2020 value itself.
- **Regional aggregation.** Cost values are levels, so aggregating countries into regions is a simple **sum** (no weighting).
- **Combining with the ACCREU energy-demand dataset** ([*CMCC Climate Adaptation Energy Dataset*](https://github.com/francescocolelli/ACCREU_energy_demand_datasets)): **drop the `Electricity` component**. The energy-demand dataset already includes residential energy expenditure, so keeping it here would double count the intensive margin. Use the three investment components from this dataset (extensive margin) together with the energy-demand dataset (intensive margin).
- **Services and industry** are not included. They could be approximated by upscaling with the top-down sectoral projections, but this is not done in these files.

## Contact

Giacomo Falchetta, CMCC Foundation, [giacomo.falchetta@cmcc.it](mailto:giacomo.falchetta@cmcc.it)

## Funding Acknowledgement

This work was supported by the **Assessing Climate Change Risk in Europe (ACCREU)** project, funded by the European Commission under the **Horizon Europe** programme (grant agreement No. 101081358).

**Project website:** [ACCREU Website](https://www.accreu.eu/)
