# E1-workroom 미션

## 📋 프로젝트 개요
Docker를 이용한 Nginx 웹서버 구축 및 배포  
바인드마운트(Bind Mount)를 활용한 데이터 영속성 실습

---

## 🚀 빠른 시작

```bash
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
🛠️ 개발환경
🏢 사무실 PC
항목	내용
OS	Windows 11
WSL2	Ubuntu 22.04.5 LTS
Docker	29.9.2
Git	설정 완료
경로	/home/binary67/projects/mywebsite
🏠 집 PC
항목	내용
OS	Windows 11
WSL2	Ubuntu 22.04
Docker	설치 완료
Git	설정 완료
경로	/home/binary68/E1-workroom
🏫 교육장 PC (GNIA-C202-E01)
항목	내용
OS	WSL2 Ubuntu 26.04.1 LTS (Resolute)
Docker	29.9.3
Git	2.53.0
사용자	binary673054
경로	/home/binary673054/E1-workroom
📁 프로젝트 구조
code
📋 복사
E1-workroom/
├── Dockerfile              # Nginx 웹서버 설정
├── index.html              # 웹페이지 (한글 지원)
├── README.md               # 프로젝트 설명
└── bind-mount-test/        # 바인드마운트 실습 폴더
    └── index.html          # 바인드마운트 테스트 페이지
🐳 Docker 실습
기본 컨테이너 실행
bash
📋 복사
# 이미지 빌드
docker build -t mywebsite .

# 컨테이너 실행
docker run -p 8080:80 mywebsite

# 실행 중인 컨테이너 확인
docker ps

# 컨테이너 중지
docker stop [container_id]
🔗 바인드마운트(Bind Mount) 실습
개념
항목	설명
정의	호스트(WSL2)의 폴더를 컨테이너 내부 폴더에 직접 연결
특징	호스트 파일 수정 → 컨테이너에 즉시 반영
용도	개발 중 실시간 파일 수정, 로그 수집
차이	볼륨(Volume)은 Docker가 관리, 바인드마운트는 호스트 경로 직접 지정
동작 원리
code
📋 복사
[호스트 WSL2]                          [컨테이너 내부]
~/E1-workroom/bind-mount-test/  ←→  /usr/share/nginx/html/
        index.html  ←─────────────────────  index.html
        (파일 수정 시 컨테이너에 즉시 반영됨)
실습 명령어
bash
📋 복사
# 1. 실습 폴더 생성
mkdir -p ~/E1-workroom/bind-mount-test

# 2. 테스트 HTML 파일 생성
nano ~/E1-workroom/bind-mount-test/index.html

# 3. 바인드마운트로 컨테이너 실행
docker run -d \
  -p 8081:80 \
  -v ~/E1-workroom/bind-mount-test:/usr/share/nginx/html \
  --name bind-test \
  nginx

# 4. 브라우저에서 확인
http://localhost:8081

# 5. 컨테이너 중지 및 삭제
docker stop bind-test
docker rm bind-test
데이터 영속성 검증
bash
📋 복사
# 컨테이너 삭제 후에도 호스트 파일은 유지됨
docker rm -f bind-test

# 파일 확인 → 그대로 남아있음 ✅
ls ~/E1-workroom/bind-mount-test/
바인드마운트 vs 볼륨 비교
항목	바인드마운트	볼륨(Volume)
경로 지정	호스트 경로 직접 지정	Docker가 자동 관리
이식성	낮음 (경로 의존)	높음
용도	개발 환경, 실시간 수정	운영 환경, DB 데이터
명령어	-v 호스트경로:컨테이너경로	-v 볼륨이름:컨테이너경로
🔐 파일 권한
권한 설정 기준
대상	숫자	표기	의미
디렉토리	755	rwxr-xr-x	소유자: 읽기·쓰기·실행 / 그룹·기타: 읽기·실행
파일	644	rw-r--r--	소유자: 읽기·쓰기 / 그룹·기타: 읽기
권한 설정 명령어
bash
📋 복사
# 디렉토리 권한 설정
chmod 755 ~/E1-workroom

# 파일 권한 일괄 설정
find ~/E1-workroom -type f -exec chmod 644 {} \;

# 권한 확인
ls -la ~/E1-workroom/
📍 경로 개념
절대 경로 vs 상대 경로
구분	설명	예시
절대 경로	루트(/)에서 시작	/home/binary673054/E1-workroom/index.html
상대 경로	현재 위치에서 시작	./index.html, ../README.md
경로 확인 명령어
bash
📋 복사
pwd                        # 현재 위치 확인
realpath ./index.html      # 절대 경로로 변환
cat ./index.html           # 상대 경로로 파일 접근
📤 Git 명령어
bash
📋 복사
git status                 # 상태 확인
git add .                  # 파일 전체 추가
git add README.md          # 특정 파일 추가
git commit -m "메시지"      # 커밋
git push origin main       # 푸시
git pull origin main       # 풀
📝 터미널 로그 기록
bash
📋 복사
history                    # 모든 기록 보기
history 20                 # 최근 20개 보기
history | grep docker      # docker 관련 검색
history | grep git         # git 관련 검색
!!                         # 마지막 명령어 재실행
Ctrl + R                   # 역방향 검색
📚 학습 내용
✅ 완료한 항목
WSL2 + Ubuntu 설치
Docker 설치 및 설정
Nginx 웹서버 Dockerfile 작성
HTML 파일 작성 (한글 지원)
Docker 이미지 빌드 및 컨테이너 실행
GitHub 저장소 생성 및 동기화
VS Code 설정
Git 사용자 정보 설정
SSH 키 생성 및 설정
절대 경로 vs 상대 경로 학습
파일 권한 (r/w/x) 학습
권한 숫자 표시 (755, 644) 학습
터미널 로그 기록 학습
파일 권한 설정 완료
바인드마운트(Bind Mount) 개념 학습
바인드마운트 실습 폴더 및 HTML 파일 생성
바인드마운트 컨테이너 실행 및 브라우저 확인
데이터 영속성 검증 완료
교육장 PC 환경 설정 및 실습 완료
README.md 업데이트
🎯 다음 단계
Docker Volume 실습
Docker Compose 학습
집 PC에서 동기화 확인
📞 참고사항
모든 명령어는 WSL2 Ubuntu 터미널에서 실행
Docker 이미지 이름: mywebsite
포트 매핑: 8080:80 (기본) / 8081:80 (바인드마운트 실습)
GitHub 저장소: E1-workroom
교육장 PC 경로: /home/binary673054/E1-workroom
작성일: 2025년 11월 07일
최종 수정: 2025년 11월 07일 (교육장 PC 환경 및 바인드마운트 실습 내용 추가)

code
📋 복사

---

### 저장 및 푸시

```bash
# nano 저장
Ctrl + O → Enter → Ctrl + X

# Git 커밋 및 푸시
cd ~/E1-workroom
git add README.md
git commit -m "docs: 교육장 PC 환경 및 바인드마운트 실습 내용 추가"
git push origin main

