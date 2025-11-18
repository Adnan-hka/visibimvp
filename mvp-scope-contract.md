# VISIBI MVP Scope Contract (v1)

This document defines the exact deliverables the developer must produce for the VISIBI MVP.  
The goals are clarity, fixed scope, predictable cost, and zero ambiguity or scope creep.

---

# 1. Objective
Build the VISIBI MVP: an AI Visibility Analytics Tool that measures how visible a brand is across generative AI engines (ChatGPT, Gemini, Perplexity) using brand name, domain, and seed topics.

The MVP must:
- Collect AI answers
- Extract brand mentions, citations, sentiment, content patterns
- Calculate a visibility score
- Store all outputs in Supabase
- Display everything in a Next.js dashboard

---

# 2. What the MVP MUST Do

## 2.1 FRONTEND (Next.js)
The frontend must provide:

### ✔ 1. Input Form
Fields required:
- Work Email
- Brand Name
- Brand Domain
- Up to 5 Seed Topics

Flow:
User submits → creates a `scan_job` → redirected to a “Scan Submitted” screen.

### ✔ 2. Dashboard `/dashboard/[jobId]`
Must display:
- Visibility Score (bar chart)
- Competitor Share of Voice (donut chart)
- Citation Table
- Content Insights
- Recommendations
- CSV Export Button

Data comes directly from Supabase tables populated by the worker.

---

## 2.2 BACKEND (Python Worker)

The worker must:
1. Poll for queued jobs
2. For each *topic × engine*:
   - Run **Visibility Prompt**
   - Run **Sentiment Prompt**
   - Run **Content Insights Prompt**
3. Parse raw answers into structured fields:
   - Brand mentions (yes/no)
   - Mention count
   - Rank position
   - Sentiment
   - Citations
   - Competitors
   - Content types
4. Compute visibility score (0–100)
5. Store results in Supabase:
   - `engine_results`
   - `citations`
   - `content_insights`
6. Generate competitor aggregates
7. Mark job completed

---

# 3. Database Schema (REQUIRED)

The worker must write into these Supabase tables:

- `scan_jobs`
- `engine_results`
- `citations`
- `content_insights`
- `competitor_aggregates`

Schema defined in `/backend/schema/supabase-schema.sql`.

---

# 4. Required AI Engine Integrations

Worker must support:

### ✔ ChatGPT  
`openai.chat.completions.create` with **web search enabled**

### ✔ Gemini  
`gemini-1.5-pro` using **google_search_retrieval** tool

### ✔ Perplexity  
`POST https://api.perplexity.ai/chat/completions`  
Model: `sonar-small-online`

---

# 5. Output Requirements

Each `(topic × engine)` must generate:

```json
{
  "brand_mentioned": true,
  "brand_mentions_count": 1,
  "brand_positions": [2],
  "sentiment": "positive",
  "visibility_score": 65,
  "citations": [
    {
      "url": "https://…",
      "domain": "hp.com",
      "position": 1,
      "is_brand": false,
      "is_competitor": true
    }
  ],
  "preferred_formats": ["review","guide"],
  "competitors": ["hp.com","epson.com"]
}


### 6. OUT OF SCOPE (IMPORTANT)
 # These will NOT be delivered in MVP:
 # No scraping ChatGPT web UI
 # No scheduled scans
 # No rolling 30-day windows
 # No billing/payment system
 # No multi-user auth
 # No admin panel
 # No proxy or geo-rotation
 # No Claude integration
 # No caching layer
 # No notification system beyond placeholder email

# 7. Acceptance Criteria
 #   MVP is COMPLETE when:
  #  A scan_job can be created
   # The worker fully processes topics
    # All tables contain correct data
    # The dashboard displays the data correctly
    # CSV export works
    # No runtime errors block execution


# 8. Ownership
# All code, IP, and model prompts belong exclusively to VISIBI (Adnan).
# Developer may not reuse or resell any component of the system.
