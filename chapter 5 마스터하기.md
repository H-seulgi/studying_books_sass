## chapter 5 마스터하기

### 연산자의 종류
프로그래밍에서 사용하는 연산자는 계산의 순서나 기호까지도 이미 알고 있는것과 크게 다르지 않다. 다만 수학시간에 배우지 않은 몇가지 연산자가 더 있을뿐이다. sass에서도 다른 프로그래밍 언어와 같은 연산자를 사용한다. 다른 언어와 차이가 있다면 숫자로 된 색상 값이나 문자로 된 속성 값 등에도 연산을 사용할 수 있으며 각각의 경우에서 사용하는 연산자가 다르다는 점이다.

- 사칙연산자<br>
기본 사칙 연산을 할 수 있다. 기본적인 수학 규칙인 덧셈과 뺄셈보다 곱셈과 나눗셈을 먼저하고 괄호를 사용한 계산을 가장 우선시한다. 

```scss
//나누기
.america{
height: (30px/7);
}

//나머지
.espresso{
height: (30px ÷ 7);
}
```

### 불(boolean)
비교/일치 연산자는 결과값으로 true(참) 또는 false(거짓)를 갖는다. 다음에 나올 제어문은 조건 식이 참일 경우에만 실행되기 때문에 boolean 값을 사용할 수 밖에 없다.

[연산의 결과값이 false인 경우]
- 비교/관계 연산자의 결과가 거짓인 경우
- null
- false 일경우

[true와 false의 구분]
```scss
.americano{
@if 8 < 5{
background-color: blue;
}
@if null{
background-color: yellow;
}
@if false{
background-color: red;
}
@if 3+5 == 8{
background-color: orange;
}

/*css 출력 값*/
.americano{
background-color: orange;
}

}
```
### 함수

- @function <br>
함수는 코드를 한데 묶어 놓고 필요할때마다 호출하여 사용하며 인자 값을 전달 할수 있다는 점이 mixin과 유사하다. 그 생김새와 사용 방법이 언뜻 비슷해 보이기 때문에 둘중에서 어떤것을 사용할지 결정하는 일이 어려울지도 모른다.

- 자주 사용하는 sass 함수 <br>
현실적으로 모든 함수를 외워서 사용할 수 없기 때문에 sass-lang 사이트에 있는 sass 함수 문서를 자주 보게 될 것이다. sass가 제공하는 함수는 색상, 문자열, 숫자, 리스트, map, 선택자 관련 함수들과 그 외의 기능을 하는 내장 함수가 있다.

함수 참조 : http://www.sass-lang.com/documentation/Sass/Script/Functions.html

- @at-root <br>
중첩 구조 안에서 부모에 종속되지 않고 하나의 선택자로 단독 선언하고 싶을 때 사용한다.

- @at-root(without:---)과 @at-root(width:---)<br>
@at-root는 기본적으로 중첩된 선택자에서만 적용되기 때문에 @media와 같은 구문으로 중첩되어 있을 경우에는 빠져 나올 수 없다. 따라서 선택자뿐만 아니라 중첩된 구문까지 어떤 경우에도 적용하기 위해서는 @at-root(without:---)를 사용한다.
여러 구문으로 중첩되어 있다면 @at-root(without:media supports)처럼 띄어쓰기로 구별하여 사용하며 구문뿐만 아니라 선택자까지 모든 중첩 구조에서 한번에 빠져 나오기 위해서는 @at-root(without:all)을 사용한다.
하지만 몇가지만 선택하여 중첩하고 싶다면 제외할 것들을 나열하는것보다 @at-root(without:---)로 중첩할 구문만 골라서 포함하는 것이 좋다. 예를 들어 @at-root(without:rule)를 사용하면 서택자 중첩만 유지하고 나머지 모든 구문에서는 빠져 나온다. 따라서 구문 중첩이 없을 경우에 사용하는 @at-root와 같다.