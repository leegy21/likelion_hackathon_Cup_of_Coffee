# likelion_hackathon_Cup_of_Coffee

# 멋쟁이사자처럼 해커톤

### 채팅 기능 구현

## ERD 다이어그램
![Image](https://github.com/user-attachments/assets/e5ee496f-e817-4ba9-98f7-fd889e862509)

## API

+ postman, MySQL Workbench, Docker(mysql) 사용
+ websocket-stomp는 postman에서 지원하지 않아 **apic** (구글확장프로그램)이용

| GET                        | 설명                                |
|----------------------------|-----------------------------------|
| `/posts`                   | 모든 post(게시글)의 내용 불러옴              |
| `/posts/{id}`              | 해당 id(post_id)의 post(게시글)내용 불러옴   |
| `/posts/{id}/comments`     | 해당 id(post_id)의 comments(댓글)들 불러옴 |
| `/users`                   | 모든 user(사용자)목록 불러옴                |
| `/users/{id}`              | 해당 id(user_id)의 정보 불러옴            |
| `/chat/rooms`              | 모든 채팅방 정보 불러옴                     |
| `/chat/room/{roomId}` | 해당 roomId를 가지고 있는 채팅방 정보 불러옴      |
| `/chat/room/enter/{roomId}` | 해당 roomId를 가지고 있는 채팅방 입장          |

| POST                              | 설명                                       |
|-----------------------------------|------------------------------------------|
| `/posts/{username}/write`         | username이 post(게시글)추가                    |
| `/posts/{username}/{id}/comments` | 해당 username과 id(post_id)의 comments(댓글)추가 |
| `/users`                          | user(사용자)추가                              |
| `/chat/room?name={name}`          | name이름을 가지는 채팅방 생성(roomId 자동생성)          |

| PUT                      | 설명                                      |
|--------------------------|-----------------------------------------|
| `/posts/{id}/{username}` | 해당username이 id(post_id)의 post(게시글)내용 수정 |

| DELETE        | 설명                           |
|---------------|------------------------------|
| `/posts/{id}` | 해당 id(post_id)의 post(게시글) 삭제 |
| `/users/{id}` | 해당 id(user_id)의 user(사용자) 삭제 |

---

+ webSocket-Stomp은 테스트 시 http://localhost:8080/ws-stomp 로 연결된다

|subsciber|설명|
|---|---|
|`/sub/chat/room/{roomId}`|POST에서 생성한 roomId로 입장|

| publisher           | 설명                                            |
|---------------------|-----------------------------------------------|
| `/pub/chat/message` | JSON형태로  message를 보냄(ENTER:입장, TALK: 채팅 입력 시) |
```json
{
  "type": "ENTER",
  "roomId": "ENTER or TALK할 roomId",
  "sender": "유저이름",
  "message": "메시지"
}
```

![Image](https://github.com/leegy21/likelion_hackathon_Cup_of_Coffee/assets/102893824/85f9a911-a179-434a-a6e0-eec4e140bcb8)
![Image](https://github.com/leegy21/likelion_hackathon_Cup_of_Coffee/assets/102893824/bb82f33c-8cca-416f-a7ae-b7dc0a686322)

## 실행 화면

+ postman, MySQL Workbench, Docker(mysql) 사용
+ websocket-stomp는 postman에서 지원하지 않기 때문에 **apic** (구글확장프로그램)을 이용
+ webSocket-Stomp은 테스트 시 http://localhost:8080/ws-stomp 로 연결된다
+ 아래 사진은 왼쪽, 오른쪽 서버를 둘 다 켜서 각각 유저1, 유저2로 접속한 모습
+ 유저1이 채팅을 보내면 양쪽 서버에 뜬다

![Image](https://github.com/user-attachments/assets/41a5b7f3-139f-49c0-a04f-51bc1256df73)
