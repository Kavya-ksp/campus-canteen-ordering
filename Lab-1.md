# Lab 1 — Git and GitHub Repository Fundamentals

**Case study:** Campus Canteen Ordering System  
**Suggested duration:** 60–75 minutes  
**Level:** Beginner  
**Tools:** Git, GitHub Repositories, a terminal, and a text editor (Visual Studio Code is recommended but optional)

---

## 1. Lab overview

In this lab, you will create a GitHub repository for a Campus Canteen Ordering System, copy it to your computer, update project documentation, save changes with Git, create a feature branch, push that branch to GitHub, and inspect the project's change history.

This is the foundation for the next labs. In Lab 2, you will gather requirements and plan work with GitHub Discussions, Issues, and Projects. In Lab 3, you will submit and review a pull request. **Do not delete this repository or the branch created in this lab**, because you can reuse them in later labs.

### Scenario

A college wants to make ordering food from its campus canteen easier. Students should eventually be able to view the menu, select food items, place orders, and check their order status. Canteen staff should be able to manage menu availability and process orders.

For this lab, you are not building the application yet. You are setting up the project's repository and learning the version-control workflow that a development team uses to manage code and documentation.

### Learning objectives

By the end of this lab, you should be able to:

1. Explain the difference between Git and GitHub.
2. Create and navigate a GitHub repository.
3. Clone a remote repository to a local computer.
4. Use `git status`, `git add`, `git commit`, `git log`, and `git diff`.
5. Create a branch, make a change, and push the branch to GitHub.
6. Inspect repository files, branches, commits, and history on GitHub.com.

---

## 2. What you need before starting

### Required

- A GitHub account that you can sign in to: <https://github.com/>
- Git installed on your computer.
- Internet access.
- Permission to create a repository in your personal GitHub account, or permission from your instructor to use a classroom organization.
- A terminal:
  - **Windows:** PowerShell or Git Bash.
  - **macOS:** Terminal.
  - **Linux:** your preferred terminal.
- A text editor. Visual Studio Code is recommended: <https://code.visualstudio.com/>. Notepad, TextEdit in plain-text mode, or another code editor is also suitable.

### Recommended

- Use a computer where you can create folders and edit files.
- Keep the lab folder in a location you can find easily, such as `Documents` or a development folder.
- If this is a classroom exercise, use the same GitHub repository in Labs 2 and 3.

### Verify Git is installed

Open your terminal and run:

```bash
git --version
```

**Expected result:** a version number, for example `git version 2.x.x`.

If your terminal says that `git` is not recognized or not found, install Git from <https://git-scm.com/downloads>, then close and reopen the terminal and run the command again.

### Configure your Git identity

Git records a name and email address in each commit. These are commit metadata; the Git name is not necessarily the same as your GitHub username. Configure them before making your first commit.

Replace the example name and email below with the name and email you want associated with your commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Verify the settings:

```bash
git config --global user.name
git config --global user.email
```

**Privacy note:** commit email addresses may be visible to people who can view the repository. If you prefer not to expose your personal email, check the email/privacy settings in your GitHub account and use the GitHub-provided `noreply` email address where appropriate. Do not use another person's identity.

---

## 3. Step 1 — Create a GitHub repository

A **repository** is the project space that stores files and their version history. Git is the version-control tool. GitHub hosts Git repositories online and adds collaboration features around them.

### 3.1 Sign in to GitHub

1. Open <https://github.com/>.
2. Sign in to your account.
3. Confirm that you can access the home page.

### 3.2 Create the repository

1. Select the **+** menu near the upper-right area of GitHub, then choose **New repository**. Depending on the current interface, you may also find a **New** option on the repositories page.
2. For **Repository name**, enter:

   `campus-canteen-ordering-lab1`

3. For the description, enter:

   `Software Engineering lab project for a Campus Canteen Ordering System.`

