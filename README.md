<meta http-equiv="X-UA-Compatible" content="IE=edge">
    Internet Explor의 랜더링 방식의 메타데이터 (최신버전으로)
<meta name="viewport" content="width=device-width, inital-scale=1.0, user-scalable=no, maximum-scale=1.0, minimum-scale=1.0">
    Viewport관련 메타데이터 
    width=device-width : 가로사이즈를 사용하는 디바이스의 가로사이즈와 동일시한다.
    inital-scale=1.0 : 초기 화면배율을 설정하는데, 1.0 = 100%로 설정한다.
    user-scalable=no : 사용자가 배율조정을 하지못하도록 설정한다.
    maximum-scale=1.0, minimum-scale=1.0 : 최대,최소 배율을 설정한다. 사용자의 배율조정은 막아놓아서 최대,최소를 기본 화면배율 설정과 동일 시하여 배율조정을 못하도록 한다.

<meta property="og:type" content="website">
    property="og:type" : og는 'Open Graph'로 일종의 '정보'를의미란다. 또 그 정보의 값으로 type임을 정의하고있는데, type는 content의 값인 website를 의미한다. 즉, 속성=정보=type=website의 의미를 내포하는 메타데이터이다.

<meta property="twitter:card" content="summary">
    twitter:card는 위에서의 og:type와 유사하며 내용은 summary = 개요의 정보를 정의하고 있다.

    Open Graph : 이 사이트에서 외부로 정의해주고자 하는 정보들을 정의해줄 수 있다. 사이트의 설명이나, 제목, 대표이미지등의 정보들을 정의한다. 비슷한 것으로 Twitter Card등이 있다.

    카카오톡이나 외부사이트에 공유할 경우 해당 사이트의 정보등이 링크와 함께 계시되는데, 이 떄 나타나는 내용등이 og, twittercard이다. 그외에 검색엔진등의 정보에서도 정보를 긁어가 활용될 수 있다.

# Favicon(파비콘)
<link rel="icon" href="favicon.png">
<link rel="apple-touch-icon" href="favicon.png">
    favicon을 정의할 떄 link를통해 icon을 참조한다. 첫 번쨰는 일반 웹사이트등에서의 favicon등록을 명시하는 내용이고, 두 번쨰의 rel="apple-touch-icon"은 모바일 환경에서 favicon을 정의해줄 떄 이용한다. apple-touch-icon라 하여 아이폰에서만 나타나는건 아니고 안드로이드 환경에서도 적용된다.

<link rel="shortcut icon" type="image/x-icon" href="favicon.ico">
    IE에서 favicon을 사용할 떄 사용하는 링크이다. IE에서는 .png보다 .ico파일을 이용하는데, 위의 코드가 없다면, Loot에서 icon파일을 찾아서 favicon으로 사용되며, 위의 코드가 있다면, 경로를 추적해 사용되는 개념이다. 만약 Loot에(반드시 Loot에 등록해주어야한다.) favicon으로 사용할 icon파일을 등록해 두었다면, 굳이 위의 코드를 사용할 필요는없다.

> 브라우저에서 찾기 용이하게 icon의 이름은 왠만하면 favicon으로 명명하는게 좋다.

# Font(외부의 웹폰트 사용)
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">

웹 폰트는 외부의 만들어진 폰트를 링크태그로 참조하여 활용하는 방식으로, 시스템에서 지원해주는 기본 폰트들보다 경량화 되어있다.

첫 번째 사용한 link태그는 현재 페이지에서 외부 도메인의 리소스를 참고하는 것을 브라우저에게 알려 미리 외부 도메인과 연결을 설정할 수 있게 하는 장치이다.
preconnect를 사용하면 브라우저가 사이트에 필요한 연결을 미리 예상할 수 있게 되고, 브라우저는 필요한 소켓을 미리 설정할 수 있기 때문에 DNS, TCP, TLS 왕복에 필요한 시간을 절약할 수 있게 된다. 한마디로 로딩 속도가 빨라진다.

