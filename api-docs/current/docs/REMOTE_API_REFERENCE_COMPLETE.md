# Complete Remote API Reference (All Endpoints)

Generated: 2026-02-21T16:41:32.037331+00:00
Updated: 2026-02-21

This reference is generated from ClawPad's live endpoint registry and ships locally with the app.

Total endpoints in this view: **143**

## AI Models

### `GET /api/models`

**Category:** AI Models

**Summary:** List AI Models

List all available AI models grouped by provider. ClawPad supports Anthropic (Claude), OpenAI (GPT), and Google (Gemini). Each project can use a different model.

**Tags:** models, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "anthropic": [
      {
        "id": "claude-sonnet-4-20250514",
        "name": "Claude Sonnet 4"
      },
      {
        "id": "claude-opus-4-20250514",
        "name": "Claude Opus 4"
      }
    ],
    "openai": [
      {
        "id": "gpt-4o",
        "name": "GPT-4o"
      },
      {
        "id": "o1",
        "name": "o1"
      }
    ],
    "google": [
      {
        "id": "gemini-2.0-flash",
        "name": "Gemini 2.0 Flash"
      }
    ]
  }
}
```

## Developer Docs & Discovery

### `GET /api/developer/dashboard`

**Category:** Developer Docs & Discovery

**Summary:** Developer Dashboard Payload (JSON)

Returns a machine-readable dashboard payload with endpoint inventory, category counts, and developer docs metadata.

**Tags:** developer, dashboard, json, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "base_url": "http://127.0.0.1:18790",
    "counts": {
      "endpoints_total": 143,
      "docs_total": 8
    },
    "openapi": {
      "swagger_ui": "/docs",
      "json": "/openapi.json"
    }
  }
}
```

**System effects:**
- Read-only discovery endpoint

### `GET /api/developer/docs`

**Category:** Developer Docs & Discovery

**Summary:** List/Search Developer Docs

Search and list long-form developer documentation articles for ClawPad Remote API. Supports full-text query and category filters.

**Tags:** developer, docs, search, read

**Query params:**
- `q` (string), optional - Full-text query
- `category` (string), optional - Docs category filter
- `limit` (integer), optional, default=50 - Max items (1-200)

**Response example:**
```json
{
  "success": true,
  "data": {
    "query": "stealth",
    "total": 1,
    "items": [
      {
        "doc_id": "stealth-mode",
        "title": "Stealth Mode: API-Only Server Runtime",
        "category": "Runtime",
        "summary": "Use ClawPad in headless offscreen mode for CI/automation."
      }
    ]
  }
}
```

**System effects:**
- Read-only discovery endpoint

### `GET /api/developer/docs/{doc_id}`

**Category:** Developer Docs & Discovery

**Summary:** Get Developer Doc Article

Retrieve one full developer documentation article, including markdown content and related endpoint references.

**Tags:** developer, docs, read

**Path params:**
- `doc_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "doc_id": "quickstart",
    "title": "Quickstart: Run ClawPad as an API Platform",
    "markdown": "# Quickstart...",
    "related_endpoints": [
      "/health",
      "/api/projects"
    ]
  }
}
```

**System effects:**
- Read-only discovery endpoint

### `GET /api/developer/reference`

**Category:** Developer Docs & Discovery

**Summary:** Complete Endpoint Reference (JSON)

Returns comprehensive endpoint documentation generated from the local registry, including descriptions, params, examples, and effects.

**Tags:** developer, reference, json, read

**Query params:**
- `q` (string), optional - Full-text endpoint query
- `method` (string), optional - HTTP method filter
- `category` (string), optional - Category filter
- `limit` (integer), optional, default=500 - Max endpoints (1-1000)

**Response example:**
```json
{
  "success": true,
  "data": {
    "total": 143,
    "returned": 143,
    "endpoints": [
      {
        "method": "GET",
        "path": "/health",
        "summary": "Health Check"
      }
    ]
  }
}
```

**System effects:**
- Read-only reference endpoint

### `GET /api/developer/reference/markdown`

**Category:** Developer Docs & Discovery

**Summary:** Complete Endpoint Reference (Markdown)

Returns the complete endpoint reference in Markdown format for local offline reading, export, or embedding in developer portals.

**Tags:** developer, reference, markdown, read

**Query params:**
- `q` (string), optional - Full-text endpoint query
- `method` (string), optional - HTTP method filter
- `category` (string), optional - Category filter
- `limit` (integer), optional, default=1000 - Max endpoints

**Response example:**
```json
{
  "content_type": "text/markdown"
}
```

**System effects:**
- Returns generated markdown

### `GET /api/developer/search`

**Category:** Developer Docs & Discovery

**Summary:** Unified Docs + Endpoint Search

Search across both developer docs and endpoint registry in a single call. Supports query text plus optional method/category filters.

**Tags:** developer, search, discovery, read

**Query params:**
- `q` (string), optional - Full-text query
- `method` (string), optional - Endpoint method filter
- `category` (string), optional - Endpoint category filter
- `limit_docs` (integer), optional, default=50 - Max docs
- `limit_endpoints` (integer), optional, default=200 - Max endpoints

**Response example:**
```json
{
  "success": true,
  "data": {
    "query": "auth token",
    "docs_total": 1,
    "endpoints_total": 4
  }
}
```

**System effects:**
- Read-only discovery endpoint

### `GET /developer/dashboard`

**Category:** Developer Docs & Discovery

**Summary:** Developer Dashboard (HTML)

Searchable HTML dashboard that lets developers browse docs and endpoints from one page in ClawPad.

**Tags:** developer, dashboard, html, read

**Response example:**
```json
{
  "content_type": "text/html"
}
```

**System effects:**
- Returns HTML UI

### `GET /docs`

**Category:** Developer Docs & Discovery

**Summary:** OpenAPI Swagger UI

Interactive OpenAPI Swagger UI generated by FastAPI. Use this for schema-driven endpoint exploration and request execution.

**Tags:** developer, openapi, swagger, docs, read

**Response example:**
```json
{
  "content_type": "text/html"
}
```

**System effects:**
- Returns HTML UI

### `GET /docs/oauth2-redirect`

**Category:** Developer Docs & Discovery

**Summary:** Swagger OAuth Redirect

Swagger UI OAuth redirect helper endpoint served by FastAPI.

**Tags:** developer, openapi, swagger, oauth, read

**Response example:**
```json
{
  "content_type": "text/html"
}
```

**System effects:**
- Returns HTML helper page

### `GET /openapi.json`

**Category:** Developer Docs & Discovery

**Summary:** OpenAPI Schema JSON

Raw OpenAPI schema JSON for codegen, tooling, and contract validation.

**Tags:** developer, openapi, schema, json, read

**Response example:**
```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "ClawPad Remote API"
  }
}
```

**System effects:**
- Read-only schema endpoint

### `GET /redoc`

**Category:** Developer Docs & Discovery

**Summary:** OpenAPI ReDoc

Alternative OpenAPI documentation UI (ReDoc) served by FastAPI.

**Tags:** developer, openapi, redoc, docs, read

**Response example:**
```json
{
  "content_type": "text/html"
}
```

**System effects:**
- Returns HTML UI

## Extensions & Tools

### `GET /api/extensions`

**Category:** Extensions & Tools

**Summary:** List Installed

List all installed extensions with their current status (running, stopped, error), install_state, enabled flag, and tool count.

**Tags:** extensions, installed, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "gmail",
      "name": "Gmail",
      "status": "running",
      "install_state": "installed",
      "enabled": true,
      "tool_count": 5
    },
    {
      "id": "filesystem",
      "name": "Filesystem",
      "status": "stopped",
      "install_state": "needs_download",
      "enabled": false,
      "tool_count": 0,
      "install_error": "Runtime artifacts are missing. Reinstall required."
    }
  ]
}
```

### `GET /api/extensions/catalog`

**Category:** Extensions & Tools

**Summary:** Browse Extension Catalog

Browse all 30 curated MCP extensions in the ClawPad catalog. Each extension adds new tool capabilities to the AI agent (e.g., Gmail, Spotify, GitHub, Notion). Returns name, author, description, category, stars, and environment variable specs.

**Tags:** extensions, catalog, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "gmail",
      "name": "Gmail",
      "description": "Read, send, and manage Gmail messages",
      "author": "ergut",
      "category": "email",
      "stars": 420,
      "env_vars": [
        {
          "name": "GMAIL_OAUTH_TOKEN",
          "required": true
        }
      ]
    }
  ]
}
```

### `GET /api/extensions/catalog/search`

**Category:** Extensions & Tools

**Summary:** Search Catalog

Full-text search across extension names, descriptions, authors, and categories. Returns matching catalog entries sorted by stars.

**Tags:** extensions, catalog, search, read

**Query params:**
- `q` (str), optional - Search query (e.g., 'gmail', 'music', 'notes')

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "gmail",
      "name": "Gmail",
      "category": "email",
      "stars": 420
    },
    {
      "id": "outlook",
      "name": "Outlook",
      "category": "email",
      "stars": 180
    }
  ]
}
```

### `GET /api/extensions/catalog/{extension_id}`

**Category:** Extensions & Tools

**Summary:** Get Catalog Entry

Get detailed information about a single extension from the catalog.

**Tags:** extensions, catalog, read

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "gmail",
    "name": "Gmail",
    "description": "Read, send, and manage Gmail messages",
    "author": "ergut",
    "category": "email",
    "stars": 420,
    "package_name": "@ergut/gmail-mcp-server",
    "package_type": "npm",
    "transport": "stdio"
  }
}
```

### `GET /api/extensions/categories`

**Category:** Extensions & Tools

**Summary:** List Categories

List all 12 extension categories with IDs, names, and icons.

