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

#### --sourcemap
--sourcemap 와 css 와 mapping 되는 sass의 정보를 알려주는 옵션으로, 최신 sass 버전에서는 기본 옵션으로 제공하고 있다. 따라서 최신 버전을 설치하였다면 별도 옵션을 설정하지 않아도 된다. 컴파일을 하면 (css 파일명).map 파일이 자동 생성되고 컴파일된 css 파일 가장 하단에 mapping 된 파일의 정보를 나타내는 /*# sourceMappingURL=파일명.css.map*/
의 주석이 생긴 것을 확인 할 수 있다. 이 옵션은 개발자 도구에서 요소 검사를 할때 scss팡ㄹ 명 코드 line number등의 정보를 나태나주기 때문에 디버깅하기 쉽다. 하지만 css파일에 출력되는 주석 때문에 때로는 스크립트 혹은 네트워크와의 오류를 발생하여 리다이렉트를 유발한다는 단점이 있다. 따라서 최종 배포 버전의 css에서는 /*# sourceMappingURL=파일명.css.map*/ 주석을
제거할 것을 권장한다.

#### --cache
--cache는 sass 템플릿 작업 및 여러 import 파일들을 더욱 빠르게 처리할 수 있도록 캐시 된 파일을 보관하는 옵션이다. sass의 기본 옵션으로 컴파일을 하면 .sass-cache라는 폴더가 자동 생성되고 관련 cache 파일이 저장된다. 만약 이 옵션을 제거하기를 원한다면 맨 처음 컴파일 할 때부터 다음과 같이 명령어를 입력해주면 된다.

[명령어] --cache 옵션 제거
```cmd
sass --watch input.scss:output.css --no-cache
```

### 컴파일 방법 소개
지금까지 명령 프롬포트에서 컴파일을 해보고 다양한 옵션을 활용해 보았다. 명령 프롬프트를 활용하면 가장 심플하고 확실하게 컴파일을 할 수 있지만, 매번 명령어를 입력해야 하는 일이 때로는 번거롭게 느껴지기도 한다.그럴 때는 이미 사용화되어 있는 툴을 활용하는 것도 좋은 방법이 될수 있다. 이번에는 컴파일을 도와주는 몇가지 유용한 툴에 대해 간단하게 소개하며 필요한 툴을 설치하여 사용해보자.

#### 컴파일 Tool
- prepros <br>
sass 뿐만 아니라 less, compass, stylus 등 다양한 css 전처리기에 대한 자동화를 제공한다.

- scout <br>
sass와 compass의 컴파일을 도와주며 무료로 사용할 수 있다.

- codekit <br>
mac에서만 사용할 수 있으며, sass, less, stylus, compass 등 다양한 css 전처리기에 대한 자동화를 제공한다.
특히 브라우저 자동 새로 고침 기능이 있어서 수정한 후 매번 새로 고침을 하는 번거로움을 줄여준다.

### LibSass
Sass는 루비 언어 기반으로 만들어진 도구이고, LibSass는 C/C++을 이용해서 만들어진 도구이다. 따라서 LibSass는 루비를 별도로 설치하지 않아도 된다.
LibSass는 Sass와 비교했을 때 컴파일 속도가 굉장히 빠르다는 장점을 가지고 있는데 프로젝트 후반부에 코드가 길어지더라도 금새 컴파일 된 css를 확인 할 수 있다.
LibSass로 컴파일을 하려면 SassC나 그 외 다른 실행 프로그램이 필요하다. SassC는 LibSass의 공식적인 실행 프로그램으로 항상 싱크를 유지하고 있다.
SassC는 LibSass를 포함한 git 서브 모듈을 사용한다. LibSass 소스를 복사해서 로컬 경로에 넣거나 설치하면 SassC를 사용할 수 있다. 하지만 SassC와 LibSass
는 문법 호환이 다르기 때문에 작업할 때 SassC의 스펙을 확인하고 해당 경로에서 정상적으로 컴파일 되는지 확인해야 한다.









