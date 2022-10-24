# Final assignment:
1. Fork https://github.com/yoselita/lyrics and clone it to your local machine.
2. Enter the folder named lyrics that will be locally created after cloning the remote repository.
3. In the lyrics folder create a new folder and name it after your Firstname_Lastname (for example Javier_Bardem).
4. Copy lyrics_template.txt into your folder.
5. Rename lyrics_template.txt after your favorite music band.
6. Open the template file [your_favorite_band].txt and write the title of your favorite song from your favorite band.
7. Stage and commit changes in your local repository.
8. Create new branch named "new_branch" and move to the new branch.
9. While being on the new_branch, open your [your_favorite_band].txt file again, and write the song lyrics after the title.
10. Stage and commit the new changes.
11. Go to the master branch, and merge  new_branch.
13. Delete the branch named new_branch.
14. Pull the changes from the forked remote repository.
15. Check the available remotes.
16. Push the changes made locally back to the remote repository forked to your account.
17. Check if the new file is created online and provide the link to your forked repository. Use the text field in the Moodle Assignment.
18. Create a pull request in your forked repository in order to merge https://github.com/[your_user]/lyrics to https://github.com/yoselita/lyrics.

---

```bash
cd /home/jovyan/Mounted/Programming/Git/introduction-to-git-main
```

## 1. Fork https://github.com/yoselita/lyrics and clone it to your local machine.

Follow the link, log in with a GitHub account and select *Fork* up in the right.

Use the following sentence:


```bash
git clone https://github.com/cayesoneira/lyrics.git
```

    Cloning into 'lyrics'...
    remote: Enumerating objects: 112, done.        
    remote: Counting objects: 100% (8/8), done.        
    remote: Compressing objects: 100% (4/4), done.        
    remote: Total 112 (delta 1), reused 7 (delta 1), pack-reused 104        
    Receiving objects: 100% (112/112), 21.53 KiB | 380.00 KiB/s, done.
    Resolving deltas: 100% (10/10), done.


## 2. Enter the folder named lyrics that will be locally created after cloning the remote repository.


```bash
cd lyrics
git init
```

    Reinitialized existing Git repository in /home/jovyan/Mounted/Programming/Git/introduction-to-git-main/lyrics/.git/



```bash
ls -A
```

    Abram_Perez       Dario_Gonzalez  Javi_Badi    Pablo_Herreros
    Cayetano_Soneira  Diego_Alvarez   Luis_Mejia   README.md
    Conrado_Muñoz     .git            Miguel_Ruiz  Ruben_Lopez


## 3. In the lyrics folder create a new folder and name it after your Firstname_Lastname (for example Javier_Bardem).


```bash
mkdir Cayetano_Soneira
```

    mkdir: cannot create directory ‘Cayetano_Soneira’: File exists




## 4. Copy lyrics_template.txt into your folder.


```bash
# I don't see the file so I create one.
touch lyrics_template.txt
cp lyrics_template.txt Cayetano_Soneira/
```

## 5. Rename lyrics_template.txt after your favorite music band.


```bash
mv Cayetano_Soneira/lyrics_template.txt Cayetano_Soneira/Radiohead.txt 
```

## 6. Open the template file [your_favorite_band].txt and write the title of your favorite song from your favorite band.


```bash
echo Reckoner > Cayetano_Soneira/Radiohead.txt
```

## 7. Stage and commit changes in your local repository.


```bash
git add Cayetano_Soneira/
git status
```

    On branch main
    Your branch is up to date with 'origin/main'.
    
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   Cayetano_Soneira/.ipynb_checkpoints/Radiohead-checkpoint.txt
    	modified:   Cayetano_Soneira/Radiohead.txt
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    	lyrics_template.txt
    



```bash
git config user.name "cayesoneira"
git config user.email "csl109@alumnos.unican.es"
git config core.editor "vim"

git config --list
```

    core.repositoryformatversion=0
    core.filemode=true
    core.bare=false
    core.logallrefupdates=true
    core.editor=vim
    remote.origin.url=https://github.com/cayesoneira/lyrics.git
    remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
    branch.main.remote=origin
    branch.main.merge=refs/heads/main
    user.name=cayesoneira
    user.email=csl109@alumnos.unican.es



```bash
git commit -m 'Add Cayetano_Soneira directory'
```

    [main 90d94d7] Add Cayetano_Soneira directory
     2 files changed, 2 insertions(+), 37 deletions(-)
     create mode 100644 Cayetano_Soneira/.ipynb_checkpoints/Radiohead-checkpoint.txt
     rewrite Cayetano_Soneira/Radiohead.txt (98%)


## 8. Create new branch named "new_branch" and move to the new branch.


```bash
git branch new_branch
```


```bash
git checkout new_branch
```

    Switched to branch 'new_branch'



```bash
git branch
```

      main
    * new_branch


## 9. While being on the new_branch, open your [your_favorite_band].txt file again, and write the song lyrics after the title.


