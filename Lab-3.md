# Lab 3 — SRS Change Management with Pull Requests and Code Reviews

**Case study:** Campus Canteen Ordering System  
**Suggested duration:** 90–120 minutes  
**Level:** Beginner to intermediate  
**Tools:** Git, GitHub Repositories, GitHub Issues, branches, Pull Requests, and Code Reviews  
**Prerequisites:** Lab 1 — Git and GitHub Repository Fundamentals; Lab 2 — Requirements Gathering and Agile Planning with GitHub

---

## 1. Lab overview

In Lab 1, you created a repository and practised the basic Git workflow. In Lab 2, you used GitHub Discussions to gather customer needs, wrote `docs/SRS.md`, created requirement Issues, and planned work with GitHub Projects.

In this lab, you will manage a change to the Software Requirements Specification (SRS) using a controlled review workflow. You will record a customer decision, create or update a tracking Issue, create a feature branch, edit the SRS, push the branch to GitHub, open a pull request, review the proposed change, respond to feedback, and merge the approved change.

**Do not edit `main` directly for this exercise.** The point is to practise proposing and reviewing a change before it becomes part of the main version of the project.

### Scenario

In Lab 2, the canteen stakeholder had not decided whether students should be allowed to cancel an order. For this training scenario, the stakeholder now confirms the following policy:

> A student may cancel their own order while its status is `Submitted`. Once canteen staff change the status to `Preparing`, the student cannot cancel the order through the application. The system must confirm a successful cancellation and explain when a cancellation is rejected.

This is a classroom decision used to practise the workflow. On a real project, confirm such a policy with the actual business stakeholder before treating it as an approved requirement.

### Learning objectives

By the end of the lab, you should be able to:

1. Explain why teams use branches and pull requests to propose changes.
2. Link a change request to a GitHub Issue and the relevant SRS requirement.
3. Update a document on a feature branch without changing `main` directly.
4. Open a pull request with a clear summary, scope, and traceability.
5. Review the changed lines and provide specific, constructive feedback.
6. Respond to requested changes by committing and pushing a follow-up update.
7. Approve and merge a reviewed pull request, then verify the change on the default branch.
8. Explain how code/document review supports requirements validation, change management, and quality assurance.

### What you will produce

- A GitHub Issue recording the cancellation-policy decision, or a reuse of the Issue created in Lab 2.
- A branch named `docs/confirm-order-cancellation-policy`.
- An update to `docs/SRS.md` that adds requirement `FR-006` and removes the resolved cancellation question.
- A pull request with a linked Issue and a meaningful description.
- At least one review comment and a response to the comment.
- A reviewed and merged pull request.
- Evidence that the final SRS is visible on the default branch.

---

## 2. What you need before starting

### Required

- A GitHub account: <https://github.com/>.
- The repository from Labs 1 and 2. The examples in this lab assume it is named `campus-canteen-ordering-lab1`; if you chose a different name, use your actual repository name throughout.
- The `docs/SRS.md` file from Lab 2.
- Git installed on your computer: <https://git-scm.com/downloads>.
- A terminal (PowerShell, Git Bash, macOS Terminal, or a Linux terminal) and a text editor such as Visual Studio Code.
- Internet access.
- Access to create a branch and push it to the repository.

### Recommended for the full peer-review exercise

- A partner who can review the pull request.
- Write access for the author, and sufficient repository access for the reviewer to submit a review. If you are using an organization-owned repository, ask the repository owner/instructor to grant the appropriate permissions.
- The repository owner should verify that the partner has accepted any collaboration invitation before the lab starts.

**If you are working alone:** You can create the branch and pull request, inspect the Files changed tab, and use the review checklist. For the actual peer-review step, ask your instructor or another participant to submit the review. Do not claim that you received an independent approval if you reviewed your own work.

### Confirm that Lab 2 is complete

1. Sign in to <https://github.com/>.
2. Open your Lab 1 repository.
3. Confirm that `docs/SRS.md` exists and contains `FR-001` through `FR-005`, `NFR-001`, and `NFR-002`.
4. Confirm that the SRS currently records the cancellation policy as an unresolved question. If your SRS differs, review the changes made in Lab 2 before continuing.
5. Open **Issues** and look for an Issue named similar to `Decision needed — define order cancellation policy`.
   - If it exists, use that Issue in this lab.
   - If it does not exist, you will create it in Step 1.
