# git branch

## When you merge your branches, if conflicts occur ~ 

### 1. Merge 상황에서 해결

git merge main  
vi {filename}  
* 수정시, (=====,<<<<<<,>>>>>>) 꼭 삭제  
* 수정 완료시, 다시 commit  

### 2. rebase의 방법으로 해결(git flow에서는 사용하지 않음)  

git rebase main  
* conflict 발생 시 conflict 해결  
vi {filename}  

* conflict 해결 후, add와 continue  
해당 변경사항 commit 넘기려면 skip  

* rebase 취소하려면 abort  
git add {filename}  
git rebase --continue  

### conflict 해결방법  

1. merge 시 해결(이미merge 명령을 내린 경우)  
git branch -D stem  

2. 미리 변경사항을 적용  
첫 push에는 remote와 local의 branch 연결(-u)이 필요  
git push -u origin stem  
git push -u origin stem  

3. See the differences  
git diff main stem  


## stash  

<작업중인 변경사항 잠시 미뤄두기>  
-- 작업 중 브랜치 이동이 필요할 때 사용  
git stash  
git stash save "{content}"  

<쌓아놓은 작업사항 복구하기>  
git stash pop  
git stash pop {index}  
git stash apply  

<쌓아둔 작업사항 리스트 확인하기>  
git stash list  

<{index} 번째 작업사항 삭제하기>  
git stash drop {index}  

## rename

- 파일 이름 혹은 위치 수정    
mv a.md to b.md
  
## undo

- working directory에서 변경사항 취소하기  
git restore {filename}  
git restore .(whole changes)  

## unstaging

- stage의 변경사항(blob) working directory로 내리기  
git reset HEAD {filename}  

## unstaging and remove

- staging area의 변경사항을 내림과 동시에 삭제  
git rm -f {filemname}  

## edit commit message

- 직전 commit message 수정하기  
git commit --amend  
  
- 이전 commit message 수정하기  
git rebase -i <commit>
git rebase --continue  
  
- rebase 취소  
git rebase --abort  

## reset commit

- 없었던 일로 만들기  
git reset --hard HEAD~{num of commit}
git push -f origin <branch>  
  
* 협업 시에는 나의 local과 clone한 remote repo에서 지워졌다고 해도 다른 곳에 남아있던 이력으로 인해 살아나거나, 충돌이 발생함  





