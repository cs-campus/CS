# Stack and Queue


- 스택(Stack)

![image](https://user-images.githubusercontent.com/72914519/158801820-8d50e6b1-d09b-4432-af88-829b55107406.png)

- 맨 밑에서 하나 하나씩 쌓아 올리는 자료구조 입니다.(후입선출 LIFO)
- 스택의 특징
    - 데이터의 출구가 하나 밖에 없어서 삽입과 삭제는 한곳에서 처리가 된다.
    - 데이터를 삽입하는 것을 push라고 합니다.
    - 데이터를 삭제하는 것을 pop이라고 합니다
    - 데이터를 삽입 삭제가 일어나는 위치를 top이라고 합니다.
    - 어플의 뒤로가기를 생각하면 이해하기가 쉽다.

![https://blog.kakaocdn.net/dn/dhaMut/btqv5W62h3N/sw7zw0JU8Bh1pr3KmcssOK/img.gif](https://blog.kakaocdn.net/dn/dhaMut/btqv5W62h3N/sw7zw0JU8Bh1pr3KmcssOK/img.gif)

![image](https://user-images.githubusercontent.com/72914519/158801856-e3ce2e9b-7988-4d4b-b3c3-54f3c569437c.png)

- 큐(Queue)
- 먼저 들어온놈이 먼저 나간다. (선입선출 FIFO)
- 큐의 특징
    - 한쪽에서는 데이터가 추가 다른 한쪽에서는 데이터가 삭제가 되는 구조이다.
    - 삽입(Enqueue)이 일어나는 쪽을 rear , 삭제(Dequeue)가 일어나는 곳을 front라고 한다.
    - 큐는 기다리는 대기행렬 업무처리에 많이 쓰인다.(운영체제의 작업 스케줄링)
- 선형큐**(Linear Queue)**
    - 1차원 배열을 이용하여 큐를 구현한다.

![image](https://user-images.githubusercontent.com/72914519/158801892-aa5e7074-a89d-4d48-8786-68280fc06ed3.png)

- 선형큐의 문제점
    - 앞에 데이터를 저장이 가능하지만 포화 상태인줄 알고 데이터가 못들어간다.

![image](https://user-images.githubusercontent.com/72914519/158801930-3dfd37da-d3ae-4a66-a8f3-5d53434cfce3.png)

- 원형큐**(Circular Queue)**
    - 선형큐의 문제점을 보안하기 위해서 나온 자료구조
    - 물리적으로 원은 아니지만 논리적으로 원처럼 보인다.
    - front와 rare를 데이터 구조 안에서 계속 순환을 하게 한다.
    
  ![image](https://user-images.githubusercontent.com/72914519/158801958-43a6304b-988f-4250-9ad8-cad5abf82292.png)
    
- Enqueue할떄 (rear+1)%arraysize == front만족하면 포화 상태이다. (if. enqueue 4  (3+1)%4==front이므로 포화 상태여서 데이터가 못들어간다.)
- 포화 상태를 알기 위해서 하나의 인덱스는 사용하지 않는다.

![image](https://user-images.githubusercontent.com/72914519/158801988-5ee05236-7e59-4cc7-8a93-f7af17668d2e.png)

- front==rear라면 비어있는 상태이다.
- 원형 모양을 계속 순환 하기위해서 모듈러 연산을 해준다.
