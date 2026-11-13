# Credential configuration and remaining owner action

This isolated security change replaces embedded credential/account-specific settings
with process-environment configuration and prevents the affected integration from
using a missing value. `.env.example` lists names only; no `.env` loader is added.
Set variables through your operating system or secret manager before starting the app.

Any formerly valid exposed credential still requires owner revocation/rotation.
Removing a literal from a new commit does not revoke it or remove Git history.
This branch does not rotate credentials, rewrite history, remove tracked databases,
delete personal records, or make the application generally safe for public deployment.

Sentinel still has a tracked populated account database and insecure authentication/
OTP behavior. The ignore rule only prevents new untracked copies; it does not untrack
or sanitize existing data. Data-owner review and separately approved cleanup are required.
