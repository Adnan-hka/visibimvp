# VISIBI MVP Scope Contract (v1)

This document defines the exact deliverables the developer must produce for the VISIBI MVP.  
The goals are clarity, fixed scope, predictable cost, and no ambiguity.

---

# 1. Objective
Build the VISIBI MVP: an AI visibility analytics tool that measures how visible a brand is inside generative AI engines (ChatGPT, Gemini, Perplexity) by analysing mentions, citations, sentiment, and content patterns based on seed topics provided by the user.

---

# 2. What the MVP MUST Do

## 2.1 Frontend (Next.js)
- Render a simple input form:
  - Brand name
  - Brand domain
  - Work email
  - Up to 5 seed topics
- Submit form → create `scan_job` record in Supabase.
- Redirect to a “Scan submitted” page.
- Dashboard page at `/dashboard/[jobId]` that displays:
  - Visibility scores (bar chart)
  - Competitor share-of-voice (donut chart)
  - Citations table
  - Content insights section
  - Recommendations section
  - CSV export

## 2.2 Backend (Python Worker)
### Must implement:
- Polling mechanism to detect `scan_jobs.status = 'queued'`
- For each `(topic × engine)`:
  1. Run **Main Visibility Prompt** → JSON
  2. Run **Sentiment Prompt**
  3. Run **Content Insights Prompt**
  4. Extract:
     - Brand mentions
     - Ranking position
     - Sentiment
     - Citations
     - Competitor domains
     - Content types
  5. Compute **visibility score (0–100)** using provided formula
  6. Store data in:
     - `engine_results`
     - `citations`
     - `content_insights`

### After all topics:
- Aggregate competitors into `competitor_aggregates`
- Mark job `completed`
- Trigger an email (placeholder function is acceptable)

---

# 3. Database Schema (Required)
Developer MUST implement the Supabase schema in `/backend/schema/supabase-schema.sql`.

---

# 4. AI Engine Integrations (Required)
- OpenAI Chat Completions (ChatGPT)
- Google Gemini 1.5 Pro
- Perplexity `chat/completions`

---

# 5. Output Requirements

For each topic × engine, system must produce:
```
{
  "brand_mentioned": true/false,
  "brand_mentions_count": int,
  "brand_positions": [1,3],
  "sentiment": "positive|neutral|negative",
  "visibility_score": 0–100
}
```

---

# 6. Out of Scope
- No UI scraping of ChatGPT interface
- No billing
- No full auth system
- No cron automation

---

# 7. Acceptance Criteria
- User can submit a scan
- Worker processes it fully
- Dashboard loads data correctly
