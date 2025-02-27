# Learning GitHub Actions

GitHub Actions is a powerful automation tool that allows you to create custom workflows for your software development lifecycle. This guide will help you get started with GitHub Actions.

## Table of Contents
1. [Introduction](#introduction)
2. [Key Concepts](#key-concepts)
3. [Creating Your First Workflow](#creating-your-first-workflow)
4. [Examples](#examples)
5. [Resources](#resources)

## Introduction
GitHub Actions enables you to automate tasks within your software development lifecycle. You can create workflows that build, test, and deploy your code right from GitHub.

## Key Concepts
- **Workflow**: A configurable automated process made up of one or more jobs.
- **Job**: A set of steps that execute on the same runner.
- **Step**: An individual task that can run commands or actions.
- **Runner**: A server that runs your workflows when triggered.

## Creating Your First Workflow
1. **Create a `.github/workflows` directory** in your repository.
2. **Add a YAML file** (e.g., `main.yml`) to define your workflow.

```yaml
name: CI

on: [push, pull_request]

jobs:
    build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Set up Node.js
            uses: actions/setup-node@v2
            with:
                node-version: '14'
        - name: Install dependencies
            run: npm install
        - name: Run tests
            run: npm test
```

## Examples
### Example 1: Deploy to GitHub Pages
```yaml
name: Deploy to GitHub Pages

on:
    push:
        branches:
            - main

jobs:
    deploy:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Build and Deploy
            run: |
                npm install
                npm run build
                npm run deploy
```

### Example 2: Lint and Test Python Code
```yaml
name: Lint and Test

on: [push, pull_request]

jobs:
    lint-and-test:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Set up Python
            uses: actions/setup-python@v2
            with:
                python-version: '3.8'
        - name: Install dependencies
            run: pip install -r requirements.txt
        - name: Lint code
            run: flake8 .
        - name: Run tests
            run: pytest
```

## Resources
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [Learning Lab: GitHub Actions](https://lab.github.com/githubtraining/github-actions:-hello-world)

Happy automating!