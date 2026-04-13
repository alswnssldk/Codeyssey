# Codeyssey

# PWD
abc@c3r1s2 ~ % pwd
/Users/abc@c3r1s2

# ls -al
abc@c3r1s2 ~ % ls -al
total 56
drwxr-x---+ 25 abc@c3r1s2  abc@c3r1s2    800 Apr  8 21:05 .
drwxr-xr-x  12 root            admin             384 Apr  8 13:24 ..
..
..

# mkdir - cd
abc@c3r1s2 ~ % mkdir dumy 
abc@c3r1s2 ~ % cd dumy 
abc@c3r1s2 dumy % 

# touch - cat - cp - mv 
abc@c3r1s2 dumy % touch sample.txt
abc@c3r1s2 dumy % echo "Workstation Test" > sample.txt
abc@c3r1s2 dumy % ls
sample.txt

abc@c3r1s2 dumy % cat sample.txt 
Workstation Test

abc@c3r1s2 dumy % cp sample.txt backup.txt
abc@c3r1s2 dumy % ls
backup.txt	sample.txt

abc@c3r1s2 dumy % mv backup.txt renamed.txt
abc@c3r1s2 dumy % ls
renamed.txt	sample.txt


# chmod 
abc@c3r1s2 dumy % ls -l                 
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:18 renamed.txt
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:13 sample.txt

abc@c3r1s2 dumy % chmod 755 renamed.txt
abc@c3r1s2 dumy % ls -l 
-rwxr-xr-x  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:18 renamed.txt
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:13 sample.txt

# docker -v
abc@c3r1s2 ~ % docker --version 
Docker version 28.5.2, build ecc6942

# docker run hello-world
abc@c3r1s2 ~ % docker run hello-world 
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:452a468a4bf985040037cb6d5392410206e47db9bf5b7278d281f94d1c2d0931
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
--

# docker pull ubuntu
abc@c3r1s2 ~ % docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
---------: Pull complete 
Digest: --------------------------------------------
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

# docker -it 
abc@c3r1s2 ~ % docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

abc@c3r1s2 ~ % docker run -it --name my-ubuntu ubuntu bash 
root@819a343a7d89:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@819a343a7d89:/# exit 
exit

# docker / Dcokerfile - index.html
<img width="308" height="126" alt="Dockerfile_index cat" src="https://github.com/user-attachments/assets/0833c521-96ab-490a-a95a-62d2f6103b5f" />

# docker / bind mount 
<img width="807" height="29" alt="bind_mount" src="https://github.com/user-attachments/assets/b199ef34-1ad6-46eb-8207-4ce6d81bfdc6" />

# docker / curl
<img width="393" height="118" alt="crul" src="https://github.com/user-attachments/assets/e25b8604-637d-4d1e-bba0-ee4cd4b0c9c1" />
<img width="1742" height="1060" alt="web_check" src="https://github.com/user-attachments/assets/ab19d717-cc51-4d11-a247-992ac1e24685" />

# docker / 로컬 파일 변경 (index.html)
<img width="304" height="129" alt="index_FIX" src="https://github.com/user-attachments/assets/ce888bdb-525c-494c-8d7e-d07b75ed7a73" />

# docker / curl 변경확인
<img width="388" height="116" alt="bind_mount_FIX" src="https://github.com/user-attachments/assets/ce7f8d9e-8530-4202-9e3d-e8c6ee93e27c" />

# docker / 볼륨 마운트
<img width="983" height="73" alt="volume mount" src="https://github.com/user-attachments/assets/1ea4942b-9e53-439b-b050-cb23a8595aab" />

# docker / 볼륨이 마운트 된 곳에서 파일 생성
<img width="281" height="87" alt="volume make file" src="https://github.com/user-attachments/assets/6dceb31c-b4a9-41b6-91fd-ba75130b0239" />

# docker / 해당 컨테이너를 지우고 볼륨 확인
<img width="559" height="144" alt="volume_live_file" src="https://github.com/user-attachments/assets/02d0b91c-f3f4-43d3-9eca-98903919cbef" />

# git / 기본설정 확인
<img width="409" height="213" alt="git_config_list" src="https://github.com/user-attachments/assets/6806c38b-bdbf-4581-8205-a77d4a87b236" />

# git ssh / ssh 키만들고 확인 
<img width="649" height="44" alt="git_ssh_log" src="https://github.com/user-attachments/assets/2e70bdc3-eb23-4533-ac87-b29de11bce7d" />

# 트러블 슈팅

1. Docker logs가 공백 로그만 반환

OS = imac
Docker version 28.5.2
img OS = 우분투

1-2. Testing

1-2-1. 컨테이너 내부 프로세스가 죽었는가? -> docker ps 확인 결과 정상 구동 중

1-2-2. OS별 문제인가? -> alpine os 문제 없음을 확인

1-2-3. 로그는 어디에 있는가? -> 컨테이너 내부 접속(exec) 후 확인 결과, 로그가 access.log 파일에만 기록되고 있음을 확인.

Root Cause: 도커 데몬은 해당 OS의 PID 1번 프로세스가 뱉는 표준출력과 에러출력만 그대로 가져와서 출력 단 해당 ubuntu는 표준출력과 에러출력을 access.log 및 에러 로그 파일에 저장중 이기에 dockerfile 이미지 설정 단계에서 "RUN ln -sf /dev/stdout /var/log/app/access.log" access파일을 pid1번 표준출력으로 심볼릭을 걸어줌 error 로그도 동일하게 적용


2. Docker의 바인드 마운트시 파일 인식 실패

OS = imac
Docker version 28.5.2
img OS = 우분투

2-2. Testing

2-2-1. 파일이 실제로 존재하는가? -> 로컬 환경에서 그랩또는 ls를 통해 파일의 확장명과 존재 유무 확인

2-2-2. dockerfile 단계에서 COPY로 미리 파일을 넣은게 문제인가? -> 삭제후 재시도 동일한 문제 발생

2-2-3. 해당 디렉토리 구조가 잘못되었는가? -> 추가적인 디렉토리 없음 

2-2-4. docker는 해당 디렉토리를 인식할수 없는가? -> 디렉토리 권한 확인시 문제없음 다만 imac의 디렉토리 보안규정확인

Root Cause: imac 특유의 home 디렉토리는 보안 규정에 따라 docker가 인식이 불가능한 경로였음 본인은 리눅스마냥 그냥 home에 디렉토리를 만들고 사용했음 그렇기에 이미지는 만들수있고 런까지 돌릴수있지만 파일 인식불가 로컬 디렉토리를 usr/ 로 이동후 재시도 -> 성공
