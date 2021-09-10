# Self study Sass Day 6

- 대표적으로 공통으로 여러 페이지에 들어가는 body css 같은 경우는 base 로 빼서, 이 역시 Partial(파샬) 로 만들어 import 해주는것이 좋다.

- 추상화적인 Partial( Scss 코드들 )들은 abstracts ("추상화") 라는 폴더로 빼서 모아놓는게 좋다.

- media query  부분을 적용시킬때는, 해당 media query 수정되는 부분이, 기본 부분 아래에 있어야 한다. 그렇지 않으면 media query 수정 되는 부분은 적용되지 않는다. 

  ```scss
  // 예시)
  
  .box {
      
      &,&-inner { // <- 기본 border css 적용되는 부분 
          border: 3px solid $border-color;
      }
  
      // ┌ 미디어 쿼리 border css 적용되는 부분    
      // 1201 이상
      @media screen and (min-width: 1201px) {
          border: 10px solid $border-color;
      }
  
      @media screen and (min-width: 601px) and (max-width:899px) {
          border: 2px solid $border-color;
      }
  
      // 600 이하 
      @media screen and (max-width: 600px) {
          border: none;
      }
  
  }
  ```

## @content

#### media query-mixin-include-content

- 원래 @mixin 과 @include을 사용할때, @include에는 인수만 들어가지 `{ }` (중괄호) 부분은 없었다. <br>하지만, `{ }` (중괄호) 부분을 사용할수 있는데, 이때 사용하는 것이 @content 이다. 

- @mixin에 @content 를 하고, @include 부분에 `{ }`(중괄호) 를 한 뒤에, 중괄호 안에 넣은 코드들이, @content 한 부분으로 들어가게 된다.

  ```scss
  // 예시)
  
  
  // _mixin.scss
  @mixin mediaQuery($screen-width) {
  
      @if($screen-width=='phone') {
          @media screen and (max-width: 600px) {
              @content
          };
      }
      @else if($screen-width=='tablet-land') {
          @media screen and (min-width: 601px) and (max-width:899px) {
              @content
          };
      }
      @else if($screen-width=='desktop-big') {
          @media screen and (min-width: 1201px) {
              @content
          };
      }
      @else {
  
      }
  }
  
  //______________________________________________________________________________
  
  //index.scss
  .box {
  
      &,
      &-inner {
          border: 3px solid $border-color;
      }
  
      // 1201 이상 : Desktop Big
      @include mediaQuery('desktop-big'){
          border: 10px solid $border-color;
      };
  
      // tablet-land : 태블릿 옆으로 뉘인거
      @include mediaQuery('tablet-land'){
          border: 2px solid $border-color;
      };
  
      // phone : 600 이하 
      @include mediaQuery('phone'){
          border: none;
      };
  }
  
  ```

---

---

# 오늘의 회고

이번 챕터에서는 @content 를 배우게 되었다. 

@include 에서는 원래 인수만 들어가는 `( )` (소괄호) 만 사용되는 줄 알았는데, @mixin 부분에 @content 를 쓰면, @include 에도 `{ }`(중괄호) 도 쓰일수 있다는 것을 알게 되었다. 

Sass 를 배우면 배울수록, 함수처럼 쓰이는 부분이 많은거 같아서 너무 용이하고 편리한거 같다. \