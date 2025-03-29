# UB (Update-Branch)

`ub` is a simple shell script that updates all your local branches from an upstream repository in one go, and then pushes those updates to your fork. No more manual switching and merging branch-by-branch.

## Setup

1. **Clone or download** this script (named `ub`).
2. **Make it executable**:
   ```bash
   chmod +x ub
   ```
3. **Move it into your PATH** (e.g., `/usr/local/bin`):
   ```bash
   sudo mv ub /usr/local/bin/
   ```

## Usage

1. **Go to your local repository** (the fork you want to update):
   ```bash
   cd <repo>
   ```
2. **Ensure you have the correct remotes**:
   - `origin` pointing to your fork
   - `upstream` pointing to the original repository
3. **Run the script** to update all your branches and push to your fork:
   ```bash
   ub pull
   ```

That’s it! All your local branches will be brought up to date with `upstream`, then pushed to `origin`.
