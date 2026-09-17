# Penny Deployment Manifest

> **Status: BLOCKED — production target must be confirmed**
>
> This file is the source of truth for Penny deployment identity. Read it before editing, committing, syncing, or deploying Penny. A production deployment is not authorized while any field marked `REQUIRED` or `UNCONFIRMED` remains unresolved.

## Project identity

| Field | Value |
|---|---|
| Project | Penny by Incyte Works |
| Project type | Static landing page / product page |
| Penny source repository | `simplyrylo413/Penny` |
| Source branch | `main` |
| Source entry point | `index.html` |
| Source assets | `assets/**` |
| Intended production URL | `https://incyte.works/penny/` |
| Deployment scope | Penny page and Penny-specific assets only |

## Production target

| Field | Value |
|---|---|
| Full-site deployment repository | `UNCONFIRMED` — expected candidate: `anythinggoessolutions/Incyte-Works` |
| Production branch | `UNCONFIRMED` |
| Penny destination directory | `UNCONFIRMED` |
| Netlify site name | `REQUIRED` |
| Netlify site ID | `REQUIRED` |
| Netlify team/account | `REQUIRED` |
| Production domain | `https://incyte.works` |
| Production route | `/penny/` |

## Repository roles

- `simplyrylo413/Penny` is Penny's standalone **source repository**.
- It must not be assumed to be the repository that deploys the entire `incyte.works` website.
- The repository or complete bundle that owns `https://incyte.works` must be identified before production deployment.
- Penny files may be synced into the confirmed full-site project only after reviewing the changed-file list.

## Hard deployment rules

1. **Never deploy this standalone repository directly over the Netlify site serving `incyte.works`.** A Netlify production deploy replaces the site's deployed bundle; it is not a file-level or page-only upload.
2. **Never deploy until all fields in “Production target” are confirmed.**
3. Before any production write, state and verify:
   - source repository and branch;
   - full-site deployment repository and branch;
   - Penny destination directory;
   - Netlify team/account, site name, and immutable site ID;
   - production domain and route;
   - exact files that will change.
4. Penny work must be limited to the Penny destination directory and Penny-specific assets. Do not modify unrelated Incyte pages unless explicitly requested.
5. Do not use a Netlify site selected only by a similar name. Match the immutable Netlify site ID.
6. Do not use conversation memory alone for deployment identity. Read this manifest and verify the current Git remote and Netlify target.
7. Do not deploy if the local checkout is dirty with unrelated changes.
8. Do not include secrets, tokens, credentials, or local environment files in commits or deploy bundles.

## Required deployment workflow

### 1. Verify source

- Confirm the active source is `simplyrylo413/Penny` on `main`.
- Pull or fetch the latest source before editing.
- Review `git status`, `git remote -v`, and the current branch.
- Preview `index.html` locally and test responsive behavior.

### 2. Review Penny changes

- List every changed file.
- Confirm all changes belong to Penny.
- Check that referenced files exist under `assets/**`.
- Check links, navigation, forms, animations, and mobile layout.
- Commit only the intended Penny files.

### 3. Sync into the confirmed production project

- Open the confirmed full-site deployment repository or complete production bundle.
- Sync only the approved Penny page and Penny-specific assets into the confirmed Penny destination directory.
- Preserve the rest of the Incyte site.
- Review the resulting full-site changed-file list before building.

### 4. Build and verify the complete site

- Run the production project's documented install and build commands.
- Verify the build output includes both the Incyte homepage and the Penny route.
- Test at minimum:
  - `/`
  - `/penny/`
  - a representative existing non-Penny route
- Stop if the root site disappears, unrelated routes change, or the Penny path resolves incorrectly.

### 5. Pre-deploy declaration

Before deploying, report this exact checklist with resolved values:

```text
SOURCE REPO:
SOURCE BRANCH:
SOURCE COMMIT:

DEPLOY REPO OR BUNDLE:
DEPLOY BRANCH:
PENNY DESTINATION:

NETLIFY TEAM/ACCOUNT:
NETLIFY SITE NAME:
NETLIFY SITE ID:

PRODUCTION DOMAIN:
PRODUCTION ROUTE:
FILES CHANGED:
BUILD RESULT:
```

If any value is missing or inconsistent with this manifest, stop.

### 6. Deploy and verify

- Deploy the complete validated production output to the confirmed Netlify site ID.
- Verify `https://incyte.works/` still loads correctly.
- Verify `https://incyte.works/penny/` loads the intended Penny version.
- Check desktop and mobile rendering.
- Record the source commit, production commit if different, Netlify deploy ID, deployment time, and verification result.

## Rollback

If production verification fails:

1. Stop further deployments.
2. Restore the last known-good Netlify production deploy.
3. Verify both `/` and `/penny/`.
4. Revert only the faulty Penny integration commit when needed; do not discard unrelated work.
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

- Exact Netlify team/account
- Exact Netlify site name
- Exact immutable Netlify site ID
- Confirmed full-site deployment repository, if used
- Confirmed production branch
- Confirmed destination directory for Penny inside the full-site project
- Confirmed sync/deployment method
