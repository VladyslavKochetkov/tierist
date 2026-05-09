<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->

# Frontend design via Gemini

This repo wires up `gemini-mcp-tool` as a project MCP server (`.mcp.json`). The `mcp__gemini-cli__ask-gemini` tool delegates to Google Gemini via the local `gemini` CLI.

**Reach for it when:**
- Doing open-ended visual or aesthetic exploration ("redesign this three different ways")
- Critiquing an existing design
- Surveying many component files where Gemini's larger context window helps

**Don't reach for it when:** the change is small and targeted, or you already know what to write. Don't use it reflexively for any frontend task.

**Prompting:** pass `@`-references to point Gemini at the relevant files. Example:

```
ask-gemini: redesign @src/app/page.tsx with a more editorial layout — give me three variants
```

**One-time setup per developer:** install Gemini CLI and run `gemini` once to authenticate. The MCP server shells out to your authenticated CLI; no API key needed.

