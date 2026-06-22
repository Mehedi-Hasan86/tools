# TaskSwift ⚡️

TaskSwift is a local-first, lightweight, and blazing-fast task management application built with React 19, Vite, Tailwind CSS v4, and TypeScript. 

It keeps all task data strictly within your browser's local storage—ensuring zero remote server latency and maximum privacy. The project also utilizes [vite-plugin-singlefile](https://github.com/richardtallent/vite-plugin-singlefile) to bundle the entire application (HTML, JS, CSS) into a **single, standalone HTML file** for easy sharing and offline usage.

---

## ✨ Features

- **⚡ Local-First & Instant**: All tasks are saved locally on the client using browser storage (`localStorage`). No sign-ups, no databases, no server delays.
- **📦 Single-File Bundle**: Compiles into a single portable `.html` file that runs in any modern browser without external dependencies.
- **🎨 Modern Slate Design**: Features a beautiful and minimal dark mode styled using Tailwind CSS v4.
- **📱 Fully Responsive**: Optimized layout that scales seamlessly from small mobile screens to large desktop monitors.

---

## 🛠️ Tech Stack

- **Framework**: [React 19](https://react.dev/)
- **Build Tool**: [Vite 7](https://vite.dev/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Bundler Plugin**: [vite-plugin-singlefile](https://github.com/richardtallent/vite-plugin-singlefile)

---

## 📂 Project Structure

Below is the directory structure of the application. Click the file links to view the source code:

- 📂 [**root**](./)
  - 📄 [package.json](./package.json) — Defines dependencies and build scripts.
  - 📄 [vite.config.ts](./vite.config.ts) — Configures Vite, including React and single-file bundling.
  - 📄 [tsconfig.json](./tsconfig.json) — TypeScript configurations.
  - 📄 [.gitignore](./.gitignore) — Configures git to ignore files like node_modules.
  - 📄 [index.html](./index.html) — HTML template entry point.
  - 📂 [src](./src)
    - 📄 [main.tsx](./src/main.tsx) — Main React entry point mounting the app.
    - 📄 [App.tsx](./src/App.tsx) — Main application logic, UI, and local storage state.
    - 📄 [index.css](./src/index.css) — Custom styles injecting Tailwind directive.
    - 📂 utils
      - 📄 [cn.ts](./src/utils/cn.ts) — Tailored class merges via `clsx` and `tailwind-merge`.

---

## 🔍 Code Walkthrough

### Core Component Structure

The app is centered around a single React component, [App](./src/App.tsx#L41). Here is a breakdown of its internal functions and types:

1. **[Task](./src/App.tsx#L3-L7)**: TypeScript representation of a task object.
   ```typescript
   type Task = {
     id: number;
     title: string;
     createdAt: number;
   };
   ```
2. **[loadTasks()](./src/App.tsx#L11-L39)**: A validation-safe helper function to fetch tasks from `localStorage` on initial load.
3. **Task State and Hooks**:
   - `tasks`: Loaded dynamically using `loadTasks()`, and synced with storage on changes via `useEffect`.
   - `taskTitle`: Holds the active title input.
   - `taskCountText`: Formatted dynamic label using `useMemo` for optimization.
4. **Utility [cn](./src/utils/cn.ts#L4)**: A utility merging helper ensuring Tailwind style conflicts resolve gracefully.

---

## 🚀 Getting Started

### 📋 Prerequisites

To run this project, make sure you have [Node.js](https://nodejs.org/) installed (v18+ recommended).

### ⚙️ Installation

Install all required dependencies:

```bash
npm install
```

### 💻 Development

Start the hot-reloading development server:

```bash
npm run dev
```

The application will run locally at `http://localhost:5173`.

### 📦 Production Build

Compile the application for production:

```bash
npm run build
```

This command runs `vite build`, producing a single, self-contained HTML file in the `dist` folder. You can double-click this file or host it on any static web host!
