# Git(Hub) Intro Workshop

A repository for the Git(Hub) Intro workshop run for the members of Western Game Design Society.

## Resources

- https://git-scm.com/downloads
- https://rogerdudler.github.io/git-guide/
- https://www.atlassian.com/git/tutorials/
- https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet
- https://github.com/skills/introduction-to-github

## Outline

### What is Git?

- The **de facto** distributed version control system.

- Git is like a **big album of _snapshots_** that helps you **keep track of changes** in your projects, and it's especially helpful when you're **working with others**.

  - Imagine you're making a big Lego creation and you want to remember all the steps you took to build it.

  - You could take a picture of your progress after each step, and then you would have a whole album of pictures showing how your Lego creation was built step by step.

  - **Git does the same thing, but instead of pictures, it takes snapshots of your code.**

  - This way, you can always go back to an earlier version if you need to make changes or fix a mistake.

  - And if you're working on a project with friends, you can use Git to share your changes with each other and see who made what changes.

- Developed in 2005 by Linus Torvalds (creator of Linux)

### Install

https://git-scm.com/downloads

**Windows**: Use the installer, which comes with Git Bash (emulator for bash and git)

** I recommend using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) instead for various reasons.

**Linux:** use your package manager of choice.

**MacOS:** use homebrew/macports package manager, or the installer (recommend homebrew)

### Pre-Requisites

1. Have a text editor
   1. VSCode (recommended)
   2. NotePad++
   3. (Neo)Vim
   4. Emacs, etc.

2. Know basic Bash commands
   1. `cd`
   2. `ls`
   3. `rm`
   4. `mkdir`
   5. `touch`, etc.

