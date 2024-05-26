#git 
Manage reflog information

Reference logs, or "reflogs", record when the tips of branches and other references were updated in the local repository. Reflogs are useful in various Git commands, to specify the old value of a reference. For example, **HEAD@{2}** means "where HEAD used to be two moves ago", **master@{one.week.ago}** means "where master used to point to one week ago in this local repository", and so on. See gitrevisions(7) for more details.

history of where the **HEAD** pinted to: `git reflog` 
