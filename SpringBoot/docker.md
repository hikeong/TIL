# Docker가 뭐지

개발을 하다 보면 "내 환경에서는 잘 되는데?"라는 말을 자주 하게 된다. 로컬 환경, 테스트 서버, 운영 서버마다 설정이나 의존성이 달라서 생기는 문제다. Docker는 이런 문제를 해결하기 위해 등장한 컨테이너 기반 가상화 플랫폼이다.

---

## 1. Docker의 개념

Docker는 애플리케이션과 그 실행 환경을 하나의 컨테이너 안에 묶어서 어디서든 동일하게 동작하도록 만들어 준다. 즉, 운영체제에 상관없이 같은 실행 환경을 보장할 수 있다.

### 컨테이너와 가상머신의 차이

* **가상머신(VM)**: OS 위에 하이퍼바이저를 두고 그 위에 또 다른 OS를 설치하는 방식. 무겁고 느리다.
* **컨테이너**: 호스트 OS 위에서 프로세스를 격리하는 방식. 훨씬 가볍고 빠르다.

---

## 2. Docker의 핵심 개념

### 2.1 이미지(Image)

* 컨테이너를 만들기 위한 템플릿.
* 코드, 라이브러리, 의존성, 설정 등이 모두 포함되어 있다.
* 예: `python:3.10`, `mysql:8.0`

### 2.2 컨테이너(Container)

* 이미지를 실행한 상태.
* 독립적인 실행 환경을 제공한다.
* 필요하면 언제든 생성/중지/삭제 가능하다.

### 2.3 레지스트리(Registry)

* 이미지를 저장하고 공유하는 저장소.
* 대표적인 예: [Docker Hub](https://hub.docker.com/)

---

## 3. 기본 명령어

### 3.1 이미지 다루기

```bash
# 이미지 다운로드
docker pull nginx

# 이미지 목록 확인
docker images

# 이미지 삭제
docker rmi nginx
```

### 3.2 컨테이너 다루기

```bash
# 컨테이너 실행
docker run -d -p 8080:80 nginx

# 실행 중인 컨테이너 확인
docker ps

# 컨테이너 중지
docker stop <container_id>

# 컨테이너 삭제
docker rm <container_id>
```

### 3.3 Dockerfile 사용하기

```dockerfile
# 베이스 이미지 지정
FROM python:3.10

# 작업 디렉토리 설정
WORKDIR /app

# 코드 복사
COPY . .

# 의존성 설치
RUN pip install -r requirements.txt

# 애플리케이션 실행 명령어
CMD ["python", "app.py"]
```

```bash
# Dockerfile로 이미지 빌드
docker build -t myapp .

# 빌드한 이미지 실행
docker run -d -p 5000:5000 myapp
```

---

## 4. Docker Compose

여러 개의 컨테이너를 한 번에 관리하려면 `docker-compose`를 쓰면 편리하다.

```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: testdb
```

```bash
# 전체 서비스 실행
docker-compose up -d

# 전체 서비스 중지
docker-compose down
```

---

## 5. Docker의 장점

* 개발 환경과 운영 환경의 일관성 보장
* 경량화된 가상화로 빠른 실행 속도
* 손쉬운 배포 및 확장성

---

ㄱ ㄱ <br>
ㅡㅡㅡ<br>
     ㅌ

