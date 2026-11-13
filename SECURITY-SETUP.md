# Security setup and required owner actions

This security branch removes the embedded SMTP account and password from the current
application source. Supply `SMTP_EMAIL` and `SMTP_PASSWORD` through the operating
system, deployment platform, or a secret manager. The application does not load
`.env` automatically, and populated `.env` files must not be committed.

The signup email path returns a service-unavailable response when SMTP configuration
is absent.

## Historical exposure that still requires owner action

An SMTP account identifier and credential-like password existed on the public default
branch and remain in Git history. The owner must:

1. Revoke the exposed SMTP or app password and issue a new, least-privilege credential.
2. Review the mail account's sign-in, sent-message, and security activity.
3. Store any replacement only in deployment secrets or local process configuration.
4. Review GitHub secret-scanning alerts and provider audit logs for unauthorized use.

## Committed account database

`signup.db` contained account/contact records. This branch removes the database from
the current branch tip and ignores future local copies. The deletion does not remove
the database from existing commits, forks, clones, pull-request refs, or caches.

The data owner must determine the provenance and sensitivity of those records, follow
applicable institutional or legal notification/retention requirements, and decide
whether coordinated history cleanup is required. Do not restore, redistribute, or use
the committed records for demonstrations.

## Prototype authentication boundary

The `/signup`, `/signin`, and OTP routes remain an insecure prototype and must not be
deployed. Their behavior is documented in `AUTHENTICATION-REVIEW.md`. This branch does
not redesign or silently modify authentication behavior. Removing or rebuilding those
routes requires an explicit product/security decision.

## History cleanup is separate

This branch does **not** rewrite public Git history. If approved later, cleanup requires
a repository-wide history rewrite, force-push, collaborator re-clone, fork review, and
GitHub cached-object cleanup. Credential rotation and data-response decisions come first.
