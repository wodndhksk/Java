
# Read Me 

#### 1. 프로젝트 소개
```
단톡방과 같이 1:N 채팅을 자바 GUI로 구현.
```

#### 2. 사용한 api, ide 등의 버전
```
-JDK 1.8
-IDE : 이클립스
-Database : mysql 15.1, MariaDB 10.5.8
```

#### 3. 잘한 점
```
-Server를 각 Client들의 송수신을 위한 징검다리로 사용하였다. 각 Client들의 textfield의 getText값을 서버로 보내고 서버는 그값을 나머지 클라이언트에게 보낸다.
  즉 값을 받을때는 해당 클라이언트가 보낸 값이 서버로 간 후 나머지 클라이언트들이 서버에서 그 해당 값을 받는다.

-Socket을 ArrayList인 sockets에 담아서 ( sockets.add(socket); )을 while문 안에 넣어 무한정 socket을 받아들여 arrayList에 추가하여 1:N 채팅을 할 수 있도록 구현하였다. 
  그리고 socket이 닫히면 해당 arraylist의 sockets를 remove 하는 코드도 추가시켜 데이터가 낭비되는 부분을 해결하였다.

-Client 클래스 에서는 서버로부터 오는 내용을 받는 스레드와 보내는 스레드 클래스들이 있었지만 채팅서버 특성상 내용을 서버로 보내는 것은 채팅을 입력한후 버튼을 눌렀을때만
  발생하므로 내용을 보내는 스레드코드 부분은 스레드 대신 actionListener에서 처리한다.
```
#### 4. 힘들었던 점
```
-Socket통신에서 bw = new PrintWriter(new OutputStreamWriter(socket.getOutputStream()), true); 을 통하여 보내는 방법을 사용하였는데
  이전에 new PrintWriter()대신 new BufferedWriter()을 사용하였는데 이부분에서 코드가 통신하지 않는 오류가 발생하였다. 이후 PrintWiter를 사용하였더니
  소켓통신이 이상없이 잘 해결되었다.
```
#### 5. 부족한 점 (개선해야 할 점)
```
-현재 구현하고자 한 로그인과 회원가입 부분이 미완성이므로 좀더 완성시켜 1:N채팅을 사용할때 아이디가 필요한 방식으로 구현을 할 예정
  (만약 아이디가 없다면 회원가입을 통해 가입을 할 수 있도록 만들예정)
```
#### 6. 구현 동영상 링크
```
아직없음
```
