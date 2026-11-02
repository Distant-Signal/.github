# Security policy

This policy covers every repository in the Distant Signal organisation, the
site at https://ds.cursed.solutions/, its API (including access delegated to
connected apps) and the container images and Helm charts the project
publishes.

## Reporting a vulnerability

Please report vulnerabilities privately, through GitHub's private
vulnerability reporting: open the repository's **Security** tab and choose
**Report a vulnerability**. If you aren't sure which repository is affected,
report it on the main repository,
[Distant-Signal](https://github.com/FasterSpeeding/Distant-Signal/security/advisories/new).

Please don't open a public issue, pull request or discussion for a
vulnerability.

A useful report says:

- what is affected (a page, an API route, an image or a chart);
- how to reproduce it, step by step;
- what an attacker could do with it.

## What to expect

Distant Signal is a personal project run by one person, so there is no
formal response time. You'll get an acknowledgement as soon as the report
has been read, and updates while it is being fixed. Once a fix is deployed,
the advisory is published, crediting you unless you'd rather stay
anonymous.

## Supported versions

Only what is currently deployed, built from the latest `main`, is
supported. There are no maintained release branches.

## Scope

Please test only against your own account, and don't degrade the service
for other users: no denial-of-service, load testing or automated scanning
of the production site. Reports about third-party data sources the project
reads from belong with those providers.
