# A git cheat sheet
This document is still in a draft state which can include some errors.


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
git rm --cached ./ -rf
```

or

```git
git restore --staged <file>
```

to unstage


## Link of interest

[lostechies.com :  Use gitk to understand git](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)
[W3schools.com :  Git Revert](https://www.w3schools.com/git/git_revert.asp?remote=github)
