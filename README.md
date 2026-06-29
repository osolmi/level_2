#HTML+CSS 26/06/22~
## HTML, CSS로 웹&앱 문서 제작하는 순서
1. 제작 문서에 맞게 의미있는 HTML 태그 구성하기
2. CSS 파일을 style 폴더에 별도로 생성하기
3. 1번에서 제작한 태그 중 디자인하려는 대상 확인하기
4. 3번 대상을 선택자로 작성하고 디자인목적에 맞게 속성:값 작성하기
## 선택자 {속성:값;}
## 선택자 {속성:값; 속성:값;}
# 선택자종류
## 태그 선택자
* 태그명을 선택자로 사용하는 선택자
* `<h1></h1>` -> `h1{속성:값;}`
## 클래스 선택자
* 반복되는 클래스명을 사용하는 선택자
* `<h1 class="title"></h1>` -> `.title{속성:값;}`
## 자식 선택자
* 특정 부모 안 자식을 사용하는 선택자
* `<h1><span></span></h1>` -> `h1>span{속성:값;}`
## 형제 선택자 + or ~
* `<div><a>1</a> <em>2</em> <del>3</del><div.>`
* `div > a + em {}` 해석) 부모div의 자식 a의 인접형제 em 선택
* `div > a ~ del {}` 해석) 부모div의 자식 a의 형제 del 선택
* `+`는 바로 옆에 있는 형제태그만 인식한다.
* `~`는 바로 옆 형제 포함 그 뒤에 모든 형제태그들을 인식한다.
# 자주 쓰는 웹 글꼴 주소
## Noto Sans KR
* <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap" rel="stylesheet">
## Pretendard
* <link rel="stylesheet" as="style" crossorigin href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard-dynamic-subset.min.css" />
# CSS 속성과 값, 활용 방법
## background
* `background-color` : 배경색상, 실제 배경색이 없어도 **영역구분용**으로 많이 사용
* `background-img:url();` : 배경 이미지, url() 안에는 **상대경로**로 작성하기
* `background-repeat` : 배경이미지반복설정(no-repeat 많이 씀), 배경이미지가 **작은 경우**만 체크하기
* `background-size` : 배경이미지크기 설정, 배경이미지가 들어간 요소보다 이미지가 작거나 클 경우
* `background-position` : 배경이미지위치 설정, **size와 함께 무조건 같이 사용하기, x y 순서로 작성**
* `background-attachment` : 배경이미지스크롤속성, 스크롤이동 시 이미지 고정시키고 싶을때만 사용
* (위) 배경 속성 작성 시 주의사항, 배경이미지는 일반 이미지태그와 다르게 요소의 크기가 자동으로 연장되지 않으므로 **반드시 width, height 크기를 함께 작성해야 한다**
## font
* `font-family` : 글꼴설정, 2개 이상 글꼴 작성하기
* `font-size` : 글자크기, px->em으로 전환해서 작성하기
* `font-weight` : 글자굵기, 보통(400) +-100 설정
* `letter-spacing` : 자간, -2% -> -0.02em
* `line-height` : 행간, 100% -> 1, 150 -> 1.5
* `color` : 글자색상
## box
* `border` : 두께 모양 색상 순서로 작성 예) 1px solid #000; 세미콜론은 맨뒤
* `padding` : 피그마의 오토레이아웃 패딩과 동일, **부모와 자식 사이 안쪽 여백**
* `margin` : 피그마의 오토레이아웃 간격과 동일, **형제와 형제 사이 바깥쪽 여백**
* `width` : 가로크기 (px, %, vw 단위 사용 가능)
    * 피그마 w 내용에 맞추기 설정 시 예) width:max-content;
    * 피그마 w 채우기 설정 시 예) width:100%;
    * 피그마 w 고정값(숫자 직접 입력 시) 설정 예) width:500px;
* `height` : 세로크기 (위 width 설정과 같음) 
* `border-radius` : 모서리 둥글기(피그마의 모서리반경과 같음), px단위사용하기
# layout
### 수평, 수직 정렬하기
* `text-align` : 수평정렬(left, center, right, justify(양쪽정렬))
* `line-height` : 글자가 1줄이고 높이가 고정되어있을 때 높이값 px를 넣어 수직중앙 정렬 설정
### flex 레이아웃 속성
#### 적용방법
1. 정렬하고자 하는 부모-자식 대상을 확인한다
2. 2개이상의 자식요소가 수평, 수직 어느방향으로 정렬되어있는지 확인한다.
3. 부모요소에게 `display:flex` 속성을 먼저 적용한다
4. 2번에서 확인한 방향을 메인축으로 지정하고 줄바꿈을 설정한다. `flex-flow`
5. 메인축 정렬, 교차축 정렬속성을 활용하여 마무리를 진행한다.
#### 주요 속성과 주의사항, 팁
* `display:flex`
* `flex-flow:방향 줄바꿈` : 메인축의 방향과 줄바꿈을 설정하는 묶음값(필수)
* `justify-content:메인축정렬값`
    * flex-flow에서 설정된 메인축방향에 따라 정렬을 정하는 속성
    * **메인축 row인 경우** : 왼쪽, 가운데, 오른쪽, 양쪽 끝, 균등여백
    * **메인축 column인 경우** : 위, 가운데, 아래, 양쪽 끝, 균등여백
    * 왼쪽, 위(flex-start), 가운데(center), 오른쪽아래(flex-end)
    * 양쪽 끝(space-between), 균등여백(space-around)
* `align-content: 교차축 2줄이상 정렬값` , `align-items:교차축 1줄 정렬값`
    * flex-flow의 값이 `nowrap`이면 -> `align-items`
    * flex-flow의 값이 `wrap`이고 교차축이 2줄이상이면 -> `align-content`
    *  **align-content만 space-between, space-around 값 사용가능**
    * **align-content, items 모두 사용가능** `flex-end, flex-start, center`
    * `flex-flow:row nowrap; align-items:flex-end;`
    * 해석) 메인축 수평, 줄바꿈 없음, 교차축 수직 - 맨 아래 왼쪽 정렬
    * `flex-flow:column wrap; align-content:center;`
    * 해석) 메인축 수직 줄바꿈 on, 교차축 수평 방향으로 2줄 이상 올때 - 가운데 정렬