6. Copy the repository URL so you can open it easily.

### Identify the default branch

Most repositories created in Lab 1 will use `main`, but use the branch name shown in your repository. To check it on GitHub, open the repository home page and look at the branch selector above the file list. The default branch is also shown in the repository settings.

The commands below use `main`. If your repository's default branch has another name, replace `main` with that branch name in all commands.

---

## 3. Step 1 — Record the change request in GitHub Issues

**Software Engineering concepts:** requirements management, change control, traceability, and stakeholder communication.

A customer request should not be handled only as an informal chat message. The team needs a record of what changed, why it changed, and which requirements or work items are affected.

### 3.1 Reuse the cancellation-decision Issue if it already exists

1. Open the repository on GitHub.
2. Select **Issues**.
3. Search for an Issue titled `Decision needed — define order cancellation policy`, or a similar cancellation-policy Issue created in Lab 2.
4. Open it and check whether it records the questions that were unresolved in Lab 2.
5. Add a comment summarizing the stakeholder's new decision. Use the text below.

```markdown
## Stakeholder decision — cancellation policy

For this classroom exercise, the stakeholder has confirmed:

- A student may cancel their own order while its status is `Submitted`.
- Once the order status is `Preparing`, the student cannot cancel it through the application.
- The system must confirm successful cancellation.
- If cancellation is not allowed for the current status, the system must explain that to the student.

The SRS must be updated to record this decision as a uniquely identified functional requirement. A reviewer must check the wording before it is merged.
```

6. Select **Comment** to add the update.
7. Copy the Issue number from the page (for example, `#12`). Your actual number will be different.

### 3.2 Create the Issue if it does not exist

If Lab 2 did not include a cancellation-decision Issue:

1. Select **Issues → New issue**.
2. Use this title:

   `Decision needed — define order cancellation policy`

3. Paste the following body:

```markdown
## Purpose

Record and validate the stakeholder's decision about when a student can cancel an order.

## Stakeholder decision for this lab

- A student may cancel their own order while its status is `Submitted`.
- Once the order status is `Preparing`, the student cannot cancel it through the application.
- Successful cancellation must show confirmation.
- A rejected cancellation must explain why the request was not accepted.

## Acceptance criteria for this decision

- [ ] The decision is recorded in `docs/SRS.md`.
- [ ] The SRS contains a uniquely identified requirement and testable acceptance criteria.
- [ ] The old cancellation-policy open question is removed from the SRS.
- [ ] A reviewer checks the change through a pull request.

## Traceability

Related document: `docs/SRS.md`  
Related discussion: add the customer-discovery Discussion URL from Lab 2, if available.
```

4. If suitable labels exist, apply `requirement` and/or `needs-clarification`. If `needs-clarification` was used in Lab 2, remove it when the question is resolved. Do not spend time creating elaborate labels for this lab.
5. Select **Create issue**.
6. Record the Issue number and URL.

### 3.3 Understand what the Issue tracks

This Issue records the cancellation-policy decision and the associated SRS update. It does **not necessarily mean the cancellation feature has been implemented in an application**. A future implementation task may need its own Issue and tests.

**Checkpoint 1**

- [ ] The customer decision has been recorded in a GitHub Issue comment or Issue body.
- [ ] You know the Issue number and URL.
- [ ] The decision is clear enough to document and review.

---

## 4. Step 2 — Prepare your local repository

This step ensures that you start from the latest version of the SRS and do not accidentally include unrelated changes in the pull request.

### 4.1 Open the local repository folder

Open your terminal and change directory to the local folder you used for Lab 1. For example, if your repository is in a `GitHub` folder under Documents, navigate to that folder and then into the repository. The path is specific to your computer.

Run:

```bash
git status
git branch --show-current
git remote -v
```

**Expected result:**

- `git status` reports the current working-tree state.
- `git branch --show-current` prints your current branch name.
- `git remote -v` shows the remote repository URL, usually named `origin`.

If the terminal says the folder is not a Git repository, use `cd` to enter the repository folder. If you did not clone the repository in Lab 1, clone it now using the repository URL from GitHub:

```bash
git clone https://github.com/YOUR-USERNAME/campus-canteen-ordering-lab1.git
cd campus-canteen-ordering-lab1
```

Replace `YOUR-USERNAME` and the repository name with the actual URL for your project. Do not type the placeholder literally.

### 4.2 Check for uncommitted changes

Run:

```bash
git status --short
```

