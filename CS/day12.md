## 네트워크 계층(Network Layer)

- 라우팅을 담당
    - 라우팅이란 출발지로부터 목적지까지 패킷이 거쳐가야 할 경로를 결정하는 것
- 포워딩(forwarding)
    - 라우터의 input으로부터 라우터의 적절한 output으로 패킷을 이동시키는 것
    - 간단하게, 패킷을 다음 라우터에게 전달
- Data plane, Control plane 두 가지 영역으로 생각할 수 있음
    - Data plane
        - 주로 인접 라우터 간 이루어짐
        - 포워딩
    - Control plane
        - 전체 네트워크 간 이루어짐
        - 라우팅
- 주요 장비: 라우터

## 전송 계층(Transport Layer)

- 다른 호스트들 사이에서 동작하는 어플리케이션 프로세스 사이 논리적 의사소통 제공
- TCP, UDP 두 가지 프로토콜이 사용됨
    - TCP
        - Transmission Control Protocol
        - 높은 신뢰성 보장
        - 순서에 따른 전달
        - 연결형 서비스(패킷 교환 방식)
        - 서버와 클라이언트 1대1 연결
        - 3-way handshaking 연결, 4-way handshaking 해제
        - 혼잡 제어, 흐름 제어
    - UDP
        - User Datagram Protocol
        - 낮은 신뢰성
        - 순서 없는 전달
        - 비연결형 서비스(데이터그램 방식)
        - CheckSum을 통한 최소한의 오류 검출
        - TCP보다 빠른 속도