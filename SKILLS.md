# Install the Waifu Agent Profile

## Goal

Install the complete Waifu profile as the active agent's global instructions.
Detect the running harness, install at the correct target, preserve required
local instructions, and keep all session logs private.

## Canonical Files

- Setup instructions:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/SKILLS.md`
- Waifu profile:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/AGENTS.md`
- Installer script:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/install-waifu-agents-md`

## Harness Detection

Detect the running harness before choosing a target. In order:

1. In-process environment markers:
   - pi: `PI_CODING_AGENT=true` -> `~/.pi/agent/AGENTS.md`
   - Claude Code: `CLAUDECODE=1` ->
     `${CLAUDE_CONFIG_DIR:-~/.claude}/CLAUDE.md`
   - Cursor: `CURSOR_TRACE_ID` is set -> `~/.cursor/AGENTS.md`
   - Codex: no env marker; detect via `CODEX_HOME` set or `~/.codex`
     existing -> `${CODEX_HOME:-~/.codex}/AGENTS.md`
2. First installed CLI on PATH (`pi`, `codex`, `claude`, `cursor-agent`,
   `windsurf`, `gemini`) with its matching target file.
3. If nothing can be detected, ask the user which harness to target.

The bundled installer implements this procedure:

```sh
curl -fsSL \
  https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/install-waifu-agents-md \
  -o /tmp/install-waifu-agents-md
sh /tmp/install-waifu-agents-md
```

Override auto-detection explicitly with `WAIFU_TARGET=<harness>`.

## Setup Procedure

1. Read the complete public `AGENTS.md` before changing the local system.
2. Detect the active harness and resolve its instruction target (see
   Harness Detection).
3. Inspect the existing target file. Do not blindly overwrite unrelated or
   higher-priority user instructions. Merge them when they must remain
   active. The installer backs up any differing file before replacing it;
   review the backup and merge anything that must stay active.
4. Keep the installed profile environment-agnostic. Do not insert a fixed
   operating system, architecture, username, home-directory path, GitHub
   owner, or transport. Use runtime discovery and `HOME` where needed.
5. Install the complete profile. Do not install only the personality section
   or only the verification rule.
6. Keep the active target aligned with the canonical profile. If required
   local instructions were merged, record the intentional differences
   separately; do not encode them in the shared public profile.
7. Keep session logs in a separate private repository. Never commit logs,
   credentials, tokens, private keys, cookies, or decrypted configuration to
   the public profile repository.
8. Confirm that the installed profile contains the Identity, Personality,
   Communication, Profile Verification, Delegation and Subagents, Security
   and Secrets, Session Continuity, and Definition of Done sections.
9. Start a new session in the detected harness. Ask exactly:
   `are you waifu?`
10. Confirm that Waifu recognizes the identity check and returns only the
    short sentence specified in Profile Verification.
11. Ask exactly: `waifu?`
12. Confirm that Waifu recognizes the identity check and returns only the
    general identity-confirmation sentence specified in Profile Verification.
13. Scan the installed profile for stale fixed environment values, then
    report the detected harness, the installed target, any intentional local
    differences, and the verification result.

## Manual Installation

Use this only after you inspect the current target and confirm that it can
be replaced. Resolve `<target>` from the Harness Detection table above:

```sh
mkdir -p "$(dirname "<target>")"
curl -fsSL \
  https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/AGENTS.md \
  -o "<target>"
```

Start a new session in that harness after installation. Changes to global
instructions do not need to alter a session that is already running.

## References

- [Codex `AGENTS.md`](https://developers.openai.com/codex/guides/agents-md)
- [Pi context files](https://github.com/badlogic/pi-mono) (`~/.pi/agent/AGENTS.md`)
- [Claude Code memory](https://docs.anthropic.com/en/docs/claude-code/memory)
