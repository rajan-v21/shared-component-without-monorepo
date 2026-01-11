# shared component using tailwind and shadcn without monorepo
NOTE: This setup is as per nextjs 15.

Step 1: Create next.js app.
  Note - Local dev (vs code) might not generate "tailwind.config.ts" file.
  Solution - a) Create Next.js app on Stackblitz
            b) this generates "tailwind.config.ts"
            c) create repo of it on github and clone it on local environment.


Step 2: Create another app "shared-library" on local environment and while choosing option to create app,
  For option - "inside 'src/directory'" choose "yes".
  a) copy tailwind file from previous app to shared-library.
  b) then in terminal run 'cd shared-library'.
  c) then do 'npm install -D tailwindcss postcss autoprefixer'

Step 3: Now tailwind is in your shared-library
  a) Install shadcn manually from [shadcn](https://ui.shadcn.com/docs/installation/manual) 
  b) In tsconfig.json add 
        "compilerOptions": {
          ...
          "baseUrl": ".",
          ...
        },
  c) In `src/styles/` create `global.css`
