# RESTful API의 의미와 설계 규칙

<div align=center>
    <img src="../assets/RESTfulAPI.webp" width="800"/>
</div>

## RESTful API 란?

API란 다른 소프트웨어 시스템과 통신하기 위해 따라야 하는 규칙을 의미합니다. 이 중 REST(Representational State Transfer) 원칙을 따르는 API를 RESTful API라고 합니다.

<strong> REST는 HTTP를 기반으로 하며, RESTfulAPI 역시 HTTP를 통해 자원은 생성, 조회, 수정, 삭제(CRUD)하는 방식으로 동작합니다! </strong>

RESTful API는 일반적으로 HTTP 메서드(GET, POST, PULL, DELETE)와 URI를 사용해서 자원을 다루며,
자원의 표현은 주로 JSON 또는 XML 형식으로 제공됩니다. (그림 참조)
자원(URI), 행위(HTTTP 메서드), 표현(JSON, XML..)이 REST를 구성하는 3가지 요소입니다.

## REST의 특징

- 클라이언트-서버 구조: 클라이언트가 서버에 요청을 보내고, 서버가 요청에 대한 결과를 만들어서 응답해주는 구조로 서버와 클라이언트의 관심사(ui와 비지니스 로직 등)를 분리해줍니다.
- 상태 없음 : 클라이언트의 정보를 서버에 저장하지 않습니다. 서버가 클라이언트의 상태를 보존하지 않기 때문에 서버의 확장성이 높지만 , 클라이언트가 지속적으로 추가 데이터를 전송해주어야 합니다.
- 캐시 가능 데이터: 서버 응답 시간을 개선하기 위해 클라이언트는 캐시를 통해 데이터를 효율적으로 처리할 수 있습니다.
- 계층화된 시스템: 클라이언트는 서버에 직접 연결되어 있는지, 중간 계층을 통해 연결되었는지 알 수 없도록 설계되어야 합니다. (ex.Proxy 같은 중계 서버)
- 온디맨드 코드: 서버는 클라이언트에게 실행 가능한 코드를 전송하여 클라이언트의 기능을 일시적으로 확장할 수 있습니다. (ex.PUG 같은 템플릿 엔진을 사용해 HTML로 렌더링된 화면을 전송)
- 일관된 인터페이스
  - 모든 리소스는 고유한 URI를 통해 식별되어야 합니다.
  - 클라이언트는 원하는 경우 리소스를 수정하거나 삭제하기에 충분한 정보를 가지고 있어야 합니다. (리소스에 대한 정보)
  - 클라이언트는 표현을 추가로 처리하는 방법에 대한 정보를 가지고 있어야 합니다. (리소스를 조작하는 방법에 대한 정보)
  - 클라이언트가 리소스에 접근한 후 하이퍼링크를 사용할 수 있어야 합니다.

## 설계 규칙 (예시는 하단의 링크 참조)

- 명사를 사용하여 리소스 표시. 동사 사용 X
- 슬래시(/)를 사용하여 계층적 관계를 표시
- URI에 후행 슬래시(/)를 사용 X
- 하이픈(-)을 사용하여 URI의 가독성 향상
- 밑줄( \_ ) 사용 안함
- URI에 소문자 사용
- 파일 확장자 사용 안 함
- URI에 CRUD 함수 이름을 사용 X
- 쿼리 파라미터를 사용해서 정렬 or 필터링

---

> 참고

- https://aws.amazon.com/ko/what-is/restful-api/
- https://www.redhat.com/ko/topics/api/what-is-a-rest-api
- https://restfulapi.net/resource-naming/