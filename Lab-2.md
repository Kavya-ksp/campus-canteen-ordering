# Lab 2 — Requirements Gathering and Agile Planning with GitHub

**Case study:** Campus Canteen Ordering System  
**Suggested duration:** 90–120 minutes  
**Level:** Beginner  
**Tools:** GitHub Discussions, GitHub Repositories, GitHub Issues, and GitHub Projects  
**Prerequisite:** Lab 1 — Git and GitHub Repository Fundamentals

---

## 1. Lab overview

In this lab, you will act as a software engineering team that is planning a Campus Canteen Ordering System. You will gather customer needs through GitHub Discussions, convert agreed needs into a Software Requirements Specification (SRS), create a GitHub Issue for every requirement, and plan the work using a GitHub Projects board.

You are **not expected to build the complete application in this lab**. The objective is to practise the activities that happen before and during software development: understanding the problem, agreeing on requirements, tracking requirements, prioritizing work, and planning an iteration.

### Learning objectives

By the end of the lab, you should be able to:

1. Explain when to use a GitHub Discussion versus a GitHub Issue.
2. Enable Discussions on a repository and conduct a structured requirements conversation.
3. Separate stakeholder needs, assumptions, decisions, and unresolved questions.
4. Create `docs/SRS.md` containing functional and non-functional requirements.
5. Create traceable GitHub Issues with descriptions and acceptance criteria.
6. Organize and prioritize Issues with labels and GitHub Projects.
7. Plan a small sprint with a clear goal, selected work, and a definition of done.

### Scenario

The college canteen currently accepts orders manually. Students may need to wait in a queue, ask which food items are available, calculate their order total, and ask staff about the status of an order. The college wants to explore a simple system that helps students select available food items and helps canteen staff process orders.

The initial project will focus on menu viewing, creating an order, calculating the total, submitting an order, and checking order status. Real payment processing is outside the first version.

### What you will produce

At the end of the lab, your repository and GitHub workspace should contain:

- A GitHub Discussion recording customer questions and the decisions made.
- `docs/SRS.md` with functional and non-functional requirements.
- Seven requirement Issues linked conceptually to the SRS.
- Useful labels and, where available, assignments.
- A GitHub Projects board containing the Issues, priority and estimate fields, and a Sprint 1 plan.
- A short list of unresolved questions and a clear sprint goal.

**Important:** Keep the repository from Lab 1. You will reuse it in Lab 3 for an SRS change request and pull-request review.

---

## 2. What you need before starting

### Required

- A GitHub account: <https://github.com/>.
- The repository created in Lab 1, normally named `campus-canteen-ordering-lab1`.
- Permission to view the repository and create Issues.
- **Repository admin permission** to enable GitHub Discussions. If the repository belongs to your instructor or an organization, ask the owner/admin to enable Discussions before you begin.
- Internet access and a browser.
- The SRS text provided in this lab.

### Recommended

- Git installed and configured as in Lab 1.
- The local repository folder from Lab 1, plus a text editor such as Visual Studio Code.
- A partner who can act as the customer/stakeholder. If you are working alone, use the sample stakeholder responses in Step 1.

### Check your Lab 1 repository

1. Sign in to <https://github.com/>.
2. Open the repository you created in Lab 1.
3. Confirm that it contains `README.md` and `docs/PROJECT-OVERVIEW.md`.
4. Record the repository URL so you can return to it easily.

If you did not complete Lab 1, create a repository named `campus-canteen-ordering-lab1`, add a README, and create `docs/PROJECT-OVERVIEW.md` using the Lab 1 instructions before continuing.

### Understand the tools before you begin

| Tool | What it is for in this lab |
|---|---|
| GitHub Discussions | Open conversations and questions used to discover customer needs and clarify assumptions. |
| GitHub Repository | Stores the SRS and other project documentation under version control. |
| GitHub Issues | Tracks a specific requirement as actionable work, with acceptance criteria and ownership. |
| GitHub Projects | Organizes Issues into a backlog and a board for prioritization and sprint planning. |

A useful rule of thumb: **use a Discussion to explore a question; use an Issue to track work that the team must do.** When a discussion produces an agreed requirement, record it in the SRS and create a related Issue.

---

## 3. Step 1 — Gather requirements using GitHub Discussions

**Software Engineering topics:** requirements elicitation, stakeholder communication, requirements analysis, and coping with change.

### 3.1 Enable GitHub Discussions

Discussions might already be enabled in the repository. If you see a **Discussions** tab near the top of the repository, continue to Step 3.2.

If the tab is missing and you own/administer the repository:

1. Open the repository on GitHub.
2. Select **Settings** in the repository navigation.
3. Find the **Features** section on the settings page.
4. Enable **Discussions**. In some versions of the interface, GitHub displays a **Set up discussions** button; use it to complete the setup.
5. If GitHub asks you to create a welcome discussion, complete the prompt or return to the repository.
6. Return to the repository home page and select **Discussions**.

