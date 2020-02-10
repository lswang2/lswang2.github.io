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

## 기타 팁
~~~~
# 모든 파일 리스트
> git ls-files

# GUI로 diff 보기
> gitk &

# 현재 커밋되지 않은 모든 수정 되돌리기 
> git checkout .
~~~~
