### 문제7(대장균의 크기에 따라 분류하기 2***) LEVEL3***

[https://school.programmers.co.kr/learn/courses/30/lessons/273711](https://school.programmers.co.kr/learn/courses/30/lessons/301649)

```sql
SELECT ID,
    CASE 
        WHEN rank_size <= (total_count * 0.25) THEN 'CRITICAL'
        WHEN rank_size <= (total_count * 0.50) THEN 'HIGH'
        WHEN rank_size <= (total_count * 0.75) THEN 'MEDIUM'
        ELSE 'LOW'
    END AS COLONY_NAME
FROM (
    SELECT ID, 
           RANK() OVER (ORDER BY SIZE_OF_COLONY DESC) AS rank_size,
           COUNT(*) OVER () AS total_count
    FROM ECOLI_DATA
) AS sample
ORDER BY ID;
```

- CASE END

```sql
    CASE 
        WHEN rank_size <= (total_count * 0.25) THEN 'CRITICAL'
        WHEN rank_size <= (total_count * 0.50) THEN 'HIGH'
        WHEN rank_size <= (total_count * 0.75) THEN 'MEDIUM'
        ELSE 'LOW'
    END AS COLONY_NAME
```

- CASE로 시작해서 WHEN에 조건을 추가하고 THEN에 이름을 새로 붙임
    - END로 끝냄
    - 마지막은 ELSE로 처리 가능
- PERCENT_RANK() OVER (ORDER BY SIZE_OF_COLONY DESC)
    - SIZE_OF_COLONY를 기준으로 랭킹을 만들어준다
    - 백분율 순위로 만들어준다
- over
    - OVER()을 사용하면 GROUP BY나 서브쿼리를 사용하지 않고 분석 함수(SUM, MAX, COUNT)과 집계 함수(ORDER BY)를 사용
    
    ```sql
    1.
    RANK()OVER(ORDER BY SAL DESC)  'RANK'
    		# 순위를 매겨준다
    2.	
    use world;
    select continent, name, gnp, 
    avg(gnp) over() '전세계 평균',
    avg(gnp) over( partition by continent ) '대륙별 평균'
    from country;
    3.
    COUNT(*) OVER () AS total_count
    전체 데이터 행의 수
    ```
    
- FROM속에 또  SELECT와 FROM을 사용할 수 있음

```sql
//JSQL
SELECT ID,
    CASE 
        WHEN rank_size <= (total_count * 0.25) THEN 'CRITICAL'
        WHEN rank_size <= (total_count * 0.50) THEN 'HIGH'
        WHEN rank_size <= (total_count * 0.75) THEN 'MEDIUM'
        ELSE 'LOW'
    END AS COLONY_NAME
FROM (
    SELECT ID, 
           RANK() OVER (ORDER BY SIZE_OF_COLONY DESC) AS rank_size,
           COUNT(*) OVER () AS total_count
    FROM ECOLI_DATA
) AS sample
ORDER BY ID;
```