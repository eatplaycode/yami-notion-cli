# PRD - yami-notion CLI Wrapper

## 1. Project Overview
Create a lightweight bash CLI wrapper for the Notion API. The goal is to encapsulate the complexity of raw `curl` calls, authentication headers, and JSON body construction into simple, reusable commands for our team's workflow.

## 2. Objectives
- **Simplicity:** Replace multi-line `curl` commands with single-line CLI calls.
- **Maintainability:** Centralize Notion API versioning and credential management.
- **Efficiency:** Speed up architectural and orchestration tasks by automating Notion updates.

## 3. Core Features
- **Authentication Management:** Automatically handle `Authorization` and `Notion-Version` headers using environment variables (e.g., `NOTION_API_KEY`).
- **Command Set:**
  - `yami-notion page get <page_id>`: Retrieve page properties.
  - `yami-notion page update <page_id> --status <status_name>`: Update the status property of a Notion page.
  - `yami-notion page append <page_id> --content <text>`: Append content (paragraphs) to a page.
  - `yami-notion search <query>`: Search for pages or databases.
- **Error Handling:** Provide meaningful exit codes and error messages for API failures (e.g., 401 Unauthorized, 404 Not Found).

## 4. Technical Constraints
- **Language:** Bash script (for maximum portability and zero dependencies).
- **Dependencies:** `curl`, `jq` (for JSON parsing/generation).
- **Environment:** Must run on the current host (`srv1314660`).

## 5. Non-Functional Requirements
- **Security:** Do not hardcode API keys; use `~/.config/notion/api_key` or environment variables.
- **Performance:** Minimal overhead on top of the raw API call.

## 6. Out of Scope
- Complex database schema management (e.g., creating new databases).
- Rich block types beyond simple paragraphs (for now).
