SELECT문 기본 형식

```jsx
SELECT 열 이름 // 보여주고 싶은 속성 이름을 지정한다. 모두 보여주고 싶다면 *을 사용
FROM 테이블 이름 // 보여줄 테이블을 지정한다. 보여줄 속성이 들어있는 테이블을 적는다.
WHERE 조건식 // 내가 원하는 조건을 정한다. 위 조건에 맞는 속성들만 보여준다.
GROUP BY 열 이름 // 적힌 속성이 같은 것 끼리 그룹화 시킨다.
HAVING 조건식 // guoup by 에서 적힌 속성에 대한 조건을 정한다. 위 조건에 맞는 속성만 그룹화 시킨다.
ORDER BY 열 이름 // 적힌 속성을 기준으로 정렬한다. 
```

```jsx
USE DB 이름
```

- SQL을 사용할 데이터베이스를 정한다.

SELECT에 사용하는 구문

DISTINCT - 중복 데이터 출력 X

```jsx
SELECT DISTINCT booknum
FROM book;
// book 테이블에 있는 booknum 속성을 중복 데이터 제거 후 조회
```

DATEDIFF - 두 값의 시간, 날짜 차이를 알 수 있다. (int로 반환해준다.)

```jsx
SELECT DATEDIFF ('day', '2023-08-22', '2023-09-01');

// 결과 : -10
```

구분자 종류

|  | 구분자 | 약어 |
| --- | --- | --- |
| 년도 | year | yy or yyyy |
| 분기 | quarter | qq or q |
| 월 | month | mm or m |
| 일 | day | dd or d |
| 주 | week | wk |
| 시간 | hour | m |
| 분 | minute | mi or n |
| 초 | second | ss or s |
| 밀리초 | millisecond | ms |
| 마이크로초 | microsecond | mcs |
| 나노초 | nanosecond | ns |
|  |  |  |

주의사항! 나는 Mysql에서 실행을 했는데 Mysql에서는 구분자 없이 day로만 값이 나오는 것 같다.