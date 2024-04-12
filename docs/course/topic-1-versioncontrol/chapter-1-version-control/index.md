---
title: Chapter 1 -  Introduction to Version Control
layout: default
parent: Topic 1 - Cooperative Software Development
has_toc: false
nav_order: 1
---

# Chapter 1 - Introduction to Version Control
## What is version control?
Version control is **a system that records changes to a file or set of files over time** so that you can recall specific versions later. It's a critical tool in modern software development, allowing developers to work collaboratively, track every modification, and revert to previous states if necessary.

> **Example Scenario**
>
> Armine and Tigran are part of a software development team tasked with creating a new mobile application. Armine is tasked with refining the user authentication system, while Tigran is implementing an innovative feature that allows users to share media within the app.
>
> **Without Version Control**: If Armine and Tigran are editing the same file, Tigran's latest upload could accidentally overwrite the changes Armine made, resulting in a loss of progress and potential conflicts in the code.
>
> **With Version Control**: Armine and Tigran can work on their updates concurrently without the risk of interfering with each other's contributions. Here's how it unfolds:
>
> - Independently, they make their changes and commit their updates to the version control system, each creating a new version in the repository.
>
> - The version control system alerts them to the presence of new, separate updates, signaling that a merge of changes is necessary.
>
> - Together, they examine the differences, carefully integrate their respective code changes, and commit the unified version to the repository.
>
> - Should an issue arise with the authentication update, Armine can revert her portion of the code to a previous state without disrupting Tigran's feature, thanks to the version history maintained by the system.

A common tool for version control is GitHub. GitHub allows you acts as a central hub for all of the different versions of your code, kind of how in google docs you can see the history of your changes. Though there are many different systems for version control, we will be learning using GitHubs features. The syntax and user interface of different products are different, but the core elements are the same. 