If you cannot see the Settings tab or cannot enable Discussions, ask the repository owner/admin to enable it. Do not create a second repository just to avoid this permission issue.

Official guide: <https://docs.github.com/en/discussions/quickstart>

### 3.2 Start a customer-discovery discussion

1. Open the repository's **Discussions** tab.
2. Select **New discussion**.
3. Choose a suitable category, such as **Q&A**, **Ideas**, or **General**. Category names depend on the repository's configuration. If no suitable category exists, use one of the available open-ended categories.
4. Enter this title:

   `Customer Discovery: Campus Canteen Ordering System`

5. Copy the following text into the discussion body and publish it.

```markdown
## Context

We are planning a Campus Canteen Ordering System. Before writing the
requirements, we need to understand what students and canteen staff need.

## Questions for the stakeholder

1. Who will use the system, and what should each user be able to do?
2. What information should be shown for each menu item?
3. Can a student select more than one item and specify quantities?
4. How should the order total be calculated? Are taxes or service charges
   included in the first version?
5. Which order statuses should students be able to see?
6. Should students be allowed to cancel an order after submitting it? If so,
   until what point in the preparation process?
7. What would be an acceptable menu response time, and under what expected load?
8. Should a student be able to view another student's order?
9. Does the first version need a real payment gateway?

## Expected result

We will record confirmed decisions in `docs/SRS.md`. Items that are not yet
agreed will be listed as open questions rather than treated as confirmed
requirements.
```

### 3.3 Conduct the requirements conversation

If you are working in a group:

1. Assign one participant to act as the **customer/stakeholder**.
2. Assign another participant to act as the **business analyst**.
3. Ask the customer to answer each question. Encourage the analyst to ask follow-up questions when an answer is unclear.
4. Have other team members reply with clarifying questions or identify contradictions.
5. Summarize the decision reached for each topic in a discussion comment.

If you are working alone, add a comment to the discussion containing the following sample stakeholder answers. These answers are a **training scenario** that allow you to complete the rest of the lab; a real project should validate them with actual stakeholders.

```markdown
## Sample stakeholder responses for this lab

1. Users: students browse the menu and place orders; canteen staff view incoming
   orders and update statuses. Administration may manage menu information later.
2. Each item should show its name, price, and availability. A short description
   is useful but is not mandatory for the first version.
3. Yes. A student may select multiple available items and enter a positive
   whole-number quantity for each item.
4. The total is the sum of item price multiplied by quantity. Taxes and service
   charges are excluded from the first-version prototype.
5. Students should see Submitted, Preparing, Ready, and Completed.
6. Cancellation policy is not agreed yet. Keep it as an open question and do
   not treat cancellation as a confirmed first-version feature.
7. For this classroom exercise, use a provisional target: 95% of menu requests
   complete within 2 seconds with 50 concurrent virtual users in the defined
   test environment. The target must be confirmed before real deployment.
8. No. A student must not be able to view another student's private order.
9. No. Real payment processing is outside the initial scope; use a simulated
   submission for the learning prototype.
```

To add a comment, scroll to the discussion's comment/reply area, paste the responses, and submit the comment. If another team member is acting as the customer, use their answers instead of the sample responses.

### 3.4 Identify requirements, assumptions, and open questions

Review the discussion and put each point into one of these groups:

- **Confirmed requirement:** the stakeholder has agreed that the system must do something.
- **Assumption:** a temporary decision used to move the exercise forward; it must be validated later.
- **Open question:** the team does not yet have enough information to specify the behavior.
- **Out of scope:** the stakeholder/team has agreed that the item is not part of the initial release.

For this lab:

- Viewing the menu and item prices is a confirmed functional need.
- The response-time target is a provisional classroom target and should be clearly identified as such.
- Order cancellation is an open question.
- Real payment gateway integration is out of scope for the initial prototype.

**Why this matters:** writing every suggestion as a requirement can produce conflicting or unnecessary features. Requirements analysis involves clarification and agreement, not simply collecting a list of ideas.

### 3.5 Checkpoint 1

Before moving on, confirm that:

- [ ] Discussions is enabled for the repository.
- [ ] A customer-discovery discussion exists.
- [ ] The discussion contains the questions and stakeholder responses.
- [ ] You have identified at least one open question and one out-of-scope feature.
- [ ] You have the URL of the discussion, which you will reference from Issues where appropriate.

---

## 4. Step 2 — Create `docs/SRS.md`

**Software Engineering topics:** functional requirements, non-functional requirements, Software Requirements Specification, requirements specification, and requirements validation.

The SRS documents **what the system must do and the conditions it must satisfy**. It should not prescribe all implementation details. Give each requirement a unique ID so that it can be referenced from Issues, design work, and tests.

### 4.1 Create the `docs/SRS.md` file

You can create the file using your local repository (recommended because it builds on Lab 1) or directly on GitHub.com.

#### Option A — Use your local repository

1. Open a terminal in the local repository folder from Lab 1.
2. Confirm the current branch:

   ```bash
   git branch --show-current
   ```

