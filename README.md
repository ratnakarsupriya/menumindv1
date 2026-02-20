# MenuMind 🍽️

> Ask anything about 9,000+ restaurants in plain English — powered by Zomato data + Claude AI.

**Live demo:** [your-url.vercel.app](https://your-url.vercel.app)

---

## What it does

MenuMind lets you chat with a real restaurant dataset in natural language. Ask things like:
- *"What are the top 5 highest rated restaurants?"*
- *"Show me cheap Italian places"*
- *"Which cuisines have the most restaurants?"*
- *"Best restaurants for delivery under 500 rupees?"*

The app does a keyword relevance search across 9,000+ rows, sends the most relevant data to Claude, and streams back a conversational answer — all grounded in real data.

---

## Tech stack

- **Frontend:** Vanilla HTML/CSS/JS — single file, zero framework
- **Backend:** Vercel serverless function (Node.js) — keeps the API key server-side
- **AI:** Anthropic Claude (claude-sonnet-4-20250514)
- **Data:** [Zomato Restaurants Dataset](https://www.kaggle.com/datasets/shrutimehta/zomato-restaurants-data) (Kaggle, free)

---

## Architecture

```
Browser (index.html)
  → loads zomato.csv locally
  → keyword searches relevant rows
  → POST /api/chat  ← your own endpoint
      → Vercel function (api/chat.js)
          → Anthropic API (API key never leaves server)
          → returns reply
  → renders response in chat UI
```

---

## Run locally

1. Clone this repo
2. Download `zomato.csv` from [Kaggle](https://www.kaggle.com/datasets/shrutimehta/zomato-restaurants-data)
3. Install Vercel CLI: `npm i -g vercel`
4. Create a `.env` file:
   ```
   ANTHROPIC_API_KEY=sk-ant-...
   ```
5. Run: `vercel dev`
6. Open `http://localhost:3000` and load your CSV

---

## Deploy to Vercel (5 minutes)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → Import project
3. Add environment variable: `ANTHROPIC_API_KEY` = your key
4. Deploy — done. Share the URL, no API key needed by visitors.

---

## Built by

Built as a portfolio prototype to demonstrate LLM integration, real dataset querying, and serverless API design.
