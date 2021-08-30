# Git
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

