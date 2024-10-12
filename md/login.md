# ❗3주차과제❗

## 네이버 로그인 페이지

- ### 요구사항
- 구조(HTML)는 `login.html` 파일에 스타일(CSS)은 `login.css` 파일에 과제에 대한 설명은 `login.md` 파일에 작성한다.
- 네이버 로그인 과제 수행에 대한 설명을 `login.md` 파일에 작성하고 `homework` 폴더에 있는 `README.md`파일에 링크로 연결한다.


**`마크업`**
- 네이버 로고 및 체크박스 관련 이미지는 아래 `코드`를 활용한다.
이때 `<svg> 요소`를 사용할 수도 있고 `svg 형식`으로 저장한 후 `<img> 요소` 또는 `배경 이미지`(CSS Background)로도 사용할 수 있다.
- 로고 이미지는 ```<svg>``` 요소로 마크업 할 것
- 웹접근성을 고려하여 로그인 폼 서식을 마크업 할 것
 (레이블 제공의 경우 WAI-ARIA가 아닌 HTML 네이티브 방식으로 구현)  
- 아이디와 비밀번호는 필수 입력 서식임을 알 수 있도록 구현할 것
- IP 보안 텍스트 클릭 시 미리 제공 된 `pages/ip_secruity.html` 파일이 새창에 열리도록 구현할 것
- 로그인 상태 유지와 IP 보안 ON/OFF UI는 마우스 이외에 `키보드로도 조작 가능`하도록 구현할 것

**`스타일링`**

- 미디어 쿼리를 사용하여 반응형으로 구현할 것(768px 미만 모바일 / 768px 이상 데스크탑)
- 모바일 퍼스트로 스타일링 할 것
(공통 스타일과 모바일 스타일을 먼저 구현한 후 데스크탑 스타일을 재정의)
- 글자 크기 및 여백(margin 및 padding)은 모두 rem 단위로 설정할 것
- 기본 글자 크기는 `16px,` 기본 글자 색상은 `#121212`로 사용할 것
(Custom Properties 활용 추천)
- 로고 가로 230px, 가운데 배치    
- 포커스 스타일을 기본 색상이 아닌 커스텀 스타일로 변경할 것(색상 `#24388d`)
- 모바일 로그인 폼 로그인 폼의 가로 크기는 `100%`(좌/우 여백 각 20px 포함)로 설정할 것
- 모바일 환경에서 IP 보안 ON/OFF 스위치 UI는 사용자에게 제공되지 않도록 구현할 것
- 데스크탑 로그인 폼의 가로 크기는 500px(좌/우 여백 각 20px 포함)로 설정할 것
- 입력 서식 글자크기 및 세로 크기, 테두리 선 색상, 배경 색상은 다음과 같이 지정할 것
    
    `기본 상태` : 14px, 45px, #dadada, #fff
    
    `포커스 상태` : #03cf5d, #e9f0fd
    
- `로그인 버튼`의 글자 크기, 세로 크기, 글자 색상, 배경색상, 위쪽 여백은 다음과 같이 지정할 것
    
    16px, 45px, #fff, #03cf5d, 20px
    
- 로그인 상태 유지 및 IP 보안 ON/OFF `스위치 UI` 영역의 위쪽 여백은 10px로 지정할 것
- 로그인 상태유지 체크박스 배경 이미지 및 크기와 여백은 다음과 같이 지정할 것
    
    `선택안함` : unchecked.svg (제공한 ```<svg>```코드를 활용하여 이미지로 저장하여 사용)
    
    `선택함` : checked.svg (제공한 ```<svg>``` 코드를 활용하여 이미지로 저장하여 사용)
    
    가로 * 세로 : 24px * 24px
    
    배경 이미지 오른쪽 여백 : 5px
    
- `IP 보안` 스위치의 글자 크기는 16px, 글자 색상은 #121212로 지정할 것


> **구현설명 전 저는 이렇게 생각했습니다.**
section태그를 안쓴 이유는 로그인 폼에는 section 태그는 문서의 구획을 나누고 특정 주제를 나타내는 데 사용되기에 부적합하다고 느꼈고 대신 div,form,fieldset을 사용하여 입력 필드를 그룹화하는 것이 올바르다고 생각하였습니다.

**구현설명**
  
