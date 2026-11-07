# E1-workroom 미션

## 📋 프로젝트 개요
Docker를 이용한 Nginx 웹서버 구축 및 배포

## 🚀 빠른 시작
# 1. 저장소 클론
git clone https://github.com/binary67890/E1-workroom.git

# 2. 폴더 이동
cd E1-workroom

# 3. Docker 이미지 빌드
docker build -t mywebsite .

# 4. 컨테이너 실행
docker run -p 8080:80 mywebsite

# 5. 브라우저에서 확인
http://localhost:8080

## 🛠️ 개발환경

### 사무실 PC
- OS: Windows 11
- WSL2: Ubuntu 22.04.5 LTS
- Docker: 29.9.2
- Git: 설정 완료
- 경로: /home/binary67/projects/mywebsite

### 집 PC
- OS: Windows 11
- WSL2: Ubuntu 22.04
- Docker: 설치 완료
- Git: 설정 완료
+ 경로: /home/binary68/E1-workroom

## 📁 프로젝트 구조
mywebsite/
├── Dockerfile # Nginx 웹서버 설정
├── index.html # 웹페이지 (한글 지원)
├── README.md # 프로젝트 설명
└── .gitignore # Git 무시 파일


## 🔐 파일 권한

### 권한 설정 기준
- **디렉토리**: 755 (rwxr-xr-x)
  - 소유자: 읽기, 쓰기, 실행
  - 그룹: 읽기, 실행
  - 기타: 읽기, 실행

- **파일**: 644 (rw-r--r--)
  - 소유자: 읽기, 쓰기
  - 그룹: 읽기
  - 기타: 읽기

### 권한 설정 명령어
```bash
# 디렉토리 권한 설정
chmod 755 /home/binary67/projects/mywebsite

# 파일 권한 설정
find /home/binary67/projects/mywebsite -type f -exec chmod 644 {} \;

📍 경로 개념
절대 경로
루트(/)에서 시작하는 경로
예: /home/binary67/projects/mywebsite/index.html
어디서든 같은 경로를 가리킴
상대 경로
현재 위치에서 시작하는 경로
예: ./index.html, ../README.md
현재 위치에 따라 달라짐
경로 확인 명령어

# 현재 위치 확인
pwd

# 절대 경로로 변환
realpath ./index.html

# 파일 접근 (절대 경로)
cat /home/binary67/projects/mywebsite/index.html

# 파일 접근 (상대 경로)
cat ./index.html

📝 터미널 로그 기록
명령어 기록 확인

# 모든 기록 보기
history

# 최근 20개 보기
history 20

# 특정 명령어 검색
history | grep docker
history | grep git

# nano 관련 명령어
history | grep nano

# git 관련 명령어
history | grep git
이전 명령어 다시 실행

# 마지막 명령어 실행
!!

# 특정 번호 명령어 실행
!25

# 특정 문자로 시작하는 명령어 실행
!docker
!git

# 역방향 검색
Ctrl + R

로그 파일 위치
~/.bash_history

🐳 Docker 명령어
이미지 빌드
docker build -t mywebsite .

컨테이너 실행
docker run -p 8080:80 mywebsite

실행 중인 컨테이너 확인
docker ps

컨테이너 중지
docker stop container_id

📤 Git 명령어
상태 확인
git status

파일 추가
git add .

커밋
git commit -m "commit message"

푸시
git push origin main

풀
git pull origin main

📚 학습 내용
완료한 항목
✅ WSL2 + Ubuntu 설치
✅ Docker 설치 및 설정
✅ Nginx 웹서버 Dockerfile 작성
✅ HTML 파일 작성 (한글 지원)
✅ Docker 이미지 빌드 및 컨테이너 실행
✅ GitHub 저장소 생성 및 동기화
✅ VS Code 설정
✅ Git 사용자 정보 설정
✅ SSH 키 생성 및 설정
✅ 절대 경로 vs 상대 경로 학습
✅ 파일 권한 (r/w/x) 학습
✅ 권한 숫자 표시 (755, 644) 학습
✅ 터미널 로그 기록 학습
✅ 파일 권한 설정 완료
   - 디렉토리: chmod 755
   - 파일: chmod 644
진행 중인 항목
🔄 README.md 작성
🎯 다음 단계
README.md 작성 완료
Git 커밋 및 푸시
집 PC에서 동기화
📞 참고사항
모든 명령어는 WSL2 Ubuntu 터미널에서 실행
Docker 이미지 이름: mywebsite
포트 매핑: 8080:80
GitHub 저장소: E1-workroom (또는 mywebsite)
프로젝트 경로: /home/binary67/projects/mywebsite

작성일 : 2025년 11월 07일