3. Have a GitHub account (create one here: https://github.com/join)

### The Mental Model

_Every committed change_ in Git is **stored as a snapshot** and referenced by a **unique hash**.

- A **snapshot is not a diff**,
- a **snapshot** is _an entire copy of the entire state of a system at a certain time._

**All files go through three possible states.**

1. **Untracked** ~ changes that are not recorded yet.
2. **Staged** ~ ready to be snapshotted.
3. **Committed** ~ snapshotted.

![The Git Mental Model](https://bernhardwenzel.com/images/posts/2021/git-final-models.png)

Source: Bernhard Wenzel

A **commit** is _a copied collection of files in the repository representing their state at a certain time, along with a message, time, and unique hash._

ie. a "safe", recoverable, and uniquely identifiable version of the project.

### Setting Up a Repository

A **Git repository** is a special directory which allows you to save and access versions of your files.

#### `git init`

- `cd` into the project's directory, and run `git init` to initialize it as a repo.

#### `git clone`

- run `git clone <repo url>` to create a local clone of a remote repository.

In either case, you should see a `.git/` sub-directory in your project after initializing it as a repository.

- [ ] Create a fork of this repository (here's how: https://docs.github.com/en/get-started/quickstart/fork-a-repo)
- [ ] Clone that repository (https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
- [ ] Create a new branch for yourself using `git switch -c <last 2 letters of last name><first 2 letters of your first name>`. Don't worry if this is confusing, we'll go through branching in more depth later!
- [ ] Create a new directory, with a name of the form `<last 2 letters of your last name><first 2 letters of your first name>`
- [ ] Inside this directory, create a new file called `about-me.md`

### Configuration

It's time to configure your Git name and email to be used by the system.

```bash
git config --global user.name <name>
git config --global user.email <email>
```

### The Git Workflow

Were finally ready to make commits (or save changes) to our repository. This is the essence of the Git workflow, and what 95% of your Git usage will look like.

1. _**Add**_ files that you want to commit to the **staging area**.
   1. `git add <file name>` adds a specific file to the staging area.
   2. `git add <directory name/path>` adds all files in the directory to the staging area.

2. _**Commit**_ everything in the staging area. `git commit -m <commit message>`

The most common set of these 2 commands looks like this:

```bash
git add .
git commit -m "hopefully it works this time 🙏"
```

![Git Workflow Diagram](https://wac-cdn.atlassian.com/dam/jcr%3A0f27e004-f2f5-4890-921d-65fa77ba2774/01.svg?cdnVersion%3D760)

Source: Atlassian Git Tutorials

We can see the past commits with:

```bash
git log
```

We can check the current status that we're in (changes in the staging area and untracked changes).

```bash
git status
```

** Writing good commit messages is DIFFICULT! I'd recommend following some of the rules found here: https://cbea.ms/git-commit/

- [ ] Open the `about-me.md` file that you created in a text editor.
- [ ] Answer the following question inside this file: What's a popular game everyone seems to love but you don't like? Why don't you like it?
- [ ] Check the current status.
- [ ] Commit this change.
- [ ] Now answer the following question in the same file, below your answer to the previous one: What are your three favourite video games of all time?
- [ ] Commit this change.

You can use `git checkout` to visit a past commit. (Move the HEAD pointer to another commit)

```bash
git checkout <commit-sha>
```

** Whenever git asks for a commit-sha, we can use `HEAD` to access the most recent commit (on the current branch), and `HEAD~1` to access 1 commit before the HEAD.

** This can put you in a detached HEAD state, so be careful when making more commits.

- [ ] Log the commit history.
- [ ] Visit a previous commit with `git checkout`, and then go back to the most recent commit.
- [ ] Now delete everything in the file!
- [ ] Commit this change.

### Undoing and Rewriting History

We can undo a commit in two ways:

1. `git revert <commit-sha>` creates a new commit with the inverse of the last commit.

- use this for public shared repositories, not ideal for minimal Git history.

2. `git reset --hard <commit-sha>`

- reset the commit history to that specified commit.

- `--hard` nukes all untracked changes after reseting.

- Without `--hard`, the changes will be untracked.

We can amend the most recent commit with

```bash
git commit --amend
```

- opens an editor to edit the commit/commit message.

![Git Checkout, Revert, and Reset](https://miro.medium.com/v2/resize%3Afit%3A1400/format%3Awebp/1%2AvsefSeRgwTGQqK-X2kpm6Q.png)

- [ ] Revert the last commit (the delete).
- [ ] Add your favourite food to the `about-me.md` file in a new line.
- [ ] Hard reset to the last commit.
- [ ] Hard reset to the commit before the delete.

### Branches

**Mental Model**

- Every repository has at least one **branch**. Think of a branch as a specific timeline in the history.
- A **branch** is a series of snapshots that represents a timeline of changes. Branches can start from any snapshot in the history.
- Branches are key for collaboration with GitHub.

We've already been using a branch that we created!

`git branch` ~ list all branches, and show current branch.

- `-a` flag lists all, including remote/non-local branches.
- `-d <branch-name>` flag deletes a branch

`git checkout <branch-name>` ~ Check out a branch.

- `-b` flag creates a new branch and checks it out.

** Alternative is to use `git switch <branch-name>` (and `-c` flag to create a new branch).

- [ ] List all (including remote) branches.
- [ ] Checkout the main branch. Notice how your directory and `about-me.md` file has disappeared.
- [ ] Create a new branch called `temp` and switch to it.
- [ ] Switch back to your branch.
- [ ] Delete the `temp` branch.

There are two important branch operations in Git:

**Rebase** ~ rebase the current branch onto a base branch/commit/tag.

`git rebase <base>`

**Merge** ~ merge a branch into the current branch.

`git merge <branch-name>`

We're going to use a common technique called "feature branching", where we create a new branch for a feature and merge it in later.

- [ ] List all (including remote) branches.
- [ ] Create and switch to a new branch called `new-feature`
- [ ] Inside your directory, create a new file called `new-file.txt`
- [ ] Type "hello world" in the file.
- [ ] Commit all changes.
- [ ] Switch to your original branch and merge the `new-feature` branch into it.

### Set-Up GitHub

### Using GitHub

___

## Notes

<details>
<summary>Notes for Ben's 👀 only</summary>

- Focus on the **mental model** of Git/GitHub.
- Only introduce git **fundamentals**, nothing fancy
- Start from the **local workflow**, then move to the **remote workflow**
- **USE VISUALS, DON’T JUST SAY “Run this command”.** Memorizing commands comes with time (not the focus of the workshop), **understanding the mental model** is vital in the beginning
- Leave room for **questions**, **examples**, and **practice exercises**

</details>
