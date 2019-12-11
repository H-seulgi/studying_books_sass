## chapter 3 시작하기
### 파일 관리
- @import
css에서는 현재 파일에 다른 css파일을 불러오는 @import라는 속성이 있다. 이 속성을 사용하면 의도에 따라 코드를 잘게 쪼개어 효율적으로 유지 보수할 수 있는 방법을 찾을 수 있다.
하지만 @import로 선언되는 css 마다 http 요청을 발생하므로 웹 페이지 성능 저하의 원인이 된다 하여 사용을 지양하고 있다.

@import 사용 예시
```scss
@import 'espresso';

body{
font:100% Helvetica, sans-serif;
background-color:#efefef;
}
```

```css
html, body, ul, ol{
margin: 0;
padding: 0;
}

body{
font:100% Helvetica, sans-serif;
background-color:#efefef;
}
```

@import 작성 방법에 따른 sass 파일 로딩 가능/불가능 여부

[scss 파일을 불러 올 수 있는 경우]

```scss
@import "espresso";
@import "espress.scss";
@import "sass/espresso";
@import "sass/espresso.scss";
```

[scss 파일을 불러 올 수 없는 경우]

```scss
@import "espresso.css";
@import "http://naver.com/espresso";
@import url('http://naver.com/espress');
@import "espress" print;
```

### 주석
sass는 css파일에 노출되지 않는 주석을 제공한다. 사용할 수 있는 주석은 여러줄(/**/)형태와 한줄(//)형태가 있다. 컴파일 된 css파일에 노출되지 않는 주석은 한 줄 주석이다. 여러 줄 주석은 scss파일과 css파일에 모두 드러난다.

### 중첩
html을 작성할 때 중첩된 계층 구조를 볼 수 있다. sass도 html과 비슷한 형식의 중첩 작성법을 제공하여 css 작성법으로 예상하기 힘든 요소 간의 관계를 조금 더 추리해 볼 수 있도록 돕는다. 하지만 지나치게 중첩된 규칙은 필요 이상의 코드를 만들어 내어 유지보수하기 더욱 어렵고 복잡해진다는 사실을 염두해 두자.

- 중첩 규칙<br>
sass는 html을 작성하듯이 선택자의 정의 안에 자식 선택자를 정의할 수 있다. 이와 같은 중첩 규칙으로 sass를 작성한다면 부모 선택자가 반복해서 작성하지 않아도 되기 때문에 중첩이 많아지더라도 코드의 레이아웃을 간결하게 해준다. 중첩이 깊어지더라도 코드의 레이아웃을 보다 깔끔하게 해주어 가독성이 높아지므로 css를 정리하기도 편리해진다.

- 부모 선택자 참조(&)<br>
선택자 대신 & 기호를 쓰는 방법이 있다. &가 굉장히 유용한 이유는 가상 클래스, 가상 요소, 속성 선택자, class나 id 셀러터를 사용하기에 매우 편리하기 때문이다.

- 속성의 중첩 <br>
css 속서에는 margin-top, margin-right, margin-bottom, margin-left와 같이 속성 명에 하이픈을 붙여 세부적으로 나누어 쓸 수 있는 속성이 있다. sass 중첩에 사용하면 이런 세세한 속성들을 가독성은 높으면서도 간단하게 작성할 수 있다.

- 중첩된 @import<br>
코드를 모듈화하여 파일 분할을 했다면 특정 부모 선택자에만 선택한 모듈이 적용될 수 있도록 @import를 사용할 수 있다. 중첩에 모듈 파일을 import하는 방법이다.
@import 는 원활한 유지보수를 위해 문서 최상단에서 사용하는 것이 좋고, 최상단 외 다른 위치에 사용한다면 의도에 따라 지정한 위치에 사용하는것이 좋다. 하지만, sass의 @import의 css 선택자 또는 @media의 중첩 내에서도 사용할 수 있도록 준비되어 있다.

- 중첩 제한 <br>
sass를 처음 사용할때 가장 흥미를 느낄 수 있는 부분이 바로 중첩이다. 적용하기 편하고 규칙이 단순해 보이기 때문이다. 그렇기 때문에 남용되기 쉬워 불필요한 코드가 증가하는 문제점도 있다. 중첩에 제한을 두는 이유는 이러한 문제를 방지하기 위해서이다.
