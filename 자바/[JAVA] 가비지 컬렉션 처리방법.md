- GC란?
    - Java Runtime시 Heap 영역에 저장되는 객체들은 따로 정리하지 않으면 계속해서 ~~매섭게쏘겠어~~ 쌓이게되어 OutOfMemmory Exception이 발생할 수 있습니다.
    - 이를 방지하기 위하여 JVM에서는 주기적으로 사용하지 않는 객체를 수집하여 정리하는 GC를 진행합니다.

![image](https://user-images.githubusercontent.com/72914519/162615337-93e32156-9354-4308-9901-b0eca7ae6523.png)

- 어떻게 구분하여 처리 할것인가?
- GC 작업을 진행하는 Garbage Collector(가비지 콜렉터)는 GC를 위해 다음 역할을 합니다.
    - 1. 메모리 할당
    - 2. 사용중인 메모리를 인식
    - 3. 사용하지 않는 메모리를 인식
- 메모리의 구조

![image](https://user-images.githubusercontent.com/72914519/162615350-2902be42-3070-412d-8ecd-80c51f1c15be.png)

- GC의 종류

| MinorGC | young Generation 에서 발생하는 GC |
| --- | --- |
| MajorGC | Old Generation (Tenured Space) 에서 발생하는 GC |
| FullGC | Heap 전체를 clear 하는 작업 (Young/Old 공간 모두) |
- GC방식
    - Serial GC
        - Mark-Compact collection method 란, 새로운 메모리 할당을 빠르게 하기 위해서 기존의 메모리에 있던 오브젝트들을 힙의 시작위치로 옮겨 놓는 방법이다.
        - Serial GC는 적은 메모리와 CPU 코어 개수가 적을 때 적합한 방식이다.
    - Parallel GC
        - 멀티 코어를 사용하여 병렬적으로 처리
    - Parallel Old GC(Parallel Compacting GC)
        - Parallel GC와 비교하여 Old 영역의 GC 알고리즘만 다르다.
    - Concurrent Mark & Sweep GC(이하 CMS)
    - G1(Garbage First) GC
        
 ![image](https://user-images.githubusercontent.com/72914519/162615361-52a37bc0-8253-4628-ac3f-be90859d1c6a.png)
        
- GC 프로세스
    - 1. 새로운 오브젝트는 Eden 영역에 할당된다. 두개의 Survivor Space 는 비워진 상태로 시작한다.
    - 2. Eden 영역이 가득차면, MinorGC 가 발생한다.
    - 3.MinorGC 가 발생하면, Reachable 오브젝트들은 S0 으로 옮겨진다. Unreachable 오브젝트들은 Eden 영역이 클리어 될때 함께 메모리에서 사라진다.
    - 4. 다음 MinorGC 가 발생할때, Eden 영역에는 3번과 같은 과정이 발생한다. Unreachable 오브젝트들은 지워지고, Reachable 오브젝트들은 Survivor Space 로 이동한다. 기존에 S0 에 있었던 Reachable 오브젝트들은 S1 으로 옮겨지는데, 이때, age 값이 증가되어 옮겨진다. 살아남은 모든 오브젝트들이 S1 으로 모두 옮겨지면, S0 와 Eden 은 클리어 된다. Survivor Space 에서 Survivor Space 로의 이동은 이동할때마다 age 값이 증가한다.
    - 5. 다음 MinorGC 가 발생하면, 4번 과정이 반복되는데, S1 이 가득차 있었으므로 S1 에서 살아남은 오브젝트들은 S0 로 옮겨지면서 Eden 과 S1 은 클리어 된다. 이때에도, age 값이 증가되어 옮겨진다. Survivor Space 에서 Survivor Space 로의 이동은 이동할때마다 age 값이 증가한다.
    - 6. Young Generation 에서 계속해서 살아남으며 age 값이 증가하는 오브젝트들은 age 값이 특정값 이상이 되면 Old Generation 으로 옮겨지는데 이 단계를 Promotion 이라고 한다.
    - 7. MinorGC 가 계속해서 반복되면, Promotion 작업도 꾸준히 발생하게 된다.
    - 8. Promotion 작업이 계속해서 반복되면서 Old Generation 이 가득차게 되면 MajorGC 가 발생하게 된다.
    
  ![image](https://user-images.githubusercontent.com/72914519/162615363-a653ba90-329d-467d-b573-09985caa39c7.png)
    

함께보면 좋은 자료: 

[https://www.youtube.com/watch?v=r_JAjpy42ug](https://www.youtube.com/watch?v=r_JAjpy42ug)
