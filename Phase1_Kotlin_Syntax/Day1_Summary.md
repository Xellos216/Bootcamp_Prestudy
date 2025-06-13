# 📚 Phase 1 - Day 1: Kotlin 기초 - 변수와 조건문

오늘은 Kotlin 개발 환경을 설정하고, Kotlin 언어의 가장 기본적인 요소인 변수와 조건문을 학습했습니다. IntelliJ IDEA 사용에 익숙해지고, 기본적인 코드 작성 및 디버깅 흐름을 경험했습니다.

---

## 1. 배운 내용 요약

* **개발 환경 설정:** OpenJDK 설치 및 JetBrains Toolbox App을 통한 IntelliJ IDEA Ultimate 설치.
* **Kotlin 프로젝트 생성:** IntelliJ IDEA에서 Gradle(Kotlin DSL) 기반의 Kotlin 콘솔 애플리케이션 프로젝트를 생성했습니다.
* **변수 선언과 데이터 타입:** `val` (읽기 전용)과 `var` (변경 가능)을 사용하여 다양한 타입의 변수를 선언하는 방법을 학습했습니다. (Int, Double, Boolean, String 등)
* **콘솔 출력:** `println()` 함수와 `$` 기호를 활용한 문자열 템플릿(`$변수명`, `${표현식}`)으로 콘솔에 값을 출력하는 방법을 익혔습니다.
* **조건문 (`if/else`, `when`):** 프로그램의 흐름을 제어하는 `if/else` 문과 Kotlin의 강력한 `when` 문(Java의 switch와 유사)을 사용하여 조건에 따라 다른 코드를 실행하는 방법을 배웠습니다.
* **IDE 사용 기본:** IntelliJ IDEA에서 코드를 실행하고, 오류 메시지를 읽고 수정하는 과정을 경험했습니다. (특히 `.idea` 폴더 `.gitignore` 처리 및 미묘한 문법 오류 해결)

---

## 2. 문법 개념 간단히 설명

### **2.1. 변수 (Variables)**

Kotlin에서 변수를 선언할 때는 `val`과 `var` 키워드를 사용합니다.

* `val`: **Value**의 약자로, 한 번 할당되면 **값을 변경할 수 없는(읽기 전용)** 변수를 선언합니다. Java의 `final` 변수와 유사합니다.
    ```kotlin
    val myName = "H" // 초기화 후 변경 불가
    ```
* `var`: **Variable**의 약자로, 할당된 **값을 나중에 변경할 수 있는** 변수를 선언합니다.
    ```kotlin
    var coffeeCount = 0 // 값 변경 가능
    coffeeCount = coffeeCount + 1
    ```

### **2.2. 콘솔 출력 및 문자열 템플릿 (`println`, `$`)**

* `println()`: 괄호 안의 내용을 콘솔에 출력하고 줄바꿈을 합니다.
* 문자열 템플릿: 문자열 안에 변수나 표현식의 값을 쉽게 삽입할 수 있는 기능입니다. `$변수명` 또는 `${표현식}` 형태로 사용합니다.
    ```kotlin
    val name = "Kotlin"
    println("Hello, $name") // $변수명
    println("1 + 2 = ${1 + 2}") // ${표현식}
    ```

### **2.3. 조건문 (Conditional Statements)**

프로그램이 특정 조건에 따라 다른 경로를 실행하도록 할 때 사용합니다.

* **`if/else` 문:** 기본적인 조건 분기입니다.
    ```kotlin
    val age = 20
    if (age >= 19) {
        println("성인입니다.")
    } else {
        println("미성년자입니다.")
    }
    ```
* **`when` 문:** 여러 개의 조건을 간결하게 처리할 때 유용하며, `if-else if` 체인보다 가독성이 좋습니다. 범위(`in`), 여러 값(`6, 7`) 등을 지정할 수 있고, 값을 반환하는 표현식으로도 사용될 수 있습니다.
    ```kotlin
    val dayOfWeek = 3
    when (dayOfWeek) {
        1 -> println("월요일")
        in 2..5 -> println("평일") // 2부터 5까지
        6, 7 -> println("주말") // 6 또는 7
        else -> println("알 수 없음")
    }
    ```

---

## 3. 사용 예시 (Day1_Summary.md)

