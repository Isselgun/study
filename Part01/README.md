# 변수와 상수, 변수와 상수 정리
#### 변수란 (==식별자) :
- 데이터(자료)를 담을 수 있는 공간(바구니)입니다.
- 값이 변경 가능한 (mutable)이라고 합니다.

#### 상수란 (==식별자) :
- 변하지 않는 데이터(자료)를 담을 수 있는 공간(바구니)입니다.
- 값이 변경 불가능한 (immutable)이라고 합니다.


#### 변수 선언 방법 : 
- 변수와 상수를 통틀어, 변수(저장된 데이터라는 관점에서)라고 일반적으로 부릅니다. 
- 변수의 이름은 소문자로 시작해야 합니다.
- 특수문자, 한자, 한글 등 사용가능 하지만, 관습적으로 잘 사용하지는 않습니다. 
```Swift
// 변수 선언방법
var a: Int = 3
var b = 7
// 상수 선언 방법
let c: Int = 1
let d = 2
```

#### 변수 여러개를 한번에 선언하는 방법 :
- 쉼표(,)를 사용합니다. 
```Swift
var x = 1, y = 2, z = 3
```

#### String Interpolation(스트링 인터폴레이션. ==문자열보간법) 사용법 :
- '\\(변수명)'을 사용합니다. 
```Swift
var name = "Rain"
print("저의 이름은 \(name)입니다.")
```

# Swift의 데이터 타입

#### 데이터 타입이란 :
- 데이터를 얼마 만큼의 크기, 그리고 어떤 형태로 저장할 것인지에 대한 약속을 하기 위해 사용 하는 것입니다.

#### 데이터 타입의 종류 :
1) Int : 정수 ⭐
2) Float : 실수. 6자리 소수점
3) Doiuble : 실수. 15자리 소수점 ⭐
4) Character : 문자
5) String : 문자열 ⭐
6) Bool : 참과 거짓 ⭐

#### 데이터 타입을 확인하는 방법 : 
- Opt를 누르고 변수명을 클릭하면 해당 변수의 타입을 확인할 수 있습니다.
- type(of: 변수명)을 사용하여 확인할 수 있습니다.
```Swift
let chr: Character = "1"
type(of: chr)     // Character.Type
```

# 타입주석/ 타입 추론 / 타입 안정성 / 타입 변환
#### 타입 주석이란 : 
- 변수를 선언하면서, 타입도 명확하게 지정하는 방식입니다. 
```Swift
var number: Int   // 변수를 선언 (타입 선언 ==타입주석)
number = 10       // 값을 저장 (초기화)
print(number)     // 값을 읽기
```

#### 타입 추론이란 : 
- 타입을 지정하지 않아도, 컴파일러가 타입을 유추해서(알아서 알맞는 타입으로 저장하는)방식을 의미합니다.
```Swift
var num1 = 2
type(of: num1)    // Int.Type
var num2 = 1.2
type(of: num2)    // Double.Type
var num3 = "Hello"
type(of: num3)    // String.Type
var num4 = true
type(of: num4)    //Bool.Type
```
#### 타입 안정성이란 : 
- Swift는 데이터 타입을 명확하게 구분하여 사용하는 언어입니다.
- Swift는 다른 타입끼리 계산할 수 없습니다.
```Swift
let num5 = 7
let num6 = 7.11
let result = num5 + num6    // 계산할 수 없다. 
```

#### 타입(형) 변환이란 :
- 변환할타입(변수명)형식으로 변환할수 있다.
- 타입컨버전이 실패했을 때 nil이 리턴될 수 있다. ⭐ 


# 타입 애일리어스 / 경고와 오류

#### 타입애일리어스(Type Alias)란? 
- 기존에 선언되어 있는 타입에 새로운 별칭을 붙여 코드 가독성을 높이는 문법입니다.
- typealias 별칭 = 타입명
```Swift
typealias Name = String
let name: Name = "홍길동"

typealias Something = (Int) -> String
func someFunction(completionHandler: Something)
```

#### 경교와 오류 표시 :
- ⚠️ 경교표시로 코드가 잘못된 것은 아니나 더 나은 방법을 제안하는 경우에 나타납니다. 
- 🛑 컴파일 오류 표시로 코드가 잘못되었음을 알려주며 반드시 수정해야합니다.


# 프로그래밍 관련 용어 정리 

#### 키워드란 : 
- Swift에서 특별한 의미로 사용하겠다고 미리 정해놓은 단어를 의미합니다.
```Swift
var
let
if
true
```

#### 리터럴(Literals)이란 ⭐ : 
- 코드에서 고정된 값으로 표현되는 문자(데이터) 그 자체를 의미합니다.
- Int Literals, Double Literals, String Literals, Character Literals, Bool Literals 등의 값 자체를 문법적으로 말하기 위해 쓰입니다. 
```Swift
"Rain"    // 문자열 리터럴
5         // Int 리터럴
5.12      // Double 리터럴
```

#### 식별자(Identifier)이란 : 
- 변수, 상수, 함수, 사용자 정의 타입의 이름을 의미합니다. 
```Swift
var name = "Rain"   // name을 식별자라 부릅니다. 
```

#### 토큰(Token)이란 : 
- 코드의 가장 작은 단위 : 코드에서 더이상 쪼갤 수 없는 최소의 단위나 의미의 단위를 의미합니다.
- 토큰 사이에 빈칸을 추가해서는 안됩니다.
```Swift
let
,
==
!=
```

#### 표현식(Expression)이란 ⭐ : 
- 값, 변수, 연산자의 조합으로 하나의 결과값으로 평가되는 코드 단위를 의미합니다.
```Swift
17
n
n + 7
n < 5
sayHelloString()    // return이 있는 함수의 경우만 해당됩니다.
```

#### 문장(Statement)이란 ⭐ : 
- 문장 또는 구문과 같이 특정작업을 실행하는 코드 단위를 의미합니다.

```Swift
var n = 5
print(n)
```

#### 밸류바인딩(Value Binding)이란?
- 바인딩이란 다른 변수/상수를 새로운 식별자로 할당하는 것을 의미합니다. 
```Swift
var a = 3
var b = a   // b에 a를 바인딩 한 것입니다. 
```


# 단축키

#### 자동 줄맞춤
- 컨트롤 i 
