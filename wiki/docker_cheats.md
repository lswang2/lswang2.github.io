# Docker

## docker hub에서 가져오기

~~~~
docker pull user/project
~~~~

## 실행

~~~~
docker run [--rm] [-it] -v [local_path:container_path] docker_image [command]
# --rm : 실행이 끝난 후 container를 지움
# -it : terminal mode로 실행
# -v : 바깥 폴더를 container에 제공된 폴더로 마운트함

# 여러 명령어를 실행하는 방법
docker run --rm -it docker_image /bin/bash -c "(cd blah;execute command; execute other command)"
~~~~

## 유용한 명령

~~~~
# 현재 모든 이미지 보기
docker images
# 이미지 지우기
docker rmi image_id

# 실행중인 컨테이너
docker ps
# 모든 컨테이너 보기
docker ps -a
# 컨테이너 죽이기
docker kill container
# 컨테이너 삭제
docker rm container

# 컨테이너를 이미지로 전환
docker commit container new_image

# 이미지 저장
docker save image_id -o image_filename
# 이미지 로딩
docker load -i image_filename
~~~~

## 새 이미지 만들기

~~~~
docker build [--no-cache] [--file dockerfile] -t app .
~~~~

## Dockerfile

~~~~
# 원본 이미지
FROM lswang2/build-tools:latest
MAINTAINER wang@picocel.com

# 내부 명령어 실행
RUN         useradd -d /home/usb -g 100 -u 4006 -m usb

# 나중에 마운트될 수있도록 준비
VOLUME      /work

# 현재 디렉토리 지정
WORKDIR        /usr/local

#내부 환경변수 선언
ENV            VERSION=1.3.1
ENV            FILE=or1k_tool_chain_wang_bionic_v${VERSION}.txz

#새 패스 설정
ENV            PATH="/new/path:${PATH}"

# 바깥의 파일을 내부로 복사
COPY       ${FILE} .
RUN            tar Jxvf ${FILE}
RUN            rm -f ${FILE}

WORKDIR     /home/usb
COPY        .vimrc .

WORKDIR     /work

# 실행했을 때 사용자
USER        usb
RUN         echo "alias list=\"or1k-elf-gcc -Wa,-adhln -g\"" >> /home/usb/.bashrc
RUN         echo "export PATH=$PATH:/usr/local/or1k/bin" >> /home/usb/.bashrc

# 실행될 명령어
# 없으면 아무 명령어나 실행할 수 있음
ENTRYPOINT ["/bin/bash"]
~~~~

## hub.docker.com

~~~~
# 도커 허브에 로그인
docker login -u "username" -p "password" docker.io

# 도커 허브에 생성된 image를 업로드
docker push username/project:tag

# 도커 허브에 태그만 바꾸어서 새로 업로드
docker tag username/project:old_tag username/project:new_tag
docker push username/project:new_tag
~~~~

