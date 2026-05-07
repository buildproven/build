# buildproven/build

> Zero to Hero with AI. A Claude Code skill that walks you through building real, live, shareable things — agent-driven, end-to-end.

## What this is

A sequenced skill suite. You install it into Claude Code, run `/buildproven:build:start`, and the agent walks you through one of two tracks:

- **Teens (12–16):** five 20-minute lessons. Build a quiz, a meme generator, a one-button game, share them, then learn how to debug and improve. Each ends with a live URL you can send to a friend.
- **Professionals (40–58):** four 60-minute lessons. Build a meeting-prep tool for your role, automate one weekly task, ship a tool your team uses, deploy publicly. Each ends with a thing you actually use Monday morning.

You don't watch a tutorial. You don't write code from scratch. You drive an AI agent and ship the output. The lessons teach you the loop: idea → prompt → run → evaluate → fix → ship.

## Install

> **Prerequisite:** [Claude Code](https://claude.com/claude-code) installed and signed in. If you've never installed it before, see [buildproven.ai/build](https://buildproven.ai/build) for a 3-minute walkthrough.

### Option 1 — Plugin marketplace (recommended)

```
/plugin install buildproven/build
```

Then in any Claude Code session:

```
/buildproven:build:start
```

### Option 2 — Manual clone

```bash
git clone https://github.com/buildproven/build ~/.claude/skills/buildproven-build
```

Then `/buildproven:build:start` in Claude Code.

## Status

**v0 — pilot.** First lesson (`teen-01-quiz`) is the only one tested end-to-end. More landing weekly. See [PLAN-buildproven-build.md](https://github.com/buildproven/buildproven/blob/main/docs/plans/PLAN-buildproven-build.md) for the roadmap.

## Contributing

This is open-source on purpose — fork it, add a `lessons/<track>/<your-lesson>.md`, and PR it back. Lesson contributions that get a real teen or professional to ship something real are extremely welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

## License

MIT — build whatever you want with it.
