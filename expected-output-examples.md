# VISIBI Expected Output Examples

---

# 1. engine_results Example
```json
{
  "brand_mentioned": true,
  "brand_mentions_count": 1,
  "brand_positions": [2],
  "sentiment": "positive",
  "visibility_score": 65
}
```

---

# 2. citations Example
```json
[
  {
    "url": "https://www.hp.com/printers",
    "domain": "hp.com",
    "position": 1,
    "is_brand": false,
    "is_competitor": true
  }
]
```

---

# 3. content_insights Example
```json
{
  "preferred_formats": ["guide", "review"]
}
```

---

# 4. competitor_aggregates Example
```json
[
  {
    "domain": "hp.com",
    "total_citations": 14
  }
]
```
