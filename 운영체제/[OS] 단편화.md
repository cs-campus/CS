- 주기억장치 할당 기법
    - 단일 분할 할당 기법
    - 다중 분할 할당 기법
    
    ---
    
- 다중 분할 할당 기법
    - 주기억장치에 여러 개의 프로그램 동시 적재 기법
    - 다중 프로그래밍을 위한 기법
    - 고정 분할 할당, 가변 분할 할당
    
    ---
    
- MTF(Multiple contiguous Fixed parTition allocation, 고정 분할 할당) 기법
    - 정적 할당 기법
    - 분할된 메모리(크기 일정)에 배치
    - 한 영역에 한 프로그램 적재 가능
    - 단편화 발생
    - 현재는 안 쓰임

<p align="center"><img src="https://user-images.githubusercontent.com/54395509/156305941-cbdd55ab-6dc5-4616-aba9-2904586af42c.png" width="400" height="300"/></p>

---

- 단편화
    - 할당과 반납의 과정에서 사용되지 않고 낭비되는 빈 공간
    - 내부 단편화: 공간이 남는 것
    - 외부 단편화: 공간이 작아서 할당을 못하는 것

- 분할된 메모리 영역 크기 4k, 프로그램 크기가 5K?
    - 외부 단편화

- 분할된 메모리 영역 크기 4k, 프로그램 크기 2K?
    - 내부 단편화

---

- MVT(Multiprogramming with a Variable number of Tasks, 가변 분할 할당) 기법
    - 동적 할당 기법
    - 프로그램을 주기억장치에 적재하면서 필요한 만큼 크기로 영역 분할
    - 프로그램 크기 제약 적다.
    - But 영역 사이 단편화 발생 가능

<p align="center"><img src="https://user-images.githubusercontent.com/54395509/156307849-9587e88f-fc7f-47c7-8c6b-b3a1fc9e3981.png" width="400" height="300"/></p>

---

- 단편화 해결
    - 단편화된 작은 공간을 모아서 하나의 큰 공간으로 만들기
    - 통합 기법
    - 압축 기법

- 통합 기법
    - 인접한 단편화 영역을 하나의 영역으로 통합하는 작업
    
- 압축 기법
    - 집약, 쓰레기 수집(Garbage Collection)
    - 단편화 영역을 한 쪽으로 옮겨 커다란 가용 공간을 만드는 작업
    - 통합 기법과 차이? 인접하지 않은 영역 통합
    - 압축이 실행되는 동안 시스템은 모든 일을 일시 중단
    - 일시 중단하는 이유? 실행 중이던 프로그램의 주소도 바뀜
 
![image](https://user-images.githubusercontent.com/54395509/156307453-d7b6feff-3022-4152-8509-98b6f0842834.png)