4. Choose the repository visibility:
   - **Private** is a good default for a classroom team or a project that is not intended to be public.
   - **Public** is acceptable for a demonstration project containing no personal, confidential, or sensitive information.
5. Select **Add a README file**. This creates an initial commit and makes the repository easier to clone and use in the next step.
6. You can leave `.gitignore` and license options unselected for this documentation-focused lab. They can be introduced when the project has a programming language and licensing decision.
7. Select **Create repository**.

**Expected result:** GitHub opens your repository page. You should see `README.md` and the initial commit.

### 3.3 Record your repository URL

On the repository page, select **Code**, choose **HTTPS**, and copy the repository URL. It should look similar to:

```text
https://github.com/YOUR-USERNAME/campus-canteen-ordering-lab1.git
```

Use the actual URL shown for your repository. `YOUR-USERNAME` is a placeholder; do not type it literally.

**Checkpoint 1:** You have a repository on GitHub, and it contains a README file.

---

## 4. Step 2 — Clone the repository to your computer

**Clone** means downloading a working copy of the repository, including its existing Git history, to your computer.

### 4.1 Open a terminal in a suitable location

Choose a folder where you want to keep your labs. For example, you can navigate to `Documents` using your operating system's file manager and open a terminal there. You can also use `cd` to move to your preferred directory.

For example, this command moves to a folder named `Documents` under your home directory on common Windows Git Bash, macOS, and Linux setups:

```bash
cd ~/Documents
```

If that location does not exist or you prefer another location, use your own working directory.

### 4.2 Clone the repository

Run the following command, replacing the URL with the one you copied from your GitHub repository:

```bash
git clone https://github.com/YOUR-USERNAME/campus-canteen-ordering-lab1.git
```

Enter the project directory:

```bash
cd campus-canteen-ordering-lab1
```

If the command ran successfully, Git created a local folder containing the project files.

### 4.3 Explore the local repository

Run these commands one at a time:

```bash
git status
git branch --show-current
git remote -v
```

What they mean:

- `git status` shows the current branch and whether files have changed.
- `git branch --show-current` shows the branch you are working on, usually `main` for a new GitHub repository.
- `git remote -v` shows the online repository address, normally named `origin`.

**Expected result:** the working tree is clean, the current branch is usually `main`, and `origin` points to your GitHub repository.

### Optional: open the folder in Visual Studio Code

If VS Code is installed and its `code` command is available, run:

```bash
code .
```

If this command is unavailable, open VS Code normally and choose **File → Open Folder**, then select `campus-canteen-ordering-lab1`.

**Checkpoint 2:** You have a local copy of the GitHub repository, and `git remote -v` displays the online repository URL.

---

## 5. Step 3 — Update the README and add a project overview

The `README.md` file is normally the first document people see when they open a repository. Use it to explain what the project is, why it exists, and what the repository contains.

### 5.1 Update `README.md`

Open the existing `README.md` in your editor and replace its contents with the following. Save the file.

```markdown
# Campus Canteen Ordering System

## Project Overview

The Campus Canteen Ordering System is a proposed application intended to make
food ordering in a college canteen more convenient for students and staff.

## Problem Statement

Students may need to wait in a queue to check the menu, place an order, and
find out whether their food is ready. The proposed system aims to make these
activities easier to manage.

## Intended Users

- Students: view menu items and place orders.
- Canteen staff: manage menu availability and process orders.
- Administrator: maintain menu information and system settings.

## Initial Scope

The initial project will explore these capabilities:

1. View available menu items and prices.
2. Select menu items and quantities.
3. Calculate an order total.
4. Submit an order.
5. View an order's status.

Payment integration and advanced inventory management are outside the initial
scope and may be considered later.

## Repository Contents

- `README.md` — project introduction.
- `docs/PROJECT-OVERVIEW.md` — initial context, goals, users, and scope.

## Project Status

Planning and documentation stage. Requirements will be gathered and recorded
before application development begins.
```

