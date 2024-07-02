### 문제1([***조건에 맞는 도서 리스트 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/144853)) LEVEL1***

(https://school.programmers.co.kr/learn/courses/30/lessons/144853)

```sql
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE PUBLISHED_DATE LIKE '2021%' AND CATEGORY = '인문';
```

```sql
//JSQL형식
SELECT BOOK_ID, TO_CHAR(PUBLISHED_DATE, 'YYYY-MM-DD') AS PUBLISHED_DATE
FROM BOOK
WHERE TO_CHAR(PUBLISHED_DATE, 'YYYY') = '2021' AND CATEGORY = '인문';

//TO_CHAR(DATE_COLUMN, 'YYYY-MM-DD')  -- 날짜를 'YYYY-MM-DD' 형식의 문자열로 변환
//TO_CHAR(DATE_COLUMN, 'MM/DD/YYYY')  -- 날짜를 'MM/DD/YYYY' 형식의 문자열로 변환
```

- SELECT A FROM B
    - B테이블에서 A를 가져온다
    - E AS F: E를 F라고 부르겠다
    - DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d')
        - (데이터, 형식)
        - 데이터를 특정 형식 모양으로 바꿔준다
- WHERE C (조건)
    - C에 맞는 조건에 맞는 A를 가져온다.
    - LIKE = 부분적으로 일치하는 칼럼
    - _ 글자 수 지정(EX 컬럼명 LIKE '홍_동')
        - 3글자인데 홍X로 구성 된 정보
    - % 글자 수 지정X(EX 컬럼명 LIKE '홍%')
        - 홍으로 시작하는 모든 정보
    - AND 다른 조건 추가

```sql
//재풀이
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE PUBLISHED_DATE LIKE '2021%' AND CATEGORY = '인문';
```