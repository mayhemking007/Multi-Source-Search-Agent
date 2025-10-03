# Multi-Source Search Agent (Console App)

This project is a **console-based multi-source search agent** powered by [LangChain](https://www.langchain.com/), [LangGraph](https://www.langchain.com/langgraph), [BrightData](https://brightdata.com/) APIs, and OpenAI’s GPT models.  

It allows you to query multiple sources (Google, Bing, Reddit, X, ChatGPT, and Perplexity) and aggregates their responses into a summarized answer with **sources included**.

---

## Features

- Console-based interactive query agent.
- Searches across:
  - Google
  - Bing
  - Reddit
  - X (Twitter)
  - ChatGPT (via BrightData dataset trigger)
  - Perplexity (via BrightData dataset trigger)
- Uses **LangGraph ReAct Agent** for orchestration.
- Aggregates and summarizes responses.
- Outputs a **final answer** along with **all sources** used.

---

## Files

- `main.py` → The script with all logic.
- `.env` → Environment variables for API keys (not committed to repo).
- `README.md` → This file.

---

## Environment Variables

The app requires a `.env` file in the project root with the following variables:

```env
BRIGHTDATA_API_KEY=your_brightdata_api_key
BRIGHTDATA_SERP_ZONE=your_serp_zone_id
BRIGHTDATA_GPT_DATASET_ID=your_brightdata_gpt_dataset_id
BRIGHTDATA_PERPLEXITY_DATASET_ID=your_brightdata_perplexity_dataset_id
```

## Requirements

- Python 3.9+

- requests

- python-dotenv

- langchain

- langgraph

- langchain-openai

## How to Run

- Clone this repository and navigate into it.

- Create a .env file with your BrightData API credentials.

- Run the script in your console:

```bash
python main.py
```

## How It Works (High-Level)

- Each search tool (google_search, bing_search, reddit_search, x_search, gpt_prompt, perplexity_prompt) is defined using @tool.

- Tools fetch data from BrightData API with requests.

- LangChain’s create_react_agent orchestrates calling multiple tools and reasoning over them.

- LangGraph is used to build a simple state graph with a single agent_node.

- The final output includes:

- Summarized text answer,

- Complete list of sources/links used.

## License

This project is provided for educational and experimental purposes.

Check BrightData and OpenAI terms before deploying in production.