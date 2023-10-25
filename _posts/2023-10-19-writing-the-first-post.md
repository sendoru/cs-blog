---
title: "Writing The First Post"
categories:
  - Others
tags:
  - html
  - css
  - markup
---

<head>
    <script type="text/x-mathjax-config">

    MathJax.Hub.Config({

    tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}

    });

    </script>

    <script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML' async></script>
</head>

Hello, world!는 언제나 국룰이다.

```c++
// cpp
#include <iostream>
int main() {
    std::cout << "Hello, world!" << std::endl;
    return 0;
}
```

```py
# python
print("Hello, world!")
```

```rust
// Rust
use std::io;
fn main() {
    println!("Hello, world!");
}
```

```js
console.log("Hello, world!")
```

## To-Do List

<ol>
    <li> ✅ 블로그에 글 하나 올리기 </li>
    <li> ✅ 블로그 메인 화면 및 사이드바 등에 개인정보 채워두기 (닉네임, 깃헙 링크 등등) </li>
    <li> ⬜ 제대로 된 자기소개 페이지 하나 만들기 <del><- 쓸 거 없어서 못 만드는 중</del> ㄱ</li>
    <li> ✅ 블로그 맨 위에 메뉴 바 만들기 </li>
    <li> ✅ 블로그 포스트 검색 기능 만들기 </li>
    <li> <del>✅</del> 폰트 및 레이아웃 조절하기. 아직 할 게 좀 남았는데 글 하나 더 써서 기록해둬야겠다.</li>
    <li> ✅ 태그 및 기능 추가하기 </li>
    <li> ❔ 블로그 포스트 연도별 / 카테고리 별 뷰 만들기 <- 반 정도 함 </li>
    <li> <del>⬜ 블로그에 HTML로 포스트 올리기</del> 생각보다 구리다. 그냥 MD에 임베드해서 쓰자. </li>
    <li> <del>⬜ Javascript 관련 기능 어떻게 쓰는지 알아보기</del> 나중에 할래</li>
</ol>

## Tips & Troubleshooting

1. Mardown 파일에 포스트 제목을 따로 쓸 필요는 없다. 굳이 쓰면 이렇게 제목이 두 번 표시된다.

    <figure style="text-align: center;">
        <img src="/cs-blog/assets/images/writing-the-first-post/image_1.png" alt="Screenshot of blog post upper part wtih duplicated title" style="border: 5px solid #555; text-align: center">
        <figcaption> 이미지에 테두리 넣는 법도 배웠다? </figcaption>
    </figure>

2. Markdown 스타일 List

    Markdown에서 ```1. ... <br> 2. ... <br> ... ```같은 형태로 글을 쓰면 저절로 ordered list가 된다. ordered list 안의 (plain text를 포함한) 컴포넌트를 작성할 때 들여쓰기를 안 해주면 컴포넌트가 리스트 밖으로 빠져나온다던가 리스트 번호가 1부터 다시 시작한다던가 하는 안 좋은 일이 일어난다. HTML의 ```<ol>``` + ```<li>``` 등의 태그에서는 스코프가 명확히 정해져 있어서 이런 걸 쓰면 크게 신경 쓸 필요는 없는 일이긴 하다.

    <figure style="text-align: center;">
        <img src="/cs-blog/assets/images/writing-the-first-post/image_2.png" alt="" style="border: 5px solid #555; text-align: center">

        <figcaption> 대충 이렇게 된다. </figcaption>
    </figure>

3. LaTeX 수식

    LaTeX로 수식을 써보자.

    $$ e^{i \theta} = \cos \theta + i \sin \theta $$

    그냥은 안 된다. 다음 코드를 HTML의 ```<head>```에 추가하면 된다. 
    ```html
    <head>
        <script type="text/x-mathjax-config">

        MathJax.Hub.Config({

        tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}

        });

        </script>

        <script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML' async></script>
    </head>
    ```
    Markdown으로 작성 중인 경우에는 ```<head> </head>``` 문서 맨 위에 새로 만들어주고 그 안에 저걸 끼워넣으면 된다. 그런데 markdown에서 이렇게 하면 VSCode의 Markdown Preview 확장 프로그램이 맛이 가기 때문에 작성 내용이 어떻게 표시되는지 보고 싶다면 웹 브라우저에서 확인해야 한다.

4. 레이아웃 변경

    지금 레이아웃에서 마음에 안 드는 게 몇 가지 있다.
    <figure style="width: 80%; margin: auto;">
        <img src="/cs-blog/assets/images/writing-the-first-post/image_3.png" alt="" style="text-align: center">
    </figure>

    일반적인 PC 환경인 가로로 길쭉한 화면 상태에서, 글씨가 쓸데없이 커져서 한 화면에 표시되는 정보량이 너무 적어진다. 화면의 가로 길이가 너무 짧다는 생각도 드는데 이것도 폰트 영향일 수도 있어서 폰트부터 고쳐 본 다음에 다시 확인해야 될 것 같다.
    <figure style="width: 80%; margin: auto;">
        <img src="/cs-blog/assets/images/writing-the-first-post/image_4.png" alt="">
        <figcaption> 이 정도면 좋을텐데 </figcaption>
    </figure>

    반응형 UI의 폰트 크기 조절은 ```_sass/minimal-mistakes/_reset.scss```에서 맨 위에 보이는 ```html``` 블럭 내의 값들을 바꿔 주면 된다. 가로 폭 조절은 ```_sass/minimal-mistakes/_variables.scss```에서 ```breakpoints```주석 아래에 있는 걸 고쳐주면 된다.

5. 태그 및 카테고리 지정

    Markdown 파일 맨 앞에 이렇게 생긴 걸 추가하면 된다.
    ```yaml
    ---
    title: "Writing The First Post"
    categories:
        - Others
    tags:
        - html
        - css
        - markup
    ---
    ```
    
    카테고리를 추가하거나 변경하면 포스트 주소가 바뀐다. 카테고리를 지정하지 않았을 때 주소가 <a href = "http://sendoru.github.io/cs-blog/writing-the-first-post">http://sendoru.github.io/cs-blog/writing-the-first-post/</a>였다면, 카테고리를 Others로 바꾼 후에는 <a href = "http://sendoru.github.io/cs-blog/others/writing-the-first-post/">http://sendoru.github.io/cs-blog/others/writing-the-first-post/</a>가 된다.

    위 문단에서 첫 번째 링크는 접속이 안 되어야 할 것 같은데 캐싱된 게 있는지 예전 페이지로 접속이 된다. 별 상관은 없을 듯

6. ```<div>``` 또는 그 이외의 컨테이너 가운데 정렬

    ```html
    <figure>
        <img src="/cs-blog/assets/images/writing-the-first-post/image_4.png" alt="">
        <figcaption> 이 정도면 좋을텐데 </figcaption>
    </figure>
    ```
    
    이렇게 이미지를 넣을 때, 이미지 사이즈를 80%로 줄이고 가운데 정렬로 만드려면  ```style="width: 80%; margin: auto;"``` 스타일 속성을 **figure**에 넣어줘야 한다.

