# 트랜잭션 격리 수준

- 트랜잭션 격리 수준
    - 동시에 여러 트랜잭션이 처리될 때, 다른 트랜잭션에서 변경하거나 조회한 데이터를 볼 수 있도록 허용 여부를 결정하는 것

- 격리 수준이 필요한 이유
    - 데이터 베이스는 ACID 특징과 같이 독립적인 수행을 해야합니다.
    - 그래서 아예 접근이 불가능게 하면 독립적인 수행을 할수 있지만 성능은 떨어지게 되고 접근을 느슨하게 하면 잘못된 값 처리가 될수 있습니다.
    - 따라서 최대한 효율적인 잠구기(Locking)가 필요하다.

- 트랜잭션 격리 수준의 종류
    - READ UNCOMMITTED(1단계)
    - READ COMMITTED(2단계)
    - REPEATABLE READ(3단계)
    - SELIALIZABLE(4단계)
- 아래로 갈수록 고립도가 올라가고 성능이 떨어집니다.

![https://miro.medium.com/max/475/1*hEpucQJzGE6K7D9M_0bEVw.gif](https://miro.medium.com/max/475/1*hEpucQJzGE6K7D9M_0bEVw.gif)

![image](https://user-images.githubusercontent.com/72914519/157220841-e7be27ff-007c-42f9-87f2-a970e1145431.png)

- READ UNCOMMITTED (트렌젝션 레벨 1)
    - 트랜잭션에서 처리 중인, 아직 커밋되지 않은 데이터를 다른 트랜잭션이 읽는 것을 허용한다.

   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/157220968-669720d9-3f62-4026-a69f-a3206d8f4ef3.png" width="500px;" alt="1"/>
   </p>

- 특징
    - Dirty Read, Non-Repeatable Read, Phantom Read 현상이 발생한다.

- 문제점
    - 데이터 정합성에 문제가 많다. 그렇기에 RDBMS 표준에서는 격리수준으로 인정하지 않는다.

- READ COMMITTED (트렌젝션 레벨 2)
    - 실제 테이블 값을 가져오는 것이 아니라 Undo 영역에 백업된 레코드에서 값을 가져온다.
   
   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/157221203-620486ac-11fe-4f3b-bf01-8f269f5a8e6b.png" width="500px;" alt="1"/>
   </p>


- 특징
    - Dirty Read 가 발생하지 않지만 Non-Repeatable Read, Phantom Read 현상은 여전히 발생한다.
    - 온라인 서비스에서 가장 많이 선택되는 격리수준이다.
- 문제점
    - NON-REPEATABLE READ 부정합 문제가 발생할 수 있다.

- NON-REPEATABLE READ
    - 한 트랜잭션 내에서 같은 쿼리를 두번 수행할 때, 그 사이에 다른 트랜잭션이 값을 수정 또는 삭제함으로써 두 쿼리가 상이하게 나타나는 비 일관성이 발생하는 것을 말한다.
     
   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/157221406-783fd3ea-517c-48ce-ba95-6f5a8574ea50.png" width="500px;" alt="1"/>
   </p>

- REPEATABLE READ (트렌젝션 레벨 3)
    - 트랜잭션이 시작되기 전에 COMMIT된 내용에 대해서만 조회할 수 있는 격리수준입니다.
    - MySQL에서는 트랜잭션마다 트랜잭션 ID를 부여하여 트랜잭션 ID보다 작은 트랜잭션 번호에서 변경한 것만 읽게 된다.
   
   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/157221529-cfe5120f-4795-4e09-a9c4-e0bc698993a4.png" width="500px;" alt="1"/>
   </p>

- 특징
    - Dirty Read와 같은 현상은 발생하지 않지만 Phantom Read현상은 여전히 발생한다.

- 문제점
    - 하나의 트랜잭션 실행시간이 길어질수록 Undo에 백업된 레코드가 많아져서 멀티 버전을 관리해야하는 단점이 있다.

- **Phantom Read**
    - 다른 트랜잭션에서 수행한 변경 작업에 의해 레코드가 보였다가 안 보였다가 하는 현상

   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/157221651-435f11c6-fbc1-4f40-a3f6-844d5ae32b5d.png" width="500px;" alt="1"/>
   </p>
   
- SERIALIZABLE (트렌젝션 레벨 4)
    - 특정 테이블을 읽는 경우 공유 잠금(shared lock) 을 걸어, 다른 트랜잭션에서 해당 테이블의 데이터를 UPDATE, DELETE, INSERT 작업을 못하도록 막는다.

- 특징
    - 가장 단순한 격리 수준이지만 가장 엄격한 격리 수준으로Phantom Read가 발생하지 않는다.

- 문제점
    - 동시 처리 능력이 다른 격리수준보다 떨어지고 성능저하가 발생하여 데이터베이스에서 거의 사용되지 않는다.
