Git worktrees are a fantastic way to handle the "I need to fix a bug on another branch but I'm in the middle of something here" struggle. Instead of stashing your changes or cloning the repo a second time, a worktree lets you have multiple branches checked out simultaneously in different directories.

Here is how you get it running.

---

## 1. The Basic Command

To create a new worktree, use the `git worktree add` command. You need to specify the path where the new directory will live and the branch you want to check out.

Bash

```
git worktree add ../my-feature-branch feature-branch
```

- **`../my-feature-branch`**: This is the destination. It’s usually best to place it outside your main repo folder so you don't accidentally nest git repositories.
    
- **`feature-branch`**: The name of the branch you want to work on.
    

---

## 2. Common Scenarios

### Creating a New Branch and Worktree at Once

If the branch doesn't exist yet, add the `-b` flag:

Bash

```
git worktree add -b hotfix-emergency ../hotfix-folder
```

### Using a Specific Commit or Tag

You can point a worktree to a specific point in history:

Bash

```
git worktree add ../legacy-version v1.0.2
```

---

## 3. Managing Your Worktrees

Once you have a few running, you’ll need to keep track of them or clean them up.

|Task|Command|
|---|---|
|**List all worktrees**|`git worktree list`|
|**Remove a worktree**|`git worktree remove <path>`|
|**Clean up administrative files**|`git worktree prune`|

Export to Sheets

---

## Important Rules to Remember

- **No Double-Dipping:** Git will not allow you to check out the same branch in two different worktrees at the same time. This prevents data corruption and "whoops" moments.
    
- **Storage:** Worktrees share the same `.git` history/database as your main repo. They are very lightweight compared to a fresh `git clone`.
    
- **Deleting:** Always use `git worktree remove` rather than just deleting the folder via your OS file manager; this ensures Git cleans up the internal pointers.
    

**Would you like me to help you write a script to automate the setup of multiple worktrees for a specific project?**