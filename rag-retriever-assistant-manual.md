I have a local tool you can use to either search our knowledge base or discover relevant web URLs. These tools should ONLY be used as a last resort when:

1. Required information is not available in the local codebase
2. No relevant URLs or documentation links are available to analyze
3. Critical knowledge is still missing after exploring other options

When you need information but lack critical knowledge, and the above conditions are met,
you can search using either the knowledge base or web search options. Here's
instructions for how to use the search functionality:

IMPORTANT:

- PLACE QUOTES AROUND THE QUERY
- The --query option searches ONLY existing content in the knowledge base
- The --web-search option uses DuckDuckGo to discover potentially relevant URLs
- Do NOT use these tools if URLs or documentation links are available for direct analysis

# Knowledge Base Search

# Basic search

rag-retriever --query "How do I get started?"

# With custom result limit

rag-retriever --query "deployment options" --limit 5

# With minimum relevance score

rag-retriever --query "advanced configuration" --score-threshold 0.5

# JSON output format

rag-retriever --query "API reference" --json

Here's an example of a knowledge base query:

$ rag-retriever --query "What is the purpose of the RAG Retriever?" --score-threshold 0.1

1.  Source: ./docs/rag-retriever-usage-guide.md
    Relevance Score: 0.4766
    Content: RAG Retriever is a command-line tool for searching and retrieving information from a knowledge base built from both web documentation and local documents.

2.  Source: ./docs/rag-retriever-usage-guide.md
    Relevance Score: 0.4249
    Content: Search results include:
    - Source URL/file path
    - Relevance score (0.0-1.0)
    - Matching content snippet

Scores range from 0 to 1, where 1 indicates perfect similarity
Default threshold is 0.3
Typical interpretation:
0.7+: Very high relevance (nearly exact matches)
0.6 - 0.7: High relevance
0.5 - 0.6: Good relevance
0.3 - 0.5: Moderate relevance
Below 0.3: Lower relevance

# Web Search

The web search option helps discover potentially relevant URLs:

# Basic search

rag-retriever --web-search "your search query"

# Control number of results

rag-retriever --web-search "your search query" --results 10

When web search returns URLs, you MUST:

1. STOP IMMEDIATELY and display this EXACT message:
   "I've found the following URLs that may contain helpful information:
   [List URLs]
   Please review these URLs and copy/paste any that you believe contain helpful details for this task."
2. Wait for URLs to be provided
3. Analyze the content from those URLs thoroughly
4. Do not proceed until analysis is complete

Example web search:

$ rag-retriever --web-search "What is RAG in AI?" --results 2

1. Source: https://example.com/ai-rag-explained
   Title: Understanding RAG (Retrieval-Augmented Generation)
   Snippet: RAG combines large language models with external knowledge retrieval...

2. Source: https://example.com/rag-tutorial
   Title: Getting Started with RAG
   Snippet: RAG helps AI models access up-to-date information without retraining...
