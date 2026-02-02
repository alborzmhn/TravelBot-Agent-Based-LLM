## TravelBot: Intelligent Agent-Based Travel Planning Assistant

This project implements **TravelBot**, an intelligent travel planning chatbot built using **LangGraph** and **tool-augmented large language models**.
The system integrates multiple real-world APIs and datasets to provide comprehensive travel assistance through structured agent reasoning.

---

## Project Overview

TravelBot is designed to answer complex travel-related queries by:

- Understanding user intent
- Dynamically selecting appropriate tools
- Aggregating information from multiple sources
- Generating coherent, user-friendly responses

The implementation follows a **graph-based agent architecture** and is fully implemented in `NLP_HW5_Q2.ipynb`.

---

## Environment Setup

The notebook is executed in **Google Colab** and uses **Google Drive** for persistent storage.

### Library Installation

All required libraries are installed from a provided `requirements.txt` file.

### API Configuration

The following API keys are configured via environment variables:

- **OpenAI-compatible LLM endpoint** (AvalAI)
- **Tavily API** for web search
- **Amadeus API** for flight and hotel search

---

## Datasets and Preprocessing

### IATA Airport Dataset

- Dataset: `zinovadr/iata-airport-code` (from Kaggle)
- Used to build a **mapping from city names to IATA airport codes**
- Enables reliable flight and hotel search via the Amadeus API

### Preprocessing Steps

- Load and clean airport data
- Filter valid IATA codes
- Construct a dictionary mapping cities to airport codes
- Persist processed data for reuse

---

## TravelBot Features

TravelBot supports a wide range of travel-related functionalities:

- ![✈️](https://fonts.gstatic.com/s/e/notoemoji/16.0/2708_fe0f/32.png)

 **Flight Search**
Retrieve flight options between cities using Amadeus API.

- ![🏨](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f3e8/32.png)

 **Hotel Search**
Find available hotels in a destination city.

- ![🌦](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f326/32.png)

 **Weather Information**
Retrieve current and forecasted weather for destinations.

- ![💱](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f4b1/32.png)

 **Currency and Exchange Rate Information**
Provide currency details and conversion-related information.

- ![🍽](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f37d/32.png)

 **Restaurant Recommendations**
Suggest restaurants and dining options in the destination city.

- ![🗺](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f5fa/32.png)

 **Attractions and Sightseeing**
Recommend popular attractions and places to visit.

- ![📅](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f4c5/32.png)

 **Trip and Itinerary Suggestions**
Generate structured travel plans and trip ideas.

- ![🌍](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f30d/32.png)

 **General Destination Information**
Answer open-ended questions about cities and countries.

---

## Agent Architecture (LangGraph)

TravelBot is implemented as a **multi-tool LLM agent** using **LangGraph**.

### Core Design Principles

- Intent-aware tool selection
- Modular tool definitions
- Sequential reasoning over multiple API calls
- Unified response synthesis

### Tools Used by the Agent

Each capability is implemented as a callable tool using LangGraph’s tool interface:

- Flight search tool (Amadeus)
- Hotel search tool (Amadeus)
- Weather information tool (Tavily)
- Currency information tool (Tavily)
- Restaurant information tool (Tavily)
- Attraction information tool (Tavily)
- Trip suggestion tool (LLM-powered)

The agent dynamically chooses which tools to invoke based on the user query.

---

## Embeddings and Retrieval

- **Embedding Model:** `BAAI/bge-small-en-v1.5`
- **Vector Store:** LanceDB

Embeddings are used to support retrieval-augmented responses and contextual grounding when necessary.

---

## Workflow

1. User submits a travel-related query.
2. The agent analyzes intent and required information.
3. Relevant tools and APIs are invoked.
4. Retrieved results are aggregated and refined.
5. A final natural-language response is generated.

---

## Tools and Technologies

- Python
- LangGraph
- LangChain
- LanceDB
- Tavily API
- Amadeus API
- Kaggle Datasets
- Sentence Transformers (`BAAI/bge-small-en-v1.5`)

---

## Key Takeaways

- Agent-based architectures enable complex, real-world task handling
- Tool-augmented LLMs significantly expand chatbot capabilities
- LangGraph provides clear structure for multi-step reasoning
- TravelBot demonstrates a practical end-to-end NLP system

All implementation details and experiments are available in the notebook `NLP_HW5_Q2.ipynb`.
