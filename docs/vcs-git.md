# Version Controlling with Git

Git serves two major purposes: _history tracking_ and _collaboration._ When a developer works on a project for a long period, it is difficult for him/her to memorize the changes the project files have gone through. Git preserves the file histories as _commits._ It helps developers go through a files history or the entire repository history whenever necessary.

Any complex project requires team collaboration. When a team of developers work together on the same project, there must be some means to keep their work in sync among themselves. Git serves this purpose with Git _remotes_, a central Git repository. Developers finish their tasks on their local repositories and _push_ their changes to the remote repository when they are done so that other developers can _pull_ his/her changes into their local repositories.

???+ info
    **The new `main` and the old `master` branches in GitHub**

    A Git repository has to start with an initial or default branch. Traditionally, it used to be called the `master` branch. But due to some [cultural controversies](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main) with the name, GitHub has renamed its new repository default branch name to `main`; when you create a new repository in GitHub, its default branch is `main`, instead of the old `master`.

    But the Git desktop client still uses `master` as the default branch name when you create a local repository with it (with the `git init` command). The change in the GitHub default branch name causes a problem when you add as GitHub repository as its remote: when you push to GitHub, changes are pushed to the `master` branch, instead of the `main` branch. As a remedy, you can rename the `master` branch to `main` before adding remote or pushing: `git branch -m main`.

## Git ignore

Git continually tracks every file and directories under its repository directory. If a file is already _tracked_ (staged once with the `git add` command), it tracks the _changes_ that took place within it; it treats other files and directories as _untracked_ and assumes they will be tracked eventually.

However, in a repository, not all files' history are important or not of any interest to the collaborators, thus do not deserve versioning. Still Git keeps treating them as untracked unless they are marked as _ignored._ It causes confusion to developers when they want to check for changes before committing; unwanted files might be staged and committed by mistake. User has to mark such files and directories as to be ignored in a file called `.gitignore`, usually at the repository root. Here follows an example git ignore file.

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

Consult this [resource](https://www.atlassian.com/git/tutorials/saving-changes/gitignore) for further details on git ignore.
