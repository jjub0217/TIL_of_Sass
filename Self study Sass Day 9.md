# Self study Sass Day 9

## 단위

### vw

- viewport - width 의 약자
- 뷰포트 넓이를 기준으로 % 단위로 움직인다. : 예시) width : 80vw  ==> 뷰포트 넓이의 80% 
- 화면 너비나 높이에 다른 상대적인 크기가 중요한 경우에 사용

### vh

- viewport - height 의 약자
- 뷰포트 높이를 기준으로 % 단위로 움직인다. : 예시) height: 50vh  ==> 뷰포트 높이의 50% 
- 화면 너비나 높이에 다른 상대적인 크기가 중요한 경우에 사용저

## 배경 이미지

### linear-gradient

- 예시 : linear-gradient(to right, #285a91 0%, #1f9cfd 100%) 
  - to right : 왼쪽에서 오른쪽 방향으로. #285a91 컬러를 투명도 0% 에서 #1f9cfd 컬러투명도 100%로 그라데이션 해라

###   background-blend-mode 

- 배경색과 이미지와 합성하는 속성

## Transform

### transition

```scss
<h1>CSS의 Animation과 Transition</h1>
<h2>Transition</h2>
<a class="btn" href="#">Transition 버튼</a>

// _______________________________________________

.btn{
    font-size: 30px;
    text-decoration: none;
    opacity: 1;
    transition: all 5s; // <------------------------
    
    &:hover{
        font-size: 50px;
        text-decoration: underline;
        opacity: 0.2;
    }
}
```

- 얘시1 : transition: all 5s
  - all : 바뀌는 속성들이 다 5s 동안을 통해서 애니메이션이 적용된다.

- 예시2 : transition: font-size 5s;
  - font-size 만 애니메이션된다. : 글씨만 서서히 커지고 나머지는 hover 하는 순간 바로 애니메이션 된다.
- 예시3 : transition: font-size 5s, opacity 10s
  - font-size 와 투명도만 애니메이션된다. : 글씨는 서서히 커지고, 투명도도 서서히 커지고, 나머지는 hover 하는 순간 바로 애니메이션 된다.

## 애니메이션

### @keyframes 

- 애니메이션은 `@keyframse` 라는 키워드로 시작하며, `@keyframse` 바로 옆에 애니메이션 이름을 지정해서 넣으면 된다. 
- 중괄호 안에 시간에 대한 `%` ( 퍼센트 )로 넣는다.

#### transform 

- 뭔가를 바꿔주는 애니메이션 속성

##### translate

- 위치를 바꿔주는 애니메이션 속성
- 기준값이 0, 0 이다. : 예시) transform : translate( 0,0 )

##### scale

- 크기를 바꿔주는 애니메이션 속성

###   animation-duration

- 애니메이션이 플레이되는 시간

###   animation-fill-mode

- 애니메이션이 끝났을때, 마지막 애니메이션 상태를 설정하고 싶을때 사용하는 속성

#### forwards

- animation-delay 딜레이가 지정되지 않았을때.

-  애니메이션 마지막 상태를, 마지막 애니매이션으로 설정한 채로 유지하고 싶을때 사용하는 속성

#### backwards

- animation-delay 딜레이 속성이 지정됬을때 처음상태로 시작

- 딜레이 시간동안 애니메이션 @keyframse 시간으로 돌아가는 속성

#### both

- forwards 와 backwards 속성 둘다 적용되는 속성

###   animation-iteration-count

- 애니메이션을 몇번인가를 반복하고 싶을때 사용하는 속성

### animation-delay

- 애니메이션 시작을 지연시키고 싶을때 사용하는 속성

---

---

# 오늘의 회고

애니메이션.... 속성이 너무 많아서 어렵다..

많이 만들어보는게 정답이겠지!!!!



