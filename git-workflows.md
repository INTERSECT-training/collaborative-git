---
title: "Git Workflows"
teaching: 30
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a git workflow?
- Why use a git workflow

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Know why to use a git workflow
- Understand some of the most common git workflows, and when you should deviate
- Be able to choose or design a workflow that meets your group's needs

::::::::::::::::::::::::::::::::::::::::::::::::





## Introduction

When you are working with others in the same git repository, you'll find you'll need to come to an agreement on how you are going to work in the repository. This can include:

- How you are going to use branches
- What is considered the "latest version", or what is "production" vs "in development"
- How those branches are merged
- When you are making pull requests and into what
- Whether you are working in a single, central repository, or separate forked repositories

These questions are often answered by what we will call a git workflow. A git workflow helps you keep organized when working on a team, helps everyone stay on the same page about the state of the code, and helps enable communication. If you've ever emailed around documents you were working on with a team, you might understand the value of everyone on the team always having access to both the latest version, and any material still in progress.

When we talk about git workflows often we are really discussing is branching strategies. The branching strategy is how you are going to use branches to work with the code. This includes the purposes of each branch (ex: a feature branch vs a release branch), where a new branch is created, and how, when, and where branches are merged. Different branches and branch types will have different lifetimes as well. For example, once a feature branch has been merged it can often be deleted, however a dedicated development branch might exist for the entire project.

The git workflow should also dictate what is stable under what conditions, what is tested, and may also include testing strategies.

## Some Common Workflows

There are a few common workflows that are talked about the most. One might be better in some cases, another in others, but no one is necessarily the best in every case than any of the others. There will likely be one that best fits your application and your team's goals, but you may find you will still need to make adjustments, and that is okay.

### Centralized or Truck-Based Workflow

With a centralized workflow you only have one main branch (or trunk, borrowing terminology from SVN, another version control system). Team members work in their local clone and push commits less frequently. The central repository is meant to be "clean" and should be stable. Git will also prevent you from pushing any changes that cause conflicts. If someone else as pushed a change that conflicts with one of your local commits, git will not let you push those changes and will require you resolve the conflict locally before pushing.

A centralized workflow with a single main branch is not the best for collaborative development, although it may work okay in small teams. We mention it to give a name to a process you might already be familiar with, and as a starting point for other workflows.

### Feature Branching Workflows and GitHub Flow

Since we've covered branching, a simple extension to the centralized workflow is a Feature Branching Workflow. The main branch is like the central repository in the centralized workflow, it is meant to be clean and stable. Instead in working directly in clones of the main branch, all development is done in feature branches, where each branch is created from the main branch to develop a specific feature. The branch is published soon after it is created in the remote repository and commits are regularly pushed. This allows other developers to see the branch and any changes early. Using feature branches also allows an individual developer to work on more than one feature at a time if needed. Say you are working on developing a feature that requires some time and thought, but in the process find a bug that should be fixed immediately. You can create a new branch, fix the bug, and merge it back into the main branch without introducing any of the partially developed code you are still working on in the other feature branch.

Once the feature is complete and tested, feature branches are merged back into the main branch through Pull Requests. Any merge conflicts should be handled in the feature branch before merging. This can be done by merging any new commits from the main branch into the feature branch, handling any conflicts that emerge. The changes are discussed and reviewed in the Pull Request, and once accepted hey are merged. Once merged, the lifecycle of a feature branch is general complete and it can be deleted if it is no longer needed.

