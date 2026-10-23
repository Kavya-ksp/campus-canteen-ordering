# Software Engineering Process Labs with GitHub

A hands-on, three-lab learning series for practising software engineering processes using Git and GitHub. The labs use one running case study—the **Campus Canteen Ordering System**—so participants can follow a project from repository setup through requirements gathering and Agile planning to change review and approval.

> **Important:** This repository contains the lab instructions. During Lab 1, each participant or team creates a separate working repository for the Campus Canteen project. Do not perform the practical work by editing the lab-instructions repository.

## Learning outcomes

By completing the labs, participants will be able to:

- Explain the difference between Git (distributed version control) and GitHub (a platform for hosting and collaborating on repositories).
- Create and maintain a repository, commit changes, use branches, and inspect history.
- Gather stakeholder requirements and record decisions in GitHub Discussions.
- Write a Software Requirements Specification (SRS) in Markdown.
- Track requirements with GitHub Issues and prioritize work using GitHub Projects.
- Plan a small sprint and define acceptance criteria and a Definition of Done.
- Propose SRS changes through pull requests, perform peer reviews, address feedback, and merge an approved change.

## Lab sequence

| Lab | Title | Suggested duration | Main tools | Main deliverables |
|---|---|---:|---|---|
| [Lab 1 — Git and GitHub Repository Fundamentals](./Lab-1.md) | Create a repository and practise the basic Git workflow. | 60–75 minutes | Git, GitHub Repositories, terminal, text editor | GitHub repository, README, project overview, commits, feature branch and pushed changes |
| [Lab 2 — Requirements Gathering and Agile Planning with GitHub](./Lab-2.md) | Gather requirements, prepare the SRS, create Issues and plan a sprint. | 90–120 minutes | GitHub Discussions, Markdown, GitHub Issues, GitHub Projects | Requirements discussion, `docs/SRS.md`, requirement Issues, prioritized backlog and sprint plan |
| [Lab 3 — SRS Change Management with Pull Requests and Code Reviews](./Lab-3.md) | Make a controlled requirements change and review it before merging. | 90–120 minutes | Git, branches, GitHub Issues, Pull Requests, Code Reviews | Change-request Issue, updated SRS, feature branch, reviewed pull request and merged change |

**Total suggested hands-on time:** approximately 4 to 5 hours and 15 minutes, depending on the participants’ experience and how much peer discussion is included.

Complete the labs in order. Lab 2 reuses the repository created in Lab 1, and Lab 3 uses the SRS and Issues created in Lab 2.

## Case study: Campus Canteen Ordering System

A college canteen currently accepts orders manually. Students may need to wait in a queue, check which menu items are available, calculate their order total, and ask staff about order status. The college wants to explore a simple system that allows students to view the menu, select food items, submit orders, and track status. Canteen staff need to manage menu availability and process orders.

The initial learning project focuses on requirements and software-engineering workflows, not on building a production-ready application. Real payment processing and other complex integrations are outside the initial scope.

## What you need before starting

### Required

