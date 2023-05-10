Say you have 2 branches, `A` and `B`. If you are on branch `B` and need to switch to `A`, but there is unfinsihed work on `B` you will face two scenarios:
1. Changes on `B` comes to `A`
2. If there is potential *conflicts* GIt will *stop the switch*.

If you have *unfinished work* it is better to **stash** it. `git stash` will take all *uncommited changes* and stash them, reverting the changes in the working directory.

## workflow
1. `git stash` on branch A you have changes *not ready to be comitted*.
2. switch to branch B
3. When you come back to branch A you can `git stash pop` to remove the *most recent stashed changes and re-apply* them to your working directory.
4. Note, you can actually run `git stash pop` on *any branches*!

## misc
- `git stash apply` is similar to `pop` except it doesn't remove the most recent stashed changes.
- `git stash list` shows all stashes
- *stash* is LIFO
- `git stash drop stash@{0}` drops most recent stash
- `git stash clear` clears all stashes