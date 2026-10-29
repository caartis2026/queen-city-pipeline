\## 2026-10-29 — Incremental ingest strategy



\*\*Decision:\*\* Each daily run pulls records with RECEIVED\_DATE >= (run date − 3 days), with no upper bound.



\*\*Why:\*\* Stateless — no watermark to store or corrupt. The 3-day lookback catches records that reach the portal late. The open upper bound captures records with future RECEIVED\_DATE values, a known data quality issue in this dataset.



\*\*Trade-off:\*\* Runs overlap, so raw/ holds duplicates. Deduplication on the record ID happens in the Phase 3 transform.



\*\*Alternative considered:\*\* OBJECTID high-water mark stored in S3. Rejected because it needs state, and because it is unverified whether OBJECTID only increases.



\## 2026-10-14 — Analysis scope



The 311 feed has no status or closed-date field, so resolution time can't be measured. Analysis focuses on request volume, request types, and trends by area.

