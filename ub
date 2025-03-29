#!/bin/bash
# ub: A utility to update all local branches from upstream

# Configurable MERGE_COMMAND - 'merge' or 'rebase'
MERGE_COMMAND="merge"

function print_help {
  echo "Usage: ub [pull|help]"
  echo
  echo "Commands:"
  echo "  pull          Fetch from upstream and origin, then $MERGE_COMMAND each local branch"
  echo "  help          Show help"
  exit 0
}

function pull_all_branches {
  # Fetch from both origin and upstream
  echo "Fetching from origin and upstream..."
  git fetch origin
  git fetch upstream

  # Get a list of all local branches (excluding the asterisk on current branch)
  echo "Updating all local branches..."
  for branch in $(git branch | sed 's/^\* //'); do
    echo "-------------------------"
    echo "Checking out $branch"
    git checkout "$branch"

    # Merge or rebase from upstream/<branch> if it exists
    if git show-ref --quiet "refs/remotes/upstream/$branch"; then
      echo "Merging upstream/$branch into $branch"
      if [[ "$MERGE_COMMAND" == "merge" ]]; then
        git merge "upstream/$branch"
      else
        git rebase "upstream/$branch"
      fi
    else
      echo "No upstream branch found for $branch, skipping merge."
    fi

    # Push changes back to origin
    echo "Pushing $branch to origin..."
    git push origin "$branch"
  done
  echo "-------------------------"
  echo "Update complete."
}

case "$1" in
  pull)
    pull_all_branches
    ;;
  help)
    print_help
    ;;
  *)
    print_help
    ;;
esac
