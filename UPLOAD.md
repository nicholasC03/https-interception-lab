# GitHub upload guide

This guide covers reviewing, committing, and pushing the HTTPS lab documentation and screenshot evidence to GitHub.

Return to the [project README](README.md).

## Open the local repository

Run these commands on the computer holding your project files, rather than inside the AWS SSH session:

```bash
cd "$HOME/Desktop/Labs/Lab 1- HTTPS MitM/https-interception-lab"
git status
git remote -v
```

If your copy is elsewhere, change the path. The intended repository is https://github.com/nicholasC03/https-interception-lab.

## Synchronize before editing

The GitHub copy includes changes made directly through GitHub. First commit reviewed local changes or save them elsewhere so the working tree is clean, then run:

```bash
git switch main
git pull --ff-only origin main
```

If Git reports divergent history, stop and inspect it rather than force-pushing.

## Review publication contents

Publish documentation, the fictional test page, and reviewed screenshots. Keep raw captures, proxy exports, credentials, SSH keys, proxy CA material, and VM images private. Ignore rules do not protect files that Git already tracks.

```bash
git status --short
git ls-files
```

Inspect screenshots for tokens, passwords, private keys, and unrelated personal information. Confirm these paths exist:

- `README.md`, `UPLOAD.md`, `breakdown.md`, and `.gitignore`
- `site/index.html` and `notes/observations.md`
- `evidence/README.md`
- The six numbered PNG screenshots in `evidence/`

## Stage and inspect

Stage the intended files explicitly:

```bash
git add README.md UPLOAD.md breakdown.md .gitignore site/index.html notes/observations.md evidence/README.md
git add evidence/00-vm-connectivity.png evidence/01-valid-origin-tls.png evidence/02-direct-tls-wireshark.png evidence/03-untrusted-proxy-rejected.png evidence/04-trusted-proxy-flow.png evidence/05-proxy-wire-capture.png
git diff --cached --stat
git diff --cached --check
git diff --cached
```

The text diff does not show screenshot contents; inspect those separately. To remove an unintended file from staging without deleting it, use `git restore --staged -- PATH_TO_FILE`.

## Commit and push

After reviewing the staged changes:

```bash
git commit -m "docs: update HTTPS lab documentation and evidence"
git push origin main
```

For separate commits per file, stage one changed file at a time and use a message describing that change. GitHub shows a file's latest modifying commit beside its name. Screenshot descriptions in `evidence/README.md` update that index's commit message, not the messages displayed beside the PNG files.

If HTTPS authentication asks for a password, use a GitHub personal access token authorized for this repository instead of your account password. Enter it only at the authentication prompt; never put it in a remote URL, command, screenshot, or committed file.

## Verify the published result

Open the [repository](https://github.com/nicholasC03/https-interception-lab), read the rendered README, and check its links to this guide, the observations, the project brief, and each evidence screenshot.

```bash
git status
git log -1 --oneline
```

A clean working tree confirms no uncommitted local changes remain; check GitHub as well to confirm publication.
