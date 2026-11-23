# From zero to GitHub, VS Code, and agentic AI

A hands-on beginner's module • Approximately 90–120 minutes • No coding experience required

> **About the pictures:** The screenshots below are real examples from GitHub and VS Code's official documentation, linked from their sites. They illustrate the key steps, not your personal account; names, colors, buttons, and layouts can differ as products change. Internet access is needed to display them. Each picture links to its source. On GitHub, click an image to enlarge it or open its source link for more pictures.

## Your learning journey

1. Understand the tools and how they fit together.
2. Create a safe practice repository on GitHub.
3. Install Git and VS Code; connect your repository to your computer.
4. Make, review, commit, and push your first change.
5. Set up GitHub Copilot and ask an agent to create a small web page.
6. Check the work, share it using a branch and pull request, and test yourself.

**You will need:** a computer (Windows, macOS, or Linux), an internet connection, an email address, permission to install apps, and a web browser. Copilot access is needed for the AI exercise; an eligible GitHub account may use Copilot Free, subject to availability and usage limits. A work/school account may have administrator restrictions. You do not need a credit card for the GitHub account exercise, and should check plan terms before agreeing to anything paid.

**Safety first:** Use a new private practice repository with no personal, company, or confidential data. Never put passwords, tokens, private keys, or customer data in a repository or an AI prompt. A private repository is not a substitute for protecting secrets. Only trust folders and approve commands you understand. You—not the AI—are responsible for the result.

---

## 1. ELI5: what are these things?

Imagine making a picture book:

| Tool or word | Like… | In real life |
| --- | --- | --- |
| **VS Code** | Your desk and pencil | An app for opening and editing project files on your computer. |
| **Git** | A time machine for your book | Software on your computer that records snapshots of selected changes. It works without GitHub. |
| **GitHub** | A bookshelf on the internet | A service that hosts Git repositories and lets people collaborate. |
| **Repository (repo)** | The book and its history | A project folder plus Git history. A GitHub repo is a remote copy; a clone is your local copy. |
| **Commit** | A labeled snapshot | A saved record in Git history. A normal local commit is not automatically online. |
| **Branch** | A draft copy of your story | An independent line of work, normally combined with `main` after review. |
| **Push / pull** | Send / bring back updates | Push sends commits to GitHub; pull downloads and integrates remote commits into your current branch. |
| **Pull request (PR)** | “Please review my draft” | A proposal on GitHub to merge one branch into another. |
| **Agentic AI** | A helper who can plan and use tools | An AI assistant that can inspect files, propose or make edits, and possibly run commands in several steps. It can be wrong. |

**The big picture:**

```text
Your computer                                     GitHub (online)
VS Code edits files → Git stages → Git commits ── push ──▶ repo + branch
                            ▲                     ◀── pull ── updates
AI agent helps in VS Code ──┘     You review, test, and decide
```

A **save** writes to your file. A **commit** records a local snapshot. A **push** sends commits to GitHub. They are three different actions!

### Quick check
Which tool records local history? **Git.** Which one hosts it online? **GitHub.** Who is the final reviewer? **You.**

---

## 2. Create your GitHub account and practice repository

If you already have a GitHub account, sign in and skip to step 3. Use your own account; don't share your login or verification codes.

