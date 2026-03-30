# 🚀 GitHub Actions 

![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

## 📌 GitHub Actions Kya Hai?

**GitHub Actions** ek CI/CD (Continuous Integration / Continuous Deployment) platform hai jo aapke code ke saath automatically kaam karta hai. Jab bhi aap koi code push karte ho, PR banate ho, ya koi event hota hai — GitHub Actions automatically tasks run karta hai.

---

## 🧩 Key Concepts

### 1. **Workflow**
- `.github/workflows/` folder mein YAML file hoti hai
- Ek ya zyada jobs define karta hai
- Events pe trigger hota hai

### 2. **Event (Trigger)**
Workflow kab chalega:
- `push` — code push hone par
- `pull_request` — PR banane par
- `schedule` — cron job ki tarah
- `workflow_dispatch` — manually trigger

### 3. **Job**
- Ek workflow mein kai jobs ho sakte hain
- Parallel ya sequential chal sakte hain

### 4. **Step**
- Har job mein steps hote hain
- Commands ya actions run karte hain

### 5. **Action**
- Reusable units of code
- GitHub Marketplace se use kar sakte hain

---

## 📁 Folder Structure

```
your-repo/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── deploy.yml
├── src/
└── README.md
```

---

## 📝 Basic Workflow Example

```yaml
name: My First Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Code checkout karo
        uses: actions/checkout@v3

      - name: Node.js setup karo
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Dependencies install karo
        run: npm install

      - name: Tests run karo
        run: npm test
```

---

## 🔥 Common Use Cases

| Use Case | Description |
|----------|-------------|
| ✅ CI Testing | Har push par tests automatically run karo |
| 🚀 Auto Deploy | Code merge hote hi deploy ho jaye |
| 📦 Package Publish | npm/PyPI par automatically publish karo |
| 🔍 Code Linting | Code quality check karo |
| 📧 Notifications | Slack/Email pe alerts bhejo |
| 🏷️ Auto Labeling | PRs ko automatically label karo |

---

## 🛠️ Popular Actions (Marketplace)

```yaml
# Checkout
uses: actions/checkout@v3

# Node.js Setup
uses: actions/setup-node@v3

# Python Setup
uses: actions/setup-python@v4

# Docker Build & Push
uses: docker/build-push-action@v4

# Deploy to AWS
uses: aws-actions/configure-aws-credentials@v2
```

---

## 🔐 Secrets & Environment Variables

```yaml
steps:
  - name: Deploy karo
    env:
      API_KEY: ${{ secrets.MY_API_KEY }}
      NODE_ENV: production
    run: ./deploy.sh
```

> ⚠️ **Important:** Secrets ko GitHub → Settings → Secrets and Variables mein add karo

---

## 🔄 Workflow Triggers Examples

```yaml
# Sirf main branch par push hone par
on:
  push:
    branches: [main]

# PR open/update hone par
on:
  pull_request:
    branches: [main, develop]

# Roz raat 12 baje (cron)
on:
  schedule:
    - cron: '0 0 * * *'

# Manually trigger karo
on:
  workflow_dispatch:
```

---

## 📊 Jobs - Parallel & Sequential

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: npm test

  deploy:
    needs: test          # test complete hone ke baad chalega
    runs-on: ubuntu-latest
    steps:
      - run: npm run deploy
```

---

## 💡 Tips & Best Practices

- ✅ Secrets kabhi bhi code mein hardcode mat karo
- ✅ `actions/checkout@v3` hamesha pehle use karo
- ✅ Specific versions pin karo (e.g., `@v3` not `@latest`)
- ✅ `runs-on: ubuntu-latest` zyada tar cases mein best hai
- ✅ Workflow ko chhota aur focused rakho

---

## 📚 Resources

- [GitHub Actions Official Docs](https://docs.github.com/en/actions)
- [GitHub Marketplace](https://github.com/marketplace?type=actions)
- [Awesome GitHub Actions](https://github.com/sdras/awesome-actions)

---

## 🤝 Contributing

Pull requests welcome hain! Koi suggestion ho toh issue open karo.

---

⭐ **Agar helpful laga toh star do!**
