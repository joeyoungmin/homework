# apple 제품 카드
그리드를 사용하여 구현하고 구현 결과를 움직이는 이미지로 생성하여 삽입해주세요.

---

[4번] 과제구현
https://joeyoungmin.github.io/homework/apple/apple.html

# ❗시작❗

>이번 과제엔 요구사항이 3번보다 많지 않기 때문에 평소에 퍼블리싱 하던대로 해보았습니다. 이번 페이지 작성엔 제 개인적인 생각을 많이 넣어서 작성해보겠습니다.(움직이는 동영상은 맨 아래 동영상으로 첨부하겠습니다.)

## 🤔과제 요구사항
>**선생님 요구사항 간단 요약**
1.1024px 기준으로 반응형을 구현.
2.img태그는 X background-image로 구현.
3.픽셀 밀도에 따른 이미지 변경
4.theme.css파일에 있는 지정된 값 쓰기
5.일요일 10시까지 시간 준수 입니다.

### 과제 구현 내용
1.모바일 구현
> 제가 지방에서 퍼블리싱을 굉장히 잘못하고 있다는 사실을 과제를구현하던 중 깨달음이 있었습니다 모바일부터 작업을하면 굉장히 편하더군요.. 그래서 모바일부터 작성했습니다.

**대제목**
피드백 중 대제목을 놓친다는 피드백이 많아서 작성을 하려했는데, 과제 영상엔 보이지 않아 css를 사용해 구현화면에만 안보이게 설정을 해놓았습니다.
```
html)
<header class="header">
<h1 aria-hidden="true" class="screen-reader-only">apple</h1>
</header>

css)
.screen-reader-only {
position: absolute;화면에서 벗어나게 함
width: 1px;최소 크기로 설정
height: 1px;최소 크기로 설정
margin: -1px;화면에서 완전히 벗어남
overflow: hidden;내용 숨김
clip: rect(0, 0, 0, 0);보이지 않도록 클립
white-space: nowrap;한 줄로 만들기
}
```
---
**카드레이아웃**
- apple사이트를 많이 참고하며 제작하였습니다.
- 2번 과제 조건을 맞추기위해`img`태그는 사용 안하였고 `<main class="main">`를 사용하였고 `section`으로 메인 컨텐츠들을 다루었습니다. 여기서 `button`태그를 사용할때에 정말 고민을 많이 했습니다. 서브 사이트로 이동하기 위해 `a`태그를 안에 넣으니 키보드로 버튼이 2번 만들어지는 상황이 발생하여 앵커태그만 쓸지 버튼태그를 쓸지 고민을 많이 했었는데 과제는 레이아웃을 만드는 과제이기 때문에 button태그를 사용하였지만 만약 취업 후 서브페이지로 이동하는 버튼을 만들라고 한다면 앵커태그를 사용커태그를 사용하고 `role="button"` 속성을 사용할 것 같은데 이 부분은 선생님한테 피드백을 받고싶습니다.
```
<main class="main">
<section class="section1">
<h2 class="section01-title">iPad Pro</h2>
<p>놀라우리만치 얇다.</p>
<p>엄청나게 강력하다.</p>
<p><span>출시일 추후 공개</span></p>
<div class="button-wrap">
<button class="btn" aria-label="더 알아보기">더 알아보기</button>
<button class="btn" aria-label="가격보기">가격보기</button>
</div>
</section>
</main>
```
<small>section태그들의 구조는 전부 같습니다.</small>

---

**apple.css**

- **@import**
```
@import url(card-component.css);
//반복되는 컴포넌트들 옮김
@import url(base.css);
//웹폰트
@import url(reset.css);
// 최적화 및 초기화
@import url(./theme.css);
//과제구현 소스


```


- **.main**
그리드 사용과제이기에 그리드를 사용하였습니다.
```
.main {
    display: grid;
    grid-template-columns: 1fr;
    gap:var(--x-small-spacing);
}
```
---

- **section**
사이즈는 `theme.css`에 제공되어있는대로 작성하였고 background는 1-7까지 이미지가 다르기때문에 따로 작성하였습니다. 패딩사이즈도 `theme.css`제공되어 있는대로 작성하였습니다.
```
section{
    grid-column: 1;
    block-size: var(--size);
    background-size:cover;
    background-repeat: no-repeat;
    background-position: center;
    text-align: center;
    padding-top:var(--large-spacing);
}
```
---
- **h2,span**
위 내용과 똑같이 `theme.css`에 제공되어있는대로 작성하였습니다.

```
h2{
    font-size:var(--large-text);
    margin-top:var(--large-spacing);
    font-weight: bold;
    margin-bottom:var(--small-spacing);
}

span{
    color:var(--gray);
}
```
---
- **p**
p도 마찬가지지만, section1에 있는 마지막 `p`태그를 컨트롤 하기위해서 다음과 같이 작성하였습니다.
```
.section1>p:last-of-type{
    margin-top:var(--small-spacing);
    margin-bottom:var(--x-small-spacing);
}

section>p:last-of-type:not(.section1>p:last-of-type){
    margin-bottom:var(--x-small-spacing);
}
```
---
- **.button-wrap**
버튼 컨트롤을 위해 제작된 `div`로 넣을지 말지 고민을 많이 하였으나, 넣는게 컨트롤 시, 보다 효과적이라고 생각하여 넣게 되었습니다.

```
.button-wrap{
    display: grid;
    grid-template-columns: repeat(2, auto);
    gap: var(--base-spacing);
    justify-content: center;
}
```
---
- **.btn**
위 내용과 똑같이 `theme.css`에 제공되어있는대로 작성하였습니다.

