# Docker 웹서버 프로젝트

## 📌 프로젝트 개요
Windows WSL2 환경에서 Docker를 이용해 nginx 웹서버를 구축하고, 한글을 지원하는 웹사이트를 배포했습니다.

## 🛠️ 사용 기술
- **OS**: Windows WSL2 + Ubuntu 22.04.5 LTS
- **컨테이너**: Docker
- **웹서버**: nginx
- **언어**: HTML5

## 📂 프로젝트 구조
mywebsite/
├── Dockerfile # Docker 이미지 설정
├── index.html # 웹사이트 메인 페이지
└── README.md # 이 파일


## 🚀 설치 및 실행 방법

### 1. Docker 이미지 빌드
```bash
docker build -t mywebsite:1.0 .

docker run -d -p 80:80 --name mywebsite-container mywebsite:1.0

📋 진행 과정
✅ 완료된 작업
WSL2 + Ubuntu 22.04.5 LTS 설치
Docker 엔진 설치 및 설정
hello-world 컨테이너 테스트
HTML 파일 작성 (한글 지원)
Dockerfile 작성 (nginx + UTF-8 인코딩)
Docker 이미지 빌드 성공
웹서버 실행 및 한글 표시 확인

FROM ubuntu:26.04
RUN apt-get update && apt-get install -y nginx
COPY index.html /var/www/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

📝 HTML 파일 특징
UTF-8 인코딩으로 한글 완벽 지원
DOCTYPE HTML5 선언
반응형 웹디자인 기초 구조
💡 학습 포인트
Docker 기본 개념: 이미지, 컨테이너, 레이어
WSL2 활용: Windows에서 Linux 환경 구축
웹서버 배포: nginx를 이용한 정적 웹사이트 호스팅
문자 인코딩: UTF-8을 통한 다국어 지원
🎯 향후 계획
CSS/JavaScript 추가
데이터베이스 연동
Docker Compose로 다중 서비스 관리
CI/CD 파이프라인 구축
📧 작성자
binary67

📅 작성일
2026년 11월 5일
