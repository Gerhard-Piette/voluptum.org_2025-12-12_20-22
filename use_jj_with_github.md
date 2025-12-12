








# jj with github










## Clone with jj

```
jj git clone https://github.com/yourusername/your-repo
```










## List of bookmarks

```
jj bookmark list
```










## Create bookmark for git branch

Git needs a branch.

A jj bookmark is used to create the corresponding Git branch.

jj uses "bookmarks" where Git uses "branches". You need to label this commit so GitHub knows what to call it (e.g., main).

The jj bookmark and git branch can be created at any time but before the first push to git.

Creation of the main bookmark and branch:

```
jj bookmark create main
```










## Describe the current change

Give the message for the current changeset when you commit the current changeset:

```
jj commit -m "message for current changeset"
```

You can give a message to your current changeset without committing it: 

```
jj describe -m "your message"
```










## Update jj's awareness

If your github repo contains new data.

```
jj git fetch 
```










## Point your bookmark to the new result and push

Every time.

```
jj bookmark set main -r @-
```

Not setting the bookmark causes this error:
```
Warning: No bookmarks found in the default push revset: remote_bookmarks(remote=origin)..@
Nothing changed.
```



### If the bookmark does not exist on remote repo 

Only once.

If jj git push causes this problem:

```
Warning: Refusing to create new remote bookmark main@origin
Hint: Use --allow-new to push new bookmark. Use --remote to specify the remote to push to.
Nothing changed.
```



### If the bookmark exists on the remote repo

Only once.

```
jj bookmark track main@origin
```

This tells jj: "Find the local bookmark named main and mark it as tracking main@origin."



### Push the changes

Every time.

```
jj git push
```










## Handle error: Won't push commit a3ba024d331f since it has no description

Example:

```
Error: Won't push commit a3ba024d331f since it has no description
Hint: Rejected commit: lpzzxvzt a3ba024d (no description set)
```

The problem is that some change in the history ( in this case Rejected commit: lpzzxvzt a3ba024d (no description set) ) has no description.
Git insists on a description.

Solution:

```
jj describe a3ba024d -m "changes"
```










## Remove jj from git repo

Running `git clean -xdf` will remove `.jj/`!

```
git clean -xdf
```



