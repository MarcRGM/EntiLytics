# EntiLytics

**News Information Management System with BiLSTM-Based Entity Extraction and Summarization**

> A web-based platform that automatically identifies, ranks, and visualizes named entities in news articles to support efficient news comprehension.

Live site: Currently Offline - AWS Student Credits Expired

---

## What It Does

Reading news articles often means sorting through large amounts of text to find the people, organizations, and locations that actually matter to the story. EntiLytics automates this process.

Given a news article, the system will:

1. **Extract entities** (persons, organizations, locations, and miscellaneous) using a pretrained BiLSTM Named Entity Recognition model via the Flair NLP library
2. **Rank entities by importance** using a pretrained transformer model that weighs each entity's position in the text, mention frequency, and contextual relevance
3. **Map relationships** between entities by detecting which entities appear together within the same sentence, then visualizing the result as an interactive network graph
4. **Generate a summary** using extractive summarization, selecting the sentences most relevant to the top-ranked entities
5. **Store and annotate** articles and analysis results per user account, with personal notes saved to a database

---

## Tech Stack

| Layer                | Technology                                                                 |
| -------------------- | -------------------------------------------------------------------------- |
| UI Framework         | [Solara](https://solara.dev) (Python-based reactive web UI)                |
| NER Model            | [Flair](https://github.com/flairNLP/flair) (BiLSTM, trained on CoNLL-2003) |
| Importance Ranking & Extractive Summarization   | Pretrained transformer model (Hugging Face Transformers)                   |
| Relationship Mapping | NetworkX + Pyvis                                                           |
| Database             | PostgreSQL (Azure Flexible Server)                                         |
| ORM                  | SQLAlchemy                                                                 |
| Authentication       | Google OAuth 2.0                                                           |
| Containerization     | Docker                                                                     |
| Container Registry   | Azure Container Registry                                                   |
| Hosting              | Azure App Service for Containers                                           |
| CI/CD                | GitHub Actions                                                             |
| Domain               | Custom domain with Azure Managed SSL Certificate                           |

## Academic Context

This system was developed as a thesis project for the degree of **Bachelor of Science in Computer Science** at **Tarlac State University**, College of Computer Studies.

---

## Known Limitations

- Analysis is limited to English-language articles only
- Some RSS feeds provide partial article content rather than full text, which may affect analysis quality
- Session persistence on page refresh is under active development
- The system does not perform fact-checking or verify the credibility of news sources
- Internet connectivity is required for pretrained model access and RSS feed retrieval
