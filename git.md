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
## Pour faire plusieurs commits à partir d'un seul  
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

# Gérer les branches

git branch -av(v)  
git branch -vv  
git branch -r  
git show-branch  
## Crée une branche et reste sur celle en cours  
git branch \<nom\>    
## Crée une branche et bascule sur celle-ci  
git checkout -b \<nom\>   
## Pour créer une branche à partir d'un commit   
* git branch \<nom\> \<hash de départ\>  
* git checkout -b \<nom\> \<hash de départ\>    
## Renommer une branche  
git branch -m (pour move, comme mv) \<vieux nom\> \<nouveau nom\>.  
Si on veut remplacer la branche actuelle: git branch -m \<nouveau nom\>  
<img src="https://user-images.githubusercontent.com/16964230/124143639-93ce1d00-da8b-11eb-9e21-3c5732e11ddb.jpg" width="250" height="250">

# Gérer le dépôt et les branches distantes  

git remote -v  
git remote rename origin zoubida  
git remote show origin  
git fetch: récupère les branches distantes. Ne change pas l'espace de travail. Ajouter un fichier sur une branche distante sur Github pour tester. Sans git fetch: git log origin/test n'affiche que les commits de la branche déjà sur le pc. Git fetch pour récupérer les commits à jour du dépôt.  
## Pour supprimer, sur le pc, la branche distante  
git branch -d -r origin/branch . Faut pusher pour que ce soit pris en compte sur le dépôt (vérifier la syntaxe).  
## Pour mettre à jour la branch origin/... sur mon pc local :  
git fetch  
git push fait en plus le merge de cette branche origin/... sur ma branche locale. Fetch ne change rien à mon répertoire de travail. Il permet d'inspecter origin/..., la met à jour par rapport à ce qu'il y a sur le dépôt.  
git branch -avv pour voir les branches locales et distantes.  
## Pour pousser une branche spécifique:  
git push \<remote\> \<branch\> 

# Rattraper les erreurs

git revert : annule de dernier commit en l'inversant et en faisant un nouveau commit  
git revert : crée un commit pour annuler les changements  
git reset : déplace HEAD sur le commit voulu dans l'espace de git (là où les commits sont stockés)  
git reset --soft HEAD~ : déplace sur le parent de HEAD (HEAD~) sans changer le répertoire de travail ni l'index. Déplace HEAD.  
git reset --mixed HEAD~ : met à jour l'index. C'est le comportement **par défaut** donc git reset HEAD~ fait ça.  
Il a désindexé donc retour à l'état avant git add et git commit. Fait ressembler l'index à HEAD.  
git reset --hard HEAD~ : met à jour la copie de travail. On retrouve les commits avec git reflog.  
git reset HEAD file.txt : ne déplace pas HEAD. Désindexe et met à jour le répertoire de travail. HEAD est ignoré (match avec le dernier commit désigné ici, exemple: HEAD\~2)  
git checkout : met à jour les fichiers non modifiés dans l'espace de travail. Pointe sur une seule branche.  
git reset --hard : remplace tout.  
git rebase  
git rebase -i commit  
git rebase -i HEAD\~3 pour modifier les 3 derniers commits  
git reflog  
git commit --amend pour modifier le dernier commit  
git biscet pour trouver le commit qui a un bug.  

# Plomberie

git clean : pour les fichiers non indexés ( -f pour forcer: sécurité)  
git clean -i ?  
HEAD~ désigne le parent du commit courant (parent de HEAD). Equivalent à HEAD\~1  
HEAD\~2 remonte de 2 commits  
git repository : là où git stocke tous les commits  

# Cherry-pick

git cherry-pick -m1 commit  ou git cherry-pick -m2 commit   
Si cherry-pick d'un commit de merge pour indiquer à git à quelle branche on fait référence.  
Cherry-pick = delta entre deux commits.  
Faire git show commit pour voir si -m1 ou -m2.  
1er parent = TOUJOURS la mainline.  

# Merge

git merge donne un conflit parce que la même ligne a été modifiée  
<img src="https://user-images.githubusercontent.com/16964230/124146694-4e5f1f00-da8e-11eb-9ce0-a0e4127880af.jpg" width="250" height="250">



