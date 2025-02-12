# Assistant Custom Tools Testing Guide

## User Queries

These are example queries you can use with the assistant. The assistant will choose the appropriate tool and command to execute.

1. "use conduit to get jira issue ACT-13"

   - Assistant used: `conduit jira issue get ACT-13`
   - Result: Failed (issue didn't exist)

2. "try ACT-3"

   - Assistant used: `conduit jira issue get ACT-3`
   - Result: Successfully retrieved issue details

3. "search the web using rag retriever for today's top political news"

   - Assistant used: `rag-retriever --web-search "today's top political news" --results 5`
   - Result: Retrieved news articles

4. "what can you find out about the Conduit knowledge tool with rag retriever?"

   - Assistant used: `rag-retriever --query "Conduit knowledge tool features capabilities documentation"`
   - Result: Retrieved tool documentation

5. "search jira for In Progress issues"

   - Assistant used: `conduit jira issue search "status = 'In Progress'"`
   - Result: Found ACT-22 in progress

6. "list all Confluence pages in the ACT space"
   - Assistant used: `conduit confluence pages list ACT`
   - Result: Retrieved 10 pages

---

# Command History

## RAG Retriever Commands

### 1. Web Search for Political News

```bash
rag-retriever --web-search "today's top political news" --results 5
```

Purpose: Search the web for current political news articles

### 2. Local Knowledge Base Search about Conduit

```bash
rag-retriever --query "Conduit knowledge tool features capabilities documentation"
```

Purpose: Search local documentation for information about the Conduit tool's features and capabilities

## Conduit Commands

### 1. Get Jira Issue (Failed Attempt)

```bash
conduit jira issue get ACT-13
```

Purpose: Attempt to retrieve details for Jira issue ACT-13 (failed due to non-existence or permissions)

### 2. Get Jira Issue (Successful)

```bash
conduit jira issue get ACT-3
```

Purpose: Successfully retrieved details for Jira issue ACT-3

### 3. Search In Progress Issues

```bash
conduit jira issue search "status = 'In Progress'"
```

Purpose: Search for all Jira issues currently in progress (found ACT-22)

### 4. List Confluence Pages

```bash
conduit confluence pages list ACT
```

Purpose: List all pages in the ACT (AI Coding Tools) Confluence space

## Available Conduit Commands (Not Yet Executed)

### Jira Operations

```bash
# Search issues using JQL
conduit jira issue search "project = ACT AND status = 'In Progress'"

# Create new issue
conduit jira issue create --project ACT-1000 --summary "TEST Issue" --description "Issue description" --type Task

# Update issue fields
conduit jira issue update ACT-1000 --summary "Updated Summary"

# Transition issue status
conduit jira issue status ACT-1000 "In Progress"
```

### Confluence Operations (If Configured)

```bash
# List pages in a space
conduit confluence pages list ACT --limit 10

# Get page content by space
conduit confluence pages content ACT --format clean

# Get specific page content by title
conduit confluence pages get ACT "Page Title" --format clean
```

Example:

```bash
# Get content of a specific page
conduit confluence pages get ACT "Conduit - MVP Scope" --format clean
```
