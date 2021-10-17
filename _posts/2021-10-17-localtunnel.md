---
title: Localtunnel 외부에서 localhost 접속
tags: [Javascript]
date: 2021-10-16 15:18:00 +09:00
categories: [Server]
---

localtunnel github : [https://github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)

Localhost를 외부에서 접근 가능한 주소를 생성한다.

# 1. Localhost에 서버를 등록한다.

1.  react webpack을 활용하는 경우

```html
npx webpack serve
```

2. package.json scripts에 등록한 경우

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/101c3a2a-9e5e-4e98-b3e5-07928f74a62a/Untitled.png)

```html
npm start
```

React에서 사용하는 포트 번호를 확인한다.

![Untitled](Localtunnel%20%E1%84%8B%E1%85%AC%E1%84%87%E1%85%AE%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5%20localhost%20%E1%84%8C%E1%85%A5%E1%86%B8%E1%84%89%E1%85%A9%E1%86%A8%20248de45842eb45fab87b1b872f666d19/Untitled%201.png)

```html
http://localhost:**8080** [port]
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

![Untitled](Localtunnel%20%E1%84%8B%E1%85%AC%E1%84%87%E1%85%AE%E1%84%8B%E1%85%A6%E1%84%89%E1%85%A5%20localhost%20%E1%84%8C%E1%85%A5%E1%86%B8%E1%84%89%E1%85%A9%E1%86%A8%20248de45842eb45fab87b1b872f666d19/Untitled%202.png)

# 3. Options

### 1. 터미널에서 명령어를 실행한다.

```html
lt --port 8080 --subdomain todo [포트번호] [도메인 이름 지정]
```

# 4. 에러 처리

### 1. Invalid Host Header error

```html
lt --port 8080 --subdomain todo [포트번호] [도메인 이름 지정]
```

위와 같이 실행하면 Invalid Host header 오류가 나는 경우가 있다.

```html
lt --port 8080 --subdomain todo --local-host localhost [포트번호] [도메인 이름
지정] [localhost options]
```

[localhost](http://localhost) options을 지정하면 해결 된다.
