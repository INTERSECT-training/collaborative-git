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