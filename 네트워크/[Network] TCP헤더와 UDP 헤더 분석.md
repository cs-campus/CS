# TCP와 UDP의 헤더분석

![image](https://user-images.githubusercontent.com/72914519/158803136-25cd3b49-8365-4f56-8b46-ed993cf64267.png)

- TCP 헤더
    - 크기 :20 to 60 byte
    
 ![image](https://user-images.githubusercontent.com/72914519/158803170-202f4f5a-ef98-4712-96e6-0d0e9859a8ef.png)
    
- **Source port, Destination port**
    - 출발지와 목적지의 주소가 들어있다.
    

![image](https://user-images.githubusercontent.com/72914519/158803184-e752c803-2269-4cfd-9fc1-20ac67c927c0.png)

- **Sequence Number**
    - 쪼개진 세그먼트의 순서를 보장해주기 위해서 번호표 정보이다.
    
 ![image](https://user-images.githubusercontent.com/72914519/158803207-c9ca922d-ac26-4b43-a73d-d9ae782e35f5.png)
    
- **Acknowledgment Number**
    - 승인 번호는 데이터를 받은 수신자가 예상하는 다음 시퀀스 번호를 의미하며, 32 bits를 할당받는다.
    - 다음에 보내줘야하는 데이터의 시작점이라고 할수있다.
    
 ![image](https://user-images.githubusercontent.com/72914519/158803241-9ab9b61e-cd3e-424a-918c-0875aef870e4.png)
    
- **Data Offset**
    - 데이터가 시작되는 위치가 어디부터인지 표시한다.
    

![image](https://user-images.githubusercontent.com/72914519/158803293-92064ede-57f0-4028-8bb1-9b4cf3844961.png)

- **Reserved (3 bits)**
    - 미래를 위한 예약 필드이다.

![image](https://user-images.githubusercontent.com/72914519/158803323-045b4679-78ee-4861-b607-b7ed8d76cd10.png)

- **Flags (NS ~ FIN)**
    - 이 플래그들은 현재 세그먼트의 속성을 나타낸다.
    
  ![image](https://user-images.githubusercontent.com/72914519/158803345-6bf9ed86-e06f-4f42-b776-eece0fbadbe2.png)
    
- UDP 헤더
    - UDP는 신뢰성을 제공하지 않는다.
    - 상위 계층에서 받은 데이터 그램을 그냥 목적지에 보내기만 하고 제대로 도달이 했는지에 대한 신뢰는 보장하지 않는다.
    - 크기는 8바이트
    - 서비스를 지연없이 최선의 서비스로 제공한다.
    - 패킷 손실이 유발될 가능성도 있으나 서비스 지연 없이 최선의 서비스가 우선이다.
    
 ![image](https://user-images.githubusercontent.com/72914519/158803374-a7773ba5-4747-4c06-bdd5-7cb2fa0a848b.png)
    
- Source Port / Destination Port
- Total Length
    - 헤더와 데이터를 합한 사용자 데이터그램의 전체 길이를 정의한다.
- Checksum
    - 헤더와 데이터의 에러 확인 용도
    - UDP는 에러 복구를 위한 필드가 불필요하기 때문에 TCP 헤더에 비해 간단하다.