**Tags:** extensions, categories, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "email",
      "name": "Email",
      "icon": "✉️"
    },
    {
      "id": "calendar",
      "name": "Calendar",
      "icon": "📅"
    },
    {
      "id": "notes",
      "name": "Notes & Docs",
      "icon": "📝"
    },
    {
      "id": "music",
      "name": "Music",
      "icon": "🎵"
    }
  ]
}
```

### `GET /api/extensions/{extension_id}`

**Category:** Extensions & Tools

**Summary:** Get Installed Extension

Get detailed info about a single installed extension including catalog metadata, runtime status, and install metadata.

**Tags:** extensions, installed, read

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "gmail",
    "name": "Gmail",
    "status": "running",
    "install_state": "installed",
    "artifact_path": "/Users/alice/Library/Application Support/ClawPad/mcp/artifacts/gmail/npm",
    "enabled": true,
    "tool_count": 5,
    "catalog": {
      "description": "Read, send, and manage Gmail messages",
      "author": "ergut",
      "stars": 420
    }
  }
}
```

### `GET /api/tools`

**Category:** Extensions & Tools

**Summary:** List All Tools

List all available tools from running MCP extensions. Each tool includes its name, description, and JSON Schema for input parameters. This is the discovery endpoint for the ClawPad platform API.

**Tags:** tools, discovery, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "name": "mcp_gmail_send_email",
      "description": "Send an email via Gmail",
      "extension_id": "gmail",
      "input_schema": {
        "type": "object",
        "properties": {
          "to": {
            "type": "string"
          },
          "subject": {
            "type": "string"
          },
          "body": {
            "type": "string"
          }
        },
        "required": [
          "to",
          "subject",
          "body"
        ]
      }
    },
    {
      "name": "mcp_filesystem_read_file",
      "description": "Read a file from disk",
      "extension_id": "filesystem",
      "input_schema": {
        "type": "object",
        "properties": {
          "path": {
            "type": "string"
          }
        },
        "required": [
          "path"
        ]
      }
    }
  ]
}
```

### `GET /api/tools/{tool_name}/schema`

**Category:** Extensions & Tools

**Summary:** Get Tool Schema

Get the JSON Schema for a specific tool's input parameters. Use this to programmatically build UI forms or validate input before calling the tool.

**Tags:** tools, schema, read

**Path params:**
- `tool_name`

**Response example:**
```json
{
  "success": true,
  "data": {
    "name": "mcp_gmail_send_email",
    "description": "Send an email via Gmail",
    "input_schema": {
      "type": "object",
      "properties": {
        "to": {
          "type": "string",
          "description": "Recipient email"
        },
        "subject": {
          "type": "string"
        },
        "body": {
          "type": "string"
        }
      },
      "required": [
        "to",
        "subject",
        "body"
      ]
    }
  }
}
```

### `POST /api/extensions/{extension_id}/enable`

**Category:** Extensions & Tools

**Summary:** Enable/Disable Extension

Enable or disable an extension. Disabled extensions won't auto-start on launch. If required config is missing or runtime is not installed, enabled will remain false.

**Tags:** extensions, config, write

**Request model:** `SetEnabledRequest`

**Path params:**
- `extension_id`

**Request example:**
```json
{
  "enabled": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "extension_id": "gmail",
    "requested_enabled": true,
    "enabled": false,
    "status": "error",
    "error_message": "Missing required configuration: GMAIL_OAUTH_TOKEN"
  }
}
```

**System effects:**
- Updates enabled flag
- Emits extension.status_changed event

### `POST /api/extensions/{extension_id}/env`

**Category:** Extensions & Tools

**Summary:** Set Environment Variable

Set an environment variable for an extension (e.g., API key, OAuth token). Secrets are stored encrypted. The extension may need to be restarted for changes to take effect.

**Tags:** extensions, config, write

**Request model:** `SetEnvVarRequest`

**Path params:**
- `extension_id`

**Request example:**
```json
{
  "name": "GMAIL_OAUTH_TOKEN",
  "value": "ya29.a0ARrdaM...",
  "is_secret": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "set": true
  }
}
```

**System effects:**
- Stores environment variable (encrypted if secret)

### `POST /api/extensions/{extension_id}/install`

**Category:** Extensions & Tools

**Summary:** Install Extension

Install an extension from the catalog by internalizing runtime artifacts into ClawPad-managed storage. Does not start it automatically — use the start endpoint to activate.

**Tags:** extensions, write

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "installed": true,
    "extension_id": "gmail",
    "install_state": "installed",
    "artifact_path": "/Users/alice/Library/Application Support/ClawPad/mcp/artifacts/gmail/npm",
    "install_error": ""
  }
}
```

**System effects:**
- Internalizes MCP runtime artifacts
- Emits extension.installed WebSocket event

### `POST /api/extensions/{extension_id}/start`

**Category:** Extensions & Tools

**Summary:** Start Extension

Start an installed extension's MCP server. Once started, the extension's tools become available to the AI agent and via the /api/tools endpoints.

**Tags:** extensions, write

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "started": true,
    "extension_id": "gmail",
    "tool_count": 5
  }
}
```

**System effects:**
- Starts MCP server process
- Registers tools
- Emits extension.started event

### `POST /api/extensions/{extension_id}/stop`

**Category:** Extensions & Tools

**Summary:** Stop Extension

Stop a running extension's MCP server. Its tools become unavailable.

**Tags:** extensions, write

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "stopped": true,
    "extension_id": "gmail"
  }
}
```

**System effects:**
- Stops MCP server process
- Unregisters tools
- Emits extension.stopped event

### `POST /api/tools/{tool_name}/call`

**Category:** Extensions & Tools

**Summary:** Execute Tool

Execute an MCP extension tool with the given arguments. This is the core platform endpoint — any external application can call Gmail, Spotify, GitHub, Notion, etc. tools through this single endpoint. Returns the tool's result or error.

**Tags:** tools, execute, write, platform

**Request model:** `ExecuteToolRequest`

**Path params:**
- `tool_name`

**Request example:**
```json
{
  "arguments": {
    "to": "alice@example.com",
    "subject": "Meeting Tomorrow",
    "body": "Hi Alice, confirming our meeting at 2pm."
  }
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "result": {
      "message_id": "18e2f3a4b5c",
      "thread_id": "18e2f3a4b5c"
    },
    "tool_name": "mcp_gmail_send_email",
    "duration_ms": 1250
  }
}
```

**System effects:**
- Executes MCP tool
- Side effects depend on tool
- Emits tool.executed event

### `DELETE /api/extensions/{extension_id}`

**Category:** Extensions & Tools

**Summary:** Uninstall Extension

Uninstall an extension. Stops the MCP server if running and removes it.

**Tags:** extensions, write, destructive

**Path params:**
- `extension_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "uninstalled": true,
    "extension_id": "gmail"
  }
}
```

**System effects:**
- Stops MCP server if running
- Removes extension
- Emits extension.removed event

## Files & Artifacts

### `GET /api/projects/{project_id}/files`

**Category:** Files & Artifacts

**Summary:** List Files

List all files attached to a project. Files have direction (input = user-provided, output = AI-generated) and full lineage tracking (source_message_id, source_file_ids) for traceability.

**Tags:** files, read

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "file_abc",
      "name": "analysis.py",
      "direction": "input",
      "file_type": "code",
      "language": "python",
      "size_bytes": 2048,
      "token_count": 512,
      "starred": true,
      "content_preview": "import pandas as pd\n..."
    }
  ]
}
```

### `GET /api/projects/{project_id}/files/stats`

**Category:** Files & Artifacts

**Summary:** File Statistics

Get file statistics grouped by type (documents, code, images, etc.).

**Tags:** files, read

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "code": 5,
    "document": 3,
    "image": 2,
    "data": 1
  }
}
```

### `GET /api/projects/{project_id}/files/{file_id}`

**Category:** Files & Artifacts

**Summary:** Get File

Get a single file with full metadata and content preview.

**Tags:** files, read

**Path params:**
- `project_id`
- `file_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "file_abc",
    "name": "analysis.py",
    "content_text": "import pandas as pd\n...",
    "source_message_id": "msg_asst1",
    "version_count": 3
  }
}
```

### `POST /api/projects/{project_id}/files`

**Category:** Files & Artifacts

**Summary:** Add File

Add a file to a project. Provide content_text for inline content or file_path for disk references. Direction can be 'input' (user-provided) or 'output' (AI-generated).

**Tags:** files, write

**Request model:** `AddFileRequest`

**Path params:**
- `project_id`

**Request example:**
```json
{
  "name": "data.csv",
  "content_text": "name,value\nfoo,42\nbar,99",
  "direction": "input"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "file_new1",
    "name": "data.csv",
    "direction": "input",
    "size_bytes": 35,
    "token_count": 15
  }
}
```

### `POST /api/projects/{project_id}/files/{file_id}/star`

**Category:** Files & Artifacts

**Summary:** Toggle Star

Toggle the starred state. Starred files are prioritized in context injection.

**Tags:** files, write

**Path params:**
- `project_id`
- `file_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "file_abc",
    "starred": true
  }
}
```

### `DELETE /api/projects/{project_id}/files/{file_id}`

**Category:** Files & Artifacts

**Summary:** Delete File

Delete a file from the project.

**Tags:** files, write

**Path params:**
- `project_id`
- `file_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "deleted": true
  }
}
```

## Gateway & Connection

### `GET /api/auth/clients`

**Category:** Gateway & Connection

**Summary:** List Enrolled API Clients

List enrolled API clients and their scopes/status. Requires admin scope.

**Tags:** security, auth, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "client_id": "cpc_a1b2c3d4e5f60708",
      "display_name": "Automation Laptop",
      "fingerprint_id": "cpid_17c3f6e4c0457ad0f8a4c930",
      "scopes": [
        "read",
        "write"
      ],
      "status": "active"
    }
  ]
}
```

### `GET /api/auth/enroll/status`

**Category:** Gateway & Connection

**Summary:** Get Enrollment Status

Get current one-time enrollment status including whether a pending code exists and when it expires.

**Tags:** security, auth, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "active": true,
    "has_pending_code": true,
    "expires_at": "2026-02-20T05:12:03.000000+00:00",
    "requested_by": "Desktop Owner"
  }
}
```

### `GET /api/auth/providers`

**Category:** Gateway & Connection

**Summary:** List Provider Auth Status

List encrypted API-key status for all supported providers. Returns only masked key previews and key type metadata.

