# Viralance MCP Server

Hosted [Model Context Protocol](https://modelcontextprotocol.io) server for [Viralance](https://viralance.com), an AI video and image platform. One connection gives an assistant 20+ video models (VEO 3.1, Kling, Seedance, Hailuo, PixVerse and more) with pay-as-you-go credits and no subscription. The cost of a job is shown before it runs.

This repository holds the connection details and documentation only. The server is a hosted service; there is nothing to install or run.

- Endpoint: `https://mcp.viralance.com/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.1 (PKCE, dynamic client registration) or an API key
- Official MCP Registry name: `com.viralance/mcp-server`
- Setup guide: https://viralance.com/features/claude-mcp
- Developer docs: https://viralance.com/developers

## Connect

### Claude Code

```bash
claude mcp add --transport http viralance https://mcp.viralance.com/mcp
```

Your client opens a Viralance sign-in page and asks you to approve access.

### Any MCP client (JSON config)

```json
{
  "mcpServers": {
    "viralance": {
      "url": "https://mcp.viralance.com/mcp"
    }
  }
}
```

### API key instead of OAuth

Create a key in the Viralance dashboard under Settings > API Keys and send it in the `Authorization` header:

```json
{
  "mcpServers": {
    "viralance": {
      "url": "https://mcp.viralance.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_VIRALANCE_API_KEY" }
    }
  }
}
```

Keep the key private. Keys are accepted only in the `Authorization` header, never in the URL, and can be revoked in the dashboard at any time.

## Tools

| Tool | What it does |
|---|---|
| Generate a video | Text to video and image to video, with optional start and end frames |
| Generate an image | Text to image and image to image |
| Edit a video | Restyle, reframe, upscale, subtitles, lip sync and more |
| Edit an image | Background removal, expand, relight, inpaint |
| Compose a film | Storyboard shots cut into one film with music |
| Generate a voiceover | Script to speech |
| Image to 3D model | A 3D model from one image |
| Virtual try-on | A garment on a person photo |
| Product dimension image | A product photo with its measurements |
| Analyze a video | Hook, pacing and virality notes |
| Write video hooks / Write a caption / Enhance a prompt | Text helpers |
| Get viral trends / Unlock trends | Trend reports |
| Plan, approve and follow an Autopilot run | A full campaign from one brief |
| List videos, images, saved products and @Elements | Your library |
| Save a product | Add a product to reuse in prompts |
| Get video status | Follow a job |
| Get credit balance, credit history and model credit costs | Check costs before spending |

Every tool carries a title and read-only or destructive hints. Tools that spend credits are marked destructive, so clients ask before each call.

## Pricing

Viralance uses one-time credit packs. Each job states its credit cost up front and failed jobs are refunded. Prices: https://viralance.com/pricing

## Support

support@viralance.com · [Privacy](https://viralance.com/privacy) · [Terms](https://viralance.com/terms)
