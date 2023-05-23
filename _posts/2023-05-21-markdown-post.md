---
title: "Markdown 문법"
date: 2023-05-21
excerpt: "여러가지 Markdown 문법에 대한 내용이다."
toc: true
toc_sticky: true
header:
  teaser: /assets/images/notebook.jpg

categories:
  - Blog
tags:
  - Blog
last_modified_at: 2023-05-23
---

## 1. 텍스트 줄바꿈

기본적인 텍스트 표기 방식이다.
마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번 표기해야 한다.

또는 enter를 2번 표기해야 한다.

다음과 같은 tag를 추가하면 추가 줄바꿈이 된다. \<br>

<br>

## 2. 텍스트 강조 표시

### 2.1. Italics

    *single asterisks* or _single underscore_

_single asterisks_ or _single underscore_

### 2.2. Bold

    **double asteriskes** or __double underscores__

**double asteriskes** or **double underscores**

### 2.3. Cancelline

    <s>strike tag</s> or <del>delete tag</del> or ~~double tilde~~

<s>strike tag</s> or <del>delete tag</del> or ~~double tilde~~

### 2.4 Underbar

    <u>underbar tag</u>

<u>underbar tag</u>

<br>

## 3. 글머리 달기

    # Part (h1)
    ## Chapter (h2)
    ### Page-section (h3)
    #### Sub-section (h4)
    ##### Sub-section unber sub-section (h5)
    ###### Paragraph (h6)

# Part (h1)

## Chapter (h2)

### Page-section (h3)

#### Sub-section (h4)

##### Sub-section unber sub-section (h5)

###### Paragraph (h6)

<br>

## 4. 인용

인용문을 사용할때는 > 블럭 인용 문자를 사용하면, 단계별 깊이를 지원한다.

    > This is a blockqute.

> This is a blockqute.

### 단계별 인용

    > This is a first blockqute.
    >> This is a second blockqute.
    >>> This is a third blockqute.

> This is a first blockqute.
>
> > This is a second blockqute.
> >
> > > This is a third blockqute.

<br>

## 5. 목록

### 5.1. 정렬 목록

    1. 봄
    2. 여름
    3. 가을
    4. 겨울

1. 봄
2. 여름
3. 가을
4. 겨울

### 5.2. 비정렬 목록

    * 과자
        * 라면
            *사탕

- 과자
  - 라면
    - 사탕

<pre>
- 과자
    - 라면
        -사탕
</pre>

- 과자
  - 라면
    - 사탕

<br>

## 6. 코드 인용

### pre tag 사용

    < pre >
    < code >
    class codeblock:
        def self.init(self):
            print('this is code block')
    < /code >
    < /pre >

<pre>
<code>
class codeblock:
    def self.init(self):
        print('this is code block')
</code>
</pre>

### ''' 사용

    ```
    function test() {
      console.log("notice the blank line before this function?");
    }
    ```

```
function test() {
  console.log("notice the blank line before this function?");
}
```

### 6.1. Ruby

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

### 6.2. C

    ```c
    int main() {
      int y = SOME_MACRO_REFERENCE;
      int x = 5 + 6;
      printf("Hello World!\n");
    }
    ```

```c
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  printf("Hello World!\n");
}
```

### 6.3. C++

    ```cpp
    int main() {
      int y = SOME_MACRO_REFERENCE;
      int x = 5 + 6;
      cout << "Hello World! " << x << std::endl();
    }
    ```

```cpp
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  cout << "Hello World! " << x << std::endl();
}
```

### 6.4. Python

    ```python
    s = "Python syntax highlighting"
    print s
    ```

```python
s = "Python syntax highlighting"
print s
```

<br>

## 7. 수평선

아래는 모두 수평선을 만드는 여러가지 표기법들이다.

    * * *
    ***
    *****
    - - -
    ---
    ---------------------------

<br>

## 8. 링크

### Insert link in text

    [Google](https://google.com)

[Google](https://google.com)

### Insert link to link

    [Google](https://google.com "google homepage")

[Google](https://google.com "google homepage")

### Reference link

    [Google link]: https://google.com
    [Google][Google link]

[Google link]: https://google.com

[Google][Google link]

### 주소를 직접 넣어도 가능하다.

    <https://google.com>

<https://google.com>

<br>

## 9. 이미지 삽입

### Basic methods

    ![Alt text](address -> local address or web address 모두 가능)

### 가운데 정렬

    ![Alt text](address){: .align-center}

### Title 추가

    ![Alt text](address "Title"){: .align-center}

### Image tag

    < img src = "주소" width = "200px" height = "200px" title = "title" />

<br>

## 10. 표 만들기

- 표 내용 중앙 정렬
<pre>
|  항목  |  가격  | 개수  |
| :----: | :----: | :---: |
| 비싼거 | 8000원 | 10개  |
|  싼거  | 900원  | 200개 |
</pre>

|  항목  |  가격  | 개수  |
| :----: | :----: | :---: |
| 비싼거 | 8000원 | 10개  |
|  싼거  | 900원  | 200개 |

- 표 내용 좌측 정렬 - 중앙 정렬 - 우측 정렬
<pre>
| 항목   |  가격  |  개수 |
| :----- | :----: | ----: |
| 비싼거 | 8000원 |  10개 |
| 싼거   | 900원  | 200개 |
</pre>

| 항목   |  가격  |  개수 |
| :----- | :----: | ----: |
| 비싼거 | 8000원 |  10개 |
| 싼거   | 900원  | 200개 |

<br>

## 출처

<https://devinlife.com/howto%20github%20pages/markdown-syntax/>
