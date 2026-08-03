# ai-technical-equipment-assistant
AI agent for answering questions about technical equipment documentation using Retrieval-Augmented Generation (RAG). Prioritizes official datasheets and falls back to web search when the requested information is unavailable.

# Overview
AI agent for answering questions about technical equipment documentation using Retrieval-Augmented Generation (RAG). Prioritizes official datasheets and falls back to web search when the requested information is unavailable.

# Features
- Answers questions using official technical documentation 
- Prioritizes information from manufacturer PDF datasheets
- Automatically falls back to Google Search when documentation is insufficient
- Maintains conversational context using memory
- Recommends compatible equipment based on official specifications
- Suggests alternative products when requested
- Explains technical specifications in natural language

# RoutingStrategy
1. Search the official PDF documentation. 
2. If the answer exists, use the documentation. 
3. Otherwise, search the web. 
4. Generate the final response while preserving conversation context.

# Architecture
- Flowise 
- OpenAI 
- Google Search 
- PDF

# TechStack
Framework
- Flowise
LLM
- OpenAI GPT-5.4-mini
Retrieval
- Retrieval-Augmented Generation (RAG)
- Vector Store
- PDF Retriever
Search
- Google Custom Search API
Memory
- Buffer Memory

# Knowledgebase
The assistant primarily relies on official manufacturer documentation stored as PDF files.

The knowledge base currently contains:

- Official product datasheet
- Technical specifications
- Recommended amplifier parameters
- Product compatibility information

If the requested information is not available in the documentation, the assistant automatically uses Google Custom Search as a secondary source.

# Tools
PDF Retriever
Google Custom Search

# Features
Answers using official documentation
Falls back to Google Search
Conversational Memory

# ExampleQuestions 
What amplifier is recommended? 
What is the impedance? 
What crossover frequency is used? 
Compatibility Recommend another amplifier. 
Internet Search Where can I buy this speaker? 
Are there reviews?

# ProjectStructure

```text ai-technical-equipment-assistant/ │ ├── README.md ├── LICENSE ├── flowise/ │ └── chatflow.json └── docs/ └── datasheet.pdf ```

# Installation
Before importing the project, make sure you have: 
- Flowise installed 
- An OpenAI API key 
- A Google Custom Search API key 
- A Google Custom Search Engine (CSE) 

- Setup 1. Clone this repository. (to install git https://git-scm.com/install)
```bash
git clone https://github.com/1845302-ops/ai-technical-equipment-assistant.git
```

2. Open Flowise. 
3. Import the file: ``` flowise/chatflow.json ``` 
4. Configure the required credentials: 
- OpenAI API 
- Google Custom Search API 
5. Add the provided PDF datasheet to the knowledge base. 
6. Save the chatflow and start chatting.

# Usage

After importing the chatflow into Flowise and configuring the required API credentials, you can start asking technical questions. 

# ExampleQuestions
Documentation 
- What amplifier is recommended for this speaker? 
- What is the nominal impedance? 
- What are the power ratings? 
- What are the dimensions of the speaker? 
- Can this speaker be used in low-impedance mode? 

Equipment Recommendations 
- Recommend another compatible amplifier. 
- Suggest an amplifier from a different brand. 
- Which amplifier is best for this speaker? 

 Web Search 
 - Where can I buy this speaker? 
 - Are there any customer reviews? 
 - Is this model still available?


# ChallengesSolutions
During development, I encountered a problem where the agent preferred web search even for documentation-related questions. I solved this by reworking the tool descriptions and priority logic so that official documentation became the primary source of knowledge, and web search was used only when information was unavailable in PDF format.

# FutureImprovements

- Support multiple PDF datasheets 
- Add image recognition for technical diagrams 
- Integrate additional web search providers 
- Improve tool routing with confidence scoring 
- Add multilingual support 
- Store conversation history in a database 
- Build a web interface for end users
