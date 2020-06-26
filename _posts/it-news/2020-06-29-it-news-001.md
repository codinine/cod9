title: '[IT News] Bootstrap5 Release'
author: COD9
tags:
  - bootstrap5
categories:
  - IT Story
  - IT News
date: 2020-06-23 19:39:00
---
드디어 Bootstrap5가 릴리즈 되었습니다!  
봄이 가기 전 나올거라는 얘기와 달리 한 여름이 다되어서 나왔네요.

Bootstrap5의 가장 큰 변화로는 Jquery 의존성을 벗어났다는 것!
하지만 기존의 프로젝트는 여전히 Jquery를 많이 사용하기 있기 때문에  
Jquery가 적용된 프로젝트에서도 문제없이 사용될 수 있도록 설계되었다고 합니다.  

https://blog.getbootstrap.com/2020/06/16/bootstrap-5-alpha/  
해당 페이지에서 Bootstrap5의 릴리즈 소식을 확인할 수 있는데  
기분 좋아지는 올드팝 영상이 링크되어 있어  
고생했을 개발자들에게 해방감을 주는 것 같네요.

또 다른 변화는 익스플로러 지원을 중단했다는 것인데  
익스플로러의 점유율이 많이 줄어들기는 했지만  
크로스 브라우징이 중요한 프로젝트에서는 Bootstrap5의 도입을  
신중하게 결정해야겠네요.

메인화면에 로고도 새롭게 변경되었습니다.  
코드블럭으로 묶여있어 javascript 친화적인 느낌이 많이 드러난 것 같습니다.  

CSS에서는 변수를 사용할 수 있게되었습니다.  
```
.table {
  --bs-table-bg: #{$table-bg};
  --bs-table-accent-bg: transparent;
  --bs-table-striped-color: #{$table-striped-color};
  --bs-table-striped-bg: #{$table-striped-bg};
  --bs-table-active-color: #{$table-active-color};
  --bs-table-active-bg: #{$table-active-bg};
  --bs-table-hover-color: #{$table-hover-color};
  --bs-table-hover-bg: #{$table-hover-bg};

  // Styles here...
}
```
대략 이런 모양인데 $ 표시를 보니 Jquery의 느낌이 다시 살아나는듯도 하고  
뭔가 낯선 모습이네요.

색상 팔렛트도 대거 추가되었습니다.  
디자인이 어려운 개발자들에게는 완전 희소식이네요.  

자체적인 아이콘셋도 추가된 모양이네요.  
기존에는 fontawesome이나 glyphicon을 활용했었는데 아이콘도 깔끔하니 괜찮아 보입니다.  
원하는 아이콘들이 다 존재할지는 모르겠네요.  

여러 reference들도 추가되고 안정된 버전이 나오면  
사이드 프로젝트할때 도입을 시도해봐야겠습니다.
