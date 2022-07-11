# 프로그래밍의 기본원리와 if 조건문
#### 프로그래밍의 기본 원리 
- 모든 프로그래밍은 순차 -> 조건 -> 반복 세가지 논리로 이루어 집니다.
- 순차는 개발자가 정한 규칙에 따라 순차적으로 (차례대로) 실행하는것을 의미합니다.
- 조건은 참 또는 거짓의 특정 조건에 따라 특정 코드만 실행하게 할 수 있는 문장을 의미합니다. 조건을 만족하면 {} 중괄호 안의 코드를 실행하는 문장을 의미합니다.
- 반복은 

# 조건문 (if문) 

#### if문이란 : 
- if 조건 {실행문}의 형식으로 사용합니다.
- if 조건 {실행문} else {실행문}의 형식을 사용하여 조건을 만족하지 않을시 실행할 실행문을 추가할 수 있습니다.
- if 조건 {실행문} else if {실행문}의 형식을 사용하여 조건을 추가 할 수 있습니다. 
```Swift
// 기본 if
if n < 10 {
  print("10보다 작다.")
}

// else
if n < 10 {
  print("10보다 작다.")
} else {
  print("10보다 크거나 같다.")
}

// else if 
if n < 10 {
  print("10보다 작다.")
} else if n == 10 {
  print("10이다.")
} else {
  print("10보다 크다")
}

```

- 조건을 &&과 ||로 연결하는 것도 가능합니다.
```Swift
if email == "abc123@naver.com" && password == "1234" {
  print("메인페이지로 이동")
}

if email != "abc123@naver.com" || password != "1234" {
  print("경고메시지 띄우기")
  print("이메일주소 또는 패스워드가 옳바르지 않습니다")
}

```

- 중첩 사용이 가능합니다.
```Swift
if n >= 70 {
  if n == 100 {
    print("만점")
  } else {
    print("70점 이상")
  }
}
```



# 조건문 (switch문)

#### switch문 이란 : 
- 여러가지 선택가능한 경우의 수에 따라 코드를 실행할때 사용하는 조건문을 의미합니다. 
- 표현식/변수를 (매칭시켜) 분기처리할때 사용합니다. if문보다는 한정적인 상황에서 사용합니다. 
- swich 표현식/변수 { case 비교할값 : 실행할문장 default: 어느 case도 해당하지 않을시 실행할 문장 } 형식으로 사용합니다.
- swich문은 (비교하고 있는) 값의 가능한 모든 경우의 수를 반드시 다루어야 하며, 모든 사례를 다루지 않았을경우 디폴트 케이스를 반드시 생성해야합니다. 
- 각 케이스에는 문장이 최소 하나 이상 있어야하며 만약 없다면 컴파일 에러가 발생하지 않기 위해, break를 반드시 입력해야합니다. 
```Swift
switch choice {
case "가위" :
  print("가위 입니다.")
case "바위" :
  print("바위 입니다.")
case "보" :
  print("보 입니다.")
default:
  break
}
```

- 콤마(,)를 또는의 의미로 사용하여 하나의 케이스에 여러 매칭값을 넣을 수 있습니다. 
```Swift
switch choice {
case "가위" :
  print("가위 입니다.")
case "바위", "보" :
  print("바위 또는 보 입니다.")
default:
  break
}
```

- fallthrough을 사용하여 매칭된 값에 대한 고려없이 무조건 다음 블럭을 실행하게 할 수 있습니다.
```Swift
switch num1 {
case ..<10 :      //범위 연산자 사용 가능
  print("1")
  fallthrough
case 10 :
  print("2")
  fallthrough
default:
  print("3")
}
```

- Switch문의 매칭값에는 비교연산자를 넣으면 안되며, 범위 연산자를 이용해야합니다. 
```Swift
switch num1 {
case < 10 :
  print("1")
default:
  break
}
// 컴파일 에러 
```


# switch문의 활용(바인딩, where)

#### switch문에 바인딩 : 
- switch문에 바인딩을 이용할 수 있습니다. 
```Swift
switch num {
case let a:     // 바인딩
  print("숫자: \(a)")
default:
  break
}
```
- swich문에서 where절을 사용하여 바인딩후 조건을 확인 할 수 있습니다. 이경우 비교연산자 사용가능
```Swift
switch num {
case let x where x % 2 == 0:     // 바인딩 후 where절을 이용하여 조건 확인
  print("짝수 숫자: \(x)")
case let x where x % 2 != 0:     // 바인딩 후 where절을 이용하여 조건 확인
  print("홀수 숫자: \(x)")
default:
  break
}
```


# 연습문제 / 가위바위보 게임 만들기 / 랜덤 빙고 게임 만들기

#### 가위바위보 게임 만들기
> 가위/바위/보 게임을 if문을 사용해서 구현해 봅니다. 컴퓨터는 가위, 바위, 보 중에서 랜덤(무작위)으로 선택하게 되고, 당신은 한가지를 고릅니다. 
그리고 결과적으로 "무승부입니다.", "당신은 졌습니다.", "당신은 이겼습니다." 이 셋 중에 한가지가 출력되도록 합니다.

> tip. 가위는 정수 0, 바위는 정수 1, 보는 정수 2와 같다고 생각하면 됩니다. 랜덤으로 숫자를 뽑는 방법은 Int.random(in: 0...2). (if문을 중첩하여 사용하는 것도 좋습니다.)


```Swift
var a: Int = 2
var randomInt: Int = Int.random(in: 0...2)

if a == randomInt {
    print("무승부입니다.")
} else if a == 0 && randomInt == 2 {
    print("당신은 이겼습니다.")
} else if a == 1 && randomInt == 0 {
    print("당신은 이겼습니다.")
} else if a == 2 && randomInt == 1 {
    print("당신은 이겼습니다.")
} else {
    print("당신은 졌습니다.")
}
```

#### 랜덤 빙고 게임 만들기
> 컴퓨터가 1부터 10사이의 정수에서 랜덤 값을 선택하고, 저장하도록 합니다. 그리고 당신은 1부터 10사이의 정수를 선택합니다. 컴퓨터가 선택한 랜덤값과 당신의 값을 비교하고 당신의 숫자가 더 높은 경우는 "Down", 당신의 숫자가 더 낮은 경우는 "Up", 당신의 숫자와 동일한 경우 "Bingo"가 출력되도록 합니다. 

> tip. 랜덤으로 숫자를 뽑는 방법은 Int.random(in: 1...10)


```Swift
var system1: Int = Int.random(in: 1...10)
var you: Int = 10

if you == system1 {
    print("Bingo")
}
else if you > system1 {
    print("Down")
}
else {
    print("Up")
}
```




