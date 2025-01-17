## 📌 1-2. MySQL 설치하기
초기 작성일: Fri Jan 17, 2025
마지막 작성일: Fri Jan 17, 2025

1. `brew update`
2. `brew install mysql`  // 여기까지 설치 과정
    1. 기본적으로 mysql 설치는 되었지만 비밀번호 설정이 안 된 상태
3. `mysql_secure_installation` // 비밀번호 설정
    1. 해당 명령어를 통해 비밀번호 설정을 해 준다.
4. `brew services start mysql`
5. `mysql -u root -p` // mysql 접속