단점 : preconnect는 외부 도메인과 연결을 구축하기 때문에 많은 CPU 시간을 차지하게되는데, 보안 연결의 경우 더 많은 시간을 차지할 수 있다. 10초 이내로 브라우저가 닫힌다면, 이전의 모든 연결 작업은 '무'로돌아가는것이기 때문에 브라우저가 빨리 닫힐 수 있는 페이지에서는 preconnect를 사용하지 않는 것을 추천한다.

참조 : https://beomy.github.io/tech/browser/preload-preconnect-prefetch/

# CSS
<link rel="stylesheet" href="css/reset.css">
<link rel="stylesheet" href="css/main.css">
css 파일을 불러오는 태그이다. 
모든 브라우저들은 기본적으로 브라우저에서 설정한 값들이 존재하기 떄문에 이를 활용할것이 아니라면 처음에 reset하는 작업이 필요하다. 요즘에는 reset.css를 배포하는 곳이 많으니 참고해서 하나의 파일로 설정을 많이해주는데, 여기서 중요한것은 이런 plug-in파일들은 기존의 css파일을 덮어쓸 수가있다. 따라서 항상 main이 되는 css파일 위에, 처음에 <link>를 통해 참조 해주어야한다.

reset.css파일이 없다면 검색창에 'reset css cdn(Content Delivery Network)'을 검색해 웹 경로를 통해 참조해줄 수도 있다. 가끔 주소 끝에 reset.css와 reset.min.css가 같이 보이는데, min.css는 압축된 파일로 내용을 보기에는 불편하기 떄문에, 실제 서비스할 때 외에는 기본적인 reset.css파일을 이용하면 된다.

> cdn(Content Delivery Network) : 콘텐츠를 효율적으로 전달하기 위해 여러 노드(지점)를 가진 네트워크에 데이터를 저장하여 제공하는 시스템을 말한다. 서비스 제공자에 직접 연결되어 데이터를 전송하기 때문에, 콘텐츠 병목(지연, 막힘)을 피할 수 있다.

# BEM(작명 규칙) 
의미 자체는 작명 규칙을 위한 것이 아니지만, 보통 CSS의 작명규칙으로 통상적으로 사용되고 있다.
1. - : 일반적인 작명(가장 많이 흔하게 사용할 수 있는 기호)

2. __ : ~의 일부분을 의미한다. 
    ex) body__container : container는 body의 일부분이다. 상하위 요소를 따지거나 포함관계를 지칭할 때 많이 사용된다.

3. -- : ~의 상태이다. 
    ex)
    <div class="btn--success"></div>
    <div class="btn--danger"></div>
    <div class="btn--primary"></div>
    현재 버튼의 상태를 의미하는 의미로 작성되었는데, 이러한 상태표시는 '--'기호를 통해 작성해준다.

# 스타일

.btn {
    height: 34px;
    background: #eee linear-gradient(to bottom, #fcfcfc, #eee);
    border: 1px solid #d5d5d5;
    border-radius: 4px;
    display: inline-flex;
    align-items: center;
    padding: 0 12px;
    font-size: 14px;
    font-weight: 500;
    line-height: 1.5;
    cursor: pointer;
    box-sizing: border-box;
    position: relative;
}

display: inline-flex;
align-items: center;
padding: 0 12px;
위의 속성으로 요소가 중앙에 배치되도록 설정해주었는데, 원래는 justify-content: center;까지 추가해 중앙 정렬을 대부분 사용하지만, display를 block요소인 flex에서 inline요소인 inline-flex로 바꾸어 버튼안의 text의 길이에 딱 맟추어 나오게 해주었고, padding을 왼쪽,오른쪽에만 12px씩 주어 약간의 공간을 넣어주어 중앙정렬을 유도해주었다.

.input--text {
  height: 34px;
  padding: 0 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-sizing: border-box;
  outline: none;
  box-shadow: inset 0 1px 2px rbga(0,0,0,0.075);
  font-size: 16px;
}
.input--text:focus {
  border-color: #51a7e8;
  box-shadow: inset 0 1px 2px rbga(0,0,0,0.075), 0 0 5px blue;
}

