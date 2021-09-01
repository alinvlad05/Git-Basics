# Sourcetree

A Git GUI that offers a visual representation of your repositories.(Rank 1 in top git software)<br/>
Download: https://www.sourcetreeapp.com/ <br/>

# Git
A version control system is a tool that lets  <br/>
you track the history and attribution of your project files over time (stored in a repository), <br/>
and which helps the developers in the team to work together.  <br/>

Create a new repository:git init <br/>
Get your own repository instance:Create on GitHub a new repository and copy address. <br/>
Open command line and navigate to the chosen directory: <br/>
git clone https://git.company.com/random (address) <br/>

Add files: <br/> 
git add (filename)<br/>
git status –s<br/>
It shows:A  file   <br/>
A=added<br/>

Publishing changes:<br/>
git push<br/>

If another developer clone the same repository and then modify a file:<br/>
Show differences(review the actual changes with the diff command):<br/>
git diff<br/>

Commit the changes:<br/>
git commit -a -m "Message"<br/>

Moving files:<br/>
git mv random.txt src\<br/>
git mv (file) (location)<br/>

Rename random.txt to rand.txt<br/>
git mv src\random.txt src\rand.txt<br/>

Use pull to bring in changes:<br/>
git pull<br/>

Create a tag:<br/>
Create a tag so you can more easily access/refer to the released version.<br/>
Use an annotated tag for this;<br/>
git tag -a -m "random v0.1" v0.1<br/>

Remove a file:<br/>
git rm -f (filename)<br/>

Undo changes to a file:<br/>
git checkout -- src\rand.txt<br/>

If you don't remember how to revert a particular type of change, or to <br/>
update what is to be committed (using git commit without -a), the <br/>
output of git status (without -s) contains information about what commands to use.<br/>
git status<br/>

To isolate this line of development from other changes, create your own named branch, and switch to it: <br/>
git checkout -b better-random  <br/>

Instead of using the git checkout –b better-random shortcut to  <br/>
create a new branch and switch to it in one command invocation, you <br/>
could have first created a branch with git branch better-random, <br/>
then switched to it with git checkout better-random.<br/>

Git just wants you to set up a remote origin as the upstream for the newly <br/>
created branch (it is using a simple push strategy); this will also push this branch <br/>
explicitly.<br/>

git push --set-upstream origin better-random<br/>

Merging a branch:<br/>
git merge origin/better-random<br/>

Undoing an unpublished merge:<br/>
git reset --hard @{1}<br/>

The structure that Git uses (on the abstract level) to represent the possible non-linear  <br/>
history of a project is called a Directed Acyclic Graph (DAG).<br/>
A directed graph is a data structure from computer science (and mathematics) <br/>
composed of nodes (vertices) that are connected with directed edges (arrows). <br/>
A directed graph is acyclic if it doesn't contain any cycles, which means that there is no <br/>
way to start at some node and follow a sequence of the directed edges to end up back <br/>
at the starting node.<br/>

Usually, the DAG of revisions is laid out left-to-right (root nodes on the left, leaves on the right) <br/>
or bottom-to-top (the most recent revisions on top). ASCII-art examples in <br/>
Git documentation use the left-to-right convention, while the Git <br/>
command line use bottom-to-top, that is, the most recent first convention.<br/>

There are two special type of nodes in any DAG:<br/>

Root nodes: These are the nodes (revisions) that have no parents (no outgoing edges).<br/>
There is at least one root node in the DAG of revisions, <br/>
which represents the initial (starting) version of a project.<br/>

Leaf nodes (or leaves): These are the nodes that have no children (no incoming edges);<br/>
there is at least one such node. They represent the most <br/>
recent versions of the project, not having any work based on them. Usually, <br/>
each leaf in the DAG of revisions has a branch head pointing to it.<br/>

A branch operation is what you use when you want your development process to  <br/>
fork into two different directions to create another line of development.<br/>

A tag operation is a way to associate a meaningful symbolic name with the specific <br/>
revision in the repository<br/>

Both branches and tags, sometimes called references (refs) together.<br/>

Git, needs to know which branch tip to advance when creating a new <br/>
commit. It needs to know which branch is the current one and is checked out into <br/>
the working directory. Git uses the HEAD pointer for this.<br/>
Usually, this points to one of branch tips, which, in turn, points to some node <br/>
in the DAG of revisions, but not always-the detached HEAD situation; hat is, when <br/>
HEAD points directly to a node in the DAG.<br/>

Git stored branches and tags in files inside .git <br/>
administrative area, in the .git/refs/heads/ and .git/<br/>
refs/tags/ directories, respectively. <br/>

The HEAD pointer (usually a symbolic reference,for example ref: <br/>
refs/heads/master) is stored in .git/HEAD.<br/>
The master branch is stored in .git/refs/heads/master, <br/>
and has refs/heads/master as full name <br/>
(branches reside in the refs/heads/ namespace).<br/>

