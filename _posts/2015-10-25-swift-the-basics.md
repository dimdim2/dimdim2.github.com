- 주저리... 주저리...
- Optional ar safer and more expressive than nil pointers in Objective-C and are at the heart of many of Swift’s most powerful feature.

### Constats and Variable
- 상수 : 변경할 수 없다.
- 변수 : 변경할 수 있다.

```
let maximumNumberOfLoginAttempts = 10  // 상수 선언
var currentLoginAttempt = 0 // 변수 선언

var x = 0.0, y = 0.0, z = 0.0  // 한줄로 복수의 변수 선언 가능 (상수도 가능)
```

### Type Annotations
- 변수 & 상수 선언시 명시적으로 타입을 지정하기 위해 type annotation을 추가할 수 있다.

```swift
var welcomeMessage: String
welcomeMessage = "Hello"

var red, grren, blue: Double   // 요런식으로도 가능하다.
```
> 변수(상수)선언시 값을 할당하는 경우 컴파일러가 알아서 타입 추론을 해주기 때문에 일반적으로는 type annotation 을 생략한다. 좀 더 자세한 내용은 "Type Safety and Type Inference" 절을 참조

### Naming Constants and Variables
- 변수&상수 이름은 대부분의 문자를 사용할 수 있다. (심지어 이모지도...)
    - Constant and variable names cannot contain whitespace characters, mathematical symbols, arrows, private-use (or invalid) Unicode code points, or line- and box-drawing characters. (다른 언어들과 유사함)
    - 예약어와 동일한 이름의 변수를 선언하고 싶으면 (`) 문자로 감싸주면 됨. (비추함)

    ```swift
    let π = 3.14159
    let 你好 = "你好世界"
    let ?? = "dogcow"
    ```

### Printing Constants and Variables
    - You can print the current value of a constant or variable with the _print(_:separator:terminator:)_ function:
    - print 함수는 전역 함수이다.
    - seperator 와 terminator 매개변수는 기본값을 가지고 있어서, 생략할수 있다. (seperator는 어떻게 사용하는걸까??)
    - 스위프트는 string interpolation 을 사용하여 문자열에 표현식을 삽입할 수 있다.

    ```swift
    var friendlyWelcome ="Bonjour!"
    print(friendlyWelcome) // prints "Bonjour!"
    print(friendlyWelcome, terminator:"") // 문자열 마지막에 개행문자 생략 가능

    print("The current value of friendlyWelcome is \(friendlyWelcome)") // string interpolation 예제
    ```

### Comments
    - C 혹은 java 랑 동일하다.

### Semicolons
    - 루비처럼 세미콜론 생략이 가능하다.

### Integers
    - Swift provides signed and unsigned integers in 8, 16, 32, and 64 bit forms.
        > UInt8 : 8bit unsigned integer
            > Int32 : 16bit signed integer
                > Int8, Int16, Int32, Int64, UInt8, UInt16, UInt32, UInt64, Int, UInt
                - Integer Bounds

                ```swift
                let minValue = UInt8.min  // minValue is equal to 0, and is of type UInt8
                let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8
                ```

                - In most cases, you don’t need to pick a specific size of integer to use in your code.

                > On a 32-bit platform, Int is the same size as Int32.
                > On a 64-bit platform, Int is the same size as Int64.

                - UInt 도 Int와 동일함

### Floating-Point Numbers
                - Double represents a 64-bit floating-point number.
                - Float represents a 32-bit floating-point number.

### Type Safety and Type Inference
                - Swift is a type safe language.
                - 스위프트는 컴파일 시점에 타입 체크를 해준다. (런타임에 사고칠 위험을 줄여준다.)
    - 스위프트는 변수/상수 선언시 값을 할당한다면, 타입추론을 통해 타입을 명시하지 않아도 컴파일러가 알아서 타입 체크를 해준다. (코딩시 타이핑 수고를 덜어 준다.)

    ```swift
    let meaningOfLife = 42 // meaningOfLife is inferred to be of type Int

    // Swift always chooses Double (rather than Float) when inferring the type of floating-point numbers.
    let pi = 3.14159  // pi is inferred to be of type Double

    let anotherPi = 3 + 0.14159 // anotherPi is also inferred to be of type Double
    ```

### Number Literals
    - 자바 혹은 C 와는 약간 다른듯???
    - 정수
        - A decimal number, with no prefix
            - A binary number, with a 0b prefix
                - An octal number, with a 0o prefix
                    - A hexadecimal number, with a 0x prefix
                    - For decimal numbers with an exponent of exp, the base number is multiplied by 10exp:
                        - 1.25e2 means 1.25 x 102, or 125.0.
                            - 1.25e-2 means 1.25 x 10-2, or 0.0125
                            - For hexadecimal numbers with an exponent of exp, the base number is multiplied by 2exp:
                                - 0xFp2 means 15 x 22, or 60.0.
                                    - 0xFp-2 means 15 x 2-2, or 3.75.

                                    ```swift
                                    let decimalInteger = 17
                                    let binaryInteger = 0b10001       // 17 in binary notation
                                    let octalInteger = 0o21           // 17 in octal notation
                                    let hexadecimalInteger = 0x11     // 17 in hexadecimal notation

                                    et decimalDouble = 12.1875
                                    let exponentDouble = 1.21875e1
                                    let hexadecimalDouble = 0xC.3p0

                                    let paddedDouble = 000123.456
                                    let oneMillion = 1_000_000
                                    let justOverOneMillion = 1_000_000.000_000_1
                                    ```

                                    - 스위프트의 숫자 리터럴 표기법은 가독성을 높이기 위한 추가적은 포맷을 지원한다. (루비와 비슷??)

    ```swift
    let paddedDouble = 000123.456
    let oneMillion = 1_000_000
    let justOverOneMillion = 1_000_000.000_000_1
    ```

### Numeric Type Conversion
    - Use the Int type for all general-purpose integer constants and variables in your code, even if they are known to be non-negative.
    - 메모리/성능 최적화 혹은 value overflow 이슈를 방지가 꼭 필요한 경우는 사이즈를 명시한 정수 타입을 사용해라. (자바로 socket 프로그래밍할때 가끔 이런게 있었으면 할때가 있었...)

#### Integer Conversion
    - 정수 타입이 지워하는 범위를 벗어나는 값을 변수 혹은 상수에 할당하면 컴파일 에러가 발생한다.

    ```swift
    let cannotBeNegative: UInt8 = -1 // UInt8 cannot store negative numbers, and so this will report an error

    let tooBig: Int8 = Int8.max + 1  // Int8 cannot store a number larger than its maximum value,and so this will also report an error

    let twoThousand: UInt16 = 2_000
    let one: UInt8 = 1
    let twoThousandAndOne = twoThousand + UInt16(one)
    ```

    - 서로 다른 정수 타입끼리는 바로 덧셈을 할 수 없다. 타입변환을 해줘야 한다.

    ```swift
    let twoThousand: UInt16 = 2_000
    let one: UInt8 = 1
    let twoThousandAndOne = twoThousand + UInt16(one)  // twoThousand + one <= 요래 하면 컴파일 에러 발생
    ```

#### Integer and Floating-Point Conversion
    - 정수와 floating-point 숫자 타입 사이에도 명시적으로 타입변환을 해줘야 한다.
    - Floating-point values are always truncated when used to initialize a new integer value in this way. This means that 4.75 becomes 4, and -3.9 becomes -3.

    ```swift
    let three = 3
    let pointOneFourOneFiveNine = 0.14159
    let pi = Double(three) + pointOneFourOneFiveNine // 타입에 대해서 자바보다 좀더 고지식?한 것 같음.

    let integerPi = Int(pi) // integerPi equals 3, and is inferred to be of type Int
    ```
    > 숫자 리터럴의 경우 변수/상수 와는 다르게 자바와 같은 룰로 사칙연산이 동작한다.

### Type Aliases
    - 이미 존재하는 타입에 대한 별명을 정의할 수 있다.
    - typealias 키워드를 이용하여 정의할 수 있다.
    ```swift
    typealias AudioSample = UInt16  // C언어의 #typedef 같은거??
    ```

### Booleans
    ```
    let orangesAreOrange = true
    let turnipsAreDelicious = false

    // prints "Eww, turnips are horrible."
    if turnipsAreDelicious {
            print("Mmm, tasty turnips!")
    } else {
            print("Eww, turnips are horrible.")
    }
```

- 스위프트는 Boolean 타입 이외의 값(표현식)은 조건문에서 사용할 수 없다. (때론 루비 혹은 자바스크립트 방식이 편할때도 있는데...)

### Tuple
    - Tuples group multiple values into a single compound value. The values within a tuple can be of any type and do not have to be of the same type as each other.
    - 튜플은 함수의 리턴값으로 유용하게 사용할 수 있다. (단순한 데이터 구조이면서, 타입이 서로 다른 복수의 값을 리턴하고자 할때 유용한듯??)

    ```swift
    let http404Error = (404, "Not Found") // http404Error is of type (Int, String)

    // decompose a tuple’s contents into separate constants or variables
    let (statusCode, statusMessage) = http404Error
    print("The status code is \(statusCode)") // prints "The status code is 404"
    print("The status message is \(statusMessage)") // prints "The status message is Not Found"

    // 튜플의 일부의 값만 필요한 경우, ignore parts of the tuple with an underscore (_) when you decompose the tuple
    let (justTheStatusCode, _) = http404Error
    print("The status code is \(justTheStatusCode)") // prints "The status code is 404"

    // access the individual element values in a tuple using index numbers starting at zero:
    print("The status code is \(http404Error.0)") // prints "The status code is 404"
    print("The status message is \(http404Error.1)") // prints "The status code is 404"

    // You can name the individual elements in a tuple when the tuple is defined:
    let http200Status = (statusCode: 200, description: "OK")
    print("The status code is \(http200Status.statusCode)") // prints "The status code is 200"
    print("The status message is \(http200Status.description)") // prints "The status message is OK"
    ```

### Optionals
    - 값이 존재하지 않을 수 있는 경우 Option 타입을 사용한다.
    - 참고: https://developer.apple.com/library/watchos/documentation/Swift/Reference/Swift_Optional_Enumeration/index.html#//apple_ref/swift/enum/s:Sq

#### nil
    - nil은 값이 없음을 나타내는 특별한 값이다.

    ```swift
    var serverResponseCode: Int? = 404 // serverResponseCode contains an actual Int value of 404
    serverResponseCode = nil // serverResponseCode now contains no value

    var surveyAnswer: String?  // surveyAnswer is automatically set to nil
    ```
    > Swift’s nil is not the same as nil in Objective-C. In Objective-C, nil is a pointer to a nonexistent object. In Swift, nil is not a pointer

#### If Statements and Forced Unwrapping
    ```swift
    // nil 도 객체?(enum) 이며 map, flatMap 메소드를 제공한다. 하지만 스칼라에 비해서는 제공하는 메소드가 좀 빈약한 듯...
    if convertedNumber != nil {
            // // prints "convertedNumber has an integer value of 123."
            print("convertedNumber has an integer value of \(convertedNumber!).")
    }
```

#### Optional Binding
```swift
let possibleNumber = "123"

// Int("???") 표현식의 결과는 Optional 타입이며, 정수로 변환이 가능하면 Optional(???)이 되고 아니면 nil 값이 된다.
// 정수 변환이 가능하면 actualNumber 에 정수값이 할당되고, if문의 body를 실행하고, 반대의 경우 else문의 body가 실행된다.
if let actualNumber = Int(possibleNumber) {
        print("\'\(possibleNumber)\' has an integer value of \(actualNumber)")
} else {
        print("\'\(possibleNumber)\' could not be converted to an integer")
}

// 아래와 같이 사용할 수도 있다.
if let firstNumber = Int("4"), secondNumber = Int("42") where firstNumber < secondNumber {
        print("\(firstNumber) < \(secondNumber)")   // prints "4 < 42"
}
```

#### Implicitly Unwrapped Optionals
- 옵셔널 타입의 변수가 항상 값을 갖고 있는 경우, 편리하다고 하는 것 같은데...???
- The primary use of implicitly unwrapped optionals in Swift is during class initialization, as described in "Unowned References and Implicitly Unwrapped Optional Properties". (주요 사용처는 나중에 확인...?? ^^;;)


```swift
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation mark
 
let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation mark
```

> "implicitly unwrapped optionals" 변수도 값이 nil 일때, 감싸진 값을 접근하면 일반적은 Optional 이랑 동일하게 에러가 발생한다.

> nil 값을 갖을 수 있는 Optional 변수는 사용하지 않는게 정신건강에 좋다고함.

### Error Handling
- 자세한 내용은 "Error Handling" 에서... 

```swift
// java의 Checked Exception과 유사한 느낌 (개인적으로는 별로 좋아하지 않는데...)
func canThrowAnError() throws {
        // this function may or may not throw an error
}

// do statement creates a new containing scope, which allows errors to be propagated to one or more catch clauses.
do {
        try canThrowAnError()  // try 키워드를 제거하면 컴파일 에러 발생
                // no error was thrown
} catch {
        // an error was thrown
}

func makeASandwich() throws {
        // ...
}
 
do {
        try makeASandwich()
                eatASandwich()
} catch Error.OutOfCleanDishes {
        washDishes()
} catch Error.MissingIngredients(let ingredients) {
        buyGroceries(ingredients)
}
```

## Assertions
- java의 assert 와 유사하며, 디버그 용도로 사용함?

#### Debugging with Assersions

```swift
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
```

> Assertions are disabled when your code is compiled with optimizations, such as when building with an app target’s default Release configuration in Xcode.

#### When to Use Assertions
- An integer subscript index is passed to a custom subscript implementation, but the subscript index value could be too low or too high. (subscript 참고: http://minsone.github.io/mac/ios/swift-subscripts-summary/)
- A value is passed to a function, but an invalid value means that the function cannot fulfill its task.
- An optional value is currently nil, but a non-nil value is essential for subsequent code to execute successfully.


