
- JVM 동작과정
    - JVM은 자바 가상 머신으로, 자바 바이트 코드를 해석하고 실행하는 역할을 합니다. 자바 코드는 JVM을 통해 실행되므로 Window, Linux와 같은 다른 OS에서도 동일하게 실행할 수 있다는 장점이 있습니다.

![image](https://user-images.githubusercontent.com/72914519/165523735-3fc9311a-a018-4c80-aa1c-9c34d53057bd.png)


1. 인간이 만든 .java파일을 바이트 코드로 변환하기 위해서 javac 컴파일러가 일을 합니다.
2. .class 파일을 class Loader로 보낸다.
3. Class Loader는 JVM Runtime Data Area에 알맞게 로딩을 하여 JVM메모리에 올라간다.

- 메모리 영역

- **Method 영역**
    - 클래스 정보, static 변수, 변수 정보, 메소드 정보 등을 저장합니다.
    - 패키지나 클래스 정보가 올라갑니다.
    - static 이 선언된 클래스 멤버도 올라갑니다.
    - JVM이 동작해서 클래스가 로딩될 때 생성됩니다.
    - JVM이 종료될때까지 유지됩니다.
    
- **Heap 영역**
    - 힙 영역은 인스턴스를 생성할 때 생성되는 메모리 형식입니다.
    - "new"를 사용하여 객체를 만들 때 저장됩니다.
    - 참조형(class, interface, enum, Array 등) 자료형도 같이 저장됩니다.
    - 힙의 참조 주소는 "스택"이 갖고 있고 해당 객체를 통해서만 힙 영역에 있는 인스턴스를 핸들링할 수 있습니다.
    - GC가 정리하기 전까지는 남아있습니다.

- **Stack 영역**
    - 지역변수, 파라미터, 리턴값, 연산에 사용되는 임시값등이 생성되는 영역
    - 메소드를 호출할 때마다 개별적으로 스택이 생성되며 종료 시 영역에서 해제된다.
    - 컴파일 타임 시 할당된다

- **PC Register 영역**
    - 스레드가 생성될때마다 생성되며 현재 스레드가 실행되는 부분의 주소와 명령을 저장하는 영역
    - 이를 이용해서 스레드를 돌아가면서 수행할 수 있게 한다.

- **Native Method 영역**
    - 자바 외 언어로 작성된 네이티브 코드(C,C++)를 위한 메모리 영역(JNI)
    

![image](https://user-images.githubusercontent.com/72914519/165523775-eda706df-90a3-434e-8dfb-71b70cdc0896.png)


- **Execution Engin**
- Execution Engine은 메모리(RuntimeDataArea)에 할당된 byteCode를 실행하는 역할을 담당한다.
- Execution Engine을 통해서 Machine이 읽을 수 있는 형태로 ByteCode(네이티브)를 변환해 주어야 한다.
- Interpreter
    - 한줄씩 컴파일을 한다.
- JIT Compiler
    - 중복되는 바이트 코드가 있으면 동적으로 변환시켜준다.
