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

# Browser automation via Playwright

This repo wires up `@playwright/mcp` as a project MCP server (`.mcp.json`). The `mcp__playwright__*` tools let you drive a real browser to verify UI behavior — navigate, click, type, take screenshots, read console output and network traffic.

**Reach for it when:**
- Verifying a frontend change actually works in the browser before claiming a task is done
- Reproducing a UI bug from a description
- Inspecting console errors or network failures that aren't reproducible from code alone

**Don't reach for it when:** the change is purely build-time, type-level, or backend logic with full unit-test coverage. Don't open a browser to verify something a type check or unit test already proves.

`browser_evaluate` and `browser_file_upload` are intentionally not pre-allowed — they execute arbitrary JS or read from disk and should require an explicit prompt.

**One-time setup per developer:** browsers are downloaded automatically on first MCP launch (~hundreds of MB, may take a minute).

