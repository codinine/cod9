---
title: "[python-기초]13.함수(1) - 함수의 기본과 매개변수"
date: 2019-03-26 14:20:18
categories:
- Python
- 기초
---

#### [](#함수-기본-형태 "함수 기본 형태")함수 기본 형태

{% codeblock %}
def <함수이름>():  
 <실행할 문장>  

def <함수이름>('매개변수1','매개변수2',...):  
 <실행할 문장>  
{% endcodeblock %}

##### [](#Example "Example")Example

{% codeblock lang:python %}
def print_n_times(value,n):  
 for i in range(n):  
 print(value)  

print_n_times("파자마코딩",3)  
{% endcodeblock %}

##### [](#Result "Result")Result

{% codeblock %}
파자마코딩  
파자마코딩  
파자마코딩  
{% endcodeblock %}

매개변수가 필요한 함수의 경우, 필요한 매개변수의 갯수만큼 정확히  
입력하지 않으면 함수 호출 에러가 발생합니다.  
매개변수 갯수를 확정지을 수 없을 떈 `가변 매개변수`를 활용할 수 있습니다.

* * *

#### [](#가변-매개변수와-기본-매개변수 "가변 매개변수와 기본 매개변수")가변 매개변수와 기본 매개변수

1.  가변매개변수
    *   가변 매개변수 뒤에는 일반 매개변수를 사용할 수 없습니다.
    *   가변 매개변수는 한번만 사용 가능합니다.
2.  기본매개변수
    *   매개변수가 입력되지 않았을때 기본으로 값이 지정되는 매개변수
    *   기본 매개변수 뒤에는 일반 매개변수가 올 수 없다.

##### [](#Example-1 "Example")Example

{% codeblock lang:python %}
def print_n_times(n, *values):  
 for i in range(n):  
 for value in  values:  
 print(value)  

print_n_times(2,"안녕","즐거운","파자마코딩")  

def print_n_times_2(value, n=2):  
 for i in range(n):  
 print(value)  

print_n_times_2("파자마코딩")  
{% endcodeblock %}

##### [](#Result-1 "Result")Result

{% codeblock %}
안녕  
즐거운  
파자마코딩  
안녕  
즐거운  
파자마코딩  
---------  
파자마코딩  
파자마코딩  
{% endcodeblock %}



* * *

#### [](#키워드-매개변수 "키워드 매개변수")키워드 매개변수

원칙적으로 가변 매개변수와 기본 매개변수는 함께 쓸 수 없는데요.  
이를 가능하게 하는 것이 바로 `키워드 매개변수` 입니다.

##### [](#Example-2 "Example")Example

{% codeblock lang:python %}
def print_n_times(*values, n=2):  
 for i in range(n):  
 for value in  values:  
 print(value)  

print_n_times("안녕","만나서","반가워", n=3) #함수내에서 매개변수를 지정해주면 됩니다.  

def test(a,b=10,c=100):  
 print(a+b+c)  

test(10,20,30)  
test(a=10,b=100,c=200)  
test(c=10,a=100,b=200)  
test(10,c=200)
{% endcodeblock %}



##### [](#Result-2 "Result")Result

{% codeblock %}
안녕  
만나서  
반가워  
안녕  
만나서  
반가워  
안녕  
만나서  
반가워  
60  
310  
310  
220
{% endcodeblock %}


##### [](#마치며… "마치며…")마치며…

파이썬 함수의 기본틀과 다양한 매개변수 입력방법에 대해서 알아봤습니다.  
다음 시간에는 재귀함수와 리턴값에 대해 알아보도록 하겠습니다.

{% blockquote Hello Coding 파이썬, 윤인성 %}
해당 포스팅은 다음의 도서을 참고하여 작성되었습니다.
{% endblockquote %}
