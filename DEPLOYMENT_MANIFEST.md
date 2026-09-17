# Penny Deployment Manifest

> **Status: BLOCKED — exact Netlify site identity is still required**
>
> This file is the source of truth for Penny deployment identity. Read it before editing, syncing, committing, or deploying Penny. Do not deploy while a field marked `REQUIRED` remains unresolved.

## Confirmed project identity

| Field | Confirmed value |
|---|---|
| Project | Penny by Incyte Works |
| Canonical Penny source repository | `simplyrylo413/Penny` |
| Penny GitHub repository ID | `1366567622` |
| Penny source branch | `main` |
| Penny source entry point | `index.html` |
| Penny source assets | `assets/**` |
| Production repository | `anythinggoessolutions/Incyte-Works` |
| Production GitHub repository ID | `1333789134` |
| Production branch | `main` |
| Penny destination directory | `penny/` |
| Production entry point | `penny/index.html` |
| Production assets | `penny/assets/**` |
| Netlify publish directory | Repository root: `.` |
| Production domain | `https://incyte.works` |
| Production route | `/penny/` |
| Deployment scope | Penny page and Penny-specific assets only |

## Netlify identity

| Field | Value |
|---|---|
| Netlify account/team | Same account/team used by `anythinggoessolutions/Incyte-Works`; exact label `REQUIRED` |
| Netlify site name | `REQUIRED` |
| Netlify site ID | `REQUIRED` |
| Git-connected production repo | `anythinggoessolutions/Incyte-Works` |
| Publish behavior | Static site; no build step; publish repository root |

The Netlify connection available when this manifest was created did not expose the correct Incyte production project. Do not substitute a similarly named Netlify project. Match the exact immutable site ID.

## Deployment architecture

Penny uses two repositories with different roles:

1. `simplyrylo413/Penny` is the canonical working/source repository for Penny.
2. Approved Penny files are copied into `anythinggoessolutions/Incyte-Works/penny/`.
3. The Incyte Works repository contains the complete production site.
4. Its `netlify.toml` publishes the repository root and routes both `/penny` and `/penny/` to `/penny/index.html`.
5. Netlify deploys the complete Incyte Works site. There is no safe page-only Netlify deployment.

### Required source-to-production mapping

| Penny source | Incyte Works production copy |
|---|---|
| `index.html` | `penny/index.html` |
| `assets/**` | `penny/assets/**` |

Do not copy the Penny repository root over the Incyte Works repository root.

## Hard deployment rules

1. **Never deploy `simplyrylo413/Penny` directly over the Netlify site serving `incyte.works`.**
2. **Never deploy until the exact Netlify account/team, site name, and immutable site ID are recorded above.**
3. Use `simplyrylo413/Penny` for Penny edits and `anythinggoessolutions/Incyte-Works/penny/` for the production copy.
4. A Penny-only request authorizes changes only to:
   - `penny/index.html`;
   - `penny/assets/**`;
   - Penny-specific routing or documentation when explicitly necessary.
5. Do not modify the Incyte homepage or unrelated files for a Penny-only request.
6. Before every production deployment, state and verify:
   - source repo, branch, and commit;
   - production repo, branch, and commit;
   - exact files changed;
   - Netlify account/team, site name, and immutable site ID;
   - production domain and route.
7. Do not select a deployment target by name alone.
8. Do not rely on conversation memory alone. Read this manifest, verify both Git remotes, and verify the Netlify site ID.
9. Do not deploy a dirty working tree containing unrelated changes.
10. Do not commit credentials, tokens, local environment files, or Netlify authentication data.

## Required deployment workflow

### 1. Edit and verify the Penny source

- Work in `simplyrylo413/Penny` on `main`.
- Fetch the latest remote state before editing.
- Confirm the Git remote and current branch.
- Preview `index.html` locally.
- Test responsive layout, links, navigation, forms, and animations.
- Review every changed file and commit only Penny changes.

### 2. Sync the approved files

- Open `anythinggoessolutions/Incyte-Works` on `main`.
- Copy `index.html` to `penny/index.html`.
- Sync `assets/**` to `penny/assets/**`.
- Do not replace or delete files outside `penny/`.
- Review the production repository's changed-file list before committing.
- Confirm the synced Penny files match their canonical source.

### 3. Verify the complete production site

The production repo is a static site with no build step. Preview the complete repository root and test at minimum:

- `/`
- `/penny/`
- one representative non-Penny asset or route

Stop if the homepage disappears, an unrelated file changes, or the Penny route resolves incorrectly.

### 4. Pre-deploy declaration

Before deploying, report this checklist with resolved values:

```text
PENNY SOURCE REPO: simplyrylo413/Penny
PENNY SOURCE BRANCH: main
PENNY SOURCE COMMIT:

PRODUCTION REPO: anythinggoessolutions/Incyte-Works
PRODUCTION BRANCH: main
PRODUCTION COMMIT:
PENNY DESTINATION: penny/

NETLIFY ACCOUNT/TEAM:
NETLIFY SITE NAME:
NETLIFY SITE ID:

PRODUCTION DOMAIN: https://incyte.works
PRODUCTION ROUTE: /penny/
FILES CHANGED:
FULL-SITE VERIFICATION RESULT:
```

If any value is missing or inconsistent with this manifest, stop.

### 5. Deploy and verify

- Deploy the complete validated Incyte Works repository to the confirmed Netlify site ID.
- Verify `https://incyte.works/` still loads correctly.
- Verify `https://incyte.works/penny/` loads the intended Penny version.
- Check desktop and mobile rendering.
- Record the commits, Netlify deploy ID, deployment time, and verification results.

## Rollback

If verification fails:

1. Stop further deployments.
2. Restore the last known-good Netlify production deploy.
3. Verify both `/` and `/penny/`.
4. Revert only the faulty Penny integration commit if needed; preserve unrelated work.
5. Record the rollback deploy ID and Git commit.

## Deployment record template

| Field | Value |
|---|---|
| Date/time | |
| Penny source commit | |
| Production commit | |
| Netlify deploy ID | |
| Deployed by | |
| Homepage verified | |
| Penny route verified | |
| Mobile verified | |
| Rollback target | |
| Notes | |

## Information still required

- Exact Netlify account/team label
- Exact Netlify site name
- Exact immutable Netlify site ID
