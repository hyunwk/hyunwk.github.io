---
title: React(React Query 사용)+ Express.js + MySQL 연동
tags: [Python, MySQL, React]
date: 2021-10-31 12:18:00 +09:00
categories: [Python, React]
---

React , Express.js, MySQL 연동 기록

## version

```python
React 17.0.2
react-query 3.29.1
Express.js 4.17.1
MySQL 8.0.27
```

# Express.js + MySQL 연동

### 서버 code

## config/db.js

```python
var mysql = require('mysql');
const db = mysql.createPool({
    host : 'localhost',
    user : 'user1',
    password : 'pw1',
    database : 'school'
});
module.exports = db;
```

mysql DB의 기본 정보들을 저장한다.

db모듈을 export하여, db를 사용하는 곳에서 Import 후 사용할 수 있다.

## server.js 기본 셋팅

```python
const express = require('express');
const app = express();
const PORT = process.env.PORT || 4000;
const db = require('./config/db');
```

`process.env.PORT || 4000` 서버의 환경 port를 사용하거나, 없으면 포트를 4000으로 지정한다.

`PORT=4444 node server.js` 의 경우에는 4444번 포트를 사용한다.

## sever.js 서버 연동

```python
app.get('/api/meal', (req, res) => {
		sql = `select meal from school';

    db.query(sql, (err, data) => {
        if(!err) res.send({ products : data });
        else res.send(err);
    })
})
```

해당 서버의 주소에서 `api/meal` 의 주소로 get reques가 들어올 경우 sql문을 실행한다.

```jsx
const PORT = process.env.PORT || 4000;

app.listen(PORT, () => {
  console.log(`Server On : http://localhost:${PORT}/`);
});
```

PORT(위의 예시의 경우 4000 포트) 로 접속 성공 시 콜백 함수를 실행한다.

간단한 쿼리를 실행하면 되기에 직접 sql문을 작성하였지만,

쿼리를 직접 실행하는 대신 더 나은 방법들이 있다.

ex) `Prisma`, `TYPEORM`, `safe-typeorm`

# react-query +Express.js 연동

```jsx
import { QueryClient, QueryClientProvider } from 'react-query';

const queryClient = new QueryClient();

ReactDOM.render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>,
  document.getElementById('root'),
);
```

`QueryClient` **:** can be used to interact with a cache (캐쉬 관리를 해준다)

`QueryClientProvider` : to connect and provide a `QueryClient` to your application:

`QueryClientProvider`로 묶는 이유는 App 컴포넌트에 client를 전달해주기 위해서다.

### React코드

```python
1.  const { status, data, error, isFetching } = useQuery('meal', async () => {
2.      const { data } = await axios.get('/api/meal');
3.      return data;
4.  });
5.  if (!data) {
6.      return <p> loading... </p>;
```

react-query의 useQuery를 사용하여 작성하였다.

`await axios.get('')` 으로 비동기로 해당 주소에서 get방식으로 데이터를 가져온다.

1. 처음 rendering 될 때, `await axios.get('/api/meal')`가 실행되는것을 기다리지 않기 때문에 바로 5번쨰 줄의 if문으로 넘어가서 return을 출력한다.
2. 데이터를 다 받아왔을 때, 다시 rendering하여 data를 return 한다.
