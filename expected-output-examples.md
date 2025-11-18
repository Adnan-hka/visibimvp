# VISIBI Expected Output Examples (Worker → Supabase)

Below are realistic examples of the exact JSON the worker must insert into Supabase for a single topic × engine.

---

# 1. engine_results Example

```json
{
  "id": "uuid",
  "job_id": "uuid",
  "engine": "chatgpt",
  "topic": "printers",
  "visibility_prompt": "List the top 5 recommended brands for printers...",
  "raw_answer": "Canon is recommended because …",
  "raw_metadata": {
    "topic": "printers",
    "target_brand": "Canon",
    "target_brand_position": 2,
    "citations": [
      "https://www.hp.com/printers",
      "https://www.canon.co.uk/printers"
    ]
  },
  "brand_mentioned": true,
  "brand_mentions_count": 1,
  "brand_positions": [2],
  "sentiment": "positive",
  "visibility_score": 65
}

# 2. citations Example
[
  {
    "url": "https://www.hp.com/printers",
    "domain": "hp.com",
    "position": 1,
    "is_brand": false,
    "is_competitor": true
  },
  {
    "url": "https://www.canon.co.uk/printers",
    "domain": "canon.co.uk",
    "position": 2,
    "is_brand": true,
    "is_competitor": false
  }
]
# 3. content_insights Example
{
  "engine": "gemini",
  "topic": "photo printing",
  "preferred_formats": [
    "long-form guide",
    "review/comparison",
    "product page"
  ],
  "summary": "AI engines prefer detailed guides and side-by-side comparisons for photo printing topics.",
  "examples": [
    {
      "url": "https://www.digitalcameraworld.com/best-photo-printers",
      "content_type": "review/comparison",
      "note": "Frequently cited across ChatGPT and Gemini."
    }
  ]
}
# 4. competitor_aggregates Example
[
  {
    "domain": "hp.com",
    "total_citations": 14,
    "engines": ["chatgpt", "gemini"],
    "topics": ["printers", "troubleshooting"],
    "is_brand": false
  },
  {
    "domain": "canon.co.uk",
    "total_citations": 8,
    "engines": ["chatgpt", "perplexity"],
    "topics": ["printers", "photo printing"],
    "is_brand": true
  }
]





