---
title: "continue와 break"
categories: Pyhton
tag: [continue, break]
toc: true
---

## continue와 break
<span style = "font-size:80%">
comment)
continue는 반복문을 수행중 특정조건에따라 수동적으로 다음문법으로
넘겨줄수있다
break는 마찬가지로 반복문 수행중 수동적으로 로직을 멈추게 할 수있다
<span>

```python
absent = [2, 5] # 결석
no_book = [7] # 책을 깜빡함
for student in range(1,11): # 1~11번 까지 학생존재
    if student in absent: # student이 absent(결석) 을 했다면!
        continue # 다음으로 넘어가고
    elif student in no_book: # student가 만약 no_book(책)을 안가져 왔다면
        print("오늘 수업 여기까지. {0}는 교무실로 따라와".format(student))
        break # 수업을 마치고 교무실로 부르겠다
    print("{0} 책 읽어봐".format(student))
```
<span style = "font-size:70%">
continue = 이슈가 발생하여도 상관없이 다음 문장으로 넘어감
break = 이슈가 발생하면 반복문을 멈추고 탈출

선생님의 수업과정을 코드로 작성해보았다

수업중에 absent(2,5) 학생이 결석했다면 그냥 수업을 진행하고
no_book(7)학생이 책을 안가져왔다면 수업을 마친다
만약 책을 가져왔다면 책을 읽도록한다.
<span> 