box-shadow: 스타일1, 스타일2;
스타일1의 그림자를 유지한채, 스타일2의 그림자도 넣어준다.
inset은 기본적으로 테두리 바깥이 기본값으로 적용되는데, 테두리 내부로 그림자를 설정하고 싶을 떄 넣어준다.
outline: none; 
input이 focus되었을 떄, 테두리 주의의 효과로 border보다 제어해주기 힘드므로 사용해주지않고, focus되었을 떄 효과를 넣는 방식을 선택하였다.

/* Vendor Prefix (브라우저 업체별 접두사) */
.input--text::-webkit-input-placeholder { color: #cacaca; }
.input--text::-ms-input-placeholder { color: #cacaca; }
.input--text::-moz-input-placeholder { color: #cacaca; }
CSS에서는 input-placeholder을 지원하지않는다. 따라서 .input--text::input-placeholder로 작성하면 스타일이 적용되지 않는것을 확인할 수 있다. 하지만 브라우저마다 실험적인 기능을 지원하는데, 이를 Vendor Prefix라한다. 
각 브라우저마다 키워드가 정해져있고, Chrome : -webkit-, MS : -ms-, Firefox : -moz-로 쓰이고 있다.
모든 브라우저마다 지원하는 기능에는 차이가 있고, 위의 input-placeholder의 기능은 위의 3브라우저에서 지원하고 있다. (-o-의 Opera브라우저는 지원하지 않는다.)

/* Header */
header {
    border-bottom: 1px solid rgba(0,0,0,0.75);
    box-shadow: 0 0 5px rgba(0,0,0,0.75);
    background: #fff;
}
header .inner {
    max-width: 980px;
    height: 78px;
    margin: 0 auto;
    background: tomato;
}

header의 풀이에서는, height가 header내가 아닌 .inner에 작성해주었다. 이는 header에 지정해주면, 지정안된 .inner에서도 한번더 작성해주어야하기떄문이고, 만약 위처럼 코드를 작성하면 header의 height: auto인 기본값으로 설정되어 자식요소에 영향을 받기 떄문에, 코드를 생략할 수 있게된다.

다음으로는 .inner의 중앙 정렬배치이다. 여기서는 margin: 0 auto를 이용하였는데, header의 width(:auto)에서 .inner에서 지정한 width값의 빈공간을 margin을 이용해 좌우에 넣어 주었고, 이를 통해 자연스럽게 중앙정렬이 됨을 확인 할 수 있다. margin을 이용하여 중앙 정렬을 행할 때에는, 꼭 해당 선택자의 width값이 지정되어야 한다.

header .menu-group {
    display: flex;
    align-items: center;
    height: 100%;
}
header .logo {
    margin-right: 10px;
}
header .logo a {
    background: url(../img/logo.svg);
    width: 32px;
    height: 32px;
    display: block;
    text-indent: -9999px;
}
header .logo a:hover {
    background: url(../img/logo_on.svg);
}
header .main-menu {
    display: flex;
}
header .main-menu li a {
    display: block;
    padding: 10px;
    color: #3c4146;

.menu-group의 위치는 아무런 설정이 없을 시, height는 인라인 요소에 영향을 받아 font-size인 16px만 가지고 있다. 우리가 필요한것은 중앙에 정렬을 해야하기에, height를 100%로 주어 .inner의 78px에 맟추어주고, flex일 때 대표적인 정렬인 align-items: center;를 주어 배치를 완성해 주었다. 

logo는 img태그를 이용한 방식이 아닌, background의 이미지 삽입 방법을 이용하였는데, url()로 이미지를 가져오고, a태그는 인라인 요소이기에, 특정한 너비를 갖지 않으므로, 원하는 크기를 설정 후, 블럭요소로 바꾸어 설정해 주었다. 여기서 <img>에서는 alt속성을 이용해 이미지가 출력되지 않을 시, 대체 텍스트를 설정해 줄 수 있지만 background에서 이미지 삽입시 해당 속성이 없다. 따라서 같은 효과로 <a>에는 대체 텍스트를 content로 넣고, 스타일에 text-indent: -9999px를 작성해 그 기능을 대신해 주었다. text-indent로 텍스트는 왼쪽으로 -9999px만큼 이동해주는데, 특별한 의미는 없이 명시적 값으로 이해하면 된다. 

/* Float */
.clearfix::after {
    content: "";
    clear: both;
    display: block;
}
.float--left {
    float: left;
}
.float--right {
    float: right;
}

왼쪽 매뉴그룹(menu-group)과 오른쪽 매뉴그룹(sign-group)를 inner안에 왼쪽과 오른쪽에 배치를 해야되는데, 이 떄, 이용하는것이 float속성이다.
일반적으로 float은 속성 값만 부여하게 되면, 부유되기(요소가 위로 떠보이는 현상)) 때문에 부모요소가 제대로 감싸줄 수 없다. 따라서 추가적으로 clearfix를 통해 해결해 줄 수 있다.
자세한 내용은 이전 float속성정리편을 참고

float을 이용한 자리 배치는 종종 중복해서 사용되므로 공통 코드로써, 재활용될 수 있게 만들어 주었다. 사용시에는 원하는 태그의 class로 넣어주면 스타일이 적용이 된다.

여기까지 진행 후 확인하면, .btn-group의 두 버튼이 한칸정도 띄어져 수평관계를 이루지만 .btn에서 지정해준 padding은 적용되지 않았다. 이는 inline-flex로 적용해주었기 때문에 수평정렬은 되었지만 padding과 margin을 무시하는 특성상 적용이 되지 않은 것이다. 또 한칸은 공간은 html코드내에서 하나의 태그를 선언하고 줄바꿈하여 다른 태그를 작성하는데, 이 떄 줄바꿈을 해주면 생기는 한칸의 공간이 스타일 상이 보여지는것으로 인식하면 된다.
이럴경우 margin과 padding을 넣어줄 부분의 수평정렬을 새로 만들어주는데, inline->block으로 바꾸어주고, 원하는 선택자에 값을 추가해 넣어준다.

/* Section & Inner */
.section {
    position: relative;
} 
.section .inner {
    max-width: 980px;
    margin: 0 auto;
    box-sizing: border-box;
    position: relative;
}
만들고자하는 홈페이지에 section과 inner의 공통부분이 많아 공통코드로 빼주어 작성해준다. padding등으로 요소가 커질 시 원하는 틀을 벗어나는 현상을 방지하기위해서, box-sizing속성을 넣어주었고, section과 inner내부에서 position을 이용하였을 때, 1차 방지라인을 위하여 position: relative을 작성해주었다. (position: absolute는 부모요소에 relative과 없을 시, 계속적으로 상위요소를 타고가 찾으며, 끝에서는 브라우저까지 가기떄문에 해당 문제를 미연해 방지한다.)

/* Visual */
.section--visual {
    background-image: url("../img/bg.jpg");
    background-repeat: no-repeat;
    background-position: bottom left;
    background-size: cover;
}
.section--visual::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background: rgba(0,0,0,.3);
}
우리는 고정너비를 max-width: 980px로 지정하였기에, 화면을 축소해보면 배경이 잘려 나오는것을 확인 할 수 있다. 이를 방지하고자,  background-size의 값을 cover로 설정하여 전체 화면에 이미지로 덮어주게 해주었다.  

화면의 .section--visual의 배경을 background-image태그로 넣고보니 원하는 색상보다 더 밝은거 같아, 어둡게하는 작업을 추가해주었다. ::before를 이용해, 검은색에 투명도를 설정하여 이미지 전체에 덮어주는 방식을 이용하였는데, 위의 코드처럼 위,아래,좌,우 모두 0의 위치에서 absolute값을 가지면, 해당 범위는 부모요소의 가로,세로너비의 100%를 가진다. 부모요소는 이미지를 넣은 선택자이기에, 원하는 어두운 배경색을 덮을 수 가있다. 
top: 0;
left: 0;
width: 100%;
height: 100%;
처럼 작성하여도 위와 효과는 동일하다.
absolute의 부모요소의 position값은 공통 코드를 통해 작성해주었다.

#sign-form [type="submit"] {
    width: 100%;
    height: 62px;
    padding: 0 25px;
    font-size: 20px;
    justify-content: center;
}
button의 특별한 이름이 없으므로, [type="submit"]을 이용해 지정해줬으며, 미리 만들어놓은 btn의 display가 inline-flex이므로 text-align속성을 사용할 수 없다. 따라서 justify-content: center을 통해 내용을 중앙에 나오도록 설정해주었다.

.section--visual .summary {
    flex-grow: 1;
    flex-basis: 0;
    /* flex: 1; */
    margin-right: 90px;
}
flex속성은 단축속성을 하나만 사용해도 flex-basis의 기본값인 auto는 자동으로 0으로 바뀌게된다. 따라서 개별속성으로 작성해도 되고, flex: 1; 작성해주면 같은 효과를 적용해 줄 수 있다.

(1)
<div class="summary__title">
    How people build software
</div>
(2)
<div class="summary__title">
    How&nbsp;people build&nbsp;software
</div>
Html에서 띄어쓰기와 같은 의미로 '&nbsp;'가있다. (1)을 적용하면 화면에 build까지 첫줄에 나타나고 software는 줄바꿈됨을 확인 할 수 있다. 하지만 원하는 바는 build부터 두 번째 줄에 나오게하고 싶은데, 이 떄 활용할 수있는게 '&nbsp;이다. &nbsp;을 이용하여 단어들을 묶어주면 해당 단어(build&nbsp;software)은 하나의 단어가 된다. 따라서 홈페이지에서는 첫 줄에 build&nbsp;software만큼에 공간은 남지 않으므로 두 번쨰줄로 자연스럽게 줄바꿈이 일어나준다. <br>을 활용할 수 도있지만 이처럼 '&nbsp;'을 통해 단어를 묶어주어 줄바꿈을 유도해주는 방법도 있다.

<br>을 사용하지 않고, &nbsp;을 활용하는 이유는 나중에 반응형으로 만들어줄 때를 고려해서이다. 축소된 상태에서 자연스러운 줄바꿈 처리를 유도하는 목적이라 생각하면 된다.
<br>은 확실히 줄바꿈을 고정할 때 이용해준다.

/* Feature */
.section--feature {
    background: #f5f5f5;
    padding-top: 66px;
}
.section--feature .summary {
    max-width: 820px;
    margin: 0 auto;
    text-align: center;
}
.section--feature .video {
    max-width: 650px;
    margin: 50px auto;
}
.section--feature .video .video-ratio {
    height: 0;
    padding-top: 56.25%;
    position: relative;
}
.section--feature .video .video-ratio iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
동영상과 약간의 설명, .tile이라 칭하는 요소가 들어가는 section이다. 그중 설명란은 글자 중앙 정렬과, margin: 0 auto;를 통해 가운데로 content를 몰아주었고, 해당 틀은 video역시 같다. video에서는 고정된 사이즈가 아닌 축소,확대시 반응형으로 만들어주기 위해서, height: 0으로 주었고, 대신에 padding-top: 56.25%를 주었다. 기본적으로 padding에서 %는 부모요소의 width의 영향을 받는데, 부모요소인 .video에 max-width로 650px로 설정해 놓았기에 그의 비율에 맟춰 padding-top으로 높이가 자동 설정됨을 알 수 있다. 56.25%비율은 16:9의 비율로 설정할 떄의 값이다. 
또, padding으로 높이가 설정되었기에 해당부분이 빈 공간으로 되어있기에 그안에 요소인 iframe은 밀려나 밑에 나타나게된다. 이를 위의 공간이 넣어주기위해서 position을 활용하였다. 
top: 0;
left: 0;
width: 100%;
height: 100%;
위 코드들은 부모요소가 설정한 frame틀에 딱 맟추기위한 코드로 이해하면 된다.

<!-- Feature -->
.section--feature .tiles ul li img {
    max-width: 100%;
    padding: 14px 10% 24px;
    box-sizing: border-box;
}
타일 아이템들을 반응형으로 만들 때 사용하는 코드들이다. 축소시 비율에 맞게 축소 확대가 이루어져하는데, 여기서 width:100%활용한다. 하지만 그냥 width을 사용시에는 매우 작게 축소할경우 아이템이 사이즈를 벗어나는경우가 발생할 수 있는데, 이를 방지하기위해서 max-width를 사용한다.
또 padding을 추가하면 아이템들이 역시 원하는 크기밖으로 넘치게되고, 이를 잡는 역할이 box-sizing: border-box 이다.

타일을 나열하는 방식들
.section--feature .tiles ul {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}
grid의 방식의 예이다. grid는 대체적으로 모던한 최근 기술이므로 구형의 브라우저에서는 동작하지 않을 수 있는 단점이 있지만, 비교적 쉽게 구현이 가능하다.

HTML
<ul class="clearfix">
CSS
.section--feature .tiles ul li {
    padding: 34px 24px;
    text-align: center;
    line-height: 1,5;
    border-right: 1px solid #e5e5e5;
    box-sizing: border-box;
    float: left;
    width: 25%;
}
다음으로 구형브라우저에서도 동작이 가능한 float을 활용한 방식이다. float: left를 통해 수평정렬로 바꿔주고, 1:1:1:1비율을 위해 전체 4등분한 25%의 너비를 넣어주었다. 
float을 활용할때는 반드시 clearfix를 추가해줘야되고, li의 상위요소인 ul태그에 넣어주어야한다. 
가끔 padding, boder속성이 있으면, 원하는 %값이 나오지 않는경우가 있는데, 이를 방지하기위해 box-sizing: border-box를 이용해주면 원하는 결과값을 얻을 수 있다.

여기서는 반응형 웹페이지를 같이 다루기때문에, 화면이 축소시(1024px미만시) 타일을 행과열이 2x2인 형태로 바꿔줄것이다. 따라서 grid를 활용하여 진행할 수는 있지만, float을 이용해 width의 %값을 다르게해주어 하는편이 조금더 간단하고 복잡도를 줄일 수 있기에, float를 활용해 줄것이다. (4등분 : 25% , 2등분 : 50%)

display: float을 사용할 때, 가운데 정렬을 사용하면 요소의 층(line 간격)이 원하지 않는 결과를 초래할 수 있다.

footer .logo {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    width: 24px;
    height: 24px;
}
위의 코드의 예는 부모요소의 content안에서 특정 요소를 정 가운데 배치할 때 사용할 수 있는 코드이다. 
위치를 지정해주고, margin:auto를 주면, 정 가운데에 위치하고 요소의 크기만큼 값을 부여해주면 완성이다.

<!-- 반응형 웹페이지 -->

async 속성 : 브라우저에 스크립트를 비동기 적으로 다운로드하고 실행하도록 요청한다. 스크립트가 실행되면 callback 매개 변수를 사용하여 지정된 함수를 호출한다.
defer 속성 : HTML코드가 전부 구현된 후, script내용을 실행한다.

@media : 다양한 미디어 유형이나 장치에 따라, 서로다른 스타일 규칙을 적용할 때 사용한다.

@media 미디어타입 and (미디어특성) {
    CSS코드
}
ex)
@media screen and (max-width: 1200px) { 
    body {
        color: red;
    }
}
일반적인 화면에서 최대가로너비가 1200px일 떄까지 body의 글자색을 빨강으로하는 예제이다. 일종의 조건문으로 이해하면 편리하다.

