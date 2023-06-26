---
title: "Branches"
teaching: 15
exercises: 15
questions:
- "Why use branches?"
- "How do we use branches?"
objectives:
- "Be able to create and merge a branch"
keypoints:
- "Branches allow team members to work on code without impacting the work of other developers or users"
- "Create a new branch with the git checkout -b command, for example: git checkout -b my_branch"
- "Change to another branch with the git checkout command, for example: git checkout my_other_branch"
- "Merge my_branch into the current branch with with the git merge command, for example: git merge my_branch"
- "The difference between merging and rebasing branches"
---

## About Branches

Branches are independent development lines. Working independently, you can likely get away with using git without creating any branches, as in the first diagram in the figure below. However, when you begin to work with others, branches allow team members to work on the code without impacting the work of other developers or users.

![Figure showing three graph diagrams representing different repository states. Each is a graph consisting of vertices (circles) and directed edges (arrows) where each horizontal path is a branch. The first shows a single path representing a repository with a single main branch, the second has two branches, a main and a feature branch, and the third has three branches, a main and two feature branches.](../fig/branches/branches.png){:width="75%"}
*These graph diagrams show repositories with different numbers of branches. The vertices, or circles, in these graphs show different commits, and each horizontal path is a branch. The first shows a repository with 1 main branch, the second a repository with 1 main and 1 feature branch, and the third repository 1 main and 2 feature branches.*

Branches can have a few different purposes. Branches created to develop a specific feature are referred to as feature branches, and are often short-lived. Branches can also be used for longer-term purposes, such as having separate development and production branches. How you organize and use branches in your project is referred to as a branching strategy, which we will cover more when we talk about git workflows.

Changes made in one branch can be brought into another branch with a merge. For example, when a feature branch is completed it may be merged into the main branch. And, if while you are working on a feature branch the main branch changes, you can merge the changes from the main branch into your feature branch while you are still working.

## How to Work with Branches

### Creating Branches

You can create a branch on your local clone of the repository. If didn't just clone the repository it is always good to make sure you have any recent changes to the main branch by checking out the main branch and running "git pull":

```bash
git checkout main
git pull
```

Then, to create a branch we can run:

```bash
git checkout -b my_new_branch
```

This will create the branch `my_new_branch` and move you to the new branch. If you run `git status` at this point it will display `On branch my_new_branch`. Making and committing any changes will only update `my_new_branch`.

![Figure showing the process of creating a branch. First a graph diagram of a repository is shown with two commits on the main branch. To the left is an arrow with the text "git checkout -b my_branch" followed by the same repository with the new feature branch added. A smiley face is used on each diagram to show where you are in the repository, the first has it on the second commit in the main branch, the second on the feature branch.](../fig/branches/create_branch.png){:width="75%"}
*Creating a new branch. When you run `git checkout -b my_branch` your new branch gets created and checked out, meaning you are now on your new branch (represented by the smiley face). Any commits you make will be on this branch until you checkout another one.*

![Figure creating commits on a branch. First a graph diagram of a repository is shown with two commits on the main branch and one on a feature branch. To the left is an arrow with the text "git commit (x2)", followed by the same repository with to additional commits on the feature branch. A smiley face is used on each diagram to show where you are in the repository, each on the last commit on the feature branch.](../fig/branches/commit_branch.png){:width="75%"}
*Every time you run the `git commit` command the commit will be added to your current branch.*

The first time you push your branch to the remote repository, you will need to publish the branch by running run:

```bash
git push --set-upstream origin my_new_branch
```

After this any commits can be pushed with a simple `git push`.

### Changing Branches

If you need to switch to another existing branch you can use the `git checkout` command. For example, to switch back to the main branch you can run:

```bash
git checkout main
```

Remember, if you aren't sure which branch you are on you can run `git status`. It is good practice before you start making changes to any of your files to check that you are on the right branch with `git status`, particularly if you haven't touched the code recently.

![Figure showing the process of changing, or checking out a branch. First a graph diagram of a repository is shown with two commits on the main branch and three on the feature branch. A smiley face is on the third commit of the feature branch to show the current location. To the left is an arrow with the text "git checkout main" followed by the same repository with the smiley face now on the second commit in the main branch.](../fig/branches/checkout_branch.png){:width="85%"}
*Switching branches using `git checkout`.*

### Merging Branches

Bring the changes from one branch into another branch by merging them. When you merge branches, changes from the specified branch are merged into the branch that you currently have checked out. For example,

```bash
git checkout my_new_branch
git merge main
```

will merge any changes introduced to `main` into the `my_new_branch`. Merging in this direction is especially useful when you've been working on `my_new_branch` for a while and `main` has changed in the meantime.

![Figure showing the process of merging the main branch into the feature branch. First a graph diagram of a repository is shown with a main and feature branch. The feature branch with three commits splits off the main branch after two commits, and the main branch has an additional two commits after the split. A smiley face is on the third commit of the feature branch to show the current location. Below is an arrow with the text "git merge main" followed by the same repository with a new arrow from the last commit on the main branch to a new commit on the feature branch, showing the changes from the main branch have been merged into the changes on the feature branch.](../fig/branches/merge_into_branch.png){:width="60%"}
*Merging new commits from the main branch into the feature branch with `git merge main`.*

When development is complete on `my_new_branch`, it would be merged into `main`:

```bash
git checkout main
git merge my_new_branch
```

![Figure showing the process of merging the feature branch into the main branch. First a graph diagram of a repository is shown with a main and feature branch. The feature branch with three commits splits off the main branch after two commits. A smiley face is on the second commit of the main branch to show the current location. Below is an arrow with the text "git merge my_branch" followed by the same repository a new commit on the main branch with two arrows from the main and feature branches, showing the changes from the feature branch have been merged into main branch.](../fig/branches/merge_into_main.png){:width="50%"}
*Merging new commits the feature branch into the main branch with `git merge my_branch`.*

Git will do its best to complete the merge automatically. For example, if none of the changes have happened in the same lines of code, things will usually merge cleanly. If the merge can't complete automatically, this is called a merge conflict. Any conflicts in the files must be resolved before the merge can be completed.

## Activity

Everyone:

- Create a new branch in your local clone
- Publish the branch to the remote repository
- Make a small change, commit, and push
- Look at the remote repository, look at your change and your group's changes

Now, one by one run the following:

- git pull
- git checkout main
- git merge branch_name
- git push

Did anyone run into merge conflicts? How might this have been prevented?

## Outline

- Use of branches
  - Why use branches
    - Allows team members to work on the code without impacting the work of other developers or users (compartmentalize)
  - How to use branches (can point to other resources):
    - How to create a branch and work with it
    - How to change branches
    - How to merge a branch
  - Merge vs Rebase?

## TODO

- Merge vs Rebase
- Build out activity

{% include links.md %}
