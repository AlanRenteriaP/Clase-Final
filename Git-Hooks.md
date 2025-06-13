---
title: "Git Hooks — Tips & Tricks"
date: 2025-06-13
slug: git/hooks-tips-tricks
summary: "Best practices, examples, and advanced usage of Git Hooks to automate your workflow."
tags: [git, hooks, automation, pre-commit, tips, husky]
---

# 🧩 Git Hooks — Tips & Tricks

> 🚀 Automate tasks, prevent mistakes, and supercharge collaboration using Git hooks.

## 🔧 What are Git Hooks?
Git hooks are scripts triggered by Git actions (e.g., committing, pushing, merging). They live in `.git/hooks/`.

---

## 🛠️ Common Git Hooks and Use Cases

| Hook          | When it runs              | Typical Use Cases                      |
|---------------|---------------------------|----------------------------------------|
| `pre-commit`  | Before committing          | Linting, testing, formatting            |
| `commit-msg`  | After commit message typed| Enforce message format                 |
| `pre-push`    | Before `git push`         | Run tests, check secrets               |
| `pre-rebase`  | Before a rebase starts    | Warn or block risky rebases            |
| `post-merge`  | After a successful merge  | Auto install dependencies, notify team |

---

## 💡 Tips and Tricks

### ✅ 1. Make your hooks executable
```bash
chmod +x .git/hooks/pre-commit
```

### ✅ 2. Use `#!/bin/sh` at the top of hook scripts
Every hook should start with a proper shebang to execute reliably.

### ✅ 3. Avoid long scripts — call external scripts
Instead of putting all logic in the hook:
```bash
#!/bin/sh
npm run lint
```
This keeps your hooks clean and version-controlled.

### ✅ 4. Use environment-specific checks
Skip certain actions in CI:
```bash
#!/bin/sh
[ "$CI" = "true" ] && exit 0
```

### ✅ 5. Enforce commit message structure
Example `commit-msg`:
```bash
#!/bin/sh
MSG=$(cat $1)
if ! echo "$MSG" | grep -qE '^JIRA-\d+: .+'; then
  echo "⛔ Commit message must start with 'JIRA-<ID>:'"
  exit 1
fi
```

---

## 🧩 Bonus: Use Husky + lint-staged for better DX

### 🔧 Setup:
```bash
npm install husky --save-dev
npx husky install
npx husky add .husky/pre-commit "npm run lint"
```

### 🧼 With lint-staged:
```json
"lint-staged": {
  "*.js": ["eslint --fix", "git add"]
}
```
This only lint-fixes staged files and auto-adds them.

---

## 🧪 Advanced: Blocking secrets from commits
Use a `pre-commit` hook to scan for things like AWS keys:
```bash
#!/bin/sh
if grep -r 'AKIA[0-9A-Z]{16}' .; then
  echo "🔒 AWS key detected — aborting commit."
  exit 1
fi
```

---

## ❤️ Final Tips
- Always test your hooks with `echo` or dry-run commands.
- Don't use destructive commands (`rm`, `reset`) unless you're 100% sure.
- Document what your hooks do in your project README.

---

Test!