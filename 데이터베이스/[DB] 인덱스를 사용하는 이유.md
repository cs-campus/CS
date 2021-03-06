# 인덱스를 사용하는 이유


- 인덱스란 무엇인가??
    - 추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조입니다.
- 실생활에 인덱스
    - 백과사전이나 책들을 보면 색인(인덱스)라는 페이지를 앞쪽 혹은 뒤쪽에서 볼수있다.
- 인덱스 관리
    - 인덱스는 항상 최신 상태를 유지해야 원하는 값을 빠르게 탐색할수있다.
    - 하지만 인덱스에서는 DB와 달리 Insert, Delete, Update가 달라서 추가적인 작업이 필요하다.
    - INSERT: 새로운 데이터에 대한 인덱스를 추가합니다.
    - DELETE: 삭제하는 데이터의 인덱스를 사용하지 않는다는 작업을 진행합니다.
    - UPDATE: 기존의 인덱스를 사용하지 않음 처리하고, 갱신된 데이터에 대해 인덱스를 추가합니다.
    - 이러한 이유로 빈번한 DELETE와 UPDATE를 하면 내가 가진 DB의 갯수보다 인덱스의 데이터가 훨씬 많아 지게 됩니다.
    - 성능에도 문제가 발생합니다. (뚱뚱해진다.)
- 인덱스의 장/단점
    - 장점 :
        - 압도적인 조회 속도, 전반적인 시스템 부하를 줄일수 있다.
    - 단점 :
        - 추가적인 공간이 필요하므로 공간이 필요하다.(평균 DB의 10%가 필요하다.)
        - 빈번한 CRUD를 하면 추가적으로 인덱스관리를 위한 추가 작업이 필요하다.
    
- 인덱스의 자료구조
    1. 해시 테이블
    - 해시테이블은 탐색속도가 O(1)로 매우 빠릅니다. 하지만 인덱스의 자료구조로 선택을 못받게 되었습니다.
- 해시테이블이 탈락한 이유
    - 헤시 테이블이 탈락한 결정적인 이유는 등호 연산에만 속도가 빠르다는 것입니다.
    - DB 검색시에 부등호(>,<)이 들어있는 경우에는 인덱스 자료구조로 해시테이블이 적합하지 않습니다.(해시 함수로 값들이 전혀 달라지므로 순차적인 검색이 불가능하다.)
    
   <p align="center">
  <img src="https://user-images.githubusercontent.com/72914519/156911492-8286b49b-9d19-4f2e-8d57-69f0309a55cf.png" width="500px;" alt="1"/>
   </p>

2. B(Balanced)-tree
    <p align="center">
     <img src="https://user-images.githubusercontent.com/72914519/156911505-25bbfcf9-6db8-4be0-955b-ed325d07b7fd.png" width="500px;" alt="2"/>
    </p>

- 사각형으로 표시된 한 개 한 개의 데이터를  노드 라고 한다.
- 루트 노드(Root Node) 브랜치 노드(Branch Node) 리프 노드(Leaf Node) 라고 한다.
    <p align="center">
     <img src="https://user-images.githubusercontent.com/72914519/156911509-39ec5d0c-435f-43a5-a2a9-803decf93618.png" width="500px;" alt="2"/>
    </p>
- B-tree가 인덱스에 사용되는 이유
    - 항상 정렬된 상태로 특정 값보다 크고 작은 부등호 연산에 문제가 없다.
    - 참조 포인터가 적어 방대한 데이터 양에도 빠른 메모리 접근이 가능하다.
    - 데이터 탐색뿐 아니라, 저장, 수정, 삭제에도 항상 O(logN)의 시간 복잡도를 가진다.

- B+tree
    - 리프 노드만 인덱스와 함께 데이터를 가지고 있고, 나머지 노드들은 데이터를 위한 인덱스(Key)만을 갖는다.
    - 리프 노드들은 LinkedList로 연결되어 있다.
    <p align="center">
     <img src="https://user-images.githubusercontent.com/72914519/156911519-a6feb76a-cec9-462f-a347-f3d3926c0eba.png" width="500px;" alt="2"/>
    </p>
- b-tree와 b+tree 비교
    <p align="center">
     <img src="https://user-images.githubusercontent.com/72914519/156911523-bf2ce816-5f57-472f-b362-be78cc8ba55a.png" width="500px;" alt="2"/>
    </p>