**Tags:** security, auth, read, admin

**Response example:**
```json
{
  "success": true,
  "data": {
    "active_provider": "anthropic",
    "providers": [
      {
        "provider": "anthropic",
        "has_api_key": true,
        "key_type": "oauth_token",
        "masked_api_key": "sk-ant...Z9x2",
        "active_provider": true
      },
      {
        "provider": "openai",
        "has_api_key": false,
        "key_type": "none",
        "masked_api_key": "",
        "active_provider": false
      }
    ]
  }
}
```

### `GET /api/auth/providers/{provider}`

**Category:** Gateway & Connection

**Summary:** Get Provider Auth Status

Get masked API-key status for one provider.

**Tags:** security, auth, read, admin

**Path params:**
- `provider`

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "anthropic",
    "has_api_key": true,
    "key_type": "oauth_token",
    "masked_api_key": "sk-ant...Z9x2",
    "active_provider": true
  }
}
```

### `GET /api/direct/client/status`

**Category:** Gateway & Connection

**Summary:** Direct Client Status

Get direct client mode configuration and live direct-session status.

**Tags:** direct, client, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "enabled": true,
    "running": true,
    "connected": true,
    "server_host": "203.0.113.10",
    "server_port": 18888,
    "device_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "session_id": "A4fT2mP1x...",
    "server_device_id": "cpid_0123456789abcdef012345",
    "sas": "913742",
    "server_fingerprint": "sha256:8f3bdc2e...",
    "last_error": "",
    "latest_server_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0"
  }
}
```

### `GET /api/direct/identity`

**Category:** Gateway & Connection

**Summary:** Direct Fingerprint Identity

Get this ClawPad instance fingerprint ID used for direct trust allowlists and pairing policies.

**Tags:** direct, identity, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "fingerprint_id": "cpid_0123456789abcdef012345"
  }
}
```

### `GET /api/direct/server/status`

**Category:** Gateway & Connection

**Summary:** Direct Server Status

Get direct server mode state, trust policy (allowed client fingerprints), certificate fingerprint, and active direct sessions.

**Tags:** direct, server, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "enabled": true,
    "running": true,
    "connected": true,
    "connected_clients": 1,
    "sessions": [
      {
        "session_id": "A4fT2mP1x...",
        "client_ip": "203.0.113.44",
        "client_device_id": "cpid_17c3f6e4c0457ad0f8a4c930",
        "connected_at": "2026-02-19T11:08:21.100200",
        "last_activity": "2026-02-19T11:08:29.991200"
      }
    ],
    "server_name": "M4 Mini ClawPad",
    "listen_host": "0.0.0.0",
    "listen_port": 18888,
    "advertised_host": "10.0.0.24",
    "allowed_client_fingerprints": [
      "cpid_17c3f6e4c0457ad0f8a4c930"
    ],
    "cert_fingerprint": "sha256:8f3bdc2e...",
    "pairing_expires_at": "2026-02-19T11:12:13.123456",
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
    "device_id": "cpid_0123456789abcdef012345"
  }
}
```

### `GET /api/direct/status`

**Category:** Gateway & Connection

**Summary:** Direct Link Status

Get combined direct server and direct client status in one payload.

**Tags:** direct, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "server": {
      "enabled": true,
      "running": true,
      "connected": true,
      "connected_clients": 1,
      "listen_host": "0.0.0.0",
      "listen_port": 18888,
      "cert_fingerprint": "sha256:8f3bdc2e..."
    },
    "client": {
      "enabled": false,
      "running": false,
      "connected": false
    }
  }
}
```

### `GET /api/gateway/status`

**Category:** Gateway & Connection

**Summary:** Gateway Status

Check if the OpenClaw gateway is running. The gateway provides the WebSocket bridge between ClawPad and AI providers.

**Tags:** gateway, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "running": true,
    "pid": 12345
  }
}
```

### `GET /api/remote/client/execution-mode`

**Category:** Gateway & Connection

**Summary:** Get Client Execution Mode

Get how this client executes chat turns: locally (`self`) or via remote server (`remote_direct`).

**Tags:** remote, client, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "mode": "remote_direct",
    "direct_connected": true
  }
}
```

### `GET /api/remote/client/status`

**Category:** Gateway & Connection

**Summary:** Remote Client Status

Get remote client mode state and current websocket connection status.

**Tags:** remote, client, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "enabled": true,
    "connected": true,
    "authenticated": true,
    "device_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "fingerprint_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "server_fingerprint": "sha256:8f3bdc2e...",
    "execution_mode": "self",
    "latest_server_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
    "transport_ready": {
      "direct": true
    },
    "transport": "direct"
  }
}
```

### `GET /api/remote/server/status`

**Category:** Gateway & Connection

**Summary:** Remote Server Status

Get remote server status and active direct sessions.

**Tags:** remote, server, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "enabled": true,
    "running": true,
    "connected": false,
    "server_name": "My ClawPad Direct",
    "listen_host": "0.0.0.0",
    "listen_port": 18888,
    "fingerprint_id": "cpid_0123456789abcdef012345",
    "advertised_host": "10.0.0.24",
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
    "active_sessions": 0,
    "transport": "direct"
  }
}
```

### `POST /api/auth/clients/revoke-all`

**Category:** Gateway & Connection

**Summary:** Revoke All API Clients

Revoke all active enrolled API clients and invalidate their tokens. Optionally keep one client ID active.

**Tags:** security, auth, write

**Request model:** `APIAuthRevokeAllClientsRequest`

**Request example:**
```json
{
  "reason": "Security reset",
  "keep_client_id": ""
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "revoked_all": true,
    "revoked_count": 3,
    "kept_client_id": "cpc_a1b2c3d4e5f60708"
  }
}
```

**System effects:**
- Revokes all selected clients and their tokens

### `POST /api/auth/clients/{client_id}/revoke`

**Category:** Gateway & Connection

**Summary:** Revoke API Client

Revoke one enrolled API client and invalidate all its tokens. Requires admin scope.

**Tags:** security, auth, write

**Request model:** `APIAuthRevokeClientRequest`

**Path params:**
- `client_id`

**Request example:**
```json
{
  "reason": "Lost device"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "revoked": true,
    "client_id": "cpc_a1b2c3d4e5f60708"
  }
}
```

**System effects:**
- Immediately invalidates all tokens for the client

### `POST /api/auth/enroll`

**Category:** Gateway & Connection

**Summary:** Enroll API Client

Enroll a client public key using one-time enrollment code and signed proof-of-possession, then issue access/refresh tokens.

**Tags:** security, auth, write

**Request model:** `APIAuthEnrollRequest`

**Request example:**
```json
{
  "display_name": "Automation Laptop",
  "fingerprint_id": "cpid_17c3f6e4c0457ad0f8a4c930",
  "public_key": "base64-ed25519-public-key",
  "enrollment_code": "48291730",
  "signature": "base64-signature",
  "scopes": [
    "read",
    "write"
  ]
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "client_id": "cpc_a1b2c3d4e5f60708",
    "access_token": "opaque-token",
    "refresh_token": "opaque-token"
  }
}
```

**System effects:**
- Registers trusted client and issues tokens

### `POST /api/auth/enroll/cancel`

**Category:** Gateway & Connection

**Summary:** Cancel Enrollment Code

Cancel and invalidate the active enrollment code immediately.

**Tags:** security, auth, write

**Request model:** `APIAuthEnrollmentCancelRequest`

**Request example:**
```json
{
  "reason": "Abort onboarding window"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "cancelled": true,
    "had_pending_code": true
  }
}
```

**System effects:**
- Invalidates pending enrollment code

### `POST /api/auth/enroll/start`

**Category:** Gateway & Connection

**Summary:** Start API Enrollment

Generate one-time local enrollment code for a new API client keypair. This endpoint is restricted to localhost requests.

**Tags:** security, auth, write

**Request model:** `APIAuthEnrollStartRequest`

**Request example:**
```json
{
  "requested_by": "Desktop Owner"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "enrollment_code": "48291730",
    "expires_at": "2026-02-19T14:05:23.000000+00:00",
    "ttl_seconds": 300
  }
}
```

**System effects:**
- Rotates active enrollment code (single-use)

### `POST /api/auth/providers/anthropic/sign-in`

**Category:** Gateway & Connection

**Summary:** Sign In Anthropic Provider

Sign in Anthropic either by storing a provided OAuth access token or by importing Claude keychain credentials.

**Tags:** security, auth, write, admin

**Request model:** `APIAnthropicSignInRequest`

**Request example:**
```json
{
  "access_token": "sk-ant-oat01-...",
  "refresh_token": "",
  "expires_in_seconds": 31536000,
  "set_as_active_provider": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "anthropic",
    "has_api_key": true,
    "key_type": "oauth_token",
    "masked_api_key": "sk-ant...Z9x2",
    "active_provider": true,
    "signed_in": true,
    "source": "manual_token"
  }
}
```

**System effects:**
- Stores Anthropic token auth and optionally switches active provider to anthropic

### `POST /api/auth/providers/{provider}/api-key/reset`

**Category:** Gateway & Connection

**Summary:** Reset Provider API Key

Explicit reset endpoint for one provider API key. Equivalent to clear, but with reset semantics for automation flows.

**Tags:** security, auth, write, admin

**Path params:**
- `provider`

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "grok",
    "has_api_key": false,
    "key_type": "none",
    "masked_api_key": "",
    "active_provider": false,
    "cleared": true,
    "reset": true,
    "removed_profile_ids": [
      "grok:clawpad"
    ]
  }
}
```

**System effects:**
- Resets encrypted provider credential and related auth profile API keys

### `POST /api/auth/providers/{provider}/token/reset`

**Category:** Gateway & Connection

**Summary:** Reset Provider Auth Token

Reset provider token-based auth state. Currently supported for Anthropic (Claude OAuth token/keychain).

**Tags:** security, auth, write, admin

**Request model:** `APIProviderTokenResetRequest`

**Path params:**
- `provider`

