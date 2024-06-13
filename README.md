# likelion_hackathon_Cup_of_Coffee

# 멋쟁이사자처럼 해커톤

### 채팅 기능 구현

## ERD 다이어그램
![멋사11기 해커톤 erd](https://github.com/leegy21/likelion_hackathon/assets/102893824/73d41513-97d9-4117-90bb-993a2440a2ec)

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
실행 화면

![멋사11기 해커톤 채팅](https://github.com/leegy21/likelion_hackathon/assets/102893824/f6dae39a-82f4-4dfd-a366-50218412f262)

![멋사11기 해커톤 채팅 실행](https://github.com/leegy21/likelion_hackathon_Cup_of_Coffee/assets/102893824/85f9a911-a179-434a-a6e0-eec4e140bcb8)
![멋사 11기 해커톤 채팅 보내기](https://github.com/leegy21/likelion_hackathon_Cup_of_Coffee/assets/102893824/bb82f33c-8cca-416f-a7ae-b7dc0a686322)

