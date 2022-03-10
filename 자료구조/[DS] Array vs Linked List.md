# Array vs Linked List

![image](https://user-images.githubusercontent.com/72914519/157438107-5ee4863b-ded5-455e-bf9e-2730b3c2ccbe.png)

- 접근
    - Array(배열)
        - Random Access를 지원합니다. 요소들을 인덱스를 통해 직접 접근 할수 있다.
        - 특정 요소에 접근하는 시간복잡도는 O(1)
    - Linkedlist(링크드리스트)
        - Sequential Access를 지원한다. 어떤 요소들을 접근할 떄 순차적으로 검색하면서 찾는다.
        - 특정 요소에 접근하는 시간복잡도는 O(N)
        
- 저장방식
    - Array(배열)
        - 요소들은 인접한 메모리 위치에 저장 되거나 메모리에 연이어 저장된다.
    - Linkedlist(링크드리스트)
        - 새로운 요소들은 메모리 “어딘가”에 저장된다.
    
- 삽입과 삭제
    - Array(배열)
        - 인덱스로 접근 후 삽입 및 삭제 O(1) + 전체 배열 요소를 1씩 Shift O(N)이다.
        
        ![image](https://user-images.githubusercontent.com/72914519/157438139-ee8c1b92-a8c9-48a0-99b6-9e1f2d6030c3.png)
        
    
   ![image](https://user-images.githubusercontent.com/72914519/157438158-7a2b656e-8a77-4b36-97e9-ab123953e620.png)
    
    - Linkedlist(링크드리스트)
        - 삽입하려는 위치 접근 후 삽입 및 삭제 O(N), 맨 앞 삽입 삭제는 O(1)이다.

![image](https://user-images.githubusercontent.com/72914519/157438197-eeb8a6a5-ba68-4ef7-88b2-c5ebf95f6eb9.png)

![image](https://user-images.githubusercontent.com/72914519/157438219-e62e5df8-9eaa-4efa-8279-907d661f5bda.png)
- 메모리 할당
    - Array(배열)
        - 메모리는 배열이 선언되자마자 Compile time에 할당되어진다.
        - Static Memory Allocation
        - Stack section에 메모리할당이 이루어진다.
    - Linkedlist(링크드리스트)
        - 새로운 노드가 추가될때마다 runtime에 할당되어 진다.
        - Dynamic memory allocation
        - Heap section에 메모리 할당이 이루어 진다.
        
- Array vs Linkedlist 차이점 결론
    - 데이터 접근이 많은 작업 → Array
    - 데이터 수정이 많은 작업 → Linkedlist
