# Attractt Popup CSS Guide : TAG

**고객사에서 직접 페이지에 삽입하여 수정하는 어트랙트 팝업 커스터마이징**

<br>

#### 위치

- 어트랙트의 콘텐츠를 클릭했을 때 생성되는 팝업

#### 대상

- 고객사에서 설정한 고급설정 태그

<br>

#### 예시

> http://test.livere.co.kr/attractt/preview.html

```css
body #attractt-popup .created-tag {
	opacity: 0.8 !important;		/* 태그버튼 기본 투명도 */
}

body #attractt-popup .created-tag.hide {
	opacity: 0 !important;			/* 숨겨진 태그버튼 : 고정값 */
}

body #attractt-popup .created-tag:after,
body #attractt-popup .created-tag:before,
body #attractt-popup .btn-tag-show:before {
	display: block;	 				/* 화살표 표시/숨김 */
	border-bottom-color: #ffffff;	/* 화살표 색 변경 */
	left: 15px; 					/* 화살표 좌우 위치 변경 : default 15px */
	bottom: 97%; 					/* 화살표 상하 위치 변경 : default 100% */
}

body #attractt-popup .created-tag i,
body #attractt-popup .btn-tag-show i {
	position: absolute;								/* 태그버튼 크기를 변경하려면 position을 absolute로 고정 */
	top: 0;											/* 태그버튼 상하 위치*/
	left: -5px;										/* 태그버튼 좌우 위치 : -(태그버튼 가로 크기 / 2) + 15, default 0px */
	width: 40px;									/* 태그버튼 가로 크기 */
	height: 40px;									/* 태그버튼 세로 크기 */
	border: 3px solid #fff;							/* 태그버튼 테두리 : default none */
	border-radius: 50% 50% 50% 50%;					/* 태그버튼 테두리 radius : default 0px */
	background-color: #d85629;						/* 태그버튼 배경색 : default #101010 */
	background-position: -11px -11px;				/* 태그버튼 이미지 위치 */
	box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);		/* 태그버튼 그림자 */
}

body #attractt-popup .created-tag.active:after,
body #attractt-popup .created-tag.active:before {
	border-bottom-color: #fff;						/* 선택된 태그버튼의 화살표 */
}

body #attractt-popup .created-tag.active i {
	background-color: #d85629;						/* 선택된 태그버튼의 배경색 */
}
```