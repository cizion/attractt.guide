# Attractt API

### 보드 정보

- **이메일 정보를 통해서 해당 계정의 모든 보드의 정보를 가져옵니다.**

  > **(GET)** /custom/track?secretToken=`{token}`=&email=`{email}`

  - **token** : 인증 토큰 번호
  - **email** : 어트랙트에 가입한 회원정보의 이메일
  
<br>

- **Request**

  ``````url
  https://www.attractt.com/custom/track?
  secretToken=sEcrEtTokEn&email=contact@attractt.com
  ``````

- **Response**

  ```js
  attracttCallback({
    resultData: [
      {
        member_seq: 163,
        track_seq: 970,
        status: 0,
        regdate: "2017-11-09 14:19",
        name: "스키장",
      },
      {
        member_seq: 163,
        track_seq: 999,
        status: 0,
        regdate: "2017-11-27 10:39",
        name: "페스티벌",
      },
      ...
    ],
    regdate: 1517314690570,
    code: 200,
    parameters: {
      secretToken: "sEcrEtTokEn",
      email: "contact@attractt.com",
    },
  })
  ```

<br>

### 콘텐츠 정보

- **이메일 정보를 통해서 특정 보드에 저장되어 있는 콘텐츠의 정보를 가져옵니다.**

  > **(GET)** /custom/track?secretToken=`{token}`&email=`{email}`&track_seq=`{seq}`

  - **token** : 인증 토큰 번호
  - **email** : 어트랙트에 가입한 회원정보의 이메일
  - **track_seq** : 검색하고자 하는 보드의 번호
  
<br>

- **Request**

  ``````url
  https://www.attractt.com/custom/track?
  secretToken=sEcrEtTokEn&email=contact@attractt.com&track_seq=970
  ``````

- **Response**

  ``````js
  attracttCallback({
    resultData: [
      {
        // type: image - 이미지
        standard_image: "https://scontent.cdninstagram.com/.../s640x640/....jpg",
        text: "아직도 못정햇어..어디가지 어디든 개장빵 출동준비완료?? . #보드복 #스노우보드#스키장 ...",
        profile_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        link: "https://www.instagram.com/p/BbQtW9UFEZx/",
        keyword: "스키장",
        search_type: "hashtag",
        type: "image",
        post_id: "1644013353746843249_2239931865",
        sns: "instagram",
        low_image: "https://scontent.cdninstagram.com/.../s320x320/....jpg",
        user_name: "1857mm",
        post_seq: 314611,
        thumbnail_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        likes: 35,
        hashtags: "saavi 스노우보드 trick 보드 156 팔로우 crabgrab rice28 오클리 union 휘팍 ...",
        user_id: "2239931865",
        created_time: 1510201685,
        comments: 6,
        hd_image: "https://scontent.cdninstagram.com/.../s1080x1080/....jpg",
        user_fullname: "YoHan Lee님이 회원님을 좋아합니다.",
      },
      {
        // type: carousel - 다중 콘텐츠
        standard_image: "https://scontent.cdninstagram.com/.../s640x640/....jpg",
        text: "곧 겨울시즌이 시작하게꾼... . . #보드 #곤지암 #트릭 #그라운드 #겨울 #스키장 ...",
        profile_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        link: "https://www.instagram.com/p/BbQoz-5lMaN/",
        keyword: "스키장",
        search_type: "hashtag",
        type: "carousel",
        post_id: "1643993358082033293_6265920586",
        sns: "instagram",
        low_image: "https://scontent.cdninstagram.com/.../s320x320/....jpg",
        user_name: "hssh0857",
        post_seq: 314613,
        thumbnail_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        likes: 7,
        carousel_media: "[Object, Object, ...]",	// String 형태. JSON.parse() 필요
        hashtags: "보드 곤지암 겨울 스키장 그라운드 형광 트릭 아디다스 눈",
        user_id: "6265920586",
        created_time: 1510199301,
        comments: 2,
        hd_image: "https://scontent.cdninstagram.com/.../s1080x1080/....jpg",
        user_fullname: "서비",
      },
      {
        // type: video - 동영상
        standard_image: "https://scontent.cdninstagram.com/.../s640x640/....jpg",
        text: "안녕하세요. December10 입니다. 페북 기능 중 "작년의 오늘" 소식들을 보니  작년 이 ...",
        location: "37.531666666667,127.06666666667",
        profile_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        link: "https://www.instagram.com/p/BbQkrxvAdhi/",
        keyword: "스키장",
        search_type: "hashtag",
        type: "video",
        post_id: "1643975202004129890_2318465040",
        sns: "instagram",
        low_image: "https://scontent.cdninstagram.com/.../s320x320/....jpg",
        user_name: "dog_made",
        post_seq: 314614,
        thumbnail_image: "https://scontent.cdninstagram.com/.../s150x150/....jpg",
        likes: 122,
        hashtags: "휘닉스파크 곤지암리조트 클럽츄러스 스노우보드 グラトリ 보드 スノボー 스노보드 오비오 ...",
        user_id: "2318465040",
        created_time: 1510197152,
        comments: 4,
        hd_image: "https://scontent.cdninstagram.com/.../s1080x1080/....jpg",
        video: "https://scontent.cdninstagram.com/....mp4",
        user_fullname: "김우용",
      },
      ...
    ],
    regdate: 1517315587254,
    code: 200,
    parameters: {
      secretToken: "sEcrEtTokEn",
      track_seq: "970",
      email: "contact@attractt.com",
    },
  })
  ``````
  - **type: carousel - 다중 콘텐츠**의 결과값 중 `carousel_media` 의 정보는 `String` 형태로 내려옵니다. `JSON.parse()` 를 이용하여 `Object` 형으로 변환 후 사용하시기 바랍니다.

