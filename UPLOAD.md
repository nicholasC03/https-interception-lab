# Upload to GitHub

Copy this package into your existing lab folder. Preserve your original screenshots and any existing Git metadata. The included site HTML is the sample page from the brief; replace it with the actual deployed page if yours differs.

Ensure these five screenshots exist with exactly these names:

- evidence/01-valid-origin-tls.png
- evidence/02-direct-tls-wireshark.png
- evidence/03-untrusted-proxy-rejected.png
- evidence/04-trusted-proxy-flow.png
- evidence/05-proxy-wire-capture.png

For example, copy the original untrusted screenshot named `03-untrusted-proxy-rejected(2).png` to `03-untrusted-proxy-rejected.png`. Keep originals until you have confirmed the copy.

Create an empty GitHub repository named `https-interception-lab` under your account, without initializing a README, license, or gitignore. Then run from the local lab folder:

```bash
cd "$HOME/Desktop/Labs/Lab 1- HTTPS MitM/https-interception-lab"
git init -b main
git add README.md breakdown.md .gitignore UPLOAD.md site/index.html notes/observations.md   evidence/01-valid-origin-tls.png   evidence/02-direct-tls-wireshark.png   evidence/03-untrusted-proxy-rejected.png   evidence/04-trusted-proxy-flow.png   evidence/05-proxy-wire-capture.png
git status --short
git diff --cached --stat
git diff --cached --check
git diff --cached
```

Review the staged files, screenshots, and documentation. If anything unexpected is staged, unstage it before continuing. Ignore rules do not remove secrets already tracked in Git or its history. The written observations deliberately qualify details that are not independently available in the current record.

After review:

```bash
git commit -m "Document controlled HTTPS interception lab"
git branch -M main
git remote -v
```

If no origin remote exists:

```bash
git remote add origin https://github.com/NicholasC03/https-interception-lab.git
git push -u origin main
```

If origin already points to that repository, run only `git push -u origin main`. If it points elsewhere, confirm the intended repository before changing it. Use a configured credential manager or GitHub authentication flow; GitHub does not accept account passwords for HTTPS Git pushes. Never place a token in a remote URL or file.

Open the rendered GitHub README and verify every image link. If the repository already has remote commits, do not force-push; reconcile the histories first.
