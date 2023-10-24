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
    <li> ⬜ 제대로 된 자기소개 페이지 하나 만들기 </li>
    <li> ✅ 블로그 맨 위에 메뉴 바 만들기 </li>
    <li> ✅ 블로그 포스트 검색 기능 만들기 </li>
    <li> ⬜ 폰트 및 레이아웃 조절하기 </li>
    <li> ⬜ 해시태그 기능 추가하기 </li>
    <li> ❔ 블로그 포스트 연도별 / 카테고리 별 뷰 만들기 </li>
    <li> ⬜ 블로그에 HTML로 포스트 올리기 </li>
    <li> ⬜ Javascript 관련 기능 어떻게 쓰는지 알아보기</li>
</ol>

## Tips & Troubleshooting

1. Mardown 파일에 포스트 제목을 따로 쓸 필요는 없다. 굳이 쓰면 이렇게 제목이 두 번 표시된다.

    <figure style="test-align: center;">
        <img src="/csblog/assets/images/writing-the-first-post/image_1.png" alt="Screenshot of blog post upper part wtih duplicated title" style="border: 5px solid #555; text-align: center">
        <figcaption> 이미지에 테두리 넣는 법도 배웠다? </figcaption>
    </figure>

2. Markdown에서 ```1. ... <br> 2. ... <br> ... ```같은 형태로 글을 쓰면 저절로 ordered list가 된다. ordered list 안의 (plain text를 포함한) 컴포넌트를 작성할 때 들여쓰기를 안 해주면 컴포넌트가 리스트 밖으로 빠져나온다던가 리스트 번호가 1부터 다시 시작한다던가 하는 안 좋은 일이 일어난다. HTML의 ```<ol>``` + ```<li>``` 등의 태그에서는 스코프가 명확히 정해져 있어서 이런 걸 쓰면 크게 신경 쓸 필요는 없는 일이긴 하다.

    <figure style="test-align: center;">
        <img src="/csblog/assets/images/writing-the-first-post/image_2.png" alt="" style="border: 5px solid #555; text-align: center">

        <figcaption> 대충 이렇게 된다. </figcaption>
    </figure>

3. LaTeX로 수식을 써보자.

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

4. 

5. 더 쓸게 없으면 기능 추가나 해 보자.