```kotlin
package org.example

fun main() {
    // 1. val (읽기 전용/immutable) 변수 선언
    val myName = "H"
    val currentYear = 2025
    val piValue = 3.14159

    println("안녕하세요, 제 이름은 $myName 입니다.")
    println("현재 연도는 $currentYear 년 입니다.") // 이전에 공백 오류 수정 경험
    println("원주율 값은 $piValue 입니다.")

    // 2. var (변경 가능/mutable) 변수 선언 및 값 변경
    var currentStatus = "Kotlin 학습 중"
    println("현재 상태 : $currentStatus")

    currentStatus = "IntelliJ IDEA 적응 중"
    println("변경 후 상태: $currentStatus")

    var coffeeCount = 0
    println("마신 커피 잔 수: $coffeeCount") // 이전에 $currentStatus -> $coffeeCount 오류 수정 경험
    coffeeCount += 1
    println("한 잔 더! 총 마신 커피 잔 수: $coffeeCount")

    // 3. Boolean 타입 변수 선언
    val isSunny = true
    println("오늘 날씨는 화창한가요? $isSunny")

    // 4. if/else 조건문 사용 예제
    val age = 20
    if (age >= 19) {
        println("나이: $age -> 성인입니다.")
    } else {
        println("나이: $age -> 미성년자입니다.")
    }

    val temperature = 25
    if (temperature > 30) {
        println("온도: $temperature -> 매우 덥습니다.")
    } else if (temperature > 20) {
        println("온도: $temperature -> 쾌적한 날씨입니다.")
    } else {
        println("온도: $temperature -> 시원합니다.")
    }

    // 5. when 조건문 사용 예제
    val dayOfWeek = 3
    when (dayOfWeek) {
        1 -> println("요일: $dayOfWeek -> 월요일입니다.")
        2 -> println("요일: $dayOfWeek -> 화요일입니다.")
        3 -> println("요일: $dayOfWeek -> 수요일입니다.")
        in 4..5 -> println("요일: $dayOfWeek -> 목요일 또는 금요일입니다.")
        6, 7 -> println("요일: $dayOfWeek -> 주말입니다.")
        else -> println("요일: $dayOfWeek -> 알 수 없는 요일입니다.")
    }

    val score = 85
    when (score) {
        in 90..100 -> println("점수: $score -> A 학점")
        in 80..89 -> println("점수: $score -> B 학점")
        in 70..79 -> println("점수: $score -> C 학점")
        else -> println("점수: $score -> F 학점")
    }

    val grade = when (score) {
        in 90..100 -> "A"
        in 80..89 -> "B"
        in 70..79 -> "C"
        else -> "F"
    }
    println("최종 학점은 $grade 입니다.")
}

---

## 1. 배운 내용 요약

* ... (기존 내용) ...
* **반복문 (`for`, `while`):** `for` (범위, 역순, 단계), `forEachIndexed` (컬렉션), `while`, `do-while` 문을 사용하여 코드 블록을 반복 실행하는 방법을 학습했습니다.

---

## 2. 문법 개념 간단히 설명

### 2.4. 반복문 (Loops)

코드 블록을 여러 번 반복하여 실행할 때 사용합니다.

* **`for` 문:** 정해진 횟수만큼 반복하거나 컬렉션을 순회할 때 주로 사용합니다. 범위(`..`, `downTo`, `step`)나 컬렉션(`.forEach`, `.forEachIndexed`)과 함께 사용합니다.
    ```kotlin
    // 1부터 5까지
    for (i in 1..5) { println(i) }
    // 5부터 1까지 역순
    for (i in 5 downTo 1) { println(i) }
    // 1부터 10까지 2씩 증가
    for (i in 1..10 step 2) { println(i) }
    // 리스트 순회
    val items = listOf("A", "B")
    for (item in items) { println(item) }
    ```
* **`while` 문:** 특정 조건이 참(true)인 동안 코드 블록을 반복 실행합니다. 조건이 거짓(false)이 되면 반복을 멈춥니다.
    ```kotlin
    var count = 0
    while (count < 3) {
        println(count)
        count++
    }
    ```
* **`do-while` 문:** `while` 문과 유사하지만, 코드 블록을 **최소 한 번** 실행한 후 조건을 검사합니다.
    ```kotlin
    var input: String
    do {
        print("입력: ")
        input = readlnOrNull() ?: ""
    } while (input != "exit")
    ```
