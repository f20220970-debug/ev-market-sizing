# India EV Two-Wheeler Aftermarket: Market Sizing

A consulting-style market-sizing case: how big is the servicing and battery-replacement market for India's
electric two-wheelers (E2Ws), how fast will it grow to FY31, and where could an independent service business play?

**Deliverables**
- **Model:** [`model/ev2w_service_market.xlsx`](model/ev2w_service_market.xlsx), formula-driven, with sourced inputs, labelled assumptions, three scenarios and a sensitivity grid.
- **Deck:** [`deck/ev2w_aftermarket_deck.pdf`](deck/ev2w_aftermarket_deck.pdf) (PowerPoint: [`.pptx`](deck/ev2w_aftermarket_deck.pptx)), 12 slides with the answer first.
- **Memo:** [`reports/case_memo.md`](reports/case_memo.md), a one-page summary.

## Key results
- **Size today:** about **₹870 Cr in FY26**, on a fleet of roughly **4.4 million** E2Ws in use.
- **Size in FY31:** about **₹5,600 Cr** in the base case (≈45% a year), across a **₹3,600–8,200 Cr** bear-to-bull range, on a fleet of about **16 million**.
- **A battery wave arrives from FY28**, when FY22's scooters reach age six. Battery replacements are roughly **a third of the FY31 base-case market**.
- **Spend per vehicle beats sales growth as the driver.** Moving annual spend from ₹2,000 to ₹4,000 changes FY31 by **₹2,200–3,000 Cr**; moving sales growth from 10% to 30% changes it by **₹800–1,600 Cr** — because most of FY31's fleet has already been sold.
- **Where to play:** independent garages could address about **₹1,400 Cr by FY31** at a 25% share, with battery diagnostics and refurbishment, fleet contracts, and multi-brand doorstep service where OEM networks are thin.
- **Recommendation:** compete for a larger share of existing per-vehicle servicing spend rather than betting on fleet growth — subject to validating willingness to pay and service-centre economics.
- **Key uncertainties:** annual spend per vehicle (no published figure), battery life and replacement timing, sales growth (11% in CY2025), and independent-service penetration. The five checks that would resolve them are in the [memo](reports/case_memo.md).

## Approach
Bottom-up: E2W sales by year (Vahan-based sources) → fleet in use after scrappage → vehicles past their free first year ×
annual service and wear-parts spend, plus battery replacements as each year's sales reach replacement age. Spend per vehicle
is cross-checked against reported e-scooter maintenance costs (about half a petrol scooter's).

## Model structure
| Sheet | Contents |
| --- | --- |
| Cover | Question, answer (live formulas), colour code, sources |
| Inputs | Sourced sales data (blue) and assumptions (blue on yellow), by scenario |
| Model | Sales, fleet, paying fleet, service, battery and total market by year for bear, base and bull |
| Summary | Key outputs and two charts |
| Sensitivity | FY31 market across sales growth (10-30%) and spend per vehicle (Rs 2,000-4,000) |

## Quality checks
`src/market_model.py` re-implements the model in Python, and `tests/test_model.py` checks the workbook's calculated
values against it (every year and scenario), so a broken Excel formula fails the GitHub Actions run.
`src/build_model.py` rebuilds the workbook from code; `src/export_data.py` and `deck/build_deck.js` rebuild the deck.

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
pytest -q
```

## Sources
Argus Media and PIB (Vahan data, FY22-FY23), Ministry of Heavy Industries via Times Drive (FY24-FY25), IESA and
JMK Research via EV Infrastructure News (FY26), EVreporter (CY2025), MeraEV (maintenance costs), e-vehicleinfo and
BikeLeague (battery costs), IESA via IANS (state shares). Full list on the Cover sheet and the last slide.
