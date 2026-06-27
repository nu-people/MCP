# nü people MCP Server

## Description

Public, **read-only** MCP (Model Context Protocol) server exposed over Streamable HTTP.
It allows AI clients such as Claude, Copilot, ChatGPT, or custom agents to discover open jobs,
view job details, inspect contract types and skill clusters, and retrieve direct application links.

## Features

- Search open jobs semantically (`search_jobs`)
- Retrieve job details by ID (`get_job_details`)
- List available contract types (`list_contract_types`)
- Get current skill clusters (`get_skill_clusters`)
- Generate a direct application link for a job (`get_application_link`)

### Technical Overview

- **Endpoint:** `https://www.nuepeople.com/mcp` (Streamable HTTP)
- **Authentication:** none (public data only)

## Available Tools

| Tool | Description |
|------|-------------|
| `search_jobs` | Searches open jobs using semantic search, with optional location and contract type filters. |
| `get_job_details` | Returns public job details for a job ID. |
| `list_contract_types` | Lists available contract types that can be used with `search_jobs`. |
| `get_skill_clusters` | Returns current skill cluster data in structured form. |
| `get_application_link` | Returns a direct application link for a job ID. |

## Configuration

### Client Configuration (VS Code / Claude Desktop)

```json
{
  "servers": {
	"nue-people": {
	  "type": "http",
	  "url": "https://www.nuepeople.com/mcp"
	}
  }
}
```


## Examples

### Example 1: Search for jobs

**User input:** “Find Senior .NET jobs in Cologne”

**Expected behavior:**
- Calls `search_jobs` with a search query and location filter
- Returns a list of matching jobs including IDs, titles, skills, and locations

### Example 2: Retrieve job details

**User input:** “Show me the details for job 123”

**Expected behavior:**
- Calls `get_job_details(id=123)`
- Returns public job details, or `null` if the job does not exist or is not public

### Example 3: Get an application link

**User input:** “I want to apply for job 123”

**Expected behavior:**
- Calls `get_application_link(jobId=123)`
- Returns a direct link to the existing CV upload / application form for that job

## Privacy Policy

This integration processes technical usage data required to operate, monitor, and secure the MCP endpoint.

Full privacy details: **https://www.nuepeople.com/datenschutz**

### Data Collection

- Collected data: technical request and telemetry data such as tool name, duration, and result status
- Usage: service operation, troubleshooting, abuse detection, and quality improvement
- Sharing: as described in the website privacy policy and applicable infrastructure providers' policies

## Support

- Contact: mail@nuepeople.com
 
## Notes

- This is an HTTP MCP endpoint embedded in a web application, not a standalone local MCPB package.
- The server is intended for public, read-only access to job-related information.