3. For this lab, use `main` as the starting point. If the command reports another branch, switch to `main`:

   ```bash
   git switch main
   ```

4. Get the latest version from GitHub:

   ```bash
   git pull origin main
   ```

5. Create a folder named `docs` if it does not exist. Inside it, create a file named `SRS.md`.
6. Paste the SRS content from Section 4.2 into the file and save it.

If your instructor has protected `main` so direct pushes are not permitted, create a branch such as `docs/add-srs` and push that branch. Follow your instructor's process for getting the SRS into the repository. Branch-based SRS updates will be practised in Lab 3.

#### Option B — Use GitHub.com in the browser

1. Open the repository's **Code** tab.
2. Select **Add file → Create new file**.
3. Enter this filename in the filename field:

   `docs/SRS.md`

   Typing `docs/` creates the path as part of the new file name; you do not need to create the folder separately.
4. Paste the SRS content from Section 4.2 into the editor.
5. Select **Commit changes**.
6. Use this commit message:

   `docs: add initial software requirements specification`

7. Commit directly to `main` if the repository permits it. If GitHub requires a branch, create a branch and follow your instructor's merge procedure.

### 4.2 SRS content — copy this into `docs/SRS.md`

```markdown
# Software Requirements Specification (SRS)
## Campus Canteen Ordering System

- **Document status:** Draft for classroom review
- **Version:** 0.1
- **Source:** Customer-discovery discussion in this repository

## 1. Purpose

The system will provide a simple way for students to view the canteen menu,
select food items, calculate an order total, submit an order, and view its
status. It will also help canteen staff review and process incoming orders.

## 2. Scope

### In scope for the initial learning prototype

- View menu items, prices, and availability.
- Select available menu items and quantities.
- Calculate and display the order total.
- Submit an order and show a confirmation/reference.
- View the status of an order.

### Out of scope for the initial prototype

- Real payment gateway integration.
- Off-campus delivery.
- Advanced stock forecasting or accounting integration.
- A final order-cancellation workflow; the policy requires stakeholder agreement.

## 3. Stakeholders and users

- **Student:** browses the menu and submits orders.
- **Canteen staff:** reviews incoming orders and updates order status.
- **College/canteen administration:** oversees the service and may maintain menu information.
- **Development team:** specifies, implements, tests, and maintains the system.

## 4. Functional requirements

### FR-001 — View menu

The system shall display menu items with their names, prices, and availability.
A short item description may be displayed when one is available.

**Acceptance criteria**
- Given that menu items exist, when a student opens the menu, each displayed item has a name and price.
- An unavailable item is clearly identified.
- Unavailable items cannot be added to a new order.

### FR-002 — Select menu items and quantities

The system shall allow a student to select one or more available menu items and
specify a positive whole-number quantity for each item.

**Acceptance criteria**
- A student can select more than one available item.
- Quantity must be an integer greater than zero.
- An unknown or unavailable item is rejected from the order.

### FR-003 — Calculate order total

The system shall calculate and display the order total by multiplying each
selected item's unit price by its quantity and adding the results. Taxes and
service charges are excluded from the initial prototype.

**Acceptance criteria**
- The displayed total equals the sum of unit price multiplied by quantity for all selected items.
- The total is recalculated when an item or quantity changes.
- The system rejects an empty order and invalid quantities.

### FR-004 — Submit an order

The system shall allow a student to submit a valid order containing at least
one available item and shall provide an order confirmation or reference.
Payment is simulated and no real payment gateway is required.

**Acceptance criteria**
- An order with at least one valid item can be submitted.
- An empty order cannot be submitted.
- A successful submission displays an order reference or confirmation.
- The confirmation reflects the order that was submitted.

### FR-005 — Track order status

The system shall allow a student to view the current status of their order.
The initial statuses are Submitted, Preparing, Ready, and Completed.

**Acceptance criteria**
- An order has a recognizable status.
- A student can view the status of their own order.
- Status changes made by authorized canteen staff are reflected when the order is viewed again.

## 5. Non-functional requirements

### NFR-001 — Menu response time

For this classroom exercise, the provisional target is that 95% of menu requests
complete within 2 seconds under 50 concurrent virtual users in a defined test
environment. The target must be confirmed and the test conditions documented
before the system is used in a real setting.

**Acceptance criteria**
- A performance test records response times for the agreed workload.
- The report identifies the test environment, number of virtual users, and measured percentile.
- The result is compared with the provisional target above.

### NFR-002 — Order privacy and authorization

The system shall prevent a student from viewing or changing another student's
private order. Canteen staff shall be able to access orders needed to process
them, subject to the permissions defined for the system.

**Acceptance criteria**
- A student can access their own order.
- A student cannot access another student's order by changing an order identifier or URL.
- Unauthorized access attempts are rejected without revealing another student's order details.

## 6. Business rules

- Only available menu items can be ordered.
- Quantities must be positive whole numbers.
- An order must contain at least one item.
- The total is calculated from item prices and quantities; taxes and service charges are excluded from the initial prototype.
- Initial order statuses are Submitted, Preparing, Ready, and Completed.
- Real payment processing is outside the initial scope.
- The cancellation policy remains unresolved and must not be implemented as a confirmed rule until the stakeholder decides it.

## 7. Assumptions and constraints

- This is an educational prototype for a college canteen.
- The menu and order data may be simulated in the earliest version.
- The performance target is a provisional classroom value, not a measured production guarantee.
- Authentication and authorization details must be designed before any real student information is used.

## 8. Open questions

- At what point, if any, can a student cancel an order?
- Which role is allowed to add, edit, or disable menu items?
- What authentication method will be used if the prototype becomes a deployed system?
- Who approves the performance target and test environment?

## 9. Validation and traceability

Each requirement has a unique identifier. The team will create a GitHub Issue for
each requirement and will include its ID in the Issue title and description.
The team will review the SRS for clarity, completeness, consistency, feasibility,
and testability. Implementation and test links will be added as they become
available in later labs.
```

