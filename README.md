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

# Index/Staging Area<br/>
   Let's consider what happens when we use the git <br/>
add command to add a file, but did not yet create a new commit adding it.<br/>
A version control system needs to store such information somewhere. Git uses something <br/>
called the index for this; it is the staging area that stores information that will go into <br/>
the next commit. The git add <file> command stages the current contents (current version) of the file, <br/>
adding it to the index.<br/>
  
git add takes the content of the file from the working directory and puts it into the staging area.<br/>
  
git commit -a command (which is git commit --all), which will take all the changed tracked files,<br/>
add them to the staging area (as if with git add -u, at least in modern Git), and create a new <br/>
commit.The new files still need to be explicitly git add to be tracked, and to be included in the new commit.<br/>
   
  You create a new revision with the git commit command, which takes the <br/>
files as they are in the staging area and stores that snapshot permanently to <br/>
your local repository.<br/>
  
  To see what you've changed but not yet staged, type git diff with no other <br/>
arguments.<br/>
  
  To see what you've staged that will go into your next commit, use git diff <br/>
--staged (or git diff --cached). This command compares what is in your <br/>
staging area to the content of your last commit.<br/>
  
  You can use git diff HEAD to compare what is in your working directory with the <br/>
last commit (or arbitrary commit with git diff <commit>). <br/>
  
# Unified Git diff format<br/>
  
diff --git a/builtin-http-fetch.c b/http-fetch.c<br/>
The first line is a git diff header in the form diff --git a/file1 b/file2.<br/>
--git option means that diff is in the git diff output format.<br/>
  
similarity index 95%<br/>
rename from builtin-http-fetch.c<br/>
rename to http-fetch.c<br/>
The first three lines in this example tell us that the file was renamed from <br/>
builtin-http-fetch.c to http-fetch.c and that these two files are 95% identical.<br/>
index f3e63d7..e8f44ba 100644<br/>
The last line in extended diff header tells us about the mode of given file<br/>
(100644 means that it is an ordinary file and not a symbolic link, and that it doesn't have executable permission bit)<br/>
Search on google 777,755,644 :P :)) <br/>
Some file permission examples: <br/>
777 - all can read/write/execute (full access). <br/>
755 - owner can read/write/execute, group/others can read/execute. <br/>
644 - owner can read/write, group/others can read only.<br/>
For the new files, pre-image(the version of the file before the given change) hash is 0000000, <br/>
the same for the deleted files with post-image(the version of the file after the change) hash.  <br/>
4-bit object type valid values in binary are 1000 (regular file), 1010 (symbolic link) and 1110 (gitlink) <br/>

@@ -1,8 +1,9 @@<br/>
This line is in the format @@ from-file-range to-file-range @@. <br/>
The from-file-range is in the form -<start line>,<number of lines>, <br/>
and to-file-range is +<start line>,<number of lines>.   <br/>
  
Next is the description of where and how files differ. The lines common <br/>
to both the files begin with a space (" ") indicator character. The lines that <br/>
actually differ between the two files have one of the following indicator <br/>
characters in the left print column:<br/>
+: A line was added here to the second file<br/>
-: A line was removed here from the first file<br/>
 
 
# Amending a commit
 the --amend flag of the git commit; it allows you to change the very last commit.<br/>
 If you just want to correct the commit message, you simply commit again, without any staged changes, and fix it:<br/>
 git commit --amend<br/>
 If you want to add some more changes to that last commit, you can simply stage <br/>
them as normal with git add and then commit again, or make the changes and use git commit -a --amend<br/>
 
WARNING: you should never amend a commit that has already been published!<br/>
This is because amend effectively produces a completely <br/>
new commit object that replaces the old one. If you're the <br/>
only person who had this commit, doing this is safe. After publishing the <br/>
original commit to a remote repository, other people might already have based their <br/>
new work on that version of the commit. Replacing the original with an amended <br/>
version will cause problems downstream.<br/>
 
 The old version of commit before amending would be available in the branch reflog and in <br/>
the HEAD reflog; Just after amend, it would be available as @{1}. <br/>
Git would keep the old version for a month, by default, unless manually removed.<br/>

# Anonymous branches
 What happens if you try to check out something that is not a local branch: for <br/>
example an arbitrary revision (like HEAD^), or a tag (like v0.9), or a remote-tracking <br/>
branch (for example, origin/master)?<br/>
 Older Git refused to switch to non-branch. Nowadays, Git will create an anonymous <br/>
branch by detaching HEAD pointer and making it refer directly to a commit, rather <br/>
than being a symbolic reference to a branch.<br/>
 To create an anonymous branch at the current position explicitly, you can use the --detach <br/>
option to the checkout command. The detached HEAD state is shown in branch <br/>
listing as (no branch) in older versions of Git, or (detached from HEAD) or (HEAD detached at ...) in newer.<br/>
 If you did detach HEAD by mistake, you can always go back to the previous branch with:<br/>
