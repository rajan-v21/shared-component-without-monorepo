# Shared UI Component Library with Tailwind & shadcn (No Monorepo)

This guide explains how to create and consume a **shared UI component library** using **Tailwind CSS** and **shadcn/ui** without a monorepo, compatible with **Next.js 15**.

---

## Tech Stack

- Next.js 15
- Tailwind CSS
- shadcn/ui
- TypeScript
- Workspace-based dependency linking

---

## Project Structure

```txt
root/
├─ my-app/              # Main Next.js application
└─ shared-library/      # Shared UI component library

```

#Step 1: Create the Main App (my-app)

Create a Next.js app:
```
npx create-next-app@latest my-app
```
Tailwind Config Issue (Local Dev)
 *  In some local environments (e.g. VS Code), tailwind.config.ts may not be generated.

Workaround
  1. Create the Next.js app on StackBlitz
  2. Ensure tailwind.config.ts is generated
  3. Push it to GitHub
  4. Clone the repo to your local machine
