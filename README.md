## 🛟 HelpMe CLI

Turn plain-English requests into precise, copy‑pasteable shell commands.

### What you can do
- **One‑shot**: `helpme "<request>"` → prints a command, copies it to the clipboard, and exits.
- **Resume chat**: `helpme --interactive` (or run with no args) → ask follow‑ups; no auto‑copy; exit with Ctrl+C.

### 🚀 Install from GitHub (global)

```bash
# replace OWNER/REPO; optionally pin a ref with @main or @v0.1.0
npm install --global github:OWNER/REPO@main

# now run anywhere
helpme "use git to pull the latest changes"
helpme --interactive
```

### ▶️ Run via npx (GitHub)

```bash
# replace OWNER/REPO with your GitHub org/repo; optionally pin a branch or tag with @main
npx --yes github:OWNER/REPO helpme "use git to pull the latest changes"

# interactive/resume mode (no argv request)
npx --yes github:OWNER/REPO helpme --interactive
```

Notes:
- Requires **Node 18+**. The command downloads the repo tarball, installs deps in a temp dir, and runs the `helpme` bin.
- Configure providers via environment (export) or a `.env` in your current working directory before running npx.

### 🧑‍💻 Local install (dev)

```bash
cd helpme-cli
npm install
# optional: create a global symlink so `helpme` runs from any terminal
npm link
```

### 🕹️ Usage

```bash
# Single-turn (copies command and exits)
helpme "use git to pull the latest changes"

# Force interactive mode (no argv request)
helpme --interactive

# Options
helpme --no-copy              # skip clipboard (one‑shot only)
helpme --provider gemini      # force provider (gemini | ollama)
```

### 🔌 Unlink / remove the global command

```bash
# remove the global symlink created by `npm link`
npm unlink -g helpme-cli
```

If your terminal does not recognize `helpme` after linking, open a new terminal window or ensure your global npm bin is on PATH (e.g., `$(npm bin -g)`).

### ⚙️ Env / Config (root project dir)

Create a `.env` file in the directory where you run `helpme`:

```
HELPME_PROVIDER=gemini      # or: ollama
OLLAMA_BASE_URL=http://127.0.0.1:11434
HELPME_OLLAMA_MODEL=llama3.2
GOOGLE_API_KEY=...
GOOGLE_MODEL=gemini-2.5-flash  # or: gemini-1.5-pro
```

### ℹ️ Notes

- If misconfigured, HelpMe shows clear setup instructions on first run.
- To switch providers quickly per‑run:
  ```bash
  HELPME_PROVIDER=ollama HELPME_OLLAMA_MODEL=llama3.2 helpme "show current git branch"
  HELPME_PROVIDER=gemini GOOGLE_API_KEY=... helpme "create and checkout a branch named feature/login"
  ```


