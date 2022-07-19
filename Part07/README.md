# 함수의 기본 개념
#### 함수란 : 
- 어떤 기능을 하는 코드의 모음을 의미합니다. 반복적인 것을 함수로 정의하여 쉽게 사용할 수 있습니다. 
- 함수는 정의문과 실행문 두단계로 사용할 수 있습니다.  
```Swift
// 1단계 정의
func doSomething() {      // func 함수명()
  // 실행할 코드           // 반복적으로 사용할 것을 문장으로 작성합니다. 
}

// 2단계 호출(또는 실행)
doSomething()             // 함수명() 으로 실행합니다. 
```

#### 함수의 형태 : 
- 단순하게 반복할 코드를 함수로 정의하여 사용할 수 있습니다. 
```Swift
func sringRepeat() {      
  print("반복1")
  print("반복2")  
  print("반복3")
  print("반복4")
}
```
- 함수의 인풋(==파라미터⭐==매개변수==인자)을 정의해 사용할 수 있습니다. 이때 파라미터의 타입을 꼭 정의해야합니다.
```Swift
func saySomething(name: Strig) {   // 파라미터의 이름과 타입을 정의 해야합니다. 
  print("안녕하세요\(name)님")        // 파라미터의 이름을 name으로 정했다면 name으로 사용해야합니다. 
}

saySomething(name: "Rain")        // 파라미터에 넣은 값인 "Rain"은 인수(==아규먼트⭐)라고 합니다. 
```
- 함수의 아웃풋을 정의해 사용할 수 있습니다. -> 타입명을 사용하며 이때 return을 꼭 사용해 정의해야합니다.
```Swift
func syeHello() -> String {
  return "아웃풋입니다"
}
```


- 함수의 인풋과 아웃풋을 모두 정의해 사용할 수 있습니다. 인풋은 여러타입이 들어갈 수 있으나 아웃풋은 하나의 타입만 나올수 있습니다. ⭐
```Swift
func plusFuntion(a: Int, b: Int) -> Int {
    let c = a + b
    return c       
}
```

- 리턴 타입이 없는 함수는 실제로 -> Void타입 으로 보통 ->()가 생략됩니다.   ?????
```Swift
var hello: Void = sayhello1()   // 리턴이 없지만 Void타입이 리턴됨으로 변수에 Void으로 담을 수 있습니다.
                                // 하지만 이렇게 사용하는 경우는 없습니다 ㅎㅎ 
```
     
 

# 함수의 응용
#### 아규먼트 레이블 이란 : 
- 일반적으로 함수를 사용할때 더 명확하게 무엇을 요구하는 지 알려주고 간단하게 사용하기 위해 사용합니다. 
- 함수명(아규먼트레이블 파라미터: 아규먼트) 형식으로 사용합니다. 
```Swift
func someFunction1(writeYourFirstNumber a:Int, writeYourSecondNumber b: Int) {
    print(a + b)
}

someFunction1(writeYourFirstNumber: 3, writeYourSecondNumber: 4) //아규먼트 레이블: 값
```
- 와일드 카드 패턴을 사용하여 아규먼트 레이블을 생략해서 사용할 수 있습니다. 
함수를 명확하게 알고 있을때 빠르고 쉽게 사용하기 위해 사용합니다. 
```Swift
func addPrintFunction(_ firstNum: Int, _ secondNum: Int) {
    print(firstNum + secondNum)
}

addPrintFunction(1, 2)
```

#### 가변 파라미터 : 
- 파라미터의 타입에 ...을 이용하여 가변 파라미터로 선언 할 수 있습니다. 
- 가변파라미터는 아래의 내용을 지켜서 사용해야합니다.
> 1) 아규먼트는 배열형태로 전달됩니다. 
> 2) 가변 파라미터는 개별함수마다 하나씩만 선언할 수 있습니다.
> 3) 가변 파라미터는 기본값을 가질 수 없다.

```Swift
func arithmeticAverage(_ numbers: Double...) -> Double {
// 타입 Double 뒤에 점 3개를 붙인것이 가변 파라미터 입니다.
    var total = 0.0
    for n in numbers {
        total += n
    }
    return total / Double(numbers.count)
}

arithmeticAverage(1.5, 2.5, 3.5, 4.5) 
// 배열 형태로 여러개를 작성해도 되며 1개를 써도 됩니다.
```

