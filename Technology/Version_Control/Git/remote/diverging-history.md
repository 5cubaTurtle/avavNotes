#git
## Visual example
![[diverging_history0.png]]
In this example the local (left) tree contain a different last commit from the last commit of the remote (right) branch. Furthermore, the [[tracking]] branch `o/main` is outdated since it does not contain the latest commit of the remote branch (`C2`) neither.
At this state, the git [[push]] command will fail.
This could be fixed using `git pull --rebase`:![[diverging-history1.png]]
Or using `git pull; git push`:
![[diverging-history2.png]]
