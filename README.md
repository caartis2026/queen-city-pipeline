\# Queen City Pipeline



A serverless AWS data lake for Charlotte's 311 service requests (potholes, missed trash pickups, code violations).



\*\*Status:\*\* In progress, Phase 1 of 6 (account setup and first data pull).



\## Architecture (planned)

\- \*\*Ingest:\*\* EventBridge triggers a Python Lambda that pulls from the City of Charlotte open data API into S3 (raw, partitioned by date)

\- \*\*Transform:\*\* Raw JSON is cleaned, deduplicated, and written as Parquet to a curated S3 layer

\- \*\*Catalog and query:\*\* Glue Data Catalog and Athena SQL views

\- \*\*Orchestration:\*\* Step Functions with CloudWatch alarms

\- \*\*Infrastructure as code:\*\* Terraform



\## Questions this project answers

\- How does 311 request volume vary by neighborhood and council district?

\- How did request volume change after major storms?

\- Which request types are growing?