### 4.3 Review and save the SRS

Read the document and check the following:

- Each requirement has a unique ID.
- Functional requirements describe system behaviors.
- Non-functional requirements describe measurable quality or security constraints.
- Acceptance criteria explain how the team would verify the requirement.
- Unresolved questions are listed rather than hidden inside confirmed requirements.
- The performance target is labelled provisional.

If you used the local repository, run:

```bash
git status
git diff
```

Stage and commit the file:

```bash
git add docs/SRS.md
git diff --staged
git commit -m "docs: add initial software requirements specification"
git push
```

If you worked on a branch, push that branch using `git push -u origin <branch-name>` and follow your instructor's procedure. Replace `<branch-name>` with the actual branch name; do not type the angle brackets.

Open `docs/SRS.md` on GitHub and verify that the content is visible online.

### 4.4 Checkpoint 2

- [ ] `docs/SRS.md` exists in the repository.
- [ ] It includes FR-001 through FR-005.
- [ ] It includes NFR-001 and NFR-002.
- [ ] The cancellation policy is recorded as an open question, not as an agreed feature.
- [ ] The SRS is committed and visible on GitHub.

---

## 5. Step 3 — Create a GitHub Issue for every requirement

**Software Engineering topics:** requirements management, work breakdown, responsibility, prioritization, and traceability.

A requirement in the SRS explains what the system must do. A GitHub Issue makes that requirement visible as work that can be discussed, assigned, prioritized, and later linked to implementation and tests.

For this lab, create **seven Issues**: one each for the five functional requirements and two non-functional requirements.

### 5.1 Prepare a small label set

1. Open the repository's **Issues** tab.
2. Select **Labels**. Depending on the interface, Labels may appear in a submenu or under the Issues page.
3. Create the following labels if they do not already exist:

   - `requirement`
   - `functional`
   - `non-functional`
   - `needs-clarification`

4. Choose any readable colors. The exact colors are not important; the label names are.

If you do not have permission to manage labels, use the labels that already exist and continue. Creating labels is helpful but should not block completion of the lab.

### 5.2 How to create an Issue

For each requirement below:

1. Select **Issues → New issue** in the repository.
2. If GitHub offers an issue template chooser, select a suitable template or choose **Open a blank issue**.
3. Enter the supplied title and body.
4. Apply `requirement` and the relevant type label (`functional` or `non-functional`).
5. If available, assign the Issue to yourself or the teammate responsible for it.
6. Submit the new Issue.
7. Record the Issue number. GitHub assigns a number such as `#1` automatically; your numbers will differ from the examples.

Official guide: <https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue>

### 5.3 Create Issue FR-001 — View menu

**Title**

`FR-001 — View menu`

**Body**

```markdown
## Requirement

The system shall display menu items with their names, prices, and availability.

## User value

As a student, I want to see available food items and prices so that I can decide what to order.

## Acceptance criteria

- Given menu items exist, when a student opens the menu, each displayed item has a name and price.
- Unavailable items are clearly identified.
- Unavailable items cannot be added to a new order.

## Traceability

- SRS: `docs/SRS.md`, requirement `FR-001`.
- Source: customer-discovery Discussion in this repository.

## Dependencies / notes

The first version may use sample menu data.
```

Apply labels: `requirement`, `functional`. Suggested priority for the Project: **High**. Suggested estimate: **3 points**.

### 5.4 Create Issue FR-002 — Select menu items and quantities

**Title**

`FR-002 — Select menu items and quantities`

**Body**

```markdown
## Requirement

The system shall allow a student to select one or more available menu items and specify a positive whole-number quantity for each item.

## User value

As a student, I want to select food items and quantities so that I can prepare an order.

## Acceptance criteria

- A student can select more than one available item.
- Quantity must be an integer greater than zero.
- Unknown or unavailable items are rejected.

## Traceability

- SRS: `docs/SRS.md`, requirement `FR-002`.
- Source: customer-discovery Discussion in this repository.
```

