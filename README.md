# yami-notion CLI Wrapper

A lightweight bash wrapper for the Notion API, optimized for use by Team Yami agents. It simplifies authentication, handles required headers, and standardizes common operations like status updates and commenting.

## Features

- **Automated Authentication**: Reads Notion API key from `~/.config/notion/api_key`.
- **Standardized Operations**: Pre-configured for the Yami Task Tracker database.
- **Fast & Efficient**: Replaces multi-line `curl` commands with single-line CLI calls.

## Usage

### Update Task Status
Updates the "Status" property of a Notion page.
```bash
./yami-notion update-status <page_id> "Planning"
```

### Add Comment/Block
Adds a new paragraph block to the body of a Notion page.
```bash
./yami-notion add-comment <page_id> "Your comment text here"
```

### Get Page Details
Retrieves the full JSON object for a specific page.
```bash
./yami-notion get-page <page_id>
```

## Setup

1. Ensure your Notion API key is stored at `~/.config/notion/api_key`.
2. Make the script executable:
   ```bash
   chmod +x yami-notion
   ```

## Files
- `yami-notion`: The bash wrapper script.
- `PRD.md`: Product Requirements Document.
- `ImplementationPlan.md`: Technical implementation details.