**Request example:**
```json
{
  "clear_keychain": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "anthropic",
    "has_api_key": false,
    "key_type": "none",
    "masked_api_key": "",
    "token_reset": true,
    "removed_profile_ids": [
      "anthropic:manual"
    ],
    "keychain": {
      "deleted_count": 1,
      "failed_count": 0
    }
  }
}
```

**System effects:**
- Removes token auth profiles and optionally clears local Claude keychain entries

### `POST /api/auth/token`

**Category:** Gateway & Connection

**Summary:** Refresh Access Token

Issue a new short-lived access token using refresh token and signed client proof.

**Tags:** security, auth, write

**Request model:** `APIAuthTokenRequest`

**Request example:**
```json
{
  "client_id": "cpc_a1b2c3d4e5f60708",
  "refresh_token": "opaque-token",
  "timestamp": 1771509801,
  "nonce": "m9f3AS2lk",
  "signature": "base64-signature"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "client_id": "cpc_a1b2c3d4e5f60708",
    "access_token": "opaque-token",
    "ttl_seconds": 900
  }
}
```

### `POST /api/direct/client/connect`

**Category:** Gateway & Connection

**Summary:** Connect Direct Client

Connect this ClawPad instance directly to another ClawPad server using pairing codes and optional expected server certificate fingerprint pinning. Prefer connection_ticket to avoid manual host/IP entry.

**Tags:** direct, client, security, write

**Request model:** `DirectClientConnectRequest`

**Request example:**
```json
{
  "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
  "device_info": "MS-1",
  "timeout_seconds": 12.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "connected": true,
    "server_host": "203.0.113.10",
    "server_port": 18888,
    "device_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "server_device_id": "cpid_0123456789abcdef012345",
    "session_id": "A4fT2mP1x...",
    "sas": "913742",
    "server_fingerprint": "sha256:8f3bdc2e...",
    "ticket_server_name": "M4 Mini ClawPad"
  }
}
```

**System effects:**
- Starts direct TLS client session
- Pins server fingerprint after successful handshake

### `POST /api/direct/client/disconnect`

**Category:** Gateway & Connection

**Summary:** Disconnect Direct Client

Disconnect this ClawPad direct client from the remote direct server.

**Tags:** direct, client, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "disconnected": true
  }
}
```

**System effects:**
- Stops direct TLS client session

### `POST /api/direct/client/rpc`

**Category:** Gateway & Connection

**Summary:** Direct Client RPC

Invoke one server-side RPC action over direct secure link transport.

**Tags:** direct, client, rpc, write

**Request model:** `DirectClientRPCRequest`

**Request example:**
```json
{
  "action": "send_message",
  "params": {
    "project_id": "project-123",
    "content": "Test from direct client",
    "wait_for_response": true
  },
  "timeout_seconds": 120.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "msg-456",
    "role": "assistant",
    "content": "Direct secure RPC response."
  }
}
```

**System effects:**
- Routes RPC over direct secure websocket session to remote server

### `POST /api/direct/server/rotate-codes`

**Category:** Gateway & Connection

**Summary:** Rotate Direct Pairing Codes

Rotate direct pairing codes and pairing expiry window without restarting server listener.

**Tags:** direct, server, security, write

**Request model:** `DirectServerRotateCodesRequest`

**Request example:**
```json
{
  "server_code": "809133",
  "expected_client_code": "004911",
  "pairing_ttl_seconds": 300
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "rotated": true,
    "pairing_expires_at": "2026-02-19T11:25:42.217810",
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
    "broadcast_clients": 1
  }
}
```

**System effects:**
- Invalidates previous pairing codes for new handshakes

### `POST /api/direct/server/start`

**Category:** Gateway & Connection

**Summary:** Start Direct Server

Start direct ClawPad-to-ClawPad TLS server mode. Server trusts clients by ClawPad fingerprint ID (not client IP).

**Tags:** direct, server, security, write

**Request model:** `DirectServerStartRequest`

**Request example:**
```json
{
  "listen_host": "0.0.0.0",
  "listen_port": 18888,
  "server_name": "M4 Mini ClawPad",
  "allowed_client_fingerprints": [
    "cpid_17c3f6e4c0457ad0f8a4c930"
  ],
  "server_code": "728194",
  "expected_client_code": "519302",
  "pairing_ttl_seconds": 300
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "started": true,
    "device_id": "cpid_0123456789abcdef012345",
    "server_name": "M4 Mini ClawPad",
    "listen_host": "0.0.0.0",
    "listen_port": 18888,
    "advertised_host": "10.0.0.24",
    "direct_url": "wss://203.0.113.10:18888/direct/cpid_0123456789abcdef012345",
    "cert_fingerprint": "sha256:8f3bdc2e...",
    "pairing_expires_at": "2026-02-19T11:12:13.123456",
    "allowed_client_fingerprints": [
      "cpid_17c3f6e4c0457ad0f8a4c930"
    ],
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0"
  }
}
```

**System effects:**
- Starts direct TLS websocket listener
- Persists direct server pairing configuration

### `POST /api/direct/server/stop`

**Category:** Gateway & Connection

**Summary:** Stop Direct Server

Stop direct TLS server mode on this ClawPad instance.

**Tags:** direct, server, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "stopped": true
  }
}
```

**System effects:**
- Stops direct TLS websocket listener

### `POST /api/gateway/reconnect`

**Category:** Gateway & Connection

**Summary:** Reconnect Gateway

Reconnect the WebSocket connection to the gateway.

**Tags:** gateway, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "reconnecting": true
  }
}
```

**System effects:**
- Re-establishes WebSocket connection

### `POST /api/gateway/restart`

**Category:** Gateway & Connection

**Summary:** Restart Gateway

Restart the OpenClaw gateway process.

**Tags:** gateway, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "restarted": true
  }
}
```

**System effects:**
- Restarts OpenClaw gateway process

### `POST /api/remote/client/connect`

**Category:** Gateway & Connection

**Summary:** Connect Remote Client

Connect this ClawPad instance as a direct remote client to another ClawPad server. Prefer using connection_ticket so users do not need to type host/IP manually.

**Tags:** remote, client, security, write

**Request model:** `DirectClientConnectRequest`

**Request example:**
```json
{
  "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
  "device_info": "Travel Laptop",
  "timeout_seconds": 12.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "connected": true,
    "device_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "fingerprint_id": "cpid_17c3f6e4c0457ad0f8a4c930",
    "server_device_id": "cpid_0123456789abcdef012345",
    "session_id": "AbCdEfGh",
    "sas": "482915",
    "server_fingerprint": "sha256:8f3bdc2e...",
    "ticket_server_name": "M4 Mini ClawPad"
  }
}
```

**System effects:**
- Enables direct remote client mode

### `POST /api/remote/client/disconnect`

**Category:** Gateway & Connection

**Summary:** Disconnect Remote Client

Disconnect this ClawPad remote client from the current remote server.

**Tags:** remote, client, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "disconnected": true
  }
}
```

**System effects:**
- Stops direct client connection

### `POST /api/remote/client/rpc`

**Category:** Gateway & Connection

**Summary:** Remote Client RPC

Invoke one allowed server-side RPC action through an established remote direct client connection. Useful for remote execution from client instance without exposing raw server API port. Allowed actions include project/message operations plus provider auth/settings operations such as set_provider_api_key.

**Tags:** remote, client, rpc, write

**Request model:** `RemoteClientRPCRequest`

**Request example:**
```json
{
  "action": "send_message",
  "params": {
    "project_id": "project-123",
    "content": "Summarize today",
    "wait_for_response": true,
    "timeout": 90.0
  },
  "timeout_seconds": 120.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "msg-456",
    "role": "assistant",
    "content": "Summary generated remotely."
  }
}
```

**System effects:**
- Routes client RPC over direct transport and returns response

### `POST /api/remote/client/send-message`

**Category:** Gateway & Connection

**Summary:** Send Message (Client Mode)

Send one user message using the current client execution mode. In `self` mode it runs locally; in remote modes it executes on the connected server engine/resources.

**Tags:** remote, client, write

**Request model:** `RemoteClientSendMessageRequest`

**Request example:**
```json
{
  "project_id": "project-123",
  "content": "Summarize this thread",
  "attachments": [],
  "timeout_seconds": 120.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "msg-456",
    "role": "assistant",
    "content": "Summary generated remotely.",
    "_execution_mode": "remote_direct",
    "_transport": "direct"
  }
}
```

**System effects:**
- Runs one chat turn according to configured client execution mode

### `POST /api/remote/server/disable`

**Category:** Gateway & Connection

**Summary:** Disable Remote Server

Disable direct remote server mode.

**Tags:** remote, server, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "disabled": true,
    "transport": "direct"
  }
}
```

**System effects:**
- Stops direct server listener

### `POST /api/remote/server/rotate-codes`

**Category:** Gateway & Connection

**Summary:** Rotate Remote Server Codes

Rotate direct remote server pairing codes and refresh pairing expiry.

**Tags:** remote, server, security, write

**Request model:** `DirectServerRotateCodesRequest`

**Request example:**
```json
{
  "server_code": "728194",
  "expected_client_code": "519302",
  "pairing_ttl_seconds": 300
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "rotated": true,
    "pairing_expires_at": "2026-02-19T11:12:13.123456",
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0",
    "broadcast_clients": 1
  }
}
```

**System effects:**
- Updates direct pairing credentials

### `POST /api/remote/server/start`

**Category:** Gateway & Connection

**Summary:** Start Remote Server

Start direct TLS remote server mode on this ClawPad instance.

**Tags:** remote, server, security, write

**Request model:** `DirectServerStartRequest`

**Request example:**
```json
{
  "listen_host": "0.0.0.0",
  "listen_port": 18888,
  "server_name": "M4 Mini ClawPad",
  "allowed_client_fingerprints": [
    "cpid_17c3f6e4c0457ad0f8a4c930"
  ],
  "server_code": "728194",
  "expected_client_code": "519302",
  "pairing_ttl_seconds": 300
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "started": true,
    "device_id": "cpid_0123456789abcdef012345",
    "fingerprint_id": "cpid_0123456789abcdef012345",
    "server_name": "M4 Mini ClawPad",
    "listen_host": "0.0.0.0",
    "listen_port": 18888,
    "advertised_host": "10.0.0.24",
    "direct_url": "wss://203.0.113.10:18888/direct/cpid_0123456789abcdef012345",
    "cert_fingerprint": "sha256:8f3bdc2e...",
    "pairing_expires_at": "2026-02-19T11:12:13.123456",
    "connection_ticket": "cpdirect1:eyJ0eXBlIjoiY2xhd3BhZF9kaXJlY3RfdGlja2V0X3YxIiwiLi4uIn0"
  }
}
```

