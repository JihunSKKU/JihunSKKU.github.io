---
title: "Go Tutorial 1"
date: 2023-07-05
excerpt: "Go에 대해서 배워보자 1"
toc: true
toc_sticky: true
header:
  teaser: /assets/images/notebook.jpg

categories:
  - 학부연구생
tags:
  - Go
last_modified_at: 2023-07-05
---

# Go란 무엇인가?

Go는 구글에서 발명된 언어로 컴파일 언어라는 특징을 가지고 있다. 그래서 컴파일러의 컴파일 속도가 매우 빨라 인터프리터 언어처럼 사용할 수 있다.

- 인터프리터 : 코드를 한 줄씩 읽어 내려가며 실행하는 프로그램. MATLAB, Python 등이 있다.

자료형 체계에 있어 정적 타입(static type) 검사가 이루어지기 때문에 Python과 조금 다르다. 문법은 C++과 유사하다.

| Go                                   | Python            | C++               |
| :----------------------------------- | :---------------- | :---------------- |
| Statically typed                     | Dynamically typed | Statically typed  |
| Fast run time                        | Slow run time     | Fast run time     |
| Compiled                             | Interpreted       | Compiled          |
| Fast compile time                    | Interpreted       | Slow compile time |
| Supports concurrency(동시성)         | No support        | Supports          |
| Has automatic garbage collection     | Has               | Does not have     |
| Does not support classes and objects | Has               | Has               |
| Does not support inheritance(상속)   | Supports          | Supports          |

- Compiled : Runtime 전에 컴퓨터가 알아들을 수 있는 언어로 해석하는 방식 -> 실행시간이 더 빠름

- Interpret : Runtime 이후 Row 단위로 해석해 프로그램을 구동시키는 방식 -> 에러가 발견되면 즉시 중단 후 에러 보고

# Go Start

### hello.go

```go
package main
import ("fmt")

func main() {
    fmt.Println("Hello world")
}
```

위 프로그램을 실행파일로 만들기 위해서는 다음과 같은 명령어를 터미널에 입력한다.

```
go mod init example.com/hello
go build .\hello.go
```

# Go Syntax

Go 파일은 아래와 같은 파트로 구분된다.

- Package declaration(선언)
- Import package
- Functions
- Statements and expression

```go
1 package main
2 import ("fmt")
3
4 func main() {
5    fmt.Println("Hello world")
6 }
```

1행 : **[Package declaration]** Go에서 모든 프로그램은 패키지의 일부이다. 이 프로그램은 `main`패키지에 속한다.  
2행 : **[Import package]** `fmt`패키지에 포함된 파일들을 import한다.  
3행 : **[White space]** Go는 공백을 무시한다. (가독성을 위해 추가)  
4행 : **[Function]** 중괄호 안의 모든 코드가 실행된다.  
5행 : **[Statements]** `fmt`패키지에서 사용할 수 있는 출력 기능이다.

## Statement

- Go에서 명령문(statement)는 Enter 또는 `';'`로 구분된다.
- `'{'`는 줄의 시작 부분에 올 수 없다. (Error 뜸)

# Go Comments -> C++과 동일

한 줄 주석은 두 개의 슬래시 `'//'`로 시작한다.

```Go
// This is a comment
package main
import ("fmt")

func main() {
  // This is a comment
  fmt.Println("Hello World!")
}
```

여러 줄 주석은 `'/*'`로 시작해서 `'*/'`로 끝난다.

```Go
package main
import ("fmt")

func main() {
  /* The code below will print Hello World
  to the screen, and it is amazing */
  fmt.Println("Hello World!")
}
```

# Go Variables

## Data types

| Data types       | 설명          | 특징                                                        |
| :--------------- | :------------ | :---------------------------------------------------------- |
| int              | 정수          | 32 bit systems에서는 32 bit, 64 bit systems에서는 64 bit    |
| float32, float64 | 실수          | 32 bit : -3.4e+38 ~ 3.4e+38 / 64 bit : -1.7e+308 ~ 1.7e+308 |
| string           | 문자열        | 문자열 값은 `"`로 묶어야 한다.                              |
| bool             | True of False | 기본값은 `false`이다.                                       |

```Go
package main
import ("fmt")

func main() {
  var a bool = true     // Boolean
  var b int = 5         // Integer
  var c float32 = 3.14  // Floating point number
  var d string = "Hi!"  // String

  fmt.Println("Boolean: ", a)
  fmt.Println("Integer: ", b)
  fmt.Println("Float:   ", c)
  fmt.Println("String:  ", d)
}
```

## Declaring (Creating) Variables

1. With the `var` keyword

`var`키워드 다음에 변수 이름 및 유형을 선언

```Go
var variablename type = value
```

2. With the `:=` sign

`:=`기호 다음에 변수 값 사용

```Go
variablename := value
```

이 경우 변수의 유형은 값에서 유추된다.

