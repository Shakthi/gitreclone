gitreclone
==========

Incremental git cloning - A heuristic approach.



Incremental cloning is a most wannabe feature in git. Those who are sitting behind slow network often blame
git, when a huge cloning process is interrupted by network failure.

However this feature seems to hard to implement on current git framework.

I am trying to develop a hacked solution for this problem.


----

Basic idea goes as follows:-
Whenever git cloning a large repo, it request object-packs from the server. Git stores this temporary packs in
the path .git/objects/pack/* In case cloning failed; this pack, including gitdir, gets deleted. 
This script is an attempt to copy those pack to a secure location (While cloning is in progress). 
 In case git cloning fails, all we left with the corrupted pack. But, believe me,we can still extract useful objects 
from the pack! Use all those objects, create a pseudo repo.

If you want to clone again the same url, add pseudo repo as a reference(alternative). So, git never asks the sever
for objects that are copied already.

----

Well, enough theory,This script performs everything neatly. However, it seems, git ignores the --reference parameter.
Honestly, I could not get any significance gain in terms of network/speed. So Please check and contribute to this little hack. 




