# Personal Command Center

A dark-green and cream personal dashboard for projects, tasks, and daily priorities.

## Current features
- Add, edit, complete, and delete tasks
- Organize tasks by life area
- Set priority and optional due date
- Search tasks and filter by area
- Load signed-in users' tasks from the Supabase `tasks` table

## Run locally
1. Install Node.js LTS from https://nodejs.org/
2. Open Terminal and move into this folder: `cd personal-command-center`
3. Install dependencies: `npm install`
4. Start the development server: `npm run dev`
5. Open the local URL printed by Vite (usually `http://localhost:5173`).

## Use it as Chrome's New Tab page
The project includes a Manifest V3 extension that opens the dashboard whenever you create a new tab.

1. Build the extension with `npm run build:extension`.
2. In Chrome, open `chrome://extensions` and turn on **Developer mode**.
3. Choose **Load unpacked** and select this project's `dist` folder.
4. Open a new tab to see the dashboard.

To continue development, edit the app as usual, run `npm run build:extension`, then choose **Reload** for the extension on `chrome://extensions`. The Vite development server still works for ordinary web development; its page does not replace New Tab.

For Supabase email confirmation links in the extension, copy the extension ID from `chrome://extensions` and add `chrome-extension://<extension-id>` to the Supabase project's Authentication URL Configuration allowlist. The extension uses the project's public Supabase URL and publishable key from `.env.local`; never place a Supabase service-role key in the extension.

## Supabase task loading
The dashboard reads rows from the `tasks` table for the signed-in user's `user_id`. The current table uses `id`, `user_id`, `title`, `project`, `due_date`, `priority`, and `is_complete`. The dashboard maps `project` to its life-area filter. If an account has no tasks, the app creates four starter tasks for that user. Supabase row-level security should restrict reads and writes to the authenticated user's rows.

Adding, editing, completing, and deleting tasks writes to the same table. Inserts set `user_id` to the signed-in user, and update/delete requests are scoped to that user. Database policies should still enforce these rules through row-level security.
