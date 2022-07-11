# 튜플 기본

#### 튜플 이란 : 
- 원하는 연관된 데이터의 조합으로 어떤 형태든 만들 수 있는 타입을 의미합니다.
- 2개 이상의 연관된 데이터(값)을 저장하는 Compound(복합/혼합) 타입입니다. 
- 튜플의 내부의 각각의 데이터에 접근이 가능합니다.
```Swift
var a = ("첫번째", 2, 3.0)

변수명.0   // "첫번째"
변수명.1   // 2
```

- 튜플의 맴버(데이터의 종류 및 갯수)는 튜플을 만들때 결정되므로 추가, 삭제는 불가능합니다.
```Swift
var a = ("첫번째", 2, 3.0)
var a = ("첫번째", 5)      //컴파일 에러
```

- Named Tuple. 튜플에 이름을 매길수 있습니다. 
```Swift
var ios = (language: "Swift", version: "5")

ios.0 == ios.language
ios.1 == ios.version
```

- 튜플의 값을 분해해서 상수나 변수에 저장을 할 수 있습니다. 
```Swift
let (a,b,c) = (1,2,3)
a       // 1
b       // 2
c       // 3
```

- 타입 앨리어스를 이용하여 치환해서 사용도 가능합니다.
```Swift
typealias GridPoint = (Int,Int)
```

- 튜플의 값을 비교할 수 있습니다. 기본적으로 첫번째 자리 값을 서로 비교하며, 첫번째 값이 같을경우 다음 값을 비교합니다.
```Swift
(1, "zebra") < (2, "apple")   // true
(3, "apple") < (3, "bird")    // true 문자열은 앞에 문자를 비교합니다. a < b

("blue", -1) < ("purple", 1)            // true
("blue", false) < ("purple", true)    // 에러 Bool 값은 비교 불가능 합니다. 
```

# 튜플의 활용

#### 조건문과 함께 사용 :
- if문 사용 예제 
```Swift
if iOS.0 == "Swift" && iOS.1 == "5" {
    print("스위프트 버전 5입니다.")
}

if iOS == ("Swift", "5") {
    print("스위프트 버전 5입니다.")
}

```
- switch문 사용 예제
```Swift
switch iOS {
case ("Swift", "5"):
    print("스위프트 버전 5입니다.")
case ("Swift", "4"):
    print("스위프트 버전 4입니다.")
default:
    break
}
```


#### 바인딩하여 사용 : 
- 바인딩 사용 예제 
```Swift
var coordinate = (0, 5)   // 좌표계

switch coordinate {
case (let distance, 0), (0, let distance):   // x축이나 y축에 있으면 출력하라는 코드. 
    print("X 또는 Y축 위에 위치하며, \(distance)만큼의 거리가 떨어져 있음")
default:
    print("축 위에 있지 않음")
}

// X 또는 Y축 위에 위치하며, 5만큼의 거리가 떨어져 있음
```
- 바인딩과 where절 활용
```
coordinate = (5, 0)

switch coordinate {
case (let x, let y) where x == y:      //각각 x와 y의 상수로 바인딩해줍니다. 그후 where의 조건문을 확인합니다. 
    print("(\(x), \(y))의 좌표는 y = x 1차함수의 그래프 위에 있다.")
    
case let (x, y) where x == -y:
    print("(\(x), \(y))의 좌표는 y = -x 1차함수의 그래프 위에 있다.")
    
case let (x, y):
    print("(\(x), \(y))의 좌표는 y = x, 또는 y = -x 그래프가 아닌 임의의 지점에 있다.")
}
// (5, 0)의 좌표는 y = x, 또는 y = -x 그래프가 아닌 임의의 지점에 있다.
```

