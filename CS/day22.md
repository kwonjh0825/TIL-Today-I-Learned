## Domain

- 웹 브라우저를 통해 특정 사이트에 진입할 때 IP주소를 대신하여 사용하는 주소
- 한 눈에 파악하기 힘든 IP 주소를 보다 분명하게 나타낼 수 있음
- URL은 도메인을 포함한 경로로, 프로토콜과 도메인을 모두 포함하여 표시하는 차이

## DNS

- Domain Name Server
- 도메인 이름을 IP 주소로 변환하거나, IP 주소를 도메인 이름으로 변환하는 일을 수행할 수 있도록 개발된 데이터베이스 시스템
- 도메인 이름을 웹 브라우저에 입력할 때 최종 사용자를 어떤 서버에 연결할 것인지 정함
- 전화번호부와 유사한 역할
- 종류에는 Local DNS, Root DNS, TLD(Top Level Domain) DNS, Authoritative DNS 등이 있음
    - Local DNS
        - URL에 도메인 이름을 입력했을 때 가장 먼저 탐색하는 DNS 서버
        - 일반적으로 컴퓨터의 ISP(인터넷 서비스 제공자)가 local DNS 담당
    - Root DNS
        - ICANN이 직접 관리하는 서버
        - TLD DNS 서버 IP를 저장해 두고 안내하는 역할
    - TLD(Top Level Domain) DNS
        - 도메인 등록 기관이 관리하는 서버
        - Authoritative DNS 서버 주소를 저장해 두고 안내하는 역할
        - 대표적으로 국가 코드 최상위 도메인(.kr, .us 등), 일반 최상위 도메인(.com, .org 등)
    - Authoritative DNS
        - 실제 개인 도메인과 IP 주소의 관계가 기록, 저장, 변경되는 서버
        - 일반적으로 도메인, 호스팅 업체의 네임서버를 말하지만, 개인 DNS 서버 구축을 한 경우도 여기 해당됨
- 동작 과정
    - 예를 들어 URL에 www.google.com 을 입력했다고 하면
    - 클라이언트가 Local DNS 서버에 요청을 보냄
    - Local DNS 서버에 해당 도메인이 없다면 Root DNS 서버에 요청 전달
    - Root DNS 서버는 .com 도메인의 TLD DNS 서버에 요청을 보내라고 알려줌
    - TLD DNS 서버에 요청을 보냄
    - TLD DNS 서버는 구글 서버 제공 업체의 DNS 서버에 요청을 보내라고 알려줌
    - 구글 서버 제공 업체의 DNS 서버에 요청을 보냄
    - www.google.com 의 IP 주소를 응답
    - 사용자는 www.google.com 의 IP 주소를 알게 됨