```bash
echo -e "Reckoner\nYou can't take it with you\nDancing for your pleasure\nYou are not to blame for\nBittersweet distractors\nDare not speak its name\nDedicated to all hu-\nAll human beings\nBecause we separate\nLike ripples on a blank shore\n(In rainbows)\nBecause we separate\nLike ripples on a blank shore\n(In rainbows)\nReckoner\nTake me with you\nDedicated to all hu-\nAll human beings" >> Cayetano_Soneira/Radiohead.txt
```


```bash
cat Cayetano_Soneira/Radiohead.txt
```

    Reckoner
    Reckoner
    You can't take it with you
    Dancing for your pleasure
    You are not to blame for
    Bittersweet distractors
    Dare not speak its name
    Dedicated to all hu-
    All human beings
    Because we separate
    Like ripples on a blank shore
    (In rainbows)
    Because we separate
    Like ripples on a blank shore
    (In rainbows)
    Reckoner
    Take me with you
    Dedicated to all hu-
    All human beings


## 10. Stage and commit the new changes.


```bash
git add Cayetano_Soneira/Radiohead.txt
git commit -m 'Add lyrics to the song'
```

    [new_branch 6424cd6] Add lyrics to the song
     1 file changed, 18 insertions(+)


## 11. Go to the master branch, and merge  new_branch.


```bash
git checkout main
```

    Switched to branch 'main'
    Your branch is ahead of 'origin/main' by 1 commit.
      (use "git push" to publish your local commits)



```bash
git merge --no-edit new_branch
```

    Updating 90d94d7..6424cd6
    Fast-forward
     Cayetano_Soneira/Radiohead.txt | 18 ++++++++++++++++++
     1 file changed, 18 insertions(+)


## 13. Delete the branch named new_branch.


```bash
git branch -d new_branch
git branch
```

    Deleted branch new_branch (was 6424cd6).
    * main


## 14. Pull the changes from the forked remote repository.

### SSH Authorization Key Setup

There are several ways to access a repository in GitHub:*https* protocol, *SSH* and *GitHub CLI* (needs installation). We are going to use the *SSH*. To do that, in a few words, we need to create and download a key that our computer will keep. Then we go to our GitHub account and set what key a PC would need to edit our repositories. Once this is done, we can *pull* in our account directly from terminal.

**The tutorial is as follows:**
- Check if SSH is set on your machine:
        
        ls -al ~/.ssh
        
- If empty:

        ssh-keygen -t rsa -b 4096 -C your_email@example.com
        
- Follow the instructions, and for each prompt press enter (and write nothing)
- Check again if SSH is set:

        ls -al ~/.ssh
        
- 2 files should be listed: 
        
        id_rsa
        id_rsa.pub
        
- Access `id_rsa.pub` in `home/<user>/.ssh` with `cat` and copy the long key: it begins with sha(...) and ends with a mail address.
- Now go to your GitHub account
- Click on your profile icon in the top right corner to get the drop-down menu. 
- Click “Settings,” then on the settings page, click “SSH and GPG keys,” on the left side “Account settings” menu. 
- Click the “New SSH key” button on the right side. 
- Add some recognizable title, paste your SSH key into the field, and click the “Add SSH key” to complete the setup.
- All set. Check your authentication from the command line:

        ssh -T git@github.com
        
- You will receive a confirmation message. You can continue with the creation of the remote.


```bash
git remote set-url origin git@github.com:cayesoneira/lyrics.git
git pull git@github.com:cayesoneira/lyrics.git main
```

    From github.com:cayesoneira/lyrics
     * branch            main       -> FETCH_HEAD
    Already up to date.


## 15. Check the available remotes.


```bash
git remote -v
```

    origin	git@github.com:cayesoneira/lyrics.git (fetch)
    origin	git@github.com:cayesoneira/lyrics.git (push)


## 16. Push the changes made locally back to the remote repository forked to your account.


```bash
git pull git@github.com:cayesoneira/lyrics.git main
```

    From github.com:cayesoneira/lyrics
     * branch            main       -> FETCH_HEAD
    Already up to date.


## 17. Check if the new file is created online and provide the link to your forked repository. Use the text field in the Moodle Assignment.

It is pulled as we wanted: https://github.com/cayesoneira/lyrics

## 18. Create a pull request in your forked repository in order to merge https://github.com/cayesoneira/lyrics to https://github.com/yoselita/lyrics.

 **Pull request** workflow:
 1. Login to GitHub
 2. Go to your forked repository
 3. By pressing the tab "pull request" you will intialize your pull request to the base repository branch
 4. Compare your branch with the branch to which you want to send the pull request
 5. Initialize the pull request by writing a descritive message
 6. Checking if the branch has any conflicts with the base branch. If not, your pull request will be sent.
 
Before final merging to the base repositry branch, the owner need to revise it and decide to accept or refuse merging. 
 1. The owner sees that there is a pull request and needs to be revised.
 2. If no conflicts and the owner decides to accept the request, the pulled changes can be merged with no problem by pressing "merge pull request" 
 3. If merge, the changes are then visible in upstream repository.      
