### Database Pool
---

- 데이터베이스 풀(pool)
    - Connection pool
    - 애플리케이션의 스레드에서 데이터베이스에 접근하기 위해선 Connection이 필요하다.
    - 따라서, 데이터베이스와 Connection한 객체들을 미리 생성하여 Pool에 저장해두었다가, 클라이언트의 요청이 있을 때마다 사용/반환하는 방식이다!
    
- 데이터베이스 접근과정
    - 웹 컨테이너 실행 → 데이터베이스와 연결된 Connection 객체들을 미리 생성하여 Pool에 저장
    - 클라이언트 요청 → Pool에서 Connection 객체를 가져와 데이터베이스에 접근
    - 요청 처리가 끝나면 다시 Pool에 Connection 객체를 반환한다.
    
- 장점
    - 매 연결마다 Connection 객체를 생성/삭제하는 비용(시간, 자원)의 감소
    - 미리 생성된 Connection 객체를 사용하기 때문에 데이터베이스 접근 시간 단축
    - Connection 수를 제한하여 부하를 조정한다
    
- 단점
    - Connection은 객체이기 때문에 메모리를 차지
    - Connection 개수를 잘 못 설정하면, 쓸데없는 Connection이 발생한다.

- 만약에 Connection이 Pool에서 부족할 경우는 어떻게 처리?
    - 클라이언트가 요청했을 때, 모든 Connection이 작업중이라서 처리를 못하게 된다면, 클라이언트의 요청을 대기 상태로 전환시킨다.
    - 따라서, 작업을 마친 Connection이 Pool에 반환되면 순차적으로 요청을 처리하게 된다.
    
- Thread Pool과 Connection Pool
    - Thread Pool도 마찬가지로, 미리 만들어놓은 쓰레드들의 집합이라고 생각하면 된다!
    - WAS(Web Application Server)에서 Thread Pool과 Connection Pool의 Thread와 Connection의 수는 메모리와 직접적으로 관련이 있음
    - Connection과 Thread 수를 많이 설정하면 메모리를 많이 차지하고, 반대로 적게 설정할 경우 처리하지 못하는 대기 요청이 많아짐
