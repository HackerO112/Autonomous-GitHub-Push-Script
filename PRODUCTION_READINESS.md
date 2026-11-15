# Production readiness assessment

Status: **local automation script; safety and cross-platform validation required**.

## Source review findings
- The original script force-pushed to an existing repository, which could overwrite remote history.
- It created new repositories as public by default.
- It staged the entire working directory without screening common credential files.

## Changes on this hardening branch
- Removed forced push; a non-fast-forward conflict now stops instead of rewriting remote history.
- Uses the authenticated GitHub CLI account rather than asking the operator to type a username.
- New repositories default to private and require an explicit visibility choice.
- Adds a staged-filename check for common secret/private-key files.

## Remaining release blockers
1. Add automated tests with a fake `git`/`gh` executable to cover all branches without touching real repositories.
2. Improve secret scanning beyond filenames and document that no filename filter can guarantee secret detection.
3. Validate branch names, remote ownership, dirty-tree behavior, and interrupted runs.
4. Test supported shells and operating systems; provide a dry-run mode and explicit confirmation before creating or pushing.
5. Document GitHub token scopes and least-privilege requirements.

## Release gate
Never run this script in a valuable repository until its behavior is reviewed. No automated integration test against a real GitHub account is included in this PR.
