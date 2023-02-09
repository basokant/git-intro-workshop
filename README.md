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

- The **de facto** modern version control system.

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

- [ ] Clone this repository
- [ ] Create a new directory, with a name of the form `<last 2 letters of your last name><first 2 letters of your first name>`
- [ ] Inside this directory, create a new file called `about-me.md`

### Configuration

It's time to configure your Git name and email to be used by the system.

```bash
git config --global user.name <name>
git config --global user.email <email>
```

### The Git Workflow

### Branches

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
