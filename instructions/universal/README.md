# Coding the Future With AI - Universal Assistant Instructions

This directory contains instruction files that are part of the Coding the Future With AI workflow system. These instructions enable AI coding assistants to interact with CTF's open source tools for accessing external knowledge, managing software projects, and automating common development tasks. This integration reduces context switching and manual operations, allowing developers to more effectively leverage AI throughout their workflow. These instructions have been tested successfully with multiple AI coding assistants including aider, Cursor Composer, and Windsurf Cascade.

NOTE: These instructions have been tested successfully with aider, Cursor Composer, and Windsurf Cascade using the Claude 3.5 Sonnet model.

## CTF Open Source Tools

These instructions rely on tools from [Coding the Future with AI](https://github.com/codingthefuturewithai):

1. [RAG Retriever](https://github.com/codingthefuturewithai/rag-retriever)

   - Web search functionality for finding relevant documentation
   - Documentation search and retrieval
   - Web content indexing
   - Local knowledge base management
   - Content relevance scoring
   - Image content analysis
   - Confluence space indexing

2. [Conduit](https://github.com/codingthefuturewithai/conduit)

   - Project management functions via Jira
   - Documentation access via Confluence
   - Link management
   - Issue tracking workflows
   - Standardized templates
   - Rich text processing

   **Important Note for Aider Users**: When using conduit commands that create or update Jira issues with aider, you must launch aider with the `--no-git` option. This is required because conduit needs to write to files outside the code repository, which conflicts with aider's default git integration safety rules.

Please refer to each tool's repository for installation and configuration instructions.

## Files Overview

- **combined-assistant-custom-instructions.md** - Complete set of instructions for tool usage and hallucination prevention
- **command-execution-instructions.md** - Guidelines for proper shell command execution in subdirectories
- **conduit-assistant-instructions.md** - Instructions for using the Conduit tool for platform integrations
- **hallucination-prevention-instructions.md** - Strict protocol to prevent AI from making assumptions or guessing
- **rag-retriever-assistant-instructions.md** - Guidelines for using the RAG Retriever tool for knowledge base and web searches

## Assistant Behavior and Tool Use Instructions Analysis

The combined instructions file (`combined-assistant-custom-instructions.md`) provides a comprehensive framework for AI assistants to leverage CTF tools and prevent hallucination. Here's what these instructions accomplish:

### Zero Hallucination Protocol

- Forces the AI to stop when it lacks knowledge of specific versions
- Prevents the AI from making assumptions about features
- Requires explicit version information before proceeding
- Makes the AI acknowledge when it doesn't have complete information
- Eliminates the AI's tendency to try to be helpful by guessing

### Command Execution Standards

- Defines how to maintain directory context in command chains
- Specifies proper use of `&&` for command chaining
- Establishes conventions for path handling
- Ensures commands execute in the correct context

### Tool Integration Framework

- Establishes clear rules for when tools can be executed
- Prevents the AI from asking users to run commands themselves
- Removes unnecessary interaction steps
- Requires immediate tool execution when requested
- Enforces exact tool syntax usage

### Tool Execution Controls

- Prevents the AI from simulating tool output
- Requires explicit user requests for tool usage
- Enforces proper tool syntax
- Processes only real tool output
- Maintains tool execution boundaries

### Documentation Access

- Structured URL retrieval
- Content relevance evaluation
- Documentation format handling
- Source tracking
- Knowledge base integration

These instructions create a framework that:

1. Prevents AI hallucination about technical details
2. Enables seamless tool integration
3. Maintains clear boundaries for tool execution
4. Provides access to documentation resources
5. Establishes clear protocols for information retrieval
6. Defines exact conditions for tool usage

The combined format allows developers to quickly implement these controls in any AI coding assistant, creating a more integrated and efficient development workflow that reduces context switching and manual operations.
