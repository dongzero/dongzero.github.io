---
title: "지역변수와 전역변수_local, global"
categories: Pyhton
tag: [local, global]
toc: true
---

## 지역변수
<span style = "font-size:80%">
comment)
지역변수는 함수내에서 사용된 변수를 인용하여 출력하는 형태를 말한다
<span>

```python
gun = 10

def checkpoint(soldiers):
    gun = 20 #함수안에 20이라는 지역변수 선언
    gun = gun - soldiers
    print("함수 내 남은 총 : {0}".format(gun))

print("전체 총 : {0}".format(gun))
checkpoint(2)
print("남은 총 : {0}".format(gun))

#결과값
전체 총 : 10
함수 내 남은 총 : 18
남은 총 : 10
```
<span style = "font-size:70%">
위처럼 checkpoint라는 함수 안에서 선언한 gun=20자루에 대한 로직을 수행하여 18이라는
결과 값을 출력한다.
<span>



## 전역변수
<span style = "font-size:80%">
comment)
전역변수는 함수 외부에있는 변수를 인용하여 로직을 수행한다.
<span>

```python
from typing import _SpecialForm


gun = 10

def checkpoint(soldiers): # 경계근무
    global gun # 전역 공간에 있는 gun 사용
    gun = gun - soldiers
    
def checkpoint_ret(gun, soldiers):
    gun = gun - soldiers
    print("함수 내 남은 총 : {0}".format(gun))
    return gun
    



print("전체 총 : {0}".format(gun))
gun = checkpoint_ret(gun, 2)# 2명이 경계 근무 나감
print("남은 총 : {0}".format(gun)) # 외부로 총들고 나가고 남은 내부의 총의 개수

#결과값
전체 총 : 10
함수 내 남은 총 : 8
남은 총 : 8
```
<span style = "font-size:70%">
함수 선언전에 선언한 변수 gun=10을 인용하여 함수 로직이 수행되는걸 볼 수 있다.
함수내에 global(전역변수선언문) gun(외부에있는 변수)를 기입하여 전역변수를 사용하였다. 
<span>