git checkout (name)<br/>
As Git informs you when creating a detached branch, you can always give a name to <br/>
the anonymous branch with git checkout -b <new-name>. <br/>
 
# Branch operations
Reset always changes where the current branch points to (moves the ref), <br/>
while checkout either switches branch, or detaches HEAD at a given revision if it is given non-branch.<br/>
 
 Delete a branch:You can do this with git branch -d.<br/>
What happens if you delete a branch, and there is no other reference to the part of <br/>
project history it pointed to? Those revisions will become unreachable and Git would <br/>
delete them after the HEAD reflog expires (which, with default configuration, is after 30 days).<br/>
 That is why Git would allow you to delete only the completely merged-in branch, <br/>
whose all commits are reachable from HEAD.<br/>
 To delete a branch that was not merged in, risking parts of the DAG becoming <br/>
unreachable, you need a stronger command, namely, git branch -D.<br/>
 You can check if the branch was merged in into any other branch, by checking <br/>
whether git branch --contains <branch> shows anything.  <br/>
You cannot delete the current branch.<br/>
 
 You can rename a branch with git branch -m (use -M if target name exists and <br/>
you want to overwrite it); it will rename a branch and move the corresponding <br/>
reflog (and add rename operation to the reflog), and change the branch in all of its <br/>
configuration (its description, its upstream, and so on).<br/>

 
 # Using git stash
 git stash command<br/>
 Stashing takes the dirty state of your working area—that is, your modified <br/>
tracked files in your worktree (though you can also stash untracked files with the <br/>
--include-untracked option), and the state of the staging area, then saves this <br/>
state, and resets both the working directory and the index to the last committed <br/>
version (to match the HEAD commit), effectively running git reset --hard HEAD. <br/>
You can then reapply the stashed changes at any time.<br/>
Stashes are saved on a stack: by default you apply the last stashed changes (stash@{0}),<br/>
though you can list stashed changes (with git stash list), and explicitly select any of the stashes.<br/>
 By default git stash pop will apply the last stashed changes, and delete the  <br/>
stash if applied successfully.<br/>
 You can use any of the older stashes by specifying the stash name as an argument. <br/>
For example, you can run git stash apply stash@{1} to apply it, and you can <br/>
drop it (remove it from the list of stashes) with git stash drop stash@{1}; the  <br/>
git stash pop command is just a shortcut for apply + drop.<br/>
 You can make git stash keep the state of the index, and reset the <br/>
working area to the staged state, with the --keep-index option.<br/>
 To stash away your changes, Git creates two automatic commits: one for the index <br/>
(staging area), and one for the working directory. With git stash --include-untracked,<br/>
 Git creates an additional third automatic commit for untracked files.<br/>
 The commit containing the work in progress in the working directory (the state of <br/>
files tracked from there) is the stash, and has the commit with the contents of the <br/>
staging area as its second parent. This commit is stored in a special ref: refs/stash. <br/>
Both WIP (stash) and index commits have the revision you were on when saving <br/>
changes as its first (and only for the index commit) parent.<br/>
 
 
 # Bare repositories
There are two types of repositories: an ordinary non-bare one, with a working directory and a staging area, <br/>
and a bare repository, bereft of the working directory. The former type is meant for private solo development, <br/>
for creating new history, while the latter type is intended for collaboration and synchronizing development results.<br/>
By convention, bare repositories use the .git extension—for example, project.git<br/>
 —while non-bare repositories don't have it—for example, project (with the administrative area and the local repository in project/.git). <br/>
 You can usually omit this extension when cloning, pushing to, or fetching from the repository; <br/>
 using either http://git.example.com/project.git or http://git.example.com/project as the repository URL will work. <br/>
 To create the bare repository, you need to add the --bare option to the init or the clone command:<br/>
 git init --bare project.git<br/>

 # Tags
 Git uses two types of tags: lightweight and annotated. A lightweight tag is very much like a branch that doesn't change – <br/>
 it's just a pointer (reference) to a specific commit in the graph of revisions,<br/>
 though in refs/tags/ namespace rather than in refs/heads/ one.<br/>
 
 Annotated tags<br/>
Annotated tags, involve tag objects. Here the tag reference (in refs/tags/) points to a tag object, which in turn points to a commit. <br/>
 Tag objects contain a creation date, the tagger identity (name and e-mail), and a tagging message. <br/>
You create an annotated tag with git tag -a (or --annotate). If you don't specify a message for an annotated tag on <br/>
 the command line (for example, with -m "<message>"), Git will launch your editor so you can enter it.<br/>
You can view the tag data along with the tagged commit with the git show command<br/>
 
 Signed tags<br/>
