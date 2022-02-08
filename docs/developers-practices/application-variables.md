---
layout: default
title: How to define application variables
nav_order: 3
description: Application variables usage
categories: [git, developers]
permalink: /developers-practices/application-variables
---

# Get Started
{: .fs-9 }

## How to define application variables


1. .env.example should keep the dummy values, not the real values.
1. If the mode is development then load from .env file (Not .env.example)
1. If the mode is not development then do not load from a file, expect that the application will get the env vars itself.
1. .env file should be create on dev machine taking reference from .env.example file and .env should be added in .gitignore file
