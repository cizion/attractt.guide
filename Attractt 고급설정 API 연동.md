# Attractt 고급설정 API 연동

### 단일 상품 정보

- **단일 상품에 대한 `상세 정보`를 내려주는 API로 개발해주시면 됩니다.**

- **API 주소는 특정한 형식없이 없습니다.**

  - 예시

    > 상하농원 : /product/detail.jsp?pid=`{product_id}`
    >
    > 뉴발란스 : /StyleList.svc/ProdDetail/id=`{product_id}`
    >
    > 폴더 : /StyleList.svc/`{product_id}`

<br>

- **Response**

  ```js
  callbackFunctionName({
    'id': '상품 고유번호',
    'name': '상품명',
    'image': [
      '상품 이미지1.jpg',
      '상품 이미지2.jpg',
      ...
    ],
    'price': '판매가',
    'discount': '할인가격',
    'unit': '중량/용량',
    'explain': '간략 상품설명',
    'link': '해당상품 페이지 주소',
    'cart': '장바구니 링크',
    'pay': '구매하기 링크'
  })
  ```

<br>

### 전체 상품 정보

- **`전체 상품 목록`을 내려주는 API로 개발해주시면 됩니다.**

- **API 주소는 특정한 형식이 없습니다.**

<br>

- **Response**

  ```js
  callbackFunctionName({
    'list': [
      {
        'id': '상품 고유번호',
        'name': '상품명',
        'api_link': '해당상품 상세정보 API 주소'
      },
      {
        'id': '상품 고유번호',
        'name': '상품명',
        'api_link': '해당상품 상세정보 API 주소'
      },
      {
        'id': '상품 고유번호',
        'name': '상품명',
        'api_link': '해당상품 상세정보 API 주소'
      },
      ...
    ]
  })
  ```

<br>

### * 주의사항

- **SSL 적용**
  어트랙트는 개인정보를 활용하는 사이트로 SSL(https 프로토콜)이 적용되어 있습니다. 따라서 API 호출 또한 SSL이 적용된 주소로만 가능합니다. 서비스 전체에 SSL 적용이 어려우시다면 특정 포트만 허용하여 주소를 전달하여 주시기 바랍니다.
  > 예) https://available.port:`{port}`/api/list....

- **크로스도메인 에러 방지를 위한 콜백 파라미터 작업**

  어트랙트측에서 데이터를 요청할 때 크로스도메인(CORS)을 방지하기 위해서 `callback=?` 파라미터를 붙여서 요청을 합니다. 서버에서 요청을 받으실 때 `callback` 파라미터 함수명을 받아 응답값을 감싸서(상단 **Response**의 `callbackFunctionName`) 내려주시면 됩니다.

- **장바구니 및 구매하기 연동시 특이사항 확인**

  고객사 홈페이지마다 장바구니 및 구매하기 연동의 제한이 걸리는 경우가 있습니다. 장바구니 동기화 및 구매가 발생할 시 파라미터 전달방식에 대한 사전 공유 부탁드립니다.