마찬가지로 `var`다음 변수 유형을 선언하지 않더라도 컴파일러가 변수의 유형을 결정한다.

```Go
package main
import ("fmt")

func main() {
  var student1 string = "John" //type is string
  var student2 = "Jane" //type is inferred
  x := 2 //type is inferred

  fmt.Println(student1)
  fmt.Println(student2)
  fmt.Println(x)
}
```

## Declare Multiple Variables

Go에서는 한 줄에 여러 변수를 선언할 수 있다.

```Go
package main
import ("fmt")

func main() {
  var a, b, c, d int = 1, 3, 5, 7

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
  fmt.Println(d)
}
```

변수 유형 `type`을 지정하지 않으면 같은 줄에서 여러 유형의 변수를 선언할 수 있다.

```Go
package main
import ("fmt")

func main() {
  var a, b = 6, "Hello"
  c, d := 7, "World!"

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
  fmt.Println(d)
}
```

가독성을 위해 다음과 같이 하나의 블록으로 여러 변수 선언을 그룹화할 수도 있다.

```Go
package main
import ("fmt")

func main() {
   var (
     a int
     b int = 1
     c string = "hello"
   )

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
}
```

## Naming Rules

- 변수 이름은 문자 또는 underbar(`_`)로 시작해야 한다.
- 변수 이름은 숫자로 시작할 수 없다.
- 변수 이름에는 영숫자와 밑줄 (`a-z`, `A-Z`, `0-9`, `_`)만 사용할 수 있다.
- 변수 이름은 대소문자를 구문한다.
- 변수 이름에 공백을 포함할 수 없다.
- 변수 이름은 어떠한 Go keyword도 될 수 없다.

# Go Constants

변수가 변경할 수 없는 고정 값을 가져야 할 경우 `const`를 이용하여 변수를 "상수"로 선언한다. 이는 변수가 **변경 불가능하고 읽기 전용**임을 의미한다.

```Go
package main
import ("fmt")

const PI = 3.14

func main() {
  fmt.Println(PI)
}
```

마찬가지로 유형이 지정되지 않은 상수는 컴파일러가 값을 기준으로 상수 유형을 결정한다.

## Naming Rules

- 상수 이름은 변수와 동일한 규칙을 따른다.
- 상수 이름은 일반적으로 대문자로 작성된다.
- 상수는 함수 내부와 외부 모두에서 선언할 수 있다.

# Go Output

## Print() Function

```Go
package main
import ("fmt")

func main() {
  var i,j string = "Hello","World"

  fmt.Print(i)
  fmt.Print(j)
}
```

> HelloWorld

줄바꿈을 하기 위해서는 `\n`을 사용해야 한다.

```Go
package main
import ("fmt")

func main() {
  var i,j string = "Hello","World"

  fmt.Print(i, "\n")
  fmt.Print(j, "\n")
}
```

> Hello<br>World<br>

여러 변수를 하나의 함수에서 print하는 것도 가능하다.

```Go
package main
import ("fmt")

func main() {
  var i,j string = "Hello","World"

  fmt.Print(i, "\n",j)
}
```

> Hello<br>World<br>

**둘 다 문자열이 아닌** 경우 인수 사이에 공백을 삽입한다.

```Go
package main
import ("fmt")

func main() {
  var i,j = 10,20

  fmt.Print(i,j)
}
```

> 10 20

## Println() Function

`Print()`함수와 달리 인수 사이에 공백이 추가되고 끝에 줄 바꿈이 추가된다.

```Go
package main
import ("fmt")

func main() {
  var i,j string = "Hello","World"

  fmt.Println(i,j)
}
```

> Hello World

## Printf() Function

주어진 서식 동사를 기반으로 인수의 서식을 지정한 다음 print한다. (C++의 printf와 유사하다고 보면 된다.)

### General Formatting Verbs

| Verb  | Description                                      |
| :---- | :----------------------------------------------- |
| `%v`  | 인수의 **값**을 출력하는 데 사용된다.            |
| `%#v` | 위와 동일, 그러나 Go-syntax format으로 출력된다. |
| `%T`  | 인수의 **유형**을 출력하는 데 사용된다.          |
| `%%`  | `%` sign을 출력한다.                             |

```Go
package main
import ("fmt")

func main() {
  var i = 15.5
  var txt = "Hello World!"

  fmt.Printf("%v\n", i)
  fmt.Printf("%#v\n", i)
  fmt.Printf("%v%%\n", i)
  fmt.Printf("%T\n", i)

  fmt.Printf("%v\n", txt)
  fmt.Printf("%#v\n", txt)
  fmt.Printf("%T\n", txt)
}
```

> 15.5<br>
> 15.5<br>
> 15.5%<br>
> float64<br>
> Hello World!<br>
> "Hello World!"<br>
> string<br>

### Integer Formatting Verbs

| Verb | Description |
| :--- | :---------- |

| %b
