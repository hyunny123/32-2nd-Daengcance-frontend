# 32기 2차 프로젝트

# 팀 소개

## 팀명 : 댕캉스(Daengcance)
- 펫시터 서비스를 제공하는 "펫플래닛" 사이트 모티브로 한 프로젝트
- 전체적인 UI적 틀과 기획부분만 클론
<br>

## 팀원 및 프로젝트 기간
- BE 최지수, 윤진섭 [댕캉스 백엔드](https://github.com/wecode-bootcamp-korea/32-2nd-Daengcance-backend)
- FE 이수광, 유동혁, 이현정, 장형원 [댕캉스 프론트엔드](https://github.com/wecode-bootcamp-korea/32-2nd-Daengcance-frontend)
- 프로젝트 기간 : 2022.05.09 (월) ~ 2022.05.20 (금) (2주)
<br><br>
## 기술 스택

- Back-End : <img src="https://user-images.githubusercontent.com/78680486/158049033-6a7836e9-da4a-4333-8f80-ea7972b2f922.svg"> <img src="https://user-images.githubusercontent.com/78680486/158049035-1b7122ad-cc99-477c-8d94-98ce48944d92.svg"> <img src= "https://user-images.githubusercontent.com/78680486/158049032-6368747a-c353-491c-8d22-63cdc1c525b1.svg"> <img src= "https://user-images.githubusercontent.com/78680486/158049036-4c7371ab-443d-4db9-baa0-6877a4528034.svg" >
- Front-End : <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=React&logoColor=white"> <img src="https://img.shields.io/badge/styledcomponents-DB7093?style=for-the-badge&logo=styled-components&logoColor=white">

## 협업 툴
 <img src="https://user-images.githubusercontent.com/78680486/158049034-cc1a893a-bc48-463f-811d-72e57853121d.svg" alt ="github"> <img src="https://user-images.githubusercontent.com/78680486/158049038-9c0dd825-e9c8-4e9d-aa60-f66deb56178d.svg" />

# 2. 서비스 소개

" 여러분의 소중한 반려견, 저희가 맡아드립니다. "의 슬로건을 가지고 기획 진행
<br>

## 2-1. 메인 서비스 소개

1. 날짜 캘린더로 원하는 기간동안 예약이 가능합니다.
2. 원하는 조건의 펫시어터를 고용할 수 있습니다.
3. 펫시어터의 장소를 보고 확인할 수 있습니다.
4. 예약 후 마이페이지에서 예약내용을 할 수 있습니다.
   <br>

# 3. 필수 구현사항

1. 로그인(카카오 소셜 로그인, 카카오 회원 가입), 로그아웃
2. 메인 페이지 (날짜 캘린더, 조건 선택 예약)
3. 지도 API

   <br>

# 4. 추가 구현사항
1. CR(U)D 리뷰 페이지
2. 마이페이지
   <br>

# 5. 서비스 개선사항

1. 회원가입, 로그인 페이지가 웹에 존재하지 않습니다.
2. 현재 예약은 어플을 통해서만 가능합니다.

---------

## 🙋‍♀️ 내가 구현 한 기능

### kakao social Login/Logout

 ![](https://velog.velcdn.com/images/hazel123/post/cbf3f5e4-761b-4dfd-a918-49fdc308381e/image.gif)

1.Restful API, 인가코드 받기
- 카카오 Restful API를 dotenv를 사용해서 env파일로 저장하고 .gitignore 파일을 사용하여 추적하지 못하게 한다.
- CRA 에 dotenv가 기본적으로 포함되어 있어서 자동으로 파일을 변환된다.
- .js 파일에 쓰는건 절대 금지!!(고소 당할 수 있음)
- 앞에는 꼭! REACT_APP_으로 시작해야 한다. 그리고 _ 사이에 빈칸이 2칸이 아닌지도 확인이 필요하다.

2.authData.js에서 process.env.REACT_APP_이름을 변수명을 사용해서 만들어 두는 파일 생성해둔다.
- 사용하기 편리해서 만들어 두었으나, 만들지 않아도 괜찮음.

3.Loginkakao 폴더 생서 그 안에 파일생성
- import로 API와 redirect_uri 받아와서 fetch 사용하여 토큰 요청
- method : POST
- code는 useLocation 사용/location.search는 url에 붙은 매개변수 반환한다.(물음표 뒤의 값)

4. 로직 
- 카카오에서 토큰을 주면 그 토큰을 백엔드에 주는 fetch 사용
- method: POST
- 백엔드와 token, nickname, username 등 상의를 통해 그대로 적어주어야 한다.
- 백엔드와 통신이 연결이 되면 토큰과 nickname을 localstorage에 저장.
- useNavigate를 사용해 로그인이 되면 메인페이지로 이동.

5.Navbar에 로그인 기능 
- 따로 페이지를 만드는 것보다 Navbar에 있는 로그인 버튼을 누르면 카카오 로그인 가능하게 기획
- 누르고 카카오 로그인창에 로그인을 하면 로그인 버튼은 로그아웃으로 바뀐다.
- 로그인이 되면 localstorage에 있는 token과 nickname을 getItem으로 사용해서 저장된 특정 키가 가르키는 값을 반환하여, navbar에 누구'님 이런식으로 출력
- 로그아웃을 클릭시 localstorage에 있는 것들을 removeItem을 사용해서 저장된 키와 값을 반환하여 로그아웃이 되고 navigate로 메인페이지 이동.
- import 해서 authData에서 URI 가지고 오기 
- 삼항식을 써서 로그인이 되었을경우 로그아웃이 뜨게 , 로그아웃을 클릭할 경우 removeItem 되어 다시 로그인 버튼으로 돌아온다.
- URI을 받아오는 태그를 a tag로 사용하다보니 로그아웃 tag도 a tag를 사용했는데 로그아웃을 하자마자 바로 로그인이 되는 상황이 발생. a 태그는 브라우저의 주소를 이동하며 페이지 자체를 새로고침한다는 것을 알고 div tag로 바꾸니 에러 해결.
 
6.Footer
- styled-components 사용해서 구현
- Login/Logout 기능 넣어놓음.
- 처음에는 그냥 반복되는 컴포넌트가 많긴해도 고정값이고 백엔드와 연동되는 부분이 없어서 그냥 하드 코딩을 했었으나, 피드백을 받고 우선 data파일을 만들고 , map을 돌려서 data를 받는 방법으로 구현하였다.
- 미디어 쿼리를 이용하여 1000px 이하 반응형 구현 해보았음.
- 컴포넌트 사용으로 구현을 더욱 가독성이 좋고 빠르게 구현할 수 있는 법을 알게됨.
- 개발자 도구에서 클래스네임으로 볼 수 없었기때문에 컴포넌트 만들시 이름짓기가 너무 어렵고 지어놔도 헷갈리는 경우가 종종 있었음.
- Navbar에 구현하였던 다크모드를 라우터에 스테이트를 만들어서 내려줘 버튼을 누를시 백그라운드 컬러가 바뀔수 있도록 구현.

7.reviewpage
- 다른 팀원 한분과 공동으로 구현
- 레이아웃은 전체적으로 팀원분이 해주시고 백엔드와 get과 post 기능 구현
- 백엔드 팀원분도 처음이고 나도 처음이어서 get부터 하나하나 맞춰가면서 구현
- post 부분에선 시간이 부족하여 백엔드도 구현이 어려워 post가 연결되어 201이 뜨는것만 확인.

-------

### 댕캉스 기능 구현 영상


로그인페이지
![](https://velog.velcdn.com/images/hazel123/post/f7e5cfbf-538e-477b-9e0d-15222086b3cf/image.gif)

메인페이지
![메인](https://velog.velcdn.com/images/hazel123/post/1fb721eb-6d45-4a38-8564-94cc23483515/image.gif)

상세페이지
![디테일페이지](https://velog.velcdn.com/images/hazel123/post/648c25f6-0e88-4e7d-8178-c285c785a566/image.gif)

리뷰페이지
![리뷰](https://velog.velcdn.com/images/hazel123/post/18e52cda-d69c-4dc6-8ae4-12ebd54782a4/image.gif)

다크모드 기능
![다크모드](https://velog.velcdn.com/images/hazel123/post/b358db3d-90a2-4205-a093-d712e975d7e8/image.gif)



YOUTUBE Full 영상
🐶[댕캉스](https://www.youtube.com/watch?v=S6aS-q1nbnk)

