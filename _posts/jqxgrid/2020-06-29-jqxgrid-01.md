---
title: "[jqxgrid]1.기본구조 살펴보기(자바스크립트 프레임워크,상용 그리드)"
date: 2019-03-26 13:16:18
categories:
- JS
- jqxgrid
---

### [](#Jqxgrid-시작하기 "Jqxgrid 시작하기")Jqxgrid 시작하기

![](/images/pricing.png)  
해당링크를 통해 다운로드 받을 수 있습니다.  
[JqxWidget Download](https://www.jqwidgets.com/download/)  
Commercial 버전과 Non-Commercial 버전이 있는데  
기능에는 특별한 차이가 없으므로 Non-Commercial 기준으로 설명하겠습니다.

다운을 받으면 다음과 같은 디렉토리 구조를 볼 수 있습니다.  
![](/images/jqxgrid_01_1.png)  
각각의 필요한 위젯 또는 테마에따라 골라쓸 수 있지만 귀찮으므로

1.  jqwidgets -> jqx-all.js
2.  jqwidgets -> style -> jqx.base.css

이렇게만 Import를 하도록 하겠습니다.  
(단, 위젯을 일괄 추가 했으므로 프로그램은 다소 무거워 질 수 있다는  
단점을 가지고 있습니다.)

### [](#Jqxgrid-기본구조-살펴보기 "Jqxgrid 기본구조 살펴보기")Jqxgrid 기본구조 살펴보기

{% codeblock lang:javascript %}
$(document).ready(function () {  
 // json 형태의 data를 만들어 준다.  
 // grid 안에 셋팅될 값들이다.  
 var data = '[{  
 "CompanyName": "Alfreds Futterkiste",  
 "ContactName": "Maria Anders",  
 "ContactTitle": "Sales Representative",  
 "Address": "Obere Str. 57",  
 "City": "Berlin",  
 "Country": "Germany" }  
 ]';  

 // 데이터 타입, 필드, 셋팅할 데이터를 설정한다.  
 var source =  
 {  
 datatype: "json", // json 형태의 데이터를 셋팅할 것이고.  
 // 각필의 이름과 타입은 datafields에 마찬가지로 json 형태이다.  
 datafields: [  
 { name: 'CompanyName', type: 'string' },  
 { name: 'ContactName', type: 'string' },  
 { name: 'ContactTitle', type: 'string' },  
 { name: 'Address', type: 'string' },  
 { name: 'City', type: 'string' },  
 { name: 'Country', type: 'string' }  
 ],  
 localdata: data // 위에서 셋팅해놓은 data를 localdata에 담아준다.  
 };  
 // jqxgrid 프레임워크에서 만든 dataAdapter object를 생성하여  
 // 위에서 셋팅한 source의 정보를 넣어준다.  
 var dataAdapter = new $.jqx.dataAdapter(source);  

 // HTML 파일에 div의 id로 입력해놓은 jqxgrid에 dataAdapter의 정보를  
 // grid 형태로 출력한다.  
 $("#jqxgrid").jqxGrid(  
 {  
 // 이곳에 들어갈 수 있는 설정값들은 매우 다양하다.  
 // 나중에 조금 더 자세히 알아보기로 하자.  
 width: 850, //높이  
 source: dataAdapter, //위에서 만든 dataAdapter  
 columnsresize: true, //column의 너비를 컨텐츠에 맞게 리사이징  
 columns: [ // 각 컬럼값들의 대한 설정이다.  
 // 일반적으로 text,datafield는 필수적으로 설정하다.  
 // 그밖에 다양한 속성값들이 있으므로 이 또한 다음 시간에 알아보기로 한다.  
 { text: 'Company Name', datafield: 'CompanyName', width: 250 },  
 { text: 'Contact Name', datafield: 'ContactName', width: 150 },  
 { text: 'Contact Title', datafield: 'ContactTitle', width: 180 },  
 { text: 'City', datafield: 'City', width: 120 },  
 { text: 'Country', datafield: 'Country'}  
 ]  
 });  
});  
{% endcodeblock %}



##### [](#마치며… "마치며…")마치며…

함수 형태로 만들면 필요할때마다 호출할 수 있고,  
다양한 검색조건들에 맞게 데이터를 불러올 수도 있습니다.  
또한 jqxgrid가 자체적으로 가지고 있는 필터 및 검색 조건들도 이용할 수 있습니다.

기본 구조만 잘 이해하고 있으면 그 후에는 조금씩만 응용되는 형태이니  
어렵지 않게 사용할 수 있을 것으로 보입니다.

다음 시간에는 주석을 귀찮아서 쓰지 않은듯한 columns의 다양한 속성값들에  
대해 알아보도록 하겠습니다.
