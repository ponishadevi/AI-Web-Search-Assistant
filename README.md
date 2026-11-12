# AI Web Search Assistant using Tavily, Groq and Streamlit

## 1. Project Overview

**Project Name:** AI Web Search Assistant  
**Project Type:** Generative AI Application  
**Programming Language:** Python

**Technologies:** Python, Streamlit, Tavily API, Groq API, GPT-OSS-120B

### What is this project?

AI Web Search Assistant is a Generative AI application that searches the internet and generates answers to user questions using a Large Language Model (LLM).

The application integrates:
- **Tavily** for web search and information retrieval.
- **Groq** for accessing an LLM.
- **Streamlit** for building the user interface.
- **Python** for application logic and API integration.

Users can enter a question, retrieve relevant information from the internet, and receive an AI-generated response based on the retrieved search results.

---

## 2. Aim of the Project

To develop a simple AI-powered web application that retrieves relevant information from the internet and generates meaningful answers using a Large Language Model.

## 3. Project Objectives

1. Build an interactive web application using Streamlit.
2. Integrate Tavily API for web searching.
3. Integrate Groq API to access a Large Language Model.
4. Retrieve relevant information based on user questions.
5. Pass retrieved search results as context to the LLM.
6. Generate answers using the retrieved information.
7. Display AI-generated answers and source URLs.
8. Understand how APIs, search engines, and LLMs work together in a Generative AI application.

---

## 4. Technologies and Concepts Used

### 4.1 Python

**Definition:** Python is a programming language used to develop applications, automate tasks, process data, and build AI solutions.

**Usage in this project:**
- Integrating external APIs.
- Processing search results.
- Preparing context.
- Sending prompts to the LLM.
- Handling application logic.

### 4.2 Streamlit

**Definition:** Streamlit is an open-source Python framework used to create interactive web applications without extensive frontend development.

**Usage in this project:**
- Creating the user interface.
- Accepting questions from users.
- Creating input fields and buttons.
- Displaying AI-generated answers.
- Displaying source links.

### 4.3 Tavily API

**Definition:** Tavily is an AI-focused web search API designed to retrieve relevant web information for AI applications.

**Usage in this project:**
- Accepts the user's question as a search query.
- Searches the internet.
- Retrieves up to five search results.
- Returns titles, content, and URLs.

### 4.4 Groq API

**Definition:** Groq provides an inference platform that allows developers to access supported Large Language Models through an API.

**Usage in this project:**
- Receives the user's question.
- Receives the retrieved search information.
- Sends messages to the selected LLM.
- Returns the generated answer.

### 4.5 LLM – Large Language Model

**Definition:** An LLM is an AI model trained on large amounts of data to understand and generate human language.

**Model used:** `openai/gpt-oss-120b`

**Usage in this project:**
- Understands the user's question.
- Processes the supplied search context.
- Generates a natural-language response.

### 4.6 API – Application Programming Interface

**Definition:** An API allows two software applications to communicate with each other.

**Usage in this project:**
- Tavily API communicates with the web search service.
- Groq API communicates with the LLM inference service.

### 4.7 API Key

**Definition:** An API key is a credential used to authenticate an application when accessing an external service.

**Usage in this project:**
- Tavily API key authenticates search requests.
- Groq API key authenticates LLM requests.

API keys are stored using Streamlit secrets.

### 4.8 Prompt Engineering

**Definition:** Prompt engineering is the process of designing instructions and input messages to guide an LLM to generate useful responses.

**Usage in this project:**

The system prompt instructs the model to:
- Answer using the provided search results.
- Clearly mention when the information is insufficient.
- Treat search results as untrusted data.

The user prompt contains the question and retrieved search results.

### 4.9 Context

**Definition:** Context is the information supplied to an LLM to help it answer a particular question.

**Usage in this project:**

The search results retrieved by Tavily are combined into a context string containing titles, content, and URLs. This context is passed to the LLM.

### 4.10 Temperature

**Definition:** Temperature controls the randomness of an LLM's generated responses.

**Usage in this project:**

Temperature is set to `0.2` to encourage relatively focused and consistent answers.

### 4.11 Virtual Environment (venv)

**Definition:** A virtual environment is an isolated Python environment used to manage project-specific dependencies.

**Usage in this project:**

It keeps the packages required for this project separate from other Python projects.

### 4.12 Streamlit Secrets Management

**Definition:** Streamlit secrets provide a way to store sensitive configuration values outside the main Python source code.

**Usage in this project:**

The Tavily and Groq API keys are stored in `.streamlit/secrets.toml` and accessed through `st.secrets`.

---

## 5. Project Architecture

```text
                 USER
                   |
                   v
          STREAMLIT APPLICATION
                   |
                   v
             USER QUESTION
                   |
                   v
               TAVILY API
                   |
                   v
              WEB SEARCH
                   |
                   v
             SEARCH RESULTS
                   |
                   v
          CONTEXT PREPARATION
                   |
                   v
                GROQ API
                   |
                   v
             GPT-OSS-120B
                   |
                   v
            GENERATED ANSWER
                   |
                   v
          STREAMLIT DISPLAY
                   |
                   v
                  USER
```

---

## 6. Working Flow – Step by Step

### Step 1: User Input

The user enters a question using the Streamlit text input field.

### Step 2: Tavily Web Search

The application sends the user's question to Tavily using the search API.

The application requests up to five search results using `max_results=5`.

### Step 3: Information Retrieval

Tavily returns search results containing:
- Title
- Content
- URL