Apply labels: `requirement`, `functional`. Suggested priority: **High**. Suggested estimate: **5 points**.

### 5.5 Create Issue FR-003 — Calculate order total

**Title**

`FR-003 — Calculate order total`

**Body**

```markdown
## Requirement

The system shall calculate and display the order total by multiplying each selected item's unit price by its quantity and summing the results. Taxes and service charges are excluded from the initial prototype.

## User value

As a student, I want to see the correct total before submitting an order so that I know how much the selected items cost.

## Acceptance criteria

- The total equals the sum of unit price multiplied by quantity for all selected items.
- The total changes when an item or quantity changes.
- Empty orders and invalid quantities are rejected.

## Traceability

- SRS: `docs/SRS.md`, requirement `FR-003`.
- Source: customer-discovery Discussion in this repository.
```

Apply labels: `requirement`, `functional`. Suggested priority: **High**. Suggested estimate: **3 points**.

### 5.6 Create Issue FR-004 — Submit an order

**Title**

`FR-004 — Submit an order`

**Body**

```markdown
## Requirement

The system shall allow a student to submit a valid order containing at least one available item and provide an order confirmation or reference. Payment is simulated.

## User value

As a student, I want to submit my selected items and receive confirmation so that I know the canteen has received the order.

## Acceptance criteria

- An order with at least one valid item can be submitted.
- An empty order cannot be submitted.
- Successful submission displays an order reference or confirmation.
- The confirmation reflects the submitted order.

## Traceability

- SRS: `docs/SRS.md`, requirement `FR-004`.
- Source: customer-discovery Discussion in this repository.
```

Apply labels: `requirement`, `functional`. Suggested priority: **High**. Suggested estimate: **5 points**.

### 5.7 Create Issue FR-005 — Track order status

**Title**

`FR-005 — Track order status`

**Body**

```markdown
## Requirement

The system shall allow a student to view the current status of their own order. Initial statuses are Submitted, Preparing, Ready, and Completed.

## User value

As a student, I want to check the status of my order so that I know whether it is being prepared or is ready for collection.

## Acceptance criteria

- Each order has a recognizable status.
- A student can view the status of their own order.
- Status updates made by authorized canteen staff are visible when the order is viewed again.

## Traceability

- SRS: `docs/SRS.md`, requirement `FR-005`.
- Source: customer-discovery Discussion in this repository.
```

Apply labels: `requirement`, `functional`. Suggested priority: **Medium**. Suggested estimate: **5 points**.

### 5.8 Create Issue NFR-001 — Meet the menu response-time target

**Title**

`NFR-001 — Verify menu response time`

**Body**

```markdown
## Requirement

For this classroom exercise, the provisional target is that 95% of menu requests complete within 2 seconds under 50 concurrent virtual users in a defined test environment.

## Acceptance criteria

- A performance test records response times under the agreed workload.
- The test report records the environment, concurrent user count, and response-time percentile.
- The result is compared with the provisional target.

## Traceability

- SRS: `docs/SRS.md`, requirement `NFR-001`.
- Source: customer-discovery Discussion in this repository.

## Note

The numbers are training targets and must be confirmed before a real deployment.
```

Apply labels: `requirement`, `non-functional`. Suggested priority: **Medium**. Suggested estimate: **3 points**.

### 5.9 Create Issue NFR-002 — Protect order privacy and authorization

**Title**

`NFR-002 — Protect order privacy and authorization`

**Body**

```markdown
## Requirement

The system shall prevent a student from viewing or changing another student's private order. Canteen staff shall access orders needed to process them, according to the system's permissions.

## Acceptance criteria

- A student can access their own order.
- A student cannot access another student's order by changing an order identifier or URL.
- Unauthorized access attempts are rejected without revealing order details.

## Traceability

- SRS: `docs/SRS.md`, requirement `NFR-002`.
- Source: customer-discovery Discussion in this repository.

## Note

Authorization requirements must be considered before any real personal or order information is used.
```

Apply labels: `requirement`, `non-functional`. Suggested priority: **High**. Suggested estimate: **5 points**.

### 5.10 Link Issues to the Discussion and SRS

Once all Issues exist:

1. Open the customer-discovery Discussion and copy its URL.
2. Open each Issue and paste the Discussion URL under its **Traceability** section, or add a short comment linking the Issue back to the discussion.
3. Confirm the Issue body includes the relevant requirement ID and the path `docs/SRS.md`.
4. If you want a clickable link to the SRS, open the SRS on GitHub, copy its URL, and paste it into the Issue body.

GitHub automatically assigns Issue numbers. Use your actual Issue numbers in later steps rather than copying numbers from another participant's screen.

### 5.11 Optional — Track the cancellation decision

Order cancellation is currently an open question, not a confirmed requirement. To practise managing uncertainty, create one additional Issue:

**Title:** `Decision needed — define order cancellation policy`

**Body:**

