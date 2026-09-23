# GitHub Workflow for UW Baja Electrical DAQ

This guide explains how UW Baja electrical team members should use this repository. The goal is to keep firmware, documentation, test data, and design notes organized so that other members can understand and continue the work later.

If you are new to Git, do not worry. Follow the steps below, ask questions early, and avoid committing directly to `main`.

## 1. What Goes in This Repository

Use this repository for development and documentation related to the UW Baja Electrical DAQ System.

Current and planned structure:

```text
docs/       -> Documentation, diagrams, setup notes, meeting notes
hardware/   -> Schematics, wiring, PCB files, BOMs
firmware/   -> Arduino / MCU code
tests/      -> Test procedures, calibration notes, test results
data/       -> Experimental data and logged vehicle data
analysis/   -> Scripts, notebooks, and plots used to process data
```

Put your work in the appropriate folder. If you are unsure where something belongs, ask the electrical lead before creating a new top-level folder.

## 2. Basic Rules

- Do not work directly on `main`.
- Keep `main` stable and understandable.
- Make a new branch for each feature, fix, experiment, or documentation update.
- Commit small, meaningful changes instead of one huge commit at the end.
- Pull the latest changes before starting work and before opening a pull request.
- Do not commit temporary files, build outputs, personal notes, or large raw data files unless the team agrees they belong here.
- Write commit messages that explain what changed.

## 3. One-Time Setup

Install Git:

- Windows: install Git from <https://git-scm.com/download/win>
- macOS: install Git from <https://git-scm.com/download/mac> or use Xcode Command Line Tools
- Linux: install Git through your package manager

Set your name and email once:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Optional but recommended for beginners: install GitHub Desktop from <https://desktop.github.com/>. You can use either the terminal or GitHub Desktop. The workflow is the same.

## 4. Clone the Repository

Clone means downloading the repository to your computer.

```bash
git clone https://github.com/jsk947/UW-baja-electrical-DAQ-system.git
cd UW-baja-electrical-DAQ-system
```

Check that everything is connected:

```bash
git status
git remote -v
```

## 5. Start New Work on a Branch

Before starting, make sure your local `main` is up to date:

```bash
git checkout main
git pull origin main
```

Create a branch with a clear name:

```bash
git checkout -b feature/your-name-short-description
```

Examples:

```text
feature/alex-rpm-sensor
feature/maya-temperature-calibration
fix/jordan-readme-typos
docs/sam-wiring-diagram
```

Use `feature/` for new work, `fix/` for bug fixes, and `docs/` for documentation-only changes.

## 6. Make Changes Locally

Edit files in the correct folder. Common examples:

- Firmware for RPM sensing goes in `firmware/hall-rpm/`.
- Firmware for temperature sensing goes in `firmware/temperature/`.
- Wiring notes, diagrams, and system explanations go in `docs/`.
- Test instructions and results go in `tests/`.

Check what changed:

```bash
git status
git diff
```

## 7. Commit Your Work

Stage the files you want to include:

```bash
git add path/to/file
```

Commit with a short message:

```bash
git commit -m "Add RPM sensor wiring notes"
```

Good commit messages:

```text
Add hall sensor RPM prototype firmware
Document temperature sensor calibration setup
Fix typo in system architecture notes
```

Avoid vague messages like:

```text
changes
update stuff
final version
```

## 8. Push Your Branch to GitHub

The first time you push a new branch:

```bash
git push -u origin your-branch-name
```

Example:

```bash
git push -u origin feature/alex-rpm-sensor
```

After the first push, you can usually use:

```bash
git push
```

## 9. Open a Pull Request

A pull request, or PR, asks the team to review your branch before merging it into `main`.

On GitHub:

1. Go to the repository page.
2. Click **Compare & pull request** for your branch.
3. Write a short summary of what you changed.
4. Mention anything that needs testing or review.
5. Request review from the electrical lead or another member.

PR description template:

```markdown
## Summary
- What did you change?
- Why was this needed?

## Testing
- How did you test it?
- What hardware/software was used?

## Notes
- Anything reviewers should know?
```

Before opening a PR, check:

- Your branch is up to date with `main`.
- The code or document is in the correct folder.
- You removed temporary/debug files.
- Firmware builds or compiles if applicable.
- Documentation is readable by someone who did not work on the task.

## 10. Keep Your Branch Updated

If other people merge changes while you are working, update your branch:

```bash
git checkout main
git pull origin main
git checkout your-branch-name
git merge main
```

Resolve any conflicts, then commit the merge if Git asks you to.

## 11. Merge Conflicts

A conflict happens when Git cannot automatically combine two edits to the same part of a file.

When this happens:

1. Open the conflicted file.
2. Look for conflict markers:

```text
<<<<<<< HEAD
Your version
=======
Other version
>>>>>>> main
```

3. Edit the file so it contains the correct final version.
4. Remove the conflict markers.
5. Stage and commit the resolved file:

```bash
git add path/to/conflicted-file
git commit
```

If you are unsure which version is correct, ask before resolving the conflict.

## 12. Working With Data and Large Files

DAQ projects can create large data files. Be careful before committing them.

Commit data only when it is useful for future team members, such as calibration data, selected test results, or small example logs.

Do not commit:

- Huge raw logs from every test run
- Duplicate exports
- Temporary plots
- Local build folders
- Personal scratch files

If the team needs to store large files regularly, discuss using Git LFS or shared cloud storage.

## 13. Useful Commands

```bash
git status                 # show changed files
git diff                   # show unstaged changes
git branch                 # show local branches
git checkout main          # switch to main
git pull origin main       # update main from GitHub
git checkout -b branch     # create and switch to a new branch
git add file               # stage a file
git commit -m "message"    # commit staged changes
git push                   # upload commits to GitHub
```

## 14. If Something Goes Wrong

Do not panic and do not delete the repository unless someone experienced tells you to.

Useful first steps:

```bash
git status
```

Then ask for help and include:

- What command you ran
- The error message
- What you were trying to do
- Whether you have uncommitted work

Git is designed to track history, so most mistakes can be fixed if we know what happened.
