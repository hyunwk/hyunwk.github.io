---
title: React mui (UI Library) table
tags: [Python, mui]
date: 2021-10-22 12:18:00 +09:00
categories: [Python]
---

### mui 라이브러리 예시 코드 정리

## table 태그 사용

```jsx
<table>
  <tr>
    <td>조회수</td>
    <td> 제목</td>
  </tr>
  {data.products.map((data, nth) => {
    return (
      <tr key={data.no}>
        <td>{data.no}</td>
        <td>{data.title}</td>
      </tr>
    );
  })}
</table>
```

## mui table 태그 사용

```jsx
<TableContainer component={Paper}>
  <Table aria-label="simple table">
    <TableHead>
      <TableRow>
        <TableCell align="right">id</TableCell>
        <TableCell align="left">제목</TableCell>
      </TableRow>
    </TableHead>
    <TableBody>
      {data.map((data, nth) => (
        <TableRow key={data.no}>
          <TableCell align="left">{data.no}</TableCell>
          <TableCell align="left">{data.title}</TableCell>
        </TableRow>
      ))}
    </TableBody>
  </Table>
</TableContainer>
```

## table 태그 사용

<img src="https://user-images.githubusercontent.com/34102064/140165527-c9309a22-2261-4783-a291-322dea51bb11.png" width="300"></img>

## mui table 태그 사용

<img src="https://user-images.githubusercontent.com/34102064/140165446-8c35f4bb-e67f-4fce-a0c0-65196b5ff266.png" width="300"></img>