```markdown
## Decision required

The stakeholder has not yet decided whether a student can cancel an order after submission.

## Questions

- Can cancellation happen while the status is Submitted?
- What happens if preparation has already started?
- Should the system show a reason when cancellation is rejected?

## Acceptance criteria for this decision

- The stakeholder confirms the rule.
- The SRS open-question section is updated.
- If the decision becomes a product requirement, the team adds or updates a requirement with a unique ID.
```

Apply `needs-clarification` if you created that label. Do not add this decision Issue to Sprint 1: it represents unresolved analysis work.

### 5.12 Checkpoint 3

- [ ] Five functional-requirement Issues exist: FR-001 to FR-005.
- [ ] Two non-functional-requirement Issues exist: NFR-001 and NFR-002.
- [ ] Each Issue includes a requirement ID and acceptance criteria.
- [ ] Appropriate labels have been applied where possible.
- [ ] The Issues refer to `docs/SRS.md` and the discovery discussion.
- [ ] Any unresolved cancellation policy is recorded separately from confirmed requirements.

---

## 6. Step 4 — Create a GitHub Projects board

**Software Engineering topics:** Agile planning, backlog management, prioritization, estimates, teamwork, and progress monitoring.

A project board provides a visual view of work. In this lab, the board will hold the requirement Issues and help the team choose a small, coherent set of work for the first sprint.

### 6.1 Create a project board

For a repository in your personal account:

1. Select your profile picture in the upper-right corner of GitHub.
2. Select **Your profile**.
3. Open the **Projects** tab on your profile.
4. Select **New project**.
5. Choose a **Board** layout or start with a blank Board template.
6. Enter this project name:

   `Campus Canteen — Product Backlog`

7. Select **Create project**.

If the repository belongs to a GitHub organization, open the organization and use its **Projects** tab to create the project instead. In some organizations, only members with specific permissions can create or edit Projects; ask the instructor/organization owner if the option is unavailable.

Official guide: <https://docs.github.com/en/issues/planning-and-tracking-with-projects/creating-projects/creating-a-project>

### 6.2 Configure the board's status columns

A new Board usually includes a **Status** field and default columns such as **Todo**, **In Progress**, and **Done**.

For this lab, use the available status options as follows:

- **Todo** — the item is in the backlog and has not started.
- **In Progress** — someone is actively working on the item.
- **Done** — the team has met the acceptance criteria and completed the item.

If your Project allows you to edit Status options, you may add **Ready** and **In Review**. This is optional; use the standard statuses if you do not see the setting.

### 6.3 Add the repository's Issues to the project

Add the seven requirement Issues you created in Step 3:

1. In the Project, find **Add item** or the **+** control at the bottom of a board column.
2. Choose the option to add an item from a repository if prompted.
3. Select `campus-canteen-ordering-lab1` (or your actual Lab 1 repository name).
4. Search for each of your seven requirement Issues by title or Issue number.
5. Select them and choose **Add selected items**.
6. Confirm that the Issues appear in the Project board.

If the control is not visible, open an Issue in the repository and look for the **Projects** field in the right-hand sidebar. Select `Campus Canteen — Product Backlog` there. Repeat for each Issue.

Official guide: <https://docs.github.com/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project>

### 6.4 Add planning fields

Projects supports built-in fields and configurable custom fields. Add the fields below if they are not already present. The labels and field menus may vary slightly with GitHub's interface updates.

1. In your Project, open the field-management option, usually named **Settings**, **Fields**, or **+ Add field**.
2. Add a **Priority** field of type **Single select**, with options `High`, `Medium`, and `Low`.
3. Add a **Requirement Type** field of type **Single select**, with options `Functional`, `Non-functional`, and `Clarification`.
4. Add an **Estimate** field of type **Number**. Use relative story-point estimates, not hours.
5. Add an **Iteration** field if it is available. Configure an iteration named **Sprint 1** with a duration suitable for your training scenario. If you cannot create an Iteration field, add a single-select field named `Sprint` with options `Sprint 1`, `Sprint 2`, and `Backlog`.

An Iteration field is useful for recurring sprint planning, while the fallback Sprint field is enough for this introductory lab.

**Why use relative estimates?** A 5-point item is expected to be more effort or uncertainty than a 3-point item for this team. Story points are not a guarantee that a task will take a specific number of hours or days.

### 6.5 Set values for the Issues

Use this table as your example plan. Your Project values may be set by editing the table cells or the item's details panel.

| Requirement | Type | Priority | Estimate | Initial status |
|---|---|---:|---:|---|
| FR-001 — View menu | Functional | High | 3 | Todo |
| FR-002 — Select menu items and quantities | Functional | High | 5 | Todo |
| FR-003 — Calculate order total | Functional | High | 3 | Todo |
| FR-004 — Submit an order | Functional | High | 5 | Todo |
| FR-005 — Track order status | Functional | Medium | 5 | Todo |
| NFR-001 — Verify menu response time | Non-functional | Medium | 3 | Todo |
| NFR-002 — Protect order privacy and authorization | Non-functional | High | 5 | Todo |

