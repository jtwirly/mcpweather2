# Weather MCP Server

A Model Context Protocol (MCP) server that provides weather information through Claude for Desktop. This server integrates with the National Weather Service API to provide weather forecasts and alerts for US locations. Created as part of the MIT MCP Hackathon (April 2025).

## Features

- `get_forecast`: Get detailed weather forecasts for any US location using latitude and longitude
- `get_alerts`: Retrieve active weather alerts for any US state using state code

## Requirements

- Python 3.10 or higher
- uv package manager
- Claude for Desktop
- MCP SDK 1.2.0 or higher

## Installation

1. Ensure you have uv installed:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. Set up the Python environment:
```bash
# Create and activate virtual environment
uv venv
source .venv/bin/activate

# Install dependencies
uv add "mcp[cli]" httpx
```

## Configuration

1. Create or edit your Claude for Desktop configuration at `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "weather": {
      "command": "/path/to/uv",
      "args": [
        "--directory",
        "/absolute/path/to/weather",
        "run",
        "weather.py"
      ]
    }
  }
}
```

2. Replace `/path/to/uv` with your uv executable path (find it using `which uv`)
3. Replace `/absolute/path/to/weather` with the absolute path to this project directory

## Usage

1. Start Claude for Desktop
2. Look for the hammer 🔨 icon to confirm the server is connected
3. Example queries:
   - "What's the weather in Sacramento?"
   - "What are the active weather alerts in Texas?"

## Troubleshooting

- Check Claude's logs at `~/Library/Logs/Claude/mcp*.log`
- Ensure all paths in the configuration are absolute
- Verify the server runs independently using `uv run weather.py`
- Check port 8001 is not in use by another process

## API Reference

The server uses the National Weather Service API:
- Base URL: https://api.weather.gov
- Endpoints used:
  - `/alerts/active/area/{state}` - Get alerts by state
  - `/points/{lat},{lon}` - Get forecast grid data
  - `/forecast` - Get detailed forecast

## About the MIT MCP Hackathon

This project was created during the MIT MCP Hackathon (April 2025), which aimed to introduce developers to the Model Context Protocol and help projects/startups launch their own MCP servers. The hackathon was part of the NANDA (Networked Agents and Decentralized AI) hub initiative at MIT.

## License

This project follows the original tutorial from [Model Context Protocol](https://modelcontextprotocol.io/quickstart/server)

## Screenshots

<img width="992" alt="Screen Shot 2025-04-06 at 10 17 10 PM" src="https://github.com/user-attachments/assets/0569b0e3-ec96-4175-a006-951c58d2b5c4" />

<img width="990" alt="Screen Shot 2025-04-06 at 10 17 26 PM" src="https://github.com/user-attachments/assets/49ae7174-e44b-4646-9c34-265130d1cc63" />

<img width="1002" alt="Screen Shot 2025-04-06 at 10 17 48 PM" src="https://github.com/user-attachments/assets/10c48fe8-e5c4-444c-8203-2874e13ccdad" />


