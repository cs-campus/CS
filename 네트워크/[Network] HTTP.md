- HTTP란
    - Hyper Text Transfer Protocol
    - 데이터를 주고 받을 수 있는 통신 규약
    - URI로 리소스만 식별하고 행위는 메서드로 구분
    - HTTP 메서드
        - Get: 서버에 데이터 요청
        - Post: 서버에 데이터 생성 요청
        - Put: 서버 데이터를 수정하거나 없으면 생성
        - Delete: 서버 데이터 제거 요청
        - Patch: 서버 데이터 일부분을 수정
        - 추가 메서드
        - Head: 바디 값 없이 헤더만 반환
        - Options: 리소스에 대한 통신 가능 옵션을 설명(CORS에서 사용)
        - Connect: 자원으로 식별되는 서버에 대한 터널 설정
        - Trace: 리소스에 대한 경로를 따라 메시지 루프백 테스트 수행
    - 헤더 안의 일반 헤더 항목들
        - Date: 생성 일시
        - Conxnection: 서버 간 연결 여부
        - Cache-control
        - Pragma - 데이터가 끊겨있는지
    - 헤더 안의 엔티티 헤더의 항목
        - Content-Type: Media type 정보
            - 컨텐츠 타입, 인코딩 방식 등을 지정
        - Content-Language: 언어
        - Content-Encoding: 압축 방식 gzip
        - Content-length: 해당 개체의 바이트 길이
        - Content-Location: 개체가 어디에 있는지
        - Location: 리소스가 리다이렉트일때 이동할 주소 또는 새로 생성된 리소스 주소(300번대 응답 or Created)
    - 헤더 안의 요청 헤더 항목
        - Host: 호스트명 및 포트 번호
        - User-Agent : 브라우저, OS 버전 정보
        - From: 클라이언트 사용자 메일 주소
        - Cookie: 클라이언트에게 제공된 쿠키 정보
        - Referer: 직전 머물렀던 웹 링크 주소
        - Authorization: 인증 토큰 헤더
        - Origin: Post 요청을 보낼때 어느 주소가 시작인지 알려줌, CORS 에러가 발생되는 곳
    - 헤더 안의 응답 헤더 항목
        - Server: 서버 정보
        - Set-Cookie: 서버에서 쿠키 설정
        - Expires: 리소스의 만료일자
        - Age: 캐시가 얼마나 있었는지 알려준다.
        - Access-Control-Allow-Origin: 요청을 보내는 프론트 주소와 백엔드 주소가 같아야 한다. 프로토콜, 도메인, 포트가 모두 같아야 한다.ㅍ
