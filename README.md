# A git cheat sheet
This document is still in a draft state which can include some errors.

## Setting up connection to Github on a debian based OS
### Download the latest [.deb package*](https://github.com/git-ecosystem/git-credential-manager/releases/latest), and run the following:
More info [here](https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/install.md).
```bash
sudo dpkg -i <path-to-package>
git-credential-manager configure
```

Set the Git Credential Manager
```bash
git config --global credential.credentialStore cache
```

Then, next time you execute a git command that need credential for your Github account, You will be asked for validate it using Github web site.


## Downloading a project

```git
git clone <github_address>
```

If the result doesn't contains the right branch

```git
git clone <github_address> --branch <branch_name_wanted>
```


## Set personnal informations globally

```git
git config --global user.email <your_email@address.moc>
git config --global user.name <your_name>
```


## Merging (even if non related branches)

First, switch to the branch you want to keep:

```git
git checkout <name_the_branch_to_keep>
```


The do a merge

```git
git merge <name_of_the_branch_to_merge>
```


If problem of unrelated histories:

```git
git merge <name_of_the_branch_to_merge> --allow-unrelated-histories
```


## Rolling back to an old commit

### V1

Rolling back to an old commit and commit it as the latest commit. Maybe the cleanest solution.

First, delete all the changes you made locally since the last local commit.
In other words, it will restore your local files to the last local commit, erasing the last changes.

```git
git restore .
```


Then revert to the old commit and recommit it:

```git
git revert <hash_of_old_commit> --no-edit
```



### V2

Rolling back to an old commit and you are not any more in a branch. You will need to commit be in a branch and commit again the files after. Not very clean...

First, delete all the changes you made locally since the last local commit.
In other words, it will restore your local files to the last local commit, erasing the last changes.
```git
git restore .
```


Rolling back to the old commit:

```git
git checkout <hash_of_old_commit>
```


Now your files are restored to the targeted commit but not any more in a branch. 


## Where to find a commit hash ???

You can use this command to see the commit and get the hash:

```git
git log
```

or in a shorter display:

```git
git log --oneline
```

## Suppress a file from the repository keeping the local file untouched

```git
git rm --cached .env
```

## After checkout to old version, creating a new branch

```git
git switch -c logging
```

## Remove file

```git
git rm a_git_cheat_sheet.md -f
```

## Merging

### Fast-forward merge

When you re-target a branch to another without applying any changes to any branches.

### “real” merge



## Create a new repository on the command line

```git
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/c0ldlimit/vimcolors.git
git push -u origin master
```

or

```git
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/c0ldlimit/vimcolors.git
git push -u origin master
```
[tip from](https://gist.github.com/c0ldlimit/4089101)

## clean working space/rollback to latest commit
```git
git checkout .
```
[more](https://stackoverflow.com/questions/1146973/how-do-i-revert-all-local-changes-in-git-managed-project-to-previous-state)

## Link of interest

- [lostechies.com :  Use gitk to understand git](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)
- [W3schools.com :  Git Revert](https://www.w3schools.com/git/git_revert.asp?remote=github)
