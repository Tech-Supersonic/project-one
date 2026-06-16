# Project One
## AI Task Workspace

*Created by TSS Talent Lab. Version 1.2.*

---

## Overview

In this project you build and deploy a working full-stack web application: an AI task workspace. Users sign in, create tasks, turn freeform notes into structured tasks with AI, and turn meeting transcripts into action items. You build it by following the software development lifecycle from start to finish, and you check that it works before you ship.

This is your first full-stack build. Project Zero set up your tools. Here you use them to ship something real. This project runs over one and a half to two weeks. One and a half weeks is the target, and two weeks is the maximum. Everything is done inside one GitHub repository and submitted there.

## What you are building

The core application, all required:

- **Tasks**: create, edit, complete, and delete tasks. Each task has a title, a description, a priority, a status, and a due date.
- **A board**: show tasks on a board with columns by status, for example To Do, In Progress, and Done, and let the user move tasks across it. This board is a feature inside the app you are building. It is separate from the ClickUp board where you track your own work on this project.
- **Notes to task (AI)**: the user types or pastes freeform text, and the app uses an AI model to turn it into one structured task with a title, description, priority, and due date, ready to save.
- **Transcript to action items (AI)**: the user pastes a meeting transcript, and the app uses an AI model to pull out several action items, each with a title, an owner, and a due date, saved as tasks.
- **Login**: each user signs in and sees only their own tasks.

## Optional bonus: connect Google Drive

If you finish the core with time to spare, take this on. It is a bonus, not a requirement, and it does not affect whether you pass. The user signs in with Google, and the app reads a meeting transcript file directly from their Google Drive and turns it into action items, with no copy and paste. It brings in Google sign-in and the Google Drive API, and it will stretch you. Only start it once the core is built, working, and deployed.

## How you work

You may use any AI agent to help you build this, including Claude Code, your teach-me agent, and your troubleshoot agent. Building fast with AI is the point of how we work. There is one hard rule alongside it: you must understand every part of what you ship. You must be able to explain what each function does, how data flows through the app from the browser to the back-end to the database and back, and why each choice was made. On your review call we will ask, and you will need to answer without notes. If you cannot explain a part, you do not yet own it, so go back and learn it with your teach-me agent before you present. The goal is to learn how to build, deploy, and ship with AI while genuinely holding the foundations underneath.

TSS provides your AI access for both building and for the app itself. If you run low on coding credit while building, tell us and we will provide a backup key. Keep every key on the server and out of Git.

## Follow the software development lifecycle

Build this the way professional teams do, moving through the lifecycle and tracking every stage on your ClickUp board.

1. **Requirements**: before you write code, write a short requirements note in docs/requirements.md. What must the app do, and what does done look like for each feature.
2. **Design**: draw an architecture diagram and save it in docs/architecture.md or as an image in docs. Show the pages, the back-end routes, the database tables, and where the AI calls happen.
3. **Build**: build the features in small, clear commits. Every piece of work has a ticket on your ClickUp board and moves across it.
4. **Test**: see the next section.
5. **Deploy**: ship to a live public URL.

## Test your app before you ship

Get a hands-on feel for testing, without going deep. Ask your teach-me agent for a short, plain explanation of what testing is and why it matters before you ship. Then check your own app: write a simple list of test cases covering your main features, what you do, what you expect, and what actually happens, and run through them. Record the results in TEST_SHEET.md as pass or fail. If you finish with time to spare, you can add one or two small automated checks on your own logic, but that is optional. You walk us through your test sheet when you present.

## Stack

- **Front-end and back-end**: Next.js with React and JavaScript. TypeScript is not required for this project.
- **Database and login**: Supabase. Postgres holds the data, and Supabase Auth handles sign-in. Use a real authentication system. Do not hand-roll password storage.
- **AI for the app**: an AI model API. TSS provides the API key for the app's AI features. Every AI call goes through your own back-end so the key stays on the server and never reaches the browser. Check the model's output before you save it, and handle the case where it returns something unexpected.
- **Google (optional bonus only)**: Google sign-in and the Google Drive API.
- **Deploy**: Vercel.

## Security, do not skip these

- Keep every secret in environment variables, never in the code and never committed. Your .env file stays in .gitignore.
- All AI calls happen on the server, so the key never reaches the browser.
- Use real authentication, and enforce access at the database. Turn on Supabase Row Level Security so the database itself only lets a user read and write their own tasks. Filtering in the front-end alone is not secure.
- Validate input before you send it to the AI or the database.
- Show loading and error states, especially around the AI calls, which can be slow or can fail.

## Repository structure

```
project-one/
  README.md            This brief. Read it, do not edit it.
  PRESENTATION.md      Your submission. All links, artifacts, and proof go here.
  LEARNING_LOG.md      One short wrap-up per skill you learn.
  TEST_SHEET.md        Your test cases and their outputs.
  skills/
    teach-me/SKILL.md       Your learning agent.
    troubleshoot/SKILL.md   Your troubleshooting agent.
  docs/
    requirements.md    Write your requirements here first.
    architecture.md    Put your architecture diagram here.
  proof/               Screenshots and any proof go here.
  web/                 Build your application here.
```

## What to submit and how to present

You present this project in three formats, plus your test sheet.

1. **Written**: fill in PRESENTATION.md with every link, artifact, and proof of learning, including a short summary of your test sheet.
2. **Video**: record a Loom walkthrough of the live app, the board, both AI features, and your repository. Add the link to PRESENTATION.md.
3. **Live**: schedule a call and present. Share your screen, demo the app live, walk through your code, and explain how it works. Expect questions on any function.

Also keep LEARNING_LOG.md updated as you go, and provide your completed TEST_SHEET.md.

## Definition of done

- [ ] Requirements written in docs/requirements.md
- [ ] Architecture diagram in docs/architecture.md
- [ ] Tasks: create, edit, complete, delete, all working
- [ ] Board with status columns the user can move tasks across
- [ ] Notes to task AI feature working, output checked before saving
- [ ] Transcript to action items AI feature working
- [ ] Login working, each user sees only their own tasks
- [ ] AI calls run on the back-end, key never exposed to the browser
- [ ] Database access restricted with Row Level Security so users reach only their own data
- [ ] Secrets in environment variables, .env kept out of Git
- [ ] App deployed to a live public URL
- [ ] TEST_SHEET.md complete with your main features checked, pass or fail
- [ ] Board tracked across the lifecycle stages as you worked
- [ ] Loom walkthrough recorded, link in PRESENTATION.md
- [ ] PRESENTATION.md and LEARNING_LOG.md complete
- [ ] TSS reviewer added as a collaborator on your repository
- [ ] Call scheduled
- [ ] Optional bonus: Google sign-in and reading a transcript from Google Drive working

---

*TSS Talent Lab | A Vertical of Tech Supersonic LLC | Confidential*