For the optional cancellation-decision Issue, set Requirement Type to `Clarification`, Priority to `Medium`, and leave it outside Sprint 1 until the stakeholder has decided the policy.

If your view does not show a field, add it from the field menu or open the item details panel. If your plan or permission does not let you add a particular field, continue using Labels and the Status field; record the priority and estimate in the Issue body as a fallback.

### 6.6 Prioritize the backlog

Discuss these questions with the team:

- Which capabilities provide the first useful experience for a student?
- Which requirements depend on other requirements?
- Which requirements could cause significant risk if ignored?
- Which work is small enough to complete and verify in the first iteration?

For this lab, use the following reasoning:

- Viewing the menu (FR-001) is a prerequisite for selecting items.
- Selecting items and quantities (FR-002) is a prerequisite for calculating the total.
- Calculating the total (FR-003) completes a small, coherent user journey.
- Submitting orders and tracking status are needed for the end-to-end order workflow, so keep them in the backlog for a later iteration in this exercise.
- Privacy/security (NFR-002) is high priority and must be considered before using real student data. It is not optional just because it is not selected for the first classroom sprint.
- Performance (NFR-001) needs an agreed test environment and measurement. It may be planned after the first workflow exists, but the target should be validated before real deployment.

Prioritization should reflect user value, dependencies, effort, and risk—not just the number of Issues.

---

## 7. Step 5 — Plan Sprint 1

**Sprint goal:** Deliver a basic menu-and-cart experience in which a student can view available items, select quantities, and see a correct order total.

For this planning exercise, the sprint is a simulation. You are choosing the work to attempt; no complete application is expected yet.

### 7.1 Select the sprint backlog

Assign these Issues to **Sprint 1** in the Iteration/Sprint field:

- FR-001 — View menu (3 points)
- FR-002 — Select menu items and quantities (5 points)
- FR-003 — Calculate order total (3 points)

Total planned estimate: **11 story points**.

Leave FR-004, FR-005, NFR-001, and NFR-002 in the broader backlog for this exercise. NFR-002 remains a high-priority constraint that must be addressed before deploying a system that contains real user data. In a real project, security may need to be implemented earlier depending on the architecture and release scope.

### 7.2 Write a sprint goal

Open the Project description or README/settings area, or create a draft note in the Project, and record:

> **Sprint 1 goal:** A student can see available menu items, select one or more items with valid quantities, and see a correctly calculated total before submitting an order.

If you prefer to keep the Project minimal, add the goal to your repository README or to a short comment in the team discussion. The goal must be visible to the team; it does not have to be stored in a particular GitHub field.

### 7.3 Agree on a Definition of Done

For Sprint 1, the team can consider an Issue done only when:

- The behavior matches the requirement and its acceptance criteria.
- Invalid inputs are handled as specified.
- The change has been reviewed by another team member when applicable.
- Relevant tests have passed (tests will be emphasized in a later lab).
- Any affected SRS documentation is updated.
- The Issue is moved to **Done** only after the team has checked the acceptance criteria.

Because this lab focuses on planning rather than application coding, leave the three selected Issues in **Todo** or **Ready** rather than marking them Done.

### 7.4 Move items and explore the board

Try the following Project actions:

1. Switch between Board and Table views if available.
2. Move one Issue from **Todo** to **In Progress**, then return it to **Todo** because implementation has not started. Observe how the same item is represented in different views.
3. Sort or group by Priority or Requirement Type if your Project view provides the option.
4. Filter to show only functional requirements.
5. Filter to show only items assigned to yourself, if you assigned Issues.
6. Check that the three Sprint 1 items are easy to distinguish from the remaining backlog.

**Learning point:** the Issue is the work item, while the Project is the planning view. Moving an Issue between Project statuses does not change the requirement itself. The SRS is still the source document for the requirement's agreed behavior.

### 7.5 Checkpoint 4

- [ ] A Project named `Campus Canteen — Product Backlog` exists.
- [ ] All seven requirement Issues have been added to the Project.
- [ ] Priority and Requirement Type have been recorded, using fields or fallback labels/body text.
- [ ] Estimates have been recorded for the seven requirements.
- [ ] FR-001, FR-002, and FR-003 are assigned to Sprint 1.
- [ ] The sprint goal and Definition of Done are visible to the team.
- [ ] The remaining Issues are still in the backlog and have not been incorrectly marked Done.

---

## 8. Review the complete requirements workflow

Trace one requirement from the original customer question to the planned work. For example, follow FR-003 — Calculate order total:

1. **Discussion:** a stakeholder confirmed that the total should be calculated from item prices and quantities.
2. **SRS:** `docs/SRS.md` records the behavior as FR-003 and defines acceptance criteria.
3. **Issue:** a GitHub Issue tracks the requirement, its acceptance criteria, and its priority/estimate.
4. **Project:** the Issue appears on the product backlog and is assigned to Sprint 1.
5. **Future implementation and testing:** in a later lab, the team will implement the feature and connect code changes and tests to the Issue.