### 5.2 Add `docs/PROJECT-OVERVIEW.md`

Create a folder named `docs` inside the repository if it does not already exist. Inside it, create a file named `PROJECT-OVERVIEW.md`.

Paste the following contents and save the file:

```markdown
# Campus Canteen Ordering System — Project Overview

## Background

The college canteen serves students and staff during breaks. Manual ordering
can result in queues and uncertainty about menu availability and order status.

## Project Goal

Explore a simple digital ordering process that helps students choose available
food items and helps canteen staff manage incoming orders.

## Stakeholders

- Students who browse the menu and place orders.
- Canteen staff who prepare orders and update their status.
- College administration that oversees the canteen service.
- The student development team that designs, implements, and tests the system.

## Initial Scope

The first version will focus on menu viewing, order preparation, total
calculation, order submission, and status tracking.

## Out of Scope for the Initial Version

- Real payment gateway integration.
- Delivery outside the campus.
- Advanced stock forecasting.
- Integration with external accounting systems.

## Assumptions to Validate

- Students need to view item names, prices, and availability.
- Canteen staff need to see incoming orders.
- The college will define the final order cancellation policy.
- Performance and security targets must be agreed with stakeholders.

## Open Questions

- Will students need to sign in?
- Can an order be cancelled after submission?
- How should staff mark an order as ready?
- Which devices must the system support?
```

### 5.3 Review the changes before saving them in Git

Return to the terminal and run:

```bash
git status
git diff
```

Look at the output:

- `git status` should show `README.md` as modified and `docs/PROJECT-OVERVIEW.md` as untracked.
- `git diff` shows changes to tracked files, such as `README.md`. It will not show the contents of a new, untracked file until you stage it.

This is your first opportunity to distinguish the **working directory** (where you edit files) from the **repository history** (what has been committed).

**Checkpoint 3:** The README is updated, and the new project overview document exists in `docs`.

---

## 6. Step 4 — Stage and commit the changes

Git lets you decide exactly which changes should be included in a commit. The process is commonly described as **working directory → staging area → commit**.

### 6.1 Check the status

```bash
git status
```

Read the output before proceeding. Confirm that the intended files are listed.

### 6.2 Stage only the files for this task

```bash
git add README.md docs/PROJECT-OVERVIEW.md
```

Staging selects these file changes for the next commit. It does not upload anything to GitHub yet.

Check what is staged:

```bash
git status
git diff --staged
```

`git diff --staged` displays the changes that will be included in the commit. Check that the file contents are correct and that you have not staged unrelated files.

### 6.3 Create a commit

```bash
git commit -m "docs: add campus canteen project overview"
```

A **commit** is a saved snapshot in Git history. The message should explain the purpose of the change.

**Expected result:** Git reports that a commit was created and lists the changed files.

### 6.4 Inspect the commit

```bash
git log --oneline --decorate -5
git show --stat --oneline HEAD
```

You should see your new commit near the top of the log. The first part of the commit ID identifies the snapshot; the message explains its purpose.

### 6.5 Push your commit to GitHub

```bash
git push
```

If Git asks you to authenticate, follow the browser or Git Credential Manager sign-in prompt if offered. GitHub account passwords are not accepted for Git operations over HTTPS. Do not paste credentials or access tokens into a shared terminal, a source file, or a screenshot.

If `git push` reports that no upstream is configured, use the current branch name shown by `git branch --show-current`. For a newly cloned repository whose current branch is `main`, this command will normally be:

```bash
git push -u origin main
```

**Expected result:** the latest commit is now visible on the GitHub repository page.

### 6.6 Compare local and remote state

Run:

```bash
git status
```

You should see a message similar to `nothing to commit, working tree clean`. After a successful push, your local branch and its configured remote branch should be synchronized.

**Checkpoint 4:** The README and project overview changes have been committed and pushed to GitHub.

---

## 7. Step 5 — Create a feature branch

