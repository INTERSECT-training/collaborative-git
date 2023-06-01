---
title: "Git Workflows"
teaching: 30
exercises: 0
questions:
- "What is a git workflow?"
- "Why use a git workflow"
objectives:
- "Know why to use a git workflow"
- "Understand some of the most common git workflows, and when you should deviate"
- "Be able to choose or design a workflow that meets your group's needs"
keypoints:
- "The definition of a git workflow TODO"
- "Git workflows keep a team organized and on the same page by helping them understand what state the code is in"
---

## Outline

- Using and designing workflows
  - What is a git workflow?
  - Why use a git workflow?
    - Keeping organized when working on a team, staying on the same page, communicating
    - Help team members understand what state code is in
  - Basic terminology and considerations
    - Branching strategies
    - What’s stable under what conditions, what’s tested
    - Testing strategies (expanded in other lessons)
    - Branch lifetimes
  - Some common workflows, when/why to use each
    - David has a colleague with a good resource we can point to
  - Communicating this to your collaborators
    - Including the workflow in the CONTRIBUTING document
    - Conventions for branch naming
  - How to enforce your workflow
    - Branch protections
    - Limiting who can push/merge
    - Testing & review requirements

## Activity

We provide a base repository to each group that each group member creates a local copy of the repository (either by forking or cloning). Students should decide which workflow to use and set up their repository accordingly. Start a contributor guide that explains the layout and rules.

{% include links.md %}
{% comment %} https://docs.gitlab.com/ee/topics/gitlab_flow.html {% endcomment %}
{% comment %} https://www.atlassian.com/git/tutorials/comparing-workflows {% endcomment %}