**System effects:**
- Starts direct TLS websocket listener

### `PUT /api/auth/providers/{provider}/api-key`

**Category:** Gateway & Connection

**Summary:** Set Provider API Key

Set or rotate encrypted API key for one provider. Optionally switch active provider in the same request.

**Tags:** security, auth, write, admin

**Request model:** `APIProviderKeySetRequest`

**Path params:**
- `provider`

**Request example:**
```json
{
  "api_key": "sk-ant-api03-xxx",
  "set_as_active_provider": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "anthropic",
    "has_api_key": true,
    "key_type": "api_key",
    "masked_api_key": "sk-ant...-xxx",
    "active_provider": true,
    "updated": true,
    "set_as_active_provider": true
  }
}
```

**System effects:**
- Stores encrypted provider credential

### `PUT /api/remote/client/execution-mode`

**Category:** Gateway & Connection

**Summary:** Set Client Execution Mode

Set client chat execution mode (`self` or `remote_direct`).

**Tags:** remote, client, write

**Request model:** `RemoteClientExecutionModeRequest`

**Request example:**
```json
{
  "mode": "remote_direct"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "mode": "remote_direct",
    "direct_connected": true
  }
}
```

**System effects:**
- Changes chat execution routing for this ClawPad client instance

### `DELETE /api/auth/providers/{provider}/api-key`

**Category:** Gateway & Connection

**Summary:** Clear Provider API Key

Delete stored encrypted API key for one provider.

**Tags:** security, auth, write, admin

**Path params:**
- `provider`

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "openai",
    "has_api_key": false,
    "key_type": "none",
    "masked_api_key": "",
    "active_provider": false,
    "cleared": true
  }
}
```

**System effects:**
- Removes encrypted provider credential

## Health & Status

### `GET /api/public/identity`

**Category:** Health & Status

**Summary:** Public API Identity

Get public ClawPad API identity information used for secure client enrollment and signed request verification.

**Tags:** security, identity, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "fingerprint_id": "cpid_0123456789abcdef012345",
    "public_key": "base64-ed25519-public-key",
    "public_key_id": "5fb2f2a1b83dc8f0",
    "signature_scheme": "ed25519-v1",
    "auth_required": true
  }
}
```

### `GET /api/state`

**Category:** Health & Status

**Summary:** Get App State

Get the full application state including project count, current settings (provider, model, theme, context injection config), and gateway connection status. Ideal for building dashboards.

**Tags:** state, monitoring

**Response example:**
```json
{
  "success": true,
  "data": {
    "app_name": "ClawPad",
    "app_version": "0.4.0",
    "project_count": 9,
    "settings": {
      "provider": "anthropic",
      "model": "claude-sonnet-4-20250514",
      "theme": "starry_night",
      "context_injection_enabled": true,
      "context_injection_mode": "auto"
    },
    "gateway": {
      "running": true
    }
  }
}
```

### `GET /api/version`

**Category:** Health & Status

**Summary:** Get Version

Returns ClawPad application name and version.

**Tags:** health, version

**Response example:**
```json
{
  "success": true,
  "data": {
    "name": "ClawPad",
    "version": "0.4.0"
  }
}
```

### `GET /health`

**Category:** Health & Status

**Summary:** Health Check

Check if the ClawPad API server is running and responsive. Returns current timestamp. Use this for monitoring and connectivity checks before making other API calls.

**Tags:** health, monitoring

**Response example:**
```json
{
  "success": true,
  "data": {
    "status": "healthy",
    "timestamp": 1770531460.01
  },
  "timestamp": "2026-02-08T06:17:40.012Z"
}
```

**System effects:**
- None — read-only

### `POST /api/app/quit`

**Category:** Health & Status

**Summary:** Quit Application

Gracefully shut down ClawPad. Stops the gateway, saves state, and exits.

**Tags:** lifecycle, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "quitting": true
  }
}
```

**System effects:**
- Application will exit

## Messages & AI

### `GET /api/projects/{project_id}/messages`

**Category:** Messages & AI

**Summary:** List Messages

Get messages for a project with pagination. Each message includes the role (user/assistant/system), full content, streaming state, and timestamp. AI responses contain the actual model output with ClawPad's context injection (global memory + topic context + file references).

**Tags:** messages, ai, read

**Path params:**
- `project_id`

**Query params:**
- `limit` (int), optional, default=100 - Max messages (1-10000)
- `offset` (int), optional, default=0 - Skip first N messages

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "msg_user1",
      "project_id": "proj_abc123",
      "role": "user",
      "content": "Review this Python function for type safety",
      "timestamp": "2026-02-08T10:30:00",
      "is_streaming": false,
      "attachments": []
    },
    {
      "id": "msg_asst1",
      "project_id": "proj_abc123",
      "role": "assistant",
      "content": "I'll analyze the function for type safety issues...",
      "timestamp": "2026-02-08T10:30:05",
      "is_streaming": false,
      "run_id": "run_xyz"
    }
  ]
}
```

### `GET /api/projects/{project_id}/messages/{message_id}`

**Category:** Messages & AI

**Summary:** Get Message

Get a single message by ID with full content and metadata.

**Tags:** messages, read

**Path params:**
- `project_id`
- `message_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "msg_asst1",
    "role": "assistant",
    "content": "Here's my analysis of the code...",
    "is_streaming": false,
    "run_id": "run_xyz"
  }
}
```

### `POST /api/projects/{project_id}/export`

**Category:** Messages & AI

**Summary:** Export Chat

Export the entire conversation as Markdown. Includes all user and assistant messages with timestamps. Ideal for archiving, sharing, or feeding into other AI workflows.

**Tags:** messages, export, read

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "markdown": "# Code Review Helper\n\n**User** (2026-02-08T10:30:00):\nReview this...\n\n**Assistant** (2026-02-08T10:30:05):\nI'll analyze..."
  }
}
```

### `POST /api/projects/{project_id}/messages`

**Category:** Messages & AI

**Summary:** Send Message

Send a message in a project, optionally triggering an AI response. ClawPad automatically injects topic context (conversation summary, recent history, file references) before sending to the AI model.

Set wait_for_response=true to block until the AI completes its response (useful for automation and testing). The response includes the full AI-generated content with context injection applied.

**Tags:** messages, ai, write, context-injection

**Request model:** `SendMessageRequest`

**Path params:**
- `project_id`

**Request example:**
```json
{
  "content": "Explain the context injection system",
  "wait_for_response": false,
  "timeout": 120.0
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "msg_new1",
    "role": "user",
    "content": "Explain the context injection system",
    "timestamp": "2026-02-08T10:35:00",
    "is_streaming": false
  }
}
```

**System effects:**
- Creates user message in database
- Triggers AI response via chat service
- Emits message.sent WebSocket event

### `POST /api/projects/{project_id}/messages/{message_id}/regenerate`

**Category:** Messages & AI

**Summary:** Regenerate Response

Delete an assistant message and re-send the last user message to get a fresh AI response. Useful for getting alternative answers.

**Tags:** messages, ai, write

**Path params:**
- `project_id`
- `message_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "regenerated": true,
    "project_id": "proj_abc123"
  }
}
```

**System effects:**
- Deletes old response
- Triggers new AI response

### `DELETE /api/projects/{project_id}/messages`

**Category:** Messages & AI

**Summary:** Clear All Messages

Delete all messages in a project. The conversation starts fresh.

**Tags:** messages, write, destructive

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "cleared": true
  }
}
```

**System effects:**
- Deletes all messages for this project

### `DELETE /api/projects/{project_id}/messages/{message_id}`

**Category:** Messages & AI

**Summary:** Delete Message

Delete a single message from the conversation.

**Tags:** messages, write

**Path params:**
- `project_id`
- `message_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "deleted": true
  }
}
```

## Projects

### `GET /api/projects`

**Category:** Projects

**Summary:** List Projects

List all projects (topics/conversations). Each project can have its own AI model override (model_provider, model_id), an AI-generated summary, and tracked message counts. Includes archived projects.

**Tags:** projects, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "proj_abc123",
      "name": "Code Review Helper",
      "description": "AI-assisted code review workflow",
      "model_provider": "anthropic",
      "model_id": "claude-sonnet-4-20250514",
      "summary": "Discussing Python best practices and type hints",
      "message_count": 42,
      "pinned": true,
      "archived": false,
      "created_at": "2026-02-01T10:00:00"
    }
  ]
}
```

### `GET /api/projects/{project_id}`

**Category:** Projects

**Summary:** Get Project

Get a single project by ID with all metadata.

**Tags:** projects, read

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "proj_abc123",
    "name": "Code Review Helper",
    "summary": "Discussing Python best practices",
    "model_provider": "anthropic",
    "model_id": "claude-sonnet-4-20250514",
    "message_count": 42,
    "session_key": "session_xyz"
  }
}
```

### `POST /api/projects`

**Category:** Projects

**Summary:** Create Project

Create a new project (conversation topic). Optionally set a per-topic AI model override — different conversations can use different models (e.g., Claude for coding, GPT-4 for creative writing).

**Tags:** projects, write

**Request model:** `CreateProjectRequest`

**Request example:**
```json
{
  "name": "My New Project",
  "description": "AI-powered data analysis",
  "model_provider": "anthropic",
  "model_id": "claude-sonnet-4-20250514"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "proj_new123",
    "name": "My New Project",
    "description": "AI-powered data analysis",
    "model_provider": "anthropic",
    "model_id": "claude-sonnet-4-20250514",
    "message_count": 0
  }
}
```

