---
title: "[jqxgrid]2.Column Attributes(자바스크립트 프레임워크,상용 그리드)"
date: 2019-03-26 13:17:18
categories:
- JS
- jqxgrid
---

### [](#Jqxgrid-Attributes "Jqxgrid Attributes")Jqxgrid Attributes

jqxgrid에는 각 컬럼들에 여러가지 속성값들을 지정해 줄 수 있습니다.  
또한 grid 전체에 일괄 적용할 수 있는 속성값들도 존재합니다.  
전체적으로 json 형태의 구조를 띄고 있지만  
**CSS의 속성명 : 속성값** 처럼 생각하시면  
더 편하게 접근하실 수 있습니다.

##### [](#Example "Example")Example

{% codeblock lang:javascript %}
$(document).ready(function () {  
 //보시기 편하도록 데이터 셋을 한글로 변환하였습니다.  
var data = '[{  
 "name": "홍길동",  
 "age": 23,  
 "address": "서울 강남구",  
 "phone": "010-1234-XXXX",  
 "birthday": "1990-02-05",  
 "allowance": 5000  
 }]';  
 // prepare the data  
 var source = {  
 datatype: "json",  
 // datafields의 type은 'string', 'date', 'number', 'float',  
 // 'int' and 'bool' 로 지정할 수 있습니다.  
 datafields: [
 {  name: 'name',  type: 'string'  },  
 {  name: 'age',  type: 'int'  },  
 {  name: 'address',  type: 'string'  },  
 {  name: 'phone',  type: 'string'  },  
 {  name: 'birthday',  type: 'date'  },  
 {  name: 'allowance',  type: 'number'  }  
 ],  
 localdata: data  
 };  
 var dataAdapter = new $.jqx.dataAdapter(source);  
 $("#jqxgrid").jqxGrid({  
 width: '100%', // width 값은 가능하면 %로 적용하는 것이 좋습니다.  
 height: '300',  
 source: dataAdapter,  
 sortable: true, //정렬 기능을 사용할 것인지 T/F로 지정합니다.  
 filterable: true, //필터 기능을 사용할 것인지 T/F로 지정합니다.  
 showstatusbar: true, //하단 상태바를 사용할 것인지 T/F로 지정합니다.  
 //추후 Sum,Ave 등의 집계데이터를 표시할때 필요합니다.  
 columnsresize: true, //컬럼의 width 변경 여부를 T/F로 지정합니다.  
 theme: 'energyblue', // Grid의 테마를 지정할 수 있습니다.  
 // Default값은 metro 테마 입니다.  
 columns: [{  
 text: '이름',  
datafield: 'name',  
 width: "10%" // 마찬가지로 Width값은 %로 지정하는 것이 좋으며  
 // 총 Column의 width의 합이 100%이면 grid 전체 크기와 일치합니다.  
 },  
 {  
 text: '나이',  
 datafield: 'age',  
 width: "10%",  
 align: 'left' //컬럼 헤더의 정렬값을 지정합니다. 기본값은 left입니다.  
 },  
 {  
 text: '주소',  
 datafield: 'address',  
 width: "20%",  
 align: 'center'  
 },  
 {  
 text: '전화번호',  
 datafield: 'phone',  
 width: "20%",  
 align: 'right'  
 },  
 {  
 text: '생일',  
 datafield: 'birthday',  
 cellsformat: "yyyy-MM-dd", // 날짜 표시 형태를 지정합니다.  
 // cellsformat을 지정하지 않으면 미국식 표기로 나옵니다.  
 width: "20%"  
 },  
 {  
 text: '용돈',  
 datafield: 'allowance',  
 cellsformat : 'd', // 세자리 마다 콤마를 찍는 숫자 표기입니다.  
 //f+숫자 :float(소수점) , p : percent 등이 있습니다.  
 cellsalign: 'right', // cell 값의 위치를 지정할 수 있습니다. (left,right,center)  
 // default는 left 입니다.  
 width: "20%"  
 }  
 ]  
 });  
});  
{% endcodeblock %}

##### [](#마치며… "마치며…")마치며…

![](/images/jqxgrid_02_1.png)  
위와 같이 column의 헤더부분을 보시면  
헤더를 한번 클릭하면 오름차순 정렬, 두번클릭하면 내림차순 정렬,  
세번클릭 기본 상태로 돌아오는걸 확인할 수 있습니다.  
또한 각 컬럼의 너비를 자유롭게 변경 할 수 있으며,  
컬럼 헤더에 마우스 오버가 됐을때, 세줄표시를 클릭하면  
다양한 조건의 범위 검색을 할 수 있습니다.  
다만 셀의 형태에 따라 검색이 원활하지 않는 경우도 있습니다.  
(이런 경우엔 Database에서 처리하는 것이 좋습니다.)

다음시간에는 Sum, Ave 등의 집계 데이터 표시하는 방법을 알아보도록 하겠습니다.
