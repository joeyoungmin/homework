2주차 과제

✅나의 생각✅

요구컨텐츠는 시멘틱한 태그 사용을 고려하여
body
- section.container
  - div.con
    - article.status(online or offline)
        - img
        - div.indicator
        - p.status-text
태그를 사용

section-container : 전체 컨테이너의 영역
div.con : 컨테이너안의 메인 컨텐츠
article.status : 메인 컨텐츠의 세부 컨텐츠
article.online : online user
article.offline : offline user
img : avatar image
div.indicator : 상태정보를 나타내기 위한 정보
p.status : aria-hidden으로 온라인 또는 오프라인 유무를 기록함

러프하게 생각해보면 이렇게 사용하여 article 4개씩 묶어서 .container에 flex 혹은 .con에 float를 주어 요구사항을 맞춰나가면 될듯하고 아미지는 콘텐츠 이미지로 마크업, indicator는 border-radius로 원 모양을 만들고 online,offline나누어서 상태 정보 구분, p태그는 접근성 부분때문에 넣었습니다.

이후 float로도 구성 해보았고 flex로 구성했을때는 float가 방해가 되기때문에 주석처리 하여 구현하였고 세세한 구현내용은 주석처리 해놓았습니다.

✅ 요구사항 체크리스트 ✅ 

- `homework` 저장소에 다음과 같은 폴더 구조를 구성하고 구조(HTML)는 `avatars.html` 파일에 스타일(CSS)은 `avatars.css` 파일에 구현한다. ✅ 

- 이미지 리소스는 압축파일을 다운로드 받아 `homework` 폴더 내 `assets` 폴더로 복사한다. ✅ 

- 아바타 이미지는 배경 방식이 아닌 `콘텐츠 이미지`(<img> 요소)로 마크업한다. ✅ 
- 이미지 `성능 최적화` 방법에 대해 고민해본다. ✅ 
- 아바타의 `상태 정보`를 알 수 있도록 정보를 제공한다. ✅ 
- 아바타 이미지의 크기 - 64px X 64px ✅ 
- 아바타 이미지 간의 간격 - 20px ✅ 
- 회색 원 배경색 - #DBDBDB ✅ 
- 초록색 원 배경색- #4CFE88 ✅ 

float을 사용하여 다음의 레이아웃을 구현해 본다. ✅ 
flex를 지원하는 환경에서는 다음과 같이 배치되도록 레이아웃을 구현해 본다. ✅ 

- 아바타 과제 수행에 대한 설명을 `md 폴더` 내 `avatars.md` 파일에 작성하고 `homework` 폴더에 있는 `README.md`에 링크로 연결한다. ✅ 
- Github에 배포까지 완료한다. (Github Pages) ✅ 