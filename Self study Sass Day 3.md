# Self study Sass Day 3

## Nesting

- Nest : 둥지 라는 의미
- Nersting 이라는 것과 Tree 구조는 동일한 의미이다.

### &

- 어떤 한 html 요소에 적용시키는 css 객체 안에, 중첩 객체로, 해당 요소의 모든 자식 요소 또는, 직계자식에 적용시키는 객체를 & 기호를 사용해, 넣을수 있다. 

  - **직계자식에 적용시키는 css 중첩 객체를 사용 할때는 `&` 를 쓴다.** : 이때 & 기호는 중첩되어있는 객체가 속해있는 바로 윗 요소이다.
  - 중첩되어있는 객체가 속해있는 요소. 바로 자신을 나타낼때 `& `를 쓴다

  ```scss
  //예시 : 모든 자식 요소에 css 적용)
  
  
  <div id="box1">
  	<a href="#">button</a>
  </div>
  
  //--------------------------------------------------
  
  #box1{
      font-size: 40px;
      background-color: #ffcccc;
      border-radius: 20px;
  
      a{
        color:#a22;
        text-decoration: none;  
      }
  }
  ```

  ```scss
  // 예시 : 바로 자신을 나타낼때 & 를 쓴다
  
  
  
     <div id="box1">
          <div id="box1-title">box1</div>
  	</div>
  
  //--------------------------------------------------
   #box1 {
      font-size: 40px;
      background-color: #ffcccc;
      border-radius: 20px;
      border: 3px solid #f00;
      box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
  
       
       &-title{ // ─────────────────────┐           ┌───── #box1-title{
         font-style: italic;//		  │     =     │		     font-style: italic;
         text-decoration: underline;//  ├─ ───────  ┤	  	     text-decoration: underline
      }// ──────────────────────────────┘			  └──────  }	
  }
  
  ```

  ```scss
  //예시1 : &  기호를 사용 - 직계자식 요소에 css 적용)
  
  
  <div id="box1">
  	<a href="#">button</a>
  </div>
  
  //--------------------------------------------------
  
  #box1{
      font-size: 40px;
      background-color: #ffcccc;
      border-radius: 20px;
  
      & > a{ // ───────────────────┐           ┌───── #box1 > a {
        color:#a22;//			     │     =   	 │		     color:#a22;
        text-decoration: none;//   ├─ ───────  ┤	  	     text-decoration: none
      }// ─────────────────────────┘			 └──────  }	
  }
  ```

  ```scss
  //예시2 : &  기호를 사용 - 직계자식 요소에 css 적용)
  
  
  <div id="box1">
  	<a href="#">button</a>
  </div>
  
  //--------------------------------------------------
  
  #box1 {
      font-size: 40px;
      background-color: #ffcccc;
      border-radius: 20px;
      border: 3px solid #f00;
      box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
  
      // ┌> 여기에서 & 는 #box1 을 나타낸다.
       & > a{ // ───────────────────────────────┐           ┌───── #box1 > a {
        	color:#a22;//			              │           │		     color:#a22;
          text-decoration: none;/*              │           └──────	 text-decoration: none }
              					              │    ===                                           */
           // ┌> 여기에서 & sms #box1 > a 를 나타낸다.
           &:hover{ //            			  │	          ┌───── #box1 > a:hover {
                color:#000;//			          │           │		     color:#000;
                text-decoration: underline;//   │           │	  	     text-decoration: underline;
              }//                               │			  └──────  }	
      }// ──────────────────────────────────────┘
    }
  ```

## Nesting - 미디어 쿼리

- 미디어 쿼리를 적용시킬 요소의, css 적용 객체의 중첩으로, `@media screen and (max-width: 500px){   }` 를 집어 넣으면 된다.

  ```scss
  // 예제)
  
  #box1 {
  
    @media screen and (max-width: 500px){ // 최대 넓이가 500px 까지의 스타일 ( 500px 보다 작을때 )
      font-size: 20px;
    }
  
    @media screen and (min-width: 501px) and (max-width: 900px){ // 최소 넓이가 501px 부터  최대 넓이 900px까지의 스타일 
        font-size: 24px;
    }
  
    font-size: 40px;
    background-color: #ffcccc;
    border-radius: 20px;
    border: 3px solid #f00;
    box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
  
    &:hover {
      background-color: #ccc;
        
      @media screen and (max-width: 500px){
        background-color: #999;
      }
    }
  ```

  

## Mixin - include

- 여러가지 css 속성들을 하나의 그룹으로 묶어서 여러군데에 재사용할수 있는 기능

- @Mixin / @include 형태로, 함수처럼 매개변수와 인수도 사용할수 있어, 매우 간편하고 편리하고 활용도가 높다.

- Mixin 의 매개변수에는 반드시 $ ( 달러 기호 )를 함께 사용해야 한다. 

  ```scss
  // 예제)
  
  
      <div id="box1">
          box1<br>
          <a href="#">button1</a>
          <div id="box2">
              box2<br>
              <a href="#">button2</a>
          </div>
      </div>
  
  
  @mixin fontSizeBgColor($fontSize, $bgColor) { // <- css 속성들을 하나로 묶는 이름과, 각기 다를 속성 값들을 매개변수에 넣는다.
    font-size: $fontSize;
    background-color: $bgColor;
  }
  
  #box1 {
        @include fontSizeBgColor(40px, #ffcccc ); // <- Mixin 에 쓰인 묶는 이름을과, 각기 다르게 넣은 속성값들을 인수에 넣는다.
  }
  
  #box1 #box2 {
    @include fontSizeBgColor(20px, #e9e9e9 ); // <- Mixin 에 쓰인 묶는 이름을과, 각기 다르게 넣은 속성값들을 인수에 넣는다.
  }
  
  ```

---

---

# 오늘의 회고 

와우!!!!! Nesting 이랑 Mixin ... 신세계다. 

## Nesting 

css 적용 묶음들을 마치 객체처럼 사용할수 있어서 너무 편리한것 같다. <br>객체에 중첩 객체에, 거기에 또 중첩객체처럼 사용할수 있다니.... 너무 편리하다ㅠㅠㅠㅠ 

다만, 여기서 주의해야 할것은 **<u>가독성</u>**이다.

너무 Nesting 으로 중첩 중첩을 하게 된다면, 이  css 묶음이 어디에 속해 있는지 찾아보려면 스크롤을 위로위로 올려봐야 하는 불편성과 가독성이 좋지 <br>않을수도 있으니, 너무 Nesting 문법을 모두 다 쓰지 않는것이 좋을것 같다. 

## Mixin - include

너무너무 신세계다ㅠㅠㅠㅠㅠㅠㅠ

그동안 css 를 만들면서 중복되는 속성들을 모듈화 한다고 이 파일 저 파일 왔다갔다 하면서 복사 붙여넣기 하는것도 힘들었고, <br>이 속성은 중복되는데, 값들이 각기 다르다면 모듈화 하기도 어려웠는데, Mixin 과 include 가 함수처럼 동작해주니까 너무 편리한거 같다.

Sass 를 다 배우고 나면 CSS 를 마구 만들수 있을 것 같은 기분이다. 

...... 이렇게 편하고 편리한건.. 초반에만 있겠지ㅠ? 이제 갈수록 어려워지겠지........? 긴장 늦추지 말자.

 

