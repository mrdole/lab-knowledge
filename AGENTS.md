# Rules for agents editing lab-knowledge

Every agent in every profile trusts this repo, so wrong content here spreads everywhere.

1. Only the `meta` profile edits this repo, and only through a branch and a draft MR.
2. New or changed facts are `status: draft`. Never set `verified` or `last_verified`.
   Only a human who checked it on the real system does that.
3. One fact or procedure per doc. Write symptom → cause → fix → how it was confirmed.
   Include exact error text, because agents search on it.
4. Never put secrets, tokens, passwords or private keys in docs or inventory. Name the
   variable or vault entry instead.
5. Inventory addresses are what bench agents connect to. Change them only when the task
   says so, and say which instrument you checked.
6. Don't edit `catalog/`. CI generates it.
7. Validate before opening the MR:
   ```
   python3 $AP_HOME/mcp/knowledge/knowledge_core.py validate . --profiles-from $AP_HOME/profiles
   ```
