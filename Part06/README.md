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
- 반복문 내에서 쓰이는 제어전송 명령문으로 흐름 제어 라고도 부릅니다. 
- 중첩사용시 가장 인접한 반복문에 영향을 미칩니다. 


#### 반복문에서 제어전송문 continue 사용법 : 
- 반복문에서 continue를 만날경우 아래(다음)에 위치한 문장들을 무시하고 다음 싸이클로 넘기는 제어전송문입니다. 


#### 반복문에서 제어전송문 break 사용법 : 






# 연습문제 - 구구단 / 배수 / 논리 구성해서 출력해보기

#### 연습문제 - 구구단
```Swift
for i in 1...9 {
    for j in 1...9 {
        print ("\(i) X \(j) = \(i*j)")
    }
}

for i in 1...9 {
    for j in 1...9 {
        print (String(i) + "X" + String(j) + "=" + String(i*j))
    }
}
```

#### 연습문제 - 배수
```Swift
for i in 1...100 {
    if i%3==0 {
        print ("3의 배수 발견: \(i)")
    }
}
```

#### 연습문제 - 논리 
```Swift
for i in 1...5 {
    for _ in 1...i {
        print ("😀", terminator: "")
    }
    print ()
}
```