This is a simple form of **requirements traceability**. It helps the team answer: where did this requirement come from, what exactly does it mean, who is responsible for it, when is it planned, and how will we verify it?

---

## 9. Troubleshooting

### I cannot see the Discussions tab

- Open repository **Settings** and look in **Features** for Discussions.
- You may not have admin permission. Ask the repository owner or instructor to enable it.
- If the repository is managed by an organization, organization policies may affect available features.

### I cannot create an Issue

- Confirm you are signed in and viewing the correct repository.
- Confirm that Issues are enabled for the repository.
- For an organization repository, ask the instructor to check your permissions.

### I cannot find Labels

- Open the Issues page and look for the **Labels** view or menu.
- If you do not have permission to create labels, use existing labels or document the type in the Issue body.

### I cannot find Projects on my profile

- Open your profile and check the **Projects** tab.
- If the repository belongs to an organization, check the organization's Projects tab.
- Your organization may restrict who can create projects. Ask the instructor/owner for access.

### I cannot add Issues to the Project

- Confirm the Issue belongs to a repository you can access.
- Open the Issue and inspect the **Projects** field in its right-hand sidebar.
- Alternatively, open the Project and add the existing Issue from the repository.
- Confirm the Project is owned by the same user or organization as the repository, or use a project that can access the repository.

### I cannot add an Iteration field

- Use a custom single-select field named `Sprint` with `Sprint 1`, `Sprint 2`, and `Backlog` options.
- If custom fields are unavailable because of permissions or plan configuration, note the sprint assignment in the Issue body and keep using the Status board.

### Git commands say my branch is behind or there are conflicts

- Check the current branch with `git branch --show-current`.
- Before editing, switch to `main` and pull the latest version as described in Step 4.1.
- Do not use force-push to resolve a beginner lab problem. Ask the instructor to help if you have conflicting local and remote changes.

### A feature or menu item looks different

GitHub periodically changes its user interface. Look for the same named action (for example, **New discussion**, **New issue**, **New project**, **Add item**, or **Settings**) in the current interface. The linked official documentation is the authoritative reference for current navigation.

---

## 10. Lab submission checklist

Before you finish, confirm that you have all of the following:

### Repository and requirements

- [ ] The Lab 1 repository is retained and reused.
- [ ] The customer-discovery Discussion is published and contains the question/answer record.
- [ ] `docs/SRS.md` is committed and visible in GitHub.
- [ ] The SRS has five functional requirements and two non-functional requirements, each with acceptance criteria.
- [ ] Open questions and out-of-scope features are clearly identified.

### Issues and Project

- [ ] Seven requirement Issues exist and correspond to FR-001 through FR-005 and NFR-001 through NFR-002.
- [ ] Issues refer to the SRS and Discussion.
- [ ] Labels, priorities, and estimates are set or recorded using the available alternatives.
- [ ] The Project board contains all seven Issues.
- [ ] Sprint 1 contains FR-001, FR-002, and FR-003.
- [ ] The sprint goal and Definition of Done are recorded.

### Evidence for the instructor

Submit or show:

1. Repository URL.
2. Customer-discovery Discussion URL.
3. `docs/SRS.md` URL.
4. URL or list of the seven requirement Issues.
5. Project board URL showing backlog, priorities, and Sprint 1.
6. One short explanation of why the order-cancellation policy remains an open question.

Do not include access tokens, passwords, private student data, or other confidential information in the submission.

---

## 11. Reflection questions

Be prepared to answer these questions:

1. What is the difference between a GitHub Discussion and a GitHub Issue?
2. Why should the team document a requirement in the SRS after it has been discussed?
3. Why does each requirement have a unique ID?
4. What makes a requirement testable? Give an example from the SRS.
5. What is the difference between a functional and a non-functional requirement?
6. Why is the performance target labelled provisional?
7. Why should the team avoid treating the cancellation policy as a confirmed requirement before the stakeholder agrees?
8. How does GitHub Projects help with backlog prioritization and sprint planning?
9. Why is security important even if the security Issue is not selected for the first classroom sprint?
10. How will the team know whether an Issue can be moved to Done?

---

## 12. Official reference links

Use these guides if GitHub's interface differs from the steps above:

- GitHub Discussions quickstart: <https://docs.github.com/en/discussions/quickstart>
- Enabling Discussions for a repository: <https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/enabling-or-disabling-github-discussions-for-a-repository>
- Creating a GitHub Issue: <https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue>
- Creating a GitHub Project: <https://docs.github.com/en/issues/planning-and-tracking-with-projects/creating-projects/creating-a-project>
- Adding items to a Project: <https://docs.github.com/en/issues/planning-and-tracking-with-projects/managing-items-in-your-project/adding-items-to-your-project>
- About GitHub Projects: <https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects>

**End of Lab 2.** Keep the repository, Discussion, SRS, Issues, and Project board. Lab 3 will use them to demonstrate a controlled SRS change through a branch, pull request, and peer review.