Signed tags are annotated tags with a clear text GnuPG signature of the tag data attached. <br/>
 You can create it with git tag -s (which uses your committer identity to select the signing key, or user.signingKey if set),<br/>
 or with git tag -u <key-id>; <br/>
both versions assume that you have a private GPG key (created, for example, with gpg --gen-key).<br/>
 Annotated or signed tags are meant for marking a release, while lightweight tags are meant for private or temporary <br/>
revision labels. For this reason, some Git commands (such as git describe) will ignore lightweight tags by default.<br/>
 Of course in collaborative workflows it is important that the signed tag is made public, and that there is a way to verify it.<br/>
 
 Publishing tags<br/>
Git does not push tags by default: you need to do it explicitly. <br/>
 One solution is to individually push a tag with git push <remote> tag <tag-name> <br/>
 (here tag <tag> is equivalent to the longer refspec refs/tags/<tag>:refs/tags/<tag>); <br/>
you can skip tag in most cases, here. <br/>
 Another solution is to push tags in mass either all the tags—both lightweight and <br/>
 annotated—with the use of the --tags option, or just all annotated tags that point to pushed commits with --follow-tags.<br/>
 This explicitness allows you to re-tag (using git tag -f) with impunity, <br/>
 if it turns out that you tagged the wrong commit, or there is a need for a last-minute <br/>
 fix—but only if the tag was not made public.<br/>
When fetching changes, Git automatically follows tags, downloading annotated <br/>
tags that point to fetched commits. This means that downstream developers will <br/>
automatically get signed tags, and will be able to verify releases.<br/>
 To verify a signed tag, you use git tag -v <tag-name>. You need the signer's <br/>
public GPG key in your keyring for this (imported using for example gpg --import <br/>
or gpg --keyserver <key-server> --recv-key <key-id>), and of course the <br/>
tagger's key needs to be vetted in your chain of trust.<br/>
 
 Merging signed tags (merge tags)<br/>
 Requesting the pull of a signed tag (available since Git version 1.7.9).<br/>
 In this workflow, you work on changes and, when they are ready, you create and <br/>
push a signed tag (tagging the last commit in the series). You don't have to push <br/>
your working branch—pushing the tag is enough. If the workflow involves sending <br/>
a pull request to the integrator, you create it using a tag as the end commit<br/>
 The signed tag being pulled is not stored in the integrator's repository, not as a <br/>
tag object. Its content is stored, hidden, in a merge commit. This is done so as to <br/>
not pollute the tag namespace with a large number of such working tags.<br/>

 # The graduation, or progressive-stability branches workflow <br/>
 In such situation, one would have at least three integration branches. There would <br/>
be one branch for the ongoing maintenance work (containing only bug fixes to the <br/>
last version), to create minor releases. One branch for stable work to create major <br/>
releases; this branch can also be used for nightly stable builds. And last, one branch <br/>
for ongoing development, possibly unstable.<br/>
 You can use this workflow as it is, with only graduation branches, and no other types <br/>
of branches. You commit bug fixes on the maintenance branch and merge it into <br/>
the stable branch and development branch, if necessary. You create revisions with <br/>
the well-tested work on the stable branch, merging it into the development branch <br/>
when needed (for example, if the new work depends on them). You put the work in <br/>
progress, possibly unstable, on the development branch. During normal development, <br/>
you never merge less stable into more stable branches, otherwise you would decrease <br/>
their stability. It is always more stable into less stable.<br/>
 In the pure graduation branches workflow, one would create minor releases (with bug fixes) <br/>
 out of the maintenance branch. Major releases (with new features) are <br/>
created out of the stable-work branch. After a major release, the stable-work branch <br/>
is merged into the maintenance branch to begin supporting the new release that was <br/>
just created. At this point also, an unstable (development) branch can be merged into <br/>
a stable one. This is the only time when merging upstream, which means merging <br/>
less stable branches into more stable branches, should be done.<br/>
 
 # The topic branches workflow<br/>
 The idea behind the topic branches workflow is to create a separate short-lived <br/>
branch for each topic, so that all the commits belonging to a given topic <br/>
 (all the steps in its development) are kept together. The purpose of each topic branch is  <br/>
a development of the new feature, or a creation of a bug fix.<br/>
 In the topic branches workflow (also called the feature branches workflow), you <br/>
have are at least two different types of branches. First, there needs to be at least one <br/>
permanent (or just long-lived) integration branch. This type of branches is used purely <br/>
for merging. Integration branches are public.<br/>
   Second, there are separate short-lived temporary feature branches, each intended for <br/>
the development of a topic or the creation of a bug fix. They are used to carry all the <br/>
steps, and only the steps required in the development of a feature or a fix; a unit  <br/>
of work for a developer. These branches can be deleted after the feature or the  <br/>
bug fix is merged. Topic branches are usually private and are often not present in <br/>
public repositories.<br/>
 
 
