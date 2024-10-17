# Version Controlling with Git

Git serves two major purposes: _history tracking_ and _collaboration._ When a developer works on a project for a long period, it is difficult for him/her to memorize the changes the project files have gone through. Git preserves the file histories as _commits._ It helps developers go through a files history or the entire repository history whenever necessary.

Any complex project requires team collaboration. When a team of developers work together on the same project, there must be some means to keep their work in sync among themselves. Git serves this purpose with Git _remotes_, a central Git repository. Developers finish their tasks on their local repositories and _push_ their changes to the remote repository when they are done so that other developers can _pull_ his/her changes into their local repositories.

See these [pages](https://github.com/git-guides) for a more exhaustive and authoritative treatment of Git.

## The Git workflow

This section gives a overview of how developers use Git. Before using Git on your computer, [download](https://git-scm.com/downloads) and install it.

### Creating a local Git repository

You can designate any directory in your computer as a Git repository. In order to do so, open Git Bash in the desired directory and run the `git init` command. This command creates a _local repository_ for you with a default _branch_ called `master`. A `.git` subdirectory also appears in the directory; this directory is used by Git for repository management. Users never need to view or modify the contents in this directory.

???+ info
    **The new `main` and the old `master` branches in GitHub**

    A Git repository has to start with an initial or default branch. Traditionally, it used to be called the `master` branch. But due to some [cultural controversies](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main) with the name, GitHub has renamed its new repository default branch name to `main`; when you create a new repository in GitHub, its default branch is `main`, instead of the old `master`.

    But the Git desktop client still uses `master` as the default branch name when you create a local repository with it (with the `git init` command). The change in the GitHub default branch name causes a problem when you add as GitHub repository as its remote: when you push to GitHub, changes are pushed to the `master` branch, instead of the `main` branch. As a remedy, you can rename the `master` branch to `main` before adding remote or pushing: `git branch -m main`.

After creating a repository, you have to set your user name and email address with the following commands. The username and email address tell Git it is you who is working in the repository and they are associated with your commits.

```
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
```

???+ info
    **The `--global` flag in the `git config` command**

    The `--global` flag in the `git config` command is optional. If you set the flag, the options you are setting becomes global in your computer, that is all the repositories you create in future in your computer uses these config values (e.g. username and email address), you don't need to set them again. See this [resource](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git) for a detailed discussion.

After setting the username and email address, you have a working _local repository._ You can start working in your repository: staging, committing, etc.

### Setting up Git remotes

The changes you make in your repository, that is your commits, remain local until you push them to a _remote_, a shared central repository. For that your have to create a remote repository in GitHub or in any other such provider (e.g. [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/), etc). After creating the repository in GitHub, copy its link and associate it as a remote in your local repository with the following command:

<div class="annotate" markdown>
```
git remote add origin(1) https://github.com/OWNER/REPOSITORY.git(2)
```
</div>

1. Name of the remote. A local repository may have multiple remotes with their unique names; the default remote name is `origin`.
2. Link to the remote repository. You can find it in the repository webpage.

Once you have associated a remote with your local repository, you can push your commits to it so that your changes are visible to others with access to the same remote repository. You may never need to associate your repository with a remote if you don't want to share your work with others.

### Creating local repositories with Git clone

Sometimes, you know from the beginning that you want collaboration in the repository you want to start. In that scenario, you don't necessarily need to create a local repository first and associate a remote later. Instead you can create the remote repository first in GitHub and then copy it into your computer with the Git clone command and start working in it.

```
git clone https://github.com/github/training-kit.git
```

This command creates the repository on your computer and copies all the contents from the remote repository. It also automatically sets the remote repository as the `origin` remote; you don't need to do it manually.

You can use Git clone when you want to work on an existing remote repository created by someone else.

## Git ignore

Git continually tracks every file and directories under its repository directory. If a file is already _tracked_ (staged once with the `git add` command), it tracks the _changes_ that took place within it; it treats other files and directories as _untracked_ and assumes they will be tracked eventually.

However, in a repository, some files' and directories' histories are neither important nor of any interest to the collaborators, thus they do not deserve versioning. Still, Git keeps treating them as untracked, causing confusion to developers when they want to check for changes before committing. Developers are overwhelmed by the list of untracked files, and they might stage unwanted files and commit them by mistake. The repository user has to mark such files and directories as to be ignored in a file called `.gitignore`, usually at the repository root. Here follows an example Git ignore file.

<div class="annotate" markdown>
```txt
node_modules/ (1)
some-file.txt (2)
some-dir/sub-dir/another-file.txt (3)
*.png (4)
```
</div>

1. Ignore the `node_modules` subdirectory, all files and sub-directories within it.
2. Ignore the specific file `some-file.txt` at the project root.
3. Ignore the specific file `another-file.txt` in the `some-dir/sub-dir/` subdirectory.
4. Ignore all `png` files in the repository.

Consult this [resource](https://www.atlassian.com/git/tutorials/saving-changes/gitignore) for further details on Git ignore.
