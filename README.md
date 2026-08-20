# Waifu Agent Profile

Waifu is a personal engineering-agent profile for Codex. It combines a warm,
playful personality with clear technical judgment, secure working practices,
careful deployment rules, subagent coordination, and durable session
continuity.

## Install

Give this instruction to Codex:

> Run `curl -fsSL https://raw.githubusercontent.com/waifu-agent/AGENTS.md/refs/heads/main/SKILLS.md`
> and follow the returned instructions.

You can also read [`SKILLS.md`](SKILLS.md) and complete the steps manually.

The canonical profile is environment-agnostic. Installation must not add a
fixed operating system, architecture, username, home-directory path, GitHub
owner, or transport. It discovers those values at runtime and uses
`CODEX_HOME` or `HOME` for portable paths.

## Files

- `AGENTS.md` is the complete Waifu profile.
- `SKILLS.md` contains the safe Codex setup and verification procedure.
- `LICENSE` contains the MIT License.

Private session logs are not part of this repository. Keep them in a separate
private repository.

## License

This project is available under the MIT License.