If the command prints nothing, your working tree has no uncommitted changes. Continue to Step 4.3.

If it lists changed files, do not discard them blindly. Either commit the work if it is complete and belongs in the current branch, or save a copy of the files and ask your instructor for help before switching branches. Do not use `git reset --hard` or force-push as a quick fix in this lab.

### 4.3 Update your local default branch

Run:

```bash
git switch main
git pull origin main
```

If your default branch is not named `main`, substitute its actual name. If `git switch main` reports that the branch does not exist locally, run:

```bash
git fetch origin
git branch -a
```

Identify the remote default branch shown by GitHub (for example, `remotes/origin/main`), then create or switch to the corresponding local branch. If you are unsure, ask the instructor before proceeding.

**Expected result:** your local default branch is up to date with GitHub and `git status` reports a clean working tree.

---

## 5. Step 3 — Create a feature branch

A branch lets you prepare a change separately from the default branch. The proposed SRS update will not become part of `main` until the pull request is reviewed and merged.

### 5.1 Create the branch

Run:

```bash
git switch -c docs/confirm-order-cancellation-policy
```

Verify the branch name:

```bash
git branch --show-current
```

Expected output:

```text
docs/confirm-order-cancellation-policy
```

If you get an error saying the branch already exists, run `git branch` to inspect local branches. If this is a branch you created for this same lab, you can switch to it with:

```bash
git switch docs/confirm-order-cancellation-policy
```

If the branch has unrelated work on it, do not reuse it. Choose a new branch name, such as `docs/confirm-cancellation-policy-lab3`, and use that exact name in the later commands.

### 5.2 Explain the branch to a partner

Before editing the SRS, tell your partner:

- The branch starts from the current default branch.
- It is intended to contain only the cancellation-policy documentation change.
- You will propose the change using a pull request rather than pushing it directly to `main`.

**Checkpoint 2:** You are working on the feature branch, not the default branch.

---

## 6. Step 4 — Update `docs/SRS.md`

**Software Engineering concepts:** requirements specification, requirements validation, change impact analysis, and configuration management.

You will update four areas of the SRS:

1. Document version/status or change history.
2. Scope, so cancellation before preparation is no longer listed as entirely out of scope.
3. Functional requirements, by adding `FR-006`.
4. Business rules and open questions, so they reflect the agreed decision.

Use the local file `docs/SRS.md` in your text editor. Preserve the existing requirements `FR-001` through `FR-005`, `NFR-001`, and `NFR-002` unless there is a direct reason to change them.

### 6.1 Update the document status/version

Near the beginning of `docs/SRS.md`, Lab 2 created metadata similar to:

```markdown
- **Document status:** Draft for classroom review
- **Version:** 0.1
```

Change the version to `0.2`. Keep the status as draft until the change has been reviewed and merged. This is a simple classroom version marker, not a substitute for a formal document baseline process.

If your document does not have a version line, add one below the title:

```markdown
- **Document status:** Draft for classroom review
- **Version:** 0.2
```

### 6.2 Update the Scope section

In Lab 2, the out-of-scope list included wording similar to:

> A final order-cancellation workflow; the policy requires stakeholder agreement.

The policy has now been agreed for the classroom scenario. Remove that bullet and replace it with wording that accurately describes the remaining boundary, for example:

```markdown
- Cancellation after preparation has started is not supported.
- Real payment processing, payment reversals, and refunds are outside the initial prototype.
```

Keep the other scope bullets that are still accurate.

### 6.3 Add FR-006 — Cancel a submitted order

Find the **Functional requirements** section. Add the following requirement after `FR-005 — Track order status` and before the **Non-functional requirements** section.

For the first version of this change, copy the text below. The review exercise will ask your reviewer to identify one missing detail in the acceptance criteria; you will then correct it in response to the review.

```markdown
### FR-006 — Cancel a submitted order

The system shall allow a student to cancel their own order while its status is
`Submitted`. Once an order's status has changed to `Preparing`, the student
shall not be able to cancel it through the application.

**Acceptance criteria**
- Given that a student's own order is `Submitted`, when the student requests
  cancellation, the system changes the order status to `Cancelled` and displays
  a confirmation.
- Given that an order is `Preparing`, `Ready`, `Completed`, or `Cancelled`,
  when the student requests cancellation, the system rejects the request and
  explains that cancellation is not available for the current status.
```