**`마크업 조건`**
- 네이버 로고 및 체크박스 관련 이미지는 아래 `코드`를 활용한다.
이때 `<svg> 요소`를 사용할 수도 있고 `svg 형식`으로 저장한 후 `<img> 요소` 또는 `배경 이미지`(CSS Background)로도 사용할 수 있다.
- 로고 이미지는 ```<svg>``` 요소로 마크업 할 것
**=> 해당 코드는 svg파일로 된 이미지였고 assets/login/3개의 파일을 넣어 사용하였습니다
해당코드 첨부**
```
1.네이버 로고 이미지
(html)
 <header class="header">
            <a href="http://www.naver.com">
                <img src="./../assets/login/naver-logo.svg" alt="네이버 로고">
            </a>
</header>
2.로그인 상태 유지에 대한 svg 이미지
(css)
.custom-checkbox {
    box-sizing: border-box;
    width: 24px;
    height: 24px;
    background: url("./../../assets/login/checkbox(unchecked).svg") center/cover no-repeat;
    margin-right: 5px;
    display: inline-block;
},
.login-state input:checked + label .custom-checkbox {
    width:24px;
    height:24px;
    background: url("./../../assets/login/checkbox(checked).svg") center/cover no-repeat; /* 체크된 이미지 */
}
```

- **웹접근성을 고려하여 로그인 폼 서식을 마크업 할 것**

1.모든 입력 필드에 ```<label>``` 요소가 포함되어 있어, 스크린 리더와 같은 보조 기술 사용자가 각 입력의 목적을 이해할 수 있도록 하였습니다.
```
<div class="id input">
 <label for="username">아이디</label>
 <input type="text" id="username" placeholder="아이디" name="username" required>
<span class="error-message">아이디는 이메일 형식으로 입력해주세요.</span>
</div>
                
<div class="password input">
<label for="password">비밀번호</label>
<input type="password" id="password" name="password" placeholder="비밀번호" required>
<span class="error-message">비밀번호는 10자리 이상 입력해주세요.</span>
</div>
(이하생략)
```

- **required 속성을 통해 사용자가 반드시 입력해야 할 필드를 명시하였으며, 이는 사용자가 폼을 제출하기 전에 필요한 정보를 확인할 수 있도록 설계하였습니다.**

이는 **아이디와 비밀번호는 필수 입력 서식임을 알 수 있도록 구현할 것**에 대한 내용이며 위 코드에 아이디, 비밀번호에 해당하는 부분에 required 옵션을 추가하여 필수 항목임을 강조하며 경고하도록 마크업하였습니다. 

또한 **각 입력 필드 아래에 오류 메시지가 배치되어 있어, 사용자가 입력한 내용이 유효하지 않을 경우 즉시 피드백을 받을 수 있도록** 설계하려 했고 error-message가 뜨도록 설계하였습니다.
```
<span class="error-message">아이디는 이메일 형식으로 입력해주세요.</span>
<span class="error-message">비밀번호는 10자리 이상 입력해주세요.</span>
```

- **체크박스에 대한 레이블이 명확하게 제공되어 있어, 사용자가 체크박스의 기능을 이해하고 선택할 수 있게 설계하였고 이로 인해 모든 사용자가 기능을 손쉽게 인식하도록 설계하였습니다.**

```
<label for="remember"> <span class="custom-checkbox"></span> 로그인 상태 유지 </label>
<label for="ip-security"><a href="./pages/ip_security.html">IP 보안<span>OFF</span></a></label>
```

5.**```<fieldset>```과 ```<legend>``` 요소를 사용하여 관련된 입력 필드를 그룹화함으로써 폼의 구조를 명확하게 하고, 시각적으로도 더 이해하기 쉽게 만들어 접근성을 향상시키도록 설계하였습니다.**

```
 <fieldset>
 <legend>로그인 정보</legend>
 (이하생략)
 </fieldset>
```



- **레이블 제공의 경우 WAI-ARIA가 아닌 HTML 네이티브 방식으로 구현**
aria-required 속성을 사용하지 않고, 기본 HTML의 required 속성을 사용하여 필수 입력 필드를 설정했습니다.


- **IP 보안 텍스트 클릭 시 미리 제공 된 `pages/ip_secruity.html` 파일이 새창에 열리도록 구현할 것**
```
<label for="ip-security"><a href="./pages/ip_security.html">IP 보안<span>OFF</span></a></label>
```

- **로그인 상태 유지와 IP 보안 ON/OFF UI는 마우스 이외에 `키보드로도 조작 가능`하도록 구현할 것**

레이블과 체크박스를 정확하게 연결하여 레이블을 클릭할 때 체크박스가 선택됩니다. 이는 키보드와 마우스 모두 동작하도록 설계하였습니다.
```
<div class="ip-security-wrap">
<input type="checkbox" id="ip-security" name="ip_security">
<label for="ip-security"><a href="./pages/ip_security.html">IP 보안<span>OFF</span></a></label>
 </div>
```

- **미디어 쿼리를 사용하여 반응형으로 구현할 것(768px 미만 모바일 / 768px 이상 데스크탑)**

