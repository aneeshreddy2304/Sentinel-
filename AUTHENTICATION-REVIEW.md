# Prototype authentication review

Sentinel's account routes are separate from the model-prediction workflow and are not
suitable for deployment. They remain in `app.py` only as documented prototype code.

## Current insecure behavior

- Signup data, including the password, is accepted through query-string parameters.
- Passwords are compared and stored as plaintext rather than password hashes.
- OTP and pending-account values are shared through process-global variables.
- OTP generation, expiration, retry limits, rate limiting, and replay protection are
  not implemented to production standards.
- Successful signin renders a page without establishing a protected server-side session.
- CSRF protection and secure account-recovery controls are absent.
- The development entry point enables Flask debug mode.

Removing the tracked `signup.db` prevents repository users from receiving the populated
records, but it does not make these routes secure. A fresh database would still be used
by the same insecure flow.

## Decision required before further code changes

Choose one path before modifying authentication behavior:

1. **Remove the prototype account feature.** Delete the signup, signin, OTP, and account
   templates/routes and present the classifier only in a local, non-authenticated demo.
2. **Rebuild authentication.** Use POST forms, password hashing, per-user expiring OTP
   records, protected sessions, CSRF controls, rate limits, secure cookies, and a proper
   database migration process.

Until that decision is approved, do not expose the Flask application publicly and do
not use real identities or credentials.
