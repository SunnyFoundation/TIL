

## What is Node.js?

- **Node.js** is a JavaScript runtime environment.  
- It allows you to run JavaScript **anywhere and everywhere**.

---

## What is `package.json`?

- Acts as the **manifest** or "menu" of your project.  
- Main roles:  
  - Lists the **frameworks and libraries** your project depends on.  
  - Defines common scripts/commands like `npm start`, `npm test`.

---

## What is `node_modules`?

- A folder where all the **installed libraries and frameworks** are stored.  
- Roles:  
  - When you run `npm install`, it installs packages listed in `package.json` here.  
  - When you use `require` or `import` in your code, Node.js looks for modules in this folder.  
- **Important:** Usually not uploaded to GitHub due to its large size.

---

## What is `package-lock.json`?

- A file that records the **exact versions** of installed libraries.  
- Role:  
  - Prevents version conflicts and ensures a consistent environment across installs.

---
