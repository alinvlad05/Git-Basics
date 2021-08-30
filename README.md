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

