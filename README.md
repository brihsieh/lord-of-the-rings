# Lord of the Rings — Quote Recommender

**Live site:** https://brihsieh.github.io/lord-of-the-rings

Describe a situation and get back the most thematically resonant quote from Tolkien's *Lord of the Rings* trilogy. Think of it like a GIF recommender, but for Middle-earth wisdom.

---

## How it works

You describe a situation in plain English. The app sends it to a Vercel serverless function, which calls the Gemini API to find the 2 best-matching quotes from a curated dataset of 50 quotes. Each result includes an explanation of why the quote fits.

```
User types a situation
        ↓
GitHub Pages frontend (index.html)
        ↓
Vercel serverless function (api/recommend.js)
        ↓
Google Gemini API (semantic matching)
        ↓
2 quote recommendations + reasons
```

---

## Repo structure

This repo holds the frontend only.

```
lord-of-the-rings/
└── index.html       # Single-file frontend — all HTML, CSS, and JS
```

The backend lives in a separate repo (`lotr-backend`) and is deployed on Vercel.

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, vanilla JavaScript |
| Hosting | GitHub Pages |
| Backend | Vercel serverless function (Node.js) |
| AI | Google Gemini API (`gemini-2.5-flash`) |
| Fonts | Cormorant Garamond + Jost (Google Fonts) |

---

## Quote dataset

50 quotes curated from:
- *The Fellowship of the Ring*
- *The Two Towers*
- *The Return of the King*

Each quote is tagged with character, book, and theme. The dataset lives directly in `index.html` as a JSON array and is sent to the backend on each request — no database required.

To add quotes, find the `QUOTES` array in `index.html` and append entries in this format:

```json
{
  "uuid": "1a2b3c4d-0051",
  "text": "Your quote here.",
  "character": "Character name",
  "book": "The Two Towers",
  "theme": "courage"
}
```

---

## Running locally

No build step required. Open `index.html` directly in a browser — note that quote recommendations won't work locally without a running backend. For local backend development, clone the `lotr-backend` repo and follow its README.

---

*Built as a portfolio prototype. Quotes should be verified against a physical copy of the books before publishing — exact wording can vary between editions and film adaptations.*