Branches let developers work on a change separately from the main line of development. In this step, you will add a short document describing the different users of the canteen system.

### 7.1 Confirm you are on the main branch

```bash
git branch --show-current
```

For this lab, the expected branch is `main`. If you are on another branch, switch to `main` before proceeding:

```bash
git switch main
```

Then make sure your local branch is up to date:

```bash
git pull
```

### 7.2 Create and switch to a new branch

Run:

```bash
git switch -c docs/add-user-roles
```

This creates the branch and switches your working directory to it.

Verify the current branch:

```bash
git branch --show-current
```

Expected output:

```text
docs/add-user-roles
```

List local branches:

```bash
git branch
```

The asterisk (`*`) identifies the branch currently checked out. Your `main` branch still exists; you have not replaced it.

### 7.3 Create a user-roles document on the branch

In the `docs` directory, create `USER-ROLES.md` and add:

```markdown
# User Roles — Campus Canteen Ordering System

## Student

- View available menu items and prices.
- Select menu items and quantities.
- Review the order total before submitting an order.
- View the status of their own orders.

## Canteen Staff

- View incoming orders.
- Review the items and quantities in an order.
- Update an order's preparation status.
- Mark an order as ready when preparation is complete.

## Administrator

- Maintain menu item names, prices, and availability.
- Manage appropriate user access.
- Review system-level configuration.

## Notes

These roles are initial assumptions for discussion. The final permissions and
workflows must be confirmed during requirements elicitation.
```

Save the file.

### 7.4 Inspect, stage, and commit the branch change

```bash
git status
git diff
```

Because `docs/USER-ROLES.md` is a new, untracked file, `git diff` may not display the file contents yet. Stage it, then inspect the staged change:

```bash
git add docs/USER-ROLES.md
git status
git diff --staged
```

Commit the change:

```bash
git commit -m "docs: add campus canteen user roles"
```

Inspect the branch's history:

```bash
git log --oneline --decorate -5
```

### 7.5 Push the feature branch to GitHub

```bash
git push -u origin docs/add-user-roles
```

The `-u` option sets the upstream remote branch so that future pushes and pulls on this branch can usually use the shorter commands `git push` and `git pull`.

**Expected result:** Git reports that the branch was pushed to `origin`. On GitHub, you should be able to select `docs/add-user-roles` from the branch selector and view `docs/USER-ROLES.md`.

**Important:** Do not merge this branch as part of Lab 1. The next lab and Lab 3 may reuse the repository, and Lab 3 will cover pull requests and reviews.

**Checkpoint 5:** The new user-roles document is committed on a separate branch and the branch is visible on GitHub.

---

## 8. Step 6 — Explore Git history and compare changes

This step explores the GitHub interface as well as Git commands. You will inspect the commits and compare the feature branch with `main`.

### 8.1 Explore the repository on GitHub.com

1. Open your repository on GitHub.
2. On the **Code** tab, confirm that `README.md` and the `docs` folder are visible.
3. Open `docs/PROJECT-OVERVIEW.md` and review its content.
4. Open `docs/USER-ROLES.md`. If you cannot see it while `main` is selected, use the branch selector to switch to `docs/add-user-roles`.
5. Find the commit history. Depending on the current GitHub interface, you can select the commit count/history link or open the repository's commits page. Review the commit messages and authors.

### 8.2 Compare branches in the GitHub interface

1. Open the repository's **Code** page.
2. Open the branch selector and confirm that both `main` and `docs/add-user-roles` exist.
3. Open the repository's compare view. A typical URL pattern is:

   `https://github.com/YOUR-USERNAME/campus-canteen-ordering-lab1/compare/main...docs/add-user-roles`

   Replace `YOUR-USERNAME` with the account or organization that owns the repository. You can also navigate to the compare view through GitHub's interface.
4. Make sure `main` is the base branch and `docs/add-user-roles` is the comparison branch.
5. Inspect the commit list and the **Files changed** view.