1. Go to [github.com](https://github.com/) and choose **Sign up**. Follow the prompts, verify your email, and sign in.
2. Set up [two-factor authentication](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication) when prompted or via your account settings. Save recovery codes somewhere secure and separate from your repo.
3. From GitHub's top-right **+** menu, choose **New repository**.

   ![GitHub top navigation with New repository highlighted](https://docs.github.com/assets/cb-29762/images/help/repository/repo-create-global-nav-update.png)

   *Source: [GitHub Hello World](https://docs.github.com/en/get-started/using-github/hello-world#step-1-create-a-repository).*

4. Name it `my-first-agent-project`. A repository is just your project's home. Choose **Private** so only authorized people can access it. (Public repositories can be viewed by anyone.)
5. Select **Add a README file**; a README is the project's introduction. Click **Create repository**.
6. **Checkpoint:** You should see a repository page containing `README.md`. Its default branch is usually `main`. Keep this browser tab open.

> Already have a repo? You can use it only if you have write access, but a new practice repo is safer. Don't create a new repo inside an existing project's folder.

---

## 3. Install Git and VS Code

1. Download and install Git from [git-scm.com/downloads](https://git-scm.com/downloads). On Windows, the installer defaults are suitable for this exercise, including the credential helper if offered. On macOS, follow the site's installer instructions; if prompted for Apple's developer tools, install them. On Linux, use the instructions for your distribution.
2. Download and install [Visual Studio Code](https://code.visualstudio.com/download) for your operating system. Open it after installation. VS Code is different from Visual Studio.
3. In VS Code choose **Terminal → New Terminal**. Type the following and press Enter:

   ```text
   git --version
   ```

   **Checkpoint:** You should see `git version` and a number. If not, restart VS Code after installing Git. If it still fails, check [Git troubleshooting](https://code.visualstudio.com/docs/sourcecontrol/troubleshooting).
4. Tell Git the name and email to put on your commits. Replace the examples with your own values; keep the quotation marks. Press Enter after each line:

   ```sh
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

   These are **author labels**, not your GitHub password. They apply as defaults on this computer. Commit author information can be visible to others when shared. For privacy, use your [GitHub-provided no-reply email](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) if you prefer. GitHub associates commits based on the email settings. If your identity is already configured and correct, skip this step.
5. **Checkpoint:** Run `git config --global user.name` and `git config --global user.email` to inspect the values (these commands don't print your password).

**Keyboard tip:** To open the Command Palette, press **Ctrl+Shift+P** on Windows/Linux or **Cmd+Shift+P** on macOS. It is a search box for VS Code commands.

---

## 4. Connect GitHub to VS Code by cloning

**Clone** means download a working copy of your GitHub repo to your computer, with its history and a connection back to GitHub called `origin`.

1. On your GitHub repo page, click the green **Code** button. Under **HTTPS**, click the copy icon beside the URL. It will look like `https://github.com/YOUR-USERNAME/my-first-agent-project.git`.

   ![GitHub Code button highlighted above repository files](https://docs.github.com/assets/cb-13128/images/help/repository/code-button.png)

   ![GitHub HTTPS clone URL and copy button](https://docs.github.com/assets/cb-60499/images/help/repository/https-url-clone-cli.png)

   *Source: [GitHub cloning guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository).*

2. In VS Code, open the Command Palette and type **Git: Clone**. Select it, paste the URL, and press Enter. Alternatively choose **Clone from GitHub** and sign in to pick your repo.

   ![VS Code Git clone prompt](https://code.visualstudio.com/assets/docs/sourcecontrol/repos-remotes/github-clone.png)

   *Source: [VS Code clone repositories](https://code.visualstudio.com/docs/sourcecontrol/repos-remotes#_clone-repositories).*

3. Choose a **parent folder** such as Documents. VS Code will create the `my-first-agent-project` folder inside it; don't choose an existing Git repository as the parent. When prompted, select **Open** to open the cloned folder.
4. If asked to sign in, follow the browser sign-in and authorization prompts and return to VS Code. A public repo can often be cloned without signing in; pushing to your own repo still requires authentication and write access. With HTTPS, GitHub does not accept an account password for Git operations; use the prompted browser/credential-helper flow, not a password in the terminal. See [GitHub authentication](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github).
5. If prompted about **Workspace Trust**, trust only a folder you created or whose contents you understand. For this new practice repo, select trust. An unknown repo can contain dangerous configuration or code.
6. **Checkpoint:** In VS Code's Explorer (files icon on the left), you see `README.md`. The bottom status bar shows a branch, usually `main`. Open **Source Control** (branch-shaped icon on the left); it should recognize your repository.

> VS Code's Git integration uses the separately installed Git program. Signing in to GitHub and having write access are different from just installing Git.

---

## 5. Make and share your first change

We will first practice on `main` in your **own new practice repo**. On shared or protected projects, follow the project's branch and review rules instead.

1. In Explorer, select `README.md`. Add a new line like `I am learning GitHub and VS Code.` Save with **Ctrl+S** (Windows/Linux) or **Cmd+S** (macOS).
2. Open **Source Control**. Under **Changes**, `README.md` should show **M** (modified). Select the file to view the **diff**: removed text is usually red on the left; added text is green on the right. For a new file, the entire file is an addition.

   ![VS Code Source Control view showing changed and untracked files](https://code.visualstudio.com/assets/docs/sourcecontrol/staging-commits/view-changes.png)

   *Source: [VS Code staging and committing](https://code.visualstudio.com/docs/sourcecontrol/staging-commits#_view-changes).*

3. Hover over `README.md` and select **+** to **stage** it. It moves to **Staged Changes**. Staging selects the current content for your next snapshot. If you edit again, stage the new edits too.

   ![VS Code Stage Changes plus button](https://code.visualstudio.com/assets/docs/sourcecontrol/staging-commits/stage-changes.png)

   *Source: [VS Code staging changes](https://code.visualstudio.com/docs/sourcecontrol/staging-commits#_staging-changes).*

4. Type `Add learning note` in the message box, then click **Commit**. This records the staged snapshot **locally**. If prompted for a name/email, complete section 3 first.
5. Select **… → Push** in Source Control. If prompted to sign in or authorize, follow the prompts. If VS Code offers **Publish Branch**, use it to upload the current branch and set its upstream. **Sync Changes** may pull before pushing, so it is not the same as push alone.
6. **Checkpoint:** Go back to the GitHub repo in your browser, select `main` if necessary, and refresh. Open `README.md`: your new line should be visible. You can also inspect the latest commit on the repository page.

If you see a secret in a diff, **do not commit or push it**. Remove it from the staged change and the file. If a secret was already committed or pushed, assume it is exposed: revoke/rotate it immediately and follow [GitHub's sensitive-data guidance](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository). Deleting a line alone does not erase Git history.

---

## 6. Set up your AI helper in VS Code

We use **GitHub Copilot** as one concrete example. Other agents exist and have different setup, prices, and privacy terms. GitHub account login for Git and Copilot access are related but separate: signing in does not guarantee your account has agent access.

1. Update VS Code to a recent stable version. In VS Code, find the **Copilot** icon in the status bar and select **Use AI Features**. If you don't see it, open the Command Palette and run **GitHub Copilot: Sign in**, or follow the [official setup guide](https://code.visualstudio.com/docs/setup/copilot).
2. Sign in with the GitHub account that has Copilot access and approve the browser prompts. Return to VS Code. An eligible account without a subscription can be enrolled in **Copilot Free**; follow the on-screen choices and read the terms. Free usage is limited; model availability, quotas, and plan requirements can change. Check the [current plans](https://docs.github.com/en/copilot/get-started/plans) and your status dashboard. If your organization manages your account, ask its administrator about access and approved use.

   ![VS Code Accounts menu with GitHub Copilot sign-in option](https://code.visualstudio.com/assets/docs/setup/copilot/vscode-accounts-menu.png)

   *Source: [VS Code Copilot setup](https://code.visualstudio.com/docs/setup/copilot#_use-a-different-github-account-with-copilot).*

3. Make sure your cloned **practice project** is open. Open Chat with **Ctrl+Alt+I** (Windows/Linux; check the Chat menu or Command Palette on macOS) and select **+** for a new chat.

   ![VS Code new chat control](https://code.visualstudio.com/assets/docs/agents/agents-quickstart/editor-new-chat.png)

   *Source: [VS Code agent quickstart](https://code.visualstudio.com/docs/agents/quickstart#_2-build-the-app).*

4. If these controls appear, choose **Session Target: Copilot**, **Agent: Agent**, **Language model: Auto**, and **Permissions: Manual permissions**. In older layouts, choose **Agent** in the chat mode dropdown. Exact choices depend on your VS Code version, account, and organization policy. If these controls are missing, update VS Code and consult the [current quickstart](https://code.visualstudio.com/docs/agents/quickstart).

   ![VS Code chat session controls for Copilot, Agent, and manual permissions](https://code.visualstudio.com/assets/docs/agents/agents-quickstart/agent-session-editor-select-harness-role-2.png)

   *Source: [VS Code agent quickstart](https://code.visualstudio.com/docs/agents/quickstart#_2-build-the-app).*

5. **Checkpoint:** A chat input is visible and you can select an agent. Manual permissions request approval for tools/resources, but the agent may still edit files in the project folder. Do not assume every file edit needs separate approval. Review changes afterward. You can stop the agent using **Stop** in the chat input.

**Privacy and cost:** A provider may receive your prompt, relevant file contents, and tool output. Check [Copilot data handling](https://resources.github.com/copilot-trust-center/) and your organization's rules before using real work. VS Code telemetry settings are not the same as AI-provider data settings. Do not enable automatic approval of everything just to make prompts go away.

---

## 7. Guided project: make a tiny task list with an agent

### A. Create a branch for the experiment

1. In VS Code, click the branch name (usually `main`) in the bottom status bar.
2. Choose **Create new branch**, type `add-task-list`, and press Enter. The new branch starts from your current branch; make sure `main` is selected and your first change is pushed before you create it.
   ![VS Code branch picker with create branch options](https://code.visualstudio.com/assets/docs/sourcecontrol/branches-worktrees/scm-create-branch.png)

   *Source: [VS Code create branches](https://code.visualstudio.com/docs/sourcecontrol/branches-worktrees#_create-new-branches).*

3. **Checkpoint:** The status bar now says `add-task-list`. Your changes will be on this branch, not `main`, until merged.

### B. Give the agent a clear task

In the Agent chat, paste this prompt and send it:

```text
In this practice repository, create one file called index.html: a simple,
accessible task list page with embedded CSS and JavaScript and no external
libraries or network requests. Let me add a non-empty task, mark it complete,
and delete it. Save tasks in browser localStorage so they persist after reload.
Do not change README.md. Do not run terminal commands or install anything.
Explain what you changed and tell me how to test it manually. Do not commit or
push; I will review the changes myself.
```

This prompt specifies the goal, file, constraints, checks, and who makes the final decision. The AI can still misunderstand or make mistakes; verify the actual files. If it asks permission to run a command, **deny it** for this exercise. Do not paste secrets into chat.

### C. Review and test like the boss

1. Read the agent's explanation. In Explorer, confirm `index.html` exists and `README.md` is unchanged. In **Source Control**, open each changed file's diff. For a new file you will see all its content as added. Ask the agent to explain anything you do not understand; reject or correct changes outside the requested scope.
2. Check the file for unexpected scripts, links, external network requests, or instructions to install something. The prompt is a request, not a security guarantee. Do not open the page if the code looks suspicious; ask for help. If the agent changed other files, inspect them and keep or undo them deliberately. **Discard Changes** can permanently remove uncommitted work; do not click it without checking.
3. To test the intended result, open `index.html` in a browser (for example, find the cloned folder in your file manager and double-click the file). No server or installation is required. Test:
   - Add `Buy milk`; it appears in the list.
   - Try an empty task; no empty task is added.
   - Mark the task complete; its completed state is visible.
   - Refresh the page; the task and its completed state remain. Storage belongs to that browser and local file context; another browser/device will not necessarily see it.
   - Delete the task; it disappears and stays gone after refresh.
   - Use Tab and Enter/Space to check that the controls can be reached and used with a keyboard.
4. If a check fails, tell the agent the exact steps and observed result, then review its next edits and repeat the tests. AI-generated code is not automatically correct or secure.
5. **Checkpoint:** The page passes the checks, and Source Control contains only changes you intend to share. Remember: browser storage is local to the browser, not a GitHub database or a secure secret store.

### D. Commit, push, and open a pull request

1. In Source Control, stage the intended file(s) with **+**, enter `Add task list page`, and click **Commit**. Confirm the bottom bar still says `add-task-list`.
2. Select **Publish Branch** if offered, or **… → Push**, and finish the authentication prompts. This sends the branch to GitHub; it does not merge it into `main`.
3. Open your GitHub repository in your browser and refresh. If **Compare & pull request** appears for `add-task-list`, click it. Otherwise choose **Pull requests → New pull request**, set **base** to `main` and **compare** to `add-task-list`.
4. Review the file changes, title, and description. Click **Create pull request**. A PR is a request to review and merge, not the merge itself.
   ![GitHub pull request diff showing removed and added lines](https://docs.github.com/assets/cb-32937/images/help/repository/diffs.png)

   *Source: [GitHub Hello World: open a pull request](https://docs.github.com/en/get-started/using-github/hello-world#step-4-open-a-pull-request).*

5. In your own practice repo, if the checks pass and GitHub allows it, click **Merge pull request → Confirm merge**. In a shared project, follow its review and branch-protection rules instead. Verify that the PR says **Merged**, switch the repo's branch selector to `main`, and confirm `index.html` is there.
6. Optional: to bring merged `main` back to your computer, switch to `main` with the VS Code branch selector, then **… → Pull**. Pull integrates remote changes into the current branch, so save or commit your work first and check which branch is active. If there is a conflict, stop and see troubleshooting.

**Success:** You created a project, edited and shared a commit, used an agent, checked its work, and merged a reviewed change!

---

## 8. A repeatable everyday workflow

1. Open the correct project and check the current branch.
2. Bring in teammates' changes when appropriate; create a branch for a focused task.
3. Ask the agent for a small task, clear boundaries, and a test plan. Share only permitted information.
4. Read requested tool permissions. Refuse commands you don't understand, especially deletion, uploads, credential access, or installing packages.
5. Review every changed file and run appropriate checks yourself. Ask for corrections if needed.
6. Stage only intended changes; commit with a descriptive message; push the branch.
7. Open a PR, review and merge according to the project's rules; pull updated `main` when ready.

**Useful prompt pattern:** “In [project], achieve [goal]. Change only [files]. Avoid [risks]. Check [acceptance criteria]. Explain changes. Do not commit or push.”

---

## 9. Troubleshooting

| Problem | Try this |
| --- | --- |
| `git` is not recognized | Install Git, close and reopen VS Code, then run `git --version`. Check your PATH if needed. |
| No repository in Source Control | Use **File → Open Folder** and open the actual cloned project folder, not its parent. |
| Clone fails | Check the copied HTTPS URL, internet connection, and whether your account can access the repository. |
| Push says permission denied or authentication failed | Confirm the correct GitHub account and that it has write access. Sign in via VS Code/browser and credential helper. Don't paste your password or tokens into chat. Organization policies or protected branches may block direct pushes. |
| Push rejected because remote has newer commits | Don't force-push. Check the current branch, save your work, and pull the remote changes when appropriate. If conflicts appear, resolve and review them before pushing; ask a teammate if unsure. |
| Merge conflict | Git found competing edits. Open the conflicted file in VS Code, examine both versions, choose or combine the intended content, save, stage, and complete the merge as VS Code prompts. Do not discard someone else's changes blindly. See [VS Code conflict help](https://code.visualstudio.com/docs/sourcecontrol/merge-conflicts). |
| Copilot/Agent missing or unavailable | Update VS Code; sign in with the account that has Copilot access; check your plan, quota, and organization policy. See [agent troubleshooting](https://code.visualstudio.com/docs/agents/agent-troubleshooting/faq). |
| Agent changed the wrong file | Stop it. Inspect the diff and ask it to fix the scope, or carefully undo unwanted changes. Discarding changes can destroy uncommitted work. |
| Commit is visible locally but not on GitHub | Check the branch, push it, refresh GitHub, and select the same branch. An unmerged branch won't appear on `main`. |
| Images don't load | Open the source links below each image. They require internet; the instructions still work without the images. |

---

## 10. Quiz and completion checklist

Try answering before looking below.

1. What is the difference between Git and GitHub?
2. Does saving a file automatically create a commit or push it online?
3. What do staging and committing do?
4. What is the difference between a branch and a pull request?
5. What should you do before approving an agent's command or sharing its output?

<details>
<summary>Show answers</summary>

1. Git records project history; GitHub hosts repositories and supports collaboration.
2. No. Save writes the file; commit records a snapshot; push uploads commits.
3. Staging selects the snapshot contents; committing records that snapshot in local history.
4. A branch is a separate line of work; a pull request proposes merging changes for review.
5. Check the command and permissions, keep secrets out, inspect changes, and test the result yourself.

</details>

**I'm ready to continue when I can:**

- [ ] Explain Git, GitHub, VS Code, and an AI agent in my own words.
- [ ] Find my repo on GitHub and open its clone in VS Code.
- [ ] Review, stage, commit, and push a small change.
- [ ] Create a branch and open a pull request.
- [ ] Give an agent a bounded task, review its work, and test it.
- [ ] Recognize that passwords and private data must stay out of repos and prompts.

## Official resources

- [GitHub Hello World: repositories, branches, and PRs](https://docs.github.com/en/get-started/using-github/hello-world)
- [VS Code: Git and source control quickstart](https://code.visualstudio.com/docs/sourcecontrol/quickstart)
- [VS Code: repositories, remotes, clone, and push](https://code.visualstudio.com/docs/sourcecontrol/repos-remotes)
- [VS Code: set up GitHub Copilot](https://code.visualstudio.com/docs/setup/copilot)
- [VS Code: complete your first task with an agent](https://code.visualstudio.com/docs/agents/quickstart)
- [GitHub Copilot plans](https://docs.github.com/en/copilot/get-started/plans)

*Documentation and screenshots checked 23 November 2026. Interfaces, availability, plans, and policies can change; the official links are the source of current details.*
