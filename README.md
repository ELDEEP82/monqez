# Monqez | منقذ

Bilingual (Arabic / English) prototype that pre-screens Egyptian orange export batches against EU pesticide rules **before shipping**.

Monqez links Egyptian-market pesticide trade names to their active substances, EU approval status (Reg. 1107/2009), orange MRLs (Reg. 396/2005) and pre-harvest intervals, then estimates the probability a batch clears EU border checks.

## Features
- **Batch check** – spray program, post-harvest / storage / growth-regulator / mixture substances, optional lab results → traffic-light verdict, clearance probability, compliant alternatives
- **Detailed report** – what went wrong, since when a substance is banned, by how much the MRL is exceeded, regulatory notes (print / PDF)
- **EU database** – 516 orange MRL entries + 1,483 active substances, searchable, CSV export
- **Export tools (beta)** – pesticide label scanner (in-browser OCR), packaging advisor, shipment carbon footprint
- **Methodology** – risk function, thresholds, limitations, roadmap

## Risk model
`P(clear) = Π (1 − p_i)` where `p_i` depends on regulatory class (banned / import tolerance / approved / very low MRL / Annex IV), Δt = harvest − spray vs PHI, post-harvest use and measured residue ÷ MRL. See `src/engine.ts`.

## Data
- `data-src/MRL_FOR_ORANGES.xlsx` – EU Pesticides Database, product 0110020 Oranges (19/09/2026)
- `data-src/ActiveSubstanceExport_20-09-2026.xlsx` – EU active substances (20/09/2026)
- `data-src/trade_names.json` – indicative demo sample of trade names / PHI (to be replaced by the Egyptian APC registry)

Rebuild data: `python3 scripts/build_data.py`

## Run
```bash
npm install
npm run dev      # local
npm run build    # production build → dist/
```

Monqez is a pre-screening and decision-support tool. It does not replace laboratory testing or official border controls.

Idea & research: Howida R. Al-Refae
