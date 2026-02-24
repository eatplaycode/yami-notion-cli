# yami-notion CLI Wrapper

A comprehensive bash wrapper for the Notion API, optimized for Team Yami orchestration. It simplifies authentication, handles required headers, and standardizes task lifecycle management.

## Features

- **Automated Authentication**: Reads Notion API key from `~/.config/notion/api_key`.
- **Standardized Operations**: Pre-configured for the Yami Task Tracker database (`3119e6a65f4d809098c9d9ee58b65868`).
- **Full Lifecycle Management**: Create, query, update, and comment on tasks with simple CLI commands.

## Usage

### Create a New Task
Initializes a new page in the Yami Task Tracker with a status of `Analyzing`.
```bash
./yami-notion create "Task Title" "Description" "/path/to/project"
```

### Query Tasks
List tasks, optionally filtered by status.
```bash
./yami-notion query "Planning"
```

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
./yami-notion get <page_id>
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
