
---

# ✅ **2. milestones.md (FULL VERSION)**

```markdown
# VISIBI MVP Milestones (Cost-Control Breakdown)

This milestone breakdown ensures clear delivery, predictable cost, and structured development.

---

# M1 — Project Setup (4–6 hours)

### Tasks:
- Setup GitHub repo & branches
- Setup Supabase project
- Create DB schema using SQL file
- Setup environment variables
- Validate API keys for OpenAI, Gemini, Perplexity

### Deliverables:
- Repo + environment working
- Supabase schema created

---

# M2 — Frontend Input Form (6–8 hours)

### Tasks:
- Create form for brand/domain/email/topics
- Validate input
- Submit → call Supabase
- Create `scan_job` row
- Redirect to “Scan submitted” page

### Deliverables:
- `/start-scan` working
- Jobs visible in Supabase

---

# M3 — Backend Worker Core (12–20 hours)

### Tasks:
- Build Python worker with polling loop
- Visibility Prompt → JSON
- Sentiment Prompt
- Content Insights Prompt
- Extract citations, competitors, mentions, sentiment
- Compute visibility score
- Insert into:
  - engine_results
  - citations
  - content_insights
- Mark scan complete

### Deliverables:
- Full processing pipeline working

---

# M4 — Dashboard (12–18 hours)

### Tasks:
- `/dashboard/[jobId]` page
- Fetch Supabase data
- Bar chart (visibility)
- Donut chart (competitor SOV)
- Citations table
- Insights panel
- CSV Export

### Deliverables:
- Beautiful fully working dashboard

---

# M5 — QA & Testing (6–10 hours)

### Tasks:
- Run scans for multiple brands
- Validate JSON parsing
- Fix edge cases + errors
- Test Supabase writes
- UI consistency check

### Deliverables:
- Stable release-ready MVP

---

# M6 — Deployment (4–6 hours)

### Tasks:
- Frontend → Vercel
- Worker → Supabase Edge Function or Render
- Final integration test

### Deliverables:
- Live production MVP

---

# Estimated Total Cost

**44–68 hours @ £85/hour**  
= **£3,740 – £5,780**

This is aligned with project expectations.
