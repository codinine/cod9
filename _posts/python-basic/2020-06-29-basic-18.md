---
title: "[python-기초]18.표준모듈(2) - sys, os, urllib"
date: 2019-03-26 14:30:18
categories:
- Python
- 기초
---
#### [](#sys-모듈 "sys 모듈")sys 모듈

시스템과 관련된 정보를 가지고 있는 모듈입니다.

##### [](#Example "Example")Example

{% codeblock lang:python %}
import sys  
print(sys.argv)  
print(sys.copyright)  
print(sys.version)  
{% endcodeblock %}



##### [](#Result "Result")Result

{% codeblock %}
Copyright (c) 2001\-2017 Python Software Foundation.  
All Rights Reserved.  

Copyright (c) 2000 BeOpen.com.  
All Rights Reserved.  

Copyright (c) 1995\-2001 Corporation for National Research Initiatives.  
All Rights Reserved.  

Copyright (c) 1991\-1995 Stichting Mathematisch Centrum, Amsterdam.  
All Rights Reserved.  
3.6.4 (v3.6.4:d48eceb, Dec 19 2017, 06:54:40) [MSC v.1900 64 bit (AMD64)]
{% endcodeblock %}



이런저런 정보들이 나오는 것을 볼 수 있습니다.

* * *

#### [](#os-모듈 "os 모듈")os 모듈

운영체제와 관련된 정보를 가지고 있는 모듈입니다.

##### [](#Example-1 "Example")Example

{% codeblock lang:python %}
import os  
print(os.name)  
print(os.getcwd())  
print(os.listdir())  
{% endcodeblock %}



##### [](#Result-1 "Result")Result

{% codeblock %}
nt  
C:\Python\Doc\lefthand # 김왼손님 파이썬 강의를 듣다가 만든 폴더라 lefthand라고 되있네요.  
['emaxple.py', 'example2.py', 'example3.py', 'example4.py', 'example5.py', 'example6.py']  
{% endcodeblock %}



그 밖의 파일이나 폴더의 생성/제거 등의 함수들이 있는데  
이것들은 사용하지 않겠습니다. 직접 찾아보시고 테스트 해보시기 바랍니다.

* * *

#### [](#urllib-모듈 "urllib 모듈")urllib 모듈

url과 관련된 모듈입니다.  
웹 개발시 많이 사용될 모듈로 보여지네요.

##### [](#Example-2 "Example")Example

{% codeblock lang:python %}
from urllib import request  

target = request.urlopen("https://google.com")  
output = target.read()  

print(output)  
{% endcodeblock %}



##### [](#Result-2 "Result")Result

{% codeblock %}
b'<!doctype html><html itemscope="" itemtype="http://schema.org/WebPage"  
lang="ko"><head><meta content="text/html; charset=UTF-8" ...
{% endcodeblock %}


구글 메인페이지의 HTML 소스를 읽어와 버리네요.

##### [](#마치며… "마치며…")마치며…

왠지 많이 사용할 것 같지 않은 모듈들이지만 그래도 필요할때가 있겠죠?  
잘 기억하고 계시다가 필요할때 유용하게 사용하시기 바랍니다.

{% blockquote Hello Coding 파이썬, 윤인성 %}
해당 포스팅은 다음의 도서을 참고하여 작성되었습니다.
{% endblockquote %}
