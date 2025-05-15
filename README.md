# Algebras Translation Status Action

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A GitHub Action to check the status of your application's translations using the [Algebras CLI](https://github.com/algebras-ai/algebras-cli).

## Overview

This action is designed for NextJS projects with i18n framework for localization. It performs a health check to ensure all translations are in sync across different languages. If any translations are missing or outdated, the action will fail, highlighting issues in your CI/CD pipeline.

## Usage

Create a workflow file in your repository (e.g. `.github/workflows/check-translations.yml`):

```yaml
name: Check Translations

on:
  pull_request:
    branches: [ main ]
    paths:
      - '**.tsx'
      - '**.ts'
      - '**/locale/**'
      - '**/translations/**'
      - '**/i18n/**'

jobs:
  translation-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Check translation status
        uses: algebras-ai/algebras-status-action@v1
        # Optional: specify a file pattern
        # with:
        #   file_pattern: "src/locale/**/*.json"
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `file_pattern` | Optional file pattern for localization files | No | "" |

## How It Works

The action:

1. Sets up Python on the runner
2. Installs the Algebras CLI
3. Runs `algebras status` to check translation health
4. Fails if any translations are missing or outdated

## About Algebras AI

[Algebras AI](https://algebras.ai) provides powerful AI-driven localization tools for applications. This action focuses on health checking your translations, not on generating translations.

## License

This project is licensed under the MIT License. 