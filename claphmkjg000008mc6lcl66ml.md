# GIT Master Branch History Lost! - A Quick Solution

# Background
While working on a past project, we encountered a problem while pushing the local changes from a new computer that has an old version of the `master` branch. We did not realize it was old initially though. 😋

# Issue while merging
The error was not so clear and it was just saying push failed. Thinking that it might be an access issue, we then tried to give that user the required access by changing the role to maintainer at GitLab repository members settings. Nothing helped. 😭
![HotMessGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1668951921212/LYu7Hn7Hd.gif align="left")

Then we messed up the master branch by forcing a push from that computer. 😭😭
```
git push --force
```
As a result, the master branch got replaced with the old version, and all its history got removed. 😰

![OmgOmgOmgOmgGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1668951993794/RDnJp9h-N.gif align="left")

# What to do now?
The team was in shock. No one has a clue. After a round of research, we came to a conclusion. To restore everything to normal, we then followed the steps mentioned below. The idea is to make the `master` point to an old commit that can be considered as most recent. Which means we need to find it somewhere. 🔬
## Find out a recent `master` commit
From another computer of a teammate, that had the latest `master` branch, we pointed the head to a previous commit.
```
git reset <commit hash>
```
**NOTE:** Commit hash can be fetched by looking into the ```git log```.
## Force push to remote `master`
Then pushed that local master to the remote master by force again.
```
git push --force
```
Now, the remote `master` pointed to a commit that was not so old and solved the purpose. 
![AomSusharAomGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1668955481162/XqY6fYpJF.gif align="left")
# Learning 
Due to all this, we learned a process that we need to follow every time we merge something to the remote `master`. 🎉

Let’s analyze that below.
 
## Basic Process of New Branch Commit, Push, and Merge
Here are some basic steps we followed in the team to prevent this issue in the future. Whenever you are ready with a change that can be merged to `master`, follow these steps.
1.	Update the local `master` branch.
```
git pull origin master
```
2.	Create a new local branch from the local `master`.
```
git branch SomeInterestingName
```
3.	Do your changes in the new branch as needed for the task.
4.	Your changes are ready.
5.	Commit and push.
```
git commit -m "Some message"
git push origin SomeInterestingBranchName
```
6.	Merge `master` and create a PR.
  
  a. Now checkout `master`.
  ```
git checkout master
```
  
  b. Update `master`.
    ```
git pull origin master
```

  c. Now checkout your new branch.
```
git checkout SomeInterestingBranchName
```

  d. Let’s merge `master` into your new branch.
```
git merge master
```

  e. Commit and push.
```
git commit -m "Some message"
git push origin SomeInterestingBranchName
```

  f. Your branch and master are now in sync.

  g. Now go to your SCM like GitLab/GitHub and select your branch.

  h. Create a Pull Request with the target branch as `master`.
  
  i. After PR is approved, merge after resolving the conflicts, if any.
 

# Would like to hear from you?
Have you faced such a situation? How did you solve it? It would be very interesting to discuss. Put a comment below. 🙏

Thanks for reading. Have a nice day. 🙂
