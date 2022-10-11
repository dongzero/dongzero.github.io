---
title: "사전_dictionary"
categories: Pyhton
tag: dictionary
toc: true
---

## 사전(dictionary)

comment)
딕셔너리는 리스트나 튜플처럼 순차적으로 해당 요소값을 구하지않고
key를 통해 value를 얻는다.

```python
cabinet = {3:"노동영", 200:"유권영"}
print(cabinet[3])
print(cabinet[200])

# get = get을 이용하여 중간에 정보가 없어 오류표시를 하지않고 none로 표현후 다음으로 넘어감

print(cabinet.get(3))
print(cabinet.get(300))
print(cabinet.get(300, "사용가능"))
print("hi")

# in = 정보가 존재하는지 확인 여부

print(3 in cabinet) # true
print(23 in cabinet) # false

callable = {"a-3":"노동영", "b-23":"유권영"}
print(callable["a-3"])
print(callable["b-23"])

# 수정하여 추가
print(callable)
callable["a-3"] = "병선"
callable["c-1"] = "광대"
print(callable)

# 정보 삭제

del callable["a-3"]
print(callable)

# key 들만 출력

print(callable.keys())

# value 들만 출력

print(callable.values())

# key, value 전부 출력
print(callable.items())

# 도서관 폐점(모든정보 삭제)
callable.clear()
print(callable)
```
