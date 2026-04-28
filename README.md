# Taste AI – Swiggy MCP POC

# Overview

Taste AI is an AI-powered food recommendation engine designed to integrate with chat-based systems like Swiggy’s MCP layer.
It understands user cravings, emotions, and intent to deliver personalized food suggestions along with intelligent upsell recommendations.

---

# Problem Statement

Food discovery inside delivery apps is often:

* Time-consuming
* Generic
* Lacking personalization

Users struggle to decide *what to eat*, especially when they don’t know exactly what they want.

---

# Solution

Taste AI acts as a **chat-based recommendation layer** that:

* Understands user intent (e.g., spicy, comfort, healthy)
* Recommends relevant dishes using AI embeddings
* Suggests upsell items to increase cart value
* Returns structured responses compatible with MCP systems

---

#  Key Features

## Intent Detection

Detects user mood and craving:

* Comfort (e.g., “bad day”)
* Spicy
* Healthy
* Late-night cravings

###  AI-Based Recommendation

* Uses Sentence Transformers (`all-MiniLM-L6-v2`)
* Semantic similarity matching (not keyword-based)

###  Smart Upsell Engine

* Suggests complementary items
* Example:

  * Biryani → Gulab Jamun
  * Pizza → Garlic Bread

###  MCP-Compatible Response

Returns structured JSON suitable for chatbot integration.

---

##  Tech Stack

* FastAPI (Backend API)
* Sentence Transformers (NLP)
* Scikit-learn (Similarity)
* Pandas (Data handling)
* Google Colab (Execution environment)

---

##  API Endpoint

### POST `/chat`

#### Request:

```json
{
  "message": "I want something spicy"
}
```

#### Response:

```json
{
  "mcp_version": "1.0",
  "intent": "spicy",
  "user_input": "I want something spicy",
  "recommendations": [
    {
      "dish_name": "Chicken Biryani",
      "category": "main",
      "confidence": 0.92
    }
  ],
  "upsell": {
    "add_on": "Gulab Jamun",
    "reason": "perfect dessert after spicy meal"
  }
}
```

---

## How to Run (Google Colab)

1. Install dependencies:

```bash
pip install fastapi uvicorn nest_asyncio sentence-transformers scikit-learn pandas
```

2. Run the notebook cells

3. Start the server (background thread)

4. Get public URL:

```python
from google.colab.output import eval_js
eval_js("google.colab.kernel.proxyPort(8000)")
```

5. Open:

```
https://<generated-url>/docs
```

---

## Demo Flow

**User Input:**

> “Had a long day, want something comforting”

**AI Output:**

* Chocolate Lava Cake
* Pasta Alfredo
* Upsell: Ice Cream

---

##  Business Impact

| Feature            | Impact                 |
| ------------------ | ---------------------- |
| AI Recommendations | Faster decision-making |
| Personalization    | Higher engagement      |
| Upsell Engine      | Increased AOV (15–25%) |
| Chat Interface     | Better UX              |

---

## Future Enhancements

* 📍 Restaurant mapping (ETA, pricing, location)
* 🧠 User personalization (history-based)
* 📊 Analytics dashboard (conversion tracking)
* 🧾 Menu ingestion using RAG (PDF/real menus)
* 💬 Full chat UI (Swiggy-like interface)

---

## Notes

* This is a Proof of Concept (POC)
* No external APIs (like Swiggy) are directly integrated
* Designed to demonstrate MCP compatibility

---

## Vision

> “Not replacing food discovery — we are making it intelligent, contextual, and conversion-driven.”

---

## Contact

For collaboration or discussion, feel free to reach out. at rey.yash99@gmail.com

---
