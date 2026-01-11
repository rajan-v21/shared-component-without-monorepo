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

# Step 1: Create the Main App (my-app)

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

# Step 2: Create the Shared Library (shared-library)

Create another Next.js app:
```
npx create-next-app@latest shared-library
```

When prompted:
* Use src/ directory? → Yes

Setup Tailwind
  1. Copy tailwind.config.ts from my-app to shared-library
  2. Install Tailwind dependencies:
```
cd shared-library
npm install -D tailwindcss postcss autoprefixer
```

# Step 3: Configure shadcn/ui in shared-library
Install shadcn/ui (Manual)

Follow the official guide:
https://ui.shadcn.com/docs/installation/manual

Update tsconfig.json
```
{
  "compilerOptions": {
    "baseUrl": "."
  }
}
```
Create Required Files & Folders
```
shared-library/
├─ components.json
├─ src/
│  ├─ styles/
│  │  └─ global.css
│  ├─ lib/
│  │  └─ utils.ts
│  ├─ components/
│  │  └─ ui/
```
Add shadcn Button Component
```
npx shadcn@latest add button
```
Export Components
`src/components/ui/index.ts`
```
export * from "./button"
```
Update Path Aliases
Change `tsconfig.json`

From:
```
{
  "paths": {
    "@/*": ["./src/*"]
  }
}
```

To:
```
{
  "paths": {
    "@/*": ["./*"]
  }
}
```
Create Root Export File
`src/index.ts`
```
export * from "./components/ui"
```
Important Notes
* Always use relative imports inside shared-library
* Update src/components/ui/button.tsx to use relative imports for utils.ts
