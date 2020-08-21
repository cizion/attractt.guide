# Attractt.v2 API 

## 1. 개요

- 보드에 설정된 데이터들만 필요한 경우 사용합니다.
- `JSON` 형태의 데이터로 제공합니다.



## 2. 호출

### URL

```
https://www.attractt.com/api/v2/posts
```

### Parameter

| Name  | Type    | Description                                               | Required |
| ----- | ------- | --------------------------------------------------------- | -------- |
| code  | String  | 보드 고유 코드값                                          | O        |
| limit | Integer | 가져올 포스트 제한값 (Default: 500, 500개 이하만 가능)      | X        |



### 호출 예시

```
GET https://www.attractt.com/api/v2/posts?code=b8zPwbRbtrpXNi1
```



## 3. 결과값

```json
{
   // 응답 코드입니다.
   "code":200,
   "result":{
      // 어트랙트 내에서 사용하는 시퀀스 입니다.
      "trackSeq":2521,
        
      // 응답값의 개수 입니다.
      "count":52,
        
      "data":[
         {
            // 어트랙트 내에서 사용하는 포스트 시퀀스입니다. 
            "postSeq":1780925,
           
            // SNS 타입입니다 현재는 youtube와 instagram만 존재합니다.
            "sns":"youtube",
           
            // 어트랙트 내에서 사용하는 멤버 시퀀스 입니다.
            "memberSeq":1282,
           
            // 어트랙트 내에서 사용하는 멤버 시퀀스 입니다.
            "trackSeq":2521,
           
            // 어트랙트 검색시 사용한 키워드
            "keyword":"cutefox",
           
            // 인스타그램 혹은 유튜브에서 사용하는 post id
            "postId":"_AtP7au_Q9w",
           
            // 유저명 
            "userName":"foxalbiazul",
           
            // 인스타그램 혹은 유튜브에서 사용하는 유저
            "userId":"UCmQjHNN11KDnK_KlzbWxiiQ",
           
            // 프로필 이미지*
            "profileImage":"",
           
            // 인스타그램 데이터 갱신 API 상황에 따라, thumnail과 standard의 주소가 같을 수 있습니다.
            // 그래도 구분하여 사용드리는 걸 권장드립니다. (이미지 해상도 차이)
            "thumbnailImage":"https://i.ytimg.com/vi/_AtP7au_Q9w/hqdefault.jpg",
            "standardImage":"https://i.ytimg.com/vi/_AtP7au_Q9w/hqdefault.jpg",
           
            // 인스타그램 게시글 내용입니다. youtube에서는 description의 내용 일부를 가져옵니다.
            "text":"Fox go FLOOF\nYep, that winter coat time of the year again!! and the fox go FLOOF, all fluffed up and poofy! This is his 6th edition winter coat (being 5 1/2 years old)! ...",
           
            // 어트랙트에서 어떤 타입의 검색어를 사용했는지 구분하기 위함입니다.
            "searchType":"hashtag",
           
            // 인스타그램의 해시태그 모음이며, 유튜브의 경우 키워드와 같습니다.
            "hashtags":"cutefox",
           
            // type의 경우 youtube는 youtube 하나이며,
            // instagram의 경우 image, video, carousel 값이 존재합니다.
            "type":"youtube",
           
            // 인스타그램 포스팅 혹은 유튜브의 링크입니다.
            "link":"https://www.youtube.com/watch?v=_AtP7au_Q9w",
           
            // 컨텐츠 생성일 입니다. 
            // unixtime이며 초 기준이므로 js 등에서 사용하실 때 1000을 곱해서 사용하시면 됩니다.
            "createdTime":1384034580,
           
            // 어트랙트에 등록된 시간입니다.
            "regdate":"2020-03-12T17:05:03",
           
            // 포스트 상태 값으로 API에서 받으시는 건 전부 DISPLAY라고 생각하시면 됩니다.
            "status":"DISPLAY",
           
            // 어트랙트 내부에서만 사용하는 값입니다.
            "pluginLikes":0,
           
            // 인스타 게시글 좋아요 수 (배치를 통해 정보 업데이트)
            "likes":0,
           
            // 인스타 코멘트 수 (배치를 통해 정보 업데이트)
            "comments":0,
           
            // 어트랙트에서 해당 포스팅 정보가 업데이트 되어진 날짜입니다.
            "updateDate":"2020-03-12T17:05:03"
         }...
      ]
   }
}
```



## 4. 항목별 설명

| Key           | Type      | Description                                                  |
| ------------- | --------- | ------------------------------------------------------------ |
| postSeq       | Integer   | 어트랙트 내에서 사용하는 포스트 시퀀스                       |
| sns           | String    | SNS 타입, `Instagram` `Youtube`  2가지 존재                  |
| memberSeq     | Integer   | 어트랙트 멤버 시퀀스                                         |
| trackSeq      | Integer   | 어트랙트 멤버 시퀀스                                         |
| keyword       | String    | 어트랙트 검색시 사용한 키워드                                |
| postId        | String    | 인스타그램 혹은 유튜브에서 사용하는 post id                  |
| userName      | String    | 유저명                                                       |
| userId        | String    | 인스타그램 혹은 유튜브에서 사용하는 유저                     |
| profileImage  | String    | 프로필 이미지                                                |
| thumnailImage | String    | 썸네일 이미지 주소                                           |
| standardImage | String    | 기본 이미지 주소                                             |
| text          | String    | 인스타그램 게시글 내용, 유튜브에서는 description 의 내용 일부 |
| searchType    | String    | 검색 구분 코드                                               |
| hashtags      | String    | 인스타그램의 해시태그 모음, 유튜브의 경우 키워드와 동일      |
| type          | String    | 인스타그램> `image`, `video`, `carousel`<br />유튜브> `youtube` |
| link          | String    | 인스타그램 포스팅 혹은 유튜브의 링크                         |
| createdTime   | Timestamp | 컨텐츠 생성일 `unixtime`                                     |
| regdate       | Date      | 어트랙트에 등록된 시간                                       |
| status        | String    | 포스트 상태 값으로 API 에서는 `DISPLAY`                      |
| pluginLikes   | Integer   | 어트랙트 내부 사용값                                         |
| likes         | Integer   | 인스타 게시글 좋아요 수 (배치를 통해 정보 업데이트)          |
| comments      | Integer   | 인스타 코멘트 수 (배치를 통해 정보 업데이트)                 |
| updateDate    | Date      | 어트랙트 포스팅 업데이트 시각                                |



## 5. 결과값 코드

| Code | Description |
| ---- | ----------- |
| 200  | 성공        |



## 6. 주의사항