```
@media screen and (max-width: 768px){
    .ip-security-wrap{
        display:none;
    }
}

@media screen and (min-width: 768px) {

    .container{
        max-width: calc(500px - 40px);
        height:222px;
        margin: 0 auto;
        padding: 0 20px;
        box-sizing: border-box;
    }

    .login-state{
        float:left;
    }
    .ip-security-wrap{
        display:block;
        float:right;
        position:relative;
        margin-top:10px;
        outline-color:#24388d;
    }

    #ip-security{
        display:none;
    }

    .ip-security-wrap label span{
        color:#121212;
        font-weight: bold;
        margin-left:5px;
        font-size: var(--main-size);
    }
    .ip-security-wrap label a{
        outline-color:#24388d;
    }

}

```



- **모바일 퍼스트로 스타일링 할 것**

중요한컨텐츠를 우선배치하여 사용자가 필요로 하는 정보를 쉽게 찾을 수 있게 된다는 생각을 하였습니다.

- **글자 크기 및 여백(margin 및 padding)은 모두 rem 단위로 설정할 것**

해당조건은 언급하신 px단위로 설정하라는 조건 외엔 모두 사용했다고 생각합니다..!
rem을 보다 안전하게 사용하기위하여 body태그에 16px로 선언후 사용하였습니다.

```
.id input::placeholder, .password input::placeholder{
    font-size:0.9rem;
    padding:1rem;
    color: var(--border-color);
}
```

- **기본 글자 크기는 `16px,` 기본 글자 색상은 `#121212`로 사용할 것**

```
:root{
    --main-size:16px;
    --main-color:#121212;
    --main-bg:#03CF5D;
    --border-color:#DADADA;
    --focus-bg:#e9f0fd;
    --focus-border:#03cf5d;
}
```

- **로고 가로 230px, 가운데 배치  **

```
.header a img{
    width:230px;
}
```

- **포커스 스타일을 기본 색상이 아닌 커스텀 스타일로 변경할 것(색상 `#24388d`)**

```
.id input, .password input{
    height: 48px;
    block-size: 48px;
    width: 100%;
    inline-size: 100%;
    border:none;
    border:1px solid var(--border-color);
    box-sizing: border-box;
    outline-color:#24388d;
    margin-top:10px;
}
```

- **모바일 로그인 폼 로그인 폼의 가로 크기는 `100%`(좌/우 여백 각 20px 포함)로 설정할 것**

```
.container{
    margin: 0 20px 0 20px;
}
```

- **모바일 환경에서 IP 보안 ON/OFF 스위치 UI는 사용자에게 제공되지 않도록 구현할 것**

```
@media screen and (max-width: 768px){
    .ip-security-wrap{
        display:none;
    }
}
```

- **데스크탑 로그인 폼의 가로 크기는 500px(좌/우 여백 각 20px 포함)로 설정할 것**

```
.container{
        max-width: calc(500px - 40px);
        height:222px;
        margin: 0 auto;
        padding: 0 20px;
        box-sizing: border-box;
    }
```

- **입력 서식 글자크기 및 세로 크기, 테두리 선 색상, 배경 색상은 다음과 같이 지정할 것**
기본 상태 : 14px, 45px, #dadada, #fff
포커스 상태 : #03cf5d, #e9f0fd
로그인 버튼의 글자 크기, 세로 크기, 글자 색상, 배경색상, 위쪽 여백
16px, 45px, #fff, #03cf5d, 20px

```
기본상태
.id input::placeholder, .password input::placeholder{
    font-size:14px;
    padding:1rem;
    color: var(--border-color);
}
포커스 상태
	--focus-bg:#e9f0fd;
    --focus-border:#03cf5d;
버튼 조건
	button{
    height: 45px;
    block-size: 45px;
    width: 100%;
    inline-size: 100%;
    background-color:var(--main-bg);
    color:#fff;
    border:1px solid #dadada;
    outline-color:#24388d;
    font-size:var(--main-size);
    margin-top:20px;
}
```

- 로그인 상태 유지 및 IP 보안 ON/OFF `스위치 UI` 영역의 위쪽 여백은 10px로 지정할 것
```
.login-state {
position: relative;
overflow: hidden;
float: right;
margin-top:10px;
}

.ip-security-wrap{
display:block;
float:right;
position:relative;
margin-top:10px;
outline-color:#24388d;
}
```


- 로그인 상태유지 체크박스 배경 이미지 및 크기와 여백은 다음과 같이 지정할 것
- `IP 보안` 스위치의 글자 크기는 16px, 글자 색상은 #121212로 지정할 것
```
.ip-security-wrap label a{
outline-color:#24388d;
font-size:var(--main-size);
color:var(--main-color);
}
```

> 제가 옛날부터 조건사항이 있는데도 조건을 무시하는 경향이 있었어서 오늘은 최대한 조건사항을 맞추면서 마크업 / 스타일링을 하려고 노력하였어서 조건사항이 제 진행 조건이기에 최대한 디테일하게 조건들을 설명하였습니다 감사합니다 :)