The remote-tracking branch, origin/master, which remembers <br/>
the last seen position of the master branch in the remote <br/>
repository, origin, is stored in .git/refs/remotes/origin/master,<br/>
and has refs/remotes/origin/master as its full name. <br/>
The v1.3-rc3 tag has refs/tags/v1.3-rc3 as the full name <br/>
(tags reside in the refs/tags/ namespace).<br/>


In Git, each revision is given a unique identifier (object name), which is a SHA-1 hash  <br/>
function, based on the contents of the revision. You can select a commit by using its <br/>
SHA-1 identifier as a 40-character long hexadecimal number (120 bits).<br/>

It is not necessary to give a full 40 characters of the SHA-1 identifier. Git is smart <br/>
enough to figure out what you meant if you provide it with the first few characters of <br/>
the SHA-1 revision identifier, as long as the partial SHA-1 is at least four characters <br/>
long. To be able to use a shortened SHA-1 to select revision, it must be long enough <br/>
to be unambiguous, that is, there is one and only one commit object which SHA-1 <br/>
identifier begins with given characters.<br/>
For example, both dae86e1950b1277e545cee180551750029cfe735 and dae86e <br/>
name the same commit object, assuming, that there is no other object in <br/>
your repository whose object name starts with dae86e.<br/>

You can also request that Git use the shortened SHA-1 in place of the full SHA-1 <br/>
revision identifiers with the --abbrev-commit option. By default, Git will use at <br/>
least seven characters for the shortened SHA-1; you can change it with the optional <br/>
parameter, for example, --abbrev-commit=12.<br/>

If you place ^ at the end of a revision name, Git resolves it to mean a (first) parent  <br/>
of that revision.<br/>
As a special case, ^0 means the commit itself;<br/>
This suffix syntax is composable. You can use HEAD^^ to mean grandparent of HEAD, <br/>
and parent of HEAD^.<br/>

As a special case, ~ is equivalent to ~ 1, so, for example, HEAD~ and HEAD^ are equivalent. <br/>
And, HEAD~2 means the first parent of the first parent, or the grandparent, and is <br/>
equivalent to HEAD^^.<br/>

Every time your HEAD and your branch head are updated for any reason, Git stores <br/>
that information for you in this local temporary log of ref history.<br/>

To specify the nth prior value of HEAD in your local repository, you can use <br/>
the HEAD@{n} notation that you see in the git reflog output. It's same with <br/>
the nth prior value of the given branch, for example, master@{n}.<br/>

The suffix, @{upstream} (short form <refname>@{u}), which can be applied only to <br/>
a local branch name, selects the branch that the ref is set to build on top of.<br/>

Commands, given a single revision as an argument, will show the set of commits reachable <br/>
from that revision, following the commit ancestry chain, all the way down to the root commits.<br/>
  
Double dot notation<br/>
The range, HEAD ~ 4..HEAD, means four commits: HEAD, HEAD^, HEAD^^, and HEAD^^^ <br/>
or in other words, HEAD ~ 0, HEAD ~ 1, HEAD ~ 2, and HEAD ~ 3, assuming that there are no merge <br/>
commits starting between the current branch and its fourth ancestor.  <br/>
  
In view of nonlinear history the double-dot notation A..B, or "between <br/>
A and B", is defined as reachable from A and not reachable from B.<br/>
  
Say your branches master and experiment diverge. You want to see <br/>
what is in your experiment branch that hasn't yet been merged into your master <br/>
branch. You can ask Git to show you a log of just those commits with master..experiment.<br/>
If, you want to see the opposite—all the commits in master that <br/>
aren't in experiment—you can reverse the branch names. <br/>
The experiment..master notation shows you everything in master not reachable from experiment.<br/>
  
Git allows you to exclude the commits that are reachable from a given revision by <br/>
prefixing the said revision with a ^.<br/>
Git allows you to use the --not option, which negates all the following <br/>
revisions.<br/>
  
There is another useful shortcut, namely A^!, which is a range composed of a single <br/>
commit. For non-merge commits, it is simply A^..A.<br/>
For merge commits, the A^!, excludes all the parents. With the help of yet <br/>
another special notation, namely A^@, denoting all the parents of A (A^1, A^2,…, A^n), <br/>
we can say that A^! is a shortcut for A --not A^@.<br/>
  
  Triple-dot notation<br/>
The last major syntax for specifying revision ranges is the triple-dot syntax, A...B. It <br/>
selects all the commits that are reachable by either of the two references, but not by <br/>
both of them.<br/>

  Index/Staging Area<br/>
   Let's consider what happens when we use the git <br/>
add command to add a file, but did not yet create a new commit adding it.<br/>
A version control system needs to store such information somewhere. Git uses something <br/>
called the index for this; it is the staging area that stores information that will go into <br/>
the next commit. The git add <file> command stages the current contents (current version) of the file, <br/>
adding it to the index.<br/>
