# git

## make repository
~~~~
git> mkdir repository
git> cd repository
git> git init --bare
~~~~

## 가져오기
~~~~
# 처음으로 가져오기
> git clone https://github.com/user/project

# 업데이트 된 것을 다시 가져오기
> git pull
~~~~

## 새 repository 만들기
~~~~
> git init
> git add files
> git commit -m "message"
> git remote add server_name user@host:port/path
> git push server_name master
~~~~

## 업로드
~~~~
> git commit -a -m "log message"
> git push       # push mater branch only
> git push --all # push all branches
~~~~

## branch & merge
~~~~
# branch만들기
> git checkout -b new_branch_name
또는
> git branch new_branch_name # 현재 버전을 branch로 고정해 둠

# edit files

# merge
> git commit -a -m "branch checkin"
> git pull
> git checkout master
> git merge new_branch_name

# edit conflicts
> git commit -a -m "merging message"
> git push
~~~~

## 서버 변경하기
~~~~
# 현재 서버 정보
> git remote -v

# 새 서버를 추가하려면
# [https,ssh]://user@server:[port]/path/to/project
> git remote add new_server_name url

# 서버 이름 변경
> git remote rename old_name new_name

# 서버 URL 변경
> git remote set-url server_name new_url

# 새 서버에 업로드
> git push server_name master
~~~~

## 롤백
~~~~
# 로그 확인하기
# commit_key는 긴 것이나 7자리의 짧은 것을 사용해도 된다.
> git log  # full log print
> git log --oneline -N  # 한줄 씩 최근 N개 출력

# 현재 커밋되지 않은 수정 되돌리기 
> git checkout .  # 모든 수정
> git checkout folder # 해당 폴더 내부 전부
> git checkout -- file # 해당 파일만

# revert
# 해당 버전 이후의 commit을 유지함
> git revert <commit_key>  # 해당 commit을 HEAD commit으로 바꿈, working directory 유지

# reset
# 해당 버전 이후의 모든 commit을 지워버림
> git reset --soft <commit_key>  # git repository에서 HEAD를 해당 버전으로 되돌림
> git reset [--mixed] <commit_key> # # repository + index(add한 상태)도 바꿈
> git reset --hard <commit_key> # 위에 덧붙여 working directory의 내용도 해당 버전으로 모두 되돌림
~~~~

## 기타 팁
~~~~
# 모든 파일 리스트
> git ls-files

# GUI로 diff 보기
> gitk &
~~~~
