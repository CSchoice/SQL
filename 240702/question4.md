### 문제4(3월에 태어난 여성 회원 목록 출력하기***) LEVEL2***

https://school.programmers.co.kr/learn/courses/30/lessons/131536

```sql
SELECT A.USER_ID, A.PRODUCT_ID
FROM ONLINE_SALE AS A
GROUP BY 1, 2
HAVING COUNT(USER_ID) >= 2
ORDER BY USER_ID ASC, PRODUCT_ID DESC;
```

```sql
SELECT USER_ID, PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(USER_ID) >= 2
ORDER BY USER_ID ASC, PRODUCT_ID DESC;
//숫자가 아닌 필드를 직접 입력
```

- GROUP BY
    - 데이터를 그룹화 해줌
    - 숫자를 사용하면 SELECT문의 몇 번째 항목인지 나타냄
    - 직접 항목을 입력해도 괜찮다
- HAVING
    - GROUP BY와 같이 사용하며 WHERE처럼 조건을 추가해준다
    - `COUNT`, `SUM`, `AVG` 등을 사용 가능
- 정렬
    - ASC: 오름차순
    - DESC: 내림차순
        
        ```sql
        //재풀이
        SELECT USER_ID,	PRODUCT_ID
        FROM ONLINE_SALE
        GROUP BY 1, 2
        HAVING COUNT(PRODUCT_ID) > 1
        ORDER BY USER_ID, PRODUCT_ID DESC
        ```