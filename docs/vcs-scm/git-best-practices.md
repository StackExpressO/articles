---
layout: default
title: Git Best Practices
nav_order: 3
description: This workflow is for developers making contributions for CI/CD enabled repository
permalink: /vcs-scm/git-best-practices
---

# Get Started
{: .fs-9 }

## Best Practices - Git

- Do not push directly to master branch

  - If you need to push any changes then first create a new branch from base branch (e.g. Master). Then push your changes to the new branch. Now create a pull request to the base branch.

- Do not push credentials to repository

  - Pushing credentials to the code repository is not secure. We should keep example values in place for credentials.

  - Original secrets file

  **File Name:** secrets.yml

  ```bash
  api_username: shivam
  api_password: 5WJfC8h6Dg36kShE
  ```

  - Example secret file
  
  **File Name:** secrets.yml.example

  ```bash
  api_username: adminuser
  Api_password: badpassword
  ```
