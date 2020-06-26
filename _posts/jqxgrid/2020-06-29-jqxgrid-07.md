---
title: "[jqxgrid]7.Cell Edit/Validation (자바스크립트 프레임워크,상용 그리드)"
date: 2019-03-26 13:22:18
categories:
- JS
- jqxgrid
---

### [](#Jqxgrid-Cell-Edit-Validation "Jqxgrid Cell Edit/Validation")Jqxgrid Cell Edit/Validation

이전까지는 단순히 불러온 데이터를 가지고  
데이터를 처리하는 방법을 해봤다면  
지금부터는 불러온 데이터를 다양한 방법을  
수정하는 법을 알아보려고 합니다.

데이터를 수정할때 유효성 체크는 매우 중요합니다.  
다행히 jqxgrid 또한 cell을 수정할때 유효성을 체크하고  
입력값의 범위 등을 조절할 수 있습니다.

##### [](#Example "Example")Example

{% codeblock lang:javascript %}
$(document).ready(function () {  
var data = '[{ "name": "홍길동", "age": "23", "address": "경기","phone": "010-1234-XXXX", "birthday": "1990-02-05","allowance": 5000, "gender":"남"}]';  

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
 {text: '나이',datafield: 'age',width: "10%", align:"center",  
 //밸리데이션이라는 속성을 함수형태로 구현해줍니다.  
 validation: function (cell, value) {  
 if (value == "") return true; //공백값은 입력받아 줍니다.  
 if (value < 18) {  
 // 18세 미만이면 다음과 같은 메세지를 출력하며 입력을 불가하게 합니다.  
 return { result: false, message: "18세 미만은 부모님의 동의가 필요합니다." };  
 }  
 return true;  
 }},  
 {text: '주소',datafield: 'address',width: "10%", align:"center"},  
 {text: '전화번호',datafield: 'phone',width: "20%", align:"center"},  
 // cellsformat: "yyyy-MM-dd" 해당 포맷을 사용하는 경우 jqxwidget 내에 있는 globalization/globalize.js  
 // 파일을 include 해줘야 합니다. 그렇지 않으면 edit할때 버그가 발생합니다.  
 // 국가별로 날짜 표기하는 방법이 달라 발생하는 것으로 보여집니다.  
 {text: '생일',datafield: 'birthday',cellsformat: "yyyy-MM-dd",width: "20%", align:"center",  
 // columntype을 지정하면 해당 타입에 맞는 최적화된 eidtor 양식을 제공합니다.  
 // 예를들어 datetimeinput은 달력 picker를 호출해주고, dropdownlist는 html의 select 형태로 제공해줍니다.  
 columntype: 'datetimeinput'},  
 {text: '용돈',datafield: 'allowance',cellsformat : 'd',cellsalign: 'right',width: "20%", align:"center",columntype: 'numberinput',  
 validation: function (cell, value) {  
 if (value == "") return true;  
 if (value < 1000) {  
 return { result: false, message: "용돈은 1000원 이상 입력해야합니다." };  
 }  
 return true;  
 },  
 // editor에 입력조건,제한등을 설정할 수 있습니다.  
 createeditor: function (row, cellvalue, editor) {  
 //jqxNumberInput 이라는 위젯을 불러와 최대 입력자릿수를 6자리로 제한하였습니다.  
 // decimalDigits는 소숫점 제한 자리입니다.  
 editor.jqxNumberInput({ decimalDigits: 0, digits: 6 });  
 }},  
 {text: '성별',datafield: 'gender',width: "10%", align:"center", columntype: 'dropdownlist'}  
 ]  
 });  

});  
{% endcodeblock %}

##### [](#마치며… "마치며…")마치며…

edit 기능을 활성화하게 되면 수반되는 작업이 많이 발생합니다.  
수정된 데이터에 대한 유효성을 체크해야 될 뿐만 아니라  
여러가지 발생될 수 있는 버그 상황에도 대비해야 합니다.  
그리고 사용자로 하여금 형식에 맞는 데이터를 입력할 수 있도록  
유도해야 합니다.

하지만 잘만 만든다면 거의 엑셀과 다름 없는 정도의  
모습이 나올 것 같습니다.

다음 시간에는 columntype을 Button으로 지정하여  
Row을 추가/삭제 하는 방법을 알아보도록 하겠습니다.
