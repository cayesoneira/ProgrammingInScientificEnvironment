# Git workflow scheme (from Josipa Milovac'notes)

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
  1. <b>git init</b> initializes Git within the selected repository.<br/>
  2. All the information is stored in the hidden <b>.git</b> directory. Note that if .git deleted, all the info saved by git will be lost! <b>
</div>

<div class="alert alert-danger" role="alert">
<b>Important</b><br/>
Before starting to work with Git, it is necessary to:<br/>
1. Check the Git installation (installation manual available on https://git-scm.com/ <br>
2. Personalize your Git (provide username, email, editor etc. ) using git config commands.
</div>

<div class="alert alert-warning" role="alert">
  <b>Good practice of writing commit messages:</b><br/>
    1. Separate the title from the body text with a blank line (if the message is longer) <br/> 
    2. Capitalize the subject line and each paragraph <br/> 
    3. Use the imperative mode in the subject line (e.g. Add, Change, Fix...) <br/> 
    4. Wrap it to 72 characters. <br/>
    5. Use the body to explain what did you do and why.<br/> 
</div>

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
git commit does 4 things:<br/>
1. Saves the current state of the staged file.<br/>
2. Gives that state a specific ID.<br/>
3. Asigns you as the author of the changes.<br/>
4. Asigns a date and a descriptive message you provided as an author.<br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
Git workflow for tracking changes:<br/>
    1. <b>git status</b> -> check current status of the respository <br/>
    2. <b>git add [file]</b> -> stage a file to be tracked by git <br/>     
    3. <b>git diff (--staged)</b> -> shows the differences made in a file after the last commit <br/>
    4. <b>git commit -m 'message'</b> -> save the current state of the file with a descriptive message <br/>
    5. <b>git log </b> -> check all the history of commits, with all metadata <br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
    1. git reset [file]  -> unstages the file <br/>
    2. git reset --[option] [commit_ID] -> undoes changes made on a file before committing <br/>
    3. git checkout --[file] -> undoes changes made on a file after committing <br/>
    4. git revert [commit_ID] -> undoes changes made on a file before committing, and updates the commited message <br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
    1. git branch -> lists the branches within the repository <br/>
    2. git branch [branch_name] -> creates a new branch named [branch_name] <br/>
    3. git branch -m [branch_new_name] -> renames the branch <br/>
    4. git branch -d [branch_name] -> deletes the [branch_name] <br/>
    5. git checkout [branch_name]-> copies a working copy of the repository to a selected [branch_name]  <br/>
    6. git merge (--no-edit) [branch_name] -> merges the [branch_name] to the currently active branch<br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important</b><br/>
    1. git merge [branch_name] -> merge aborted due to conflict <br/>
    2. git status -> to confirm the existance of the conflict <br/>
    3. Edit the file and manually fix the conflict following the Git instructions <br/>
    4. Stage the modified file and commit the changes <br/>
    5. Branches merged, and the new branch can be deleted. <br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important </b><br/>
From local to remote:<br/>
    1. Create a remote repository on your GitHub account <br/>
    2. Go to your local repository that you want push online <br/>
    3. In the command line check if any remote declared: <b> git remote -v </b> <br/>
    5. Declare remote: <b> git remote add [remote_alias] [https://github.com/[username]/[Repositry_name] </b> <br/>
    6. Push changes online: <b> git push [option] [remote_alias] [branch] </b><br/>
</div>

<div class="alert alert-danger" role="alert">
  <b>Important </b><br/>
<b>From remote to local and back to forked remote repository:</b><br/>
    1. Fork a public repositry to you personal GitHub account<br/>
    2. Clone the forked repositry to your local machine using the command:<br/> 
    <b> git clone https://github.com/[username]/[Repositry_name]</b> <br/>
    3. Make changes on your local machine. <br/>
    4. Check if the cloned repository changed in the meanwhile and pull all the changes: <br/>
    <b> git pull [remote_alias] [branch]</b> <br/>
    5. Push back changes online to your GitHub account:<br/> <b> git push [option] [remote_alias] [branch]</b> <br/>
</div>


 __Pull request__ workflow:
 1. Login to github
 2. Go to your forked repository
 3. By pressing the tab "pull request" you will intialize your pull request to the base repository branch
 4. Compare your branch with the branch to which you want to send the pull request
 5. Initialize the pull request by writing a descritive message
 6. Checking if the branch has any conflicts with the base branch. If not, your pull request will be sent.
 
Before final merging to the base repositry branch, the owner need to revise it and decide to accept or refuse merging. 
 1. The owner sees that there is a pull request and needs to be revised.
 2. If no conflicts and the owner decides to accept the request, the pulled changes can be merged with no problem by pressing "merge pull request" 
 3. If merge, the changes are then visible in upstream repository.      

A nice schematic representation of the links between local, remote, and upstream repositories can be seen in [figure](https://www.authorea.com/users/5990/articles/17489/master/file/figures/Fig4/Fig4.png) from Blischak et al.(2016).

<div class="alert alert-danger" role="alert">
  <b>Important </b><br/>
<b>From forked remote to upstream remote repository:</b><br/>
    1. Create a pull request on your GitHub account.<br/>
    2. Write a clear comment to describe what has been changed. <br/>
    3. Check if merging with the upstream repository is possible, check for conflicts. <br/>
    4. If GitHub shows that merging is possible, and no conflicts detected, the pull request can be sent.<br/>
    5. Mergening is being approved/rejected by the owner of the upstream remote. <br/>
</div>


<div class="alert alert-block alert-info">
<b>Exercise</b><br/>
    1. In your local repository "My_scripts"<br/>
    2. Edit README.md and overwrite the text with the line: "This is my first repository on GitHub that contains a bash script."<br/>
    3. Check the status, stage the file, commit the changes. <br/>
    4. Create a new remote repository on GitHub named "MyFirstRepo". <br/>
    5. Check available remotes in your local repository. <br/>
    6. Declare a new remote named "my_remote" to "https://github.com/[your_username]/MyFirstRepo/"  <br/>
    7. Push your local master branch to the declared remote named "my_remote". <br/>
    8. Check you remote repository MyFirstRepo on Github. Can you find all the files from your local repository My_scripts there? <br/>
</div>


# Literature and online material

* Book: [Effective Computation in Physics](https://www.oreilly.com/library/view/effective-computation-in/9781491901564)
* Online course from Software Carpentry: [Version Control with Git](https://swcarpentry.github.io/git-novice/)
* Git refernce manual online: [Online manual](https://git-scm.com/doc)
* A quick introduction to Git and GitHub : [Article](https://www.authorea.com/users/5990/articles/17489/_show_article)
* Summary: [Cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)

