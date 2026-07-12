---
title: "Introduction"
teaching: 10
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- What are the challenges for sharing code?
- How can we ensure everyone has access to the latest version?
- How can we enable equal contribution?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand how git tools and processes address challenges for collaborative code development

::::::::::::::::::::::::::::::::::::::::::::::::




You may have used git for your own projects, but how can it be used to work collaboratively on a software project?

There are a few challenges that come up when working on shared code. We want to make sure everyone has access to and knows what is the latest version, and we want to make sure everyone has an equal opportunity to contribute. It can also be difficult to keep organized while code is being actively developed and make sure everyone is on the same page about the state of the code.

We can use sites like GitHub, GitLab, BitBucket, and similar to share code with others. These sites also enable teams to contribute to software projects that they are working on together by hosting the code in a centralized location that everyone has access to. This allows everyone to view the latest version, and make updates as needed. It also provides a mechanism for outside collaborators to contribute to the project, say for open source software.

In this lesson we will be briefly going over some more advanced git tools that become essential when working collaboratively. These are branches and pull requests. In a collaborative environment, branches allow more than one person to work on the code independently, separate from the centralized main branch. Pull or merge requests provide a transparent mechanism to bring the changes made on a branch into the main branch, and encourage communication amongst the maintainers on whether the changes should be pulled in or if further changes are needed.

While technology helps, it is not the solution on its own. We will also discuss git workflows, which describe the strategy of how branches and pull requests should be used to stay organized and productive. We will show a few common workflows, and give general guidance on how to choose what will work well for your project and team.

## AI Coding Agents and Git

AI coding agents can be used to be more productive than we could be on our own. Working in a git repository will make your AI coding agent even more productive. In a git repository it has the context of the history of the code and can see how it has evolved over time. It can look at file diffs (what has changed between versions), which is helpful for context and can help you write commit messages. Testing can be more efficient because your agent can more easily compare the results of the current version with the previous version.

It is therefore just as important to have good version control and git practices, whether you are working with AI agents, human collaborators, both, or neither. AI agents can help: it can run git commands for you, write commit messages, and even make and review pull requests. You will, however, have to instruct your agent to do these things and so it is even more important for you to understand the process and know the best practices so you can make sure these are being followed. You can and should include these in your agent configuration files (CLAUDE.md, AGENTS.md, copilot-instructions.md), but be aware that your agent treats these as context, rather than rules to follow.

::::::::::::::::::::::::::::::::::::::::::  callout

## Agent Configuration Files

To test the use of agent configuration files, I made a CLAUDE.md file in my repository, listing out the git best practices that I try to follow. I was disappointed to find that these were mostly ignored, even with a short CLAUDE.md file. The following was from a conversation with Claude where I asked why this was happening.

> **Question**: The advice is to add a CLAUDE.md file to repositories so agents know how you like to work in the repo. But every time I try to test it with a new feature Claude ignores it and instead starts working. Is there something I am doing wrong?

> **Answer**: Nothing wrong on your end — this is a known gap. CLAUDE.md gets read as background context during exploration (it's just another file among several I read to understand the codebase), so its prose gets absorbed as "useful info" rather than treated as a mandatory gate that has to fire before the first edit. Imperative instructions buried in markdown compete with everything else in context, and "read the rules" and "act on the rules" aren't the same event to me unless something forces the connection — which is exactly what happened here: I read the workflow section, then went straight to editing files without treating it as a checklist to execute.

:::::::::::::::::::::::::::::::::::::::::::::::::::


## Review

Before diving in, we should review some basic terminology and commands. Note that while other options are available, we are focusing on GitHub for this lesson.

- *repository (repo)*: The project, contains all data and history (commits, branches, tags).
- *remote (repository)*: The copy of the repository on a remote server, such as GitHub. Accessible to anyone who has access to the repository on the server. Also referred to as the "central" repository.
- *local (repository)*: A copy of the repository in another place, such as a laptop or your home directory on a cluster. Generally accessible to one person.
- *commit*: Snapshot of the project, gets a unique identifier (e.g. c7f0e8bfc718be04525847fc7ac237f470add76e).
- *branch*: Independent development line. The main development line is often called main or master.
- *tag*: A pointer to one commit, to be able to refer to it later. Like a commemorative plaque that you attach to a particular commit (e.g. phd-printed or paper-submitted).
- *clone*: Copying the whole repository to your laptop - the first time. This creates a local copy of the repository. "Clone" as a noun refers to the local copy of the repository.
- *fork*: Taking a copy of a repository (which is typically not yours) - your copy (fork) stays on GitHub/GitLab and you can make changes to your copy. "Fork" as a noun refers to the your forked copy of the repository.
- *pull*: Bring changes from a remote repository to your local repository.
- *push*: Bring changes from your local repository to the remote repository.

These definitions are adapted from [Code Refinery: Concepts around Collaboration](https://coderefinery.github.io/git-collaborative/concepts/).

To use git and GitHub independently, we expect that you might follow this basic pattern:

0. Clone the repository with `git clone URL`. You can retrieve the URL for the repository you will be working in by going to its page on GitHub. Click the green "Code" button and copy the URL that is displayed. You only need to do this once.
1. Make the changes you need to make (we will talk about branching in the next section).
2. Commit your changes. This takes two steps:
    1. `git add filename`: specify which files you'd like to include in the commit. Run `git status` for a reminder of what files have changed.
    2. `git commit -m "Commit message"`: make the commit. Include a short but descriptive commit message.
3. Push your changes to the remote repository with `git push`.

A note about git integrations: You may find that your IDE has git built in allowing you to use the GUI instead of running the commands we talk about here. In this lesson we are focusing on the command line git commands, since they should be universal across any system you use. After this lesson we encourage you to use what you are most comfortable with, and the commands we cover will also help you better understand the functionality of your IDE git integration.

## Activity

Verify that you can access your GitHub account, have git installed on your computer, and can authenticate with GitHub from your computer, either using gh auth, ssh keys, or using your preferred GUI application.

Work in small groups of 3-4. Have one person in your group create a repository from the [provided template](https://github.com/INTERSECT-training/intersect-training-practice). To create a repository from the template click "Use this Template" in the top right, then "Create a New Repository". Give access to the others in your group. Everyone should accept the invitation to collaborate and then create a local clone with `git clone`. We will use this repository for the remainder of the exercises in this section.

## Additional Resources
- [Code Refinery: Concepts around Collaboration](https://coderefinery.github.io/git-collaborative/concepts/)
- [Code Refinery: Introduction to Version Control](https://coderefinery.github.io/git-intro/)
- [Slide version of this lesson](https://github.com/INTERSECT-training/collaborative-git/blob/main/presentations/CollaborativeGit.pdf)





::::::::::::::::::::::::::::::::::::: keypoints 

- Challenges for sharing code include making sure everyone has access to the latest version, everyone can contribute equally, keeping organized, and making sure everyone has equal opportunity to contribute.
- Branches and pull/merge requests provide mechanisms for individuals to work on the code independently and then integrate those changes into the main codebase.
- Git workflows are used to stay organized and productive.

::::::::::::::::::::::::::::::::::::::::::::::::