### Step 4: Context Preparation

Python extracts the retrieved search results and combines them into a single context string.

The context includes the title, content, and URL of each search result.

### Step 5: Groq API Integration

The application sends the user question and retrieved context to the selected LLM through the Groq API.

### Step 6: LLM Processing

The LLM processes the question and supplied context based on the system instructions.

It generates a natural-language answer.

### Step 7: Response Display

Streamlit displays the generated answer to the user.

### Step 8: Source Display

The application displays the URLs of the retrieved web sources.

---

## 7. Important Code Components

| Code | Purpose |
|---|---|
| `st.set_page_config()` | Configures the Streamlit page |
| `st.title()` | Displays the application title |
| `st.secrets` | Reads API keys securely |
| `TavilyClient()` | Initializes the Tavily client |
| `Groq()` | Initializes the Groq client |
| `st.text_input()` | Accepts the user's question |
| `st.button()` | Creates the search button |
| `st.spinner()` | Displays a loading indicator |
| `tavily_client.search()` | Retrieves web search results |
| `search_results.get("results", [])` | Extracts search results |
| `context` | Stores formatted search information |
| `groq_client.chat.completions.create()` | Sends messages to the LLM |
| `temperature=0.2` | Controls response randomness |
| `response.choices[0].message.content` | Extracts the generated answer |
| `st.write()` | Displays the AI answer |
| `st.markdown()` | Displays clickable source links |
| `st.warning()` | Displays warning messages |

---

## 8. Project Folder Structure

```text
AI-Web-Search-Assistant/
│
├── app.py
│
├── README.md
│
├── requirements.txt
│
├── .gitignore
│
└── .streamlit/
    └── secrets.toml
```

### File Descriptions

| File | Purpose |
|---|---|
| `app.py` | Main Python application |
| `README.md` | Project documentation |
| `requirements.txt` | Lists required Python packages |
| `.gitignore` | Excludes unwanted and sensitive files from Git |
| `secrets.toml` | Stores API keys locally |

**Note:** The `.streamlit/secrets.toml` file must not be uploaded to GitHub.

---

## 9. Installation and Execution

### Prerequisites

- Python 3.10 or later
- VS Code or another Python editor
- Tavily API key
- Groq API key

### Step 1: Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### Step 2: Navigate to the project folder

```bash
cd AI-Web-Search-Assistant
```

### Step 3: Create a virtual environment

```bash
python -m venv venv
```

### Step 4: Activate the virtual environment

Windows PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

### Step 5: Install dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Configure API keys

Create a folder named `.streamlit` and a file named `secrets.toml` inside it.

Add your own API keys:

```toml
TAVILY_API_KEY = "your_tavily_api_key"
GROQ_API_KEY = "your_groq_api_key"
```

Never upload real API keys to GitHub.

### Step 7: Run the application

```bash
streamlit run app.py
```

The application will open in your browser.

---

## 10. Python Packages Used

The project uses the following Python packages:

```text
streamlit
tavily-python
groq
```

These packages should be listed in `requirements.txt`.

---

## 11. Difference Between the Technologies

| Technology | Responsibility |
|---|---|
| Python | Application logic |
| Streamlit | User interface |
| Tavily | Web search and information retrieval |
| Groq | LLM inference platform |
| GPT-OSS-120B | Language model that generates answers |
| API | Communication between applications |
| MCP | Standard protocol for connecting AI applications with tools and data sources |

**Important distinction:**

This project currently uses direct API integration.

It does not currently implement an MCP server, MCP client, vector database, conversation memory, or autonomous agent loop.

MCP integration can be added as a future enhancement.

---

## 12. What I Learned from This Project

Through this project, I learned:

1. How to create and activate a Python virtual environment.
2. How to install and manage Python dependencies.
3. How to use API keys for external service authentication.
4. How to integrate Tavily for web search.
5. How to integrate Groq to access an LLM.
6. How to retrieve and process web search results.
7. How to prepare context and pass it to an LLM.
8. How to use system and user prompts.
9. How to build a web interface using Streamlit.
10. How to display AI-generated answers and source links.
11. How to manage API keys using Streamlit secrets.
12. How different components work together in a Generative AI application.

---

## 13. Current Limitations

- The application depends on external API availability.
- Search quality depends on the results returned by Tavily.
- Answer quality depends on the selected LLM and supplied context.
- The application does not currently maintain conversation history.
- The application does not currently use a vector database.
- The application does not currently implement MCP.
- The application does not have an autonomous agent decision-making loop.
- Source links are displayed, but individual factual claims are not independently verified.

---

## 14. Future Enhancements

1. Integrate Tavily as an MCP tool.
2. Build a custom MCP server using FastMCP.
3. Connect an MCP client to the application.
4. Develop an AI agent that can decide when to use search tools.
5. Add conversation history and memory.
6. Integrate additional tools such as calculators and database search.
7. Implement a RAG pipeline using a vector database.
8. Improve source citations and answer validation.
9. Add chat history and a better user interface.

---

## 15. Project Summary

AI Web Search Assistant demonstrates how to build a basic Generative AI web application using Python, Streamlit, Tavily, Groq, and GPT-OSS-120B.

Tavily retrieves information from the internet, Groq provides access to the selected LLM, and Streamlit provides an interactive interface for users.

This project provides a foundation for understanding API integration, information retrieval, prompt engineering, context preparation, and LLM-based answer generation.

**Project Status:** Basic AI Web Search Application – Completed as a learning project.

**Repository:** AI-Web-Search-Assistant
