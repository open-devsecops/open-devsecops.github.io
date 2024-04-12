---
title: Chapter 3 - Git Intermediate Concepts
layout: default
parent: Topic 1 - Cooperative Software Development
has_toc: false
nav_order: 3
---

# Chapter 3 - Intermediate Concepts
## Branching Strategies

Branching in Git allows multiple developers to work on different tasks simultaneously without interfering with each other's work. Here are some common strategies:

- **Feature Branching**: Create branches for each new feature to keep changes isolated from the main codebase.
- **Release Branching**: Maintain separate branches for release candidates, allowing for bug fixes and preparation for a production release.
- **Hotfix Branching**: Quickly create branches to address urgent bugs in production code.

Each strategy serves a specific purpose and can be chosen based on the team's workflow and project requirements.

## Types of Merging

Merging is the process of integrating changes from one branch into another. Git offers several types of merges:

- **Fast-Forward Merge**: Moves the base branch pointer forward until it equals the feature branch's pointer.
- **Three-Way Merge**: Used when two branches have diverged. A new "merge commit" is created to join the two histories.
- **Squash Merge**: Combines all feature branch commits into a single commit for a cleaner history when merging into the base branch.

Understanding the implications of each merge type is crucial for maintaining a coherent project history.

## Important Concepts

Other intermediate concepts of version control include:

- **Pull Requests (PRs)**: PRs are a feature of hosting services like GitHub and GitLab. They let you tell others about changes you've pushed to a branch in a repository.
- **Workflows**: Workflows like Gitflow and GitHub Flow offer structured methods for branching and merging that fit different types of projects and development cycles.
- **Rebasing**: Rebasing is an alternative to merging, rewriting the commit history to produce a straight, linear progression of changes.
- **Stashing**: Save uncommitted changes in a stack while you switch branches.

By mastering these concepts, developers can collaborate more effectively and maintain a clean, functional codebase.