**System effects:**
- Creates new project in database
- Emits project.created WebSocket event

### `POST /api/projects/{project_id}/pin`

**Category:** Projects

**Summary:** Toggle Pin

Toggle the pinned state of a project. Pinned projects appear at the top of the sidebar.

**Tags:** projects, write

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "proj_abc123",
    "pinned": true
  }
}
```

### `POST /api/projects/{project_id}/select`

**Category:** Projects

**Summary:** Select Project

Switch the active project in the UI. Loads conversation and updates the chat view.

**Tags:** projects, ui, write

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "selected": true
  }
}
```

**System effects:**
- Changes active project in UI

### `PUT /api/projects/{project_id}`

**Category:** Projects

**Summary:** Update Project

Partially update a project. Only non-null fields are applied. Use this to rename, change description, switch AI model, or archive.

**Tags:** projects, write

**Request model:** `UpdateProjectRequest`

**Path params:**
- `project_id`

**Request example:**
```json
{
  "name": "Renamed Project",
  "model_id": "gpt-4o"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "proj_abc123",
    "name": "Renamed Project",
    "model_id": "gpt-4o"
  }
}
```

**System effects:**
- Updates project in database
- Emits project.updated WebSocket event

### `DELETE /api/projects/{project_id}`

**Category:** Projects

**Summary:** Delete Project

Permanently delete a project and all its messages and files.

**Tags:** projects, write, destructive

**Path params:**
- `project_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "deleted": true
  }
}
```

**System effects:**
- Deletes project, messages, and files
- Emits project.deleted event

## Screenshots

### `GET /api/screenshot`

**Category:** Screenshots

**Summary:** Capture Screenshot (Transient)

Capture a screenshot of the ClawPad window and return it as a PNG image. This is a one-shot capture — the image is NOT saved to the database. Use POST /api/screenshots/capture for persistent storage.

**Tags:** screenshots, capture, read

**Response example:**
```text
<PNG binary data>
```

### `GET /api/screenshot/full`

**Category:** Screenshots

**Summary:** Capture Full-Window Screenshot

Capture a screenshot using full-screen grab + window crop, which includes popup menus and overlays that widget.grab() can miss.

**Tags:** screenshots, capture, full-window, read

**Response example:**
```text
<PNG binary data>
```

### `GET /api/screenshots`

**Category:** Screenshots

**Summary:** List Screenshots

List all saved screenshots sorted by creation time (newest first). Each entry includes metadata but NOT the image data (use the /image or /thumbnail endpoints to retrieve binary data).

**Tags:** screenshots, list, read

**Query params:**
- `limit` (int), optional, default=100 - Max results (1-1000)

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "90e861d6-3bd5-40be-8ce8-eab64379f23e",
      "width": 2092,
      "height": 1282,
      "file_size": 164073,
      "label": "initial-state",
      "source": "api",
      "view_context": "welcome",
      "created_at": "2026-02-14T06:46:18.976429+00:00"
    }
  ]
}
```

### `GET /api/screenshots/{screenshot_id}`

**Category:** Screenshots

**Summary:** Get Screenshot Metadata

Get metadata for a single screenshot by ID (without image data).

**Tags:** screenshots, metadata, read

**Path params:**
- `screenshot_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "90e861d6-3bd5-40be-8ce8-eab64379f23e",
    "width": 2092,
    "height": 1282,
    "file_size": 164073,
    "label": "initial-state",
    "source": "api",
    "view_context": "welcome",
    "created_at": "2026-02-14T06:46:18.976429+00:00"
  }
}
```

### `GET /api/screenshots/{screenshot_id}/image`

**Category:** Screenshots

**Summary:** Get Screenshot Image

Get the full-resolution PNG image for a screenshot. Returns binary PNG data with Content-Type: image/png. Typical size: 100-250KB for a 2092x1282 window.

**Tags:** screenshots, image, binary, read

**Path params:**
- `screenshot_id`

**Response example:**
```text
<PNG binary data — full resolution>
```

### `GET /api/screenshots/{screenshot_id}/thumbnail`

**Category:** Screenshots

**Summary:** Get Screenshot Thumbnail

Get the thumbnail (256px wide) for a screenshot. Returns binary PNG data. Typically 10-20KB. Use this for listings and previews.

**Tags:** screenshots, thumbnail, binary, read

**Path params:**
- `screenshot_id`

**Response example:**
```text
<PNG binary data — 256px wide thumbnail>
```

### `POST /api/screenshots/capture`

**Category:** Screenshots

**Summary:** Capture & Save Screenshot

Capture the ClawPad window and save it persistently to the database. Generates a 256px-wide thumbnail automatically. Records the current view context (welcome, chat, settings, extensions) and custom label/source metadata. Returns screenshot ID and metadata (width, height, file_size).

**Tags:** screenshots, capture, database, write

**Request model:** `CaptureScreenshotRequest`

**Request example:**
```json
{
  "label": "test-state",
  "source": "api"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "id": "90e861d6-3bd5-40be-8ce8-eab64379f23e",
    "width": 2092,
    "height": 1282,
    "file_size": 164073,
    "label": "test-state",
    "source": "api",
    "view_context": "welcome",
    "created_at": "2026-02-14T06:46:18.976429+00:00"
  }
}
```

**System effects:**
- Captures window screenshot
- Saves PNG + thumbnail to database

### `DELETE /api/screenshots/{screenshot_id}`

**Category:** Screenshots

**Summary:** Delete Screenshot

Permanently delete a screenshot and its thumbnail from the database.

**Tags:** screenshots, delete, write, destructive

**Path params:**
- `screenshot_id`

**Response example:**
```json
{
  "success": true,
  "data": {
    "deleted": true,
    "id": "90e861d6-3bd5-40be-8ce8-eab64379f23e"
  }
}
```

**System effects:**
- Removes screenshot and thumbnail from database

## Search

### `GET /api/projects/{project_id}/search/files`

**Category:** Search

**Summary:** Search Project Files

Search files within a specific project by name or content.

**Tags:** search, read

**Path params:**
- `project_id`

**Query params:**
- `q` (str), optional - Search query (required)

**Response example:**
```json
{
  "success": true,
  "data": []
}
```

### `GET /api/projects/{project_id}/search/messages`

**Category:** Search

**Summary:** Search Project Messages

Search messages within a specific project.

**Tags:** search, read

**Path params:**
- `project_id`

**Query params:**
- `q` (str), optional - Search query (required)

**Response example:**
```json
{
  "success": true,
  "data": []
}
```

### `GET /api/search/messages`

**Category:** Search

**Summary:** Global Message Search

Search across all messages in all projects. Returns matching messages with context.

**Tags:** search, read

**Query params:**
- `q` (str), optional - Search query (required)
- `limit` (int), optional, default=50 - Max results (1-500)

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "project_id": "proj_abc",
      "message_id": "msg_1",
      "content": "...matching text..."
    }
  ]
}
```

### `GET /api/search/projects`

**Category:** Search

**Summary:** Search Projects

Search projects by name or description.

**Tags:** search, read

**Query params:**
- `q` (str), optional - Search query (required)

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "id": "proj_abc",
      "name": "Code Review Helper"
    }
  ]
}
```

## Settings & Config

### `GET /api/local-model/providers/status`

**Category:** Settings & Config

**Summary:** Local Provider Chain Status

Get local provider failover-chain ordering, cooldown state, and latest probe snapshots without forcing a new network probe.

**Tags:** settings, local-model, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "primary_provider": "embedded",
    "local_fallback_chain": [
      "ollama:qwen3:4b",
      "lmstudio:qwen3-4b-instruct"
    ],
    "probe_enabled": true,
    "cooldown_seconds": 60,
    "candidates": []
  }
}
```

### `GET /api/local-model/status`

**Category:** Settings & Config

**Summary:** Local Model Status

Get local-model runtime readiness, downloaded model list, current loaded model, and hardware profile for the Local Model tab.

**Tags:** settings, local-model, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "enabled": true,
    "selected_model": "qwen3-4b-q4",
    "license_acknowledged": true,
    "runtime": {
      "installed": true,
      "message": ""
    },
    "engine": {
      "loaded": true,
      "loaded_model": "qwen3-4b-q4"
    },
    "provider_routing": {
      "primary_provider": "embedded",
      "local_fallback_chain": [
        "ollama:qwen3:4b"
      ],
      "probe_enabled": true,
      "cooldown_seconds": 60
    }
  }
}
```

### `GET /api/openclaw-gateway/status`

**Category:** Settings & Config

**Summary:** OpenClaw Gateway Status

Get status for optional external OpenClaw benchmark gateway (running, port, status string, last error).

**Tags:** settings, openclaw, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "available": true,
    "mode": "original_gateway",
    "enabled": true,
    "running": true,
    "status": "running",
    "port": 18789,
    "last_error": ""
  }
}
```

### `GET /api/openclaw/settings`

**Category:** Settings & Config

**Summary:** OpenClaw Tab Settings

Get focused OpenClaw settings used by the OpenClaw tab (mode, port, command, benchmark timeout, model override) plus live gateway status.

**Tags:** settings, openclaw, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "openclaw_mode": "embedded",
    "openclaw_gateway_enabled": false,
    "openclaw_gateway_port": 18789,
    "openclaw_gateway_command": "",
    "openclaw_gateway_benchmark_timeout": 180,
    "openclaw_gateway_model_override": "",
    "gateway_status": {
      "available": true,
      "running": false,
      "status": "stopped",
      "last_error": ""
    }
  }
}
```

### `GET /api/settings`

**Category:** Settings & Config

**Summary:** Get Settings

Get the full application settings including AI provider/model defaults, context injection configuration (enabled, mode, max_history, include_files), system prompt template, appearance, notification preferences, local-model assist settings, and OpenClaw benchmark gateway settings.

**Tags:** settings, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "anthropic",
    "model": "claude-sonnet-4-20250514",
    "theme": "starry_night",
    "local_model_enabled": true,
    "primary_local_model": "qwen3-4b-q4",
    "openclaw_mode": "embedded",
    "openclaw_gateway_enabled": false,
    "openclaw_gateway_port": 18789,
    "context_injection_enabled": true,
    "context_injection_mode": "auto",
    "context_max_history_messages": 10,
    "context_include_files": true,
    "max_context_tokens": 8000,
    "system_prompt_template": "You are a helpful AI assistant for {project_name}.",
    "zoom_level": 100,
    "sounds_enabled": true
  }
}
```

