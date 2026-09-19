# 오픈소스 스튜디오 01분반

22300650 / 전도원

## Assignment 3. Multi-Page CRUD Frontend UI

## Service Topic

내가 본 영화를 기록하고 평점과 리뷰를 관리하는 영화 감상 기록 서비스(무비로그)를 CRUD Frontend Service 주제로 정했습니다.

## Data Fields

제목, 장르, 감독, 평점, 리뷰/메모, 포스터 이미지 URL 총 6개 필드로 데이터를 구성했습니다:

1. 제목: 영화 제목
2. 장르: 영화 장르
3. 감독: 영화 감독
4. 평점: 영화를 보고 난 후 남기는 별점 (5점 만점)
5. 리뷰/메모: 영화 감상 후 남기는 감상평
6. 포스터 이미지 URL: 영화의 포스터 이미지

## List Page

index.html 목록에는 6개 필드 중 포스터, 제목, 장르, 감독, 평점 5개 필드를 표시했습니다. 목록의 각 항목을 클릭하면 view.html로 이동합니다.

## Validation

add.html과 edit.html에 공통으로 쓰이는 validateAddForm() / validateEditForm() 함수를 만들어서, form의 onsubmit에서 호출하는 방식으로 4가지 검증을 적용했습니다.

1. 필수값 입력 여부 - 제목, 장르, 감독, 평점이 비어 있으면 alert 후 제출을 막음
2. 문자열 길이 - 제목이 2자 미만이거나 80자를 초과하면 막음
3. 숫자 범위 - 평점이 1~5 범위를 벗어나면 막음
4. Select 선택 여부 - 장르를 선택하지 않으면 막음

검증을 다 통과해야 add.html에서는 alert("게시물이 추가됩니다.")가 뜨고, edit.html에서는 confirm("게시물을 수정할까요?")이 떠서 취소를 누르면 수정이 취소됩니다. view.html의 Delete 버튼도 confirm으로 한 번 더 확인하도록 했습니다.

## RWD

- Bootstrap Grid(container, row/col)와 d-none/d-md-block, d-md-none 유틸리티로 Desktop에서는 Table, Mobile에서는 Card List가 보이도록 나눴습니다.
- my.css에 Media Query를 추가해서 576px 이하에서는 여백과 폼 카드 너비를, 576~992px 구간에서는 상세 페이지 포스터 크기를 조정했습니다.
- 네비게이션 바는 Bootstrap navbar-toggler, collapse를 이용해 Mobile에서 햄버거 메뉴로 접히게 했습니다.

## Bootstrap

container, row/col, navbar(navbar-toggler, collapse 포함), table(table-responsive, table-hover), list-group, form-control/form-select, btn 등을 사용했습니다.

## Problem & Solution

문제
index.html의 표(table)를 Mobile 화면에 그대로 두니 좌우로 스크롤이 생기고 한 화면에 내용이 다 안 들어와서 가독성이 떨어졌습니다.

해결
table-responsive만으로는 부족해서, Bootstrap 유틸리티 클래스(d-none d-md-block / d-md-none)로 Desktop에서는 Table, Mobile에서는 Card List가 각각 따로 렌더링되도록 나눴습니다.

## Reflection

같은 화면을 하나의 CSS로 화면 크기에 따라 늘였다 줄였다 하는 것과, Desktop/Mobile용 마크업을 아예 따로 두고 Bootstrap 유틸리티로 하나만 보이게 전환하는 것은 다른 접근이라는 걸 알게 됐습니다. index.html은 후자(Table <-> Card List) 방식을 쓰고 나머지 페이지는 my.css의 Media Query로 여백과 크기만 조정하는 전자 방식을 썼는데, 상황에 따라 두 방식을 섞어 써도 된다는 걸 배웠습니다.