You should find that the feature branch adds `docs/USER-ROLES.md`, while `main` does not contain that file yet. Comparing branches shows the changes that exist in one branch but not the other.

### 8.3 Explore the same history from the terminal

Return to your terminal and run:

```bash
git branch -a
git log --oneline --graph --decorate --all -10
git diff main...docs/add-user-roles --
```

What these commands do:

- `git branch -a` lists local and remote-tracking branches.
- `git log --oneline --graph --decorate --all -10` displays a compact view of recent history across branches.
- `git diff main...docs/add-user-roles --` displays the changes introduced on the feature branch relative to its common starting point with `main`.

If you have not fetched remote branches after another participant or computer updated the remote repository, use `git fetch origin` and rerun the branch listing. In this single-user lab, the branch should already be available after you pushed it.

### 8.4 Observe the final state

Run:

```bash
git status
git branch --show-current
```

You should still be on `docs/add-user-roles`, and the working tree should be clean. The main branch remains unchanged by the feature-branch commit because the branch has not been merged.

**Checkpoint 6:** You can locate commits on GitHub, switch branches, and compare the feature branch to `main`.

---

## 9. Essential Git commands reference

| Command | Purpose |
|---|---|
| `git --version` | Verify that Git is installed. |
| `git config --global user.name "Your Name"` | Set the name recorded in future commits. |
| `git clone <URL>` | Copy a remote repository to your computer. |
| `git status` | Show the current branch and file-change status. |
| `git branch --show-current` | Display the current branch name. |
| `git remote -v` | Display remote repository URLs. |
| `git diff` | Show unstaged changes to tracked files. |
| `git add <path>` | Stage selected file changes. |
| `git diff --staged` | Review staged changes before committing. |
| `git commit -m "message"` | Save staged changes as a commit. |
| `git log --oneline` | View compact commit history. |
| `git switch -c <branch>` | Create a branch and switch to it. |
| `git push` | Send local commits to a configured remote branch. |
| `git push -u origin <branch>` | Push a branch and set its upstream. |
| `git fetch origin` | Download information about remote branches without merging it into the current branch. |
| `git diff main...<branch> --` | Compare changes introduced by a branch. |

---

## 10. Troubleshooting

### Problem: `git` is not recognized or command not found

**Cause:** Git may not be installed, or the terminal has not picked up the installation path.

**Fix:** Install Git from <https://git-scm.com/downloads>, close and reopen the terminal, and run `git --version` again.

### Problem: `Author identity unknown`

**Cause:** Git does not have a commit name or email configured.

**Fix:** Set them and retry the commit:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### Problem: Authentication failed during `git push`

**Cause:** GitHub needs an approved authentication method to allow the push.

**Fix:** Follow a Git Credential Manager or browser sign-in prompt if available. If prompted for HTTPS credentials in a setup that requires a token, use an approved personal access token with the required repository permission; do not use your GitHub account password as the Git password. Never share or commit the token. If using a college organization, check whether it requires single sign-on or administrator approval.

### Problem: `Repository not found`

**Possible causes:** The URL is misspelled, the repository belongs to a different owner, or your account does not have access to a private repository.

**Fix:** Open the repository in your browser, select **Code → HTTPS**, copy the URL again, and check repository access. You can inspect the configured remote with:

```bash
git remote -v
```

### Problem: `nothing to commit, working tree clean`

**Meaning:** Git does not detect any uncommitted changes. You may already have committed your work, or the file was not saved.

**Fix:** Check that the file is saved in the repository folder and that you edited the intended file. Then run `git status` again.

### Problem: The file does not appear in `git diff`

**Cause:** A new file is untracked, and ordinary `git diff` does not show untracked file contents.

**Fix:** Stage the intended file, then inspect it with `git diff --staged`:

```bash
git add docs/PROJECT-OVERVIEW.md
git diff --staged
```

### Problem: `src refspec ... does not match any`