The second acceptance criterion intentionally leaves one detail implicit: what should happen to the status when cancellation is rejected? Your reviewer should notice that the requirement can be made more precise. Do not merge this first draft until that feedback has been addressed.

### 6.4 Update the Business rules section

Find the current business rules. Remove the bullet that says the cancellation policy remains unresolved. Add or replace it with these rules:

```markdown
- A student may cancel only their own order while its status is `Submitted`.
- A successful cancellation changes the order status to `Cancelled`.
- Once the order status is `Preparing`, `Ready`, or `Completed`, the student
  cannot cancel the order through the application.
- A rejected cancellation request must not change the order's current status.
```

Keep the existing business rules about available menu items, positive quantities, order totals, order statuses, and simulated payments.

### 6.5 Update the Open questions section

Find the open question similar to:

> At what point, if any, can a student cancel an order?

Remove it because the stakeholder decision in this lab has resolved it. Keep other unresolved questions, such as who can maintain the menu and which authentication method would be used in a deployed system.

If your SRS does not have an Open questions heading, add or update a short list that contains only genuinely unresolved questions. Do not leave a resolved question in the document as if it were still undecided.

### 6.6 Add a change-history entry (recommended)

If you have a change-history section, add an entry similar to:

```markdown
| Version | Change | Status |
|---|---|---|
| 0.2 | Added FR-006 and clarified the order-cancellation policy based on stakeholder decision. | Under review |
```

If no change-history section exists, you may add a small `## Change history` section near the end of the SRS. If your instructor prefers a concise SRS, the version marker and Issue/PR history are sufficient for this lab.

### 6.7 Review your own SRS before committing

Read the full section around the change and verify:

- `FR-001` through `FR-005` are still present and unchanged.
- `FR-006` has a unique ID and uses precise language.
- The new rule does not contradict the known statuses in `FR-005`.
- The SRS no longer says the cancellation policy is unresolved.
- The scope still excludes real payments and refunds.
- The new requirement and business rules agree with each other.
- Only the intended SRS file changed.

Do not decide that the SRS is fully validated just because it reads well to its author. The next steps deliberately use an independent reviewer.

---

## 7. Step 5 — Inspect, commit, and push the proposed change

### 7.1 Inspect the changed files

Run:

```bash
git status
git diff --check
git diff -- docs/SRS.md
```

What these commands do:

- `git status` lists changed files and the current branch.
- `git diff --check` checks for common whitespace errors such as trailing whitespace.
- `git diff -- docs/SRS.md` shows the exact lines added, removed, or modified.

Read the diff carefully. A pull request should contain only the intended changes. If other files appear unexpectedly, investigate before continuing.

### 7.2 Stage and commit the SRS update

Run:

```bash
git add docs/SRS.md
git commit -m "docs(srs): define order cancellation policy"
```

**Expected result:** Git creates a commit containing the SRS change. If Git says there is nothing to commit, check that you saved `docs/SRS.md` and that the file actually changed.

### 7.3 Push the feature branch to GitHub

Run:

```bash
git push -u origin docs/confirm-order-cancellation-policy
```

The `-u` option sets the upstream so Git can associate your local branch with the remote branch.

**Expected result:** the branch appears on GitHub. You have not changed `main`; you have uploaded the proposal branch only.

If Git asks you to authenticate, follow GitHub's sign-in flow or your configured credential method. Do not paste a password, personal access token, or other secret into the lab document, a commit, or a chat message.

### 7.4 Verify the branch online

1. Open the repository on GitHub.
2. Select the branch selector above the file list.
3. Choose `docs/confirm-order-cancellation-policy`.
4. Open `docs/SRS.md` and check that the new `FR-006` is visible on the branch.
5. Return to the repository home page.

**Checkpoint 3:** The proposed SRS update exists on the feature branch on GitHub, and `main` has not yet been updated.

---

## 8. Step 6 — Open a pull request

A pull request (PR) asks the team to review a proposed change and decide whether it should be merged. It is a place to examine differences, discuss the rationale, review the linked Issue, and record approval or requested changes.

### 8.1 Create the pull request

After you push the branch, GitHub may display a **Compare & pull request** button. Select it if it appears. Otherwise:

1. Open the repository on GitHub.
2. Select **Pull requests**.
3. Select **New pull request**.
4. Set the **base** branch to the repository's default branch (normally `main`). This is where the change is intended to go.
5. Set the **compare** branch to `docs/confirm-order-cancellation-policy`. This is the branch containing your proposed change.
6. Review the displayed file comparison and confirm that `docs/SRS.md` is the intended change.
7. Select **Create pull request**.

