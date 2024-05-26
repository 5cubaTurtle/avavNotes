#git

When the HEAD pointer does not points to any branch. In this state any further commits will **not** belong to any branch.
![[detached-HEAD-state.png]]
- Thus it will be harder to find them.
- These commits will be eventually collected by the [[git's-garbage-collector]](~2 weeks) since nothing refers to them.
Preserved these commits for long term, we can [[tag]] them or to [[checkout|create]] a branch for them: `git checkout -b temp_branch`.