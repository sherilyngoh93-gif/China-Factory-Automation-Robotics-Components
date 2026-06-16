# Workflow Manual: GitHub + Claude Code + Claude Web

**Purpose:** This guide walks you through how to use GitHub as a file repository, convert PDF files to Markdown using Claude Code, and link Claude Web to your repository so you can chat with your documents.

---

## Table of Contents

1. [Setting Up a GitHub Repository](#1-setting-up-a-github-repository)
2. [Uploading Files to GitHub](#2-uploading-files-to-github)
3. [Linking Your Repository to Claude Web](#3-linking-your-repository-to-claude-web)
4. [Starting a Claude Code Session](#4-starting-a-claude-code-session)
5. [Converting PDFs to Markdown with Claude Code](#5-converting-pdfs-to-markdown-with-claude-code)
6. [Accessing Your Markdown Files in Claude Web](#6-accessing-your-markdown-files-in-claude-web)
7. [Tips & Best Practices](#7-tips--best-practices)

---

## 1. Setting Up a GitHub Repository

A **repository** (repo) is a folder on GitHub that stores all your files with version history.

### Steps

1. Go to [github.com](https://github.com) and sign in to your account.

   [SCREENSHOT: GitHub homepage with Sign In button highlighted]

2. Click the **+** icon in the top-right corner and select **New repository**.

   [SCREENSHOT: Top-right "+" dropdown menu with "New repository" option highlighted]

3. Fill in the repository details:
   - **Repository name**: Choose a descriptive name (e.g., `China-Factory-Automation-Robotics-Components`)
   - **Description**: Optional but recommended
   - **Visibility**: Choose `Public` (anyone can view) or `Private` (only you and invited collaborators)
   - Check **Add a README file** to initialize the repo

   [SCREENSHOT: New repository form filled out with the fields above]

4. Click **Create repository**.

   [SCREENSHOT: Newly created repository main page]

---

## 2. Uploading Files to GitHub

### Option A — Upload via GitHub Web Interface (no coding required)

1. On your repository page, click **Add file** → **Upload files**.

   [SCREENSHOT: Repository page with "Add file" dropdown showing "Upload files"]

2. Drag and drop your files (e.g., PDFs) into the upload area, or click **choose your files** to browse.

   [SCREENSHOT: Upload files page with files being dragged in]

3. Scroll down, add a short commit message (e.g., `Upload product PDF catalogues`), and click **Commit changes**.

   [SCREENSHOT: Commit changes section at the bottom of the upload page]

4. Your files now appear in the repository.

   [SCREENSHOT: Repository file list showing uploaded PDFs]

### Option B — Upload via Git (command line)

If you are comfortable with the terminal:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME
# Copy your files into this folder, then:
git add .
git commit -m "Upload PDF files"
git push origin main
```

---

## 3. Linking Your Repository to Claude Web

Claude Web (claude.ai/code) can connect directly to a GitHub repository so it can read, edit, and create files on your behalf.

### Steps

1. Go to [claude.ai/code](https://claude.ai/code) and sign in.

   [SCREENSHOT: Claude Code web landing page]

2. Click **New Session** or **Connect Repository**.

   [SCREENSHOT: Claude Code dashboard with "New Session" or "Connect Repository" button highlighted]

3. When prompted, select **GitHub** as your source and authorize Claude to access your account.

   [SCREENSHOT: GitHub authorization page asking for permissions]

4. Select the repository you want to work with (e.g., `China-Factory-Automation-Robotics-Components`).

   [SCREENSHOT: Repository selection dropdown or list]

5. Choose the branch to work on (default is `main`). Click **Start Session**.

   [SCREENSHOT: Branch selection and Start Session button]

6. Claude Code will clone your repository into a secure remote environment. You will see the session chat interface with your repo files accessible.

   [SCREENSHOT: Claude Code chat session open with repository connected]

---

## 4. Starting a Claude Code Session

Once your repository is linked, every new session you start will:

- Clone a fresh copy of your chosen branch
- Give Claude access to all files in the repo
- Allow Claude to create, edit, and commit files back to GitHub

### Key things to know

| Concept | What it means |
|---|---|
| **Branch** | A version of your repo. Work happens on a branch before being merged to `main`. |
| **Commit** | Saving a set of changes with a description message. |
| **Push** | Sending committed changes from the session back to GitHub. |
| **Main branch** | The primary branch — files here are what you see by default on GitHub and Claude Web. |

---

## 5. Converting PDFs to Markdown with Claude Code

Markdown (`.md`) files are plain text files with simple formatting. Converting your PDFs to Markdown makes them searchable and readable by Claude in future sessions.

### Steps

1. With your session open and your repo connected, type the following instruction in the chat:

   ```
   markitdown all my pdf files in this repo
   ```

   [SCREENSHOT: Claude Code chat with the above message typed]

2. Claude will automatically:
   - Find all `.pdf` files in the repository
   - Install any required tools
   - Convert each PDF to a `.md` file with the same name
   - Commit and push the new `.md` files to the branch

   [SCREENSHOT: Claude Code chat showing conversion progress and success messages]

3. Once done, Claude will confirm which files were created (e.g., `FA1.md`, `Hengli1.md`, `Robotics1.md`).

   [SCREENSHOT: Claude Code chat showing list of converted markdown files]

4. To make the files available on the `main` branch (so they appear by default), tell Claude:

   ```
   Merge these to main
   ```

   [SCREENSHOT: Claude Code chat confirming the merge and push to main]

5. Check your GitHub repository — the `.md` files will now appear alongside your PDFs.

   [SCREENSHOT: GitHub repository file list showing both .pdf and .md files]

---

## 6. Accessing Your Markdown Files in Claude Web

Once your `.md` files are on the `main` branch, you can start a new Claude Web session and interact with the document contents directly.

### Steps

1. Go to [claude.ai](https://claude.ai) and start a new conversation.

2. Use the **Attach** or **Add content** feature to reference files from your connected repository, or simply start a new Claude Code session (claude.ai/code) which will have access to all files.

   [SCREENSHOT: Claude Web new conversation with file attach option highlighted]

3. Ask Claude questions about your documents, for example:

   ```
   Summarise the key products in Hengli1.md
   ```

   ```
   Compare the specifications in FA1.md and FA2.md
   ```

   [SCREENSHOT: Claude Web chat showing a question and Claude's answer based on the markdown content]

---

## 7. Tips & Best Practices

### Keep PDFs and Markdown files together
Store both `.pdf` and `.md` versions in the same repository folder so everything stays organized.

### Re-run conversion when PDFs are updated
If you upload a new or updated PDF, start a new Claude Code session and ask it to convert the new file:
```
Convert NewFile.pdf to markdown
```

### Use descriptive file names
Good file names make it easier to ask Claude questions. For example:
- `Hengli-Cable-Catalogue-2024.pdf` is better than `Hengli1.pdf`

### Always work on main for visibility
Files pushed to other branches won't appear when you open the repo in a default Claude Web session. Always merge to `main` when the conversion is complete (Claude can do this for you).

### Branch naming
When Claude Code creates a working branch automatically (e.g., `claude/affectionate-allen-vek62i`), that is normal — it works on a separate branch for safety, then merges to `main` when you confirm.

---

*Last updated: June 2026*
