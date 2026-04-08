# Codeyssey

# PWD
abc@c3r1s2 ~ % pwd
/Users/abc

# ls -al
abc@c3r1s2 ~ % ls -al
total 56
drwxr-x---+ 25 abc  abc    800 Apr  8 21:05 .
drwxr-xr-x  12 root            admin             384 Apr  8 13:24 ..
..
..

# mkdir - cd
abc@c3r1s2 ~ % mkdir dumy 
abc@c3r1s2 ~ % cd dumy 
abc@c3r1s2 dumy % 

# touch - cat - cp - mv 
alswnssldk4632@c3r1s2 dumy % touch sample.txt
alswnssldk4632@c3r1s2 dumy % echo "Workstation Test" > sample.txt
alswnssldk4632@c3r1s2 dumy % ls
sample.txt

alswnssldk4632@c3r1s2 dumy % cat sample.txt 
Workstation Test

alswnssldk4632@c3r1s2 dumy % cp sample.txt backup.txt
alswnssldk4632@c3r1s2 dumy % ls
backup.txt	sample.txt

alswnssldk4632@c3r1s2 dumy % mv backup.txt renamed.txt
alswnssldk4632@c3r1s2 dumy % ls
renamed.txt	sample.txt


# chmod 
alswnssldk4632@c3r1s2 dumy % ls -l                 
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:18 renamed.txt
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:13 sample.txt

alswnssldk4632@c3r1s2 dumy % chmod 755 renamed.txt
alswnssldk4632@c3r1s2 dumy % ls -l 
-rwxr-xr-x  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:18 renamed.txt
-rw-r--r--  1 alswnssldk4632  alswnssldk4632  17 Apr  8 21:13 sample.txt

# docker -v
alswnssldk4632@c3r1s2 ~ % docker --version 
Docker version 28.5.2, build ecc6942

# docker run hello-world
alswnssldk4632@c3r1s2 ~ % docker run hello-world 
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:452a468a4bf985040037cb6d5392410206e47db9bf5b7278d281f94d1c2d0931
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
--

# docker pull ubuntu
alswnssldk4632@c3r1s2 ~ % docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
---------: Pull complete 
Digest: --------------------------------------------
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

# docker -it 
alswnssldk4632@c3r1s2 ~ % docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

alswnssldk4632@c3r1s2 ~ % docker run -it --name my-ubuntu ubuntu bash 
root@819a343a7d89:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@819a343a7d89:/# exit 
exit

# docker / Dcokerfile - index.html

# docker / bind mount 

# docker / curl

# docker / 로컬 파일 변경 (index.html)

# docker / curl 변경확인

# docker / 볼륨 마운트

# docker / 볼륨이 마운트 된 곳에서 파일 생성

# docker / 해당 컨테이너를 지우고 볼륨 확인

# git / 기본설정 확인

# git ssh / ssh 키 만들고 확인
