---
title: "[python-기초]15.튜플"
date: 2019-03-26 14:24:18
categories:
- Python
- 기초
---

### [](#파이썬-튜플 "파이썬 튜플")파이썬 튜플

튜플은 리스트와 비슷하지만 리스트와 다른 점은  
한번 결정된 요소를 바꿀 수 없다는 것입니다.  

{% codeblock %}
<튜플명> = (<식별자>,...)  
{% endcodeblock %}



##### [](#Example "Example")Example

{% codeblock lang:python %}
tuple_a = (10,20,30)  
for i in tuple_a:  
 print(tuple_a[i])  
tuple_a[0] = 20
{% endcodeblock %}



#요소를 하나만 가지는 튜플  
tuple_b = (20, ) # 쉼표가 없으면 튜플이 아니라  
 # 숫자형에 괄호를 친것으로 인식합니다.  

##### [](#Result "Result")Result

{% codeblock %}
10  
20  
30  
TypeError: 'tuple' object does not support item assignment  
{% endcodeblock %}

* * *

#### [](#리스트와-튜플의-다른-형태 "리스트와 튜플의 다른 형태")리스트와 튜플의 다른 형태

##### [](#Example-1 "Example")Example

{% codeblock lang:python %}
#각각의 변수를 선언하여 값을 할당  
[a, b] = [10, 20]  
(c, d) = (30, 40)  
print("a:{} b:{} c:{} d:{}".format(a,b,c,d))  

#괄호 없는 튜플  
tuple_a = 10, 20, 30, 40  
print(tuple_a)  
print(type(tuple_a))  
a, b, c = 9, 8, 7  
print("a:{} b:{} c:{}".format(a,b,c))  
{% endcodeblock %}


##### [](#Result-1 "Result")Result

{% codeblock %}
a:10 b:20 c:30 d:40  

(10, 20, 30, 40)  
<class 'tuple'>  
a:9 b:8 c:7  
{% endcodeblock %}


* * *

#### [](#여러개의-값-리턴 "여러개의 값 리턴")여러개의 값 리턴

##### [](#Example-2 "Example")Example

{% codeblock lang:python %}
def test():  
 return (10,20,30)  
a,b,c = test()  
print("a:{} b:{} c:{}".format(a,b,c))  
{% endcodeblock %}


##### [](#Result-2 "Result")Result

{% codeblock %}
a:10 b:20 c:30  
{% endcodeblock %}


##### [](#마치며… "마치며…")마치며…

튜플은 값을 변경할 수 없기 떄문에 초기에 기준 값을 설정하거나  
상수의 형태로 많이 이용할 것으로 보입니다.  
`머신러닝`에서도 많이 쓰인다고 하니 나중에 다시 볼 수 있겠죠?  
이젠 파이썬의 좀 더 깊이 있는 부분을 공부할 차례입니다.

{% blockquote Hello Coding 파이썬, 윤인성 %}
해당 포스팅은 다음의 도서을 참고하여 작성되었습니다.
{% endblockquote %}