### `GET /api/usage/dashboard`

**Category:** Settings & Config

**Summary:** Usage Dashboard

Get token-efficiency analytics for Local AI Engine. Includes session/daily/weekly/monthly summaries, cloud-token avoidance, estimated baseline-vs-actual cloud cost, and per-day trend rows.

**Tags:** settings, usage, analytics, read

**Query params:**
- `days` (int), optional, default=30 - Trend window size (1-365 days).
- `project_id` (str), optional - Optional project scope.

**Response example:**
```json
{
  "success": true,
  "data": {
    "window_days": 30,
    "cloud_reference_model": "claude-opus-4-6",
    "daily": {
      "total_messages": 42,
      "free_pct": 81.0,
      "estimated_savings_usd": 0.37
    },
    "weekly": {
      "total_messages": 201,
      "free_pct": 84.6,
      "estimated_savings_usd": 2.14
    },
    "monthly": {
      "total_messages": 844,
      "free_pct": 86.3,
      "estimated_savings_usd": 9.02
    },
    "session": {
      "total_messages": 57,
      "free_pct": 80.7,
      "estimated_savings_usd": 0.61
    },
    "efficiency_layers": {
      "semantic_cache_hit_rate_pct": 21.3,
      "local_route_rate_pct": 65.0,
      "cloud_token_avoidance_pct": 86.1
    },
    "local_assist": {
      "window_days": 30,
      "events_total": 128,
      "profile_refresh_count": 22,
      "query_optimized_count": 41,
      "query_optimization_skip_count": 19,
      "query_optimization_skip_reasons": {
        "engine_busy_or_not_loaded": 11,
        "no_effect": 5,
        "invalid_json": 3
      },
      "avg_optimization_reduction_pct": 18.7,
      "proactive_seed_count": 36
    },
    "timeseries": [
      {
        "day": "2026-02-18",
        "total_messages": 42
      }
    ]
  }
}
```

### `POST /api/local-model/download`

**Category:** Settings & Config

**Summary:** Download Local Model

Download a specific local GGUF model from Hugging Face. Requires local_model_license_acknowledged=true in settings.

**Tags:** settings, local-model, write

**Request model:** `LocalModelDownloadRequest`

**Request example:**
```json
{
  "model_id": "qwen3-4b-q4"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "model_id": "qwen3-4b-q4",
    "path": "~/.clawpad/models/qwen3-4b-q4.gguf",
    "size_bytes": 2621440000
  }
}
```

**System effects:**
- Downloads model file to local storage

### `POST /api/local-model/providers/probe`

**Category:** Settings & Config

**Summary:** Probe Local Provider

Run explicit capability probe (models/chat/tools) against one OpenAI-compatible local endpoint and persist the result.

**Tags:** settings, local-model, write

**Request model:** `LocalProviderProbeRequest`

**Request example:**
```json
{
  "provider_id": "ollama",
  "endpoint": "http://127.0.0.1:11434/v1",
  "model": "qwen3:4b",
  "timeout_s": 6.0,
  "force": true
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider_id": "ollama",
    "endpoint": "http://127.0.0.1:11434/v1",
    "selected_model": "qwen3:4b",
    "supports_tools": false,
    "supports_images": false,
    "success": true,
    "error": ""
  }
}
```

### `POST /api/local-model/runtime/install`

**Category:** Settings & Config

**Summary:** Install Local Runtime

Install local runtime dependencies (llama-cpp-python + huggingface-hub) to ClawPad-managed runtime directory.

**Tags:** settings, local-model, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "installed": true,
    "runtime_packages_dir": "~/.clawpad/runtime_packages"
  }
}
```

**System effects:**
- Installs local Python runtime packages

### `POST /api/openclaw-gateway/benchmark`

**Category:** Settings & Config

**Summary:** Run OpenClaw A/B Benchmark

Run one fair benchmark prompt through both ClawPad and external OpenClaw gateway and return response/token telemetry.

**Tags:** settings, openclaw, benchmark, write

**Request model:** `OpenClawBenchmarkRequest`

**Request example:**
```json
{
  "prompt": "Summarize the latest channel integration status.",
  "timeout_s": 180,
  "model_override": "anthropic/claude-opus-4-6"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "clawpad": {
      "actual_total_tokens": 1234
    },
    "openclaw": {
      "actual_total_tokens": 1450
    }
  }
}
```

**System effects:**
- Runs two model calls for benchmark

### `POST /api/openclaw-gateway/query`

**Category:** Settings & Config

**Summary:** Query OpenClaw Gateway

Run one prompt directly through external OpenClaw gateway only. Useful for API-level testing of Original OpenClaw mode.

**Tags:** settings, openclaw, write, testing

**Request model:** `OpenClawGatewayQueryRequest`

**Request example:**
```json
{
  "prompt": "Give one sentence summary of the current topic.",
  "timeout_s": 120,
  "model_override": "openai/gpt-4o-mini"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "openclaw": {
      "engine": "openclaw_gateway",
      "response": "One-sentence answer...",
      "actual_total_tokens": 1234
    }
  }
}
```

**System effects:**
- Runs one OpenClaw gateway model call

### `POST /api/openclaw-gateway/restart`

**Category:** Settings & Config

**Summary:** Restart OpenClaw Gateway

Restart external OpenClaw benchmark gateway process.

**Tags:** settings, openclaw, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "restarted": true,
    "status": "starting"
  }
}
```

**System effects:**
- Restarts benchmark gateway process

### `POST /api/openclaw-gateway/start`

**Category:** Settings & Config

**Summary:** Start OpenClaw Gateway

Start external OpenClaw benchmark gateway process.

**Tags:** settings, openclaw, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "started": true,
    "status": "starting"
  }
}
```

**System effects:**
- Starts benchmark gateway process

### `POST /api/openclaw-gateway/stop`

**Category:** Settings & Config

**Summary:** Stop OpenClaw Gateway

Stop external OpenClaw benchmark gateway process.

**Tags:** settings, openclaw, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "stopped": true,
    "status": "stopping"
  }
}
```

**System effects:**
- Stops benchmark gateway process

### `PUT /api/openclaw/settings`

**Category:** Settings & Config

**Summary:** Update OpenClaw Tab Settings

Update OpenClaw-only settings for targeted tab automation/testing without sending a full /api/settings payload.

**Tags:** settings, openclaw, write

**Request model:** `UpdateOpenClawSettingsRequest`

**Request example:**
```json
{
  "openclaw_mode": "original_gateway",
  "openclaw_gateway_port": 18789,
  "openclaw_gateway_model_override": "openai/gpt-4o-mini"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "openclaw_mode": "original_gateway",
    "gateway_status": {
      "status": "starting",
      "running": false
    }
  }
}
```

**System effects:**
- Updates OpenClaw settings and applies runtime mode switch

### `PUT /api/settings`

**Category:** Settings & Config

**Summary:** Update Settings

Partially update settings. Only non-null fields are applied. Supports changing AI model, theme, context injection behavior, system prompt, local-model assist settings, OpenClaw benchmark gateway settings, zoom level, and more.

**Tags:** settings, write

**Request model:** `UpdateSettingsRequest`

**Request example:**
```json
{
  "provider": "openai",
  "model": "gpt-4o",
  "local_model_enabled": true,
  "primary_local_model": "qwen3-4b-q4",
  "local_primary_provider": "embedded",
  "local_fallback_chain": [
    "ollama:qwen3:4b",
    "lmstudio:qwen3-4b-instruct"
  ],
  "openclaw_mode": "original_gateway",
  "openclaw_gateway_enabled": true,
  "openclaw_gateway_port": 18789,
  "context_injection_mode": "full"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "provider": "openai",
    "model": "gpt-4o",
    "local_model_enabled": true,
    "primary_local_model": "qwen3-4b-q4",
    "local_primary_provider": "embedded",
    "local_fallback_chain": [
      "ollama:qwen3:4b",
      "lmstudio:qwen3-4b-instruct"
    ],
    "openclaw_mode": "original_gateway",
    "openclaw_gateway_enabled": true,
    "openclaw_gateway_port": 18789,
    "context_injection_mode": "full"
  }
}
```

**System effects:**
- Updates settings in database
- May change AI behavior

## System & Database

### `GET /api/database/info`

**Category:** System & Database

**Summary:** Database Info

Get database path, size, and schema version.

**Tags:** database, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "path": "~/.clawpad/clawpad.db",
    "size_bytes": 438272,
    "schema_version": 5
  }
}
```

### `GET /api/notifications`

**Category:** System & Database

**Summary:** List Notifications

Get recent notifications, optionally filtered by project.

**Tags:** notifications, read

**Query params:**
- `project_id` (str), optional - Filter by project (optional)
- `limit` (int), optional, default=50 - Max results (1-500)

**Response example:**
```json
{
  "success": true,
  "data": []
}
```

### `POST /api/database/backup`

**Category:** System & Database

**Summary:** Create Backup

Create a timestamped backup of the database file.

**Tags:** database, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "backup_path": "~/.clawpad/clawpad.backup_1770531747.db"
  }
}
```

**System effects:**
- Creates database backup file on disk

### `DELETE /api/notifications`

**Category:** System & Database

**Summary:** Clear Notifications

Clear all notifications, optionally for a specific project.

**Tags:** notifications, write

**Query params:**
- `project_id` (str), optional - Clear for project (optional)

**Response example:**
```json
{
  "success": true,
  "data": {
    "cleared": true
  }
}
```

## Themes & Appearance

### `GET /api/themes`

**Category:** Themes & Appearance

**Summary:** List Themes

List all available UI themes with their display names.

