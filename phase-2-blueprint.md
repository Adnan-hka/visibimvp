# VISIBI Phase 2 Blueprint

This document outlines the planned evolution after MVP.  
Phase 2 focuses on scale, accuracy, automation, and industry leadership.

---

# 1. Multi-Prompt Query Expansion

Instead of 5 seed topics, VISIBI will expand into 20–200 prompts per topic:

- Discovery queries  
- Comparison queries  
- Problem-solving queries  
- Feature-based queries  

Example:
## “printers” → 50 natural-language query variations

---

# 2. Rolling 30-Day Window (Trend Analytics)

Store daily/delta results to enable:
- 7-day changes
- 30-day rolling visibility
- Trend lines
- Competitor emergence detection
- Seasonal variance analysis

Requires new table:
`daily_engine_results`

---

# 3. Automated Scheduling

Add:
- Weekly scans
- Monthly scans
- Category-level scanning

Via:
- Supabase cron jobs
- Worker queues

---

# 4. Additional AI Engines

Add integrations for:
- Claude 3 / Anthropic
- ChatGPT Web UI mode (Playwright automation)
- Gemini Advanced
- Perplexity Deep Search

---

# 5. Geographic Localisation

Support:
- US
- UK
- Canada
- Australia
- EU

Using:
- Prompt-based regional modifiers
- Proxy/geolocation rotation

---

# 6. Real ChatGPT Interface Capture (Premium Feature)

Scrape real UI (not API):
- Citations
- Interface-level content
- Footnotes
- Metadata

Using:
- Playwright
- Rotating residential proxies

---

# 7. Brand Reputation Layer

Extract:
- Positive attributes  
- Negative associations  
- Feature gaps  
- Pain points  
- Customer concerns  

Using NER + sentiment + clustering.

---

# 8. Multi-Brand Team Accounts

Add:
- Authentication
- Projects
- Teams
- Shared dashboards

---

# Summary

Phase 2 transforms VISIBI from an MVP into the industry’s leading AI Visibility Intelligence platform.

