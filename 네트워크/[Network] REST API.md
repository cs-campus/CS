- REST란
    - Representational State Transfer(대표 상태 전달)
    - 클라이언트와 서버 사이 통신 방식 중 하나. graphql
    - URI를 통해 자원을 명시하고, 메서드로 행위를 나타낸다.
    - 장점
        - 범용성
        - HTTP 프로토콜의 표준을 잘 지킨다.
    - 단점
        - Header에 들어갈 정보가 많아질 수 있다.
        - 구형 브라우저에 따라 Put, Delete가 지원이 안될 수 있다.
    - 필요한 이유
        - 애플리케이션 분리 및 통합
        - 다양한 사용 환경의 등장 - 모바일, 컴퓨터, IOS 등
    - 구성 요소
        - 자원: URI
        - 행위: 메서드
        - 표현: Json or XML 형태
    - 특징
        - 무상태
        - 캐시 처리 가능
        - 계층화
        - 코드 의존
        - 인터페이스 일관성
        - 범용성

- Rest API
    - REST를 기반으로 API 구현
    - 특징
        - 확장성
        - 재사용성
        - 유지보수 편의
        - 여러 언어로 제작 가능
    - 규칙
        - URI
            - 동사보다는 명사
            - 영어, 소문자. 복수형 사용
        - 메서드
            - URI에 메서드 들어가면 안된다.
            - URI 동사 표현은 안된다.
        - 설계 규칙
            - 슬래시로 계층 관계 구분
            - 마지막은 생략
            - 하이픈(-)으로 가독성 높인다.
            - 밑줄은 사용하지 않는다.
            - 소문자 추천
            - 파일 확장자는 포함하지 않는다.(헤더 사용)

- REST API 성숙도 모델

![image](https://user-images.githubusercontent.com/58693617/158403678-ae37c642-4ce1-49b6-b1dd-1881b2b777dc.png)

Lv0: 웹 메커니즘 사용 X

Lv1: 리소스 도입 URI

Lv2: 메서드 도입 - 많이 사용

Lv3: 다음 request에 필요한 endpoint(uri)까지 제공. (hateoas)
