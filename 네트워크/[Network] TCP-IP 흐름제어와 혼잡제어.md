# TCP/IP 흐름제어와 혼잡제어

- ****흐름 제어? 혼잡 제어?****
    - 흐름 제어
        - 송신측과 수신측의 데이터 처리 속도 차이를 해결하기 위한 기법
        - 송신측의 데이터의 전송량 제어
    - 혼잡 제어
        - 송신측의 데이터 전달과 네트워크 상의 데이터 처리 속도 차이를 해결하기 위한 기법
        - 송신측의 데이터 전송 속도 제어

- 흐름제어
    - Stop and wait 방식
        - 매번 전송한 패킷에 대한 확인 응답을 받아야만 다음 패킷을 전송 하는 방법
        
    ![image](https://user-images.githubusercontent.com/72914519/158803629-5f528115-f4cc-41f1-a2c7-53a7ab936b36.png)
        
    - Sliding window 슬라이딩 윈도우 기법
        - stop and wait방식의 문제점을 해결하기 위한 방법
        - 확인 응답이 없이 패킷을 전송한다.
        - 수신 측에서 설정한 윈도우 크기만큼 송신 측에서 확인 응답(ACK) 없이 패킷을 전송할 수 있게 하여 데이터 흐름을 동적으로 조절하는 제어 기법이다.
        - 이때 윈도우의 크기는 3 way handshaking 통해 결정이 된다.
        
   ![image](https://user-images.githubusercontent.com/72914519/158803646-b8b7d044-5ae4-4e3a-9d69-de3bf8475fb2.png)
        
- 혼잡 제어
    - **AIMD (Additive Increase Multicative Decrease)**
        - 합 증가/ 곱 감소 알고리즘
        - 처음에 패킷을 보내고 확인이 오면 윈도우 크기를 1씩 올려서 전송한다.
        - 패킷 전송이 실패를 하면 윈도우 크기를 절반으로 감소 시킨다.
            - 문제점
                - 초기 네트워크의 높은 대역폭을 사용하지 못함
                - 속도를 올리는데 시간이 걸린다.
                - 뒤늦은 감소로 근본적인 혼잡문제를 해결 못함
    
   ![image](https://user-images.githubusercontent.com/72914519/158803662-1e852480-54c2-4ad4-b782-aaa407062e05.png)
    
    - Slow start
        - 전송 속도를 빠르게 올리기 위해서 선형적인 AIMD와 달리 윈도우 크기를 두배로 올린다.
        - window size는 이전의 절반까지는 지수꼴로 증가, 이후부터는 완만하게 1씩 증가
        - 혼잡 현상이 발생하면 윈도우 크기를 1로 떨어트림
        
    - Fast Retransmit (빠른 재전송)
        - 빠른 재전송은 TCP 혼잡 제어에 추가된 정책
        - 중복 순번의 패킷을 감지하여 window size를 줄임
        - 3아웃제도
    - Fast Recovery (빠른 회복)
        - 혼잡한 상태가 되면, 윈도우 사이즈를 1로 줄이지 않고 반으로 줄이고 선형증가 시키는 방법
        - 혼잡상태로 반까지 줄고 난 이후, AIMD방식처럼 동작
        
      ![image](https://user-images.githubusercontent.com/72914519/158803684-44bff6f1-8f74-47d3-b9ec-b9ddcbe4ecfa.png)
