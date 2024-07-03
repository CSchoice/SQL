### 문제6(**대장균들의 자식의 수 구하기*) LEVEL3***

[https://school.programmers.co.kr/learn/courses/30/lessons/273711](https://school.programmers.co.kr/learn/courses/30/lessons/299305)

```sql
SELECT A.ID, COALESCE(COUNT(B.PARENT_ID), 0) AS CHILD_COUNT
FROM ECOLI_DATA A
LEFT JOIN ECOLI_DATA B ON B.PARENT_ID = A.ID
GROUP BY A.ID
ORDER BY A.ID;
```

- COALESCE(A,B)
    - A 와 B를 비교하는데 A의 값이 NULL인 경우 B 값으로 대체, 둘 다 NULL이면 NULL값 사용
- JOIN
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/c44bdff3-448d-41a1-99ac-a641e8a78595/d79bf6e1-72f6-4487-bd42-116a6af842f0/Untitled.png)
    

```sql
// JSQL
SELECT A.ID, COALESCE(COUNT(B.PARENT_ID), 0) AS CHILD_COUNT
FROM ECOLI_DATA A
LEFT JOIN ECOLI_DATA B ON B.PARENT_ID = A.ID
GROUP BY A.ID
ORDER BY A.ID;
```