Do not reverse the base and compare branches. The base is the destination; the compare branch is the proposed change.

### 8.2 Fill in the pull request title and description

Use this title:

`[SRS] Define order cancellation policy`

Use a description based on this template. Replace `#<ISSUE_NUMBER>` with the actual Issue number from Step 1.

```markdown
## Purpose

Record the stakeholder-approved cancellation policy in the SRS.

## Changes

- Added FR-006 — Cancel a submitted order.
- Updated the Scope section to reflect the agreed cancellation boundary.
- Updated business rules and removed the resolved cancellation open question.
- Updated the SRS version to 0.2.

## Requirements validation

- [ ] FR-006 has a unique ID.
- [ ] Acceptance criteria can be verified.
- [ ] Business rules and open questions agree with the decision.
- [ ] A second participant has reviewed the diff.

## Traceability

Related decision Issue: #<ISSUE_NUMBER>
SRS file: docs/SRS.md

## Scope note

This pull request updates requirements documentation only. It does not implement
order cancellation in a running application.
```

If the pull request fully completes the decision-only Issue's acceptance criteria, you may use `Closes #<ISSUE_NUMBER>` instead of `Related decision Issue: #<ISSUE_NUMBER>`. GitHub can automatically close a linked Issue when a pull request targeting the default branch is merged. If the Issue also tracks implementation work that is not complete, use `Refs #<ISSUE_NUMBER>` or a normal link instead; do not close unfinished work.

Select **Create pull request** to publish the proposal.

### 8.3 Request a reviewer

1. On the pull request page, locate the **Reviewers** section in the right sidebar.
2. Select your partner or instructor if the option is available.
3. Send a brief message asking them to inspect `docs/SRS.md` against the review checklist in Step 9.

If your repository does not allow you to select a reviewer, contact the partner directly and share the pull request URL. The reviewer can still open the PR and use **Files changed** if they have sufficient repository access.

### 8.4 Understand the pull request tabs

Explore the following areas:

- **Conversation:** PR description, general discussion, review summaries, and status.
- **Commits:** commits included in the proposed change.
- **Files changed:** line-by-line differences between the source branch and base branch.
- **Reviewers / Checks / status indicators:** review and automated-check status where configured.

At this point, the PR should not be merged. The reviewer is expected to find and report one issue in the first draft of FR-006.

**Checkpoint 4:** The pull request targets the default branch, refers to the cancellation decision Issue, describes the change, and has a reviewer assigned or contacted.

---

## 9. Step 7 — Review the pull request and provide feedback

**Software Engineering concepts:** peer review, requirements validation, quality assurance, and professional communication.

The reviewer should act as a teammate who did not author the change. Reviewing is not simply checking spelling. The reviewer checks whether the proposed requirement is clear, complete, consistent, feasible, and testable.

### 9.1 Open the proposed change

The reviewer should:

1. Open the pull request URL shared by the author.
2. Read the title and description to understand the reason for the change.
3. Open the **Files changed** tab.
4. Inspect `docs/SRS.md` and read the surrounding context, not only the added lines.
5. Check whether the changed SRS agrees with the linked Issue and the cancellation decision.

### 9.2 Use the review checklist

The reviewer should check each item below:

| Review area | Question to ask |
|---|---|
| Traceability | Is the change connected to the decision Issue and the SRS? |
| Completeness | Does the requirement cover successful cancellation and rejected cancellation? |
| Clarity | Can the developer and tester interpret the rule the same way? |
| Consistency | Does FR-006 agree with the order statuses in FR-005 and the business rules? |
| Testability | Could a tester write a test for each acceptance criterion? |
| Scope | Does the change avoid promising real payment reversal or refund behavior? |
| Change impact | Were the old open question and the scope statement updated? |
| Documentation quality | Are the requirement ID, heading, formatting, and version consistent? |

### 9.3 Add an inline review comment

The first draft intentionally omits an explicit statement about whether the current order status remains unchanged when cancellation is rejected. The reviewer should identify this missing detail.

1. In **Files changed**, move to the relevant line in the second FR-006 acceptance criterion.
2. Select the comment icon that appears next to the changed line.
3. Enter a constructive comment similar to:

   > Please state explicitly that a rejected cancellation request leaves the order's current status unchanged. This is important for testability—for example, an order that is already `Preparing` should remain `Preparing` when cancellation is rejected.

