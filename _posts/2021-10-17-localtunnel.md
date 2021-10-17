---
title: [Linux Server] Localtunnel 외부에서 localhost 접속
tags: [Linux, Server]
date: 2021-10-16 15:18:00 +09:00
categories: [Linux, Server]
---

localtunnel github : [https://github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)

Localhost를 외부에서 접근 가능한 주소를 생성한다.

# 1. Localhost에 서버를 등록한다.

1.  react webpack을 활용하는 경우

```html
npx webpack serve
```

2. package.json scripts에 등록한 경우

![1](https://user-images.githubusercontent.com/34102064/137619106-4cc9bd8e-0e69-4ea1-a594-1f48f4f69acf.png)

```html
npm start
```

React에서 사용하는 포트 번호를 확인한다.

![2](https://user-images.githubusercontent.com/34102064/137619110-e8f9e1fb-0229-4ece-9597-dc4f5e235f30.png)

```html
http://localhost:[port]
```

# 2. localtunnel 설치 및 실행

### 2-1, 2-2 중 하나만 선택

### 1. Global 설치 및 실행

다른 프로젝트에서도 실행 가능

**global 설치**

```html
npm i -g localtunnel
```

**global 실행**

```html
lt --port 8080
```

### 2. 해당 프로젝트에서만 설치 및 실행

해당 프로젝트 에서만 사용 가능하다.

```html
npm i localtunnel
```

실행

```html
npx localtunnel --port 8080
```

### 3. Click to Continue 를 클릭한다.

![3](https://user-images.githubusercontent.com/34102064/137619112-2eb7a396-9d90-48c6-a180-c61f05c1cb40.png)

# 3. Options

### 1. 터미널에서 명령어를 실행한다.

```
lt --port 8080 --subdomain todo
   [포트번호]     [도메인 이름 지정]
```

# 4. 에러 처리

### 1. Invalid Host Header error

```
lt --port 8080 --subdomain todo
   [포트번호]     [도메인 이름 지정]
```

위와 같이 실행하면 Invalid Host header 오류가 나는 경우가 있다.

```
lt --port 8080 --subdomain todo --local-host localhost
      [포트번호] [도메인이름지정] [localhost options]
```

[localhost](http://localhost) options을 지정하면 해결 된다.
