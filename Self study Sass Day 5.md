# Self study Sass Day 5

- playground : 테스트 코드나, 시험 코드 넣는 폴더

- 코드의 작성에 있어서, 한눈에 알아볼수 있도록 코딩하는 것이 좋으므로, 컬러 같은 경우에는 `#` 를 붙여서 나타내는 컬러에는 변수를 지정해서, <bR>컬러를 할당해서 코딩 하는 것이 좋다.  

  ```scss
  $color-white : #fff;
  $color-black : #000;
  $color-gray : #ccc;
  $color-gray-light : #efefef;
  $color-red : #f00;
  $color-blue : #00f;
  ```

- 바뀔수도 있는 컬러값 같은 경우에는 별도로, 바뀔수도 있는 컬러값의 속성을 변수를 생성하고, 해당 변수에 컬러값을 할당하는 것이 좋다. 

  ```scss
  $color-white : #fff;
  $color-black : #000;
  $color-gray : #ccc;
  $color-gray-light : #efefef;
  $color-red : #f00;
  $color-blue : #00f;
  
  $border-color : $color-blue;
  ```

---

---

# 오늘의 회고

원래 이틀전에 끝냈어야 하는 챕터인데... 이틀전인 날로 되는 새벽늦게까지 공부를 하는 바람에 그 이튿날을 통째로 날려버렸다....

그러면 어제 다 끝냈어야 하는 거 아니냐!!!!!!! .....지만.. 다른 공부로 하루종일 붙잡고 있느라 Sass 공부를 못하고 하루를 또 넘겨버렸다.... 

체력도 그지, 계획도 그지..하................. 

오늘 전부 끝내서 계획에 차질없도록 바싹 따라가자!!!

