---
title: "[python-기초]11.반복문-기본 (for, while)"
date: 2019-03-26 14:16:18
categories:
- Python
- 기초
---

### [](#파이썬-for-반복문 "파이썬 for 반복문")파이썬 for 반복문

#### [](#기본형태 "기본형태")기본형태

{% codeblock %}
for <반복자> in <반복할 수 있는 것>:  
 <실행할 문장>  

for <변수> in <리스트>:  
 <실행할 문장>  

for <변수> in <문자열>:  
 <실행할 문장>  

for <키 변수> in <딕셔너리>:  
 <실행할 문장>  

for <int형 변수> in range(시작범위,끝범위,간격):  
 <실행할 문장>  
{% endcodeblock %}

##### [](#Example "Example")Example

{% codeblock lang:python %}
list_a = [254,342,134,928,683]  
for var_a in list_a:  
 print(var_a)  

for var_b in "파자마코딩":  
 print(var_b)  

dict_a = {  
 "name" : "홍길동",  
 "age" : "27",  
 "address" : "서울 도봉구",  
 "phone" : "010-1234-XXXX",  
 "hobby" : ["축구","게임","독서"]  
 }  
for key in dict_a:  
 print(dict_a[key])  

for num in range(5):  
 print(num)  

for num in range(0,10,3):  
 print(str(num)+"번째 입니다.")  
{% endcodeblock %}



##### [](#Result "Result")Result

{% codeblock %}
254  
342  
134  
928  
683  
파  
자  
마  
코  
딩  
홍길동  
27  
서울 도봉구  
010-1234-XXXX  
['축구', '게임', '독서']  
0  
1  
2  
3  
4  
0번째 입니다.  
3번째 입니다.  
6번째 입니다.  
9번째 입니다.  
{% endcodeblock %}



* * *

#### [](#반복문-응용 "반복문 응용")반복문 응용

예제가 길어져서 2단계로 나누었습니다.

##### [](#Example-1 "Example")Example

{% codeblock lang:python %}
list_a = [254,342,134,928,683]  
for i in range(len(list_a)):  
 print(str(i)+"번째 값은 :"+str(list_a[i]))  

for i in reversed(range(len(list_a))):  
 print("거꾸로 출력 {}번째 값은 : {}".format(i,list_a[i]))  
{% endcodeblock %}



##### [](#Result-1 "Result")Result

{% codeblock %}
0번째 값은 :254  
1번째 값은 :342  
2번째 값은 :134  
3번째 값은 :928  
4번째 값은 :683  
거꾸로 출력 4번째 값은 : 683  
거꾸로 출력 3번째 값은 : 928  
거꾸로 출력 2번째 값은 : 134  
거꾸로 출력 1번째 값은 : 342  
거꾸로 출력 0번째 값은 : 254  
{% endcodeblock %}

reversed 함수까지 있어서 인덱스를 거꾸로 불러오는 것도  
쉽게 처리할 수가 있네요.

* * *

### [](#파이썬-while-반복문 "파이썬 while 반복문")파이썬 while 반복문

#### [](#기본형태-1 "기본형태")기본형태

{% codeblock %}
while <불 표현식>:  
 <실행할 문장>
{% endcodeblock %}

for는 범위를 지정하여 사용하는 반복문이라면  
while은 참 거짓을 반별하여 사용하는 반복문입니다.

두 반복문은 구현 방법이 비슷한 부분도 있지만  
상황에 따라 달리 쓰일 수 있습니다. 어떤 것이 적절한지는  
개발자의 판단에 따릅니다.

##### [](#Example-2 "Example")Example

{% codeblock lang:python %}
num = 1  
while num < 5:  
 print(num)  
 num += 1  

list_a = [1,2,3,4,2,2,4,5,1]  
target_value = 2  
while target_value in list_a:  
 list_a.remove(target_value) #리스트의 특정 값을 삭제합니다.  
print(list_a)
{% endcodeblock %}



##### [](#Result-2 "Result")Result

{% codeblock %}
1  
2  
3  
4  
[1, 3, 4, 4, 5, 1]  
{% endcodeblock %}

* * *

#### [](#무한루프 "무한루프")무한루프

##### [](#Example-3 "Example")Example

{% codeblock lang:python %}
while True:  
 print(".", end="")  

num = 0  
while True:  
 print(num)  
 num += 1  
 ip_text = input("> 종료하시겠습니까?(y): ")  
 if ip_text in ["y","Y"]:  
 print("반복을 종료합니다")  
 break  

nums = [6,13,15,34,8,1,99]  
for i in nums:  
 if i < 15:  
 continue # continue는 다음 반복으로 넘어갑니다. 건너뛰기라고 보면 됩니다.  
 print(i)  
{% endcodeblock %}


##### [](#Result-3 "Result")Result

{% codeblock %}
....................<무한루프>  
# 이런 경우에는 while 문장 안에 조건을 넣어 break로 탈출시켜줘야 합니다.  
0  
> 종료하시겠습니까?(y): a  
1  
> 종료하시겠습니까?(y): b  
2  
> 종료하시겠습니까?(y): y # y 또는 Y를 눌렀을때 종료  
반복을 종료합니다  

15  
34  
99
{% endcodeblock %}



##### [](#마치며… "마치며…")마치며…

조건문과 반복문은 프로그래밍에 있어 가장 기초적이며 가장 중요한  
문법입니다. 나중에 조금 더 깊이 다룰 수 있는 시간이 있었으면 좋겠습니다.

다음 시간에는 리스트와 딕셔너리를 반복문과 활용하여  
응용해서 사용할 수 있는 다양한 함수들을 살펴보도록 하겠습니다.

{% blockquote Hello Coding 파이썬, 윤인성 %}
해당 포스팅은 다음의 도서을 참고하여 작성되었습니다.
{% endblockquote %}