#### 함수의 기본값 설정 : 
- 함수에 기본값을 설정하여 일부의 아규먼트를 생략하더라도 사용할 수 있습니다.
```Swift
func numFunction(num1: Int, num2: Int = 5) -> Int {
// num2의 데이터 타입은 정수임으로 기본값으로 정수를 넣습니다.
// 함수 실행할 때 숫자 주지 않으면 5를 쓰겠다는 의미입니다.
    var result = num1 + num2
    return result
}

numFunction(num1: 3)
// 기본값을 num2: 5를 사용하여 return 8 이 됩니다.
numFunction(num1: 3, num2: 7)
// 기본값을 설정하였더라도 사용하지 않고도 사용이 가능합니다. 
```

# 함수 사용시 주의점 
#### 함수 파라미터에 대한 정확한 이해 :
- 파라미터는 상수로 선언이 되기 때문에 변경 할 수 없습니다. 
```Swift
func someAdd(a: Int) -> Int {            // let a: Int 
    a = a + 1
    // a는 파라미터이기 때문에 변경이 불가능 합니다.
    // 내부에서 값을 바꾸고 싶다면, 내부에서 새로운 변수 선언해야 합니다.
    return a
}
```

#### 함수내에서 선언한 변수의 Scope(스코프)
- 함수내에서 선언한 변수는 함수 내에서만 사용할 수 있습니다.
```Swift
func sumOfNum(a: Int) -> Int {
    var sum = 0
    sum += a
    return sum
}

sum
// 함수내에서 선언한 함수임으로 사용이 불가능합니다.

sumOfNum(a: 3)
```

#### return 키워드의 정확한 이해 :
 - 1) 리턴타입이 있는 함수의 경우(아웃풋이 있는 경우):
      리턴 키워드 다음의 표현식을 평가한 다음에 그 결과를 리턴하면서 함수를 벗어날때 사용합니다.
 - 2) 리턴타입이 없는 함수의 경우(아웃풋이 없는 경우):
      함수의 실행을 중지하고 함수를 벗어날때 사용합니다. ⭐️
      
#### 리턴타입이 있는 경우, 함수의 실행문의 의미 : 
- 리턴 타입이 있는 함수를 호출하는 것은 표현식(표현식의 결과는 함수가 리턴하는 값)을 호출한 것이라는 것을 인지 해야합니다.
> 표현식 : 값, 변수, 연산자의 조합으로 하나의 결과값으로 평가되는 코드 단위를 의미합니다. 
```Swift
if nameString() == "스티브" {
// 함수가 리턴되어 하나의 결과값으로 사용됩니다. 
    print("이름이 일치합니다.")
}
```

#### 함수의 중첩 사용(Nested Functions) :
- 함수 안에 함수를 작성할 수도 있다. 단, 함수 안에 있는 함수는 밖에서 사용이 불가능합니다. 
- 여러개의 함수를 중첩 사용하여 함수를 제한적으로 사용하고 싶을 때 사용합니다.
```Swift
func chooseStepFunction(backward: Bool, value: Int) -> Int {
    
    func stepForward(input: Int) -> Int {
        return input + 1
    }
    
    func stepBackward(input: Int) -> Int {
        return input - 1
    }
    if backward {
        return stepBackward(input: value)
    } else {
        return stepForward(input: value)
    }
    
}

stepForward(input: 5)
// 함수 안에 있는 함수이기 때문에 사용이 불가능!! 
```


# 함수의 표기법(지칭) / 함수의 타입 표기  
#### 함수를 지칭 하는 방법 : 
- 함수를 지칭하려는 경우 함수명(파라미터명:파라미터명:)으로 표기하여 사용합니다.
- 파라미터가 없는 경우
```Swift
doSomething
```
- 아규먼트 레이블이 있는 경우
```Swift
numberPrint(n:)
// 함수명(아규먼트레이블:)로 작성합니다. 
```
- 파라미터가 여러개인 경우
```Swift
chooseStepFunction(backward:value:)
// 함수명(파라미터명:파라미터명:) 이때 , 쉼표를 꼭 빼서 지칭합니다.
```
- 아규먼트 레이블이 생략된 경우는 아래와 같이 표기합니다. 
```Swift
addPrintFunction(_:_:)
```
- 섞어서 써져있는 경우 
```Swift
func addPrintFunction(firstNum: Int, _ secondNum: Int, ex rraan: Int) {
    print(firstNum + secondNum + rraan)
}

let rain = addPrintFunction(firstNum:_:ex:)
// 파라미터:와일드카드:아규먼트레이블: 섞어서 사용가능하며 지칭도 가능합니다.
```

