---
title: React 무료 서버 호스팅 Github page
tags: [Linux, Git]
date: 2021-10-18 15:18:00 +09:00
categories: [Git, Linux]
---

Create-React-App 없이 webpack으로 react를 구성한 프로젝트를 위한 github page 연동이다.

github page를 사용하여 무료로 서버를 사용할 수 있다.

## 1. npm i gh-pages

npm i command로 gh-pages 패키지를 추가한다.

## 2. package.json 추가

주소는 repository - Settings - Pages에 있다.

![1](https://user-images.githubusercontent.com/34102064/137724712-b2479691-b622-4e25-bfaf-cce99dd61974.png)

package.json에 homepage와 predeploy, deploy를 추가한다.

```html
"homepage": "주소",
```

```html
"scripts": { "start": "webpack serve", "build": "webpack --mode production",
"predeploy": "npm run build", "deploy": "gh-pages -d dist" },
```

## 3. npm run deploy

명령어로 dist폴더를 생성 후, 그 안에 있는 폴더를 해당 주소로 연동해준다.

github에 dist폴더가 올라간 후부터 [github.io](http://github.io) page에 연동되기 까지 delay가 있다.
