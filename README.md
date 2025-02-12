# AI Tool Custom Instructions

This repository contains instruction sets and documentation that can be loaded into AI assistants to enhance their capabilities with custom tools. These instructions have been tested successfully with multiple AI coding assistants including aider, Cursor Composer, and Windsurf Cascade using the Claude 3.5 Sonnet model.

## Getting Started

To configure your AI coding assistant with these instructions:

1. Follow our [Setup Guide](instructions/setup/ai-assistant-setup-guide.md) which provides step-by-step instructions for:
   - Installing prerequisites (RAG Retriever and Conduit tools)
   - Configuring supported AI assistants (Aider, Cursor, and Windsurf)
   - Verifying your setup is working correctly

## Directory Structure

```
.
├── LICENSE.md
├── README.md
├── instructions/
│   ├── universal/           # Universal instruction sets
│   │   ├── README.md
│   │   ├── combined-assistant-custom-instructions.md
│   │   ├── command-execution-instructions.md
│   │   ├── conduit-assistant-instructions.md
│   │   ├── hallucination-prevention-instructions.md
│   │   └── rag-retriever-assistant-instructions.md
│   └── custom/             # Custom instruction sets
├── tests/
│   └── assistant-custom-tools-tests.md
```

## Instruction Sets

### Universal Instructions

The [universal instructions](instructions/universal/README.md) directory contains core instruction sets that can be used across different AI assistants:

- **Combined Assistant Instructions** - Complete set of instructions for tool usage and hallucination prevention
- **Command Execution Instructions** - Guidelines for proper shell command execution in subdirectories
- **Conduit Assistant Instructions** - Instructions for using the Conduit tool for platform integrations
- **Hallucination Prevention Instructions** - Strict protocol to prevent AI from making assumptions or guessing
- **RAG Retriever Assistant Instructions** - Guidelines for using the RAG Retriever tool for knowledge base and web searches

### Custom Instructions

The custom instructions directory contains specialized instruction sets for specific use cases or environments.

## Testing

The [tests](tests/assistant-custom-tools-tests.md) directory contains test cases and validation scenarios for the instruction sets.

## Tools Integration

These instructions enable AI assistants to work with the following tools:

1. **RAG Retriever**

   - Web search functionality
   - Documentation search and retrieval
   - Content relevance scoring
   - Knowledge base management

2. **Conduit**
   - Jira integration
   - Confluence integration
   - Issue tracking workflows
   - Standardized templates

## Contributing

This repository welcomes contributions of new instruction sets that can enhance AI assistant capabilities across various domains and use cases.

## License

[MIT License](LICENSE.md)
