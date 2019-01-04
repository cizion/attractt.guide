# Attractt API - getPosting

## 1. 개요

- 어트랙트 설치코드를 통하여 설치하는 경우가 아닌, 직접 API를 호출해서 작업하는 경우 사용합니다.
- `JSON` 형태의 데이터로 제공됩니다.

<br>
<br>

## 2. 호출

```javascript
<!-- jQuery가 없을 경우 넣어주세요. -->
<script type="text/javascript" src="https://code.jquery.com/jquery-1.12.4.min.js"></script>

<script type="text/javascript">
    <!-- Attractt 데이터 호출 코드 -->
    $.ajax({
        url : "https://www.attractt.com/api/posts",
        data : {
            code : 고객사 계정, 보드별 고유 코드 제공
        },
	dataType : "jsonp",
	jsonp : "attracttCallback",
	success : function(data) {
            // 결과값 출력
            // 결과값의 자세한 정보는 아래 4.항목별 설명 참조
            console.log(data);
        },
	error : function(data) {
            // 에러코드 출력
            // 에러코드의 자세한 정보는 아래 5.결과값 코드 참조
            console.log(data);
        }
    });
    <!-- Attractt 데이터 호출 코드 끝 -->
</script>
```

<br>
<br>

## 3. 결과값 예시

```json
{
  "code": 200,
  "track_seq": Integer,
  "result": {  
    "count": Integer,
    "data": [
      {
      	"post_seq": Integer,
        "post_id": String,
        "sns": String,
        "user_name": String,
        "profile_image": String,
        "created_time": Timestamp,
        "link": String,
        "type": String,
        "thumbnail_image": String,
        "low_image": String,
        "standard_image": String,
        "hd_image": String,
        "video": String,
        "carousel_media": String,
        "hashtags": String,
        "text": String,
        "likes": Integer,
        "comments": Integer,
        "regdate": Date,
        "keyword": String,
        "search_type": String
      },
      ...
    ],
  }
}
```

<br>
<br>

## 4. 항목별 설명

> 해당 항목들은 Instagram Graph API 정책 변경에 따라 추후에 변경되거나 제거될 수 있습니다. 

| Key                 | Type      | Description                                                  |
| ------------------- | --------- | ------------------------------------------------------------ |
| **post_seq**        | Integer   | Attractt에 저장된 순서의 sequence                            |
| **post_id**         | String    | Instagram에서 제공되는 콘텐츠 고유 ID                        |
| **sns**             | String    | 콘텐츠가 게시되어 있는 서비스                                |
| **user_name**       | String    | 콘텐츠 게시자 이름(Instagram Graph API 변경으로 현재 제공되지 않음) |
| **profile_image**   | String    | 콘텐츠 게시자 프로필 이미지(Instagram Graph API 변경으로 현재 제공되지 않음) |
| **created_time**    | Timestamp | SNS에 콘텐츠가 게시되어진 시간. Timestamp 형식으로 `new Date()` 함수를 사용하거나 외부 라이브러리를 이용하여 식별할 수 있는 데이터로 전환하여 사용해야 함.(Instagram Graph API 변경으로 현재 제공되지 않음) |
| **link**            | String    | 개별 콘텐츠 링크                                             |
| **type**            | String    | 콘텐츠 형태 - image, video, carousel                         |
| **thumbnail_image** | String    | 대표 섬네일 이미지 - 검색 유형이나 콘텐츠 형태에 따라서 제공되지 않을 수 있음. image 라고 명시되어 있으나 동영상의 경우에 동영상 주소로 내려옴. 주소를 정규식으로 판별하여 image/video 여부를 판단하고 html 태그를 구분하여 삽입하여야 함. |
| **low_image**       | String    | 150x150 픽셀 크기의 대표 이미지(이전 데이터에서만 제공됨)    |
| **standard_image**  | String    | 640x640 픽셀 크기의 대표 이미지                              |
| **hd_image**        | String    | 1080x1080 픽셀 크기의 대표 이미지(현재 사용 불가능한 주소 형식) |
| **video**           | String    | 동영상 데이터 주소 - 동영상이 있을 경우에만 제공             |
| **carousel_media**  | String    | 다중 콘텐츠 데이터 - `Array` 형식을 `JSON.stringify` 로 `String` 화 하여 저장하고 내려줌. 사용하기 전 `JSON.parse()` 로 `Object` 화 하여 사용. 없는 경우 제공 안됨. |
| **hashtags**        | String    | 콘텐츠 본문 내용에 있는 해시태그만 도출하여 저장한 내용 - `#` 을 제거한 텍스트 형태로 저장. ex) `attractt 어트랙트 시지온` |
| **text**            | String    | 콘텐츠 본문 내용. 해시태그 포함.                             |
| **likes**           | Integer   | 콘텐츠 좋아요수                                              |
| **comments**        | Integer   | 콘텐츠 댓글수                                                |
| **regdate**         | Date      | Attractt의 보관함에 저장되어진 시간                          |
| **keyword**         | String    | Attractt에서 검색할 때 사용한 검색어                         |
| **search_type**     | String    | Attractt에서 검색할 때 사용한 검색어 유형 - hashtag(#), user(@) |

<br>
<br>

## 5. 결과값 코드

| Code | Description                                                  |
| ---- | ------------------------------------------------------------ |
| 200  | 성공                                                         |
| 409  | 결제 필요 - 결제내역이 존재하지 않는 보드는 www.attractt.com 외부에서는 데이터 호출이 불가능합니다. |

> 데이터가 존재하지 않는 경우에도 코드값은 `200` 으로 내려옵니다. `result.data` 내부에 데이터가 존재하는지를 확인하여 `결과없음` 여부를 판단해주세요.

<br>

<br>

## 6. 주의사항

- 고객사에서 데이터를 직접 다루고 개발해야하는 과정으로, 시지온 측에서 직접적인 코드 수정이나 개선이 어렵습니다.

- `thumbnail_image` 가 없는 경우 대표 이미지나 다중 콘텐츠 데이터 - `carousel_media` - 의 가장 첫번째 데이터를 이용하여 섬네일을 삽입하여야 합니다.

  > `carousel_media` 의 경우 Graph API 로 바뀌면서 사진, 동영상에 관계 없이 `media_type` 과 `media_url` 로 통합되어 내려오도록 바뀌었지만, 이전의 데이터들은 `images` 또는 `videos` 의 `Object` 안에 `type` 과 `standard_resolution.url` 을 통해서 데이터가 제공됩니다. 데이터의 형태를 판단하여 예외처리를 하여 두 가지 모두 가능하도록 개발하여야 합니다. 

- Instagram Graph API 교체건으로 인해 이전 데이터들과의 혼용이 있어 개발하는데 착오가 발생할 수 있습니다.

  > API 교체로 인해 제공되지 않거나 변경된 형식의 데이터들이 다수 존재합니다.
