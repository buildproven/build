# Contributing to buildproven/build

Lesson contributions, bug reports, and forks are all welcome.

## The bar for a new lesson

Before you PR a new `lessons/<track>/NN-<name>.md`, the lesson must pass these:

1. **Tested with a real human in the target audience.** Teen lessons → tested by a teen. Pro lessons → tested by a non-developer professional. No exceptions.
2. **Ships a public URL.** Every lesson must end with a deployed, real artifact, not a localhost demo.
3. **Stays inside the time box.** Teen lessons ≤ 20 min. Pro lessons ≤ 60 min. If yours runs over for the test user, cut a step.
4. **Names the failure modes.** Include a "Stuck-flow notes" section at the bottom with the 3–5 most likely places this lesson breaks and how to recover.
5. **No AI tells.** Run the lesson markdown through the BuildProven 7-layer detector and clear **≥ 85/100** before opening the PR:
   ```bash
   python ~/Projects/internal/buildproven/scripts/de_ai.py lessons/<track>/NN-name.md
   ```
   Common flags: em-dash overuse (replace some with periods), rule-of-three count >4/1000w (use 2- and 4-item lists), low burstiness (vary sentence length deliberately). The full pattern guide is in `commands/bs/deaify.md` of the claude-setup repo.
6. **Frontmatter complete:** `id`, `title`, `track`, `duration_minutes`, `produces`, `builds_on`, `enables`, `artifact_filename`.

## Lesson markdown shape

```markdown
---
id: <track>-NN-<slug>
title: <user-facing title>
track: teen | pro
duration_minutes: 20
produces: [live_url, html_artifact]
builds_on: [previous-lesson-id]
enables: [next-lesson-id]
artifact_filename: <e.g., quiz.html>
---

# What we're building
[one paragraph + ideally a screenshot of the finished thing]

# Why this matters
[1–2 sentences — what they'll be able to do after]

# Step 1 — <action>
[the exact prompt to paste, or the exact thing to ask the agent to do]

# Step 2 — ...
...

# Step N — Ship it
[deploy via here-now → return URL]

# What you learned
[name the concept that was just demonstrated]

# What's next
[seed the next lesson]

# Stuck-flow notes (for the orchestrator)
[3–5 likely failure points + recovery]
```

## PR template

When you open a PR, include:

- **Test user description:** age band + relevant context (no PII; "12yo who plays Minecraft" is enough)
- **Time to complete:** observed minutes from start to deployed URL
- **What confused them:** the bit they got stuck on (this becomes the lesson's main teaching moment if it's bad enough)
- **Outcome URL:** the actual deployed artifact from the test run

PRs without a real test-user write-up will be closed.

## What we're not accepting (yet)

- Lessons that teach syntax instead of agent-driving
- Lessons that don't end with a public URL
- Generic "intro to AI" content
- Lessons longer than the time box
- "Curriculum" PRs (5 lessons in one PR) — one lesson per PR, each one fully tested

## License

By contributing, you agree your contribution is licensed under MIT, same as the rest of the repo.
