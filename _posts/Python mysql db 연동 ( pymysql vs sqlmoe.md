---
title: Python mysql db 연동 ( pymysql vs sqlmodel(ORM) )
tags: [Python, MySQL]
date: 2021-10-30 12:18:00 +09:00
categories: [Python]
---

#### 간단한 insert 쿼리로 비교하는 python mysql db 연동 쿼리

# 1. pymysql

## Data class

```python
@dataclass
class School:
    day: str
    members: str
```

## db code

```python
import pymysql as mysql
import logging
from 파이썬파일 import Schools

db = mysql.connect(host='localhost', user='a',
                   password='b', database='c', charset='utf8')

try:
    with db.cursor() as cursor:
        for School in Schools:
              # insert meal
              sql_day_insert = f"insert into school \
                                  values('{School.day}', '{School.member}');"
              cursor.execute(sql_day_insert)
        db.commit()
except Exception as ex:
    logging.error(ex)
finally:
    db.close()
```

## 2. sqlmodel

참조 : [https://sqlmodel.tiangolo.com/tutorial/create-db-and-table/](https://sqlmodel.tiangolo.com/tutorial/create-db-and-table/)

## Data class

```python
class School(SQLModel, table=True):
    day: Optional[str] = Field(default=None, primary_key=True)
    members: int
```

table=True 는 SQLModel에게 table models이라고 알려주는 것이다.

없으면 data models 이다.

day는 PK인데 Optional을 사용한 이유

day는 코드가 아니라 DB에서 auto_increment(자동 생성되어 증가)한다.

따라서 DB에 집어 넣기 전 까지 None이기 때문에 Optional로 None을 허용했다.

## db code

```python
from typing import List
from sqlmodel import (
    create_engine, Session, SQLModel,
)
from 파이썬파일 import Schools

db_user = 'a'
db_pw = 'b'
db_name = 'c'
engine = create_engine(
    f'mysql+pymysql://{db_user}:{db_pw}@localhost/{db_name}')

SQLModel.metadata.create_all(engine)

def insert_notices(Schools: List[School]):
    with Session(engine) as session:
        for School in Schools:
            session.add(School)
        session.commit()
```
