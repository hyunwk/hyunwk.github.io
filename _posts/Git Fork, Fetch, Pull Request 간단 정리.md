---
title: Git Fork, Fetch, Pull Request 간단 정리
tags: [Git]
date: 2021-10-28 12:18:00 +09:00
categories: [Git]
---

## fork

다른 사람 Repository를 내 저장소로 가져온다.

## fetch

Remote repository에 commit 등 변동사항이 있을 경우, local에서는 remote repository의 변동사항을 모른다. fetch로 local 데이터와 병합하지 않고, 변동사항을 가져올 수 있다.

## pull request

1. fork로 가져온 내 repository에서 변경사항 있을 시 push로 최신상태로 만든다.
2. 내 repository의 변경사항을 folk 했던 repository에서도 업데이트 하고 싶을 때 pull request를 날린다.

## pull request message convention

양식(convention)이 존재하는 경우에만 준수하면 된다.
