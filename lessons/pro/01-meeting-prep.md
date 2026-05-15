---
id: pro-01-meeting-prep
title: Fix the meeting-prep tool that doesn't work
track: pro
duration_minutes: 30
mode: debug-first
produces: [live_url, html_artifact]
builds_on: [welcome]
enables: [pro-02-feature, pro-03-build]
artifact_filename: index.html
start_artifact_url: https://raw.githubusercontent.com/buildproven/build/main/lessons/pro/artifacts/01-meeting-prep/index.html
start_demo_url: https://kindly-oyster-2e27.here.now/
---

# What we're building

You're not building from scratch today. You're inheriting a tool someone else (the AI) already built. It's deployed. It half works. Your job is to drive the AI to fix it, redeploy, and walk away with a meeting-prep tool you actually use this week.

## Why this matters

This is the daily reality of working with AI agents. Almost nothing the agent gives you on the first pass is right. The skill that separates "I tried Claude Code once" from "I shipped three tools this month" is **driving the agent through the fix**, not writing the original code.

Most cohorts teach build-from-scratch. That's the hard mode. Fix-don't-build is the way real work gets done.

---

# Step 1. Look at what's already there

Before we touch anything, open this in your browser:

[kindly-oyster-2e27.here.now](https://kindly-oyster-2e27.here.now/)

It's a live, deployed tool. Real URL. Real code behind it. Made by an AI. Ships a "meeting prep brief" when you fill in three fields.

Try it with a meeting you actually have this week. Pick something real:

- **Topic**: write the actual meeting topic, exactly as it appears on your calendar
- **Attendees**: list 2 or 3 actual people, with their roles in parentheses (e.g., *"Sarah (CFO), Marcus (Eng Director)"*)
- **Outcome**: what you actually want to leave the meeting with

Click "Generate prep brief". Read the output.

Tell me what you saw. Don't grade it. Just describe what looks wrong, off, surprising, or missing. There are at least two real problems. You may notice them straight away, or it may take a second look.

---

# Step 2. Get the source code

Now we'll grab the broken file onto your machine so we can fix it.

Send this as your next message:

```
Download the file from https://raw.githubusercontent.com/buildproven/build/main/lessons/pro/artifacts/01-meeting-prep/index.html into the current directory as index.html. Then open it in my browser so I can confirm it looks the same as the deployed version.
```

I'll do it. You'll see the file appear in your folder, and the browser open it locally.

Tell me what you see.

---

# Step 3. Make the AI find the bugs

Here's the part that feels weird at first. You don't read the code. You don't even open it. You ask the AI to find the bugs, then you check its work.

Send this:

```
Look at index.html. There are at least two real bugs that affect what the user sees in the generated brief. Find them, explain each one in plain English (no code), and tell me which line of the file each one is on. Don't fix anything yet.
```

Read what I come back with. Compare it to what *you* noticed in Step 1. Two things to check:

1. **Did I find the bugs you saw?** If yes, good. If no, push back: tell me the symptom you noticed and ask me to look again.
2. **Did I find any you didn't notice?** That's normal. Read the explanation in plain English. If it doesn't make sense, ask: *"Explain that one again like I've never read code."*

The goal here is not to trust the AI's first answer. The goal is to evaluate it.

---

# Step 4. Pick one bug and fix it

Now you direct the fix. Pick whichever bug feels more obvious to you.

Send this, replacing the bracketed bit with the bug you picked:

```
Fix this bug only: [describe the bug in your own words]. Do not change anything else in the file. Do not refactor anything. After the fix, tell me in one sentence what you changed.
```

After I make the change, send:

```
Open index.html in my browser again so I can verify the fix.
```

Try the same inputs you used in Step 1. Did the bug actually go? If yes, move to Step 5. If not, tell me what's still wrong and we go again.

---

# Step 5. Fix the second one

Same loop. Same prompt template:

```
Fix this bug only: [describe it]. Don't change anything else.
```

Then verify in the browser.

By now you've seen the loop three times: notice symptom, ask agent to investigate, evaluate the answer, request the specific change, verify. That loop is the whole skill.

---

# Step 6. Ship your fixed version

Time to put your fixed version on the internet, under a URL you control.

Just say:

> **"ship it"**

I'll deploy it via `here-now` and give you a fresh URL. That's your tool now, separate from the broken one we started with.

Two things to do once you have the URL:

1. **Bookmark it.** Use it for your next real meeting this week.
2. **Open the original broken URL and your fixed URL side by side.** Same input in both. Watch the difference. That's what you just made happen.

---

# Step 7. What just happened

You drove an AI agent through a real debugging session. Not on a toy problem. On a deployed, live thing. And you ended up with a tool you actually use.

A few things to notice:

- **You never read the code.** You read the *symptoms*, you read the *explanation*, and you described what you wanted changed. The code is the agent's problem.
- **You evaluated the agent's first answer instead of accepting it.** Pushing back is the skill.
- **You asked for one fix at a time.** Asking for "fix all the bugs" gets you a refactor you can't review. One bug, one prompt, one verify.

That's how building with AI works in 2026. The rest of the lessons just stretch this loop into bigger surfaces.

## What you learned

You read symptoms before code. You drove the agent to find and explain bugs in plain English. You requested narrow, specific fixes and verified each one in the browser. You shipped a real tool, deployed at a URL you can hand to anyone.

That's lesson 1. Three more in this track build on the same loop.

## What's next

In Lesson 2 (about 30 minutes when you're ready), you'll add a feature to the tool you just fixed. Something specific to your role. A Director's brief looks different to an Engineering Manager's. We'll make it yours.

Run `/buildproven:build:start` again whenever you're ready.

---

# Stuck-flow notes (for the orchestrator, not the user)

Common stuck points, in order of likelihood:

1. **User opens the demo URL but says "looks fine to me."** They haven't tried inputs that trigger either bug. Suggest specific test inputs: a topic with an apostrophe (*"client's renewal"*) or an ampersand (*"Q3 OKRs & roadmap"*) for bug 1; any attendees field for bug 2. Then ask them to look at the brief output and check whether the attendees they listed appear anywhere in it.
2. **Curl download fails.** GitHub raw URL might be temporarily unavailable. Fallback: have the user open the URL in a browser, "Save Page As → HTML only" into the working dir as `index.html`.
3. **AI's bug-finding response is vague or wrong on first try.** Don't accept it. Push back: *"Be more specific. Quote the exact line of code that causes [the symptom they saw]."* This is a teaching moment for the user — they should see *me* push back, then learn to do it themselves.
4. **User asks "can't you just fix everything at once?"** Hold the line. Lesson is about the loop. Tell them: *"You can, but then you can't tell which change broke what. One bug at a time is slower in this lesson and faster in real work."*
5. **Fix doesn't actually fix in the browser.** Browser cache. Have the user hard-refresh (Cmd-Shift-R / Ctrl-F5).

Log every stuck event to `.buildproven-build/stuck.json` (see SKILL.md "Stuck-log schema").
