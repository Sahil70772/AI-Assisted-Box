# Step-by-step: building this assignment with GitHub

## One-time setup
1. Create a free account at github.com. Install Git (`git --version` to check).
2. `git config --global user.name "Your Name"` and `git config --global user.email "you@example.com"`
3. On GitHub: **New repository** -> name `box-selection-django` -> Public -> don't add README (you already have one).

## Connect the project
```bash
cd box_selector
git init -b main
git add .
git commit -m "Initial Django project with models and box packer"
git remote add origin https://github.com/<you>/box-selection-django.git
git push -u origin main
```
(If asked for a password, use a Personal Access Token, or run `gh auth login`.)

## Develop in small commits (reviewers read your history)
Use one branch per piece of work, then merge via a Pull Request:
```bash
git switch -c feature/packing-algorithm
# ...edit, run `python manage.py test`...
git add -A && git commit -m "Add extreme-point packer with rotations"
git push -u origin feature/packing-algorithm
```
On GitHub click **Compare & pull request** -> **Merge** -> then locally:
`git switch main && git pull`

Suggested commit sequence:
1. Project scaffold + models + admin
2. Weight/volume checks
3. Geometry packer + unit tests
4. API endpoints + API tests
5. README, AI_USAGE.md, CI workflow
6. TEST_OUTPUT.md, transcript, LEARNINGS.md

## Tests on GitHub (Actions)
The file `.github/workflows/tests.yml` runs `python manage.py test` on every push.
After pushing, open the **Actions** tab, click the latest run, and copy that URL for your submission.
If it's red, read the log, fix, commit, push again.

## Submit
Make sure the repo is public, all files in `SUBMISSION_CHECKLIST.md` are committed, and send the repo URL.