미디어타입
타입        의미                                기본값
all         모든 미디어 타입에 적용              all
screen      컴퓨터 화면, 타블렛, 스마트폰 등
print       인쇄 적용

미디어특성
특성
width       뷰포트의 가로 너비
max-width   뷰포트의 최대 가로 너비(이하)
min-width   뷰포트의 최소 가로 너비(이상)

height       뷰포트의 세로 너비
max-height   뷰포트의 최대 세로 너비(이하)
min-height   뷰포트의 최소 세로 너비(이상)

orientation  뷰포트의 방향(portrait, landscape)
    portrait : 뷰포트의 세로 너비가 가로 너비가보다 더 클 때의 조건식
    landscape : 뷰포트의 가로 너비가 세로 너비가보다 더 클 때의 조건식
기타      

디바이스별 가로 너비 단위 Media(Grid) options
|      종류      |     디바이스     |  단위(px)   |
| :------------: | :--------------: | :---------: |
| Large Devices  |     Desktops     | 1024px 이상 |
| Medium Devices |     Tablets      | 1024px 이하 |
| Small Devices  | Tablets + Phones | 768px 이하  |

표준 기준은 아니며, 디바이스 종류에 따라 단위가 달라질 수 있다.

/* Media */
@media (max-width: 1024) {
    header .inner {
        max-width: none;
    }
}
우리가 원하는 구조는 1024px이하 일 떄, width를 전부 다 사용할 것이고, 그를 위해서 최대 너비를 정해줬던 980px의 속성을 없애 줄 것이다. 이떄 기존의 공통 코드로 .section .inner 안에 max-width를 설정해 주었는데, 위에 처럼 header .inner에서 max-width의 속성값을 초기화해주면 원하는 결과가 나오지 않음을 확인할 수 있다. 이는 명시도값에 의한 우선순위 떄문인데, class선택자로 .section .inner는 명시도값이 20점이지만, header .inner는 태그선택자와 class선택자이므로 명시도값이 11점으로 우선순위에서 밀려나게된다. 따라서 이를 고려해 일치선택자를 추가하는 것으로 코드를 수정해주어 해결할 수 있다.
/* Media */
@media (max-width: 1024) {
    header.section .inner {
        max-width: none;
    }
}
명시도 : 21점
따라서 초기화하는 과정에서는 명시도를 감안해 우선순위를 따져봐야 한다.