```
.btn{
    padding: var(--x-small-spacing) var(--small-spacing);
    gap:var(--base-spacing);
    border-radius: var(--large-spacing);
}
```
---
**card-component.css**
>apple엔 겹치지않고 기본적인 코드들만 작성하였고 전에 혼자 작업할때엔 컨텐츠 하나당 하나의 컴포넌트를 운영했었는데 과제에 요구되는 컴포넌트는 1개인듯하여, 컴포넌트 구분 기준이 좀 애매하다고 생각이 들어서 반복성이 짙은 코드만 컴포넌트에 옮겨서 작성하였습니다. 컴포넌트 구분 기준에 대해서 명확한 피드백을 받고 싶습니다..!

- **픽셀 밀도에 따른 이미지 설정**
>html로는 srcset을 사용하여 작성 해본적이 많은데 background--image로는 안해보았고 아마도 이번주에 결석을 몇번 했었는데 제가 못들은건지 졸다가 넘어간건지 잘 모르겠어서 구글링하여 과제를 작성하였습니다. 좋은코드인지, 나쁜코드인지 인지가 불가능하여 이 부분 피드백 부탁드립니다..!

```
@media only screen and (min-resolution: 192dpi), 
       only screen and (-webkit-min-device-pixel-ratio: 2) {
        .section1{
            background-image: url(./../products/ipad_pro_2x.jpeg);
        }
        .section2{
            background-image: url(./../products/ipad_air_2x.jpeg);
        }
        .section3{
            background-image: url(./../products/iphone15_pro_2x.jpeg);
        }
        .section4{
            background-image: url(./../products/iphone15_2x.jpeg);
        }
        .section5{
            background-image: url(./../products/apple_watch_2x.jpeg);
        }
        .section6{
            background-image: url(./../products/macbook_air_2x.jpeg);
        }
        .section7{
            background-image: url(./../products/airpods_pro_2x.jpeg);
        }
}

@media only screen and (max-resolution: 191dpi), 
       only screen and (-webkit-min-device-pixel-ratio: 1) {
        .section1{
            background-image: url(./../products/ipad_pro.jpeg);
        }
        .section2{
            background-image: url(./../products/ipad_air.jpeg);
        }
        .section3{
            background-image: url(./../products/iphone15_pro.jpeg);
        }
        .section4{
            background-image: url(./../products/iphone15.jpeg);
        }
        .section5{
            background-image: url(./../products/apple_watch.jpeg);
        }
        .section6{
            background-image: url(./../products/macbook_air.jpeg);
        }
        .section7{
            background-image: url(./../products/airpods_pro.jpeg);
        }
}
```
---
-홀수번째 섹션과 짝수번째 섹션의 버튼 색상이 다르기 때문에 사용한 코드 및 `theme.css` 이행

```
section:nth-child(odd){
    color:var(--white);
}

section:nth-child(odd) button:nth-of-type(odd) {
    background-color: var(--blue-200);
    color: var(--white);
    border:none;
}

section:nth-child(even) button:nth-of-type(odd) {
    background-color: var(--black);
    color: var(--white);
    border:none;
}

section:nth-child(odd) button:nth-last-of-type(1){
    border:1px solid var(--blue-200);
    color: var(--blue-100);
    background-color: transparent;
}

section:nth-child(even) button:nth-last-of-type(1){
    border:1px solid var(--black);
    color: var(--black);
    background-color: transparent;
}

section:nth-child(odd) button:hover{
    background-color: var(--blue-100);
    color:var(--white);
}

section:nth-child(even) button:hover{
    background-color: var(--black);
    color:var(--white);
}
```

- **반응형으로 인한 구조 변경**

```
@media only screen and (min-width: 1024px) {
    @media only screen and (max-resolution: 191dpi), 
       only screen and (-webkit-min-device-pixel-ratio: 1){
        .section1{
            background-image: url(./../products/ipad_pro_wide.jpeg);
        }
        .section2{
            background-image: url(./../products/ipad_air_wide.jpeg);
        }
        .section3{
            background-image: url(./../products/iphone15_pro_wide.jpeg);
        }  
    }
    @media only screen and (max-resolution: 191dpi), 
       only screen and (-webkit-min-device-pixel-ratio: 2){
        .section1{
            background-image: url(./../products/ipad_pro_wide_2x.jpeg);
        }
        .section2{
            background-image: url(./../products/ipad_air_wide_2x.jpeg);
        }
        .section3{
            background-image: url(./../products/iphone15_pro_wide_2x.jpeg);
        }
    }

    section{
        padding-top:var( --extra-large-spacing);
    }
    h1{
        font-size:var(--extra-large-text)
    }
    p{
        font-size:var(--medium-text)
    }
    button{
        font-size:var(--x-small-text)
    }
    .main {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap:var(--x-small-spacing);
    }

    .main {
        display: grid;
        grid-template-columns: 1fr 1fr!important;
        gap:var(--x-small-spacing);
    }

    .section1,.section2,.section3{
        grid-column: 1/3;
    }
    .section5,.section7{
        grid-column: 2;
    }
}
```
---
- ***그리드를 사용하여 구현하고 구현 결과를 움직이는 이미지로 생성하여 삽입해주세요.***

https://github.com/user-attachments/assets/aed2d1c4-7cab-4afa-8921-a6ca18ef7adc
동영상 업로드 문제로 재 업로드하였습니다

