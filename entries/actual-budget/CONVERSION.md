# Conversion of Actual Budget

From `ActualBudget`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- actualbudget: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- actualbudget: container_name "actualbudget" is dropped; Maître names the container, and other containers reach it as "actualbudget"
- actualbudget: CasaOS's /DATA/AppData/actual-budget is the Service volume "actual_budget", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The volume is "data", not "actual_budget".
- Health is its own /health.