4. Select **Start a review** or the equivalent option to add the comment to a pending review. Interface labels may differ slightly.
5. If other useful findings exist, add them as separate comments on the relevant lines. Do not invent cosmetic problems merely to increase the comment count.

### 9.4 Submit the review

When the reviewer is ready, choose **Review changes**. Select one of the following outcomes:

- **Comment:** General feedback without approving or formally requesting changes.
- **Request changes:** The author should address the feedback before the PR is approved.
- **Approve:** The change meets the review standard and may be merged, subject to repository rules.

For this exercise, choose **Request changes** because the first draft needs clarification. Add a summary comment such as:

> The SRS update is well scoped and traceable. Please clarify that the order status remains unchanged when cancellation is rejected, then request another review.

Select **Submit review**.

**Important:** A review marked `Request changes` does not prevent merging by itself in every repository. Enforced review requirements depend on branch rules, permissions, and the repository plan. The class should follow the intended review procedure even if the UI does not technically block a merge.

### 9.5 Author: read and acknowledge the feedback

The author should open the pull request's **Conversation** tab, read the review, and respond politely. For example:

> Thanks for identifying the ambiguity. I will update FR-006 so the expected state after a rejected cancellation is explicit.

Do not merge the PR at this stage.

**Checkpoint 5:** The pull request contains an independent review comment explaining a specific improvement needed in FR-006.

---

## 10. Step 8 — Apply the review feedback and update the pull request

The author should make the correction on the **same feature branch**. Do not create a new pull request for the same change.

### 10.1 Edit the acceptance criteria

Open the local `docs/SRS.md`. Replace the FR-006 acceptance criteria with the corrected version below:

```markdown
**Acceptance criteria**
- Given that a student's own order is `Submitted`, when the student requests
  cancellation, the system changes the order status to `Cancelled` and displays
  a confirmation.
- Given that an order is `Preparing`, `Ready`, `Completed`, or `Cancelled`,
  when the student requests cancellation, the system rejects the request,
  explains that cancellation is not available for the current status, and leaves
  the order's status unchanged.
```

The final criterion now describes both the rejected action and the expected state after rejection. Keep the business rules consistent with this behavior.

### 10.2 Inspect the follow-up edit

Run:

```bash
git status
git diff --check
git diff -- docs/SRS.md
```

Read the output and confirm that the intended acceptance criterion is now explicit.

### 10.3 Commit and push the correction

Run:

```bash
git add docs/SRS.md
git commit -m "docs(srs): clarify rejected cancellation behavior"
git push
```

Because the upstream was set in Step 7.3, `git push` should update the same remote feature branch. If Git asks you to specify the upstream, use:

```bash
git push -u origin docs/confirm-order-cancellation-policy
```

**Expected result:** the existing pull request updates automatically with the new commit and the corrected `docs/SRS.md`. You do not need to open another PR.

### 10.4 Respond to the review comment

1. Return to the pull request on GitHub.
2. Reply to the review comment or conversation thread.
3. Explain the correction briefly, for example:

   > Updated FR-006 to state that a rejected cancellation request leaves the current order status unchanged. The clarification is committed on this pull request.
4. If GitHub displays a **Resolve conversation** option, use it only after the issue raised by that comment has actually been addressed.

### 10.5 Ask for another review

Notify the reviewer that the PR has been updated. The reviewer should re-open **Files changed**, confirm the new wording, and check that the other SRS changes are still correct.

**Checkpoint 6:** The PR includes the follow-up commit, the reviewer comment is addressed, and the author has asked for another review.

---

## 11. Step 9 — Approve and merge the pull request

### 11.1 Reviewer: verify the updated change

The reviewer should confirm that:

- The corrected FR-006 explicitly states that a rejected cancellation leaves the status unchanged.
- The rule is consistent with the business rules.
- The unresolved cancellation question has been removed.
- The change is still limited to the intended SRS update.
- Any review conversations that required action have been addressed.

If the change is satisfactory, open **Review changes**, write a short summary, select **Approve**, and submit the review.

If another problem is discovered, add a specific comment and ask the author to address it before approval. Do not approve simply to finish the exercise.

### 11.2 Author: confirm approval and merge

