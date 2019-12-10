## chapter 2 설치하기

### 컴파일러 설치하기

#### sass 컴파일러
sass는 브라우저가 바로 이해할 수 있는 언어가 아니기 때문에 컴파일러 이용하여 브라우저가 이해할수 있게 css로 변화해주는 과정이 필요하다. 각 os환경에 맞춰 sass 컴파일러를 설치해 보고 컴파일 하는 과정에 대해 알아보자.

#### 윈도우에서 설치하기
- 루비 설치
- sass 컴파일러 설치

#### 컴파일 옵션
sass는 다양한 옵션을 제공하는데 그 중 컴파일에 관련된 몇가지 옵션에 대해 자세히 살펴보도록 하자. 옵션에 명령 프롬프트에 입력하여 적용할 수 있으며, 각 에디터에 환경 설정 메뉴에서도 설정할 수 있다.

- --watch <br>
--watch는 단어 뜻처럼 변화를 주시하는 의미로, 이 옵션을 설정해 주면 컴파일 할때마다 명령어를 입력하지 않아도 자동으로 컴파일 한다.

[명령어] 자동 컴파일 - 파일 별
```cmd
sass --watch input.scss:output.css
```

- --style <br>
--style은 output 스타일에 대한 옵션으로 서로 다른 4가지 output 스타일을 제공한다.

```css

:nested
:expanded
:compact
:compressed

```

- :nested <br>
기본 sass 스타일로 아무런 옵션을 설정하지 않았다면 nested의 css 스타일로 컴파일 된다. sass 파일에 대괄호로 그룹핑 한 가장 첫 번째 선택자를 기준으로 들여쓰기 되기 때문에 html 파일을 확인하지 않고도 어떤 구조인지 쉽게 알 수 있으며, 각 속성은 한줄씩 컴파일 된다.

[명령어] :nested 옵션 적용
```cmd
sass --watch input.scss:output.css --style nested
```

- :expanded <br>
사용자가 선언한 순서대로 출력되는 일반적인 css 스타일로 각 속성은 규칙 내에서 들여 쓰기가 되며 한줄씩 컴파일된다.

[명령어] :expanded 옵션 적용
```cmd
sass --watch input.scss:output.css --style expanded
```

- :compact <br>
:nested 와 :expanded보다 공백이 적은 스타일로 모든 속성이 한줄에 선언된다.

[명령어] :compact 옵션 적용
```cmd
sass --watch input.scss:output.css --style compact
```

- :compressed <br>
최소한의 공백을 차지하는 스타일로 모든 속성간의 공백과 줄 바꿈없이 컴파일 된다. 압축 형태기이 때문에 유지보수에는 어려움이 있으나 배포 버전에 포함되는 경우 :compressed 를 적용하면 용량을 최소화하는데 도움이 된다.

[명령어] :compressed 옵션 적용
```cmd
sass --watch input.scss:output.css --style compressed
```