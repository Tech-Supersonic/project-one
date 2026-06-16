# Project One
## AI Task Workspace

*Created by TSS Talent Lab. Version 1.3.*

---

## Overview

In this project you build and deploy a working full-stack web application: an AI task workspace. Users sign up, sign in, manage tasks organised by category, and use AI to turn freeform notes and meeting transcripts into structured tasks. You follow the software development lifecycle from start to finish and verify everything works before you ship.

This project runs over one and a half to two weeks. One and a half weeks is the target; two weeks is the maximum. Everything lives in one GitHub repository.

**The rule**: use AI to build fast. But you must understand every line you ship. On your review call we will ask you to explain any function, any route, any database decision. If you cannot explain it, you do not own it yet. Go back and learn it with your teach-me agent first.

---

## Before you start

Confirm you have all of these before writing any code:

- [ ] Repository forked and cloned locally
- [ ] Node.js installed
- [ ] Supabase account and project created
- [ ] Vercel account created
- [ ] AI API key received from TSS
- [ ] ClickUp board set up with the lifecycle columns

---

## What you are building

### Authentication and profile

- Sign up with email and password
- Log in and log out
- Forgot password — user receives a reset email and sets a new password
- Change password from the profile page
- Update profile: display name
- Every user sees only their own data — enforced at the database with Row Level Security, not just in the frontend

### Tasks

Each task has:

| Field | Values |
|---|---|
| Title | Required text |
| Description | Optional text |
| Priority | Low / Medium / High |
| Status | To Do / In Progress / Done |
| Due date | Date picker |
| Category | Chosen from the user's own categories |

A user can create, edit, mark complete, and delete any of their tasks. They can filter the task list by category, priority, or status.

### Categories

- Create a category with a name
- Rename or delete a category
- Assign a task to a category when creating or editing
- View all tasks under a specific category

### Board

- Kanban board with three columns: To Do, In Progress, Done
- Move a task from one column to another
- Board and task list show the same data — they stay in sync

### AI: notes to task

- User types or pastes freeform text
- App sends it to the AI via a server-side route (key never leaves the server)
- AI returns one structured task: title, description, priority, due date
- User reviews the result and can edit before saving
- App handles the case where the AI returns something unexpected

### AI: transcript to action items

- User pastes a meeting transcript
- App sends it to the AI via a server-side route
- AI returns several action items, each with a title, an owner, and a due date
- Each item is saved as a task
- App handles the case where the AI returns something unexpected

### Optional bonus: Google Drive

If you finish the core with time to spare, let the user sign in with Google and read a meeting transcript directly from their Google Drive — no copy and paste. Only start this once the core is built, deployed, and fully working.

---

## Learn before you build

Use your teach-me agent on every skill listed below before you write code for it. Say: *"teach me [skill name]"* and work through the full sprint. Log your confidence score in LEARNING_LOG.md before moving on. This is not optional.

### 1. Next.js foundations
- **File-based routing** — how pages map to URLs, dynamic routes (`[id]`), nested routes
- **App Router** — layouts, `page.js` vs `layout.js`, loading states
- **Server vs client components** — when to use each and why it matters
- **API routes / Route Handlers** — how to write a server-side endpoint
- **Environment variables** — `.env.local`, what `NEXT_PUBLIC_` exposes, why secrets must stay on the server

### 2. React fundamentals
- **useState** — managing local component state
- **useEffect** — running code when something changes
- **Controlled forms** — connecting inputs to state
- **Conditional rendering** — showing different UI depending on state
- **Props** — passing data between components

### 3. Supabase and the database
- **Supabase project setup** — creating tables, using the dashboard
- **Postgres basics** — tables, columns, data types, primary keys, foreign keys
- **Supabase JS client** — querying, inserting, updating, deleting rows
- **Row Level Security (RLS)** — policies that stop users accessing each other's data — do not skip this
- **Relationships** — how tasks link to categories and to users

### 4. Authentication
- **Supabase Auth** — signup, login, logout, password reset email flow
- **Sessions** — how logged-in state persists between page loads
- **Protected routes** — redirecting unauthenticated users
- **Profile updates** — changing display name and password after sign-in

