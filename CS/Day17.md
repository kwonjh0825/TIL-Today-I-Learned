## 3 way handshake

- TCP/IP 프로토콜을 이용해 통신하는 응용 프로그램이 데이터를 전송하기 전 정확한 전송을 보장하기 위해 상대 컴퓨터와 사전에 세션을 수립하는 과정
- 양 쪽 모두 데이터를 전송할 준비가 되었음을 보장
- 상태
    - CLOSED: 닫힌 상태로, 데이터를 주고 받기 전 연결이 성립되지 않은 상태
    - SYN_SENT: 클라이언트에서 SYN 신호를 보낸 상태, 서버 측의 응답을 대기하고 있는 상태
    - LISTEN: CLOSED 상태의 서버가 데이터를 받을 준비가 되어 대기중인 상태
    - SYN_RECIEVED: 서버가 클라이언트 측에서 보낸 SYN을 잘 수신한 상태
    - ESTABLISHED: 연결이 성공적으로 완료된 상태
- 연결 과정
    - 클라이언트가 서버에 접속을 요청하는 SYN 패킷 전송
    - 서버는 SYN 요청을 받은 뒤 요청을 수락한다는 ACK와 SYN Flag가 설정된 패킷 발송
    - 클라이언트는 서버에게 ACK를 전송, 이후 연결이 성립되고 데이터가 오고 감

## 4 way handshake

- 서버와 클라이언트 간 데이터 교환이 끝나고 연결을 해제하는 과정
- 상태
    - FIN_WAIT: 클라이언트가 서버에게 연결을 해제하겠다고 신호를 전송한 상태
    - CLOSE_WAIT: 서버가 클라이언트에게 연결 해제 신호를 수신한 상태, 전송이 완료될 때까지 대기 상태
    - LAST_ACK: 서버가 클라이언트에게 전송이 완전히 끝났다는 신호를 전송한 상태
    - TIME_WAIT: 클라이언트가 서버에게 전송이 완전히 끝났다는 신호를 수신한 상태, 연결 해제를 준비하는 상태
    - CLOSED: 연결이 해제된 상태로, 클라이언트와 서버의 기본 상태
- 연결 해제 과정
    - 클라이언트에서 서버와 연결 종료를 위해 FIN 패킷을 보냄
    - 서버는 FIN 패킷을 받고 확인했다는 ACK를 클라이언트에 전송, 남은 데이터가 있다면 계속 전송
    - 서버가 데이터 전송을 완료했다면 연결 해제를 합의한다는 의미로 FIN 패킷을 클라이언트에게 전송
    - 클라이언트는 응답 ACK를 서버에 전송
    - 이후 소켓을 닫아 연결 해제