위의 문제로 주의할 사항이 @media를 통해 스타일을 부여할 때에는 지정하는 선택자의 양식을 동일하게 해주어야한다. 예를들어 기본 형태에서는 ul li {}로 스타일을 넣어주었는데, @media를 통해 같은 선택자에 스타일을 부여할 때에도 같은 ul li {}로 부여해주는편이 좋다. 
만약 너무 길어 단축해서 코드를 작성하거나, 생략이 가능해 서로의 선택자 형식이 다르다면, 명시도에 의해 @media조건과 상관없이 항상 우선순위가 높은 선택자에만 적용된다. 위에 같이 우선순위를 이용할 때에는 주의하여 코드를 작성해도 되지만 그렇지 않을 때는 위의 사항을 주의하면 작성해주어야한다.

@media를 작성하다보면, 코드의 길이가 너무길어져 특정 부분을 참고하기위해 css파일의 스크롤을 자주 위 아래로 움직여주어야하는데, 이를 개선할 방법으로는 편집기의 분할도 있겠지만, @media를 특정한 css파일로 따로 뺴주어 링크를 걸어줄 수 있다. 
<link rel="stylesheet" media="(max-width: 1024px)" href="css/main_medium.css">
같이 media속성으로 @media에서 추가해주었던 조건과 미디어 특성을 설정할 수 있다.
main.css의 코드를 줄일 수 있고, 따로 파일을 빼내어 작성했으므로 그 파일은 고유성도 가져(medium일 떄의 코드) 나중에 코드 분석 시에도 유리하다.

