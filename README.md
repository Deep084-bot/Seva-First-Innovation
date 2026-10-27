# Bharuch Unified Works Portal (Demo Prototype)

This is an improved standalone HTML/CSS/JavaScript prototype for the Seva First Innovation Challenge 2026. It demonstrates cross-department work coordination with explainable, human-in-the-loop duplicate screening.

## How to run
1. Save `bharuch-works-portal-live-map.html` to your local machine.
2. Open it in a modern browser (Chrome/Edge/Safari) with internet access (for Leaflet tiles and place search).
3. No build step or server required - runs as a local HTML file.

## Key features
- **Dashboard**: Corrected metrics (distinguishes proposed/approved/in-progress/completed; labels "recorded value" not "sanctioned"). Shows session counters for reviews/withdrawals.
- **Map & Registry**: Filters, search, map-registry linkage. Approximate locations clearly labeled.
- **Propose a work**: Validation, location selection, explainable duplicate check with evidence.
- **Bulk import**: CSV validation, overlap flagging, detailed import summary (uses shared matching logic).
- **Public view**: Read-only; citizen reporting is demo-only (no server submission).
- **Tests & evaluation**: Deterministic synthetic scenarios for the matching engine.

## Demo data
- All records are **synthetic/illustrative**. Coordinates are approximate (derived from village centroids with offsets).
- Use "Reset to demo data" to restore original dataset. Data persists in localStorage (`bwlive_v2`).

## Matching logic (explainable)
- Candidate retrieval by type/proximity/village/name; proximity alone is not conclusive.
- Evidence-based scoring with normalization (handles common abbreviations like rd/marg).
- Classifications: High-priority potential overlap / Possible overlap requiring review / Weak similarity / No match.
- Human review required; matches not auto-rejected/deleted.

## Limitations (important)
- **No auth**: Role selector is UI simulation only; no authentication/authorization.
- **No backend**: All data in browser localStorage; audit log not tamper-proof.
- **Geospatial**: Point/approx geometry only - no precise road-segment/PostGIS spatial ops in this prototype.
- **No official integration**: PFMS/e-Gram Swaraj/GIS labeled as future work requiring authorization.
- **Demo only**: No real citizen report delivery, no government validation.

## Future architecture (proposed)
React/Node.js API + PostgreSQL/PostGIS, authenticated RBAC, centralized IDs, server audit trail, controlled imports, approved hosting/integrations.

## Safety notes
- HTML escaping used for dynamic text; validation on inputs.
- Malformed localStorage handled by falling back to demo data.
- No secrets/credentials in code.
