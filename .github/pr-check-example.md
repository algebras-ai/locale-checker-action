# Example: How the Translation Status Check Appears in GitHub

When all translations are up-to-date:

![Successful Check](https://via.placeholder.com/800x100/009900/FFFFFF?text=✓+Translation+Status+Check+Passed)

When translations are missing or outdated:

![Failed Check](https://via.placeholder.com/800x400/990000/FFFFFF?text=✗+Translation+Status+Check+Failed)

## Example Error Output

```
Error: Translation status check failed! Some translations are missing or outdated.

The following translations are missing:
- en/common.json: 3 missing keys
- de/about.json: 5 missing keys
- fr/profile.json: 2 missing keys

See output above for complete details on missing translations.
```

## How to Fix

1. Run `algebras status` locally to see the missing translations
2. Add the missing translations to your locale files
3. Commit and push the changes to your PR 