#### 함수의 타입 표기 : 
- 함수도 타입 표기를 할 수 있습니다. 타입 표기시 리턴 타입을 생략해서는 안됩니다. 
```Swift
var function1: (Int) -> () = numberPrint(n:)
// (Int) -> () 해당 함수의 타입을 표기한 것입니다. 
// (Int) -> Void로 표기가 가능합니다. 단, 생략해서는 안됩니다.
var function2: (Int, Int) -> () = addPrintFunction(_:_:)
// (Int, Int) -> () 중첩 타입을 표기한 것입니다. 
// (Int, Int) -> Void로 표기가 가능합니다. 단, 생략해서는 안됩니다.
```



# 함수의 오버로딩(overloading)
> 오버로드(overload): 영어로 과적하다라는 뜻

#### 함수의 오버로딩이란 : 
- 같은 이름의 함수에 매개변수(파라미터)를 다르게 선언하여, 하나의 함수 이름에 실제 여러개의 함수를 대응 시키는 것입니다.
즉, 함수의 이름을 재사용할 수 있다는 것입니다. 
- 오버로딩이 되지 않는다면 같은 기능을 제공하는 함수를 파라미터 형식마다 이름을 다르게 구현해야하기 때문에 함수의 이름이 많아지고, 구별해서 사용하는 것이 어려워집니다.
- Swift는 ⭐️ 함수이름, 파라미터 수/자료형, 아규먼트 레이블, 리턴형을 모두포함해서 함수를 식별합니다. 
```Swift
func doSomething(value: String) {
    print(value)
}

func doSomething(_ value: String) {
    print(value)
}

func doSomethging(value1: String, value2: Int) {
    print(value1, value2)
}

// 같은 이름 조금 다른 함수들 

doSomething(value: 5)
doSomething(value: 3.4)
doSomething(value: 3)
// 사용할때는 매우 편하게 사용 가능하다! 
```

# 범위(Scope)에 대한 이해 
#### 스코프 Scope : 
 - 변수는 코드에서 선언이 되어야 그 이하의 코드에서 접근이 가능합니다. (전역변수는 예외)
 - 상위스코프(범위)에 선언된 변수와 상수에 접근가능하며, 하위스코프(범위)에는 접근할 수 없다.
 - 동일한 스코프에서 이름이 중복될 수 없지만, 다른 스코프에서는 이름 중복이 가능하다.
 - 가장 인접한 스코프에 있는 변수와 상수에 먼저 접근 한다.
```Swift
func greeting1() {
    print("Hello")
    
    var myName = "홍길동" 
    print(myName)
    
    print(name)
    // 상위 스코프에 접근 가능 
    
    if true {
        print(myName)
        print(name)
    }
}

print(myName)
// 함수 내부에 있는 변수이기 때문에 접근 할 수 없습니다. 
// 하위 스코프에 접근 불가

var name = "잡스" 
// 전역변수로 함수 내부에서 접근 가능합니다.

```

- 코드는 순서대로 작동하기 때문에, 선언이 되어있어야 사용 가능하다. 
```Swift
func doSomething() {
    print(realName)       
    // 변수가 아래에 선언 되어 있기 때문에 오류가 발생합니다.  
    var realName = "Rain"
}

doSomething()
```

# 제어전송문 정리 
#### break :
- switch문에서 case나 default에 실행하는 문장이 없을때, 반드시 입력해야 합니다 ⭐ 
- 반복문(for/while 등)에서 가장 인접한 반복문을 아예 중지시킬 때 사용합니다. ⭐

#### fallthrough : 
- switch문에서 사용하며, 다음 케이스도 실행 시키고 싶을 때 사용합니다. 
```Swift
switch a {
case 1:
    print("1입니다.")
    fallthrough
case 2:
    print(a)
default:
    break
}
// 1입니다.
// 안녕하세요
```

