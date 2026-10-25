# University Building Decarbonisation Analysis

An Excel and Power BI project assessing the potential costs, energy use and emissions impact of replacing gas heating with heat pumps across **20 fictional university buildings**.

The project combines a formula driven Excel model with a simple two page Power BI report. It explores how building data and consultant estimates can be brought together to support an estate wide decarbonisation programme.

**All buildings, consultant studies and engineering inputs are fictional.** UK government emissions factors and published business energy prices provide the reference assumptions. Results are illustrative and do not represent the University of Oxford or any other institution.

## Project objectives

- Estimate total capital expenditure and annual emissions avoided.
- Calculate useful heat demand and heat-pump electricity consumption.
- Compare heating energy costs and total annual operating costs before and after conversion.
- Recalculate consultant bill estimates using a common set of tariffs.
- Compare results across four building clusters.
- Identify missing inputs, electrical capacity shortfalls and assumptions requiring verification.

## Tools and deliverables

| Tool / file | Purpose |
| --- | --- |
| Microsoft Excel | Building register, editable assumptions, calculations, summaries and QA |
| Power Query | Import and join workbook tables using building IDs |
| DAX | Calculate report totals, ratios and filtered results |
| Power BI Desktop | Interactive overview and building review pages |
| `University_Decarbonisation_Buildings.xlsx` | Main analysis workbook |
| `University_Decarbonisation.pbix` | Power BI report with imported data |

## Dataset

The synthetic estate contains libraries, teaching spaces, laboratories, residences, offices and other university facilities. Each of the **North, Central, South and West** clusters contains five buildings.

Building inputs include annual gas and electricity consumption, boiler efficiency, heat demand reductions, seasonal heat-pump performance, design heat loads, proposed solar PV capacity, fabric treatment areas and available electrical capacity.

The model assumes all existing gas consumption serves heating and hot water, and that heat pumps replace this gas use completely.

## Methodology

The Excel workbook contains eight worksheets: **Summary, Assumptions, Energy, CAPEX, Consultant, Buildings, QA, and Guide and sources**. Editable inputs are highlighted in amber.

The main calculations are:

| Calculation | Method |
| --- | --- |
| Baseline useful heat | Gas consumption × boiler efficiency |
| Proposed useful heat | Baseline useful heat × (1 − heat demand reduction) |
| Heat-pump electricity | Proposed useful heat ÷ seasonal coefficient of performance (SCOP) |
| Proposed grid electricity | Existing electricity + heat-pump electricity − self-used PV generation |
| Annual emissions avoided | Baseline Scope 1 and 2 emissions − proposed Scope 1 and 2 emissions |
| Annual OPEX saving | Baseline energy and maintenance costs − proposed energy and maintenance costs |
| Cost per annual tonne avoided | Total CAPEX ÷ annual tonnes of CO₂e avoided |
| Simple payback | Total CAPEX ÷ positive annual OPEX saving |

**CAPEX** is the upfront investment in heat pumps, electrical upgrades, PV and fabric works, including fees and contingency. **OPEX** covers annual energy bills and modelled plant maintenance.

Heating energy costs are compared separately: baseline gas cost versus proposed heat-pump electricity cost, before PV credits and maintenance. This keeps heating costs distinct from whole-building operating costs.

For consultant comparisons, the same energy quantities are priced using each fictional consultant's tariffs and then the common tariffs. This isolates the effect of tariff assumptions.

## Headline findings

Results below use the supplied base assumptions and are rounded.

| Metric | Result |
| --- | ---: |
| Total estimated CAPEX | £21.91 million |
| Annual emissions avoided | 3,147 tCO₂e |
| Reduction in modelled operational emissions | 48.4% |
| Annual heating energy cost before conversion | £1,003,200 |
| Annual heating energy cost after conversion | £997,472 |
| Annual heating energy saving | £5,728 |
| Annual whole-building OPEX saving | £323,603 |
| CAPEX per tonne of annual CO₂e avoided | £6,962 |
| Simple programme payback | 67.7 years |
| Additional peak electrical demand | 3,120 kW |
| Sum of building electrical capacity shortfalls | 2,080 kW |
| Increase in annual grid electricity imports | 10.4% |

The Central cluster has the largest estimated investment requirement and annual emissions reduction. Heating energy costs fall only slightly across the estate and increase in some clusters. Solar PV savings contribute substantially to the wider operating cost reduction.

