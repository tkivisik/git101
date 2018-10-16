# Git Notes

## General commands

### Getting Help
See git help
```bash
git --help
```

See git manual
```bash
man git
```


### General
See the status of git. Which branch are you on and which files have been modified.
```bash
git status
```

Show recent commit history with an author, date and a commit message.
```bash
git log

# Also show detailed branches
git log --graph --all --decorate
```

Show the name of a tracked remote (non-local) repository. Remote has a name and a URL associated with it.  Origin is a common remote repository name.
```bash
git remote

# Also show the remote repository URL
git remote --verbose
```

Show currently tracked branches
```bash
git branch

# Also show the last commit message
git branch --verbose
```

## Creating a Repository

### Start locally
```bash
echo "# HeadingName" >> README.md
git init
git add .     #to add all
git status
git commit -m "comments for the commit"

# The remote repository must already exist.
git remote origin https://www.github.com/github-user-name/repository-name
git push origin master
git status
```

### Start remotely

When a repository already exists, the easiest to hop on board is to clone it.
```bash
git clone https://www.github.com/github-user-name/repository-name
```

## Working with a Repository

### Branch > Work > Pull Master > Merge > Push

**General**

```bash
# Make sure the local branch is up to date with the remote
git pull <remotename> <branchname>

# The next two commands can be combined into writin:
# git checkout -b <newbranchname>
git branch <newbranchname>
git checkout <newbranchname>


# The next four steps are to be repeated until a new branch is mature enough
# to be merged back into the main branch:
# *heavy programming*
git add .
git commit -m "<comment>"
git push origin <newbranchname>

# Switch back to the main branch, make sure you have the latest remote version
# of it locally, then merge the new branch into it and push it to remote.
git checkout <branchname>   # switch back to devel branch for example
git pull origin <branchname>
git merge <newbranchname>
git push origin <branchname>

# Clean up (remove) the branch locally
git branch -d <newbranchname>
# Clean up (remove) the branch remotely
git push origin --delete <newbranchname>
```

**An example**
```bash
git pull origin master
git branch newbranch
git checkout newbranch
# *heavy programming*
git add .
git commit -m "One line to explain recent coding"
git checkout master
git pull origin master
git merge newbranch
git push origin master

# Clean up development branches locally and remotely
git branch -d newbranch             # locally
git push origin --delete newbranch  # remotely
```

## Branches and Naming

Read also:
* [Successful git branching model](http://nvie.com/posts/a-successful-git-branching-model)

It makes sense to keep your development separate from working and tested code. That can be achieved by first branching off from a master to a development branch (copy of a working system). Then, real work can be done on feature branches branched off from a single development branch.

```bash
# Create a remote repository (github, bitbucket, etc.)
# Clone it (it becomes a master branch)
git clone https://www.github.com/github-user-name/repository-name
# Create a development branch to keep development and nicely
# running code separate.
git checkout -b devel
# Create feature branches to allow for parallel development
# of separate features.
git checkout -b feat/user1/explain-what-you-are-developing-1

# Move back to develoment branch
git checkout devel
# Branch off to start another line of development in parallel
git checkout -b feat/user2/explain-what-you-are-developing-2

git checkout devel
# Merge merges a branch you name into a branch you are currently
# checked out to (currently, to devel).
git merge feat/user2/explain-what-you-are-developing-2

# Branch off from a development branch to a release candidate branch
# once there are enough potential new additions to production code.
# Apply only bug fixes
git checkout -b rc1/explain-added-features
git checkout master

# Once tested enough, merge the release candidate into the master.
git merge rc1/explain-added-features
```

## Contributing to Open Source Projects

Recommended read to get started with open source:
https://www.digitalocean.com/community/tutorial_series/an-introduction-to-open-source

Also this:
https://opensource.guide/

Every now and then there are also events like Hacktoberfest:
https://hacktoberfest.digitalocean.com/

### General Workflow

1. Find a project to contribute to
2. Read through their contributing guidelines
3. Find a part which needs contributions (Look under the Issues section in GitHub, filter based on tags like *needs help* or *good first issue* or *hacktoberfest*)
4. See if anybody already claimed the issue for himself/herself to solve. If not, ask if it's fine if you claimed it.
5. Fork the project (it will copy the project to your github account)
6. Add a new remote pointing to the original source repository, e.g. named *upstream*. `git remote add upstream https://github.com/original-owner-username/original-repository.git`
7. Clone the forked project to your computer
8. Make a new branch for your changes
9. Make your changes on that branch & Add them to staging & commit them.
10. Merge your changes to the master branch
11. Get the latest version of the original source repository (upstream) `git fetch upstream`
12. Merge the original and your contributions (while being on the master branch). `git merge upstream/master`
13. Deal with conflicts when they appeared
14. Create a pull request so the maintainers of the original source can merge your contribution
15. Be ready to make further updates and changes based on the maintainers feedback

Also

* Feel great about what you've learned along the way
* Feel part of the community
* Feel great about your contribution
* Feel great about the support you have been given
