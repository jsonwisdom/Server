# Security Boundary

## This repo is unaudited

`Server-master.zip` contains unknown server code, configuration, and dependencies.

The following must be true before any use:

| Check | Required |
|---|---|
| No `.env` files with live credentials | YES |
| No private keys, including hex or PEM keys | YES |
| No API tokens, passwords, or secrets | YES |
| No database connection strings with credentials | YES |
| No service account JSONs | YES |
| No hardcoded internal endpoints exposing infrastructure | YES |

## If any secret is found during extraction

1. Rotate the credential immediately.
2. Do not commit extracted files back to this repo without cleaning.
3. Treat the archive as contaminated until proven otherwise.
4. Consider restructuring this repo as normal source files so automated secret scanning can function.

## Archive-Only Pattern

Storing server code as a single zip file prevents or weakens:

- GitHub secret scanning
- dependency graph analysis
- Dependabot alerts
- normal code review
- targeted configuration audits

This should be remediated by extracting the archive into normal repository structure and removing the zip file after secrets have been verified absent.

## Boundary Rule

No deployment or production-readiness claim is valid until the archive has been extracted and scanned.

Rule: no unaudited server deployment.