### 5. AI integration
- **Server-side API calls** — why the key must never go to the browser
- **Prompt design** — writing a prompt that reliably returns structured JSON
- **Parsing and validating AI output** — what to do when the model surprises you
- **Error handling** — loading states, timeouts, user-facing error messages

### 6. Deployment
- **Vercel setup** — connecting your GitHub repo, auto-deploy on push
- **Environment variables in Vercel** — setting them in the dashboard
- **Production vs development** — what changes when you go live

---

## Build order

Learn the skills first, then build. Do not start a phase until the previous one is working.

| Phase | What you build | Learn first |
|---|---|---|
| 1 | Auth: signup, login, logout, reset, profile | Supabase Auth, sessions, protected routes |
| 2 | Database schema: tasks, categories, profiles with RLS | Postgres basics, Supabase client, RLS |
| 3 | Task CRUD: create, edit, complete, delete, filter | React forms, API routes, Supabase queries |
| 4 | Categories: create, assign, filter | Relationships, Supabase queries |
| 5 | Board: kanban columns, move tasks | React state, conditional rendering |
| 6 | AI: notes to task | Prompt design, server routes, output validation |
| 7 | AI: transcript to action items | Same as phase 6 |
| 8 | Deploy to Vercel | Vercel setup, env vars in production |
| 9 | Bonus: Google Drive | Google OAuth, Drive API |

---

## Stack

| Layer | Technology |
|---|---|
| Frontend + backend | Next.js with React and JavaScript |
| Database + auth | Supabase (Postgres + Supabase Auth) |
| AI | API key provided by TSS — all calls go through your server |
| Deployment | Vercel |
| Bonus only | Google OAuth + Google Drive API |

---

## Security — do not skip

- All secrets in environment variables — never in code, never committed
- `.env.local` is in `.gitignore` — verify this before your first push
- All AI calls happen server-side — the key never reaches the browser
- Row Level Security on every table — test that a user cannot access another user's rows
- Validate all input before sending to the AI or the database
- Show loading and error states on every AI call

---

## How to use your agents

**teach-me** (`skills/teach-me/SKILL.md`)
Say *"teach me [skill]"* before each phase. Work through all five steps — do not skip the break-it step. Log your score in LEARNING_LOG.md.

**troubleshoot** (`skills/troubleshoot/SKILL.md`)
When something breaks, come here before guessing. Paste the exact error message. Work through the steps — do not ask for the fix.

---

## Test before you ship

Write a test case in TEST_SHEET.md for every main feature: what you do, what you expect, what actually happened. Run through them all and record pass or fail. Walk us through your sheet on the review call.

---

## What to submit

1. **Written** — complete PRESENTATION.md with every link, artifact, and proof
2. **Video** — Loom walkthrough of the live app, both AI features, your board, your repository
3. **Live call** — demo the app, walk through your code, explain every decision

---

## Definition of done

- [ ] Requirements written in docs/requirements.md
- [ ] Architecture diagram in docs/architecture.md
- [ ] Sign up, log in, log out working
- [ ] Forgot password and reset flow working
- [ ] Change password and update profile working
- [ ] Tasks: create, edit, complete, delete working
- [ ] Categories: create, assign, filter working
- [ ] Board with columns and task movement working
- [ ] Notes to task AI feature working, output validated before saving
- [ ] Transcript to action items AI feature working
- [ ] All AI calls run server-side — key never in the browser
- [ ] Row Level Security on all tables — tested, not assumed
- [ ] All secrets in environment variables, .env.local out of Git
- [ ] App deployed to a live public URL
- [ ] TEST_SHEET.md complete with all main features checked
- [ ] LEARNING_LOG.md updated after every skill
- [ ] ClickUp board tracked across all lifecycle stages
- [ ] Loom recorded and linked in PRESENTATION.md
- [ ] PRESENTATION.md complete
- [ ] TSS reviewer added as collaborator
- [ ] Review call scheduled
- [ ] Optional bonus: Google sign-in and Drive transcript reading working

---

*TSS Talent Lab | A Vertical of Tech Supersonic LLC | Confidential*
