# Working with a New Branch

To create a new branch that is based on your currently checked out (`HEAD`) branch, simply use `git branch` with the name of the new branch as the only parameter:

```git
$ git branch <new-branch-name>
```

If you want to create a new branch based on an existing one, add another parameter `base-branch`:

```git
$ git branch <new-branch> <base-branch>
```

To publish your new local branch, you'll want to push it to your remote repository in order to share your work. 

```git
$ git push -u origin <local-branch>
```

The `-u` flag tells Git to establish a "tracking connection", which makes pushing/pulling much easier in the future.