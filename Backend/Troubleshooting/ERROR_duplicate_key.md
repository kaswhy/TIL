## 📌 PK 중복 오류 해결

초기 작성일: Wed Mar 19, 2025<br/>
마지막 작성일: Wed Mar 19, 2025

> org.postgresql.util.PSQLException: ERROR: **duplicate key** value violates unique constraint "recruit_member_pkey"<br/>
> Detail: Key (id)=(294) already exists.

### ✅ 오류 설명

postgres에서 객체에서 생성된 pk 값이 이미 테이블에 있는 경우 pk가 중복되는 오류가 발생한다.

### ✅ 원인

서버 이전 시 기존 db의 데이터를 옮길 때 Datagrip의 export 기능을 사용했다. <br/>
데이터를 옮긴 후 pk 값은 그대로 유지되었지만, 테이블의 순서는 함께 업데이트되지 않아서 pk 중복 문제가 발생하였다.

### ✅ 해결

1. 현재 시퀀스 값 확인
    ```SQL
    SELECT last_value FROM recruit_member_id_seq;
    ```
2. 현재 데이터에서 가장 큰 id 값 확인
    ```SQL
    SELECT MAX(id) FROM recruit_member;
    ```
3. 시퀀스 값 업데이트
    ```SQL
    SELECT setval('recruit_member_id_seq', (SELECT MAX(id) FROM recruit_member) + 1);
    ```
