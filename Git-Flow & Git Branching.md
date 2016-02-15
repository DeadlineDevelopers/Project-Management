What is Git-Flow ?
===================

The Git-Flow Workflow defines a strict branching model designed around the project release. This is a very good way for git branching and release management strategy.

![Example structure of Git-Flow](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/05.svg)

As you can see above, instead of a single master branch, this workflow uses 2 master branches which are master and develop branch.

-**master:** stores official release history. It is convenient that tag all commits with the version number of release.


-**develop:** serves as an integration branch for features.

----------

###Others

-**feature:** is used for new features. When a feature is complete, you should merge this branch back into develop branch. Git-Flow makes it easy to work on multiple features at the same time.

Common conventions:
>- branch off: develop
>- merge into: develop
>- naming convention: *feature-** or *feature/**

**note:** never interact with master directly.

----------
-**release:** When you add enough features to release project, you should create release branch from delevop. When that particular release is ready to ship, it should be merged into both master and develop branch.

Common conventions:
>- branch off: develop
>- merge into: master and develop
>- naming convention: *release-** or *release/**

----------
-**hotfix:** This is the only branch that should be created from master branch. As soon as the fix is complete, it should be merged back into master and develop branches and tagged with the updated version number.

Common conventions:
>- branch off: master
>- merge into: master and develop
>- naming convention: *hotfix-** or *hotfix/**>

----------

## Using Git-Flow 
>- if you are familiar with command interfaces, you can use Git-Flow by using commands. You can install git-flow with this command: `brew install git-flow` and start with `init`command (`$ git flow init`) .
or
>- you can use SourceTree.


---------

##Example

The example below demonstrates how this workflow can be used to manage a single release cycle. We’ll assume you have already created a central repository.

###Create a Develop Branch
![Create a Develop Branch](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/06.svg)

The first step is to complement the default master with a develop branch. A simple way to do this is for one developer to create an empty develop branch locally and push it to the server.

This branch will contain the complete history of the project, whereas master will contain an abridged version. Other developers should now clone the central repository and create a tracking branch for develop:

Everybody now has a local copy of the historical branches set up.

###Furkan and Ahmet begin new features
![Furkan and Ahmet begin new features](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/07.svg)

Our example starts with Furkan and Ahmet working on separate features. They both need to create separate branches for their respective features. Instead of basing it on master, they should both base their feature branches on develop.

Both of them add commits to the feature branch in the usual fashion: edit, stage, commit.

###Furkan finishes his feature
![Furkan finishes her feature](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/08.svg)

After adding a few commits, Furkan decides her feature is ready. If her team is using pull requests, this would be an appropriate time to open one asking to merge her feature into develop. Otherwise, she can merge it into her local develop and push it to the central repository.

The first command makes sure the develop branch is up to date before trying to merge in the feature. Note that features should never be merged directly into master. Conflicts can be resolved in the same way as in the Centralized Workflow.

###Furkan begins to prepare a release
![Furkan begins to prepare a release](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/09.svg)

While Ahmet is still working on his feature, Furkan starts to prepare the first official release of the project. Like feature development, he uses a new branch to encapsulate the release preparations. 

This branch is a place to clean up the release, test everything, update the documentation, and do any other kind of preparation for the upcoming release. It’s like a feature branch dedicated to polishing the release.

As soon as Furkan creates this branch and pushes it to the central repository, the release is feature-frozen. Any functionality that isn’t already in develop is postponed until the next release cycle.

###Furkan finishes the release
![Furkan finishes the release](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/10.svg)

Once the release is ready to ship, Furkan merges it into master and develop, then deletes the release branch(optional). It’s important to merge back into develop because critical updates may have been added to the release branch and they need to be accessible to new features. Again, if Furkan’s organization stresses code review, this would be an ideal place for a pull request.

Release branches act as a buffer between feature development (develop) and public releases (master). Whenever you merge something into master, you should tag the commit for easy reference.

###End-user discovers a bug
![End-user discovers a bug](https://www.atlassian.com/git/images/tutorials/collaborating/comparing-workflows/gitflow-workflow/11.svg)
After shipping the release, Furkan goes back to developing features for the next release with Ahmet. That is, until an end-user opens a ticket complaining about a bug in the current release. To address the bug, Furkan (or Ahmet) creates a maintenance branch off of master, fixes the issue with as many commits as necessary, then merges it **directly back into master**.

Like release branches, maintenance branches contain important updates that need to be included in develop, so Furkan needs to perform that merge as well. Then, Furkan’s free to delete the branch.

**IMPORTANT**: Git-Flow on SourceTree example video will be added if requested.

Useful Links
------
For more information:
>- [https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

>- [http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)
