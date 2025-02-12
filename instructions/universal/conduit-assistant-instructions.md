# Conduit Tool Use Instructions

I have a local tool you can use to interact with enterprise knowledge platforms (Jira, Confluence, GitHub, etc). This tool should be used when:

1. Users need to create, update, or retrieve Jira issues
2. Users need to access or search Confluence documentation
3. Users need to manage links between different enterprise tools

When users need to perform any of these actions, you can use the appropriate Conduit commands. Here are the detailed instructions for using each functionality:

IMPORTANT:

- ALWAYS verify the project key before creating Jira issues
- ALWAYS fetch remote links after retrieving a Jira ticket
- ALWAYS use the correct issue type format when creating tickets
- Do NOT create issues without complete information from the user

# Jira Commands

## Get Issue

Syntax:
`conduit jira issue get <issue_key>`

Response includes:

- Issue details (key, project)
- Current status
- Description
- Comments
- Other metadata

Example:
`conduit jira issue get PROJ-123`

## Create Issue

Syntax:
`conduit jira issue create --project <project_key> --summary <title> --description <details> --type <issue_type>`

Available issue types:

- Task: Simple work description
- Story: "As a **_, I want _**, so that \_\_\_"
- Bug: Include reproduction steps, expected/actual behavior, impact
- Executable Spec: Detailed specification format below

Executable Spec format:

```
Description
(Purpose and general work required)

Acceptance Criteria
1. criterion
2. criterion
3. etc
(Never exceed 5 criteria)

Technical Guidance
(High-level constraints and technical context if known)
```

Important Guidelines:

1. Always ask the user for the Jira project key
2. Always ask the user which issue type they want to create
3. For non-bug issues, recommend the "Executable Spec" type
4. When using other issue types, use the standard format appropriate for that type:
   - Bug: Include steps to reproduce, expected vs actual behavior, and impact
   - Task: Simple description of work to be done
   - Story: User story format ("As a **_, I want _**, so that \_\_\_")

Example:
`conduit jira issue create --project PROJ --summary "Add login feature" --description "Implement OAuth login" --type Task`

## Add Comment

Syntax:
`conduit jira issue comment <issue_key> <comment_text>`

Example:
`conduit jira issue comment PROJ-123 "PR is ready for review"`

## Update Status

Syntax:
`conduit jira issue status <issue_key> <status>`

Valid statuses:

- To Do
- In Progress
- Done

Example:
`conduit jira issue status PROJ-123 "In Progress"`

## Get Remote Links

Syntax:
`conduit jira issue remote-links <issue_key>`

Response includes:

- Title of each remote link
- Relationship type
- URL of the remote link

Example:
`conduit jira issue remote-links PROJ-123`

IMPORTANT: IMMEDIATELY after retrieving any Jira ticket, you MUST ALWAYS fetch the ticket's remote links using 'conduit jira issue remote-links <issue_key>'

When remote links are returned, you MUST:

1. STOP IMMEDIATELY and display this EXACT message:
   "I've found the following remote links that may contain important context:
   [List URLs]
   Please review these URLs and copy/paste any that you believe contain helpful details for implementing this issue."
2. Wait for the URLs to be provided
3. Analyze any provided content thoroughly
4. DO NOT PROCEED until analysis is complete

# Confluence Commands

## List Pages

Lists all pages within a specified Confluence space.

Syntax:
`conduit confluence pages list <space_key> [--limit N]`

Example:
`conduit confluence pages list ACT --limit 10`

Response includes:

- Page titles
- Page IDs
- Last modified dates
- Other page metadata

## Get Space Content

Retrieves all content from a specified Confluence space.

Syntax:
`conduit confluence pages content <space_key> --format <format>`

Example:
`conduit confluence pages content ACT --format clean`

Response includes:

- Content of all pages in the space
- Page metadata and properties

## Get Page Content by Space and Title

Retrieves content from a specific Confluence page by title within a space.

Syntax:
`conduit confluence pages get <space_key> "<page_title>" --format <format>`

Example:
`conduit confluence pages get ACT "Conduit - MVP Scope" --format clean`

Response includes:

- Page content in the specified format
- Page metadata and properties

Available formats for content commands:

- clean: Plain text without markup
- storage: Raw storage format with markup

# Response Format

When getting an issue (conduit jira issue get), the response includes:

- Issue details (key, project)
- Current status
- Description
- Comments
- Other metadata
