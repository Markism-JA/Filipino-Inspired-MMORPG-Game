## Branch Protection Rules

### For Master Branch (Production)

---

#### 1. Emergency & Admin Access

Only **Admin (Mark)**, the **Lead Developer**, may bypass the rules below. This should only be done for **emergencies or critical maintenance**.

| Action            | Who Can Do It  | What Others **Cannot** Do                                                            |
| ----------------- | -------------- | ------------------------------------------------------------------------------------ |
| **Override All**  | Lead Developer | Can bypass all protection rules if necessary.                                        |
| **Direct Push**   | Lead Developer | **All direct pushes are blocked** for everyone else — all work must go through a PR. |
| **Create/Delete** | Lead Developer | Prevents others from **creating or deleting** the `master` branch.                   |

---

#### 2. Required Review Gates

All changes must pass the following checks through a Pull Request (PR):

| Rule                 | Description                                              |
| -------------------- | -------------------------------------------------------- |
| **Use a PR**         | All code modifications must come from a separate branch. |
| **3 Approvals**      | **At least 3 teammates must approve** before merging.    |
| **Stale Approvals**  | Adding new commits will **dismiss existing approvals.**  |
| **Resolve Comments** | All review comments must be **resolved** before merging. |

---

#### 3. Clean History Policy

These rules maintain a clear and traceable commit history to simplify debugging and auditing.

| Rule                 | Description                                                                         |
| -------------------- | ----------------------------------------------------------------------------------- |
| **Linear History**   | **Prevents messy merge commits.** Only **Squash** or **Rebase** merges are allowed. |
| **Block Force Push** | **Disables `git push --force`** for everyone except the Lead Developer.             |

---

### For Develop Branch (Staging)

Most rules are identical to those for `master`, with the following adjustments:

- Only **1 approval** is required per PR.
- This branch is the main environment for **integration testing**, configured through GitHub Actions.
- In the future, the `master` branch rules will also include **deployment success** and **status checks** (integration/unit tests) as additional requirements before merging.

> _Maintained by the Lead Developer. Updated as needed._
