# Self study Sass Day 11

# pseudo element ( 가상 요소 )

- 수도[^1] 엘리먼트 

### before

- `특정 요소::before` 의 형태로 작성하는 속성
- 특정 요소 앞에 들어갈 가상의 요소

### after

- `특정 요소::after` 의 형태로 작성하는 속성

- 특정 요소 뒤에 들어갈 가상의 요소

[^1]:  '가상' 이라는 뜻

### float

- '부유'(공중에 떠있는) 라는 뜻이다. 
- 자식요소에 float 속성을 주게 되면, 부모요소가 자식요소를 잃어버린다. 이때의 해결방법은 `clearfix` 와, `after` 가상 요소이다. 

#### .clearfix

- float 을 준 요소의 밑에 또 다른 요소를 주고, 해당 요소의 class 이름은 `clearfix` 라고 준 다음, 해당 `clearfix` 요소에 CSS 속성으로 `clear` 라는 속성을 주고, 해당 속성의 값으로 `both` 를 주면 해결된다. 

```scss
// 예시)


// pseudo.html
<div class="box-parent">
    <div class="box-child"></div>
    <div class="box-child"></div>
    <div class="box-child"></div>

    <div class="clearfix"></div>
</div>


// pseudo.scss
.box-parent{

    padding: 20px;
    background-color: #00f;

    .box-child{
        width: 200px;
        height: 200px;
        background-color: #f00;
        border: 1px solid #ff0;
        float: left;
    }
        
    .clearfix{
         clear: both;
     }
}
```

#### ::after

```scss
// 예시)


// pseudo.html
<div class="box-parent">

    <div class="box-child"></div>
    <div class="box-child"></div>
    <div class="box-child"></div>

</div>


// pseudo.scss
.box-parent{

    padding: 20px;
    background-color: #00f;

    .box-child{
        width: 200px;
        height: 200px;
        background-color: #f00;
        border: 1px solid #ff0;
        float: left;
    }
        
    &::after{
        content: '';
        display: block;
        clear: left;
    }
}
```

```scss
// ::after 예시를 mixin으로 해결

// 예시)


// pseudo.html
<div class="box-parent">

    <div class="box-child"></div>
    <div class="box-child"></div>
    <div class="box-child"></div>

</div>


// pseudo.scss
@mixin clearfix {
    &::after {
        content: '';
        display: block;
        clear: left;
    }
}

.box-parent{

    padding: 20px;
    background-color: #00f;

    .box-child{
        width: 200px;
        height: 200px;
        background-color: #f00;
        border: 1px solid #ff0;
        float: left;
    }
        
    @include clearfix();
}
```

### not

- 특정 요소를 제외시켜주는 속성

```scss
// 예시)

// pseudo.html
<div class="box-parent">

    <div class="box-child"></div>
    <div class="box-child"></div>
    <div class="box-child"></div>

</div>


// pseudo.scss
.box-parent {

    padding: 20px;
    background-color: #00f;

    .box-child {
        width: 200px;
        height: 200px;
        background-color: #f00;
        border: 1px solid #ff0;
        float: left;

        &:not(:last-child){ // <- last-child 인 마지막 요소를 제외(not)한 요소들
            margin-right: 40px;
        }
    }
    
    @include clearfix()
}
```

---

---

# 오늘의 회고

오늘은 부트캡프에서 배웠던 `float` 와, float 해제 방법에 대해서 다시 배웠다. <br>그때의 기억이 새록새록 났다...ㅋ

근데, 그때도 헷갈렸던게 `:nth-child` 랑 `:nth-last-child` , `:nth-last-of-type` , `:nth-of-type` , `:last-child` 같은거였다. 

이게 순서를 잘 생각해야, 뒤죽박죽으로 안됐던걸로 기억하는데..... 그래서 엄청 헷갈렸는데.. 이번 Sass 에서는 CSS 를 배우는 게 아니라서 그냥 가볍게 훑고 지나가버린거라서 여전히 확실히 이해를 못한채로 남겨졋다...ㅎ

그래도 `:not` 을 사용한 속성은 이번에 써먹어봐서 어떻게 쓰게 되는건지는 감을 익히게 된것 같다.