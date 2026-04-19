# Codeyssey

## 1. 환경 구성 및 기본 명령어 실습

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
backup.txt  sample.txt

abc@c3r1s2 dumy % mv backup.txt renamed.txt
abc@c3r1s2 dumy % ls
renamed.txt sample.txt


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

---

## 2. 핵심 기술 원리 및 설계 근거

**1. 프로젝트 디렉토리 구조 및 경로 선택 기준**
*   **구조 설계:** 호스트의 소스 코드 및 설정 파일(Dockerfile 등)을 작업 환경과 완전히 분리하여 구성했습니다. 이는 로컬 환경의 오염을 막고 컨테이너 내부 환경의 독립성을 보장하기 위함입니다.
*   **경로 선택 (절대경로 vs 상대경로):** 로컬 환경에서 디렉토리를 탐색하고 파일을 조작할 때는 현재 위치를 기준으로 하는 **상대 경로**가 빠르고 직관적입니다. 반면, Dockerfile을 통한 이미지 빌드나 데이터 파이프라인과 같은 자동화 스크립트 작성 시에는 실행 환경에 구애받지 않고 항상 동일한 자원을 참조해야 하므로 **절대 경로**를 명시하여 무결성을 유지했습니다.

**2. 파일 권한 규칙 (chmod 755의 의미)**
리눅스의 파일 권한은 Read(4), Write(2), Execute(1)의 합산으로 결정됩니다. `chmod 755`는 소유자(Owner)에게 읽기/쓰기/실행 권한(4+2+1=7)을 모두 부여하고, 그룹(Group)과 기타 사용자(Others)에게는 읽기/실행 권한(4+1=5)만 부여하여 외부의 무단 수정을 방지하면서도 실행 및 접근이 가능하게 만드는 기본적인 보안 규칙입니다.

**3. 이미지와 컨테이너의 차이 (Build / Run / Change)**
*   **Build (이미지):** 애플리케이션 실행에 필요한 모든 환경(OS, 라이브러리, 소스코드)이 패키징된 '정적 스냅샷'입니다.
*   **Run (컨테이너):** 이미지를 바탕으로 메모리에 적재되어 실제 동작하는 '독립된 프로세스'입니다.
*   **Change (변경):** 컨테이너 내부에서 발생한 파일 생성 및 수정 등은 컨테이너 레이어에 임시로 저장되며, 원본 이미지에는 영향을 주지 않습니다. 컨테이너가 삭제되면 변경 사항도 함께 초기화됩니다.

**4. 포트/볼륨 설정의 재현성 및 네트워크 매핑의 필요성**
*   **포트 매핑 필요성:** 컨테이너는 호스트 망과 논리적으로 분리된 자체 가상 네트워크(Bridge)를 사용합니다. 보안이 적용된 내부 통신망을 외부와 연결하려면 별도의 게이트웨이가 필요하듯, 호스트의 포트와 컨테이너의 포트를 바인딩(-p)해주어야만 외부 클라이언트가 컨테이너 내부 서비스에 접근할 수 있습니다.
*   **설정의 재현 가능성:** 포트와 볼륨 바인딩 규칙을 모두 `docker run -p 8080:80 -v /host/path:/container/path`와 같이 명시적인 커맨드 라인 인자로 문서화하여, 어느 환경에서든 명령어 복사만으로 100% 동일한 인프라가 재현되도록 정리했습니다.
*   **데이터 소실 대안 (볼륨):** 컨테이너의 일회성(Ephemeral) 특징으로 인한 데이터 소실을 방지하기 위해, 컨테이너 생명주기와 독립적으로 호스트의 파일 시스템에 데이터를 영구 저장하는 Bind Mount와 Docker Volume 마운트를 활용했습니다.

---

## 3. 트러블 슈팅 (Troubleshooting)

**1. Docker logs가 공백 로그만 반환하는 현상**
*   **환경:** OS = iMac / Docker version 28.5.2 / Image OS = Ubuntu
*   **진단 과정 (가설 → 확인):**
    1.  컨테이너 내부 프로세스 사망 여부 검증 → `docker ps` 확인 결과 정상 구동 중.
    2.  특정 OS 베이스 이미지 문제인지 검증 → Alpine OS 환경에서는 문제없이 출력됨을 확인.
    3.  로그 파일의 위치 추적 → 컨테이너 내부 접속(`docker exec`) 후 점검 결과, 애플리케이션 로그가 표준 출력이 아닌 컨테이너 내부의 `access.log` 파일에만 단독 기록되고 있음을 발견.
*   **Root Cause 및 조치:** Docker 데몬은 PID 1번 프로세스의 표준 출력(stdout)과 에러 출력(stderr)만 수집하여 로그로 보여줍니다. 해당 Ubuntu 컨테이너의 서비스가 파일에만 로그를 쓰고 있었으므로, Dockerfile 단계에서 `RUN ln -sf /dev/stdout /var/log/app/access.log` 명령어를 추가해 로그 파일을 PID 1번의 표준 출력으로 심볼릭 링크를 걸어 문제를 해결했습니다. (Error 로그도 동일 방식 적용)

**2. Docker의 바인드 마운트(Bind Mount) 시 호스트 파일 인식 실패**
*   **환경:** OS = iMac / Docker version 28.5.2 / Image OS = Ubuntu
*   **진단 과정 (가설 → 확인):**
    1.  로컬 파일 누락 확인 → 로컬 환경에서 `ls` 및 `grep`으로 타겟 파일 존재 검증 (정상).
    2.  Dockerfile의 `COPY` 명령어 충돌 여부 확인 → 명령어 제거 후 빌드/실행 시도 (동일 문제 발생).
    3.  디렉토리 권한 문제 점검 → 디렉토리 자체의 rwx 권한에는 이상 없음 판단.
    4.  iMac(macOS) 고유의 보안 규정 의심 → Docker가 접근할 수 있는 디렉토리 권한 점검.
*   **Root Cause 및 조치:** macOS 환경에서는 보안 규정으로 인해 루트 디렉토리나 특정 `home` 하위 경로에 대해 Docker 데몬의 접근(Mount)이 제한됩니다. 리눅스 환경과 동일하게 생각하여 `home`에 임의로 디렉토리를 생성한 것이 원인이었습니다. 컨테이너 런타임 자체는 동작하지만 마운트 포인트를 읽을 수 없었으므로, 로컬 작업 디렉토리를 보안 접근이 허용된 `usr/` 하위 경로(또는 Docker Desktop File Sharing 허용 경로)로 이동하여 마운트한 결과 정상적으로 인식됨을 확인했습니다.

**3. 추가 예상 이슈: 호스트 포트 충돌 시 진단 순서**
*   "Host port already in use" 에러가 발생할 경우 다음 순서로 조치합니다.
    1.  **가설 설정 및 확인:** 해당 호스트 포트가 이미 다른 데몬에 의해 점유되어 매핑이 거부됨. `lsof -i :<충돌포트>` 또는 `netstat -tulpn` (Mac의 경우 `lsof -i -P -n | grep LISTEN`) 명령어로 점유 중인 프로세스(PID)를 파악합니다.
    2.  **조치 판단:** 점유 중인 프로세스가 불필요한 경우 `kill -9 <PID>`로 종료 후 재시도합니다. 해당 프로세스를 유지해야 한다면, `docker run -p <새로운포트>:<컨테이너포트>`와 같이 호스트 측 매핑 포트를 변경하여 실행합니다.