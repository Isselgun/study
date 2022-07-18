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
# 함수의 표기법(지칭) / 함수의 타입 표기  
# 함수의 오버로딩 
# 범위(Scope)에 대한 이해 
# 제어전송문 정리 
# 함수 실행의 메모리 구조 - 1 
# 함수 실행의 메모리 구조 - 2 
# 조건문과 반복문의 명령어(CPU) 구조 
# 입출력(inout) 파라미터 
# guard문 
# 함수의 리턴값과 discardableResult 
# 튜플을 사용하는 이유 - 함수와 연관지어서 
# 연습문제 - 문자열 중에서 랜덤 뽑아내기 / 소수 판별 
# 연습문제 - 팩토리얼 함수 만들어 보기 / 재귀함수 메모리 구조 
# print함수 제대로 알기 / API에 대한 이해 
