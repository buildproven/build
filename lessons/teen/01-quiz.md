---
id: teen-01-quiz
title: Build a Quiz About {favourite_thing}
track: teen
duration_minutes: 20
produces: [live_url, html_artifact]
builds_on: [welcome]
enables: [teen-02-meme, teen-03-game]
artifact_filename: quiz.html
---

# What we're building

A quiz about **{favourite_thing}**. Five questions. You pick the topic. The AI writes the code. At the end you get a real link you can send to a friend, and they can play it on their phone.

## Why this matters

By the end of this lesson you'll have done something most adults haven't: you drove an AI to build a real, working website, and you put it on the internet. That's the whole game.

---

# Step 1 — Tell the AI to make the quiz

You're the boss. The AI is the builder. To make it build, you **send it the exact instructions** for what to make.

**Send this as your next message** — copy it, paste it into the chat, and hit enter:

```
Create a single-page HTML quiz file called quiz.html in the current directory.

Topic: {favourite_thing}
Number of questions: 5
Style: clean, mobile-friendly, dark background with one bright accent color of your choice.

For each question:
- Show one question at a time
- 4 multiple-choice answers as buttons
- When I click an answer, show if it was right or wrong
- Then a "Next" button to go to the next question
- At the end, show my score out of 5 with a fun comment

Pick reasonable questions about {favourite_thing} and just build it. Use only HTML, CSS, and JavaScript in one file. No external libraries.
```

The AI will write the file in your folder. When it's done, it'll say so.

---

## Did it work?

> Tell me: **yes**, **no**, or **looks weird**.

(Don't worry — "no" and "weird" are normal. We'll fix it.)

---

# Step 2 — Open it and try it

Tell the AI:

```
Open quiz.html in my browser
```

Your browser should pop open with the quiz. Try answering all 5 questions.

**Two things I want you to notice:**

1. Are the questions actually about {favourite_thing}? (Sometimes the AI gets it wrong — that's fixable.)
2. Does it look good on your phone if you load the file there too? (You don't have to test this yet — we'll deploy it next.)

> Tell me: **yes it works**, or describe what looks off.

---

# Step 3 — Make one thing better

Now you're going to change one thing. This is the most important step in the whole lesson — **you're going to tell the AI exactly what to change**, and it'll do it.

Pick one of these to ask for, or invent your own:

- *"Change the background to my favourite colour: [colour]"*
- *"Make the questions harder — they're too easy"*
- *"Add a 6th question about [specific thing in {favourite_thing}]"*
- *"After the score, show a different comment for 5/5, 3-4/5, and 0-2/5"*
- *"Make the right answer flash green and the wrong answer flash red for half a second"*

**Send your change request** like this:

```
Update quiz.html: [your change here]. Don't change anything else.
```

When the AI is done, tell it: `Open quiz.html again` to see the change.

> Tell me: **looks good** or **something broke**.

---

# Step 4 — Ship it (this is the magic part)

Right now your quiz only works on **your computer**. Time to put it on the internet so anyone can play it.

I'm going to use a tool called `here-now` to publish your file. You don't have to do anything — just say:

> **"ship it"**

I'll publish it and give you back a real URL.

When I give you the link:

1. **Open it on your phone right now.** Make sure it works.
2. **Send the link to one friend or family member** with the message: *"I built this. Tell me what you think."*

Don't skip the send-it part. Shipping ≠ live URL. Shipping = someone you know is using it.

---

# Step 5 — What just happened

You just drove an AI agent to build a real website, and you put it live. Two things you should notice:

1. **You didn't write code.** You wrote *instructions* for the AI. That's the whole skill — telling an AI exactly what you want, and noticing when it gets it wrong.
2. **The thing on the internet is yours.** Not a tutorial. Not a sandbox. A real URL. Someone is playing your quiz on their phone right now.

That's "building with AI." Everything else is variations on this loop.

## What you learned

- How to **drive an agent** with a clear prompt
- How to **read what it made** and decide if it's right
- How to **ask for a change** and notice if the change worked
- How to **ship something live** so someone else can use it

You did all four. That's harder than most adults have done this year.

## What's next

In Lesson 2 (about 20 minutes when you're ready), you'll build a **meme generator** about {favourite_thing}. People type in their own caption, hit a button, get a meme they can save. Same idea — different shape.

Run `/buildproven:build:start` again whenever you're ready.

---

# Stuck-flow notes (for the orchestrator, not the user)

Common stuck points in this lesson, in order of likelihood:

1. **AI created the file in the wrong directory.** Check `pwd`; if `quiz.html` isn't there, ask the user to confirm what folder they're in and re-run Step 1.
2. **Questions aren't about {favourite_thing}.** Don't fix it silently — tell the user the AI guessed, and have *them* paste a corrective prompt. That's the lesson.
3. **`open quiz.html` doesn't open a browser.** Different OS — try `start quiz.html` (Windows) or `xdg-open quiz.html` (Linux). If still stuck, instruct the user to open the file manager and double-click the file.
4. **`here-now` is missing or fails.** Fall back to local-only: have the user open the file in their browser. Tell them: *"We'll publish it next session — your file is saved."*
5. **The user says "I don't get it" with no specifics.** Don't push forward. Ask exactly: *"Look at the screen right now. What's the last thing the AI said?"* Read that, then proceed.

Log every stuck event to `.buildproven-build/stuck.json` with: lesson_id, step, user_quote, resolution.
