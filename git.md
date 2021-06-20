# Début

git init  
git clone https://  
git status  
git config  
Pour créer un alias: git config --global alias.rename 'branch -m'

# Commiter

git commit -m  
git cherry-pick commit  
git diff  
git checkout  
git checkout -b \<branch\>  
git branch -b  
git branch -d / git branch -D  
git add .  
git ignore  
## Pour commiter une portion de fichier seulement  
git add -p fichier (ou git add --patch fichier) puis e pour éditer à la main. Le mot est **hunk** ou **patch**.  
## Pour faire plusieurs commits à partir d'un  
* reset et commiter les changements voulus. Et git rebase -i
* git show commit

# Tag

git tag  
git tag -m zoubida (étiquette légère) sur le dernier commit  
puis git show zoubida  
git tag -a (annotée) V1.4 (étiquette) -m commentaire (-f pour force) Le commentaire apparaît en faisant git show etiquette V1.4  
git tag etiquette (pas besoin de -m) puis git show etiquette  
Pour tag un ancien commit: git tag -a etiquette commit  
git tag : affiche la liste des tags  
git push ne pousse pas les étiquettes ; faire :  
* git push origin etiquette  
* git push push origin --tags (pour toutes les étiquettes) 
 
git tag -d etiquette pour effacer  

# Stash

git stash save  
git stash list  
git stash drop/apply  
git stash pop (apply puis drop)  

# Logs

git log --graph --decorate --pretty=oneline  
git log --graph --pretty=oneline --all  
gitrevisions : git log master..origin/master (affiche les commits dans cette plage, le range)  
git show commit pour voir les détails d'un commit particulier  
