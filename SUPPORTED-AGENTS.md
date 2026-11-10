# Supported agents

Each agent you create with `cclaw newagent` runs one of the coding agents below on your computer. You pick it when you create the agent, and it can't be changed afterwards. To use a different one, create another agent.

## Before you start

You need Node.js 22 or later, on macOS or Linux. Sign in to the coding agent itself before you start it. If it isn't signed in, `cclaw start` tells you what to run.

| Agent            | Install                                 | Sign in                                                        |
| ---------------- | --------------------------------------- | -------------------------------------------------------------- |
| Claude Code      | cclaw starts it for you                 | Run `claude` once and sign in                                  |
| Codex            | cclaw starts it for you                 | `codex login`                                                  |
| DeepSeek Harness | cclaw starts it for you                 | See the DeepSeek Harness docs                                  |
| Gemini CLI       | cclaw starts it for you                 | Set `GEMINI_API_KEY` where you start cclaw, or use Vertex AI   |
| GitHub Copilot   | cclaw starts it for you                 | `copilot login`                                                |
| Cursor           | Install the Cursor CLI (`cursor-agent`) | `cursor-agent login`                                           |
| OpenCode         | Install OpenCode (`opencode`)           | `opencode auth login` (OpenCode's free models need no sign-in) |

Another agent that supports the Agent Client Protocol (ACP) can be added as a custom launch command. What works then depends on that agent.

## What works with each agent

✓ works · ~ works, with a limit (see notes) · ✗ not available · ? not verified

|                                                    | Claude Code | Codex           | DeepSeek | Gemini | Copilot | Cursor | OpenCode |
| -------------------------------------------------- | ----------- | --------------- | -------- | ------ | ------- | ------ | -------- |
| Shows the reply while it's being written           | ✓           | ✓               | ✓        | ✓      | ✓       | ✓      | ✓        |
| Reads images you send                              | ✓           | ✓               | ✓        | ✓      | ?       | ✓      | ~ [1]    |
| Receives the group files your message refers to    | ✓           | ✓               | ✓        | ✓      | ?       | ✓      | ✓        |
| Continues the conversation after a restart         | ✓           | ✓               | ✓        | ✓      | ?       | ✓      | ✓        |
| `/` commands                                       | ✓           | ✓               | ✗        | ✓      | ?       | ✓      | ✓        |
| Uses ChubbyClaw tools (group files, memory, …)     | ✓           | ✓               | ✓        | ~ [2]  | ?       | ✓      | ✓        |
| Shows a plan for multi-step work                   | ✓           | ✓               | ✓        | ✓      | ✓       | ✓      | ✓        |
| Asks you before risky actions, in its default mode | ✓           | ✓               | ~ [3]    | ✓      | ✓       | ~ [4]  | ✗ [4]    |
| Change the permission mode from ChubbyClaw         | ✓           | ✓               | ~ [5]    | ✓      | ?       | ✓      | ✓        |
| Change the model from ChubbyClaw                   | ✓           | ✓               | ✓        | ✓      | ✗       | ✓      | ✓        |
| Stop button ends the work [6]                      | ✓           | ✓               | ✓        | ✓      | ?       | ✓      | ✓        |
| A message sent while it's busy                     | Waits       | Joins the reply | Waits    | Waits  | ?       | Waits  | Waits    |
| Shows context and usage-limit status               | ✓           | ✓               | ✗        | ✗      | ✗       | ✗      | ✗        |

**Notes**

1. OpenCode's default free model can't read images. Choose a model that can.
2. Gemini CLI uses ChubbyClaw tools only in a folder you trust. cclaw asks you about the folder when you create the agent.
3. In DeepSeek Harness's default mode, it edits files inside its working folder without asking. It asks before changes outside it.
4. In their default modes, Cursor runs most actions and OpenCode runs all actions without asking. Pick another mode if you want to approve actions first.
5. For DeepSeek Harness, a permission mode change applies from the next conversation.
6. Stop ends the commands the agent started for that work. Commands started fully detached, for example with `nohup … &`, keep running.

## Full-access modes

These modes run actions without asking you first: Claude Code's `bypassPermissions`, Codex's `agent-full-access`, DeepSeek Harness's `danger-full-access`, Gemini CLI's `yolo` and GitHub Copilot's `autopilot`. In these modes, people who can message the agent can run commands on your computer. ChubbyClaw marks them with a warning when you pick one.