**Possible causes:** The branch name is wrong, or no commit exists on that branch yet.

**Fix:** Check the current branch and commit history:

```bash
git branch --show-current
git log --oneline -5
```

Use the exact branch name returned by Git, and make sure you have committed a change before pushing.

### Problem: I cannot see `docs/USER-ROLES.md` on GitHub

**Cause:** The file was pushed to `docs/add-user-roles`, but GitHub is displaying `main`.

**Fix:** Use the branch selector to switch to `docs/add-user-roles`. The file will not appear on `main` until the branch is merged later.

### Problem: `git switch main` reports an issue

**Cause:** The repository may use a different default branch, or the local branch has a different name.

**Fix:** Run `git branch -a` to see the available branches. For a repository created as described in this lab, the default branch is normally `main`.

---

## 11. Optional extension exercises

Complete these only after all checkpoints pass.

### Exercise A — Make a second commit

1. Update the **Project Status** section of `README.md` to say that repository setup is complete and requirements discovery is the next activity.
2. Run `git diff` and review the change.
3. Stage the README, review the staged diff, and commit with a meaningful message.
4. Push the change on your current branch.
5. Use `git log --oneline -5` to compare your commits.

### Exercise B — Explore file history

On GitHub, open `README.md` and find its history. Identify which commit changed it. Compare the previous and current versions of the file.

### Exercise C — Explain branching

In your own words, answer:

- Why did you create `docs/add-user-roles` instead of making the change directly on `main`?
- What would happen to the main branch if the feature branch is not merged?
- What is the difference between saving a commit locally and pushing it to GitHub?
- What information can you learn from `git status` that is not shown by the repository's README page?

---

## 12. Lab submission checklist

Before finishing, verify each item:

- [ ] A GitHub repository named `campus-canteen-ordering-lab1` exists.
- [ ] The repository has a meaningful README.
- [ ] The repository contains `docs/PROJECT-OVERVIEW.md`.
- [ ] The project overview changes were committed and pushed.
- [ ] At least one meaningful commit appears in the history after the initial repository setup.
- [ ] A branch named `docs/add-user-roles` exists locally and on GitHub.
- [ ] `docs/USER-ROLES.md` is present on the feature branch.
- [ ] I can view the branch and its commit on GitHub.com.
- [ ] I can compare `main` with `docs/add-user-roles`.
- [ ] My working tree is clean, or I can explain any remaining changes.
- [ ] I have **not** merged the feature branch, so the repository is ready for the later labs.

### Evidence to share with the instructor

Submit the GitHub repository URL and, if requested, a screenshot of:

1. The repository's Code page with the `docs` directory visible.
2. The branch selector showing `docs/add-user-roles`.
3. The branch comparison showing `docs/USER-ROLES.md` as a new file.
4. The terminal output of `git log --oneline --graph --decorate --all -10`.

Do not include credentials, access tokens, private email addresses, or other sensitive information in screenshots.

---

## 13. Completion and connection to the next labs

You have now created a remote repository, cloned it locally, edited and committed documentation, created and pushed a feature branch, and explored Git history.

In **Lab 2**, you will use GitHub Discussions to gather stakeholder requirements, maintain an SRS, create Issues, and organize a backlog with GitHub Projects. In **Lab 3**, you will update the SRS on a branch, create a pull request, review changes, respond to comments, and merge the approved update.

Keep the repository and branch from this lab. They form the starting point for the rest of the Campus Canteen Ordering System practical.

---

## Official references

- Git installation: <https://git-scm.com/downloads>
- GitHub repository quickstart: <https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories>
- Cloning a repository: <https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository>
- Setting your Git username: <https://docs.github.com/en/get-started/git-basics/setting-your-username-in-git>
- Pushing commits to a remote repository: <https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository>
- Comparing commits and branches: <https://docs.github.com/en/pull-requests/committing-changes-to-your-project/viewing-and-comparing-commits>
