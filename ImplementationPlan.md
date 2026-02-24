# Implementation Plan - yami-notion CLI Wrapper

## 1. Project Goal
Develop a bash script `yami-notion` to encapsulate the complexity of Notion API calls, simplifying our architectural and orchestration workflows.

## 2. Technical Strategy
- **Language:** Bash script.
- **Dependencies:** `curl`, `jq`.
- **Authentication:** Load the Notion API key from `~/.config/notion/api_key` or `NOTION_API_KEY` environment variable.

## 3. Script Structure
The script will follow a standard CLI pattern:
- **Global Variables:**
  - `NOTION_VERSION="2025-09-03"`
  - `NOTION_API_URL="https://api.notion.com/v1"`
- **Internal Helper Functions:**
  - `_api_call()`: A generic function to perform the `curl` call with the required headers.
  - `_load_notion_key()`: Function to fetch the API key from the standard location.
- **Sub-Commands:**
  - `notion_get_page()`: Handles `GET /pages/{page_id}`.
  - `notion_update_status()`: Handles `PATCH /pages/{page_id}` with a status property.
  - `notion_append_content()`: Handles `PATCH /blocks/{block_id}/children`.
  - `notion_search()`: Handles `POST /search`.
- **Command Router:** A simple `case` statement to dispatch calls based on the first argument (e.g., `page`, `search`).

## 4. Implementation Details
### Authentication
- The script will search for the key in:
  1. `NOTION_API_KEY` environment variable.
  2. `~/.config/notion/api_key` file.
- Error and exit if no key is found.

### Example Function: `notion_update_status`
```bash
notion_update_status() {
  local page_id="$1"
  local status_name="$2"
  _api_call PATCH "/pages/$page_id" -d '{
    "properties": {
      "Status": {
        "status": { "name": "'"$status_name"'" }
      }
    }
  }'
}
```

## 5. Phased Roadmap
### Phase 1: Core Framework
- Implement `_load_notion_key` and `_api_call`.
- Basic script structure and help command.

### Phase 2: Status & Search
- Implement `notion_update_status` and `notion_search`.
- Test with the current "Team Yami Workflow" Notion page.

### Phase 3: Content Management
- Implement `notion_append_content` for updating ticket logs.

## 6. Handoff Checklist
- [ ] Bash script is executable (`chmod +x`).
- [ ] `jq` is available on the host.
- [ ] All functions work correctly with valid `page_id` and `data_source_id`.
- [ ] Error messages are clear for 4xx/5xx responses.
