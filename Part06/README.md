# 반복문 (for문)
#### for문이란 : 
- for 반복상수 in 범위or컬렉션 {실행문}의 형식으로 사용합니다.
- 반복할 범위에는 범위연산자, 변수, 배열 등이 들어갈 수 있습니다. 
```Swift
for i in 1...5 {                    // 범위 연산자
  print("\(i)번째 반복입니다.")
}

for i in (1...5).reversed {                    // 특정한 함수를 넣어서 사용할 수 있습니다. 
  print("\(i)번째 반복입니다.")
}

for i in stride(from: 1, to: 15, by:2) {       // stride 함수를 이용하여 다른 언어의 for문 처럼 쓸 수 있습니다.
  print(i)                                     // to에 기재한 수는 반복상수에 들어가지 않습니다. (언어차이 있음)
}

var number = 10
for i in 1...number {               // 변수 
  print("\(i)번째 반복입니다.")
}

let list = ["swift", "programing", "Language"]        // 배열, 컬렉션
for i in list {
  print(i)
}
for i in "HELLO" {                  // 문자열. 문자 하나씩 반복상수에 넣어집니다.
  print(i)
}

// 이외에도 Int범위, 문자열, 컬렉션(배열, 딕셔너리, Set)을 사용할 수 있습니다. 
```

- 반복상수를 쓰지 않고 '와일드 카드 패턴 _(언더바)'를 사용할 수 있습니다. 생략의 의미로 _(언더바)를 사용합니다. 
```Swift
for _ in 1...5 {                   
  print("반복문입니다.")
}
```

#### for문 사용시 주의점 :
- for문에서 사용한 반복상수는 반복문이 종료 된후 사용할 수 없습니다. 
- 반복문안에서 사용되는 동일한 이름의 변수는 제일 가까운 변수를 찾아 사용됩니다. 
```
for i in (1...10) {
  print(i)
}
print(i)                // 반복상수는 반복문 안에서 사용이 가능합니다. 

var i = "Rain"
for i in (1...10) {
  print(i)              // Rain이 출력되지 않고 1...10까지 출력됩니다. 
}
print(i)                // Rain이 출력됩니다. 
```

# while문 / repeat-while문

#### while문 이란 : 
- while 조건문 {실행문}의 형식으로 사용합니다. 조건은 True일경우에만 실행됩니다. 
- while의 실행문에는 조건을 변화시키는 문장을 넣어야 합니다. 조건을 변화시키지 않을시 무한루프가 될수 있습니다. 
```Swift
var sum = 0
var num = 1
while num <= 50 { 
    sum += num
    num += 1     
}
print("총 합의 출력: ", sum)       // 1275


while num <= 50 {   
    sum += num
    // num += 1      // 조건문을 변화시키지 않으면 무한반복, 무한루프 하게 됩니다.
}
print("총 합의 출력: ", sum)
```

#### repeat-while문 이란 :
- 조건문의 참거짓에 상관없이 1번 실행이 됩니다. 그후 조건문이 참이라면 반복하는 문장을 의미합니다.
```Swift
var sum = 0
var num = 1

repeat {   
    sum += num
    num += 1    
} while num <= 50 
print("총 합의 출력: ", sum)       // 1275


var sum = 0
var num = 50
repeat {   
    sum += num
    num += 1    
} while num <= 50 
print("num : ", num)            // num : 51    조건과 관계없이 1번 실행됩니다.
print("총 합의 출력: ", sum)
```

# 반복문의 제어전송문 (continue / break)
#### 제어 전송문이란 : 
- 제어전송 명령문으로 흐름 제어를 하기 위해 사용됩니다. 
- 중첩사용시 가장 인접한 반복문에 영향을 미칩니다. ⭐


#### 반복문에서 제어전송문 continue 사용법 : 
- 반복문에서 continue를 만날경우 아래(다음)에 위치한 문장들을 무시하고 다음 싸이클로 넘기는 제어전송문입니다. 
```Swift
for num in 1...20 {
    if num % 2 == 0 {   // num 2의 배수일 경우 continue를 만나며, 아래의 문장을 무시하고 반복상수에 다음 범위를 넣어 진행시킵니다. 
        continue
    }
    print(num)
}
```

#### 반복문에서 제어전송문 break 사용법 : 
- 반복문에서 break를 만날경우 반복문을 종료하는 제어전송문입니다. 
```Swift
for num in 1...20 {
    if num % 2 == 0 {
        break               // num에 2를 만나는 순간 break를 만나며, 해당 반복문은 종료됩니다. 
    }
    print(num)
}
```

#### Labeled Statements 
- 반복문을 중첩사용할 경우 반복문에 이름을 붙여 continue 이름 , break 이름으로 사용하여 제어할 수 있습니다. 
- 관습적으로 반복문의 이름은 대문자로 사용합니다. ⭐
```Swift
OUTER: for i in 0...3 {
    print("OUTER \(i)")
    INNER: for j in 0...3 {
        if i > 1 {
            print("  j :", j)
            continue OUTER
            //break OUTER
        }
        print("  INNER \(j)")
    }
    
}
```


# 연습문제 - 구구단 / 배수 / 논리 구성해서 출력해보기

#### 연습문제 - 구구단
> 반복문을 이용하여 구구단을 출력해 봅니다. 
> 힌트. 어떤 부분이 반복이 되고 있는지 잘 살펴보세요. 반복문을 중첩시킬 수도 있어요.
```Swift
for i in 1...9 {
    for j in 1...9 {
        print ("\(i) X \(j) = \(i*j)")    // 수업 정답
    }
}

for i in 1...9 {
    for j in 1...9 {
        print (String(i) + "X" + String(j) + "=" + String(i*j))   // 길게 길게 만들었던 코드
    }
}
```

#### 연습문제 - 배수
> 1부터 100까지의 숫자로 3으로 나누어 지는 숫자를 찾아봅니다. 즉, 3의 배수를 찾습니다. 그리고 아래와 같이 출력하도록 합니다. 
> >힌트. 어떤 부분이 반복이 되고 있는지 잘 살펴보세요. 나누어 떨어지는 숫자는 앞에서 배웠던 %(모듈로) 연산자를 활용할 수 있어요.  
```
3의 배수 발견 : 3
3의 배수 발견 : 6
...
3의 배수 발견 : 99
```

```Swift
for i in 1...100 {
    if i%3==0 {
        print ("3의 배수 발견: \(i)")
    }
}

for i in 1...100 {
    if i % 3 != 0 {   // 조건을 만족하지 못했을 때 다음으로 넘어갑니다. 
        continue      // 여러조건이 있을경우 가독성이 높아질수 있습니다.
    }
    print("3의 배수 발견: \(i)")
}
```

#### 연습문제 - 논리 
> 반복문, 조건문을 활용하여 아래와 같이 출력해 봅니다.
> > 힌트.반복문, 조건문을 활용하여 아래와 같이 출력해 봅니다. 문자열"😀"만 이용해야합니다. print함수의 원래 형태는 print(_:separator:terminator:)이고 print ("😀", terminator: "")를 이용하면, 줄 바꿈을 하지 않고 연속해서 출력할 수 있어요. print()는 줄바꿈을 위해 사용할 수 있어요. 
```
😀
😀😀
😀😀😀
😀😀😀😀
😀😀😀😀😀
```
```Swift
for i in 1...5 {
    for _ in 1...i {
        print ("😀", terminator: "")
    }
    print ()
}
```