header .sign-group {
    display: block;
}
원래 flex값을 가지는 display를 수직구조로 바꾸기위하여 block으로 바꾸어 주었고, 이로인해 .sign-group의 구조가 변할것을 확인 할 수 있다.
이는 우리가 원래 order를 이용해 순서를 임의로 바꾸어주었고, 이 order는 display: flex일 때 적용할 수 있는 속성이다보니, block으로 바꾸어준 시점부터 적용되지 않아 원해의 구조로 돌아간것이다.

토글과 같이 on,off의 이벤트가 있을경우 스타일을 정의 할 떄, @media 쿼리 안에 스타일을 정의하는 코드들도 있지만 스타일의 정의는 왠만하면 @media쿼리 밖에 css파일에서 정의하는 편이 좋다.


<!-- main_small.css -->
/* Summary */
.summary__title {
    font-size: 34px !important;
}
small_device에서(모바일환경)는 전체적인 font-size를 줄여줄려고 하는데, 이를 담당하는 공통 부분이 .summary__title과 summary__description이다. 해당 부분을 같은 선택자 형식으로 주어 작성했지만, 일부 적용이되지 않는데, 이는 main.css에서 명시도값이 높은 부분이 존재하는것이므로 찾아보았더니, 
.section--visual .summary__title {
    color: #fff;
    font-size: 54px;
    text-shadow: 0 1px 1px rgba(0,0,0,.25), 
                 0 1px 25px rgba(0,0,0,.75);
}
.section--visual .summary__description {
    color: #fff;
    text-shadow: 0 1px 1px rgba(0,0,0,.25), 
                 0 1px 25px rgba(0,0,0,.75);
}
가 있기에, 해당 부분은 적용되지 않고 있다. 이를 해결해주기위에서 같은 형식으로 선택자를 추가해 덮어써주는 방법이 있겠지만, 이는 별로 좋은 방법이 아니므로 !important를 사용하였다.
!important는 해당 파일 내에서 가장 중요하다는 것으로 명시도 값에 상관없이 우선순위를 가장 높음을 의미한다. 따라서 font-size: 34px !important;부분은 이 속성만큼은 main_small.css파일 내에서 우선순위가 가장 높으므로 main.css와 상관없이 우선 적용되어 원하는 효과를 얻을 수 있다.

