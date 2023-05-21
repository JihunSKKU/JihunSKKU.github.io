---
title: "Markdown 문법"
date: 2023-05-21
excerpt: "여러가지 Markdown 문법에 대해 공부한 내용이다."
toc: true
toc_sticky: true
header:
  teaser: /assets/images/notebook.jpg

categories:
  - Blog
tags:
  - Blog
last_modified_at: 2023-05-21
---

## 1. 텍스트 줄바꿈

<br>
기본적인 텍스트 표기 방식이다.
마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번 표기해야 한다.

또는 enter를 2번 표기해야 한다.

다음과 같은 tag를 추가하면 추가 줄바꿈이 된다. \<br>

<br>

---

<br>

## 2. 텍스트 강조 표시

### 2.1. Italics

<pre>
*single asterisks* or _single underscore_
</pre>

_single asterisks_ or _single underscore_

<br>

### 2.2. Bold

<pre>
**double asteriskes** or __double underscores__
</pre>

**double asteriskes** or **double underscores**

<br>

### 2.3. Cancelline

<pre>
< s >strike tag< /s > or < del >delete tag< /del > or ~~double tilde~~
+ '< >'에 있는 띄어쓰기는 붙여야 한다 (표기상의 문제로 띄워두었음)
</pre>

<s>strike tag</s> or <del>delete tag</del> or ~~double tilde~~

<br>

### 2.4 Underbar

<pre>
< u >underbar tag< /u >
+ 마찬가지로 '< >'에 있는 띄어쓰기는 붙여야 한다 (표기상의 문제로 띄워두었음)
</pre>

<u>underbar tag</u>

<br>

---

<br>

## 3. 글머리 달기

<br>

<pre>
# Part (h1)

## Chapter (h2)

### Page-section (h3)

#### Sub-section (h4)

##### Sub-section unber sub-section (h5)

###### Paragraph (h6)
</pre>

# Part (h1)

## Chapter (h2)

### Page-section (h3)

#### Sub-section (h4)

##### Sub-section unber sub-section (h5)

###### Paragraph (h6)

<br>

---

<br>

## 4. 인용

인용문을 사용할때는 > 블럭 인용 문자를 사용하면, 단계별 깊이를 지원한다.

<pre>
> This is a blockqute.
</pre>

> This is a blockqute.

<br>

### 단계별 인용

<pre>
> This is a first blockqute.
>> This is a second blockqute.
>>> This is a third blockqute.
</pre>

> This is a first blockqute.
>
> > This is a second blockqute.
> >
> > > This is a third blockqute.

<br>

---

<br>

## 5. 목록

<br>

### 5.1. 정렬 목록

<pre>
1. 봄
2. 여름
3. 가을
4. 겨울
</pre>

1. 봄
2. 여름
3. 가을
4. 겨울

### 5.2. 비정렬 목록

<pre>
* 과자
    * 라면
        *사탕
</pre>

- 과자
  - 라면
    - 사탕

<br>

<pre>
- 과자
    - 라면
        -사탕
</pre>

- 과자
  - 라면
    - 사탕

<br>

---

<br>

## 6. 코드 인용

<br>

### pre tag 사용

<pre>
< pre >
< code >
class codeblock:
    def self.init(self):
        print('this is code block')
< /code >
< /pre >
</pre>

<pre>
<code>
class codeblock:
    def self.init(self):
        print('this is code block')
</code>
</pre>

<br>

### ''' 사용

<pre>
```
function test() {
  console.log("notice the blank line before this function?");
}
```
</pre>

```
function test() {
  console.log("notice the blank line before this function?");
}
```

<br>

### 6.1. Ruby

<pre>
```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```
</pre>

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

<br>

### 6.2. C

<pre>
```c
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  printf("Hello World!\n");
}
```
</pre>

```c
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  printf("Hello World!\n");
}
```

<br>

### 6.3. C++

<pre>
```cpp
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  cout << "Hello World! " << x << std::endl();
}
```
</pre>

```cpp
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  cout << "Hello World! " << x << std::endl();
}
```

### 6.4. Python

<pre>
```python
s = "Python syntax highlighting"
print s
```
</pre>

```python
s = "Python syntax highlighting"
print s
```

<br>

---

<br>

## 7. 수평선

<br>

아래는 모두 수평선을 만드는 여러가지 표기법들이다.

<pre>
* * *
***
*****
- - -
---
---------------------------
</pre>

<br>

---

<br>

## 8. 링크

<br>

### Insert link in text

<pre>
[Google](https://google.com)
</pre>

[Google](https://google.com)

<br>

### Insert link to link

<pre>
[Google](https://google.com "google homepage")
</pre>

[Google](https://google.com "google homepage")

<br>

### Reference link

<pre>
[Google link]: https://google.com
[Google][Google link]
</pre>

[Google link]: https://google.com

[Google][Google link]

<br>

### 주소를 직접 넣어도 가능하다.

<pre>
< https://google.com >
</pre>

<https://google.com>

<br>

## 9. 이미지 삽입

<br>

### Basic methods

<pre>
![Alt text](address -> local address or web address 모두 가능)
</pre>

### 가운데 정렬

<pre>
![Alt text](address){: .align-center}
</pre>

<br>

### Title 추가

<pre>
![Alt text](address "Title"){: .align-center}
</pre>

<br>

### Image tag

<pre>
< img src = "주소" width = "200px" height = "200px" title = "title" />
</pre>

<br>

## 10. 표 만들기

<br>

- 표 내용 중앙 정렬

<pre>
| 항목 | 가격 | 개수 |
|:---:|:----:|:----:|
| 비싼거 | 8000원 | 10개 |
| 싼거 | 900원 | 200개 |
</pre>

|  항목  |  가격  | 개수  |
| :----: | :----: | :---: |
| 비싼거 | 8000원 | 10개  |
|  싼거  | 900원  | 200개 |

<br>

- 표 내용 좌측 정렬 - 중앙 정렬 - 우측 정렬

<pre>
| 항목 | 가격 | 개수 |
|:----|:----:|----:|
| 비싼거 | 8000원 | 10개 |
| 싼거 | 900원 | 200개 |
</pre>

| 항목   |  가격  |  개수 |
| :----- | :----: | ----: |
| 비싼거 | 8000원 |  10개 |
| 싼거   | 900원  | 200개 |

<br>

<br>

### 출처

<https://devinlife.com/howto%20github%20pages/markdown-syntax/>
