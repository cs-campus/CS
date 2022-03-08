# 정규화

- 정규화란?
    - 여러 규칙을 사용해 데이터베이스를 완벽하게(이상현상 없게) 설계하는 방법이고 이를 통해 데이터베이스에 저장된 데이터의 무결성을 향상시키고 저장공간을 절약 합니다.
    - 정규화 방법은  문제가 있는 테이블은 문제가 없는 작은 테이블로 쪼개는 방법입니다.
    - 나누는 정도에 따라 규칙(제약조건)이 있고 그 정도를 정규형(Normal Form)이라고 부른다.
    - 정규형은 1NF, 2NF, 3NF, BCNF, 4NF, 5NF, 6NF가 있는데 차수가 높아질수록 규칙(제약조건)이 까다로워진다. (정보처리기사 대비용으로 **도부이결다조** (두부이겨다줘)
    - 일반적으로는 1~3NF(또는 ~BCNF)까지만 사용하고 나머지 정규형은 학문적 용도(전공, 수업, 논문 등)로 사용된다.

- 1차 정규화
    - 테이블(릴레이션)에 각 도메인은 원자성(Atomicity)을 가진다.

![image](https://user-images.githubusercontent.com/72914519/157224134-5aadc955-89b6-4658-ae58-a44485dea4d1.png)

- 2차 정규화
    - 우선 2NF는 1NF를 먼저 충족이 되어야 진행을 할수 있다.
    - 그다음 속성 값의 결정이 기본키(또는 복합키)의 전체를 참조해야한다.

![image](https://user-images.githubusercontent.com/72914519/157224181-0d1683bc-7871-4c6a-87eb-13ef95fd7dbb.png)

![image](https://user-images.githubusercontent.com/72914519/157224248-6b555ac9-eef1-431b-b4db-c9b245a561ab.png)

![image](https://user-images.githubusercontent.com/72914519/157224273-e7fa0356-5917-4a57-839f-8343fea66a13.png)

![image](https://user-images.githubusercontent.com/72914519/157224299-9ee10f6e-06b5-47d8-a7aa-697efc39cb9f.png)

![image](https://user-images.githubusercontent.com/72914519/157224322-b0b2da4a-3013-430e-a4e2-51dcba92cbd9.png)

- 3차 정규화
    - 3NF도 2NF를 충족시킨 상태에서 진행할 수 있다.
    - 3NF는 모든 속성이 기본키(또는 복합키)에 **이행적 함수 종속**이 되지 않아야 한다.
        - 이행적 함수 종속 : X→Y이고 Y→Z면 X→Z가 되는 것을 말한다.

- 501학생이 수강하는 강좌가 스포츠 경영학으로 바꾼다면 15000짜리 수업을 20000에 듣게 된다.
- 물론 다시 수강료를 변경하면 해결이 되지만 번거롭다.
- 이를 해결하기 위해서 테이블을 분해를 한다.
- 학생 번호를 통해 강좌 이름을 참조하고, 강좌 이름으로 수강료를 참조하도록 테이블을 분해한다.

![image](https://user-images.githubusercontent.com/72914519/157224350-f8c327e4-eacc-484b-8d8f-b825f57ccc20.png)

![image](https://user-images.githubusercontent.com/72914519/157224372-e02c8a0e-4d4c-4071-ae09-b26d693162ff.png)
