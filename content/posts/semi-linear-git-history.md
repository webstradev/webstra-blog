+++
title = "GitLab's semi-linear Git history"
date = 2023-05-18T21:23:17+02:00
draft = true
tags = ['git', 'coding', 'software-engineering']
+++

![clean history](/images/clean-history.png)
_Photo by [Yancy Min](https://unsplash.com/@yancymin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/photos/842ofHC6MaI?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)_

# Introduction
Working with multiple developers on the same project can often result in messy git histories and unnecessary merge commits when updating feature branches from main. 

Moreover, merge requests might not be based on the latest version of main when all CI checks pass and manual testing is done. This can result in CI passing on the merge request but failing once merged to main. Or even features that were working when tested on the feature branch, that broke after being merged to main. 

Lastly, a non-linear history results in commits from a feature branch being scattered on the main branch, ordered only by the commit's timestamp. This can make it hard to trace which commits were introduced in which order and makes it virtually impossible to check out previous commits without including various other unrelated changes.

In this post, we will take a look at some of the different merge strategies and how GitLab's semi-linear history can help you keep a much cleaner git history.

# A non-linear history
If a merge request MR#1 is based on an older version of main, the tests that run on the merge requests are not guaranteed to pass after being merged to main. This is because newer commits on main could conflict with or break code on MR#1 without necessarily having a merge conflict that prevents MR#1 from being merged. 

Naturally, this could be solved by *always* merging `main` into a feature branch before creating a merge request. However, there are a few drawbacks to this merging strategy:

- It requires the developer to manually update their branch from main *locally* before creating a merge request. This can be forgotten or done incorrectly. 

- It Puts the responsibility of the branch being up to date on the developer, without an easy way to see this on a merge request.

- It creates superfluous merge commits like Merge branch 'main' into 'feature-1'

- Commits from different branches get entangled quickly because they are kept in order of time. This is easiest to explain visually. So I will demonstrate this below.

 
Let's look at a straightforward git flow. Commits in blue are (merge) commits on main. The green and orange branches have the same root on main and are developed in parallel (simulating two developers working on different feature branches simultaneously). Furthermore, there is an extra commit on main (simulating a hotfix, a third branch being merged or something along those lines).

![Non-Linear Example](/images/non-linear-example.png)

The merge request for feat/green is merged on Jan 7 and feat/orange is merged on Jan 10.
Before merging the feature branches were first updated from main which is necessary to ensure the CI on the merge request includes the latest commits on main.
 
With a standard non-linear history where branches are updated from main using `git merge` we would get something like this:

![Non-Linear Example #2](/images/non-linear-example2.png)

The three main issues are that we have lost a bit of traceability on which commits belong together, it would be a lot harder to check out an earlier commit without also throwing out any commits that happened after that on different branches and lastly, we have created two unnecessary merge commits when updating our feature branches from `main`.
 

This can quite clearly make the git history difficult to read and manage without visual editors that draw all the diverging branches for you like [GitKraken](https://www.gitkraken.com/). Whilst being able to see the diverging branches on an editor can come in handy, it can also get hard to read very quickly if you don't keep a clean git history.

![Messy Git History](/images/messy-history.png)
_A messy Git history. Source: [When do you use Git rebase instead of Git merge?](https://stackoverflow.com/questions/804115/when-do-you-use-git-rebase-instead-of-git-merge?ref=workingsoftware.dev)_

_One important thing to note is that these problems get considerably amplified when you increase the number of developers working on a repository or the time spent on a feature branch (or both)._

---
# A semi-linear history
To solve the issues mentioned above, we can use GitLab's semi-linear history. This is a history where we update our feature branches from main using `git rebase` instead of `git merge`, but still merge feature branches into main with a `git merge` (resulting in a merge commit). This gives us a history where the commits from the feature branch are added on top of the latest commit on main with a merge commit so the entire merge can easily be reverted.

As you can see in the image below, commits still retain their actual commit dates; however, they are ordered based on when they were merged to `main`. This leads to a much cleaner git history while still preserving merge commits allowing for easy reverts and traceability.

![non-linear vs semi-linear](/images/non-vs-semi.png)
_standard merge commits vs merge commit with semi-linear history_


---
# A linear history (fast-forward-merge)
I'm going to skim over this one rather quickly as I truly believe this is never the right way to go for any project that has more than one developer.

A fully linear history is a history where all commits are added on top of each other in a straight line. This can be achieved by keeping feature branches up to date with main using `git rebase` and then merging the feature branch into main using `git merge --ff-only`. This will result in a fast-forward merge where the commits from the feature branch are added on top of the latest commit on main.

GitLab has the option to enforce this, but I would advise against it. If you use this merge method, there will no longer be any merge commits on your `main` branch. This means you will no longer be able to revert all the commits from a single merge request in one action. Besides that, you won't be able to see any distinction between commits from different merge requests, unless you go onto the actual merge request on GitLab. If we go back to the example used above we would simply end up with a straight line with no merge commits and no way to tell which commits belong together (even in visual editors like GitKraken).


![full-linear history](/images/full-linear.png)
_A full linear git history, otherwise known as "Traceability Nightmare"_