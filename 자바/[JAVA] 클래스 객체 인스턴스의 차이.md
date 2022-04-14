- 클래스란?
    - 객체를 만들어 내기 위한 설계도, 틀
    - 연관되어 있는 변수와 메서드의 집합

- 객체
    
    ![image](https://user-images.githubusercontent.com/72914519/163405443-33748f9b-d4fc-4952-8115-2fcca2468032.png)
    
    - 소프트웨어에서 구현할 대상
    - 클래스에서 선언된 모양 그대로 생성된 실체

- 인스턴스
    - 설계도를 바탕으로 소프트웨어 세계에 구현된 구체적인 실체
        - 실체화된 인스턴스는 메모리에 올라간다.

```java
/* 클래스 */
public class Animal {
  ...
}
/* 객체와 인스턴스 */
public class Main {
  public static void main(String[] args) {
    Animal cat, dog; // '객체'

    // 인스턴스화
    cat = new Animal(); // cat은 Animal 클래스의 '인스턴스'(객체를 메모리에 할당)
    dog = new Animal(); // dog은 Animal 클래스의 '인스턴스'(객체를 메모리에 할당)
  }
}
```