This is also known as "GitHub Flow", as it is used by the developers of GitHub for sections of their website, including their documentation. GitHub even has a [dedicated page in their documentation](https://docs.github.com/en/get-started/quickstart/github-flow) describing the workflow. It is most useful for projects that have a rolling development cycle without specific versioned releases.

### Git Flow

Git Flow is one of the most commonly used workflows. It is used for software projects that require robust, production-ready releases. It is suitable for larger teams where more than one person might work on the same feature.

Git Flow builds on a feature branching workflow, where instead of creating feature branches from the main branch, they are created from a separate permanent development branch. When a feature is complete, its branch is merged into the development branch. Individual release branches are created from the development branch, and once production-ready are merged into the main branch upon release and tagged. The main branch therefore contains only fully tested, stable, production code associated with a particular version. If the code has a bug in the main branch that needs to be fixed immediately, hotfix branches can be created off the main branched and merged directly back into the main branch without being added to the development branch or a release branch.

Git Flow was introduced with a blog post in 2010, which you can see [here](https://nvie.com/posts/a-successful-git-branching-model/) if you are interested.

### GitLab Flow

Similar to GitHub Flow, GitLab Flow gets its name because it is the workflow used by GitLab. GitLab is a bit closer to the simplicity of GitHub Flow, but is more appropriate in cases where the rolling releases of GitHub Flow are not possible. GitLab Flow is similar to Git Flow in that feature branches are not merged directly into the production branch, however instead it has a separate named production branch and the feature branches are merged into the main branch, which is more like the development branch of Git Flow. Release branches are optional, and only recommended only when software is released to the outside world.

For more information, see GitLab's article on [GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html).

### Forking Workflows

In each of these example workflows we have assumed that anyone contributing to a repository has the ability to directly push commits to a repository. However, sometimes you want to enable developers to contribute to a project without giving them access to the repository itself. In this case, a forking workflow might be suitable. Any of the workflows we've talked about already could incorporate forking. With a forking workflow individual developers create their own fork of a repository and do their development within their fork. When a feature is complete, the developer creates a Pull Request into the appropriate branch of the original repository. The owners of the repository can then approve the Pull Request at their discretion. This is how many open source projects encourage contributions.

With a forking workflow it can be easy to end up with an old version of the code, especially if it changes frequently. It can get confusing whether we are attempting to pull from or push to the fork or the original repository. Setting up remotes with easy to remember aliases makes this much easier. A "remote" is a named connection to a remote repository. You can add and remove remotes with the `git remote add` and `git remote rm` commands, respectively. For example:

```shell
git remote add upstream https://github.com/project_team/project.git
git remote add my-fork https://github.com/me/project.git
```

Here we are adding a remote called "upstream" for our central team repository and another called "my-fork" for our own fork. We can view our remotes with `git remote -v`. Now when you want to retrieve any changes from the upstream repository you can run `git fetch upstream`. To update your main branch with these changes, you would merge them into your local forked repository:

```shell
git checkout main # this is the main branch for your fork that you have cloned locally
git merge upstream/main
```

Using remotes, fetching and merging upstream changes frequently, and running commands like `git status` and `git remote -v` can help you be successful using a forking workflow. Merging upstream changes directly before making a Pull Request and ensuring there are no merge conflicts is good etiquette and will make it more likely that your Pull Request will be accepted.

## Communicating with your Collaborators

Now that you've chosen a workflow for your project, how do you communicate it? This is most often done with a CONTRIBUTING document. The CONTRIBUTING document describes the git workflow you are using, any conventions for branch naming that you have, and anything else a collaborator should know in order to contribute. It should be tailored to your project and team, and so it might also include how to run the tests for the project, requirements before creating Pull Requests, or perhaps detailed instructions for how follow the workflow if your team is less familiar with git. One of the goals of a CONTRIBUTING document is to lower the barrier to entry to contributing to a project and a good one will encourage collaboration.

## Enforcing your Workflow

There are tools that you can use to make sure everyone follows the agreed upon workflow, which can make it easier to collaborate with others. First, you can add branch protections, which will enforce certain rules for certain branches. A common one is to not allow commits directly to the main branch, requiring changes to go through a Pull Request. There are many options for branch protection that you can read about on the [GitHub web page](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches). Similarly, you can limit who on the team is able to push or merge changes into a particular branch, or in the entire repository. It is also a good idea to have testing and review requirements, particularly for production branches. These requirements and branch protections should be documented in the CONTRIBUTING document as well.

We will end with a quick note if your team works on shared systems, including clusters and HPC systems. Be careful with clones on shared drives, you never want to share a cloned repository. Each person should work within their own clone. You might also consider having additional "production" clone that is used for running. No one edits the production clone directly, it is only updated by pulling changes from the repository.

## Activity

For your group's "project" that you have been working on through this lesson discuss which workflow would work best for your team. Set up the repository as needed to support this workflow. Start a contributor guide that explains the workflow and any rules for contributing.

If time allows, discuss any projects that your group members work on collaboratively with others. Is there a specified workflow for this project? How would someone contribute to the project?

## Additional Resources

- [Code Refinery: Centralized Workflow](https://coderefinery.github.io/git-collaborative/centralized/)
- [Code Refinery: Distributed version control and forking workflow](https://coderefinery.github.io/git-collaborative/distributed/)
- [GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [Atlassian Git Tutorial: Comparing Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Atlassian Git Tutorial: Git Forks and Upstreams: How-to and a cool tip](https://www.atlassian.com/git/tutorials/git-forks-and-upstreams)
- [Slide version of this lesson](https://github.com/INTERSECT-training/collaborative-git/blob/main/presentations/CollaborativeGit.pdf)




::::::::::::::::::::::::::::::::::::: keypoints 

- A git workflow describes how a team or group of contributors is to interact with a repository
- Git workflows keep a team organized and on the same page by helping them understand what state the code is in

::::::::::::::::::::::::::::::::::::::::::::::::