1. Open the pull request's **Conversation** tab.
2. Confirm that the reviewer has approved the current version of the change.
3. Check whether any conversations or required checks remain outstanding.
4. If you have permission to merge and the required review process is complete, select **Merge pull request**.
5. Choose the merge method available to the repository. For this documentation-focused lab, the default method is fine unless your instructor specifies otherwise.
6. Confirm the merge.

If you are not permitted to merge, ask the repository owner/instructor to do so after verifying the approval. Do not work around repository rules by pushing directly to the default branch.

### 11.3 Verify the change on the default branch

1. Open the repository home page.
2. Select the default branch (normally `main`) in the branch selector.
3. Open `docs/SRS.md`.
4. Verify that it includes `FR-006 — Cancel a submitted order` and the corrected acceptance criteria.
5. Verify that the cancellation question no longer appears among open questions.
6. Open the pull request and confirm its status is **Merged**.
7. Open the linked Issue and check whether it was closed automatically or still needs a status update.

If you used `Refs #<ISSUE_NUMBER>` instead of `Closes #<ISSUE_NUMBER>`, GitHub will link the Issue but will not automatically close it. Close the decision-only Issue manually after confirming its acceptance criteria are complete. Do not close a separate Issue that still tracks implementation or testing work.

### 11.4 Update your local repository

Return to your terminal and run:

```bash
git switch main
git pull origin main
git log --oneline -5
```

Replace `main` if the repository uses a different default branch. Inspect the latest history and confirm that the merged documentation change is now present locally.

You may delete the merged feature branch through GitHub or locally after confirming the pull request is merged. Branch deletion is optional for this lab; keep the pull request itself as the review record.

**Checkpoint 7:** The PR is merged, the final SRS is on the default branch, and the Issue status reflects whether the decision work is complete.

---

## 12. Optional instructor extension — protect the default branch

This is optional and requires suitable repository permissions. It may also depend on the repository visibility and GitHub plan. Do not make this a prerequisite for completing the core lab.

An instructor or repository administrator can configure a branch protection rule or ruleset for the default branch that requires pull requests and approving reviews before merging. Depending on available settings, they can also require status checks or resolution of review conversations.

Typical navigation:

1. Open the repository on GitHub.
2. Select **Settings**.
3. Under repository code/planning settings, locate **Branches** or **Rules**.
4. Add a rule that targets the default branch.
5. If supported and appropriate, enable the requirement for a pull request before merging and require at least one approving review.
6. Save the rule and test it with a harmless practice change.

Do not enable a rule without confirming that the team has someone who can approve pull requests; otherwise, participants may block their own work. Branch protection options vary by plan and repository type. Consult the official documentation linked at the end of this lab.

### Discussion prompt

Ask participants: “What would happen if every developer could push directly to `main`? What risks do branch reviews reduce, and what problems can they not eliminate?”

Expected themes include accidental changes, unclear requirements, missed defects, knowledge sharing, traceability, review overhead, and the fact that a review is not a substitute for testing or stakeholder acceptance.

---

## 13. Troubleshooting

### I cannot find the repository or `docs/SRS.md`

- Confirm that you are signed in to the correct GitHub account.
- Open the repository used for Labs 1 and 2, not a new repository.
- Confirm that `docs/SRS.md` was committed in Lab 2.
- If the repository is owned by an instructor or organization, ask for the correct URL and access.

### `git switch main` fails

- Run `git branch -a` to see local and remote branches.
- Confirm the repository's default branch on GitHub.
- Use the actual branch name rather than assuming it is `main`.
- If unsure, ask the instructor before attempting to rename or recreate branches.

### The working tree contains unrelated changes

- Run `git status` and identify the files.
- Save a backup and complete or commit the unrelated work on its proper branch.
- Do not delete files or use `git reset --hard` to make the status clean without understanding the changes.

### `git push` is rejected or authentication fails

- Confirm that the `origin` URL is the correct repository by running `git remote -v`.
- Confirm that your account has permission to push branches.
- Complete GitHub authentication using the supported browser/device or credential method.
- If the push is rejected because the remote branch has different work, stop and ask the instructor to help reconcile the branches. Do not force-push.

### I cannot open a pull request

- Confirm that you pushed the feature branch successfully.
- Confirm the compare branch is the branch you pushed and the base branch is the repository's default branch.
- If you do not have write access to the source branch or repository workflow, ask the repository owner to grant access or use the instructor's prescribed fork workflow.
- Make sure the source and base branches differ; a PR cannot be opened between the same branch.

