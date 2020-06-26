---
title: "[jqxgrid]5.Grouping (자바스크립트 프레임워크,상용 그리드)"
date: 2019-03-26 13:20:18
categories:
- JS
- jqxgrid
---

### [](#Jqxgrid-Grouping "Jqxgrid Grouping")Jqxgrid Grouping

조회된 데이터들을 특정한 조건에 맞게 그룹화하여 보고 싶을때가 있습니다.  
데이터를 분석하는데 필수적인 기능 중 하나죠.  
엑셀에서는 이런 강력한 기능들이 잘 구현이 되어있습니다.  
jqxgrid도 못지 않게 훌륭한 기능을 가지고 있습니다.  
그럼 굳이 엑셀이 필요하지 않을 수도 있지 않을까요?  
적어도 조회(SELECT)를 하는 기능에서만큼요.

##### [](#Example "Example")Example

{% codeblock lang:javascript %}
$(document).ready(function () {  
// grouping 구현을 더 잘 보여드리기 위해 주소 정보를 간소화 시키고, 성별 컬럼을 추가하였습니다.  
var data = '\[{ "name": "홍길동", "age": "23", "address": "경기","phone": "010-1234-XXXX", "birthday": "1990-02-05","allowance": 5000, "gender":"남"}]';  

var source = {  
 datatype: "json",  
 datafields:[  
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

// 그룹화했을때 보여질 정보를 함수형태로 구현합니다.  
// 매개변수로 지정된 text,group,expanded,data는 console.log로 찍으면  
// 자세하게 살펴보실 수 있습니다.  
var groupsrenderer = function (text, group, expanded, data) {  
 var allowance\_sum; // 그룹했을때 용돈합계를 구해보도록 하겠습니다.  
 if (data.subItems.length > 0) {  
 // 그룹화된 데이터의 용돈 합계를 구해 allowance\_sum 변수에 넣어줍니다.  
 allowance\_sum = this.getcolumnaggregateddata('allowance',['sum'], true, data.subItems);  
 } else {  
 // rows 배열을 선언합니다.  
 // 만약 이 변수를 선언하지 않으면 두개 이상의 컬럼을 그룹화 했을때 디자인이 깨지는  
 // 버그가 발생합니다.  
 var rows = new Array();  
 var getRows = function (group, rows) {  
 if (group.subGroups.length > 0) {  
 for (var i = 0; i < group.subGroups.length; i++) {  
 // 각 그룹의 정보를 재귀함수 형태로 호출합니다.  
 // 최종 그룹에 도달할때까지 계속 호출합니다.  
 getRows(group.subGroups\[i], rows);  
 }  
 } else {  
 for (var k = 0; k < group.subItems.length; k++) {  
 //마지막 그룹에 도달했을때 해당 item(row)정보를 rows 배열에 넣습니다.  
 rows.push(group.subItems\[k]);  
 }  
 }  
 }  
 //최종적으로 getRows 함수를 다시한번 호출합니다.  
 getRows(data, rows);  
 // 위와같이 그룹화된 데이터의 용돈 합계를 구해 allowance\_sum 변수에 넣어줍니다.  
 allowance\_sum = this.getcolumnaggregateddata('allowance',['sum'], true, rows);  
 }  
 //그룹내에 row 수를 아이템 또는 그룹의 길이로 확인합니다.  
 var count = data.subItems.length || data.subGroups.length;  

 // 리턴할 결과를 html tag 형태로 보여줍니다.  
 return '<div style="margin-top:5px;"><span style="font-weight: bold; width:150px; display: inline-block;">'+text+'</span>'+  
 'Row수: <span style="width:10px; display: inline-block; text-align:right; margin-right:20px;">'\+ count+'</span>'+  
 '용돈합계: <span style="width:30px; display: inline-block; text-align:right; margin-right:20px;">'\+ allowance\_sum.sum+'</span></div>';  
}  


$("#jqxgrid").jqxGrid({  
 width: '100%',  
 height: '300',  
 source: dataAdapter,  
 sortable: true,  
 filterable: true,  
 showstatusbar: true,  
 columnsresize: true,  
 groupable: true, // 그룹핑을 사용하기 위해 groupable 속성을 true로 만들고  
 groupsrenderer: groupsrenderer,  //그룹정보를 렌더링하여 그룹집계를 Custom 할 수 있습니다.  
 //groupsrenderer는 상단처럼 함수형태로 구현해줍니다.  
 theme: 'energyblue',  
 columns:[  
 {text: '이름',datafield: 'name',width: "10%", align:"center"},  
 {text: '나이',datafield: 'age',width: "10%", align:"center"},  
 {text: '주소',datafield: 'address',width: "10%", align:"center"},  
 {text: '전화번호',datafield: 'phone',width: "20%", align:"center"},  
 {text: '생일',datafield: 'birthday',cellsformat: "yyyy-MM-dd",width: "20%", align:"center"},  
 {text: '용돈',datafield: 'allowance',cellsformat : 'd',cellsalign: 'right',width: "20%", align:"center"},  
 {text: '성별',datafield: 'gender',width: "10%", align:"center"}  
 ],  
 groups:['address','gender'] //처음 출력될때 주소와 성별을 미리 그룹핑합니다.  
});  
{% endcodeblock %}

##### [](#마치며… "마치며…")마치며…

groupsrenderer을 구현할때 Parameter로 쓰이는 group,data의 구조를  
정확하게 파악하지 못하면 해당 내용을 이해하기 어렵울 수 있습니다.  
저도 주석을 작성하는 과정에서 다시 한번 공부하게 되었네요.

만약 처음부터 여기까지 오셨다면 jqxgrid의 절반 이상은 알고 계신다고  
보셔도 될 것 같습니다. 더 다양하고 많은 기능들이 있지만  
핵심적인 기능들을 위주로 알아보았으니까요.

다음 시간에는 Row를 선택(select),클릭(click) 했을때 발생하는  
Event들에 대해 알아보도록 하겠습니다.
