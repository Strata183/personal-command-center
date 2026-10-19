# Personal Command Center

A dark-green and cream personal dashboard for projects, tasks, and daily priorities.

## Current features
- Add, edit, complete, and delete tasks
- Organize tasks by life area
- Set priority and optional due date
- Search tasks and filter by area
- Save tasks in this browser using localStorage

## Run locally
1. Install Node.js LTS from https://nodejs.org/
2. Open Terminal and move into this folder: `cd personal-command-center`
3. Install dependencies: `npm install`
4. Start the development server: `npm run dev`
5. Open the local URL printed by Vite (usually `http://localhost:5173`).

## Storage note
This first version stores tasks in this browser profile. It does not sync between computers or browsers. Before using it for private data, the next step is to add Supabase authentication and row-level security.