- A GitHub account: [Create or sign in to GitHub](https://github.com/).
- Git installed on your computer: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
- A terminal or command-line application (for example, PowerShell or Windows Terminal on Windows, Terminal on macOS, or a terminal emulator on Linux).
- A web browser and internet access.
- A text editor. [Visual Studio Code](https://code.visualstudio.com/) is recommended but not required.
- Permission to create a repository and use Issues. Lab 2 also needs Discussions and Projects to be available for the working repository.

### Recommended

- A second participant or instructor to act as the customer in Lab 2 and review a pull request in Lab 3.
- A repository that you control, or a team repository where every participant has the permissions needed for the exercise.
- Basic familiarity with files, folders, and opening a terminal.

### Verify Git is installed

Open a terminal and run:

```bash
git --version
```

Git should print an installed version. If the command is not recognized, install Git and reopen the terminal.

Configure the name and email that Git will record in your commits (use the identity you are comfortable associating with your work):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check the configuration:

```bash
git config --global --list
```

Replace the example name and email with your own values. If you prefer not to expose your personal email in public commits, review GitHub's email privacy settings and use the GitHub-provided `noreply` address if appropriate.

## Before Lab 1: understand the two repositories

You may use two repositories during the course:

1. **Lab-instructions repository:** This repository contains `README.md`, `Lab-1.md`, `Lab-2.md`, and `Lab-3.md`. Read these files; do not use this repository for your practical commits.
2. **Campus Canteen working repository:** You create this repository in Lab 1 and use it in Labs 2 and 3. A suggested name is `campus-canteen-ordering`. If working as a group, a name such as `campus-canteen-ordering-team-a` also works.

Keeping these repositories separate prevents student work from changing the original instructions.

## How to use these lab instructions

1. Open the relevant lab file using the links in the Lab sequence table.
2. Read the learning objectives and prerequisites before starting.
3. Follow the steps in order and copy commands carefully. Replace placeholders such as `YOUR-USERNAME` with your own values.
4. Complete each checkpoint before moving to the next step.
5. Keep the working repository, its Issues, Discussions and Project board between labs; later exercises depend on the earlier artifacts.
6. Capture the evidence requested in each lab, such as repository links, commit history, Discussion links, Issue links, Project board and pull request.
7. Complete the final checklist and reflection questions in each lab.

If you downloaded this repository as a ZIP, extract it first and open the Markdown files in a text editor or Markdown viewer. If you are reading the files on GitHub.com, use the repository's file list to open each lab.

## Expected working-repository structure

As the labs progress, the Campus Canteen working repository should contain files similar to the following. Some files are created on a separate branch during Lab 1 and may not be on the default branch until you merge them. The lab instructions explain when each file should be created.

```text
campus-canteen-ordering/
├── README.md
└── docs/
    ├── PROJECT-OVERVIEW.md
    ├── USER-ROLES.md
    └── SRS.md
```

The same working repository will also contain Git history and branches. Discussions, Issues, pull requests, and the GitHub Projects board are GitHub-hosted collaboration artifacts and do not appear as local files in the folder structure above.

## What each lab produces

### After Lab 1

- A GitHub repository for the Campus Canteen project.
- A README describing the project.
- `docs/PROJECT-OVERVIEW.md` and `docs/USER-ROLES.md` as instructed in the lab.
- At least one commit on the default branch and a pushed feature branch.
- A basic understanding of `git status`, `git add`, `git commit`, `git diff`, `git log`, `git branch`, and `git push`.

### After Lab 2

- A GitHub Discussion containing customer-discovery questions and recorded decisions.
- `docs/SRS.md` with functional and non-functional requirements, business rules, assumptions and open questions.
- Requirement Issues with descriptions, labels and acceptance criteria.
- A GitHub Projects board with a prioritized backlog and planned first sprint.

### After Lab 3

- A change request recorded in GitHub Issues.
- An SRS change made on a feature branch instead of directly on the default branch.
- A pull request that explains the proposed change and links it to the Issue.
- Peer-review feedback, an updated change, approval and a merged pull request.
- Confirmation that the accepted SRS change appears on the repository's default branch.

## Working individually or in teams

- **Individual mode:** Complete the repository and documentation steps yourself. For Lab 2, use the sample stakeholder responses in the lab if no partner is available. For Lab 3, ask an instructor or another participant to review your pull request; the review is most valuable when performed by someone other than the author.
- **Team mode:** Assign roles such as stakeholder/customer, business analyst, product owner, developer, and reviewer. Rotate roles so that each participant experiences requirements gathering, planning and review.
- If multiple people share one working repository, agree on naming, avoid simultaneous conflicting edits to `docs/SRS.md`, and pull the latest changes before starting a new task.

## Good practices and safety

- Use meaningful commit messages that explain the change.
- Do not commit passwords, access tokens, API keys, private student information, or other secrets.
- Use fictional classroom data. Do not use real payment details or personal customer data.
- Record assumptions and unresolved questions instead of silently treating them as approved requirements.
- Keep Issues and SRS requirement IDs aligned so that requirements can be traced to planned work and reviews.
- Do not merge a proposed SRS change until the reviewer’s comments have been considered and the change is ready.
- A passing exercise or checklist is not a guarantee that a real production application is secure, performant, or complete; those qualities need suitable validation and testing.

## Troubleshooting and official references

Start with the Troubleshooting section in the lab where the issue occurs. These official resources can also help:

- [Git documentation](https://git-scm.com/doc)
- [GitHub repositories](https://docs.github.com/en/repositories)
- [GitHub Discussions](https://docs.github.com/en/discussions)
- [GitHub Issues](https://docs.github.com/en/issues)
- [GitHub Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [Pull requests](https://docs.github.com/en/pull-requests)
- [GitHub Actions](https://docs.github.com/en/actions)

GitHub's interface and available features may vary with repository permissions and plan. If an option is missing, check the relevant lab's troubleshooting section and ask the repository owner or instructor to review the permissions.