/* Google Map */
#map {
    width: auto;
    margin: 40px -20px 0 -20px;
}
모바일 환경에서는 가로너비가 작으므로 기존의 margin으로 양옆에 빈 공간을 만들어주었던 스타일을 넣어 줄 필요가 없다. 따라서 이를 없애주기위해 기존의 margin값에서 위아래는 유지하되 좌우를 없애고, width: 100%로 해주려고 생각을 했지만, 원하는 결과를 없지 못했다. 
margin: 40px 0 0 0; 과 width: 100%;로적용되면, .inner의 좌우 padding값 20px이 적용되어 양옆에 빈 공간이 그대로 남게된다. 
하지만 .inner의 양옆공간은 다른 요소들에게는 필요한 효과이므로 map부분만 없애주기위해서는 다른 방법이 필요하다. 이를위해 위의 코드처럼 margin에 원하는 좌우 공간으로 -20px를 넣으면 안쪽으로 공간이 들어오는것과 반대로 바깥쪽으로 20px밀어나므로 원하는 결과를 유도할 수 있다.
또 width: 100%로 고정하고 margin을 줄 경우에는 원하는 양 옆의 공간이 아닌 한쪽으로 치우쳐지는 문제가 발생하므로 width: auto;로 초기 상태로 바꿔주어야한다.
width의 %는 부모요소의 가로너비를 따르므로 만약 부모요소에 padding등 다른 값이 추가되어있다면 원한는 크기로 설정하는게 어려우므로 width: auto로 초기 상태로 만들어주어 진행하는 편이 수월하다.

footer .inner .site-links {
    float: none;
    display: block;
    text-align: center;
}
footer .inner .site-links li {
    display: inline;
}
footer의 site-links의 내용들이 float으로 적용되어있었지만 모바일 환경에서는 수평으로 보여지고 가운데 정렬로 바꿔주려고 한다. 이를 위해서 기존의 float을 none으로 바꿔주고, 처음에는 justify-content: center을 이용해 가운데 정렬을 유도하였으나, 특정 px에서는 원하는 효과를 얻었지만 계속적으로 축소를 하다보면 글씨와 크기의 형태가 깨지는 문제가 발생하는 것을 발견했다. 
따라서 해결방법으로 text의 정렬시 사용하는 text-aglin: center을 사용해주었고, 기존의 display: flex를 block으로 바꾸어 수직으로 나타내어 주었지만 여기서도 모든 링크텍스트가 수직으로 쌓이지는 문제가 발생했다. 따라서 links를 감싼는 틀은 block으로 주었고, 그 안에 내용들은 display: inline으로 바꾸어 수평으로 바꾸어주었다. inline은 안의 item의 크기에만 반응하므로 축소를 해주어도 일정한 틀을 유지해주어 형태가 깨지는 문제도 해결되었다. 
