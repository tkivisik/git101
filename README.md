# Git Notes

**General commands**

* git status
* git log
* git remote

## Creating a Repository

### Start locally

echo "# HeadingName" >> README.md  
git init  
git add . #to add all  
git status  
git commit -m "comments for the commit"  
git remote origin https://www.github.com/tkivisik/RepositoryName  
git push origin master  
git status  

### Start remotely

git clone https://www.github.com/tkivisik/RepositoryName

## Working with a Repository

### Branch > Work > Pull Master > Merge > Push

**General**  
git pull <remotename> <branchname>  
git branch <newbranchname>  
git checkout <newbranchname>  
*heavy programming*  
git add .
git commit -m "<comment>"
git checkout <branchname>  
git pull origin <branchname>  
git merge <newbranchname>  
git push origin <branchname>  
git branch -d <newbranchname>
git push origin --delete <newbranchname>  

**An example**  
git pull origin master  
git branch newbranch  
git checkout newbranch  
*heavy programming*  
git add .  
git commit -m "Did some heavy programming"  
git checkout master  
git pull origin master  
git merge newbranch  
git push origin master  
git branch -d newbranch  
git push origin --delete newbranch