The results also highlight the difference between carbon savings and financial returns: substantial emissions reductions coexist with a long simple payback period and additional electrical infrastructure requirements.

**£6,962 per annual tonne is an investment-to-annual-savings ratio. It is not a lifetime marginal abatement cost.** The programme ratio is calculated from portfolio totals, rather than averaging building-level ratios.

## Power BI report

### Programme overview

Four headline figures show CAPEX, annual emissions avoided, annual heating energy savings and CAPEX per annual tonne avoided. Three charts compare CAPEX, emissions avoided and heating costs by cluster. A cluster filter supports further exploration.

### Building review

A building-level table shows missing inputs, workbook QA results, verification status, capacity shortfalls and cost per annual tonne avoided. Additional figures highlight the number of buildings requiring verification and the increase in grid electricity imports.

## Data quality and verification

The supplied dataset has **no missing required numeric building inputs**, and all 20 building QA checks pass. Checks cover input completeness, duplicate IDs, energy balances, capital cost reconciliation and the consultant tariff comparison.

However, **all 20 buildings require verification** because their data are fictional. A QA pass confirms the listed arithmetic and input checks; it does not verify survey findings or cost estimates.

Before applying the model to a real estate, confirm meter data, boiler efficiencies, fabric savings, heat-pump performance, PV generation, electrical headroom and supplier quotations.

## How to use

1. Open the Excel workbook and review **Guide and sources**.
2. Update the amber input cells in **Assumptions**, **Buildings** and **Consultant**.
3. Recalculate and save the workbook, then review **QA**.
4. Open the `.pbix` file in Power BI Desktop. Its saved data can be viewed immediately.
5. Before refreshing on another computer, open **Transform data**, select the **Buildings** query and update the workbook path in **Advanced Editor**.
6. Select **Refresh** in Power BI and use the cluster filter to explore the results.

Power BI reads Excel's saved formula results; it does not recalculate the workbook. Adding buildings also requires extending the workbook's calculation rows, lookup ranges, QA and summaries.

## Reference assumptions and sources

Research date: **25 October 2026**.

| Assumption | Value | Basis |
| --- | ---: | --- |
| Natural gas combustion factor | 0.18231 kgCO₂e/kWh | DESNZ 2026, gross calorific value, Scope 1 |
| UK grid electricity factor | 0.13096 kgCO₂e/kWh | DESNZ 2026, location-based Scope 2 |
| Electricity benchmark | 24.51 p/kWh | DESNZ Q2 2026, all non-domestic consumption bands |
| Gas benchmark | 5.28 p/kWh | DESNZ Q2 2026, all non-domestic consumption bands |

The price benchmarks include the Climate Change Levy and exclude VAT. They are fully delivered average prices, not university contract quotes or marginal tariffs. Q2 2026 prices were provisional at publication.

- [DESNZ greenhouse gas reporting conversion factors 2026](https://www.gov.uk/government/publications/greenhouse-gas-reporting-conversion-factors-2026)
- [DESNZ non-domestic gas and electricity prices](https://www.gov.uk/government/statistical-data-sets/gas-and-electricity-prices-in-the-non-domestic-sector)
- [Quarterly Energy Prices: September 2026](https://www.gov.uk/government/statistics/quarterly-energy-prices-september-2026)

Exact source workbook references and further notes are recorded in **Guide and sources**. Engineering performance, capital costs and maintenance allowances are editable planning assumptions rather than government benchmarks.

## Limitations

- Annual calculations do not capture hourly demand, weather variation, PV timing or detailed system operation.
- Electrical peaks use a separate design COP. Cluster peaks are undiversified sums, and spare capacity is not pooled between buildings.
- Emissions cover gas combustion and location-based grid electricity. Embodied carbon, refrigerants and Scope 3 emissions are excluded.
- Costs exclude VAT, grants, financing, inflation, replacement cycles and residual values. Simple payback is not a discounted investment appraisal.
- Emissions factors and tariffs remain fixed. The model does not forecast future grid decarbonisation or energy prices.

## Possible next steps

Replace synthetic inputs with verified feasibility studies and meter data, separate space heating from hot water, test tariff and SCOP sensitivity, and develop a discounted whole-life cost assessment.

