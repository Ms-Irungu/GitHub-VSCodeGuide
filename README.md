# 🚀 GitHub + VS Code Setup Guide (with GitHub CLI)

This guide will walk you through the **entire process** of setting up GitHub CLI (`gh`), connecting **multiple GitHub accounts** (personal + company), cloning repositories, configuring authorship, and working in **Visual Studio Code**.

---

## 📌 Prerequisites
Before starting, ensure you have:
- **VS Code** installed
- **Git** installed → check with:
  ```bash
  git --version
  ```
- A **GitHub account** (personal and/or company)

---

## 🔧 Step 1: Install GitHub CLI (`gh`)

### Windows

1. Go to [https://cli.github.com/](https://cli.github.com/)
2. Download the latest `.msi` installer
3. Run installer → it adds `gh` to PATH
4. Verify:

   ```bash
   gh --version
   ```

### macOS

```bash
brew install gh
gh --version
```

### Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install gh
gh --version
```

✅ If a version prints, installation worked.

---

## 🔑 Step 2: Authenticate Accounts

You can log in with **both accounts** separately.

### Personal Account

```bash
gh auth login
```

* Select: `GitHub.com`
* Protocol: `HTTPS`
* Authenticate Git with credentials? → `Yes`
* Authentication method → `Login with browser`
* Copy code → paste in browser → log into **personal GitHub**

### Company Account

Run again:

```bash
gh auth login
```

Repeat process → but use **company GitHub account**.

---

## 🧾 Step 3: Verify Accounts

Check which accounts are connected:

```bash
gh auth status
```

You’ll see both accounts listed. One will be **active**.

---

## 📂 Step 4: Clone a Repository

### Choose Location

On Windows, switch drive and folder:

```powershell
D:
mkdir D:\GitHubRepos
cd D:\GitHubRepos
```

### Clone Repo

Switch to correct account first:

```bash
gh auth switch
```

Clone: (Acquire the links from the GitHub Repository )

```bash
gh repo clone Ms-Irungu/Pata-Places
cd event
```

Or via HTTPS:

```bash
git clone https://github.com/Ms-Irungu/Pata-Places.git
cd Pata-Places
```

---

## 🖊 Step 5: Configure Commit Authorship

🔹 This ensures commits show up under the **correct GitHub account**.
There are two levels:

### Global Default (fallback)

🔹 This is your personal identity and is used everywhere unless overridden.

```bash
git config --global user.name "Your Name"
git config --global user.email "personal@email.com"
```

### Per Repository (recommended)

Inside **personal repo**:

```bash
git config user.name "PersonalUsername"
git config user.email "personal@email.com"
```

Inside **company repo**:

```bash
git config user.name "CompanyUsername"
git config user.email "company@email.com"
```

Check:

```bash
git config user.name
git config user.email
```

#### 🧠 How Git Decides (Global vs Local)

- Git always checks local repo config first (.git/config)

- If none is set → it falls back to global config (~/.gitconfig)

- If none is set globally → it uses system defaults

#### ✅ Best practice:

- Use `global config` for `personal account (set once)`.

- Use `local overrides` only for `work/company repos`.

---

## 🖥 Step 6: Open Repo in VS Code

From inside the repo folder:

```bash
code .
```

If `code .` doesn’t work:

* In VS Code, run:
  `Ctrl + Shift + P` → search **“Shell Command: Install 'code' command in PATH”** → hit Enter.

---

## 🔄 Step 7: Everyday Workflow

1. Navigate to repo folder:

   ```bash
   cd D:\GitHubRepos\project-name
   ```
2. Confirm active account:

   ```bash
   gh auth status
   ```

   Switch if needed:

   ```bash
   gh auth switch
   ```
3. Confirm correct identity:

   ```bash
   git config user.email
   ```
4. Open in VS Code:

   ```bash
   code .
   ```
5. Work normally:

   ```bash
   git add .
   git commit -m "Your commit message"
   git push
   ```

---

## ⚡ 5-Second Checklist (Before You Start Work)

✅ Navigate to correct folder (`cd project`)
✅ Check `gh auth status`
✅ Switch account if needed (`gh auth switch`)
✅ Confirm email (`git config user.email`)
✅ Open with `code .`

---

## 🛠 Troubleshooting

* **`gh not recognized`** → Restart VS Code, check PATH
* **`repo not found`** → Accept invitation if invited to a private repository.
* **Wrong commits under wrong account** → Fix with `git config user.email`
* **Auth failed** → Run `gh auth switch` and retry

---

## 📌 Useful GitHub CLI Commands

```bash
gh auth login            # log in with account
gh auth status           # check connected accounts
gh auth switch           # switch active account
gh repo clone owner/repo # clone repo
gh repo create           # create new repo
gh issue list            # list issues
gh pr create             # create pull request
```

---

## ✅ Example Full Session

```powershell
# move to drive
D:
mkdir D:\GitHubRepos
cd D:\GitHubRepos

# check gh
gh --version
gh auth status
gh auth switch  # pick correct account

# clone repo
gh repo clone 612teres/event
cd event

# set authorship
git config user.name "Valentine Irungu"
git config user.email "personal@email.com"

# open in VS Code
code .

# work as usual
git status
git add .
git commit -m "Initial commit"
git push
```

---

🎉 Done! You can now safely work with **both personal & company GitHub accounts** inside VS Code using GitHub CLI.

```

---

Would you like me to also add a **diagram of the workflow** (Accounts ↔ Repo ↔ VS Code) in ASCII/Markdown style so it’s easier to visualize?
```
