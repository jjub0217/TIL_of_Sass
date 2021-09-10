# Self study Sass Day 4

## extend

- 코드의 재사용이 가능한 기능

- 여러 요소들에, 똑같은 속성과 속성값이 적용되어있다면, 그 부분을 한데 묶어서 재사용 가능하게끔 해주는 기능.

- `%` 기호와, 함수이름처럼 속성과 속성값들의 묶음 이름을 넣으면 된다. <br>그리고, 해당 묶음을 써먹을때는 `@` 기호와 함께 `extend` 라고 하고 %랑 같이 내가 지었던 묶음이름을 집어 넣으면 된다. 

- 주의점 : Moxin 과 달리, 매개변수와 인수가 필요없다.

  ```scss
  // 예시)
  
  
  // extend
  %boxShape {
    border-radius: 20px;
    border: 3px solid #f00;
    box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
  }
  
  
  #box1{
  	@extend %boxShape;
  }
  
  #box2{
      @extend %boxShape;
  }
  ```

## Partial(파샬)

- "부분적인"
- 여러 코드들을 묶어서 별도의 다른 파일로 나눠서 저장하고, 그 파일을 가져다 쓸수 있는 기능

- 모듈화 파일을 만드는거라고 생각하면 된다. 
  - 공통적인 코드를 묶어서 **`_` (언더스코어.언더바) 기호와 함께 파일이름**을 만들고, <br>**해당 파일을 갖다 쓸 파일안에서 `@import "(공통소스 묶은 파일 이름)"`** 을 집어 넣으면 된다.  <br>여기서 주의할점!!!! `"(공통소스 묶은 파일 이름)"` 여기 **따옴표 안에 확장자 이름이 들어가면 안된다.** 
    -  `_` (언더스코어.언더바) 기호로 시작하는 이름의 파일은 컴파일이 되지 않는다. Partial 기능을 위해서 컴파일이 되지 않는것도 있지만, <br>**Sass 는 `_ ` 로 시작하는 파일 이름은 컴파일이 되지 않는다.** 

```scss
// 예시)


// App.scss
@import "mixins" // <- mixins.scss 파일을 가져오겠다.
@import "partial/styles"; // <- styles.scss 파일을 가져오겠다.

#box1{
     @include fontSizeBgColor(40px, #ffcccc); // <- mixin fontSizeBgColor 을 가져다 쓰겠다.
     @extend %boxShape; // <- 같은 속성과 같은 속성값들의 묶음으로 만든 %boxShape 이라는 파일을 extend 기능을 사용해서 가져다 쓰겠다.
    
        &>a {
        @include linkStyle(#a22); // <- mixin linkStyle 을 가져다 쓰겠다.
    	}
	
}


// _mixins.scss : 이 파일은 컴파일 되지 않는다.
@mixin fontSizeBgColor($fontSize, $bgColor) {
    font-size: $fontSize;
    background-color: $bgColor;
  }
  
  @mixin linkStyle($textColor, $textDeco: none) {
    color: $textColor;
    text-decoration: $textDeco;
  }


// _styles.scss : 이 파일은 컴파일 되지 않는다.
// extend
%boxShape {
    border-radius: 20px;
    border: 3px solid #f00;
    box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
  }
```

## if / if...else / if...else..if

- Sass 에서 if 문 / if else 문 / if else if 문을 사용할 수 있다. 

- Sass 안에서의 조건문 규칙

  1. **`if` 와 `else if` 와 `else` 앞에 반드시 `@` 기호를 붙여야 한다.**  

  2. **`@if` 뒤에는 반드시 `$` 기호를 붙인 변수를 써야 한다.** 
  3. `===`가 아니라 **`==` 를 써야 한다.**

```scss
// 예제)



<div id="box1">box1</div>
<div id="box2">box2</div>
<div id="box3">box3</div>



@mixin textAndBgColor($textColor, $bgColor){
    color: $textColor;
    background-color: $bgColor;
}

@mixin theme($mood){
    @if $mood == 'light' {
        @include textAndBgColor(#333, #ff0);
    }
    @else if $mood == 'dark'{
        @include textAndBgColor(#fff, #000);
    }
    @else{
        @include textAndBgColor(#f00, #aaa);
    }
}


#box1{
    @include theme('light')
}
#box2{
    @include theme('dark')
}
#box3{
    @include theme('ddddd')
}

```

---

---

# 오늘의 회고

오늘도 역시나 Sass 는 신세계라는걸 느꼈다. <br>CSS 인데 CSS 안에서 조건문이 사용되다니!!!!!!!! 싱기방기.

그리고 처음에 배웠던것마냥 @mixin 이 속성들로만 묶어져있는 묶음이라기 보다는, 함수처럼 쓰이는 것을 보고 너무너무 놀라웠다. 

자바스크립트를 배우고 난 뒤에 프로젝트를 하면서 CSS 를 작업할때, CSS 도 함수마냥 재사용할수 있다면 얼마나 좋을까... 라고 생각했었는데, 그게 Sass 에 있었다니.... 너무너무 편리한것 같다. 

앞으로도 Sass 가 마냥 편리하고 놀라운 언어였으면 좋겠다....

