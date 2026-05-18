# Intelligent-Knowledge-Retrieval-System-Yu-Gi-Oh-

# Yu-Gi-Oh! Card Finding Assistant

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Framework-009688.svg)](https://fastapi.tiangolo.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Frontend-FF4B4B.svg)](https://streamlit.io/)
[![Weaviate](https://img.shields.io/badge/Weaviate-Vector_DB-black.svg)](https://weaviate.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-DB-336791.svg)](https://www.postgresql.org/)
[![LangChain](https://img.shields.io/badge/LangChain-Framework-white.svg)](https://langchain.com/)

An AI-powered chat assistant that helps players and collectors quickly and easily find the right Yu-Gi-Oh! cards from a database of over 40,000 cards.


## Motivation & Goal
Finding suitable cards for specific decks or strategies in large Yu-Gi-Oh! collections is often time-consuming and frustrating. There is frequently a lack of a good overview of relevant cards and their properties.

**This project demonstrates how modern LLMs (Large Language Models) combined with semantic search can provide real value.** **Goals:**
* Fast retrieval of relevant cards from a large collection.
* Automatic, understandable recommendations for users via natural language.
* Increasing efficiency and reducing frustration during card searches.


## Tech Stack & Architecture
The project is based on a modern RAG (Retrieval-Augmented Generation) architecture:

* **Frontend:** Streamlit (Interactive Chat)
* **Backend:** FastAPI
* **Databases:** PostgreSQL (Relational Data) & Weaviate (Vector Database for semantic search)
* **AI & Orchestration:** GPT-4o-Mini, LangChain Middleware & LangGraph (Agent control)

### Security Mechanisms (Guardrails)
A strong focus was placed on securing the system (In/Output Guardrails via LangChain):
* Blocking off-topic requests (e.g., writing Python scripts, discussing economic crises).
* Preventing toxic inputs (insults).
* **Data Integrity:** Strict blocking of database manipulations (`UPDATE`, `DELETE`, `INSERT`).


## 📊 Dataset & Preprocessing
* **Data Source:** [Yu-Gi-Oh Full Card Database Index](https://www.kaggle.com/datasets/hammadus/yugioh-full-card-database-index-august-1st-2025) (Kaggle)
* **Size:** 40,791 cards
* **Preprocessing:** * Text cleaning (removing spaces, special characters).
  * Structuring into relational lookup tables (types, attributes, volatilities) and main tables (cards, sets).
  * Harmonizing numerical values (price, attack, defense) and standardizing missing values (`= 0`).


## Results & Limitations

### What works well:
* Fast and very precise card matches via the chat.
* The pipeline (FastAPI + LLM + Weaviate) runs extremely stable.
* Guardrails reliably intercept unwanted prompts.

### Where are the weaknesses?
* The LLM sometimes confuses similar cards.
* The model still lacks a deep understanding of meta-strategies or complex synergies between different cards, which is why recommendations are not always strategically perfect.

### Future Enhancements:
* Use the model as an active "opponent" / training partner.
* Integrate a feature for automated and meaningful deck assembly (Deck-Building-Assistant).
