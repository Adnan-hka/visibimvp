
---

# ✅ **4. validation-checklist.md (FULL VERSION)**

```markdown
# VISIBI Developer Validation Checklist (Before Approval)

This checklist must be fully passed before payment or milestone approval.

---

# 1. Backend Worker Validation

## Functionality
- [ ] Worker reads queued jobs
- [ ] Processes all topics × engines
- [ ] Stores results in correct tables
- [ ] Marks job completed
- [ ] No blocking errors

## Prompt Execution
- [ ] Visibility prompt returns valid JSON
- [ ] Sentiment prompt valid
- [ ] Content insights prompt valid

## Parsing
- [ ] Citations extracted correctly
- [ ] Sentiment parsed correctly
- [ ] Rank positions correct
- [ ] Competitors extracted

## Score
- [ ] Visibility score matches formula

---

# 2. Supabase Database Validation
- [ ] scan_jobs populated
- [ ] engine_results populated
- [ ] citations populated w/ correct FK
- [ ] content_insights populated
- [ ] competitor_aggregates correct
- [ ] No orphaned rows
- [ ] No null critical fields

---

# 3. Dashboard Validation
- [ ] Bar chart loads correctly
- [ ] Donut chart loads correctly
- [ ] Citation table loads
- [ ] Content insights visible
- [ ] CSV export works
- [ ] No React warnings or blank screens

---

# 4. Error Handling
- [ ] API failures handled cleanly
- [ ] Invalid JSON retries properly
- [ ] Worker continues even if one engine fails
- [ ] Failed jobs marked `failed`

---

# 5. Final Acceptance
- [ ] Tested with 10 real scans
- [ ] Citations validated manually
- [ ] Score validated manually
- [ ] Dashboard displays cleanly
- [ ] No performance issues

If all boxes are checked → the milestone is accepted.

