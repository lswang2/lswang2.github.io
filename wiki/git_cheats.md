# git

## make repository
    git> mkdir repository
    git> cd repository
    git> git init --bare
    
## 가져오기
    # 처음으로 가져오기
    > git clone https://github.com/user/project
    
    # 업데이트 된 것을 다시 가져오기
    > git pull
    
## 업로드
    > git commit -a -m "log message"
    > git push
    
## 서버 변경하기
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
    
