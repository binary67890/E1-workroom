# Docker 웹서버 구축 프로젝트

## 📋 프로젝트 개요
- **목표**: Docker를 이용한 Nginx 웹서버 구축 및 GitHub 제출
- **환경**: WSL2 + Ubuntu 22.04.5 LTS
- **상태**: 진행중 (웹서버 구축 완료, GitHub 푸시 대기)

---

## ✅ 완료된 작업

### 1. 개발 환경 구축
- WSL2 + Ubuntu 22.04.5 LTS 설치
- Unix 계정 생성
- apt update 실행

### 2. Docker 설치
- 보안 도구 설치 (curl, ca-certificates, gnupg)
- Docker GPG 키 등록 및 검증
- Docker 저장소 주소 등록
- Docker 엔진 설치 (8개 패키지)
- Docker 데몬 실행 및 상태 확인
- hello-world 컨테이너 테스트 성공

### 3. Docker 실습
- Ubuntu 26.04 컨테이너 진입 체험
- 컨테이너 탈출 성공

### 4. 웹서버 프로젝트 구축
- 작업폴더 생성: `~/projects/mywebsite`
- **index.html** 작성 (한글 포함)
- **Dockerfile** 작성 (Nginx 기반, 한글 인코딩 설정)
- 이미지 빌드 성공

### 5. GitHub 저장소 생성
- 저장소명: **E1-workroom**
- 사용자명: **binary67890**

---

## 📁 프로젝트 구조

\`\`\`
~/projects/mywebsite/
├── Dockerfile
├── index.html
└── README.md
\`\`\`

### Dockerfile 내용
\`\`\`dockerfile
FROM nginx:latest
RUN apt-get update && apt-get install -y locales
RUN sed -i 's/# ko_KR.UTF-8/ko_KR.UTF-8/' /etc/locale.gen && locale-gen
ENV LANG=ko_KR.UTF-8
COPY index.html /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
\`\`\`

### index.html 내용
\`\`\`html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Docker 웹서버</title>
</head>
<body>
    <h1>Docker 웹서버에 오신 것을 환영합니다!</h1>
    <p>한글 인코딩 테스트: 성공! ✓</p>
</body>
</html>
\`\`\`

---

## ⏳ 다음 작업: GitHub 푸시

### Git 초기화 및 커밋
\`\`\`bash
cd ~/projects/mywebsite

git init
git add .
git commit -m "Docker 웹서버 구축 - Nginx + 한글 지원"
\`\`\`

### GitHub에 푸시
\`\`\`bash
git remote add origin https://github.com/binary67890/E1-workroom.git
git branch -M main
git push -u origin main
\`\`\`

### 확인 명령어
\`\`\`bash
git remote -v
git log
\`\`\`

---

## 📝 주의사항
- GitHub 토큰 필요 (비밀번호 대신 Personal Access Token 사용)
- 푸시 시 인증 정보 입력 필요
- WSL과 Windows 간 파일 동기화 확인

---

## 🔗 관련 링크
- GitHub: https://github.com/binary67890/E1-workroom
- Docker Hub: https://hub.docker.com/_/nginx
- Docker 공식 문서: https://docs.docker.com/

---

**마지막 업데이트**: 웹서버 구축 완료  
**다음 작업**: GitHub 푸시