#### continue : 
- continue는 반복문을 다음 싸이클로 보낼때 사용합니다.

#### return : 
- 리턴 타입의 함수에서 리턴 키워드 다음의 표현식을 평가한다음 결과를 리턴 하면서 함수를 벗어날때 사용합니다.
- 리턴 타입이 없는 함수에서 함수의 실행을 중지하고 함수를 벗어날때 사용합니다.

#### throw : (나중의 단원에서 나옴)
- 에러가 발생 가능하도록 정의된 함수에서 throw키워드 다음에 정의된 에러의 타입을 리턴하면서 함수를 벗어나게 할때 사용합니다.
```Swift
enum APIError: Error {
    case aError
    case bError
}
// 에러 케이스를 정리


func doSomething2() throws -> String {
    print("1")
    print("2")
    
    if true {
        throw APIError.aError    // 리턴과 동일한 역할(함수를 종료시킴) ===> 에러를 던지고 함수를 벗어남
    }
    
    print("3")
    print("4")
    
    return "안녕하세요"
}
```

# 함수 실행의 메모리 구조 - 1 
#### 컴퓨터의 기본 동작원리 : 
- 컴퓨터의 기본 동작은 아래와 같이 순서대로 진행됩니다. 
1. 하드디스크에 코드가 있다가 실행시키면 램(메모리)위에 복사되어서 올라갑니다. 
2. 램(메모리)는 코드, 데이터, 힙, 스택으로 공간이 있습니다. 
3. 코드영역에는 코드들이 명령어 형태로 변경되어 저장이 됩니다.
4. 코드영역에 있는 것들을 CPU가 한줄씩 실행시키며 처리됩니다.

#### 스택이란 : 
- 컴퓨터의 메모리에서 처리 할때는 스택의 형태로 처리됩니다. 
- 스택이란 아래에서 부터 쌓이고 제거 할때는 위에서부터 제거할 수 있는 구조이며 반대편이 뚫려 있지 않은 통이라고 생각하면 됩니다.

#### 함수 실행의 메모리 구조 : 
- 명령어의 영역에서 함수가 있는 영역이 존재하고 코드를 MAIN부터 순서대로 실행하다가 함수 실행문을 만나게 되면 함수의 특정 메모리 주소를 찾아가서 실행 시킵니다.  

#### 함수 실행의 메모리 동작 구조 : 
- 프로그램이 실행되면 CPU는 코드에 있는 main()을 찾아갑니다.
- 'main() 함수 스택 프레임'이 메모리 스택 영역에 생성됩니다. 
- main()의 내용을 CPU가 한줄씩 일을 처리합니다.
이때, 변수나 상수가 선언되면 main() 함수 스택 프레임에 메모리 공간이 생성되고 값이 저장됩니다.
이때, 함수를 만나게 되면 메모리 스택 영역에서 main() 함수 영역 위에 층을 쌓아서 올려 새로운 스택 프레임 영역 생성합니다.
- 그후 함수 스택 프레임 영역으로 CPU의 제어권이 옮겨가며 제일 먼저 함수의 스택에 복귀주소를 저장합니다.
- 그후 함수가 함수값/원시값이 있다면, 스택 프레임 내부에 함수값/원시값을 저장할 임시 공간을 생성합니다. 
- 함수의 내용을 CPU가 한줄씩 일을 처리합니다. 
이때, 변수나 상수가 선언되면 main()스택 프레임이 아닌 함수 스택 프레임에 메모리 공간이 생성되고 값이 저장됩니다.
- 함수의 동작이 끝나면, 리턴값과 CPU의 제어권이 복귀주소를 통해 반환되며 스택 프레임이 사라집니다.
- 다시 한줄씩 CPU가 실행시킵니다. 

# 함수 실행의 메모리 구조 - 2 
# 조건문과 반복문의 명령어(CPU) 구조 
# 입출력(inout) 파라미터 
# guard문 
# 함수의 리턴값과 discardableResult 
# 튜플을 사용하는 이유 - 함수와 연관지어서 
# 연습문제 - 문자열 중에서 랜덤 뽑아내기 / 소수 판별 
# 연습문제 - 팩토리얼 함수 만들어 보기 / 재귀함수 메모리 구조 
# print함수 제대로 알기 / API에 대한 이해 
