# Learn Git branching
---
## Introduction Sequence
### 1.
``` git commit -m "message" ``` - create commit
```sh
git commit
git commit
```
### 2.
``` git branch <newName>``` - create new branch
``` git checkout <name>``` - switch to existing branch
``` git checkout -b <yourbranchname>``` - create a new branch and check it out
```sh
git branch bugFix
git checkout bugFix
```
### 3.
``` git merge <branch>``` - to combine work
```sh
git branch bugFix
git checkout bugFix
git commit
git checkout main
git commit
git merge bugFix
```
### 4.
``` git rebase <branch>``` - take a copy and combine to the branch
```sh
git checkout -b bugFix
git commit
git checkout main
git commit
git checkout bugFix
git rebase main
```
---
## Ramping Up
### 1.
``` git checkout <commit>``` - make a special pointer (HEAD) that represents your current position in the repository
```sh
git checkout C4
```
### 2.
``` ^``` - moving upwards one commit
``` ~<num>``` - moving upwards a number of times
```sh
git checkout HEAD^
```
### 3.
``` git branch -f command```
``` git branch -f <from branch> <to commit>```
``` git branch -f <branch> HEAD~<num>``` - directly reassign a branch to a commit (by force)
```sh
git branch -f main C6
git branch -f bugFix C0
git checkout C1
```
---
## Moving Work Around
### 1.
``` git cherry-pick <Commit1> <Commit2> <...>``` - to copy a series of commits below your current location (HEAD)
```sh
git cherry-pick C3 C4 C7
```
### 2.
``` rebase -i``` - git open a UI to show you which commits are about to copied
```sh
git rebase -i HEAD~4
```
---
## Locally stacked commits
### 1.
```sh
git checkout main
git cherry-pick C4
```
### 2.
``` git commit --ammend``` - to make the slight modification
```sh
git rebase -i HEAD~2
git commit --amend
git rebase -i HEAD~2
git branch -f main C3''
```
### 3.
```sh
git checkout main
git cherry-pick C2
git commit --ammend
git cherry-pick C3
```
### 4.
``` git tag v1 C1``` - making a tag at C1 which is our version 1 prototype
```sh
git tag v1 side~1
git tag v0 main~2
git checkout v1
```
### 5.
``` git describe <ref>```
``` <tag>_<numCommits>_g<hash>``` - the output of the command looks like
```sh
git describe bugfix
git commit
```
---
## Advanced Topics
### 1.
```sh
git rebase main bugFix
git rebase bugFix side
git rebase side another
git rebase another main
```
### 2.
``` git checkout main^``` - alege care părinte să urmezi (important la merge commits).
``` git checkout HEAD~``` - numără câți pași înapoi să mergi (mereu pe primul părinte).
``` git checkout HEAD~^2~2```
```main^^``` se citește ca ```main^1^1``` - adică: mergi la primul părinte al lui main (```main^```), apoi din nou la primul părinte al acelui commit.
```sh
git branch bugWork main^^2^
```
### 3.
```sh
git checkout one
git cherry-pick C4 C3 C2
git checkout two
git cherry-pick C5 C4 C3 C2
git branch -f three C2
```
---
## Push & Pull -- Git Remotes!
### 1.
``` git clone "link"``` - clonam repository-ul remote
ramurile remote se află în repository-ul tău local, nu pe repository-ul remote.
```sh
git clone
```
### 2.
```sh
git commit
git checkout o/main
git commit
```
### 3.
``` git fetch``` realizează doi pași principali:
- descarcă commit-urile pe care remote-ul le are, dar care lipsesc din repository-ul nostru local, și...
- actualizează unde indică ramurile noastre remote (de exemplu, o/main).
```sh
git fetch
```
### 4.
``` git pull``` - aduce schimbările de pe remote și le îmbină automat cu branch-ul local pe care ești acum.
```sh
git pull
```
### 5.
```sh
git clone
git fakeTeamwork main 2
git commit
git pull
```
### 6.
``` git pull --rebase``` - descarca modificarile remote si adauge tot ce ai facut pana la moment dupa modificarile remote
```sh
git clone
git fakeTeamwork main
git commit
git pull --rebase
git push
```
### 7.
```sh
git commit
git commit
git push
```
### 8.
```sh
git branch -f main o/main
git checkout -b feature C2
git push origin feature
```

## To Origin And Beyond -- Adanced Git Remotes!
### 1.
```sh
git fetch
git rebase o/main side1
git rebase side1 side2
git rebase side2 side3
git rebase side3 main
git push
```
### 2.
```sh
git checkout main
git pull
git merge side1
git merge side2
git merge side3
git push
```
### 3.
``` git checkout -b <branch> o/main``` - face track la ``` o/main``` din ``` <branch>```
``` git branch -u o/main <branch>``` - face track la ``` o/main``` din ``` <branch>```
```sh
git checkout -b side o/main
git commit
git pull --rebase
git push
```
### 4. 
``` git push <remote> <place>```
```sh
git push origin main
git push origin foo
```
### 5.
``` git push origin <source>:<destination>```
``` git push origin main:newBranch``` 
```sh
git push origin foo:main
git push origin main^:foo
```

### 6. 
```sh
git fetch origin C3:foo
git fetch origin C6:main
git checkout foo
git merge main
```
### 7.
``` git push origin :<branch>``` - sterge branch-ul remote
``` git fetch origin :<branch>``` - cream un branch nou
```sh
git fetch origin :bar
git push origin :foo
```
### 8.
``` git pull origin foo``` = ``` git fetch origin foo; git merge o/foo```
``` git pull origin bar:bugFix``` = ``` git fetch origin bar:bugFix; git merge bugFix```
```sh
git pull origin C3:foo
git pull origin C2:side
```