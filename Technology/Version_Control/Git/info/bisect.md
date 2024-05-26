#git 
Use binary search to find the commit that introduced a bug

1. Mark last good revision and first bad revision
2. Resets code to mid-point
3. Mark as good or bad revision
$...$ Repeat

### Procedure
- Initiate the bisect: `git bisect start`.
> The following 2 steps will set the bounds of the bisect. 
- Set the reference where the *"bug"* exists: `git bisect bad <ref>`.
- Set the reference where the *"bug"* does not exists: `git bisect good <ref>`.
At this point the bisect is undergoing. At each step the user needs to note whether the *"bug"* exists or not. 
Once the 1st bad commit was found, use `git bisect reset` to end the procedure and go back to the [[Technology/Version_Control/Git/miscellaneous/HEAD|HEAD]] as it was before the start of the bisect.

Alternatively, `old`/`new`  could be used instead of `good`/`bad`.
