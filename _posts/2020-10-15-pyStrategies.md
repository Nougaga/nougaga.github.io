---
layout: post
categories: blog
date: 2020-10-15
title: '[python] Speed Performance를 위한 코드 전략'
---

* [https://wiki.python.org/moin/PythonSpeed/PerformanceTips](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)

의 일부 내용을 메모

---

### 문자열을 연결할 때
<br>
'+' 연산을 이용하는 것은 되게 비효율적이에요. 이거 대신
```
s = ""
for elt in somelist:
    s += some_function(elt)
```

이렇게 써요
```
slist = [some_function(elt) for elt in somelist]
s = "".join(slist)
```
<br>
이거 대신

```
out = "<html>" + head + prologue + query + tail + "</html>"
```
이렇게 써요
```
out = "<html>%s%s%s%s</html>" % (head, prologue, query, tail)
out = "<html>%(head)s%(prologue)s%(query)s%(tail)s</html>" % locals()
```
<br>

### Loops를 이용할 때
<br>

이거 대신
```
newlist = []
for word in oldlist:
    newlist.append(word.upper())
```

map()을 이용해요. 정말 빨라요!
```
newlist = map(str.upper, oldlist)
```
Loops 안에서 '.'로 무언가를 호출시키게 되면 되게 비효율적이에요. 차라리 이렇게 써요.
```
upper = str.upper
newlist = []
append = newlist.append
for word in oldlist:
    append(upper(word))
```
변수 선언도 local에서 해주면 global에서 선언해서 쓰는 것보다 더 효과적이에요.
```
def func():
    upper = str.upper
    newlist = []
    append = newlist.append
    for word in oldlist:
        append(upper(word))
    return newlist
```
<br>

### dict()에 새로운 key로 initializing이 필요하다면

<br>

if문은 굉장히 비효율적이에요. 이거 대신
```
wdict = {}
for word in words:
    if word not in wdict:
        wdict[word] = 0
    wdict[word] += 1
```
오류를 피하기 위해서라면 차라리 try/except를 써요.
```
wdict = {}
for word in words:
    try:
        wdict[word] += 1
    except KeyError:
        wdict[word] = 1
```
또는, get() 메서드를 써요.
```
wdict = {}
get = wdict.get
for word in words:
    wdict[word] = get(word, 0) + 1
```
dict()의 value가 list형이라면 setdefault() 메서드를 이용해요.
```
wdict.setdefault(key, []).append(new_element)
```
collections 모듈에 이럴 때 쓰기 좋은 적절한 메서드도 있어요.
```
from collections import defaultdict
wdict = defaultdict(int)
for word in words:
    wdict[word] += 1
```
<br>


### 그 외

- import는 특정 func을 딱 한 번이나 0번 실행시키는 경우 아니면 그냥 global에서. 괜히 local로 해서 여러 번 import 되느라 시간걸리나 global에서 딱 한번 되나 이후로도 그 모듈을 계속 쓸 수 있는건 같다.

- loop 안에 function 넣고 싶다면 function에 loop 넣는 것이 낫다. function call 횟수를 줄이자.

- python은 C가 아니다. 놀랍게도 x+x가 **x*2나 x\<\<1보다 빠르다.** 와ㅋㅋㅋㅋ

- function 안에 if를 넣는 것보다 특정 조건 이후 function을 다시 쓰는 것(re-mapping)이 더 좋을 수도 있다. 이 정도로 if는 굉장히 비효율적이므로 될 수 있으면 피하자.

