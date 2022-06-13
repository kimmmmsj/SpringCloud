# USERS
- user_id       - pk
- firebase_id(?) - 익명 인증 토큰
- device_token  - 푸시 알림 위한 디바이스 토큰
- user_name     - 랜덤 아이디 제공될라나
- folder_select_yn - 찜할때마다 폴더 설정여부


# ALERT
- alert_id
- alert_title
- alert_content
- alert_date_time


# FOLDER
- folder_id
- ##### user_id
- folder_name(unique)
- folder_rate(폴더 순위)


# ITEM
- item_id
- ##### user_id
- ##### folder_id
- url(og:url)
- title(og:title)
- description(og:description)
- image(og:image)
- site_name(og:site_name)
- price(product:price:amount) : 현재가격
- ??(product:price:currency) : ISO 규격 통화(예시 : KRW)
- sale_price(product:sale_price:amount) : 세일 가격
- ??(product:sale_price:currency) : 세일 가격 통화
- item_date(년 월정도)


- 유저가 들어왔을때, device_token에 따라 필요데이터들(카테고리들, 아이템들) 가져오기
(없으면 새로 token 만들고 데이터 가져올 필요는 x)
- 새로운 카테고리 만들기(유저에 따라서)
- 카테고리 삭제. (아이템들의 category_id도 없애기 - 그러면 프론트에서 자동적으로 메인 카테고리)
- 아이템 리스트들과 넣고싶은 카테고리 id, user_id 받아서 category_id 넣기(업데이트)
- og 데이터 필요한거 받아서 아이템 추가
- 아이템 삭제
- 유저에 따른 특정 카테고리의 아이템 조회()




## 메인기능
- 처음 실행 시, token값에 따라 모든 데이터(카테고리, 그에 상응하는 아이템) 가져오기
(cf. 해당 token없으면 아이디 만들고, 기본카테고리 생성만)
즉, 카테고리와 아이템들 다 가져오기(+ 아이디 없으면 만들기까지) __개별__

#### 카테고리 기능
- 카테고리 만들기 __개별__

- 카테고리 삭제(그에 따른 아이템들은 기본 카테고리로 이동) __개별__

- 카테고리 이름 변경 __개별__

- 카테고리 위치 변경 __개별__

#### item 기능
- 아이템 만들기(카테고리도 같이 받아서 한번에) __MSA(카테고리쪽)__

- 아이템 삭제 __개별__

- 아이템의 카테고리 이동(변경) __개별__


#### User 기능
- User 삭제 __MSA__

- User 생성(메인기능) __MSA(카테고리쪽)__

- User 정보 변경 __개별__

## Alert 기능
- alert창 누르면 title과 content 정보들 가져오기(__GET__) __개별__
  - 보낼 것: 없음
  - 받을 것: List<alerts>로 alert안에는 title/content 들어있음

- alert 추가(title, content)(__POST__) __개별__
  - 보낼 것: 없음
  - 받을 것: 성공여부

- alert 삭제(__POST__) __개별__
  - 보낼 것: alert_id
  - 받을 것: 성공여부

- alter 업데이트(__PUT__) __개별__
  - 보낼 것 : alert_id, title, content
  - 받을 것 : 성공 여부

