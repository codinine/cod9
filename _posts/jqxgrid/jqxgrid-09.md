---
title: "[jqxgrid]9.Cellrender (자바스크립트 프레임워크,상용 그리드)"
date: 2019-03-26 13:24:18
categories:
- JS
- jqxgrid
---

### [](#Jqxgrid-Cellrender "Jqxgrid Cellrender")Jqxgrid Cellrender

jqxgrid를 더욱 적극적으로 활용을 하다보면  
cell 단위의 작업이 필요한 경우가 있습니다.  
cell 내부의 태그를 직접 컨트롤 하고 싶어지는 경우도 있고  
조건에 따라 스타일링(CSS)을 적용하고 싶을 수도 있습니다.

그 방법을 지금부터 알아보도록 하겠습니다.

##### [](#Example "Example")Example

{% codeblock lang:javascript %}

$(document).ready(function () {  
 // 실습을 위해 데이터 하나의 주소 정보를 삭제하였습니다.  
var data = '[{ "name": "홍길동", "age": "23", "address": "","phone": "010-1234-XXXX", "birthday": "1990-02-05","allowance": 5000, "gender":"남"}]';  

 var source = {  
 datatype: "json",  
 datafields: [  
 {name: 'name',type: 'string'},  
 {name: 'age',type: 'int'},  
 {name: 'address',type: 'string'},  
 {name: 'phone',type: 'string'},  
 {name: 'birthday',type: 'date'},  
 {name: 'allowance',type: 'number'},  
 {name: 'gender',type: 'string'}  
 ],  
 localdata: data  
 };  
 var dataAdapter = new $.jqx.dataAdapter(source);  

 // 아래 columns 에서 정의된 속성중 allowance 필드의  
 // cellclassname으로 정의되어 있습니다.  
 var allowupdown = function (row, columnfield, value) {  
 //용돈이 1만원 이하라면 class를 red로  
 //용돈이 2만원 이상라면 class를 yellow로  
 //그 밖에는 green으로 지정합니다.  
 if (value <= 10000) {  
 return 'red';  
 }  
 else if (value >= 20000) {  
 return 'yellow';  
 }  
 else return 'green';  
 }  

 // 아래 columns 에서 정의된 속성중 address 필드의  
 // cellsrenderer로 정의되어 있습니다.  
 var cellsrenderer = function (row, columnfield, value, defaulthtml, columnproperties) {  
 // 값이 없으면 주소를 입력하라 띄우고  
 // 그렇지 않으면 value 값을 보여줍니다.  
 if(value == ""){  
 return '<span style="margin: 4px; color: #f65757; font-weight:bold" >주소입력</span>';  
 }else{  
 return '<span style="margin: 4px; color: #000000; font-weight:bold" >'+value+'</span>';  
 }  
 }  


 $("#jqxgrid").jqxGrid({  
 width: '100%',  
 height: '300',  
 source: dataAdapter,  
 sortable: true,  
 filterable: true,  
 editable: true,  
 showstatusbar: true,  
 columnsresize: true,  
 theme: 'energyblue',  
 columns: [  
 {text: '이름',datafield: 'name',width: "10%", align:"center"},  
 {text: '나이',datafield: 'age',width: "10%", align:"center",validation: function (cell, value) {  
 if (value == "") return true;  
 if (value < 18) {  
 return { result: false, message: "18세 미만은 부모님의 동의가 필요합니다." };  
 }  
 return true;  
 }},  
 // cellsrenderer 속성을 지정합니다.  
 {text: '주소',datafield: 'address',width: "10%", align:"center", cellsrenderer : cellsrenderer},  
 {text: '전화번호',datafield: 'phone',width: "20%", align:"center"},  
 {text: '생일',datafield: 'birthday',cellsformat: "yyyy-MM-dd",width: "20%", align:"center",columntype: 'datetimeinput'},  
 // cellclassname 속성을 지정합니다.  
 {text: '용돈',datafield: 'allowance',cellsformat : 'd',cellsalign: 'right',width: "20%", align:"center",cellclassname : allowupdown},  
 {text: '성별',datafield: 'gender',width: "10%", align:"center", columntype: 'dropdownlist'}  
 ]  
 });  

});  
{% endcodeblock %}
##### [](#마치며… "마치며…")마치며…

실행 결과를 확인해보면 cellsrenderer의 속성이 적용된 주소 필드는  
텍스트의 디자인이 다른 필드의 모양에서 다소 벗어난 느낌이 듭니다.

차이를 확인하시라고 일부로 저렇게 두었는데요.  
cellsrenderer는 cell 내부의 형태 전체를 HTML tag 형태로 표현하도록  
되어있습니다.

그렇지만 cellclassname은 그저 cell의 class만을 지정하도록 되어있습니다.  
단순히 CSS를 통한 디자인의 변경만을 하신다면 cellclassname을  
cell 내부의 틀을 변경하고 싶다면 cellsrenderer를 사용하시면 됩니다.

다음시간에는 PHP를 통해 DB에서 데이터를 조회하여 dataset을 가져오는 방법을  
알아보도록 하겠습니다.
