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
      - '**/locale/**'
      - '**/translations/**'
      - '**/i18n/**'

jobs:
  translation-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
    - name: Algebras Translation Status
      uses: algebras-ai/locale-checker-action@main
        # Optional: specify a file pattern
        # with:
        #   file_pattern: "src/locale/**/*.json"
        #   only-missing: true
        # Optional: only report missing keys (ignore outdated ones)
        # with:
        #   only-missing: true

## Inputs

- `file_pattern` (optional): Specify a glob pattern for your localization files (e.g., `src/locale/**/*.json`).
- `only-missing` (optional): If set to `true`, the action will only report missing translation keys and ignore outdated keys. Default is `false`.

## Example Outputs

### Success Case
```
Loaded configuration: /path/to/.algebras.config
Available languages: en, fr, es, de
Source language: en
Running CI checks...
Scanning for translation files...
Found files by language: {'en': ['src/locales/en.json'], 'fr': ['src/locales/fr.json'], 'es': ['src/locales/es.json'], 'de': ['src/locales/de.json']}

Processing languages: fr, es, de
All translation keys are up-to-date! ✅
::notice::Translation status check passed! All translations are up-to-date.
```

### Failure Case
```
Loaded configuration: /path/to/.algebras.config
Available languages: en, fr, es, ru
Source language: en
Running CI checks...

CI Check: Found issues with translations:

Language 'ru': Missing keys:
  - Features.feature6_description
  - Features.feature6_title
  - TodoForm.some_new_key_to_test

Language 'ru': Outdated keys:
  - Features.feature1_title (Source updated: 2024-10-08, Target: 2024-10-03)
  - Hero.title (Source updated: 2024-10-07, Target: 2024-10-03)

::error::Translation status check failed! Some translations are missing or outdated.
Error: Process completed with exit code 1.
```