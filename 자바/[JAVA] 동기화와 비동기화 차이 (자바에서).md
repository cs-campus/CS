- 동기화(Syncronous)
    - 한 자원에 동시에 접근하는 것 제한
    - 순차적으로 진행
    - Java에서 synchronized 키워드 사용

- 비동기화(Asyncronous)
    - 현재 실행 중인 명령이 종료되지 않아도 다음 명령 실행 가능

```java
class User {
    private int userNo = 0;
 
    // 임계 영역을 지정하는 synchronized메소드
    public void add(String name) {
        System.out.println(name + " : " + userNo++ + "번째 사용");
    }
}
 
class UserThread extends Thread {
    User user;
 
    UserThread(User user, String name) {
        super(name);
        this.user = user;
    }
 
    public void run() {
        try {
            for (int i = 0; i < 3; i++) {
                user.add(getName());
                sleep(500);
            }
        } catch (InterruptedException e) {
            System.err.println(e.getMessage());
        }
    }
}
 
public class SyncThread {
 
    public static void main(String[] args) {
 
        User user = new User();
 
        // 3개의 스레드 객체 생성
        UserThread p1 = new UserThread(user, "A1");
        UserThread p2 = new UserThread(user, "B2");
        UserThread p3 = new UserThread(user, "C3");
 
        // 스레드 스케줄링 : 우선순위 부여
        p1.setPriority(p1.MAX_PRIORITY);
        p2.setPriority(p2.NORM_PRIORITY);
        p3.setPriority(p3.MIN_PRIORITY);
 
        System.out.println("-----------------------");
        System.out.println("sychronized 적용안한 경우");
        System.out.println("-----------------------");
 
        // 스레드 시작
        p1.start();
        p2.start();
        p3.start();
    }
}
```

```java
-----------------------
sychronized 적용안한 경우
-----------------------
B2 : 1번째 사용
A1 : 0번째 사용
C3 : 2번째 사용
B2 : 3번째 사용
C3 : 5번째 사용
A1 : 4번째 사용
B2 : 6번째 사용
C3 : 7번째 사용
A1 : 8번째 사용
```

- 동기화를 원하는곳에 synchronized키워드 적용

```java
class User {
  private int userNo = 0;

  public synchronized void add(String name) {
    System.out.println(name + " : " + userNo++);
  }
}
```

```java
-----------------------
sychronized 적용한 경우
-----------------------
A1 : 0번째 사용
C3 : 1번째 사용
B2 : 2번째 사용
A1 : 3번째 사용
C3 : 4번째 사용
B2 : 5번째 사용
A1 : 6번째 사용
C3 : 7번째 사용
B2 : 8번째 사용
```
