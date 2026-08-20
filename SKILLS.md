# Install the Waifu Agent Profile

## Goal

Install the complete Waifu profile as the user's global Codex instructions.
Preserve required local instructions and keep all session logs private.

## Canonical Files

- Setup instructions:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/SKILLS.md`
- Waifu profile:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/AGENTS.md`
- Default Codex target: `~/.codex/AGENTS.md`
- If `CODEX_HOME` is set, use `$CODEX_HOME/AGENTS.md` instead.

## Setup Procedure

1. Read the complete public `AGENTS.md` before changing the local system.
2. Find the active Codex instruction target. Use `CODEX_HOME` when it is set;
   otherwise, use `~/.codex/AGENTS.md`.
3. Inspect the existing target file. Do not blindly overwrite unrelated or
   higher-priority user instructions. Merge them when they must remain active.
4. Keep the installed profile environment-agnostic. Do not insert a fixed
   operating system, architecture, username, home-directory path, GitHub owner,
   or transport. Use runtime discovery, `CODEX_HOME`, and `HOME` where needed.
5. Install the complete profile. Do not install only the personality section
   or only the verification rule.
6. Keep the active target aligned with the canonical profile. If required local
   instructions were merged, record the intentional differences separately;
   do not encode them in the shared public profile.
7. Keep session logs in a separate private repository. Never commit logs,
   credentials, tokens, private keys, cookies, or decrypted configuration to
   the public profile repository.
8. Confirm that the installed profile contains the Identity, Personality,
   Communication, Profile Verification, Delegation and Subagents, Security and
   Secrets, Session Continuity, and Definition of Done sections.
9. Start a new Codex session. Ask exactly: `are you waifu?`
10. Confirm that Waifu recognizes the identity check and returns only the short
    sentence specified in Profile Verification.
11. Ask exactly: `waifu?`
12. Confirm that Waifu recognizes the identity check and returns only the
    general identity-confirmation sentence specified in Profile Verification.
13. Scan the installed profile for stale fixed environment values, then report
    the installed target, any intentional local differences, and the
    verification result.

## Manual Installation

Use these commands only after you inspect the current target and confirm that
it can be replaced:

```sh
codex_dir="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$codex_dir"
curl -fsSL \
  https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/AGENTS.md \
  -o "$codex_dir/AGENTS.md"
```

Start a new Codex session after installation. Changes to global instructions
do not need to alter a session that is already running.

Official reference: [Codex `AGENTS.md`][codex].

[codex]: https://developers.openai.com/codex/guides/agents-md
