# 자바 jdbc

- JDBC란?
    - 자바에서 데이터베이스를 사용하기 위한 절차에 대한 규약을 의미한다.
    - DBMS에 따라 DB를 다루는 방식이 다르다면, 사용자는 알아야 할 것이 매우 많을 것임
    - 그래서 JDBC를 통해 추상화된 인터페이스를 제공하기만 하고, 각 벤더들( Oracle, Mysql 등.. )은 각자의 DBMS에 맞게 구현을 해놓은 상태이다.
    - 따라서, JDBC는 인터페이스를 제공하기 때문에 어떤 종류의 DB(벤더)를 사용하든지 사용하는 방법에는 변함이 없는 것이다.

- JDBC API 클래스
    - 데이터베이스를 연결하여 테이블 형태의 자료를 참조
    - SQL 문을 질의
    - SQL 문의 결과를 처리

![image](https://user-images.githubusercontent.com/46801877/156502661-5b082684-d635-4b30-8324-344f0c7a5bd6.png)


- JDBC를 이용한 데이터베이스 연동과정

![image](https://user-images.githubusercontent.com/46801877/156502697-0a6b4f14-7cbf-4ad1-979f-cbcf5ea2c89a.png)


- 드라이버를 로드 → 그에 따른 Connection 객체를 생성 → 이때 커넥션 객체를 통해 쿼리를 날리는 Statement를 작성할 수 있다.
- 만약에 테이블 형태의 결과를 반환하는 쿼리문들은 Statement의 executeQuery() 메서드를 사용한다. → 예) select * from student; 모든 학생 정보를 불러오는 테이블 조회를 한다면 결과는 테이블의 형태일 것이다 → 이와 같은 테이블 형태로 결과를 반환할 때 반환형은 ResultSet 인터페이스다.
- ResultSet 인터페이스에는 현재 행을 가리키는 커서(Cursor)의 개념이 있다. 이 커서를 다음으로 이동시키는 메서드가 next()다.
- INSERT는 일반적으로 동적으로 값이 할당되므로 createStatement()를 호출하지 않고, 쿼리를 준비하는 statement라는 의미로 prepareStatement() 메서드를 호출한다. → 값이 할당되면 executeUpdate() 메서드를 실행해서 값을 삽입할 수 있다.

- 정리
    - 쿼리를 수행할 때 동적으로 할당해야 하는 값이 있으면 PreparedStatement 객체를 사용하고, 동적으로 할당할 필요가 없으면 Statement 객체를 사용한다.
    - 쿼리의 결과가 있으면 executeQuery() 메서드를 호출하여 ResultSet 객체에 담고, 쿼리의 결과가 없으면 executeUpdate() 메서드를 호출하여 int형 변수에 결과 값을 할당한다.
    - 정적 : 단순 조회
    - 동적 : 값을 삽입, 삭제, 수정 등등
