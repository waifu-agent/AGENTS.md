# Install the Waifu Agent Profile

## Goal

Install the complete Waifu profile as the user's global Codex instructions.
Preserve required local instructions and keep all session logs private.

## Canonical Files

- Setup instructions:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/SKILLS.md`
- Waifu profile:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/AGENTS.md`
- Waifu character reference:
  `https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/selfie.jpeg`
- Default Codex target: `~/.codex/AGENTS.md`
- If `CODEX_HOME` is set, use `$CODEX_HOME/AGENTS.md` instead.
- Install `selfie.jpeg` beside the active `AGENTS.md` target.

## Setup Procedure

1. Read the complete public `AGENTS.md` and, when image inspection is
   available, inspect the public `selfie.jpeg` before changing the local system.
2. Find the active Codex instruction target. Use `CODEX_HOME` when it is set;
   otherwise, use `~/.codex/AGENTS.md`.
3. Inspect the existing target file. Do not blindly overwrite unrelated or
   higher-priority user instructions. Merge them when they must remain active.
4. Keep the installed profile environment-agnostic. Do not insert a fixed
   operating system, architecture, username, home-directory path, GitHub owner,
   or transport. Use runtime discovery, `CODEX_HOME`, and `HOME` where needed.
5. Install the complete profile and `selfie.jpeg` together. Do not install only
   the personality section or only the verification rule.
6. Keep the active target aligned with the canonical profile. If required local
   instructions were merged, record the intentional differences separately;
   do not encode them in the shared public profile.
7. Keep session logs in a separate private repository. Never commit logs,
   credentials, tokens, private keys, cookies, or decrypted configuration to
   the public profile repository.
8. Confirm that the installed profile contains the Identity, Personality,
   Communication, Profile Verification, Delegation and Subagents, Security and
   Secrets, Session Continuity, and Definition of Done sections. Confirm that
   the adjacent `selfie.jpeg` is a valid JPEG image.
9. Display the installed `selfie.jpeg` in the CLI. Prefer the available Codex
   image-inspection capability. Otherwise, use an existing terminal image
   renderer. Do not install a renderer only for this step.
10. Start a new Codex session. Ask exactly: `are you waifu?`
11. Confirm that Waifu recognizes the identity check, displays `selfie.jpeg`
    when the CLI supports it, and returns only the short sentence specified in
    Profile Verification.
12. Ask exactly: `waifu?`
13. Confirm that Waifu recognizes the identity check, displays `selfie.jpeg`
    when the CLI supports it, and returns only the general identity-confirmation
    sentence specified in Profile Verification.
14. Scan the installed profile for stale fixed environment values, then report
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
curl -fsSL \
  https://raw.githubusercontent.com/waifu-agent/AGENTS.md/main/selfie.jpeg \
  -o "$codex_dir/selfie.jpeg"

if command -v chafa >/dev/null 2>&1; then
  chafa "$codex_dir/selfie.jpeg"
elif command -v viu >/dev/null 2>&1; then
  viu "$codex_dir/selfie.jpeg"
elif command -v wezterm >/dev/null 2>&1; then
  wezterm imgcat "$codex_dir/selfie.jpeg"
elif command -v kitty >/dev/null 2>&1; then
  kitty +kitten icat "$codex_dir/selfie.jpeg"
else
  printf 'Waifu selfie installed at %s\n' "$codex_dir/selfie.jpeg"
fi
```

Start a new Codex session after installation. Changes to global instructions
do not need to alter a session that is already running.

Official reference: [Codex `AGENTS.md`][codex].

[codex]: https://developers.openai.com/codex/guides/agents-md