**Tags:** themes, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "name": "starry_night",
      "display_name": "Starry Night"
    },
    {
      "name": "royal_sapphire",
      "display_name": "Royal Sapphire"
    },
    {
      "name": "deco_luxe",
      "display_name": "Champagne Noir"
    },
    {
      "name": "monet_lilies",
      "display_name": "Monet Lilies"
    }
  ]
}
```

### `POST /api/themes/{theme_name}`

**Category:** Themes & Appearance

**Summary:** Apply Theme

Apply a theme by name. Changes the UI immediately.

**Tags:** themes, write

**Path params:**
- `theme_name`

**Response example:**
```json
{
  "success": true,
  "data": {
    "applied": "starry_night"
  }
}
```

**System effects:**
- Changes UI theme globally

## UI Control

### `GET /api/ui/current-view`

**Category:** UI Control

**Summary:** Get Current View

Get information about the currently active view. Returns the view name (welcome, chat, settings, extensions), and view-specific details like settings tab index/name, scroll position, and window geometry.

**Tags:** ui, state, inspection, read

**Response example:**
```json
{
  "success": true,
  "data": {
    "view": "settings",
    "settings_tab_index": 0,
    "settings_tab": "general",
    "window_geometry": {
      "x": 100,
      "y": 100,
      "width": 2092,
      "height": 1282
    }
  }
}
```

### `GET /api/ui/element-geometry/{element_name}`

**Category:** UI Control

**Summary:** Get Element Geometry

Get the screen coordinates and size of a named UI element. Use this to calculate click targets for coordinate-based interaction. Available elements: extensions_button, settings_button, new_topic_button, sidebar, search_bar, chat_input, send_button, content_area, extensions_search, check_updates_btn, download_update_btn, local_model_enable_cb, local_model_combo, local_model_license_ack_cb, local_model_download_btn, local_model_runtime_btn.

**Tags:** ui, geometry, automation, read

**Path params:**
- `element_name`

**Response example:**
```json
{
  "success": true,
  "data": {
    "element": "settings_button",
    "x": 12,
    "y": 810,
    "width": 44,
    "height": 44,
    "global_x": 212,
    "global_y": 1080
  }
}
```

### `GET /api/ui/elements`

**Category:** UI Control

**Summary:** List Supported UI Elements

Return the canonical remotely-addressable UI element inventory, including element name, expected view context, and click policy.

**Tags:** ui, inventory, automation, read

**Response example:**
```json
{
  "success": true,
  "data": [
    {
      "name": "settings_button",
      "view": "chat",
      "widget_type": "QPushButton",
      "click_target": "center"
    }
  ]
}
```

### `GET /api/ui/widget-tree`

**Category:** UI Control

**Summary:** Get Widget Tree

Get the full Qt widget hierarchy of the current view as a JSON tree. Each node includes type, objectName, visibility, enabled state, geometry, text content (for labels/buttons), and checked state (for checkboxes). Use max_depth to limit tree depth for performance.

**Tags:** ui, inspection, accessibility, automation, read

**Query params:**
- `max_depth` (int), optional, default=5 - Maximum tree depth (1-20)

**Response example:**
```json
{
  "success": true,
  "data": {
    "view": "settings",
    "tree": {
      "type": "SettingsView",
      "name": "settingsView",
      "visible": true,
      "enabled": true,
      "geometry": {
        "x": 0,
        "y": 0,
        "w": 1788,
        "h": 1248
      },
      "children": [
        {
          "type": "QPushButton",
          "name": "settingsBackBtn",
          "visible": true,
          "text": "←",
          "geometry": {
            "x": 12,
            "y": 10,
            "w": 44,
            "h": 44
          }
        }
      ]
    }
  }
}
```

### `POST /api/ui/check-for-updates`

**Category:** UI Control

**Summary:** Check for Updates

Trigger a software update check. Compares the current version against the remote version manifest. Returns whether an update is available and the current version string.

**Tags:** ui, updates, system, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "update_available": false,
    "current_version": "0.4.0",
    "error": null
  }
}
```

**System effects:**
- Contacts update server
- May update Settings UI with result

### `POST /api/ui/click`

**Category:** UI Control

**Summary:** Click Element

Click a UI element by name or screen coordinates. When using element name, the click targets the center of the widget. When using coordinates (x, y), the click is delivered to whatever widget is at that position. Returns the widget type and name that received the click.

**Tags:** ui, interaction, automation, write

**Request model:** `ClickRequest`

**Request example:**
```json
{
  "element": "check_updates_btn"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "success": true,
    "clicked": "check_updates_btn"
  }
}
```

**System effects:**
- Triggers click event on target widget

### `POST /api/ui/key-press`

**Category:** UI Control

**Summary:** Send Key Press

Send a keyboard event to the application. Supports key names (e.g., 'Return', 'Escape', 'Tab', 'A', 'F5') and optional modifier keys (Ctrl, Shift, Alt, Meta). The key event is delivered to the currently focused widget.

**Tags:** ui, keyboard, interaction, write

**Request model:** `KeyPressRequest`

**Request example:**
```json
{
  "key": "Return",
  "modifiers": [
    "Ctrl"
  ]
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "success": true,
    "key": "Return",
    "modifiers": [
      "Ctrl"
    ],
    "target": "MainWindow"
  }
}
```

**System effects:**
- Sends key event to focused widget

### `POST /api/ui/open-settings`

**Category:** UI Control

**Summary:** Open Settings

Open the Settings view in the main content area.

**Tags:** ui, navigation, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "opened": true
  }
}
```

**System effects:**
- Switches main content to Settings view

### `POST /api/ui/resize-window`

**Category:** UI Control

**Summary:** Resize Window

Resize and optionally reposition the main ClawPad window. Useful for automation/video capture setups with exact dimensions.

**Tags:** ui, window, automation, write

**Request example:**
```json
{
  "width": 2560,
  "height": 1440,
  "x": 120,
  "y": 80
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "resized": true,
    "width": 2560,
    "height": 1440,
    "x": 120,
    "y": 80
  }
}
```

**System effects:**
- Resizes and optionally moves application window

### `POST /api/ui/scroll`

**Category:** UI Control

**Summary:** Scroll View

Scroll the active view up or down by a specified number of steps. Works in chat view (message list) and settings view (scroll area). Returns the current scroll position and maximum.

**Tags:** ui, scroll, interaction, write

**Request model:** `ScrollRequest`

**Request example:**
```json
{
  "direction": "down",
  "amount": 5
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "scrolled": true,
    "direction": "down",
    "position": 100,
    "maximum": 180,
    "view": "settings"
  }
}
```

**System effects:**
- Scrolls the active scrollable area

### `POST /api/ui/scroll-to-bottom`

**Category:** UI Control

**Summary:** Scroll to Bottom

Scroll the chat view to the bottom to show the latest messages.

**Tags:** ui, scroll, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "scrolled": true
  }
}
```

**System effects:**
- Scrolls chat view to bottom

### `POST /api/ui/set-input-text`

**Category:** UI Control

**Summary:** Set Input Text

Set the text content of the chat message input field programmatically.

**Tags:** ui, input, write

**Request example:**
```json
{
  "text": "Hello, AI!"
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "text_set": true
  }
}
```

**System effects:**
- Updates chat input field text

### `POST /api/ui/set-sidebar-visible`

**Category:** UI Control

**Summary:** Set Sidebar Visibility

Explicitly show or hide the sidebar. Pass visible=true to show, visible=false to hide. Idempotent — hiding an already-hidden sidebar is a no-op.

**Tags:** ui, sidebar, navigation, write

**Request example:**
```json
{
  "visible": false
}
```

**Response example:**
```json
{
  "success": true,
  "data": {
    "visible": false
  }
}
```

**System effects:**
- Shows or hides the sidebar

### `POST /api/ui/settings-tab/{tab_name}`

**Category:** UI Control

**Summary:** Switch Settings Tab

Switch to a specific tab within the Settings view. Valid tab names: general, connection, channels, models, local_model, openclaw, ai_context, memory, database, security, remote, agent, notifications.

**Tags:** ui, navigation, settings, write

**Path params:**
- `tab_name`

**Response example:**
```json
{
  "success": true,
  "data": {
    "tab": "openclaw",
    "index": 4
  }
}
```

**System effects:**
- Switches the active settings tab

### `POST /api/ui/show-chat`

**Category:** UI Control

**Summary:** Show Chat View

Switch the main content area back to the Chat view.

**Tags:** ui, navigation, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "shown": true
  }
}
```

**System effects:**
- Switches main content to Chat view

### `POST /api/ui/show-extensions`

**Category:** UI Control

**Summary:** Show Extensions View

Open the Extensions marketplace view in the main content area.

**Tags:** ui, navigation, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "shown": true
  }
}
```

**System effects:**
- Switches main content to Extensions view

### `POST /api/ui/toggle-sidebar`

**Category:** UI Control

**Summary:** Toggle Sidebar

Toggle the sidebar (topic list) visibility. If visible, collapses it to give 100% content width. If hidden, restores it to its previous width.

**Tags:** ui, sidebar, navigation, write

**Response example:**
```json
{
  "success": true,
  "data": {
    "toggled": true,
    "visible": false
  }
}
```

**System effects:**
- Toggles sidebar visibility

## WebSocket

### `WebSocket /ws`

**Category:** WebSocket

**Summary:** Real-Time Events

WebSocket endpoint for real-time bidirectional communication. Receive live events as they happen: message streaming chunks, AI response completions, project changes, and more.

On connect, you receive a welcome message. Send a subscribe message to filter events by topic (default: all).

**Tags:** websocket, realtime, streaming

**Request example:**
```json
{
  "subscribe": {
    "action": "subscribe",
    "topics": [
      "message.sent",
      "project.created"
    ]
  },
  "ping": {
    "action": "ping"
  }
}
```

**Response example:**
```json
{
  "welcome": {
    "type": "welcome",
    "data": {
      "message": "Connected to ClawPad API"
    }
  },
  "event": {
    "type": "message.sent",
    "topic": "message.sent",
    "data": {
      "id": "msg_new1",
      "role": "user",
      "content": "Hello AI"
    },
    "seq": 42
  }
}
```

**System effects:**
- Maintains persistent connection
- Receives real-time events