### I cannot choose a reviewer or submit an approval

- Confirm that the reviewer has access to the repository and has accepted any invitation.
- Ask the repository owner/instructor to review if the role or organization settings restrict reviews.
- Do not impersonate another participant or claim a review was approved when it was not.

### The reviewer requested changes, but the PR does not update

- Confirm that you are still on the feature branch.
- Commit your change and push it to the same branch used for the PR.
- Refresh the pull request. New commits pushed to the PR's source branch should appear in the existing PR.

### The Issue did not close after merge

- Review the PR description to see whether it used `Closes #N` or only `Refs #N`.
- Closing keywords work when the pull request targets the repository's default branch. A reference alone links the Issue but does not close it.
- Close the Issue manually only if the work it tracks is complete. Keep implementation Issues open if the code feature remains unimplemented.

### GitHub's interface differs from the instructions

GitHub updates its interface periodically. Look for the same named function (for example, **Pull requests**, **Files changed**, **Review changes**, **Reviewers**, or **Merge pull request**) and use the official documentation links below if a control has moved.

---

## 14. Lab completion checklist

### Change request and branch

- [ ] The cancellation-policy decision is recorded in a GitHub Issue.
- [ ] The local repository is up to date before creating the branch.
- [ ] Branch `docs/confirm-order-cancellation-policy` (or the documented alternative) was created.
- [ ] The SRS update was committed on the feature branch, not directly on `main`.

### SRS update

- [ ] `docs/SRS.md` has a version marker of `0.2` or another clearly documented increment.
- [ ] `FR-006 — Cancel a submitted order` has been added.
- [ ] The scope reflects the agreed cancellation boundary.
- [ ] Business rules describe the cancellation policy.
- [ ] The resolved cancellation question is removed from Open questions.
- [ ] The final acceptance criteria say that rejected cancellation leaves the current status unchanged.

### Pull request and review

- [ ] A PR exists from the feature branch into the default branch.
- [ ] The PR has a meaningful title and description.
- [ ] The PR links to the decision Issue.
- [ ] A reviewer inspected **Files changed**.
- [ ] At least one specific review comment was submitted.
- [ ] The author responded and pushed a correction to the same branch.
- [ ] The reviewer approved the corrected change.
- [ ] The pull request is merged.

### Final verification

- [ ] The final FR-006 appears on the default branch.
- [ ] The pull request shows **Merged**.
- [ ] The decision Issue is closed only if its work is complete.
- [ ] The local default branch was updated after the merge.

---

## 15. Evidence to submit to the instructor

Submit the following URLs or screenshots using the method specified by your instructor:

1. Repository URL.
2. Cancellation-policy decision Issue URL.
3. Feature branch name.
4. Pull request URL, showing the PR description and linked Issue.
5. Screenshot or URL showing the review comment and the author's response.
6. Screenshot or URL showing the approving review and merged PR.
7. URL to `docs/SRS.md` on the default branch showing the final FR-006.
8. A short explanation (3–5 sentences) of why a PR review is useful even when the change is documentation rather than source code.

Do not include passwords, access tokens, private student information, or other secrets in evidence.

---

## 16. Reflection and viva questions

Be prepared to answer:

1. Why did you create a feature branch instead of editing `main` directly?
2. What is the difference between a commit and a pull request?
3. What should a pull request description explain?
4. Why is the Issue linked to the pull request?
5. What is the difference between a general review comment, an approval, and a request for changes?
6. How did the reviewer improve the testability of FR-006?
7. Why should a requirement be reviewed for consistency with business rules and other requirements?
8. Does a merged SRS change mean the cancellation feature has been implemented? Why or why not?
9. When should a linked Issue be closed, and when should it remain open?
10. What are the benefits and limitations of branch protection rules?

---

## 17. Official reference links

Use the official GitHub documentation if a navigation step differs from the current interface:

- Creating a pull request: <https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request>
- Reviewing proposed changes in a pull request: <https://docs.github.com/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request>
- Linking a pull request to an Issue: <https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue>
- About protected branches: <https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches>
- Managing a branch protection rule: <https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule>
- Git documentation: <https://git-scm.com/doc>

**End of Lab 3.** Keep the repository, SRS, Issues, Project board, and merged pull request. Together, Labs 1–3 demonstrate a simple software engineering workflow: repository setup, requirements discovery and planning, and controlled change through review.
